---
title: Scripts de acciones
description: >-
  Haz que los botones y menús hagan cosas con scripts de acciones y descubre
  todas las acciones de FancyMenu.
sourceBlobSha: 07ed5af6f189a91c518131cf3a7ab7a1e0a8305d
---

# Scripts de acciones

Un script de acciones es una lista de cosas que hace FancyMenu cuando ocurre algo, como al hacer clic en un botón o al abrirse un menú. Cada elemento es una acción: abrir un menú, conectarse a un servidor, mostrar un mensaje, reproducir un sonido y mucho más. Las instrucciones como IF y WHILE determinan qué acciones se ejecutan y con qué frecuencia.

> [!CAUTION]
> Los scripts de acciones pueden modificar archivos, ponerse en contacto con servidores, abrir enlaces y ejecutar comandos. Usa únicamente scripts de diseños en los que confíes.

<img width="800" alt="El script de acciones de un botón se crea en el editor de diseños: Edit Action Script, el selector de acciones con Show Toast y el título y mensaje del aviso" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_make.gif?raw=true">

# Crear un script de acciones

1. En el editor de diseños, haz clic derecho en un botón y selecciona **Editar script de acciones**.
2. Pulsa `A` para abrir el selector de acciones.
3. Busca la acción, haz clic en ella y selecciona **Siguiente paso**.
4. Configura la acción en su ventana y selecciona **Listo**. Para las acciones sin ajustes, solo tienes que seleccionar **Listo** en el selector.
5. Selecciona **Listo** en el editor de scripts y guarda el diseño.

Fuera del editor, el botón ejecuta su script cuando haces clic en él:

<img width="800" alt="Al hacer clic en el botón What's New? de la pantalla del título, aparece un aviso con el título y el mensaje de la actualización" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_use.gif?raw=true">

> [!TIP]
> Haz clic derecho en el área del script y abre **Añadir acción** para ver una lista de todas las acciones. Haz clic derecho en una acción de la lista para añadirla a favoritos y que aparezca en la parte superior.

# Dónde puedes usar scripts de acciones

| Dónde | Se ejecuta cuando | Dónde editarlo |
|---|---|---|
| [Botón](/elements#button) | Se hace clic en el botón. | Haz clic derecho en el botón -> **Editar script de acciones** |
| [Control deslizante](/elements#slider) | Cambia el valor del control deslizante. `$$value` es el nuevo valor. | Haz clic derecho en el control deslizante -> **Editar script de acciones** |
| [Casilla](/elements#checkbox) | Se marca o desmarca la casilla. `$$value` es su nuevo estado: `true` o `false`. | Haz clic derecho en la casilla -> **Editar script de acciones** |
| [Temporizador](/elements#ticker) | Según indique su **Modo de temporizador**: repetidamente, una vez por sesión de juego o una vez al cargar el menú. | Haz clic derecho en el temporizador -> **Editar script de acciones** |
| Al abrir un menú | Se abre el menú del diseño. | Haz clic derecho en el fondo del editor -> **Editar script de acciones «Abrir pantalla»** |
| Al cerrar un menú | Se cierra el menú del diseño. | Haz clic derecho en el fondo del editor -> **Editar script de acciones «Cerrar pantalla»** |
| [Escuchas](/listeners) | Se produce el evento que detectan, como pulsar una tecla o recibir un mensaje en el chat. | **Barra de menú -> Personalización -> Gestionar escuchas** |
| [Programadores](/schedulers) | Cuando se cumple su temporizador, incluso si no hay ningún menú abierto. | **Barra de menú -> Personalización -> Gestionar programadores** |

También puedes acceder a los scripts de apertura y cierre desde el menú **Diseño -> Propiedades del diseño** del editor.

# El editor de scripts

- Las acciones se ejecutan de arriba abajo. Las entradas de una instrucción o carpeta aparecen sangradas debajo de esta.
- Las nuevas entradas se añaden debajo de la entrada seleccionada. Si seleccionas una instrucción o carpeta, se añaden al principio de esta.
- Haz doble clic en un valor para editarlo directamente en la lista. Si un valor muestra un breve resumen, se abrirá su ventana.
- Arrastra las entradas para moverlas. Las cadenas IF, los bucles y las carpetas se pueden contraer con el pequeño botón que tienen delante. Esto solo cambia la vista.
- La barra de la derecha es un mapa de todo el script. Haz clic en ella para saltar a una parte.
- Haz clic derecho en el área del script para ver el resto de opciones, como añadir instrucciones y **Exportar script de acciones para IA** (consulta [Exportar para IA](/export-for-ai)).
- Si seleccionas **Cancelar** o cierras la ventana, se descartan los cambios. Si hay cambios, el editor te lo pregunta antes.

## Atajos

En macOS, `Ctrl` equivale a `Cmd`.

| Atajo | Qué hace |
|---|---|
| `A` | Abre el selector de acciones. |
| `Enter` | Edita la entrada seleccionada. |
| `Delete` | Elimina la entrada seleccionada. |
| `Arriba` / `Abajo` | Selecciona la entrada anterior o siguiente. |
| `Shift + Arriba` / `Shift + Abajo` | Mueve la entrada seleccionada hacia arriba o abajo. |
| `Ctrl + C` / `Ctrl + V` | Copia y pega una acción. No se pueden copiar instrucciones ni bloques. |
| `Ctrl + Z` | Deshacer. |
| `Ctrl + Y` o `Ctrl + Shift + Z` | Rehacer. |
| `Ctrl + S` | Guarda el script y cierra el editor, igual que **Listo**. |

# Instrucciones

Las instrucciones determinan qué acciones se ejecutan y con qué frecuencia. Añádelas haciendo clic derecho en el área del script.

## If, Else-If y Else

**Añadir instrucción IF** solicita [requisitos](/conditions). Las acciones de IF solo se ejecutan si se cumplen.

Haz clic derecho en una instrucción IF para añadir más elementos a su cadena:

- **Añadir instrucción ELSE-IF**: comprueba sus propios requisitos si no se ha ejecutado la instrucción IF anterior.
- **Añadir instrucción ELSE**: se ejecuta si no se ha ejecutado nada de lo anterior en la cadena.

Por ejemplo, una instrucción IF con **El diseño está activado** puede mostrar un aviso únicamente mientras esté activo el diseño de invierno, y una instrucción ELSE puede reproducir un sonido en caso contrario.

## Bucle While

**Añadir bucle WHILE** repite sus acciones mientras se cumplan sus [requisitos](/conditions).

Cada ejecución se detiene después de 3 segundos, así que un bucle infinito no puede bloquear el juego. No es un temporizador: para ejecutar cosas más tarde o repetidamente, usa [Ejecutar más tarde](#execute-later), un [temporizador](/elements#ticker) o un [programador](/schedulers).

## Bucle For Each

**Añadir bucle FOR EACH** ejecuta sus acciones una vez por cada elemento de una [variable de lista](/variables#text-and-list-variables), desde el primero hasta el último.

- `$$list_entry` es el elemento actual y `$$list_index` su índice. El índice del primer elemento es 0.
- Ambos funcionan en los valores de las acciones y en los requisitos del bucle.
- Escribe el nombre de la lista sin `$$`, por ejemplo, `quest_log`. También puedes usar marcadores de posición en el nombre.
- El bucle lee la lista una sola vez al empezar, así que las acciones que contiene pueden modificarla sin problemas.
- Al igual que los bucles WHILE, cada ejecución se detiene después de 3 segundos.

Consulta [Recorrer una lista](/variables#going-through-a-list) para ver ejemplos.

# Bloques

Los bloques cambian cuándo se ejecutan las acciones o ayudan a mantener ordenado el script. Añádelos haciendo clic derecho en el área del script.

## Bloque de retardo

**Añadir bloque DELAY GATE** retrasa sus acciones durante un tiempo en milisegundos (`1000` equivale a un segundo).

- La primera vez que el script llega al bloque, inicia el temporizador y omite sus acciones. El resto del script continúa de inmediato.
- Cada vez que el script vuelve a llegar al bloque antes de que termine el tiempo, vuelve a omitir esas acciones.
- A partir de entonces, sus acciones se ejecutan cada vez que el script llega al bloque.
- En los scripts de elementos, el temporizador vuelve a empezar al abrirse de nuevo el menú o al cambiar su tamaño.

Es una buena opción para los [temporizadores](/elements#ticker), por ejemplo, para mostrar algo solo cuando el menú lleve abierto unos segundos. No ejecuta nada por sí solo: para eso, usa Ejecutar más tarde.

## Ejecutar más tarde

**Añadir bloque EXECUTE LATER** ejecuta sus acciones una vez, tras un tiempo en milisegundos. El resto del script continúa de inmediato.

Cada vez que el script llega al bloque, se inicia una nueva cuenta atrás. Es útil para scripts que solo se ejecutan una vez, como al hacer clic en un botón o al abrir un menú.

## Carpeta

**Añadir carpeta** agrupa acciones bajo un nombre. Ejecuta todo lo que contiene y sirve únicamente para mantener ordenados los scripts largos. Haz doble clic en el nombre para cambiarlo.

## Comentario

**Añadir comentario** añade una nota para ti. No hace nada. Haz doble clic para editarla.

# Cómo se ejecutan los scripts

- Las acciones se ejecutan de arriba abajo. Si una acción falla, se escribe un error en el registro del juego, pero el resto del script sigue ejecutándose.
- Los marcadores de posición de los valores se sustituyen por su valor actual justo cuando se ejecuta la acción, así que esta ve los cambios realizados por las acciones anteriores.
- Las descargas, la extracción de archivos ZIP y las solicitudes web se completan en segundo plano. La acción siguiente no espera a que terminen. Para ejecutar acciones cuando hayan terminado, usa las escuchas [**Al descargar un archivo mediante una acción**](/listeners#on-file-downloaded-via-action) y [**Al extraer un ZIP mediante una acción**](/listeners#on-zip-extracted-via-action), o una variable de respuesta de [**Enviar solicitud HTTP**](#send-http-request).

# Valores de las acciones

La mayoría de las acciones necesitan un valor, como la dirección de un servidor. Los valores sencillos son texto que escribes. Las acciones con más ajustes tienen su propia ventana.

## Marcadores de posición

Los valores pueden contener [marcadores de posición](/placeholders), como el nombre del jugador. Se sustituyen cuando se ejecuta la acción:

```
/say Welcome back, {"placeholder":"playername"}!
```

## Variables $$

Escribe `$$` seguido del nombre de una variable para usar su valor en una acción o un requisito. Se distingue entre mayúsculas y minúsculas. Esto funciona con dos tipos de variables:

### Tus propias variables

Todas las variables que crees en **Barra de menú -> Personalización -> Gestionar variables** funcionan con `$$` y su nombre. Una variable llamada `coins` se escribe `$$coins` en cualquier script. Por ejemplo, con este valor, **Mostrar en el chat [del lado del cliente]** le indica al jugador cuántas monedas tiene:

```
&6Tienes $$coins monedas.
```

Consulta [Variables](/variables) para aprender a crearlas y modificarlas.

### Variables del script

Algunas funciones proporcionan variables propias al script:

- Un [control deslizante](/elements#slider) proporciona `$$value`, su nuevo valor.
- Una [casilla](/elements#checkbox) proporciona `$$value`, su nuevo estado: `true` o `false`.
- Un [bucle For Each](#for-each-loop) proporciona `$$list_entry` y `$$list_index`.
- Cada [escucha](/listeners#listener-variables) indica las variables que proporciona, como la tecla que se ha pulsado.

Solo existen mientras se ejecuta el script. Si una variable del script tiene el mismo nombre que una de tus variables, `$$name` hace referencia a la variable del script.

# Todas las acciones

Todas las acciones de FancyMenu, agrupadas según lo que hacen.

## Pantallas y menús

### Abrir pantalla o interfaz gráfica personalizada

**Identificador:** `opengui`

Abre un menú del juego, de un mod o una [interfaz gráfica personalizada](/custom-guis).

**Valor:** el [identificador de pantalla](/screen-identifiers), por ejemplo, `options_screen`

Se distingue entre mayúsculas y minúsculas. Algunos menús de mods no se pueden abrir de esta forma. En ese caso, usa [**Imitar botón vanilla/mod**](#mimic-vanillamod-button) en un botón que lo abra.

### Cerrar pantalla

**Identificador:** `closegui`

Cierra el menú abierto. Si no estás en un mundo, se abre la pantalla del título.

**Valor:** ninguno

### Actualizar pantalla

**Identificador:** `update_screen`

Vuelve a crear el menú abierto, como cuando se cambia el tamaño de la ventana. Es útil después de cambiar la escala de la interfaz u otras opciones.

**Valor:** ninguno

### Volver a la pantalla anterior

**Identificador:** `back_to_last_screen`

Vuelve al menú que estaba abierto anteriormente. Si se trata de una [interfaz gráfica personalizada](/custom-guis), vuelve al menú desde el que se abrió.

**Valor:** ninguno

### Mostrar aviso

**Identificador:** `show_toast`

Muestra una notificación en la esquina superior derecha. Se configura en su ventana:

- **Ancho del aviso**: de 120 a 320 píxeles.
- **Duración (ms)**: cuánto tiempo se muestra, desde 1 segundo (`1000`) hasta 10 minutos.
- **Título** y **Mensaje**: texto con [códigos de formato](/text-formatting#minecraft-text-formatting) o en formato JSON de componentes de texto de Minecraft.
- **Origen de la textura del icono** y **Origen de la textura del fondo**: [imágenes](/resources) opcionales. Los iconos quedan mejor a 20x20 píxeles y los fondos deberían tener 32 píxeles de alto y el mismo ancho que el aviso.

### Imitar botón vanilla/mod

**Identificador:** `mimicbutton`

Hace clic en un botón del juego o de un mod, como si lo hiciera el jugador.

**Valor:** el [localizador del elemento](/widget-locators) del botón, por ejemplo, `title_screen:mc_titlescreen_options_button`

Para obtenerlo, haz clic derecho en el botón del editor y selecciona **Copiar localizador del elemento**.

## Diseños y elementos

### Alternar diseño

**Identificador:** `toggle_layout`

Desactiva un diseño si está activado y lo activa si está desactivado.

**Valor:** el nombre del diseño, sin `.txt`, por ejemplo, `winter_title_screen`

### Activar diseño

**Identificador:** `enable_layout`

Activa un diseño.

**Valor:** el nombre del diseño, sin `.txt`

### Desactivar diseño

**Identificador:** `disable_layout`

Desactiva un diseño.

**Valor:** el nombre del diseño, sin `.txt`

Las tres acciones de diseño guardan el cambio y actualizan el menú abierto de inmediato. Se distingue entre mayúsculas y minúsculas en el nombre.

### Alternar animador de elementos

**Identificador:** `toggle_element_animator`

Activa un [animador de elementos](/element-animator) si está desactivado y lo desactiva si está activado. La animación empieza desde el principio. El estado se guarda.

**Valor:** el identificador del animador de elementos

### Activar animador de elementos

**Identificador:** `enable_element_animator`

Activa un [animador de elementos](/element-animator). Si estaba desactivado, su animación empieza desde el principio.

**Valor:** el identificador del animador de elementos

### Desactivar animador de elementos

**Identificador:** `disable_element_animator`

Desactiva un [animador de elementos](/element-animator) y reinicia su animación.

**Valor:** el identificador del animador de elementos

### Reiniciar animador de elementos

**Identificador:** `reset_element_animator`

Inicia desde el principio la animación de un [animador de elementos](/element-animator), sin activarlo ni desactivarlo.

**Valor:** el identificador del animador de elementos

### Establecer valor del campo de entrada de texto

**Identificador:** `set_text_input_field_value`

Establece el texto de un [campo de entrada de texto](/elements#text-input-field), de FancyMenu o del juego.

**Valor:** `element_identifier|||text|||force`

Si `force` está establecido en `true`, el texto también cambia cuando el campo está desactivado (inactivo).

### Desplazar un elemento

**Identificador:** `scroll_scroll_area`

Desplaza un [área desplazable](/scrollable-areas) o un elemento de [texto](/elements#text). Se configura en su ventana:

- **Identificador del elemento que se va a desplazar**: el área o el texto que se va a desplazar.
- **Desplazar hasta**:
  - **Inicio** o **Final**.
  - **Posición**: la **Posición horizontal** y la **Posición vertical** en píxeles. Deja una sin rellenar para mantenerla.
  - **Elemento** (solo áreas): se desplaza hasta que el elemento con el **Identificador del elemento al que se va a desplazar** quede al principio.
  - **Número de línea** (solo textos): la primera línea es `1`.
  - **Línea con texto** (solo textos): la primera línea que contiene el **Texto de la línea**. No se distingue entre mayúsculas y minúsculas.
- **Desplazamiento suave**: se desplaza suavemente en lugar de saltar. El desplazamiento suave debe estar activado para el elemento.

No hace nada si el elemento no existe.

## Audio y vídeo

### Pista siguiente

**Identificador:** `audio_next_track`

Pasa a la siguiente pista de un [elemento de audio](/elements#audio).

**Valor:** el identificador del elemento de audio, por ejemplo, `menu_music`

### Pista anterior

**Identificador:** `audio_previous_track`

Vuelve a la pista anterior de un [elemento de audio](/elements#audio).

**Valor:** el identificador del elemento de audio

### Establecer volumen de la pista

**Identificador:** `set_audio_element_volume`

Establece el volumen de un [elemento de audio](/elements#audio), desde `0.0` (0 %) hasta `1.0` (100 %).

**Valor:** `element_identifier:volume`, por ejemplo, `menu_music:0.5`

### Alternar reproducción/pausa de la pista

**Identificador:** `audio_toggle_play`

Pausa un [elemento de audio](/elements#audio) que se esté reproduciendo o reproduce uno que esté en pausa.

**Valor:** el identificador del elemento de audio

### Reproducir audio

**Identificador:** `play_audio`

Reproduce una vez un archivo de audio, que se configura en su ventana: el **Origen del audio**, el **Canal de sonido** y el **Volumen base** (hasta el 100 %).

- FancyMenu espera hasta diez segundos a que se cargue el audio.
- No funciona en un [temporizador](/elements#ticker) que se ejecute en segundo plano (de forma asíncrona). En su lugar, FancyMenu muestra un error.

[**Detener todos los audios de acciones**](#stop-all-action-audios) detiene los audios iniciados con esta acción.

### Detener todos los audios de acciones

**Identificador:** `stop_all_action_audios`

Detiene todos los audios iniciados con [**Reproducir audio**](#play-audio). Los elementos de audio, los sonidos de los menús y los sonidos de los botones siguen reproduciéndose.

**Valor:** ninguno

### Establecer volumen del elemento de vídeo

**Identificador:** `set_video_element_volume`

Establece el volumen de un [elemento de vídeo](/video), desde `0.0` (0 %) hasta `1.0` (100 %).

**Valor:** `video_element_identifier:volume`

### Establecer tiempo de reproducción del elemento de vídeo

**Identificador:** `set_video_element_play_time`

Salta a un momento de un [elemento de vídeo](/video), en milisegundos.

**Valor:** `video_element_identifier:time_in_ms`, por ejemplo, `intro_video:30000`

### Alternar estado de pausa del elemento de vídeo

**Identificador:** `toggle_video_element_pause_state`

Pausa un [elemento de vídeo](/video) que se esté reproduciendo o reproduce uno que esté en pausa.

**Valor:** el identificador del elemento de vídeo

### Establecer volumen del fondo de vídeo

**Identificador:** `set_video_menu_background_volume`

Establece el volumen de un [fondo de menú de vídeo](/video), desde `0.0` (0 %) hasta `1.0` (100 %).

**Valor:** `background_identifier:volume`

> [!NOTE]
> Para obtener el identificador de un fondo de menú, haz clic derecho en el fondo del editor y selecciona **Copiar identificador del fondo**.

### Establecer tiempo de reproducción del fondo de vídeo

**Identificador:** `set_video_menu_background_play_time`

Salta a un momento de un [fondo de menú de vídeo](/video), en milisegundos.

**Valor:** `background_identifier:time_in_ms`

### Alternar estado de pausa del fondo de vídeo

**Identificador:** `toggle_video_menu_background_pause_state`

Pausa un [fondo de menú de vídeo](/video) que se esté reproduciendo o reproduce uno que esté en pausa.

**Valor:** el identificador del fondo del menú

## Mundos y servidores

### Conectarse a un servidor

**Identificador:** `joinserver`

Se conecta a un servidor de Minecraft.

**Valor:** `dirección` o `dirección:puerto`, por ejemplo, `play.example.net`

Si no se especifica un puerto, se usa `25565`. Si hay un mundo o servidor cargado, muestra un error. Los servidores que no están en la lista de servidores se añaden a ella.

### Entrar en un mundo

**Identificador:** `loadworld`

Carga un mundo de un jugador.

**Valor:** el nombre de la carpeta del mundo en `saves`, por ejemplo, `Survival Island`

No hace nada si el mundo no existe. Si hay un mundo o servidor cargado, muestra un error.

### Entrar en el último mundo/servidor

**Identificador:** `join_last_world`

Carga el mundo o se conecta al servidor en el que jugó el jugador por última vez.

**Valor:** ninguno

Si hay un mundo o servidor cargado, muestra un error. Los servidores que no están en la lista de servidores se añaden a ella.

### Salir del mundo o del servidor

**Identificador:** `disconnect_server_or_world`

Sale del mundo o del servidor y abre un menú.

**Valor:** el [identificador de pantalla](/screen-identifiers) del menú que se va a abrir, por ejemplo, `title_screen`

Solo funciona si hay un mundo cargado. También funciona con [interfaces gráficas personalizadas](/custom-guis). Si no se puede abrir el menú, se abre la pantalla del título.

## Chat y comandos

### Enviar mensaje/comando al chat

**Identificador:** `sendmessage`

Envía un mensaje al chat o ejecuta un comando, como si lo hubiera escrito el jugador.

**Valor:** el mensaje o un comando que empiece por `/`, por ejemplo, `/spawn`

### Ejecutar comando como servidor integrado

**Identificador:** `execute_command_as_integrated_server`

En un mundo de un jugador, ejecuta un comando como servidor, independientemente de los permisos del jugador o de si los trucos están activados.

**Valor:** el comando, por ejemplo, `/give @p minecraft:diamond 1`

> [!WARNING]
> Solo funciona en un mundo de un jugador que no esté abierto a la LAN. En cualquier otro caso, no hace nada.

### Pegar en el chat

**Identificador:** `paste_to_chat`

Introduce texto en el campo de entrada del chat mientras hay un mundo cargado. Si el chat no está abierto, lo abre con el texto.

**Valor:** `true:text` añade el texto a lo que ya está escrito; `false:text` lo sustituye

### Mostrar en el chat [del lado del cliente]

**Identificador:** `display_in_chat_client_side`

Muestra un mensaje de chat que solo ve este jugador. No se envía nada al servidor.

**Valor:** el texto, con [códigos de formato](/text-formatting#minecraft-text-formatting) o en formato JSON de componentes de texto de Minecraft, por ejemplo, `&a¡Bienvenido de nuevo!`

No hace nada si no hay ningún mundo cargado.

## Variables y listas

### Establecer valor de variable (variable de FM)

**Identificador:** `set_variable`

Establece una [variable](/variables).

**Valor:** `nombre_variable:valor`, por ejemplo, `coins:100`

- Solo el primer `:` separa el nombre del valor.
- Las [variables de lista](/variables#text-and-list-variables) siguen siendo listas: una matriz JSON como `["a","b"]` se convierte en sus elementos; cualquier otro texto se convierte en su único elemento, y el texto vacío vacía la lista.

### Eliminar variable (variable de FM)

**Identificador:** `delete_variable`

Elimina por completo una [variable](/variables). Las demás variables se conservan. Para vaciarla sin eliminarla, usa [**Establecer valor de variable (variable de FM)**](#set-variable-value-fm-variable).

**Valor:** el nombre de la variable

### Borrar todas las variables (variable de FM)

**Identificador:** `clear_variables`

Elimina todas las [variables](/variables), tanto de texto como de lista.

**Valor:** ninguno

### Añadir a la lista (variable de FM)

**Identificador:** `add_to_list`

Añade un elemento a una [variable de lista](/variables#list-actions).

- **Variable de lista**: el nombre de la lista. Si todavía no existe ninguna variable con ese nombre, la acción crea la lista.
- **Nuevo elemento**: el texto del elemento.
- **Índice (opcional)**: dónde se añade el elemento. Si se deja vacío, se añade al final. Los elementos a partir de esa posición se desplazan una posición.
- **Omitir si ya está en la lista**: no añade nada si la lista ya contiene un elemento con el mismo texto. **Ignorar mayúsculas y minúsculas** hace que `Apple` coincida con `apple`.

### Establecer elemento de la lista (variable de FM)

**Identificador:** `set_list_entry`

Sustituye el elemento del **Índice** indicado de una [variable de lista](/variables#list-actions) por un **Nuevo valor**. No hace nada si la lista no tiene ningún elemento en esa posición.

### Quitar de la lista (variable de FM)

**Identificador:** `remove_from_list`

Quita elementos de una [variable de lista](/variables#list-actions). **Quitar** permite elegir cuáles:

- **Elemento en el índice**: el elemento que ocupa un índice determinado.
- **Primera coincidencia**: el primer elemento cuyo texto coincide exactamente con el **Valor que se va a quitar**.
- **Todas las coincidencias**: todos los elementos que coincidan.

**Ignorar mayúsculas y minúsculas** hace que `Apple` coincida con `apple`.

### Vaciar lista (variable de FM)

**Identificador:** `clear_list`

Quita todos los elementos de una [variable de lista](/variables#list-actions). La lista vacía se conserva.

### Establecer lista (variable de FM)

**Identificador:** `set_list`

Sustituye todos los elementos de una [variable de lista](/variables#list-actions). **Obtener elementos de** permite elegir de dónde proceden:

- **Dividir texto**: divide el **Texto que se va a dividir** por el **Separador**, por ejemplo, `,`. Si el separador está vacío, divide el texto por saltos de línea. **Recortar elementos** elimina los espacios del principio y del final, y **Omitir elementos vacíos** excluye los elementos vacíos.
- **Matriz JSON**: usa los elementos de una matriz como `["Diamonds","Emeralds"]` o `$$other_list` para copiar otra lista. Cualquier otro texto se convierte en el único elemento y el texto vacío vacía la lista.

La ventana muestra una vista previa de los elementos.

### Ordenar lista (variable de FM)

**Identificador:** `arrange_list`

Cambia el orden de una [variable de lista](/variables#list-actions). **Orden**:

- **Orden alfabético A-Z** y **Orden alfabético Z-A**: ordena alfabéticamente.
- **Números, de menor a mayor** y **Números, de mayor a menor**: ordena por número. Los elementos que no sean números se colocan al final.
- **Orden inverso**: el último elemento pasa a ser el primero.
- **Aleatorio**: establece un orden aleatorio.
- **Eliminar duplicados**: conserva solo la primera aparición de cada valor.

En todas las acciones de lista, el índice del primer elemento es `0` y `-1` corresponde al último. El nombre de la lista puede contener marcadores de posición y, si se antepone `$$`, la acción usa el valor de esa variable como nombre de la lista. Si una variable de texto tiene un valor, se conserva tal cual y la acción escribe un aviso en el registro del juego.

## Web y redes

### Abrir URL en el navegador

**Identificador:** `openlink`

Abre un enlace en el navegador predeterminado sin pedir confirmación.

**Valor:** el enlace, por ejemplo, `https://discord.gg/example`

Usa únicamente enlaces de confianza.

### Enviar solicitud HTTP

**Identificador:** `send_http_request`

Envía una solicitud web en segundo plano. Puede escribir la respuesta en el registro del juego o guardarla en una variable.

| Ajuste | Qué hace |
|---|---|
| URL | La dirección HTTP o HTTPS. |
| Método | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` u `OPTIONS`. |
| Cuerpo | Los datos que se van a enviar. No se envía con `GET` ni `HEAD`. |
| Tipo de contenido | El `Content-Type` del cuerpo, por ejemplo, `application/json`. |
| Tiempo de espera | El tiempo en segundos que se espera a que se establezca la conexión y llegue la respuesta. |
| Registrar respuesta | Escribe la respuesta en el registro del juego. |
| Variable de respuesta | Guarda la respuesta en esta variable cuando llega. |
| Respuesta en una sola línea | Elimina los saltos de línea de la respuesta antes de guardarla. |
| Autenticación | Ninguna, Basic, Bearer o clave de API. |
| Cabeceras | Cabeceras adicionales de la solicitud. |

La acción siguiente no espera a que llegue la respuesta. Los errores de respuesta también se registran y se guardan. No incluyas contraseñas ni tokens de acceso en la acción: cualquiera que tenga el diseño podrá leerlos.

### Enviar datos de FM al servidor

**Identificador:** `send_fm_data_to_server`

Envía [datos de FM](/fm-data) al servidor, que también debe tener FancyMenu.

**Valor:** `data_identifier||data`

### Conectarse a un servidor remoto

**Identificador:** `connect_to_remote_server`

Se conecta a un servidor remoto o utiliza una conexión que ya esté abierta.

**Valor:** la dirección del servidor, por ejemplo, `wss://example.com/ws`

Consulta [Comunicación con servidores remotos](/remote-server-communication#url-modes) para ver las direcciones compatibles.

### Enviar datos a un servidor remoto

**Identificador:** `send_data_to_remote_server`

Envía texto a un servidor remoto y se conecta primero si es necesario.

**Valor:** `server_address||data`

### Cerrar conexión con un servidor remoto

**Identificador:** `close_remote_server_connection`

Cierra una conexión con un servidor remoto.

**Valor:** su ID de solicitud, que suele ser `$$request_id` de [**Al conectarse a un servidor remoto**](/listeners#on-remote-server-connected)

### Cerrar todas las conexiones con servidores remotos

**Identificador:** `close_all_remote_server_connections`

Cierra todas las conexiones con servidores remotos que haya abierto FancyMenu.

**Valor:** ninguno

## Archivos

### Crear archivo en la carpeta del juego

**Identificador:** `create_file_in_game_dir`

Crea un archivo vacío. También crea las carpetas que falten. Si el archivo ya existe, lo deja tal cual.

**Valor:** la ruta del archivo, por ejemplo, `config/mymodpack/first_start.txt`

Todas las acciones de archivos solo funcionan dentro de la carpeta del juego (la carpeta de la instancia). Las rutas que empiezan por `.minecraft/` utilizan la carpeta `.minecraft` predeterminada, que puede ser otra distinta.

### Eliminar archivo/carpeta de la carpeta del juego

**Identificador:** `delete_file_in_game_dir`

Elimina un archivo o una carpeta con todo su contenido.

**Valor:** la ruta, por ejemplo, `config/mymodpack/cache.txt`

Si la ruta termina en `*`, por ejemplo, `config/downloads/*`, elimina todos los archivos que haya directamente en esa carpeta, pero conserva la carpeta y las subcarpetas.

### Copiar archivo/carpeta en la carpeta del juego

**Identificador:** `copy_file_in_game_dir`

Copia un archivo o una carpeta con todo su contenido.

**Valor:** `origen||destino`, por ejemplo, `config/presets/default.json||config/mymod/settings.json`

- Si el origen termina en `*`, por ejemplo, `config/presets/*||config/mymod/`, copia todos los archivos que haya directamente en esa carpeta, pero no las subcarpetas. En ese caso, el destino es una carpeta y se crea si es necesario.
- No se sobrescribe nada: si el destino ya existe, la acción falla.

### Mover archivo/carpeta en la carpeta del juego

**Identificador:** `move_file_in_game_dir`

Mueve un archivo o una carpeta con todo su contenido.

**Valor:** `origen||destino`

Si el origen termina en `*`, funciona igual que en [**Copiar archivo/carpeta en la carpeta del juego**](#copy-filefolder-in-game-directory). No se sobrescribe nada.

### Cambiar nombre de archivo/carpeta en la carpeta del juego

**Identificador:** `rename_file_in_game_dir`

Cambia el nombre de un archivo o una carpeta. La acción falla si ya existe algo con el nuevo nombre.

**Valor:** `ruta||nuevo_nombre`, por ejemplo, `config/mymod/old_name.txt||new_name.txt`

### Descargar archivo a la carpeta del juego

**Identificador:** `download_file_to_game_dir`

Descarga un archivo en una carpeta, en segundo plano.

**Valor:** `url||carpeta_destino`, por ejemplo, `https://example.com/pack.zip||downloads`

- La segunda parte debe ser una carpeta, no un nombre de archivo. FancyMenu obtiene el nombre de la descarga o del enlace.
- Si ya existe un archivo con el mismo nombre, se sobrescribe.
- [**Al descargar un archivo mediante una acción**](/listeners#on-file-downloaded-via-action) se ejecuta cuando la descarga termina o falla. Si se completa correctamente, `$$target_file_path` contiene la ruta del archivo guardado.

### Extraer archivo ZIP en la carpeta del juego

**Identificador:** `extract_zip_file_in_game_dir`

Extrae un archivo ZIP en una carpeta, en segundo plano.

**Valor:** `ruta_zip||carpeta_destino`, por ejemplo, `downloads/pack.zip||resourcepacks/MyPack`

Los archivos con el mismo nombre se sustituyen y no se crea ninguna carpeta adicional con el nombre del ZIP. [**Al extraer un ZIP mediante una acción**](/listeners#on-zip-extracted-via-action) se ejecuta cuando termina. Extrae únicamente archivos ZIP de confianza.

### Abrir archivo/carpeta de la carpeta del juego

**Identificador:** `open_file_folder_in_game_dir`

Abre un archivo o una carpeta con el programa que el sistema tenga asociado.

**Valor:** la ruta, por ejemplo, `screenshots`

### Escribir archivo en la carpeta del juego

**Identificador:** `write_file_in_game_dir`

Escribe texto en un archivo. El archivo y sus carpetas se crean si es necesario.

**Valor:** `ruta|||texto|||añadir_al_final`, por ejemplo, `config/mymodpack/log.txt|||Se ha conectado al servidor\n|||true`

`\n` inicia una nueva línea. Si `append` está establecido en `true`, añade el texto al final del archivo; si está establecido en `false`, sustituye su contenido.

### Seleccionar archivo del sistema

**Identificador:** `select_file_to_game_dir`

Abre el selector de archivos del sistema y copia el archivo seleccionado en la carpeta del juego.

**Valor:** `ruta_destino|||nombre_filtro|||extensiones|||sobrescribir`, por ejemplo, `config/fancymenu/assets/background.png|||Images|||png;jpg|||true`

- `target_path` es la ruta completa de la copia, incluido el nombre del archivo.
- Separa las extensiones con `;` o `,`. Si no especificas extensiones, se puede seleccionar cualquier archivo.
- Si `overwrite` está establecido en `false`, la acción falla si el archivo ya existe.

[**Al seleccionar un archivo**](/listeners#on-file-selected) se ejecuta cuando se copia el archivo, se cancela el selector o se produce algún error.

## El juego y FancyMenu

### Salir de Minecraft

**Identificador:** `quitgame`

Cierra el juego.

**Valor:** ninguno

### Establecer opción de Minecraft

**Identificador:** `edit_minecraft_option`

Cambia una opción de Minecraft, como la distancia de renderizado o la escala de la interfaz.

**Valor:** `nombre_opción:valor`, por ejemplo, `renderDistance:12`

Consulta [Opciones de Minecraft](/minecraft-options) para ver los nombres de las opciones.

### Imitar una tecla

**Identificador:** `mimic_keybind`

Pulsa una tecla de Minecraft, como la de saltar o agacharse, y puede mantenerla pulsada.

**Valor:** `tecla|||mantener|||duración_ms`, por ejemplo, `key.jump|||false|||1000`

| Parte | Qué es |
|---|---|
| `keybind` | El ID de la tecla, por ejemplo, `key.jump` o `key.sneak`. |
| `hold` | `true` mantiene la tecla pulsada; `false` la pulsa una vez. |
| `duration_ms` | Cuánto tiempo se mantiene pulsada, en milisegundos. Si se omite, se usa `1000`. |

### Gestionar paquete de recursos

**Identificador:** `manage_resource_pack`

Activa o desactiva un paquete de recursos. Se configura en su ventana:

- **Paquete de recursos de destino**: el nombre del paquete tal como aparece en la pantalla Paquetes de recursos. No se distingue entre mayúsculas y minúsculas.
- **Modo de acción**: **Activar**, **Desactivar** o **Alternar**.
- **Recargar recursos**: recarga los paquetes de recursos justo después del cambio. Desactiva esta opción para recargarlos más tarde, por ejemplo, con [**Recargar paquetes de recursos**](#reload-resource-packs).

No se pueden desactivar los paquetes que necesita el juego.

### Recargar paquetes de recursos

**Identificador:** `reload_resource_packs`

Recarga los paquetes de recursos, como `F3 + T`. Durante los cinco segundos posteriores a una recarga, la acción no hace nada, para evitar que se repita una y otra vez.

**Valor:** ninguno

### Recargar FancyMenu

**Identificador:** `reloadmenu`

Vuelve a cargar los diseños, las [interfaces gráficas personalizadas](/custom-guis), los [panoramas](/panoramas), las [presentaciones](/slideshows), los ajustes y los archivos de FancyMenu. No vuelve a cargar los paquetes de recursos.

**Valor:** ninguno

> [!WARNING]
> La recarga tarda un momento. Úsala en un botón, nunca en un [temporizador](/elements#ticker) ni en una [escucha](/listeners) que se ejecute a menudo.

### Iniciar programador

**Identificador:** `start_scheduler`

Inicia un [programador](/schedulers).

**Valor:** el identificador del programador

### Detener programador

**Identificador:** `stop_scheduler`

Detiene un [programador](/schedulers).

**Valor:** el identificador del programador

### Copiar texto al portapapeles

**Identificador:** `copytoclipboard`

Copia texto al portapapeles.

**Valor:** el texto, por ejemplo, `play.example.net`

### Escribir en el registro del juego

**Identificador:** `print_to_log`

Escribe una línea en el registro del juego. Es útil para averiguar qué hace un script.

**Valor:** el texto
