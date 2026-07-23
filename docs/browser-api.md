---
title: Browser JavaScript API
description: How to use FancyMenu's JavaScript API in MCEF-based mod features like the Browser element.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-08-24T09:30:22.976Z
---

# FancyMenu JavaScript API

FancyMenu injects a JavaScript bridge into every MCEF-backed feature (for example the **Browser** element). The bridge lets web content:

- run any FancyMenu [action](./action-scripts) directly from JavaScript,
- read any FancyMenu [placeholder](/placeholders) asynchronously.

Two globals expose the API:
- `window.fancymenu` – primary namespace
- `window.FancyMenu` – alias (mirrors the exact shape of `fancymenu`)

Use the `fancymenu-ready` event, or feature detection, to ensure the bridge is available before calling it.

## 1. Namespaces & Structure

- `fancymenu.actions` – execute FancyMenu actions from the browser.
- `fancymenu.placeholders` – read FancyMenu placeholder values asynchronously.
- `FancyMenu` mirrors `fancymenu`, so both expose the same sub-namespaces.

Actions expose two helpers:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Availability

```javascript
if (typeof fancymenu !== 'undefined') {
    // safe to use
}

window.addEventListener('fancymenu-ready', () => {
    console.log('FancyMenu API is ready');
});
```

Content may also be hosted locally: place HTML files in `<game-directory>/config/fancymenu/assets/` and load them through URLs of the form `file:///config/fancymenu/assets/<name>.html`.

## 3. Executing Actions

Use the `fancymenu.actions` namespace. Each call mirrors the action strings used in FancyMenu scripts.

### Quick Calls

```javascript
fancymenu.actions.execute('quitgame');                // action without value
fancymenu.actions.execute('opengui', 'title_screen'); // action with value
fancymenu.actions.execute('set_variable', 'hp:20');   // value uses name:value format
```

### With Callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Opened title screen'),
    error  => console.error('Open failed:', error)
);

// The value parameter is optional. When omitted, pass the callbacks directly after actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Quit triggered'),
    error  => console.error('Quit failed:', error)
);

Legacy helpers `fancymenu.execute(...)` and `fancymenu.executeWithCallback(...)` still work and delegate to the `actions` namespace, so existing content does not need immediate changes.
```

### Common Action Types

- `quitgame` – immediately quits the game (no value)
- `back_to_last_screen` – returns to the previous GUI (no value)
- `opengui` – opens a FancyMenu or vanilla screen (value: screen identifier)
- `openlink` – launches a browser (value: URL)
- `sendmessage` – posts a chat line (value: message text)
- `set_variable` – assigns a FancyMenu variable (value: `name:value`)
- `joinserver` – connects to a server (value: address)
- `disconnect_server_or_world` – disconnects and moves to a target screen (value: screen identifier)

Every action that exists in FancyMenu is available through the bridge; see [action scripts](./action-scripts) for the complete catalog.

## 4. Reading Placeholders

FancyMenu’s [placeholder](/placeholders) system is exposed through `fancymenu.placeholders` (and `FancyMenu.placeholders`). Both helper methods return `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Supplying Variables

- Variables are strings in `name:value` form. The bridge splits on the **first** colon only, so the value can contain additional colons.
- Names and values are trimmed; empty names are rejected.
- Provide as many variables as the placeholder requires. Omit optional ones.

### Examples

```javascript
// No variables
fancymenu.placeholders.get('playername')
    .then(name => console.log('Player:', name));

// One variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Uptime (s):', seconds));

// Multiple variables
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Selected part:', part));
```

### Error Model

Rejected promises contain a structured error:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Example handling:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Complete Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>FancyMenu Integration</title>
</head>
<body>
    <h1>Game Controls</h1>
    
    <button onclick="quitGame()">Quit Game</button>
    <button onclick="openTitleScreen()">Title Screen</button>
    <button onclick="disconnectFromServer()">Disconnect</button>
    <button onclick="setVariable()">Set Variable</button>
    <button onclick="loadPlaceholders()">Load Placeholders</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('FancyMenu API is not available yet.');
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
                () => console.log('Title screen opened!'),
                err => console.error('Error:', err)
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
            var varName = prompt('Variable name:');
            var varValue = prompt('Variable value:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('FancyMenu placeholder API is not available yet.');
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
                    'Player: ' + playerName + '\n' +
                    'Uptime (seconds): ' + uptimeSeconds + '\n' +
                    'Second fruit: ' + secondFruit;
            }).catch(error => {
                console.error('Placeholder request failed:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Best Practices & Notes

- **Detect the bridge** before using it, or listen for `fancymenu-ready`.
- **Handle errors** (callbacks for [actions](/action-scripts), `.catch` for [placeholders](/placeholders)) to present useful feedback.
- **Validate input** before passing it to actions or [placeholder](/placeholders) variables.
- **Throttle requests**; avoid spamming the bridge with rapid-fire calls (especially placeholder refresh loops).
- **Security**: actions execute with the player’s normal permissions. Treat user-provided data with care to avoid injection.

## 7. Troubleshooting

1. Confirm the page is loaded in a FancyMenu-controlled MCEF browser.
2. Check the browser console for JavaScript errors.
3. Verify the [placeholder](/placeholders) identifier or [action](/action-scripts) type is correct and that required values are supplied.
4. Review the Minecraft log (`latest.log`) for FancyMenu error messages if execution fails unexpectedly.
