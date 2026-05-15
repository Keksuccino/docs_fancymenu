---
title: API de Shaders GLSL
description: >-
  Escribe shaders GLSL de FancyMenu para fondos, elementos y superposiciones
  decorativas.
---

# API de Shaders GLSL de FancyMenu

Este documento describe el entorno de ejecución GLSL utilizado por:

- el fondo de menú `GLSL`
- el elemento `GLSL`
- la superposición decorativa `GLSL`

Cubre los modos de compilación, el enrutado multipaso, las uniformes compatibles y patrones prácticos para crear shaders.

## 1. Visión general del entorno de ejecución

FancyMenu renderiza shaders con una canalización interna de OpenGL (`#version 150`) y admite:

- shaders de un solo pase (`Image` únicamente)
- shaders multipaso (`Buffer A` / `B` / `C` / `D` + `Image`)
- puntos de entrada al estilo Shadertoy (`mainImage`)
- puntos de entrada directos de fragmento (`main`)

Las fuentes de shader son campos de texto en línea:

- `Shader Source` (pase `Image`, necesario para renderizar)
- `Buffer A Source` (opcional)
- `Buffer B Source` (opcional)
- `Buffer C Source` (opcional)
- `Buffer D Source` (opcional)

Si la fuente de `Image` está vacía, el renderizado falla con un error de "no source".

## 2. Modos de compilación

FancyMenu admite tres modos de compilación:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Modo Shadertoy

Punto de entrada esperado:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu lo envuelve en `main()` y pasa las coordenadas del área local:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

El envoltorio multiplica la alfa de salida por `fmOpacity`.

### 2.2 Modo directo

Punto de entrada esperado:

```glsl
void main()
```

Comportamiento de compatibilidad:

- Se intenta una variante compatible con `gl_FragColor`.
- También se intenta una variante sin compatibilidad (para shaders modernos con `out vec4` explícito).

En el modo directo, `fmOpacity` no se aplica automáticamente a la salida. Aplícalo manualmente si hace falta.

### 2.3 Modo automático

Auto prueba variantes compatibles en secuencia (Shadertoy/directo) y usa la primera que compile.

## 3. Preprocesado de fuentes y macros integradas

Antes de compilar, FancyMenu normaliza la fuente:

- elimina el BOM UTF-8
- convierte CRLF/CR a LF
- elimina líneas `#version ...`
- elimina líneas `precision ...;`

El preámbulo inyectado en tiempo de ejecución incluye:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV a pantalla completa en `[0,1]`, origen en la esquina inferior izquierda)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Nota:

- Si tu fuente ya declara un nombre de uniforme conocido (por ejemplo, `iTime`), FancyMenu evita inyectar una declaración duplicada.
- Aun así, FancyMenu intenta subir valores a ese nombre en tiempo de ejecución.
- `textureCube` aquí solo es una macro alias; `iChannel0..3` son uniformes `sampler2D`.

## 4. Sistema de pases (`Image` + `Buffer A-D`)

FancyMenu tiene 5 ranuras de pase:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (pase final en pantalla)

Comportamiento:

- Los pases de buffer solo se ejecutan si su fuente no está vacía.
- El pase `Image` debe estar presente para renderizar salida.
- Los buffers se renderizan a texturas en coma flotante (`GL_RGBA16F`) y luego usan ping-pong (intercambio lectura/escritura en cada frame).

### 4.1 Enrutado de canales por pase

Cada pase expone enrutado para `iChannel0..3`. Por canal puedes seleccionar:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Los canales de recurso provienen de los ajustes `iChannel# Resource`.

Valores predeterminados:

- todos los enrutados de `iChannel` empiezan en `None`
- ningún pase de buffer está activo hasta que la fuente de ese buffer no esté vacía

Importante:

- Enrutar al mismo pase de buffer (feedback) lee datos del frame anterior (textura de lectura ping-pong).
- Si la fuente enrutada falta o está inactiva, se enlaza una textura de respaldo y `iChannelResolution[n].z` pasa a ser `0.0`.

## 5. Coordenadas y semántica del área

Los shaders se ejecutan en un rectángulo de área:

- Fondo del menú: área de pantalla completa
- Elemento GLSL: rectángulo del elemento

Convenciones de coordenadas:

- Las uniformes de píxel están en píxeles locales del área.
- El origen Y está en la esquina inferior izquierda para las coordenadas de píxel que ve el shader.
- Las coordenadas del ratón no se recortan; los valores pueden quedar fuera del área si el cursor está fuera.

Campos especiales:

- `fmAreaOffset`: posición de la esquina inferior izquierda del área en espacio de píxeles de pantalla
- `fmAreaTopLeft`: posición de la esquina superior izquierda del área en espacio de píxeles de pantalla
- `fmAreaSize`: tamaño del área en píxeles

## 6. Referencia de la API de uniformes

Todas las uniformes siguientes están disponibles tanto para shaders de fondo como para shaders de elementos.

## 6.1 Uniformes compatibles con Shadertoy

| Uniforme | Tipo | Significado |
|---|---|---|
| `iResolution` | `vec3` | `(anchuraDelÁreaPx, alturaDelÁreaPx, 1.0)` |
| `iTime` | `float` | Tiempo acumulado del shader en segundos |
| `iTimeDelta` | `float` | Delta de tiempo del último render, afectado por congelación/escala de tiempo |
| `iFrameRate` | `float` | FPS de reserva del runtime respecto a Minecraft |
| `iFrame` | `int` | Contador de frames de este runtime |
| `iMouse` | `vec4` | Ver detalles más abajo |
| `iDate` | `vec4` | `(año, mes, día, segundosDelDíaConFracción)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Actualmente todas están ajustadas a `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(ancho, alto, marcaDeValidez)` por canal |
| `iChannel0..3` | `sampler2D` | Entradas de textura enrutadas |

### Detalles de `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: posición actual del ratón en píxeles locales del área, o comportamiento de mantenimiento/congelación si el interruptor está activado
- `z`, `w`: origen del clic izquierdo
  - positivo mientras el botón izquierdo está pulsado
  - negativo tras soltarlo

Comportamiento controlado por interruptor:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` se actualiza de forma continua
- `... = On`:
  - `iMouse.xy` solo se actualiza mientras el botón izquierdo está pulsado y luego permanece en la última posición mantenida

Valor predeterminado:

- `Off` (actualizaciones continuas)

## 6.2 Uniformes específicos de FancyMenu

| Uniforme | Tipo | Significado |
|---|---|---|
| `fmAreaOffset` | `vec2` | Desplazamiento en píxeles de la esquina inferior izquierda del área en espacio de pantalla |
| `fmAreaSize` | `vec2` | Tamaño del área en píxeles |
| `fmAreaPosition` | `vec2` | Igual que `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Desplazamiento en píxeles de la esquina superior izquierda del área en espacio de pantalla |
| `fmScreenSize` | `vec2` | Tamaño total de la pantalla en píxeles |
| `fmGuiScale` | `float` | Escala actual de la interfaz |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Delta del ratón en píxeles del área (Y está invertido hacia arriba para el shader) |
| `fmMouseButtons` | `ivec4` | Estados de pulsación de los botones `0..3` |
| `fmMouseClickCount` | `ivec4` | Conteos acumulados de pulsaciones para los botones `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Conteos acumulados de liberaciones para los botones `0..3` |
| `fmMouseScroll` | `vec2` | Delta de desplazamiento desde el render anterior de este runtime |
| `fmMouseScrollTotal` | `vec2` | Totales acumulados de desplazamiento |
| `fmKeyEvent` | `ivec4` | `(últimoKeyCode, últimoScanCode, últimosModificadores, últimaAcción)` |
| `fmKeyEventCount` | `int` | Contador acumulado de eventos de teclado |
| `fmCharEvent` | `ivec4` | `(últimoCodePoint, últimosModificadores, 0, 0)` |
| `fmCharEventCount` | `int` | Contador acumulado de eventos de caracteres escritos |
| `fmDateParts` | `ivec4` | `(año, mes, día, díaDeLaSemanaIso1A7)` |
| `fmTimeParts` | `ivec4` | `(hora, minuto, segundo, parteMilisegundos0A999)` |
| `fmDayOfYear` | `int` | Día del año |
| `fmWeekOfYear` | `int` | Semana ISO del año |
| `fmUnixTimeSeconds` | `int` | Segundos desde la época Unix |
| `fmUnixTimeMilliseconds` | `int` | Parte de milisegundos de la hora actual (`0..999`) |
| `fmPartialTick` | `float` | Tick parcial actual |
| `fmGameDeltaTicks` | `float` | Delta ticks del juego de Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Delta ticks en tiempo real de Minecraft |
| `fmInWorld` | `int` | `1` cuando se está en un mundo, si no `0` |
| `fmIsPaused` | `int` | `1` cuando está en pausa, si no `0` |
| `fmOpacity` | `float` | Multiplicador efectivo de opacidad (`0..1`) |
| `fmVariableCount` | `int` | Cantidad actual de variables de FancyMenu |

Valores de acción de tecla (`fmKeyEvent.w`):

- `0` = soltar
- `1` = pulsar
- `2` = repetición

## 6.3 API de uniformes de variables de FancyMenu

Las variables de FancyMenu se exponen directamente como uniformes en tiempo de ejecución (para shaders de fondo, elementos y superposiciones decorativas) sin recompilar el shader cuando cambian los valores.

### Nomenclatura

Para cada variable `<name>`, FancyMenu expone:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = la variable existe actualmente, `0` = ausente/eliminada)

Sanitización del sufijo del uniforme para `<name>`:

- los caracteres permitidos son `[A-Za-z0-9_]`
- todos los demás caracteres se convierten en `_`
- si el primer carácter es un dígito, se antepone `_`

Ejemplos:

- variable `player_hp` -> sufijo `player_hp`
- variable `player-hp` -> sufijo `player_hp`
- variable `2nd_phase` -> sufijo `_2nd_phase`

Importante:

- estos uniformes dinámicos de variables **no se declaran automáticamente** en la fuente del shader (declara manualmente los que vayas a usar)
- evita nombres de variables que se saniticen al mismo sufijo, porque se asignan al mismo nombre de uniforme GLSL

### Conversión de valores

Dado el valor de texto de la variable `v`:

- `fmVarFloat_*`: float analizado (`0.0` como respaldo)
- `fmVarInt_*`: int analizado (`0` como respaldo)
- `fmVarBool_*`: interpretación booleana/int (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, en otro caso numérico distinto de cero => `1`)
- el análisis de vectores acepta separadores: espacios en blanco, `,`, `;`, `|`
  - `fmVarVec2_*`: primeras 2 componentes analizadas
  - `fmVarVec3_*`: primeras 3 componentes analizadas
  - `fmVarVec4_*`: primeras 4 componentes analizadas
  - si hay menos componentes, la última componente analizada se repite para los huecos faltantes
  - si no hay componentes numéricas, todas las componentes del vector usan el valor de respaldo escalar

Si una variable se elimina:

- `fmVarExists_*` pasa a `0`
- todos los valores correspondientes `fmVar*_*` se restablecen a `0`

### Ejemplo de declaración y uso

```glsl
uniform float fmVarFloat_player_hp;
uniform int fmVarBool_is_boss_phase;
uniform vec3 fmVarVec3_theme_color;
uniform int fmVarExists_player_hp;

void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;

    float hp = clamp(fmVarFloat_player_hp / 100.0, 0.0, 1.0);
    vec3 theme = fmVarVec3_theme_color;
    float boss = float(fmVarBool_is_boss_phase);

    vec3 col = mix(theme * 0.25, theme, hp);
    col += vec3(0.2, 0.0, 0.0) * boss;

    if (fmVarExists_player_hp == 0) {
        col = vec3(0.15);
    }

    fragColor = vec4(col, 1.0);
}
```

## 7. Modelo de seguimiento de entradas

FancyMenu sigue las entradas globalmente y toma una instantánea por render:

- movimiento/arrastre del ratón
- pulsación/soltado del ratón
- desplazamiento
- pulsación/soltado/repetición de teclas
- caracteres escritos

Robustez del ratón:

- El runtime reconcilia los estados de los botones con el sondeo de GLFW en cada frame para evitar estados de botón atascado.

Si `Pass Input Events To Shader` está desactivado:

- las uniformes de entrada se restablecen a valores neutros en cada frame
- los contadores y eventos se ponen a cero en los datos visibles para el shader

## 8. Detalles de entrada de texturas

Los canales de recurso (`iChannel# Resource`) esperan texturas 2D.

Estado de la textura por canal:

- recurso válido: textura enlazada, ancho/alto reales, `iChannelResolution[n].z = 1.0`
- ausente/inactivo/None: textura de respaldo, `iChannelResolution[n].xyz = (0,0,0)`

Texturas de buffer:

- formato interno: `RGBA16F` (coma flotante)
- filtrado: lineal
- wrap: clamp-to-edge

Esto es adecuado para datos multipaso (incluidos valores fuera de `[0,1]`).

## 9. Notas sobre renderizado y mezcla

- Los pases de buffer se renderizan fuera de pantalla sin mezcla.
- El pase final `Image` usa el ajuste `Enable Blending` para la composición.
- El envoltorio de Shadertoy aplica `fmOpacity` a la alfa automáticamente.
- Los shaders directos deben aplicar `fmOpacity` manualmente si es necesario.

## 10. Plantillas prácticas

## 10.1 Shader mínimo al estilo Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Shader de fragmento directo mínimo

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Multipaso de feedback mínimo

### Fuente de Buffer A

Ruta: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Fuente de Image

Ruta: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Lista de comprobación para solución de problemas

- Sin salida:
  - comprueba que la fuente de `Image` no esté vacía
  - comprueba que el modo de compilación coincida con tu punto de entrada (`mainImage` frente a `main`)
- Texturas moradas o no válidas:
  - verifica los enlaces de recursos y el enrutado de canales
  - comprueba `iChannelResolution[n].z` (`0.0` significa inválido/no disponible)
- Coordenadas incorrectas en un shader directo:
  - usa `gl_FragCoord.xy - fmAreaOffset` para coordenadas locales del área
- El comportamiento del arrastre es incorrecto:
  - usa el interruptor `Update iMouse Position Only While Holding LMB`
- La opacidad no se aplica en un shader directo:
  - multiplica la alfa por `fmOpacity` tú mismo
