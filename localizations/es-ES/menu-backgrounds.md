---
title: Fondos de menú
description: >-
  Cómo configurar fondos de menú personalizados (imágenes, animaciones) para las
  pantallas.
---
# Fondos de menú

FancyMenu te permite configurar fondos personalizados para los menús. Puedes usar imágenes, texturas animadas, presentaciones, panoramas cúbicos, colores, navegadores, vídeos, sombreadores GLSL y más.

# Configuración de un fondo

La personalización del fondo del menú está disponible desde el menú contextual del editor de diseño:

1. Abre el editor de diseño.
2. Haz clic derecho en el fondo del editor.
3. Abre **Fondos de menú**.
4. Activa y configura el/los tipo(s) de fondo que quieras.

Los tipos de fondo más comunes incluyen:

- Vanilla
- Imagen
- Presentación
- Panorama cúbico
- Color (HEX)
- Navegador
- Vídeo
- Sombreado GLSL
- Vídeo [MCEF] (obsoleto)
- Tipos de fondo adicionales de complementos

El antiguo tipo de fondo **Vídeo [MCEF]** está obsoleto. Usa el [**Vídeo** nativo](./video), impulsado por Watermedia V3, para los nuevos diseños.

# Eliminar el fondo personalizado

Vuelve a abrir **Fondos de menú** y desactiva o elimina el tipo de fondo personalizado que ya no quieras. Si no hay ningún tipo de fondo personalizado activo, la pantalla volverá al comportamiento normal de fondo vanilla.

# Apilado de fondos

Se pueden activar varios tipos de fondo de menú en un mismo diseño. Los fondos activos se renderizan como una pila, por lo que una imagen base o un panorama pueden combinarse con capas translúcidas de navegador, sombreado, paralaje u otras.

Si además tienes varios diseños activos, sus pilas de fondos también pueden combinarse. Para ordenar los diseños y hacer que aparezcan en un orden concreto, haz clic derecho en el fondo del editor y pulsa en **Índice de diseño**.

# Fondos transparentes

FancyMenu renderiza una capa negra de respaldo detrás de los fondos personalizados activos. Por tanto, los píxeles transparentes del fondo situado más abajo mostrarán negro. Usa un fondo base opaco y luego apila encima fondos translúcidos.

Para hacer translúcida una imagen de fondo, usa el editor de imágenes que prefieras.

# Fondos de navegador

El tipo de fondo **Navegador** funciona igual que el [elemento de navegador](./elements#browser), pero ocupa toda la pantalla y recibe el foco automáticamente. Es útil para contenido web a pantalla completa, páginas HTML locales o capas de vídeo web.

# Fondos de sombreado GLSL

El tipo de fondo **Sombreado GLSL** renderiza sombreadores GLSL personalizados y admite la creación de sombreadores al estilo de Shadertoy. Consulta la página de [API de sombreado GLSL](/glsl-shader-api) para ver los uniformes compatibles y la estructura del sombreador.
