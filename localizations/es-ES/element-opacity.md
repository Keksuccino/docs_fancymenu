---
title: Opacidad de elementos
description: Cómo controlar la opacidad de los elementos.
---

# Opacidad de elementos

La mayoría de los elementos de FancyMenu (con algunas excepciones) permiten configurar su opacidad mediante su menú contextual con clic derecho.

El valor de opacidad de los elementos admite placeholders, lo que permite actualizar su opacidad de forma dinámica en función del placeholder.

Esto hace posible crear una lógica de desvanecimiento personalizada cuando se combina con elementos Ticker para actualizar valores de variables y luego aplicarlos como opacidad mediante placeholders.

Para establecer la opacidad de los elementos, **clic derecho en el elemento -> Opacidad -> Establecer**.

# Desvanecer elementos al aparecer/desaparecer

Si simplemente quieres que los elementos aparezcan o desaparezcan con un desvanecimiento, probablemente sea más fácil usar la función de desvanecimiento integrada de los elementos. Puedes activar el desvanecimiento en el menú contextual con clic derecho de los elementos.

Esta función hace que los elementos aparezcan con un desvanecimiento cada vez que se cargan, ya sea durante la carga inicial al abrir un menú o cuando los requisitos de carga del elemento hacen que se cargue. Desaparecerán con un desvanecimiento siempre que sus requisitos de carga provoquen que se descarguen o queden invisibles.

La función de desvanecimiento permite establecer una velocidad de desvanecimiento para controlar con qué rapidez debe aparecer o desaparecer un elemento.
