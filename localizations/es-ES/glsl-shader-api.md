---
title: API de sombreadores GLSL
description: >-
  Escribe sombreadores GLSL de FancyMenu para fondos, elementos y
  superposiciones decorativas.
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# API de sombreadores GLSL de FancyMenu

Este documento describe el entorno de ejecución GLSL que utiliza FancyMenu para:

- el fondo de menú `GLSL`
- los elementos `GLSL`
- las superposiciones decorativas `GLSL`

Incluye los modos de compilación, el enrutamiento multipaso, los uniformes disponibles y patrones prácticos para crear sombreadores.

## 1. Descripción general del entorno de ejecución

FancyMenu renderiza los sombreadores mediante una canalización interna de OpenGL (`#version 150`) y admite:

- sombreadores de un solo paso (solo el paso `Image`)
- sombreadores multipaso (`Buffer A` / `B` / `C` / `D` + `Image`)
- puntos de entrada al estilo de Shadertoy (`mainImage`)
- puntos de entrada directos de fragmento (`main`)

El código fuente de los sombreadores se introduce en campos de texto:

- `Shader Source` (paso Image, necesario para renderizar)
- `Buffer A Source` (opcional)
- `Buffer B Source` (opcional)
- `Buffer C Source` (opcional)
- `Buffer D Source` (opcional)

Si el código fuente de Image está vacío, el renderizado falla con un error «no source».

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

FancyMenu lo integra en `main()` y le pasa las coordenadas locales del área:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

El envoltorio multiplica automáticamente la alfa de salida por `fmOpacity`.

### 2.2 Modo directo

Punto de entrada esperado:

```glsl
void main()
```

Comportamiento de compatibilidad:

- Se intenta una variante compatible con `gl_FragColor`.
- También se intenta una variante sin compatibilidad (para sombreadores modernos con `out vec4` explícito).

En el modo directo, `fmOpacity` no se aplica automáticamente a la salida. Aplícalo manualmente si es necesario.

### 2.3 Modo automático

El modo automático prueba las variantes compatibles en secuencia (Shadertoy/directo) y utiliza la primera que se compila correctamente.

## 3. Preprocesamiento del código fuente y macros integradas

Antes de compilar, FancyMenu normaliza el código fuente:

- elimina la marca BOM de UTF-8
- convierte CRLF/CR en LF
- elimina las líneas `#version ...`
- elimina las líneas `precision ...;`

El preámbulo que se inyecta en tiempo de ejecución incluye:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV de pantalla completa en `[0,1]`, con origen abajo a la izquierda)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Nota:

- Si el código fuente ya declara un nombre de uniforme conocido (por ejemplo, `iTime`), FancyMenu evita inyectar una declaración duplicada.
- FancyMenu sigue intentando asignar valores a ese nombre en tiempo de ejecución.
- Aquí, `textureCube` solo es una macro de alias; `iChannel0..3` son uniformes `sampler2D`.

## 4. Sistema de pasos (Image + Buffer A-D)

FancyMenu tiene 5 pasos disponibles:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (paso final que se muestra en pantalla)

Comportamiento:

- Los pasos de búfer solo se ejecutan si su código fuente no está vacío.
- Es necesario que exista el paso Image para renderizar la salida.
- Los búferes se renderizan en texturas de coma flotante (`GL_RGBA16F`) y, después, se alternan mediante doble búfer (se intercambian las texturas de lectura y escritura en cada fotograma).

### 4.1 Enrutamiento de canales por paso

Cada paso permite configurar el enrutamiento de `iChannel0..3`. Para cada canal puedes seleccionar:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Los canales de recurso proceden de los ajustes `iChannel# Resource`.

Valores predeterminados:

- todos los enrutamientos de `iChannel` se establecen en `None`
- ningún paso de búfer está activo hasta que se introduce código fuente en ese búfer

Importante:

- Si se enruta un paso hacia sí mismo (retroalimentación), se leen los datos del fotograma anterior (la textura de lectura del doble búfer).
- Si el origen enrutado no existe o está inactivo, se asigna una textura alternativa y `iChannelResolution[n].z` pasa a ser `0.0`.

## 5. Coordenadas y semántica del área

Los sombreadores se ejecutan dentro de un área rectangular:

- Fondo de menú: área de pantalla completa
- Elemento GLSL: rectángulo del elemento

Convenciones de coordenadas:

- Los uniformes de píxel se expresan en píxeles locales al área.
- El origen de las coordenadas de píxel que utilizan los sombreadores está abajo a la izquierda.
- Las coordenadas del ratón no se limitan; pueden quedar fuera del área si el cursor está fuera de ella.

Campos especiales:

- `fmAreaOffset`: posición de la esquina inferior izquierda del área en el espacio de píxeles de la pantalla
- `fmAreaTopLeft`: posición de la esquina superior izquierda del área en el espacio de píxeles de la pantalla
- `fmAreaSize`: tamaño del área en píxeles

## 6. Referencia de la API de uniformes

Todos los uniformes siguientes están disponibles tanto para los sombreadores de fondo como para los de elementos.

## 6.1 Uniformes compatibles con Shadertoy

| Uniforme | Tipo | Significado |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Tiempo acumulado del sombreador en segundos |
| `iTimeDelta` | `float` | Tiempo transcurrido desde el último renderizado; puede verse afectado por la pausa o la escala de tiempo |
| `iFrameRate` | `float` | FPS del entorno de ejecución; usa los FPS de Minecraft como valor alternativo |
| `iFrame` | `int` | Contador de fotogramas del entorno de ejecución |
| `iMouse` | `vec4` | Consulta los detalles a continuación |
| `iDate` | `vec4` | `(año, mes, día, segundosDelDíaConFracción)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Actualmente, todos se establecen en `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(ancho, alto, indicadorDeValidez)` para cada canal |
| `iChannel0..3` | `sampler2D` | Entradas de textura enrutadas |

### Detalles de `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: posición actual del ratón en píxeles locales al área, o posición retenida/congelada si la opción está activada
- `z`, `w`: posición de origen del clic izquierdo
  - positiva mientras el botón izquierdo del ratón está pulsado
  - negativa después de soltarlo

Comportamiento controlado por el ajuste:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` se actualiza continuamente
- `... = On`:
  - `iMouse.xy` solo se actualiza mientras se mantiene pulsado el botón izquierdo; después conserva la última posición registrada mientras estaba pulsado

Valor predeterminado:

- `Off` (actualización continua)

## 6.2 Uniformes específicos de FancyMenu

| Uniforme | Tipo | Significado |
|---|---|---|
| `fmAreaOffset` | `vec2` | Desplazamiento en píxeles de la esquina inferior izquierda del área en el espacio de pantalla |
| `fmAreaSize` | `vec2` | Tamaño del área en píxeles |
| `fmAreaPosition` | `vec2` | Igual que `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Desplazamiento en píxeles de la esquina superior izquierda del área en el espacio de pantalla |
| `fmScreenSize` | `vec2` | Tamaño completo de la pantalla en píxeles |
| `fmGuiScale` | `float` | Escala actual de la interfaz |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Desplazamiento del ratón en píxeles del área (Y se invierte para que apunte hacia arriba en el sombreador) |
| `fmMouseButtons` | `ivec4` | Estados de pulsación de los botones `0..3` |
| `fmMouseClickCount` | `ivec4` | Número acumulado de pulsaciones de los botones `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Número acumulado de liberaciones de los botones `0..3` |
| `fmMouseScroll` | `vec2` | Desplazamiento de la rueda desde el renderizado anterior de este entorno de ejecución |
| `fmMouseScrollTotal` | `vec2` | Desplazamiento acumulado de la rueda |
| `fmKeyEvent` | `ivec4` | `(últimoCódigoDeTecla, últimoCódigoDeEscaneo, últimosModificadores, últimaAcción)` |
| `fmKeyEventCount` | `int` | Contador acumulado de eventos de teclado |
| `fmCharEvent` | `ivec4` | `(últimoPuntoDeCódigo, últimosModificadores, 0, 0)` |
| `fmCharEventCount` | `int` | Contador acumulado de eventos de caracteres escritos |
| `fmDateParts` | `ivec4` | `(año, mes, día, díaDeLaSemanaISO1A7)` |
| `fmTimeParts` | `ivec4` | `(hora, minuto, segundo, parteDeMilisegundo0A999)` |
| `fmDayOfYear` | `int` | Día del año |
| `fmWeekOfYear` | `int` | Semana ISO del año |
| `fmUnixTimeSeconds` | `int` | Segundos desde la época Unix |
| `fmUnixTimeMilliseconds` | `int` | Parte de milisegundo de la hora actual (`0..999`) |
| `fmPartialTick` | `float` | Tick parcial actual |
| `fmGameDeltaTicks` | `float` | Ticks de delta del juego de Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Ticks de delta en tiempo real de Minecraft |
| `fmInWorld` | `int` | `1` si estás en un mundo; de lo contrario, `0` |
| `fmIsPaused` | `int` | `1` si el juego está pausado; de lo contrario, `0` |
| `fmOpacity` | `float` | Multiplicador de opacidad efectivo (`0..1`) |
| `fmVariableCount` | `int` | Número actual de variables de FancyMenu |

Valores de acción de tecla (`fmKeyEvent.w`):

- `0` = soltar
- `1` = pulsar
- `2` = repetición

## 6.3 API de uniformes de variables de FancyMenu

Las variables de FancyMenu se exponen directamente como uniformes en tiempo de ejecución (para los sombreadores de fondo, elementos y superposiciones decorativas), sin necesidad de recompilar los sombreadores cuando cambian sus valores.

### Nombres

Para cada variable `<name>`, FancyMenu expone:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = la variable existe actualmente, `0` = no está presente o se ha eliminado)

Normalización del sufijo del uniforme para `<name>`:

- los caracteres permitidos son `[A-Za-z0-9_]`
- todos los demás caracteres se convierten en `_`
- si el primer carácter es un dígito, se antepone `_`

Ejemplos:

- variable `player_hp` -> sufijo `player_hp`
- variable `player-hp` -> sufijo `player_hp`
- variable `2nd_phase` -> sufijo `_2nd_phase`

Importante:

- estos uniformes dinámicos de variables **no se declaran automáticamente** en el código fuente del sombreador (declara manualmente los que utilices)
- evita los nombres de variable que se normalicen al mismo sufijo, ya que se asignan al mismo nombre de uniforme GLSL

### Conversión de valores

Dado un valor de texto de variable `v`:

- `fmVarFloat_*`: número decimal analizado (valor alternativo `0.0`)
- `fmVarInt_*`: entero analizado (valor alternativo `0`)
- `fmVarBool_*`: interpretación como booleano/entero (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`; en cualquier otro caso, un valor numérico distinto de cero => `1`)
- el análisis de vectores admite estos separadores: espacios en blanco, `,`, `;`, `|`
  - `fmVarVec2_*`: los 2 primeros componentes analizados
  - `fmVarVec3_*`: los 3 primeros componentes analizados
  - `fmVarVec4_*`: los 4 primeros componentes analizados
  - si hay menos componentes, se repite el último componente analizado en los espacios que faltan
  - si no hay componentes numéricos, todos los componentes del vector utilizan el valor escalar alternativo

Las [variables de lista](/variables#text-and-list-variables) devuelven el número de elementos en lugar del texto:

- `fmVarFloat_*` y `fmVarInt_*`: número de elementos, por ejemplo, `3` para una lista con 3 elementos
- `fmVarBool_*`: `1` si la lista tiene elementos, `0` si está vacía
- `fmVarVec2_*`, `fmVarVec3_*` y `fmVarVec4_*`: número de elementos en cada componente

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

FancyMenu realiza un seguimiento global de las entradas y captura su estado para cada renderizado:

- movimiento y arrastre del ratón
- pulsación y liberación del ratón
- desplazamiento de la rueda
- pulsación, liberación y repetición de teclas
- escritura de caracteres

Fiabilidad del ratón:

- El entorno de ejecución sincroniza cada fotograma el estado de los botones con las consultas de GLFW para evitar que queden atascados.

Si `Pass Input Events To Shader` está desactivado:

- los uniformes de entrada se restablecen a valores neutros en cada fotograma
- los contadores y eventos se ponen a cero en los datos visibles para el sombreador

## 8. Detalles de las entradas de textura

Los canales de recurso (`iChannel# Resource`) esperan texturas 2D.

Estado de la textura por canal:

- recurso válido: textura asignada, ancho y alto reales, `iChannelResolution[n].z = 1.0`
- recurso inexistente, inactivo o `None`: textura alternativa, `iChannelResolution[n].xyz = (0,0,0)`

Texturas de búfer:

- formato interno: `RGBA16F` (coma flotante)
- filtrado: lineal
- ajuste de bordes: limitar al borde

Es adecuado para datos multipaso (incluidos valores fuera de `[0,1]`).

## 9. Notas sobre el renderizado y la mezcla

- Los pasos de búfer se renderizan fuera de pantalla, sin mezcla.
- El paso Image final utiliza el ajuste `Enable Blending` para la composición.
- El envoltorio de Shadertoy aplica automáticamente `fmOpacity` a la alfa.
- Los sombreadores directos deben aplicar `fmOpacity` manualmente si es necesario.

## 10. Plantillas prácticas

## 10.1 Sombreador mínimo al estilo de Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Sombreador mínimo de fragmento directo

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

Enrutamiento: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Código fuente de Image

Enrutamiento: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Lista de comprobación para resolver problemas

- No hay salida:
  - comprueba que el código fuente de Image no esté vacío
  - comprueba que el modo de compilación coincida con el punto de entrada (`mainImage` o `main`)
- Texturas moradas o no válidas:
  - comprueba las asignaciones de recursos y el enrutamiento de canales
  - consulta `iChannelResolution[n].z` (`0.0` significa que el recurso no es válido o no está disponible)
- Coordenadas incorrectas en un sombreador directo:
  - utiliza `gl_FragCoord.xy - fmAreaOffset` para obtener las coordenadas locales al área
- El arrastre no funciona como se espera:
  - utiliza el ajuste `Update iMouse Position Only While Holding LMB`
- La opacidad no se aplica en un sombreador directo:
  - multiplica la alfa por `fmOpacity` manualmente
