---
title: Vídeos (MP4)
description: Qué debes saber sobre el uso de vídeos en FancyMenu.
---
# Vídeos

FancyMenu admite la reproducción de vídeos MP4 como [elementos](./elements#video), [fondos de menú](./menu-backgrounds) y contenido de [Game Intro](./game-intro).

El [**elemento de vídeo**](./elements#video) nativo y el fondo de menú **Video** usan Watermedia V3. Los antiguos tipos **Video [Rinku]** están obsoletos y solo deberían permanecer en diseños que todavía los necesiten.

También existen las siguientes **acciones** para controlar los fondos y elementos de vídeo:

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) establece el volumen de un elemento de vídeo.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) adelanta o retrocede un elemento de vídeo a una marca de tiempo en milisegundos.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) alterna el estado de pausa de un elemento de vídeo.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) establece el volumen de un fondo de menú de vídeo.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) adelanta o retrocede un fondo de menú de vídeo a una marca de tiempo en milisegundos.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) alterna el estado de pausa de un fondo de menú de vídeo.

Y los siguientes **marcadores de posición** para obtener información sobre los fondos y elementos de vídeo:

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) devuelve el volumen de un elemento de vídeo.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) devuelve la duración de un elemento de vídeo.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) devuelve el progreso actual de un elemento de vídeo.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) devuelve si un elemento de vídeo está en pausa.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) devuelve el volumen de un fondo de menú de vídeo.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) devuelve la duración de un fondo de menú de vídeo.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) devuelve el progreso actual de un fondo de menú de vídeo.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) devuelve si un fondo de menú de vídeo está en pausa.

Los marcadores de posición de duración y tiempo de reproducción devuelven `MM:SS` de forma predeterminada. Establece `output_as_timestamp` en `true` cuando necesites marcas de tiempo en milisegundos. Los marcadores de posición de tiempo de reproducción aún pueden usar `show_percentage` para valores de progreso de 0 a 100.

Los valores de volumen y estado de pausa son metadatos del controlador asociados con el identificador. Los valores de duración y tiempo de reproducción requieren que el elemento o fondo de vídeo correspondiente esté activo y listo en la pantalla actual.

El [**listener On Video Playback Status Changed**](./listeners#on-video-playback-status-changed-video_playback_status_changed) puede reaccionar a `PLAYING`, `PAUSED`, `STOPPED` y `FINISHED`.

## Requisitos

Para usar el nuevo tipo nativo de elemento de vídeo y fondo de menú, necesitas instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Estas son dependencias opcionales, así que deben añadirse manualmente a la instancia si quieres compatibilidad con vídeo.

La reproducción de vídeo nativa también requiere un renderizador OpenGL. La reproducción mediante Watermedia no está disponible mientras Minecraft use Vulkan; cambia a OpenGL para usar elementos de vídeo, fondos de menú de vídeo y [Game Intros de vídeo](./game-intro).

El tipo obsoleto **Video [Rinku]** sigue usando [Rinku](https://modrinth.com/mod/rinku). Para diseños nuevos, usa en su lugar el tipo de vídeo nativo impulsado por Watermedia.

## Vídeos en pantallas de carga

La compatibilidad con vídeo NO funciona en las pantallas de carga (pantalla de carga del juego/recurso y pantalla de carga del mundo).

Esto también significa que NO debes añadir vídeos a la pantalla de carga del juego mediante **Drippy Loading Screen**, ya que en la mayoría de los casos no funcionará.

En su lugar, usa animaciones [AFMA/FMA](./fma) cortas y sencillas en las pantallas de carga.

## Solución de problemas

Si el vídeo nativo no se reproduce, confirma que Watermedia V3 y Watermedia Binaries V3 coinciden con la versión de Minecraft/modloader y que Minecraft está usando OpenGL en lugar de Vulkan.
