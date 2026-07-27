---
title: Oyentes
description: Cómo crear y usar oyentes en FancyMenu.
---

# Oyentes

Los oyentes ejecutan [scripts de acción](./action-scripts) cuando ocurren eventos específicos. No están vinculados a una pantalla abierta, por lo que también pueden ejecutarse mientras juegas o se está cargando.

Los oyentes pueden proporcionar valores `$$`, como una tecla pulsada o un botón del ratón pulsado, a sus acciones y requisitos.

> [!CAUTION]
> Un oyente puede ejecutar acciones de archivo, red, comandos, portapapeles, resource pack o enlace sin que haya una pantalla abierta. Importa oyentes solo de fuentes en las que confíes.

# Uso de oyentes

Fuera del Editor de diseño, abre **barra de menú -> Personalización -> Gestionar oyentes** para crear o editar oyentes.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Gestionar oyentes" style="max-width:800px;width:100%;height:auto;">

# Variables del oyente

Los oyentes pueden proporcionar valores de solo lectura a sus acciones y requisitos. Usa sus nombres `$$` en los campos de texto compatibles.

Por ejemplo, usa [**Al pulsar una tecla del teclado**](#on-keyboard-key-pressed-keyboard_key_pressed) con la [acción **Imprimir en el registro del juego**](./action-scripts#print-to-game-log-print_to_log). El valor `¡Tecla pulsada! La tecla es: $$key_name` inserta el nombre de la tecla pulsada.

> [!WARNING]
> Las variables de oyente son independientes de las [variables almacenadas](./variables) de FancyMenu. Las acciones, los requisitos y los marcadores de posición de variables almacenadas no funcionan con valores `$$`.

Los nombres de las variables del oyente distinguen mayúsculas y minúsculas y solo funcionan dentro del script de ese oyente.

Trata como no fiables los valores procedentes del chat, servidores remotos, archivos y la entrada del usuario. No los insertes directamente en rutas, URL o comandos.

Las variables de oyente son cadenas de texto. Cuando la información no esté disponible, un oyente puede devolver un valor centinela documentado como `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` o una cadena vacía. Comprueba estos valores antes de insertar datos del oyente en rutas, comandos o URL.

# Oyentes en detalle

Esta sección enumera los oyentes integrados de FancyMenu.

## Al hacer clic en texto Markdown (`text_clicked`)
- Se activa cuando se hace clic en [texto Markdown con un evento `click:`](./text-formatting#click-and-hover-events), por ejemplo `[Abrir](click:open_menu)`.
- Variables:
  - `$$text_event_id` – ID del evento del enlace Markdown

## Al pasar el ratón sobre texto Markdown (`text_hovered`)
- Se activa cuando se pasa el ratón sobre [texto Markdown con un evento `hover:`](./text-formatting#click-and-hover-events), por ejemplo `[Pista](hover:show_hint)`.
- Variables:
  - `$$text_event_id` – ID del evento del enlace Markdown

## Al extraer un ZIP mediante una acción (`zip_extracted_via_action`)
- Se activa cuando termina la [acción **Extraer archivo ZIP en el directorio del juego**](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir).
- Variables:
  - `$$source_zip_path` – ruta de origen normalizada y visible para el usuario; las rutas del directorio del juego pueden devolverse como `/...`, mientras que las rutas convencionales del directorio de Minecraft pueden usar `.minecraft/...`
  - `$$target_folder_path` – ruta de destino normalizada y visible para el usuario usando los mismos formatos de ruta
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – texto de error cuando falla la extracción

## Al generar un elemento (`element_spawned_via_action`)
- Se activa cuando una función compatible de FancyMenu o un complemento genera dinámicamente una instancia de elemento.
- Variables:
  - `$$element_type` – tipo de elemento generado
  - `$$element_identifier` – identificador del elemento generado
  - `$$target_screen` – identificador de la pantalla de destino

## Al empezar a reproducirse una textura animada (`animated_texture_started_playing`)
- Se activa cuando una [textura animada](./fma) empieza a reproducirse.
- Variables:
  - `$$texture_source` – origen de la textura
  - `$$texture_source_type` – tipo de origen
  - `$$texture_will_restart` – true/false

## Al terminar de reproducirse una textura animada (`animated_texture_finished_playing`)
- Se activa cuando una textura animada termina de reproducirse.
- Variables:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## Al cambiar el estado de reproducción de un vídeo (`video_playback_status_changed`)
- Se activa cuando un [elemento de vídeo o el fondo del menú](./video) cambia su estado de reproducción.
- Variables:
  - `$$video_source` – origen del vídeo
  - `$$video_source_type` – tipo de origen
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` o `FINISHED`

## Al recibir un mensaje del sistema en el chat (`system_message_received_in_chat`)
- Se activa cuando el cliente recibe un mensaje de chat del sistema, como una respuesta de un comando.
- Variables:
  - `$$system_message_string` – mensaje en texto plano
  - `$$system_message_component` – componente JSON

## Al recibir datos de FM (`fm_data_received`)
- Se activa cuando un servidor envía [datos de FM](./fm-data) a este cliente mediante `/fmdata send`.
- Variables:
  - `$$data_identifier` – cadena identificadora de los datos
  - `$$data` – carga de datos
  - `$$sent_by` – IP del servidor o `integrated_server`

## Al conectarse a un servidor remoto (`remote_server_connected`)
- Se activa después de que una [conexión a un servidor remoto](./remote-server-communication) se abra correctamente.
- Variables:
  - `$$request_id` – ID de solicitud en caché
  - `$$remote_server_url` – URL del servidor remoto

## Al recibir datos de un servidor remoto (`remote_server_data_received`)
- Se activa cuando se reciben datos de texto desde un servidor remoto conectado.
- Variables:
  - `$$request_id` – ID de solicitud
  - `$$remote_server_url` – URL del servidor remoto
  - `$$data` – carga recibida

## Al cerrarse la conexión con un servidor remoto (`remote_server_connection_closed`)
- Se activa cuando se cierra una conexión con un servidor remoto.
- Variables:
  - `$$request_id` – ID de solicitud
  - `$$remote_server_url` – URL del servidor remoto
  - `$$intentionally_closed` – TRUE si se cerró mediante una acción
  - `$$crashed` – TRUE si la conexión se cerró de forma inesperada
  - `$$unknown_close_reason` – TRUE si no había ningún motivo de cierre conocido disponible

## Al pulsar una tecla del teclado (`keyboard_key_pressed`)
- Se activa cada vez que se pulsa una tecla (se repite mientras se mantiene pulsada; funciona en pantallas y en juego).
- Variables:
  - `$$key_name` – nombre visible de la tecla
  - `$$key_keycode` – código de tecla GLFW
  - `$$key_scancode` – código de exploración GLFW
  - `$$key_modifiers` – máscara de bits de modificadores activos

## Al soltar una tecla del teclado (`keyboard_key_released`)
- Se activa cuando se suelta una tecla (pantallas y en juego).
- Variables:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## Al escribir un carácter del teclado en una pantalla (`keyboard_char_typed`)
- Se activa cuando se escribe un carácter mientras hay una pantalla abierta.
- Variables:
  - `$$char` – carácter escrito

## Al mover el ratón en una pantalla (`mouse_moved`)
- Se activa cada vez que se mueve el ratón mientras hay una pantalla abierta.
- Variables:
  - `$$mouse_pos_x` – X actual
  - `$$mouse_pos_y` – Y actual
  - `$$mouse_move_delta_x` – delta en X desde el último evento
  - `$$mouse_move_delta_y` – delta en Y desde el último evento

## Al hacer clic en un botón del ratón (`mouse_button_clicked`)
- Se activa cuando se pulsa un botón del ratón (pantallas y en juego).
- Variables:
  - `$$button` – izquierdo/derecho/central
  - `$$mouse_pos_x` – X actual
  - `$$mouse_pos_y` – Y actual

## Al soltar un botón del ratón (`mouse_button_released`)
- Se activa cuando se suelta un botón del ratón (pantallas y en juego).
- Variables:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## Al desplazar la rueda del ratón en una pantalla (`mouse_scrolled`)
- Se activa cuando se desplaza la rueda del ratón mientras hay una pantalla abierta.
- Variables:
  - `$$scroll_delta_y` – cantidad de desplazamiento vertical

## Al abrirse una pantalla (`screen_open`)
- Se ejecuta justo después de que cualquier pantalla se vuelva activa; puede usarse para anularla.
- Variables:
  - `$$screen_identifier` – identificador de la pantalla abierta

## Al cerrarse una pantalla (`screen_close`)
- Se ejecuta inmediatamente después de que una pantalla se cierre.
- Variables:
  - `$$screen_identifier` – identificador de la pantalla cerrada

## Al salir de Minecraft (`quit_minecraft`)
- Se activa una vez cuando el cliente empieza a cerrarse.
- Variables:
  - `$$timestamp_millis` – milisegundos desde la época al salir
  - `$$timestamp_iso` – marca temporal ISO-8601 del momento de salida

## Al morir (`player_death`)
- Se ejecuta cuando se abre la pantalla de muerte estándar para el jugador local.
- Variables:
  - `$$days_survived` – días desde la última muerte
  - `$$death_reason_string` – causa en texto plano
  - `$$death_reason_component` – causa como componente JSON
  - `$$death_pos_x` – coordenada X de la muerte
  - `$$death_pos_y` – coordenada Y de la muerte
  - `$$death_pos_z` – coordenada Z de la muerte

## Al actualizarse una variable [FM Variable] (`fm_variable_updated`)
- Se activa cada vez que se establece o actualiza una [variable de FancyMenu](./variables).
- Variables:
  - `$$var_name` – nombre de la variable
  - `$$old_value` – valor anterior
  - `$$new_value` – valor nuevo

## Al descargarse un archivo mediante una acción (`file_downloaded_via_action`)
- Se activa después de que termine la [acción **Descargar archivo al directorio del juego**](./action-scripts#download-file-to-game-directory-download_file_to_game_dir).
- Variables:
  - `$$download_url` – origen de la descarga
  - `$$target_file_path` – ruta del archivo guardado si tiene éxito; si falla, esto puede contener solo el directorio de destino porque no se resolvió un nombre de archivo final
  - `$$download_succeeded` – true/false

## Al seleccionar un archivo (`file_selected_via_action`)
- Se activa después de que termine la [acción **Seleccionar archivo del sistema**](./action-scripts#select-file-from-system-select_file_to_game_dir).
- Variables:
  - `$$selected_file_path` – ruta absoluta del archivo elegido o vacía si se canceló
  - `$$target_file_path` – ruta resuelta dentro de la instancia
  - `$$selection_succeeded` – true si la copia tuvo éxito
  - `$$selection_cancelled` – true si se cerró el diálogo
  - `$$failure_reason` – información del error en caso de fallo

## Al recibir un mensaje de chat (`chat_message_received`)
- Se activa cuando aparece una línea normal de chat de jugador en el cliente.
- Variables:
  - `$$chat_message_string` – línea en texto plano
  - `$$chat_message_component` – componente JSON completo
  - `$$sender_uuid` – UUID del remitente o ERROR
  - `$$sender_name` – nombre del remitente o ERROR

## Al enviar un mensaje de chat (`chat_message_sent`)
- Se activa cuando el jugador local envía un mensaje de chat.
- Variables:
  - `$$chat_message_string` – línea en texto plano
  - `$$chat_message_component` – componente JSON completo

## Al ganar un efecto (`effect_gained`)
- Se activa cuando el jugador obtiene un efecto de estado.
- Variables:
  - `$$effect_key` – ubicación del recurso del efecto
  - `$$effect_type` – positivo/negativo/neutro
  - `$$effect_duration` – ticks restantes

## Al perder un efecto (`effect_lost`)
- Se activa cuando el jugador pierde un efecto de estado.
- Variables:
  - `$$effect_key` – efecto caducado
  - `$$effect_type` – categoría

## Al cambiar la experiencia (`experience_changed`)
- Se activa cada vez que cambia la experiencia total del jugador.
- Variables:
  - `$$new_experience_amount` – después del cambio
  - `$$old_experience_amount` – antes del cambio
  - `$$is_level_up` – TRUE si ha aumentado de nivel

## Al recibir daño (`damage_taken`)
- Se activa una vez por impacto cuando el jugador recibe daño.
- Variables:
  - `$$damage_amount` – salud reducida
  - `$$damage_type` – ubicación del recurso del tipo de daño
  - `$$is_fatal_damage` – TRUE si es letal
  - `$$damage_source` – ubicación del recurso del atacante o NONE

## Al empezar a congelarse (`started_freezing`)
- Se activa cuando el jugador empieza a congelarse.
- Variables:
  - `$$freezing_intensity` – 0.0 sin congelación, 1.0 totalmente congelado

## Al dejar de congelarse (`stopped_freezing`)
- Se activa cuando el jugador deja de congelarse.
- Variables:
  - (ninguna)

## Al congelarse por completo (`fully_frozen`)
- Se activa una vez cuando el jugador queda totalmente congelado.
- Variables:
  - (ninguna)

## Al empezar a mirar un bloque (`start_looking_at_block`)
- Se activa una vez cuando la mira apunta por primera vez a un bloque (distancia máxima de 20 bloques).
- Variables:
  - `$$block_key` – bloque objetivo
  - `$$block_pos_x` – X del bloque
  - `$$block_pos_y` – Y del bloque
  - `$$block_pos_z` – Z del bloque
  - `$$distance_to_player` – de los ojos al punto de impacto

## Al dejar de mirar un bloque (`stop_looking_at_block`)
- Se activa cuando la mira deja de apuntar a un bloque (informa del último bloque objetivo, máximo 20 bloques).
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## Al empezar a mirar una entidad (`start_looking_at_entity`)
- Se activa una vez cuando la mira apunta por primera vez a una entidad (máximo 20 bloques).
- Variables:
  - `$$entity_key` – tipo de entidad objetivo
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Al dejar de mirar una entidad (`stop_looking_at_entity`)
- Se activa cuando la mira deja de apuntar a una entidad (informa de la última entidad objetivo, máximo 20 bloques).
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Al aparecer una entidad (`entity_spawned`)
- **Requiere FancyMenu en el servidor.** Se activa cuando aparece cualquier entidad en cualquier lugar del mundo/servidor conectado.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player` – −1 si está en otra dimensión
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## Al morir una entidad (`entity_died`)
- **Requiere FancyMenu en el servidor.** Se activa cuando muere cualquier entidad en el mundo/servidor conectado.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player` – −1 si está en otra dimensión
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## Al empezar a ver una entidad (`entity_starts_being_in_sight`)
- Se activa cuando una entidad se vuelve visible por primera vez dentro de 200 bloques.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Al dejar de estar a la vista una entidad (`entity_stops_being_in_sight`)
- Se activa cuando una entidad que antes era visible sale de la vista o se mueve más allá de 200 bloques.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Al interactuar con una entidad (`entity_interacted`)
- Se activa cuando el jugador interactúa correctamente con una entidad.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Al montar una entidad (`entity_mounted`)
- Se activa cuando el jugador empieza a montar una entidad.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Al desmontar una entidad (`entity_unmounted`)
- Se activa cuando el jugador deja de montar la entidad actual.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Al romper un bloque (`block_broke`)
- Se activa cuando el jugador rompe un bloque.
- Variables:
  - `$$block_key`
  - `$$broke_with_item_key` – herramienta utilizada o EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Al colocar un bloque (`block_placed`)
- Se activa cuando el jugador coloca un bloque.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Al interactuar con un bloque (`interacted_with_block`)
- Se activa cuando el jugador interactúa correctamente con un bloque.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Al pisar un bloque (`stepping_on_block`)
- Se activa cuando el jugador pisa un bloque.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Al entrar en un bioma (`enter_biome`)
- Se activa cuando el jugador entra en un bioma nuevo.
- Variables:
  - `$$biome_key` – bioma al que se ha entrado

## Al salir de un bioma (`leave_biome`)
- Se activa cuando el jugador sale de su bioma actual.
- Variables:
  - `$$biome_key` – bioma que acaba de dejarse

## Al entrar en una estructura (`enter_structure`)
- **Requiere FancyMenu en el servidor.** Detección aproximada del área de la estructura; puede activarse cerca, encima o debajo de la estructura.
- Variables:
  - `$$structure_key` – estructura a la que se ha entrado

## Al salir de una estructura (`leave_structure`)
- **Requiere FancyMenu en el servidor.** Detección aproximada; puede activarse cerca de la huella de la estructura.
- Variables:
  - `$$structure_key` – estructura que acaba de abandonarse

## Al entrar en una estructura (alta precisión) (`enter_structure_high_precision`)
- **Requiere FancyMenu en el servidor.** Se activa cuando el jugador entra en las cajas delimitadoras de una estructura.
- Variables:
  - `$$structure_key`

## Al salir de una estructura (alta precisión) (`leave_structure_high_precision`)
- **Requiere FancyMenu en el servidor.** Se activa después de que el jugador salga de las cajas delimitadoras de una estructura.
- Variables:
  - `$$structure_key`

## Al entrar en una dimensión (`enter_dimension`)
- Se activa cuando el jugador entra en una dimensión nueva.
- Variables:
  - `$$dimension_key` – dimensión a la que se ha entrado

## Al empezar a nadar (`start_swimming`)
- Se activa cuando el jugador empieza a nadar.
- Variables:
  - `$$fluid_type` – ubicación del recurso del fluido

## Al dejar de nadar (`stop_swimming`)
- Se activa cuando el jugador deja de nadar.
- Variables:
  - `$$fluid_type` – fluido en el que dejó de nadar

## Al empezar a tocar un fluido (`start_touching_fluid`)
- Se activa cuando el jugador empieza a tocar un fluido.
- Variables:
  - `$$fluid_type` – fluido tocado

## Al dejar de tocar un fluido (`stop_touching_fluid`)
- Se activa cuando el jugador deja de tocar un fluido.
- Variables:
  - `$$fluid_type` – fluido que ya no se toca

## Al iniciarse una pista de música (`music_track_started`)
- Se activa cuando comienza una nueva pista de música.
- Variables:
  - `$$track_resource_location` – archivo de audio
  - `$$track_display_name` – nombre legible por personas o UNKNOWN
  - `$$track_artist` – artista o UNKNOWN
  - `$$track_duration_ms` – milisegundos (0 si se desconoce)

## Al detenerse una pista de música (`music_track_stopped`)
- Se activa cuando la pista de música actual termina o se sustituye.
- Variables:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## Al activarse un sonido del mundo (`world_sound_triggered`)
- Se activa cuando un sonido posicional del mundo empieza cerca del jugador.
- Variables:
  - `$$sound_resource_location` – archivo de sonido
  - `$$sound_display_name` – nombre del subtítulo cuando esté disponible
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – grados 0–360 relativos a la orientación

## Al cambiar el clima (`weather_changed`)
- Se activa cuando el clima cambia de forma global o local (un cambio de bioma o entrar en interiores puede volver a activarlo).
- Variables:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE si se renderiza nieve
  - `$$weather_can_rain` – TRUE si se renderiza lluvia

## Al empezar a arder (`started_burning`)
- Se activa cuando el jugador empieza a arder.
- Variables:
  - (ninguna)

## Al dejar de arder (`stopped_burning`)
- Se activa cuando el jugador deja de arder.
- Variables:
  - (ninguna)

## Al empezar a ahogarse (`started_drowning`)
- Se activa cuando el jugador empieza a recibir daño por ahogamiento.
- Variables:
  - (ninguna)

## Al cambiar la posición (`position_changed`)
- Se activa cada vez que cambia la posición del bloque del jugador.
- Variables:
  - `$$old_pos_x` – bloque X anterior
  - `$$old_pos_y` – bloque Y anterior
  - `$$old_pos_z` – bloque Z anterior
  - `$$new_pos_x` – nuevo bloque X
  - `$$new_pos_y` – nuevo bloque Y
  - `$$new_pos_z` – nuevo bloque Z

## Al empezar a correr (`started_running`)
- Se activa cuando el jugador empieza a esprintar.
- Variables:
  - (ninguna)

## Al dejar de correr (`stopped_running`)
- Se activa cuando el jugador deja de esprintar.
- Variables:
  - (ninguna)

## Al saltar (`jump`)
- Se activa cada vez que el jugador salta.
- Variables:
  - (ninguna)

## Al unirse a un servidor (`server_joined`)
- Se activa después de unirse correctamente a un servidor multijugador.
- Variables:
  - `$$server_ip` – dirección del servidor al que se ha unido

## Al salir de un servidor (`server_left`)
- Se activa después de desconectarse de un servidor multijugador.
- Variables:
  - `$$server_ip` – dirección del servidor del que se ha salido

## Al entrar en un mundo individual (`world_entered`)
- Se activa después de que un mundo en solitario termine de cargarse y se devuelva el control.
- Variables:
  - `$$world_name` – nombre visible
  - `$$world_save_path` – carpeta de guardado absoluta
  - `$$world_difficulty` – clave de dificultad
  - `$$world_cheats_allowed` – TRUE si los trucos están activados
  - `$$world_icon_path` – ruta absoluta del icono
  - `$$world_is_first_join` – TRUE en la primera visita

## Al salir de un mundo individual (`world_left`)
- Se activa después de que un mundo en solitario se cierre y termine de guardarse.
- Variables:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## Al unirse otro jugador al mundo/servidor (`other_player_joined_world`)
- Se activa cuando otro jugador se une al mundo/servidor actual.
- Variables:
  - `$$player_name` – nombre del jugador que se une
  - `$$player_uuid` – UUID

## Al salir otro jugador del mundo/servidor (`other_player_left_world`)
- Se activa cuando otro jugador abandona el mundo/servidor actual.
- Variables:
  - `$$player_name`
  - `$$player_uuid`

## Al morir otro jugador (`other_player_died`)
- Se activa cuando otro jugador del mundo actual muere.
- Variables:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## Al recoger un objeto (`item_picked_up`)
- Se activa cuando el jugador recoge una entidad de objeto.
- Variables:
  - `$$item_key` – ubicación del recurso del objeto recogido

## Al soltar un objeto (`item_dropped`)
- Se activa cuando el jugador suelta un objeto de su inventario.
- Variables:
  - `$$item_key` – ubicación del recurso del objeto soltado

## Al consumirse un objeto (`item_consumed`)
- Se activa cuando el jugador termina de consumir un objeto.
- Variables:
  - `$$item_key` – objeto consumido

## Al pasar el ratón sobre un objeto en el inventario (`item_hovered_in_inventory`)
- Se activa cuando el usuario pasa el ratón sobre un objeto en cualquier pantalla de inventario.
- Variables:
  - `$$item_key` – ubicación del recurso del objeto sobre el que se pasa el ratón
  - `$$item_display_name_string` – nombre visible del objeto en texto plano
  - `$$item_display_name_json` – nombre visible del objeto como componente JSON

## Al usar un objeto (`item_used`)
- Se activa cuando el jugador usa un objeto.
- Variables:
  - `$$item_key` – objeto usado
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – tipo de entidad objetivo o vacío
  - `$$used_on_block_key` – bloque objetivo o vacío
  - `$$target_pos_x` – X objetivo o -1
  - `$$target_pos_y` – Y objetivo o -1
  - `$$target_pos_z` – Z objetivo o -1

## Al romperse un objeto (`item_broke`)
- Se activa cuando un objeto del inventario del jugador se rompe.
- Variables:
  - `$$item_key` – objeto roto
  - `$$item_type` – herramienta/armadura/otro
