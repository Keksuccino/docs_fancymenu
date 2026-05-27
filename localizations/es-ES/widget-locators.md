---
title: Localizadores de widgets
description: Qué son los localizadores de widgets y cómo encontrarlos.
---
# Localizadores de widgets

Los localizadores de widgets se usan para señalar un widget específico de Vanilla (botón, deslizador, campo de entrada de texto) en un menú, lo cual es necesario para algunas funciones de FancyMenu que necesitan interactuar con un widget de alguna manera.

# Cómo obtener el localizador de un widget

Hay dos formas de obtener el localizador de un widget de Vanilla.

La primera es activar la **superposición de depuración** en el menú que contiene el widget, pulsando **CTRL + ALT + D**, y luego **hacer clic derecho sobre el widget**, lo que abrirá un menú contextual con la opción de copiar el localizador al portapapeles.

La segunda es abrir el **editor de diseño** del menú que contiene el widget, y luego **hacer clic derecho sobre el elemento del widget**, lo que también abrirá un menú contextual con la opción de copiar el localizador al portapapeles.

>[!WARNING]
>Si **no puedes hacer clic derecho** sobre el widget mediante la superposición de depuración, o **no aparece** en el editor de diseño, probablemente no sea visible para FancyMenu, lo que significa que en ese caso no tiene un localizador. Esto suele ocurrir con botones de mods que se añaden a los menús de formas extrañas.
