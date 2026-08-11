---
title: Fondos del menú
description: >-
  Cómo configurar fondos personalizados del menú (imágenes, animaciones) para
  las pantallas.
---
# Fondos del menú

FancyMenu te permite configurar fondos personalizados para los menús. Puedes usar imágenes, texturas animadas, presentaciones de diapositivas, panoramas cúbicos, colores, navegadores, videos, sombreadores GLSL y más.

# Configurar un fondo

La personalización del fondo del menú está disponible desde el menú contextual del editor de diseño:

1. Abre el editor de diseño.
2. Haz clic derecho en el fondo del editor.
3. Abre **Fondos del menú**.
4. Activa y configura el(los) tipo(s) de fondo que quieras.

Los tipos de fondo más comunes incluyen:

- Vanilla
- Imagen
- Presentación de diapositivas
- Panorama cúbico
- Color (HEX)
- Navegador
- Video
- Sombreador GLSL
- Video [Rinku] (obsoleto)
- Tipos de fondo adicionales de complementos

El antiguo tipo de fondo **Video [Rinku]** está obsoleto. Usa el [**Video** nativo](./video), impulsado por Watermedia V3, para los nuevos diseños.

# Quitar el fondo personalizado

Abre **Fondos del menú** de nuevo y desactiva o elimina el tipo de fondo personalizado que ya no quieras. Si no hay ningún tipo de fondo personalizado activo, la pantalla volverá a su comportamiento normal de fondo vanilla.

# Apilar fondos

Se pueden activar varios tipos de fondo del menú en un mismo diseño. Los fondos activos se renderizan en forma de pila, así que una imagen base o un panorama se puede combinar con capas translúcidas de navegador, sombreadores, paralaje u otras.

Si también tienes varios diseños activos, sus pilas de fondo también se pueden combinar. Para ordenar los diseños y hacer que aparezcan en un orden específico, haz clic derecho en el fondo del editor y luego en **Índice de diseño**.

# Fondos transparentes

FancyMenu renderiza una capa base negra detrás de los fondos personalizados activos. Por lo tanto, los píxeles transparentes en el fondo más inferior muestran negro. Usa un fondo base opaco y luego apila encima fondos translúcidos.

Para hacer translúcida una imagen de fondo, usa el editor de imágenes que prefieras.

# Fondos de navegador

El tipo de fondo **Navegador** funciona como el [elemento de navegador](./elements#browser), pero ocupa toda la pantalla y se enfoca automáticamente. Esto es útil para contenido web a pantalla completa, páginas HTML locales o capas de video web.

# Fondos de sombreadores GLSL

El tipo de fondo **Sombreador GLSL** renderiza sombreadores GLSL personalizados y es compatible con la creación de sombreadores al estilo Shadertoy. Consulta la página de [API de sombreadores GLSL](/glsl-shader-api) para ver los uniforms y la estructura del sombreador admitidos.
