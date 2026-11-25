---
title: Personalizaciones globales
description: >-
  Cambia los botones, controles deslizantes, fondos de menú, música y ventana de
  todas las pantallas a la vez, sin usar diseños.
sourceBlobSha: cafc7ed87ce931e406fb14b7a605085b565ce1a7
---

# Personalizaciones globales

Las personalizaciones globales cambian todas las pantallas a la vez: botones, controles deslizantes, fondos de menú, música, la ventana del juego y más. No necesitan un diseño y también funcionan en las pantallas cuya personalización está desactivada.

Ábrelas desde **barra de menú -> Personalización -> Personalizaciones globales**, en cualquier pantalla fuera del editor de diseños. Los cambios se aplican de inmediato y se guardan automáticamente.

<img width="800" alt="Las pantallas Título, Opciones y Música y sonidos sin ningún diseño, todas con los mismos botones de madera, controles de latón, etiquetas que se vuelven doradas al pasar el cursor y un fondo nocturno" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/global_customizations_tour.gif?raw=true">

> [!TIP]
> Para cambiar solo algunas pantallas, usa [diseños](/layout-editor). Para darles un estilo propio a los botones de ciertos diseños, usa [Plantillas de botones y controles deslizantes](/button-slider-templates).

# Botones y controles deslizantes

Estos ajustes cambian todos los botones y controles deslizantes de todas las pantallas, incluidos los de otros mods.

- Los botones y controles deslizantes que tengan texturas o ajustes de etiquetas propios de un [diseño](/layout-editor) o una [plantilla](/button-slider-templates) los conservan.
- Los botones que son solo una imagen, como el botón del libro de recetas, conservan su apariencia.

## Texturas de botones

**Texturas de botones personalizadas** tiene una textura para cada estado de un botón:

- **Normal**
- **Al pasar el cursor**: cuando el cursor está sobre el botón o cuando lo seleccionas con el teclado.
- **Inactivo**: cuando no se puede hacer clic en el botón.

Configura los tres estados. Si un estado no tiene textura, se muestra el botón original de Minecraft.

Más ajustes en el mismo menú:

- **Fondo transparente** oculta el fondo de todos los botones y solo muestra sus etiquetas. Este ajuste tiene prioridad sobre las texturas.
- **Fondos de botón en nueve partes** mantiene nítidos los bordes de las texturas con cualquier tamaño de botón, usando los cuatro tamaños de borde que aparecen debajo. Consulta [División en nueve partes y repetición](/nine-slicing-and-tiling).

> [!TIP]
> Sin la división en nueve partes, las texturas se estiran para ajustarse al tamaño de cada botón. Los botones de Minecraft miden 20 píxeles de alto y, por lo general, 200 o 150 píxeles de ancho. Con la división en nueve partes, una sola textura pequeña sirve para todos.

## Texturas de controles deslizantes

**Texturas de controles deslizantes personalizadas** tiene dos partes:

- **Textura del fondo del control deslizante**: la barra del control. Configúrala con **Establecer textura**. **Fondo transparente** y **Fondo del control deslizante en nueve partes** funcionan igual que en los botones.
- **Texturas del control del deslizador**: la parte que arrastras, con texturas **Normal**, **Al pasar el cursor** e **Inactivo**, además de **Control del deslizador en nueve partes**.

El control de los deslizadores de Minecraft mide 8 píxeles de ancho y tiene la misma altura que el deslizador, que suele ser de 20 píxeles. Sin la división en nueve partes, las texturas del control se estiran para ajustarse a ese tamaño.

## Etiquetas

**Etiquetas de botones** y **Etiquetas de controles deslizantes** tienen los mismos ajustes:

| Ajuste | Qué hace |
|---|---|
| **Subrayar etiqueta al pasar el cursor** | Subraya la etiqueta cuando el cursor está sobre ella. |
| **Color base de la etiqueta** | El color de la etiqueta. Selecciónalo con el selector de color o escribe un código HEX, como `#FFF1D6`. |
| **Color de la etiqueta al pasar el cursor** | El color de la etiqueta cuando el cursor está sobre ella. |
| **Escala de la etiqueta** | El tamaño de la etiqueta. `1` es el tamaño normal. |
| **Alineación de la etiqueta** | **Izquierda**, **Centrada** o **Derecha**. |
| **Sombra de la etiqueta** | La sombra oscura detrás de la etiqueta. Si se desactiva, ninguna etiqueta tendrá sombra, ni siquiera las de los diseños. |

Las etiquetas con ajustes propios de un diseño o una plantilla los conservan. En **Escala de la etiqueta** y **Alineación de la etiqueta**, solo usan el ajuste global las etiquetas con tamaño normal y alineación **Centrada**.

## Sonido al hacer clic

- **Sonido de clic personalizado para botones** reemplaza el sonido de clic de Minecraft para botones y controles deslizantes. Los botones con un sonido de clic propio definido en un diseño lo conservan.
- **Volumen del sonido de clic personalizado para botones** va del 0 % al 100 %. El control de volumen de su canal de sonido en los ajustes de sonido de Minecraft se aplica además de este.
- **Canal del sonido de clic personalizado para botones** es el canal de sonido en el que se reproduce, como Música. De forma predeterminada, es Volumen maestro, el canal de todos los sonidos.

# Fondos de menú

**Textura de fondo de menú personalizada** es una imagen que aparece detrás de todos los menús, excepto la pantalla de título:

- También aparece detrás del menú de pausa y de las opciones mientras juegas, así que oculta el mundo en esos casos. Los inventarios, letreros y libros siguen siendo transparentes.
- **Conservar la proporción de la textura de fondo** mantiene las proporciones de la imagen. De todos modos, ocupa toda la pantalla y se recortan las partes que no caben. Si se desactiva, la imagen se estira para ajustarse a la pantalla.

**Panorama de menú personalizado** reemplaza el panorama de Minecraft en la pantalla de título y en todos los menús antes de entrar a un mundo:

- **Elegir panorama** selecciona uno de tus [panoramas](/panoramas).
- **Quitar panorama** restaura el panorama de Minecraft.
- **Panorama actual** muestra cuál está configurado.

Si configuras ambos, la textura cubre el panorama, por lo que este solo se muestra en la pantalla de título.

Las pantallas cuyo diseño tenga su propio [fondo de menú](/menu-backgrounds) muestran ese fondo en su lugar.

# Música de menú

- **Reproducir música de menú original** activa o desactiva la música de Minecraft en los menús.
- **Pistas de música de menú personalizadas** abre **Administrar pistas de música de menú**. **Agregar pista** agrega un sonido, **Eliminar pista** elimina la pista seleccionada, **Borrar pistas** las elimina todas y **Listo** guarda la lista.

Las pistas se reproducen en orden aleatorio en los menús antes de entrar a un mundo, en lugar de la música de menú de Minecraft. Consulta más información sobre ellas y sobre la música en pantallas individuales en [Música de fondo de menú](/background-music).

# Pantallas y ventanas emergentes

| Ajuste | Qué hace |
|---|---|
| [**Intro del juego**](/game-intro) | Reproduce una animación o un video antes de que aparezca la pantalla de título. |
| **Íconos de mundos en la pantalla de un jugador** | Los íconos de los mundos en la lista de mundos. Si se desactiva, se ocultan. |
| **Íconos de servidores en la pantalla multijugador** | Los íconos de los servidores en la lista de servidores. Si se desactiva, se ocultan. |
| [**Carga fluida de mundos**](/seamless-world-loading) | Toma una captura de pantalla al salir de un mundo o servidor y la muestra como fondo de carga cuando vuelves a entrar. |
| **Avisos de logros** | Las ventanas emergentes de la esquina superior derecha cuando desbloqueas un logro, así como sus sonidos. Si se desactiva, se ocultan. Los mensajes de logros en el chat se mantienen y el listener [Al desbloquear un logro](/listeners#on-achievement-unlocked) sigue funcionando. |

# Ventana e inicio del juego

| Ajuste | Qué hace |
|---|---|
| [**Ícono de ventana personalizado**](/window-customization#custom-icon) | El ícono de la ventana del juego. Necesita un ícono PNG de 16x16 y otro de 32x32, además de un ícono para macOS. |
| [**Título de ventana personalizado**](/window-customization#custom-title) | Reemplaza el título de la ventana de Minecraft. Los [marcadores de posición](/placeholders) funcionan y el título se actualiza cuando cambian. |
| **Escala predeterminada de la interfaz gráfica** | Configura la escala de la interfaz gráfica de Minecraft una sola vez, en el primer inicio de la instancia del juego; por ejemplo, `2` o `3`. `-1` la desactiva. Está pensado para modpacks. |
| **Forzar pantalla completa al iniciar** | Inicia el juego en pantalla completa cada vez. |

FancyMenu recuerda que configuró la **Escala predeterminada de la interfaz gráfica** en `fancymenu_data/default_scale_set.fm`. Elimina ese archivo para que vuelva a configurar la escala en el siguiente inicio (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#instance-data)).

# Información útil

- Las personalizaciones globales se guardan en el archivo `options.txt` de FancyMenu, así que pertenecen al [perfil](/profiles) cargado y se incluyen en los modpacks que tengan `config/fancymenu/`.
- Las texturas y los sonidos pueden ser archivos de tu instancia, enlaces web o archivos de paquetes de recursos. Consulta [Recursos](/resources).
- **barra de menú -> Ayuda -> Exportar para IA -> Ajustes de FancyMenu** los incluye, por si tienes preguntas para un [chat de IA](/export-for-ai).
