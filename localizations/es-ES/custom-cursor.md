---
title: Cursor personalizado
description: Cómo hacer que los menús utilicen un cursor del ratón personalizado.
sourceBlobSha: 6ccd4932bed99ab10c094adffd503bd0a44d9edd
---

# Cursor del ratón personalizado

Añade un [elemento **Cursor**](/elements#cursor) a un diseño para sustituir el cursor del sistema en esa pantalla:

1. Selecciona **Nuevo elemento -> Cursor**.
2. Establece una textura PNG con color RGBA.
3. Establece **Punto activo X** y **Punto activo Y** en el píxel de la textura donde deben producirse los clics.
4. Activa la vista previa del editor cuando quieras comprobar el cursor mientras editas.
5. Utiliza un [diseño universal](/universal-layouts) si quieres que aparezca el mismo cursor en varias pantallas compatibles.

Se recomiendan texturas de cursor pequeñas, como `32×32` o `64×64`. El aspecto y el comportamiento del cursor pueden variar según el sistema operativo.
