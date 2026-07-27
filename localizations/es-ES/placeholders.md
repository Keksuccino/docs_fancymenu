---
title: Marcadores de posición
description: Cómo usar los marcadores de posición.
---
# Marcadores de posición

Los marcadores de posición insertan valores en tiempo real en texto, botones, requisitos y otros campos compatibles.

# Información general

## Sintaxis básica
Los marcadores de posición en FancyMenu usan una sintaxis similar a JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Por ejemplo, para mostrar el nombre del jugador:
```
{"placeholder":"playername"}
```

## Anidar marcadores de posición
Puedes usar un marcador de posición dentro del valor de otro marcador de posición.

Ejemplo de marcadores de posición anidados:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Este ejemplo toma el valor máximo de RAM y lo divide entre 1024 para convertirlo de MB a GB.

> [!IMPORTANT]
> Esta es la sintaxis de FancyMenu, no JSON. Los marcadores de posición anidados usan la forma exacta sin escapar que se muestra arriba, por lo que los formateadores de JSON lo rechazarán o lo reescribirán. Los nombres de los marcadores de posición distinguen entre mayúsculas y minúsculas; los marcadores mal formados o desconocidos permanecen visibles como texto y se registran.

# Uso de marcadores de posición

La mayoría de los elementos que tienen entradas de texto admiten marcadores de posición. Puedes ver si una entrada de texto los admite al editarla. Si al editar el texto se abre el **editor de texto** a pantalla completa, admite marcadores de posición.

Para encontrar una **lista de todos los marcadores de posición**, solo tienes que hacer clic en el botón **Marcadores de posición** de la **esquina superior derecha** del **editor de texto**.

En la parte superior de la lista de marcadores de posición hay una **barra de búsqueda** que te permite buscarlos.

Al hacer clic en un marcador de posición de la lista, se pegará en el contenido de texto.

# Marcadores de posición en detalle

Esta sección enumera los marcadores de posición integrados de FancyMenu.

## Resultados no disponibles

La salida de un marcador de posición es siempre texto. Cuando los datos no están disponibles, el resultado depende del marcador de posición: los valores de reserva habituales son una cadena vacía, `0`, `0.0`, `00:00`, `false`, `UNKNOWN` o `ERROR`. Las entradas con un valor de reserva específico lo indican directamente; prueba el valor de reserva antes de usar salidas dependientes del entorno en un [requisito](./conditions), ruta, comando o URL.

## Nombre del jugador (`playername`)

**Finalidad:** Devuelve el nombre de usuario del jugador actual.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"playername"}
```

**Salida:** `Steve`

## UUID del jugador (`playeruuid`)

**Finalidad:** Devuelve el identificador único del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"playeruuid"}
```

**Salida:** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Versión de Minecraft (`mcversion`)

**Finalidad:** Devuelve la versión actual de Minecraft.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"mcversion"}
```

**Salida:** `1.21.1`

## Versión del cargador de mods (`loaderver`)

**Finalidad:** Devuelve la versión del cargador de mods (Fabric/NeoForge).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"loaderver"}
```

**Salida:** `0.16.14`

## Nombre del cargador de mods (`loadername`)

**Finalidad:** Devuelve el nombre del cargador de mods.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"loadername"}
```

**Salida:** `Fabric`

## Versión del mod (`modversion`)

**Finalidad:** Devuelve la versión de un mod específico.

**Valores:** `modid`

**Ejemplo:**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**Salida:** `1.2.3`

## Recuento total de mods (`totalmods`)

**Finalidad:** Devuelve un recuento aproximado de archivos de mods basado en el directorio `mods` y en la cantidad de mods cargados. No cuenta de forma fiable todos los mods desactivados.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"totalmods"}
```

**Salida:** `45`

## Recuento de mods activos (`loadedmods`)

**Finalidad:** Devuelve el número de mods cargados actualmente.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"loadedmods"}
```

**Salida:** `43`

## Progreso de carga del mundo (`world_load_progress`)

**Finalidad:** Devuelve el progreso actual de carga del mundo en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"world_load_progress"}
```

**Salida:** `75`

## Valor de una opción de Minecraft (`minecraft_option_value`)

**Finalidad:** Devuelve el valor de una opción de Minecraft.

**Valores:** `name`

**Ejemplo:**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**Salida:** `70`

## Último mundo o servidor (`last_world_server`)

**Finalidad:** Devuelve información sobre el último mundo o servidor al que se accedió.

**Valores:** `type`, `full_world_path`

**Ejemplo:**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parámetros:
- `type`: Determina qué tipo de información devolver
  - `"both"`: Devuelve el último mundo o servidor al que se accedió (valor predeterminado)
  - `"server"`: Solo devuelve algo si lo último al que se accedió fue un servidor
  - `"world"`: Solo devuelve algo si lo último al que se accedió fue un mundo
- `full_world_path`: Controla cómo se muestran las rutas de los mundos
  - `"true"`: Devuelve la ruta completa del mundo (valor predeterminado)
  - `"false"`: Devuelve solo el nombre del mundo sin la ruta (no afecta a los servidores)

Ejemplos:
- Servidor: `mc.hypixel.net`
- Mundo con ruta completa: `saves/New World`
- Mundo sin ruta completa: `New World`

## Ancho de la pantalla (`guiwidth`)

**Finalidad:** Devuelve el ancho actual de la pantalla en píxeles escalados por la interfaz, no en píxeles físicos del monitor.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"guiwidth"}
```

**Salida:** `960`

## Alto de la pantalla (`guiheight`)

**Finalidad:** Devuelve la altura actual de la pantalla en píxeles escalados por la interfaz, no en píxeles físicos del monitor.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"guiheight"}
```

**Salida:** `540`

## Identificador de la pantalla actual (`screenid`)

**Finalidad:** Devuelve el identificador de la pantalla actual.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"screenid"}
```

**Salida:** `title_screen`

## Ancho de un elemento (`elementwidth`)

**Finalidad:** Devuelve el ancho de un elemento específico.

**Valores:** `id`

**Ejemplo:**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**Salida:** `200`

## Alto de un elemento (`elementheight`)

**Finalidad:** Devuelve la altura de un elemento específico.

**Valores:** `id`

**Ejemplo:**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**Salida:** `20`

## Posición X de un elemento (`elementposx`)

**Finalidad:** Devuelve la posición X de un elemento específico.

**Valores:** `id`

**Ejemplo:**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**Salida:** `150`

## Posición Y de un elemento (`elementposy`)

**Finalidad:** Devuelve la posición Y de un elemento específico.

**Valores:** `id`

**Ejemplo:**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**Salida:** `100`

## Posición X del ratón (`mouseposx`)

**Finalidad:** Devuelve la posición X actual del ratón.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"mouseposx"}
```

**Salida:** `960`

## Posición Y del ratón (`mouseposy`)

**Finalidad:** Devuelve la posición Y actual del ratón.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"mouseposy"}
```

**Salida:** `540`

## Clics por segundo (`clicks_per_second`)

**Finalidad:** Devuelve los clics por segundo actuales de un botón del ratón.

**Valores:** `mouse_button`

**Ejemplo:**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parámetros:
- `mouse_button`: `left` o `right`

**Salida:** `8`

## Escala de la interfaz (`guiscale`)

**Finalidad:** Devuelve la escala actual de la interfaz.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"guiscale"}
```

**Salida:** `2`

## Etiqueta/texto de un widget/botón de Vanilla (`vanillabuttonlabel`)

**Finalidad:** Devuelve la etiqueta o el texto de un widget/botón de Vanilla.

**Valores:** `locator`

**Ejemplo:**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**Salida:** `Options...`

## Valor de un campo de entrada de texto (`text_input_field_value`)

**Finalidad:** Devuelve el valor actual de un campo de entrada de texto personalizado o de Vanilla a partir del identificador del elemento.

**Valores:** `element_identifier`

**Ejemplo:**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**Salida:** `Hello World`

## Salud actual del jugador (`current_player_health`)

**Finalidad:** Devuelve los puntos de salud actuales del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_health"}
```

**Salida:** `20.0`

## Salud máxima del jugador (`max_player_health`)

**Finalidad:** Devuelve los puntos de salud máximos del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"max_player_health"}
```

**Salida:** `20.0`

## Salud actual del jugador (porcentaje) (`current_player_health_percent`)

**Finalidad:** Devuelve la salud del jugador en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_health_percent"}
```

**Salida:** `100`

## Salud de absorción actual del jugador (`current_player_absorption_health`)

**Finalidad:** Devuelve los puntos de salud de absorción del jugador (corazones dorados).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_absorption_health"}
```

**Salida:** `4.0`

## Salud de absorción máxima del jugador (`max_player_absorption_health`)

**Finalidad:** Devuelve la salud de absorción máxima.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"max_player_absorption_health"}
```

**Salida:** `4.0`

## Salud de absorción actual del jugador (porcentaje) (`current_player_absorption_health_percent`)

**Finalidad:** Devuelve la salud de absorción del jugador en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**Salida:** `100`

## Nivel de comida actual del jugador (`current_player_hunger`)

**Finalidad:** Devuelve el nivel de hambre actual del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_hunger"}
```

**Salida:** `20`

## Nivel máximo de comida del jugador (`max_player_hunger`)

**Finalidad:** Devuelve el nivel máximo de hambre.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"max_player_hunger"}
```

**Salida:** `20`

## Nivel de comida actual del jugador (porcentaje) (`current_player_hunger_percent`)

**Finalidad:** Devuelve el hambre del jugador en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_hunger_percent"}
```

**Salida:** `100`

## Saturación de hambre actual del jugador (`current_player_hunger_saturation`)

**Finalidad:** Devuelve el valor actual de saturación de hambre del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_hunger_saturation"}
```

**Salida:** `5.0`

## Armadura actual del jugador (`current_player_armor`)

**Finalidad:** Devuelve el valor actual de armadura del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_armor"}
```

**Salida:** `20`

## Dureza de armadura del jugador (`player_armor_toughness`)

**Finalidad:** Devuelve el valor total de dureza de armadura del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_armor_toughness"}
```

**Salida:** `8.0`

## Armadura máxima del jugador (`max_player_armor`)

**Finalidad:** Devuelve el valor máximo de armadura.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"max_player_armor"}
```

**Salida:** `20`

## Armadura actual del jugador (porcentaje) (`current_player_armor_percent`)

**Finalidad:** Devuelve la armadura del jugador en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_armor_percent"}
```

**Salida:** `100`

## Nivel de oxígeno actual del jugador (`current_player_oxygen`)

**Finalidad:** Devuelve el nivel actual de oxígeno del jugador (burbujas de aire).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_oxygen"}
```

**Salida:** `300`

## Nivel máximo de oxígeno del jugador (`max_player_oxygen`)

**Finalidad:** Devuelve el nivel máximo de oxígeno.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"max_player_oxygen"}
```

**Salida:** `300`

## Nivel de oxígeno actual del jugador (porcentaje) (`current_player_oxygen_percent`)

**Finalidad:** Devuelve el nivel de oxígeno del jugador en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_oxygen_percent"}
```

**Salida:** `100`

## Nivel actual del jugador (`current_player_level`)

**Finalidad:** Devuelve el nivel de experiencia actual del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_level"}
```

**Salida:** `30`

## Experiencia actual del jugador (`current_player_exp`)

**Finalidad:** Devuelve los puntos de experiencia totales del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_exp"}
```

**Salida:** `1250`

## Progreso de experiencia del jugador (porcentaje) (`current_player_exp_progress`)

**Finalidad:** Devuelve el progreso de experiencia del jugador hacia el siguiente nivel en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_player_exp_progress"}
```

**Salida:** `75`

## Fuerza de ataque del jugador (porcentaje) (`player_attack_strength`)

**Finalidad:** Devuelve el tiempo de reutilización del ataque del jugador en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_attack_strength"}
```

**Salida:** `100`

## Modo de juego del jugador (`player_gamemode`)

**Finalidad:** Devuelve el modo de juego actual del jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_gamemode"}
```

**Salida:** `survival`

## Dirección de visión del jugador (`player_view_direction`)

**Finalidad:** Devuelve la dirección hacia la que mira el jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_view_direction"}
```

**Salida:** `north`

## Coordenada X del jugador (`player_x_coordinate`)

**Finalidad:** Devuelve la posición X del jugador en el mundo.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_x_coordinate"}
```

**Salida:** `125`

## Coordenada Y del jugador (`player_y_coordinate`)

**Finalidad:** Devuelve la posición Y del jugador en el mundo.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_y_coordinate"}
```

**Salida:** `64`

## Coordenada Z del jugador (`player_z_coordinate`)

**Finalidad:** Devuelve la posición Z del jugador en el mundo.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_z_coordinate"}
```

**Salida:** `-250`

## Salud actual del montura (`current_mount_health`)

**Finalidad:** Devuelve la salud actual de la entidad sobre la que va montado el jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_mount_health"}
```

**Salida:** `30.0`

## Salud máxima del montura (`max_mount_health`)

**Finalidad:** Devuelve la salud máxima de la entidad sobre la que va montado el jugador.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"max_mount_health"}
```

**Salida:** `30.0`

## Salud actual del montura (porcentaje) (`current_mount_health_percent`)

**Finalidad:** Devuelve la salud de la montura en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_mount_health_percent"}
```

**Salida:** `100`

## Medidor de salto actual de la montura (porcentaje) (`current_mount_jump_meter`)

**Finalidad:** Devuelve el valor del medidor de potencia de salto de la montura.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_mount_jump_meter"}
```

**Salida:** `75`

## Salud del jefe actual (porcentaje) (`current_boss_health`)

**Finalidad:** Devuelve la salud de un jefe activo seleccionado como un porcentaje entero de `0` a `100`. `boss_index` empieza en cero; `0` selecciona la primera barra de jefe.

**Valores:** `boss_index`

**Ejemplo:**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**Salida:** `75`

## Nombre del jefe (`boss_name`)

**Finalidad:** Devuelve el nombre del jefe activo.

**Valores:** `boss_index`, `as_json`

**Ejemplo:**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**Salida:** `Ender Dragon`

## Cantidad de jefes (`boss_count`)

**Finalidad:** Devuelve el número de jefes activos.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"boss_count"}
```

**Salida:** `1`

## Cantidad de efectos activos (`effects_count`)

**Finalidad:** Devuelve el número de efectos de poción activos.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"effects_count"}
```

**Salida:** `3`

## Efecto activo (`active_effect`)

**Finalidad:** Devuelve información sobre un efecto activo específico.

**Valores:** `effect_index`

**Ejemplo:**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**Salida:** `minecraft:speed`

## Ranura de la barra rápida seleccionada (`active_hotbar_slot`)

**Finalidad:** Devuelve la ranura de la barra rápida seleccionada actualmente (0-8).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"active_hotbar_slot"}
```

**Salida:** `4`

## Objeto de una ranura (`slot_item`)

**Finalidad:** Devuelve información sobre un objeto en una ranura de inventario específica.

**Valores:** `slot`

**Ejemplo:**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**Salida:** `minecraft:diamond_sword`

## Cantidad de objetos en la ranura (`slot_item_count`)

**Finalidad:** Devuelve el tamaño de la pila del objeto en una ranura específica del inventario del jugador.

**Valores:** `slot`

**Ejemplo:**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**Salida:** `64`

## Durabilidad del objeto en la ranura (`slot_item_durability`)

**Finalidad:** Devuelve información de durabilidad del objeto en una ranura específica del inventario del jugador.

**Valores:** `slot`, `format`

**Ejemplo:**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parámetros:
- `slot`: Número de ranura del inventario del jugador.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` o `percent`.

**Salida:** `87`

## Nombre visible del objeto en la ranura (`slot_item_display_name_fm`)

**Finalidad:** Devuelve el nombre visible del objeto de una ranura específica como un componente de texto JSON. En modo espectador, las ranuras de la barra rápida pueden resolverse como nombres de objetos del menú de espectador, salvo que `ignore_spectator` sea `true`.

**Valores:** `slot`, `ignore_spectator`

**Ejemplo:**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**Salida:** `{"text":"Diamond Sword","color":"aqua"}`

**Cantidad de objetos en el inventario (`inventory_item_count`)

**Finalidad:** Devuelve el número total de objetos coincidentes en el inventario del jugador. Cuando `item` está vacío, suma las cantidades de todas las ranuras ocupadas del inventario.

**Valores:** `item`

**Ejemplo:**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**Salida:** `12`

## Cantidad de restauración de puntos de comida en una ranura del inventario (`inventory_slot_food_point_restore_amount`)

**Finalidad:** Devuelve los puntos de hambre restaurados por el objeto de comida de la ranura dada del inventario del jugador.

**Valores:** `slot`

**Ejemplo:**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**Salida:** `4.0`

## Objeto del inventario bajo el cursor (`hovered_inventory_item`)

**Finalidad:** Devuelve la clave del objeto sobre el que está el cursor actualmente en una pantalla de inventario.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"hovered_inventory_item"}
```

**Salida:** `minecraft:apple`

## Tiempo de juego del mundo (`game_time`)

**Finalidad:** Devuelve el contador actual de ticks del tiempo en el juego.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"game_time"}
```

**Salida:** `18000`

## Hora del día del mundo (`world_daytime`)

**Finalidad:** Devuelve la hora actual del día del mundo.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"world_daytime"}
```

**Salida:** `13000`

## Hora del día del mundo (`world_daytime_hour`)

**Finalidad:** Devuelve la hora del tiempo del mundo. De forma predeterminada usa formato de 24 horas; establece `twelve_hour_format` en `"true"` para formato de 12 horas.

**Valores:** `twelve_hour_format`

**Ejemplo:**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**Salida:** `12`

## Minuto de la hora del mundo (`world_daytime_minute`)

**Finalidad:** Devuelve el componente de minutos del tiempo del mundo (00-59).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"world_daytime_minute"}
```

**Salida:** `30`

## Dificultad del mundo (`world_difficulty`)

**Finalidad:** Devuelve la dificultad actual del mundo.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"world_difficulty"}
```

**Salida:** `normal`

## Semilla del mundo actual (`current_world_seed`)

**Finalidad:** Devuelve la semilla del mundo actual en un jugador. Devuelve un valor vacío cuando la semilla no está disponible.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_world_seed"}
```

**Salida:** `123456789`

## Bioma actual (`current_biome`)

**Finalidad:** Devuelve el bioma en el que está actualmente el jugador. Establece `as_key` en `"false"` para devolver, cuando esté disponible, un nombre traducido o visible.

**Valores:** `as_key`

**Ejemplo:**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**Salida:** `minecraft:plains`

## Dimensión actual (`current_dimension`)

**Finalidad:** Devuelve la dimensión en la que está actualmente el jugador. Establece `as_key` en `"false"` para devolver, cuando esté disponible, un nombre traducido o visible.

**Valores:** `as_key`

**Ejemplo:**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**Salida:** `minecraft:overworld`

## Valor de gamerule (`gamerule_value`)

**Finalidad:** Devuelve el valor actual de una gamerule en el mundo/servidor cargado. Los mundos de servidor requieren FancyMenu en el servidor.

**Valores:** `name`

**Ejemplo:**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**Salida:** `true`

## Categoría de objeto (`item_category`)

**Finalidad:** Devuelve la categoría de la pestaña creativa de un objeto. Establece `as_key` en `"true"` para devolver la clave de la categoría en lugar del nombre visible.

**Valores:** `item`, `as_key`

**Ejemplo:**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**Salida:** `Combat`

## Título/subtítulo actual de la HUD (`current_title`)

**Finalidad:** Devuelve el texto del título que se muestra actualmente.

**Valores:** `is_subtitle`, `as_json`

**Ejemplo:**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**Salida:** `Game Over!`

## Mensaje de la barra de acción (`action_bar_message_fm`)

**Finalidad:** Devuelve el mensaje actual de la barra de acción de Vanilla como un componente de texto de Minecraft serializado.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"action_bar_message_fm"}
```

**Salida:** `{"text":"You may not rest now","color":"red"}`

## Tiempo del mensaje de la barra de acción (`action_bar_message_time_fm`)

**Finalidad:** Devuelve cuántos ticks seguirá mostrándose el mensaje actual de la barra de acción de Vanilla.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"action_bar_message_time_fm"}
```

**Salida:** `42`

## Rotación X de la cámara (`camera_rotation_x_fm`)

**Finalidad:** Devuelve el pitch actual de la cámara en grados.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"camera_rotation_x_fm"}
```

**Salida:** `12.5`

## Rotación Y de la cámara (`camera_rotation_y_fm`)

**Finalidad:** Devuelve el yaw actual de la cámara en grados.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"camera_rotation_y_fm"}
```

**Salida:** `-90.0`

## Delta X de la rotación de la cámara (`camera_rotation_delta_x_fm`)

**Finalidad:** Devuelve el cambio por tick del pitch de la cámara.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**Salida:** `0.4`

## Delta Y de la rotación de la cámara (`camera_rotation_delta_y_fm`)

**Finalidad:** Devuelve el cambio por tick del yaw de la cámara.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**Salida:** `-1.2`

## Tiempo del objeto resaltado (`highlighted_item_time_fm`)

**Finalidad:** Devuelve cuántos ticks seguirá mostrándose el nombre del objeto resaltado encima de la barra rápida.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"highlighted_item_time_fm"}
```

**Salida:** `30`

## Progreso de uso del objeto del jugador (`player_item_use_progress_fm`)

**Finalidad:** Devuelve el progreso actual de uso del objeto de `0.0` a `1.0`.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_item_use_progress_fm"}
```

**Salida:** `0.65`

## Delta X de la posición del jugador (`player_position_delta_x_fm`)

**Finalidad:** Devuelve el cambio por tick de la posición del jugador en el eje X.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_position_delta_x_fm"}
```

**Salida:** `0.0`

## Delta Y de la posición del jugador (`player_position_delta_y_fm`)

**Finalidad:** Devuelve el cambio por tick de la posición del jugador en el eje Y.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_position_delta_y_fm"}
```

**Salida:** `-0.08`

## Delta Z de la posición del jugador (`player_position_delta_z_fm`)

**Finalidad:** Devuelve el cambio por tick de la posición del jugador en el eje Z.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"player_position_delta_z_fm"}
```

**Salida:** `0.12`

## IP actual del servidor (`current_server_ip`)

**Finalidad:** Devuelve la IP del servidor conectado.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"current_server_ip"}
```

**Salida:** `mc.hypixel.net`

## Lista de jugadores del mundo (`world_players_list`)

**Finalidad:** Devuelve una lista de todos los jugadores que están actualmente en el mundo.

**Valores:** `separator`

**Ejemplo:**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**Salida:** `Steve, Alex, Notch`

## MOTD del servidor (`servermotd`)

**Finalidad:** Devuelve el mensaje del día de un servidor.

**Valores:** `ip`, `line`

**Ejemplo:**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**Salida:** `Welcome to Hypixel!`

## PING del servidor (`serverping`)

**Finalidad:** Devuelve la latencia a un servidor en milisegundos.

**Valores:** `ip`

**Ejemplo:**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**Salida:** `54`

## Recuento de jugadores del servidor (`serverplayercount`)

**Finalidad:** Devuelve la cantidad de jugadores de un servidor.

**Valores:** `ip`

**Ejemplo:**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**Salida:** `25000/30000`

## Estado del servidor (`serverstatus`)

**Finalidad:** Devuelve el estado en línea o fuera de línea de un servidor.

**Valores:** `ip`

**Ejemplo:**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**Salida:** `§aOnline` o `§cOffline`

## Versión del servidor (`serverversion`)

**Finalidad:** Devuelve la versión de Minecraft de un servidor.

**Valores:** `ip`

**Ejemplo:**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**Salida:** `1.21.1`

> [!NOTE]
> Los marcadores de posición en tiempo real de abajo aceptan un valor `timezone`. Usa un identificador de zona horaria de Java como `UTC`, `Europe/Berlin` o `America/New_York`; omítelo o usa `system` para la zona horaria del sistema. `unix_time` devuelve siempre la marca de tiempo Unix y no tiene valor `timezone`.

## Año (`realtimeyear`)

**Finalidad:** Devuelve el año actual.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"realtimeyear"}
```

**Salida:** `2024`

## Mes (`realtimemonth`)

**Finalidad:** Devuelve el mes actual (01-12).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"realtimemonth"}
```

**Salida:** `01`

## Día (`realtimeday`)

**Finalidad:** Devuelve el día actual del mes (01-31).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"realtimeday"}
```

**Salida:** `27`

## Hora (`realtimehour`)

**Finalidad:** Devuelve la hora actual. De forma predeterminada usa formato de 24 horas; establece `twelve_hour_format` en `"true"` para formato de 12 horas.

**Valores:** `twelve_hour_format`, `timezone`

**Ejemplo:**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**Salida:** `14`

## Minuto (`realtimeminute`)

**Finalidad:** Devuelve el minuto actual (00-59).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"realtimeminute"}
```

**Salida:** `30`

## Segundo (`realtimesecond`)

**Finalidad:** Devuelve el segundo actual (00-59).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"realtimesecond"}
```

**Salida:** `45`

## Hora actual en milisegundos (marca de tiempo Unix) (`unix_time`)

**Finalidad:** Devuelve la marca de tiempo Unix actual en milisegundos.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"unix_time"}
```

**Salida:** `1716552478123`

## Información de la CPU (`cpuinfo`)

**Finalidad:** Devuelve información sobre la CPU.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"cpuinfo"}
```

**Salida:** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Uso de CPU (JVM) (`jvmcpu`)

**Finalidad:** Devuelve el uso de CPU de la JVM en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"jvmcpu"}
```

**Salida:** `25.5`

## Uso de CPU (SO) (`oscpu`)

**Finalidad:** Devuelve el uso de CPU del sistema operativo en porcentaje.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"oscpu"}
```

**Salida:** `42.8`

## Información de la GPU (`gpuinfo`)

**Finalidad:** Devuelve el nombre informado para el dispositivo de renderizado activo de Minecraft. No garantiza identificar una GPU física concreta.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"gpuinfo"}
```

**Salida:** `NVIDIA GeForce RTX 3080`

## Versión de Java (`javaver`)

**Finalidad:** Devuelve la versión de Java.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"javaver"}
```

**Salida:** `17.0.2`

## Máquina virtual de Java (`jvmname`)

**Finalidad:** Devuelve el nombre de la Máquina Virtual de Java.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"jvmname"}
```

**Salida:** `OpenJDK 64-Bit Server VM`

## Versión de OpenGL (`glver`)

**Finalidad:** Devuelve información del controlador del dispositivo de renderizado activo de Minecraft. A pesar del nombre heredado `glver`, no se garantiza que el valor sea solo una cadena de versión de OpenGL.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"glver"}
```

**Salida:** `4.6.0 NVIDIA 516.94`

## Nombre del sistema operativo (`osname`)

**Finalidad:** Devuelve el nombre del sistema operativo.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"osname"}
```

**Salida:** `Windows 10`

## FPS (fotogramas por segundo) (`fps`)

**Finalidad:** Devuelve los fotogramas por segundo actuales.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"fps"}
```

**Salida:** `120`

## RAM usada en MB (`usedram`)

**Finalidad:** Devuelve la cantidad de RAM actualmente en uso (MB).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"usedram"}
```

**Salida:** `4096`

## RAM máxima en MB (`maxram`)

**Finalidad:** Devuelve la RAM máxima asignada (MB).

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"maxram"}
```

**Salida:** `8192`

## RAM usada en %% (`percentram`)

**Finalidad:** Devuelve el porcentaje de RAM actualmente en uso.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"percentram"}
```

**Salida:** `50`

## Volumen de un elemento de audio (`audio_element_vol`)

**Finalidad:** Devuelve el volumen de un elemento de audio.

**Valores:** `element_identifier`

**Ejemplo:**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**Salida:** `0.5`

## Pista de audio actual (`audio_element_current_track`)

**Finalidad:** Devuelve el nombre de la pista de un elemento de audio.

**Valores:** `element_identifier`, `display_name_mappings`

**Ejemplo:**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

En `display_name_mappings`, `=>` separa un nombre de archivo de su nombre visible y `%:%` separa los mapeos.

**Salida:** `Menu Theme`

## Duración del audio (`audio_duration`)

**Finalidad:** Devuelve la duración de la pista cargada actual del [elemento de audio](./elements#audio) en formato `MM:SS`. La pista puede estar reproduciéndose, en pausa o detenida.

**Valores:** `element_identifier`

**Ejemplo:**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**Salida:** `03:45`

## Tiempo de reproducción del audio (`audio_playtime`)

**Finalidad:** Devuelve el tiempo de reproducción actual de una pista de audio. Establece `show_percentage` en `"true"` para obtener un valor de progreso de 0 a 100 en lugar de `MM:SS`.

**Valores:** `element_identifier`, `show_percentage`

**Ejemplo:**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**Salida:** `01:30` (o `45` cuando `show_percentage` es `"true"`)

**Resultado no disponible:** `00:00`, o `0` en modo porcentaje. El valor actual está disponible mientras la pista se está reproduciendo o en pausa; las pistas detenidas, ausentes o no listas usan el resultado no disponible.

## Estado de reproducción de audio (`audio_playing_state`)

**Finalidad:** Devuelve si un elemento de audio se está reproduciendo (true/false).

**Valores:** `element_identifier`

**Ejemplo:**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**Salida:** `true`

## Volumen de un elemento de vídeo (`video_element_vol`)

**Finalidad:** Devuelve el nivel de volumen de un elemento de vídeo (0.0 a 1.0).

**Valores:** `element_identifier`

**Ejemplo:**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**Salida:** `0.5`

## Duración de un elemento de vídeo (`video_element_duration`)

**Finalidad:** Devuelve la duración total de un elemento de vídeo en formato `MM:SS`. Establece `output_as_timestamp` en `"true"` para devolver una marca de tiempo en milisegundos.

**Valores:** `element_identifier`, `output_as_timestamp`

**Ejemplo:**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**Salida:** `02:00` (o `120000` cuando `output_as_timestamp` es `"true"`)

## Tiempo de reproducción de un elemento de vídeo (`video_element_playtime`)

**Finalidad:** Devuelve el tiempo de reproducción actual (progreso) de un elemento de vídeo en formato `MM:SS`. Establece `show_percentage` en `"true"` para un valor de progreso de 0 a 100, o `output_as_timestamp` en `"true"` para milisegundos.

**Valores:** `element_identifier`, `show_percentage`, `output_as_timestamp`

**Ejemplo:**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**Salida:** `00:45` (o `38` como porcentaje, o `45200` como marca de tiempo)

## Estado de pausa de un elemento de vídeo (`video_element_paused_state`)

**Finalidad:** Devuelve si un elemento de vídeo está en pausa (true/false).

**Valores:** `element_identifier`

**Ejemplo:**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**Salida:** `false`

## Volumen del fondo de vídeo (`video_background_vol`)

**Finalidad:** Devuelve el nivel de volumen de un fondo de menú de vídeo (0.0 a 1.0).

**Valores:** `background_identifier`

**Ejemplo:**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**Salida:** `0.7`

## Duración del fondo de vídeo (`video_background_duration`)

**Finalidad:** Devuelve la duración total de un fondo de menú de vídeo en formato `MM:SS`. Establece `output_as_timestamp` en `"true"` para devolver una marca de tiempo en milisegundos.

**Valores:** `background_identifier`, `output_as_timestamp`

**Ejemplo:**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**Salida:** `03:00` (o `180000` cuando `output_as_timestamp` es `"true"`)

## Tiempo de reproducción del fondo de vídeo (`video_background_playtime`)

**Finalidad:** Devuelve el tiempo de reproducción actual (progreso) de un fondo de menú de vídeo en formato `MM:SS`. Establece `show_percentage` en `"true"` para un valor de progreso de 0 a 100, o `output_as_timestamp` en `"true"` para milisegundos.

**Valores:** `background_identifier`, `show_percentage`, `output_as_timestamp`

**Ejemplo:**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**Salida:** `01:00` (o `33` como porcentaje, o `60500` como marca de tiempo)

## Estado de pausa del fondo de vídeo (`video_background_paused_state`)

**Finalidad:** Devuelve si un fondo de menú de vídeo está en pausa (true/false).

**Valores:** `background_identifier`

**Ejemplo:**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**Salida:** `true`

## Calculadora (`calc`)

**Finalidad:** El marcador de posición calculadora es una herramienta potente que te permite realizar cálculos matemáticos dentro de tus diseños. Admite una amplia variedad de operaciones matemáticas y puede trabajar tanto con números decimales como enteros.

**Valores:** `decimal`, `expression`

### Sintaxis básica

**Ejemplo:**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

La calculadora tiene dos parámetros principales:
- `decimal`: Determina si el resultado debe incluir decimales (`true`) o redondearse a enteros (`false`)
- `expression`: La expresión matemática a evaluar

### Operaciones compatibles
La calculadora admite estas operaciones matemáticas:
- Aritmética básica: `+` (suma), `-` (resta), `*` (multiplicación), `/` (división)
- Paréntesis: `( )` para agrupar operaciones
- Potencia: `^` para exponentes
- Raíz cuadrada: `sqrt()`
- Funciones trigonométricas: `sin()`, `cos()`, `tan()`
- Constantes matemáticas: `pi`, `e`
- Valor absoluto: `abs()`
- Logaritmos: `log()`, `ln()`

## Número aleatorio (`random_number`)

**Finalidad:** Genera un número aleatorio dentro de un intervalo especificado.

**Valores:** `min`, `max`

**Ejemplo:**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**Salida:** `42`

## Número máximo (`maxnum`)

**Finalidad:** Devuelve el mayor de dos números.

**Valores:** `first`, `second`

**Ejemplo:**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**Salida:** `20`

## Número mínimo (`minnum`)

**Finalidad:** Devuelve el menor de dos números.

**Valores:** `first`, `second`

**Ejemplo:**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**Salida:** `10`

## Número absoluto (`absnum`)

**Finalidad:** Devuelve el valor absoluto de un número.

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**Salida:** `10.5`

## Hacer negativo un número (`negnum`)

**Finalidad:** Convierte un número positivo en negativo. El cero y los valores ya negativos se devuelven sin cambios.

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**Salida:** `-10.5`

## *pi* (Matemáticas) (`math_pi`)

**Finalidad:** Devuelve el valor de π.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"math_pi"}
```

**Salida:** `3.141592653589793`

## Seno trigonométrico (Matemáticas) (`math_sin`)

**Finalidad:** Devuelve el seno de un ángulo en radianes. Convierte primero los valores en grados a radianes.

**Valores:** `angle`

**Ejemplo:**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**Salida:** `1.0`

## Coseno trigonométrico (Matemáticas) (`math_cos`)

**Finalidad:** Devuelve el coseno de un ángulo en radianes. Convierte primero los valores en grados a radianes.

**Valores:** `angle`

**Ejemplo:**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**Salida:** `1.0`

## Tangente trigonométrica (Matemáticas) (`math_tan`)

**Finalidad:** Devuelve la tangente de un ángulo en radianes. Convierte primero los valores en grados a radianes.

**Valores:** `angle`

**Ejemplo:**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**Salida:** `0.0`

## Piso (Matemáticas) (`math_floor`)

**Finalidad:** Devuelve el floor matemático de un número, formateado con el sufijo decimal `.0`.

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**Salida:** `3.0`

## Techo (Matemáticas) (`math_ceil`)

**Finalidad:** Devuelve el techo matemático de un número, formateado con el sufijo decimal `.0`.

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**Salida:** `4.0`

Usa [**Round**](#round-math-math_round) o [**Calculator**](#calculator-calc) con la salida decimal desactivada cuando necesites texto entero sin `.0`.

## Redondear (Matemáticas) (`math_round`)

**Finalidad:** Redondea un número. De forma predeterminada se redondea al entero más cercano; establece `decimals` en un número no negativo para redondear a esa cantidad de decimales.

**Valores:** `num`, `decimals`

**Ejemplo:**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**Salida:** `3.14` (con `decimals:-1` o si se omite → `3`)

## Signo (Matemáticas) (`math_sign`)

**Finalidad:** Devuelve el signo de un número (1 para positivo, -1 para negativo, 0 para cero).

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**Salida:** `-1`

## Seno hiperbólico (Matemáticas) (`math_sinh`)

**Finalidad:** Devuelve el seno hiperbólico de un número.

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**Salida:** `1.1752011936438014`

## Coseno hiperbólico (Matemáticas) (`math_cosh`)

**Finalidad:** Devuelve el coseno hiperbólico de un número.

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**Salida:** `1.5430806348152437`

## Tangente hiperbólica (Matemáticas) (`math_tanh`)

**Finalidad:** Devuelve la tangente hiperbólica de un número.

**Valores:** `num`

**Ejemplo:**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**Salida:** `0.7615941559557649`

## Dividir texto (`split_text`)

**Finalidad:** Divide texto usando un delimitador especificado.

**Valores:** `input`, `regex`, `max_parts`, `split_index`

**Ejemplo:**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**Salida:** `world`

## Recortar texto (`trim_text`)

**Finalidad:** Elimina los espacios en blanco iniciales y finales.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**Salida:** `hello world`

## Recortar texto por extremos (`crop_text`)

**Finalidad:** Elimina caracteres del inicio y del final del texto.

**Valores:** `text`, `remove_from_start`, `remove_from_end`

**Ejemplo:**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**Salida:** `ello worl`

## Convertir a cadena (`stringify`)

**Finalidad:** Convierte un texto en una cadena escapando todos los caracteres de sintaxis.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**Salida:** `text with \{special\} \"characters\"`

## Localizar texto (`local`)

**Finalidad:** Obtiene texto localizado para una clave.

**Valores:** `key`

**Ejemplo:**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**Salida:** `Singleplayer`

## Texto web (`webtext`)

**Finalidad:** Obtiene contenido de texto desde una URL web.

**Valores:** `link`

**Ejemplo:**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**Salida:** `Welcome to the server!`

## Texto aleatorio (`randomtext`)

**Finalidad:** Devuelve una línea aleatoria de un archivo de texto, una URL o texto plano directo. El texto cambia a intervalos especificados. El contenido de archivos y URLs se actualiza aproximadamente cada 30 segundos; el contenido de texto plano directo permanece en caché porque no necesita recargarse.

**Valores:** `source`, `interval`

En los valores de los marcadores de posición, `/config/...` significa `<game-directory>/config/...`; no es una ruta raíz del sistema de archivos. Consulta [Recursos](./resources#local-resources).

**Ejemplo:**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parámetros:
- `source`: La fuente de las líneas de texto (sustituye al antiguo parámetro `path`)
  - Ruta de archivo: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Texto plano: `Line 1\nLine 2\nLine 3`
- `interval`: Tiempo en segundos entre cambios de texto

El marcador de posición ahora admite tres tipos de fuente:
1. **Archivos locales**: archivos de texto del directorio del juego
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: archivos de texto remotos de Internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texto plano**: entrada de texto directa con líneas separadas por `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Nota: los marcadores de posición antiguos que usan `path` en lugar de `source` seguirán funcionando.

## Analizador JSON (`json`)

**Finalidad:** Analiza datos JSON desde un archivo, una URL o contenido JSON directo, y extrae valores mediante expresiones de ruta JSON.

**Valores:** `source`, `json_path`

**Ejemplo:**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parámetros:
- `source`: La fuente de los datos JSON
  - Ruta de archivo: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - JSON directo: `{"name":"Steve","level":42}`
- `json_path`: La expresión de ruta JSON para extraer datos

El marcador de posición ahora admite tres tipos de fuente:
1. **Archivos locales**: archivos JSON del directorio del juego
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: datos JSON remotos de APIs o servicios web
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON directo**: contenido JSON en línea
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Ejemplos de rutas JSON:
- `$.name` - Obtiene el campo "name" desde la raíz
- `$.player.level` - Obtiene el campo anidado "level" dentro de "player"
- `$.items[0].id` - Obtiene el "id" del primer elemento de una matriz
- `$.scores.*` - Obtiene todos los valores del objeto "scores"

## Ruta absoluta de archivo/carpeta (`absolute_path`)

**Finalidad:** Devuelve la ruta absoluta de un archivo.

**Valores:** `short_path`

**Ejemplo:**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**Salida:** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## Recuento de caracteres del texto (`text_character_count`)

**Finalidad:** Devuelve el número de caracteres del texto dado.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**Salida:** `12`

## Ancho del texto (`text_width`)

**Finalidad:** Devuelve el ancho en píxeles del texto dado cuando se renderiza.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**Salida:** `66`

## Texto en mayúsculas (`uppercase_text`)

**Finalidad:** Convierte el texto de entrada a letras mayúsculas.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**Salida:** `HELLO WORLD`

## Texto en minúsculas (`lowercase_text`)

**Finalidad:** Convierte el texto de entrada a letras minúsculas.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**Salida:** `hello world`

## Texto en formato de título (`title_case_text`)

**Finalidad:** Convierte el texto de entrada a formato de título.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**Salida:** `Hello World`

## Texto en formato de oración (`sentence_case_text`)

**Finalidad:** Convierte el texto de entrada a formato de oración.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**Salida:** `Hello world. This is fancymenu!`

## Texto en snake_case (`snake_case_text`)

**Finalidad:** Convierte el texto de entrada a `snake_case`.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**Salida:** `hello_world`

## Texto en kebab-case (`kebab_case_text`)

**Finalidad:** Convierte el texto de entrada a `kebab-case`.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**Salida:** `hello-world`

## Texto en mayúsculas y minúsculas alternas (`alternating_case_text`)

**Finalidad:** Convierte el texto de entrada a mayúsculas y minúsculas alternas.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**Salida:** `aLtErNaTiNg CaSe`

## Alternar mayúsculas y minúsculas del texto (`toggle_case_text`)

**Finalidad:** Alterna el uso de mayúsculas y minúsculas de cada letra del texto de entrada.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**Salida:** `tOGGLE cASE`

## Codificar a Base64 (`base64_encode`)

**Finalidad:** Codifica el texto dado como Base64.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**Salida:** `SGVsbG8gV29ybGQ=`

## Decodificar desde Base64 (`base64_decode`)

**Finalidad:** Decodifica una cadena Base64 de nuevo a texto plano.

**Valores:** `text`

**Ejemplo:**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**Salida:** `Hello World`

## Texto de archivo (`file_text`)

**Finalidad:** Devuelve líneas de texto de un archivo o URL. Puede devolver todas las líneas o solo las últimas X líneas.

**Valores:** `path_or_url`, `mode`, `separator`, `last_lines`

**Ejemplo:**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parámetros:
- `path_or_url`: Ruta de archivo o URL desde la que leer
- `mode`: `"all"` (devuelve todas las líneas) o `"last"` (devuelve solo las últimas X líneas)
- `separator`: Texto usado entre líneas (predeterminado: `"\n"`)
- `last_lines`: Número de líneas a devolver cuando el modo es `"last"` (predeterminado: `"1"`)

**Salida:**

```text
First line
Second line
```

## Contenido del portapapeles (`clipboard_content`)

**Finalidad:** Devuelve el contenido de texto actual almacenado en el portapapeles del sistema.

**Valores:** Ninguno

**Ejemplo:**

```
{"placeholder":"clipboard_content"}
```

**Salida:** `Hello from the clipboard`

## Reemplazar texto (`replace_text`)

**Finalidad:** Reemplaza texto en una cadena usando texto literal o expresiones regulares.

**Valores:** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**Ejemplo:**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parámetros:
- `text`: El texto de entrada que se va a procesar
- `search`: El texto o patrón regex que se buscará
- `replacement`: El texto de reemplazo
- `use_regex`: Si se usa regex (`"true"`) o coincidencia literal (`"false"`)
- `replace_all`: Reemplaza todas las apariciones (`"true"`) o solo la primera (`"false"`)

**Salida:** `Hello FancyMenu! This is a test.`

## Estructura switch-case (`switch_case`)

**Finalidad:** Realiza una operación switch-case basada en un valor.

**Valores:** `value`, `cases`, `default`

**Ejemplo:**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**Salida:** `first case` (si el valor es 1)

## Obtener valor de variable (variable de FM) (`getvariable`)

**Finalidad:** Recupera el valor de una variable guardada previamente.

**Valores:** `name`

**Ejemplo:**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**Salida:** `42`

## Obtener datos NBT (`nbt_data_get`)

**Finalidad:** Recupera datos NBT en el cliente (similar al comando `/data get`). Usa la variante del servidor `nbt_data_get_server` cuando estés conectado a un servidor y necesites valores autoritativos del lado del servidor.

**Valores:** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**Ejemplo:**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parámetros:
- `source_type`: `"entity"` o `"block"`
- `entity_selector`: Selector de entidad como `@s`, `@p`, `@e` o UUID/nombre (para entidades)
- `block_pos`: Posición del bloque en formato `"x y z"` (para bloques)
- `nbt_path`: La ruta NBT que se va a recuperar
- `scale`: Factor de escalado opcional para valores numéricos (predeterminado: `"1.0"`)
- `return_type`: Cómo devolver los datos:
  - `"value"`: Valor predeterminado, devuelve el valor (con escalado opcional para números)
  - `"string"`: Devuelve los datos NBT reales como cadena
  - `"snbt"`: Devuelve como SNBT (NBT formateado)
  - `"json"`: Devuelve como componente con formato JSON (para etiquetas compuestas)

**Salida:** `20` (para el nivel de comida)

## Obtener datos NBT (lado del servidor) (`nbt_data_get_server`)

**Finalidad:** Consulta datos NBT en el lado del servidor (mediante un paquete) y almacena en caché los resultados brevemente. Los valores son equivalentes al marcador de posición del lado del cliente.

**Valores:** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**Ejemplo:**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**Salida:** `minecraft:diamond_sword`

## Último mensaje de muerte (`lastdeathmessage`)

**Finalidad:** Devuelve el último mensaje de muerte registrado del jugador cliente. Establece `as_json_component` en `"true"` para obtener el componente de texto JSON sin procesar.

**Valores:** `as_json_component`

**Ejemplo:**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**Salida:** `Steve was slain by Zombie`

## Duración del tiempo de actividad (`uptime_duration`)

**Finalidad:** Devuelve cuánto tiempo lleva cargado FancyMenu. De forma predeterminada, el valor está en segundos; establece `output_as_millis` en `"true"` para recibir milisegundos.

**Valores:** `output_as_millis`

**Ejemplo:**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**Salida:** `742` (segundos desde la carga)

## Nombres de guardados del mundo (`level_save_names`)

**Finalidad:** Enumera todos los nombres de guardados del mundo local unidos por el separador elegido. Se ejecuta en el hilo del cliente.

**Valores:** `separator`

**Ejemplo:**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**Salida:** `Creative Test, Survival World, Hardcore`

## Datos del guardado del mundo (`level_save_data`)

**Finalidad:** Devuelve los datos serializados del nivel para el nombre de mundo dado (debe coincidir con el nombre visible mostrado en la lista de mundos guardados).

**Valores:** `level_name`

**Ejemplo:**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**Salida:** `{"name":"Survival World","gameMode":"survival",...}`

## Convertidor de base numérica (`number_base_convert`)

**Finalidad:** Convierte un número (entero o fraccionario) de una base a otra (2–36). Usa base decimal por defecto si no se especifican las bases.

**Valores:** `input`, `from_base`, `to_base`

**Ejemplo:**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**Salida:** `43.8`

## Tamaño de archivo (`file_size`)

**Finalidad:** Devuelve el tamaño de un archivo local en bytes. Solo se permiten rutas locales.

**Valores:** `path`

**Ejemplo:**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Salida:** `1284`

## MD5 de archivo (`file_md5`)

**Finalidad:** Devuelve el hash MD5 de un archivo local como una cadena hexadecimal en minúsculas.

**Valores:** `path`

**Ejemplo:**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Salida:** `d41d8cd98f00b204e9800998ecf8427e`

# Ejemplos prácticos

## Crear un indicador dinámico de memoria
```
RAM usada: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Crear un reloj en tiempo real
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

## Crear un indicador de información del sistema
```
SO: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD de estado del jugador
```
Salud: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armadura: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Nivel de XP: {"placeholder":"current_player_level"}
```

## Cálculo complejo con marcadores de posición anidados
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Mostrar coordenadas con redondeo
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Buenas prácticas

1. **Cachea operaciones costosas**: Algunos marcadores de posición (como los que leen información del sistema) pueden consumir recursos. Considera usar variables para almacenar sus valores si necesitas utilizarlos varias veces.

2. **Usa los ajustes decimales adecuados**: Al trabajar con cálculos, usa el parámetro `decimal` de forma apropiada. Establécelo en `false` cuando necesites enteros y en `true` cuando necesites valores decimales precisos.

3. **Gestiona los valores faltantes**: Considera siempre qué debe ocurrir si un marcador de posición no devuelve ningún valor. Puede que quieras proporcionar valores predeterminados en esos casos.

4. **Prueba el rendimiento**: Al usar muchos marcadores de posición o estructuras anidadas complejas, prueba el impacto en el rendimiento, especialmente en sistemas de gama baja.

5. **Usa el dimensionado/posicionamiento avanzado**: Para elementos de interfaz dinámicos, combina marcadores de posición con dimensionado y posicionamiento avanzados para crear diseños adaptables.

6. **Combínalos con variables**: Usa marcadores de posición junto con variables para contenido aún más dinámico que se pueda actualizar mediante acciones.

# Problemas comunes y soluciones

## El marcador de posición no se actualiza
Si el valor de un marcador de posición no se actualiza como esperas, comprueba:
- Si el marcador de posición está formateado correctamente
- Si estás usando la mayúscula/minúscula correcta en los identificadores de los marcadores de posición
- Si el marcador de posición requiere condiciones específicas para actualizarse

## Los marcadores de posición anidados no funcionan
Al anidar marcadores de posición:
- Asegúrate de escapar correctamente las comillas
- Verifica que cada marcador de posición anidado sea válido por sí mismo

## Problemas de rendimiento
Si notas problemas de rendimiento:
- Reduce el número de marcadores de posición utilizados
- Evita el anidamiento innecesario
- Considera usar variables para valores accedidos con frecuencia
- Usa el marcador de posición adecuado para lo que necesitas (por ejemplo, no uses marcadores de posición en tiempo real cuando bastaría con valores estáticos)
