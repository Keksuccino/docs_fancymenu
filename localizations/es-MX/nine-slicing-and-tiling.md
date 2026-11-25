---
title: División en nueve partes y mosaico
description: >-
  Haz que las texturas con marcos se adapten a cualquier tamaño sin deformarse,
  o repite un patrón en lugar de estirarlo.
sourceBlobSha: 0dca8e7070606cdafccd9edc23a77535048d4ba3
---

# División en nueve partes y mosaico

Tus propias texturas se estiran para ajustarse al tamaño del elemento. Esto está bien para las fotos, pero los marcos, paneles y botones con bordes se deforman cuando se hacen más anchos o más altos. Hay dos opciones para solucionarlo:

- La división en nueve partes mantiene la forma de las esquinas y los bordes de una textura y solo rellena la parte del medio.
- El mosaico repite una textura en lugar de estirarla, así que el patrón conserva su tamaño.

<img width="800" alt="Una textura de panel cuadrada dividida en nueve partes por cuatro líneas, y la misma textura como panel ancho con las esquinas y los bordes sin deformar" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png">

# Cómo funciona la división en nueve partes

Cuatro líneas dividen la textura en nueve partes. Las cuatro esquinas siempre conservan el mismo tamaño, los bordes solo se alargan y la parte del medio rellena el espacio restante.

1. Configura tu textura.
2. Activa la opción de división en nueve partes. Consulta [Dónde funciona](#where-it-works) para ver cómo se llama.
3. Configura el tamaño de los bordes según el grosor del marco de tu textura, en píxeles de la textura. Si el marco tiene 4 píxeles de grosor, usa `4`.

Ten en cuenta lo siguiente:

- Los bordes se ven en pantalla con el mismo tamaño que tienen en la textura. Por eso, una textura con bordes de 40 píxeles se ve muy tosca en un botón pequeño. Procura que la textura tenga un tamaño parecido al del elemento.
- La mayoría de las texturas tienen un solo tamaño para los bordes izquierdo y derecho (bordes X) y otro para los bordes superior e inferior (bordes Y). Las barras de progreso, las ayudas emergentes y las personalizaciones globales tienen un tamaño para cada lado.
- Si los bordes son demasiado grandes para la textura, su tamaño se reduce automáticamente.

# Dónde funciona

| Textura | División en nueve partes | Mosaico |
|---|---|---|
| Texturas de [botones](/elements#button), en **Texturas de botones** | **Fondo personalizado con división en nueve partes** | - |
| Texturas de [controles deslizantes](/elements#slider), en **Texturas de controles deslizantes** | **Fondo personalizado con división en nueve partes** y **Control personalizado con división en nueve partes** | - |
| Elementos de [imagen](/elements#image) | **Textura con división en nueve partes** | **Repetir textura** |
| El **fondo** de los elementos de [texto](/text-in-menus#background) y las [áreas desplazables](/scrollable-areas#background) | **Fondo personalizado con división en nueve partes** | **Textura en mosaico** |
| **Fondos de barras de desplazamiento** de elementos de texto y áreas desplazables | siempre activada | - |
| El **fondo** de los elementos de [ayuda emergente](/elements#tooltip) | siempre activada; tamaños en **Configuración de división en nueve partes** | - |
| Texturas de [barras de progreso](/elements#progress-bar) | **Textura de barra con división en nueve partes** y **Textura de fondo con división en nueve partes** | - |
| [Texturas globales de botones y controles deslizantes](/global-customizations#buttons-and-sliders) | **Fondos de botones con división en nueve partes**, **Fondo de control deslizante con división en nueve partes** y **Control de control deslizante con división en nueve partes** | - |
| [Fondos de menú con imagen](/menu-backgrounds#image) | - | **Repetir textura** |
| Encabezado y pie de página de las [pantallas desplazables](/customizing-scrollable-screens) | - | **Repetir textura del encabezado** y **Repetir textura del pie de página** |

## Fondos de elementos de texto y áreas desplazables

Abre **Fondo** en el menú que aparece al hacer clic derecho en un elemento de texto o un área desplazable:

- **Textura de fondo personalizada** reemplaza el panel oscuro integrado con tu propia textura. Restablécela para recuperar el panel.
- **Fondo personalizado con división en nueve partes** está activada de forma predeterminada. Configura los bordes con **Bordes X del fondo con división en nueve partes (izquierdo y derecho)** y **Bordes Y del fondo con división en nueve partes (superior e inferior)**.
- **Textura en mosaico** repite la textura en lugar de estirarla. Al combinarla con la división en nueve partes, se repiten los bordes y la parte del medio, mientras que las esquinas conservan su forma.
- **Mostrar fondo** desactiva todo el fondo.

## Fondos de barras de desplazamiento

Abre **Barras de desplazamiento -> Fondos de barras de desplazamiento** en un elemento de texto o un área desplazable. **Textura de barra vertical** y **Textura de barra horizontal** dibujan una textura a lo largo del recorrido del control de desplazamiento. Siempre se dividen en nueve partes, así que sus extremos conservan la forma en barras de cualquier longitud. Configura los bordes con las dos opciones de bordes que aparecen debajo.

# Cómo funciona el mosaico

El mosaico coloca la textura junto a sí misma tantas veces como quepa, con su tamaño original. Usa una textura sin uniones, en la que el borde izquierdo encaje con el derecho y el borde superior con el inferior. De lo contrario, verás líneas entre los mosaicos.

En los elementos de imagen, **Repetir textura** y **Textura con división en nueve partes** no funcionan al mismo tiempo. Si ambas opciones están activadas, la imagen se repite.
