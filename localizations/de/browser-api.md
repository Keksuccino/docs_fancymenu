---
title: Browser-JavaScript-API
description: >-
  Wie du die JavaScript-API von FancyMenu in MCEF-basierten Mod-Funktionen wie
  dem Browser-Element verwendest.
---

# FancyMenu JavaScript API

FancyMenu fügt in jede MCEF-gestützte Funktion einen JavaScript-Bridge ein (zum Beispiel in das **Browser**-Element). Über diesen Bridge kann Web-Inhalt:

- jede FancyMenu-[Aktion](./action-scripts) direkt aus JavaScript ausführen,
- jeden FancyMenu-[Platzhalter](/placeholders) asynchron auslesen.

Zwei globale Objekte stellen die API bereit:
- `window.fancymenu` – primärer Namensraum
- `window.FancyMenu` – Alias (spiegelt exakt die Struktur von `fancymenu`)

Verwende das Ereignis `fancymenu-ready` oder eine Feature-Erkennung, um sicherzustellen, dass der Bridge verfügbar ist, bevor du ihn aufrufst.

## 1. Namensräume & Struktur

- `fancymenu.actions` – führt FancyMenu-Aktionen aus dem Browser aus.
- `fancymenu.placeholders` – liest FancyMenu-Platzhalterwerte asynchron aus.
- `FancyMenu` spiegelt `fancymenu`, daher stellen beide dieselben Unter-Namensräume bereit.

Aktionen stellen zwei Hilfsfunktionen bereit:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Verfügbarkeit

```javascript
if (typeof fancymenu !== 'undefined') {
    // sicher verwendbar
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API ist bereit');
});
```

Inhalte können auch lokal gehostet werden: Lege HTML-Dateien in `config/fancymenu/assets/` ab und lade sie über URLs der Form `file:///config/fancymenu/assets/<name>.html`.

## 3. Aktionen ausführen

Verwende den Namensraum `fancymenu.actions`. Jeder Aufruf entspricht den Aktionsstrings, die in FancyMenu-Skripten verwendet werden.

### Schnelle Aufrufe

```javascript
fancymenu.actions.execute('quitgame');                // Aktion ohne Wert
fancymenu.actions.execute('opengui', 'title_screen'); // Aktion mit Wert
fancymenu.actions.execute('set_variable', 'hp:20');   // Wert im Format name:wert
```

### Mit Callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Titelseite geöffnet'),
    error  => console.error('Öffnen fehlgeschlagen:', error)
);

// Der Wert-Parameter ist optional. Wenn er weggelassen wird, gib die Callbacks direkt nach actionType an.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Beenden ausgelöst'),
    error  => console.error('Beenden fehlgeschlagen:', error)
);

Legacy-Hilfsfunktionen `fancymenu.execute(...)` und `fancymenu.executeWithCallback(...)` funktionieren weiterhin und leiten an den Namensraum `actions` weiter, sodass vorhandene Inhalte nicht sofort angepasst werden müssen.
```

### Häufige Aktionstypen

- `quitgame` – beendet das Spiel sofort (kein Wert)
- `back_to_last_screen` – kehrt zur vorherigen GUI zurück (kein Wert)
- `opengui` – öffnet ein FancyMenu- oder Vanilla-UI (Wert: Bildschirm-ID)
- `openlink` – öffnet einen Browser (Wert: URL)
- `sendmessage` – sendet eine Chat-Nachricht (Wert: Nachrichtentext)
- `set_variable` – setzt eine FancyMenu-Variable (Wert: `name:wert`)
- `joinserver` – verbindet sich mit einem Server (Wert: Adresse)
- `disconnect_server_or_world` – trennt die Verbindung und wechselt zu einem Zielbildschirm (Wert: Bildschirm-ID)

Jede in FancyMenu vorhandene Aktion ist über den Bridge verfügbar; siehe [Action-Skripte](./action-scripts) für den vollständigen Katalog.

## 4. Platzhalter lesen

Das [Platzhalter](/placeholders)-System von FancyMenu ist über `fancymenu.placeholders` (und `FancyMenu.placeholders`) verfügbar. Beide Hilfsmethoden geben `Promise<string>` zurück:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Variablen übergeben

- Variablen sind Zeichenketten im Format `name:wert`. Der Bridge trennt nur am **ersten** Doppelpunkt, sodass der Wert weitere Doppelpunkte enthalten kann.
- Namen und Werte werden getrimmt; leere Namen werden abgelehnt.
- Gib so viele Variablen an, wie der Platzhalter benötigt. Optionale kannst du weglassen.

### Beispiele

```javascript
// Keine Variablen
fancymenu.placeholders.get('playername')
    .then(name => console.log('Spieler:', name));

// Eine Variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Laufzeit (s):', seconds));

// Mehrere Variablen
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Ausgewählter Teil:', part));
```

### Fehlermodell

Abgelehnte Promises enthalten einen strukturierten Fehler:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Beispiel für Fehlerbehandlung:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Vollständiges Beispiel

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu-Integration</title>
</head>
<body>
    <h1>Spielsteuerung</h1>
    
    <button onclick="quitGame()">Spiel beenden</button>
    <button onclick="openTitleScreen()">Titelseite</button>
    <button onclick="disconnectFromServer()">Trennen</button>
    <button onclick="setVariable()">Variable setzen</button>
    <button onclick="loadPlaceholders()">Platzhalter laden</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('Die FancyMenu-API ist noch nicht verfügbar.');
                return null;
            }
            return fancymenu.actions || fancymenu;
        }

        function quitGame() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('quitgame');
        }
        
        function openTitleScreen() {
            const actions = getActions();
            if (!actions) return;
            actions.executeWithCallback(
                'opengui',
                'title_screen',
                () => console.log('Titelseite geöffnet!'),
                err => console.error('Fehler:', err)
            );
        }
        
        function disconnectFromServer() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('disconnect_server_or_world', 'title_screen');
        }
        
        function setVariable() {
            const actions = getActions();
            if (!actions) return;
            var varName = prompt('Variablenname:');
            var varValue = prompt('Variablenwert:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('Die FancyMenu-Platzhalter-API ist noch nicht verfügbar.');
                return;
            }

            Promise.all([
                fancymenu.placeholders.get('playername'),
                fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false'),
                fancymenu.placeholders.getWithVars(
                    'split_text',
                    'input:apple|banana|carrot',
                    'regex:\\|',
                    'max_parts:-1',
                    'split_index:1'
                )
            ]).then(([playerName, uptimeSeconds, secondFruit]) => {
                document.getElementById('placeholderOutput').textContent =
                    'Spieler: ' + playerName + '\n' +
                    'Laufzeit (Sekunden): ' + uptimeSeconds + '\n' +
                    'Zweites Fruchtstück: ' + secondFruit;
            }).catch(error => {
                console.error('Platzhalteranfrage fehlgeschlagen:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Best Practices & Hinweise

- **Den Bridge erkennen**, bevor du ihn verwendest, oder auf `fancymenu-ready` warten.
- **Fehler behandeln** (Callbacks für [Aktionen](/action-scripts), `.catch` für [Platzhalter](/placeholders)), um hilfreiche Rückmeldungen anzuzeigen.
- **Eingaben validieren**, bevor du sie an Aktionen oder [Platzhalter](/placeholders)-Variablen übergibst.
- **Anfragen drosseln**; vermeide es, den Bridge mit sehr vielen Aufrufen in kurzer Zeit zu belasten (insbesondere bei Platzhalter-Aktualisierungsschleifen).
- **Sicherheit**: Aktionen werden mit den normalen Berechtigungen des Spielers ausgeführt. Gehe vorsichtig mit benutzerbereitgestellten Daten um, um Injektionen zu vermeiden.

## 7. Fehlerbehebung

1. Stelle sicher, dass die Seite in einem von FancyMenu gesteuerten MCEF-Browser geladen wird.
2. Prüfe die Browser-Konsole auf JavaScript-Fehler.
3. Verifiziere, dass die [Platzhalter](/placeholders)-ID bzw. der [Aktions](/action-scripts)-Typ korrekt ist und die erforderlichen Werte angegeben wurden.
4. Sieh im Minecraft-Log (`latest.log`) nach FancyMenu-Fehlermeldungen, falls die Ausführung unerwartet fehlschlägt.
