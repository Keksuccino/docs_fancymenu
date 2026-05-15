---
title: Elementos Vanilla
description: Cómo personalizar elementos que forman parte de las pantallas por defecto.
---

# Elementos Vanilla

FancyMenu no solo te permite agregar cosas nuevas a las pantallas, sino que también hace posible personalizar elementos existentes del juego base (Vanilla) e incluso de otros mods.

## Botones y deslizadores Vanilla (widgets)

Para personalizar widgets existentes de Vanilla/mod, solo crea un nuevo diseño **"para la pantalla actual"** (¡NO universal!) y haz **clic derecho** sobre los elementos en el editor, igual que lo harías con los personalizados.

Puedes personalizar sus **etiquetas y texturas** igual que lo harías con botones y deslizadores personalizados.

Lo único que **no puedes hacer** con widgets de Vanilla/mod es personalizar su **script de acción** (como cambiar lo que hacen al interactuar con ellos). Esto solo es posible con botones y deslizadores personalizados.

Para **mover** y **cambiar el tamaño** de widgets de Vanilla/mod, primero necesitas asignarles un punto de anclaje. Para hacerlo, haz **clic derecho** sobre ellos y luego clic en **Punto de anclaje**. Cámbialo a cualquier opción distinta de **Original**, porque ese es el anclaje predeterminado de los elementos Vanilla/mod.

También puedes **ocultar** widgets de Vanilla/mod simplemente haciendo **clic derecho** sobre ellos y luego clic en **Eliminar**. En realidad no se eliminan, solo se ocultan, y puedes restaurarlos haciendo clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y luego **clic izquierdo** sobre el/los elemento(s) que quieras volver a mostrar.

> El widget de **Copyright** en la pantalla de título es el único que **NO PUEDES** ocultar/eliminar. Esto es intencional. Por favor, no elimines los avisos de copyright.
{.is-warning}

## Elementos de la pantalla de título

La pantalla de título tiene elementos que no son widgets normales (como el logo, el texto aleatorio, etc.) y que no se pueden mover ni personalizar. La idea es eliminarlos y reemplazarlos con elementos personalizados (como un elemento de Imagen para el logo o un elemento personalizado de Texto aleatorio para el texto aleatorio Vanilla).

Para eliminarlos, solo haz clic derecho sobre ellos. Si quieres restaurarlos después, solo haz clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y luego **clic izquierdo** sobre el elemento que quieras volver a mostrar.

## Solución de problemas: los elementos Vanilla no se ven en el editor

Si no puedes ver los elementos Vanilla en el editor, probablemente se deba a que estás usando un **diseño universal** en lugar de uno **para la pantalla actual**. Asegúrate de crear un diseño para la pantalla actual. Solo puedes crear diseños para la pantalla actual cuando las personalizaciones están habilitadas para esa pantalla.

## Solución de problemas: las personalizaciones no se aplican

Si las personalizaciones de elementos Vanilla no se aplican fuera del editor, por lo general se debe a que otro mod está sobrescribiendo o modificando el menú principal de esos elementos Vanilla.

Un muy buen ejemplo de un mod que sobrescribe una pantalla/menú es **Ice and Fire**, que sobrescribe la pantalla de título.

Que las personalizaciones no se apliquen a los menús no se limita a los elementos Vanilla. Es probable que los elementos personalizados agregados a las pantallas tampoco se apliquen a los menús si un mod los está sobrescribiendo o modificando.
