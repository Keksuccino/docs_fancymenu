---
title: Elementos Vanilla
description: Cómo personalizar los elementos que forman parte de las pantallas por defecto.
---
# Elementos Vanilla

FancyMenu no solo te permite añadir cosas nuevas a las pantallas, sino que también hace posible personalizar elementos existentes del juego base (Vanilla) e incluso de otros mods.

## Botones y deslizadores Vanilla (widgets)

Para personalizar widgets Vanilla/mod existentes, solo tienes que crear un nuevo diseño **"para la pantalla actual"** (¡NO universal!) y hacer **clic derecho** sobre los elementos en el editor, igual que harías con los personalizados.

Puedes personalizar sus **etiquetas y texturas** igual que harías con botones y deslizadores personalizados.

Lo único que **no puedes hacer** con widgets Vanilla/mod es personalizar su **script de acción** (por ejemplo, cambiar lo que hacen al interactuar con ellos). Esto solo es posible con botones y deslizadores personalizados.

## Clics automatizados

Los widgets Vanilla y de mods tienen una propiedad de **Clics automatizados**. Establécela en un entero mayor que `0` para invocar el comportamiento original de clic izquierdo del widget ese número de veces cuando se cargue la pantalla. Por ejemplo, si se establece en `2`, se hace clic en el widget dos veces durante la primera actualización de cada pantalla recién abierta. El valor predeterminado `0` desactiva los clics automatizados.

Se trata de clics reales sobre el widget: cada clic puede cambiar el valor de un deslizador o de un botón cíclico, ejecutar la devolución de llamada normal del widget o incluso abrir otra pantalla. Comprueba el resultado con cuidado, especialmente cuando configures más de un clic.

Para **mover** y **redimensionar** widgets Vanilla/mod, primero necesitas asignarles un punto de anclaje. Para ello, haz **clic derecho** sobre ellos y luego haz clic en **Punto de anclaje**. Configúralo a cualquier opción distinta de **Original**, porque ese es el anclaje predeterminado de los elementos Vanilla/mod.

También puedes **ocultar** widgets Vanilla/mod simplemente haciendo **clic derecho** sobre ellos y luego clic en **Eliminar**. En realidad no se eliminan, sino que se ocultan, y puedes restaurarlos haciendo clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y luego **clic izquierdo** sobre el/los elemento(s) que quieras volver a mostrar.

> El widget de **Copyright** de la pantalla de título es el único que **NO PUEDES** ocultar/eliminar. Está hecho así a propósito. Por favor, no elimines los avisos de copyright.
{.is-warning}

## Elementos de la pantalla de título

La pantalla de título tiene elementos que no son widgets normales (como el logotipo, el texto de presentación, etc.) y que no se pueden mover ni personalizar. Están pensados para ser eliminados y sustituidos por elementos personalizados (como un elemento de Imagen para el logotipo o un elemento de Texto de presentación personalizado para el texto de presentación Vanilla).

Para eliminarlos, simplemente haz clic derecho sobre ellos. Si quieres restaurarlos más tarde, solo tienes que hacer clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y hacer **clic izquierdo** sobre el elemento que quieras volver a mostrar.

## Solución de problemas: los elementos Vanilla no son visibles en el editor

Si no puedes ver los elementos Vanilla en el editor, probablemente se deba a que estás usando un **diseño universal** en lugar de uno **para la pantalla actual**. Asegúrate de crear un diseño para la pantalla actual. Solo puedes crear diseños para la pantalla actual cuando las personalizaciones están habilitadas para esa pantalla.

## Solución de problemas: las personalizaciones no se aplican

Si las personalizaciones de elementos Vanilla no se aplican fuera del editor, normalmente se debe a que otro mod está sobrescribiendo o alterando el menú principal de los elementos Vanilla.

Un buen ejemplo de un mod que sobrescribe una pantalla/menú es **Ice and Fire**, que sobrescribe la pantalla de título.

Que las personalizaciones no se apliquen a los menús no se limita a los elementos Vanilla. También es probable que los elementos personalizados añadidos a las pantallas no se apliquen a los menús si un mod los está sobrescribiendo o alterando.
