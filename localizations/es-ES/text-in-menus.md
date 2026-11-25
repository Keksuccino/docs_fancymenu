---
title: Texto en los menús
description: >-
  Cómo mostrar texto en los menús con los elementos Text y Tooltip, y cómo
  aplicar estilos y desplazarse por él.
sourceBlobSha: 557734a5ca4e53d75045d7086642e9c561805b29
---
# Texto en los menús

FancyMenu tiene dos elementos para mostrar texto:

- **Text** muestra texto directamente en el menú, desde una sola línea hasta páginas largas con desplazamiento, como registros de cambios, normas o noticias.
- **Tooltip** muestra un cuadro de texto en una posición fija o junto al cursor, por ejemplo, al pasar el ratón por encima de un botón.

Ambos admiten [Markdown](/text-formatting) y [marcadores de posición](/placeholders), y comparten los mismos ajustes de aspecto y estilo.

<img width="800" alt="Edición de un elemento Text" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/text_editor_showcase.gif?raw=true">

> [!TIP]
> Esta página trata sobre los elementos y sus ajustes. Para saber todo lo que puedes escribir, como títulos, listas, enlaces y colores, consulta [Formato de texto](/text-formatting).

# Añadir texto

1. Abre un diseño en el editor de diseños.
2. Haz clic derecho en el fondo del editor y selecciona **New Element -> Text**.
3. Haz clic derecho en el nuevo elemento y selecciona **Text Content**.
4. Escribe el texto y haz clic en **Done**.

# Contenido del texto

## Modo de origen

Haz clic derecho en el elemento y configura **Source Mode**:

- **Direct**: escribes el texto directamente en el editor de texto.
- **Resource**: el texto procede de un archivo de texto. Haz clic en **Text Source** para elegir un archivo local de `<game-directory>/config/fancymenu/assets/`, una URL web o un archivo de un paquete de recursos. Consulta [Recursos](/resources).

Las fuentes web son ideales para contenido como registros de cambios o noticias, que siempre está actualizado y no requiere actualizar el modpack.

FancyMenu recuerda el contenido de los archivos y las fuentes web hasta que se cierra el juego. Para volver a cargarlo, recarga FancyMenu desde **menu bar -> Customization -> Reload FancyMenu**.

## Texto dinámico

El texto puede mostrar valores en tiempo real mediante [marcadores de posición](/placeholders), por ejemplo, `¡Te damos la bienvenida, {"placeholder":"playername"}!`. También puede mostrar los valores de las [variables](/variables). El texto se actualiza automáticamente cuando cambian esos valores.

## El editor de texto

Al hacer clic en **Text Content** se abre el editor de texto. Haz clic en **Placeholders**, en la esquina superior derecha, para consultar todos los marcadores de posición y añadirlos al texto.

### Atajos de formato

El editor de texto de los elementos Text y Tooltip incluye atajos para aplicar formatos habituales. En macOS, usa `Cmd` en lugar de `Ctrl`.

| Atajo | Función |
|---|---|
| `Ctrl + B` | Negrita |
| `Ctrl + I` | Cursiva |
| `Ctrl + U` | Subrayado |
| `Ctrl + L` | Alinear a la izquierda |
| `Ctrl + E` | Centrar |
| `Ctrl + R` | Alinear a la derecha |

- Selecciona primero el texto para darle formato. Pulsa el mismo atajo de nuevo para quitar el formato.
- Si no hay nada seleccionado, el atajo añade los caracteres de formato y coloca el cursor entre ellos, para que puedas seguir escribiendo.
- Los atajos de alineación funcionan en las líneas seleccionadas o en la línea donde está el cursor. Si pulsas `Ctrl + E` o `Ctrl + R` en líneas que ya tienen esa alineación, volverán a alinearse a la izquierda.
- Haz clic derecho en el editor y abre **Formatting** para ver todos estos atajos en un menú.

### Otros atajos

El mismo editor de texto se abre para la mayoría de los textos de FancyMenu, como los valores de las acciones y muchos ajustes de los elementos. Estos atajos funcionan en todos ellos. En macOS, usa `Cmd` en lugar de `Ctrl`.

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
| `Ctrl + Home` / `Ctrl + End` | Ir al principio o al final del texto |
| `Ctrl + G` | Ir a una línea: escribe su número y pulsa `Enter` |
| `Ctrl + S` | Equivale a **Done** |

Para consultar los atajos del editor de diseños, visita [Editor de diseños](/layout-editor#shortcuts).

# Aspecto y estilos

Haz clic derecho en el elemento y abre **Markdown** para cambiar el aspecto del texto.

## Aspectos

Un **Look** aplica de una vez todas las opciones de estilo del texto:

- **Pixel**: arte pixelado diseñado para la fuente de Minecraft, con colores cálidos, detalles dorados y marcadores dibujados a mano.
- **Classic**: el aspecto clásico de FancyMenu, con texto blanco, recuadros grises y líneas grises.
- **Neutral**: un aspecto limpio con los colores del tema actual de la interfaz de FancyMenu. Los colores se guardan con el elemento, por lo que no cambian aunque cambies de tema más adelante.

<img width="800" alt="Los tres aspectos de Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_looks.png?raw=true">

Los elementos nuevos empiezan con el aspecto Pixel. Los elementos de diseños antiguos conservan el aspecto Classic que ya tenían.

> [!NOTE]
> Al elegir un aspecto, se sustituyen los cambios de estilo que hayas hecho. ¿Has cambiado de idea? Deshazlo con `Ctrl + Z`.

## Opciones de estilo

Después de elegir un aspecto, puedes ajustar cada uno de sus elementos. El menú **Markdown** incluye opciones para **Text**, **Headlines**, **Lists**, **Links**, **Code**, **Quotes**, **Callouts**, **Tables**, **Images** y **Separators**. Pasa el cursor por una opción para ver qué hace.

En **Markdown -> Text** encontrarás los ajustes básicos, como el color del texto, la sombra, el espaciado entre líneas y el margen entre el texto y los bordes del elemento.

## Desactivar Markdown

Si no necesitas Markdown, desactiva **Markdown -> Markdown Parser**. El texto se mostrará exactamente como lo hayas escrito y, además, el proceso será algo más rápido con textos muy largos.

## Otros ajustes de texto

Haz clic derecho en el elemento para encontrar también estos ajustes:

- **Text Scale** aumenta o reduce el tamaño del texto.
- **Case Mode** muestra el texto tal cual, en mayúsculas o en minúsculas.
- **Auto Line Wrapping** ajusta las líneas que son demasiado largas para el elemento. Si está desactivado, las líneas largas continúan sin ajustarse.
- **Remove HTML Line Breaks** elimina los saltos de línea HTML (`<br>`) del texto, algo útil para el texto procedente de páginas web.

# Fondo

Los elementos Text pueden dibujar un panel detrás del texto. Abre **Background** en el menú contextual del elemento:

- **Show Background** activa o desactiva el panel. Está activado en los elementos Text nuevos.
- De forma predeterminada, se usa un panel oscuro integrado. Puedes usar tu propia textura y aplicar [división en nueve partes](/nine-slicing-and-tiling) y mosaico para conservar la forma de los bordes.
- **Padding** define cuánto sobresale el fondo alrededor del texto.
- **Reach Behind Scroll Bars** permite que el fondo cubra también las barras de desplazamiento. Si está desactivado, las barras quedan justo al lado del fondo.

Los elementos Tooltip tienen su propio menú **Background**, donde puedes configurar una textura y su división en nueve partes.

# Desplazamiento

Un elemento Text se desplaza cuando el texto no cabe en él. Usa la rueda del ratón para desplazarte. Mantén pulsada la tecla `Shift` para desplazarte horizontalmente.

**Scroll Direction** define si el texto se desplaza en vertical (**Vertical**), en horizontal (**Horizontal**) o en ambas direcciones (**Both**). En las direcciones en las que no haya desplazamiento, se recortará todo lo que no quepa.

## Ajustes de desplazamiento

Abre **Scrolling** en el menú contextual del elemento:

| Ajuste | Función |
|---|---|
| **Let Players Scroll** | Permite que los jugadores se desplacen por el texto. Si está desactivado, el texto solo se desplaza automáticamente o mediante acciones. |
| **Scroll Speed** | Distancia que avanza el texto con cada paso de la rueda del ratón. |
| **Smooth Scrolling** | Hace que el texto se desplace suavemente en lugar de dar saltos. |
| **Drag to Scroll** | Permite que los jugadores agarren el texto con el ratón y lo arrastren, como en una pantalla táctil. |
| **Scroll with Keyboard** | Cuando el cursor está sobre el texto, `Page Up` y `Page Down` desplazan una página, y `Home` y `End` van al principio y al final. |
| **Snap** | Determina dónde se detiene el texto: en cualquier punto (**Off**), con una línea completa en la parte superior (**To Lines**), con un título en la parte superior (**To Headlines**) o avanzando una página entera cada vez (**To Pages**). |
| **Start At** | Determina si el texto empieza por el principio (**Start**) o por el final (**End**). El final es útil para cosas como los registros, donde lo más reciente aparece abajo. |
| **Reset When Screen Opens** | Devuelve el texto al principio cada vez que se abre la pantalla. Si está desactivado, el texto recuerda hasta dónde se había desplazado hasta que se cierre el juego. |

## Desplazamiento automático

Abre **Auto-Scroll** para que el texto se desplace lentamente por sí solo, como los créditos o un teletipo de noticias:

- **Scroll on Its Own** activa el desplazamiento automático.
- **Speed [Pixels per Second]** define la velocidad de desplazamiento.
- **Start Over at the End** vuelve a empezar desde arriba al llegar al final.
- **Pause While Hovered** detiene el desplazamiento mientras el cursor está sobre el texto, para que los jugadores puedan leer tranquilamente.

## Barras de desplazamiento

Abre **Scroll Bars** para cambiar las barras:

- **Show** determina cuándo se muestran: **Always**, solo **While Scrolling** o **Never**. Aunque elijas **Never**, la rueda del ratón seguirá desplazando el texto.
- **Thickness** define el grosor de las barras.
- **Vertical Bar on the Left** y **Horizontal Bar on Top** colocan las barras en el lado opuesto.
- **Scroll Grabber Style** elige el aspecto de los controles deslizantes: **Theme Bar** (con los colores del tema actual de la interfaz de FancyMenu) o **Pixel Handle** (arte pixelado que combina muy bien con el aspecto Pixel).
- **Scroll Grabber Textures** y **Scroll Grabber Color [HEX]** sustituyen los controles deslizantes por tus propias texturas o colores.
- **Scroll Bar Backgrounds** añade texturas detrás de los controles deslizantes, a lo largo de su recorrido.

## Desplazamiento con acciones

También puedes controlar y consultar el desplazamiento desde otras partes de FancyMenu:

- La [acción](/action-scripts) **Scroll an Element** desplaza un elemento Text hasta el principio, el final, una posición, un número de línea o la primera línea que contenga un texto determinado.
- Los [marcadores de posición](/placeholders) **Element Scroll Position**, **Element Scroll Percent** y **Element Scroll Content Size** indican cuánto se ha desplazado el texto y cuál es su tamaño.
- El [requisito](/conditions) **Is Element Scrolled to End** comprueba si el texto ha llegado al final. Por ejemplo, permite activar un botón «Aceptar» solo después de que se hayan leído las normas.
- Los [listeners](/listeners) **On Element Scrolled**, **On Element Scrolled to Start** y **On Element Scrolled to End** ejecutan acciones mientras el texto se desplaza.

Todos estos ajustes necesitan el [identificador del elemento](/element-identifiers) Text.

# Interacción con elementos Text

Los elementos Text reaccionan al ratón para que funcionen sus enlaces y barras de desplazamiento. Esto también significa que interceptan los clics, así que es posible que los botones situados detrás o delante de un elemento Text no los reciban.

Si esto supone un problema, haz clic derecho en el elemento Text y desactiva **Interactable**. Entonces ya no se podrá desplazar el texto ni hacer clic en sus enlaces.

# Tooltips

Los elementos Tooltip funcionan como los elementos Text, pero sin desplazamiento:

- Sus ajustes de texto, aspecto y estilo son los mismos que los de los elementos Text.
- **Follow Mouse** hace que el tooltip siga al cursor.
- Usa [requisitos](/conditions) para decidir cuándo se muestra el tooltip, como el requisito [**Is Element Hovered**](/conditions#is-element-hovered), que lo muestra al pasar el cursor por encima de un botón.
