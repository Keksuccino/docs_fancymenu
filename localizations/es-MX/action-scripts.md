---
title: Scripts de Acción
description: 'Cómo usar scripts de acción con botones, sliders, tickers y más.'
---

# Scripts de Acción

FancyMenu te permite agregar interactividad a tus menús asignando **acciones** a los elementos. Estas acciones se ejecutan cuando se hace clic en un botón, cuando un ticker está actualizándose, cuando se usa un slider o cuando una pantalla se abre o se cierra. También puedes crear scripts de acción avanzados usando instrucciones de control simples, como **if**, **else-if**, **else** y **while**, para controlar qué acciones se ejecutan y cuándo.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Editor de scripts de acción" style="max-width:800px;width:100%;height:auto;">

# ¿Qué son las acciones?

Una **acción** es una tarea o trabajo que FancyMenu ejecuta cuando se activa. Por ejemplo, una acción puede abrir una nueva pantalla, enviar un mensaje al chat o ajustar el volumen de un elemento de audio. En el editor de FancyMenu, las acciones se configuran con un valor (si se necesita) que proporciona detalles extra, como una URL o una dirección de servidor.

# ¿Qué son las instrucciones?

Para crear comportamientos más complejos, FancyMenu admite instrucciones de control básicas en los scripts de acción. Estas incluyen:

- **Instrucción If:** Ejecuta un bloque de acciones solo si se cumple una [condición](/en/conditions) específica.
- **Instrucción Else-If:** Verifica otra [condición](/en/conditions) si el *if* anterior (o un *else-if* previo) no se cumplió.
- **Instrucción Else:** Se ejecuta si ninguna de las [condiciones](/en/conditions) anteriores se cumple.
- **Instrucción While:** Repite un bloque de acciones continuamente mientras una [condición](/en/conditions) siga siendo verdadera (con un tiempo de espera integrado para evitar ciclos infinitos).
- **Bloque Delay:** Espera el tiempo especificado antes de ejecutar las acciones que contiene. El resto del script sigue ejecutándose mientras corre el temporizador.
- **Bloque Execute Later:** Encola las acciones contenidas para ejecutarlas en el hilo principal después de una demora en milisegundos.
- **Comentario:** Agrega una nota dentro del script para organizarlo. Los comentarios no ejecutan ninguna acción.

Al combinar estas instrucciones con acciones, puedes crear comportamientos dinámicos y condicionales; por ejemplo, verificar si la salud de un jugador está baja antes de enviar un mensaje de advertencia o repetir una actualización hasta que cambie una condición.

# ¿Dónde puedes usar scripts de acción?

Los scripts de acción son versátiles y se pueden usar en todo tu diseño. Puedes asignarlos, por ejemplo, a:

- **Botones:** Ejecutan una acción cuando se hace clic en el botón.
- **Tickers:** Ejecutan continuamente un script de acción para actualizar información en pantalla dentro de un diseño.
- **Sliders:** Activan un script de acción cada vez que cambia el valor del slider.
- **Eventos de pantalla:** Ejecutan scripts cuando una pantalla se abre o se cierra (por ejemplo, reproducir un sonido cuando aparece un menú).
- **Listeners:** Cuando se dispara un listener que escucha un evento específico, ejecutará su script de acción.
- **Schedulers:** Ejecutan acciones en intervalos programados, incluso cuando no hay ninguna pantalla abierta.

# Uso de placeholders en acciones

Los valores de las acciones admiten contenido dinámico mediante **placeholders**. La mayoría de las veces, estos placeholders usan una sintaxis parecida a JSON y se reemplazan con datos en vivo cuando se ejecuta la acción.

## Placeholders tipo JSON

Estos son los [placeholders](/en/placeholders) normales que se pueden usar en muchos lugares dentro de los diseños.

Siguen esta sintaxis:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Pueden obtener datos del juego, como el nombre del jugador, las dimensiones de la pantalla o valores calculados usando el placeholder **Calculator**. También puedes anidar placeholders para usos más avanzados.

## Placeholders `$$` (Variables)

Los placeholders `$$` son especiales. Algunas funciones de FancyMenu proporcionarán estos placeholders especiales para sus acciones anidadas, requisitos y placeholders normales, de modo que se puedan usar dentro para obtener más información sobre el entorno (elemento, listener, etc.) en el que se encuentran.

Por ejemplo, si las acciones se usan dentro de un slider, usar `$$value` en la acción se reemplazará con el valor actual del slider.

Cuando se usan acciones en listeners, cada listener proporcionará su propio conjunto único de variables/placeholders para obtener más información sobre el listener, como el botón del mouse presionado, la estructura ingresada, etc.

# Cómo configurar y editar acciones

Para agregar, editar o quitar acciones (y bloques de instrucciones) de un elemento, simplemente **haz clic derecho sobre el elemento** (ya sea un botón, slider, ticker u otro elemento interactivo) y luego selecciona **Administrar script de acción**. Esto abre la pantalla de Administración de acciones, donde puedes:

- **Agregar acciones o instrucciones nuevas:** Inserta nuevas entradas de acción o instrucciones de control (if, else-if, else, while) para construir tu script.
- **Editar acciones o instrucciones existentes:** Modifica el valor de la acción o cambia la lógica de control.
- **Eliminar acciones o instrucciones:** Borra del script las acciones que no quieras.

Para los [listeners](/listeners) hay un menú especial para administrar y crear listeners, incluyendo el acceso a sus scripts de acción para tener la misma experiencia que al editar, por ejemplo, el script de acción de un botón o slider.

> Cuando estés en la pantalla del Editor de scripts de acción, solo haz clic derecho en el área grande de color gris oscuro para abrir un menú contextual y agregar acciones, instrucciones y más.
{.is-info}


# Atajos y más del Editor de scripts de acción

El editor de scripts de acción tiene varias funciones muy útiles que hacen que editar scripts sea súper fácil.

## Atajos

- `DEL` : Elimina rápidamente la entrada seleccionada
- `ENTER` : Inicia la edición en línea de la entrada seleccionada (o abre la pantalla de edición si no hay edición en línea para la entrada seleccionada)
- `CTRL + C` : Copia la acción seleccionada (por ahora solo funciona con acciones)
- `CTRL + V` : Pega la acción copiada previamente
- `CTRL + Z` : Un paso atrás (deshacer)
- `CTRL + Y` : Un paso adelante (rehacer)
- `ARROW UP` : Navega una entrada hacia arriba desde la seleccionada actualmente
- `ARROW DOWN` : Navega una entrada hacia abajo desde la seleccionada actualmente
- `SHIFT + ARROW UP` : Mueve la entrada seleccionada una posición hacia arriba
- `SHIFT + ARROW DOWN` : Mueve la entrada seleccionada una posición hacia abajo
- `A` : Abre rápidamente la pantalla de Selección de acciones para agregar una nueva acción
- `CTRL + S` : Termina/guarda desde la ventana del editor

## Más funciones útiles

- Hacer doble clic en el valor de una acción te permite editarlo sin entrar a la pantalla completa de edición de valor.
- Las cadenas de instrucciones IF (con instrucciones ELSE/ELSE-IF agregadas), los bucles WHILE y las carpetas se pueden contraer (solo visualmente, no afecta la lógica del script).
- El editor siempre agrega nuevas acciones debajo de la entrada seleccionada (o anidadas dentro de la cadena/bucle/carpeta seleccionada).
- Hacer clic derecho en el fondo gris oscuro del área del script abre un menú contextual con opciones para agregar acciones, instrucciones y todo lo demás importante.

# Acciones en detalle

Esta lista contiene la mayoría, si no es que todas, las acciones disponibles en FancyMenu. Es posible que la lista a veces esté un poco desactualizada debido a actualizaciones del mod.

## Siguiente pista (`audio_next_track`)
- **Descripción:** Va a la siguiente pista en un elemento de audio
- **Valor requerido:** Sí - `audio_element_identifier` (el ID del elemento de audio a controlar)

## Pista anterior (`audio_previous_track`)
- **Descripción:** Va a la pista anterior en un elemento de audio
- **Valor requerido:** Sí - `audio_element_identifier` (el ID del elemento de audio a controlar)

## Establecer volumen de la pista (`set_audio_element_volume`)
- **Descripción:** Establece el volumen de un elemento de audio (0.0 a 1.0)
- **Valor requerido:** Sí - `element_identifier:volume`

## Alternar reproducir/pausa de la pista (`audio_toggle_play`)
- **Descripción:** Alterna el estado de reproducir/pausa de la pista actual de un elemento de audio
- **Valor requerido:** Sí - `audio_element_identifier`

## Reproducir audio (`play_audio`)
- **Descripción:** Reproduce un recurso de audio una sola vez. La acción rastrea el audio que inició para que después pueda detenerse con `stop_all_action_audios`.
- **Valor requerido:** Sí - Configuración JSON con `audioSource`, `soundChannel` y `baseVolume`
- **Ejemplo de valor:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

## Detener todos los audios de acción (`stop_all_action_audios`)
- **Descripción:** Detiene todas las pistas de audio que se iniciaron con la acción **Reproducir audio**. Esto no detiene los elementos de audio, los sonidos al abrir/cerrar menús, los sonidos de botones ni otros sistemas de audio.
- **Valor requerido:** No

## Establecer volumen del elemento de video (`set_video_element_volume`)
- **Descripción:** Establece el volumen de un elemento de video (0.0 a 1.0)
- **Valor requerido:** Sí - `video_element_identifier:volume`

## Establecer tiempo de reproducción del elemento de video (`set_video_element_play_time`)
- **Descripción:** Avanza un elemento de video a una marca de tiempo en milisegundos
- **Valor requerido:** Sí - `video_element_identifier:timestamp_ms`

## Alternar estado de pausa del elemento de video (`toggle_video_element_pause_state`)
- **Descripción:** Alterna el estado de pausa de un elemento de video
- **Valor requerido:** Sí - `video_element_identifier`

## Establecer volumen del fondo de video (`set_video_menu_background_volume`)
- **Descripción:** Establece el volumen de un fondo de menú de video (0.0 a 1.0)
- **Valor requerido:** Sí - `background_identifier:volume`

> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y luego haz clic en 'Copy Background Identifier'.
{.is-info}

## Establecer tiempo de reproducción del fondo de video (`set_video_menu_background_play_time`)
- **Descripción:** Avanza un fondo de menú de video a una marca de tiempo en milisegundos
- **Valor requerido:** Sí - `background_identifier:timestamp_ms`

> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y luego haz clic en 'Copy Background Identifier'.
{.is-info}

## Alternar estado de pausa del fondo de video (`toggle_video_menu_background_pause_state`)
- **Descripción:** Alterna el estado de pausa de un fondo de menú de video
- **Valor requerido:** Sí - `background_identifier`

> Para obtener el identificador de un fondo, haz clic derecho en el fondo del editor y luego haz clic en 'Copy Background Identifier'.
{.is-info}

## Alternar diseño (`toggle_layout`)
- **Descripción:** Alterna un diseño (activar/desactivar) por su nombre
- **Valor requerido:** Sí - `layout_name`

## Activar diseño (`enable_layout`)
- **Descripción:** Activa un diseño por su nombre
- **Valor requerido:** Sí - `layout_name`

## Desactivar diseño (`disable_layout`)
- **Descripción:** Desactiva un diseño por su nombre
- **Valor requerido:** Sí - `layout_name`

## Abrir pantalla o GUI personalizada (`opengui`)
- **Descripción:** Abre una pantalla por su identificador (vanilla, mod o GUI personalizada)
- **Valor requerido:** Sí - `screen_identifier`

> Esta acción **no funcionará en todas las pantallas**, especialmente en las pantallas de mods. Si la acción no logra abrir una pantalla, mostrará un error. En ese caso no hay mucho que puedas hacer, porque probablemente sea una pantalla demasiado compleja para que FancyMenu la abra automáticamente.
> 
> La compatibilidad con pantallas de mods tampoco se agregará manualmente por parte de FancyMenu, porque agregar compatibilidad para todos los mods existentes tomaría muchísimo tiempo, lo sentimos. En la mayoría de los casos tampoco se recomienda contactar al desarrollador del otro mod, porque si FancyMenu no puede abrir la pantalla, no hay una forma sencilla de agregar compatibilidad. La solución recomendada aquí es intentar usar la acción **"Mimic Vanilla/Mod Button"** para imitar un botón que abra esa pantalla específica. Si no hay un botón, entonces no hay mucho que se pueda hacer, lo sentimos.
{.is-info}

## Cerrar pantalla (`closegui`)
- **Descripción:** Cierra la pantalla activa
- **Valor requerido:** No

## Actualizar pantalla (`update_screen`)
- **Descripción:** Reinicializa la pantalla actual
- **Valor requerido:** No

## Volver a la última pantalla (`back_to_last_screen`)
- **Descripción:** Vuelve a la pantalla anterior (la que estaba antes de la actual)
- **Valor requerido:** No

## Unirse al servidor (`joinserver`)
- **Descripción:** Conecta al jugador a un servidor de Minecraft
- **Valor requerido:** Sí - `server_ip:port`

## Entrar al mundo (`loadworld`)
- **Descripción:** Entra a un mundo de Minecraft
- **Valor requerido:** Sí - `world_folder_name`

## Entrar/unirse al último mundo/servidor (`join_last_world`)
- **Descripción:** Entra o se une al último mundo o servidor en el que estuvo el jugador
- **Valor requerido:** No

## Salir del mundo o servidor (`disconnect_server_or_world`)
- **Descripción:** Sale de un mundo o servidor y abre una pantalla especificada
- **Valor requerido:** Sí - `screen_identifier`

## Salir de Minecraft (`quitgame`)
- **Descripción:** Cierra Minecraft por completo
- **Valor requerido:** No

## Enviar mensaje/comando al chat (`sendmessage`)
- **Descripción:** Envía un mensaje al chat o ejecuta un comando de chat
- **Valor requerido:** Sí - `message_text` o `/command_text`

## Ejecutar comando como servidor integrado (`execute_command_as_integrated_server`)
- **Descripción:** Ejecuta forzosamente un comando en un jugador en el servidor integrado, ignorando permisos y la configuración de trucos.
- **Valor requerido:** Sí - Texto del comando, por ejemplo `/give @p minecraft:diamond 1`

> Esta acción solo funciona en un jugador mientras el mundo no esté abierto a LAN. Intencionalmente no hace nada en servidores multijugador.
{.is-warning}

## Pegar en el chat (`paste_to_chat`)
- **Descripción:** Pega texto en el campo de entrada del chat (agregar o reemplazar)
- **Valor requerido:** Sí - `true:Text` o `false:Text`

## Mostrar en el chat [del cliente] (`display_in_chat_client_side`)
- **Descripción:** Imprime texto directamente en el chat local (sin servidor)
- **Valor requerido:** Sí - `text_or_json`

## Enviar datos FM al servidor (`send_fm_data_to_server`)
- **Descripción:** Envía datos de texto personalizados al servidor actual de FancyMenu a través del canal de paquetes FM Data.
- **Valor requerido:** Sí - `data_identifier||data`

## Conectar a servidor remoto (`connect_to_remote_server`)
- **Descripción:** Abre o reutiliza una conexión WebSocket iniciada por el cliente con un servidor remoto externo.
- **Valor requerido:** Sí - URL del servidor remoto, por ejemplo `wss://example.com/ws`

## Enviar datos al servidor remoto (`send_data_to_remote_server`)
- **Descripción:** Abre o reutiliza una conexión con un servidor remoto y le envía datos de texto.
- **Valor requerido:** Sí - `remote_server_url||data`

## Cerrar conexión del servidor remoto (`close_remote_server_connection`)
- **Descripción:** Cierra una conexión específica con un servidor remoto mediante el ID de solicitud.
- **Valor requerido:** Sí - ID de solicitud, normalmente de una variable de listener de servidor remoto como `$$request_id`

## Cerrar todas las conexiones del servidor remoto (`close_all_remote_server_connections`)
- **Descripción:** Cierra todas las conexiones activas con servidores remotos abiertas por FancyMenu.
- **Valor requerido:** No

## Abrir URL en el navegador (`openlink`)
- **Descripción:** Abre un enlace en tu navegador predeterminado
- **Valor requerido:** Sí - `https://example.com`

## Copiar texto al portapapeles (`copytoclipboard`)
- **Descripción:** Copia texto al portapapeles
- **Valor requerido:** Sí - `text_to_copy`

## Imprimir en el log del juego (`print_to_log`)
- **Descripción:** Escribe una línea en el registro del juego
- **Valor requerido:** Sí - `text_to_log`

## Establecer valor de variable (variable de FM) (`set_variable`)
- **Descripción:** Guarda contenido de texto en una variable de FancyMenu
- **Valor requerido:** Sí - `variable_name:variable_value`

## Borrar todas las variables (variable de FM) (`clear_variables`)
- **Descripción:** Borra TODAS las variables almacenadas de FancyMenu
- **Valor requerido:** No

## Enviar solicitud HTTP (`send_http_request`)
- **Descripción:** Envía una solicitud HTTP; puede guardar la respuesta en una variable
- **Valor requerido:** Sí - Configuración de la solicitud HTTP

> Esta acción te permite enviar datos a APIs REST, webhooks o cualquier endpoint HTTP.
> Admite varios métodos de autenticación, encabezados personalizados y distintos tipos de solicitud.
> 
> ¡Esta acción también te permite guardar la respuesta de la solicitud en una variable de FancyMenu para usarla más adelante!
{.is-info}

## Administrar paquete de recursos (`manage_resource_pack`)
- **Descripción:** Activa/desactiva/alternar un paquete de recursos por su nombre visible (recarga opcional)
- **Valor requerido:** Sí - `pack_name|||MODE|||reload_bool`

## Recargar paquetes de recursos (`reload_resource_packs`)
- **Descripción:** Recarga los paquetes de recursos (enfriamiento de 5 s)
- **Valor requerido:** No

## Recargar FancyMenu (`reloadmenu`)
- **Descripción:** Recarga FancyMenu, incluidas panorámicas, presentaciones y todos los recursos (pesado)
- **Valor requerido:** No

> Esta acción tiene un **gran impacto en el rendimiento** y puede causar lag si se usa en Tickers. No se recomienda usar esta acción en nada que no sea un botón.
{.is-warning}

## Alternar animador de elemento (`toggle_element_animator`)
- **Descripción:** Alterna el estado de reproducción de un animador de elemento
- **Valor requerido:** Sí - `animator_identifier`

## Activar animador de elemento (`enable_element_animator`)
- **Descripción:** Activa un animador de elemento
- **Valor requerido:** Sí - `animator_identifier`

## Desactivar animador de elemento (`disable_element_animator`)
- **Descripción:** Desactiva un animador de elemento
- **Valor requerido:** Sí - `animator_identifier`

## Reiniciar animador de elemento (`reset_element_animator`)
- **Descripción:** Reinicia la línea de tiempo/estado de un animador de elemento
- **Valor requerido:** Sí - `animator_identifier`

## Imitar botón de vanilla/mod (`mimicbutton`)
- **Descripción:** Imita la acción de clic de un botón de vanilla o de mod
- **Valor requerido:** Sí - `screen_identifier:widget_locator`

## Imitar tecla (`mimic_keybind`)
- **Descripción:** Ejecuta una tecla de Minecraft (mantener presionado opcional)
- **Valor requerido:** Sí - `keybind_id|||keep_pressed_bool|||duration_ms`

## Establecer valor de campo de texto (`set_text_input_field_value`)
- **Descripción:** Establece el valor de un campo de entrada personalizado o de vanilla por identificador de elemento.
- **Valor requerido:** Sí - `element_identifier|||new_value|||force_set_when_inactive`

## Crear archivo en el directorio del juego (`create_file_in_game_dir`)
- **Descripción:** Crea un archivo vacío en el directorio del juego (raíz de la instancia). Acepta el prefijo `.minecraft/` para apuntar al directorio predeterminado del perfil del launcher (puede ser diferente del directorio de la instancia actual).
- **Valor requerido:** Sí - `file_path`

## Eliminar archivo/carpeta en el directorio del juego (`delete_file_in_game_dir`)
- **Descripción:** Elimina un archivo o carpeta en el directorio del juego (raíz de la instancia). Acepta el prefijo `.minecraft/` para apuntar al perfil predeterminado del launcher (puede diferir de la instancia en ejecución). Agrega `*` para eliminar **todos los archivos directamente dentro** de una carpeta (ignora subdirectorios; conserva la carpeta).
- **Valor requerido:** Sí - `target_path`

## Copiar archivo/carpeta en el directorio del juego (`copy_file_in_game_dir`)
- **Descripción:** Copia dentro del directorio del juego (raíz de la instancia); el prefijo `.minecraft/` apunta al perfil predeterminado del launcher (no siempre a la instancia actual). Agrega `*` a la ruta de **origen** para copiar todos los archivos directamente dentro de esa carpeta (ignora subdirectorios); el destino debe ser un directorio y no puede usar `*`.
- **Valor requerido:** Sí - `source||destination`

## Mover archivo/carpeta en el directorio del juego (`move_file_in_game_dir`)
- **Descripción:** Mueve dentro del directorio del juego (raíz de la instancia); el prefijo `.minecraft/` apunta al perfil predeterminado del launcher (puede ser diferente de la instancia actual). Agrega `*` a la ruta de **origen** para mover todos los archivos directamente dentro de esa carpeta (ignora subdirectorios); el destino debe ser un directorio y no puede usar `*`.
- **Valor requerido:** Sí - `source||destination`

## Cambiar nombre de archivo/carpeta en el directorio del juego (`rename_file_in_game_dir`)
- **Descripción:** Cambia el nombre de un archivo o carpeta dentro del directorio del juego (raíz de la instancia); el prefijo `.minecraft/` apunta al perfil predeterminado del launcher (puede diferir de la instancia actual). Conserva el contenido intacto, solo cambia el nombre.
- **Valor requerido:** Sí - `path||new_name`

## Descargar archivo al directorio del juego (`download_file_to_game_dir`)
- **Descripción:** Descarga un archivo de forma asincrónica al directorio del juego (raíz de la instancia); el prefijo `.minecraft/` apunta al perfil predeterminado del launcher (no necesariamente a la instancia en ejecución). Proporciona la **carpeta de destino**; el nombre del archivo se deriva automáticamente de los encabezados/URL.
- **Valor requerido:** Sí - `url||target_folder`

## Extraer archivo ZIP en el directorio del juego (`extract_zip_file_in_game_dir`)
- **Descripción:** Extrae un archivo ZIP a una carpeta de destino dentro del directorio del juego o del directorio `.minecraft` predeterminado. Activa el listener **On ZIP Extracted via Action** cuando termina.
- **Valor requerido:** Sí - `source_zip_path||target_folder_path`

## Abrir archivo/carpeta en el directorio del juego (`open_file_folder_in_game_dir`)
- **Descripción:** Abre un archivo o carpeta con la aplicación predeterminada del sistema operativo. El destino debe permanecer dentro del directorio del juego o del directorio `.minecraft` predeterminado por razones de seguridad.
- **Valor requerido:** Sí - `target_path`

## Escribir archivo en el directorio del juego (`write_file_in_game_dir`)
- **Descripción:** Escribe o agrega texto dentro del directorio del juego (raíz de la instancia); el prefijo `.minecraft/` apunta al perfil predeterminado del launcher (puede diferir de esta instancia). Crea el archivo si no existe. Admite `\n` en el valor para insertar saltos de línea; el modo de agregar se controla con el booleano final.
- **Valor requerido:** Sí - `path|||content|||append_bool`

## Seleccionar archivo del sistema (`select_file_to_game_dir`)
- **Descripción:** Abre un selector de archivos nativo (cualquier ubicación) y copia el archivo seleccionado al directorio del juego (raíz de la instancia) o al `.minecraft/` predeterminado cuando se usa el prefijo (ese valor predeterminado puede diferir de esta instancia). Admite filtros por extensión, etiqueta personalizada del filtro y un interruptor opcional para sobrescribir.
- **Valor requerido:** Sí - configuración de selección

## Mostrar toast (`show_toast`)
- **Descripción:** Muestra una notificación toast configurable
- **Valor requerido:** Sí - configuración del toast

## Iniciar scheduler (`start_scheduler`)
- **Descripción:** Inicia un scheduler por su ID de scheduler.
- **Valor requerido:** Sí - `scheduler_id`

## Detener scheduler (`stop_scheduler`)
- **Descripción:** Detiene un scheduler por su ID de scheduler.
- **Valor requerido:** Sí - `scheduler_id`

## Establecer opción de Minecraft (`edit_minecraft_option`)
- **Descripción:** Edita una opción de configuración de Minecraft
- **Valor requerido:** Sí - `option_name:set_to_value`
