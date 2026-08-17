---
title: Browser-JavaScript-API
description: >-
  So verwendest du die JavaScript-API von FancyMenu in Rinku-basierten
  Mod-Funktionen wie dem Browser-Element.
---
# FancyMenu-JavaScript-API

FancyMenu injiziert eine JavaScript-Bridge in jede auf [Rinku](https://modrinth.com/mod/rinku) basierende Funktion (zum Beispiel das **Browser**-Element). Die Bridge ermöglicht Webinhalten:

- jede FancyMenu-[Aktion](./action-scripts) direkt aus JavaScript auszuführen,
- jeden FancyMenu-[Platzhalter](/placeholders) asynchron auszulesen.

Zwei globale Objekte stellen die API bereit:
- `window.fancymenu` – primärer Namespace
- `window.FancyMenu` – Alias (spiegelt exakt die Struktur von `fancymenu` wider)

Verwende das Ereignis `fancymenu-ready` oder eine Funktionserkennung, um sicherzustellen, dass die Bridge vor ihrer Verwendung verfügbar ist.

## 1. Namespaces und Struktur

- `fancymenu.actions` – FancyMenu-Aktionen im Browser ausführen.
- `fancymenu.placeholders` – FancyMenu-Platzhalterwerte asynchron auslesen.
- `FancyMenu` spiegelt `fancymenu` wider, daher stellen beide dieselben Unternamespaces bereit.

Aktionen stellen zwei Hilfsfunktionen bereit:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Verfügbarkeit

```javascript
if (typeof fancymenu !== 'undefined') {
    // kann sicher verwendet werden
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu-API ist bereit');
});
```

Inhalte können auch lokal gehostet werden: Lege HTML-Dateien in `<game-directory>/config/fancymenu/assets/` ab und lade sie über URLs der Form `file:///config/fancymenu/assets/<name>.html`.

## 3. Aktionen ausführen

Verwende den Namespace `fancymenu.actions`. Jeder Aufruf entspricht den in FancyMenu-Skripten verwendeten Aktionszeichenfolgen.

### Schnelle Aufrufe

```javascript
fancymenu.actions.execute('quitgame');                // Aktion ohne Wert
fancymenu.actions.execute('opengui', 'title_screen'); // Aktion mit Wert
fancymenu.actions.execute('set_variable', 'hp:20');   // Wert im Format name:value
```

### Mit Rückruffunktionen

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Titelseite geöffnet'),
    error  => console.error('Öffnen fehlgeschlagen:', error)
);

// Der value-Parameter ist optional. Wenn er weggelassen wird, übergib die Rückruffunktionen direkt nach actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Beenden ausgelöst'),
    error  => console.error('Beenden fehlgeschlagen:', error)
);
```

Die älteren Hilfsfunktionen `fancymenu.execute(...)` und `fancymenu.executeWithCallback(...)` delegieren weiterhin an den Namespace `actions`.

### Häufige Aktionstypen

- `quitgame` – beendet das Spiel sofort (kein Wert)
- `back_to_last_screen` – kehrt zur vorherigen GUI zurück (kein Wert)
- `opengui` – öffnet einen FancyMenu- oder Vanilla-Bildschirm (Wert: Bildschirmkennung)
- `openlink` – startet einen Browser (Wert: URL)
- `sendmessage` – sendet eine Chatzeile (Wert: Nachrichtentext)
- `set_variable` – weist eine FancyMenu-Variable zu (Wert: `name:value`)
- `joinserver` – verbindet sich mit einem Server (Wert: Adresse)
- `disconnect_server_or_world` – trennt die Verbindung und wechselt zu einem Zielbildschirm (Wert: Bildschirmkennung)

Jede in FancyMenu vorhandene Aktion ist über die Bridge verfügbar. Eine vollständige Übersicht findest du unter [Aktionsskripte](./action-scripts).

## 4. Platzhalter auslesen

Das [Platzhalter](/placeholders)-System von FancyMenu wird über `fancymenu.placeholders` (und `FancyMenu.placeholders`) bereitgestellt. Beide Hilfsmethoden geben `Promise<string>` zurück:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Variablen übergeben

- Variablen sind Zeichenfolgen im Format `name:value`. Die Bridge teilt nur am **ersten** Doppelpunkt, daher darf der Wert weitere Doppelpunkte enthalten.
- Namen und Werte werden von Leerzeichen am Anfang und Ende bereinigt; leere Namen werden abgelehnt.
- Gib so viele Variablen an, wie der Platzhalter benötigt. Optionale Variablen können weggelassen werden.

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

Beispiel für die Fehlerbehandlung:

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
    <button onclick="disconnectFromServer()">Verbindung trennen</button>
    <button onclick="setVariable()">Variable setzen</button>
    <button onclick="loadPlaceholders()">Platzhalter laden</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('FancyMenu-API ist noch nicht verfügbar.');
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
                console.warn('FancyMenu-Platzhalter-API ist noch nicht verfügbar.');
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
                    'Zweite Frucht: ' + secondFruit;
            }).catch(error => {
                console.error('Platzhalteranfrage fehlgeschlagen:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Bewährte Methoden und Hinweise

- **Erkenne die Bridge**, bevor du sie verwendest, oder höre auf `fancymenu-ready`.
- **Behandle Fehler** (Rückruffunktionen für [Aktionen](/action-scripts), `.catch` für [Platzhalter](/placeholders)), um hilfreiche Rückmeldungen anzuzeigen.
- **Validiere Eingaben**, bevor du sie an Aktionen oder [Platzhalter](/placeholders)-Variablen übergibst.
- **Begrenze die Anfragen**; vermeide es, die Bridge mit schnellen, aufeinanderfolgenden Aufrufen zu überlasten (insbesondere bei Schleifen zur regelmäßigen Aktualisierung von Platzhaltern).
- **Sicherheit:** Browserinhalte können jede registrierte FancyMenu-Aktion aufrufen, einschließlich Datei-, Netzwerk-, Befehls-, Zwischenablage-, Ressourcenpaket-, Link- und Beenden-Aktionen. Lade nur vertrauenswürdige Seiten und validiere alle aus Webinhalten empfangenen Daten.

## 7. Fehlerbehebung

1. Stelle sicher, dass die Seite in einem von FancyMenu kontrollierten Rinku-Browser geladen ist.
2. Überprüfe die Browserkonsole auf JavaScript-Fehler.
3. Vergewissere dich, dass die [Platzhalter](/placeholders)-Kennung bzw. der [Aktionstyp](/action-scripts) korrekt ist und alle erforderlichen Werte angegeben wurden.
4. Wenn die Ausführung unerwartet fehlschlägt, überprüfe das Minecraft-Log (`latest.log`) auf FancyMenu-Fehlermeldungen.
