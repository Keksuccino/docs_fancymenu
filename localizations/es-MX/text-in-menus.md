---
title: Texto en los menús
description: >-
  Cómo mostrar texto en los menús con los elementos Texto y Tooltip, y cómo
  darle estilo y desplazarte por él.
sourceBlobSha: 557734a5ca4e53d75045d7086642e9c561805b29
---
# Texto en los menús

FancyMenu tiene dos elementos para mostrar texto:

- **Texto** muestra texto directamente en tu menú, desde una sola línea hasta páginas largas con desplazamiento, como registros de cambios, reglas o noticias.
- **Tooltip** muestra un cuadro de texto en una posición fija o junto al cursor, por ejemplo, al pasar el cursor sobre un botón.

Ambos admiten [Markdown](/text-formatting) y [marcadores de posición](/placeholders), y comparten las mismas opciones de apariencia y estilo.

<img width="800" alt="Edición de un elemento Texto" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/text_editor_showcase.gif?raw=true">

> [!TIP]
> Esta página trata sobre los elementos y sus opciones. Para ver todo lo que puedes escribir, como encabezados, listas, enlaces y colores, consulta [Formato de texto](/text-formatting).

# Agregar texto

1. Abre un diseño en el editor de diseños.
2. Haz clic derecho en el fondo del editor y selecciona **New Element -> Text**.
3. Haz clic derecho en el elemento nuevo y selecciona **Text Content**.
4. Escribe el texto y haz clic en **Done**.

# Contenido de texto

## Modo de origen

Haz clic derecho en el elemento y configura **Source Mode**:

- **Direct**: Escribes el texto directamente en el editor de texto.
- **Resource**: El texto proviene de un archivo de texto. Haz clic en **Text Source** para elegir un archivo local de `<game-directory>/config/fancymenu/assets/`, una URL web o un archivo de un paquete de recursos. Consulta [Recursos](/resources).

Las fuentes web son muy útiles para mantener actualizados elementos como registros de cambios o noticias, sin tener que actualizar tu modpack.

FancyMenu conserva el texto de los archivos y las fuentes web hasta que se cierra el juego. Para volver a cargarlo, recarga FancyMenu desde **menu bar -> Customization -> Reload FancyMenu**.

## Texto dinámico

El texto puede mostrar valores en tiempo real con [marcadores de posición](/placeholders), por ejemplo, `¡Te damos la bienvenida, {"placeholder":"playername"}!`. También puede mostrar los valores de las [variables](/variables). El texto se actualiza automáticamente cuando cambian estos valores.

## El editor de texto

Al hacer clic en **Text Content**, se abre el editor de texto. Haz clic en **Placeholders**, en la esquina superior derecha, para explorar todos los marcadores de posición y agregarlos al texto.

### Atajos de formato

El editor de texto de los elementos Texto y Tooltip incluye atajos para aplicar formatos comunes. En macOS, usa `Cmd` en lugar de `Ctrl`.

| Atajo | Función |
|---|---|
| `Ctrl + B` | Negrita |
| `Ctrl + I` | Cursiva |
| `Ctrl + U` | Subrayado |
| `Ctrl + L` | Alinear a la izquierda |
| `Ctrl + E` | Centrar |
| `Ctrl + R` | Alinear a la derecha |

- Primero selecciona el texto al que quieras dar formato. Presiona el mismo atajo otra vez para quitar el formato.
- Si no hay texto seleccionado, el atajo agrega los caracteres de formato y coloca el cursor entre ellos, para que puedas seguir escribiendo.
- Los atajos de alineación se aplican a las líneas seleccionadas o a la línea donde está el cursor. Si usas `Ctrl + E` o `Ctrl + R` en líneas que ya tienen esa alineación, volverán a alinearse a la izquierda.
- Haz clic derecho en el editor y abre **Formatting** para ver todos estos atajos en un menú.

### Otros atajos

El mismo editor de texto se abre para la mayoría de los textos de FancyMenu, como los valores de las acciones y muchas opciones de los elementos. Estos atajos funcionan en todos ellos. En macOS, usa `Cmd` en lugar de `Ctrl`.

| Atajo | Función |
|---|---|
| `Ctrl + C` | Copiar el texto seleccionado |
| `Ctrl + X` | Cortar el texto seleccionado |
| `Ctrl + V` | Pegar |
| `Ctrl + A` | Seleccionar todo el texto |
| `Ctrl + Z` | Deshacer |
| `Ctrl + Y` | Rehacer |
| `Ctrl + D` | Duplicar la línea donde está el cursor |
| `Alt + Flecha arriba` / `Alt + Flecha abajo` | Mover hacia arriba o abajo la línea donde está el cursor |
| `Shift + Teclas de flecha` | Seleccionar texto |
| `Ctrl + Home` / `Ctrl + End` | Ir al inicio o al final del texto |
| `Ctrl + G` | Ir a una línea: escribe su número y presiona `Enter` |
| `Ctrl + S` | Equivale a **Done** |

Para consultar los atajos del editor de diseños, ve a [Editor de diseños](/layout-editor#shortcuts).

# Apariencia y estilos

Haz clic derecho en el elemento y abre **Markdown** para cambiar la apariencia del texto.

## Apariencias

Una **apariencia** aplica de una sola vez todas las opciones de estilo del texto:

- **Pixel**: Estilo de pixel art pensado para la fuente de Minecraft, con colores cálidos, detalles dorados y marcadores dibujados a mano.
- **Classic**: La apariencia clásica de FancyMenu, con texto blanco, cuadros grises y líneas grises.
- **Neutral**: Una apariencia limpia con los colores del tema actual de la interfaz de FancyMenu. Los colores se guardan con el elemento, así que no cambian si después cambias de tema.

<img width="800" alt="Las tres apariencias de Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_looks.png?raw=true">

Los elementos nuevos usan la apariencia Pixel. Los elementos de diseños anteriores conservan la apariencia Classic que siempre han tenido.

> [!NOTE]
> Al elegir una apariencia, se reemplazan los cambios de estilo que hayas hecho. ¿Cambiaste de opinión? Deshaz el cambio con `Ctrl + Z`.

## Opciones de estilo

Después de elegir una apariencia, puedes ajustar cada uno de sus aspectos. El menú **Markdown** incluye opciones para **Text**, **Headlines**, **Lists**, **Links**, **Code**, **Quotes**, **Callouts**, **Tables**, **Images** y **Separators**. Pasa el cursor sobre una opción para ver qué hace.

En **Markdown -> Text** encontrarás opciones básicas, como el color del texto, la sombra, el espaciado entre líneas y el margen entre el texto y los bordes del elemento.

## Desactivar Markdown

Si no necesitas Markdown, desactiva **Markdown -> Markdown Parser**. El texto se mostrará exactamente como lo escribiste. Esto también puede hacer que los textos muy largos se procesen un poco más rápido.

## Otras opciones de texto

Haz clic derecho en el elemento para encontrar también estas opciones:

- **Text Scale** aumenta o reduce el tamaño del texto.
- **Case Mode** muestra el texto normalmente, todo en mayúsculas o todo en minúsculas.
- **Auto Line Wrapping** ajusta las líneas demasiado largas al ancho del elemento. Si está desactivado, las líneas largas continúan sin ajustarse.
- **Remove HTML Line Breaks** quita del texto los saltos de línea HTML (`<br>`). Es útil para texto proveniente de sitios web.

# Fondo

Los elementos Texto pueden mostrar un panel detrás del texto. Abre **Background** desde el menú contextual del elemento:

- **Show Background** activa o desactiva el panel. Está activado de forma predeterminada en los elementos Texto nuevos.
- De forma predeterminada, se usa un panel oscuro integrado. Puedes usar una textura propia y aplicar [división en nueve partes](/nine-slicing-and-tiling) y mosaico para conservar la forma de los bordes.
- **Padding** define cuánto sobresale el fondo alrededor del texto.
- **Reach Behind Scroll Bars** permite que el fondo cubra también las barras de desplazamiento. Si está desactivado, las barras quedan justo junto al fondo.

Los tooltips tienen su propio menú **Background**, donde puedes configurar una textura y su división en nueve partes.

# Desplazamiento

Un elemento Texto permite desplazarse cuando el texto no cabe dentro de él. Usa la rueda del mouse para desplazarte. Mantén presionada la tecla `Shift` para desplazarte horizontalmente.

**Scroll Direction** define si el texto se desplaza **Vertical**, **Horizontal** o en **Both** direcciones. En la dirección que no se desplace, se recortará todo lo que no quepa.

## Opciones de desplazamiento

Abre **Scrolling** desde el menú contextual del elemento:

| Opción | Función |
|---|---|
| **Let Players Scroll** | Define si los jugadores pueden desplazarse por el texto. Si está desactivada, el texto solo se desplaza automáticamente o mediante acciones. |
| **Scroll Speed** | Define cuánto se desplaza el texto con cada movimiento de la rueda del mouse. |
| **Smooth Scrolling** | Hace que el texto se desplace de manera fluida en lugar de dar saltos. |
| **Drag to Scroll** | Permite que los jugadores arrastren el texto con el mouse, como en una pantalla táctil. |
| **Scroll with Keyboard** | Cuando el cursor está sobre el texto, `Page Up` y `Page Down` desplazan una página, mientras que `Home` y `End` saltan al inicio y al final. |
| **Snap** | Define dónde se detiene el texto: en cualquier lugar (**Off**), con una línea completa en la parte superior (**To Lines**), con un encabezado en la parte superior (**To Headlines**) o al completar una página (**To Pages**). |
| **Start At** | Define si el texto empieza en el **Start** o en el **End**. El final es útil para elementos como los registros, donde lo más reciente aparece al final. |
| **Reset When Screen Opens** | Devuelve el texto al inicio cada vez que se abre la pantalla. Si está desactivada, el texto conserva su posición hasta que se cierra el juego. |

## Desplazamiento automático

Abre **Auto-Scroll** para que el texto se desplace lentamente por sí solo, como los créditos o un cintillo de noticias:

- **Scroll on Its Own** activa el desplazamiento automático.
- **Speed [Pixels per Second]** define la velocidad de desplazamiento.
- **Start Over at the End** vuelve a empezar desde arriba al llegar al final.
- **Pause While Hovered** detiene el desplazamiento cuando el cursor está sobre el texto, para que los jugadores puedan leer con calma.

## Barras de desplazamiento

Abre **Scroll Bars** para cambiar las barras:

- **Show** define cuándo aparecen las barras: **Always**, solo **While Scrolling** o **Never**. Si eliges **Never**, la rueda del mouse seguirá permitiendo desplazarte.
- **Thickness** define el grosor de las barras.
- **Vertical Bar on the Left** y **Horizontal Bar on Top** mueven las barras al lado opuesto.
- **Scroll Grabber Style** elige la apariencia de los controles deslizantes: **Theme Bar** (con los colores del tema actual de la interfaz de FancyMenu) o **Pixel Handle** (pixel art que combina muy bien con la apariencia Pixel).
- **Scroll Grabber Textures** y **Scroll Grabber Color [HEX]** reemplazan los controles deslizantes por texturas o colores propios.
- **Scroll Bar Backgrounds** agrega texturas detrás de los controles deslizantes, a lo largo de su recorrido.

## Controlar el desplazamiento con acciones

También puedes controlar y consultar el desplazamiento desde otras partes de FancyMenu:

- La [acción](/action-scripts) **Scroll an Element** desplaza un elemento Texto hasta el inicio, el final, una posición, un número de línea o la primera línea que contenga cierto texto.
- Los [marcadores de posición](/placeholders) **Element Scroll Position**, **Element Scroll Percent** y **Element Scroll Content Size** indican qué tanto se ha desplazado el texto y cuál es su tamaño.
- El [requisito](/conditions) **Is Element Scrolled to End** comprueba si el texto llegó al final. Por ejemplo, puedes usarlo para activar un botón «Aceptar» solo después de que se hayan leído las reglas.
- Los [listeners](/listeners) **On Element Scrolled**, **On Element Scrolled to Start** y **On Element Scrolled to End** ejecutan acciones mientras el texto se desplaza.

Todos estos necesitan el [identificador del elemento](/element-identifiers) del elemento Texto.

# Permitir hacer clic a través de los elementos Texto

Los elementos Texto responden al mouse para que funcionen sus enlaces y barras de desplazamiento. Esto también significa que capturan los clics, así que es posible que no puedas hacer clic en los botones que estén detrás o delante de un elemento Texto.

Si esto causa problemas, haz clic derecho en el elemento Texto y desactiva **Interactable**. Ya no podrás desplazarte por el texto ni hacer clic en sus enlaces.

# Tooltips

Los elementos Tooltip funcionan como los elementos Texto, pero sin desplazamiento:

- Sus opciones de texto, apariencia y estilo son las mismas que las de los elementos Texto.
- **Follow Mouse** hace que el tooltip siga al cursor.
- Usa [requisitos](/conditions) para decidir cuándo aparece el tooltip, como el requisito [**Is Element Hovered**](/conditions#is-element-hovered) para mostrarlo cuando el cursor está sobre un botón.
