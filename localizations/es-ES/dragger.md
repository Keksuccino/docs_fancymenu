---
title: Dragger
description: >-
  Permite que los jugadores agarren un panel, una nota o cualquier otro elemento
  de los menús y lo muevan donde quieran.
sourceBlobSha: 5cfe57388c5b839c5a98045d0086a94df6b4110c
---

# Dragger

Un Dragger es una zona invisible que los jugadores pueden agarrar con el ratón y mover. Todo lo que esté anclado a él también se mueve, como un panel con notas de la versión o una nota con las reglas del servidor. El menú recuerda dónde lo dejaron los jugadores, incluso después de reiniciar el juego.

<img width="800" alt="Un jugador agarra un banner con las notas de la versión por el mango de cuero de su varilla y lo arrastra del lado izquierdo al derecho de la pantalla del título; abre las opciones, vuelve y el banner sigue a la derecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_hero.gif?raw=true">

Los jugadores solo pueden arrastrarlo fuera del editor de diseños. En el editor, el Dragger es un cuadro rojo con su nombre (**Color en el editor** en su menú contextual cambia el rojo), y todo permanece donde lo coloca el diseño.

# Cómo hacer que algo se pueda mover

<img width="800" alt="Añadir un Dragger desde Nuevo elemento, cambiar su tamaño para que coincida con el banner, arrastrarlo hasta el banner y bajarlo dos capas; después, arrastrar el banner fuera del Dragger y volver a colocarlo encima, manteniéndolo ahí hasta que la barra se llene para anclarlo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_setup.gif?raw=true">

1. Crea lo que quieras mover, por ejemplo, una imagen de banner con un elemento de texto encima.
2. Haz clic con el botón derecho en un espacio libre del editor de diseños y selecciona **Nuevo elemento -> Dragger**.
3. Ajusta el tamaño del Dragger para que coincida con el del banner y colócalo encima.
4. Haz clic con el botón derecho en el Dragger y selecciona **Bajar una capa** hasta que quede por debajo de todos los elementos del banner. Los elementos seleccionados siempre se muestran encima; haz clic en un espacio libre para ver el cambio.
5. Ancla el banner al Dragger: arrastra el banner un poco fuera del Dragger, vuelve a colocarlo encima y mantenlo ahí hasta que la barra se llene. Encontrarás más información en [Posicionar elementos](/positioning-elements#anchoring-elements-to-other-elements).
6. Guarda el diseño y pruébalo fuera del editor.

Los elementos anclados a otro elemento que se mueve también se desplazan con él. En el GIF, el texto está anclado al banner, así que el Dragger solo hace falta para el banner.

Para anclar varios elementos a la vez, haz clic con el botón derecho en el Dragger y selecciona **Copiar ID del elemento** antes del paso 4. Después, selecciona los elementos, haz clic con el botón derecho en uno de ellos, selecciona **Punto de anclaje -> Otro elemento** y pega el ID.

> [!TIP]
> Los jugadores no pueden ver el Dragger, así que indícales dónde agarrar, por ejemplo, con una barra de título o un asa.

# Guardar la posición

La opción **Guardar desplazamiento del arrastre del usuario** está activada de forma predeterminada en los nuevos Draggers.

- **Activada**: la posición se guarda cuando el jugador suelta el elemento. Se mantiene al cerrar la pantalla y reiniciar el juego.
- **Desactivada**: todo vuelve a su posición en el diseño al abrir la pantalla de nuevo y cuando cambia el tamaño de la ventana o la escala de la interfaz.

Si desactivas esta opción en el editor, también se olvida la posición que los jugadores hayan guardado para ese Dragger.

Las posiciones se guardan para cada Dragger según su [ID de elemento](/element-identifiers), en `fancymenu_data/dragger_metas.json`. Esa carpeta no forma parte de los [perfiles](/profiles), así que las posiciones a las que hayas arrastrado elementos durante las pruebas no acaban en la carpeta `config/fancymenu/` de tu modpack. Consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#instance-data).

Para devolver todos los Draggers a su posición en el diseño, elimina `dragger_metas.json` con el juego cerrado.

# Qué pueden agarrar los jugadores

Los jugadores pueden agarrar el Dragger en las zonas donde ningún elemento situado encima intercepte el clic:

- Las imágenes situadas encima dejan pasar el clic, así que los jugadores agarran el propio banner.
- Los botones y las palabras de los elementos de texto situados encima reciben el clic, por lo que siguen funcionando en un panel que se puede mover.
- Si el Dragger queda por encima de un botón, el botón no recibe los clics. Por eso, en los pasos anteriores el Dragger se coloca debajo del banner.

Si los [requisitos](/element-visibility#showing-elements-only-sometimes) del Dragger hacen que se oculte, los jugadores no podrán agarrarlo.

# Mantenerse en pantalla

La opción **Mantener en pantalla** está activada de forma predeterminada en los elementos nuevos. Hace que el Dragger se detenga en los bordes de la pantalla, para que los jugadores no puedan arrastrarlo fuera de la vista. Si el Dragger tiene el mismo tamaño que todo el banner, el banner también se detiene en el borde.

También funciona un Dragger que solo cubra una parte, como una barra de título. Sin embargo, los elementos anclados a él tienen su propia opción **Mantener en pantalla**: al llegar al borde, se detienen por su cuenta mientras el Dragger sigue moviéndose, y el panel se descompone. Desactiva **Mantener en pantalla** en esos elementos para que sigan moviéndose con el Dragger y solo la barra de título permanezca en pantalla.
