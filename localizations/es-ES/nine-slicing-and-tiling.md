---
title: División en nueve partes y repetición
description: >-
  Haz que las texturas con marcos se adapten a cualquier tamaño sin deformarse,
  o repite un patrón en lugar de estirarlo.
sourceBlobSha: 0dca8e7070606cdafccd9edc23a77535048d4ba3
---

# División en nueve partes y repetición

Tus propias texturas se estiran hasta alcanzar el tamaño del elemento. Esto está bien para las fotografías, pero los marcos, paneles y botones con bordes se deforman al ensancharse o alargarse. Hay dos ajustes que lo solucionan:

- La división en nueve partes conserva la forma de las esquinas y los bordes de una textura y solo rellena la parte central.
- La repetición reproduce una textura en lugar de estirarla, para que el patrón mantenga su tamaño.

<img width="800" alt="Una textura de panel cuadrado dividida en nueve partes mediante cuatro líneas, y la misma textura en un panel ancho cuyas esquinas y bordes conservan su forma" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png">

# Cómo funciona la división en nueve partes

Cuatro líneas dividen la textura en nueve partes. Las cuatro esquinas siempre mantienen el mismo tamaño, los bordes solo se alargan y la parte central rellena el espacio restante.

1. Configura la textura.
2. Activa la opción de división en nueve partes. Consulta [Dónde funciona](#dónde-funciona) para saber cómo se llama.
3. Establece el grosor de los bordes en píxeles de la textura. Si el marco tiene 4 píxeles de grosor, usa `4`.

A tener en cuenta:

- Los bordes se muestran en pantalla con el mismo tamaño que tienen en la textura. Por eso, una textura con bordes de 40 píxeles puede quedar demasiado recargada en un botón pequeño. Procura que la textura tenga un tamaño parecido al del elemento.
- La mayoría de las texturas tienen un mismo tamaño para los bordes izquierdo y derecho (bordes X) y otro para los bordes superior e inferior (bordes Y). Las barras de progreso, las ventanas emergentes y las personalizaciones globales tienen un tamaño para cada lado.
- Si los bordes son demasiado grandes para la textura, se reducen automáticamente.

# Dónde funciona

| Textura | División en nueve partes | Repetición |
|---|---|---|
| Texturas de [botones](/elements#button), en **Texturas de botones** | **Fondo personalizado con división en nueve partes** | - |
| Texturas de [deslizadores](/elements#slider), en **Texturas de deslizadores** | **Fondo personalizado con división en nueve partes** y **Controlador personalizado con división en nueve partes** | - |
| Elementos de [imagen](/elements#image) | **Textura con división en nueve partes** | **Repetir textura** |
| El **fondo** de los elementos de [texto](/text-in-menus#background) y las [áreas desplazables](/scrollable-areas#background) | **Fondo personalizado con división en nueve partes** | **Mosaico de textura** |
| **Fondos de las barras de desplazamiento** de los elementos de texto y las áreas desplazables | Siempre activada | - |
| El **fondo** de los elementos de [ventana emergente](/elements#tooltip) | Siempre activada; tamaños en **Ajustes de división en nueve partes** | - |
| Texturas de [barras de progreso](/elements#progress-bar) | **Textura de barra con división en nueve partes** y **Textura de fondo con división en nueve partes** | - |
| [Texturas globales de botones y deslizadores](/global-customizations#buttons-and-sliders) | **Fondos de botones con división en nueve partes**, **Fondo de deslizador con división en nueve partes** y **Controlador de deslizador con división en nueve partes** | - |
| [Fondos de menú con imagen](/menu-backgrounds#image) | - | **Repetir textura** |
| Encabezado y pie de página de las [pantallas desplazables](/customizing-scrollable-screens) | - | **Repetir textura del encabezado** y **Repetir textura del pie de página** |

## Fondos de los elementos de texto y las áreas desplazables

Abre **Fondo** desde el menú del botón derecho de un elemento de texto o un área desplazable:

- **Textura de fondo personalizada** sustituye el panel oscuro integrado por tu propia textura. Restablécela para recuperar el panel.
- **Fondo personalizado con división en nueve partes** está activada de forma predeterminada. Ajusta los bordes con **Bordes X del fondo con división en nueve partes (izquierda y derecha)** y **Bordes Y del fondo con división en nueve partes (arriba y abajo)**.
- **Mosaico de textura** repite la textura en lugar de estirarla. Si también está activada la división en nueve partes, se repiten los bordes y la parte central, mientras que las esquinas permanecen como están.
- **Mostrar fondo** desactiva todo el fondo.

## Fondos de las barras de desplazamiento

Abre **Barras de desplazamiento -> Fondos de las barras de desplazamiento** en un elemento de texto o un área desplazable. **Textura de barra vertical** y **Textura de barra horizontal** dibujan una textura a lo largo del recorrido del controlador de desplazamiento. Siempre se aplica la división en nueve partes, de modo que los extremos conservan su forma en barras de cualquier longitud. Ajusta los bordes con los dos ajustes de bordes que aparecen debajo.

# Cómo funciona la repetición

La repetición coloca la textura junto a sí misma tantas veces como quepa, manteniendo su tamaño original. Usa una textura sin uniones, en la que el borde izquierdo encaje con el derecho y el borde superior con el inferior. De lo contrario, verás líneas entre las repeticiones.

En los elementos de imagen, **Repetir textura** y **Textura con división en nueve partes** no funcionan a la vez. Si activas ambas opciones, la imagen se repite.
