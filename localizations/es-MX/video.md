---
title: Videos (MP4)
description: Qué debes saber sobre el uso de videos en FancyMenu.
---
# Videos

FancyMenu admite la reproducción de videos MP4 como [elementos](./elements#video), [fondos de menú](./menu-backgrounds) y contenido de [Introducción del juego](./game-intro).

El [**elemento Video**](./elements#video) nativo y el fondo de menú **Video** usan Watermedia V3. Los tipos antiguos **Video [MCEF]** están obsoletos y solo deben permanecer en diseños que todavía los necesiten.

También existen las siguientes **acciones** para controlar fondos y elementos de video:

- [**Establecer volumen del elemento de video**](./action-scripts#set-video-element-volume-set_video_element_volume) ajusta el volumen de un elemento Video.
- [**Establecer tiempo de reproducción del elemento de video**](./action-scripts#set-video-element-play-time-set_video_element_play_time) lleva un elemento Video a una marca de tiempo en milisegundos.
- [**Alternar estado de pausa del elemento de video**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) alterna el estado de pausa de un elemento Video.
- [**Establecer volumen del fondo de video**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) ajusta el volumen de un fondo de menú Video.
- [**Establecer tiempo de reproducción del fondo de video**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) lleva un fondo de menú Video a una marca de tiempo en milisegundos.
- [**Alternar estado de pausa del fondo de video**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) alterna el estado de pausa de un fondo de menú Video.

Y los siguientes **placeholders** para obtener información sobre fondos y elementos de video:

- [**Volumen del elemento de video**](./placeholders#video-element-volume-video_element_vol) devuelve el volumen de un elemento Video.
- [**Duración del elemento de video**](./placeholders#video-element-duration-video_element_duration) devuelve la duración de un elemento Video.
- [**Tiempo de reproducción del elemento de video**](./placeholders#video-element-play-time-video_element_playtime) devuelve el progreso actual de un elemento Video.
- [**Estado de pausa del elemento de video**](./placeholders#video-element-paused-state-video_element_paused_state) devuelve si un elemento Video está en pausa.
- [**Volumen del fondo de video**](./placeholders#video-background-volume-video_background_vol) devuelve el volumen de un fondo de menú Video.
- [**Duración del fondo de video**](./placeholders#video-background-duration-video_background_duration) devuelve la duración de un fondo de menú Video.
- [**Tiempo de reproducción del fondo de video**](./placeholders#video-background-play-time-video_background_playtime) devuelve el progreso actual de un fondo de menú Video.
- [**Estado de pausa del fondo de video**](./placeholders#video-background-paused-state-video_background_paused_state) devuelve si un fondo de menú Video está en pausa.

Los placeholders de duración y tiempo de reproducción devuelven `MM:SS` de forma predeterminada. Establece `output_as_timestamp` en `true` cuando necesites marcas de tiempo en milisegundos. Los placeholders de tiempo de reproducción aún pueden usar `show_percentage` para valores de progreso de 0 a 100.

Los valores de volumen y estado de pausa son metadatos del controlador asociados con el identificador. Los valores de duración y tiempo de reproducción requieren que el elemento Video o el fondo correspondiente estén activos y listos en la pantalla actual.

El [**escuchador de Cambio de estado de reproducción de video**](./listeners#on-video-playback-status-changed-video_playback_status_changed) puede reaccionar a `PLAYING`, `PAUSED`, `STOPPED` y `FINISHED`.

## Requisitos

Para usar el nuevo elemento Video nativo y el tipo de fondo de menú, necesitas instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Estas son dependencias opcionales, así que deben agregarse manualmente a la instancia si quieres soporte de video.

La reproducción de video nativa también requiere un renderizador OpenGL. La reproducción de Watermedia no está disponible mientras Minecraft use Vulkan; cambia a OpenGL para usar elementos Video, fondos de menú Video e [introducciones del juego en video](./game-intro).

El tipo obsoleto **Video [MCEF]** sigue usando MCEF. Para diseños nuevos, usa en su lugar el tipo Video nativo impulsado por Watermedia.

## Videos en pantallas de carga

El soporte de video NO funciona en las pantallas de carga (pantalla de carga del juego/recurso y pantalla de carga del mundo).

Esto también significa que NO debes agregar videos a la pantalla de carga del juego mediante **Drippy Loading Screen**, ya que en la mayoría de los casos no funcionará.

En su lugar, usa animaciones [AFMA/FMA](./fma) cortas y simples en las pantallas de carga.

## Solución de problemas

Si el video nativo no se reproduce, confirma que Watermedia V3 y Watermedia Binaries V3 coincidan con tu versión de Minecraft/modloader y que Minecraft esté usando OpenGL en lugar de Vulkan.
