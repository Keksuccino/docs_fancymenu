---
title: API de JavaScript del navegador
description: >-
  Cómo usar la API de JavaScript de FancyMenu en funciones basadas en Rinku,
  como el elemento **Navegador**.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# API de JavaScript de FancyMenu

FancyMenu inyecta un puente de JavaScript en todas las funciones que usan [Rinku](https://modrinth.com/mod/rinku) (por ejemplo, el elemento **Navegador**). Este puente permite que el contenido web:

- ejecute directamente desde JavaScript cualquier [acción](/action-scripts) de FancyMenu;
- lea de forma asíncrona cualquier [marcador de posición](/placeholders) de FancyMenu.

Hay dos objetos globales que exponen la API:
- `window.fancymenu`: espacio de nombres principal;
- `window.FancyMenu`: alias (reproduce exactamente la estructura de `fancymenu`).

Usa el evento `fancymenu-ready` o comprueba que la función esté disponible antes de llamar a la API.

## 1. Espacios de nombres y estructura

- `fancymenu.actions`: ejecuta acciones de FancyMenu desde el navegador.
- `fancymenu.placeholders`: lee de forma asíncrona los valores de los marcadores de posición de FancyMenu.
- `FancyMenu` reproduce `fancymenu`, por lo que ambos exponen los mismos subespacios de nombres.

Las acciones tienen dos métodos:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilidad

```javascript
if (typeof fancymenu !== 'undefined') {
    // ya se puede usar de forma segura
}

window.addEventListener('fancymenu-ready', () => {
    console.log('La API de FancyMenu está lista');
});
```

También puedes alojar el contenido en local: coloca los archivos HTML en `<game-directory>/config/fancymenu/assets/` y cárgalos mediante direcciones URL con este formato: `file:///config/fancymenu/assets/<name>.html`.

## 3. Ejecutar acciones

Usa el espacio de nombres `fancymenu.actions`. Cada llamada reproduce las cadenas de acción que se usan en los scripts de FancyMenu.

### Llamadas rápidas

```javascript
fancymenu.actions.execute('quitgame');                // acción sin valor
fancymenu.actions.execute('opengui', 'title_screen'); // acción con valor
fancymenu.actions.execute('set_variable', 'hp:20');   // el valor usa el formato nombre:valor
```

### Con funciones de devolución de llamada

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Se ha abierto la pantalla del título'),
    error  => console.error('Error al abrirla:', error)
);

// El parámetro de valor es opcional. Si lo omites, pasa las funciones de devolución de llamada directamente después de actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Se ha iniciado el cierre del juego'),
    error  => console.error('Error al cerrar el juego:', error)
);
```

Los métodos heredados `fancymenu.execute(...)` y `fancymenu.executeWithCallback(...)` siguen delegando en el espacio de nombres `actions`.

### Tipos de acción habituales

- `quitgame`: cierra el juego inmediatamente (sin valor).
- `back_to_last_screen`: vuelve a la interfaz anterior (sin valor).
- `opengui`: abre una pantalla de FancyMenu o de Minecraft (valor: identificador de la pantalla).
- `openlink`: abre un navegador (valor: URL).
- `sendmessage`: envía un mensaje al chat (valor: texto del mensaje).
- `set_variable`: asigna un valor a una variable de FancyMenu (valor: `nombre:valor`).
- `joinserver`: se conecta a un servidor (valor: dirección).
- `disconnect_server_or_world`: se desconecta y pasa a una pantalla de destino (valor: identificador de la pantalla).

El puente permite usar todas las acciones disponibles en FancyMenu. Consulta [scripts de acciones](/action-scripts) para ver el catálogo completo.

## 4. Leer marcadores de posición

El sistema de [marcadores de posición](/placeholders) de FancyMenu está disponible mediante `fancymenu.placeholders` (y `FancyMenu.placeholders`). Ambos métodos devuelven `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Proporcionar variables

- Las variables son cadenas con el formato `nombre:valor`. El puente solo divide por los dos puntos **primero**, así que el valor puede contener más dos puntos.
- Se eliminan los espacios al principio y al final de los nombres y valores; los nombres vacíos no son válidos.
- Proporciona todas las variables que necesite el marcador de posición. Omite las opcionales.

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

### Gestión de errores

Las promesas rechazadas contienen un error estructurado:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Ejemplo de gestión:

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
    <button onclick="openTitleScreen()">Pantalla del título</button>
    <button onclick="disconnectFromServer()">Desconectarse</button>
    <button onclick="setVariable()">Definir variable</button>
    <button onclick="loadPlaceholders()">Cargar marcadores de posición</button>

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
                () => console.log('¡Se ha abierto la pantalla del título!'),
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
                console.warn('La API de marcadores de posición de FancyMenu aún no está disponible.');
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
                console.error('Error al solicitar marcadores de posición:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Buenas prácticas y notas

- **Comprueba que el puente esté disponible** antes de usarlo o escucha el evento `fancymenu-ready`.
- **Gestiona los errores** (funciones de devolución de llamada para las [acciones](/action-scripts), `.catch` para los [marcadores de posición](/placeholders)) para ofrecer información útil.
- **Valida los datos de entrada** antes de pasarlos a las acciones o a las variables de los [marcadores de posición](/placeholders).
- **Limita la frecuencia de las solicitudes**; evita saturar el puente con llamadas muy seguidas (especialmente en bucles de actualización de marcadores de posición).
- **Seguridad:** el contenido del navegador puede invocar cualquier acción registrada de FancyMenu, incluidas las acciones de archivos, red, comandos, portapapeles, paquetes de recursos, enlaces y cierre del juego. Carga solo páginas de confianza y valida todos los datos que recibas del contenido web.

## 7. Solución de problemas

1. Comprueba que la página se haya cargado en un navegador Rinku controlado por FancyMenu.
2. Comprueba si hay errores de JavaScript en la consola del navegador.
3. Verifica que el identificador del [marcador de posición](/placeholders) o el tipo de [acción](/action-scripts) sean correctos y que se hayan proporcionado los valores necesarios.
4. Si la ejecución falla inesperadamente, revisa el registro de Minecraft (`latest.log`) para buscar mensajes de error de FancyMenu.
