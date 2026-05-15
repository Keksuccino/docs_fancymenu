---
title: Escuchadores
description: Cómo crear y usar escuchadores en FancyMenu.
---

# Escuchadores

A partir de FancyMenu v3.8.0, hay una nueva función llamada "escuchadores".

Los escuchadores ejecutan scripts de acciones cuando ocurren eventos específicos del cliente o de la jugabilidad.
Pueden exponer variables para acciones, placeholders y requisitos anidados dentro del escuchador.

A diferencia de la mayoría de las cosas en FancyMenu, los escuchadores no están ligados a una pantalla o superposición. Se ejecutan constantemente en segundo plano, escuchando sus eventos. En cuanto se dispara un escuchador, ejecuta su script de acciones, incluso si no hay ninguna pantalla abierta en ese momento.

# Uso de los escuchadores

Para crear un nuevo escuchador que escuche un evento y ejecute un script de acciones, haz clic en **barra de menú -> Personalización -> Administrar escuchadores** mientras **NO** estés en el editor de diseño. Ahí encontrarás una interfaz fácil de usar para crear y administrar escuchadores.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Administrar escuchadores" style="max-width:800px;width:100%;height:auto;">

# Variables del escuchador

Los escuchadores a menudo exponen un tipo especial de variable para sus acciones, requisitos y placeholders anidados.
Estas variables se pueden acceder como placeholders (en efecto, son placeholders).

Puedes usar estas variables simplemente escribiendo sus nombres con el prefijo `$$` en campos de texto, de forma similar a como usarías un placeholder normal.

Por ejemplo, si usas el escuchador **On Keyboard Key Pressed** y quieres imprimir el nombre de la tecla en el registro mediante la acción **Print to Log**, usarías algo como `¡Tecla presionada! La tecla es: $$key_name` como entrada para el mensaje que la acción debe imprimir. El placeholder de la variable luego se reemplazará con el nombre real de la tecla.

> Aunque se llaman "variables", no tienen ninguna relación con el [sistema de variables](/variables) normal de FancyMenu. No puedes establecer estas variables, ya que son **de solo lectura**. Tampoco puedes usar acciones, requisitos ni placeholders pensados para el sistema de variables de FancyMenu con estas variables especiales del escuchador, así que **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** o **Set Variable Value [FM Variable]** no funcionarán con variables de escuchador.
{.is-warning}

# Escuchadores en detalle

Esta lista debería incluir la mayoría, si no es que todos, los escuchadores de FancyMenu. Es posible que la lista no siempre esté actualizada debido a las actualizaciones del mod.

## On Markdown Text Clicked
- Se activa cuando se hace clic en texto Markdown con un evento `click:`, por ejemplo `[Abrir](click:open_menu)`.
- Variables:
  - `$$text_event_id` – ID del evento del enlace Markdown

## On Markdown Text Hovered
- Se activa cuando se pasa el cursor sobre texto Markdown con un evento `hover:`, por ejemplo `[Pista](hover:show_hint)`.
- Variables:
  - `$$text_event_id` – ID del evento del enlace Markdown

## On ZIP Extracted via Action
- Se activa cuando termina la acción **Extract ZIP File In Game Directory**.
- Variables:
  - `$$source_zip_path` – ruta de origen del ZIP resuelta
  - `$$target_folder_path` – ruta de destino de extracción resuelta
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – texto de error cuando falla la extracción

## On Element Spawned
- Se activa cuando un elemento se genera mediante una acción o un flujo de generación de elementos con script.
- Variables:
  - `$$element_type` – tipo de elemento generado
  - `$$element_identifier` – identificador del elemento generado
  - `$$target_screen` – identificador de la pantalla destino

## On Animated Texture Started Playing
- Se activa cuando una textura animada comienza a reproducirse.
- Variables:
  - `$$texture_source` – origen de la textura
  - `$$texture_source_type` – tipo de origen
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing
- Se activa cuando una textura animada termina de reproducirse.
- Variables:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed
- Se activa cuando un elemento de video o el fondo de video del menú cambia su estado de reproducción.
- Variables:
  - `$$video_source` – origen del video
  - `$$video_source_type` – tipo de origen
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` o `FINISHED`

## On System Message Received in Chat
- Se activa cuando el cliente recibe un mensaje de chat del sistema, como una respuesta de comando.
- Variables:
  - `$$system_message_string` – mensaje en texto plano
  - `$$system_message_component` – componente JSON

## On FM Data Received
- Se activa cuando un servidor envía FM Data a este cliente mediante `/fmdata send`.
- Variables:
  - `$$data_identifier` – cadena del identificador de datos
  - `$$data` – carga útil de datos
  - `$$sent_by` – IP del servidor o `integrated_server`

## On Remote Server Connected
- Se activa cuando FancyMenu inicializa una conexión con un servidor remoto.
- Variables:
  - `$$request_id` – ID de solicitud en caché
  - `$$remote_server_url` – URL del servidor remoto

## On Remote Server Data Received
- Se activa cuando se reciben datos de texto de un servidor remoto conectado.
- Variables:
  - `$$request_id` – ID de solicitud
  - `$$remote_server_url` – URL del servidor remoto
  - `$$data` – carga útil recibida

## On Remote Server Connection Closed
- Se activa cuando se cierra una conexión con un servidor remoto.
- Variables:
  - `$$request_id` – ID de solicitud
  - `$$remote_server_url` – URL del servidor remoto
  - `$$intentionally_closed` – TRUE si se cerró mediante una acción
  - `$$crashed` – TRUE si la conexión falló inesperadamente
  - `$$unknown_close_reason` – TRUE si no había una razón de cierre conocida disponible

## On Keyboard Key Pressed
- Se activa cada vez que se presiona una tecla (se repite mientras se mantiene presionada; funciona en pantallas y en el juego).
- Variables:
  - `$$key_name` – nombre visible de la tecla
  - `$$key_keycode` – código de tecla GLFW
  - `$$key_scancode` – código de escaneo GLFW
  - `$$key_modifiers` – máscara de bits de modificadores activos

## On Keyboard Key Released
- Se activa cuando se suelta una tecla (pantallas y en el juego).
- Variables:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- Se activa cuando se escribe un carácter mientras hay una pantalla abierta.
- Variables:
  - `$$char` – carácter escrito

## On Mouse Moved in Screen
- Se activa cada vez que el mouse se mueve mientras hay una pantalla abierta.
- Variables:
  - `$$mouse_pos_x` – X actual
  - `$$mouse_pos_y` – Y actual
  - `$$mouse_move_delta_x` – delta en X desde el último evento
  - `$$mouse_move_delta_y` – delta en Y desde el último evento

## On Mouse Button Clicked
- Se activa cuando se presiona un botón del mouse (pantallas y en el juego).
- Variables:
  - `$$button` – izquierdo/derecho/medio
  - `$$mouse_pos_x` – X actual
  - `$$mouse_pos_y` – Y actual

## On Mouse Button Released
- Se activa cuando se suelta un botón del mouse (pantallas y en el juego).
- Variables:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- Se activa cuando se desplaza la rueda del mouse mientras hay una pantalla abierta.
- Variables:
  - `$$scroll_delta_y` – cantidad de desplazamiento vertical

## On Screen Opened
- Se ejecuta justo después de que cualquier pantalla se vuelve activa; se puede usar para anularla.
- Variables:
  - `$$screen_identifier` – identificador de la pantalla abierta

## On Screen Closed
- Se ejecuta inmediatamente después de que una pantalla se cierra.
- Variables:
  - `$$screen_identifier` – identificador de la pantalla cerrada

## On Quit Minecraft
- Se activa una vez cuando el cliente comienza a cerrarse.
- Variables:
  - `$$timestamp_millis` – milisegundos desde epoch cuando se sale
  - `$$timestamp_iso` – marca de tiempo ISO-8601 del momento de salida

## On Death
- Se ejecuta cuando se abre la pantalla de muerte vanilla para el jugador local.
- Variables:
  - `$$days_survived` – días desde la última muerte
  - `$$death_reason_string` – causa en texto plano
  - `$$death_reason_component` – causa como componente JSON
  - `$$death_pos_x` – coordenada X de la muerte
  - `$$death_pos_y` – coordenada Y de la muerte
  - `$$death_pos_z` – coordenada Z de la muerte

## On Variable Updated [FM Variable]
- Se activa cada vez que se establece o actualiza una variable de FancyMenu.
- Variables:
  - `$$var_name` – nombre de la variable
  - `$$old_value` – valor anterior
  - `$$new_value` – valor nuevo

## On File Downloaded via Action
- Se activa después de que termina la acción “Download File to Game Directory”.
- Variables:
  - `$$download_url` – origen de la descarga
  - `$$target_file_path` – ruta del archivo guardado
  - `$$download_succeeded` – true/false

## On File Selected
- Se activa después de que se completa la acción “Select File”.
- Variables:
  - `$$selected_file_path` – ruta absoluta del archivo elegido o vacío si se canceló
  - `$$target_file_path` – ruta resuelta dentro de la instancia
  - `$$selection_succeeded` – true si la copia tuvo éxito
  - `$$selection_cancelled` – true si se cerró el diálogo
  - `$$failure_reason` – información del error si falla

## On Chat Message Received
- Se activa cuando una línea normal de chat de un jugador aparece en el cliente.
- Variables:
  - `$$chat_message_string` – línea en texto plano
  - `$$chat_message_component` – componente JSON completo
  - `$$sender_uuid` – UUID del remitente o ERROR
  - `$$sender_name` – nombre del remitente o ERROR

## On Chat Message Sent
- Se activa cuando el jugador local envía un mensaje de chat.
- Variables:
  - `$$chat_message_string` – línea en texto plano
  - `$$chat_message_component` – componente JSON completo

## On Effect Gained
- Se activa cuando el jugador obtiene un efecto de estado.
- Variables:
  - `$$effect_key` – ubicación de recurso del efecto
  - `$$effect_type` – positivo/negativo/neutro
  - `$$effect_duration` – ticks restantes

## On Effect Lost
- Se activa cuando el jugador pierde un efecto de estado.
- Variables:
  - `$$effect_key` – efecto expirado
  - `$$effect_type` – categoría

## On Experience Changed
- Se activa cada vez que cambia la XP total del jugador.
- Variables:
  - `$$new_experience_amount` – después del cambio
  - `$$old_experience_amount` – antes del cambio
  - `$$is_level_up` – TRUE si el nivel aumentó

## On Damage Taken
- Se activa una vez por golpe cuando el jugador recibe daño.
- Variables:
  - `$$damage_amount` – salud removida
  - `$$damage_type` – ubicación de recurso del tipo de daño
  - `$$is_fatal_damage` – TRUE si fue letal
  - `$$damage_source` – ubicación de recurso del atacante o NONE

## On Started Freezing
- Se activa cuando el jugador empieza a congelarse.
- Variables:
  - `$$freezing_intensity` – 0.0 nada, 1.0 completamente congelado

## On Stopped Freezing
- Se activa cuando el jugador deja de congelarse.
- Variables:
  - (ninguna)

## On Fully Frozen
- Se activa una vez cuando el jugador queda completamente congelado.
- Variables:
  - (ninguna)

## On Start Looking At Block
- Se activa una vez cuando la mira apunta por primera vez a un bloque (distancia máxima de 20 bloques).
- Variables:
  - `$$block_key` – bloque objetivo
  - `$$block_pos_x` – X del bloque
  - `$$block_pos_y` – Y del bloque
  - `$$block_pos_z` – Z del bloque
  - `$$distance_to_player` – de los ojos al punto de impacto

## On Stop Looking At Block
- Se activa cuando la mira deja de apuntar a un bloque (reporta el último bloque objetivo, máximo 20 bloques).
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- Se activa una vez cuando la mira apunta por primera vez a una entidad (máximo 20 bloques).
- Variables:
  - `$$entity_key` – tipo de entidad objetivo
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- Se activa cuando la mira deja de apuntar a una entidad (reporta la última entidad objetivo, máximo 20 bloques).
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **Requiere FancyMenu en el servidor.** Se activa cuando cualquier entidad aparece en cualquier parte del mundo/servidor conectado.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player` – −1 si está en otra dimensión
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **Requiere FancyMenu en el servidor.** Se activa cuando cualquier entidad muere en el mundo/servidor conectado.
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

## On Entity Starts Being In Sight
- Se activa cuando una entidad se vuelve visible por primera vez dentro de 200 bloques.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- Se activa cuando una entidad que antes era visible sale de la vista o se mueve más allá de 200 bloques.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- Se activa cuando el jugador interactúa correctamente con una entidad.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- Se activa cuando el jugador comienza a montar una entidad.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- Se activa cuando el jugador deja de montar su entidad actual.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- Se activa cuando el jugador rompe un bloque.
- Variables:
  - `$$block_key`
  - `$$broke_with_item_key` – herramienta usada o EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- Se activa cuando el jugador coloca un bloque.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- Se activa cuando el jugador interactúa correctamente con un bloque.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- Se activa cuando el jugador pisa un bloque.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- Se activa cuando el jugador entra en un bioma nuevo.
- Variables:
  - `$$biome_key` – bioma al que se entró

## On Leave Biome
- Se activa cuando el jugador sale de su bioma actual.
- Variables:
  - `$$biome_key` – bioma que acaba de dejar

## On Enter Structure
- **Requiere FancyMenu en el servidor.** Detección aproximada del área de estructuras; puede activarse cerca, arriba o debajo de la estructura.
- Variables:
  - `$$structure_key` – estructura a la que se entró

## On Leave Structure
- **Requiere FancyMenu en el servidor.** Detección aproximada; puede activarse cerca de la huella de la estructura.
- Variables:
  - `$$structure_key` – estructura que acaba de dejar

## On Enter Structure (High Precision)
- **Requiere FancyMenu en el servidor.** Se activa cuando el jugador entra en los volúmenes de colisión de una estructura.
- Variables:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **Requiere FancyMenu en el servidor.** Se activa después de que el jugador salga de los volúmenes de colisión de una estructura.
- Variables:
  - `$$structure_key`

## On Dimension Entered
- Se activa cuando el jugador entra en una nueva dimensión.
- Variables:
  - `$$dimension_key` – dimensión a la que se entró

## On Start Swimming
- Se activa cuando el jugador comienza a nadar.
- Variables:
  - `$$fluid_type` – ubicación de recurso del fluido

## On Stop Swimming
- Se activa cuando el jugador deja de nadar.
- Variables:
  - `$$fluid_type` – fluido en el que dejó de nadar

## On Start Touching Fluid
- Se activa cuando el jugador comienza a tocar un fluido.
- Variables:
  - `$$fluid_type` – fluido tocado

## On Stop Touching Fluid
- Se activa cuando el jugador deja de tocar un fluido.
- Variables:
  - `$$fluid_type` – fluido que ya no se toca

## On Music Track Started
- Se activa cuando comienza una nueva pista de música.
- Variables:
  - `$$track_resource_location` – archivo de audio
  - `$$track_display_name` – nombre legible o UNKNOWN
  - `$$track_artist` – artista o UNKNOWN
  - `$$track_duration_ms` – milisegundos (0 si se desconoce)

## On Music Track Stopped
- Se activa cuando la pista de música actual termina o es reemplazada.
- Variables:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- Se activa cuando un sonido posicional del mundo comienza cerca del jugador.
- Variables:
  - `$$sound_resource_location` – archivo de sonido
  - `$$sound_display_name` – nombre de subtítulo cuando esté disponible
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – grados 0–360 relativos a la dirección a la que se mira

## On Weather Changed
- Se activa cuando el clima cambia global o localmente (un cambio de bioma o entrar a interiores puede volver a activarlo).
- Variables:
  - `$$weather_type` – despejado/lluvia/tormenta
  - `$$weather_can_snow` – TRUE si se renderiza nieve
  - `$$weather_can_rain` – TRUE si se renderiza lluvia

## On Started Burning
- Se activa cuando el jugador comienza a arder.
- Variables:
  - (ninguna)

## On Stopped Burning
- Se activa cuando el jugador deja de arder.
- Variables:
  - (ninguna)

## On Started Drowning
- Se activa cuando el jugador empieza a recibir daño por ahogamiento.
- Variables:
  - (ninguna)

## On Position Changed
- Se activa cada vez que cambia la posición de bloque del jugador.
- Variables:
  - `$$old_pos_x` – bloque X anterior
  - `$$old_pos_y` – bloque Y anterior
  - `$$old_pos_z` – bloque Z anterior
  - `$$new_pos_x` – bloque X nuevo
  - `$$new_pos_y` – bloque Y nuevo
  - `$$new_pos_z` – bloque Z nuevo

## On Started Running
- Se activa cuando el jugador empieza a correr rápido.
- Variables:
  - (ninguna)

## On Stopped Running
- Se activa cuando el jugador deja de correr rápido.
- Variables:
  - (ninguna)

## On Jump
- Se activa cada vez que el jugador salta.
- Variables:
  - (ninguna)

## On Server Joined
- Se activa después de unirse correctamente a un servidor multijugador.
- Variables:
  - `$$server_ip` – dirección del servidor al que se unió

## On Server Left
- Se activa después de desconectarse de un servidor multijugador.
- Variables:
  - `$$server_ip` – dirección del servidor que se dejó

## Singleplayer World Entered
- Se activa después de que un mundo de un jugador termina de cargar y se devuelve el control.
- Variables:
  - `$$world_name` – nombre visible
  - `$$world_save_path` – carpeta de guardado absoluta
  - `$$world_difficulty` – clave de dificultad
  - `$$world_cheats_allowed` – TRUE si los trucos están habilitados
  - `$$world_icon_path` – ruta absoluta del ícono
  - `$$world_is_first_join` – TRUE en la primera visita

## Singleplayer World Left
- Se activa después de que un mundo de un jugador se cierra y termina de guardarse.
- Variables:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- Se activa cuando otro jugador entra al mundo/servidor actual.
- Variables:
  - `$$player_name` – nombre del jugador que se une
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- Se activa cuando otro jugador sale del mundo/servidor actual.
- Variables:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- Se activa cuando otro jugador en el mundo actual muere.
- Variables:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- Se activa cuando el jugador recoge una entidad de objeto.
- Variables:
  - `$$item_key` – ubicación de recurso del objeto recogido

## On Item Dropped
- Se activa cuando el jugador tira un objeto de su inventario.
- Variables:
  - `$$item_key` – ubicación de recurso del objeto tirado

## On Item Consumed
- Se activa cuando el jugador termina de consumir un objeto.
- Variables:
  - `$$item_key` – objeto consumido

## On Item Hovered in Inventory
- Se activa cuando el usuario pasa el cursor sobre un objeto en cualquier pantalla de inventario.
- Variables:
  - `$$item_key` – ubicación de recurso del objeto señalado
  - `$$item_display_name_string` – nombre visible del objeto en texto plano
  - `$$item_display_name_json` – nombre visible del objeto como componente JSON

## On Item Used
- Se activa cuando el jugador usa un objeto.
- Variables:
  - `$$item_key` – objeto usado
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – tipo de entidad objetivo o vacío
  - `$$used_on_block_key` – bloque objetivo o vacío
  - `$$target_pos_x` – X objetivo o -1
  - `$$target_pos_y` – Y objetivo o -1
  - `$$target_pos_z` – Z objetivo o -1

## On Item Broke
- Se activa cuando un objeto en el inventario del jugador se rompe.
- Variables:
  - `$$item_key` – objeto roto
  - `$$item_type` – herramienta/armadura/otro
