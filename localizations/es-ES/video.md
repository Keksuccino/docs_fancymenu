---
title: Vídeos (MP4)
description: Qué debes saber sobre el uso de vídeos en FancyMenu.
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# Vídeos

FancyMenu permite reproducir vídeos MP4 como [elementos](/elements#video), [fondos de menú](/menu-backgrounds#video) y contenido de [introducción del juego](/game-intro).

El [elemento **Video**](/elements#video) nativo y el fondo de menú **Video** usan Watermedia V3. Los antiguos tipos **Video [Rinku]** están obsoletos y solo deberían conservarse en diseños que aún los necesiten.

También están disponibles las siguientes [acciones](/action-scripts) para controlar los fondos y elementos de vídeo:

- [**Establecer el volumen del elemento de vídeo**](/action-scripts#set-video-element-volume) establece el volumen de un elemento Video.
- [**Establecer el tiempo de reproducción del elemento de vídeo**](/action-scripts#set-video-element-play-time) adelanta o retrocede un elemento Video hasta una marca de tiempo en milisegundos.
- [**Alternar el estado de pausa del elemento de vídeo**](/action-scripts#toggle-video-element-paused-state) alterna el estado de pausa de un elemento Video.
- [**Establecer el volumen del fondo de vídeo**](/action-scripts#set-video-background-volume) establece el volumen de un fondo de menú Video.
- [**Establecer el tiempo de reproducción del fondo de vídeo**](/action-scripts#set-video-background-play-time) adelanta o retrocede un fondo de menú Video hasta una marca de tiempo en milisegundos.
- [**Alternar el estado de pausa del fondo de vídeo**](/action-scripts#toggle-video-background-paused-state) alterna el estado de pausa de un fondo de menú Video.

Y los siguientes [marcadores de posición](/placeholders) para consultar información sobre los fondos y elementos de vídeo:

- [**Volumen del elemento de vídeo**](/placeholders#video-element-volume) devuelve el volumen de un elemento Video.
- [**Duración del elemento de vídeo**](/placeholders#video-element-duration) devuelve la duración de un elemento Video.
- [**Tiempo de reproducción del elemento de vídeo**](/placeholders#video-element-play-time) devuelve el progreso actual de un elemento Video.
- [**Estado de pausa del elemento de vídeo**](/placeholders#video-element-paused-state) devuelve si un elemento Video está en pausa.
- [**Volumen del fondo de vídeo**](/placeholders#video-background-volume) devuelve el volumen de un fondo de menú Video.
- [**Duración del fondo de vídeo**](/placeholders#video-background-duration) devuelve la duración de un fondo de menú Video.
- [**Tiempo de reproducción del fondo de vídeo**](/placeholders#video-background-play-time) devuelve el progreso actual de un fondo de menú Video.
- [**Estado de pausa del fondo de vídeo**](/placeholders#video-background-paused-state) devuelve si un fondo de menú Video está en pausa.

De forma predeterminada, los marcadores de posición de duración y tiempo de reproducción devuelven `MM:SS`. Establece `output_as_timestamp` en `true` si necesitas marcas de tiempo en milisegundos. Los marcadores de posición de tiempo de reproducción también pueden usar `show_percentage` para mostrar valores de progreso de 0 a 100.

Los valores de volumen y estado de pausa son metadatos del controlador asociados al identificador. Los valores de duración y tiempo de reproducción requieren que el elemento Video o el fondo correspondiente esté activo y listo en la pantalla actual.

El [detector **Cambio del estado de reproducción del vídeo**](/listeners#video-playback-status-changed) puede reaccionar a `PLAYING`, `PAUSED`, `STOPPED` y `FINISHED`.

## Requisitos

Para usar el nuevo elemento Video nativo y el nuevo tipo de fondo de menú, debes instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Son dependencias opcionales, así que tendrás que añadirlas manualmente a la instancia si quieres usar vídeos.

La reproducción de vídeo nativa también requiere un renderizador OpenGL. Watermedia no está disponible mientras Minecraft usa Vulkan; cambia a OpenGL para usar elementos Video, fondos de menú Video e [introducciones del juego con vídeo](/game-intro).

El tipo obsoleto **Video [Rinku]** sigue usando [Rinku](https://modrinth.com/mod/rinku). Para los diseños nuevos, usa en su lugar el tipo Video nativo basado en Watermedia.

## Vídeos en las pantallas de carga

La compatibilidad con vídeos NO funciona en las pantallas de carga (la pantalla de carga del juego o de recursos y la pantalla de carga del mundo).

Esto también significa que NO deberías añadir vídeos a la pantalla de carga del juego mediante **Drippy Loading Screen**, ya que en la mayoría de los casos no funcionará.

En su lugar, usa [animaciones](/animations) breves y sencillas (APNG o GIF) en las pantallas de carga.

## Solución de problemas

Si el vídeo nativo no se reproduce, comprueba que Watermedia V3 y Watermedia Binaries V3 sean compatibles con tu versión de Minecraft y del cargador de mods, y que Minecraft esté usando OpenGL en lugar de Vulkan.
