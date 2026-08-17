---
title: Videos (MP4)
description: Qué debes saber sobre el uso de videos en FancyMenu.
---
# Videos

FancyMenu admite la reproducción de videos MP4 como [elementos](./elements#video), [fondos de menú](./menu-backgrounds) y contenido de [Game Intro](./game-intro).

El [**elemento de Video**](./elements#video) nativo y el fondo de menú **Video** usan Watermedia V3. Los tipos antiguos **Video [Rinku]** están obsoletos y solo deberían permanecer en diseños que todavía los necesiten.

También existen las siguientes **acciones** para controlar fondos y elementos de video:

- [**Set Video Element Volume**](./action-scripts#set-video-element-volume-set_video_element_volume) establece el volumen de un elemento de Video.
- [**Set Video Element Play Time**](./action-scripts#set-video-element-play-time-set_video_element_play_time) adelanta un elemento de Video a una marca de tiempo en milisegundos.
- [**Toggle Video Element Paused State**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) alterna el estado de pausa de un elemento de Video.
- [**Set Video Background Volume**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) establece el volumen de un fondo de menú de Video.
- [**Set Video Background Play Time**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) adelanta un fondo de menú de Video a una marca de tiempo en milisegundos.
- [**Toggle Video Background Paused State**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) alterna el estado de pausa de un fondo de menú de Video.

Y los siguientes **placeholders** para obtener información sobre fondos y elementos de video:

- [**Video Element Volume**](./placeholders#video-element-volume-video_element_vol) devuelve el volumen de un elemento de Video.
- [**Video Element Duration**](./placeholders#video-element-duration-video_element_duration) devuelve la duración de un elemento de Video.
- [**Video Element Play Time**](./placeholders#video-element-play-time-video_element_playtime) devuelve el progreso actual de un elemento de Video.
- [**Video Element Paused State**](./placeholders#video-element-paused-state-video_element_paused_state) devuelve si un elemento de Video está en pausa.
- [**Video Background Volume**](./placeholders#video-background-volume-video_background_vol) devuelve el volumen de un fondo de menú de Video.
- [**Video Background Duration**](./placeholders#video-background-duration-video_background_duration) devuelve la duración de un fondo de menú de Video.
- [**Video Background Play Time**](./placeholders#video-background-play-time-video_background_playtime) devuelve el progreso actual de un fondo de menú de Video.
- [**Video Background Paused State**](./placeholders#video-background-paused-state-video_background_paused_state) devuelve si un fondo de menú de Video está en pausa.

Los placeholders de duración y tiempo de reproducción devuelven `MM:SS` de forma predeterminada. Establece `output_as_timestamp` en `true` cuando necesites marcas de tiempo en milisegundos. Los placeholders de tiempo de reproducción aún pueden usar `show_percentage` para valores de progreso de 0 a 100.

Los valores de volumen y estado de pausa son metadatos del controlador asociados con el identificador. Los valores de duración y tiempo de reproducción requieren que el elemento o fondo de Video correspondiente esté activo y listo en la pantalla actual.

El [**On Video Playback Status Changed** listener](./listeners#on-video-playback-status-changed-video_playback_status_changed) puede reaccionar a `PLAYING`, `PAUSED`, `STOPPED` y `FINISHED`.

## Requisitos

Para usar el nuevo elemento nativo de Video y el tipo de fondo de menú, necesitas instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Estas son dependencias opcionales, así que deben agregarse manualmente a la instancia si quieres compatibilidad con video.

La reproducción nativa de video también requiere un renderizador OpenGL. La reproducción de Watermedia no está disponible mientras Minecraft usa Vulkan; cambia a OpenGL para usar elementos de Video, fondos de menú de Video y [Game Intros de video](./game-intro).

El tipo obsoleto **Video [Rinku]** todavía usa [Rinku](https://modrinth.com/mod/rinku). Para diseños nuevos, usa en su lugar el tipo nativo de Video con Watermedia.

## Videos en Pantallas de Carga

La compatibilidad con video NO funciona en las pantallas de carga (pantalla de carga del juego/recurso y pantalla de carga del mundo).

Esto también significa que NO debes agregar videos a la pantalla de carga del juego mediante **Drippy Loading Screen**, ya que en la mayoría de los casos no funcionará.

En su lugar, usa animaciones cortas y sencillas de [AFMA/FMA](./fma) en las pantallas de carga.

## Solución de problemas

Si el video nativo no se reproduce, confirma que Watermedia V3 y Watermedia Binaries V3 coincidan con tu versión de Minecraft/modloader y que Minecraft esté usando OpenGL en lugar de Vulkan.
