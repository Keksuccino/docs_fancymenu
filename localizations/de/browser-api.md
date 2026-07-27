---
title: Browser JavaScript-API
description: >-
  So verwenden Sie die JavaScript-API von FancyMenu in MCEF-basierten
  Mod-Funktionen wie dem Browser-Element.
---

# FancyMenu JavaScript-API

FancyMenu injiziert eine JavaScript-Bridge in jede auf MCEF basierende Funktion (zum Beispiel das **Browser**-Element). Über diese Bridge kann Webinhalt:

- beliebige FancyMenu-[Aktionen](./action-scripts) direkt aus JavaScript ausführen,
- beliebige FancyMenu-[Platzhalter](/placeholders) asynchron auslesen.

Zwei globale Objekte stellen die API bereit:
- `window.fancymenu` – primärer Namespace
- `window.FancyMenu` – Alias (spiegelt exakt die Struktur von `fancymenu`)

Verwenden Sie das Ereignis `fancymenu-ready` oder eine Feature-Erkennung, um sicherzustellen, dass die Bridge verfügbar ist, bevor Sie sie aufrufen.

## 1. Namespaces & Struktur

- `fancymenu.actions` – führt FancyMenu-Aktionen im Browser aus.
- `fancymenu.placeholders` – liest FancyMenu-Platzhalterwerte asynchron aus.
- `FancyMenu` spiegelt `fancymenu`, daher stellen beide dieselben Unter-Namespaces bereit.

Aktionen bieten zwei Hilfsfunktionen:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Verfügbarkeit

```javascript
if (typeof fancymenu !== 'undefined') {
    // sicher verwendbar
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu-API ist bereit');
});
```

Inhalt kann auch lokal gehostet werden: Legen Sie HTML-Dateien in `<game-directory>/config/fancymenu/assets/` ab und laden Sie sie über URLs der Form `file:///config/fancymenu/assets/<name>.html`.

## 3. Aktionen ausführen

Verwenden Sie den Namespace `fancymenu.actions`. Jeder Aufruf entspricht den Aktions-Strings, die in FancyMenu-Skripten verwendet werden.

### Schnelle Aufrufe

```javascript
fancymenu.actions.execute('quitgame');                // Aktion ohne Wert
fancymenu.actions.execute('opengui', 'title_screen'); // Aktion mit Wert
fancymenu.actions.execute('set_variable', 'hp:20');   // Wert verwendet das Format name:value
```

### Mit Callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Titelbildschirm geöffnet'),
    error  => console.error('Öffnen fehlgeschlagen:', error)
);

// Der Parameter value ist optional. Wenn er weggelassen wird, übergeben Sie die Callbacks direkt nach actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Beenden ausgelöst'),
    error  => console.error('Beenden fehlgeschlagen:', error)
);
```

Die Legacy-Helfer `fancymenu.execute(...)` und `fancymenu.executeWithCallback(...)` leiten weiterhin an den Namespace `actions` weiter.

### Häufige Aktionstypen

- `quitgame` – beendet das Spiel sofort (kein Wert)
- `back_to_last_screen` – kehrt zur vorherigen GUI zurück (kein Wert)
- `opengui` – öffnet ein FancyMenu- oder Vanilla-Menü (Wert: Bildschirmkennung)
- `openlink` – öffnet einen Browser (Wert: URL)
- `sendmessage` – sendet eine Chat-Nachricht (Wert: Nachrichtentext)
- `set_variable` – weist eine FancyMenu-Variable zu (Wert: `name:value`)
- `joinserver` – verbindet mit einem Server (Wert: Adresse)
- `disconnect_server_or_world` – trennt die Verbindung und wechselt zu einem Zielbildschirm (Wert: Bildschirmkennung)

Jede in FancyMenu vorhandene Aktion ist über die Bridge verfügbar; siehe [action scripts](./action-scripts) für den vollständigen Katalog.

## 4. Platzhalter lesen

Das [Platzhalter](/placeholders)-System von FancyMenu wird über `fancymenu.placeholders` (und `FancyMenu.placeholders`) bereitgestellt. Beide Hilfsmethoden geben `Promise<string>` zurück:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Variablen übergeben

- Variablen sind Zeichenketten im Format `name:value`. Die Bridge trennt nur am **ersten** Doppelpunkt, sodass der Wert weitere Doppelpunkte enthalten kann.
- Namen und Werte werden getrimmt; leere Namen werden abgelehnt.
- Übergeben Sie so viele Variablen, wie der Platzhalter benötigt. Optionale Variablen können weggelassen werden.

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

Beispiel für die Behandlung:

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
    <button onclick="openTitleScreen()">Titelbildschirm</button>
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
                () => console.log('Titelbildschirm geöffnet!'),
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

## 6. Best Practices & Hinweise

- **Erkennen Sie die Bridge**, bevor Sie sie verwenden, oder hören Sie auf `fancymenu-ready`.
- **Behandeln Sie Fehler** (Callbacks für [actions](/action-scripts), `.catch` für [placeholders](/placeholders)), um hilfreiches Feedback anzuzeigen.
- **Validieren Sie Eingaben**, bevor Sie sie an Aktionen oder [Platzhalter](/placeholders)-Variablen übergeben.
- **Drosseln Sie Anfragen**; vermeiden Sie es, die Bridge mit sehr häufigen Aufrufen zu überlasten (insbesondere bei Platzhalter-Aktualisierungsschleifen).
- **Sicherheit:** Browser-Inhalt kann jede registrierte FancyMenu-Aktion aufrufen, einschließlich Datei-, Netzwerk-, Befehls-, Zwischenablage-, Resource-Pack-, Link- und Beenden-Aktionen. Laden Sie nur vertrauenswürdige Seiten und validieren Sie alle Daten, die aus Webinhalt empfangen werden.

## 7. Fehlerbehebung

1. Stellen Sie sicher, dass die Seite in einem von FancyMenu gesteuerten MCEF-Browser geladen wird.
2. Prüfen Sie die Browser-Konsole auf JavaScript-Fehler.
3. Vergewissern Sie sich, dass die [Platzhalter](/placeholders)-Kennung oder der [Aktion](/action-scripts)-Typ korrekt ist und die erforderlichen Werte übergeben werden.
4. Prüfen Sie das Minecraft-Protokoll (`latest.log`) auf FancyMenu-Fehlermeldungen, falls die Ausführung unerwartet fehlschlägt.
