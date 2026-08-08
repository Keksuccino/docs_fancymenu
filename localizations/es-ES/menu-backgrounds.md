---
title: Fondos de menú
description: >-
  Cómo configurar fondos de menú personalizados (imágenes, animaciones) para las
  pantallas.
---
# Fondos de menú

FancyMenu te permite configurar fondos personalizados para los menús. Puedes usar imágenes, texturas animadas, pases de diapositivas, panoramas cúbicos, colores, navegadores, vídeos, shaders GLSL y mucho más.

# Configuración de un fondo

La personalización del fondo del menú está disponible desde el menú contextual del editor de diseño:

1. Abre el editor de diseño.
2. Haz clic con el botón derecho en el fondo del editor.
3. Abre **Fondos de menú**.
4. Activa y configura el/los tipo(s) de fondo que quieras.

Los tipos de fondo más habituales incluyen:

- Vanilla
- Image
- Slideshow
- Cubic Panorama
- Color (HEX)
- Browser
- Video
- GLSL Shader
- Video [Rinku] (obsoleto)
- Tipos de fondo adicionales del complemento

El antiguo tipo de fondo **Video [Rinku]** está obsoleto. Usa el [fondo **Video** nativo](./video) impulsado por Watermedia V3 para los diseños nuevos.

# Quitar el fondo personalizado

Vuelve a abrir **Fondos de menú** y desactiva o elimina el tipo de fondo personalizado que ya no quieras. Si no hay ningún tipo de fondo personalizado activo, la pantalla volverá a su comportamiento normal de fondo vanilla.

# Apilar fondos

Se pueden activar varios tipos de fondo de menú en un mismo diseño. Los fondos activos se renderizan como una pila, de modo que una imagen o panorama base puede combinarse con un navegador translúcido, un shader, capas de paralaje u otras capas.

Si además tienes varios diseños activos, sus pilas de fondos también pueden combinarse. Para ordenar los diseños y hacer que aparezcan en un orden concreto, haz clic con el botón derecho en el fondo del editor y pulsa **Índice de diseño**.

# Fondos transparentes

FancyMenu renderiza una capa de fondo negra detrás de los fondos personalizados activos. Por tanto, los píxeles transparentes del fondo situado más abajo mostrarán negro. Usa un fondo base opaco y luego coloca encima fondos translúcidos.

Para hacer translúcida una imagen de fondo, usa el editor de imágenes que prefieras.

# Fondos de navegador

El tipo de fondo **Browser** funciona igual que el [elemento Browser](./elements#browser), pero ocupa toda la pantalla y recibe automáticamente el foco. Esto es útil para contenido web a pantalla completa, páginas HTML locales o capas de vídeo web.

# Fondos de shaders GLSL

El tipo de fondo **GLSL Shader** renderiza shaders GLSL personalizados y admite la creación de shaders al estilo de Shadertoy. Consulta la página de la [API de shaders GLSL](/glsl-shader-api) para ver los uniformes y la estructura de shader compatibles.
