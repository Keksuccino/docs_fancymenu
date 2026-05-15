---
title: Configurar/Obtener opciones de Minecraft
description: >-
  Cómo configurar y obtener opciones de Minecraft como volumen, FOV, distancia
  de renderizado, etc.
---

# Trabajar con opciones de Minecraft en FancyMenu

FancyMenu te permite obtener y configurar los ajustes del juego de Minecraft (opciones) usando distintos elementos de interfaz. Esta guía te mostrará cómo usar botones, deslizadores y elementos tipo ticker para trabajar con opciones de Minecraft en tus diseños de menú personalizados.

# Entender las opciones de Minecraft

Minecraft tiene muchas opciones integradas que controlan desde los ajustes gráficos hasta el volumen del sonido. FancyMenu te permite acceder a estas opciones por su nombre.

Algunos nombres comunes de opciones incluyen:
- `soundCategory_master` - Volumen principal
- `soundCategory_music` - Volumen de la música
- `soundCategory_ambient` - Volumen de sonidos ambientales
- `soundCategory_players` - Volumen de sonidos de jugadores
- `soundCategory_blocks` - Volumen de bloques
- `fov` - Campo de visión
- `gamma` - Brillo
- `renderDistance` - Distancia de renderizado

# Mostrar valores de opciones

Puedes mostrar el valor actual de cualquier opción de Minecraft usando un marcador de posición especial.

El marcador de posición se ve así:
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

Reemplaza `option_name` con el nombre real de la opción que quieres mostrar.

# Configurar opciones con botones

Los botones se pueden usar para establecer valores específicos de las opciones de Minecraft.

## Cómo configurar un botón:

1. Crea un nuevo elemento Button
2. Configura la etiqueta del botón (lo que aparece en el botón)
3. Agrega una acción: clic derecho en el botón → Edit Action Script → Add Action → Set Minecraft Option Value
4. En la ventana "Set Minecraft Option Value":
   - Name: Ingresa el nombre de la opción (como `renderDistance`)
   - Value: Ingresa el valor que quieres establecer (como `16`)

## Ejemplo: 

Crear un botón que configure la distancia de renderizado a 16 chunks:
- Option Name: `renderDistance`
- Value: `16`
- Label: "Configurar distancia de renderizado en 16 chunks"

# Configurar opciones con deslizadores

Los deslizadores son perfectos para opciones con un rango de valores, como los ajustes de volumen o el brillo.

## Cómo configurar un deslizador:

1. Crea un nuevo elemento Slider
2. Configura el tipo de deslizador:
   - Para números enteros (como la distancia de renderizado): elige "Integer Range"
   - Para números decimales (como el volumen): elige "Decimal Range"
3. Define los valores mínimo y máximo
4. Agrega una acción para establecer la opción de Minecraft:
   - Clic derecho → Edit Action Script → Add Action → Set Minecraft Option Value
   - Name: El nombre de la opción
   - Value: `$$value` (esta variable especial contiene el valor actual del deslizador)
5. Configura el valor preseleccionado con el valor actual de la opción:
   - Establece "Pre-Selected Value" a `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

## Ejemplos de formatos de etiqueta para deslizadores:

Para mostrar el valor actual de la opción en la etiqueta del deslizador, usa:
```
Volumen: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

Para mostrar un porcentaje (útil para el volumen):
```
Volumen: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# Configurar opciones con tickers

Los tickers son elementos invisibles que pueden cambiar opciones automáticamente en un horario.

## Cómo configurar un ticker:

1. Crea un nuevo elemento Ticker
2. Configura los ajustes de tick:
   - Tick Mode: Elige cuándo se debe actualizar la opción
   - Tick Delay: Define cada cuánto se actualiza (en milisegundos)
3. Agrega la acción para establecer una opción de Minecraft:
   - Clic derecho → Edit Action Script → Add Action → Set Minecraft Option Value
   - Configura el nombre y el valor de la opción

## Ejemplo:

Configurar gamma (brillo) al máximo cuando se cargue el menú:
- Tick Mode: On Load Screen
- Name: `gamma`
- Value: `1.0`

# Casos de uso comunes

Aquí tienes algunos casos comunes de lo que puedes hacer al usar FancyMenu para configurar y obtener opciones de Minecraft.

## Crear deslizadores de volumen personalizados

Los deslizadores de volumen son un uso común para la integración de opciones de Minecraft. Así puedes crear un deslizador personalizado de volumen de música:

1. Crea un nuevo elemento Slider
2. Configura "Slider Type" en "Decimal Range"
3. Configura "Minimum Range Value" en "0.0"
4. Configura "Maximum Range Value" en "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Configura Name en `soundCategory_music`
   - Configura Value en `$$value`
6. Configura "Pre-Selected Value" a `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`
7. Para mostrar el volumen como porcentaje, establece la etiqueta a: 
   ```
   Música: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

Puedes crear deslizadores similares para otras categorías de sonido:
- Volumen principal: `soundCategory_master`
- Música: `soundCategory_music`
- Ambiental: `soundCategory_ambient`
- Bloques: `soundCategory_blocks`
- Jugadores: `soundCategory_players`
- Clima: `soundCategory_weather`

## Crear un deslizador personalizado de FOV

El campo de visión (FOV) es un ajuste gráfico importante que determina qué tan amplia es tu vista en el juego. La opción FOV usa internamente valores de -1.0 a 1.0, pero se muestra como 30 a 110 en la interfaz.

### Entender la asignación del valor de FOV
- Rango de valor interno: -1.0 a 1.0
- Rango de valor mostrado: 30 a 110
- Fórmula de asignación: `(internal_value + 1) * 40 + 30`

### Paso 1: Crear un elemento Ticker para actualizar el texto de FOV

Primero, necesitamos un ticker que revise el valor actual de FOV y establezca una variable con la descripción adecuada:

1. Crea un nuevo elemento Ticker
2. Configura "Tick Mode" en "Normal" (para que se actualice constantemente)
3. Configura "Tick Delay" en alrededor de "10" (milisegundos) para evitar comprobaciones excesivas

Ahora necesitamos configurar acciones para las etiquetas de FOV. Así debería verse la estructura de tu Action Script:

```
▶ Action Script
│
├─▶ IF (mapped FOV = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (mapped FOV = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[calculated numeric value]
```

Vamos a configurar cada parte:

#### Configurar la etiqueta "Normal" para FOV:
1. Clic derecho → Edit Action Script → Add Action
2. Haz clic en "IF Statement" para agregar un bloque condicional
3. Configura el requisito en "Is Number" con:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "70"
4. Dentro de este bloque IF, agrega la acción "Set Variable Value (FM Variable)" con:
   - Value: `fov_text:Normal`

#### Configurar la etiqueta "Quake Pro" para FOV:
1. Dentro de Action Script, agrega "ELSE-IF Statement"
2. Configura el requisito en "Is Number" con:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "110"
3. Dentro de este bloque ELSE-IF, agrega la acción "Set Variable Value (FM Variable)" con:
   - Value: `fov_text:Quake Pro`

#### Configurar la etiqueta numérica de FOV:
1. Agrega un bloque "ELSE Statement"
2. Dentro de este bloque ELSE, agrega la acción "Set Variable Value (FM Variable)" con:
   - Value: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="FOV Slider Action Script" style="max-width: 600px; height: auto;">

### Paso 2: Crear el deslizador de FOV

1. Crea un nuevo elemento Slider
2. Configura "Slider Type" en "Decimal Range"
3. Configura "Minimum Range Value" en "-1.0"
4. Configura "Maximum Range Value" en "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Configura Name en `fov`
   - Configura Value en `$$value`
6. Configura "Pre-Selected Value" a `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`

### Paso 3: Configurar la etiqueta del deslizador

Configura la etiqueta del deslizador para que muestre simplemente la variable de texto de FOV:

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

Esta etiqueta mostrará:
- "FOV: Normal" cuando el valor sea 70
- "FOV: Quake Pro" cuando el valor sea 110  
- "FOV: 85" (o cualquier otro número) para todos los demás valores

### Consejos para deslizadores de FOV

- El rango interno del deslizador es de -1.0 a 1.0, y debe mapearse a 30 a 110 para mostrarse
- La fórmula de conversión es: `(internal_value + 1) * 40 + 30`
- Solo dos valores tienen etiquetas especiales: 70 (Normal) y 110 (Quake Pro)
- El FOV predeterminado en Minecraft es 70 (lo que corresponde al valor interno 0.0)
- La variable `fov_text` contiene automáticamente la etiqueta especial o el valor numérico

## Mostrar valores de opciones en elementos de texto

También puedes mostrar los valores actuales de las opciones en elementos de texto:

1. Crea un elemento Text
2. Para el contenido del texto, usa el marcador de posición: `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

Por ejemplo, para mostrar la distancia de renderizado actual:
```
Distancia de renderizado actual: {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} chunks
```

# Encontrar nombres de opciones

Puedes encontrar los nombres de todas las opciones disponibles de esta manera:

  1. Crear un botón
  2. Hacer clic derecho sobre él
  3. Hacer clic en "Edit Action Script"
  4. Agregar la acción "Set Minecraft Option Value"
  5. Al editar el valor de la acción, observa las sugerencias del menú desplegable cuando empieces a escribir en el campo "Name"
  
# Consejos importantes

- **Valores válidos**: No todas las opciones aceptan todos los valores. Por ejemplo:
  - Las opciones de volumen aceptan valores de 0.0 a 1.0
  - La distancia de renderizado normalmente acepta números enteros de 2 a 32
  - Las opciones booleanas (true/false) como `pauseOnLostFocus` aceptan "true" o "false"

- **Pruebas**: ¡Prueba siempre tus ajustes para asegurarte de que funcionen como esperas!

- **Retroalimentación visual**: Da a los usuarios retroalimentación visual sobre el valor actual usando los marcadores de posición descritos arriba.
