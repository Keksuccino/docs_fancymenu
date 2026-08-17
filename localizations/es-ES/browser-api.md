---
title: API de JavaScript del navegador
description: >-
  Cómo utilizar la API de JavaScript de FancyMenu en funciones basadas en Rinku,
  como el elemento Browser.
---
# API de JavaScript de FancyMenu

FancyMenu inyecta un puente de JavaScript en todas las funciones basadas en [Rinku](https://modrinth.com/mod/rinku) (por ejemplo, el elemento **Browser**). El puente permite al contenido web:

- ejecutar directamente cualquier [acción](./action-scripts) de FancyMenu desde JavaScript;
- leer de forma asíncrona cualquier [marcador de posición](/placeholders) de FancyMenu.

Dos variables globales exponen la API:
- `window.fancymenu`: espacio de nombres principal
- `window.FancyMenu`: alias (refleja exactamente la estructura de `fancymenu`)

Utiliza el evento `fancymenu-ready` o la detección de funciones para asegurarte de que el puente está disponible antes de llamarlo.

## 1. Espacios de nombres y estructura

- `fancymenu.actions`: ejecuta acciones de FancyMenu desde el navegador.
- `fancymenu.placeholders`: lee de forma asíncrona los valores de los marcadores de posición de FancyMenu.
- `FancyMenu` refleja `fancymenu`, por lo que ambos exponen los mismos subespacios de nombres.

Las acciones exponen dos métodos auxiliares:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilidad

```javascript
if (typeof fancymenu !== 'undefined') {
    // se puede utilizar de forma segura
}

window.addEventListener('fancymenu-ready', () => {
    console.log('La API de FancyMenu está lista');
});
```

El contenido también puede alojarse localmente: coloca los archivos HTML en `<game-directory>/config/fancymenu/assets/` y cárgalos mediante URL con el formato `file:///config/fancymenu/assets/<name>.html`.

## 3. Ejecución de acciones

Utiliza el espacio de nombres `fancymenu.actions`. Cada llamada refleja las cadenas de acción utilizadas en los scripts de FancyMenu.

### Llamadas rápidas

```javascript
fancymenu.actions.execute('quitgame');                // acción sin valor
fancymenu.actions.execute('opengui', 'title_screen'); // acción con valor
fancymenu.actions.execute('set_variable', 'hp:20');   // el valor utiliza el formato nombre:valor
```

### Con callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Pantalla principal abierta'),
    error  => console.error('No se ha podido abrir:', error)
);

// El parámetro value es opcional. Si se omite, pasa los callbacks directamente después de actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Salida iniciada'),
    error  => console.error('No se ha podido salir:', error)
);
```

Los métodos auxiliares heredados `fancymenu.execute(...)` y `fancymenu.executeWithCallback(...)` siguen delegando en el espacio de nombres `actions`.

### Tipos de acción habituales

- `quitgame`: cierra el juego inmediatamente (sin valor)
- `back_to_last_screen`: vuelve a la interfaz gráfica anterior (sin valor)
- `opengui`: abre una pantalla de FancyMenu o de Minecraft (valor: identificador de pantalla)
- `openlink`: abre un navegador (valor: URL)
- `sendmessage`: envía una línea de chat (valor: texto del mensaje)
- `set_variable`: asigna una variable de FancyMenu (valor: `name:value`)
- `joinserver`: se conecta a un servidor (valor: dirección)
- `disconnect_server_or_world`: se desconecta y pasa a una pantalla de destino (valor: identificador de pantalla)

Todas las acciones existentes en FancyMenu están disponibles a través del puente; consulta los [scripts de acciones](./action-scripts) para ver el catálogo completo.

## 4. Lectura de marcadores de posición

El sistema de [marcadores de posición](/placeholders) de FancyMenu está disponible mediante `fancymenu.placeholders` (y `FancyMenu.placeholders`). Ambos métodos auxiliares devuelven `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Suministro de variables

- Las variables son cadenas con el formato `name:value`. El puente divide la cadena únicamente por los **dos puntos** iniciales, por lo que el valor puede contener más dos puntos.
- Los nombres y valores se recortan; los nombres vacíos se rechazan.
- Proporciona tantas variables como requiera el marcador de posición. Omite las opcionales.

### Ejemplos

```javascript
// Sin variables
fancymenu.placeholders.get('playername')
    .then(name => console.log('Jugador:', name));

// Una variable
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Tiempo de actividad (s):', seconds));

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
    <title>Integración con FancyMenu</title>
</head>
<body>
    <h1>Controles del juego</h1>
    
    <button onclick="quitGame()">Salir del juego</button>
    <button onclick="openTitleScreen()">Pantalla principal</button>
    <button onclick="disconnectFromServer()">Desconectar</button>
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
                () => console.log('¡Pantalla principal abierta!'),
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
                    'Tiempo de actividad (segundos): ' + uptimeSeconds + '\n' +
                    'Segunda fruta: ' + secondFruit;
            }).catch(error => {
                console.error('La solicitud de marcadores de posición ha fallado:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Prácticas recomendadas y notas

- **Detecta el puente** antes de utilizarlo o escucha `fancymenu-ready`.
- **Gestiona los errores** (callbacks para las [acciones](/action-scripts) y `.catch` para los [marcadores de posición](/placeholders)) para mostrar información útil.
- **Valida los datos de entrada** antes de pasarlos a las acciones o a las variables de los [marcadores de posición](/placeholders).
- **Limita las solicitudes**; evita saturar el puente con llamadas rápidas y repetidas (especialmente en bucles de actualización de marcadores de posición).
- **Seguridad:** el contenido del navegador puede invocar cualquier acción de FancyMenu registrada, incluidas las acciones de archivos, red, comandos, portapapeles, paquetes de recursos, enlaces y salida. Carga únicamente páginas de confianza y valida todos los datos recibidos del contenido web.

## 7. Solución de problemas

1. Confirma que la página está cargada en un navegador Rinku controlado por FancyMenu.
2. Comprueba la consola del navegador en busca de errores de JavaScript.
3. Verifica que el identificador del [marcador de posición](/placeholders) o el tipo de [acción](/action-scripts) sean correctos y que se hayan proporcionado los valores necesarios.
4. Si la ejecución falla inesperadamente, revisa el registro de Minecraft (`latest.log`) para comprobar si hay mensajes de error de FancyMenu.
