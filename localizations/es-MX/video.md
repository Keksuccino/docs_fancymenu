---
title: Videos (MP4)
description: Lo que debes saber sobre el uso de videos en FancyMenu.
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# Videos

FancyMenu permite reproducir videos MP4 como [elementos](/elements#video), [fondos de menú](/menu-backgrounds#video) y contenido de [Intro del juego](/game-intro).

El [elemento **Video**](/elements#video) nativo y el fondo de menú **Video** usan Watermedia V3. Los antiguos tipos **Video [Rinku]** están obsoletos y solo deben conservarse en diseños que aún los necesiten.

También están disponibles las siguientes [acciones](/action-scripts) para controlar los fondos y elementos de video:

- [**Establecer el volumen del elemento Video**](/action-scripts#set-video-element-volume) establece el volumen de un elemento Video.
- [**Establecer el tiempo de reproducción del elemento Video**](/action-scripts#set-video-element-play-time) adelanta o retrocede un elemento Video a una marca de tiempo en milisegundos.
- [**Alternar el estado de pausa del elemento Video**](/action-scripts#toggle-video-element-paused-state) alterna el estado de pausa de un elemento Video.
- [**Establecer el volumen del fondo de Video**](/action-scripts#set-video-background-volume) establece el volumen de un fondo de menú Video.
- [**Establecer el tiempo de reproducción del fondo de Video**](/action-scripts#set-video-background-play-time) adelanta o retrocede un fondo de menú Video a una marca de tiempo en milisegundos.
- [**Alternar el estado de pausa del fondo de Video**](/action-scripts#toggle-video-background-paused-state) alterna el estado de pausa de un fondo de menú Video.

También están disponibles los siguientes [marcadores de posición](/placeholders) para obtener información sobre los fondos y elementos de video:

- [**Volumen del elemento Video**](/placeholders#video-element-volume) devuelve el volumen de un elemento Video.
- [**Duración del elemento Video**](/placeholders#video-element-duration) devuelve la duración de un elemento Video.
- [**Tiempo de reproducción del elemento Video**](/placeholders#video-element-play-time) devuelve el progreso actual de un elemento Video.
- [**Estado de pausa del elemento Video**](/placeholders#video-element-paused-state) devuelve si un elemento Video está en pausa.
- [**Volumen del fondo de Video**](/placeholders#video-background-volume) devuelve el volumen de un fondo de menú Video.
- [**Duración del fondo de Video**](/placeholders#video-background-duration) devuelve la duración de un fondo de menú Video.
- [**Tiempo de reproducción del fondo de Video**](/placeholders#video-background-play-time) devuelve el progreso actual de un fondo de menú Video.
- [**Estado de pausa del fondo de Video**](/placeholders#video-background-paused-state) devuelve si un fondo de menú Video está en pausa.

De forma predeterminada, los marcadores de posición de duración y tiempo de reproducción devuelven el formato `MM:SS`. Establece `output_as_timestamp` en `true` si necesitas marcas de tiempo en milisegundos. Los marcadores de posición de tiempo de reproducción también pueden usar `show_percentage` para mostrar valores de progreso del 0 al 100.

Los valores de volumen y estado de pausa son metadatos del controlador asociados al identificador. Los valores de duración y tiempo de reproducción requieren que el elemento Video o el fondo correspondiente estén activos y listos en la pantalla actual.

El [escuchador **Cambio en el estado de reproducción de video**](/listeners#video-playback-status-changed) puede reaccionar a `PLAYING`, `PAUSED`, `STOPPED` y `FINISHED`.

## Requisitos

Para usar el nuevo elemento Video nativo y el tipo de fondo de menú, debes instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Estas dependencias son opcionales, así que debes agregarlas manualmente a la instancia si quieres usar videos.

La reproducción de video nativa también requiere un renderizador OpenGL. La reproducción con Watermedia no está disponible mientras Minecraft usa Vulkan; cambia a OpenGL para usar elementos Video, fondos de menú Video e [Intros del juego con video](/game-intro).

El tipo obsoleto **Video [Rinku]** todavía usa [Rinku](https://modrinth.com/mod/rinku). Para los diseños nuevos, usa el tipo Video nativo basado en Watermedia.

## Videos en pantallas de carga

La compatibilidad con videos NO funciona en las pantallas de carga (la pantalla de carga del juego o de recursos, y la pantalla de carga del mundo).

Esto también significa que NO debes agregar videos a la pantalla de carga del juego mediante **Drippy Loading Screen**, ya que en la mayoría de los casos no funcionarán.

En su lugar, usa [animaciones](/animations) cortas y sencillas (APNG o GIF) en las pantallas de carga.

## Solución de problemas

Si el video nativo no se reproduce, confirma que Watermedia V3 y Watermedia Binaries V3 sean compatibles con tu versión de Minecraft y del cargador de mods, y que Minecraft esté usando OpenGL en lugar de Vulkan.
