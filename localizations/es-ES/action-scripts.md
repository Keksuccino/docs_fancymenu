---
title: Scripts de acción
description: 'Cómo usar scripts de acción con botones, deslizadores, ticker y más.'
---
# Scripts de acción

Los scripts de acción ejecutan tareas configuradas cuando se hace clic en un [Botón](./elements#button), se actualiza un [Ticker](./elements#ticker), cambia un [Deslizador](./elements#slider), se abre o cierra una pantalla, o cuando ocurre otro evento compatible. Instrucciones como **if**, **else-if**, **else** y **while** añaden control condicional.

> [!CAUTION]
> Los scripts de acción importados pueden modificar archivos, contactar con servidores, abrir enlaces o ejecutar comandos. Usa solo fuentes en las que confíes.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Editor de scripts de acción" style="max-width:800px;width:100%;height:auto;">

# ¿Qué son las acciones?

Una **acción** es una tarea o trabajo que FancyMenu ejecuta cuando se activa. Por ejemplo, una acción puede abrir una nueva pantalla, enviar un mensaje al chat o ajustar el volumen de un [elemento de audio](./elements#audio). En el editor de FancyMenu, las acciones se configuran con un valor (si es necesario) que proporciona detalles adicionales, como una URL o una dirección de servidor.

# Instrucciones

Para crear un comportamiento más complejo, FancyMenu admite instrucciones de control en los scripts de acción:

| Instrucción | Comportamiento |
|---|---|
| **If** | Ejecuta sus acciones solo cuando se cumplen sus [requisitos](./conditions). |
| **Else-If** | Comprueba otro conjunto de [requisitos](./conditions) cuando el **If** o **Else-If** anterior no se ejecutó. |
| **Else** | Se ejecuta cuando ninguno de los **If** o **Else-If** anteriores cumple los requisitos. |
| **While** | Repite sus acciones mientras se mantengan verdaderos sus [requisitos](./conditions). Se detiene tras tres segundos para evitar bucles infinitos; no lo uses como temporizador. |

# Bloques

Se pueden añadir bloques a los scripts, y ofrecen funciones útiles para tener más control sobre el flujo/tiempo de ejecución del script, además de algunas mejoras de comodidad:

| Bloque | Comportamiento |
|---|---|
| **Delay** | Inicia una cuenta atrás sin detener el resto del script. Sus acciones anidadas pasan a poder ejecutarse tras el retraso; la reinicialización de la pantalla reinicia la cuenta atrás. |
| **Execute Later** | Programa una nueva ejecución de sus acciones anidadas después del retraso cada vez que se alcanza el bloque. |
| **Comment** | Añade una nota dentro del script para organizarlo y no ejecuta ninguna acción. |

# Ejecución del script

Las acciones se ejecutan de arriba abajo. Si una acción falla, se registra y el script continúa.

Las descargas, la extracción de ZIP y las solicitudes HTTP finalizan más tarde; la siguiente acción no espera. Usa [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) o una variable de respuesta HTTP cuando el trabajo posterior dependa del resultado.

# ¿Dónde puedes usar scripts de acción?

Los scripts de acción son versátiles y se pueden usar en toda tu interfaz. Puedes asignarlos, por ejemplo, a:

- [**Buttons**](./elements#button): ejecutan una acción cuando se hace clic en el botón.
- [**Tickers**](./elements#ticker): ejecutan continuamente un script de acción para actualizar la información en pantalla dentro de un diseño.
- [**Sliders**](./elements#slider): activan un script de acción cada vez que cambia el valor del deslizador.
- **Eventos de pantalla:** ejecutan scripts cuando una pantalla se abre o se cierra (por ejemplo, reproducir un sonido cuando aparece un menú).
- [**Listeners**](./listeners): cuando un listener recibe su evento configurado, ejecuta su script de acción.
- [**Schedulers**](./schedulers): ejecutan acciones de forma programada, incluso cuando no hay ninguna pantalla abierta.

# Uso de marcadores de posición en acciones

Los valores de las acciones admiten contenido dinámico mediante **marcadores de posición**. La mayoría de las veces, estos marcadores usan una sintaxis parecida a JSON y se reemplazan por datos en tiempo real cuando se ejecuta la acción.

## Marcadores de posición tipo JSON

Estos son los [marcadores de posición](./placeholders) normales que se pueden usar en muchos lugares dentro de los diseños.

Siguen esta sintaxis:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Pueden obtener datos del juego, como el nombre del jugador, las dimensiones de la pantalla o valores calculados mediante el [marcador de posición **Calculator**](./placeholders#calculator-calc). También puedes anidar marcadores de posición para usos más avanzados.

## Marcadores de posición `$$` (variables)

Los valores `$$` son valores de solo lectura proporcionados a un script de acción concreto por la función que lo ejecuta.

Por ejemplo, un [Slider](./elements#slider) proporciona su valor actual como `$$value`.

Cada [listener](./listeners) documenta los valores `$$` que proporciona, como el botón del ratón pulsado o la estructura introducida.

Los nombres `$$` distinguen entre mayúsculas y minúsculas y solo funcionan en el script que los proporciona. Consulta [Listeners](./listeners#listener-variables).

## Delimitadores de valores de acción

Usa el delimitador exacto que se muestra para cada acción: `:`, `||` o `|||`. No existe sintaxis de escape para delimitadores dentro de un campo.

Los marcadores de posición se reemplazan antes de dividir el valor. Para `set_variable`, solo los dos puntos primeros separan el nombre del valor, por lo que los demás dos puntos siguen formando parte del valor.

## Valores de texto

Los [códigos de formato de FancyMenu](./text-formatting#minecraft-text-formatting) usan `&` en lugar del carácter `§` de Minecraft dondequiera que una acción acepte texto con formato.

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) y [**Paste to Chat**](#paste-to-chat-paste_to_chat) admiten estos códigos de formato.
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) acepta texto plano o JSON serializado de componentes de texto de Minecraft.
- [**Open URL in Browser**](#open-url-in-browser-openlink) aplica la misma conversión de códigos de formato antes de pasar la URL al sistema operativo.

# Cómo configurar y editar acciones

Para editar las acciones de un elemento y los bloques de instrucciones, **haz clic derecho sobre el elemento** y selecciona **Manage Action Script**. En el editor, puedes:

- **Añadir nuevas acciones o instrucciones:** inserta nuevas entradas de acción o instrucciones de control (if, else-if, else, while) para construir tu script.
- **Editar acciones o instrucciones existentes:** modifica el valor de la acción o cambia la lógica de control.
- **Eliminar acciones o instrucciones:** borra del script las acciones que no quieras.

Crea y edita scripts de listeners a través de [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Atajos del editor de scripts de acción

## Atajos

- `DEL` : Elimina rápidamente la entrada seleccionada
- `ENTER` : Inicia la edición en línea de la entrada seleccionada (o abre la pantalla de edición si no hay edición en línea para la entrada seleccionada)
- `Ctrl/Command + C` : Copia la acción seleccionada (por ahora solo funciona con acciones)
- `Ctrl/Command + V` : Pega la acción copiada previamente
- `Ctrl/Command + Z` : Un paso atrás (deshacer)
- `Ctrl/Command + Y` : Un paso adelante (rehacer)
- `ARROW UP` : Navega una entrada hacia arriba desde la seleccionada actualmente
- `ARROW DOWN` : Navega una entrada hacia abajo desde la seleccionada actualmente
- `SHIFT + ARROW UP` : Mueve la entrada seleccionada una posición arriba
- `SHIFT + ARROW DOWN` : Mueve la entrada seleccionada una posición abajo
- `A` : Abre rápidamente la pantalla Action Chooser para añadir una nueva acción
- `Ctrl/Command + S` : Termina/guarda desde la ventana del editor

## Edición

- Hacer doble clic en el valor de una acción te permite editarlo sin pasar por la pantalla completa de edición del valor.
- Las cadenas de instrucciones IF (con declaraciones ELSE/ELSE-IF añadidas), los bucles WHILE y las carpetas se pueden contraer (solo visualmente, no afecta a la lógica del script).
- El editor siempre añade las nuevas acciones debajo de la entrada seleccionada (o dentro de la cadena/bucle/carpeta seleccionada).
- Hacer clic derecho sobre el fondo gris oscuro del área del script abre un menú contextual con opciones para añadir acciones, instrucciones y todo lo demás importante.

# Acciones en detalle

Esta sección enumera las acciones integradas de FancyMenu.

## Next Track (`audio_next_track`)

**Propósito:** Pasa a la siguiente pista en un [elemento de audio](./elements#audio)

**Valor:** Obligatorio — `audio_element_identifier` (el ID del elemento de audio a controlar)

## Previous Track (`audio_previous_track`)

**Propósito:** Pasa a la pista anterior en un [elemento de audio](./elements#audio)

**Valor:** Obligatorio — `audio_element_identifier` (el ID del elemento de audio a controlar)

## Set Track Volume (`set_audio_element_volume`)

**Propósito:** Establece el volumen de un [elemento de audio](./elements#audio) (`0.0` a `1.0`)

**Valor:** Obligatorio — `element_identifier:volume`

## Toggle Play/Pause Track (`audio_toggle_play`)

**Propósito:** Alterna la pista actual de un [elemento de audio](./elements#audio) entre reproducción y pausa

**Valor:** Obligatorio — `audio_element_identifier`

## Play Audio (`play_audio`)

**Propósito:** Reproduce un recurso de audio una vez. El audio iniciado por esta acción se puede detener más tarde con [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

**Valor:** Obligatorio — configuración JSON con `audioSource`, `soundChannel` y `baseVolume`

**Ejemplo:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Comportamiento:**

- `baseVolume` se limita entre `0.0` y `1.0`.
- Un canal de sonido desconocido usa el canal Master.
- La acción no puede ejecutarse desde un [Ticker](./elements#ticker) asíncrono; FancyMenu muestra un error en su lugar.
- FancyMenu espera hasta diez segundos a que el recurso de audio esté listo.
- Las pistas iniciadas correctamente se pueden detener con [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

## Stop All Action Audios (`stop_all_action_audios`)

**Propósito:** Detiene todas las pistas de audio que se iniciaron mediante la [acción **Play Audio**](#play-audio-play_audio). Esto no detiene [elementos de audio](./elements#audio), sonidos de apertura/cierre de menú, sonidos de botones ni otros sistemas de audio.

**Valor:** No obligatorio

## Set Video Element Volume (`set_video_element_volume`)

**Propósito:** Establece el volumen de un [elemento de vídeo](./video) (`0.0` a `1.0`)

**Valor:** Obligatorio — `video_element_identifier:volume`

## Set Video Element Play Time (`set_video_element_play_time`)

**Propósito:** Sitúa un [elemento de vídeo](./video) en una marca de tiempo en milisegundos

**Valor:** Obligatorio — `video_element_identifier:timestamp_ms`

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)

**Propósito:** Alterna el estado de pausa de un [elemento de vídeo](./video)

**Valor:** Obligatorio — `video_element_identifier`

## Set Video Background Volume (`set_video_menu_background_volume`)

**Propósito:** Establece el volumen de un [fondo de vídeo del menú](./video) (`0.0` a `1.0`)

**Valor:** Obligatorio — `background_identifier:volume`

> [!NOTE]
> Para obtener el identificador de un fondo, haz clic derecho sobre el fondo del editor y selecciona 'Copy Background Identifier'.

## Set Video Background Play Time (`set_video_menu_background_play_time`)

**Propósito:** Sitúa un [fondo de vídeo del menú](./video) en una marca de tiempo en milisegundos

**Valor:** Obligatorio — `background_identifier:timestamp_ms`

> [!NOTE]
> Para obtener el identificador de un fondo, haz clic derecho sobre el fondo del editor y selecciona 'Copy Background Identifier'.

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)

**Propósito:** Alterna el estado de pausa de un [fondo de vídeo del menú](./video)

**Valor:** Obligatorio — `background_identifier`

> [!NOTE]
> Para obtener el identificador de un fondo, haz clic derecho sobre el fondo del editor y selecciona 'Copy Background Identifier'.

## Toggle Layout (`toggle_layout`)

**Propósito:** Alterna un diseño (activar/desactivar) por su nombre de archivo sin `.txt`

**Valor:** Obligatorio — `layout_name`

## Enable Layout (`enable_layout`)

**Propósito:** Activa y guarda un diseño por su nombre de archivo sin `.txt`

**Valor:** Obligatorio — `layout_name`

## Disable Layout (`disable_layout`)

**Propósito:** Desactiva y guarda un diseño por su nombre de archivo sin `.txt`

**Valor:** Obligatorio — `layout_name`

Las tres acciones de diseño guardan el estado en el archivo del diseño y actualizan la pantalla actual de inmediato. Usa el nombre de archivo distinguiendo mayúsculas y minúsculas, sin `.txt`.

## Open Screen or Custom GUI (`opengui`)

**Propósito:** Abre una pantalla por su identificador (vanilla, mod o interfaz personalizada)

**Valor:** Obligatorio — `screen_identifier`

Copia el identificador exacto, distinguiendo mayúsculas y minúsculas, desde la superposición de depuración [Screen Identifiers](./screen-identifiers).

Algunas pantallas de mods no se pueden crear directamente. Si la apertura falla, usa [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) en un widget que normalmente abriría esa pantalla.

## Close Screen (`closegui`)

**Propósito:** Cierra la pantalla activa

**Valor:** No obligatorio

## Update Screen (`update_screen`)

**Propósito:** Reinicializa la pantalla actual

**Valor:** No obligatorio

## Back to Last Screen (`back_to_last_screen`)

**Propósito:** Vuelve al padre de una [Custom GUI](./custom-guis) o a la instancia de pantalla cerrada más reciente

**Valor:** No obligatorio

## Join Server (`joinserver`)

**Propósito:** Conecta al jugador a un servidor de Minecraft

**Valor:** Obligatorio — `server_ip` o `server_ip:port`

Esta acción no puede ejecutarse mientras ya haya un mundo o servidor cargado. Se usa el puerto `25565` cuando se omite. Si la dirección no está en la lista de servidores guardados de Minecraft, FancyMenu la añade y la guarda.

## Enter World (`loadworld`)

**Propósito:** Entra en un mundo de Minecraft

**Valor:** Obligatorio — `world_folder_name`

El valor es el nombre de la carpeta de guardado. La acción no hace nada si ese guardado no existe o si ya hay otro mundo/servidor cargado.

## Enter/Join Last World/Server (`join_last_world`)

**Propósito:** Entra/conecta al último mundo o servidor en el que estuvo el jugador

**Valor:** No obligatorio

Esta acción no puede ejecutarse mientras haya otro mundo/servidor cargado. Un servidor recordado que no esté en la lista de servidores guardados de Minecraft se añade y se guarda antes de conectar.

## Leave World or Server (`disconnect_server_or_world`)

**Propósito:** Sale de un mundo o servidor y abre una pantalla especificada

**Valor:** Obligatorio — `screen_identifier`

Esta acción solo se ejecuta mientras haya un mundo y un jugador cargados. El destino puede ser un identificador de [Custom GUI](./custom-guis) o un [screen identifier](./screen-identifiers) que FancyMenu pueda construir. Si no se puede abrir el destino, FancyMenu vuelve a la pantalla de título.

## Quit Minecraft (`quitgame`)

**Propósito:** Cierra Minecraft por completo

**Valor:** No obligatorio

## Send Chat Message/Command (`sendmessage`)

**Propósito:** Envía un mensaje de chat o ejecuta un comando de chat. El texto del mensaje admite [códigos de formato de FancyMenu](./text-formatting#minecraft-text-formatting).

**Valor:** Obligatorio — `message_text` o `/command_text`

## Execute Command As Integrated Server (`execute_command_as_integrated_server`)

**Propósito:** Ejecuta forzosamente un comando en un jugador individual como servidor integrado, ignorando permisos y la configuración de trucos.

**Valor:** Obligatorio — texto del comando, por ejemplo `/give @p minecraft:diamond 1`

> [!WARNING]
> Esta acción solo funciona en un jugador individual mientras el mundo **no esté abierto a LAN**. Intencionadamente no hace nada cuando no existe un servidor integrado o cuando el servidor integrado se publica en LAN.

## Paste to Chat (`paste_to_chat`)

**Propósito:** Pega texto con formato en el campo de entrada del chat mientras hay un jugador/mundo cargado

**Valor:** Obligatorio — `true:Text` o `false:Text`

Cuando el chat todavía no está abierto, FancyMenu lo abre y establece el texto de entrada. Cuando el chat ya está abierto, `true` añade el texto al contenido existente y `false` lo reemplaza.

## Display In Chat [Client-Side] (`display_in_chat_client_side`)

**Propósito:** Muestra un mensaje de chat del lado del cliente mientras hay un mundo o servidor cargado. No envía nada al servidor.

**Valor:** Obligatorio — `text_or_json`

El valor puede ser texto plano o un componente de texto de Minecraft serializado. La acción no hace nada cuando no hay ningún mundo cargado.

## Send FM Data To Server (`send_fm_data_to_server`)

**Propósito:** Envía [FM Data](./fm-data) al servidor actual de FancyMenu.

**Valor:** Obligatorio — `data_identifier||data`

## Connect To Remote Server (`connect_to_remote_server`)

**Propósito:** Abre o reutiliza una conexión WebSocket iniciada por el cliente con un servidor remoto externo.

**Valor:** Obligatorio — URL del servidor remoto, por ejemplo `wss://example.com/ws`

Consulta [Remote Server Communication](./remote-server-communication#url-modes) para ver los formatos de URL aceptados.

## Send Data To Remote Server (`send_data_to_remote_server`)

**Propósito:** Abre o reutiliza una conexión con un servidor remoto y le envía datos de texto.

**Valor:** Obligatorio — `remote_server_url||data`

## Close Remote Server Connection (`close_remote_server_connection`)

**Propósito:** Cierra una conexión específica con un servidor remoto mediante su ID de solicitud.

**Valor:** Obligatorio — ID de solicitud, normalmente `$$request_id` de [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected)

## Close All Remote Server Connections (`close_all_remote_server_connections`)

**Propósito:** Cierra todas las conexiones activas con servidores remotos abiertas por FancyMenu.

**Valor:** No obligatorio

## Open URL in Browser (`openlink`)

**Propósito:** Pasa una URL al manejador predeterminado del sistema operativo sin mostrar un mensaje de confirmación de FancyMenu

**Valor:** Obligatorio — `https://example.com`

Usa enlaces `https://` de confianza. FancyMenu no muestra un mensaje de confirmación antes de pasar la URL al sistema operativo.

## Copy Text to Clipboard (`copytoclipboard`)

**Propósito:** Copia texto al portapapeles

**Valor:** Obligatorio — `text_to_copy`

## Print to Game Log (`print_to_log`)

**Propósito:** Escribe una línea en el registro del juego

**Valor:** Obligatorio — `text_to_log`

## Set Variable Value (FM Variable) (`set_variable`)

**Propósito:** Guarda contenido de texto en una [variable de FancyMenu](./variables)

**Valor:** Obligatorio — `variable_name:variable_value`

Los dos puntos primeros separan el nombre del valor. Los siguientes dos puntos siguen formando parte del valor. Los cambios se guardan de inmediato.

## Clear All Variables (FM Variable) (`clear_variables`)

**Propósito:** Borra todos los valores almacenados de [variables de FancyMenu](./variables)

**Valor:** No obligatorio

## Send HTTP Request (`send_http_request`)

**Propósito:** Inicia una solicitud HTTP/HTTPS en segundo plano; puede registrar y/o almacenar la respuesta en una variable

**Valor:** Obligatorio — configuración de la solicitud HTTP

| Ajuste | Comportamiento |
|---|---|
| URL | Punto final HTTP o HTTPS |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` o `OPTIONS` |
| Body | Se envía para métodos distintos de `GET` y `HEAD` |
| Content type | Valor `Content-Type` de la solicitud |
| Timeout | Segundos usados tanto para la conexión como para la lectura de la respuesta |
| Log response | Lee y escribe la respuesta en el registro |
| Response variable | Lee la respuesta y la almacena cuando finaliza la solicitud |
| Single-line response | Elimina los saltos de línea de la respuesta antes de almacenarla |
| Authentication | Ninguna, Basic, Bearer o API key |
| Headers | Encabezados personalizados opcionales de la solicitud |

Las solicitudes se ejecutan de forma asíncrona, así que la siguiente acción no espera. Los cuerpos de respuesta solo se leen cuando el registro está activado o se configura una variable de respuesta; los cuerpos de error que no son satisfactorios se leen desde la respuesta de error. No almacenes contraseñas ni tokens de acceso en la configuración de la acción.

## Manage Resource Pack (`manage_resource_pack`)

**Propósito:** Activa, desactiva o alterna un paquete de recursos, con recarga opcional

**Valor:** Obligatorio — `pack_name_or_id|||MODE|||reload_bool`

Los nombres visibles y los ID internos de los paquetes se comparan sin distinguir mayúsculas y minúsculas. Los paquetes marcados como obligatorios no se pueden desactivar.

## Reload Resource Packs (`reload_resource_packs`)

**Propósito:** Recarga los paquetes de recursos de Minecraft. Un tiempo de espera integrado de cinco segundos ignora las activaciones repetidas durante ese periodo para evitar abusos de recarga.

**Valor:** No obligatorio

## Reload FancyMenu (`reloadmenu`)

**Propósito:** Recarga diseños, [Custom GUIs](./custom-guis), [panoramas](./panoramas), [slideshows](./slideshows), ajustes y recursos gestionados por FancyMenu

**Valor:** No obligatorio

Esto no recarga los paquetes de recursos de Minecraft. Usa [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs) para eso.

> [!WARNING]
> Recargar es costoso. Actívalo desde una acción de botón deliberada, no desde un [Ticker](./elements#ticker) ni desde un [listener](./listeners) que se dispare con frecuencia.

## Toggle Element Animator (`toggle_element_animator`)

**Propósito:** Alterna el estado de reproducción guardado y reinicia la línea de tiempo activa coincidente del Animator

**Valor:** Obligatorio — `animator_identifier`

Consulta [Element Animator](./element-animator) para ver la configuración y los detalles del identificador.

## Enable Element Animator (`enable_element_animator`)

**Propósito:** Activa la reproducción; la línea de tiempo activa del Animator solo se reinicia cuando el estado cambia de desactivado a activado

**Valor:** Obligatorio — `animator_identifier`

## Disable Element Animator (`disable_element_animator`)

**Propósito:** Desactiva la reproducción y reinicia la línea de tiempo activa coincidente del Animator

**Valor:** Obligatorio — `animator_identifier`

## Reset Element Animator (`reset_element_animator`)

**Propósito:** Reinicia la línea de tiempo activa coincidente del Animator sin cambiar si la reproducción está activada

**Valor:** Obligatorio — `animator_identifier`

## Mimic Vanilla/Mod Button (`mimicbutton`)

**Propósito:** Imita la acción de clic de un botón vanilla o de un mod

**Valor:** Obligatorio — el [localizador de widget](./widget-locators) completo, por ejemplo `example.menu.identifier:505280`

## Mimic Keybind (`mimic_keybind`)

**Propósito:** Ejecuta un atajo de teclado o ratón de Minecraft, opcionalmente manteniéndolo pulsado

**Valor:** Obligatorio — `keybind_id|||keep_pressed_bool|||duration_ms`

| Campo | Significado |
|---|---|
| `keybind_id` | Identificador del atajo de teclado de Minecraft, como `key.jump` |
| `keep_pressed_bool` | `true` para mantener pulsada la tecla; `false` para una pulsación normal |
| `duration_ms` | Duración de la pulsación cuando `keep_pressed_bool` es `true`; por defecto `1000` |

## Set Text Input Field Value (`set_text_input_field_value`)

**Propósito:** Establece el valor de un [Campo de entrada de texto](./elements#text-input-field) personalizado o vanilla mediante su identificador de elemento.

**Valor:** Obligatorio — `element_identifier|||new_value|||force_set_when_inactive`

Los tres campos deben separarse con el delimitador triple `|||`. Establece `force_set_when_inactive` en `true` para actualizar también un campo de entrada deshabilitado; cuando es `false`, los campos inactivos no se modifican.

## Create File in Game Directory (`create_file_in_game_dir`)

**Propósito:** Crea un archivo vacío relativo al directorio de juego activo. Acepta el prefijo `.minecraft/` para apuntar al directorio convencional de Minecraft (que puede diferir de la instancia actual).

**Valor:** Obligatorio — `file_path`

Ejemplo: `config/some_mod_folder/new_file.txt`. Se crean los directorios padre que falten; un archivo existente no se modifica.

## Delete File/Folder in Game Directory (`delete_file_in_game_dir`)

**Propósito:** Elimina un archivo o borra recursivamente una carpeta relativa al directorio de juego activo. Acepta `.minecraft/` para apuntar al directorio convencional de Minecraft. Añade `*` para eliminar **todos los archivos directamente dentro** de una carpeta (ignora subdirectorios y conserva la carpeta).

**Valor:** Obligatorio — `target_path`

Por ejemplo, `config/downloads/*` elimina los archivos directamente dentro de `config/downloads/`, pero no recorre ni elimina sus subdirectorios.

## Copy File/Folder in Game Directory (`copy_file_in_game_dir`)

**Propósito:** Copia dentro del directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft. Un directorio con nombre se copia de forma recursiva. Añade `*` a la ruta de **origen** para copiar solo cada archivo hijo directo; el destino debe ser un directorio y no puede usar `*`.

**Valor:** Obligatorio — `source||destination`

Por ejemplo, `config/source/*||config/destination/` copia solo los archivos directamente dentro de `config/source/`. Con un origen con comodín, FancyMenu crea el directorio de destino cuando hace falta, pero no copia ningún subdirectorio del origen. La copia rechaza cualquier destino ya existente o archivo en conflicto en lugar de sobrescribirlo.

## Move File/Folder in Game Directory (`move_file_in_game_dir`)

**Propósito:** Mueve dentro del directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft. Añade `*` a la ruta de **origen** para mover solo cada archivo hijo directo; el destino debe ser un directorio y no puede usar `*`.

**Valor:** Obligatorio — `source||destination`

Por ejemplo, `config/source/*||config/destination/` mueve solo los archivos directamente dentro de `config/source/`. Con un origen con comodín, FancyMenu crea el directorio de destino cuando hace falta, pero deja los subdirectorios del origen en su sitio. El movimiento rechaza un destino ya existente o un archivo en conflicto en lugar de sobrescribirlo.

## Rename File/Folder in Game Directory (`rename_file_in_game_dir`)

**Propósito:** Cambia el nombre de un archivo o carpeta dentro de su carpeta padre actual; `.minecraft/` apunta al directorio convencional de Minecraft. Conserva el contenido intacto y rechaza un nombre de destino ya existente.

**Valor:** Obligatorio — `path||new_name`

## Download File to Game Directory (`download_file_to_game_dir`)

**Propósito:** Descarga un archivo en segundo plano a un directorio relativo al directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft.

**Valor:** Obligatorio — `url||target_folder`

El segundo campo es un **directorio de destino**, no una ruta completa de archivo de destino. FancyMenu crea el directorio cuando hace falta y determina el nombre del archivo a partir del encabezado `Content-Disposition` de la respuesta; si no, recurre a la ruta de la URL. El nombre resuelto se decodifica desde la URL y se sanea antes de usarse; si ninguna de las dos fuentes proporciona un nombre válido, FancyMenu genera uno. Un archivo existente con el mismo nombre se sobrescribe.

El [**On File Downloaded via Action** listener](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) se activa tanto tras intentos de descarga exitosos como fallidos y expone la URL, la ruta de destino resuelta y el estado de éxito.

Si tiene éxito, `$$target_file_path` es la ruta del archivo guardado. Si falla, puede contener solo el directorio de destino porque no se resolvió ningún nombre final de archivo.

## Extract ZIP File In Game Directory (`extract_zip_file_in_game_dir`)

**Propósito:** Extrae un ZIP en una carpeta de destino dentro del directorio de juego activo o del directorio convencional `.minecraft`. Activa [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) al finalizar.

**Valor:** Obligatorio — `source_zip_path||target_folder_path`

Los archivos existentes con nombres coincidentes se reemplazan. Extrae solo archivos ZIP de confianza.

## Open File/Folder In Game Directory (`open_file_folder_in_game_dir`)

**Propósito:** Abre un archivo o carpeta con la aplicación predeterminada del sistema operativo. El destino debe permanecer dentro del directorio de juego o del directorio `.minecraft` predeterminado por motivos de seguridad.

**Valor:** Obligatorio — `target_path`

## Write File in Game Directory (`write_file_in_game_dir`)

**Propósito:** Escribe o añade texto relativo al directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft. Crea el archivo y los directorios padre si faltan. `\n` inserta saltos de línea; `append_bool=false` reemplaza un archivo existente.

**Valor:** Obligatorio — `path|||content|||append_bool`

## Select File from System (`select_file_to_game_dir`)

**Propósito:** Abre un selector de archivos nativo y copia el archivo seleccionado dentro del directorio de juego activo, o del `.minecraft/` convencional cuando se usa el prefijo. Admite filtros por extensión, una etiqueta personalizada para el filtro y una opción de sobrescritura.

**Valor:** Obligatorio — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` es la ruta completa del archivo de destino. Separa varias extensiones con `;` o `,`, por ejemplo `png;jpg`; una lista de extensiones vacía permite todos los archivos. Si `overwrite_bool` es `false`, la acción falla en lugar de reemplazar un archivo de destino existente.

El [**On File Selected** listener](./listeners#on-file-selected-file_selected_via_action) se activa cuando el archivo se copia, se cancela el selector o falla la selección. Expone la ruta seleccionada, la ruta de destino resuelta, los estados de éxito/cancelación y un motivo de fallo.

## Show Toast (`show_toast`)

**Propósito:** Muestra una notificación toast configurable

**Valor:** Obligatorio — configuración JSON del toast

El editor almacena esta acción como JSON. Prefiere su ventana de configuración en lugar de editar el valor manualmente.

| Campo | Significado |
|---|---|
| `width` | Limitado entre `120` y `320` píxeles |
| `durationMs` | Limitado entre `1000` y `600000` milisegundos |
| `title` | Texto plano, un componente de texto de Minecraft serializado o vacío |
| `message` | Texto plano, un componente de texto serializado o vacío |
| `iconSource` | [Origen de imagen](./resources) opcional |
| `backgroundSource` | [Origen de imagen](./resources) opcional |

## Start Scheduler (`start_scheduler`)

**Propósito:** Inicia un scheduler por su ID de scheduler.

**Valor:** Obligatorio — `scheduler_id`

Consulta [Schedulers](./schedulers) para crear y gestionar IDs de scheduler.

## Stop Scheduler (`stop_scheduler`)

**Propósito:** Detiene un scheduler por su ID de scheduler.

**Valor:** Obligatorio — `scheduler_id`

## Set Minecraft Option (`edit_minecraft_option`)

**Propósito:** Edita una opción de configuración de Minecraft

**Valor:** Obligatorio — `option_name:set_to_value`
