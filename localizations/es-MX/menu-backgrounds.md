---
title: Fondos del menú
description: >-
  Cómo configurar fondos personalizados del menú (imágenes, animaciones) para
  las pantallas.
---
# Fondos del menú

FancyMenu te permite configurar fondos personalizados para los menús. Puedes usar imágenes, texturas animadas, presentaciones, panoramas cúbicos, colores, navegadores, videos, shaders GLSL y más.

# Configurar un fondo

La personalización del fondo del menú está disponible desde el menú contextual del editor de diseño:

1. Abre el editor de diseño.
2. Haz clic derecho sobre el fondo del editor.
3. Abre **Fondos del menú**.
4. Habilita y configura el/los tipo(s) de fondo que quieras.

Los tipos de fondo más comunes incluyen:

- Vanilla
- Imagen
- Presentación
- Panorama cúbico
- Color (HEX)
- Navegador
- Video
- Shader GLSL
- Video [MCEF] (obsoleto)
- Tipos de fondo adicionales del complemento

El antiguo tipo de fondo **Video [MCEF]** está obsoleto. Usa el [**Video** nativo](./video) impulsado por Watermedia V3 para los diseños nuevos.

# Quitar el fondo personalizado

Abre **Fondos del menú** de nuevo y deshabilita o elimina el tipo de fondo personalizado que ya no quieras. Si no hay ningún tipo de fondo personalizado activo, la pantalla volverá a su comportamiento normal de fondo vanilla.

# Apilar fondos

Se pueden habilitar varios tipos de fondo del menú en un mismo diseño. Los fondos activos se renderizan como una pila, así que una imagen base o un panorama se puede combinar con capas translúcidas de navegador, shader, paralaje u otras.

Si además tienes varios diseños activos, sus pilas de fondo también se pueden combinar. Para ordenar los diseños y hacer que aparezcan en un orden específico, haz clic derecho en el fondo del editor y luego haz clic en **Índice de diseño**.

# Fondos transparentes

FancyMenu renderiza una capa base negra detrás de los fondos personalizados activos. Por eso, los píxeles transparentes en el fondo más inferior muestran negro. Usa un fondo base opaco y luego apila fondos translúcidos encima.

Para hacer translúcida una imagen de fondo, usa el editor de imágenes de tu preferencia.

# Fondos de navegador

El tipo de fondo **Navegador** funciona como el [elemento de navegador](./elements#browser), pero ocupa toda la pantalla y se enfoca automáticamente. Esto es útil para contenido web en pantalla completa, páginas HTML locales o capas de video web.

# Fondos de shader GLSL

El tipo de fondo **Shader GLSL** renderiza shaders GLSL personalizados y es compatible con la creación de shaders al estilo Shadertoy. Consulta la página de [API de Shader GLSL](/glsl-shader-api) para ver los uniformes compatibles y la estructura del shader.
