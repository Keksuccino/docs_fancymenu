---
title: Elementos de Vanilla
description: >-
  Cómo personalizar los elementos que vienen de forma predeterminada en las
  pantallas.
sourceBlobSha: 3943106d1e4f0722aad0d1578908262b7c8d92ec
---

# Elementos de Vanilla

FancyMenu no solo te permite agregar cosas nuevas a las pantallas, también te permite personalizar elementos existentes del juego base (Vanilla) e incluso de otros mods.

## Botones y controles deslizantes de Vanilla (widgets)

Para personalizar los botones y controles deslizantes de una pantalla, crea un diseño para la pantalla actual (no un [diseño universal](/universal-layouts)) y haz clic derecho sobre ellos en el editor.

Tienen las mismas opciones que tus propios [botones](/elements#button) y [controles deslizantes](/elements#slider), como texturas, sonidos y descripciones emergentes. Lo único que no puedes cambiar es su script de acción: seguirán haciendo lo mismo que antes.

Los elementos de Vanilla no pueden colocarse en [áreas desplazables](/scrollable-areas), porque forman parte del menú.

### Etiquetas

- **Label** y **Hover Label** reemplazan el texto de un botón. En otros widgets, como los controles deslizantes, se llaman **Widget Text** y **Hover Widget Text**. Si no los usas, el widget conserva su propio texto.
- **Label Alignment** coloca la etiqueta a la **Left**, **Centered** o a la **Right** del widget. Las etiquetas demasiado anchas para el widget se desplazan de un lado a otro, sin importar su alineación.
- **Label Scale**, **Label Base Color**, **Label Hover Color**, **Label Shadow** y **Underline Label On Hover** cambian el tamaño, los colores y la sombra de la etiqueta.

Para alinear las etiquetas de varios botones a la vez, selecciónalos con `Ctrl` + clic (consulta [Seleccionar](/layout-editor#selecting)), haz clic derecho en uno de ellos y configura **Label Alignment** para todos. Para las etiquetas de todos los menús, usa **Label Alignment** en [Personalizaciones globales](/global-customizations#labels). Una [plantilla](/button-slider-templates) también puede aplicar a todos los botones de una pantalla el estilo de etiqueta definido en ella.

## Clics automatizados

Los widgets de Vanilla y de mods tienen la propiedad **Automated Clicks**. Asigna un número entero mayor que `0` para ejecutar esa cantidad de veces la acción original del clic izquierdo del widget cuando se cargue la pantalla. Por ejemplo, si configuras `2`, el widget recibirá dos clics durante la primera actualización de cada pantalla que se abra. El valor predeterminado, `0`, desactiva los clics automatizados.

Estos son clics reales en el widget: cada clic puede cambiar el valor de un control deslizante o de un botón con opciones, ejecutar la función normal del widget o incluso abrir otra pantalla. Prueba el resultado con cuidado, sobre todo si configuras más de un clic.

Para **mover** y **cambiar el tamaño** de los widgets de Vanilla o de mods, primero debes asignarles un punto de anclaje. Para hacerlo, **haz clic derecho** sobre ellos y selecciona **Anchor Point**. Elige cualquier opción distinta de **Original**, que es el punto de anclaje predeterminado para los elementos de Vanilla y de mods.

También puedes **ocultar** los widgets de Vanilla o de mods: solo tienes que **hacer clic derecho** sobre ellos y seleccionar **Delete**. En realidad, no se eliminan, sino que se ocultan. Para volver a mostrarlos, ve a **menu bar -> Element -> Deleted Vanilla Elements** y **haz clic izquierdo** en los elementos que quieras restaurar.

> [!WARNING]
> El widget **Copyright** de la pantalla de título es el único que **NO PUEDES** ocultar ni eliminar. Esto es intencional. No elimines los avisos de derechos de autor.

## Elementos de la pantalla de título

La pantalla de título tiene elementos que no son widgets normales (como el logotipo, el texto de bienvenida, etc.) y que no se pueden mover ni personalizar. La idea es eliminarlos y reemplazarlos por elementos personalizados (por ejemplo, un elemento Image para el logotipo o un elemento Splash Text personalizado para el texto de bienvenida de Vanilla).

Para eliminarlos, solo tienes que hacer clic derecho sobre ellos. Si quieres restaurarlos más adelante, ve a **menu bar -> Element -> Deleted Vanilla Elements** y **haz clic izquierdo** en el elemento que quieras volver a mostrar.

## Solución de problemas: los elementos de Vanilla no se ven en el editor

Si no puedes ver los elementos de Vanilla en el editor, probablemente estés usando un **diseño universal** en vez de uno **para la pantalla actual**. Asegúrate de crear un diseño para la pantalla actual. Solo puedes hacerlo si las personalizaciones están habilitadas para esa pantalla.

## Solución de problemas: no se aplican las personalizaciones

Si las personalizaciones de los elementos de Vanilla no se aplican fuera del editor, normalmente se debe a que otro mod está sobrescribiendo o modificando el menú principal de esos elementos.

**Ice and Fire** es un buen ejemplo de un mod que sobrescribe una pantalla o un menú: sobrescribe la pantalla de título.

Este problema no se limita a los elementos de Vanilla. Es probable que los elementos personalizados que agregues a las pantallas tampoco se apliquen si un mod las sobrescribe o modifica.
