---
title: Cabezas de jugador
description: Cómo mostrar la cabeza de un jugador como imagen 2D o 3D en un menú.
---

# Cabezas de jugador en menús

Para mostrar la cabeza de un jugador como una imagen 2D o 3D usando un elemento de imagen, puedes utilizar una API web de terceros llamada «Minotar».

## Imagen 2D

### 1. Añade un elemento de imagen

En el editor de FancyMenu, haz clic derecho sobre el fondo, selecciona «Nuevo elemento» y, a continuación, elige «Imagen» (o «Picture»).

### 2. Establece la fuente web

Haz clic derecho en el elemento de imagen para acceder a sus propiedades. Para el tipo de origen, selecciona «Web».

### 3. Construye la URL con el marcador de posición correcto

En el campo «Source», introducirías la siguiente URL:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu utilizará `{"placeholder":"playername"}` para insertar dinámicamente el nombre de usuario del jugador actual en la URL, lo que permite que el elemento de imagen obtenga y muestre su cabeza desde Minotar.

## Imagen 3D

Esta es bastante parecida a la versión 2D, pero aquí necesitamos usar una URL diferente:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

En este caso, `200` es el tamaño en píxeles, así que si quieres una versión más pequeña, simplemente cámbialo por `100`, por ejemplo; o, para una más grande, usa `300` y así sucesivamente.
