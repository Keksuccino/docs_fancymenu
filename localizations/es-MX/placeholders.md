---
title: Marcadores de posición
description: Cómo usar marcadores de posición.
---

# Marcadores de posición

Los marcadores de posición son valores dinámicos que se reemplazan por contenido real cuando se usan. En FancyMenu, los marcadores de posición te permiten insertar contenido dinámico en varios elementos como texto, botones y requisitos de carga. Piensa en ellos como variables que se evalúan y se reemplazan por sus valores reales cuando se muestran tus diseños.

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
Una de las funciones más potentes del sistema de marcadores de posición de FancyMenu es que puedes anidarlos dentro de otros marcadores de posición. Esto significa que puedes usar la salida de un marcador de posición como entrada para otro.

Ejemplo de marcadores de posición anidados:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Este ejemplo toma el valor máximo de RAM y lo divide entre 1024 para convertirlo de MB a GB.

# Uso de marcadores de posición

La mayoría de los elementos que tienen entradas de texto admiten marcadores de posición. Puedes ver si una entrada de texto los admite cuando la editas. Si al editar el texto se abre el **editor de texto** a pantalla completa, sí admite marcadores de posición. 

Para encontrar una **lista de todos los marcadores de posición**, solo haz clic en el botón **Placeholders** en la **esquina superior derecha** del **editor de texto**.

En la parte superior de la lista de marcadores de posición hay una **barra de búsqueda** que te permite buscar marcadores de posición.

Al hacer clic en un marcador de posición de la lista, se pegará en el contenido de texto.

# Marcadores de posición en detalle

Esta lista contiene la mayoría, si no es que todos, los marcadores de posición disponibles en FancyMenu. La lista a veces puede quedar un poco desactualizada debido a actualizaciones del mod.

## Nombre del jugador (playername)
Devuelve el nombre de usuario del jugador actual.
```
{"placeholder":"playername"}
```
Ejemplo de salida: `Steve`

## UUID del jugador (playeruuid)
Devuelve el identificador único del jugador.
```
{"placeholder":"playeruuid"}
```
Ejemplo de salida: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Versión de Minecraft (mcversion)
Devuelve la versión actual de Minecraft.
```
{"placeholder":"mcversion"}
```
Ejemplo de salida: `1.19.2`

## Versión del cargador de mods (loaderver)
Devuelve la versión del cargador de mods (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Ejemplo de salida: `43.2.0`

## Nombre del cargador de mods (loadername)
Devuelve el nombre del cargador de mods.
```
{"placeholder":"loadername"}
```
Ejemplo de salida: `Forge`

## Versión del mod (modversion)
Devuelve la versión de un mod específico.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Ejemplo de salida: `2.14.9`

## Total de mods instalados (totalmods)
Devuelve el número total de mods instalados.
```
{"placeholder":"totalmods"}
```
Ejemplo de salida: `45`

## Cantidad de mods activos (loadedmods)
Devuelve la cantidad de mods cargados actualmente.
```
{"placeholder":"loadedmods"}
```
Ejemplo de salida: `43`

## Progreso de carga del mundo (world_load_progress)
Devuelve el progreso actual de carga del mundo en porcentaje.
```
{"placeholder":"world_load_progress"}
```
Ejemplo de salida: `75`

## Valor de opción de Minecraft (minecraft_option_value)
Devuelve el valor de una opción de Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Ejemplo de salida: `70`

## Último mundo o servidor (last_world_server)
Devuelve información sobre el último mundo o servidor al que se accedió.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parámetros:
- `type`: Determina qué tipo de información devolver
  - `"both"`: Devuelve el último mundo o servidor al que se accedió (predeterminado)
  - `"server"`: Solo devuelve si lo último accedido fue un servidor
  - `"world"`: Solo devuelve si lo último accedido fue un mundo
- `full_world_path`: Controla cómo se muestran las rutas del mundo
  - `"true"`: Devuelve la ruta completa del mundo (predeterminado)
  - `"false"`: Devuelve solo el nombre del mundo sin la ruta (no afecta a los servidores)

Ejemplos:
- Servidor: `mc.hypixel.net`
- Mundo con ruta completa: `saves/New World`
- Mundo sin ruta completa: `New World`

## Ancho de la pantalla (guiwidth)
Devuelve el ancho actual de la pantalla.
```
{"placeholder":"guiwidth"}
```
Ejemplo de salida: `1920`

## Alto de la pantalla (guiheight)
Devuelve la altura actual de la pantalla.
```
{"placeholder":"guiheight"}
```
Ejemplo de salida: `1080`

## Identificador de la pantalla actual (screenid)
Devuelve el identificador de la pantalla actual.
```
{"placeholder":"screenid"}
```
Ejemplo de salida: `title_screen`

## Ancho del elemento (elementwidth)
Devuelve el ancho de un elemento específico.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Ejemplo de salida: `200`

## Alto del elemento (elementheight)
Devuelve la altura de un elemento específico.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Ejemplo de salida: `20`

## Posición X del elemento (elementposx)
Devuelve la posición X de un elemento específico.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Ejemplo de salida: `150`

## Posición Y del elemento (elementposy)
Devuelve la posición Y de un elemento específico.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Ejemplo de salida: `100`

## Posición X del mouse (mouseposx)
Devuelve la posición X actual del mouse.
```
{"placeholder":"mouseposx"}
```
Ejemplo de salida: `960`

## Posición Y del mouse (mouseposy)
Devuelve la posición Y actual del mouse.
```
{"placeholder":"mouseposy"}
```
Ejemplo de salida: `540`

## Clics por segundo (clicks_per_second)
Devuelve los clics por segundo actuales para un botón del mouse.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parámetros:
- `mouse_button`: `left` o `right`

Ejemplo de salida: `8`

## Escala de la interfaz (guiscale)
Devuelve la escala actual de la interfaz.
```
{"placeholder":"guiscale"}
```
Ejemplo de salida: `2`

## Etiqueta/texto de widget vanilla (vanillabuttonlabel)
Devuelve la etiqueta o texto de un widget/botón vanilla.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Ejemplo de salida: `Options...`

## Valor de un campo de texto (text_input_field_value)
Devuelve el valor actual de un campo de texto personalizado o vanilla mediante el identificador del elemento.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Ejemplo de salida: `Hello World`

## Salud actual del jugador (current_player_health)
Devuelve los puntos de salud actuales del jugador.
```
{"placeholder":"current_player_health"}
```
Ejemplo de salida: `20.0`

## Salud máxima del jugador (max_player_health)
Devuelve los puntos máximos de salud del jugador.
```
{"placeholder":"max_player_health"}
```
Ejemplo de salida: `20.0`

## Salud actual del jugador (porcentaje) (current_player_health_percent)
Devuelve la salud del jugador en porcentaje.
```
{"placeholder":"current_player_health_percent"}
```
Ejemplo de salida: `100`

## Salud de absorción actual del jugador (current_player_absorption_health)
Devuelve los puntos de salud por absorción del jugador (corazones dorados).
```
{"placeholder":"current_player_absorption_health"}
```
Ejemplo de salida: `4.0`

## Salud máxima de absorción del jugador (max_player_absorption_health)
Devuelve la salud máxima de absorción.
```
{"placeholder":"max_player_absorption_health"}
```
Ejemplo de salida: `4.0`

## Salud de absorción actual del jugador (porcentaje) (current_player_absorption_health_percent)
Devuelve la salud de absorción del jugador en porcentaje.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Ejemplo de salida: `100`

## Nivel de hambre actual del jugador (current_player_hunger)
Devuelve el nivel actual de hambre del jugador.
```
{"placeholder":"current_player_hunger"}
```
Ejemplo de salida: `20`

## Nivel máximo de hambre del jugador (max_player_hunger)
Devuelve el nivel máximo de hambre.
```
{"placeholder":"max_player_hunger"}
```
Ejemplo de salida: `20`

## Nivel de hambre actual del jugador (porcentaje) (current_player_hunger_percent)
Devuelve el hambre del jugador en porcentaje.
```
{"placeholder":"current_player_hunger_percent"}
```
Ejemplo de salida: `100`

## Saturación de hambre actual del jugador (current_player_hunger_saturation)
Devuelve el valor actual de saturación de hambre del jugador.
```
{"placeholder":"current_player_hunger_saturation"}
```
Ejemplo de salida: `5.0`

## Armadura actual del jugador (current_player_armor)
Devuelve el valor actual de armadura del jugador.
```
{"placeholder":"current_player_armor"}
```
Ejemplo de salida: `20`

## Dureza de armadura del jugador (player_armor_toughness)
Devuelve el valor total de dureza de armadura del jugador.
```
{"placeholder":"player_armor_toughness"}
```
Ejemplo de salida: `8.0`

## Armadura máxima del jugador (max_player_armor)
Devuelve el valor máximo de armadura.
```
{"placeholder":"max_player_armor"}
```
Ejemplo de salida: `20`

## Armadura actual del jugador (porcentaje) (current_player_armor_percent)
Devuelve la armadura del jugador en porcentaje.
```
{"placeholder":"current_player_armor_percent"}
```
Ejemplo de salida: `100`

## Nivel de oxígeno actual del jugador (current_player_oxygen)
Devuelve el nivel actual de oxígeno del jugador (burbujas de aire).
```
{"placeholder":"current_player_oxygen"}
```
Ejemplo de salida: `300`

## Nivel máximo de oxígeno del jugador (max_player_oxygen)
Devuelve el nivel máximo de oxígeno.
```
{"placeholder":"max_player_oxygen"}
```
Ejemplo de salida: `300`

## Nivel de oxígeno actual del jugador (porcentaje) (current_player_oxygen_percent)
Devuelve el nivel de oxígeno del jugador en porcentaje.
```
{"placeholder":"current_player_oxygen_percent"}
```
Ejemplo de salida: `100`

## Nivel actual del jugador (current_player_level)
Devuelve el nivel de experiencia actual del jugador.
```
{"placeholder":"current_player_level"}
```
Ejemplo de salida: `30`

## Experiencia actual del jugador (current_player_exp)
Devuelve los puntos totales de experiencia del jugador.
```
{"placeholder":"current_player_exp"}
```
Ejemplo de salida: `1250`

## Progreso de experiencia del jugador (porcentaje) (current_player_exp_progress)
Devuelve el progreso de experiencia del jugador hacia el siguiente nivel en porcentaje.
```
{"placeholder":"current_player_exp_progress"}
```
Ejemplo de salida: `75`

## Fuerza de ataque del jugador (porcentaje) (player_attack_strength)
Devuelve el enfriamiento del ataque del jugador en porcentaje.
```
{"placeholder":"player_attack_strength"}
```
Ejemplo de salida: `100`

## Modo de juego del jugador (player_gamemode)
Devuelve el modo de juego actual del jugador.
```
{"placeholder":"player_gamemode"}
```
Ejemplo de salida: `survival`

## Dirección de vista del jugador (player_view_direction)
Devuelve la dirección hacia la que está mirando el jugador.
```
{"placeholder":"player_view_direction"}
```
Ejemplo de salida: `north`

## Coordenada X del jugador (player_x_coordinate)
Devuelve la posición X del jugador en el mundo.
```
{"placeholder":"player_x_coordinate"}
```
Ejemplo de salida: `125`

## Coordenada Y del jugador (player_y_coordinate)
Devuelve la posición Y del jugador en el mundo.
```
{"placeholder":"player_y_coordinate"}
```
Ejemplo de salida: `64`

## Coordenada Z del jugador (player_z_coordinate)
Devuelve la posición Z del jugador en el mundo.
```
{"placeholder":"player_z_coordinate"}
```
Ejemplo de salida: `-250`

## Salud actual de la montura (current_mount_health)
Devuelve la salud actual de la entidad que el jugador está montando.
```
{"placeholder":"current_mount_health"}
```
Ejemplo de salida: `30.0`

## Salud máxima de la montura (max_mount_health)
Devuelve la salud máxima de la entidad que el jugador está montando.
```
{"placeholder":"max_mount_health"}
```
Ejemplo de salida: `30.0`

## Salud actual de la montura (porcentaje) (current_mount_health_percent)
Devuelve la salud de la montura en porcentaje.
```
{"placeholder":"current_mount_health_percent"}
```
Ejemplo de salida: `100`

## Medidor de salto actual de la montura (porcentaje) (current_mount_jump_meter)
Devuelve el valor del medidor de potencia de salto de la montura.
```
{"placeholder":"current_mount_jump_meter"}
```
Ejemplo de salida: `75`

## Salud actual del jefe (porcentaje) (current_boss_health)
Devuelve la salud del jefe activo.
```
{"placeholder":"current_boss_health"}
```
Ejemplo de salida: `150.0`

## Nombre del jefe (boss_name)
Devuelve el nombre del jefe activo.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Ejemplo de salida: `Ender Dragon`

## Cantidad de jefes (boss_count)
Devuelve el número de jefes activos.
```
{"placeholder":"boss_count"}
```
Ejemplo de salida: `1`

## Cantidad de efectos activos (effects_count)
Devuelve el número de efectos de poción activos.
```
{"placeholder":"effects_count"}
```
Ejemplo de salida: `3`

## Efecto activo (active_effect)
Devuelve información sobre un efecto activo específico.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Ejemplo de salida: `minecraft:speed`

## Ranura seleccionada de la barra rápida (active_hotbar_slot)
Devuelve la ranura de la barra rápida actualmente seleccionada (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Ejemplo de salida: `4`

## Objeto de la ranura (slot_item)
Devuelve información sobre un objeto en una ranura específica del inventario.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Ejemplo de salida: `minecraft:diamond_sword`

## Cantidad de objetos en la ranura (slot_item_count)
Devuelve el tamaño de la pila del objeto en una ranura específica del inventario del jugador.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Ejemplo de salida: `64`

## Durabilidad del objeto en la ranura (slot_item_durability)
Devuelve información de durabilidad del objeto en una ranura específica del inventario del jugador.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parámetros:
- `slot`: Número de ranura del inventario del jugador.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` o `percent`.

Ejemplo de salida: `87`

## Nombre mostrado del objeto en la ranura (slot_item_display_name_fm)
Devuelve el nombre mostrado del objeto en una ranura específica como un componente de texto JSON. En modo espectador, las ranuras de la barra rápida pueden resolver nombres de objetos del menú de espectador, a menos que `ignore_spectator` sea `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Ejemplo de salida: `{"text":"Diamond Sword","color":"aqua"}`

## Cantidad de objetos en el inventario (inventory_item_count)
Devuelve la cantidad total de un tipo de objeto en el inventario del jugador. Si `item` está vacío, cuenta todos los stacks de objetos en el inventario.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Ejemplo de salida: `12`

## Cantidad de restauración de hambre de un alimento en la ranura del inventario (inventory_slot_food_point_restore_amount)
Devuelve los puntos de hambre restaurados por el alimento en la ranura dada del inventario del jugador.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Ejemplo de salida: `4.0`

## Objeto del inventario bajo el cursor (hovered_inventory_item)
Devuelve la clave del objeto que está actualmente bajo el cursor en una pantalla de inventario.
```
{"placeholder":"hovered_inventory_item"}
```
Ejemplo de salida: `minecraft:apple`

## Tiempo del juego del mundo (game_time)
Devuelve el contador actual de ticks del tiempo en el juego.
```
{"placeholder":"game_time"}
```
Ejemplo de salida: `18000`

## Hora del día del mundo (world_daytime)
Devuelve la hora actual del día del mundo.
```
{"placeholder":"world_daytime"}
```
Ejemplo de salida: `13000`

## Hora del día del mundo (world_daytime_hour)
Devuelve el componente de hora del tiempo del mundo. De forma predeterminada usa formato de 24 horas; establece `twelve_hour_format` en `"true"` para formato de 12 horas.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Ejemplo de salida: `12`

## Minuto del día del mundo (world_daytime_minute)
Devuelve el componente de minuto del tiempo del mundo (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Ejemplo de salida: `30`

## Dificultad del mundo (world_difficulty)
Devuelve la dificultad actual del mundo.
```
{"placeholder":"world_difficulty"}
```
Ejemplo de salida: `normal`

## Semilla del mundo actual (current_world_seed)
Devuelve la semilla del mundo actual en un jugador. Devuelve un valor vacío cuando la semilla no está disponible.
```
{"placeholder":"current_world_seed"}
```
Ejemplo de salida: `123456789`

## Bioma actual (current_biome)
Devuelve el bioma en el que está actualmente el jugador. Establece `as_key` en `"false"` para devolver un nombre traducido/visible cuando esté disponible.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Ejemplo de salida: `minecraft:plains`

## Dimensión actual (current_dimension)
Devuelve la dimensión en la que está actualmente el jugador. Establece `as_key` en `"false"` para devolver un nombre traducido/visible cuando esté disponible.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Ejemplo de salida: `minecraft:overworld`

## Valor de gamerule (gamerule_value)
Devuelve el valor actual de una gamerule en el mundo/servidor cargado. Los mundos de servidor requieren FancyMenu en el servidor.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Ejemplo de salida: `true`

## Categoría del objeto (item_category)
Devuelve la pestaña creativa a la que pertenece un objeto. Establece `as_key` en `"true"` para devolver la clave de la categoría en lugar del nombre visible.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Ejemplo de salida: `Combat`

## Título/Subtítulo HUD actual (current_title)
Devuelve el texto del título que se muestra actualmente.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Ejemplo de salida: `Game Over!`

## Mensaje de la barra de acción (action_bar_message_fm)
Devuelve el mensaje actual de la barra de acción vanilla encima de la barra rápida.
```
{"placeholder":"action_bar_message_fm"}
```
Ejemplo de salida: `You may not rest now`

## Tiempo del mensaje de la barra de acción (action_bar_message_time_fm)
Devuelve cuántos ticks más se seguirá mostrando el mensaje actual de la barra de acción vanilla.
```
{"placeholder":"action_bar_message_time_fm"}
```
Ejemplo de salida: `42`

## Rotación X de la cámara (camera_rotation_x_fm)
Devuelve el pitch actual de la cámara en grados.
```
{"placeholder":"camera_rotation_x_fm"}
```
Ejemplo de salida: `12.5`

## Rotación Y de la cámara (camera_rotation_y_fm)
Devuelve el yaw actual de la cámara en grados.
```
{"placeholder":"camera_rotation_y_fm"}
```
Ejemplo de salida: `-90.0`

## Delta de rotación X de la cámara (camera_rotation_delta_x_fm)
Devuelve el cambio por tick del pitch de la cámara.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Ejemplo de salida: `0.4`

## Delta de rotación Y de la cámara (camera_rotation_delta_y_fm)
Devuelve el cambio por tick del yaw de la cámara.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Ejemplo de salida: `-1.2`

## Tiempo del objeto resaltado (highlighted_item_time_fm)
Devuelve cuántos ticks más se seguirá mostrando el nombre del objeto resaltado encima de la barra rápida.
```
{"placeholder":"highlighted_item_time_fm"}
```
Ejemplo de salida: `30`

## Progreso de uso de objeto del jugador (player_item_use_progress_fm)
Devuelve el progreso actual de uso del objeto de `0.0` a `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Ejemplo de salida: `0.65`

## Delta de posición X del jugador (player_position_delta_x_fm)
Devuelve el cambio por tick de la posición del jugador en el eje X.
```
{"placeholder":"player_position_delta_x_fm"}
```
Ejemplo de salida: `0.0`

## Delta de posición Y del jugador (player_position_delta_y_fm)
Devuelve el cambio por tick de la posición del jugador en el eje Y.
```
{"placeholder":"player_position_delta_y_fm"}
```
Ejemplo de salida: `-0.08`

## Delta de posición Z del jugador (player_position_delta_z_fm)
Devuelve el cambio por tick de la posición del jugador en el eje Z.
```
{"placeholder":"player_position_delta_z_fm"}
```
Ejemplo de salida: `0.12`

## IP actual del servidor (current_server_ip)
Devuelve la IP del servidor conectado.
```
{"placeholder":"current_server_ip"}
```
Ejemplo de salida: `mc.hypixel.net`

## Lista de jugadores del mundo (world_players_list)
Devuelve una lista de todos los jugadores que están actualmente en el mundo.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Ejemplo de salida: `Steve, Alex, Notch`

## MOTD del servidor (servermotd)
Devuelve el Message of the Day de un servidor.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Ejemplo de salida: `Welcome to Hypixel!`

## PING del servidor (serverping)
Devuelve la latencia a un servidor en milisegundos.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Ejemplo de salida: `54`

## Cantidad de jugadores del servidor (serverplayercount)
Devuelve la cantidad de jugadores de un servidor.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Ejemplo de salida: `25000/30000`

## Estado del servidor (serverstatus)
Devuelve el estado en línea/fuera de línea de un servidor.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Ejemplo de salida: `§aOnline` o `§cOffline`

## Versión del servidor (serverversion)
Devuelve la versión de Minecraft de un servidor.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Ejemplo de salida: `1.19.2`

## Año (realtimeyear)
Devuelve el año actual.
```
{"placeholder":"realtimeyear"}
```
Ejemplo de salida: `2024`

## Mes (realtimemonth)
Devuelve el mes actual (01-12).
```
{"placeholder":"realtimemonth"}
```
Ejemplo de salida: `01`

## Día (realtimeday)
Devuelve el día actual del mes (01-31).
```
{"placeholder":"realtimeday"}
```
Ejemplo de salida: `27`

## Hora (realtimehour)
Devuelve la hora actual. De forma predeterminada usa formato de 24 horas; establece `twelve_hour_format` en `"true"` para formato de 12 horas.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Ejemplo de salida: `14`

## Minuto (realtimeminute)
Devuelve el minuto actual (00-59).
```
{"placeholder":"realtimeminute"}
```
Ejemplo de salida: `30`

## Segundo (realtimesecond)
Devuelve el segundo actual (00-59).
```
{"placeholder":"realtimesecond"}
```
Ejemplo de salida: `45`

## Tiempo actual en milisegundos (marca de tiempo Unix) (unix_time)
Devuelve la marca de tiempo Unix actual en milisegundos.
```
{"placeholder":"unix_time"}
```
Ejemplo de salida: `1716552478123`

> Los marcadores de posición de tiempo real (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` y `unix_time`) admiten un valor `timezone`. Usa identificadores normales de zona horaria de Java como `UTC`, `Europe/Berlin` o `America/New_York`; omítelo o usa `system` para la zona horaria del sistema.
{.is-info}

## Información de CPU (cpuinfo)
Devuelve información sobre la CPU.
```
{"placeholder":"cpuinfo"}
```
Ejemplo de salida: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Uso de CPU (JVM) (jvmcpu)
Devuelve el uso de CPU de la JVM en porcentaje.
```
{"placeholder":"jvmcpu"}
```
Ejemplo de salida: `25.5`

## Uso de CPU (SO) (oscpu)
Devuelve el uso de CPU del sistema operativo en porcentaje.
```
{"placeholder":"oscpu"}
```
Ejemplo de salida: `42.8`

## Información de GPU (gpuinfo)
Devuelve información sobre la GPU.
```
{"placeholder":"gpuinfo"}
```
Ejemplo de salida: `NVIDIA GeForce RTX 3080`

## Versión de Java (javaver)
Devuelve la versión de Java.
```
{"placeholder":"javaver"}
```
Ejemplo de salida: `17.0.2`

## Máquina virtual de Java (jvmname)
Devuelve el nombre de la Máquina Virtual de Java.
```
{"placeholder":"jvmname"}
```
Ejemplo de salida: `OpenJDK 64-Bit Server VM`

## Versión de OpenGL (glver)
Devuelve la versión de OpenGL.
```
{"placeholder":"glver"}
```
Ejemplo de salida: `4.6.0 NVIDIA 516.94`

## Nombre del sistema operativo (osname)
Devuelve el nombre del sistema operativo.
```
{"placeholder":"osname"}
```
Ejemplo de salida: `Windows 10`

## FPS (fotogramas por segundo) (fps)
Devuelve los fotogramas por segundo actuales.
```
{"placeholder":"fps"}
```
Ejemplo de salida: `120`

## RAM usada en MB (usedram)
Devuelve la cantidad de RAM que se está usando actualmente (MB).
```
{"placeholder":"usedram"}
```
Ejemplo de salida: `4096`

## RAM máxima en MB (maxram)
Devuelve la RAM máxima asignada (MB).
```
{"placeholder":"maxram"}
```
Ejemplo de salida: `8192`

## RAM usada en %% (percentram)
Devuelve el porcentaje de RAM que se está usando actualmente.
```
{"placeholder":"percentram"}
```
Ejemplo de salida: `50`

## Volumen de un elemento de audio (audio_element_vol)
Devuelve el volumen de un elemento de audio.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Ejemplo de salida: `0.5`

## Pista de audio actual (audio_element_current_track)
Devuelve el nombre de la pista de un elemento de audio.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Ejemplo de salida: `Cool Track Name`

## Duración del audio (audio_duration)
Devuelve la duración total de una pista de audio en formato MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Ejemplo de salida: `03:45`

## Tiempo de reproducción del audio (audio_playtime)
Devuelve el tiempo de reproducción actual de una pista de audio. Establece `show_percentage` en `"true"` para obtener un valor de progreso de 0-100 en lugar de `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Ejemplo de salida: `01:30` (o `45` cuando `show_percentage` es `"true"`)

## Estado de reproducción del audio (audio_playing_state)
Devuelve si un elemento de audio se está reproduciendo (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Ejemplo de salida: `true`

## Volumen de un elemento de video (video_element_vol)
Devuelve el nivel de volumen de un elemento de video (0.0 a 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Ejemplo de salida: `0.5`

## Duración de un elemento de video (video_element_duration)
Devuelve la duración total de un elemento de video en formato `MM:SS`. Establece `output_as_timestamp` en `"true"` para devolver una marca de tiempo en milisegundos.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Ejemplo de salida: `02:00` (o `120000` cuando `output_as_timestamp` es `"true"`)

## Tiempo de reproducción de un elemento de video (video_element_playtime)
Devuelve el tiempo de reproducción actual (progreso) de un elemento de video en formato `MM:SS`. Establece `show_percentage` en `"true"` para un valor de progreso de 0-100, o `output_as_timestamp` en `"true"` para milisegundos.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Ejemplo de salida: `00:45` (o `38` como porcentaje, o `45200` como marca de tiempo)

## Estado de pausa de un elemento de video (video_element_paused_state)
Devuelve si un elemento de video está en pausa (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Ejemplo de salida: `false`

## Volumen del fondo de video (video_background_vol)
Devuelve el nivel de volumen de un fondo de video del menú (0.0 a 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Ejemplo de salida: `0.7`

## Duración del fondo de video (video_background_duration)
Devuelve la duración total de un fondo de video del menú en formato `MM:SS`. Establece `output_as_timestamp` en `"true"` para devolver una marca de tiempo en milisegundos.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Ejemplo de salida: `03:00` (o `180000` cuando `output_as_timestamp` es `"true"`)

## Tiempo de reproducción del fondo de video (video_background_playtime)
Devuelve el tiempo de reproducción actual (progreso) de un fondo de video del menú en formato `MM:SS`. Establece `show_percentage` en `"true"` para un valor de progreso de 0-100, o `output_as_timestamp` en `"true"` para milisegundos.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Ejemplo de salida: `01:00` (o `33` como porcentaje, o `60500` como marca de tiempo)

## Estado de pausa del fondo de video (video_background_paused_state)
Devuelve si un fondo de video del menú está en pausa (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Ejemplo de salida: `true`

## Calculadora (calc)
El marcador de posición de calculadora es una herramienta poderosa que te permite realizar cálculos matemáticos dentro de tus diseños. Admite una amplia gama de operaciones matemáticas y puede trabajar tanto con números decimales como enteros.

### Sintaxis básica
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"tu_expresion"}}
```

La calculadora tiene dos parámetros principales:
- `decimal`: Determina si el resultado debe incluir decimales (`true`) o redondearse a enteros (`false`)
- `expression`: La expresión matemática que se evaluará

### Operaciones admitidas
La calculadora admite estas operaciones matemáticas:
- Aritmética básica: `+` (suma), `-` (resta), `*` (multiplicación), `/` (división)
- Paréntesis: `( )` para agrupar operaciones
- Potencia: `^` para exponentes
- Raíz cuadrada: `sqrt()`
- Funciones trigonométricas: `sin()`, `cos()`, `tan()`
- Constantes matemáticas: `pi`, `e`
- Valor absoluto: `abs()`
- Logaritmos: `log()`, `ln()`

## Número aleatorio (random_number)
Genera un número aleatorio dentro de un rango especificado.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Ejemplo de salida: `42`

## Número máximo (maxnum)
Devuelve el mayor de dos números.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Ejemplo de salida: `20`

## Número mínimo (minnum)
Devuelve el menor de dos números.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Ejemplo de salida: `10`

## Número absoluto (absnum)
Devuelve el valor absoluto de un número.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Ejemplo de salida: `10.5`

## Negar número (negnum)
Devuelve el valor negado de un número.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Ejemplo de salida: `-10.5`

## *pi* (Matemáticas) (math_pi)
Devuelve el valor de π.
```
{"placeholder":"math_pi"}
```
Ejemplo de salida: `3.141592653589793`

## Seno trigonométrico (Matemáticas) (math_sin)
Devuelve el seno de un ángulo.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Ejemplo de salida: `0.7071067811865476`

## Coseno trigonométrico (Matemáticas) (math_cos)
Devuelve el coseno de un ángulo.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Ejemplo de salida: `0.7071067811865476`

## Tangente trigonométrica (Matemáticas) (math_tan)
Devuelve la tangente de un ángulo.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Ejemplo de salida: `1.0`

## Piso (Matemáticas) (math_floor)
Redondea un número hacia abajo al entero más cercano.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Ejemplo de salida: `3`

## Techo (Matemáticas) (math_ceil)
Redondea un número hacia arriba al entero más cercano.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Ejemplo de salida: `4`

## Redondear (Matemáticas) (math_round)
Redondea un número. De forma predeterminada redondea al entero más cercano; establece `decimals` en un número no negativo para redondear a esa cantidad de decimales.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Ejemplo de salida: `3.14` (con `decimals:-1` o si se omite → `3`)

## Signo (Matemáticas) (math_sign)
Devuelve el signo de un número (1 para positivo, -1 para negativo, 0 para cero).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Ejemplo de salida: `-1`

## Seno hiperbólico (Matemáticas) (math_sinh)
Devuelve el seno hiperbólico de un ángulo.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Ejemplo de salida: `1.1752011936438014`

## Coseno hiperbólico (Matemáticas) (math_cosh)
Devuelve el coseno hiperbólico de un ángulo.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Ejemplo de salida: `1.5430806348152437`

## Tangente hiperbólica (Matemáticas) (math_tanh)
Devuelve la tangente hiperbólica de un ángulo.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Ejemplo de salida: `0.7615941559557649`

## Dividir texto (split_text)
Divide texto usando un delimitador especificado.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Ejemplo de salida: `world`

## Recortar texto (trim_text)
Elimina espacios en blanco al inicio y al final.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Ejemplo de salida: `hello world`

## Cortar texto (crop_text)
Elimina caracteres del inicio y del final del texto.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Ejemplo de salida: `ello worl`

## Convertir a cadena (stringify)
Convierte un texto en cadena escapando todos los caracteres de sintaxis.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Ejemplo de salida: `text with \{special\} \"characters\"`

## Localizar texto (local)
Recupera texto localizado para una clave.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Ejemplo de salida: `Singleplayer`

## Texto web (webtext)
Recupera contenido de texto desde una URL web.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Ejemplo de salida: Contenido de texto desde la URL

## Texto aleatorio (randomtext)
Devuelve una línea aleatoria de un archivo de texto, una URL o texto plano directo. El texto cambia en intervalos especificados.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parámetros:
- `source`: La fuente de las líneas de texto (reemplaza el parámetro `path` anterior)
  - Ruta de archivo: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Texto plano: `Line 1\nLine 2\nLine 3`
- `interval`: Tiempo en segundos entre cambios de texto

El marcador de posición ahora admite tres tipos de fuente:
1. **Archivos locales**: Archivos de texto desde tu directorio del juego
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: Archivos de texto remotos desde internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texto plano**: Entrada de texto directa con líneas separadas por `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Nota: Los marcadores de posición antiguos que usan `path` en lugar de `source` seguirán funcionando.

## Analizador JSON (json)
Analiza datos JSON desde un archivo, una URL o contenido JSON directo y extrae valores usando expresiones JSONPath.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parámetros:
- `source`: La fuente de los datos JSON
  - Ruta de archivo: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - JSON directo: `{"name":"Steve","level":42}`
- `json_path`: La expresión JSONPath para extraer datos

El marcador de posición ahora admite tres tipos de fuente:
1. **Archivos locales**: Archivos JSON desde tu directorio del juego
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: Datos JSON remotos desde APIs o servicios web
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON directo**: Contenido JSON en línea
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Ejemplos de JSONPath:
- `$.name` - Obtiene el campo "name" desde la raíz
- `$.player.level` - Obtiene el campo anidado "level" dentro de "player"
- `$.items[0].id` - Obtiene el "id" del primer elemento de un arreglo
- `$.scores.*` - Obtiene todos los valores del objeto "scores"

## Ruta absoluta de archivo/carpeta (absolute_path)
Devuelve la ruta absoluta de un archivo.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Ejemplo de salida: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Conteo de caracteres de texto (text_character_count)
Devuelve el número de caracteres en el texto dado.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Ejemplo de salida: `12`

## Ancho del texto (text_width)
Devuelve el ancho en píxeles del texto dado al renderizarse.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Ejemplo de salida: `66`

## Texto en mayúsculas (uppercase_text)
Convierte el texto de entrada a todas mayúsculas.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Ejemplo de salida: `HELLO WORLD`

## Texto en minúsculas (lowercase_text)
Convierte el texto de entrada a todas minúsculas.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Ejemplo de salida: `hello world`

## Texto en formato de título (title_case_text)
Convierte el texto de entrada a formato de título.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Ejemplo de salida: `Hello World`

## Texto en formato de oración (sentence_case_text)
Convierte el texto de entrada a formato de oración.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Ejemplo de salida: `Hello world. This is fancymenu!`

## Texto en snake_case (snake_case_text)
Convierte el texto de entrada a `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Ejemplo de salida: `hello_world`

## Texto en kebab-case (kebab_case_text)
Convierte el texto de entrada a `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Ejemplo de salida: `hello-world`

## Texto en mayúsculas y minúsculas alternadas (alternating_case_text)
Convierte el texto de entrada a mayúsculas y minúsculas alternadas.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Ejemplo de salida: `aLtErNaTiNg CaSe`

## Alternar mayúsculas/minúsculas (toggle_case_text)
Alterna el uso de mayúsculas y minúsculas de cada letra en el texto de entrada.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Ejemplo de salida: `tOGGLE cASE`

## Codificar a Base64 (base64_encode)
Codifica el texto dado como Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Ejemplo de salida: `SGVsbG8gV29ybGQ=`

## Decodificar desde Base64 (base64_decode)
Decodifica una cadena Base64 de vuelta a texto plano.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Ejemplo de salida: `Hello World`

## Texto de archivo (file_text)
Devuelve líneas de texto desde un archivo o URL. Puede devolver todas las líneas o solo las últimas X líneas.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parámetros:
- `path_or_url`: Ruta de archivo o URL desde donde leer
- `mode`: Puede ser `"all"` (devuelve todas las líneas) o `"last"` (devuelve solo las últimas X líneas)
- `separator`: Texto con el que se unirán las líneas (predeterminado: `"\n"`)
- `last_lines`: Número de líneas a devolver cuando el modo es `"last"` (predeterminado: `"1"`)

Ejemplo de salida: Depende del contenido del archivo

## Contenido del portapapeles (clipboard_content)
Devuelve el contenido de texto actual almacenado en el portapapeles del sistema.
```
{"placeholder":"clipboard_content"}
```
Ejemplo de salida: Cualquier texto que esté actualmente en el portapapeles

## Reemplazar texto (replace_text)
Reemplaza texto en una cadena usando texto literal o expresiones regulares.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parámetros:
- `text`: El texto de entrada a procesar
- `search`: El texto o patrón regex a buscar
- `replacement`: El texto de reemplazo
- `use_regex`: Si se usa regex (`"true"`) o coincidencia literal (`"false"`)
- `replace_all`: Reemplaza todas las coincidencias (`"true"`) o solo la primera (`"false"`)

Ejemplo de salida: `Hello FancyMenu! This is a test.`

## Cambiar según caso (switch_case)
Realiza una operación tipo switch-case según un valor.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Ejemplo de salida: `first case` (si el valor es 1)

## Obtener valor de variable (Variable de FM) (getvariable)
Recupera el valor de una variable almacenada previamente.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Ejemplo de salida: Depende del valor almacenado

## Obtener datos NBT (nbt_data_get)
Recupera datos NBT en el cliente (similar al comando `/data get`). Usa la variante del servidor `nbt_data_get_server` cuando estés conectado a un servidor y necesites valores autoritativos del lado del servidor.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parámetros:
- `source_type`: Puede ser `"entity"` o `"block"`
- `entity_selector`: Selector de entidad como `@s`, `@p`, `@e`, o UUID/nombre (para entidades)
- `block_pos`: Posición del bloque en formato `"x y z"` (para bloques)
- `nbt_path`: La ruta NBT que se va a recuperar
- `scale`: Factor de escala opcional para valores numéricos (predeterminado: `"1.0"`)
- `return_type`: Cómo devolver los datos:
  - `"value"`: Predeterminado, devuelve el valor (con escalado opcional para números)
  - `"string"`: Devuelve los datos NBT reales como cadena
  - `"snbt"`: Devuelve SNBT (NBT formateado)
  - `"json"`: Devuelve como componente formateado en JSON (para etiquetas compuestas)

Ejemplo de salida: `20` (para nivel de hambre)

## Obtener datos NBT (lado del servidor) (nbt_data_get_server)
Consulta datos NBT del lado del servidor (usando un paquete) y almacena en caché los resultados por un momento. Los valores son equivalentes al marcador de posición del lado del cliente.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Ejemplo de salida: `minecraft:diamond_sword`

## Último mensaje de muerte (lastdeathmessage)
Devuelve el último mensaje de muerte registrado del jugador cliente. Establece `as_json_component` en `"true"` para obtener el componente de texto JSON sin procesar.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Ejemplo de salida: `Steve was slain by Zombie`

## Duración de actividad (uptime_duration)
Devuelve cuánto tiempo ha estado cargado FancyMenu. De forma predeterminada el valor está en segundos; establece `output_as_millis` en `"true"` para recibir milisegundos.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Ejemplo de salida: `742` (segundos desde la carga)

## Nombres de guardados del mundo (level_save_names)
Enumera todos los nombres de guardados de mundos locales unidos por el separador elegido. Se ejecuta en el hilo del cliente.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Ejemplo de salida: `Creative Test, Survival World, Hardcore`

## Datos de guardado del mundo (level_save_data)
Devuelve datos serializados de nivel para el nombre de mundo dado (debe coincidir con el nombre visible mostrado en la lista de guardados).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Ejemplo de salida: `{"name":"Survival World","gameMode":"survival",...}`

## Convertidor de base numérica (number_base_convert)
Convierte un número (entero o fraccionario) de una base a otra (2–36). Usa decimal por defecto si no se proporcionan bases.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Ejemplo de salida: `43.8`

## Tamaño de archivo (file_size)
Devuelve el tamaño de un archivo local en bytes. Solo se permiten rutas locales.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Ejemplo de salida: `1284`

## MD5 de archivo (file_md5)
Devuelve el hash MD5 de un archivo local como una cadena hexadecimal en minúsculas.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Ejemplo de salida: `d41d8cd98f00b204e9800998ecf8427e`

# Ejemplos prácticos

## Crear una visualización dinámica de memoria
```
RAM usada: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Hacer un reloj en tiempo real
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Crear una visualización de información del sistema
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

1. **Cacha operaciones costosas**: Algunos marcadores de posición (como los que leen información del sistema) pueden consumir muchos recursos. Considera usar variables para almacenar sus valores si necesitas usarlos varias veces.

2. **Usa ajustes de decimales apropiados**: Al trabajar con cálculos, usa el parámetro `decimal` de manera adecuada. Ponlo en `false` cuando necesites enteros y en `true` cuando necesites valores decimales precisos.

3. **Maneja valores faltantes**: Siempre considera qué debe pasar si un marcador de posición no devuelve ningún valor. Quizá quieras proporcionar valores predeterminados en esos casos.

4. **Prueba el rendimiento**: Cuando uses muchos marcadores de posición o estructuras anidadas complejas, prueba el impacto en el rendimiento, especialmente en sistemas de gama baja.

5. **Usa dimensionamiento/posicionamiento avanzado**: Para elementos dinámicos de la interfaz, combina marcadores de posición con dimensionamiento y posicionamiento avanzados para crear diseños responsivos.

6. **Combínalos con variables**: Usa marcadores de posición junto con variables para obtener contenido aún más dinámico que pueda actualizarse mediante acciones.

# Problemas comunes y soluciones

## El marcador de posición no se actualiza
Si el valor de un marcador de posición no se actualiza como esperas, revisa:
- Si el marcador de posición está formateado correctamente
- Si estás usando el caso correcto para los IDs de los marcadores de posición
- Si el marcador de posición requiere condiciones específicas para actualizarse

## Los marcadores de posición anidados no funcionan
Al anidar marcadores de posición:
- Asegúrate de escapar correctamente las comillas
- Verifica que cada marcador de posición anidado sea válido por sí mismo

## Problemas de rendimiento
Si notas problemas de rendimiento:
- Reduce la cantidad de marcadores de posición usados
- Evita el anidamiento innecesario
- Considera usar variables para valores a los que accedes con frecuencia
- Usa el marcador de posición adecuado para lo que necesitas (por ejemplo, no uses marcadores de tiempo en tiempo real cuando basten valores estáticos)
