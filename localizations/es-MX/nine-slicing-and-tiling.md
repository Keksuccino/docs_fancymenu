---
title: Nine-Slicing y Repetición
description: Cómo usar nine-slicing y repetición en FancyMenu.
---

# Nine-Slicing y Repetición

Cuando estás diseñando menús geniales en Minecraft con FancyMenu, quizá quieras usar imágenes que necesiten redimensionarse correctamente o repetirse en patrones. Esta guía explica cómo usar **Nine-Slicing** y **Repetición** (también llamadas texturas repetidas) para que tus menús se vean increíbles.

# ¿Qué es Nine-Slicing?

Nine-slicing es una técnica que te permite estirar una imagen a cualquier tamaño sin que se vea rara. Funciona dividiendo tu imagen en nueve partes (como un tablero de gato). Las esquinas conservan el mismo tamaño, los bordes se estiran en una sola dirección y el centro se estira en ambas direcciones.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Ejemplo de Nine-Slice" style="max-width: 500px; height: auto;" />

## ¿Dónde puedo usar Nine-Slicing?

En FancyMenu, Nine-Slicing está disponible para:
- **Elementos de botón** (tanto botones personalizados como al editar botones de Vanilla)
- **Texturas de barra de progreso** (texturas de la barra y del fondo)

## Cómo usar Nine-Slicing con botones

1. **Crea o selecciona un elemento de botón** en tu editor de diseño.
2. Haz clic derecho sobre el botón y busca la opción "Button Textures".
3. Configura las texturas de fondo de tu botón (estados normal, al pasar el cursor e inactivo).
4. Activa la opción "Nine-Slice Custom Background".
5. Define los **Nine-Slice Background X-Borders** (tamaño del borde izquierdo y derecho).
6. Define los **Nine-Slice Background Y-Borders** (tamaño del borde superior e inferior).

### Consejos para Nine-Slicing en botones

- Usa una imagen con bordes y esquinas bien definidos.
- Los valores de borde (X e Y) le indican a FancyMenu cuántos píxeles desde cada borde deben tratarse como borde.
- Un valor típico podría ser 5 píxeles tanto para los bordes X como Y.
- Las esquinas siempre conservarán el mismo tamaño, mientras que las partes del centro se estirarán para llenar el botón.

# ¿Qué es la repetición?

La repetición (también llamada texturas repetidas) te permite llenar un área grande con una imagen pequeña repitiéndola como mosaicos en el piso. Esto es perfecto para fondos o imágenes grandes donde quieres que un patrón continúe.

## ¿Dónde puedo usar la repetición?

En FancyMenu, la repetición está disponible para:
- **Elementos de imagen**
- **Fondos de menú de imagen**

## Cómo usar la repetición con elementos de imagen

1. **Crea o selecciona un elemento de imagen** en tu editor de diseño.
2. Haz clic derecho sobre la imagen y busca "Image Source" para definir tu textura.
3. Busca y activa la opción **"Repeat Texture"**.
4. Cambia el tamaño de tu elemento de imagen para ver cómo la textura se repite y llena el espacio.

## Cómo usar la repetición con fondos de menú

1. Abre **Menu Backgrounds** desde el menú contextual de fondo del editor de diseño.
2. Elige el tipo de fondo **Image**.
3. Selecciona tu imagen de fondo.
4. Activa la opción **"Repeat Texture"**.
5. Tu fondo ahora repetirá la textura para llenar toda la pantalla.

# Cómo crear buenas texturas para Nine-Slicing y Repetición

## Para Nine-Slicing:
- Crea texturas con bordes y esquinas bien diferenciados.
- Asegúrate de que tus bordes sean claros y tengan un ancho consistente.
- Prueba diferentes tamaños de borde para encontrar lo que mejor funcione.
- Los botones suelen funcionar bien con bordes de 3 a 5 píxeles.

## Para Repetición:
- Crea texturas sin costuras que puedan conectarse consigo mismas en todos los lados.
- Mantén los patrones simples para evitar confusión visual.
- Prueba tu textura repitiéndola primero en un área pequeña.

# Ejemplos

## Ejemplo de botón con Nine-Slicing
Un botón sencillo podría comenzar como una imagen de 30x30 con bordes de 5 píxeles en todos los lados. Cuando haces el botón más grande, las esquinas se mantienen en 5x5 píxeles, mientras que los bordes y el centro se estiran para ajustarse al tamaño del botón.

## Ejemplo de fondo repetido
Un mosaico pequeño de 64x64 con un patrón sutil puede repetirse para llenar todo el fondo de tu menú, sin importar el tamaño de la pantalla.

# Problemas comunes y soluciones

## Mi botón con nine-slicing se ve estirado o distorsionado:
- Tus valores de borde pueden ser demasiado pequeños o demasiado grandes.
- Intenta cambiar los valores de borde para que coincidan con tu textura real.

## Mi fondo repetido tiene uniones visibles:
- Tu textura no es sin costuras.
- Intenta editar tu imagen para asegurarte de que los bordes coincidan perfectamente.

## Mis texturas se ven borrosas al escalarse:
- Usa texturas de mayor resolución.
- Mantén tus diseños simples y con líneas limpias.

# Recuerda

- **Nine-Slicing** es perfecto para elementos de la interfaz que necesitan cambiar de tamaño pero conservar su apariencia, como los botones.
- **La repetición** es ideal para llenar áreas grandes con un patrón, como los fondos.
- ¡Ambas funciones ayudan a que tu interfaz se vea bien en cualquier resolución o tamaño de pantalla!

¡Ahora crea menús increíbles de Minecraft con botones perfectamente estirados y hermosos fondos repetidos!
