---
title: Marcadores de posición
description: Cómo usar marcadores de posición.
---
# Marcadores de posición

Los marcadores de posición son valores dinámicos que se reemplazan con contenido real cuando se usan. En FancyMenu, los marcadores de posición te permiten insertar contenido dinámico en varios elementos como texto, botones y requisitos de carga. Piénsalos como variables que se evalúan y se reemplazan por sus valores reales cuando se muestran tus diseños.

# Información general

## Sintaxis básica
Los marcadores de posición en FancyMenu usan una sintaxis parecida a JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Por ejemplo, para mostrar el nombre del jugador:
```
{"placeholder":"playername"}
```

## Marcadores de posición anidados
Una de las funciones más potentes del sistema de marcadores de posición de FancyMenu es que puedes anidarlos dentro de otros marcadores de posición. Esto significa que puedes usar la salida de un marcador de posición como entrada de otro.

Ejemplo de marcadores de posición anidados:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Este ejemplo toma el valor máximo de RAM y lo divide entre 1024 para convertirlo de MB a GB.

> [!IMPORTANT]
> A diferencia del JSON real, los marcadores de posición anidados **no** se **escapan** usando `\`. Esto es muy importante, porque los marcadores de posición dejarán de funcionar cuando se escapen (obviamente). Los marcadores de posición solo usan una sintaxis parecida a JSON. No son JSON real.

# Uso de marcadores de posición

La mayoría de los elementos que tienen entradas de texto admiten marcadores de posición. Puedes ver si una entrada de texto los admite al editarla. Si al editar el texto se abre el **editor de texto** de pantalla completa, entonces admite marcadores de posición.

Para encontrar una **lista de todos los marcadores de posición**, solo haz clic en el botón **Marcadores de posición** en la **esquina superior derecha** del **editor de texto**.

Hay una **barra de búsqueda** en la parte superior de la lista de marcadores de posición que te permite buscarlos.

Al hacer clic en un marcador de posición en la lista, se pegará en el contenido de texto.

# Marcadores de posición en detalle

Esta lista contiene la mayoría, si no es que todos, los marcadores de posición disponibles en FancyMenu. La lista puede quedar un poco desactualizada debido a actualizaciones del mod.

## Nombre del jugador (playername)
Devuelve el nombre de usuario del jugador actual.
```
{"placeholder":"playername"}
```
Salida de ejemplo: `Steve`

## UUID del jugador (playeruuid)
Devuelve el identificador único del jugador.
```
{"placeholder":"playeruuid"}
```
Salida de ejemplo: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Versión de Minecraft (mcversion)
Devuelve la versión actual de Minecraft.
```
{"placeholder":"mcversion"}
```
Salida de ejemplo: `1.19.2`

## Versión del cargador de mods (loaderver)
Devuelve la versión del cargador de mods (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Salida de ejemplo: `43.2.0`

## Nombre del cargador de mods (loadername)
Devuelve el nombre del cargador de mods.
```
{"placeholder":"loadername"}
```
Salida de ejemplo: `Forge`

## Versión del mod (modversion)
Devuelve la versión de un mod específico.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Salida de ejemplo: `2.14.9`

## Conteo total de mods (totalmods)
Devuelve el número total de mods instalados.
```
{"placeholder":"totalmods"}
```
Salida de ejemplo: `45`

## Conteo de mods activos (loadedmods)
Devuelve el número de mods cargados actualmente.
```
{"placeholder":"loadedmods"}
```
Salida de ejemplo: `43`

## Progreso de carga del mundo (world_load_progress)
Devuelve el progreso actual de carga del mundo como porcentaje.
```
{"placeholder":"world_load_progress"}
```
Salida de ejemplo: `75`

## Valor de opción de Minecraft (minecraft_option_value)
Devuelve el valor de una opción de Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Salida de ejemplo: `70`

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
- `full_world_path`: Controla cómo se muestran las rutas de los mundos
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
Salida de ejemplo: `1920`

## Alto de la pantalla (guiheight)
Devuelve el alto actual de la pantalla.
```
{"placeholder":"guiheight"}
```
Salida de ejemplo: `1080`

## Identificador de la pantalla actual (screenid)
Devuelve el identificador de la pantalla actual.
```
{"placeholder":"screenid"}
```
Salida de ejemplo: `title_screen`

## Ancho del elemento (elementwidth)
Devuelve el ancho de un elemento específico.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Salida de ejemplo: `200`

## Alto del elemento (elementheight)
Devuelve el alto de un elemento específico.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Salida de ejemplo: `20`

## Posición X del elemento (elementposx)
Devuelve la posición X de un elemento específico.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Salida de ejemplo: `150`

## Posición Y del elemento (elementposy)
Devuelve la posición Y de un elemento específico.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Salida de ejemplo: `100`

## Posición X del mouse (mouseposx)
Devuelve la posición X actual del mouse.
```
{"placeholder":"mouseposx"}
```
Salida de ejemplo: `960`

## Posición Y del mouse (mouseposy)
Devuelve la posición Y actual del mouse.
```
{"placeholder":"mouseposy"}
```
Salida de ejemplo: `540`

## Clics por segundo (clicks_per_second)
Devuelve los clics por segundo actuales para un botón del mouse.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parámetros:
- `mouse_button`: `left` o `right`

Salida de ejemplo: `8`

## Escala de la interfaz (guiscale)
Devuelve la escala actual de la interfaz.
```
{"placeholder":"guiscale"}
```
Salida de ejemplo: `2`

## Etiqueta/texto de widget vanilla (vanillabuttonlabel)
Devuelve la etiqueta o texto de un widget/botón vanilla.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Salida de ejemplo: `Options...`

## Valor de campo de entrada de texto (text_input_field_value)
Devuelve el valor actual de un campo de entrada de texto personalizado o vanilla por identificador de elemento.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Salida de ejemplo: `Hello World`

## Salud actual del jugador (current_player_health)
Devuelve los puntos de salud actuales del jugador.
```
{"placeholder":"current_player_health"}
```
Salida de ejemplo: `20.0`

## Salud máxima del jugador (max_player_health)
Devuelve los puntos máximos de salud del jugador.
```
{"placeholder":"max_player_health"}
```
Salida de ejemplo: `20.0`

## Salud actual del jugador (porcentaje) (current_player_health_percent)
Devuelve la salud del jugador como porcentaje.
```
{"placeholder":"current_player_health_percent"}
```
Salida de ejemplo: `100`

## Salud de absorción actual del jugador (current_player_absorption_health)
Devuelve los puntos de salud de absorción del jugador (corazones dorados).
```
{"placeholder":"current_player_absorption_health"}
```
Salida de ejemplo: `4.0`

## Salud máxima de absorción del jugador (max_player_absorption_health)
Devuelve la salud máxima de absorción.
```
{"placeholder":"max_player_absorption_health"}
```
Salida de ejemplo: `4.0`

## Salud de absorción actual del jugador (porcentaje) (current_player_absorption_health_percent)
Devuelve la salud de absorción del jugador como porcentaje.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Salida de ejemplo: `100`

## Nivel de hambre actual del jugador (current_player_hunger)
Devuelve el nivel actual de hambre del jugador.
```
{"placeholder":"current_player_hunger"}
```
Salida de ejemplo: `20`

## Nivel máximo de hambre del jugador (max_player_hunger)
Devuelve el nivel máximo de hambre.
```
{"placeholder":"max_player_hunger"}
```
Salida de ejemplo: `20`

## Nivel de hambre actual del jugador (porcentaje) (current_player_hunger_percent)
Devuelve el hambre del jugador como porcentaje.
```
{"placeholder":"current_player_hunger_percent"}
```
Salida de ejemplo: `100`

## Saturación de hambre actual del jugador (current_player_hunger_saturation)
Devuelve el valor actual de saturación de hambre del jugador.
```
{"placeholder":"current_player_hunger_saturation"}
```
Salida de ejemplo: `5.0`

## Armadura actual del jugador (current_player_armor)
Devuelve el valor actual de armadura del jugador.
```
{"placeholder":"current_player_armor"}
```
Salida de ejemplo: `20`

## Dureza de la armadura del jugador (player_armor_toughness)
Devuelve el valor total de dureza de la armadura del jugador.
```
{"placeholder":"player_armor_toughness"}
```
Salida de ejemplo: `8.0`

## Armadura máxima del jugador (max_player_armor)
Devuelve el valor máximo de armadura.
```
{"placeholder":"max_player_armor"}
```
Salida de ejemplo: `20`

## Armadura actual del jugador (porcentaje) (current_player_armor_percent)
Devuelve la armadura del jugador como porcentaje.
```
{"placeholder":"current_player_armor_percent"}
```
Salida de ejemplo: `100`

## Nivel de oxígeno actual del jugador (current_player_oxygen)
Devuelve el nivel actual de oxígeno del jugador (burbujas de aire).
```
{"placeholder":"current_player_oxygen"}
```
Salida de ejemplo: `300`

## Nivel máximo de oxígeno del jugador (max_player_oxygen)
Devuelve el nivel máximo de oxígeno.
```
{"placeholder":"max_player_oxygen"}
```
Salida de ejemplo: `300`

## Nivel de oxígeno actual del jugador (porcentaje) (current_player_oxygen_percent)
Devuelve el nivel de oxígeno del jugador como porcentaje.
```
{"placeholder":"current_player_oxygen_percent"}
```
Salida de ejemplo: `100`

## Nivel actual del jugador (current_player_level)
Devuelve el nivel de experiencia actual del jugador.
```
{"placeholder":"current_player_level"}
```
Salida de ejemplo: `30`

## Experiencia actual del jugador (current_player_exp)
Devuelve los puntos totales de experiencia del jugador.
```
{"placeholder":"current_player_exp"}
```
Salida de ejemplo: `1250`

## Progreso de experiencia del jugador (porcentaje) (current_player_exp_progress)
Devuelve el progreso de experiencia del jugador hacia el siguiente nivel como porcentaje.
```
{"placeholder":"current_player_exp_progress"}
```
Salida de ejemplo: `75`

## Fuerza de ataque del jugador (porcentaje) (player_attack_strength)
Devuelve el tiempo de reutilización del ataque del jugador como porcentaje.
```
{"placeholder":"player_attack_strength"}
```
Salida de ejemplo: `100`

## Modo de juego del jugador (player_gamemode)
Devuelve el modo de juego actual del jugador.
```
{"placeholder":"player_gamemode"}
```
Salida de ejemplo: `survival`

## Dirección de visión del jugador (player_view_direction)
Devuelve la dirección hacia la que mira el jugador.
```
{"placeholder":"player_view_direction"}
```
Salida de ejemplo: `north`

## Coordenada X del jugador (player_x_coordinate)
Devuelve la posición X del jugador en el mundo.
```
{"placeholder":"player_x_coordinate"}
```
Salida de ejemplo: `125`

## Coordenada Y del jugador (player_y_coordinate)
Devuelve la posición Y del jugador en el mundo.
```
{"placeholder":"player_y_coordinate"}
```
Salida de ejemplo: `64`

## Coordenada Z del jugador (player_z_coordinate)
Devuelve la posición Z del jugador en el mundo.
```
{"placeholder":"player_z_coordinate"}
```
Salida de ejemplo: `-250`

## Salud actual de la montura (current_mount_health)
Devuelve la salud actual de la entidad que el jugador está montando.
```
{"placeholder":"current_mount_health"}
```
Salida de ejemplo: `30.0`

## Salud máxima de la montura (max_mount_health)
Devuelve la salud máxima de la entidad que el jugador está montando.
```
{"placeholder":"max_mount_health"}
```
Salida de ejemplo: `30.0`

## Salud actual de la montura (porcentaje) (current_mount_health_percent)
Devuelve la salud de la montura como porcentaje.
```
{"placeholder":"current_mount_health_percent"}
```
Salida de ejemplo: `100`

## Medidor actual de salto de la montura (porcentaje) (current_mount_jump_meter)
Devuelve el valor del medidor de potencia de salto de la montura.
```
{"placeholder":"current_mount_jump_meter"}
```
Salida de ejemplo: `75`

## Salud actual del jefe (porcentaje) (current_boss_health)
Devuelve la salud del jefe activo.
```
{"placeholder":"current_boss_health"}
```
Salida de ejemplo: `150.0`

## Nombre del jefe (boss_name)
Devuelve el nombre del jefe activo.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Salida de ejemplo: `Ender Dragon`

## Conteo de jefes (boss_count)
Devuelve el número de jefes activos.
```
{"placeholder":"boss_count"}
```
Salida de ejemplo: `1`

## Conteo de efectos activos (effects_count)
Devuelve el número de efectos de poción activos.
```
{"placeholder":"effects_count"}
```
Salida de ejemplo: `3`

## Efecto activo (active_effect)
Devuelve información sobre un efecto activo específico.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Salida de ejemplo: `minecraft:speed`

## Casilla seleccionada de la barra rápida (active_hotbar_slot)
Devuelve la casilla de la barra rápida seleccionada actualmente (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Salida de ejemplo: `4`

## Ítem de la casilla (slot_item)
Devuelve información sobre un ítem en una casilla específica del inventario.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Salida de ejemplo: `minecraft:diamond_sword`

## Cantidad de ítems en la casilla (slot_item_count)
Devuelve el tamaño de la pila del ítem en una casilla específica del inventario del jugador.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Salida de ejemplo: `64`

## Durabilidad del ítem en la casilla (slot_item_durability)
Devuelve información de durabilidad del ítem en una casilla específica del inventario del jugador.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parámetros:
- `slot`: Número de casilla del inventario del jugador.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` o `percent`.

Salida de ejemplo: `87`

## Nombre mostrado del ítem en la casilla (slot_item_display_name_fm)
Devuelve el nombre mostrado del ítem en una casilla específica como un componente de texto JSON. En modo espectador, las casillas de la barra rápida pueden resolver los nombres de los ítems del menú espectador, a menos que `ignore_spectator` sea `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Salida de ejemplo: `{"text":"Diamond Sword","color":"aqua"}`

## Conteo de ítems en el inventario (inventory_item_count)
Devuelve el conteo total de un tipo de ítem en el inventario del jugador. Si `item` está vacío, cuenta todas las pilas de ítems en el inventario.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Salida de ejemplo: `12`

## Cantidad de restauración de comida en la casilla del inventario (inventory_slot_food_point_restore_amount)
Devuelve los puntos de hambre restaurados por el ítem de comida en la casilla dada del inventario del jugador.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Salida de ejemplo: `4.0`

## Ítem del inventario apuntado por el cursor (hovered_inventory_item)
Devuelve la clave del ítem que actualmente está bajo el cursor en una pantalla de inventario.
```
{"placeholder":"hovered_inventory_item"}
```
Salida de ejemplo: `minecraft:apple`

## Tiempo del juego del mundo (game_time)
Devuelve el contador actual de ticks del tiempo en el juego.
```
{"placeholder":"game_time"}
```
Salida de ejemplo: `18000`

## Hora del día del mundo (world_daytime)
Devuelve la hora actual del día del mundo.
```
{"placeholder":"world_daytime"}
```
Salida de ejemplo: `13000`

## Hora del día del mundo (world_daytime_hour)
Devuelve el componente de hora del tiempo del mundo. Por defecto usa formato de 24 horas; establece `twelve_hour_format` en `"true"` para formato de 12 horas.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Salida de ejemplo: `12`

## Minuto del día del mundo (world_daytime_minute)
Devuelve el componente de minuto del tiempo del mundo (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Salida de ejemplo: `30`

## Dificultad del mundo (world_difficulty)
Devuelve la dificultad actual del mundo.
```
{"placeholder":"world_difficulty"}
```
Salida de ejemplo: `normal`

## Semilla del mundo actual (current_world_seed)
Devuelve la semilla del mundo de un solo jugador actual. Devuelve un valor vacío cuando la semilla no está disponible.
```
{"placeholder":"current_world_seed"}
```
Salida de ejemplo: `123456789`

## Bioma actual (current_biome)
Devuelve el bioma en el que se encuentra actualmente el jugador. Establece `as_key` en `"false"` para devolver un nombre traducido/visible cuando esté disponible.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Salida de ejemplo: `minecraft:plains`

## Dimensión actual (current_dimension)
Devuelve la dimensión en la que se encuentra actualmente el jugador. Establece `as_key` en `"false"` para devolver un nombre traducido/visible cuando esté disponible.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Salida de ejemplo: `minecraft:overworld`

## Valor de gamerule (gamerule_value)
Devuelve el valor actual de una gamerule en el mundo/servidor cargado. Los mundos de servidor requieren FancyMenu en el servidor.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Salida de ejemplo: `true`

## Categoría del ítem (item_category)
Devuelve la categoría de pestaña creativa de un ítem. Establece `as_key` en `"true"` para devolver la clave de la categoría en lugar del nombre visible.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Salida de ejemplo: `Combat`

## Título/subtítulo actual del HUD (current_title)
Devuelve el texto del título que se muestra actualmente.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Salida de ejemplo: `Game Over!`

## Mensaje de la barra de acción (action_bar_message_fm)
Devuelve el mensaje actual de la barra de acción vanilla encima de la barra rápida.
```
{"placeholder":"action_bar_message_fm"}
```
Salida de ejemplo: `You may not rest now`

## Tiempo del mensaje de la barra de acción (action_bar_message_time_fm)
Devuelve cuántos ticks más se mostrará el mensaje actual de la barra de acción vanilla.
```
{"placeholder":"action_bar_message_time_fm"}
```
Salida de ejemplo: `42`

## Rotación X de la cámara (camera_rotation_x_fm)
Devuelve el pitch actual de la cámara en grados.
```
{"placeholder":"camera_rotation_x_fm"}
```
Salida de ejemplo: `12.5`

## Rotación Y de la cámara (camera_rotation_y_fm)
Devuelve el yaw actual de la cámara en grados.
```
{"placeholder":"camera_rotation_y_fm"}
```
Salida de ejemplo: `-90.0`

## Delta X de rotación de la cámara (camera_rotation_delta_x_fm)
Devuelve el cambio por tick en el pitch de la cámara.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Salida de ejemplo: `0.4`

## Delta Y de rotación de la cámara (camera_rotation_delta_y_fm)
Devuelve el cambio por tick en el yaw de la cámara.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Salida de ejemplo: `-1.2`

## Tiempo del ítem resaltado (highlighted_item_time_fm)
Devuelve cuántos ticks más se mostrará el nombre del ítem resaltado encima de la barra rápida.
```
{"placeholder":"highlighted_item_time_fm"}
```
Salida de ejemplo: `30`

## Progreso de uso de ítem del jugador (player_item_use_progress_fm)
Devuelve el progreso actual de uso de ítem de `0.0` a `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Salida de ejemplo: `0.65`

## Delta X de posición del jugador (player_position_delta_x_fm)
Devuelve el cambio por tick en la posición del jugador en el eje X.
```
{"placeholder":"player_position_delta_x_fm"}
```
Salida de ejemplo: `0.0`

## Delta Y de posición del jugador (player_position_delta_y_fm)
Devuelve el cambio por tick en la posición del jugador en el eje Y.
```
{"placeholder":"player_position_delta_y_fm"}
```
Salida de ejemplo: `-0.08`

## Delta Z de posición del jugador (player_position_delta_z_fm)
Devuelve el cambio por tick en la posición del jugador en el eje Z.
```
{"placeholder":"player_position_delta_z_fm"}
```
Salida de ejemplo: `0.12`

## IP actual del servidor (current_server_ip)
Devuelve la IP del servidor al que estás conectado.
```
{"placeholder":"current_server_ip"}
```
Salida de ejemplo: `mc.hypixel.net`

## Lista de jugadores del mundo (world_players_list)
Devuelve una lista de todos los jugadores actualmente en el mundo.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Salida de ejemplo: `Steve, Alex, Notch`

## MOTD del servidor (servermotd)
Devuelve el mensaje del día de un servidor.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Salida de ejemplo: `Welcome to Hypixel!`

## PING del servidor (serverping)
Devuelve la latencia a un servidor en milisegundos.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Salida de ejemplo: `54`

## Cantidad de jugadores en el servidor (serverplayercount)
Devuelve la cantidad de jugadores de un servidor.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Salida de ejemplo: `25000/30000`

## Estado del servidor (serverstatus)
Devuelve el estado en línea/fuera de línea de un servidor.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Salida de ejemplo: `§aOnline` o `§cOffline`

## Versión del servidor (serverversion)
Devuelve la versión de Minecraft de un servidor.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Salida de ejemplo: `1.19.2`

## Año (realtimeyear)
Devuelve el año actual.
```
{"placeholder":"realtimeyear"}
```
Salida de ejemplo: `2024`

## Mes (realtimemonth)
Devuelve el mes actual (01-12).
```
{"placeholder":"realtimemonth"}
```
Salida de ejemplo: `01`

## Día (realtimeday)
Devuelve el día actual del mes (01-31).
```
{"placeholder":"realtimeday"}
```
Salida de ejemplo: `27`

## Hora (realtimehour)
Devuelve la hora actual. Por defecto usa formato de 24 horas; establece `twelve_hour_format` en `"true"` para formato de 12 horas.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Salida de ejemplo: `14`

## Minuto (realtimeminute)
Devuelve el minuto actual (00-59).
```
{"placeholder":"realtimeminute"}
```
Salida de ejemplo: `30`

## Segundo (realtimesecond)
Devuelve el segundo actual (00-59).
```
{"placeholder":"realtimesecond"}
```
Salida de ejemplo: `45`

## Tiempo actual en milisegundos (marca de tiempo Unix) (unix_time)
Devuelve la marca de tiempo Unix actual en milisegundos.
```
{"placeholder":"unix_time"}
```
Salida de ejemplo: `1716552478123`

> Los marcadores de posición de tiempo real (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` y `unix_time`) admiten un valor `timezone`. Usa identificadores de zona horaria de Java normales como `UTC`, `Europe/Berlin` o `America/New_York`; omítelo o usa `system` para la zona horaria del sistema.
{.is-info}

## Información de CPU (cpuinfo)
Devuelve información sobre la CPU.
```
{"placeholder":"cpuinfo"}
```
Salida de ejemplo: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Uso de CPU (JVM) (jvmcpu)
Devuelve el uso de CPU de la JVM como porcentaje.
```
{"placeholder":"jvmcpu"}
```
Salida de ejemplo: `25.5`

## Uso de CPU (SO) (oscpu)
Devuelve el uso de CPU del sistema operativo como porcentaje.
```
{"placeholder":"oscpu"}
```
Salida de ejemplo: `42.8`

## Información de GPU (gpuinfo)
Devuelve información sobre la GPU.
```
{"placeholder":"gpuinfo"}
```
Salida de ejemplo: `NVIDIA GeForce RTX 3080`

## Versión de Java (javaver)
Devuelve la versión de Java.
```
{"placeholder":"javaver"}
```
Salida de ejemplo: `17.0.2`

## Máquina virtual de Java (jvmname)
Devuelve el nombre de la máquina virtual de Java.
```
{"placeholder":"jvmname"}
```
Salida de ejemplo: `OpenJDK 64-Bit Server VM`

## Versión de OpenGL (glver)
Devuelve la versión de OpenGL.
```
{"placeholder":"glver"}
```
Salida de ejemplo: `4.6.0 NVIDIA 516.94`

## Nombre del sistema operativo (osname)
Devuelve el nombre del sistema operativo.
```
{"placeholder":"osname"}
```
Salida de ejemplo: `Windows 10`

## FPS (fotogramas por segundo) (fps)
Devuelve los fotogramas por segundo actuales.
```
{"placeholder":"fps"}
```
Salida de ejemplo: `120`

## RAM usada en MB (usedram)
Devuelve la cantidad de RAM que se está usando actualmente (MB).
```
{"placeholder":"usedram"}
```
Salida de ejemplo: `4096`

## RAM máxima en MB (maxram)
Devuelve la RAM máxima asignada (MB).
```
{"placeholder":"maxram"}
```
Salida de ejemplo: `8192`

## RAM usada en %% (percentram)
Devuelve el porcentaje de RAM que se está usando actualmente.
```
{"placeholder":"percentram"}
```
Salida de ejemplo: `50`

## Volumen de elemento de audio (audio_element_vol)
Devuelve el volumen de un elemento de audio.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Salida de ejemplo: `0.5`

## Pista de audio actual (audio_element_current_track)
Devuelve el nombre de la pista de un elemento de audio.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Salida de ejemplo: `Cool Track Name`

## Duración de audio (audio_duration)
Devuelve la duración total de una pista de audio en formato MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Salida de ejemplo: `03:45`

## Tiempo reproducido de audio (audio_playtime)
Devuelve el tiempo reproducido actual de una pista de audio. Establece `show_percentage` en `"true"` para obtener un valor de progreso de 0-100 en lugar de `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Salida de ejemplo: `01:30` (o `45` cuando `show_percentage` es `"true"`)

## Estado de reproducción de audio (audio_playing_state)
Devuelve si un elemento de audio se está reproduciendo (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Salida de ejemplo: `true`

## Volumen de elemento de video (video_element_vol)
Devuelve el nivel de volumen de un elemento de video (0.0 a 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Salida de ejemplo: `0.5`

## Duración de elemento de video (video_element_duration)
Devuelve la duración total de un elemento de video en formato `MM:SS`. Establece `output_as_timestamp` en `"true"` para devolver una marca de tiempo en milisegundos.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Salida de ejemplo: `02:00` (o `120000` cuando `output_as_timestamp` es `"true"`)

## Tiempo reproducido de elemento de video (video_element_playtime)
Devuelve el tiempo actual de reproducción (progreso) de un elemento de video en formato `MM:SS`. Establece `show_percentage` en `"true"` para un valor de progreso de 0-100, o `output_as_timestamp` en `"true"` para milisegundos.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Salida de ejemplo: `00:45` (o `38` como porcentaje, o `45200` como marca de tiempo)

## Estado de pausa de elemento de video (video_element_paused_state)
Devuelve si un elemento de video está en pausa (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Salida de ejemplo: `false`

## Volumen de fondo de video (video_background_vol)
Devuelve el nivel de volumen de un fondo de video del menú (0.0 a 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Salida de ejemplo: `0.7`

## Duración de fondo de video (video_background_duration)
Devuelve la duración total de un fondo de video del menú en formato `MM:SS`. Establece `output_as_timestamp` en `"true"` para devolver una marca de tiempo en milisegundos.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Salida de ejemplo: `03:00` (o `180000` cuando `output_as_timestamp` es `"true"`)

## Tiempo reproducido de fondo de video (video_background_playtime)
Devuelve el tiempo actual de reproducción (progreso) de un fondo de video del menú en formato `MM:SS`. Establece `show_percentage` en `"true"` para un valor de progreso de 0-100, o `output_as_timestamp` en `"true"` para milisegundos.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Salida de ejemplo: `01:00` (o `33` como porcentaje, o `60500` como marca de tiempo)

## Estado de pausa de fondo de video (video_background_paused_state)
Devuelve si un fondo de video del menú está en pausa (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Salida de ejemplo: `true`

## Calculadora (calc)
El marcador de posición de calculadora es una herramienta poderosa que te permite realizar cálculos matemáticos dentro de tus diseños. Admite una amplia gama de operaciones matemáticas y puede trabajar tanto con números decimales como enteros.

### Sintaxis básica
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

La calculadora tiene dos parámetros principales:
- `decimal`: Determina si el resultado debe incluir decimales (`true`) o redondearse a enteros (`false`)
- `expression`: La expresión matemática que se va a evaluar

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

## Número aleatorio (random_number)
Genera un número aleatorio dentro de un rango especificado.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Salida de ejemplo: `42`

## Número máximo (maxnum)
Devuelve el mayor de dos números.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Salida de ejemplo: `20`

## Número mínimo (minnum)
Devuelve el menor de dos números.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Salida de ejemplo: `10`

## Número absoluto (absnum)
Devuelve el valor absoluto de un número.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Salida de ejemplo: `10.5`

## Negar número (negnum)
Devuelve el valor negado de un número.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Salida de ejemplo: `-10.5`

## *pi* (Matemáticas) (math_pi)
Devuelve el valor de π.
```
{"placeholder":"math_pi"}
```
Salida de ejemplo: `3.141592653589793`

## Seno trigonométrico (Matemáticas) (math_sin)
Devuelve el seno de un ángulo.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Salida de ejemplo: `0.7071067811865476`

## Coseno trigonométrico (Matemáticas) (math_cos)
Devuelve el coseno de un ángulo.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Salida de ejemplo: `0.7071067811865476`

## Tangente trigonométrica (Matemáticas) (math_tan)
Devuelve la tangente de un ángulo.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Salida de ejemplo: `1.0`

## Piso (Matemáticas) (math_floor)
Redondea un número hacia abajo al entero más cercano.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Salida de ejemplo: `3`

## Techo (Matemáticas) (math_ceil)
Redondea un número hacia arriba al entero más cercano.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Salida de ejemplo: `4`

## Redondear (Matemáticas) (math_round)
Redondea un número. Por defecto redondea al entero más cercano; establece `decimals` en un número no negativo para redondear a esa cantidad de decimales.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Salida de ejemplo: `3.14` (con `decimals:-1` o si se omite → `3`)

## Signo (Matemáticas) (math_sign)
Devuelve el signo de un número (1 para positivo, -1 para negativo, 0 para cero).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Salida de ejemplo: `-1`

## Seno hiperbólico (Matemáticas) (math_sinh)
Devuelve el seno hiperbólico de un ángulo.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Salida de ejemplo: `1.1752011936438014`

## Coseno hiperbólico (Matemáticas) (math_cosh)
Devuelve el coseno hiperbólico de un ángulo.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Salida de ejemplo: `1.5430806348152437`

## Tangente hiperbólica (Matemáticas) (math_tanh)
Devuelve la tangente hiperbólica de un ángulo.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Salida de ejemplo: `0.7615941559557649`

## Dividir texto (split_text)
Divide el texto usando un delimitador especificado.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Salida de ejemplo: `world`

## Recortar texto (trim_text)
Elimina espacios en blanco al inicio y al final.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Salida de ejemplo: `hello world`

## Cortar texto (crop_text)
Elimina caracteres del inicio y del final del texto.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Salida de ejemplo: `ello worl`

## Stringify (stringify)
Convierte un texto en cadena escapando todos los caracteres de sintaxis.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Salida de ejemplo: `text with \{special\} \"characters\"`

## Localizar texto (local)
Recupera texto localizado para una clave.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Salida de ejemplo: `Singleplayer`

## Texto web (webtext)
Recupera contenido de texto desde una URL web.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Salida de ejemplo: Contenido de texto de la URL

## Texto aleatorio (randomtext)
Devuelve una línea aleatoria de un archivo de texto, una URL o texto plano directo. El texto cambia en intervalos especificados.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parámetros:
- `source`: El origen de las líneas de texto (sustituye al parámetro antiguo `path`)
  - Ruta de archivo: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Texto plano: `Line 1\nLine 2\nLine 3`
- `interval`: Tiempo en segundos entre cambios de texto

El marcador de posición ahora admite tres tipos de origen:
1. **Archivos locales**: Archivos de texto de tu directorio del juego
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: Archivos de texto remotos de internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texto plano**: Entrada de texto directa con líneas separadas por `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Nota: Los marcadores de posición antiguos que usan `path` en lugar de `source` seguirán funcionando.

## Analizador JSON (json)
Analiza datos JSON de un archivo, una URL o contenido JSON directo, y extrae valores usando expresiones JSON path.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parámetros:
- `source`: El origen de los datos JSON
  - Ruta de archivo: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - JSON directo: `{"name":"Steve","level":42}`
- `json_path`: La expresión JSON path para extraer datos

El marcador de posición ahora admite tres tipos de origen:
1. **Archivos locales**: Archivos JSON de tu directorio del juego
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: Datos JSON remotos de APIs o servicios web
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON directo**: Contenido JSON en línea
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Ejemplos de JSON path:
- `$.name` - Obtiene el campo "name" desde la raíz
- `$.player.level` - Obtiene el campo anidado "level" dentro de "player"
- `$.items[0].id` - Obtiene el "id" del primer elemento de un arreglo
- `$.scores.*` - Obtiene todos los valores del objeto "scores"

## Ruta absoluta de archivo/carpeta (absolute_path)
Devuelve la ruta absoluta de un archivo.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Salida de ejemplo: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Conteo de caracteres del texto (text_character_count)
Devuelve el número de caracteres en el texto dado.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Salida de ejemplo: `12`

## Ancho del texto (text_width)
Devuelve el ancho en píxeles del texto dado cuando se renderiza.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Salida de ejemplo: `66`

## Texto en mayúsculas (uppercase_text)
Convierte el texto de entrada a todas mayúsculas.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Salida de ejemplo: `HELLO WORLD`

## Texto en minúsculas (lowercase_text)
Convierte el texto de entrada a todas minúsculas.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Salida de ejemplo: `hello world`

## Texto en formato de título (title_case_text)
Convierte el texto de entrada a formato de título.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Salida de ejemplo: `Hello World`

## Texto en formato de oración (sentence_case_text)
Convierte el texto de entrada a formato de oración.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Salida de ejemplo: `Hello world. This is fancymenu!`

## Texto en snake_case (snake_case_text)
Convierte el texto de entrada a `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Salida de ejemplo: `hello_world`

## Texto en kebab-case (kebab_case_text)
Convierte el texto de entrada a `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Salida de ejemplo: `hello-world`

## Texto en mayúsculas y minúsculas alternadas (alternating_case_text)
Convierte el texto de entrada a mayúsculas y minúsculas alternadas.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Salida de ejemplo: `aLtErNaTiNg CaSe`

## Alternar mayúsculas/minúsculas (toggle_case_text)
Cambia entre mayúsculas y minúsculas cada letra del texto de entrada.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Salida de ejemplo: `tOGGLE cASE`

## Codificar a Base64 (base64_encode)
Codifica el texto dado como Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Salida de ejemplo: `SGVsbG8gV29ybGQ=`

## Decodificar de Base64 (base64_decode)
Decodifica una cadena Base64 de vuelta a texto plano.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Salida de ejemplo: `Hello World`

## Texto de archivo (file_text)
Devuelve líneas de texto de un archivo o URL. Puede devolver todas las líneas o solo las últimas X líneas.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parámetros:
- `path_or_url`: Ruta de archivo o URL desde la que se leerá
- `mode`: Puede ser `"all"` (devuelve todas las líneas) o `"last"` (devuelve solo las últimas X líneas)
- `separator`: Texto con el que se unirán las líneas (predeterminado: `"\n"`)
- `last_lines`: Número de líneas a devolver cuando `mode` es `"last"` (predeterminado: `"1"`)

Salida de ejemplo: Depende del contenido del archivo

## Contenido del portapapeles (clipboard_content)
Devuelve el contenido de texto actual almacenado en el portapapeles del sistema.
```
{"placeholder":"clipboard_content"}
```
Salida de ejemplo: Cualquier texto que esté actualmente en el portapapeles

## Reemplazar texto (replace_text)
Reemplaza texto en una cadena usando texto literal o expresiones regulares.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parámetros:
- `text`: El texto de entrada a procesar
- `search`: El texto o patrón regex que se buscará
- `replacement`: El texto de reemplazo
- `use_regex`: Si se usa regex (`"true"`) o coincidencia literal (`"false"`)
- `replace_all`: Reemplazar todas las apariciones (`"true"`) o solo la primera (`"false"`)

Salida de ejemplo: `Hello FancyMenu! This is a test.`

## Cambiar según caso (switch_case)
Realiza una operación switch-case basada en un valor.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Salida de ejemplo: `first case` (si el valor es 1)

## Obtener valor de variable (variable de FM) (getvariable)
Recupera el valor de una variable guardada previamente.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Salida de ejemplo: Depende del valor almacenado

## Obtener datos NBT (nbt_data_get)
Recupera datos NBT en el cliente (similar al comando `/data get`). Usa la variante del servidor `nbt_data_get_server` cuando estés conectado a un servidor y necesites valores autoritativos del lado del servidor.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parámetros:
- `source_type`: Puede ser `"entity"` o `"block"`
- `entity_selector`: Selector de entidad como `@s`, `@p`, `@e`, o UUID/nombre (para entidades)
- `block_pos`: Posición del bloque en formato `"x y z"` (para bloques)
- `nbt_path`: La ruta NBT que se recuperará
- `scale`: Factor de escala opcional para valores numéricos (predeterminado: `"1.0"`)
- `return_type`: Cómo devolver los datos:
  - `"value"`: Predeterminado, devuelve el valor (con escala opcional para números)
  - `"string"`: Devuelve los datos NBT reales como cadena
  - `"snbt"`: Devuelve como SNBT (NBT formateado)
  - `"json"`: Devuelve como componente formateado en JSON (para etiquetas compuestas)

Salida de ejemplo: `20` (para el nivel de comida)

## Obtener datos NBT (lado del servidor) (nbt_data_get_server)
Consulta datos NBT del lado del servidor (usando un paquete) y almacena en caché los resultados por poco tiempo. Los valores reflejan el marcador de posición del lado del cliente.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Salida de ejemplo: `minecraft:diamond_sword`

## Último mensaje de muerte (lastdeathmessage)
Devuelve el último mensaje de muerte registrado del jugador cliente. Establece `as_json_component` en `"true"` para obtener el componente de texto JSON en bruto.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Salida de ejemplo: `Steve was slain by Zombie`

## Duración de funcionamiento (uptime_duration)
Devuelve cuánto tiempo ha estado cargado FancyMenu. Por defecto el valor está en segundos; establece `output_as_millis` en `"true"` para recibir milisegundos.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Salida de ejemplo: `742` (segundos desde la carga)

## Nombres de guardados del mundo (level_save_names)
Enumera todos los nombres de guardados de mundos locales unidos por el separador elegido. Se ejecuta en el hilo del cliente.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Salida de ejemplo: `Creative Test, Survival World, Hardcore`

## Datos de guardado del mundo (level_save_data)
Devuelve los datos serializados del nivel para el nombre de mundo dado (debe coincidir con el nombre mostrado en la lista de guardados).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Salida de ejemplo: `{"name":"Survival World","gameMode":"survival",...}`

## Conversor de base numérica (number_base_convert)
Convierte un número (entero o fraccionario) de una base a otra (2–36). Usa decimal por defecto si no se proporcionan bases.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Salida de ejemplo: `43.8`

## Tamaño de archivo (file_size)
Devuelve el tamaño de un archivo local en bytes. Solo se permiten rutas locales.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Salida de ejemplo: `1284`

## MD5 de archivo (file_md5)
Devuelve el hash MD5 de un archivo local como una cadena hexadecimal en minúsculas.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Salida de ejemplo: `d41d8cd98f00b204e9800998ecf8427e`

# Ejemplos prácticos

## Crear una vista dinámica de memoria
```
RAM usada: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Hacer un reloj en tiempo real
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Crear una vista de información del sistema
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

# Mejores prácticas

1. **Cacha las operaciones costosas**: Algunos marcadores de posición (como los que leen información del sistema) pueden consumir recursos. Considera usar variables para almacenar sus valores si necesitas usarlos varias veces.

2. **Usa configuraciones decimales adecuadas**: Al trabajar con cálculos, usa el parámetro `decimal` de forma apropiada. Establécelo en `false` cuando necesites enteros y en `true` cuando necesites valores decimales precisos.

3. **Maneja valores faltantes**: Siempre considera qué debe pasar si un marcador de posición no devuelve ningún valor. Tal vez quieras proporcionar valores predeterminados en esos casos.

4. **Prueba el rendimiento**: Al usar muchos marcadores de posición o estructuras anidadas complejas, prueba el impacto en el rendimiento, especialmente en sistemas de gama baja.

5. **Usa dimensiones avanzadas de tamaño/posición**: Para elementos dinámicos de la interfaz, combina marcadores de posición con tamaño y posicionamiento avanzados para crear diseños responsivos.

6. **Combínalos con variables**: Usa marcadores de posición junto con variables para contenido aún más dinámico que pueda actualizarse mediante acciones.

# Problemas comunes y soluciones

## El marcador de posición no se actualiza
Si el valor de un marcador de posición no se actualiza como esperas, revisa:
- Si el marcador de posición está formateado correctamente
- Si estás usando la mayúscula/minúscula correcta para los IDs de los marcadores de posición
- Si el marcador de posición requiere condiciones específicas para actualizarse

## Los marcadores de posición anidados no funcionan
Al anidar marcadores de posición:
- Asegúrate de escapar correctamente las comillas
- Verifica que cada marcador de posición anidado sea válido por sí solo

## Problemas de rendimiento
Si notas problemas de rendimiento:
- Reduce la cantidad de marcadores de posición utilizados
- Evita anidamientos innecesarios
- Considera usar variables para valores consultados con frecuencia
- Usa el marcador de posición apropiado para tus necesidades (por ejemplo, no uses marcadores de posición de tiempo real cuando valores estáticos sean suficientes)
