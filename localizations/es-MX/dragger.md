---
title: Dragger
description: >-
  Permite que los jugadores agarren un panel, una nota o cualquier otro elemento
  de tus menús y lo muevan a donde quieran.
sourceBlobSha: 5cfe57388c5b839c5a98045d0086a94df6b4110c
---

# Dragger

Un Dragger es un área invisible que los jugadores pueden agarrar con el mouse y mover. Todo lo que esté anclado a él también se mueve, como un panel con notas de actualización o una nota con las reglas del servidor. El menú recuerda dónde lo dejaron los jugadores, incluso después de reiniciar el juego.

<img width="800" alt="Un jugador agarra un banner de notas de actualización por el mango de cuero de su varilla y lo mueve del lado izquierdo al lado derecho de la pantalla de título. Abre Opciones, regresa y el banner sigue del lado derecho" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_hero.gif?raw=true">

Los jugadores solo pueden arrastrarlo fuera del editor de diseño. En el editor, el Dragger es un recuadro rojo con su nombre (la opción **In-Editor Color** de su menú contextual cambia el color rojo), y todo permanece donde lo coloca el diseño.

# Cómo hacer que algo se pueda mover

<img width="800" alt="Agregar un Dragger desde Nuevo elemento, cambiar su tamaño para que coincida con el banner, arrastrarlo hasta el banner y bajarlo dos capas; después, arrastrar el banner fuera del Dragger y de vuelta, y mantenerlo ahí hasta que la barra se llene para anclarlo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_setup.gif?raw=true">

1. Crea lo que quieras mover, como una imagen de banner con un elemento de texto encima.
2. Haz clic derecho en un espacio libre del editor de diseño y selecciona **New Element -> Dragger**.
3. Ajusta el tamaño del Dragger para que coincida con el del banner y muévelo encima de este.
4. Haz clic derecho en el Dragger y selecciona **Move One Layer Down** hasta que quede debajo de todos los elementos del banner. Los elementos seleccionados siempre se muestran encima, así que haz clic en un espacio libre para ver el cambio.
5. Ancla el banner al Dragger: arrastra el banner un poco fuera del Dragger y de vuelta, y mantenlo ahí hasta que la barra se llene. Encontrarás más información en [Posicionar elementos](/positioning-elements#anchoring-elements-to-other-elements).
6. Guarda el diseño y pruébalo fuera del editor.

Los elementos anclados a otro elemento que se mueve también se mueven con él. En el GIF, el texto está anclado al banner, así que el único elemento que necesita el Dragger es el banner.

Para anclar varios elementos a la vez, haz clic derecho en el Dragger y selecciona **Copy Element ID** antes del paso 4. Después, selecciona los elementos, haz clic derecho en uno de ellos, selecciona **Anchor Point -> Other Element** y pega el ID.

> [!TIP]
> Los jugadores no pueden ver el Dragger, así que indícales dónde agarrar el elemento, por ejemplo, con una barra de título o un mango.

# Guardar la posición

La opción **Save User Drag Offset** del menú contextual del Dragger está activada de manera predeterminada para los Draggers nuevos.

- **Activada**: la posición se guarda cuando el jugador suelta el elemento. Se conserva aunque cierre la pantalla y reinicie el juego.
- **Desactivada**: todo vuelve a su posición en el diseño cuando se abre la pantalla de nuevo, y cuando cambia el tamaño de la ventana o la escala de la interfaz.

Si desactivas esta opción en el editor, también se olvida la posición que los jugadores hayan guardado para este Dragger.

Las posiciones se guardan para cada Dragger según su [ID de elemento](/element-identifiers), en `fancymenu_data/dragger_metas.json`. Esa carpeta no forma parte de los [perfiles](/profiles), así que las posiciones que hayas movido durante las pruebas no terminan en la carpeta `config/fancymenu/` de tu modpack. Consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#instance-data).

Para devolver todos los Draggers a su posición en el diseño, elimina `dragger_metas.json` con el juego cerrado.

# Qué pueden agarrar los jugadores

Los jugadores pueden agarrar el Dragger en las áreas donde ningún elemento encima de él reciba el clic:

- Las imágenes encima de él dejan pasar el clic, así que los jugadores agarran directamente el banner.
- Los botones y las palabras de los elementos de texto encima de él reciben el clic, así que siguen funcionando en un panel movible.
- Si el Dragger está encima de un botón, el botón no recibe clics. Por eso, en los pasos anteriores, el Dragger se coloca debajo del banner.

Cuando los [requisitos](/element-visibility#showing-elements-only-sometimes) oculten el Dragger, los jugadores no podrán agarrarlo.

# Mantenerlo dentro de la pantalla

La opción **Stay on Screen** está activada para los elementos nuevos. Hace que el Dragger se detenga en los bordes de la pantalla para que los jugadores no puedan arrastrarlo fuera de la vista. Si el Dragger tiene el mismo tamaño que todo el banner, el banner también se detiene en el borde.

También puedes usar un Dragger que cubra solo una parte del elemento, como una barra de título. Sin embargo, los elementos anclados a él tienen su propia opción **Stay on Screen**: al llegar al borde, se detienen por su cuenta mientras el Dragger sigue moviéndose, y el panel se desarma. Desactiva **Stay on Screen** en esos elementos para que se muevan junto con el Dragger y solo la barra de título permanezca en pantalla.
