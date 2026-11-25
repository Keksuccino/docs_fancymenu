---
title: Personalizaciones globales
description: >-
  Cambia a la vez los botones, los controles deslizantes, los fondos de los
  menús, la música y la ventana de todas las pantallas, sin usar diseños.
sourceBlobSha: cafc7ed87ce931e406fb14b7a605085b565ce1a7
---

# Personalizaciones globales

Las personalizaciones globales cambian todas las pantallas a la vez: botones, controles deslizantes, fondos de los menús, música, la ventana del juego y mucho más. No necesitan ningún diseño y también funcionan en pantallas cuya personalización está desactivada.

Puedes acceder a ellas desde **barra de menús -> Personalización -> Personalizaciones globales**, en cualquier pantalla fuera del editor de diseños. Los cambios se aplican de inmediato y se guardan automáticamente.

<img width="800" alt="Las pantallas Título, Opciones y Música y sonidos sin ningún diseño, todas con los mismos botones de madera, controles de latón, etiquetas que se vuelven doradas al pasar el cursor y un fondo nocturno" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/global_customizations_tour.gif?raw=true">

> [!TIP]
> Para cambiar solo algunas pantallas, usa [diseños](/layout-editor). Para dar un aspecto propio a los botones de determinados diseños, usa [plantillas de botones y controles deslizantes](/button-slider-templates).

# Botones y controles deslizantes

Estos ajustes cambian todos los botones y controles deslizantes de todas las pantallas, incluidos los de otros mods.

- Los botones y controles deslizantes que tengan texturas o ajustes de etiquetas propios de un [diseño](/layout-editor) o una [plantilla](/button-slider-templates) los conservan.
- Los botones que sean solo una imagen, como el del libro de recetas, mantienen su aspecto.

## Texturas de los botones

**Texturas personalizadas de botones** incluye una textura para cada estado de un botón:

- **Normal**
- **Al pasar el cursor**: cuando el cursor está sobre el botón o este está seleccionado con el teclado.
- **Inactivo**: cuando no se puede hacer clic en el botón.

Configura los tres estados. Si un estado no tiene textura, se mostrará el botón propio de Minecraft.

En el mismo menú hay más ajustes:

- **Fondo transparente** oculta el fondo de todos los botones, de modo que solo se vean sus etiquetas. Este ajuste tiene prioridad sobre las texturas.
- **Fondos de botones con nueve cortes** mantiene nítidos los bordes de las texturas con cualquier tamaño de botón, usando los cuatro tamaños de borde que aparecen debajo. Consulta [Nueve cortes y mosaico](/nine-slicing-and-tiling).

> [!TIP]
> Sin los nueve cortes, las texturas se estiran para adaptarse al tamaño de cada botón. Los botones de Minecraft miden 20 píxeles de alto y, por lo general, 200 o 150 píxeles de ancho. Con los nueve cortes, una textura pequeña sirve para todos.

## Texturas de los controles deslizantes

**Texturas personalizadas de controles deslizantes** tiene dos partes:

- **Textura del fondo del control deslizante**: la barra del control. Configúrala con **Establecer textura**. **Fondo transparente** y **Fondo del control deslizante con nueve cortes** funcionan igual que en los botones.
- **Texturas del tirador del control deslizante**: la parte que arrastras, con texturas **Normal**, **Al pasar el cursor** e **Inactivo**, además de **Tirador del control deslizante con nueve cortes**.

El tirador de los controles deslizantes de Minecraft mide 8 píxeles de ancho y tiene la misma altura que el control, que suele ser de 20 píxeles. Sin los nueve cortes, las texturas del tirador se estiran para adaptarse a ese tamaño.

## Etiquetas

**Etiquetas de botones** y **Etiquetas de controles deslizantes** tienen los mismos ajustes:

| Ajuste | Qué hace |
|---|---|
| **Subrayar la etiqueta al pasar el cursor** | Subraya la etiqueta cuando el cursor está sobre ella. |
| **Color base de la etiqueta** | El color de la etiqueta. Selecciónalo con el selector de color o como código HEX, por ejemplo, `#FFF1D6`. |
| **Color de la etiqueta al pasar el cursor** | El color de la etiqueta cuando el cursor está sobre ella. |
| **Tamaño de la etiqueta** | El tamaño de la etiqueta. `1` es el tamaño normal. |
| **Alineación de la etiqueta** | **Izquierda**, **Centrada** o **Derecha**. |
| **Sombra de la etiqueta** | La sombra oscura que aparece detrás de la etiqueta. Si se desactiva, ninguna etiqueta tendrá sombra, ni siquiera las de los diseños. |

Las etiquetas con ajustes propios de un diseño o una plantilla los conservan. En **Tamaño de la etiqueta** y **Alineación de la etiqueta**, solo se aplica el ajuste global a las etiquetas que tengan el tamaño normal y estén **Centradas**.

## Sonido al hacer clic

- **Sonido personalizado al hacer clic en botones** sustituye el sonido de clic de Minecraft para los botones y controles deslizantes. Los botones que tengan un sonido de clic propio de un diseño lo conservan.
- **Volumen del sonido personalizado al hacer clic en botones** va del 0 % al 100 %. El control de volumen de su canal en los ajustes de sonido de Minecraft se aplica además de este.
- **Canal del sonido personalizado al hacer clic en botones** es el canal de sonido en el que se reproduce, como Música. De forma predeterminada, es Volumen principal, el canal de todos los sonidos.

# Fondos de los menús

**Textura personalizada de fondo de los menús** es una imagen que aparece detrás de todos los menús, excepto la pantalla Título:

- También aparece detrás del menú de pausa y de las opciones mientras juegas, por lo que oculta el mundo. Los inventarios, los carteles y los libros siguen siendo transparentes.
- **Mantener la proporción de la textura de fondo** conserva las proporciones de la imagen. Aun así, cubre toda la pantalla y se recortan las partes que no caben. Si se desactiva, la imagen se estira para ocupar la pantalla.

**Panorama personalizado de fondo de los menús** sustituye el panorama de Minecraft en la pantalla Título y en todos los menús antes de entrar en un mundo:

- **Elegir panorama** selecciona uno de tus [panoramas](/panoramas).
- **Borrar panorama** restaura el panorama de Minecraft.
- **Panorama actual** muestra cuál está seleccionado.

Si configuras ambos, la textura cubre el panorama, que solo se verá en la pantalla Título.

Las pantallas cuyo diseño tenga su propio [fondo de menú](/menu-backgrounds) mostrarán ese fondo en su lugar.

# Música de los menús

- **Reproducir música original de los menús** activa o desactiva la música de Minecraft en los menús.
- **Pistas de música personalizadas de los menús** abre **Administrar pistas de música de los menús**. **Añadir pista** añade un sonido, **Eliminar pista** elimina la seleccionada, **Borrar pistas** las elimina todas y **Listo** guarda la lista.

Las pistas se reproducen en orden aleatorio en los menús antes de entrar en un mundo, en lugar de la música de los menús de Minecraft. Encontrarás más información sobre ellas y sobre la música en pantallas individuales en [Música de fondo de los menús](/background-music).

# Pantallas y ventanas emergentes

| Ajuste | Qué hace |
|---|---|
| [**Introducción del juego**](/game-intro) | Reproduce una animación o un vídeo antes de que aparezca la pantalla Título. |
| **Iconos de mundos en la pantalla de un jugador** | Los iconos de los mundos en la lista. Si se desactiva, se ocultan. |
| **Iconos de servidores en la pantalla Multijugador** | Los iconos de los servidores en la lista. Si se desactiva, se ocultan. |
| [**Carga de mundos sin interrupciones**](/seamless-world-loading) | Hace una captura de pantalla al salir de un mundo o servidor y la muestra como fondo de carga al volver a entrar. |
| **Notificaciones de logros** | Las ventanas emergentes de la esquina superior derecha que aparecen al desbloquear un logro, junto con sus sonidos. Si se desactiva, se ocultan. Los mensajes de logros en el chat se mantienen y el listener [Al desbloquear un logro](/listeners#on-achievement-unlocked) sigue funcionando. |

# Ventana e inicio del juego

| Ajuste | Qué hace |
|---|---|
| [**Icono personalizado de la ventana**](/window-customization#custom-icon) | El icono de la ventana del juego. Necesita un icono PNG de 16x16, otro de 32x32 y un icono para macOS. |
| [**Título personalizado de la ventana**](/window-customization#custom-title) | Sustituye el título de la ventana de Minecraft. Se pueden usar [marcadores de posición](/placeholders) y el título se actualiza cuando estos cambian. |
| **Escala predeterminada de la interfaz** | Establece la escala de la interfaz de Minecraft una sola vez, al iniciar por primera vez la instancia del juego; por ejemplo, `2` o `3`. `-1` la desactiva. Está pensado para modpacks. |
| **Forzar pantalla completa al iniciar** | Activa el modo de pantalla completa cada vez que se inicia el juego. |

FancyMenu recuerda que ha establecido la **Escala predeterminada de la interfaz** en `fancymenu_data/default_scale_set.fm`. Elimina ese archivo para que vuelva a establecer la escala en el próximo inicio (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#instance-data)).

# Información útil

- Las personalizaciones globales se guardan en el `options.txt` de FancyMenu, así que pertenecen al [perfil](/profiles) cargado y se incluyen en los modpacks que contienen `config/fancymenu/`.
- Las texturas y los sonidos pueden ser archivos de tu instancia, enlaces web o archivos de paquetes de recursos. Consulta [Recursos](/resources).
- **barra de menús -> Ayuda -> Exportar para IA -> Ajustes de FancyMenu** los incluye para que puedas consultarlos en un [chat de IA](/export-for-ai).
