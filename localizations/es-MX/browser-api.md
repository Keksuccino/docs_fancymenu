---
title: API de JavaScript del navegador
description: >-
  Cómo usar la API de JavaScript de FancyMenu en funciones de mods basadas en
  Rinku, como el elemento Browser.
---
# API de JavaScript de FancyMenu

FancyMenu inyecta un puente de JavaScript en cada función respaldada por [Rinku](https://modrinth.com/mod/rinku) (por ejemplo, el elemento **Browser**). El puente permite que el contenido web:

- ejecute cualquier [acción de FancyMenu](./action-scripts) directamente desde JavaScript,
- lea de forma asíncrona cualquier [placeholder de FancyMenu](/placeholders).

Dos globals exponen la API:
- `window.fancymenu` – espacio de nombres principal
- `window.FancyMenu` – alias (refleja exactamente la misma estructura que `fancymenu`)

Usa el evento `fancymenu-ready`, o la detección de características, para asegurarte de que el puente esté disponible antes de llamarlo.

## 1. Espacios de nombres y estructura

- `fancymenu.actions` – ejecuta acciones de FancyMenu desde el navegador.
- `fancymenu.placeholders` – lee valores de placeholders de FancyMenu de forma asíncrona.
- `FancyMenu` refleja a `fancymenu`, así que ambos exponen los mismos subespacios de nombres.

Las acciones exponen dos ayudas:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilidad

```javascript
if (typeof fancymenu !== 'undefined') {
    // es seguro usarlo
}

window.addEventListener('fancymenu-ready', () => {
    console.log('La API de FancyMenu está lista');
});
```

El contenido también puede alojarse localmente: coloca archivos HTML en `<game-directory>/config/fancymenu/assets/` y cárgalos mediante URLs con el formato `file:///config/fancymenu/assets/<nombre>.html`.

## 3. Ejecución de acciones

Usa el espacio de nombres `fancymenu.actions`. Cada llamada refleja las cadenas de acción usadas en los scripts de FancyMenu.

### Llamadas rápidas

```javascript
fancymenu.actions.execute('quitgame');                // acción sin valor
fancymenu.actions.execute('opengui', 'title_screen'); // acción con valor
fancymenu.actions.execute('set_variable', 'hp:20');   // el valor usa el formato nombre:valor
```

### Con callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Se abrió la pantalla de título'),
    error  => console.error('Error al abrir:', error)
);

// El parámetro de valor es opcional. Si se omite, pasa los callbacks directamente después de actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Se activó la salida'),
    error  => console.error('Error al salir:', error)
);
```

Las funciones heredadas `fancymenu.execute(...)` y `fancymenu.executeWithCallback(...)` todavía delegan al espacio de nombres `actions`.

### Tipos de acción comunes

- `quitgame` – sale del juego de inmediato (sin valor)
- `back_to_last_screen` – regresa a la interfaz gráfica anterior (sin valor)
- `opengui` – abre una pantalla de FancyMenu o de vanilla (valor: identificador de pantalla)
- `openlink` – abre un navegador (valor: URL)
- `sendmessage` – envía una línea al chat (valor: texto del mensaje)
- `set_variable` – asigna una variable de FancyMenu (valor: `nombre:valor`
- `joinserver` – conecta a un servidor (valor: dirección)
- `disconnect_server_or_world` – desconecta y cambia a una pantalla destino (valor: identificador de pantalla)

Todas las acciones que existen en FancyMenu están disponibles a través del puente; consulta los [scripts de acción](./action-scripts) para ver el catálogo completo.

## 4. Lectura de placeholders

El sistema de [placeholders](/placeholders) de FancyMenu se expone mediante `fancymenu.placeholders` (y `FancyMenu.placeholders`). Ambos métodos de ayuda regresan `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Cómo proporcionar variables

- Las variables son cadenas con el formato `nombre:valor`. El puente divide solo en el **primer** dos puntos, así que el valor puede contener más dos puntos.
- Los nombres y valores se recortan; los nombres vacíos se rechazan.
- Proporciona tantas variables como requiera el placeholder. Omite las opcionales.

### Ejemplos

```javascript
// Sin variables
fancymenu.placeholders.get('playername')
    .then(name => console.log('Jugador:', name));

// Una variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Tiempo activo (s):', seconds));

// Varias variables
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Parte seleccionada:', part));
```

### Modelo de errores

Las promesas rechazadas contienen un error estructurado:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Ejemplo de manejo:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Ejemplo completo

```html
<!DOCTYPE html>
<html>
<head>
    <title>Integración de FancyMenu</title>
</head>
<body>
    <h1>Controles del juego</h1>
    
    <button onclick="quitGame()">Salir del juego</button>
    <button onclick="openTitleScreen()">Pantalla de título</button>
    <button onclick="disconnectFromServer()">Desconectar</button>
    <button onclick="setVariable()">Establecer variable</button>
    <button onclick="loadPlaceholders()">Cargar placeholders</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('La API de FancyMenu aún no está disponible.');
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
                () => console.log('¡Se abrió la pantalla de título!'),
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
            var varName = prompt('Nombre de la variable:');
            var varValue = prompt('Valor de la variable:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('La API de placeholders de FancyMenu aún no está disponible.');
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
                    'Jugador: ' + playerName + '\n' +
                    'Tiempo activo (segundos): ' + uptimeSeconds + '\n' +
                    'Segunda fruta: ' + secondFruit;
            }).catch(error => {
                console.error('Falló la solicitud del placeholder:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Buenas prácticas y notas

- **Detecta el puente** antes de usarlo, o escucha el evento `fancymenu-ready`.
- **Maneja errores** (callbacks para [acciones](/action-scripts), `.catch` para [placeholders](/placeholders)) para mostrar información útil.
- **Valida la entrada** antes de pasarla a acciones o variables de [placeholders](/placeholders).
- **Limita la frecuencia de solicitudes**; evita saturar el puente con llamadas muy rápidas (especialmente en bucles de actualización de placeholders).
- **Seguridad:** El contenido del navegador puede invocar cualquier acción de FancyMenu registrada, incluidas acciones de archivos, red, comandos, portapapeles, paquetes de recursos, enlaces y salida. Carga solo páginas de confianza y valida todos los datos recibidos desde contenido web.

## 7. Solución de problemas

1. Confirma que la página se cargue en un navegador Rinku controlado por FancyMenu.
2. Revisa la consola del navegador en busca de errores de JavaScript.
3. Verifica que el identificador del [placeholder](/placeholders) o el tipo de [acción](/action-scripts) sea correcto y que se proporcionen los valores requeridos.
4. Revisa el registro de Minecraft (`latest.log`) para ver mensajes de error de FancyMenu si la ejecución falla de forma inesperada.
