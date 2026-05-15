---
title: Opacidad de elementos
description: Cómo controlar la opacidad de los elementos.
---

# Opacidad de elementos

La mayoría de los elementos en FancyMenu (con algunas excepciones) permiten configurar su opacidad desde su menú de clic derecho.

El valor de opacidad de los elementos admite placeholders, lo que hace posible actualizar su opacidad de forma dinámica según el placeholder.

Esto permite crear una lógica de desvanecimiento personalizada cuando se usa en combinación con elementos Ticker para actualizar valores de variables y luego aplicarlos como opacidad mediante placeholders.

Para configurar la opacidad de los elementos, **haz clic derecho en el elemento -> Opacidad -> Establecer**.

# Desvanecer elementos al aparecer/desaparecer

Si solo quieres que los elementos aparezcan o desaparezcan con un desvanecimiento, probablemente sea más fácil usar la función de desvanecimiento integrada de los elementos. Puedes habilitar el desvanecimiento en el menú de clic derecho de los elementos.

Esta función hace que los elementos se desvanezcan cada vez que se cargan, ya sea en la carga inicial al abrir un menú o cuando los requisitos de carga del elemento hacen que se cargue. Se desvanecerán al ocultarse siempre que sus requisitos de carga hagan que se descarguen o se vuelvan invisibles.

La función de desvanecimiento permite establecer una velocidad de desvanecimiento para controlar qué tan rápido debe aparecer o desaparecer un elemento.
