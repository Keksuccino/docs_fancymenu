---
title: Scripts de acciones
description: 'Cómo usar scripts de acciones con botones, deslizadores, tickers y más.'
---
# Scripts de acciones

Los scripts de acciones ejecutan tareas configuradas cuando se hace clic en un [Botón](./elements#button), cuando un [Ticker](./elements#ticker) se actualiza, cuando un [Deslizador](./elements#slider) cambia, cuando una pantalla se abre o se cierra, o cuando ocurre otro evento compatible. Las instrucciones como **if**, **else-if**, **else** y **while** agregan control condicional.

> [!CAUTION]
> Los scripts de acciones importados pueden modificar archivos, contactar servidores, abrir enlaces o ejecutar comandos. Úsalos solo de fuentes en las que confíes.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Editor de scripts de acciones" style="max-width:800px;width:100%;height:auto;">

# ¿Qué son las acciones?

Una **acción** es una tarea o trabajo que FancyMenu ejecuta cuando se activa. Por ejemplo, una acción puede abrir una nueva pantalla, enviar un mensaje al chat o ajustar el volumen de un [elemento de audio](./elements#audio). En el editor de FancyMenu, las acciones se configuran con un valor (si es necesario) que proporciona detalles adicionales, como una URL o la dirección de un servidor.

# Instrucciones

Para crear comportamientos más complejos, FancyMenu admite instrucciones de control en los scripts de acciones:

| Instrucción | Comportamiento |
|---|---|
| **If** | Ejecuta sus acciones solo cuando se cumplen sus [requisitos](./conditions). |
| **Else-If** | Verifica otro conjunto de [requisitos](./conditions) cuando el **If** o **Else-If** anterior no se ejecutó. |
| **Else** | Se ejecuta cuando ninguno de los **If** o **Else-If** anteriores cumple sus requisitos. |
| **While** | Repite sus acciones mientras sus [requisitos](./conditions) sigan siendo verdaderos. Se detiene después de tres segundos para evitar bucles infinitos; no lo uses como temporizador. |

# Bloques

Se pueden agregar bloques a los scripts, y ofrecen funciones útiles para tener más control sobre el flujo y el tiempo de ejecución del script, además de algunas funciones prácticas de calidad de vida:

| Bloque | Comportamiento |
|---|---|
| **Delay** | Inicia una cuenta regresiva sin detener el resto del script. Sus acciones anidadas quedan habilitadas después del retraso; la reinicialización de la pantalla restablece la cuenta regresiva. |
| **Execute Later** | Programa una nueva ejecución de sus acciones anidadas después del retraso cada vez que se llega al bloque. |
| **Comment** | Agrega una nota dentro del script para organizarlo y no ejecuta ninguna acción. |

# Ejecución del script

Las acciones se ejecutan de arriba hacia abajo. Si una acción falla, se registra y luego el script continúa.

Las descargas, la extracción de ZIP y las solicitudes HTTP terminan después; la siguiente acción no espera. Usa [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) o una variable de respuesta HTTP cuando el trabajo posterior dependa del resultado.

# ¿Dónde puedes usar scripts de acciones?

Los scripts de acciones son versátiles y pueden usarse en todo tu diseño. Puedes asignarlos, por ejemplo, a:

- [**Botones**](./elements#button): Ejecutan una acción cuando se hace clic en el botón.
- [**Tickers**](./elements#ticker): Ejecutan continuamente un script de acciones para actualizar información en pantalla dentro de un diseño.
- [**Deslizadores**](./elements#slider): Activan un script de acciones cada vez que cambia el valor del deslizador.
- **Eventos de pantalla:** Ejecutan scripts cuando una pantalla se abre o se cierra (por ejemplo, reproducir un sonido cuando aparece un menú).
- [**Listeners**](./listeners): Cuando un listener recibe el evento configurado, ejecuta su script de acciones.
- [**Schedulers**](./schedulers): Ejecutan acciones de forma programada, incluso cuando no hay ninguna pantalla abierta.

# Uso de placeholders en las acciones

Los valores de las acciones admiten contenido dinámico mediante **placeholders**. La mayoría de las veces, estos placeholders usan una sintaxis similar a JSON y se reemplazan con datos en tiempo real cuando se ejecuta la acción.

## Placeholders con formato similar a JSON

Estos son los [placeholders](./placeholders) normales que se pueden usar en muchos lugares dentro de los diseños.

Siguen esta sintaxis:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Pueden obtener datos del juego como el nombre del jugador, las dimensiones de la pantalla o valores calculados usando el [placeholder **Calculator**](./placeholders#calculator-calc). También puedes anidar placeholders para usos más avanzados.

## Placeholders `$$` (variables)

Los valores `$$` son valores de solo lectura proporcionados a un script de acciones específico por la función que lo ejecuta.

Por ejemplo, un [Deslizador](./elements#slider) proporciona su valor actual como `$$value`.

Cada [listener](./listeners) documenta los valores `$$` que proporciona, como un botón del mouse presionado o una estructura ingresada.

Los nombres `$$` distinguen mayúsculas y minúsculas y solo funcionan en el script que los proporciona. Consulta [Listeners](./listeners#listener-variables).

## Delimitadores de valores de acción

Usa el delimitador exacto que se muestra para cada acción: `:`, `||` o `|||`. No existe sintaxis de escape para delimitadores dentro de un campo.

Los placeholders se reemplazan antes de que el valor se divida. Para `set_variable`, solo el primer dos puntos separa el nombre del valor, así que los dos puntos posteriores siguen formando parte del valor.

## Valores de texto

Los [códigos de formato de FancyMenu](./text-formatting#minecraft-text-formatting) usan `&` en lugar del carácter `§` de Minecraft donde sea que una acción acepte texto con formato.

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) y [**Paste to Chat**](#paste-to-chat-paste_to_chat) admiten estos códigos de formato.
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) acepta texto simple o JSON serializado de componentes de texto de Minecraft.
- [**Open URL in Browser**](#open-url-in-browser-openlink) aplica la misma conversión de códigos de formato antes de pasar la URL al sistema operativo.

# Cómo configurar y editar acciones

Para editar las acciones y bloques de instrucciones de un elemento, **haz clic derecho sobre el elemento** y selecciona **Manage Action Script**. En el editor, puedes:

- **Agregar nuevas acciones o instrucciones:** Inserta nuevas entradas de acción o instrucciones de control (if, else-if, else, while) para construir tu script.
- **Editar acciones o instrucciones existentes:** Modifica el valor de la acción o cambia la lógica de control.
- **Eliminar acciones o instrucciones:** Borra las acciones o instrucciones que no quieras.

Crea y edita scripts de listeners mediante [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Atajos del editor de scripts de acciones

## Atajos

- `DEL` : Elimina rápidamente la entrada seleccionada
- `ENTER` : Inicia la edición en línea de la entrada seleccionada (o abre la pantalla de edición si no hay edición en línea para la entrada seleccionada)
- `Ctrl/Command + C` : Copia la acción seleccionada (por ahora solo funciona con acciones)
- `Ctrl/Command + V` : Pega la acción copiada previamente
- `Ctrl/Command + Z` : Un paso atrás (deshacer)
- `Ctrl/Command + Y` : Un paso adelante (rehacer)
- `ARROW UP` : Navega una entrada hacia arriba desde la actualmente seleccionada
- `ARROW DOWN` : Navega una entrada hacia abajo desde la actualmente seleccionada
- `SHIFT + ARROW UP` : Mueve la entrada seleccionada una posición hacia arriba
- `SHIFT + ARROW DOWN` : Mueve la entrada seleccionada una posición hacia abajo
- `A` : Abre rápidamente la pantalla Action Chooser para agregar una nueva acción
- `Ctrl/Command + S` : Termina/guarda desde la ventana del editor

## Edición

- Hacer doble clic en el valor de una acción te permite editarlo sin entrar a la pantalla completa de edición de valores.
- Las cadenas de instrucciones IF (con ELSE/ELSE-IF agregados), los bucles WHILE y las carpetas se pueden contraer (solo visualmente, no afecta la lógica del script).
- El editor siempre agrega nuevas acciones debajo de la entrada seleccionada (o anidadas en la cadena/bucle/carpeta seleccionada).
- Hacer clic derecho en el fondo gris oscuro del área del script abre un menú contextual con opciones para agregar acciones, instrucciones y todo lo demás importante.

# Acciones en detalle

Esta sección enumera las acciones integradas de FancyMenu.

## Siguiente pista (`audio_next_track`)

**Propósito:** Va a la siguiente pista en un [elemento de audio](./elements#audio)

**Valor:** Requerido — `audio_element_identifier` (el ID del elemento de audio a controlar)

## Pista anterior (`audio_previous_track`)

**Propósito:** Va a la pista anterior en un [elemento de audio](./elements#audio)

**Valor:** Requerido — `audio_element_identifier` (el ID del elemento de audio a controlar)

## Establecer volumen de la pista (`set_audio_element_volume`)

**Propósito:** Establece el volumen de un [elemento de audio](./elements#audio) (`0.0` a `1.0`)

**Valor:** Requerido — `element_identifier:volume`

## Alternar reproducir/pausar pista (`audio_toggle_play`)

**Propósito:** Alterna la pista actual de un [elemento de audio](./elements#audio) entre reproducida y en pausa

**Valor:** Requerido — `audio_element_identifier`

## Reproducir audio (`play_audio`)

**Propósito:** Reproduce un recurso de audio una sola vez. El audio iniciado por esta acción se puede detener después con [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

**Valor:** Requerido — Configuración JSON con `audioSource`, `soundChannel` y `baseVolume`

**Ejemplo:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Comportamiento:**

- `baseVolume` se limita a `0.0`–`1.0`.
- Un canal de sonido desconocido usa el canal Master.
- La acción no puede ejecutarse desde un [Ticker](./elements#ticker) asíncrono; FancyMenu muestra un error en su lugar.
- FancyMenu espera hasta diez segundos a que el recurso de audio esté listo.
- Las pistas iniciadas correctamente se pueden detener con [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

## Detener todos los audios de acción (`stop_all_action_audios`)

**Propósito:** Detiene todas las pistas de audio que fueron iniciadas por la [acción **Play Audio**](#play-audio-play_audio). Esto no detiene [elementos de audio](./elements#audio), sonidos de abrir/cerrar menú, sonidos de botones ni otros sistemas de audio.

**Valor:** No requerido

## Establecer volumen del elemento de video (`set_video_element_volume`)

**Propósito:** Establece el volumen de un [elemento de video](./video) (`0.0` a `1.0`)

**Valor:** Requerido — `video_element_identifier:volume`

## Establecer tiempo de reproducción del elemento de video (`set_video_element_play_time`)

**Propósito:** Avanza un [elemento de video](./video) a una marca de tiempo en milisegundos

**Valor:** Requerido — `video_element_identifier:timestamp_ms`

## Alternar estado de pausa del elemento de video (`toggle_video_element_pause_state`)

**Propósito:** Alterna el estado de pausa de un [elemento de video](./video)

**Valor:** Requerido — `video_element_identifier`

## Establecer volumen del fondo de video (`set_video_menu_background_volume`)

**Propósito:** Establece el volumen de un [fondo de menú de video](./video) (`0.0` a `1.0`)

**Valor:** Requerido — `background_identifier:volume`

> [!NOTE]
> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y selecciona 'Copy Background Identifier'.

## Establecer tiempo de reproducción del fondo de video (`set_video_menu_background_play_time`)

**Propósito:** Avanza un [fondo de menú de video](./video) a una marca de tiempo en milisegundos

**Valor:** Requerido — `background_identifier:timestamp_ms`

> [!NOTE]
> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y selecciona 'Copy Background Identifier'.

## Alternar estado de pausa del fondo de video (`toggle_video_menu_background_pause_state`)

**Propósito:** Alterna el estado de pausa de un [fondo de menú de video](./video)

**Valor:** Requerido — `background_identifier`

> [!NOTE]
> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y selecciona 'Copy Background Identifier'.

## Alternar diseño (`toggle_layout`)

**Propósito:** Activa o desactiva un diseño por su nombre de archivo sin `.txt`

**Valor:** Requerido — `layout_name`

## Activar diseño (`enable_layout`)

**Propósito:** Habilita y guarda un diseño por su nombre de archivo sin `.txt`

**Valor:** Requerido — `layout_name`

## Desactivar diseño (`disable_layout`)

**Propósito:** Deshabilita y guarda un diseño por su nombre de archivo sin `.txt`

**Valor:** Requerido — `layout_name`

Las tres acciones de diseño guardan el estado en el archivo del diseño y actualizan la pantalla actual de inmediato. Usa el nombre exacto del archivo, respetando mayúsculas y minúsculas, sin `.txt`.

## Abrir pantalla o GUI personalizada (`opengui`)

**Propósito:** Abre una pantalla por su identificador (vanilla, mod o GUI personalizada)

**Valor:** Requerido — `screen_identifier`

Copia el identificador exacto, respetando mayúsculas y minúsculas, desde la superposición de depuración [Screen Identifiers](./screen-identifiers).

Algunas pantallas de mods no se pueden crear directamente. Si la apertura falla, usa [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) en un widget que normalmente abriría esa pantalla.

## Cerrar pantalla (`closegui`)

**Propósito:** Cierra la pantalla activa

**Valor:** No requerido

## Actualizar pantalla (`update_screen`)

**Propósito:** Reinicializa la pantalla actual

**Valor:** No requerido

## Regresar a la última pantalla (`back_to_last_screen`)

**Propósito:** Regresa al padre de una [GUI personalizada](./custom-guis) o a la instancia de pantalla cerrada más reciente

**Valor:** No requerido

## Unirse a un servidor (`joinserver`)

**Propósito:** Conecta al jugador a un servidor de Minecraft

**Valor:** Requerido — `server_ip` o `server_ip:port`

Esta acción no puede ejecutarse mientras ya haya un mundo o servidor cargado. Se usa el puerto `25565` cuando se omite. Si la dirección no está en la lista de servidores guardados de Minecraft, FancyMenu la agrega y la guarda.

## Entrar a un mundo (`loadworld`)

**Propósito:** Entra a un mundo de Minecraft

**Valor:** Requerido — `world_folder_name`

El valor es el nombre de la carpeta de guardado. La acción no hace nada si ese guardado no existe o si ya hay otro mundo/servidor cargado.

## Entrar/Unirse al último mundo/servidor (`join_last_world`)

**Propósito:** Entra o se une al último mundo o servidor en el que estuvo el jugador

**Valor:** No requerido

Esta acción no puede ejecutarse mientras otro mundo/servidor esté cargado. Un servidor recordado que no esté en la lista de servidores guardados de Minecraft se agrega y se guarda antes de conectarse.

## Salir del mundo o servidor (`disconnect_server_or_world`)

**Propósito:** Sale de un mundo o servidor y abre una pantalla específica

**Valor:** Requerido — `screen_identifier`

Esta acción solo se ejecuta cuando hay un mundo y un jugador cargados. El destino puede ser un identificador de [GUI personalizada](./custom-guis) o un [identificador de pantalla](./screen-identifiers) que FancyMenu pueda construir. Si el destino no se puede abrir, FancyMenu regresa a la pantalla de título.

## Salir de Minecraft (`quitgame`)

**Propósito:** Cierra Minecraft por completo

**Valor:** No requerido

## Enviar mensaje/comando al chat (`sendmessage`)

**Propósito:** Envía un mensaje al chat o ejecuta un comando de chat. El texto del mensaje admite [códigos de formato de FancyMenu](./text-formatting#minecraft-text-formatting).

**Valor:** Requerido — `message_text` o `/command_text`

## Ejecutar comando como servidor integrado (`execute_command_as_integrated_server`)

**Propósito:** Fuerza la ejecución de un comando en un jugador individual como servidor integrado, ignorando permisos y la configuración de trucos.

**Valor:** Requerido — Texto del comando, por ejemplo `/give @p minecraft:diamond 1`

> [!WARNING]
> Esta acción solo funciona en un jugador individual mientras el mundo **no esté abierto a LAN**. Intencionalmente no hace nada cuando no existe un servidor integrado o cuando el servidor integrado está publicado a LAN.

## Pegar al chat (`paste_to_chat`)

**Propósito:** Pega texto con formato en el campo de entrada del chat mientras hay un jugador/mundo cargado

**Valor:** Requerido — `true:Text` o `false:Text`

Cuando el chat aún no está abierto, FancyMenu lo abre y establece el texto de entrada. Cuando el chat ya está abierto, `true` agrega al texto existente y `false` lo reemplaza.

## Mostrar en el chat [Del lado del cliente] (`display_in_chat_client_side`)

**Propósito:** Muestra un mensaje de chat del lado del cliente mientras hay un mundo o servidor cargado. No envía nada al servidor.

**Valor:** Requerido — `text_or_json`

El valor puede ser texto simple o un componente de texto de Minecraft serializado. La acción no hace nada cuando no hay un mundo cargado.

## Enviar datos FM al servidor (`send_fm_data_to_server`)

**Propósito:** Envía [FM Data](./fm-data) al servidor actual de FancyMenu.

**Valor:** Requerido — `data_identifier||data`

## Conectarse a un servidor remoto (`connect_to_remote_server`)

**Propósito:** Abre o reutiliza una conexión WebSocket iniciada por el cliente a un servidor remoto externo.

**Valor:** Requerido — URL del servidor remoto, por ejemplo `wss://example.com/ws`

Consulta [Remote Server Communication](./remote-server-communication#url-modes) para conocer los formatos de URL aceptados.

## Enviar datos a un servidor remoto (`send_data_to_remote_server`)

**Propósito:** Abre o reutiliza una conexión a un servidor remoto y le envía datos de texto.

**Valor:** Requerido — `remote_server_url||data`

## Cerrar conexión con servidor remoto (`close_remote_server_connection`)

**Propósito:** Cierra una conexión específica con un servidor remoto por ID de solicitud.

**Valor:** Requerido — ID de solicitud, normalmente `$$request_id` de [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected)

## Cerrar todas las conexiones con servidores remotos (`close_all_remote_server_connections`)

**Propósito:** Cierra todas las conexiones activas con servidores remotos abiertas por FancyMenu.

**Valor:** No requerido

## Abrir URL en el navegador (`openlink`)

**Propósito:** Pasa una URL al manejador predeterminado del sistema operativo sin mostrar un aviso de confirmación de FancyMenu

**Valor:** Requerido — `https://example.com`

Usa enlaces `https://` de confianza. FancyMenu no muestra un aviso de confirmación antes de pasar la URL al sistema operativo.

## Copiar texto al portapapeles (`copytoclipboard`)

**Propósito:** Copia texto al portapapeles

**Valor:** Requerido — `text_to_copy`

## Imprimir en el registro del juego (`print_to_log`)

**Propósito:** Escribe una línea en el registro del juego

**Valor:** Requerido — `text_to_log`

## Establecer valor de variable (variable de FM) (`set_variable`)

**Propósito:** Guarda contenido de texto en una [variable de FancyMenu](./variables)

**Valor:** Requerido — `variable_name:variable_value`

El primer dos puntos separa el nombre del valor. Los dos puntos posteriores siguen formando parte del valor. Los cambios se guardan de inmediato.

## Borrar todas las variables (variable de FM) (`clear_variables`)

**Propósito:** Borra todos los valores almacenados de [variables de FancyMenu](./variables)

**Valor:** No requerido

## Enviar solicitud HTTP (`send_http_request`)

**Propósito:** Inicia una solicitud HTTP/HTTPS en segundo plano; puede registrar y/o guardar la respuesta en una variable

**Valor:** Requerido — Configuración de solicitud HTTP

| Configuración | Comportamiento |
|---|---|
| URL | Endpoint HTTP o HTTPS |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` u `OPTIONS` |
| Body | Se envía para métodos distintos de `GET` y `HEAD` |
| Content type | Valor `Content-Type` de la solicitud |
| Timeout | Segundos usados tanto para la conexión como para la lectura de la respuesta |
| Log response | Lee y escribe la respuesta en el registro |
| Response variable | Lee la respuesta y la guarda después de que la solicitud termina |
| Single-line response | Elimina los saltos de línea de la respuesta antes de guardarla |
| Authentication | Ninguna, Basic, Bearer o clave API |
| Headers | Encabezados personalizados opcionales de la solicitud |

Las solicitudes se ejecutan de forma asíncrona, así que la siguiente acción no espera. Los cuerpos de respuesta solo se leen cuando el registro está habilitado o se configura una variable de respuesta; los cuerpos que no son exitosos se leen desde la respuesta de error. No guardes contraseñas ni tokens de acceso en la configuración de la acción.

## Administrar paquete de recursos (`manage_resource_pack`)

**Propósito:** Habilita, deshabilita o alterna un paquete de recursos, con recarga opcional

**Valor:** Requerido — `pack_name_or_id|||MODE|||reload_bool`

Los nombres visibles y los IDs internos de los paquetes se comparan sin distinguir mayúsculas y minúsculas. Los paquetes marcados como obligatorios no se pueden deshabilitar.

## Recargar paquetes de recursos (`reload_resource_packs`)

**Propósito:** Recarga los paquetes de recursos de Minecraft. Un enfriamiento integrado de cinco segundos ignora activaciones repetidas durante ese periodo para evitar spam de recargas.

**Valor:** No requerido

## Recargar FancyMenu (`reloadmenu`)

**Propósito:** Recarga los diseños, [GUIs personalizadas](./custom-guis), [panoramas](./panoramas), [presentaciones de diapositivas](./slideshows), ajustes y recursos administrados por FancyMenu

**Valor:** No requerido

Esto no recarga los paquetes de recursos de Minecraft. Usa [**Recargar paquetes de recursos**](#recargar-paquetes-de-recursos-reload_resource_packs) para eso.

> [!WARNING]
> Recargar es costoso. Actívalo desde una acción de botón deliberada, no desde un [Ticker](./elements#ticker) ni desde un [listener](./listeners) que se dispare con frecuencia.

## Alternar animador de elemento (`toggle_element_animator`)

**Propósito:** Alterna el estado de reproducción guardado y reinicia la línea de tiempo activa del Animator correspondiente

**Valor:** Requerido — `animator_identifier`

Consulta [Element Animator](./element-animator) para ver la configuración y los detalles del identificador.

## Habilitar animador de elemento (`enable_element_animator`)

**Propósito:** Habilita la reproducción; una línea de tiempo activa del Animator solo se reinicia cuando el estado cambia de deshabilitado a habilitado

**Valor:** Requerido — `animator_identifier`

## Deshabilitar animador de elemento (`disable_element_animator`)

**Propósito:** Deshabilita la reproducción y reinicia la línea de tiempo activa del Animator correspondiente

**Valor:** Requerido — `animator_identifier`

## Restablecer animador de elemento (`reset_element_animator`)

**Propósito:** Restablece la línea de tiempo activa del Animator correspondiente sin cambiar si la reproducción está habilitada

**Valor:** Requerido — `animator_identifier`

## Imitar botón vanilla/mod (`mimicbutton`)

**Propósito:** Imita la acción de clic de un botón vanilla o de un mod

**Valor:** Requerido — el [selector de widget](./widget-locators) completo, por ejemplo `example.menu.identifier:505280`

## Imitar tecla asignada (`mimic_keybind`)

**Propósito:** Ejecuta una tecla o botón del mouse de Minecraft, opcionalmente manteniéndolo presionado

**Valor:** Requerido — `keybind_id|||keep_pressed_bool|||duration_ms`

| Campo | Significado |
|---|---|
| `keybind_id` | Identificador de tecla asignada de Minecraft, como `key.jump` |
| `keep_pressed_bool` | `true` para mantener presionada la tecla; `false` para una pulsación normal |
| `duration_ms` | Duración de la pulsación cuando `keep_pressed_bool` es `true`; el valor predeterminado es `1000` |

## Establecer valor de campo de entrada de texto (`set_text_input_field_value`)

**Propósito:** Establece el valor de un [Campo de entrada de texto](./elements#text-input-field) personalizado o vanilla por identificador de elemento.

**Valor:** Requerido — `element_identifier|||new_value|||force_set_when_inactive`

Los tres campos deben separarse con el delimitador de triple barra `|||`. Establece `force_set_when_inactive` en `true` para actualizar también un campo de entrada deshabilitado; cuando es `false`, los campos inactivos no se modifican.

## Crear archivo en el directorio del juego (`create_file_in_game_dir`)

**Propósito:** Crea un archivo vacío relativo al directorio activo del juego. Acepta el prefijo `.minecraft/` para apuntar al directorio convencional de Minecraft (que puede ser distinto de la instancia actual).

**Valor:** Requerido — `file_path`

Ejemplo: `config/some_mod_folder/new_file.txt`. Se crean los directorios padre faltantes; un archivo existente no se modifica.

## Eliminar archivo/carpeta en el directorio del juego (`delete_file_in_game_dir`)

**Propósito:** Elimina un archivo o borra recursivamente una carpeta relativa al directorio activo del juego. Acepta `.minecraft/` para apuntar al directorio convencional de Minecraft. Agrega `*` para eliminar **solo todos los archivos directamente dentro** de una carpeta (ignora subdirectorios y conserva la carpeta).

**Valor:** Requerido — `target_path`

Por ejemplo, `config/downloads/*` elimina los archivos directamente dentro de `config/downloads/`, pero no recorre ni elimina sus subdirectorios.

## Copiar archivo/carpeta en el directorio del juego (`copy_file_in_game_dir`)

**Propósito:** Copia dentro del directorio activo del juego; `.minecraft/` apunta al directorio convencional de Minecraft. Un directorio con nombre se copia de forma recursiva. Agrega `*` a la ruta de **origen** para copiar solo cada archivo hijo directo; el destino debe ser un directorio y no puede usar `*`.

**Valor:** Requerido — `source||destination`

Por ejemplo, `config/source/*||config/destination/` copia solo los archivos directamente dentro de `config/source/`. Con un origen comodín, FancyMenu crea el directorio de destino cuando es necesario, pero no copia ningún subdirectorio del origen. La copia rechaza cualquier destino existente o archivo en conflicto en lugar de sobrescribirlo.

## Mover archivo/carpeta en el directorio del juego (`move_file_in_game_dir`)

**Propósito:** Mueve dentro del directorio activo del juego; `.minecraft/` apunta al directorio convencional de Minecraft. Agrega `*` a la ruta de **origen** para mover solo cada archivo hijo directo; el destino debe ser un directorio y no puede usar `*`.

**Valor:** Requerido — `source||destination`

Por ejemplo, `config/source/*||config/destination/` mueve solo los archivos directamente dentro de `config/source/`. Con un origen comodín, FancyMenu crea el directorio de destino cuando es necesario, pero deja en su lugar los subdirectorios del origen. El movimiento rechaza un destino existente o un archivo en conflicto en lugar de sobrescribirlo.

## Renombrar archivo/carpeta en el directorio del juego (`rename_file_in_game_dir`)

**Propósito:** Renombra un archivo o carpeta dentro de su directorio padre actual; `.minecraft/` apunta al directorio convencional de Minecraft. Conserva el contenido intacto y rechaza un nombre de destino existente.

**Valor:** Requerido — `path||new_name`

## Descargar archivo al directorio del juego (`download_file_to_game_dir`)

**Propósito:** Descarga un archivo en segundo plano a un directorio relativo al directorio activo del juego; `.minecraft/` apunta al directorio convencional de Minecraft.

**Valor:** Requerido — `url||target_folder`

El segundo campo es un **directorio destino**, no una ruta completa de archivo de destino. FancyMenu crea el directorio cuando es necesario y determina el nombre de archivo a partir del encabezado `Content-Disposition` de la respuesta; si no, usa la ruta de la URL. El nombre resuelto se decodifica desde URL y se sanitiza antes de usarse; si ninguna fuente proporciona un nombre utilizable, FancyMenu genera uno. Un archivo existente con el mismo nombre se sobrescribe.

El [**listener On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) se activa después de intentos de descarga exitosos y fallidos, y expone la URL, la ruta de destino resuelta y el estado de éxito.

Si tiene éxito, `$$target_file_path` es la ruta del archivo guardado. Si falla, puede contener solo el directorio de destino porque no se resolvió un nombre final de archivo.

## Extraer archivo ZIP en el directorio del juego (`extract_zip_file_in_game_dir`)

**Propósito:** Extrae un ZIP a una carpeta destino dentro del directorio activo del juego o del directorio convencional `.minecraft`. Activa [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) al terminar.

**Valor:** Requerido — `source_zip_path||target_folder_path`

Los archivos existentes con nombres coincidentes se reemplazan. Extrae solo archivos ZIP de confianza.

## Abrir archivo/carpeta en el directorio del juego (`open_file_folder_in_game_dir`)

**Propósito:** Abre un archivo o carpeta con la aplicación predeterminada del sistema operativo. Por seguridad, el destino debe permanecer dentro del directorio del juego o del directorio `.minecraft` predeterminado.

**Valor:** Requerido — `target_path`

## Escribir archivo en el directorio del juego (`write_file_in_game_dir`)

**Propósito:** Escribe o agrega texto relativo al directorio activo del juego; `.minecraft/` apunta al directorio convencional de Minecraft. Crea el archivo y sus directorios padre si no existen. `\n` inserta saltos de línea; `append_bool=false` reemplaza un archivo existente.

**Valor:** Requerido — `path|||content|||append_bool`

## Seleccionar archivo desde el sistema (`select_file_to_game_dir`)

**Propósito:** Abre un selector nativo de archivos y copia el archivo seleccionado dentro del directorio activo del juego, o del `.minecraft/` convencional cuando se usa el prefijo. Admite filtros por extensión, una etiqueta de filtro personalizada y un interruptor de sobrescritura.

**Valor:** Requerido — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` es la ruta completa del archivo de destino. Separa varias extensiones con `;` o `,`, por ejemplo `png;jpg`; una lista de extensiones vacía permite todos los archivos. Si `overwrite_bool` es `false`, la acción falla en lugar de reemplazar un archivo de destino existente.

El [**listener On File Selected**](./listeners#on-file-selected-file_selected_via_action) se activa cuando el archivo se copia, el selector se cancela o la selección falla. Expone la ruta seleccionada, la ruta de destino resuelta, los estados de éxito/cancelado y un motivo de falla.

## Mostrar aviso emergente (`show_toast`)

**Propósito:** Muestra una notificación emergente configurable

**Valor:** Requerido — Configuración JSON del toast

El editor guarda esta acción como JSON. Prefiere su ventana de configuración en lugar de editar el valor manualmente.

| Campo | Significado |
|---|---|
| `width` | Limitado a `120`–`320` píxeles |
| `durationMs` | Limitado a `1000`–`600000` milisegundos |
| `title` | Texto simple, un componente de texto de Minecraft serializado o vacío |
| `message` | Texto simple, un componente de texto serializado o vacío |
| `iconSource` | [Origen de imagen](./resources) opcional |
| `backgroundSource` | [Origen de imagen](./resources) opcional |

## Iniciar scheduler (`start_scheduler`)

**Propósito:** Inicia un scheduler por su ID de scheduler.

**Valor:** Requerido — `scheduler_id`

Consulta [Schedulers](./schedulers) para crear y administrar IDs de scheduler.

## Detener scheduler (`stop_scheduler`)

**Propósito:** Detiene un scheduler por su ID de scheduler.

**Valor:** Requerido — `scheduler_id`

## Establecer opción de Minecraft (`edit_minecraft_option`)

**Propósito:** Edita una opción de configuración de Minecraft

**Valor:** Requerido — `option_name:set_to_value`
