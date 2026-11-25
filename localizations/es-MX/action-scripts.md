---
title: Scripts de acciones
description: >-
  Haz que los botones y menús hagan cosas con los scripts de acciones y descubre
  todas las acciones de FancyMenu.
sourceBlobSha: 07ed5af6f189a91c518131cf3a7ab7a1e0a8305d
---

# Scripts de acciones

Un script de acciones es una lista de cosas que FancyMenu hace cuando sucede algo, como cuando se hace clic en un botón o se abre un menú. Cada elemento es una acción: abrir un menú, conectarse a un servidor, mostrar un mensaje, reproducir un sonido y mucho más. Las instrucciones como IF y WHILE deciden qué acciones se ejecutan y con qué frecuencia.

> [!CAUTION]
> Los scripts de acciones pueden modificar archivos, conectarse a servidores, abrir enlaces y ejecutar comandos. Usa únicamente scripts de diseños en los que confíes.

<img width="800" alt="El script de acciones de un botón se crea en el editor de diseños: Edit Action Script, el selector de acciones con Show Toast y el título y el mensaje de la notificación" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_make.gif?raw=true">

# Crear un script de acciones

1. En el editor de diseños, haz clic derecho en un botón y selecciona **Edit Action Script**.
2. Presiona `A` para abrir el selector de acciones.
3. Busca la acción, haz clic en ella y selecciona **Next Step**.
4. Configura la acción en su ventana y selecciona **Done**. Para las acciones que no tienen opciones, solo tienes que seleccionar **Done** en el selector.
5. Selecciona **Done** en el editor de scripts y guarda el diseño.

Fuera del editor, el botón ejecuta su script cuando haces clic en él:

<img width="800" alt="Al hacer clic en el botón What's New? de la pantalla de título, aparece una notificación con el título y el mensaje de la actualización" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_use.gif?raw=true">

> [!TIP]
> Haz clic derecho en el área del script y abre **Add Action** para ver una lista de todas las acciones. Haz clic derecho en una acción de la lista para agregarla a favoritos; así aparecerá en la parte superior.

# Dónde puedes usar scripts de acciones

| Dónde | Se ejecuta cuando | Dónde editarlo |
|---|---|---|
| [Botón](/elements#button) | Haces clic en el botón. | Haz clic derecho en el botón -> **Edit Action Script** |
| [Deslizador](/elements#slider) | Cambia el valor del deslizador. `$$value` es el nuevo valor. | Haz clic derecho en el deslizador -> **Edit Action Script** |
| [Casilla](/elements#checkbox) | Marcas o desmarcas la casilla. `$$value` es su nuevo estado: `true` o `false`. | Haz clic derecho en la casilla -> **Edit Action Script** |
| [Ticker](/elements#ticker) | Según lo que indique **Tick Mode**: una y otra vez, una vez por sesión de juego o una vez al cargar el menú. | Haz clic derecho en el ticker -> **Edit Action Script** |
| Al abrir un menú | Se abre el menú del diseño. | Haz clic derecho en el fondo del editor -> **Edit 'Open Screen' Action Script** |
| Al cerrar un menú | Se cierra el menú del diseño. | Haz clic derecho en el fondo del editor -> **Edit 'Close Screen' Action Script** |
| [Escuchas](/listeners) | Ocurre el evento que les corresponde, como presionar una tecla o recibir un mensaje de chat. | **Barra de menú -> Customization -> Manage Listeners** |
| [Programadores](/schedulers) | Se cumple el tiempo programado, incluso si no hay ningún menú abierto. | **Barra de menú -> Customization -> Manage Schedulers** |

También puedes encontrar los scripts de apertura y cierre en el menú **Layout -> Layout Properties** del editor.

# El editor de scripts

- Las acciones se ejecutan de arriba abajo. Las entradas que están dentro de una instrucción o carpeta aparecen indentadas debajo de esta.
- Las entradas nuevas se agregan debajo de la entrada seleccionada. Si seleccionas una instrucción o carpeta, se agregan al inicio de esta.
- Haz doble clic en un valor para editarlo directamente en la lista. Si el valor muestra un resumen breve, se abrirá su ventana.
- Arrastra las entradas para moverlas. Las cadenas IF, los ciclos y las carpetas se pueden contraer con el pequeño botón que aparece delante. Esto solo cambia la vista.
- La barra de la derecha es un mapa de todo el script. Haz clic en ella para saltar a una parte.
- Haz clic derecho en el área del script para ver las demás opciones, como agregar instrucciones y **Export Action Script for AI** (consulta [Exportar para IA](/export-for-ai)).
- Si seleccionas **Cancel** o cierras la ventana, se descartan tus cambios. Si hiciste alguno, el editor te lo preguntará primero.

## Atajos

En macOS, `Ctrl` equivale a `Cmd`.

| Atajo | Función |
|---|---|
| `A` | Abre el selector de acciones. |
| `Enter` | Edita la entrada seleccionada. |
| `Delete` | Elimina la entrada seleccionada. |
| `Up` / `Down` | Selecciona la entrada anterior o siguiente. |
| `Shift + Up` / `Shift + Down` | Mueve la entrada seleccionada hacia arriba o hacia abajo. |
| `Ctrl + C` / `Ctrl + V` | Copia y pega una acción. No se pueden copiar instrucciones ni bloques. |
| `Ctrl + Z` | Deshacer. |
| `Ctrl + Y` o `Ctrl + Shift + Z` | Rehacer. |
| `Ctrl + S` | Guarda el script y cierra el editor, igual que **Done**. |

# Instrucciones

Las instrucciones determinan qué acciones se ejecutan y con qué frecuencia. Para agregarlas, haz clic derecho en el área del script.

## If, Else-If y Else

**Add IF Statement** solicita [requisitos](/conditions). Las acciones dentro de IF solo se ejecutan si se cumplen.

Haz clic derecho en un IF para agregar más instrucciones a la cadena:

- **Append ELSE-IF Statement**: comprueba sus propios requisitos si no se ejecutó el IF anterior.
- **Append ELSE Statement**: se ejecuta si no se ejecutó ninguna instrucción anterior de la cadena.

Por ejemplo, un IF con **Is Layout Enabled** puede mostrar una notificación solo cuando está activo el diseño de invierno, mientras que un ELSE reproduce un sonido en caso contrario.

## Ciclo While

**Add WHILE Loop** repite sus acciones mientras se cumplan sus [requisitos](/conditions).

Cada ejecución se detiene después de 3 segundos para que un ciclo infinito no pueda congelar el juego. No es un temporizador: si quieres que algo suceda después o se repita una y otra vez, usa [Execute Later](#execute-later), un [Ticker](/elements#ticker) o un [programador](/schedulers).

## Ciclo For Each

**Add FOR EACH Loop** ejecuta sus acciones una vez por cada entrada de una [variable de lista](/variables#text-and-list-variables), desde la primera hasta la última.

- `$$list_entry` es la entrada actual y `$$list_index` es su índice. La primera entrada tiene el índice 0.
- Ambos funcionan en los valores de las acciones y en los requisitos dentro del ciclo.
- Escribe el nombre de la lista sin `$$`, por ejemplo, `quest_log`. También puedes usar marcadores de posición en el nombre.
- El ciclo lee la lista una sola vez al iniciarse, así que las acciones que contiene pueden modificarla sin problema.
- Al igual que los ciclos WHILE, cada ejecución se detiene después de 3 segundos.

Consulta [Recorrer una lista](/variables#going-through-a-list) para ver ejemplos.

# Bloques

Los bloques cambian cuándo se ejecutan las acciones o ayudan a mantener ordenado el script. Para agregarlos, haz clic derecho en el área del script.

## Bloque Delay Gate

**Add DELAY GATE Block** retrasa sus acciones durante cierto tiempo, expresado en milisegundos (`1000` equivale a un segundo).

- La primera vez que el script llega al bloque, inicia el temporizador y omite sus acciones. El resto del script continúa de inmediato.
- Cada vez que el script vuelve a llegar al bloque antes de que termine el tiempo, vuelve a omitirlas.
- A partir de entonces, las acciones se ejecutan cada vez que el script llega al bloque.
- En los scripts de elementos, el temporizador vuelve a empezar cuando se abre el menú de nuevo o se cambia su tamaño.

Es útil para los [Tickers](/elements#ticker), por ejemplo, para mostrar algo solo después de que el menú haya estado abierto unos segundos. El bloque no ejecuta nada por su cuenta: para eso, usa Execute Later.

## Execute Later

**Add EXECUTE LATER Block** ejecuta sus acciones una vez, después de cierto tiempo expresado en milisegundos. El resto del script continúa de inmediato.

Cada vez que el script llega al bloque, inicia una nueva cuenta regresiva. Es útil en scripts que solo se ejecutan una vez, como al hacer clic en un botón o al abrir un menú.

## Carpeta

**Add Folder** agrupa acciones bajo un nombre. Ejecuta todo lo que contiene y solo sirve para mantener ordenados los scripts largos. Haz doble clic en su nombre para cambiarlo.

## Comentario

**Add Comment** agrega una nota para ti. No hace nada. Haz doble clic para editarla.

# Cómo se ejecutan los scripts

- Las acciones se ejecutan de arriba abajo. Si una acción falla, se escribe un error en el registro del juego, pero el resto del script se sigue ejecutando.
- Los marcadores de posición de los valores se reemplazan por su valor actual justo cuando se ejecuta la acción. Así, una acción ve los cambios que hicieron las acciones anteriores.
- Las descargas, la extracción de archivos ZIP y las solicitudes web se completan en segundo plano. La siguiente acción no espera a que terminen. Para ejecutar acciones cuando hayan terminado, usa las escuchas [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action) y [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action), o una variable de respuesta de [**Send HTTP Request**](#send-http-request).

# Valores de las acciones

La mayoría de las acciones necesitan un valor, como la dirección de un servidor. Los valores sencillos son texto que escribes. Las acciones con más opciones tienen su propia ventana.

## Marcadores de posición

Los valores pueden contener [marcadores de posición](/placeholders), como el nombre del jugador. Se reemplazan cuando se ejecuta la acción:

```
/say Welcome back, {"placeholder":"playername"}!
```

## Variables $$

Escribe `$$` seguido del nombre de una variable para usar su valor en una acción o un requisito. Se distingue entre mayúsculas y minúsculas en los nombres. Esto funciona con dos tipos de variables:

### Tus propias variables

Todas las variables que crees en **Barra de menú -> Customization -> Manage Variables** funcionan con `$$` y su nombre. Una variable llamada `coins` se escribe `$$coins` en cualquier script. Por ejemplo, **Display In Chat [Client-Side]** con este valor le indica al jugador cuántas monedas tiene:

```
&6¡Tienes $$coins monedas!
```

Consulta [Variables](/variables) para aprender a crearlas y modificarlas.

### Variables del script

Algunas funciones proporcionan sus propias variables al script:

- Un [deslizador](/elements#slider) proporciona `$$value`, su nuevo valor.
- Una [casilla](/elements#checkbox) proporciona `$$value`, su nuevo estado: `true` o `false`.
- Un [ciclo For Each](#ciclo-for-each) proporciona `$$list_entry` y `$$list_index`.
- Cada [escucha](/listeners#listener-variables) indica las variables que proporciona, como la tecla que se presionó.

Estas variables solo existen mientras se ejecuta el script. Si una tiene el mismo nombre que una de tus variables, `$$name` se refiere a la variable del script.

# Todas las acciones

Todas las acciones de FancyMenu, agrupadas según lo que hacen.

## Pantallas y menús

### Abrir pantalla o interfaz personalizada

**Identifier:** `opengui`

Abre un menú del juego, de un mod o una [interfaz personalizada](/custom-guis).

**Value:** el [identificador de pantalla](/screen-identifiers), por ejemplo, `options_screen`

Se distingue entre mayúsculas y minúsculas. Algunos menús de mods no se pueden abrir de esta forma. En ese caso, usa [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button) en un botón que los abra.

### Cerrar pantalla

**Identifier:** `closegui`

Cierra el menú abierto. Fuera de un mundo, se abre la pantalla de título.

**Value:** ninguno

### Actualizar pantalla

**Identifier:** `update_screen`

Vuelve a crear el menú abierto, como cuando cambias el tamaño de la ventana. Es útil después de cambiar la escala de la interfaz u otras opciones.

**Value:** ninguno

### Volver a la pantalla anterior

**Identifier:** `back_to_last_screen`

Vuelve al menú que estaba abierto antes. Si se trata de una [interfaz personalizada](/custom-guis), vuelve al menú desde el que se abrió.

**Value:** ninguno

### Mostrar notificación

**Identifier:** `show_toast`

Muestra una notificación en la esquina superior derecha. Configúrala en su ventana:

- **Toast Width**: de 120 a 320 píxeles.
- **Duration (ms)**: cuánto tiempo permanece visible, desde 1 segundo (`1000`) hasta 10 minutos.
- **Title** y **Message**: texto con [códigos de formato](/text-formatting#minecraft-text-formatting) o JSON de componentes de texto de Minecraft.
- **Icon Texture Source** y **Background Texture Source**: [imágenes](/resources) opcionales. Los iconos se ven mejor a 20x20 píxeles; los fondos deben tener 32 píxeles de alto y el mismo ancho que la notificación.

### Imitar botón de Vanilla/mod

**Identifier:** `mimicbutton`

Hace clic en un botón del juego o de un mod como si lo hiciera el jugador.

**Value:** el [localizador de widget](/widget-locators) del botón, por ejemplo, `title_screen:mc_titlescreen_options_button`

Para obtenerlo, haz clic derecho en el botón en el editor y selecciona **Copy Widget Locator**.

## Diseños y elementos

### Alternar diseño

**Identifier:** `toggle_layout`

Desactiva un diseño si está activado y lo activa si está desactivado.

**Value:** el nombre del diseño, sin `.txt`, por ejemplo, `winter_title_screen`

### Activar diseño

**Identifier:** `enable_layout`

Activa un diseño.

**Value:** el nombre del diseño, sin `.txt`

### Desactivar diseño

**Identifier:** `disable_layout`

Desactiva un diseño.

**Value:** el nombre del diseño, sin `.txt`

Las tres acciones de diseño guardan el cambio y actualizan el menú abierto de inmediato. Se distingue entre mayúsculas y minúsculas en el nombre.

### Alternar animador de elementos

**Identifier:** `toggle_element_animator`

Activa un [animador de elementos](/element-animator) si está desactivado y lo desactiva si está activado. La animación comienza desde el principio. El estado queda guardado.

**Value:** el identificador del animador de elementos

### Activar animador de elementos

**Identifier:** `enable_element_animator`

Activa un [animador de elementos](/element-animator). Si estaba desactivado, la animación comienza desde el principio.

**Value:** el identificador del animador de elementos

### Desactivar animador de elementos

**Identifier:** `disable_element_animator`

Desactiva un [animador de elementos](/element-animator) y reinicia su animación.

**Value:** el identificador del animador de elementos

### Reiniciar animador de elementos

**Identifier:** `reset_element_animator`

Inicia desde el principio la animación de un [animador de elementos](/element-animator), sin activarlo ni desactivarlo.

**Value:** el identificador del animador de elementos

### Establecer el valor de un campo de texto

**Identifier:** `set_text_input_field_value`

Establece el texto de un [campo de entrada de texto](/elements#text-input-field), ya sea de FancyMenu o del juego.

**Value:** `element_identifier|||text|||force`

Si `force` se establece en `true`, el texto también cambia cuando el campo está desactivado (inactivo).

### Desplazar un elemento

**Identifier:** `scroll_scroll_area`

Desplaza un [área desplazable](/scrollable-areas) o un elemento de [texto](/elements#text). Configúralo en su ventana:

- **Identifier of the Element to Scroll**: el área o el texto que se desplazará.
- **Scroll To**:
  - **Start** o **End**.
  - **Position**: la **Horizontal Position** y la **Vertical Position** en píxeles. Deja una vacía para conservarla.
  - **Element** (solo áreas): desplaza el contenido hasta que el elemento indicado en **Identifier of the Element to Scroll To** quede al inicio.
  - **Line Number** (solo textos): la primera línea es `1`.
  - **Line with Text** (solo textos): la primera línea que contenga el **Text in the Line**. No se distingue entre mayúsculas y minúsculas.
- **Glide There**: se desplaza suavemente hasta ahí en lugar de saltar. El desplazamiento suave debe estar activado en el elemento.

No hace nada si no existe el elemento indicado.

## Audio y video

### Pista siguiente

**Identifier:** `audio_next_track`

Pasa a la pista siguiente de un [elemento de audio](/elements#audio).

**Value:** el identificador del elemento de audio, por ejemplo, `menu_music`

### Pista anterior

**Identifier:** `audio_previous_track`

Vuelve a la pista anterior de un [elemento de audio](/elements#audio).

**Value:** el identificador del elemento de audio

### Establecer volumen de pista

**Identifier:** `set_audio_element_volume`

Establece el volumen de un [elemento de audio](/elements#audio), de `0.0` (0 %) a `1.0` (100 %).

**Value:** `element_identifier:volume`, por ejemplo, `menu_music:0.5`

### Alternar reproducción o pausa de pista

**Identifier:** `audio_toggle_play`

Pausa un [elemento de audio](/elements#audio) que se está reproduciendo o reproduce uno que está en pausa.

**Value:** el identificador del elemento de audio

### Reproducir audio

**Identifier:** `play_audio`

Reproduce un archivo de audio una vez. Configura en su ventana **Audio Source**, **Sound Channel** y **Base Volume** (hasta 100 %).

- FancyMenu espera hasta diez segundos a que se cargue el audio.
- No funciona en un [Ticker](/elements#ticker) que se ejecuta en segundo plano (asíncrono). En su lugar, FancyMenu muestra un error.

[**Stop All Action Audios**](#stop-all-action-audios) detiene los audios iniciados con esta acción.

### Detener todos los audios de acciones

**Identifier:** `stop_all_action_audios`

Detiene todos los audios iniciados con [**Play Audio**](#play-audio). Los elementos de audio, los sonidos del menú y los sonidos de los botones siguen reproduciéndose.

**Value:** ninguno

### Establecer volumen del elemento de video

**Identifier:** `set_video_element_volume`

Establece el volumen de un [elemento de video](/video), de `0.0` (0 %) a `1.0` (100 %).

**Value:** `video_element_identifier:volume`

### Establecer tiempo de reproducción del elemento de video

**Identifier:** `set_video_element_play_time`

Salta a un momento de un [elemento de video](/video), expresado en milisegundos.

**Value:** `video_element_identifier:time_in_ms`, por ejemplo, `intro_video:30000`

### Alternar pausa del elemento de video

**Identifier:** `toggle_video_element_pause_state`

Pausa un [elemento de video](/video) que se está reproduciendo o reproduce uno que está en pausa.

**Value:** el identificador del elemento de video

### Establecer volumen del fondo de video

**Identifier:** `set_video_menu_background_volume`

Establece el volumen de un [fondo de menú de video](/video), de `0.0` (0 %) a `1.0` (100 %).

**Value:** `background_identifier:volume`

> [!NOTE]
> Para obtener el identificador de un fondo de menú, haz clic derecho en el fondo del editor y selecciona **Copy Background Identifier**.

### Establecer tiempo de reproducción del fondo de video

**Identifier:** `set_video_menu_background_play_time`

Salta a un momento de un [fondo de menú de video](/video), expresado en milisegundos.

**Value:** `background_identifier:time_in_ms`

### Alternar pausa del fondo de video

**Identifier:** `toggle_video_menu_background_pause_state`

Pausa un [fondo de menú de video](/video) que se está reproduciendo o reproduce uno que está en pausa.

**Value:** el identificador del fondo de menú

## Mundos y servidores

### Conectarse a un servidor

**Identifier:** `joinserver`

Se conecta a un servidor de Minecraft.

**Value:** `address` o `address:port`, por ejemplo, `play.example.net`

Si no se indica un puerto, se usa `25565`. Si hay un mundo o servidor cargado, muestra un error. Los servidores que no están en la lista de servidores se agregan a ella.

### Entrar a un mundo

**Identifier:** `loadworld`

Carga un mundo de un jugador.

**Value:** el nombre de la carpeta del mundo dentro de `saves`, por ejemplo, `Survival Island`

No hace nada si el mundo no existe. Si hay un mundo o servidor cargado, muestra un error.

### Entrar al último mundo o servidor

**Identifier:** `join_last_world`

Carga el mundo o se conecta al servidor en el que jugó el jugador por última vez.

**Value:** ninguno

Si hay un mundo o servidor cargado, muestra un error. Si el servidor no está en la lista de servidores, se agrega a ella.

### Salir del mundo o servidor

**Identifier:** `disconnect_server_or_world`

Sale del mundo o servidor y abre un menú.

**Value:** el [identificador de pantalla](/screen-identifiers) del menú que se abrirá, por ejemplo, `title_screen`

Solo funciona si hay un mundo cargado. También funcionan las [interfaces personalizadas](/custom-guis). Si no se puede abrir el menú, se abre la pantalla de título.

## Chat y comandos

### Enviar mensaje o comando de chat

**Identifier:** `sendmessage`

Envía un mensaje de chat o ejecuta un comando como si lo hubiera escrito el jugador.

**Value:** el mensaje o un comando con `/`, por ejemplo, `/spawn`

### Ejecutar comando como servidor integrado

**Identifier:** `execute_command_as_integrated_server`

Ejecuta un comando en un mundo de un jugador como servidor, sin importar los permisos del jugador ni si los trucos están activados.

**Value:** el comando, por ejemplo, `/give @p minecraft:diamond 1`

> [!WARNING]
> Solo funciona en un mundo de un jugador que no esté abierto a LAN. En cualquier otro caso, no hace nada.

### Pegar en el chat

**Identifier:** `paste_to_chat`

Escribe texto en el campo de entrada del chat cuando hay un mundo cargado. Si el chat no está abierto, lo abre con el texto.

**Value:** `true:text` agrega el texto a lo que ya está escrito; `false:text` lo reemplaza

### Mostrar en el chat [solo en el cliente]

**Identifier:** `display_in_chat_client_side`

Muestra un mensaje de chat que solo ve este jugador. No se envía nada al servidor.

**Value:** el texto con [códigos de formato](/text-formatting#minecraft-text-formatting) o en formato JSON de componentes de texto de Minecraft, por ejemplo, `&a¡Qué bueno verte de nuevo!`

No hace nada si no hay ningún mundo cargado.

## Variables y listas

### Establecer el valor de una variable (variable de FM)

**Identifier:** `set_variable`

Establece una [variable](/variables).

**Value:** `variable_name:value`, por ejemplo, `coins:100`

- Solo el primer `:` separa el nombre del valor.
- Las [variables de lista](/variables#text-and-list-variables) siguen siendo listas: un arreglo JSON como `["a","b"]` se convierte en sus entradas; cualquier otro texto se convierte en su única entrada; y el texto vacío las deja vacías.

### Eliminar variable (variable de FM)

**Identifier:** `delete_variable`

Elimina por completo una [variable](/variables). Las demás variables se conservan. Para dejarla vacía, usa [**Set Variable Value (FM Variable)**](#set-variable-value-fm-variable).

**Value:** el nombre de la variable

### Borrar todas las variables (variable de FM)

**Identifier:** `clear_variables`

Elimina todas las [variables](/variables), tanto de texto como de lista.

**Value:** ninguno

### Agregar a una lista (variable de FM)

**Identifier:** `add_to_list`

Agrega una entrada a una [variable de lista](/variables#list-actions).

- **List Variable**: el nombre de la lista. Si todavía no existe una variable con ese nombre, la acción crea la lista.
- **New Entry**: el texto de la entrada.
- **Index (Optional)**: dónde colocar la entrada. Si lo dejas vacío, se agrega al final. Las entradas que siguen a esa posición se recorren una posición.
- **Skip If Already in List**: no agrega nada si la lista ya contiene una entrada con el mismo texto. **Ignore Case** hace que `Apple` coincida con `apple`.

### Establecer entrada de lista (variable de FM)

**Identifier:** `set_list_entry`

Reemplaza la entrada en el **Index** indicado de una [variable de lista](/variables#list-actions) por un **New Value**. No hace nada si la lista no tiene una entrada en esa posición.

### Eliminar de una lista (variable de FM)

**Identifier:** `remove_from_list`

Elimina entradas de una [variable de lista](/variables#list-actions). **Remove** permite elegir cuáles:

- **Entry at Index**: la entrada que está en el índice indicado.
- **First Match**: la primera entrada que coincida exactamente con **Value to Remove**.
- **All Matches**: todas las entradas que coincidan.

**Ignore Case** hace que `Apple` coincida con `apple`.

### Vaciar lista (variable de FM)

**Identifier:** `clear_list`

Elimina todas las entradas de una [variable de lista](/variables#list-actions). La lista vacía se conserva.

### Establecer lista (variable de FM)

**Identifier:** `set_list`

Reemplaza todas las entradas de una [variable de lista](/variables#list-actions). **Entries From** permite elegir de dónde vienen:

- **Split Text**: divide el **Text to Split** usando el **Separator**, por ejemplo, `,`. Si el separador está vacío, divide el texto en los saltos de línea. **Trim Entries** elimina los espacios al inicio y al final de cada entrada; **Skip Empty Entries** omite las entradas vacías.
- **JSON Array**: usa las entradas de un arreglo como `["Diamonds","Emeralds"]` o `$$other_list` para copiar otra lista. Cualquier otro texto se convierte en la única entrada; el texto vacío deja la lista vacía.

La ventana muestra una vista previa de las entradas.

### Ordenar lista (variable de FM)

**Identifier:** `arrange_list`

Cambia el orden de una [variable de lista](/variables#list-actions). **Arrangement**:

- **Sort A–Z** y **Sort Z–A**: ordena alfabéticamente.
- **Numbers, Smallest First** y **Numbers, Biggest First**: ordena por número. Las entradas que no sean números se colocan al final.
- **Reverse Order**: la última entrada pasa a ser la primera.
- **Shuffle**: orden aleatorio.
- **Remove Duplicates**: conserva solo la primera aparición de cada valor.

En todas las acciones de listas, la primera entrada tiene el índice `0` y `-1` corresponde a la última. El nombre de la lista puede contener marcadores de posición. Si antepones `$$`, la acción usa el valor de esa variable como nombre de la lista. Las variables de texto que tengan un valor se conservan tal cual y la acción escribe una advertencia en el registro del juego.

## Web y redes

### Abrir URL en el navegador

**Identifier:** `openlink`

Abre un enlace en el navegador predeterminado sin pedir confirmación.

**Value:** el enlace, por ejemplo, `https://discord.gg/example`

Usa únicamente enlaces en los que confíes.

### Enviar solicitud HTTP

**Identifier:** `send_http_request`

Envía una solicitud web en segundo plano. Puede escribir la respuesta en el registro del juego o guardarla en una variable.

| Configuración | Función |
|---|---|
| URL | La dirección HTTP o HTTPS. |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` u `OPTIONS`. |
| Body | Los datos que se enviarán. No se envían con `GET` ni `HEAD`. |
| Content type | El `Content-Type` del cuerpo, por ejemplo, `application/json`. |
| Timeout | Los segundos que se esperará a que se establezca la conexión y llegue la respuesta. |
| Log response | Escribe la respuesta en el registro del juego. |
| Response variable | Guarda la respuesta en esta variable cuando llegue. |
| Single-line response | Elimina los saltos de línea de la respuesta antes de guardarla. |
| Authentication | Ninguna, Basic, Bearer o API key. |
| Headers | Encabezados adicionales de la solicitud. |

La siguiente acción no espera la respuesta. Los errores en las respuestas también se registran y guardan. No incluyas contraseñas ni tokens de acceso en la acción: cualquier persona que tenga el diseño puede leerlos.

### Enviar datos de FM al servidor

**Identifier:** `send_fm_data_to_server`

Envía [datos de FM](/fm-data) al servidor, que también debe tener FancyMenu.

**Value:** `data_identifier||data`

### Conectarse a un servidor remoto

**Identifier:** `connect_to_remote_server`

Se conecta a un servidor remoto o usa una conexión que ya esté abierta.

**Value:** la dirección del servidor, por ejemplo, `wss://example.com/ws`

Consulta [Comunicación con servidores remotos](/remote-server-communication#url-modes) para ver qué direcciones son compatibles.

### Enviar datos a un servidor remoto

**Identifier:** `send_data_to_remote_server`

Envía texto a un servidor remoto y se conecta primero si hace falta.

**Value:** `server_address||data`

### Cerrar conexión con un servidor remoto

**Identifier:** `close_remote_server_connection`

Cierra una conexión con un servidor remoto.

**Value:** su ID de solicitud, normalmente `$$request_id` de [**On Remote Server Connected**](/listeners#on-remote-server-connected)

### Cerrar todas las conexiones con servidores remotos

**Identifier:** `close_all_remote_server_connections`

Cierra todas las conexiones con servidores remotos que abrió FancyMenu.

**Value:** ninguno

## Archivos

### Crear archivo en la carpeta del juego

**Identifier:** `create_file_in_game_dir`

Crea un archivo vacío. También crea las carpetas que falten. Si el archivo ya existe, se conserva tal como está.

**Value:** la ruta del archivo, por ejemplo, `config/mymodpack/first_start.txt`

Todas las acciones de archivos solo funcionan dentro de la carpeta del juego (la carpeta de la instancia). Las rutas que empiezan con `.minecraft/` usan en su lugar la carpeta `.minecraft` predeterminada, que puede ser otra carpeta.

### Eliminar archivo o carpeta de la carpeta del juego

**Identifier:** `delete_file_in_game_dir`

Elimina un archivo o una carpeta junto con todo lo que contiene.

**Value:** la ruta, por ejemplo, `config/mymodpack/cache.txt`

Si agregas `*` al final, como en `config/downloads/*`, elimina todos los archivos que están directamente en esa carpeta, pero conserva la carpeta y las carpetas que contiene.

### Copiar archivo o carpeta en la carpeta del juego

**Identifier:** `copy_file_in_game_dir`

Copia un archivo o una carpeta junto con todo lo que contiene.

**Value:** `source||destination`, por ejemplo, `config/presets/default.json||config/mymod/settings.json`

- Si agregas `*` al final del origen, como en `config/presets/*||config/mymod/`, copia todos los archivos que están directamente en esa carpeta, pero no las carpetas. En ese caso, el destino debe ser una carpeta y se crea si hace falta.
- No se sobrescribe nada: si el destino ya existe, la acción falla.

### Mover archivo o carpeta en la carpeta del juego

**Identifier:** `move_file_in_game_dir`

Mueve un archivo o una carpeta junto con todo lo que contiene.

**Value:** `source||destination`

Si agregas `*` al final del origen, funciona igual que en [**Copiar archivo o carpeta en la carpeta del juego**](#copiar-archivo-o-carpeta-en-la-carpeta-del-juego). No se sobrescribe nada.

### Cambiar el nombre de un archivo o carpeta en la carpeta del juego

**Identifier:** `rename_file_in_game_dir`

Cambia el nombre de un archivo o carpeta. La acción falla si ya existe algo con el nuevo nombre.

**Value:** `path||new_name`, por ejemplo, `config/mymod/old_name.txt||new_name.txt`

### Descargar archivo a la carpeta del juego

**Identifier:** `download_file_to_game_dir`

Descarga un archivo a una carpeta en segundo plano.

**Value:** `url||target_folder`, por ejemplo, `https://example.com/pack.zip||downloads`

- La segunda parte debe ser una carpeta, no un nombre de archivo. FancyMenu obtiene el nombre de la descarga o del enlace.
- Si ya existe un archivo con el mismo nombre, se sobrescribe.
- [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action) se ejecuta cuando la descarga termina o falla. Si tiene éxito, `$$target_file_path` contiene la ruta del archivo guardado.

### Extraer archivo ZIP en la carpeta del juego

**Identifier:** `extract_zip_file_in_game_dir`

Extrae un archivo ZIP en una carpeta en segundo plano.

**Value:** `zip_path||target_folder`, por ejemplo, `downloads/pack.zip||resourcepacks/MyPack`

Los archivos con el mismo nombre se reemplazan y no se crea otra carpeta con el nombre del ZIP. [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action) se ejecuta cuando termina la extracción. Extrae únicamente archivos ZIP en los que confíes.

### Abrir archivo o carpeta de la carpeta del juego

**Identifier:** `open_file_folder_in_game_dir`

Abre un archivo o carpeta con el programa que el sistema tiene asignado.

**Value:** la ruta, por ejemplo, `screenshots`

### Escribir archivo en la carpeta del juego

**Identifier:** `write_file_in_game_dir`

Escribe texto en un archivo. Si hace falta, se crean el archivo y sus carpetas.

**Value:** `path|||text|||append`, por ejemplo, `config/mymodpack/log.txt|||Joined the server\n|||true`

`\n` inicia una nueva línea. Si `append` se establece en `true`, el texto se agrega al final del archivo; si se establece en `false`, reemplaza el contenido.

### Seleccionar archivo del sistema

**Identifier:** `select_file_to_game_dir`

Abre el selector de archivos del sistema y copia el archivo elegido a la carpeta del juego.

**Value:** `target_path|||filter_name|||extensions|||overwrite`, por ejemplo, `config/fancymenu/assets/background.png|||Images|||png;jpg|||true`

- `target_path` es la ruta completa de la copia, incluido el nombre del archivo.
- Separa las extensiones con `;` o `,`. Si no especificas extensiones, puedes elegir cualquier archivo.
- Si `overwrite` se establece en `false`, la acción falla cuando el archivo ya existe.

[**On File Selected**](/listeners#on-file-selected) se ejecuta cuando se copia el archivo, se cancela el selector o ocurre un error.

## El juego y FancyMenu

### Salir de Minecraft

**Identifier:** `quitgame`

Cierra el juego.

**Value:** ninguno

### Cambiar opción de Minecraft

**Identifier:** `edit_minecraft_option`

Cambia una opción de Minecraft, como la distancia de renderizado o la escala de la interfaz.

**Value:** `option_name:value`, por ejemplo, `renderDistance:12`

Consulta [Opciones de Minecraft](/minecraft-options) para conocer los nombres de las opciones.

### Imitar una combinación de teclas

**Identifier:** `mimic_keybind`

Presiona una tecla asignada de Minecraft, como saltar o agacharse, y puede mantenerla presionada.

**Value:** `keybind|||hold|||duration_ms`, por ejemplo, `key.jump|||false|||1000`

| Parte | Descripción |
|---|---|
| `keybind` | El ID de la tecla asignada, por ejemplo, `key.jump` o `key.sneak`. |
| `hold` | `true` mantiene la tecla presionada; `false` la presiona una vez. |
| `duration_ms` | Cuánto tiempo se mantiene presionada, en milisegundos. Si no se especifica, se usa `1000`. |

### Administrar paquete de recursos

**Identifier:** `manage_resource_pack`

Activa o desactiva un paquete de recursos. Configúralo en su ventana:

- **Target Resource Pack**: el nombre del paquete tal como aparece en la pantalla de Paquetes de recursos. No se distingue entre mayúsculas y minúsculas.
- **Action Mode**: **Enable**, **Disable** o **Toggle**.
- **Reload Resources**: vuelve a cargar los paquetes de recursos justo después del cambio. Desactívalo para volver a cargarlos más tarde, por ejemplo, con [**Reload Resource Packs**](#reload-resource-packs).

No se pueden desactivar los paquetes que el juego necesita.

### Volver a cargar paquetes de recursos

**Identifier:** `reload_resource_packs`

Vuelve a cargar los paquetes de recursos, igual que con `F3 + T`. Durante los cinco segundos posteriores a la recarga, la acción no hace nada para evitar que se repita una y otra vez.

**Value:** ninguno

### Volver a cargar FancyMenu

**Identifier:** `reloadmenu`

Vuelve a cargar los diseños, las [interfaces personalizadas](/custom-guis), los [panoramas](/panoramas), las [presentaciones de diapositivas](/slideshows), la configuración y los archivos de FancyMenu. Los paquetes de recursos no se vuelven a cargar.

**Value:** ninguno

> [!WARNING]
> La recarga tarda un momento. Úsala en un botón, nunca en un [Ticker](/elements#ticker) ni en una [escucha](/listeners) que se ejecute con frecuencia.

### Iniciar programador

**Identifier:** `start_scheduler`

Inicia un [programador](/schedulers).

**Value:** el identificador del programador

### Detener programador

**Identifier:** `stop_scheduler`

Detiene un [programador](/schedulers).

**Value:** el identificador del programador

### Copiar texto al portapapeles

**Identifier:** `copytoclipboard`

Copia texto al portapapeles.

**Value:** el texto, por ejemplo, `play.example.net`

### Escribir en el registro del juego

**Identifier:** `print_to_log`

Escribe una línea en el registro del juego. Es útil para averiguar qué hace un script.

**Value:** el texto
