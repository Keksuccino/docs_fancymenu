---
title: Scripts de acciones
description: 'Cómo usar scripts de acciones con botones, deslizadores, tickers y más.'
---
# Scripts de acciones

Los scripts de acciones ejecutan tareas configuradas cuando se hace clic en un [Botón](./elements#button), se actualiza un [Ticker](./elements#ticker), cambia un [Deslizador](./elements#slider), se abre o cierra una pantalla, o cuando ocurre otro evento compatible. Instrucciones como **if**, **else-if**, **else** y **while** añaden control condicional.

> [!CAUTION]
> Los scripts de acciones importados pueden modificar archivos, conectarse a servidores, abrir enlaces o ejecutar comandos. Usa solo fuentes de confianza.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Editor de scripts de acciones" style="max-width:800px;width:100%;height:auto;">

# ¿Qué son las acciones?

Una **acción** es una tarea o trabajo que FancyMenu ejecuta cuando se activa. Por ejemplo, una acción puede abrir una nueva pantalla, enviar un mensaje al chat o ajustar el volumen de un [elemento de audio](./elements#audio). En el editor de FancyMenu, las acciones se configuran con un valor (si es necesario) que aporta detalles adicionales, como una URL o la dirección de un servidor.

# ¿Qué son las instrucciones?

Para crear comportamientos más complejos, FancyMenu admite instrucciones básicas de control en los scripts de acciones. Estas incluyen:

- **Instrucción If:** Ejecuta un bloque de acciones solo si se cumplen sus [requisitos](./conditions).
- **Instrucción Else-If:** Comprueba otro conjunto de [requisitos](./conditions) si el anterior *if* o *else-if* no se cumplió.
- **Instrucción Else:** Se ejecuta si no se cumple ninguno de los requisitos anteriores.
- **Instrucción While:** Repite un bloque mientras sus [requisitos](./conditions) sigan siendo verdaderos. Se detiene tras tres segundos para evitar bucles infinitos; no la uses como temporizador.
- **Bloque Delay:** Inicia un temporizador cuando se alcanza por primera vez. Sus acciones se ejecutan la siguiente vez que el script alcanza el bloque después del retraso. Reinicializar la pantalla restablece el temporizador.
- **Bloque Execute Later:** Programa sus acciones automáticamente tras el retraso en milisegundos configurado cada vez que se alcanza el bloque.
- **Comentario:** Añade una nota dentro del script para organizarlo. Los comentarios no ejecutan ninguna acción.

Combinando estas instrucciones con acciones, puedes crear comportamientos dinámicos y condicionales; por ejemplo, comprobar si la salud de un jugador es baja antes de enviar un mensaje de aviso o repetir una actualización hasta que cambie una condición.

Las acciones se ejecutan de arriba abajo. Si una acción falla, se registra y el script continúa.

Las descargas, la extracción de ZIP y las solicitudes HTTP finalizan más tarde; la siguiente acción no espera. Usa [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action) o una variable de respuesta HTTP cuando el trabajo posterior dependa del resultado.

# ¿Dónde puedes usar scripts de acciones?

Los scripts de acciones son versátiles y pueden usarse en todo tu diseño. Puedes asignarlos, por ejemplo, a:

- [**Botones**](./elements#button): Ejecutan una acción cuando se hace clic en el botón.
- [**Tickers**](./elements#ticker): Ejecutan continuamente un script de acciones para actualizar la información en pantalla dentro de un diseño.
- [**Deslizadores**](./elements#slider): Activan un script de acciones cada vez que cambia el valor del deslizador.
- **Eventos de pantalla:** Ejecutan scripts cuando una pantalla se abre o se cierra (por ejemplo, reproduciendo un sonido cuando aparece un menú).
- [**Listeners**](./listeners): Cuando un listener recibe su evento configurado, ejecuta su script de acciones.
- [**Schedulers**](./schedulers): Ejecutan acciones de forma programada, incluso cuando no hay ninguna pantalla abierta.

# Uso de placeholders en las acciones

Los valores de las acciones admiten contenido dinámico mediante **placeholders**. La mayoría de las veces, estos placeholders usan una sintaxis similar a JSON y se reemplazan por datos en tiempo real cuando se ejecuta la acción.

## Placeholders tipo JSON

Estos son los [placeholders](./placeholders) normales que pueden usarse en muchos lugares del diseño.

Siguen esta sintaxis:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Pueden obtener datos del juego, como el nombre del jugador, las dimensiones de la pantalla o valores calculados usando el [placeholder **Calculator**](./placeholders#calculator-calc). También puedes anidar placeholders para usos más avanzados.

## Placeholders `$$` (variables)

Los valores `$$` son valores de solo lectura proporcionados a un script de acciones específico por la función que lo ejecuta.

Por ejemplo, un [Deslizador](./elements#slider) proporciona su valor actual como `$$value`.

Cada [listener](./listeners) documenta los valores `$$` que proporciona, como un botón del ratón pulsado o una estructura introducida.

Los nombres `$$` distinguen entre mayúsculas y minúsculas y solo funcionan en el script que los proporciona. Consulta [Listeners](./listeners#listener-variables).

## Delimitadores de valores de acción

Usa el delimitador exacto que se muestra para cada acción: `:`, `||` o `|||`. No existe sintaxis de escape para delimitadores dentro de un campo.

Los placeholders se sustituyen antes de dividir el valor. Para `set_variable`, solo el primer dos puntos separa el nombre del valor, por lo que los demás dos puntos siguen formando parte del valor.

# Cómo configurar y editar acciones

Para editar las acciones y bloques de instrucciones de un elemento, **haz clic derecho en el elemento** y selecciona **Manage Action Script**. En el editor, puedes:

- **Añadir nuevas acciones o instrucciones:** Inserta nuevas entradas de acción o instrucciones de control (if, else-if, else, while) para construir tu script.
- **Editar acciones o instrucciones existentes:** Modifica el valor de la acción o cambia la lógica de control.
- **Eliminar acciones o instrucciones:** Borra del script las acciones que no quieras.

Crea y edita scripts de listeners mediante [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Atajos del editor de scripts de acciones

## Atajos

- `DEL` : Borra rápidamente la entrada seleccionada
- `ENTER` : Inicia la edición en línea de la entrada seleccionada (o abre la pantalla de edición si esa entrada no admite edición en línea)
- `CTRL + C` : Copia la acción seleccionada (por ahora solo funciona con acciones)
- `CTRL + V` : Pega la acción copiada previamente
- `CTRL + Z` : Un paso atrás (deshacer)
- `CTRL + Y` : Un paso adelante (rehacer)
- `ARROW UP` : Navega una entrada hacia arriba desde la seleccionada actualmente
- `ARROW DOWN` : Navega una entrada hacia abajo desde la seleccionada actualmente
- `SHIFT + ARROW UP` : Mueve la entrada seleccionada una posición arriba
- `SHIFT + ARROW DOWN` : Mueve la entrada seleccionada una posición abajo
- `A` : Abre rápidamente la pantalla Action Chooser para añadir una nueva acción
- `CTRL + S` : Finalizar/guardar desde la ventana del editor

## Edición

- Hacer doble clic en el valor de una acción te permite editar el valor sin entrar en la pantalla completa de edición del valor.
- Las cadenas de instrucciones IF (con instrucciones ELSE/ELSE-IF añadidas), los bucles WHILE y las carpetas pueden plegarse (solo visualmente, no afecta a la lógica del script).
- El editor siempre añade nuevas acciones debajo de la entrada seleccionada (o anidadas en la cadena/bucle/carpeta seleccionados).
- Hacer clic derecho en el fondo gris oscuro del área del script abre un menú contextual con opciones para añadir acciones, instrucciones y todo lo demás importante.

# Acciones en detalle

Esta sección enumera las acciones integradas de FancyMenu.

## Siguiente pista (`audio_next_track`)
- **Descripción:** Va a la siguiente pista en un [elemento de audio](./elements#audio)
- **Valor requerido:** Sí - `audio_element_identifier` (el ID del elemento de audio que controlar)

## Pista anterior (`audio_previous_track`)
- **Descripción:** Va a la pista anterior en un [elemento de audio](./elements#audio)
- **Valor requerido:** Sí - `audio_element_identifier` (el ID del elemento de audio que controlar)

## Establecer volumen de la pista (`set_audio_element_volume`)
- **Descripción:** Establece el volumen de un [elemento de audio](./elements#audio) (`0.0` a `1.0`)
- **Valor requerido:** Sí - `element_identifier:volume`

## Alternar reproducir/pausar pista (`audio_toggle_play`)
- **Descripción:** Alterna la pista actual de un [elemento de audio](./elements#audio) entre reproducida y pausada
- **Valor requerido:** Sí - `audio_element_identifier`

## Reproducir audio (`play_audio`)
- **Descripción:** Reproduce un recurso de audio una vez. El audio iniciado por esta acción puede detenerse más tarde con [**Detener todos los audios de acción**](#stop-all-action-audios-stop_all_action_audios).
- **Valor requerido:** Sí - Configuración JSON con `audioSource`, `soundChannel` y `baseVolume`
- **Valor de ejemplo:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Comportamiento:**

- `baseVolume` se limita a `0.0`–`1.0`.
- Si el canal de sonido es desconocido, se usa el canal Master.
- La acción no puede ejecutarse desde un [Ticker](./elements#ticker) asíncrono; FancyMenu mostrará un error en su lugar.
- FancyMenu espera hasta diez segundos a que el recurso de audio esté listo.
- Las pistas iniciadas correctamente pueden detenerse con [**Detener todos los audios de acción**](#stop-all-action-audios-stop_all_action_audios).

## Detener todos los audios de acción (`stop_all_action_audios`)
- **Descripción:** Detiene todas las pistas de audio iniciadas por la [**acción Reproducir audio**](#play-audio-play_audio). Esto no detiene [elementos de audio](./elements#audio), sonidos de abrir/cerrar menús, sonidos de botones ni otros sistemas de audio.
- **Valor requerido:** No

## Establecer volumen del elemento de vídeo (`set_video_element_volume`)
- **Descripción:** Establece el volumen de un [elemento de vídeo](./video) (`0.0` a `1.0`)
- **Valor requerido:** Sí - `video_element_identifier:volume`

## Establecer tiempo de reproducción del elemento de vídeo (`set_video_element_play_time`)
- **Descripción:** Avanza un [elemento de vídeo](./video) hasta una marca de tiempo en milisegundos
- **Valor requerido:** Sí - `video_element_identifier:timestamp_ms`

## Alternar estado de pausa del elemento de vídeo (`toggle_video_element_pause_state`)
- **Descripción:** Alterna el estado de pausa de un [elemento de vídeo](./video)
- **Valor requerido:** Sí - `video_element_identifier`

## Establecer volumen del fondo de vídeo (`set_video_menu_background_volume`)
- **Descripción:** Establece el volumen de un [fondo de menú de vídeo](./video) (`0.0` a `1.0`)
- **Valor requerido:** Sí - `background_identifier:volume`

> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y pulsa en 'Copy Background Identifier'.
{.is-info}

## Establecer tiempo de reproducción del fondo de vídeo (`set_video_menu_background_play_time`)
- **Descripción:** Avanza un [fondo de menú de vídeo](./video) hasta una marca de tiempo en milisegundos
- **Valor requerido:** Sí - `background_identifier:timestamp_ms`

> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y pulsa en 'Copy Background Identifier'.
{.is-info}

## Alternar estado de pausa del fondo de vídeo (`toggle_video_menu_background_pause_state`)
- **Descripción:** Alterna el estado de pausa de un [fondo de menú de vídeo](./video)
- **Valor requerido:** Sí - `background_identifier`

> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y pulsa en 'Copy Background Identifier'.
{.is-info}

## Alternar diseño (`toggle_layout`)
- **Descripción:** Alterna un diseño (activar/desactivar) por su nombre de archivo sin `.txt`
- **Valor requerido:** Sí - `layout_name`

## Activar diseño (`enable_layout`)
- **Descripción:** Activa y guarda un diseño por su nombre de archivo sin `.txt`
- **Valor requerido:** Sí - `layout_name`

## Desactivar diseño (`disable_layout`)
- **Descripción:** Desactiva y guarda un diseño por su nombre de archivo sin `.txt`
- **Valor requerido:** Sí - `layout_name`

Las tres acciones de diseño guardan el estado en el archivo del diseño y actualizan la pantalla actual de inmediato. Usa el nombre de archivo exacto y sensible a mayúsculas/minúsculas sin `.txt`.

## Abrir pantalla o GUI personalizada (`opengui`)
- **Descripción:** Abre una pantalla por su identificador (vanilla, mod o GUI personalizada)
- **Valor requerido:** Sí - `screen_identifier`

Copia el identificador exacto, sensible a mayúsculas/minúsculas, desde la superposición de depuración [Screen Identifiers](./screen-identifiers).

Algunas pantallas de mods no pueden crearse directamente. Si la apertura falla, usa [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) en un widget que normalmente abra esa pantalla.

## Cerrar pantalla (`closegui`)
- **Descripción:** Cierra la pantalla activa
- **Valor requerido:** No

## Actualizar pantalla (`update_screen`)
- **Descripción:** Reinicializa la pantalla actual
- **Valor requerido:** No

## Volver a la última pantalla (`back_to_last_screen`)
- **Descripción:** Vuelve al padre de una [GUI personalizada](./custom-guis) o a la instancia de pantalla cerrada más reciente
- **Valor requerido:** No

## Unirse a un servidor (`joinserver`)
- **Descripción:** Conecta al jugador a un servidor de Minecraft
- **Valor requerido:** Sí - `server_ip` o `server_ip:port`

Esta acción no puede ejecutarse mientras ya haya un mundo o servidor cargado. Se usa el puerto `25565` cuando no se especifica. Si la dirección no está en la lista de servidores guardados de Minecraft, FancyMenu la añade y la guarda.

## Entrar en un mundo (`loadworld`)
- **Descripción:** Entra en un mundo de Minecraft
- **Valor requerido:** Sí - `world_folder_name`

El valor es el nombre de la carpeta de guardado. La acción no hace nada si ese guardado no existe o ya hay otro mundo/servidor cargado.

## Entrar/unirse al último mundo/servidor (`join_last_world`)
- **Descripción:** Entra o se une al último mundo o servidor en el que estuvo el jugador
- **Valor requerido:** No

Esta acción no puede ejecutarse mientras haya cargado otro mundo/servidor. Un servidor recordado que no esté en la lista de servidores guardados de Minecraft se añade y guarda antes de conectar.

## Salir de un mundo o servidor (`disconnect_server_or_world`)
- **Descripción:** Abandona un mundo o servidor y abre una pantalla especificada
- **Valor requerido:** Sí - `screen_identifier`

Esta acción solo se ejecuta mientras haya cargados un mundo y un jugador. El destino puede ser un identificador de [GUI personalizada](./custom-guis) o un [identificador de pantalla](./screen-identifiers) que FancyMenu pueda construir. Si no se puede abrir el destino, FancyMenu vuelve a la pantalla Title.

## Salir de Minecraft (`quitgame`)
- **Descripción:** Cierra Minecraft por completo
- **Valor requerido:** No

## Enviar mensaje/comando al chat (`sendmessage`)
- **Descripción:** Envía un mensaje de chat o ejecuta un comando de chat
- **Valor requerido:** Sí - `message_text` o `/command_text`

## Ejecutar comando como servidor integrado (`execute_command_as_integrated_server`)
- **Descripción:** Ejecuta forzosamente un comando en un jugador como servidor integrado, ignorando permisos y la configuración de trucos.
- **Valor requerido:** Sí - Texto del comando, por ejemplo `/give @p minecraft:diamond 1`

> Esta acción solo funciona en un jugador mientras el mundo **no esté abierto a LAN**. Intencionadamente no hace nada cuando no existe un servidor integrado o cuando el servidor integrado está publicado en LAN.
{.is-warning}

## Pegar en el chat (`paste_to_chat`)
- **Descripción:** Pega texto en el campo de entrada del chat (añadir o reemplazar)
- **Valor requerido:** Sí - `true:Text` o `false:Text`

## Mostrar en el chat [lado cliente] (`display_in_chat_client_side`)
- **Descripción:** Muestra un mensaje de chat del lado cliente mientras hay un mundo o servidor cargado. No envía nada al servidor.
- **Valor requerido:** Sí - `text_or_json`

## Enviar datos FM al servidor (`send_fm_data_to_server`)
- **Descripción:** Envía [datos FM](./fm-data) al servidor de FancyMenu actual.
- **Valor requerido:** Sí - `data_identifier||data`

## Conectar a un servidor remoto (`connect_to_remote_server`)
- **Descripción:** Abre o reutiliza una conexión WebSocket iniciada por el cliente con un servidor remoto externo.
- **Valor requerido:** Sí - URL del servidor remoto, por ejemplo `wss://example.com/ws`

Consulta [Comunicación con servidor remoto](./remote-server-communication#url-modes) para ver los formatos de URL admitidos.

## Enviar datos a un servidor remoto (`send_data_to_remote_server`)
- **Descripción:** Abre o reutiliza una conexión con un servidor remoto y le envía datos de texto.
- **Valor requerido:** Sí - `remote_server_url||data`

## Cerrar conexión con servidor remoto (`close_remote_server_connection`)
- **Descripción:** Cierra una conexión específica con un servidor remoto mediante el ID de solicitud.
- **Valor requerido:** Sí - ID de solicitud, normalmente `$$request_id` de un [listener de servidor remoto](./listeners#on-remote-server-connected)

## Cerrar todas las conexiones con servidores remotos (`close_all_remote_server_connections`)
- **Descripción:** Cierra todas las conexiones activas con servidores remotos abiertas por FancyMenu.
- **Valor requerido:** No

## Abrir URL en el navegador (`openlink`)
- **Descripción:** Pasa una URL al gestor predeterminado del sistema operativo sin un mensaje de confirmación de FancyMenu
- **Valor requerido:** Sí - `https://example.com`

Usa enlaces `https://` de confianza. FancyMenu no muestra un aviso de confirmación antes de pasar la URL al sistema operativo.

## Copiar texto al portapapeles (`copytoclipboard`)
- **Descripción:** Copia texto al portapapeles
- **Valor requerido:** Sí - `text_to_copy`

## Imprimir en el registro del juego (`print_to_log`)
- **Descripción:** Escribe una línea en el registro del juego
- **Valor requerido:** Sí - `text_to_log`

## Establecer valor de variable (variable FM) (`set_variable`)
- **Descripción:** Almacena contenido de texto en una [variable de FancyMenu](./variables)
- **Valor requerido:** Sí - `variable_name:variable_value`

Los primeros dos puntos separan el nombre del valor. Los demás dos puntos siguen formando parte del valor. Los cambios se guardan de inmediato.

## Limpiar todas las variables (variable FM) (`clear_variables`)
- **Descripción:** Borra todos los valores almacenados de [variables de FancyMenu](./variables)
- **Valor requerido:** No

## Enviar solicitud HTTP (`send_http_request`)
- **Descripción:** Inicia una solicitud HTTP/HTTPS en segundo plano; puede registrar y/o guardar la respuesta en una variable
- **Valor requerido:** Sí - Configuración de la solicitud HTTP

| Configuración | Comportamiento |
|---|---|
| URL | Endpoint HTTP o HTTPS |
| Método | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` u `OPTIONS` |
| Cuerpo | Se envía para métodos distintos de `GET` y `HEAD` |
| Tipo de contenido | Valor `Content-Type` de la solicitud |
| Tiempo de espera | Segundos usados tanto para la conexión como para la lectura de la respuesta |
| Registrar respuesta | Lee y escribe la respuesta en el registro |
| Variable de respuesta | Lee la respuesta y la guarda al completar la solicitud |
| Respuesta de una sola línea | Elimina los saltos de línea de la respuesta antes de guardarla |
| Autenticación | Ninguna, Basic, Bearer o clave API |
| Encabezados | Encabezados personalizados opcionales de la solicitud |

Las solicitudes se ejecutan de forma asíncrona, por lo que la siguiente acción no espera. Los cuerpos de respuesta solo se leen cuando el registro está activado o se configura una variable de respuesta; los cuerpos que no son de éxito se leen de la respuesta de error. No almacenes contraseñas ni tokens de acceso en la configuración de la acción.

## Gestionar paquete de recursos (`manage_resource_pack`)
- **Descripción:** Activa, desactiva o alterna un paquete de recursos, con una recarga opcional
- **Valor requerido:** Sí - `pack_name_or_id|||MODE|||reload_bool`

Los nombres visibles y los ID internos del paquete se comparan sin distinguir mayúsculas/minúsculas. Los paquetes marcados como obligatorios no pueden desactivarse.

## Recargar paquetes de recursos (`reload_resource_packs`)
- **Descripción:** Recarga los paquetes de recursos de Minecraft. Un tiempo de espera interno de cinco segundos ignora los activadores repetidos durante ese periodo para evitar spam de recargas.
- **Valor requerido:** No

## Recargar FancyMenu (`reloadmenu`)
- **Descripción:** Recarga diseños, [GUIs personalizadas](./custom-guis), [panoramas](./panoramas), [diapositivas](./slideshows), ajustes y recursos gestionados por FancyMenu
- **Valor requerido:** No

Esto no recarga los paquetes de recursos de Minecraft. Usa [**Recargar paquetes de recursos**](#reload-resource-packs-reload_resource_packs) para eso.

> Recargar es costoso. Actívalo desde la acción deliberada de un botón, no desde un [Ticker](./elements#ticker) ni desde un [listener](./listeners) que se dispare con frecuencia.
{.is-warning}

## Alternar Animator de elemento (`toggle_element_animator`)
- **Descripción:** Alterna el estado de reproducción guardado y restablece la línea de tiempo activa del Animator correspondiente
- **Valor requerido:** Sí - `animator_identifier`

Consulta [Element Animator](./element-animator) para la configuración y los detalles del identificador.

## Activar Animator de elemento (`enable_element_animator`)
- **Descripción:** Activa la reproducción; una línea de tiempo activa del Animator solo se restablece cuando el estado cambia de desactivado a activado
- **Valor requerido:** Sí - `animator_identifier`

## Desactivar Animator de elemento (`disable_element_animator`)
- **Descripción:** Desactiva la reproducción y restablece la línea de tiempo activa del Animator correspondiente
- **Valor requerido:** Sí - `animator_identifier`

## Reiniciar Animator de elemento (`reset_element_animator`)
- **Descripción:** Restablece la línea de tiempo activa del Animator correspondiente sin cambiar si la reproducción está activada
- **Valor requerido:** Sí - `animator_identifier`

## Emular botón de Vanilla/Mod (`mimicbutton`)
- **Descripción:** Emula la acción de clic de un botón de vanilla o de mod
- **Valor requerido:** Sí - [`screen_identifier`](./screen-identifiers):[`widget_locator`](./widget-locators)

## Emular tecla asignada (`mimic_keybind`)
- **Descripción:** Ejecuta una tecla asignada de Minecraft (mantener opcionalmente)
- **Valor requerido:** Sí - `keybind_id|||keep_pressed_bool|||duration_ms`

## Establecer valor de un campo de entrada de texto (`set_text_input_field_value`)
- **Descripción:** Establece el valor de un [Campo de entrada de texto](./elements#text-input-field) personalizado o de Vanilla mediante el identificador del elemento.
- **Valor requerido:** Sí - `element_identifier|||new_value|||force_set_when_inactive`

Los tres campos deben separarse con el delimitador de triple barra `|||`. Establece `force_set_when_inactive` en `true` para actualizar también un campo de entrada deshabilitado; cuando es `false`, los campos inactivos no se modifican.

## Crear archivo en el directorio del juego (`create_file_in_game_dir`)
- **Descripción:** Crea un archivo vacío relativo al directorio de juego activo. Acepta el prefijo `.minecraft/` para apuntar al directorio convencional de Minecraft (que puede diferir de la instancia actual).
- **Valor requerido:** Sí - `file_path`

Ejemplo: `config/some_mod_folder/new_file.txt`. Se crean los directorios padre que falten; si el archivo ya existe, no se modifica.

## Eliminar archivo/carpeta en el directorio del juego (`delete_file_in_game_dir`)
- **Descripción:** Elimina un archivo o borra recursivamente una carpeta relativa al directorio de juego activo. Acepta `.minecraft/` para apuntar al directorio convencional de Minecraft. Añade `*` para eliminar **solo todos los archivos directamente dentro** de una carpeta (ignora los subdirectorios y conserva la carpeta).
- **Valor requerido:** Sí - `target_path`

Por ejemplo, `config/downloads/*` elimina los archivos directamente dentro de `config/downloads/`, pero no recorre ni elimina sus subdirectorios.

## Copiar archivo/carpeta en el directorio del juego (`copy_file_in_game_dir`)
- **Descripción:** Copia dentro del directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft. Un directorio con nombre se copia de forma recursiva. Añade `*` a la ruta de **origen** para copiar solo cada archivo hijo directo; el destino debe ser un directorio y no puede usar `*`.
- **Valor requerido:** Sí - `source||destination`

Por ejemplo, `config/source/*||config/destination/` copia solo los archivos directamente dentro de `config/source/`. Con un origen con comodín, FancyMenu crea el directorio de destino cuando es necesario, pero no copia ningún subdirectorio del origen. La copia rechaza cualquier destino existente o archivo en conflicto en lugar de sobrescribirlo.

## Mover archivo/carpeta en el directorio del juego (`move_file_in_game_dir`)
- **Descripción:** Mueve dentro del directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft. Añade `*` a la ruta de **origen** para mover solo cada archivo hijo directo; el destino debe ser un directorio y no puede usar `*`.
- **Valor requerido:** Sí - `source||destination`

Por ejemplo, `config/source/*||config/destination/` mueve solo los archivos directamente dentro de `config/source/`. Con un origen con comodín, FancyMenu crea el directorio de destino cuando es necesario, pero deja los subdirectorios del origen en su sitio. El movimiento rechaza un destino existente o un archivo en conflicto en lugar de sobrescribirlo.

## Cambiar nombre de archivo/carpeta en el directorio del juego (`rename_file_in_game_dir`)
- **Descripción:** Cambia el nombre de un archivo o carpeta dentro de su directorio padre actual; `.minecraft/` apunta al directorio convencional de Minecraft. Conserva intacto el contenido y rechaza un nombre de destino existente.
- **Valor requerido:** Sí - `path||new_name`

## Descargar archivo al directorio del juego (`download_file_to_game_dir`)
- **Descripción:** Descarga un archivo en segundo plano a un directorio relativo al directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft.
- **Valor requerido:** Sí - `url||target_folder`

El segundo campo es un **directorio de destino**, no una ruta completa de archivo de destino. FancyMenu crea el directorio cuando es necesario y determina el nombre de archivo a partir del encabezado `Content-Disposition` de la respuesta; si no, recurre a la ruta de la URL. El nombre resultante se decodifica desde URL y se sanea antes de usarse; si ninguna de las fuentes proporciona un nombre utilizable, FancyMenu genera uno. Si ya existe un archivo con el mismo nombre, se sobrescribe.

El [**listener On File Downloaded via Action**](./listeners#on-file-downloaded-via-action) se activa tanto tras intentos de descarga exitosos como fallidos, y expone la URL, la ruta de destino resuelta y el estado de éxito.

Si la descarga tiene éxito, `$$target_file_path` es la ruta del archivo guardado. Si falla, puede contener solo el directorio de destino porque no se resolvió un nombre final de archivo.

## Extraer archivo ZIP en el directorio del juego (`extract_zip_file_in_game_dir`)
- **Descripción:** Extrae un ZIP en una carpeta de destino dentro del directorio de juego activo o del directorio convencional `.minecraft`. Activa [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action) al finalizar.
- **Valor requerido:** Sí - `source_zip_path||target_folder_path`

Los archivos existentes con nombres coincidentes se reemplazan. Extrae solo archivos ZIP de confianza.

## Abrir archivo/carpeta en el directorio del juego (`open_file_folder_in_game_dir`)
- **Descripción:** Abre un archivo o carpeta con la aplicación predeterminada del sistema operativo. El destino debe permanecer dentro del directorio del juego o del directorio predeterminado `.minecraft` por razones de seguridad.
- **Valor requerido:** Sí - `target_path`

## Escribir archivo en el directorio del juego (`write_file_in_game_dir`)
- **Descripción:** Escribe o añade texto relativo al directorio de juego activo; `.minecraft/` apunta al directorio convencional de Minecraft. Crea el archivo y sus padres si no existen. `\n` inserta saltos de línea; `append_bool=false` reemplaza un archivo existente.
- **Valor requerido:** Sí - `path|||content|||append_bool`

## Seleccionar archivo del sistema (`select_file_to_game_dir`)
- **Descripción:** Abre un selector de archivos nativo y copia el archivo seleccionado dentro del directorio de juego activo, o del `.minecraft/` convencional cuando se usa el prefijo. Admite filtros por extensión, una etiqueta de filtro personalizada y un conmutador de sobrescritura.
- **Valor requerido:** Sí - `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` es la ruta completa del archivo de destino. Separa varias extensiones con `;` o `,`, por ejemplo `png;jpg`; una lista de extensiones vacía permite todos los archivos. Si `overwrite_bool` es `false`, la acción falla en lugar de reemplazar un archivo de destino existente.

El [**listener On File Selected**](./listeners#on-file-selected) se activa cuando el archivo se copia, se cancela el selector o la selección falla. Expone la ruta seleccionada, la ruta de destino resuelta, los estados de éxito/cancelado y un motivo del fallo.

## Mostrar aviso emergente (`show_toast`)
- **Descripción:** Muestra una notificación toast configurable
- **Valor requerido:** Sí - configuración del toast

| Campo | Significado |
|---|---|
| Anchura | Limitada a `120`–`320` píxeles |
| Duración | Limitada a `1000`–`600000` milisegundos |
| Título | Texto sin formato o un componente de texto de Minecraft serializado |
| Mensaje | Texto sin formato opcional o componente de texto serializado |
| Icono | [Origen de imagen](./resources) opcional |
| Fondo | [Origen de imagen](./resources) opcional |

## Iniciar scheduler (`start_scheduler`)
- **Descripción:** Inicia un scheduler por su ID de scheduler.
- **Valor requerido:** Sí - `scheduler_id`

Consulta [Schedulers](./schedulers) para crear y gestionar IDs de scheduler.

## Detener scheduler (`stop_scheduler`)
- **Descripción:** Detiene un scheduler por su ID de scheduler.
- **Valor requerido:** Sí - `scheduler_id`

## Establecer opción de Minecraft (`edit_minecraft_option`)
- **Descripción:** Edita una opción de configuración de Minecraft
- **Valor requerido:** Sí - `option_name:set_to_value`
