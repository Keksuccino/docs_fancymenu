---
title: Personalizaciones globales
description: Aplica ajustes globales de FancyMenu que afectan todas las pantallas.
---

# Personalizaciones globales

Las Personalizaciones globales son ajustes de FancyMenu que se aplican a toda la interfaz del juego.
Úsalas cuando quieras un estilo o comportamiento uniforme en todos lados, en vez de editar cada diseño de pantalla por separado.

> [!INFO]
> A diferencia de la mayoría de las funciones de personalización de FancyMenu, las Personalizaciones globales funcionan incluso si las personalizaciones normales de pantalla están desactivadas.
> No requieren habilitar personalizaciones por pantalla, lo que significa que un solo cambio puede afectar de inmediato a todas las pantallas.

Ejemplos comunes:

- Usa un solo estilo compartido de botones y deslizadores para todas las pantallas.
- Reemplaza globalmente el fondo del menú, el panorama y la música del menú.
- Aplica de forma global el comportamiento de inicio/ventana (escala de la GUI, pantalla completa, título/icono de la ventana).
- Reemplaza globalmente las texturas de botones de vanilla sin un paquete de recursos.
- Reemplaza globalmente la música del menú de vanilla sin un paquete de recursos.

# Dónde encontrarlas

Abre la **barra de menús** de FancyMenu mientras **no** estés en el editor de diseños, luego ve a **Customization -> Global Customizations**.

# Inicio rápido

1. Abre **Customization -> Global Customizations**.
2. Elige una categoría para empezar (por ejemplo, **Custom Button Textures**).
3. Configura las opciones de esa categoría (selectores de recursos, interruptores o campos numéricos).
4. Prueba el resultado en varias pantallas.
5. Ajusta con más detalle las opciones relacionadas (por ejemplo, transparencia, estilos de etiquetas, bordes de nueve-slice).

# Qué puedes personalizar

## Comportamiento global e inicio

- **Game Intro** (un video o animación de introducción que se reproduce antes de que aparezca la pantalla de título)
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- **Seamless World Loading** (usa una captura de pantalla del mundo como fondo de la pantalla de carga del mundo)
- **Custom Window Icon**
- **Custom Window Title**
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## Aspecto de los botones

- **Custom Button Textures** (estados Normal/Hover/Inactive, modo transparente, nine-slice + tamaños de borde)
- **Button Labels** (subrayado al pasar el cursor, color base/de hover, escala, sombra)

## Aspecto de los deslizadores

- **Custom Slider Textures**
- **Slider Background Texture** (textura, modo transparente, nine-slice + tamaños de borde)
- **Slider Handle Textures** (estados Normal/Hover/Inactive, nine-slice + tamaños de borde)
- **Slider Labels** (subrayado al pasar el cursor, color base/de hover, escala, sombra)

## Aspecto y audio del menú

- **Custom Menu Background Texture**
- **Custom Menu Background Panorama**
- **Play Vanilla Menu Music** (habilita o deshabilita la reproducción de la música vanilla del menú)
- **Custom Menu Music Tracks**
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

Usa **Custom Menu Music Tracks** para crear una lista aleatoria de pistas para los menús.

Las pistas personalizadas configuradas reemplazan la música vanilla del menú en los menús.

- Abre **Custom Menu Music Tracks** para abrir **Manage Menu Music Tracks**.
- Usa **Add Track** para agregar fuentes de audio.
- Usa **Remove Track** para quitar una entrada.
- Usa **Clear Tracks** para eliminar todas las entradas.
