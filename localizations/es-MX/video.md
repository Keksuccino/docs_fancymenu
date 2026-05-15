---
title: Videos (MP4)
description: Qué debes saber sobre el uso de videos en FancyMenu.
---

# Videos

FancyMenu admite reproducir videos MP4 como elementos, fondos de menú y contenido de Intro del Juego.

FancyMenu 3.9.0 agrega un nuevo elemento nativo **Video** y un fondo de menú **Video** impulsados por Watermedia V3. El tipo antiguo de elemento/fondo **Video [MCEF]** está obsoleto y solo debe conservarse para diseños antiguos que todavía lo necesiten.

También existen las siguientes **acciones** para controlar fondos y elementos de video:

- **Set Video Element Volume** para establecer el volumen de un elemento de Video
- **Set Video Element Play Time** para mover un elemento de Video a una marca de tiempo en milisegundos
- **Toggle Video Element Paused State** para alternar el estado de pausa de un elemento de Video
- **Set Video Background Volume** para establecer el volumen de un fondo de menú de Video
- **Set Video Background Play Time** para mover un fondo de menú de Video a una marca de tiempo en milisegundos
- **Toggle Video Background Paused State** para alternar el estado de pausa de un fondo de menú de Video

Y los siguientes **placeholders** para obtener información sobre fondos y elementos de video:

- **Video Element Volume** para obtener el volumen de un elemento de Video
- **Video Element Duration** para obtener la duración de un elemento de Video
- **Video Element Play Time** para obtener el tiempo de reproducción actual (progreso) de un elemento de Video
- **Video Element Paused State** para obtener el estado de pausa (true/false) de un elemento de Video
- **Video Background Volume** para obtener el volumen de un fondo de menú de Video
- **Video Background Duration** para obtener la duración de un fondo de menú de Video
- **Video Background Play Time** para obtener el tiempo de reproducción actual (progreso) de un fondo de menú de Video
- **Video Background Paused State** para obtener el estado de pausa (true/false) de un fondo de menú de Video

Los placeholders de duración y tiempo de reproducción devuelven `MM:SS` de forma predeterminada. Configura `output_as_timestamp` en `true` cuando necesites marcas de tiempo en milisegundos. Los placeholders de tiempo de reproducción todavía pueden usar `show_percentage` para valores de progreso de 0 a 100.

FancyMenu 3.9.0 también agrega el listener **On Video Playback Status Changed**, que puede reaccionar a `PLAYING`, `PAUSED`, `STOPPED` y `FINISHED`.

## Requisitos

Para usar el nuevo elemento nativo de Video y el tipo de fondo de menú, necesitas instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Estas son dependencias opcionales, así que deben agregarse a la instancia manualmente si quieres soporte para video.

El tipo obsoleto **Video [MCEF]** sigue usando MCEF. Para diseños nuevos, usa en su lugar el tipo nativo de Video impulsado por Watermedia.

## Videos en pantallas de carga

El soporte de video NO funciona en pantallas de carga (pantalla de carga del juego/recurso y pantalla de carga del mundo).

Esto también significa que NO debes agregar videos a la pantalla de carga del juego mediante **Drippy Loading Screen**, ya que en la mayoría de los casos no funcionará.

En su lugar, deberías usar archivos AFMA/FMA cortos y simples en las pantallas de carga, ya que los usuarios no notan que se vuelvan a cargar en la mayoría de los casos cuando la animación es lo suficientemente simple y corta.

## Solución de problemas

Si tienes problemas con el soporte nativo de video, primero confirma que tanto Watermedia V3 como Watermedia Binaries V3 estén instalados y que coincidan con tu versión de Minecraft/modloader.
