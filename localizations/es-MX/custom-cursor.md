---
title: Cursor personalizado
description: Cómo hacer que los menús usen un cursor de mouse personalizado.
---
# Cursor de mouse personalizado

Agrega un [**elemento Cursor**](./elements#cursor) a un diseño para reemplazar el cursor del sistema en esa pantalla:

1. Selecciona **Nuevo elemento -> Cursor**.
2. Establece una textura PNG con color RGBA.
3. Configura **Hotspot X** y **Hotspot Y** en el píxel de la textura donde deben ocurrir los clics.
4. Activa la vista previa del editor cuando quieras revisar el cursor mientras editas.
5. Usa un [Diseño universal](./universal-layouts) cuando el mismo cursor deba aparecer en varias pantallas compatibles.

Se recomiendan texturas de cursor pequeñas, como `32×32` o `64×64`. La apariencia y el comportamiento del cursor pueden variar según el sistema operativo.
