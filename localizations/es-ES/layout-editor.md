---
title: Editor de diseños
description: >-
  Cómo abrir el editor de diseños, seleccionar, mover y cambiar el tamaño de los
  elementos, ordenarlos con capas y grupos, guardar el diseño y consultar todos
  los atajos del editor.
sourceBlobSha: c247d44a67ac209f2a0b638cb4748b408c7e7b13
---

# Editor de diseños

El editor de diseños es donde creas [diseños](/home#your-first-layout): añades elementos, los mueves y cambias su tamaño, y modificas el menú que los rodea. Muestra el menú tal y como lo ven los jugadores, para que veas enseguida qué aspecto tiene.

<img width="800" alt="Mover, ensanchar y ajustar un título; después, seleccionar dos botones, copiarlos y pegarlos, arrastrar las copias hacia abajo y deshacer el cambio" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_basics.gif?raw=true">

# Abrir el editor

1. Abre el menú que quieras modificar, como la pantalla del título.
2. Haz clic en **Barra de menú -> Personalización -> Personalización de la pantalla actual**, hasta que aparezca **Activado**.
3. Haz clic en **Barra de menú -> Personalización -> Diseños -> Nuevo -> Para la pantalla actual**.

- **Para todas las pantallas [Universal]** crea un [diseño universal](/universal-layouts), que se muestra en todos los menús.
- Los diseños que ya tengas también aparecen en **Diseños**. Pasa el cursor por encima de uno y haz clic en **Editar diseño**.
- En cualquier menú, `Ctrl + Alt + L` abre el último diseño que editaste. Consulta [los atajos de la barra de menú](/home#menu-bar-shortcuts).

# Vista general del editor

<img width="800" alt="El editor de diseños con un botón Unirse al servidor seleccionado, la barra de menú en la parte superior y el panel Capas a la derecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Haz clic derecho en el fondo para acceder a la configuración de todo el diseño y añadir elementos con **Nuevo elemento**.
- Haz clic derecho en un elemento para acceder a su configuración. Consulta [Elementos](/elements#settings-of-all-elements).
- **Capas**, a la derecha, muestra todos los elementos del diseño. Consulta [Capas y grupos](#layers-and-groups).
- La barra de menú de la parte superior:

| Menú | Contenido |
|---|---|
| **Diseño** | **Nuevo**, **Abrir**, **Guardar**, **Guardar como**, **Exportar diseño para IA**, **Propiedades del diseño** (lo mismo que el menú contextual del fondo), **Configuración** y **Cerrar editor** |
| **Edición** | **Deshacer**, **Rehacer**, **Copiar**, **Pegar** y **Seleccionar todo** |
| **Elemento** | **Nuevo** para añadir elementos y **Elementos vanilla eliminados** para recuperar [elementos vanilla que hayas eliminado](/deleted-vanilla-elements) |
| **Ventana** | **Widgets del editor**, la [cuadrícula](#grid-and-anchor-overlay), la [superposición de anclajes](#grid-and-anchor-overlay), **Controles de rotación de elementos** y **Controles de inclinación de elementos** |

## Configuración del diseño

El menú contextual del fondo contiene todo lo relacionado con el propio diseño, como:

- [**Fondos de menú**](/menu-backgrounds) y [**Superposiciones decorativas**](/decoration-overlays)
- **Título de pantalla personalizado** para el texto de la parte superior de algunos menús, como «Opciones». Puedes usar [marcadores de posición](/placeholders).
- **Personalizaciones de encabezado y pie de página** para [pantallas con desplazamiento](/customizing-scrollable-screens)
- **Índice del diseño [Orden de varios diseños]** y **Modo aleatorio** para [usar varios diseños en un mismo menú](/randomize-layouts)
- **Requisitos de carga [para todo el diseño]**, consulta [Requisitos](/conditions#layout-wide-requirements)
- **Editar el script de acción «Abrir pantalla»** y **Editar el script de acción «Cerrar pantalla»**, consulta [Scripts de acción](/action-scripts)
- **Opciones de diseño universal**, solo en [diseños universales](/universal-layouts)

# Trabajar con elementos

## Seleccionar

- Haz clic en un elemento para seleccionarlo. Haz clic en el fondo para anular todas las selecciones.
- Arrastra sobre el fondo para seleccionar todos los elementos dentro del rectángulo.
- `Ctrl` + clic añade un elemento a la selección o lo quita si ya estaba seleccionado.
- `Ctrl + A` selecciona todos los elementos.

Los clics, los rectángulos y `Ctrl + A` omiten los elementos que hayas [ocultado en Capas](#hiding-and-renaming).

## Mover

- Arrastra un elemento para moverlo. Para mover varios elementos seleccionados, mantén pulsado `Ctrl` mientras empiezas a arrastrarlos. Si no pulsas `Ctrl`, el clic selecciona solo el elemento sobre el que has hecho clic.
- Las teclas de flecha mueven los elementos seleccionados un píxel.
- Al arrastrar, se muestran los puntos de anclaje. Mantén el elemento sobre otro punto de anclaje o elemento para anclarlo allí. Consulta [Colocar elementos](/positioning-elements).
- Suelta un elemento sobre un [área desplazable](/scrollable-areas) para colocarlo dentro.

## Cambiar el tamaño

Arrastra un borde o una esquina de un elemento seleccionado. Mantén pulsada la tecla `Shift` para conservar la proporción.

Solo se puede cambiar el tamaño cuando hay un único elemento seleccionado.

## Girar e inclinar

Los elementos seleccionados que lo admiten muestran controles para [girarlos e inclinarlos](/rotating-elements). Mantén pulsada la tecla `Shift` mientras los arrastras para ajustarlos en incrementos: 45° para el giro y 15° para la inclinación.

Las opciones **Ventana -> Controles de rotación de elementos** y **Controles de inclinación de elementos** ocultan los controles.

## Copiar, pegar y eliminar

- `Ctrl + C` copia los elementos seleccionados y `Ctrl + V` los pega. Las copias aparecen encima de los originales y quedan seleccionadas, así que puedes arrastrarlas a otro sitio directamente.
- También puedes pegarlas en otro diseño, siempre que no cierres el juego.
- `Delete` elimina los elementos seleccionados. Los elementos vanilla solo se ocultan: puedes recuperarlos con **Elemento -> Elementos vanilla eliminados**.
- Al eliminar un área desplazable, se te preguntará si también quieres eliminar su contenido o si prefieres dejarlo en el diseño.

## Deshacer y rehacer

`Ctrl + Z` deshace el último cambio y `Ctrl + Y` lo vuelve a aplicar. Ambas opciones también están en el menú **Edición**.

## Elementos invisibles

Los jugadores no pueden ver los elementos [Audio](/elements#audio), [Arrastrador](/dragger), [Animador de elementos](/element-animator), [Controlador de música](/elements#music-controller) y [Ticker](/elements#ticker). En el editor aparecen como recuadros de colores con su nombre para que puedas encontrarlos, moverlos y cambiarles el tamaño.

- **Color en el editor**, en su menú contextual, cambia el color del recuadro; por ejemplo, para distinguir varios Ticker. Los colores se indican como `#RRGGBB` o `#RRGGBBAA` si tienen transparencia: un color semitransparente como `#E30E2366` deja ver lo que hay detrás del recuadro.
- El nombre del recuadro es el nombre de capa del elemento; consulta [Ocultar y cambiar el nombre](#hiding-and-renaming).

Los jugadores nunca ven el recuadro, su color ni su nombre.

# Capas y grupos

**Capas** muestra todos los elementos del diseño, empezando por el que está más arriba: un elemento aparece delante de todos los que están por debajo en la lista. **Ventana -> Widgets del editor -> Capas** muestra u oculta este panel.

<img width="800" alt="Arrastrar la capa Fondo de noticias debajo de Texto de noticias para que aparezcan las notas del parche al anular la selección; después, añadir un grupo, colocar ambas capas dentro, ocultar y mostrar el grupo con el icono del ojo y contraerlo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_layers.gif?raw=true">

## Cambiar el orden

- Haz clic en una capa para seleccionar su elemento y arrástrala hacia arriba o hacia abajo. Una línea indica dónde quedará. Todas las capas seleccionadas se mueven juntas.
- También puedes hacer clic derecho en un elemento o en su capa y seleccionar **Subir una capa** o **Bajar una capa**.

En el editor, los elementos seleccionados siempre aparecen delante de los demás. Anula su selección para ver el orden real.

En algunas versiones de Minecraft, los elementos [Entidad de jugador](/elements#player-entity) y [Objeto](/elements#item) aparecen delante de todo, independientemente de la capa en la que estén. Consulta [Problemas conocidos](/known-issues#1-player-entity--item-elements-are-always-in-front-of-everything).

## Elementos vanilla

La fila **Elementos vanilla** representa todos los elementos del propio menú, como sus botones. No se puede cambiar su orden, pero el botón situado a la derecha de la fila coloca todos tus elementos detrás o delante de ellos. Hace lo mismo que **Elementos personalizados detrás de los vanilla**, en el menú contextual del fondo.

## Ocultar y cambiar el nombre

- El icono del ojo de una capa oculta su elemento en el editor para que no estorbe mientras trabajas con los demás. Vuelve a hacer clic en él para mostrar el elemento.
- No se puede hacer clic en los elementos ocultos, ni moverlos, copiarlos o eliminarlos. Los jugadores siguen viéndolos; solo están ocultos en el editor. El diseño recuerda cuáles has ocultado.
- Haz clic derecho en una capa y selecciona **Cambiar nombre de capa** para asignarle un nombre más fácil de reconocer, como `Panel de noticias`. Es lo mismo que el **Nombre para mostrar en el editor** del elemento, y los jugadores no lo ven.

## Grupos

Los grupos reúnen capas relacionadas bajo un mismo nombre, como todas las partes de un panel de noticias. Solo sirven para organizar la lista: los elementos se muestran y funcionan como antes.

- Haz clic derecho dentro de Capas y selecciona **Añadir grupo**. El grupo aparecerá debajo de las capas.
- Arrastra capas al grupo para incluirlas. Arrástralas fuera para quitarlas.
- Haz clic en un grupo para seleccionar todos sus elementos. Arrástralo para moverlos todos hacia arriba o hacia abajo a la vez.
- La flecha de un grupo contrae o despliega sus capas, y el icono del ojo las oculta o las muestra todas.
- Haz clic derecho en un grupo para cambiarle el nombre, subirlo o bajarlo una capa, o eliminarlo. **Eliminar grupo** conserva sus elementos.

**Subir una capa** y **Bajar una capa** mantienen el elemento dentro de su grupo. Para sacarlo, arrastra su capa fuera del grupo.

El diseño guarda los grupos y cuáles están contraídos.

## Áreas desplazables

Los elementos de un [área desplazable](/scrollable-areas) aparecen debajo de la capa del área, con sangría.

- Arrastra una capa hasta la mitad inferior de la capa de un área para incluir el elemento en ella. Arrástrala fuera, entre otras capas, para sacarla. El elemento no cambia de posición en la pantalla.
- La flecha de la capa de un área contrae o despliega sus elementos.
- Los elementos de un área no pertenecen a ningún grupo. Se mueven junto con el área.

# Cuadrícula y superposición de anclajes

El menú **Ventana** contiene la configuración de las ayudas del editor:

- **Cuadrícula** muestra las líneas de la cuadrícula; `Ctrl + G` las activa o desactiva. **Tamaño de la cuadrícula** define la distancia entre ellas.
- **Ajustar a la cuadrícula** hace que un elemento arrastrado se ajuste a las líneas mientras la cuadrícula está visible. **Intensidad del ajuste a la cuadrícula** define la fuerza del ajuste.
- **Visibilidad de la superposición de anclajes** determina cuándo se muestran los puntos de anclaje:
  - **Mostrar al arrastrar elementos**: mientras arrastras elementos.
  - **Siempre visible**: en todo momento.
  - **Mostrar al pulsar una tecla (tecla «O»)**: mientras mantienes pulsada `O`.
  - **Desactivado**: nunca.
- **Anclaje al pasar sobre un área** determina si mantener un elemento sobre un punto de anclaje cambia su anclaje. **Anclaje al pasar sobre un elemento** añade otros elementos a los puntos de anclaje, por lo que esta opción solo funciona si **Anclaje al pasar sobre un área** también está activado.

# Guardar y cerrar

- `Ctrl + S` o **Diseño -> Guardar** guarda el diseño. La primera vez, FancyMenu te pide un nombre de archivo.
- **Diseño -> Guardar como** guarda el diseño en un archivo nuevo.
- Mientras haya cambios sin guardar, la barra de menú mostrará **\* ¡Cambios sin guardar! \***.
- La X a la derecha de la barra de menú o **Diseño -> Cerrar editor** cierra el editor. Si hay cambios sin guardar, primero te preguntará qué quieres hacer.

# Atajos

En macOS, usa `Cmd` en lugar de `Ctrl`.

| Atajo | Función |
|---|---|
| `Ctrl + S` | Guardar |
| `Ctrl + Z` | Deshacer |
| `Ctrl + Y` | Rehacer |
| `Ctrl + C` | Copiar los elementos seleccionados |
| `Ctrl + V` | Pegar |
| `Ctrl + A` | Seleccionar todos los elementos |
| `Delete` | Eliminar los elementos seleccionados |
| Teclas de flecha | Mover los elementos seleccionados un píxel |
| `Ctrl` + clic | Añadir un elemento a la selección o quitarlo |
| `Ctrl` + arrastrar | Mover varios elementos seleccionados |
| `Shift` + cambiar el tamaño | Conservar la proporción |
| `Shift` + girar o inclinar | Ajustar en incrementos |
| `Ctrl + G` | Activar o desactivar la cuadrícula |
| Mantener pulsada `O` | Mostrar los puntos de anclaje, con **Mostrar al pulsar una tecla (tecla «O»)** |

> [!TIP]
> El editor de texto tiene sus propios atajos; consulta [Texto en los menús](/text-in-menus#the-text-editor). Las ventanas, como [Scripts de acción](/action-scripts#shortcuts), indican sus atajos en sus respectivas páginas.
