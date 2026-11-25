---
title: Detectores
description: >-
  Ejecuta scripts de acciones cuando ocurre algo en el juego, como pulsar una
  tecla, recibir un mensaje de chat o conseguir un logro.
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# Detectores

Los detectores ejecutan un [script de acciones](/action-scripts) cuando ocurre algo en el juego: se pulsa una tecla, se abre una pantalla, consigues un logro y muchas cosas más. Funcionan en todos los menús y mientras juegas, y no pertenecen a ninguna disposición.

La mayoría de los detectores también proporcionan al script variables sobre lo que ha ocurrido, como el nombre de la tecla pulsada.

<img width="800" alt="Se pulsan teclas en la pantalla del título y aparece un aviso con el nombre de cada tecla pulsada" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> Un detector puede ejecutar acciones de archivo, red, comandos, portapapeles, paquetes de recursos y enlaces aunque no haya ningún menú abierto. Usa únicamente detectores de perfiles y archivos de personas en las que confíes.

# Añadir un detector

<img width="800" alt="Se abre Manage Listeners, se añade un detector On Keyboard Key Pressed con una acción Show Toast y se pulsa H para probarlo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. Abre **barra de menú -> Personalización -> Manage Listeners**.
2. Haz clic en **Add Listener**.
3. Haz clic en el evento en **Available Listeners**. La barra de búsqueda permite encontrar detectores por su nombre y descripción.
   - **Listener Description** muestra lo que hace el detector y las variables que proporciona.
   - **Copy Variables to Clipboard** copia los nombres de sus variables.
   - **Pop Out Description** abre la descripción en una ventana independiente.
4. Haz clic en **Done** o haz doble clic en el detector. Se abrirá el editor de scripts de acciones.
5. Añade las acciones que quieras ejecutar y haz clic en **Done**. Consulta [Scripts de acciones](/action-scripts#making-an-action-script).
6. Haz clic en **Done** en **Manage Listeners** para guardar los cambios. El detector empezará a funcionar de inmediato.

**Cancel** descarta todos los cambios que hayas hecho en **Manage Listeners**, después de pedirte confirmación.

# Gestionar detectores

<img width="800" alt="La ventana Manage Listeners con cinco detectores, uno seleccionado y su script de acciones a la derecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- Haz clic en un detector para ver su tipo y su script de acciones a la derecha.
- **Edit Actions** o hacer clic derecho en un detector abre su script de acciones.
- Haz doble clic en el nombre de un detector para cambiarlo, por ejemplo, a `Tecla de ayuda`. Pulsa `Enter` para guardar el nombre o `Esc` para cancelar. Si el nombre está vacío, se volverá a mostrar el tipo de detector.
- **Remove Listener** elimina el detector seleccionado.
- **Export for AI** copia el detector seleccionado o todos los detectores para un [chat de IA](/export-for-ai), incluidos los cambios que no hayas guardado.

Los detectores se guardan en `config/fancymenu/listener_instances.txt` (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations)). Cada [perfil](/profiles) tiene sus propios detectores.

# Variables de los detectores

Las variables de un detector empiezan por `$$` y funcionan en todo su propio script: en todos los valores de las acciones y en los requisitos de las [sentencias IF](/action-scripts#if-else-if-and-else). Se distingue entre mayúsculas y minúsculas. A continuación se enumeran las variables de cada detector; también aparecen en su descripción dentro del selector de detectores.

<img width="800" alt="El selector de detectores con On Achievement Unlocked seleccionado y una descripción que enumera sus variables" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

Por ejemplo, este detector abre una pantalla de ayuda al pulsar `H`:

1. Añade un detector **On Keyboard Key Pressed**.
2. En su script, usa **Add IF Statement** con el requisito [**Is Text**](/conditions#is-text). Establece **Compare Mode** en **Equals**, **Text** en `$$key_name` y **Compare to Text** en `H`.
3. Dentro del IF, añade [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui) con tu pantalla de ayuda.

Más información sobre las variables de los detectores:

- Las variables de los detectores siempre son texto. Si un detector no puede averiguar un valor, la variable tendrá un valor alternativo, como `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` o ningún valor.
- Las variables de los detectores se rellenan antes que los [marcadores de posición](/placeholders), así que también funcionan dentro de ellos.
- Las variables de los detectores solo existen mientras se ejecuta su script. Para conservar un valor, guárdalo en una de tus [variables](/variables) con [**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable).
- Tus propias variables de **barra de menú -> Personalización -> Manage Variables** también funcionan en los scripts de detectores, con `$$` seguido de su nombre; por ejemplo, `$$coins`. Si una de ellas tiene el mismo nombre que una variable del detector, `$$name` se refiere a la variable del detector. Tus variables con nombres más largos, como `key_name_log`, seguirán funcionando.
- El texto procedente del chat, los servidores, los archivos y otros jugadores puede ser cualquier cosa. No lo insertes directamente en comandos, rutas de archivo ni enlaces.

# Información útil

- Algunos detectores necesitan que FancyMenu esté instalado en el servidor. Se indica en su descripción. En un mundo de un jugador siempre funcionan.
- Algunos detectores se ejecutan muy a menudo, como **On Mouse Moved in Screen**, **On Element Scrolled**, **On Position Changed** y **On World Sound Triggered**. Mantén sus scripts breves y no uses nunca en ellos acciones lentas como [**Reload FancyMenu**](/action-scripts#reload-fancymenu).
- Para sustituir una pantalla con **On Screen Opened**, comprueba primero `$$screen_identifier` con una sentencia IF. De lo contrario, se sustituirán todas las pantallas, incluida la que abras.

# Todos los detectores

Todos los detectores de FancyMenu, ordenados según lo que detectan.

## Teclado y ratón

Para comprobar qué tecla se ha pulsado, usa `$$key_name`. Los códigos numéricos de las teclas no son iguales en todas las versiones de Minecraft.

### Al pulsar una tecla del teclado

**Identificador:** `keyboard_key_pressed`

Se ejecuta al pulsar una tecla, tanto en los menús como mientras juegas. Si mantienes pulsada una tecla, se ejecuta una y otra vez.

- `$$key_name`: el nombre de la tecla, como `H` o `Left Shift`
- `$$key_keycode`: el código numérico de la tecla
- `$$key_scancode`: el código de exploración de la tecla
- `$$key_modifiers`: un número que representa las teclas modificadoras pulsadas al mismo tiempo, como `Shift` y `Ctrl`

### Al soltar una tecla del teclado

**Identificador:** `keyboard_key_released`

Se ejecuta al soltar una tecla, tanto en los menús como mientras juegas.

Proporciona las mismas variables que **Al pulsar una tecla del teclado**: `$$key_name`, `$$key_keycode`, `$$key_scancode` y `$$key_modifiers`.

### Al escribir un carácter en una pantalla

**Identificador:** `keyboard_char_typed`

Se ejecuta por cada carácter que se escribe mientras hay una pantalla abierta.

- `$$char`: el carácter escrito

### Al mover el ratón en una pantalla

**Identificador:** `mouse_moved`

Se ejecuta cada vez que se mueve el ratón mientras hay una pantalla abierta.

- `$$mouse_pos_x`, `$$mouse_pos_y`: la posición del ratón, en píxeles de la interfaz
- `$$mouse_move_delta_x`, `$$mouse_move_delta_y`: cuánto se ha movido desde la última vez

### Al hacer clic con un botón del ratón

**Identificador:** `mouse_button_clicked`

Se ejecuta una vez al pulsar un botón del ratón, tanto en los menús como mientras juegas.

- `$$button`: `left`, `right` o `middle`. Los demás botones muestran su número.
- `$$mouse_pos_x`, `$$mouse_pos_y`: la posición del ratón, en píxeles de la interfaz

### Al soltar un botón del ratón

**Identificador:** `mouse_button_released`

Se ejecuta una vez al soltar un botón del ratón, tanto en los menús como mientras juegas.

Proporciona las mismas variables que **Al hacer clic con un botón del ratón**: `$$button`, `$$mouse_pos_x` y `$$mouse_pos_y`.

### Al desplazar la rueda del ratón en una pantalla

**Identificador:** `mouse_scrolled`

Se ejecuta al girar la rueda del ratón mientras hay una pantalla abierta.

- `$$scroll_delta_y`: cuánto se ha girado la rueda. Es mayor que `0` al desplazar hacia arriba y menor que `0` al desplazar hacia abajo.

## Pantallas y elementos

### Al abrirse una pantalla

**Identificador:** `screen_open`

Se ejecuta justo después de abrirse una pantalla. Una acción [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui) en su script puede sustituirla por otra.

- `$$screen_identifier`: el [identificador](/screen-identifiers) de la pantalla

### Al cerrarse una pantalla

**Identificador:** `screen_close`

Se ejecuta justo después de cerrarse una pantalla.

- `$$screen_identifier`: el [identificador](/screen-identifiers) de la pantalla cerrada

### Al hacer clic en un texto Markdown

**Identificador:** `text_clicked`

Se ejecuta cuando alguien hace clic en un [evento de clic](/text-formatting#click-and-hover-events) de un texto, como `[Leer las normas](click:open_rules)`.

- `$$text_event_id`: el ID del evento, como `open_rules`

### Al pasar el cursor sobre un texto Markdown

**Identificador:** `text_hovered`

Se ejecuta cuando el ratón pasa sobre un [evento al pasar el cursor](/text-formatting#click-and-hover-events) de un texto, como `[¿Qué es esto?](hover:show_hint)`.

- `$$text_event_id`: el ID del evento, como `show_hint`

### Al desplazarse un elemento

**Identificador:** `scroll_area_scrolled`

Se ejecuta cada vez que se desplaza el contenido de un [área desplazable](/scrollable-areas) o de un [elemento de texto](/text-in-menus). Mientras el contenido se desliza, se ejecuta en cada fotograma. No se ejecuta en el editor de disposiciones.

- `$$element_identifier`: el [identificador](/element-identifiers) del elemento
- `$$scroll_x`: cuánto se ha desplazado el contenido horizontalmente, en píxeles
- `$$scroll_y`: cuánto se ha desplazado el contenido hacia abajo, en píxeles
- `$$scroll_percent`: cuánto se ha desplazado el contenido en la dirección principal del elemento, desde `0` (inicio) hasta `100` (final)

### Al desplazarse un elemento hasta el inicio

**Identificador:** `scroll_area_reached_start`

Se ejecuta cuando el contenido de un área desplazable o de un elemento de texto vuelve al inicio.

Proporciona las mismas variables que **Al desplazarse un elemento**: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` y `$$scroll_percent`.

### Al desplazarse un elemento hasta el final

**Identificador:** `scroll_area_reached_end`

Se ejecuta cuando el contenido de un área desplazable o de un elemento de texto llega al final, por ejemplo, cuando alguien se desplaza por todas las normas.

Proporciona las mismas variables que **Al desplazarse un elemento**: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` y `$$scroll_percent`.

### Al empezar a reproducirse una textura animada

**Identificador:** `animated_texture_started_playing`

Se ejecuta cuando empieza a reproducirse una [textura animada](/animations) (GIF, APNG o FMA) y cada vez que vuelve a empezar.

- `$$texture_source`: de dónde procede la textura: una ruta de archivo, un enlace web o una ubicación de recurso
- `$$texture_source_type`: `LOCAL`, `WEB` o `RESOURCE_LOCATION`
- `$$texture_will_restart`: `true` si vuelve a empezar después de esta reproducción; de lo contrario, `false`

### Al terminar de reproducirse una textura animada

**Identificador:** `animated_texture_finished_playing`

Se ejecuta cuando una textura animada termina una reproducción. Si se repite en bucle, se ejecuta justo antes de que vuelva a empezar.

Proporciona las mismas variables que **Al empezar a reproducirse una textura animada**: `$$texture_source`, `$$texture_source_type` y `$$texture_will_restart`.

### Al cambiar el estado de reproducción de un vídeo

**Identificador:** `video_playback_status_changed`

Se ejecuta cuando un elemento [vídeo](/video) o un fondo de menú empieza, se pausa, se detiene o termina.

- `$$video_source`: de dónde procede el vídeo: una ruta de archivo, un enlace web o una ubicación de recurso
- `$$video_source_type`: `LOCAL`, `WEB` o `RESOURCE_LOCATION`
- `$$is_looping`: `true` si el vídeo se repite en bucle; de lo contrario, `false`
- `$$new_status`:
  - `PLAYING`: el vídeo ha empezado o se ha reanudado
  - `PAUSED`: el vídeo se ha pausado
  - `STOPPED`: el vídeo se ha detenido
  - `FINISHED`: el vídeo ha llegado al final. Los vídeos en bucle también lo indican justo antes de volver a empezar.

## Variables, archivos y datos

### Al actualizarse una variable [FM Variable]

**Identificador:** `fm_variable_updated`

Se ejecuta cada vez que se establece una [variable](/variables).

- `$$var_name`: el nombre de la variable
- `$$old_value`: su valor anterior
- `$$new_value`: su nuevo valor

En las variables de lista, ambos valores corresponden a la lista completa en forma de matriz JSON, como `["Diamonds","Emeralds"]`.

### Al empezar a descargarse un archivo mediante una acción

**Identificador:** `file_download_started_via_action`

Se ejecuta cuando empieza una descarga de [**Download File to Game Directory**](/action-scripts#download-file-to-game-directory), en cuanto se conoce el nombre del archivo. El archivo no aparecerá en su ruta hasta que termine la descarga; para saber cuándo está listo, usa **On File Downloaded via Action**.

- `$$download_url`: el enlace del archivo
- `$$target_file_path`: dónde se guardará el archivo

### Al descargarse un archivo mediante una acción

**Identificador:** `file_downloaded_via_action`

Se ejecuta cuando termina o falla una descarga de [**Download File to Game Directory**](/action-scripts#download-file-to-game-directory).

- `$$download_url`: el enlace del archivo
- `$$target_file_path`: dónde se ha guardado el archivo. Si la descarga ha fallado, puede que solo indique la carpeta.
- `$$download_succeeded`: `true` o `false`

### Al seleccionar un archivo

**Identificador:** `file_selected_via_action`

Se ejecuta cuando termina [**Select File from System**](/action-scripts#select-file-from-system): se ha copiado el archivo, se ha cancelado el selector de archivos o se ha producido un error.

- `$$selected_file_path`: la ruta completa del archivo elegido. Está vacío si se ha cancelado el selector.
- `$$target_file_path`: dónde se ha copiado el archivo, dentro de la carpeta del juego
- `$$selection_succeeded`: `true` si se ha copiado el archivo
- `$$selection_cancelled`: `true` si se ha cerrado el selector sin elegir ningún archivo
- `$$failure_reason`: lo que ha fallado. Está vacío si no se ha producido ningún error.

### Al extraer un ZIP mediante una acción

**Identificador:** `zip_extracted_via_action`

Se ejecuta cuando termina [**Extract ZIP File In Game Directory**](/action-scripts#extract-zip-file-in-game-directory).

- `$$source_zip_path`: el archivo ZIP
- `$$target_folder_path`: la carpeta donde se ha extraído
- `$$extract_succeeded`: `true` o `false`
- `$$failure_reason`: lo que ha fallado. Está vacío si no se ha producido ningún error.

Las rutas dentro de la carpeta del juego empiezan por `/`, como `/config/fancymenu/assets/pack.zip`. Las rutas dentro de la carpeta `.minecraft` empiezan por `.minecraft/`.

### Al recibir datos de FM

**Identificador:** `fm_data_received`

Se ejecuta cuando el servidor envía datos a este jugador con `/fmdata send`. Consulta [Datos de FM](/fm-data).

- `$$data_identifier`: el identificador con el que se han enviado los datos
- `$$data`: los datos
- `$$sent_by`: la IP del servidor o `integrated_server` en un mundo de un jugador

### Al conectarse a un servidor remoto

**Identificador:** `remote_server_connected`

Se ejecuta cuando se establece una [conexión con un servidor remoto](/remote-server-communication).

- `$$request_id`: el ID de solicitud de la conexión
- `$$remote_server_url`: el enlace del servidor remoto

### Al recibir datos de un servidor remoto

**Identificador:** `remote_server_data_received`

Se ejecuta cada vez que un servidor remoto conectado envía texto.

- `$$request_id`: el ID de solicitud de la conexión
- `$$remote_server_url`: el enlace del servidor remoto
- `$$data`: el texto enviado

### Al cerrarse la conexión con un servidor remoto

**Identificador:** `remote_server_connection_closed`

Se ejecuta cuando se cierra una conexión con un servidor remoto.

- `$$request_id`: el ID de solicitud de la conexión
- `$$remote_server_url`: el enlace del servidor remoto
- `$$intentionally_closed`: `true` si la conexión se ha cerrado con [**Close Remote Server Connection**](/action-scripts#close-remote-server-connection)
- `$$crashed`: `true` si la conexión se ha interrumpido por un error
- `$$unknown_close_reason`: `true` si se ha cerrado por un motivo desconocido

## Juego, mundos y servidores

### Al salir de Minecraft

**Identificador:** `quit_minecraft`

Se ejecuta una vez cuando el juego empieza a cerrarse.

- `$$timestamp_millis`: la hora en milisegundos desde 1970
- `$$timestamp_iso`: la hora en formato ISO-8601, como `2026-11-24T18:30:00.123Z`

### Al hacer una captura de pantalla

**Identificador:** `screenshot_taken`

Se ejecuta cuando se hace y se guarda una captura de pantalla, por ejemplo, con la tecla de captura.

- `$$screenshot_path`: la ruta de la captura en la carpeta del juego, como `/screenshots/2026-10-29_14.30.00.png`

### Al entrar en un mundo de un jugador

**Identificador:** `world_entered`

Se ejecuta cuando termina de cargarse un mundo de un jugador y puedes moverte.

- `$$world_name`: el nombre del mundo
- `$$world_save_path`: la ruta completa de la carpeta de guardado del mundo
- `$$world_difficulty`: la dificultad del mundo
- `$$world_cheats_allowed`: `true` si los trucos están activados
- `$$world_icon_path`: la ruta completa del icono del mundo
- `$$world_is_first_join`: `true` en la primera visita tras crear el mundo

### Al salir de un mundo de un jugador

**Identificador:** `world_left`

Se ejecuta cuando se cierra y se guarda un mundo de un jugador.

Proporciona las mismas variables que **Al entrar en un mundo de un jugador**, salvo `$$world_is_first_join`: `$$world_name`, `$$world_save_path`, `$$world_difficulty`, `$$world_cheats_allowed` y `$$world_icon_path`.

### Al empezar a conectarse a un servidor

**Identificador:** `start_joining_server`

Se ejecuta cuando el juego empieza a conectarse a un servidor o Realm, antes de entrar. También se ejecuta si la conexión falla o se cancela, por lo que puede recordar el servidor; por ejemplo, para un botón de reconexión en la pantalla de desconexión.

- `$$server_ip`: la IP del servidor

### Al entrar en un servidor

**Identificador:** `server_joined`

Se ejecuta después de entrar en un servidor multijugador.

- `$$server_ip`: la IP del servidor

### Al salir de un servidor

**Identificador:** `server_left`

Se ejecuta después de salir de un servidor multijugador.

- `$$server_ip`: la IP del servidor

### Al entrar otro jugador en un mundo o servidor

**Identificador:** `other_player_joined_world`

Se ejecuta cuando otro jugador entra en tu mundo o servidor.

- `$$player_name`: el nombre del jugador
- `$$player_uuid`: el UUID del jugador

### Al salir otro jugador de un mundo o servidor

**Identificador:** `other_player_left_world`

Se ejecuta cuando otro jugador sale de tu mundo o servidor.

- `$$player_name`: el nombre del jugador
- `$$player_uuid`: el UUID del jugador

### Al morir otro jugador

**Identificador:** `other_player_died`

Se ejecuta cuando muere otro jugador en tu mundo.

- `$$player_name`: el nombre del jugador
- `$$player_uuid`: el UUID del jugador
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: dónde ha muerto el jugador

## Chat

### Al recibir un mensaje de chat

**Identificador:** `chat_message_received`

Se ejecuta cuando aparece en tu chat un mensaje de un jugador.

- `$$chat_message_string`: el mensaje como texto sin formato
- `$$chat_message_component`: el mensaje como componente de texto JSON
- `$$sender_uuid`: el UUID del remitente o `ERROR` si se desconoce
- `$$sender_name`: el nombre del remitente o `ERROR` si se desconoce

### Al enviar un mensaje de chat

**Identificador:** `chat_message_sent`

Se ejecuta cuando envías un mensaje de chat. Los comandos no cuentan.

- `$$chat_message_string`: el mensaje como texto sin formato
- `$$chat_message_component`: el mensaje como componente de texto JSON

### Al recibir un mensaje del sistema en el chat

**Identificador:** `system_message_received_in_chat`

Se ejecuta cuando aparece en tu chat un mensaje que no procede de un jugador, como la respuesta de un comando.

- `$$system_message_string`: el mensaje como texto sin formato
- `$$system_message_component`: el mensaje como componente de texto JSON

## Jugador

### Al morir

**Identificador:** `player_death`

Se ejecuta justo después de abrirse la pantalla de muerte.

- `$$days_survived`: los días del juego transcurridos desde tu última muerte, redondeados hacia abajo
- `$$death_reason_string`: el mensaje de muerte como texto sin formato
- `$$death_reason_component`: el mensaje de muerte como componente de texto JSON
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: dónde has muerto

### Al recibir daño

**Identificador:** `damage_taken`

Se ejecuta una vez por cada golpe que recibes.

- `$$damage_amount`: cuánta salud te ha quitado el golpe
- `$$damage_type`: el tipo de daño, como `minecraft:fall`
- `$$is_fatal_damage`: `true` si el golpe te ha matado
- `$$damage_source`: el tipo de entidad que lo ha causado, como `minecraft:zombie`, o `NONE`

### Al obtener un efecto

**Identificador:** `effect_gained`

Se ejecuta una vez al obtener un efecto de estado.

- `$$effect_key`: el efecto, como `minecraft:speed`
- `$$effect_type`: `positive`, `negative` o `neutral`
- `$$effect_duration`: cuánto dura, en ticks (20 ticks equivalen a 1 segundo)

### Al perder un efecto

**Identificador:** `effect_lost`

Se ejecuta una vez cuando termina un efecto de estado.

- `$$effect_key`: el efecto, como `minecraft:speed`
- `$$effect_type`: `positive`, `negative` o `neutral`

### Al cambiar la experiencia

**Identificador:** `experience_changed`

Se ejecuta cada vez que aumentan o disminuyen tus puntos de experiencia.

- `$$new_experience_amount`: tus puntos de experiencia totales actuales
- `$$old_experience_amount`: tus puntos de experiencia totales anteriores
- `$$is_level_up`: `true` si has subido de nivel

### Al conseguir un logro

**Identificador:** `achievement_unlocked`

Se ejecuta una vez al conseguir un logro (avance). No cuenta si ya lo habías conseguido, por ejemplo, al entrar en un mundo.

- `$$achievement_key`: el logro, como `minecraft:story/mine_diamond`
- `$$achievement_label`: su título en el idioma del juego
- `$$achievement_description`: su descripción en el idioma del juego
- `$$achievement_icon_item_key`: el objeto de su icono, como `minecraft:diamond`
- `$$achievement_type`: `advancement`, `goal` o `challenge`

### Al saltar

**Identificador:** `jump`

Se ejecuta cada vez que saltas. No tiene variables.

### Al empezar a correr

**Identificador:** `started_running`

Se ejecuta una vez cuando empiezas a esprintar. No tiene variables.

### Al dejar de correr

**Identificador:** `stopped_running`

Se ejecuta una vez cuando dejas de esprintar. No tiene variables.

### Al cambiar de posición

**Identificador:** `position_changed`

Se ejecuta cada vez que te mueves a otro bloque.

- `$$old_pos_x`, `$$old_pos_y`, `$$old_pos_z`: la posición anterior del bloque
- `$$new_pos_x`, `$$new_pos_y`, `$$new_pos_z`: la nueva posición del bloque

### Al empezar a arder

**Identificador:** `started_burning`

Se ejecuta una vez cuando empiezas a arder. No tiene variables.

### Al dejar de arder

**Identificador:** `stopped_burning`

Se ejecuta una vez cuando dejas de arder. No tiene variables.

### Al empezar a ahogarse

**Identificador:** `started_drowning`

Se ejecuta una vez cuando empiezas a recibir daño por ahogamiento. No tiene variables.

### Al empezar a congelarse

**Identificador:** `started_freezing`

Se ejecuta una vez cuando empiezas a congelarte, por ejemplo, en nieve en polvo.

- `$$freezing_intensity`: cuánto te has congelado, de `0.0` (nada) a `1.0` (por completo)

### Al dejar de congelarse

**Identificador:** `stopped_freezing`

Se ejecuta una vez cuando dejas de congelarte. No tiene variables.

### Al congelarse por completo

**Identificador:** `fully_frozen`

Se ejecuta una vez cuando te congelas por completo. No tiene variables.

### Al empezar a nadar

**Identificador:** `start_swimming`

Se ejecuta una vez cuando empiezas a nadar.

- `$$fluid_type`: el fluido, como `minecraft:water`

### Al dejar de nadar

**Identificador:** `stop_swimming`

Se ejecuta una vez cuando dejas de nadar.

- `$$fluid_type`: el fluido, como `minecraft:water`

### Al empezar a tocar un fluido

**Identificador:** `start_touching_fluid`

Se ejecuta una vez cuando empiezas a tocar un fluido, como agua o lava.

- `$$fluid_type`: el fluido, como `minecraft:lava`

### Al dejar de tocar un fluido

**Identificador:** `stop_touching_fluid`

Se ejecuta una vez cuando dejas de tocar un fluido.

- `$$fluid_type`: el fluido, como `minecraft:lava`

## Objetos

### Al recoger un objeto

**Identificador:** `item_picked_up`

Se ejecuta una vez cuando recoges un objeto.

- `$$item_key`: el objeto, como `minecraft:diamond`

### Al soltar un objeto

**Identificador:** `item_dropped`

Se ejecuta una vez cuando sueltas un objeto del inventario.

- `$$item_key`: el objeto, como `minecraft:diamond`

### Al consumir un objeto

**Identificador:** `item_consumed`

Se ejecuta una vez cuando terminas de comer o beber un objeto.

- `$$item_key`: el objeto, como `minecraft:golden_apple`

### Al usar un objeto

**Identificador:** `item_used`

Se ejecuta una vez cuando usas un objeto.

- `$$item_key`: el objeto, como `minecraft:flint_and_steel`
- `$$used_on_type`: sobre qué se ha usado: `block`, `entity`, `self` o `none`
- `$$used_on_entity_key`: el tipo de entidad sobre la que se ha usado. Está vacío si no se ha usado sobre ninguna.
- `$$used_on_block_key`: el bloque sobre el que se ha usado. Está vacío si no se ha usado sobre ninguno.
- `$$target_pos_x`, `$$target_pos_y`, `$$target_pos_z`: la posición donde se ha usado o `-1`

### Al romperse un objeto

**Identificador:** `item_broke`

Se ejecuta una vez cuando se rompe un objeto de tu inventario.

- `$$item_key`: el objeto, como `minecraft:iron_pickaxe`
- `$$item_type`: `tool`, `armor` u `other`

### Al pasar el cursor sobre un objeto del inventario

**Identificador:** `item_hovered_in_inventory`

Se ejecuta una vez cuando el ratón pasa sobre un objeto de cualquier inventario, como el tuyo o el de un cofre.

- `$$item_key`: el objeto, como `minecraft:diamond_sword`
- `$$item_display_name_string`: el nombre del objeto como texto sin formato
- `$$item_display_name_json`: el nombre del objeto como componente de texto JSON

## Bloques

### Al empezar a mirar un bloque

**Identificador:** `start_looking_at_block`

Se ejecuta una vez cuando tu punto de mira empieza a señalar un bloque situado a un máximo de 20 bloques.

- `$$block_key`: el bloque, como `minecraft:oak_log`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: la posición del bloque
- `$$distance_to_player`: la distancia desde tus ojos hasta el punto al que señala la mira

### Al dejar de mirar un bloque

**Identificador:** `stop_looking_at_block`

Se ejecuta una vez cuando tu punto de mira deja de señalar un bloque.

Proporciona las mismas variables que **Al empezar a mirar un bloque**, correspondientes al bloque que mirabas antes: `$$block_key`, `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` y `$$distance_to_player`.

### Al romper un bloque

**Identificador:** `block_broke`

Se ejecuta una vez cuando rompes un bloque.

- `$$block_key`: el bloque, como `minecraft:stone`
- `$$broke_with_item_key`: el objeto que tienes en la mano, como `minecraft:iron_pickaxe`, o `EMPTY`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: la posición del bloque

### Al colocar un bloque

**Identificador:** `block_placed`

Se ejecuta una vez cuando colocas un bloque.

- `$$block_key`: el bloque, como `minecraft:torch`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: la posición del bloque

### Al interactuar con un bloque

**Identificador:** `interacted_with_block`

Se ejecuta una vez cuando interactúas con un bloque, por ejemplo, al abrir un cofre o pulsar un botón.

- `$$block_key`: el bloque, como `minecraft:chest`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: la posición del bloque

### Al pisar un bloque

**Identificador:** `stepping_on_block`

Se ejecuta una vez cuando pisas un bloque.

- `$$block_key`: el bloque, como `minecraft:grass_block`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: la posición del bloque

## Entidades

### Al empezar a mirar una entidad

**Identificador:** `start_looking_at_entity`

Se ejecuta una vez cuando tu punto de mira empieza a señalar una entidad situada a un máximo de 20 bloques.

- `$$entity_key`: el tipo de entidad, como `minecraft:villager`
- `$$distance_to_player`: la distancia desde tus ojos hasta el punto al que señala la mira
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al dejar de mirar una entidad

**Identificador:** `stop_looking_at_entity`

Se ejecuta una vez cuando tu punto de mira deja de señalar una entidad.

Proporciona las mismas variables que **Al empezar a mirar una entidad**, correspondientes a la entidad que mirabas antes: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` y `$$entity_uuid`.

### Al aparecer una entidad en tu campo de visión

**Identificador:** `entity_starts_being_in_sight`

Se ejecuta una vez cuando una entidad se hace visible en tu pantalla, hasta a 200 bloques de distancia.

- `$$entity_key`: el tipo de entidad, como `minecraft:creeper`
- `$$distance_to_player`: la distancia desde tus ojos hasta la entidad
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al salir una entidad de tu campo de visión

**Identificador:** `entity_stops_being_in_sight`

Se ejecuta una vez cuando una entidad visible sale de tu pantalla o se aleja más de 200 bloques.

Proporciona las mismas variables que **Al aparecer una entidad en tu campo de visión**: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` y `$$entity_uuid`.

### Al interactuar con una entidad

**Identificador:** `entity_interacted`

Se ejecuta una vez cuando interactúas con una entidad, por ejemplo, al comerciar con un aldeano.

- `$$entity_key`: el tipo de entidad, como `minecraft:villager`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al montar una entidad

**Identificador:** `entity_mounted`

Se ejecuta una vez cuando empiezas a montar una entidad, como un caballo o una barca.

- `$$entity_key`: el tipo de entidad, como `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al desmontar una entidad

**Identificador:** `entity_unmounted`

Se ejecuta una vez cuando dejas de montar una entidad.

- `$$entity_key`: el tipo de entidad, como `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al aparecer una entidad

**Identificador:** `entity_spawned`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando aparece una entidad en cualquier lugar del mundo, incluso muy lejos o en otra dimensión.

- `$$entity_key`: el tipo de entidad, como `minecraft:zombie`
- `$$distance_to_player`: la distancia hasta ti o `-1` si está en otra dimensión
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: dónde ha aparecido
- `$$entity_uuid`: el UUID de la entidad
- `$$dimension_key`: la dimensión, como `minecraft:overworld`
- `$$is_same_dimension_as_player`: `true` si ha aparecido en tu dimensión

### Al morir una entidad

**Identificador:** `entity_died`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando muere una entidad en cualquier lugar del mundo, incluso muy lejos o en otra dimensión.

- `$$entity_key`: el tipo de entidad, como `minecraft:ender_dragon`
- `$$distance_to_player`: la distancia hasta ti o `-1` si está en otra dimensión
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: dónde ha muerto
- `$$entity_uuid`: el UUID de la entidad
- `$$dimension_key`: la dimensión, como `minecraft:the_end`
- `$$damage_type`: el tipo de daño que la ha matado, como `minecraft:player_attack`
- `$$is_same_dimension_as_player`: `true` si ha muerto en tu dimensión
- `$$entity_killed_by_name`: el nombre de quien la ha matado o `NONE`
- `$$entity_killed_by_key`: el tipo de quien la ha matado, como `minecraft:player`, o `NONE`
- `$$entity_killed_by_uuid`: el UUID de quien la ha matado o `NONE`

## Mundo y lugares

### Al entrar en un bioma

**Identificador:** `enter_biome`

Se ejecuta una vez cuando entras en otro bioma.

- `$$biome_key`: el bioma, como `minecraft:cherry_grove`

### Al salir de un bioma

**Identificador:** `leave_biome`

Se ejecuta una vez cuando sales de un bioma.

- `$$biome_key`: el bioma del que has salido, como `minecraft:cherry_grove`

### Al entrar en una estructura

**Identificador:** `enter_structure`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando entras en la zona de una estructura. La zona es aproximada, así que también puede ejecutarse cerca de una estructura o encima de ella, por ejemplo, si hay una mina abandonada debajo de ti. Para detectar únicamente el interior, usa **On Enter Structure (High Precision)**.

- `$$structure_key`: la estructura, como `minecraft:village_plains`

### Al salir de una estructura

**Identificador:** `leave_structure`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando sales de la zona de una estructura, con la misma precisión aproximada que **Al entrar en una estructura**.

- `$$structure_key`: la estructura de la que has salido

### Al entrar en una estructura (alta precisión)

**Identificador:** `enter_structure_high_precision`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando entras en el interior de una estructura.

- `$$structure_key`: la estructura, como `minecraft:stronghold`

### Al salir de una estructura (alta precisión)

**Identificador:** `leave_structure_high_precision`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando vuelves a estar completamente fuera de una estructura.

- `$$structure_key`: la estructura de la que has salido

### Al entrar en una dimensión

**Identificador:** `enter_dimension`

Se ejecuta una vez cuando entras en otra dimensión.

- `$$dimension_key`: la dimensión, como `minecraft:the_nether`

### Al cambiar el tiempo

**Identificador:** `weather_changed`

Se ejecuta una vez cuando cambia el tiempo. También se ejecuta si cambia el tiempo en el lugar donde estás: mientras llueve, entrar en un desierto, un bioma nevado o un edificio también cuenta.

- `$$weather_type`: `clear`, `rain` o `thunder`
- `$$weather_can_snow`: `true` si podría nevar donde estás
- `$$weather_can_rain`: `true` si podría llover donde estás

### Al empezar una incursión

**Identificador:** `raid_started`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando empieza una incursión mientras estás en su zona, por lo que aparece la barra de la incursión. No tiene variables.

Entrar en una incursión que ya está en marcha no cuenta. Para eso, usa **On Enter Active Raid Area**.

### Al entrar en la zona de una incursión activa

**Identificador:** `enter_active_raid_area`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando entras en la zona de una incursión que ya está en marcha, por lo que aparece la barra de la incursión. No tiene variables.

### Al salir de la zona de una incursión activa

**Identificador:** `leave_active_raid_area`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando sales de la zona de una incursión, por lo que desaparece la barra. También cuenta morir o cambiar de dimensión en esa zona, pero no el final de la incursión. No tiene variables.

### Al terminar una incursión

**Identificador:** `raid_finished`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando termina una incursión mientras estás en su zona.

- `$$raid_result`: `victory` o `defeat`

## Sonido y música

### Al empezar una pista musical

**Identificador:** `music_track_started`

Se ejecuta una vez cuando empieza a reproducirse una pista musical.

- `$$track_resource_location`: el archivo de sonido de la pista
- `$$track_display_name`: el nombre de la pista o `UNKNOWN`
- `$$track_artist`: el artista de la pista o `UNKNOWN`
- `$$track_duration_ms`: cuánto dura, en milisegundos, o `0` si se desconoce

### Al detenerse una pista musical

**Identificador:** `music_track_stopped`

Se ejecuta una vez cuando se detiene la pista musical, porque ha terminado o porque otra la ha sustituido.

Proporciona las mismas variables que **Al empezar una pista musical**: `$$track_resource_location`, `$$track_display_name`, `$$track_artist` y `$$track_duration_ms`.

### Al reproducirse un sonido del mundo

**Identificador:** `world_sound_triggered`

Se ejecuta cada vez que empieza a reproducirse un sonido del mundo cerca de ti, como una puerta o un creeper.

- `$$sound_resource_location`: el archivo de sonido
- `$$sound_display_name`: el subtítulo del sonido o `UNKNOWN`
- `$$sound_origin_pos_x`, `$$sound_origin_pos_y`, `$$sound_origin_pos_z`: de dónde procede el sonido
- `$$sound_origin_distance_to_player`: a qué distancia está
- `$$sound_origin_direction_from_player`: su dirección en grados (de 0 a 360), en relación con hacia dónde miras
