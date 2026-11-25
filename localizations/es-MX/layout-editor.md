---
title: Editor de diseños
description: >-
  Cómo abrir el editor de diseños, seleccionar, mover y cambiar el tamaño de los
  elementos, ordenarlos con capas y grupos, guardar tu diseño y consultar todos
  los atajos del editor.
sourceBlobSha: c247d44a67ac209f2a0b638cb4748b408c7e7b13
---

# Editor de diseños

El editor de diseños es donde creas [diseños](/home#your-first-layout): agregas elementos, los mueves y cambias su tamaño, y modificas el menú que los rodea. Muestra el menú tal como lo ven los jugadores, así que puedes ver de inmediato cómo queda.

<img width="800" alt="Mover, ensanchar y ajustar un título, luego seleccionar dos botones, copiarlos y pegarlos, arrastrar las copias hacia abajo y deshacer el cambio" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_basics.gif?raw=true">

# Abrir el editor

1. Abre el menú que quieras modificar, como la pantalla de título.
2. Haz clic en **barra de menú -> Personalización -> Personalizar pantalla actual**, para que muestre **Activado**.
3. Haz clic en **barra de menú -> Personalización -> Diseños -> Nuevo -> Para la pantalla actual**.

- **Para todas las pantallas [Universal]** crea un [diseño universal](/universal-layouts), que aparece en todos los menús.
- Los diseños que ya tienes también aparecen en **Diseños**. Pasa el cursor sobre uno y haz clic en **Editar diseño**.
- En cualquier menú, `Ctrl + Alt + L` abre el último diseño que editaste. Consulta [los atajos de la barra de menú](/home#menu-bar-shortcuts).

# Vista general del editor

<img width="800" alt="El editor de diseños con el botón Unirse al servidor seleccionado, la barra de menú en la parte superior y el widget Capas a la derecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Haz clic derecho en el fondo para ver la configuración de todo el diseño y agregar elementos con **Nuevo elemento**.
- Haz clic derecho en un elemento para ver su configuración. Consulta [Elementos](/elements#settings-of-all-elements).
- **Capas**, a la derecha, muestra todos los elementos del diseño. Consulta [Capas y grupos](#layers-and-groups).
- La barra de menú de la parte superior:

| Menú | Qué contiene |
|---|---|
| **Diseño** | **Nuevo**, **Abrir**, **Guardar**, **Guardar como**, **Exportar diseño para IA**, **Propiedades del diseño** (lo mismo que el menú contextual del fondo), **Configuración** y **Cerrar editor** |
| **Editar** | **Deshacer**, **Rehacer**, **Copiar**, **Pegar** y **Seleccionar todo** |
| **Elemento** | **Nuevo** para agregar elementos y **Elementos vanilla eliminados** para restaurar [elementos vanilla que eliminaste](/deleted-vanilla-elements) |
| **Ventana** | **Widgets del editor**, la [cuadrícula](#grid-and-anchor-overlay), la [superposición de puntos de anclaje](#grid-and-anchor-overlay), **Controles de rotación de elementos** y **Controles de inclinación de elementos** |

## Configuración del diseño

El menú contextual del fondo contiene todo lo relacionado con el diseño, por ejemplo:

- [**Fondos del menú**](/menu-backgrounds) y [**Superposiciones decorativas**](/decoration-overlays)
- **Título de pantalla personalizado** para el texto que aparece en la parte superior de algunos menús, como «Opciones». Puedes usar [marcadores de posición](/placeholders).
- **Personalizaciones de encabezado y pie de página** para [pantallas desplazables](/customizing-scrollable-screens)
- **Índice del diseño [Orden de varios diseños]** y **Modo aleatorio** para [usar varios diseños en un menú](/randomize-layouts)
- **Requisitos de carga [para todo el diseño]**; consulta [Requisitos](/conditions#layout-wide-requirements)
- **Editar el script de acción «Abrir pantalla»** y **Editar el script de acción «Cerrar pantalla»**; consulta [Scripts de acción](/action-scripts)
- **Opciones de diseño universal**, solo en [diseños universales](/universal-layouts)

# Trabajar con elementos

## Seleccionar

- Haz clic en un elemento para seleccionarlo. Haz clic en el fondo para quitar la selección de todo.
- Arrastra sobre el fondo para seleccionar todos los elementos dentro del rectángulo.
- `Ctrl` + clic agrega un elemento a la selección o lo quita si ya estaba seleccionado.
- `Ctrl + A` selecciona todos los elementos.

Los clics, los rectángulos y `Ctrl + A` omiten los elementos que [ocultaste en Capas](#hiding-and-renaming).

## Mover

- Arrastra un elemento para moverlo. Para mover varios elementos seleccionados, mantén presionado `Ctrl` mientras empiezas a arrastrarlos. Sin `Ctrl`, el clic solo selecciona el elemento en el que hiciste clic.
- Las teclas de flecha mueven los elementos seleccionados un píxel.
- Al arrastrar, aparecen los puntos de anclaje. Mantén el elemento sobre otro punto de anclaje o elemento para anclarlo ahí. Consulta [Colocar elementos](/positioning-elements).
- Suelta un elemento sobre un [área desplazable](/scrollable-areas) para colocarlo dentro de ella.

## Cambiar el tamaño

Arrastra un borde o una esquina de un elemento seleccionado. Mantén presionada la tecla `Shift` para conservar la proporción.

Solo puedes cambiar el tamaño cuando hay un elemento seleccionado.

## Girar e inclinar

Los elementos seleccionados que admiten esta función muestran controles para [girarlos e inclinarlos](/rotating-elements). Mantén presionada la tecla `Shift` mientras los arrastras para ajustar el movimiento a intervalos: 45° al girar y 15° al inclinar.

**Ventana -> Controles de rotación de elementos** y **Controles de inclinación de elementos** ocultan los controles.

## Copiar, pegar y eliminar

- `Ctrl + C` copia los elementos seleccionados y `Ctrl + V` los pega. Las copias aparecen encima de los originales y quedan seleccionadas, así que puedes arrastrarlas para apartarlas de inmediato.
- También puedes pegarlas en otro diseño, hasta que cierres el juego.
- `Delete` elimina los elementos seleccionados. Los elementos vanilla solo se ocultan: puedes restaurarlos con **Elemento -> Elementos vanilla eliminados**.
- Si eliminas un área desplazable, se te preguntará si también quieres eliminar su contenido o conservarlo en el diseño.

## Deshacer y rehacer

`Ctrl + Z` revierte el último cambio y `Ctrl + Y` lo vuelve a aplicar. Ambas opciones también están en el menú **Editar**.

## Elementos invisibles

Los jugadores no pueden ver los elementos [Audio](/elements#audio), [Arrastrador](/dragger), [Animador de elementos](/element-animator), [Controlador de música](/elements#music-controller) y [Ticker](/elements#ticker). En el editor aparecen como cuadros de colores con su nombre para que puedas encontrarlos, moverlos y cambiar su tamaño.

- **Color en el editor**, en su menú contextual, cambia el color del cuadro. Por ejemplo, puedes usarlo para distinguir varios Tickers. Los colores se escriben como `#RRGGBB` o `#RRGGBBAA` si tienen transparencia: un color translúcido como `#E30E2366` deja ver lo que hay detrás del cuadro.
- El nombre que aparece en el cuadro es el nombre de capa del elemento. Consulta [Ocultar y cambiar nombres](#hiding-and-renaming).

Los jugadores nunca ven el cuadro, su color ni su nombre.

# Capas y grupos

**Capas** muestra todos los elementos del diseño, empezando por el que está más arriba: un elemento aparece delante de todo lo que esté debajo en la lista. **Ventana -> Widgets del editor -> Capas** muestra u oculta esta sección.

<img width="800" alt="Arrastrar la capa Fondo de noticias debajo de Texto de noticias para que las notas del parche aparezcan al quitar la selección; luego agregar un grupo, colocar ambas capas dentro, ocultar y mostrar el grupo con el icono del ojo y contraerlo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_layers.gif?raw=true">

## Cambiar el orden

- Haz clic en una capa para seleccionar su elemento y luego arrástrala hacia arriba o hacia abajo. Una línea indica dónde quedará. Todas las capas seleccionadas se mueven juntas.
- También puedes hacer clic derecho en un elemento o su capa y seleccionar **Subir una capa** o **Bajar una capa**.

En el editor, los elementos seleccionados siempre aparecen delante de los demás. Quita la selección para ver el orden real.

En algunas versiones de Minecraft, los elementos [Entidad de jugador](/elements#player-entity) y [Objeto](/elements#item) aparecen delante de todo, sin importar su capa. Consulta [Problemas conocidos](/known-issues#1-player-entity--item-elements-are-always-in-front-of-everything).

## Elementos vanilla

La fila **Elementos vanilla** representa todos los elementos propios del menú, como sus botones. No puedes cambiar su orden, pero el botón que aparece a la derecha de la fila coloca todos tus elementos detrás o delante de ellos. Hace lo mismo que **Elementos personalizados detrás de los vanilla**, en el menú contextual del fondo.

## Ocultar y cambiar nombres

- El icono del ojo de una capa oculta su elemento en el editor para que no estorbe mientras trabajas con los demás. Haz clic otra vez para mostrarlo.
- No puedes hacer clic en los elementos ocultos ni moverlos, copiarlos o eliminarlos. Los jugadores siguen viéndolos; solo se ocultan en el editor. El diseño recuerda cuáles ocultaste.
- Haz clic derecho en una capa y selecciona **Cambiar nombre de capa** para asignarle un nombre más fácil de identificar, como `Panel de noticias`. Es lo mismo que el **Nombre para mostrar en el editor** del elemento y los jugadores no lo ven.

## Grupos

Los grupos organizan bajo un mismo nombre las capas relacionadas, como todas las partes de un panel de noticias. Solo ordenan la lista: los elementos siguen apareciendo y funcionando como antes.

- Haz clic derecho dentro de Capas y selecciona **Agregar grupo**. El grupo aparecerá debajo de las capas.
- Arrastra capas al grupo para agregarlas. Arrástralas fuera para quitarlas.
- Haz clic en un grupo para seleccionar todos sus elementos. Arrástralo para moverlos todos hacia arriba o hacia abajo al mismo tiempo.
- La flecha de un grupo contrae o despliega sus capas, y el icono del ojo las oculta o las muestra todas.
- Haz clic derecho en un grupo para cambiarle el nombre, subirlo o bajarlo una capa, o eliminarlo. **Eliminar grupo** conserva sus elementos.

**Subir una capa** y **Bajar una capa** mantienen el elemento dentro de su grupo. Para sacarlo, arrastra su capa fuera del grupo.

El diseño guarda los grupos y cuáles están contraídos.

## Áreas desplazables

Los elementos de un [área desplazable](/scrollable-areas) aparecen debajo de la capa del área, con sangría.

- Arrastra una capa a la mitad inferior de la capa del área para colocar el elemento dentro. Arrástrala fuera, entre las demás capas, para sacarlo. El elemento permanece en el mismo lugar de la pantalla.
- La flecha de la capa del área contrae o despliega sus elementos.
- Los elementos de un área no pertenecen a ningún grupo. Se mueven junto con el área.

# Cuadrícula y superposición de puntos de anclaje

El menú **Ventana** contiene la configuración de las herramientas auxiliares del editor:

- **Cuadrícula** muestra las líneas de la cuadrícula. `Ctrl + G` las activa o desactiva. **Tamaño de cuadrícula** establece la distancia entre ellas.
- **Ajustar a la cuadrícula** hace que los elementos que arrastras se ajusten a las líneas, mientras la cuadrícula está visible. **Intensidad del ajuste a la cuadrícula** determina qué tan fuerte es el ajuste.
- **Visibilidad de la superposición de puntos de anclaje** establece cuándo se muestran los puntos de anclaje:
  - **Mostrar al arrastrar elementos**: mientras arrastras elementos.
  - **Siempre visible**: todo el tiempo.
  - **Mostrar al presionar una tecla (tecla «O»)**: mientras mantienes presionada la tecla `O`.
  - **Desactivado**: nunca.
- **Anclaje al pasar sobre un área** determina si mantener un elemento sobre un punto de anclaje cambia su anclaje. **Anclaje al pasar sobre un elemento** agrega otros elementos a los puntos de anclaje, así que solo funciona cuando también está activado **Anclaje al pasar sobre un área**.

# Guardar y cerrar

- `Ctrl + S` o **Diseño -> Guardar** guarda el diseño. La primera vez, FancyMenu te pedirá un nombre de archivo.
- **Diseño -> Guardar como** guarda el diseño en un archivo nuevo.
- Si hay cambios sin guardar, la barra de menú muestra **\* ¡Hay cambios sin guardar! \***.
- La X a la derecha de la barra de menú o **Diseño -> Cerrar editor** cierra el editor. Si hay cambios sin guardar, primero te lo preguntará.

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
| `Ctrl` + clic | Agregar un elemento a la selección o quitarlo |
| `Ctrl` + arrastrar | Mover varios elementos seleccionados |
| `Shift` + cambiar el tamaño | Conservar la proporción |
| `Shift` + girar o inclinar | Ajustar el movimiento a intervalos |
| `Ctrl + G` | Activar o desactivar la cuadrícula |
| Mantener presionada la tecla `O` | Mostrar los puntos de anclaje, con **Mostrar al presionar una tecla (tecla «O»)** |

> [!TIP]
> El editor de texto tiene sus propios atajos; consulta [Texto en los menús](/text-in-menus#the-text-editor). Las ventanas como [Scripts de acción](/action-scripts#shortcuts) indican sus atajos en sus respectivas páginas.
