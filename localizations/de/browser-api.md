---
title: Browser-JavaScript-API
description: >-
  So verwendest du die JavaScript-API von FancyMenu in Rinku-basierten
  Mod-Funktionen wie dem Browser-Element.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# FancyMenu-JavaScript-API

FancyMenu fügt jeder Funktion, die auf [Rinku](https://modrinth.com/mod/rinku) basiert (zum Beispiel dem Element **Browser**), eine JavaScript-Bridge hinzu. Damit können Webinhalte:

- jede FancyMenu-[Aktion](/action-scripts) direkt aus JavaScript ausführen,
- jeden FancyMenu-[Platzhalter](/placeholders) asynchron auslesen.

Zwei globale Variablen machen die API verfügbar:
- `window.fancymenu` – primärer Namensraum
- `window.FancyMenu` – Alias (hat exakt dieselbe Struktur wie `fancymenu`)

Verwende das Ereignis `fancymenu-ready` oder eine Feature-Erkennung, um sicherzustellen, dass die Bridge verfügbar ist, bevor du sie aufrufst.

## 1. Namensräume und Struktur

- `fancymenu.actions` – führt FancyMenu-Aktionen im Browser aus.
- `fancymenu.placeholders` – liest FancyMenu-Platzhalterwerte asynchron aus.
- `FancyMenu` entspricht `fancymenu`; beide stellen also dieselben Unternamensräume bereit.

Für Aktionen gibt es zwei Hilfsfunktionen:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Verfügbarkeit

```javascript
if (typeof fancymenu !== 'undefined') {
    // Kann sicher verwendet werden
}

window.addEventListener('fancymenu-ready', () => {
    console.log('Die FancyMenu-API ist bereit');
});
```

Inhalte können auch lokal gehostet werden: Lege HTML-Dateien in `<game-directory>/config/fancymenu/assets/` ab und lade sie über URLs im Format `file:///config/fancymenu/assets/<name>.html`.

## 3. Aktionen ausführen

Verwende den Namensraum `fancymenu.actions`. Jeder Aufruf entspricht den Aktionszeichenfolgen, die in FancyMenu-Skripten verwendet werden.

### Schnellaufrufe

```javascript
fancymenu.actions.execute('quitgame');                // Aktion ohne Wert
fancymenu.actions.execute('opengui', 'title_screen'); // Aktion mit Wert
fancymenu.actions.execute('set_variable', 'hp:20');   // Wert im Format name:value
```

### Mit Callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Titelbildschirm geöffnet'),
    error  => console.error('Öffnen fehlgeschlagen:', error)
);

// Der Wert-Parameter ist optional. Wenn du ihn weglässt, übergib die Callbacks direkt nach actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Beenden ausgelöst'),
    error  => console.error('Beenden fehlgeschlagen:', error)
);
```

Die älteren Hilfsfunktionen `fancymenu.execute(...)` und `fancymenu.executeWithCallback(...)` leiten Aufrufe weiterhin an den Namensraum `actions` weiter.

### Häufige Aktionstypen

- `quitgame` – beendet das Spiel sofort (ohne Wert)
- `back_to_last_screen` – kehrt zur vorherigen GUI zurück (ohne Wert)
- `opengui` – öffnet einen FancyMenu- oder Vanilla-Bildschirm (Wert: Bildschirmkennung)
- `openlink` – öffnet einen Browser (Wert: URL)
- `sendmessage` – sendet eine Chatnachricht (Wert: Nachrichtentext)
- `set_variable` – weist einer FancyMenu-Variable einen Wert zu (Wert: `name:value`)
- `joinserver` – verbindet sich mit einem Server (Wert: Adresse)
- `disconnect_server_or_world` – trennt die Verbindung und wechselt zu einem Zielbildschirm (Wert: Bildschirmkennung)

Über die Bridge sind alle in FancyMenu verfügbaren Aktionen erreichbar. Eine vollständige Übersicht findest du unter [Aktionsskripte](/action-scripts).

## 4. Platzhalter auslesen

Das [Platzhaltersystem](/placeholders) von FancyMenu ist über `fancymenu.placeholders` (und `FancyMenu.placeholders`) verfügbar. Beide Hilfsfunktionen geben ein `Promise<string>` zurück:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Variablen angeben

- Variablen sind Zeichenfolgen im Format `name:value`. Die Bridge trennt nur am **ersten** Doppelpunkt, daher kann der Wert weitere Doppelpunkte enthalten.
- Namen und Werte werden von Leerzeichen am Anfang und Ende bereinigt; leere Namen werden abgelehnt.
- Gib alle vom Platzhalter benötigten Variablen an. Optionale Variablen kannst du weglassen.

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

### Fehlerbehandlung

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
    <button onclick="openTitleScreen()">Titelbildschirm</button>
    <button onclick="disconnectFromServer()">Verbindung trennen</button>
    <button onclick="setVariable()">Variable festlegen</button>
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
                    'Zweite Frucht: ' + secondFruit;
            }).catch(error => {
                console.error('Platzhalterabfrage fehlgeschlagen:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Bewährte Vorgehensweisen und Hinweise

- **Prüfe, ob die Bridge verfügbar ist**, bevor du sie verwendest, oder höre auf `fancymenu-ready`.
- **Behandle Fehler** (Callbacks für [Aktionen](/action-scripts), `.catch` für [Platzhalter](/placeholders)), um hilfreiche Rückmeldungen geben zu können.
- **Überprüfe Eingaben**, bevor du sie an Aktionen oder [Platzhalter](/placeholders) übergibst.
- **Begrenze die Anfragehäufigkeit** und vermeide zu viele schnelle Aufrufe der Bridge (insbesondere Schleifen, die Platzhalter ständig aktualisieren).
- **Sicherheit:** Browserinhalte können jede registrierte FancyMenu-Aktion aufrufen, darunter Datei-, Netzwerk-, Befehls-, Zwischenablage-, Ressourcenpaket-, Link- und Beenden-Aktionen. Lade nur vertrauenswürdige Seiten und überprüfe alle von Webinhalten empfangenen Daten.

## 7. Fehlerbehebung

1. Vergewissere dich, dass die Seite in einem von FancyMenu gesteuerten Rinku-Browser geladen ist.
2. Prüfe die Browserkonsole auf JavaScript-Fehler.
3. Überprüfe, ob die [Platzhalterkennung](/placeholders) oder der [Aktionstyp](/action-scripts) korrekt ist und alle erforderlichen Werte angegeben wurden.
4. Falls die Ausführung unerwartet fehlschlägt, suche im Minecraft-Protokoll (`latest.log`) nach FancyMenu-Fehlermeldungen.
