---
title: Efecto Parallax
description: Mueve fondos y elementos con el cursor del mouse.
---

# Efecto Parallax

Parallax desplaza un fondo o un elemento según el movimiento del mouse para crear profundidad visual.

# Fondo de imagen del menú

1. Haz clic derecho sobre el fondo del editor de diseño.
2. Abre [**Fondos del menú**](./menu-backgrounds) -> **Imagen**.
3. Configura el origen de la imagen.
4. Activa **Efecto Parallax**.
5. Configura los valores de intensidad X e Y.
6. Opcionalmente, activa **Invertir movimiento Parallax**.

Los valores X e Y controlan de forma independiente el movimiento horizontal y vertical. Usa valores de `0.0` (ninguno) a `1.0` (máximo).

# Elementos

1. Haz clic derecho en un [elemento](./elements).
2. Activa **Efecto Parallax**.
3. Configura **Intensidad Parallax X** e **Intensidad Parallax Y**.
4. Opcionalmente, invierte el movimiento.

Usa una intensidad menor para capas lejanas y una mayor para capas del primer plano. Las diferencias grandes o las capas invertidas crean un efecto de profundidad más fuerte.

# Solución de problemas

- Una intensidad de `0` no produce movimiento en ese eje.
- **Deslizar imágenes anchas de izquierda a derecha** entra en conflicto con el parallax del fondo y debe desactivarse.
- Un movimiento muy pequeño puede verse en escalones porque las posiciones de la interfaz gráfica usan píxeles enteros.
