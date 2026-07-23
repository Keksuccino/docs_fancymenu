---
title: Elementos vanilla
description: Cómo personalizar elementos que forman parte de las pantallas por defecto.
---
# Elementos vanilla

FancyMenu no solo te permite añadir cosas nuevas a las pantallas, sino que también hace posible personalizar elementos existentes del juego base (vanilla) e incluso de otros mods.

## Botones y deslizadores vanilla (widgets)

Para personalizar widgets existentes de vanilla o de mods, solo tienes que crear un nuevo diseño **"para la pantalla actual"** (¡NO universal!) y hacer **clic derecho** en los elementos del editor, igual que harías con los personalizados.

Puedes personalizar sus **etiquetas y texturas** igual que harías con botones y deslizadores personalizados.

Lo único que **no puedes hacer** con widgets de vanilla o de mods es personalizar su **script de acción** (por ejemplo, cambiar lo que hacen al interactuar con ellos). Esto solo es posible con botones y deslizadores personalizados.

## Clics automatizados

Los widgets de vanilla y de mods tienen una propiedad de **Clics automatizados**. Establécela en un entero mayor que `0` para invocar el comportamiento original de clic izquierdo del widget ese número de veces cuando se cargue la pantalla. Por ejemplo, si la estableces en `2`, se hará clic en el widget dos veces durante la primera actualización de cada pantalla recién abierta. El valor predeterminado `0` desactiva los clics automatizados.

Estos son clics reales sobre el widget: cada clic puede cambiar el valor de un deslizador o de un botón cíclico, ejecutar la función de retorno normal del widget o incluso abrir otra pantalla. Prueba el resultado con cuidado, especialmente al configurar más de un clic.

Para **mover** y **redimensionar** widgets de vanilla o de mods, primero debes asignarles un punto de anclaje. Para hacerlo, haz **clic derecho** sobre ellos y pulsa **Punto de anclaje**. Cámbialo por cualquier opción distinta de **Original**, porque ese es el ancla predeterminada de los elementos de vanilla o de mods.

También puedes **ocultar** widgets de vanilla o de mods simplemente haciendo **clic derecho** sobre ellos y pulsando **Eliminar**. En realidad no se eliminan, sino que se ocultan, y puedes restaurarlos haciendo clic en **barra de menú -> Elemento -> Elementos vanilla eliminados** y haciendo **clic izquierdo** sobre el o los elementos que quieras volver a mostrar.

> [!WARNING]
> El widget de **Copyright** de la pantalla del título es el único que **NO PUEDES** ocultar/eliminar. Esto es intencionado. Por favor, no elimines los avisos de copyright.

## Elementos de la pantalla del título

La pantalla del título tiene elementos que no son widgets normales (como el logo, el texto aleatorio, etc.) y que no se pueden mover ni personalizar. Están pensados para eliminarse y sustituirse por elementos personalizados (como un elemento de Imagen para el logo o un elemento personalizado de Texto aleatorio para el texto aleatorio de vanilla).

Para eliminarlos, solo tienes que hacerles clic derecho. Si quieres restaurarlos más tarde, solo tienes que hacer clic en **barra de menú -> Elemento -> Elementos vanilla eliminados** y hacer **clic izquierdo** sobre el elemento que quieras volver a mostrar.

## Solución de problemas: los elementos vanilla no son visibles en el editor

Si no puedes ver los elementos vanilla en el editor, probablemente se deba a que estás usando un **diseño universal** en lugar de uno **para la pantalla actual**. Asegúrate de crear un diseño para la pantalla actual. Solo puedes crear diseños para la pantalla actual cuando las personalizaciones estén habilitadas para esa pantalla.

## Solución de problemas: las personalizaciones no se aplican

Si las personalizaciones de los elementos vanilla no se aplican fuera del editor, normalmente se debe a que otro mod sobrescribe o altera el menú padre de los elementos vanilla.

Un buen ejemplo de un mod que sobrescribe una pantalla/menú es **Ice and Fire**, que sobrescribe la pantalla del título.

Que las personalizaciones no se apliquen a los menús no se limita a los elementos vanilla. Es probable que los elementos personalizados añadidos a las pantallas tampoco se apliquen a los menús si un mod los está sobrescribiendo o alterando.
