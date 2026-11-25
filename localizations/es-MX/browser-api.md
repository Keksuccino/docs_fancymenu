---
title: API de JavaScript para el navegador
description: >-
  Cómo usar la API de JavaScript de FancyMenu en funciones basadas en Rinku,
  como el elemento Browser.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# API de JavaScript de FancyMenu

FancyMenu inyecta un puente de JavaScript en todas las funciones que usan [Rinku](https://modrinth.com/mod/rinku) (por ejemplo, el elemento **Browser**). El puente permite que el contenido web pueda:

- ejecutar directamente desde JavaScript cualquier [acción](/action-scripts) de FancyMenu;
- leer de forma asíncrona cualquier [marcador de posición](/placeholders) de FancyMenu.

La API está disponible mediante dos variables globales:
- `window.fancymenu`: espacio de nombres principal
- `window.FancyMenu`: alias (tiene exactamente la misma estructura que `fancymenu`)

Usa el evento `fancymenu-ready` o la detección de funciones para asegurarte de que el puente esté disponible antes de llamarlo.

## 1. Espacios de nombres y estructura

- `fancymenu.actions`: ejecuta acciones de FancyMenu desde el navegador.
- `fancymenu.placeholders`: lee de forma asíncrona los valores de los marcadores de posición de FancyMenu.
- `FancyMenu` es un reflejo de `fancymenu`, por lo que ambos exponen los mismos subespacios de nombres.

Las acciones tienen dos métodos auxiliares:
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

También puedes alojar el contenido localmente: coloca los archivos HTML en `<game-directory>/config/fancymenu/assets/` y cárgalos mediante URL con este formato: `file:///config/fancymenu/assets/<name>.html`.

## 3. Ejecutar acciones

Usa el espacio de nombres `fancymenu.actions`. Cada llamada corresponde a las cadenas de acción que se usan en los scripts de FancyMenu.

### Llamadas rápidas

```javascript
fancymenu.actions.execute('quitgame');                // acción sin valor
fancymenu.actions.execute('opengui', 'title_screen'); // acción con valor
fancymenu.actions.execute('set_variable', 'hp:20');   // el valor usa el formato nombre:valor
```

### Con funciones de callback

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Se abrió la pantalla de título'),
    error  => console.error('No se pudo abrir:', error)
);

// El parámetro de valor es opcional. Si lo omites, pasa las funciones de callback directamente después de actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Se inició el cierre del juego'),
    error  => console.error('No se pudo cerrar el juego:', error)
);
```

Los métodos heredados `fancymenu.execute(...)` y `fancymenu.executeWithCallback(...)` siguen delegando las llamadas al espacio de nombres `actions`.

### Tipos de acción comunes

- `quitgame`: cierra el juego de inmediato (sin valor)
- `back_to_last_screen`: vuelve a la interfaz anterior (sin valor)
- `opengui`: abre una pantalla de FancyMenu o de Minecraft (valor: identificador de la pantalla)
- `openlink`: abre un navegador (valor: URL)
- `sendmessage`: envía un mensaje al chat (valor: texto del mensaje)
- `set_variable`: asigna una variable de FancyMenu (valor: `name:value`)
- `joinserver`: se conecta a un servidor (valor: dirección)
- `disconnect_server_or_world`: se desconecta y cambia a una pantalla de destino (valor: identificador de la pantalla)

Todas las acciones disponibles en FancyMenu también están disponibles mediante el puente. Consulta [scripts de acción](/action-scripts) para ver el catálogo completo.

## 4. Leer marcadores de posición

El sistema de [marcadores de posición](/placeholders) de FancyMenu está disponible mediante `fancymenu.placeholders` (y `FancyMenu.placeholders`). Ambos métodos auxiliares devuelven `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Proporcionar variables

- Las variables son cadenas con el formato `nombre:valor`. El puente solo divide en el **primer** signo de dos puntos, así que el valor puede contener otros signos de dos puntos.
- Se eliminan los espacios al principio y al final de los nombres y valores; no se permiten nombres vacíos.
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
    <title>Integración con FancyMenu</title>
</head>
<body>
    <h1>Controles del juego</h1>
    
    <button onclick="quitGame()">Cerrar el juego</button>
    <button onclick="openTitleScreen()">Pantalla de título</button>
    <button onclick="disconnectFromServer()">Desconectarse</button>
    <button onclick="setVariable()">Establecer variable</button>
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
                console.error('Error en la solicitud del marcador de posición:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Recomendaciones y notas

- **Detecta el puente** antes de usarlo o escucha el evento `fancymenu-ready`.
- **Maneja los errores** (funciones de callback para las [acciones](/action-scripts), `.catch` para los [marcadores de posición](/placeholders)) y muestra información útil al usuario.
- **Valida los datos de entrada** antes de pasarlos a las acciones o a las variables de los [marcadores de posición](/placeholders).
- **Limita la frecuencia de las solicitudes**; evita saturar el puente con llamadas consecutivas (sobre todo en ciclos de actualización de marcadores de posición).
- **Seguridad:** el contenido del navegador puede invocar cualquier acción de FancyMenu registrada, incluidas las acciones de archivos, red, comandos, portapapeles, paquetes de recursos, enlaces y cierre del juego. Carga solo páginas de confianza y valida todos los datos que recibas del contenido web.

## 7. Solución de problemas

1. Confirma que la página esté cargada en un navegador Rinku controlado por FancyMenu.
2. Revisa si hay errores de JavaScript en la consola del navegador.
3. Verifica que el identificador del [marcador de posición](/placeholders) o el tipo de [acción](/action-scripts) sea correcto y que hayas proporcionado los valores requeridos.
4. Si la ejecución falla de forma inesperada, revisa el registro de Minecraft (`latest.log`) para buscar mensajes de error de FancyMenu.
