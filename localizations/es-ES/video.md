---
title: Vídeos (MP4)
description: Lo que debes saber sobre el uso de vídeos en FancyMenu.
---

# Vídeos

FancyMenu admite la reproducción de vídeos MP4 como elementos, fondos de menú y contenido de introducción del juego.

FancyMenu 3.9.0 añade un nuevo elemento nativo **Video** y un fondo de menú **Video** impulsados por Watermedia V3. El antiguo tipo de elemento/fondo **Video [MCEF]** está obsoleto y solo debería mantenerse para diseños antiguos que todavía lo necesiten.

También existen las siguientes **acciones** para controlar fondos y elementos de vídeo:

- **Set Video Element Volume** para establecer el volumen de un elemento de vídeo
- **Set Video Element Play Time** para ir a un instante en milisegundos de un elemento de vídeo
- **Toggle Video Element Paused State** para alternar el estado de pausa de un elemento de vídeo
- **Set Video Background Volume** para establecer el volumen de un fondo de menú de vídeo
- **Set Video Background Play Time** para ir a un instante en milisegundos de un fondo de menú de vídeo
- **Toggle Video Background Paused State** para alternar el estado de pausa de un fondo de menú de vídeo

Y los siguientes **placeholders** para obtener información sobre fondos y elementos de vídeo:

- **Video Element Volume** para obtener el volumen de un elemento de vídeo
- **Video Element Duration** para obtener la duración de un elemento de vídeo
- **Video Element Play Time** para obtener el tiempo de reproducción actual (progreso) de un elemento de vídeo
- **Video Element Paused State** para obtener el estado de pausa (true/false) de un elemento de vídeo
- **Video Background Volume** para obtener el volumen de un fondo de menú de vídeo
- **Video Background Duration** para obtener la duración de un fondo de menú de vídeo
- **Video Background Play Time** para obtener el tiempo de reproducción actual (progreso) de un fondo de menú de vídeo
- **Video Background Paused State** para obtener el estado de pausa (true/false) de un fondo de menú de vídeo

Los placeholders de duración y tiempo de reproducción devuelven `MM:SS` de forma predeterminada. Establece `output_as_timestamp` en `true` cuando necesites marcas de tiempo en milisegundos. Los placeholders de tiempo de reproducción también pueden usar `show_percentage` para valores de progreso de 0 a 100.

FancyMenu 3.9.0 también añade el listener **On Video Playback Status Changed**, que puede reaccionar a `PLAYING`, `PAUSED`, `STOPPED` y `FINISHED`.

## Requisitos

Para usar el nuevo elemento nativo Video y el tipo de fondo de menú, necesitas instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Estas son dependencias opcionales, así que debes añadirlas manualmente a la instancia si quieres soporte para vídeo.

El tipo obsoleto **Video [MCEF]** sigue usando MCEF. Para diseños nuevos, usa en su lugar el tipo Video nativo impulsado por Watermedia.

## Vídeos en pantallas de carga

El soporte de vídeo NO funciona en las pantallas de carga (pantalla de carga del juego/recurso y pantalla de carga del mundo).

Esto también significa que NO debes añadir vídeos a la pantalla de carga del juego mediante **Drippy Loading Screen**, ya que en la mayoría de los casos no funcionará.

En su lugar, deberías usar archivos AFMA/FMA cortos y sencillos en las pantallas de carga, ya que los usuarios normalmente no notan que se recarguen cuando la animación es lo bastante simple y breve.

## Solución de problemas

Si tienes problemas con el soporte nativo de vídeo, primero confirma que tanto Watermedia V3 como Watermedia Binaries V3 están instalados y coinciden con tu versión de Minecraft/modloader.
