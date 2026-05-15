---
title: API JavaScript del navegador
description: >-
  Cómo usar la API JavaScript de FancyMenu en funciones del mod basadas en MCEF,
  como el elemento Browser.
---

# API JavaScript de FancyMenu

FancyMenu inyecta un puente JavaScript en cada función basada en MCEF (por ejemplo, el elemento **Browser**). Este puente permite al contenido web:

- ejecutar directamente cualquier [acción](./action-scripts) de FancyMenu desde JavaScript,
- leer de forma asíncrona cualquier [placeholder](/placeholders) de FancyMenu.

Dos globales exponen la API:
- `window.fancymenu` – espacio de nombres principal
- `window.FancyMenu` – alias (refleja exactamente la misma estructura que `fancymenu`)

Usa el evento `fancymenu-ready`, o la detección de características, para asegurarte de que el puente está disponible antes de llamarlo.

## 1. Espacios de nombres y estructura

- `fancymenu.actions` – ejecuta acciones de FancyMenu desde el navegador.
- `fancymenu.placeholders` – lee valores de placeholders de FancyMenu de forma asíncrona.
- `FancyMenu` refleja `fancymenu`, así que ambos exponen los mismos subespacios de nombres.

Las acciones exponen dos ayudantes:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilidad

```javascript
if (typeof fancymenu !== 'undefined') {
    // se puede usar con seguridad
}

window.addEventListener('fancymenu-ready', () => {
    console.log('La API de FancyMenu está lista');
});
```

El contenido también puede alojarse localmente: coloca archivos HTML en `config/fancymenu/assets/` y cárgalos mediante URL con el formato `file:///config/fancymenu/assets/<name>.html`.

## 3. Ejecución de acciones

Usa el espacio de nombres `fancymenu.actions`. Cada llamada refleja las cadenas de acción usadas en los scripts de FancyMenu.

### Llamadas rápidas

```javascript
fancymenu.actions.execute('quitgame');                // acción sin valor
fancymenu.actions.execute('opengui', 'title_screen'); // acción con valor
fancymenu.actions.execute('set_variable', 'hp:20');   // el valor usa el formato name:value
```

### Con callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Pantalla de título abierta'),
    error  => console.error('Error al abrir:', error)
);

// El parámetro value es opcional. Si se omite, pasa los callbacks directamente después de actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Salida activada'),
    error  => console.error('Error al salir:', error)
);

Los ayudantes heredados `fancymenu.execute(...)` y `fancymenu.executeWithCallback(...)` siguen funcionando y delegan en el espacio de nombres `actions`, así que el contenido existente no necesita cambios inmediatos.
```

### Tipos de acción comunes

- `quitgame` – cierra el juego inmediatamente (sin valor)
- `back_to_last_screen` – vuelve a la interfaz anterior (sin valor)
- `opengui` – abre una pantalla de FancyMenu o vanilla (valor: identificador de pantalla)
- `openlink` – abre un navegador (valor: URL)
- `sendmessage` – publica una línea de chat (valor: texto del mensaje)
- `set_variable` – asigna una variable de FancyMenu (valor: `name:value`)
- `joinserver` – conecta a un servidor (valor: dirección)
- `disconnect_server_or_world` – desconecta y lleva a una pantalla objetivo (valor: identificador de pantalla)

Todas las acciones que existen en FancyMenu están disponibles a través del puente; consulta los [scripts de acción](./action-scripts) para ver el catálogo completo.

## 4. Lectura de placeholders

El sistema de [placeholders](/placeholders) de FancyMenu se expone mediante `fancymenu.placeholders` (y `FancyMenu.placeholders`). Ambos métodos auxiliares devuelven `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Proporcionar variables

- Las variables son cadenas con el formato `name:value`. El puente divide solo en el **primer** carácter dos puntos, así que el valor puede contener más dos puntos.
- Los nombres y los valores se recortan; se rechazan los nombres vacíos.
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

### Modelo de error

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
                console.warn('La API de FancyMenu todavía no está disponible.');
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
                () => console.log('¡Pantalla de título abierta!'),
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
                console.warn('La API de placeholders de FancyMenu todavía no está disponible.');
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
                console.error('La solicitud del placeholder ha fallado:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Buenas prácticas y notas

- **Detecta el puente** antes de usarlo, o escucha `fancymenu-ready`.
- **Gestiona los errores** (callbacks para [acciones](/action-scripts), `.catch` para [placeholders](/placeholders)) para mostrar información útil.
- **Valida la entrada** antes de pasársela a acciones o variables de [placeholders](/placeholders).
- **Limita la frecuencia de solicitudes**; evita saturar el puente con llamadas muy seguidas (especialmente bucles de actualización de placeholders).
- **Seguridad**: las acciones se ejecutan con los permisos normales del jugador. Trata con cuidado los datos proporcionados por el usuario para evitar inyecciones.

## 7. Solución de problemas

1. Confirma que la página se carga en un navegador MCEF controlado por FancyMenu.
2. Comprueba la consola del navegador en busca de errores de JavaScript.
3. Verifica que el identificador del [placeholder](/placeholders) o el tipo de [acción](/action-scripts) sea correcto y que se proporcionen los valores necesarios.
4. Revisa el registro de Minecraft (`latest.log`) en busca de mensajes de error de FancyMenu si la ejecución falla de forma inesperada.
