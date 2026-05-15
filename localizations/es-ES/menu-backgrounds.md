---
title: Fondos de menú
description: >-
  Cómo configurar fondos de menú personalizados (imágenes, animaciones) para las
  pantallas.
---

# Fondos de menú

FancyMenu te permite establecer fondos personalizados para los menús. Puedes usar imágenes, texturas animadas, presentaciones, panoramas cúbicos, colores, navegadores, vídeos, shaders GLSL y más.

# Configurar un fondo

En FancyMenu 3.9.0+, la personalización del fondo del menú se realiza directamente desde el menú contextual del editor de diseño:

1. Abre el editor de diseño.
2. Haz clic derecho sobre el fondo del editor.
3. Abre **Fondos de menú**.
4. Activa y configura el/los tipo(s) de fondo que quieras.

Los tipos de fondo más comunes incluyen:

- Vanilla
- Image
- Slideshow
- Cubic Panorama
- Color (HEX)
- Browser
- Video
- GLSL Shader
- Video [MCEF] (obsoleto)
- y más.

El antiguo tipo de fondo **Video [MCEF]** está obsoleto en FancyMenu 3.9.0. Usa el nuevo fondo nativo **Video**, impulsado por Watermedia V3, para los nuevos diseños.

# Eliminar el fondo personalizado

Vuelve a abrir **Fondos de menú** y desactiva o elimina el tipo de fondo personalizado que ya no quieras. Si no hay ningún tipo de fondo personalizado activo, la pantalla volverá a su comportamiento normal de fondo vanilla.

# Superponer fondos

FancyMenu 3.9.0 permite activar varios tipos de fondo de menú en el mismo diseño. Los fondos activos se renderizan como una pila, así que puedes combinar una imagen base o un panorama con superposiciones translúcidas, capas de navegador, capas de shaders, capas de paralaje y otros efectos.

Si además tienes varios diseños activos, sus pilas de fondos también pueden combinarse. Para ordenar los diseños y hacer que aparezcan en un orden específico, haz clic derecho sobre el fondo del editor y pulsa **Índice de diseño**.

# Fondos transparentes

Como no hay nada detrás de los fondos, no es posible hacer transparente el fondo que está en la parte más baja, porque eso provocaría fallos gráficos. Sin embargo, sí es totalmente posible usar transparencia en configuraciones de fondos apilados, siempre que el de abajo permanezca con opacidad total. De ese modo, puedes tener capas de fondo translúcidas encima de la capa inferior.

Para hacer translúcida una imagen de fondo, usa el editor de imágenes que prefieras.

# Fondos de navegador

El tipo de fondo **Browser** funciona como el elemento Browser, pero ocupa toda la pantalla y recibe el foco automáticamente. Esto es útil para contenido web a pantalla completa, páginas HTML locales o capas de vídeo web.

# Fondos de shader GLSL

El tipo de fondo **GLSL Shader** renderiza shaders GLSL personalizados y admite la creación de shaders al estilo Shadertoy. Consulta la página [API de GLSL Shader](/glsl-shader-api) para ver los uniforms compatibles y la estructura del shader.
