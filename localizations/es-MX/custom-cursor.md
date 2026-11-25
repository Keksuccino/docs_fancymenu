---
title: Cursor personalizado
description: Cómo hacer que los menús usen un cursor personalizado.
sourceBlobSha: 6ccd4932bed99ab10c094adffd503bd0a44d9edd
---

# Cursor personalizado del mouse

Agrega un [elemento **Cursor**](/elements#cursor) a un diseño para reemplazar el cursor del sistema en esa pantalla:

1. Selecciona **Nuevo elemento -> Cursor**.
2. Configura una textura PNG con color RGBA.
3. Configura **Hotspot X** y **Hotspot Y** en el píxel de la textura donde deben ocurrir los clics.
4. Activa la vista previa del editor cuando quieras revisar el cursor mientras editas.
5. Usa un [diseño universal](/universal-layouts) si quieres que aparezca el mismo cursor en varias pantallas compatibles.

Se recomiendan texturas pequeñas para el cursor, como `32×32` o `64×64`. La apariencia y el comportamiento del cursor pueden variar según el sistema operativo.
