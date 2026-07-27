---
title: Personalizaciones globales
description: Aplica ajustes globales de FancyMenu que afectan a todas las pantallas.
---

# Personalizaciones globales

Las personalizaciones globales aplican ajustes compartidos de la interfaz y del inicio sin editar el diseño de cada pantalla. Funcionan incluso cuando la personalización normal de pantallas está desactivada.

Ejemplos habituales:

- Usar un único estilo compartido de botones y deslizadores para todas las pantallas.
- Sustituir globalmente el fondo del menú, el panorama y la música del menú.
- Aplicar globalmente el comportamiento de inicio/ventana (escala de la interfaz, pantalla completa, título/icono de la ventana).
- Sustituir globalmente las texturas de los botones de Vanilla sin un paquete de recursos.
- Sustituir globalmente la música del menú de Vanilla sin un paquete de recursos.

# Dónde encontrarlas

Abre la **barra de menú** de FancyMenu mientras **no** estés en el editor de diseños y luego ve a **Personalización -> Personalizaciones globales**.

# Qué puedes personalizar

## Comportamiento global e inicio

- [**Intro del juego**](./game-intro) (un vídeo o animación de introducción que se reproduce antes de la pantalla de título)
- **Iconos del mundo en la pantalla de un jugador**
- **Iconos de servidores en la pantalla multijugador**
- [**Carga continua del mundo**](./seamless-world-loading) (usa una captura reciente del mundo como fondo de la pantalla de carga)
- [**Icono personalizado de la ventana**](./window-customization#custom-icon)
- [**Título personalizado de la ventana**](./window-customization#custom-title)
- **Escala de la interfaz predeterminada**
- **Forzar pantalla completa al iniciar**

## Aspecto de los botones

- **Texturas personalizadas de botones** (estados Normal/Al pasar el ratón/Inactivo, modo transparente, [nine-slice](./nine-slicing-and-tiling) + tamaños de borde)
- **Etiquetas de los botones** (subrayado al pasar el ratón, color base/al pasar el ratón, escala, sombra)

## Aspecto de los deslizadores

- **Texturas personalizadas de deslizadores**
- **Textura de fondo del deslizador** (textura, modo transparente, [nine-slice](./nine-slicing-and-tiling) + tamaños de borde)
- **Texturas del control del deslizador** (estados Normal/Al pasar el ratón/Inactivo, [nine-slice](./nine-slicing-and-tiling) + tamaños de borde)
- **Etiquetas de los deslizadores** (subrayado al pasar el ratón, color base/al pasar el ratón, escala, sombra)

## Aspecto y audio del menú

- [**Textura personalizada del fondo del menú**](./menu-backgrounds)
- [**Panorama personalizado del fondo del menú**](./panoramas)
- **Reproducir música del menú de Vanilla** (activar/desactivar la música del menú de Vanilla)
- [**Pistas de música personalizadas del menú**](./background-music)
- **Sonido personalizado al hacer clic en botones/deslizadores**

# Pistas de música personalizadas del menú

Usa **Pistas de música personalizadas del menú** para crear una lista aleatoria de pistas para los menús.

> [!IMPORTANT]
> Las pistas globales personalizadas del menú solo se reproducen cuando no hay ningún mundo cargado, como en la pantalla de título. Usa un elemento de [**Audio**](./elements#audio) para audio del menú dentro del mundo.

Las pistas configuradas usan el canal de sonido Music y sustituyen la música del menú de Vanilla en los menús compatibles sin mundo.

- La primera pista empieza después de unos cinco segundos.
- Las siguientes pistas empiezan tras un retardo aleatorio de entre uno y treinta segundos.
- Las pistas se seleccionan aleatoriamente.
- Con varias pistas, la pista anterior no se selecciona dos veces seguidas.

Gestiona la lista de pistas desde **Pistas de música personalizadas del menú**:

- Abre **Pistas de música personalizadas del menú** para abrir **Gestionar pistas de música del menú**.
- Usa **Añadir pista** para agregar fuentes de audio.
- Usa **Eliminar pista** para quitar una entrada.
- Usa **Borrar pistas** para eliminar todas las entradas.
