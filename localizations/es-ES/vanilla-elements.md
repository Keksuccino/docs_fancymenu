---
title: Elementos del juego base
description: >-
  Cómo personalizar elementos que forman parte de las pantallas de forma
  predeterminada.
sourceBlobSha: 3943106d1e4f0722aad0d1578908262b7c8d92ec
---

# Elementos del juego base

FancyMenu no solo te permite añadir elementos nuevos a las pantallas, sino que también te permite personalizar los elementos existentes del juego base (Vanilla) e incluso los de otros mods.

## Botones y controles deslizantes del juego base (widgets)

Para personalizar los botones y controles deslizantes de una pantalla, crea un diseño para la pantalla actual (no un [diseño universal](/universal-layouts)) y haz clic derecho sobre ellos en el editor.

Tienen los mismos ajustes que tus propios [botones](/elements#button) y [controles deslizantes](/elements#slider), como texturas, sonidos y descripciones emergentes. Lo único que no puedes cambiar es su script de acción: seguirán haciendo lo mismo que antes.

Los elementos del juego base no pueden añadirse a [áreas desplazables](/scrollable-areas), porque pertenecen al propio menú.

### Etiquetas

- **Etiqueta** y **Etiqueta al pasar el cursor** sustituyen el texto de un botón. En otros widgets, como los controles deslizantes, se llaman **Texto del widget** y **Texto del widget al pasar el cursor**. Si no se usan, el widget conserva su propio texto.
- **Alineación de la etiqueta** coloca la etiqueta a la **Izquierda**, **Centrada** o a la **Derecha** del widget. Las etiquetas demasiado anchas para el widget se desplazan de un lado a otro, independientemente de su alineación.
- **Escala de la etiqueta**, **Color base de la etiqueta**, **Color de la etiqueta al pasar el cursor**, **Sombra de la etiqueta** y **Subrayar la etiqueta al pasar el cursor** modifican el tamaño, los colores y la sombra de la etiqueta.

Para alinear las etiquetas de varios botones a la vez, selecciónalos con `Ctrl` + clic (consulta [Seleccionar](/layout-editor#selecting)), haz clic derecho en uno de ellos y establece **Alineación de la etiqueta** para todos. Para las etiquetas de todos los menús, usa **Alineación de la etiqueta** en [Personalizaciones globales](/global-customizations#labels). Una [plantilla](/button-slider-templates) también puede aplicar a todos los botones de una pantalla el estilo de etiqueta que defina.

## Clics automatizados

Los widgets del juego base y de los mods tienen una propiedad **Clics automatizados**. Asígnale un número entero mayor que `0` para ejecutar esa cantidad de veces la acción original del widget al hacer clic con el botón izquierdo cuando se cargue la pantalla. Por ejemplo, si estableces el valor en `2`, el widget se pulsará dos veces durante la primera actualización de cada pantalla que se abra. El valor predeterminado, `0`, desactiva los clics automatizados.

Estos son clics reales en el widget: cada clic puede cambiar el valor de un control deslizante o de un botón de ciclo, ejecutar la acción habitual del widget o incluso abrir otra pantalla. Comprueba el resultado con cuidado, sobre todo si configuras más de un clic.

Para **mover** y **cambiar el tamaño** de los widgets del juego base o de los mods, primero tienes que asignarles un punto de anclaje. Para ello, haz **clic derecho** en el widget y selecciona **Punto de anclaje**. Elige cualquier opción que no sea **Original**, ya que esa es la opción de anclaje predeterminada para los elementos del juego base y de los mods.

También puedes **ocultar** estos widgets. Para ello, haz **clic derecho** en ellos y selecciona **Eliminar**. En realidad, no se eliminan, sino que se ocultan. Para volver a mostrarlos, haz clic en **barra de menú -> Elemento -> Elementos del juego base eliminados** y haz **clic izquierdo** en los elementos que quieras mostrar de nuevo.

> [!WARNING]
> El widget **Copyright** de la pantalla de título es el único que **NO PUEDES** ocultar ni eliminar. Es intencionado. No elimines los avisos de copyright.

## Elementos de la pantalla de título

La pantalla de título tiene elementos que no son widgets normales (como el logotipo, el texto de presentación, etc.) y que no se pueden mover ni personalizar. Están pensados para eliminarse y sustituirse por elementos personalizados (como un elemento Imagen para el logotipo o un elemento Texto de presentación personalizado para el texto de presentación del juego base).

Para eliminarlos, haz clic derecho en ellos. Si más adelante quieres restaurarlos, haz clic en **barra de menú -> Elemento -> Elementos del juego base eliminados** y haz **clic izquierdo** en el elemento que quieras volver a mostrar.

## Solución de problemas: los elementos del juego base no se ven en el editor

Si no puedes ver los elementos del juego base en el editor, probablemente se deba a que estás usando un **diseño universal** en vez de uno **para la pantalla actual**. Asegúrate de crear un diseño para la pantalla actual. Solo puedes crear diseños para la pantalla actual si las personalizaciones están activadas para esa pantalla.

## Solución de problemas: no se aplican las personalizaciones

Si las personalizaciones de los elementos del juego base no se aplican fuera del editor, normalmente se debe a que otro mod está sobrescribiendo o modificando el menú principal de esos elementos.

Un buen ejemplo de un mod que sobrescribe una pantalla o un menú es **Ice and Fire**, que sobrescribe la pantalla de título.

El problema de que no se apliquen las personalizaciones a los menús no se limita a los elementos del juego base. Es probable que los elementos personalizados añadidos a las pantallas tampoco se apliquen si un mod las sobrescribe o modifica.
