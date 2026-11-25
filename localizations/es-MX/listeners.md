---
title: Eventos
description: >-
  Ejecuta scripts de acciones cuando sucede algo en el juego, como presionar una
  tecla, recibir un mensaje de chat o desbloquear un logro.
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# Eventos

Los eventos ejecutan un [script de acciones](/action-scripts) cuando sucede algo en el juego: se presiona una tecla, se abre una pantalla, desbloqueas un logro y mucho más. Funcionan en todos los menús y mientras juegas, y no pertenecen a ningún diseño.

La mayoría de los eventos también proporcionan a su script variables sobre lo que sucedió, como el nombre de la tecla que se presionó.

<img width="800" alt="Se presionan teclas en la pantalla de título y una notificación muestra el nombre de cada tecla" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> Un evento puede ejecutar acciones de archivos, red, comandos, portapapeles, paquetes de recursos y enlaces aunque no haya ningún menú abierto. Usa únicamente eventos de perfiles y archivos de personas de confianza.

# Agregar un evento

<img width="800" alt="Se abre Administrar eventos, se agrega un evento Al presionar una tecla del teclado con una acción Mostrar notificación y se presiona H para probarlo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. Abre **barra de menú -> Personalización -> Administrar eventos**.
2. Haz clic en **Agregar evento**.
3. Haz clic en el evento en **Eventos disponibles**. La barra de búsqueda encuentra eventos por nombre y descripción.
   - **Descripción del evento** muestra lo que hace y las variables que proporciona.
   - **Copiar variables al portapapeles** copia los nombres de sus variables.
   - **Abrir descripción en otra ventana** abre la descripción en su propia ventana.
4. Haz clic en **Listo** o haz doble clic en el evento. Se abrirá el editor de scripts de acciones.
5. Agrega las acciones que se deben ejecutar y haz clic en **Listo**. Consulta [Scripts de acciones](/action-scripts#making-an-action-script).
6. Haz clic en **Listo** en **Administrar eventos** para guardar. El evento funcionará de inmediato.

**Cancelar** descarta todos los cambios que hiciste en **Administrar eventos**, después de pedirte confirmación.

# Administrar eventos

<img width="800" alt="La ventana Administrar eventos con cinco eventos, uno seleccionado y su script de acciones a la derecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- Haz clic en un evento para ver su tipo y script de acciones a la derecha.
- **Editar acciones** o hacer clic derecho en un evento abre su script de acciones.
- Haz doble clic en el nombre de un evento para cambiarlo, por ejemplo, a `Tecla de ayuda`. `Enter` guarda el nombre y `Esc` cancela. Si el nombre está vacío, se vuelve a mostrar el tipo de evento.
- **Eliminar evento** borra el evento seleccionado.
- **Exportar para IA** copia el evento seleccionado o todos los eventos para un [chat de IA](/export-for-ai), incluidos los cambios sin guardar.

Los eventos se guardan en `config/fancymenu/listener_instances.txt` (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations)). Cada [perfil](/profiles) tiene sus propios eventos.

# Variables de eventos

Las variables de un evento empiezan con `$$` y funcionan en todo su script: en cada valor de acción y en los requisitos de las [instrucciones IF](/action-scripts#if-else-if-and-else). Se distingue entre mayúsculas y minúsculas. Cada evento que aparece abajo indica sus variables; también se muestran en su descripción, en el selector de eventos.

<img width="800" alt="El selector de eventos con Al desbloquear un logro seleccionado y su descripción muestra sus variables" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

Por ejemplo, este evento abre una pantalla de ayuda cuando se presiona `H`:

1. Agrega un evento **Al presionar una tecla del teclado**.
2. En su script, usa **Agregar instrucción IF** con el requisito [**Es texto**](/conditions#is-text). Establece **Modo de comparación** en **Es igual a**, **Texto** en `$$key_name` y **Comparar con texto** en `H`.
3. Dentro de la instrucción IF, agrega [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui) con tu pantalla de ayuda.

Más información sobre las variables de eventos:

- Las variables de eventos siempre son texto. Cuando un evento no puede obtener un valor, la variable recibe un valor predeterminado, como `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` o nada.
- Las variables de eventos se completan antes que los [marcadores de posición](/placeholders), así que también funcionan dentro de ellos.
- Las variables de eventos solo existen mientras se ejecuta su script. Para conservar un valor, guárdalo en una de tus [variables](/variables) con [**Establecer valor de variable (variable de FM)**](/action-scripts#set-variable-value-fm-variable).
- Tus propias variables de **barra de menú -> Personalización -> Administrar variables** también funcionan en scripts de eventos. Usa `$$` seguido del nombre, como `$$coins`. Si alguna tiene el mismo nombre que una variable de evento, `$$name` se refiere a la variable del evento. Tus variables con nombres más largos, como `key_name_log`, siguen funcionando.
- El texto del chat, los servidores, los archivos y otros jugadores puede ser cualquier cosa. Nunca lo insertes directamente en comandos, rutas de archivos ni enlaces.

# Información útil

- Algunos eventos necesitan que FancyMenu esté instalado en el servidor. Se indica más abajo. En un mundo de un jugador, siempre funcionan.
- Algunos eventos se ejecutan con mucha frecuencia, como **Al mover el mouse en una pantalla**, **Al desplazarse por un elemento**, **Al cambiar de posición** y **Al reproducirse un sonido en el mundo**. Mantén sus scripts breves y nunca uses acciones lentas como [**Recargar FancyMenu**](/action-scripts#reload-fancymenu) en ellos.
- Para reemplazar una pantalla con **Al abrir una pantalla**, primero comprueba `$$screen_identifier` con una instrucción IF. De lo contrario, se reemplazarán todas las pantallas, incluida la que abras.

# Todos los eventos

Todos los eventos que tiene FancyMenu, ordenados según a qué reaccionan.

## Teclado y mouse

Para comprobar qué tecla fue, usa `$$key_name`. Los códigos numéricos de las teclas no son iguales en todas las versiones de Minecraft.

### Al presionar una tecla del teclado

**Identificador:** `keyboard_key_pressed`

Se ejecuta cuando se presiona una tecla, en los menús y mientras juegas. Mientras mantienes presionada una tecla, se ejecuta una y otra vez.

- `$$key_name`: el nombre de la tecla, como `H` o `Left Shift`
- `$$key_keycode`: el código numérico de la tecla
- `$$key_scancode`: el código de escaneo de la tecla
- `$$key_modifiers`: un número que representa las teclas modificadoras que se presionan al mismo tiempo, como `Shift` y `Ctrl`

### Al soltar una tecla del teclado

**Identificador:** `keyboard_key_released`

Se ejecuta cuando se suelta una tecla, en los menús y mientras juegas.

Proporciona las mismas variables que **Al presionar una tecla del teclado**: `$$key_name`, `$$key_keycode`, `$$key_scancode` y `$$key_modifiers`.

### Al escribir un carácter del teclado en una pantalla

**Identificador:** `keyboard_char_typed`

Se ejecuta por cada carácter que escribes mientras hay una pantalla abierta.

- `$$char`: el carácter escrito

### Al mover el mouse en una pantalla

**Identificador:** `mouse_moved`

Se ejecuta cada vez que mueves el mouse mientras hay una pantalla abierta.

- `$$mouse_pos_x`, `$$mouse_pos_y`: la posición del mouse, en píxeles de la GUI
- `$$mouse_move_delta_x`, `$$mouse_move_delta_y`: cuánto se movió desde la última vez

### Al hacer clic con un botón del mouse

**Identificador:** `mouse_button_clicked`

Se ejecuta una vez cuando se presiona un botón del mouse, en los menús y mientras juegas.

- `$$button`: `left`, `right` o `middle`. Los demás botones muestran su número.
- `$$mouse_pos_x`, `$$mouse_pos_y`: la posición del mouse, en píxeles de la GUI

### Al soltar un botón del mouse

**Identificador:** `mouse_button_released`

Se ejecuta una vez cuando se suelta un botón del mouse, en los menús y mientras juegas.

Proporciona las mismas variables que **Al hacer clic con un botón del mouse**: `$$button`, `$$mouse_pos_x` y `$$mouse_pos_y`.

### Al desplazarse con el mouse en una pantalla

**Identificador:** `mouse_scrolled`

Se ejecuta cuando giras la rueda del mouse mientras hay una pantalla abierta.

- `$$scroll_delta_y`: cuánto giró la rueda. Es mayor que `0` al desplazarte hacia arriba y menor que `0` al desplazarte hacia abajo.

## Pantallas y elementos

### Al abrir una pantalla

**Identificador:** `screen_open`

Se ejecuta justo después de que se abre una pantalla. Una acción [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui) en su script puede reemplazarla por otra.

- `$$screen_identifier`: el [identificador](/screen-identifiers) de la pantalla

### Al cerrar una pantalla

**Identificador:** `screen_close`

Se ejecuta justo después de que se cierra una pantalla.

- `$$screen_identifier`: el [identificador](/screen-identifiers) de la pantalla que se cerró

### Al hacer clic en texto Markdown

**Identificador:** `text_clicked`

Se ejecuta cuando alguien hace clic en un [evento de clic](/text-formatting#click-and-hover-events) de un texto, como `[Leer las reglas](click:open_rules)`.

- `$$text_event_id`: el ID del evento, como `open_rules`

### Al pasar el mouse sobre texto Markdown

**Identificador:** `text_hovered`

Se ejecuta cuando el mouse se mueve sobre un [evento al pasar el mouse](/text-formatting#click-and-hover-events) de un texto, como `[¿Qué es esto?](hover:show_hint)`.

- `$$text_event_id`: el ID del evento, como `show_hint`

### Al desplazarse por un elemento

**Identificador:** `scroll_area_scrolled`

Se ejecuta cada vez que se mueve el contenido de un [área desplazable](/scrollable-areas) o un [elemento de texto](/text-in-menus). Mientras el contenido se desliza, se ejecuta en cada fotograma. No se ejecuta en el editor de diseños.

- `$$element_identifier`: el [identificador](/element-identifiers) del elemento
- `$$scroll_x`: cuánto se desplazó el contenido hacia los lados, en píxeles
- `$$scroll_y`: cuánto se desplazó el contenido hacia abajo, en píxeles
- `$$scroll_percent`: cuánto se desplazó el contenido en su dirección principal, de `0` (inicio) a `100` (final)

### Al desplazar un elemento hasta el inicio

**Identificador:** `scroll_area_reached_start`

Se ejecuta cuando el contenido de un área desplazable o de un elemento de texto vuelve a su inicio al desplazarse.

Proporciona las mismas variables que **Al desplazarse por un elemento**: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` y `$$scroll_percent`.

### Al desplazar un elemento hasta el final

**Identificador:** `scroll_area_reached_end`

Se ejecuta cuando el contenido de un área desplazable o de un elemento de texto llega al final, por ejemplo, cuando alguien se desplaza por todas las reglas.

Proporciona las mismas variables que **Al desplazarse por un elemento**: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` y `$$scroll_percent`.

### Al comenzar la reproducción de una textura animada

**Identificador:** `animated_texture_started_playing`

Se ejecuta cuando comienza la reproducción de una [textura animada](/animations) (GIF, APNG o FMA), y cada vez que vuelve a empezar.

- `$$texture_source`: de dónde proviene la textura: una ruta de archivo, un enlace web o una ubicación de recursos
- `$$texture_source_type`: `LOCAL`, `WEB` o `RESOURCE_LOCATION`
- `$$texture_will_restart`: `true` si vuelve a empezar después de esta reproducción; de lo contrario, `false`

### Al terminar la reproducción de una textura animada

**Identificador:** `animated_texture_finished_playing`

Se ejecuta cuando termina una reproducción de una textura animada. Si se repite en bucle, se ejecuta justo antes de que vuelva a empezar.

Proporciona las mismas variables que **Al comenzar la reproducción de una textura animada**: `$$texture_source`, `$$texture_source_type` y `$$texture_will_restart`.

### Al cambiar el estado de reproducción de un video

**Identificador:** `video_playback_status_changed`

Se ejecuta cuando comienza, se pausa, se detiene o termina un [video](/video) o el fondo de un menú.

- `$$video_source`: de dónde proviene el video: una ruta de archivo, un enlace web o una ubicación de recursos
- `$$video_source_type`: `LOCAL`, `WEB` o `RESOURCE_LOCATION`
- `$$is_looping`: `true` si el video se repite en bucle; de lo contrario, `false`
- `$$new_status`:
  - `PLAYING`: el video comenzó o se reanudó
  - `PAUSED`: el video se pausó
  - `STOPPED`: el video se detuvo
  - `FINISHED`: el video llegó al final. También se activa con videos en bucle, justo antes de que vuelvan a empezar.

## Variables, archivos y datos

### Al actualizar una variable [variable de FM]

**Identificador:** `fm_variable_updated`

Se ejecuta cada vez que se establece una [variable](/variables).

- `$$var_name`: el nombre de la variable
- `$$old_value`: su valor anterior
- `$$new_value`: su nuevo valor

En las variables de lista, ambos valores son la lista completa como un arreglo JSON, por ejemplo, `["Diamonds","Emeralds"]`.

### Al iniciar una descarga de archivo mediante una acción

**Identificador:** `file_download_started_via_action`

Se ejecuta cuando comienza una descarga de [**Descargar archivo al directorio del juego**](/action-scripts#download-file-to-game-directory), en cuanto se conoce el nombre del archivo. El archivo solo aparece en su ruta cuando termina la descarga, así que usa **Al descargar un archivo mediante una acción** para saber cuándo está listo.

- `$$download_url`: el enlace del archivo
- `$$target_file_path`: dónde se guardará

### Al descargar un archivo mediante una acción

**Identificador:** `file_downloaded_via_action`

Se ejecuta cuando termina o falla una descarga de [**Descargar archivo al directorio del juego**](/action-scripts#download-file-to-game-directory).

- `$$download_url`: el enlace del archivo
- `$$target_file_path`: dónde se guardó el archivo. Si la descarga falló, puede ser únicamente la carpeta.
- `$$download_succeeded`: `true` o `false`

### Al seleccionar un archivo

**Identificador:** `file_selected_via_action`

Se ejecuta cuando termina [**Seleccionar archivo del sistema**](/action-scripts#select-file-from-system): se copió el archivo, se canceló el selector de archivos o algo falló.

- `$$selected_file_path`: la ruta completa del archivo elegido. Está vacío si se canceló el selector.
- `$$target_file_path`: dónde se copió el archivo, dentro de la carpeta del juego
- `$$selection_succeeded`: `true` si se copió el archivo
- `$$selection_cancelled`: `true` si se cerró el selector sin elegir un archivo
- `$$failure_reason`: qué salió mal. Está vacío si no hubo ningún problema.

### Al extraer un ZIP mediante una acción

**Identificador:** `zip_extracted_via_action`

Se ejecuta cuando termina [**Extraer archivo ZIP en el directorio del juego**](/action-scripts#extract-zip-file-in-game-directory).

- `$$source_zip_path`: el archivo ZIP
- `$$target_folder_path`: la carpeta en la que se extrajo
- `$$extract_succeeded`: `true` o `false`
- `$$failure_reason`: qué salió mal. Está vacío si no hubo ningún problema.

Las rutas dentro de la carpeta del juego empiezan con `/`, como `/config/fancymenu/assets/pack.zip`. Las rutas dentro de la carpeta `.minecraft` empiezan con `.minecraft/`.

### Al recibir datos de FM

**Identificador:** `fm_data_received`

Se ejecuta cuando el servidor envía datos a este jugador con `/fmdata send`. Consulta [Datos de FM](/fm-data).

- `$$data_identifier`: el identificador con el que se enviaron los datos
- `$$data`: los datos
- `$$sent_by`: la IP del servidor o `integrated_server` en un mundo de un jugador

### Al conectarse a un servidor remoto

**Identificador:** `remote_server_connected`

Se ejecuta cuando se abre una [conexión con un servidor remoto](/remote-server-communication).

- `$$request_id`: el ID de solicitud de la conexión
- `$$remote_server_url`: el enlace del servidor remoto

### Al recibir datos de un servidor remoto

**Identificador:** `remote_server_data_received`

Se ejecuta cada vez que un servidor remoto conectado envía texto.

- `$$request_id`: el ID de solicitud de la conexión
- `$$remote_server_url`: el enlace del servidor remoto
- `$$data`: el texto que envió

### Al cerrarse una conexión con un servidor remoto

**Identificador:** `remote_server_connection_closed`

Se ejecuta cuando se cierra una conexión con un servidor remoto.

- `$$request_id`: el ID de solicitud de la conexión
- `$$remote_server_url`: el enlace del servidor remoto
- `$$intentionally_closed`: `true` si se cerró con [**Cerrar conexión con servidor remoto**](/action-scripts#close-remote-server-connection)
- `$$crashed`: `true` si la conexión dejó de funcionar
- `$$unknown_close_reason`: `true` si se cerró por un motivo desconocido

## Juego, mundos y servidores

### Al salir de Minecraft

**Identificador:** `quit_minecraft`

Se ejecuta una vez cuando el juego comienza a cerrarse.

- `$$timestamp_millis`: la hora en milisegundos desde 1970
- `$$timestamp_iso`: la hora como texto ISO-8601, por ejemplo, `2026-11-24T18:30:00.123Z`

### Al tomar una captura de pantalla

**Identificador:** `screenshot_taken`

Se ejecuta cuando se toma y guarda una captura de pantalla, por ejemplo, al presionar la tecla de captura.

- `$$screenshot_path`: la ruta de la captura dentro de la carpeta del juego, por ejemplo, `/screenshots/2026-10-29_14.30.00.png`

### Al entrar a un mundo de un jugador

**Identificador:** `world_entered`

Se ejecuta cuando termina de cargarse un mundo de un jugador y ya puedes moverte.

- `$$world_name`: el nombre del mundo
- `$$world_save_path`: la ruta completa de la carpeta de guardado del mundo
- `$$world_difficulty`: la dificultad del mundo
- `$$world_cheats_allowed`: `true` si los trucos están activados
- `$$world_icon_path`: la ruta completa del ícono del mundo
- `$$world_is_first_join`: `true` en la primera visita después de crear el mundo

### Al salir de un mundo de un jugador

**Identificador:** `world_left`

Se ejecuta cuando se cierra y guarda un mundo de un jugador.

Proporciona las mismas variables que **Al entrar a un mundo de un jugador**, excepto `$$world_is_first_join`: `$$world_name`, `$$world_save_path`, `$$world_difficulty`, `$$world_cheats_allowed` y `$$world_icon_path`.

### Al comenzar a entrar a un servidor

**Identificador:** `start_joining_server`

Se ejecuta cuando el juego empieza a conectarse a un servidor o Realm, antes de entrar. También se ejecuta si la conexión falla o se cancela, para poder recordar el servidor, por ejemplo, para un botón de reconexión en la pantalla de desconexión.

- `$$server_ip`: la IP del servidor

### Al entrar a un servidor

**Identificador:** `server_joined`

Se ejecuta después de que entras a un servidor multijugador.

- `$$server_ip`: la IP del servidor

### Al salir de un servidor

**Identificador:** `server_left`

Se ejecuta después de que sales de un servidor multijugador.

- `$$server_ip`: la IP del servidor

### Al entrar otro jugador al mundo o servidor

**Identificador:** `other_player_joined_world`

Se ejecuta cuando otro jugador entra a tu mundo o servidor.

- `$$player_name`: el nombre del jugador
- `$$player_uuid`: el UUID del jugador

### Al salir otro jugador del mundo o servidor

**Identificador:** `other_player_left_world`

Se ejecuta cuando otro jugador sale de tu mundo o servidor.

- `$$player_name`: el nombre del jugador
- `$$player_uuid`: el UUID del jugador

### Al morir otro jugador

**Identificador:** `other_player_died`

Se ejecuta cuando muere otro jugador en tu mundo.

- `$$player_name`: el nombre del jugador
- `$$player_uuid`: el UUID del jugador
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: dónde murió el jugador

## Chat

### Al recibir un mensaje de chat

**Identificador:** `chat_message_received`

Se ejecuta cuando aparece en tu chat un mensaje de un jugador.

- `$$chat_message_string`: el mensaje como texto sin formato
- `$$chat_message_component`: el mensaje como componente de texto JSON
- `$$sender_uuid`: el UUID de quien lo envió o `ERROR` si se desconoce
- `$$sender_name`: el nombre de quien lo envió o `ERROR` si se desconoce

### Al enviar un mensaje de chat

**Identificador:** `chat_message_sent`

Se ejecuta cuando envías un mensaje de chat. Los comandos no cuentan.

- `$$chat_message_string`: el mensaje como texto sin formato
- `$$chat_message_component`: el mensaje como componente de texto JSON

### Al recibir un mensaje del sistema en el chat

**Identificador:** `system_message_received_in_chat`

Se ejecuta cuando aparece en tu chat un mensaje que no proviene de un jugador, como la respuesta de un comando.

- `$$system_message_string`: el mensaje como texto sin formato
- `$$system_message_component`: el mensaje como componente de texto JSON

## Jugador

### Al morir

**Identificador:** `player_death`

Se ejecuta justo después de que se abre la pantalla de muerte.

- `$$days_survived`: los días de juego transcurridos desde tu última muerte, redondeados hacia abajo
- `$$death_reason_string`: el mensaje de muerte como texto sin formato
- `$$death_reason_component`: el mensaje de muerte como componente de texto JSON
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: dónde moriste

### Al recibir daño

**Identificador:** `damage_taken`

Se ejecuta una vez por cada golpe que recibes.

- `$$damage_amount`: cuánta salud quitó el golpe
- `$$damage_type`: el tipo de daño, como `minecraft:fall`
- `$$is_fatal_damage`: `true` si el golpe te mató
- `$$damage_source`: el tipo de entidad que lo causó, como `minecraft:zombie`, o `NONE`

### Al obtener un efecto

**Identificador:** `effect_gained`

Se ejecuta una vez cuando recibes un efecto de estado.

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

Se ejecuta cada vez que tus puntos de experiencia aumentan o disminuyen.

- `$$new_experience_amount`: tus puntos de experiencia totales actuales
- `$$old_experience_amount`: tus puntos de experiencia totales anteriores
- `$$is_level_up`: `true` si subiste de nivel

### Al desbloquear un logro

**Identificador:** `achievement_unlocked`

Se ejecuta una vez cuando desbloqueas un logro (progreso). No cuenta si ya lo habías completado, como cuando entras a un mundo.

- `$$achievement_key`: el logro, como `minecraft:story/mine_diamond`
- `$$achievement_label`: su título en el idioma del juego
- `$$achievement_description`: su descripción en el idioma del juego
- `$$achievement_icon_item_key`: el objeto de su ícono, como `minecraft:diamond`
- `$$achievement_type`: `advancement`, `goal` o `challenge`

### Al saltar

**Identificador:** `jump`

Se ejecuta cada vez que saltas. No tiene variables.

### Al empezar a correr

**Identificador:** `started_running`

Se ejecuta una vez cuando empiezas a correr a toda velocidad. No tiene variables.

### Al dejar de correr

**Identificador:** `stopped_running`

Se ejecuta una vez cuando dejas de correr a toda velocidad. No tiene variables.

### Al cambiar de posición

**Identificador:** `position_changed`

Se ejecuta cada vez que te mueves a otro bloque.

- `$$old_pos_x`, `$$old_pos_y`, `$$old_pos_z`: la posición anterior del bloque
- `$$new_pos_x`, `$$new_pos_y`, `$$new_pos_z`: la nueva posición del bloque

### Al empezar a quemarse

**Identificador:** `started_burning`

Se ejecuta una vez cuando empiezas a quemarte. No tiene variables.

### Al dejar de quemarse

**Identificador:** `stopped_burning`

Se ejecuta una vez cuando dejas de quemarte. No tiene variables.

### Al empezar a ahogarse

**Identificador:** `started_drowning`

Se ejecuta una vez cuando empiezas a recibir daño por ahogamiento. No tiene variables.

### Al empezar a congelarse

**Identificador:** `started_freezing`

Se ejecuta una vez cuando empiezas a congelarte, por ejemplo, en nieve en polvo.

- `$$freezing_intensity`: qué tanto te has congelado, de `0.0` (nada) a `1.0` (por completo)

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

Se ejecuta una vez cuando sueltas un objeto de tu inventario.

- `$$item_key`: el objeto, como `minecraft:diamond`

### Al consumir un objeto

**Identificador:** `item_consumed`

Se ejecuta una vez cuando terminas de comer o beber un objeto.

- `$$item_key`: el objeto, como `minecraft:golden_apple`

### Al usar un objeto

**Identificador:** `item_used`

Se ejecuta una vez cuando usas un objeto.

- `$$item_key`: el objeto, como `minecraft:flint_and_steel`
- `$$used_on_type`: en qué se usó: `block`, `entity`, `self` o `none`
- `$$used_on_entity_key`: el tipo de entidad sobre la que se usó. Está vacío si no se usó en una entidad.
- `$$used_on_block_key`: el bloque sobre el que se usó. Está vacío si no se usó en un bloque.
- `$$target_pos_x`, `$$target_pos_y`, `$$target_pos_z`: la posición en la que se usó o `-1`

### Al romperse un objeto

**Identificador:** `item_broke`

Se ejecuta una vez cuando se rompe un objeto de tu inventario.

- `$$item_key`: el objeto, como `minecraft:iron_pickaxe`
- `$$item_type`: `tool`, `armor` u `other`

### Al pasar el mouse sobre un objeto del inventario

**Identificador:** `item_hovered_in_inventory`

Se ejecuta una vez cuando mueves el mouse sobre un objeto de cualquier inventario, como el tuyo o el de un cofre.

- `$$item_key`: el objeto, como `minecraft:diamond_sword`
- `$$item_display_name_string`: el nombre del objeto como texto sin formato
- `$$item_display_name_json`: el nombre del objeto como componente de texto JSON

## Bloques

### Al empezar a mirar un bloque

**Identificador:** `start_looking_at_block`

Se ejecuta una vez cuando tu punto de mira empieza a apuntar a un bloque que está a una distancia máxima de 20 bloques.

- `$$block_key`: el bloque, como `minecraft:oak_log`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: la posición del bloque
- `$$distance_to_player`: la distancia desde tus ojos hasta el punto al que apunta el punto de mira

### Al dejar de mirar un bloque

**Identificador:** `stop_looking_at_block`

Se ejecuta una vez cuando tu punto de mira deja de apuntar a un bloque.

Proporciona las mismas variables que **Al empezar a mirar un bloque**, para el bloque que mirabas antes: `$$block_key`, `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` y `$$distance_to_player`.

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

Se ejecuta una vez cuando usas un bloque, por ejemplo, al abrir un cofre o presionar un botón.

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

Se ejecuta una vez cuando tu punto de mira empieza a apuntar a una entidad que está a una distancia máxima de 20 bloques.

- `$$entity_key`: el tipo de entidad, como `minecraft:villager`
- `$$distance_to_player`: la distancia desde tus ojos hasta el punto al que apunta el punto de mira
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al dejar de mirar una entidad

**Identificador:** `stop_looking_at_entity`

Se ejecuta una vez cuando tu punto de mira deja de apuntar a una entidad.

Proporciona las mismas variables que **Al empezar a mirar una entidad**, para la entidad que mirabas antes: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` y `$$entity_uuid`.

### Al aparecer una entidad en tu campo de visión

**Identificador:** `entity_starts_being_in_sight`

Se ejecuta una vez cuando una entidad aparece en tu pantalla, a una distancia máxima de 200 bloques.

- `$$entity_key`: el tipo de entidad, como `minecraft:creeper`
- `$$distance_to_player`: la distancia desde tus ojos hasta la entidad
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al dejar de ver una entidad

**Identificador:** `entity_stops_being_in_sight`

Se ejecuta una vez cuando una entidad visible sale de tu pantalla o se aleja a más de 200 bloques.

Proporciona las mismas variables que **Al aparecer una entidad en tu campo de visión**: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` y `$$entity_uuid`.

### Al interactuar con una entidad

**Identificador:** `entity_interacted`

Se ejecuta una vez cuando usas una entidad, por ejemplo, al comerciar con un aldeano.

- `$$entity_key`: el tipo de entidad, como `minecraft:villager`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: la posición de la entidad
- `$$entity_uuid`: el UUID de la entidad

### Al montar una entidad

**Identificador:** `entity_mounted`

Se ejecuta una vez cuando empiezas a montar una entidad, como un caballo o un bote.

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

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando aparece una entidad en cualquier lugar del mundo, incluso lejos o en otra dimensión.

- `$$entity_key`: el tipo de entidad, como `minecraft:zombie`
- `$$distance_to_player`: la distancia hasta ti o `-1` si está en otra dimensión
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: dónde apareció
- `$$entity_uuid`: el UUID de la entidad
- `$$dimension_key`: la dimensión, como `minecraft:overworld`
- `$$is_same_dimension_as_player`: `true` si apareció en tu dimensión

### Al morir una entidad

**Identificador:** `entity_died`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando muere una entidad en cualquier lugar del mundo, incluso lejos o en otra dimensión.

- `$$entity_key`: el tipo de entidad, como `minecraft:ender_dragon`
- `$$distance_to_player`: la distancia hasta ti o `-1` si está en otra dimensión
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: dónde murió
- `$$entity_uuid`: el UUID de la entidad
- `$$dimension_key`: la dimensión, como `minecraft:the_end`
- `$$damage_type`: el tipo de daño que la mató, como `minecraft:player_attack`
- `$$is_same_dimension_as_player`: `true` si murió en tu dimensión
- `$$entity_killed_by_name`: el nombre de quien la mató o `NONE`
- `$$entity_killed_by_key`: el tipo de quien la mató, como `minecraft:player`, o `NONE`
- `$$entity_killed_by_uuid`: el UUID de quien la mató o `NONE`

## Mundo y lugares

### Al entrar a un bioma

**Identificador:** `enter_biome`

Se ejecuta una vez cuando entras a otro bioma.

- `$$biome_key`: el bioma, como `minecraft:cherry_grove`

### Al salir de un bioma

**Identificador:** `leave_biome`

Se ejecuta una vez cuando sales de un bioma.

- `$$biome_key`: el bioma del que saliste, como `minecraft:cherry_grove`

### Al entrar a una estructura

**Identificador:** `enter_structure`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando entras al área de una estructura. El área es aproximada, así que también puede activarse cerca de una estructura o encima de ella, como cuando hay una mina abandonada debajo de ti. Para detectar solo el interior, usa **Al entrar a una estructura (alta precisión)**.

- `$$structure_key`: la estructura, como `minecraft:village_plains`

### Al salir de una estructura

**Identificador:** `leave_structure`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando sales del área de una estructura. El área es tan aproximada como la de **Al entrar a una estructura**.

- `$$structure_key`: la estructura de la que saliste

### Al entrar a una estructura (alta precisión)

**Identificador:** `enter_structure_high_precision`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando entras al interior de una estructura.

- `$$structure_key`: la estructura, como `minecraft:stronghold`

### Al salir de una estructura (alta precisión)

**Identificador:** `leave_structure_high_precision`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta una vez cuando sales por completo de una estructura.

- `$$structure_key`: la estructura de la que saliste

### Al entrar a una dimensión

**Identificador:** `enter_dimension`

Se ejecuta una vez cuando entras a otra dimensión.

- `$$dimension_key`: la dimensión, como `minecraft:the_nether`

### Al cambiar el clima

**Identificador:** `weather_changed`

Se ejecuta una vez cuando cambia el clima. También se ejecuta cuando cambia el clima del lugar donde estás: mientras llueve, entrar a un desierto, un bioma nevado o una construcción también cuenta.

- `$$weather_type`: `clear`, `rain` o `thunder`
- `$$weather_can_snow`: `true` si podría nevar donde estás
- `$$weather_can_rain`: `true` si podría llover donde estás

### Al iniciar una incursión

**Identificador:** `raid_started`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando empieza una incursión mientras estás en su área, y aparece la barra de incursión. No tiene variables.

Entrar a una incursión que ya está en curso no cuenta. Para eso, usa **Al entrar al área de una incursión activa**.

### Al entrar al área de una incursión activa

**Identificador:** `enter_active_raid_area`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando entras al área de una incursión que ya está en curso, y aparece la barra de incursión. No tiene variables.

### Al salir del área de una incursión activa

**Identificador:** `leave_active_raid_area`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando sales del área de una incursión y desaparece la barra. Morir o cambiar de dimensión en esa zona también cuenta, pero el final de la incursión no. No tiene variables.

### Al terminar una incursión

**Identificador:** `raid_finished`

Necesita que FancyMenu esté instalado en el servidor. Se ejecuta cuando termina una incursión mientras estás en su área.

- `$$raid_result`: `victory` o `defeat`

## Sonido y música

### Al empezar una pista musical

**Identificador:** `music_track_started`

Se ejecuta una vez cuando empieza a reproducirse una pista musical.

- `$$track_resource_location`: el archivo de sonido de la pista
- `$$track_display_name`: el nombre de la pista o `UNKNOWN`
- `$$track_artist`: el artista de la pista o `UNKNOWN`
- `$$track_duration_ms`: su duración en milisegundos o `0` si se desconoce

### Al detenerse una pista musical

**Identificador:** `music_track_stopped`

Se ejecuta una vez cuando se detiene la pista musical, ya sea porque terminó o porque otra la reemplazó.

Proporciona las mismas variables que **Al empezar una pista musical**: `$$track_resource_location`, `$$track_display_name`, `$$track_artist` y `$$track_duration_ms`.

### Al reproducirse un sonido en el mundo

**Identificador:** `world_sound_triggered`

Se ejecuta cada vez que empieza a reproducirse un sonido cerca de ti en el mundo, como el de una puerta o un creeper.

- `$$sound_resource_location`: el archivo de sonido
- `$$sound_display_name`: el subtítulo del sonido o `UNKNOWN`
- `$$sound_origin_pos_x`, `$$sound_origin_pos_y`, `$$sound_origin_pos_z`: de dónde proviene el sonido
- `$$sound_origin_distance_to_player`: qué tan lejos está
- `$$sound_origin_direction_from_player`: su dirección en grados (de 0 a 360), con respecto a hacia dónde miras
