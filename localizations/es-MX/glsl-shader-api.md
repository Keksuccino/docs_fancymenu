---
title: API de shaders GLSL
description: >-
  Escribe shaders GLSL de FancyMenu para fondos, elementos y capas de
  decoración.
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# API de shaders GLSL de FancyMenu

Este documento describe el entorno de ejecución de GLSL que FancyMenu usa para:

- fondos de menú `GLSL`
- elementos `GLSL`
- capas de decoración `GLSL`

Abarca los modos de compilación, el enrutamiento multipaso, los uniforms compatibles y patrones prácticos para escribir shaders.

## 1. Descripción general del entorno de ejecución

FancyMenu renderiza shaders con un pipeline interno de OpenGL (`#version 150`) y admite:

- shaders de un solo paso (solo el paso `Image`)
- shaders multipaso (`Buffer A` / `B` / `C` / `D` + `Image`)
- puntos de entrada al estilo Shadertoy (`mainImage`)
- puntos de entrada directos para fragmentos (`main`)

El código fuente de los shaders se escribe en campos de texto en línea:

- `Shader Source` (paso Image; obligatorio para renderizar)
- `Buffer A Source` (opcional)
- `Buffer B Source` (opcional)
- `Buffer C Source` (opcional)
- `Buffer D Source` (opcional)

Si el código fuente de Image está vacío, el renderizado falla con el error "no source".

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

FancyMenu lo envuelve en `main()` y le pasa las coordenadas locales del área:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

El wrapper multiplica automáticamente el alfa de salida por `fmOpacity`.

### 2.2 Modo directo

Punto de entrada esperado:

```glsl
void main()
```

Comportamiento de compatibilidad:

- Se intenta una variante compatible con `gl_FragColor`.
- También se intenta una variante sin compatibilidad (para shaders modernos que declaran explícitamente `out vec4`).

En el modo directo, `fmOpacity` no se aplica automáticamente a la salida. Aplícalo manualmente si es necesario.

### 2.3 Modo Auto

Auto prueba variantes compatibles en secuencia (Shadertoy/directo) y usa la primera que compile.

## 3. Preprocesamiento del código fuente y macros integradas

Antes de compilar, FancyMenu normaliza el código fuente:

- elimina la marca BOM de UTF-8
- convierte CRLF/CR a LF
- elimina las líneas `#version ...`
- elimina las líneas `precision ...;`

El preámbulo que se inserta durante la ejecución incluye:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV de pantalla completa en `[0,1]`, con el origen en la esquina inferior izquierda)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Nota:

- Si tu código fuente ya declara un nombre de uniform conocido (por ejemplo, `iTime`), FancyMenu evita insertar una declaración duplicada.
- Aun así, FancyMenu intenta enviar valores a ese nombre durante la ejecución.
- Aquí `textureCube` solo es una macro de alias; `iChannel0..3` son uniforms `sampler2D`.

## 4. Sistema de pasos (Image + Buffer A-D)

FancyMenu tiene 5 espacios para pasos:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (paso final que se muestra en pantalla)

Comportamiento:

- Los pasos Buffer solo se ejecutan si su código fuente no está vacío.
- El paso Image debe estar presente para renderizar la salida.
- Los buffers se renderizan en texturas de punto flotante (`GL_RGBA16F`) y luego se intercambian mediante ping-pong (se intercambian las texturas de lectura y escritura en cada cuadro).

### 4.1 Enrutamiento de canales por paso

Cada paso permite configurar el enrutamiento de `iChannel0..3`. Para cada canal, puedes elegir:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Los canales Resource se obtienen de la configuración `iChannel# Resource`.

Valores predeterminados:

- todos los enrutamientos de `iChannel` están configurados en `None`
- ningún paso Buffer está activo hasta que su código fuente deje de estar vacío

Importante:

- Al enrutar un buffer a sí mismo (retroalimentación), se leen los datos del cuadro anterior (la textura de lectura del intercambio ping-pong).
- Si una fuente enrutada no existe o está inactiva, se asigna una textura alternativa y `iChannelResolution[n].z` pasa a ser `0.0`.

## 5. Coordenadas y semántica del área

Los shaders se ejecutan dentro de un rectángulo de área:

- Fondo del menú: área de pantalla completa
- Elemento GLSL: rectángulo del elemento

Convenciones de coordenadas:

- Los uniforms de píxeles usan coordenadas locales del área.
- El origen de las coordenadas de píxeles que reciben los shaders está en la esquina inferior izquierda.
- Las coordenadas del mouse no se limitan; pueden quedar fuera del área si el cursor está afuera.

Campos especiales:

- `fmAreaOffset`: posición de la esquina inferior izquierda del área en el espacio de píxeles de la pantalla
- `fmAreaTopLeft`: posición de la esquina superior izquierda del área en el espacio de píxeles de la pantalla
- `fmAreaSize`: tamaño del área en píxeles

## 6. Referencia de la API de uniforms

Todos los uniforms que se indican a continuación están disponibles para los shaders de fondo y de elementos.

## 6.1 Uniforms compatibles con Shadertoy

| Uniform | Tipo | Significado |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Tiempo acumulado del shader en segundos |
| `iTimeDelta` | `float` | Delta de tiempo del último renderizado; puede verse afectado por la pausa y la escala de tiempo |
| `iFrameRate` | `float` | FPS del entorno de ejecución, con los FPS de Minecraft como respaldo |
| `iFrame` | `int` | Contador de cuadros por entorno de ejecución |
| `iMouse` | `vec4` | Consulta los detalles a continuación |
| `iDate` | `vec4` | `(año, mes, día, segundos del día con fracción)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Actualmente, todos se establecen en `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(ancho, alto, indicador de validez)` para cada canal |
| `iChannel0..3` | `sampler2D` | Entradas de textura enrutadas |

### Detalles de `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: posición actual del mouse en píxeles locales del área, o comportamiento de retención/congelamiento si la opción está activada
- `z`, `w`: origen del clic izquierdo
  - positivo mientras se mantiene presionado el botón izquierdo del mouse
  - negativo después de soltarlo

Comportamiento controlado por la opción:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` se actualiza continuamente
- `... = On`:
  - `iMouse.xy` se actualiza solo mientras se mantiene presionado el botón izquierdo del mouse; después conserva la última posición registrada mientras estaba presionado

Valor predeterminado:

- `Off` (actualizaciones continuas)

## 6.2 Uniforms específicos de FancyMenu

| Uniform | Tipo | Significado |
|---|---|---|
| `fmAreaOffset` | `vec2` | Desplazamiento de píxeles de la esquina inferior izquierda del área en el espacio de pantalla |
| `fmAreaSize` | `vec2` | Tamaño del área en píxeles |
| `fmAreaPosition` | `vec2` | Igual que `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Desplazamiento de píxeles de la esquina superior izquierda del área en el espacio de pantalla |
| `fmScreenSize` | `vec2` | Tamaño completo de la pantalla en píxeles |
| `fmGuiScale` | `float` | Escala actual de la interfaz |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Delta del mouse en píxeles del área (el eje Y se invierte para que apunte hacia arriba en el shader) |
| `fmMouseButtons` | `ivec4` | Estados de los botones `0..3` (presionado o no) |
| `fmMouseClickCount` | `ivec4` | Conteos acumulados de presiones para los botones `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Conteos acumulados de liberaciones para los botones `0..3` |
| `fmMouseScroll` | `vec2` | Delta del desplazamiento desde el renderizado anterior de este entorno de ejecución |
| `fmMouseScrollTotal` | `vec2` | Totales acumulados del desplazamiento |
| `fmKeyEvent` | `ivec4` | `(último código de tecla, último código de escaneo, últimos modificadores, última acción)` |
| `fmKeyEventCount` | `int` | Contador acumulado de eventos de teclado |
| `fmCharEvent` | `ivec4` | `(último punto de código, últimos modificadores, 0, 0)` |
| `fmCharEventCount` | `int` | Contador acumulado de eventos de escritura de caracteres |
| `fmDateParts` | `ivec4` | `(año, mes, día, día de la semana ISO del 1 al 7)` |
| `fmTimeParts` | `ivec4` | `(hora, minuto, segundo, milisegundos del 0 al 999)` |
| `fmDayOfYear` | `int` | Día del año |
| `fmWeekOfYear` | `int` | Semana ISO del año |
| `fmUnixTimeSeconds` | `int` | Segundos desde la época Unix |
| `fmUnixTimeMilliseconds` | `int` | Parte en milisegundos de la hora actual (`0..999`) |
| `fmPartialTick` | `float` | Tick parcial actual |
| `fmGameDeltaTicks` | `float` | Delta de ticks del juego en Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Delta de ticks en tiempo real de Minecraft |
| `fmInWorld` | `int` | `1` si estás en un mundo; de lo contrario, `0` |
| `fmIsPaused` | `int` | `1` si el juego está en pausa; de lo contrario, `0` |
| `fmOpacity` | `float` | Multiplicador de opacidad efectivo (`0..1`) |
| `fmVariableCount` | `int` | Cantidad actual de variables de FancyMenu |

Valores de acción de tecla (`fmKeyEvent.w`):

- `0` = liberación
- `1` = presión
- `2` = repetición

## 6.3 API de uniforms de variables de FancyMenu

Las variables de FancyMenu se exponen directamente como uniforms del entorno de ejecución (para shaders de fondo, elementos y capas de decoración), sin recompilar el shader cuando cambian sus valores.

### Nombres

Para cada variable `<name>`, FancyMenu expone:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = la variable existe actualmente, `0` = no está presente o se eliminó)

Normalización del sufijo del uniform para `<name>`:

- los caracteres permitidos son `[A-Za-z0-9_]`
- todos los demás caracteres se convierten en `_`
- si el primer carácter es un dígito, se antepone `_`

Ejemplos:

- variable `player_hp` -> sufijo `player_hp`
- variable `player-hp` -> sufijo `player_hp`
- variable `2nd_phase` -> sufijo `_2nd_phase`

Importante:

- estos uniforms dinámicos de variables **no se declaran automáticamente** en el código fuente del shader (declara manualmente los que uses)
- evita los nombres de variable que se normalicen al mismo sufijo, ya que se asignan al mismo nombre de uniform GLSL

### Conversión de valores

Dado el valor de texto `v` de una variable:

- `fmVarFloat_*`: número de punto flotante analizado (valor alternativo `0.0`)
- `fmVarInt_*`: entero analizado (valor alternativo `0`)
- `fmVarBool_*`: interpretación booleana/entera (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`; de lo contrario, cualquier valor numérico distinto de cero => `1`)
- el análisis de vectores acepta estos separadores: espacios en blanco, `,`, `;`, `|`
  - `fmVarVec2_*`: los primeros 2 componentes analizados
  - `fmVarVec3_*`: los primeros 3 componentes analizados
  - `fmVarVec4_*`: los primeros 4 componentes analizados
  - si hay menos componentes de los necesarios, se repite el último componente analizado en los espacios faltantes
  - si no hay componentes numéricos, todos los componentes del vector usan el valor escalar alternativo

Las [variables de lista](/variables#text-and-list-variables) proporcionan la cantidad de elementos en lugar de su texto:

- `fmVarFloat_*` y `fmVarInt_*`: cantidad de elementos; por ejemplo, `3` para una lista con 3 elementos
- `fmVarBool_*`: `1` si la lista contiene elementos, `0` si está vacía
- `fmVarVec2_*`, `fmVarVec3_*` y `fmVarVec4_*`: cantidad de elementos en cada componente

Si se elimina una variable:

- `fmVarExists_*` pasa a ser `0`
- todos los valores correspondientes a `fmVar*_*` se restablecen a `0`

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

FancyMenu hace un seguimiento global de las entradas y guarda una captura de su estado para cada renderizado:

- movimiento/arrastre del mouse
- presión/liberación del mouse
- desplazamiento
- presión/liberación/repetición de teclas
- escritura de caracteres

Robustez del mouse:

- En cada cuadro, el entorno de ejecución reconcilia los estados de los botones con la consulta de GLFW para evitar que queden botones en estado presionado.

Si la opción `Pass Input Events To Shader` está desactivada:

- los uniforms de entrada se restablecen a valores neutros en cada cuadro
- los contadores y eventos se ponen en cero en los datos visibles para el shader

## 8. Detalles de las entradas de textura

Los canales Resource (`iChannel# Resource`) esperan texturas 2D.

Estado de la textura por canal:

- recurso válido: se asigna la textura, se usan el ancho y alto reales, y `iChannelResolution[n].z = 1.0`
- si falta, está inactivo o es `None`: se asigna una textura alternativa y `iChannelResolution[n].xyz = (0,0,0)`

Texturas Buffer:

- formato interno: `RGBA16F` (punto flotante)
- filtrado: lineal
- ajuste de bordes: clamp-to-edge

Esto es adecuado para datos multipaso (incluidos valores fuera de `[0,1]`).

## 9. Notas sobre el renderizado y la mezcla

- Los pasos Buffer se renderizan fuera de pantalla, sin mezcla.
- El paso Image final usa la opción `Enable Blending` para componer la imagen.
- El wrapper de Shadertoy aplica automáticamente `fmOpacity` al alfa.
- Si es necesario, los shaders directos deben aplicar `fmOpacity` manualmente.

## 10. Plantillas prácticas

## 10.1 Shader mínimo al estilo Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Shader mínimo directo para fragmentos

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Retroalimentación multipaso mínima

### Código fuente de Buffer A

Ruta: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Código fuente de Image

Ruta: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Lista de verificación para solucionar problemas

- No hay salida:
  - verifica que el código fuente de Image no esté vacío
  - verifica que el modo de compilación coincida con tu punto de entrada (`mainImage` o `main`)
- Texturas moradas o no válidas:
  - verifica las asignaciones de recursos y el enrutamiento de canales
  - revisa `iChannelResolution[n].z` (`0.0` significa que el canal no es válido o no está disponible)
- Coordenadas incorrectas en un shader directo:
  - usa `gl_FragCoord.xy - fmAreaOffset` para obtener las coordenadas locales del área
- El comportamiento del arrastre es incorrecto:
  - usa la opción `Update iMouse Position Only While Holding LMB`
- La opacidad no se aplica en un shader directo:
  - multiplica el alfa por `fmOpacity` manualmente
