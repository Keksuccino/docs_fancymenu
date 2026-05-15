---
title: API de Shader GLSL
description: >-
  Escribe shaders GLSL de FancyMenu para fondos, elementos y superposiciones de
  decoración.
---

# API de Shader GLSL de FancyMenu

Este documento describe el tiempo de ejecución GLSL que usa FancyMenu para:

- fondo de menú `GLSL`
- elemento `GLSL`
- superposición de decoración `GLSL`

Cubre modos de compilación, enrutamiento multipaso, uniforms compatibles y patrones prácticos para escribir shaders.

## 1. Resumen del tiempo de ejecución

FancyMenu renderiza shaders con una canalización interna de OpenGL (`#version 150`) y admite:

- shaders de un solo paso (solo el pase `Image`)
- shaders multipaso (`Buffer A` / `B` / `C` / `D` + `Image`)
- puntos de entrada al estilo Shadertoy (`mainImage`)
- puntos de entrada directos de fragmento (`main`)

Las fuentes del shader son campos de texto en línea:

- `Shader Source` (pase `Image`, obligatorio para renderizar)
- `Buffer A Source` (opcional)
- `Buffer B Source` (opcional)
- `Buffer C Source` (opcional)
- `Buffer D Source` (opcional)

Si la fuente de Image está vacía, el render falla con un error de "no source".

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

FancyMenu lo envuelve en `main()` y pasa coordenadas del área local:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

El envoltorio multiplica la opacidad de salida por `fmOpacity`.

### 2.2 Modo directo

Punto de entrada esperado:

```glsl
void main()
```

Comportamiento de compatibilidad:

- Se intenta una variante compatible con `gl_FragColor`.
- También se intenta una variante sin compatibilidad (para shaders modernos con `out vec4` explícito).

En modo directo, `fmOpacity` no se aplica automáticamente a la salida. Aplícalo manualmente si lo necesitas.

### 2.3 Modo automático

Auto prueba variantes compatibles en secuencia (Shadertoy/directo) y usa la primera que compile.

## 3. Preprocesamiento de la fuente y macros integradas

Antes de compilar, FancyMenu normaliza la fuente:

- elimina BOM UTF-8
- convierte CRLF/CR a LF
- elimina líneas `#version ...`
- elimina líneas `precision ...;`

El prefijo inyectado en tiempo de ejecución incluye:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV de pantalla completa en `[0,1]`, origen en la esquina inferior izquierda)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Nota:

- Si tu fuente ya declara un nombre de uniform conocido (por ejemplo, `iTime`), FancyMenu evita inyectar una declaración duplicada.
- Aun así, FancyMenu intenta subir valores a ese nombre en tiempo de ejecución.
- `textureCube` aquí solo es un alias macro; `iChannel0..3` son uniforms `sampler2D`.

## 4. Sistema de pases (Image + Buffer A-D)

FancyMenu tiene 5 ranuras de pase:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (pase final en pantalla)

Comportamiento:

- Los pases de Buffer solo se ejecutan si su fuente no está vacía.
- El pase Image debe estar presente para renderizar salida.
- Los buffers se renderizan a texturas de punto flotante (`GL_RGBA16F`) y luego usan ping-pong (intercambio de lectura/escritura en cada fotograma).

### 4.1 Enrutamiento de canales por pase

Cada pase expone enrutamiento para `iChannel0..3`. Por canal puedes seleccionar:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Los canales de recurso provienen de la configuración `iChannel# Resource`.

Valores predeterminados:

- todos los enrutamientos de `iChannel` inician en `None`
- ningún pase de buffer está activo hasta que su fuente no esté vacía

Importante:

- El enrutamiento al mismo pase de buffer (feedback) lee datos del fotograma anterior (textura de lectura ping-pong).
- Si una fuente enrutada falta o está inactiva, se enlaza una textura de respaldo y `iChannelResolution[n].z` pasa a `0.0`.

## 5. Coordenadas y semántica del área

Los shaders se ejecutan en un rectángulo de área:

- Fondo del menú: área de pantalla completa
- Elemento GLSL: rectángulo del elemento

Convenciones de coordenadas:

- Los uniforms de píxel están en píxeles locales del área.
- El origen Y está abajo a la izquierda para las coordenadas de píxel visibles para el shader.
- Las coordenadas del mouse no se limitan; los valores pueden estar fuera del área si el cursor está afuera.

Campos especiales:

- `fmAreaOffset`: posición inferior izquierda del área en espacio de píxeles de pantalla
- `fmAreaTopLeft`: posición superior izquierda del área en espacio de píxeles de pantalla
- `fmAreaSize`: tamaño del área en píxeles

## 6. Referencia de la API de uniforms

Todos los uniforms siguientes están disponibles tanto para shaders de fondo como para shaders de elemento.

## 6.1 Uniforms compatibles con Shadertoy

| Uniform | Tipo | Significado |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Tiempo acumulado del shader en segundos |
| `iTimeDelta` | `float` | Delta de tiempo del último render, afectado por congelación/escala de tiempo |
| `iFrameRate` | `float` | FPS de respaldo del runtime para Minecraft |
| `iFrame` | `int` | Contador de fotogramas de este runtime |
| `iMouse` | `vec4` | Ver detalles abajo |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Actualmente todos se establecen en `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(width, height, validFlag)` por canal |
| `iChannel0..3` | `sampler2D` | Entradas de textura enrutadas |

### Detalles de `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: posición actual del mouse en píxeles locales del área, o comportamiento de retención/congelado si el ajuste está activado
- `z`, `w`: origen del clic izquierdo
  - positivo mientras el botón izquierdo está presionado
  - negativo después de soltarlo

Comportamiento controlado por ajuste:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` se actualiza continuamente
- `... = On`:
  - `iMouse.xy` se actualiza solo mientras LMB está presionado y luego permanece en la última posición mantenida

Valor predeterminado:

- `Off` (actualizaciones continuas)

## 6.2 Uniforms específicos de FancyMenu

| Uniform | Tipo | Significado |
|---|---|---|
| `fmAreaOffset` | `vec2` | Desplazamiento en píxeles de la esquina inferior izquierda del área en espacio de pantalla |
| `fmAreaSize` | `vec2` | Tamaño del área en píxeles |
| `fmAreaPosition` | `vec2` | Igual que `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Desplazamiento en píxeles de la esquina superior izquierda del área en espacio de pantalla |
| `fmScreenSize` | `vec2` | Tamaño total de la pantalla en píxeles |
| `fmGuiScale` | `float` | Escala actual de la GUI |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Delta del mouse en píxeles del área (Y está invertido para que apunte hacia arriba en el shader) |
| `fmMouseButtons` | `ivec4` | Estados presionados de los botones `0..3` |
| `fmMouseClickCount` | `ivec4` | Conteos acumulados de presión para los botones `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Conteos acumulados de liberación para los botones `0..3` |
| `fmMouseScroll` | `vec2` | Delta de desplazamiento desde el render anterior de este runtime |
| `fmMouseScrollTotal` | `vec2` | Totales acumulados de desplazamiento |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | Contador acumulado de eventos de teclado |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | Contador acumulado de eventos de caracteres escritos |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | Día del año |
| `fmWeekOfYear` | `int` | Semana ISO del año |
| `fmUnixTimeSeconds` | `int` | Segundos Unix desde la época |
| `fmUnixTimeMilliseconds` | `int` | Parte en milisegundos de la hora actual (`0..999`) |
| `fmPartialTick` | `float` | Partial tick actual |
| `fmGameDeltaTicks` | `float` | Delta ticks del juego de Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Delta ticks en tiempo real de Minecraft |
| `fmInWorld` | `int` | `1` cuando está en un mundo, de lo contrario `0` |
| `fmIsPaused` | `int` | `1` cuando está en pausa, de lo contrario `0` |
| `fmOpacity` | `float` | Multiplicador efectivo de opacidad (`0..1`) |
| `fmVariableCount` | `int` | Cantidad actual de variables de FancyMenu |

Valores de acción de teclado (`fmKeyEvent.w`):

- `0` = soltar
- `1` = presionar
- `2` = repetir

## 6.3 API de uniforms para variables de FancyMenu

Las variables de FancyMenu se exponen directamente como uniforms de tiempo de ejecución (para shaders de fondo, elemento y superposición de decoración) sin recompilar el shader cuando cambian los valores.

### Nomenclatura

Para cada variable `<name>`, FancyMenu expone:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = la variable existe actualmente, `0` = no está presente/eliminada)

Sanitización del sufijo del uniform para `<name>`:

- los caracteres permitidos son `[A-Za-z0-9_]`
- todos los demás caracteres se convierten en `_`
- si el primer carácter es un dígito, se antepone `_`

Ejemplos:

- variable `player_hp` -> sufijo `player_hp`
- variable `player-hp` -> sufijo `player_hp`
- variable `2nd_phase` -> sufijo `_2nd_phase`

Importante:

- estos uniforms dinámicos de variables **no se declaran automáticamente** en la fuente del shader (declara manualmente los que uses)
- evita nombres de variables que se saniticen al mismo sufijo, porque se asignan al mismo nombre de uniform GLSL

### Conversión de valores

Dado el valor de texto de una variable `v`:

- `fmVarFloat_*`: float analizado (`0.0` como respaldo)
- `fmVarInt_*`: int analizado (`0` como respaldo)
- `fmVarBool_*`: interpretación booleana/entera (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, de lo contrario un valor numérico distinto de cero => `1`)
- el análisis de vectores acepta separadores: espacios, `,`, `;`, `|`
  - `fmVarVec2_*`: primeras 2 componentes analizadas
  - `fmVarVec3_*`: primeras 3 componentes analizadas
  - `fmVarVec4_*`: primeras 4 componentes analizadas
  - si hay menos componentes, la última componente analizada se repite en los espacios faltantes
  - si no hay componentes numéricos, todas las componentes del vector usan el respaldo escalar

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

## 7. Modelo de rastreo de entrada

FancyMenu rastrea la entrada globalmente y toma una instantánea por render:

- movimiento/arrastre del mouse
- presionar/soltar mouse
- desplazamiento
- presionar/soltar/repetir teclado
- caracteres escritos

Robustez del mouse:

- El runtime reconcilia los estados de los botones con el sondeo de GLFW en cada fotograma para evitar estados de botón atascados.

Si `Pass Input Events To Shader` está desactivado:

- los uniforms de entrada se restablecen a valores neutros en cada fotograma
- los contadores y eventos se ponen en cero en los datos visibles por el shader

## 8. Detalles de entrada de texturas

Los canales de recurso (`iChannel# Resource`) esperan texturas 2D.

Estado de textura por canal:

- recurso válido: textura enlazada, ancho/alto reales, `iChannelResolution[n].z = 1.0`
- faltante/inactivo/None: textura de respaldo, `iChannelResolution[n].xyz = (0,0,0)`

Texturas de buffer:

- formato interno: `RGBA16F` (punto flotante)
- filtrado: lineal
- wrap: clamp-to-edge

Esto es adecuado para datos multipaso (incluyendo valores fuera de `[0,1]`).

## 9. Notas de renderizado y mezcla

- Los pases de Buffer se renderizan fuera de pantalla sin mezcla.
- El pase final Image usa el ajuste `Enable Blending` para composición.
- El envoltorio de Shadertoy aplica `fmOpacity` automáticamente a la alpha.
- Los shaders directos deben aplicar `fmOpacity` manualmente si hace falta.

## 10. Plantillas prácticas

## 10.1 Shader mínimo estilo Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Shader mínimo de fragmento directo

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Multipaso de retroalimentación mínimo

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

## 11. Lista de verificación para solución de problemas

- Sin salida:
  - verifica que la fuente de Image no esté vacía
  - verifica que el modo de compilación coincida con tu punto de entrada (`mainImage` vs `main`)
- Texturas moradas/inválidas:
  - verifica los enlaces de recursos y el enrutamiento de canales
  - revisa `iChannelResolution[n].z` (`0.0` significa inválido/no disponible)
- Coordenadas incorrectas en shader directo:
  - usa `gl_FragCoord.xy - fmAreaOffset` para coordenadas locales del área
- El comportamiento de arrastre es incorrecto:
  - usa el ajuste `Update iMouse Position Only While Holding LMB`
- La opacidad no se aplica en shader directo:
  - multiplica la alpha por `fmOpacity` tú mismo
