---
title: Personalizaciones globales
description: Aplica ajustes globales de FancyMenu que afectan a todas las pantallas.
---

# Personalizaciones globales

Las Personalizaciones globales aplican ajustes compartidos de la interfaz y del inicio sin editar el diseño de cada pantalla. Funcionan incluso cuando la personalización normal de pantallas está deshabilitada.

Ejemplos comunes:

- Usar un solo estilo compartido de botón y deslizador para todas las pantallas.
- Reemplazar globalmente el fondo del menú, el panorama y la música del menú.
- Aplicar comportamiento global de inicio/ventana (escala de la GUI, pantalla completa, título/icono de la ventana).
- Reemplazar globalmente las texturas de botones de Vanilla sin un paquete de recursos.
- Reemplazar globalmente la música del menú de Vanilla sin un paquete de recursos.

# Dónde encontrarlas

Abre la **barra de menú** de FancyMenu mientras **no** estés en el editor de diseños, luego ve a **Personalización -> Personalizaciones globales**.

# Qué puedes personalizar

## Comportamiento global e inicio

- [**Intro del juego**](./game-intro) (un video o animación de introducción que se reproduce antes de la pantalla de Título)
- **Iconos del mundo en la pantalla de un jugador**
- **Iconos de servidor en la pantalla multijugador**
- [**Carga fluida del mundo**](./seamless-world-loading) (usa una captura reciente del mundo como fondo de la pantalla de carga)
- [**Icono personalizado de la ventana**](./window-customization#custom-icon)
- [**Título personalizado de la ventana**](./window-customization#custom-title)
- **Escala de GUI predeterminada**
- **Forzar pantalla completa al iniciar**

## Apariencia de los botones

- **Texturas personalizadas de botones** (estados Normal/Al pasar el cursor/Inactivo, modo transparente, [nine-slice](./nine-slicing-and-tiling) + tamaños de borde)
- **Etiquetas de botones** (subrayado al pasar el cursor, color base/hover, escala, sombra)

## Apariencia de los deslizadores

- **Texturas personalizadas de deslizadores**
- **Textura del fondo del deslizador** (textura, modo transparente, [nine-slice](./nine-slicing-and-tiling) + tamaños de borde)
- **Texturas del control del deslizador** (estados Normal/Al pasar el cursor/Inactivo, [nine-slice](./nine-slicing-and-tiling) + tamaños de borde)
- **Etiquetas de deslizadores** (subrayado al pasar el cursor, color base/hover, escala, sombra)

## Apariencia y audio del menú

- [**Textura personalizada del fondo del menú**](./menu-backgrounds)
- [**Panorama personalizado del fondo del menú**](./panoramas)
- **Reproducir música del menú de Vanilla** (activar/desactivar la reproducción de la música del menú de Vanilla)
- [**Pistas de música personalizadas del menú**](./background-music)
- **Sonido personalizado al hacer clic en botones/deslizadores**

# Pistas de música personalizadas del menú

Usa **Pistas de música personalizadas del menú** para crear una lista aleatoria de pistas para los menús.

> [!IMPORTANT]
> Las pistas personalizadas globales del menú solo se reproducen cuando no hay un mundo cargado, como en la pantalla de Título. Usa un elemento de [**Audio**](./elements#audio) para audio del menú dentro de un mundo.

Las pistas configuradas usan el canal de sonido Music y reemplazan la música del menú de Vanilla en los menús compatibles que no son del mundo.

- La primera pista comienza después de unos cinco segundos.
- Las siguientes pistas comienzan después de un retraso aleatorio de aproximadamente uno a treinta segundos.
- Las pistas se seleccionan aleatoriamente.
- Con varias pistas, la pista anterior no se selecciona dos veces seguidas.

Administra la lista de pistas desde **Pistas de música personalizadas del menú**:

- Abre **Pistas de música personalizadas del menú** para abrir **Administrar pistas de música del menú**.
- Usa **Agregar pista** para añadir fuentes de audio.
- Usa **Eliminar pista** para quitar una entrada.
- Usa **Limpiar pistas** para eliminar todas las entradas.
