---
title: Cabezas de jugador
description: Cómo mostrar la cabeza de un jugador como imagen 2D o 3D en un menú.
---

# Cabezas de jugador en menús

Para mostrar la cabeza de un jugador como una imagen 2D o 3D usando un elemento de imagen, puedes usar una API web de terceros llamada "Minotar".

## Imagen 2D

### 1. Agrega un elemento de imagen

En el editor de FancyMenu, haz clic derecho sobre el fondo, selecciona "Nuevo elemento" y luego elige "Imagen" (o "Picture").

### 2. Configura la fuente web

Haz clic derecho en el elemento de imagen para acceder a sus propiedades. Para el tipo de fuente, selecciona "Web".

### 3. Construye la URL con el marcador de posición correcto

En el campo "Source", deberías ingresar la siguiente URL:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu usará `{"placeholder":"playername"}` para insertar dinámicamente el nombre de usuario actual del jugador en la URL, permitiendo que el elemento de imagen obtenga y muestre su cabeza desde Minotar.

## Imagen 3D

Esta es bastante similar a la versión 2D, pero aquí necesitamos usar una URL diferente:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

El `200` es el tamaño en píxeles en este caso, así que si quieres una versión más pequeña, simplemente cámbialo por `100`, por ejemplo, o para una versión más grande, usa `300` y así sucesivamente.
