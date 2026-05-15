---
title: Pantallas desplazables
description: Cómo personalizar pantallas desplazables.
---

# Personalizar pantallas desplazables

Personalizar pantallas desplazables, como las pantallas de opciones, puede ser un poco complicado, ya que FancyMenu no puede "ver" ni personalizar el contenido dentro de las áreas desplazables.

Desde FancyMenu v3.6.0+, es posible hacer que ALGUNAS de estas pantallas sean personalizables exponiendo automáticamente los widgets dentro de las áreas desplazables de una pantalla específica. Esto es bastante potente, pero también bastante experimental, así que no funcionará en todas las pantallas.

Para activar la función de exposición en una pantalla concreta, haz clic en **barra de menú -> Personalización -> Exponer el contenido del área desplazable de la pantalla actual**. No es posible activar esta función para todas las pantallas a la vez y algunas pantallas no permitirán activarla en absoluto, como los menús de Un jugador y Multijugador.

Al activar esta función, todos los widgets encontrados en las áreas desplazables se apilarán en la esquina superior izquierda de la pantalla. Esto es intencionado y no un error. Después puedes abrir un diseño **para la pantalla actual** y deberías poder ver y editar (mover, cambiar el tamaño, etc.) estos widgets en el editor.

Lo más importante que hay que tener en cuenta al usar esta función es que exponer los widgets del área desplazable ELIMINARÁ el área desplazable original de la pantalla y todo lo que haya dentro del área desplazable que no sea un widget normal (los widgets son botones y deslizadores) se PERDERÁ, por lo que no será visible ni interactuable mientras la función de exposición esté activada.
