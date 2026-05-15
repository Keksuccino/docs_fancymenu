---
title: Elementos básicos
description: >-
  Cómo personalizar los elementos que forman parte de las pantallas de forma
  predeterminada.
---

# Elementos básicos

FancyMenu no solo te permite añadir cosas nuevas a las pantallas, sino que también hace posible personalizar elementos existentes del juego base (Vanilla) e incluso de otros mods.

## Botones y deslizadores Vanilla (widgets)

Para personalizar widgets Vanilla/mod existentes, solo tienes que crear un nuevo diseño **«para la pantalla actual»** (¡NO universal!) y hacer **clic derecho** sobre los elementos en el editor igual que harías con los personalizados.

Puedes personalizar sus **etiquetas y texturas** igual que harías con botones y deslizadores personalizados.

Lo único que **no puedes hacer** con widgets Vanilla/mod es personalizar su **script de acción** (por ejemplo, cambiar lo que hacen al interactuar con ellos). Esto solo es posible con botones y deslizadores personalizados.

Para **mover** y **redimensionar** widgets Vanilla/mod, primero necesitas darles un punto de anclaje. Para ello, haz **clic derecho** sobre ellos y pulsa en **Anchor Point**. Cámbialo a cualquier opción distinta de **Original**, porque ese es el ancla predeterminada de los elementos Vanilla/mod.

También puedes **ocultar** widgets Vanilla/mod simplemente haciendo **clic derecho** sobre ellos y pulsando en **Delete**. En realidad no se eliminan, sino que se ocultan, y puedes restaurarlos haciendo clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y haciendo **clic izquierdo** sobre el/los elemento(s) que quieras volver a mostrar.

> El widget **Copyright** de la pantalla de título es el único que **NO PUEDES** ocultar/eliminar. Esto es intencionado. Por favor, no elimines los avisos de copyright.
{.is-warning}

## Elementos de la pantalla de título

La pantalla de título tiene elementos que no son widgets normales (como el logotipo, el texto de presentación, etc.) que no se pueden mover ni personalizar. Están pensados para eliminarse y sustituirse por elementos personalizados (como un elemento de imagen para el logotipo o un elemento personalizado de texto de presentación para el texto de presentación Vanilla).

Para eliminarlos, solo tienes que hacer clic derecho sobre ellos. Si quieres restaurarlos más adelante, solo tienes que hacer clic en **barra de menú -> Elemento -> Elementos Vanilla eliminados** y hacer **clic izquierdo** sobre el elemento que quieras volver a mostrar.

## Solución de problemas: los elementos Vanilla no son visibles en el editor

Si no puedes ver los elementos Vanilla en el editor, probablemente se deba a que estás usando un **diseño universal** en lugar de uno **para la pantalla actual**. Asegúrate de crear un diseño para la pantalla actual. Solo puedes crear diseños para la pantalla actual cuando las personalizaciones están activadas para esa pantalla.

## Solución de problemas: las personalizaciones no se aplican

Si las personalizaciones de elementos Vanilla no se aplican fuera del editor, normalmente se debe a que otro mod sobrescribe o altera el menú padre de los elementos Vanilla.

Un ejemplo bastante claro de un mod que sobrescribe una pantalla/menú es **Ice and Fire**, que sobrescribe la pantalla de título.

Que las personalizaciones no se apliquen a los menús no se limita a los elementos Vanilla. Es probable que los elementos personalizados añadidos a las pantallas tampoco se apliquen a los menús si un mod los está sobrescribiendo o alterando.
