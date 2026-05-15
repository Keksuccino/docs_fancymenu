---
title: Nine-Slicing y Tiling
description: Cómo usar nine-slicing y tiling en FancyMenu.
---

# Nine-Slicing y Tiling

Cuando estás diseñando menús chulos en Minecraft con FancyMenu, quizá quieras usar imágenes que necesiten redimensionarse correctamente o repetirse en patrones. Esta guía explica cómo usar **Nine-Slicing** y **Tiling** (también llamado texturas repetidas) para que tus menús se vean geniales.

# ¿Qué es Nine-Slicing?

Nine-slicing es una técnica que permite estirar una imagen a cualquier tamaño sin que se vea rara. Funciona dividiendo la imagen en nueve partes (como un tablero de tres en raya). Las esquinas se mantienen del mismo tamaño, los bordes se estiran en una sola dirección y la parte central se estira en ambas direcciones.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Ejemplo de Nine-Slice" style="max-width: 500px; height: auto;" />

## ¿Dónde puedo usar Nine-Slicing?

En FancyMenu, Nine-Slicing está disponible para:
- **Elementos de botón** (tanto botones personalizados como al editar botones de Vanilla)
- **Texturas de barra de progreso** (texturas de la barra y del fondo)

## Cómo usar Nine-Slicing con botones

1. **Crea o selecciona un elemento de botón** en tu editor de diseño.
2. Haz clic derecho en el botón y busca la opción "Button Textures".
3. Establece las texturas de fondo de tu botón (estados normal, al pasar el cursor e inactivo).
4. Activa la opción "Nine-Slice Custom Background".
5. Define los **Nine-Slice Background X-Borders** (tamaño del borde izquierdo y derecho).
6. Define los **Nine-Slice Background Y-Borders** (tamaño del borde superior e inferior).

### Consejos para Nine-Slicing en botones

- Usa una imagen con bordes y esquinas bien definidos.
- Los valores de borde (X e Y) indican a FancyMenu cuántos píxeles desde cada borde deben tratarse como borde.
- Un valor típico podría ser 5 píxeles tanto para los bordes X como para los Y.
- Las esquinas siempre mantendrán el mismo tamaño, mientras que las partes centrales se estirarán para rellenar el botón.

# ¿Qué es Tiling?

Tiling (también llamado texturas repetidas) te permite rellenar un área grande con una imagen pequeña repitiéndola como baldosas en el suelo. Es perfecto para fondos o imágenes grandes en las que quieres que un patrón continúe.

## ¿Dónde puedo usar Tiling?

En FancyMenu, Tiling está disponible para:
- **Elementos de imagen**
- **Fondos de menú de imagen**

## Cómo usar Tiling con elementos de imagen

1. **Crea o selecciona un elemento de imagen** en tu editor de diseño.
2. Haz clic derecho en la imagen y busca "Image Source" para establecer tu textura.
3. Busca y activa la opción **"Repeat Texture"**.
4. Redimensiona el elemento de imagen para ver cómo la textura se repite y rellena el espacio.

## Cómo usar Tiling con fondos de menú

1. Abre **Menu Backgrounds** desde el menú contextual de fondo del editor de diseño.
2. Elige el tipo de fondo **Image**.
3. Selecciona tu imagen de fondo.
4. Activa la opción **"Repeat Texture"**.
5. Tu fondo repetirá ahora la textura para rellenar toda la pantalla.

# Cómo crear buenas texturas para Nine-Slicing y Tiling

## Para Nine-Slicing:
- Crea texturas con bordes y esquinas bien diferenciados.
- Asegúrate de que los bordes sean claros y tengan un ancho uniforme.
- Prueba distintos tamaños de borde para encontrar el que mejor funcione.
- Los botones suelen funcionar bien con bordes de 3 a 5 píxeles.

## Para Tiling:
- Crea texturas sin juntas visibles que puedan encajar consigo mismas por todos los lados.
- Mantén los patrones simples para evitar confusión visual.
- Prueba la textura repitiéndola primero en un área pequeña.

# Ejemplos

## Ejemplo de botón con Nine-Slicing
Un botón sencillo podría partir de una imagen de 30x30 con bordes de 5 píxeles en todos los lados. Cuando haces el botón más grande, las esquinas se mantienen en 5x5 píxeles, mientras que los bordes y el centro se estiran para adaptarse al tamaño del botón.

## Ejemplo de fondo en mosaico
Un mosaico pequeño de 64x64 con un patrón sutil puede repetirse para rellenar todo el fondo de tu menú, sin importar el tamaño de la pantalla.

# Problemas comunes y soluciones

## Mi botón con nine-slicing se ve estirado o deformado:
- Puede que los valores de borde sean demasiado pequeños o demasiado grandes
- Prueba a cambiar los valores de borde para que coincidan con tu textura real

## Mi fondo repetido tiene juntas visibles:
- Tu textura no es continua
- Prueba a editar la imagen para asegurarte de que los bordes encajan perfectamente

## Mis texturas se ven borrosas al escalarlas:
- Usa texturas de mayor resolución
- Mantén tus diseños simples y con líneas limpias

# Recuerda

- **Nine-Slicing** es perfecto para elementos de interfaz que necesitan cambiar de tamaño sin perder su aspecto (como los botones).
- **Tiling** es ideal para rellenar áreas grandes con un patrón (como los fondos).
- ¡Ambas funciones ayudan a que tu interfaz se vea bien a cualquier resolución o tamaño de pantalla!

¡Ahora ve y crea menús de Minecraft increíbles con botones perfectamente estirados y preciosos fondos en mosaico!
