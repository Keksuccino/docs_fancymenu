---
title: Listeners
description: Cómo crear y usar listeners en FancyMenu.
---

# Listeners

A partir de FancyMenu v3.8.0, hay una nueva función llamada "listeners".

Los listeners ejecutan scripts de acción cuando se producen eventos concretos del cliente o del juego.
Pueden exponer variables para las acciones, placeholders y requisitos anidados dentro del listener.

A diferencia de la mayoría de cosas en FancyMenu, los listeners no están vinculados a una pantalla ni a un overlay. Se ejecutan constantemente en segundo plano, escuchando sus eventos. En cuanto se activa un listener, ejecuta su script de acción, incluso si no hay ninguna pantalla abierta en ese momento.

# Uso de Listeners

Para crear un nuevo listener que escuche un evento y ejecute un script de acción, haz clic en **barra de menú -> Personalización -> Gestionar Listeners** mientras **NO** estés en el editor de diseño. Allí encontrarás una interfaz fácil de usar para crear y gestionar listeners.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Gestionar listeners" style="max-width:800px;width:100%;height:auto;">

# Variables de Listener

Los listeners suelen exponer un tipo especial de variable para sus acciones, requisitos y placeholders anidados.
Estas variables se pueden acceder como si fueran placeholders (de hecho, funcionan como placeholders).

Puedes usar estas variables simplemente escribiendo sus nombres con el prefijo `$$` en los campos de texto, de forma similar a como usarías un placeholder normal.

Por ejemplo, si usas el listener **On Keyboard Key Pressed** y quieres imprimir el nombre de la tecla en el log mediante la acción **Print to Log**, usarías algo como `¡Tecla pulsada! La tecla es: $$key_name` como entrada para el mensaje que debe imprimir la acción. Más adelante, el placeholder de la variable se sustituirá por el nombre real de la tecla.

> Aunque estas se llamen "variables", no tienen ninguna relación con el [sistema de variables](/variables) normal de FancyMenu. No puedes establecer estas variables, ya que son **de solo lectura**. Tampoco puedes usar ninguna acción, requisito o placeholder pensado para el sistema de variables de FancyMenu con estas variables especiales de listener, así que usar **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** o **Set Variable Value [FM Variable]** no funcionará con las variables de listener.
{.is-warning}

# Listeners en detalle

Esta lista debería incluir la mayoría, si no todos, los listeners de FancyMenu. Es posible que la lista no esté siempre actualizada debido a las actualizaciones del mod.

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
  - `$$failure_reason` – texto del error cuando falla la extracción

## On Element Spawned
- Se activa cuando un elemento se genera mediante una acción o un flujo de generación de elementos mediante script.
- Variables:
  - `$$element_type` – tipo de elemento generado
  - `$$element_identifier` – identificador del elemento generado
  - `$$target_screen` – identificador de la pantalla de destino

## On Animated Texture Started Playing
- Se activa cuando una textura animada empieza a reproducirse.
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
- Se activa cuando un elemento de vídeo o el fondo del menú con vídeo cambia de estado de reproducción.
- Variables:
  - `$$video_source` – origen del vídeo
  - `$$video_source_type` – tipo de origen
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` o `FINISHED`

## On System Message Received in Chat
- Se activa cuando el cliente recibe un mensaje de sistema del chat, como una respuesta de comando.
- Variables:
  - `$$system_message_string` – mensaje en texto plano
  - `$$system_message_component` – componente JSON

## On FM Data Received
- Se activa cuando un servidor envía FM Data a este cliente mediante `/fmdata send`.
- Variables:
  - `$$data_identifier` – cadena identificadora de los datos
  - `$$data` – carga de datos
  - `$$sent_by` – IP del servidor o `integrated_server`

## On Remote Server Connected
- Se activa cuando FancyMenu inicializa una conexión con un servidor remoto.
- Variables:
  - `$$request_id` – ID de solicitud almacenado en caché
  - `$$remote_server_url` – URL del servidor remoto

## On Remote Server Data Received
- Se activa cuando se reciben datos de texto de un servidor remoto conectado.
- Variables:
  - `$$request_id` – ID de solicitud
  - `$$remote_server_url` – URL del servidor remoto
  - `$$data` – carga recibida

## On Remote Server Connection Closed
- Se activa cuando se cierra la conexión con un servidor remoto.
- Variables:
  - `$$request_id` – ID de solicitud
  - `$$remote_server_url` – URL del servidor remoto
  - `$$intentionally_closed` – TRUE si se cerró mediante una acción
  - `$$crashed` – TRUE si la conexión falló inesperadamente
  - `$$unknown_close_reason` – TRUE si no había un motivo de cierre conocido disponible

## On Keyboard Key Pressed
- Se dispara cada vez que se pulsa una tecla (se repite mientras se mantiene pulsada; funciona en pantallas y en el juego).
- Variables:
  - `$$key_name` – nombre visible de la tecla
  - `$$key_keycode` – código de tecla GLFW
  - `$$key_scancode` – código de escaneo GLFW
  - `$$key_modifiers` – máscara de modificadores activos

## On Keyboard Key Released
- Se dispara cuando se suelta una tecla (pantallas y en el juego).
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
- Se activa siempre que se mueve el ratón mientras hay una pantalla abierta.
- Variables:
  - `$$mouse_pos_x` – X actual
  - `$$mouse_pos_y` – Y actual
  - `$$mouse_move_delta_x` – delta en X desde el último evento
  - `$$mouse_move_delta_y` – delta en Y desde el último evento

## On Mouse Button Clicked
- Se activa cuando se pulsa un botón del ratón (pantallas y en el juego).
- Variables:
  - `$$button` – izquierda/derecha/central
  - `$$mouse_pos_x` – X actual
  - `$$mouse_pos_y` – Y actual

## On Mouse Button Released
- Se activa cuando se suelta un botón del ratón (pantallas y en el juego).
- Variables:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- Se activa cuando se mueve la rueda del ratón mientras hay una pantalla abierta.
- Variables:
  - `$$scroll_delta_y` – cantidad de desplazamiento vertical

## On Screen Opened
- Se ejecuta justo después de que cualquier pantalla se vuelva activa; puede usarse para anularla.
- Variables:
  - `$$screen_identifier` – identificador de la pantalla abierta

## On Screen Closed
- Se ejecuta inmediatamente después de que una pantalla se cierre.
- Variables:
  - `$$screen_identifier` – identificador de la pantalla cerrada

## On Quit Minecraft
- Se activa una vez cuando el cliente empieza a cerrarse.
- Variables:
  - `$$timestamp_millis` – milisegundos desde la época en el momento de salir
  - `$$timestamp_iso` – marca de tiempo ISO-8601 del momento de salida

## On Death
- Se ejecuta cuando se abre la pantalla de muerte de vanilla para el jugador local.
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
- Se activa después de que termine la acción “Download File to Game Directory”.
- Variables:
  - `$$download_url` – origen de la descarga
  - `$$target_file_path` – ruta del archivo guardado
  - `$$download_succeeded` – true/false

## On File Selected
- Se activa después de completar la acción “Select File”.
- Variables:
  - `$$selected_file_path` – ruta absoluta del archivo elegido o vacío si se canceló
  - `$$target_file_path` – ruta resuelta dentro de la instancia
  - `$$selection_succeeded` – true si la copia se realizó correctamente
  - `$$selection_cancelled` – true si se cerró el diálogo
  - `$$failure_reason` – información del error en caso de fallo

## On Chat Message Received
- Se activa cuando aparece en el cliente una línea normal de chat de jugador.
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
- Se activa cada vez que cambia la experiencia total del jugador.
- Variables:
  - `$$new_experience_amount` – después del cambio
  - `$$old_experience_amount` – antes del cambio
  - `$$is_level_up` – TRUE si el nivel ha aumentado

## On Damage Taken
- Se activa una vez por golpe cuando el jugador recibe daño.
- Variables:
  - `$$damage_amount` – vida reducida
  - `$$damage_type` – ubicación de recurso del tipo de daño
  - `$$is_fatal_damage` – TRUE si es letal
  - `$$damage_source` – ubicación de recurso del atacante o NONE

## On Started Freezing
- Se activa cuando el jugador empieza a congelarse.
- Variables:
  - `$$freezing_intensity` – 0.0 sin congelación, 1.0 totalmente congelado

## On Stopped Freezing
- Se activa cuando el jugador deja de congelarse.
- Variables:
  - (ninguna)

## On Fully Frozen
- Se activa una vez cuando el jugador queda totalmente congelado.
- Variables:
  - (ninguna)

## On Start Looking At Block
- Se activa una vez cuando la mira apunta por primera vez a un bloque (distancia máxima de 20 bloques).
- Variables:
  - `$$block_key` – bloque objetivo
  - `$$block_pos_x` – X del bloque
  - `$$block_pos_y` – Y del bloque
  - `$$block_pos_z` – Z del bloque
  - `$$distance_to_player` – distancia desde los ojos hasta el punto de impacto

## On Stop Looking At Block
- Se activa cuando la mira deja de apuntar a un bloque (informa del último bloque objetivo, máximo 20 bloques).
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
- Se activa cuando la mira deja de apuntar a una entidad (informa de la última entidad objetivo, máximo 20 bloques).
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **Requiere FancyMenu en el servidor.** Se activa cuando cualquier entidad aparece en cualquier lugar del mundo/servidor conectado.
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
- Se activa cuando una entidad pasa a ser visible por primera vez dentro de 200 bloques.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- Se activa cuando una entidad previamente visible sale de la vista o se aleja más de 200 bloques.
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
- Se activa cuando el jugador empieza a montar una entidad.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- Se activa cuando el jugador deja de montar la entidad actual.
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
  - `$$biome_key` – bioma al que se ha प्रवेशado

## On Leave Biome
- Se activa cuando el jugador sale de su bioma actual.
- Variables:
  - `$$biome_key` – bioma que acaba de abandonar

## On Enter Structure
- **Requiere FancyMenu en el servidor.** Detección aproximada del área de la estructura; puede activarse cerca, encima o debajo de la estructura.
- Variables:
  - `$$structure_key` – estructura a la que se ha entrado

## On Leave Structure
- **Requiere FancyMenu en el servidor.** Detección aproximada; puede activarse cerca del perímetro de la estructura.
- Variables:
  - `$$structure_key` – estructura que acaba de abandonarse

## On Enter Structure (High Precision)
- **Requiere FancyMenu en el servidor.** Se activa cuando el jugador entra en las cajas delimitadoras de una estructura.
- Variables:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **Requiere FancyMenu en el servidor.** Se activa después de que el jugador salga de las cajas delimitadoras de una estructura.
- Variables:
  - `$$structure_key`

## On Dimension Entered
- Se activa cuando el jugador entra en una nueva dimensión.
- Variables:
  - `$$dimension_key` – dimensión a la que se ha entrado

## On Start Swimming
- Se activa cuando el jugador empieza a nadar.
- Variables:
  - `$$fluid_type` – ubicación de recurso del fluido

## On Stop Swimming
- Se activa cuando el jugador deja de nadar.
- Variables:
  - `$$fluid_type` – fluido en el que se dejó de nadar

## On Start Touching Fluid
- Se activa cuando el jugador empieza a tocar un fluido.
- Variables:
  - `$$fluid_type` – fluido tocado

## On Stop Touching Fluid
- Se activa cuando el jugador deja de tocar un fluido.
- Variables:
  - `$$fluid_type` – fluido que ya no se toca

## On Music Track Started
- Se activa cuando comienza una nueva pista musical.
- Variables:
  - `$$track_resource_location` – archivo de audio
  - `$$track_display_name` – nombre legible o UNKNOWN
  - `$$track_artist` – artista o UNKNOWN
  - `$$track_duration_ms` – milisegundos (0 si se desconoce)

## On Music Track Stopped
- Se activa cuando la pista musical actual termina o es reemplazada.
- Variables:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- Se activa cuando un sonido posicional del mundo comienza cerca del jugador.
- Variables:
  - `$$sound_resource_location` – archivo de sonido
  - `$$sound_display_name` – nombre del subtítulo cuando está disponible
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – grados 0–360 relativos a la dirección de la mirada

## On Weather Changed
- Se activa cuando el clima cambia global o localmente (un cambio de bioma o entrar en interiores puede volver a dispararlo).
- Variables:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE si se renderiza nieve
  - `$$weather_can_rain` – TRUE si se renderiza lluvia

## On Started Burning
- Se activa cuando el jugador empieza a arder.
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
  - `$$old_pos_x` – X anterior del bloque
  - `$$old_pos_y` – Y anterior del bloque
  - `$$old_pos_z` – Z anterior del bloque
  - `$$new_pos_x` – nueva X del bloque
  - `$$new_pos_y` – nueva Y del bloque
  - `$$new_pos_z` – nueva Z del bloque

## On Started Running
- Se activa cuando el jugador empieza a esprintar.
- Variables:
  - (ninguna)

## On Stopped Running
- Se activa cuando el jugador deja de esprintar.
- Variables:
  - (ninguna)

## On Jump
- Se activa cada vez que el jugador salta.
- Variables:
  - (ninguna)

## On Server Joined
- Se activa después de unirse correctamente a un servidor multijugador.
- Variables:
  - `$$server_ip` – dirección del servidor al que se ha unido

## On Server Left
- Se activa después de desconectarse de un servidor multijugador.
- Variables:
  - `$$server_ip` – dirección del servidor abandonado

## Singleplayer World Entered
- Se activa después de que un mundo de un jugador termine de cargar y se devuelva el control.
- Variables:
  - `$$world_name` – nombre visible
  - `$$world_save_path` – carpeta de guardado absoluta
  - `$$world_difficulty` – clave de dificultad
  - `$$world_cheats_allowed` – TRUE si los trucos están activados
  - `$$world_icon_path` – ruta absoluta del icono
  - `$$world_is_first_join` – TRUE en la primera visita

## Singleplayer World Left
- Se activa después de que un mundo de un jugador se cierre y termine de guardarse.
- Variables:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- Se activa cuando otro jugador se une al mundo/servidor actual.
- Variables:
  - `$$player_name` – nombre del jugador que se une
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- Se activa cuando otro jugador abandona el mundo/servidor actual.
- Variables:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- Se activa cuando otro jugador del mundo actual muere.
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
- Se activa cuando el jugador suelta un objeto de su inventario.
- Variables:
  - `$$item_key` – ubicación de recurso del objeto soltado

## On Item Consumed
- Se activa cuando el jugador termina de consumir un objeto.
- Variables:
  - `$$item_key` – objeto consumido

## On Item Hovered in Inventory
- Se activa cuando el usuario pasa el cursor sobre un objeto en cualquier pantalla de inventario.
- Variables:
  - `$$item_key` – ubicación de recurso del objeto sobre el que se pasa el cursor
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
- Se activa cuando se rompe un objeto del inventario del jugador.
- Variables:
  - `$$item_key` – objeto roto
  - `$$item_type` – herramienta/armadura/otro
