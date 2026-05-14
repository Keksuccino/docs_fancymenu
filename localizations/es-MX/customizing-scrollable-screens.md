---
title: Pantallas con desplazamiento
description: Cómo personalizar pantallas con desplazamiento.
---

# Personalizar pantallas con desplazamiento

Personalizar pantallas con desplazamiento, como las pantallas de Opciones, puede ser un poco complicado, ya que FancyMenu no puede "ver" ni personalizar el contenido dentro de las áreas de desplazamiento.

Desde FancyMenu v3.6.0+, es posible hacer que ALGUNAS de estas pantallas se puedan personalizar exponiendo automáticamente los widgets dentro de las áreas de desplazamiento de una pantalla específica. Esto es muy potente, pero también bastante experimental, así que no funcionará en todas las pantallas.

Para habilitar la función de exposición para una pantalla específica, haz clic en **barra de menú -> Personalización -> Exponer el contenido del área de desplazamiento de la pantalla actual**. No es posible habilitar esta función para todas las pantallas al mismo tiempo, y algunas pantallas no permitirán habilitarla en absoluto, como los menús de Un jugador y Multijugador.

Al habilitar esta función, todos los widgets que se encuentren en áreas de desplazamiento se apilarán en la esquina superior izquierda de la pantalla. Esto es intencional y no es un error. Luego puedes abrir un diseño **para la pantalla actual** y deberías poder ver y editar (mover, cambiar el tamaño, etc.) estos widgets en el editor.

Lo más importante que debes tener en cuenta al usar esta función es que exponer los widgets del área de desplazamiento ELIMINARÁ el área de desplazamiento original de la pantalla y todo lo que esté dentro del área de desplazamiento que no sea un widget normal (los widgets son botones y controles deslizantes) se PERDERÁ, así que no será visible ni se podrá interactuar con ello mientras la función de exposición esté habilitada.
