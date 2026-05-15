---
title: Fondos del menú
description: >-
  Cómo configurar fondos personalizados para los menús (imágenes, animaciones)
  para las pantallas.
---

# Fondos del menú

FancyMenu te permite configurar fondos personalizados para los menús. Puedes usar imágenes, texturas animadas, presentaciones de diapositivas, panoramas cúbicos, colores, navegadores, videos, shaders GLSL y más.

# Configurar un fondo

En FancyMenu 3.9.0+, la personalización del fondo del menú se hace directamente desde el menú contextual del editor de diseño:

1. Abre el editor de diseño.
2. Haz clic derecho sobre el fondo del editor.
3. Abre **Fondos del menú**.
4. Habilita y configura el o los tipos de fondo que quieras.

Los tipos de fondo más comunes incluyen:

- Vanilla
- Image
- Slideshow
- Cubic Panorama
- Color (HEX)
- Browser
- Video
- GLSL Shader
- Video [MCEF] (deprecated)
- y más..

El antiguo tipo de fondo **Video [MCEF]** está obsoleto en FancyMenu 3.9.0. Usa el nuevo fondo nativo **Video**, impulsado por Watermedia V3, para los diseños nuevos.

# Quitar el fondo personalizado

Abre **Fondos del menú** otra vez y desactiva o elimina el tipo de fondo personalizado que ya no quieras. Si no hay ningún tipo de fondo personalizado activo, la pantalla volverá a su comportamiento normal de fondo vanilla.

# Superposición de fondos

FancyMenu 3.9.0 permite habilitar varios tipos de fondo de menú en un mismo diseño. Los fondos activos se renderizan como una pila, así que puedes combinar una imagen o panorama base con superposiciones translúcidas, capas de navegador, capas de shader, capas de paralaje y otros efectos.

Si también tienes varios diseños activos, sus pilas de fondo también pueden combinarse. Para ordenar los diseños y hacer que aparezcan en un orden específico, haz clic derecho sobre el fondo del editor y luego haz clic en **Índice del diseño**.

# Fondos transparentes

Como no hay nada detrás de los fondos, no es posible hacer transparente el fondo que está hasta abajo, porque eso provocaría fallas gráficas; pero sí es totalmente posible usar transparencia en configuraciones de fondos apilados, siempre y cuando el de abajo se mantenga con opacidad completa. De esa forma puedes tener capas de fondo translúcidas encima de la capa inferior.

Para hacer translúcida una imagen de fondo, usa el editor de imágenes que prefieras.

# Fondos del navegador

El tipo de fondo **Browser** funciona igual que el elemento Browser, pero ocupa toda la pantalla y recibe foco automáticamente. Esto es útil para contenido web de pantalla completa, páginas HTML locales o capas de video web.

# Fondos de shaders GLSL

El tipo de fondo **GLSL Shader** renderiza shaders GLSL personalizados y admite la creación de shaders al estilo de Shadertoy. Consulta la página [API de Shader GLSL](/glsl-shader-api) para ver los uniformes compatibles y la estructura del shader.
