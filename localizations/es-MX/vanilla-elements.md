---
title: Elementos Vanilla
description: >-
  Cómo personalizar elementos que forman parte de las pantallas de forma
  predeterminada.
---
# Elementos Vanilla

FancyMenu no solo te permite agregar cosas nuevas a las pantallas, también hace posible personalizar elementos existentes del juego base (Vanilla) e incluso de otros mods.

## Botones y deslizadores Vanilla (Widgets)

Para personalizar widgets Vanilla/de mods existentes, solo crea un nuevo diseño **"para la pantalla actual"** (¡NO universal!) y haz **clic derecho** en los elementos del editor, igual que harías con los personalizados.

Puedes personalizar sus **etiquetas y texturas** igual que harías con botones y deslizadores personalizados.

Lo único que **no puedes hacer** con widgets Vanilla/de mods es personalizar su **script de acción** (como cambiar lo que hacen al interactuar con ellos). Esto solo es posible con botones y deslizadores personalizados.

## Clics automáticos

Los widgets Vanilla y de mods tienen una propiedad de **Clics automáticos**. Establécela en un entero mayor que `0` para invocar el comportamiento original de clic izquierdo del widget esa cantidad de veces cuando se cargue la pantalla. Por ejemplo, establecerlo en `2` hace clic en el widget dos veces durante la primera actualización de cada pantalla recién abierta. El valor predeterminado `0` desactiva los clics automáticos.

Estos son clics reales en el widget: cada clic puede cambiar el valor de un deslizador o de un botón cíclico, ejecutar la devolución de llamada normal del widget o incluso abrir otra pantalla. Prueba el resultado con cuidado, especialmente al configurar más de un clic.

Para **mover** y **redimensionar** widgets Vanilla/de mods, primero necesitas darles un punto de anclaje. Para hacerlo, haz **clic derecho** sobre ellos y luego haz clic en **Punto de anclaje**. Cámbialo por cualquier opción que no sea **Original**, porque ese es el anclaje predeterminado de los elementos Vanilla/de mods.

También puedes **ocultar** widgets Vanilla/de mods simplemente haciendo **clic derecho** sobre ellos y luego haciendo clic en **Eliminar**. En realidad no se eliminan, solo se ocultan, y puedes restaurarlos haciendo clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y luego haciendo **clic izquierdo** en el/los elemento(s) que quieras volver a hacer visibles.

> [!WARNING]
> El widget de **Copyright** en la pantalla de título es el único que **NO puedes** ocultar/eliminar. Esto es intencional. Por favor, no elimines los avisos de copyright.

## Elementos de la pantalla de título

La pantalla de título tiene elementos que no son widgets normales (como el logo, el texto destacado, etc.) y que no se pueden mover ni personalizar. Están pensados para eliminarse y reemplazarse con elementos personalizados (como un elemento de Imagen para el logo o un elemento de Texto destacado personalizado para el texto destacado Vanilla).

Para eliminarlos, solo haz clic derecho sobre ellos. Si quieres restaurarlos después, solo haz clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y luego haz **clic izquierdo** en el elemento que quieras volver a hacer visible.

## Solución de problemas: los elementos Vanilla no son visibles en el editor

Si no puedes ver los elementos Vanilla en el editor, probablemente se deba a que estás usando un **diseño universal** en lugar de uno **para la pantalla actual**. Asegúrate de crear un diseño para la pantalla actual. Solo puedes crear diseños para la pantalla actual cuando las personalizaciones están habilitadas para esa pantalla.

## Solución de problemas: las personalizaciones no se aplican

Si las personalizaciones a elementos Vanilla no se aplican fuera del editor, por lo general se debe a que otro mod está sobrescribiendo o modificando el menú principal de los elementos Vanilla.

Un buen ejemplo de un mod que sobrescribe una pantalla/menú es **Ice and Fire**, que sobrescribe la pantalla de título.

Que las personalizaciones no se apliquen a los menús no se limita a los elementos Vanilla. Es probable que los elementos personalizados agregados a las pantallas tampoco se apliquen a los menús si un mod los está sobrescribiendo o modificando.
