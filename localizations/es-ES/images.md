---
title: Imágenes
description: Todo lo importante sobre los recursos de imagen en FancyMenu.
---
# Imágenes

FancyMenu admite recursos de imagen en muchos lugares, como fondos de menús, texturas de botones y mucho más.

Puedes usar archivos de imagen PNG, JPEG, GIF y APNG en FancyMenu, pero se recomienda utilizar PNG para imágenes estáticas siempre que sea posible. En lugar de usar GIF y APNG para las animaciones, es mejor utilizar [un archivo AFMA](/fma), el formato de imagen animada propio de FancyMenu, ya que los archivos AFMA están mucho más optimizados que los GIF/APNG, utilizan menos RAM y tienen un menor impacto en el rendimiento.

# Convertir imágenes a formatos compatibles

Cuando necesites convertir imágenes a uno de los formatos compatibles con FancyMenu, o simplemente quieras convertir un formato compatible a otro por diversos motivos, consulta la siguiente lista de sitios web que funcionan bien para convertir imágenes en línea, sin necesidad de descargar ningún programa.

## De GIF a APNG
Para convertir una imagen GIF a APNG, utiliza este sitio: https://ezgif.com/gif-to-apng.

## De APNG a GIF
Para convertir un APNG a GIF, esto es lo que necesitas: https://ezgif.com/apng-to-gif.

## De MP4 a APNG
Si necesitas convertir una secuencia de vídeo corta a APNG, prueba este sitio: https://ezgif.com/video-to-apng

## De PNG a JPEG
A veces usar JPEG puede hacer que los recursos ocupen menos, así que en esos casos puede ser buena idea utilizar JPEG en lugar de PNG: https://www.freeconvert.com/png-to-jpeg. Ten en cuenta que los archivos JPEG no admiten transparencia.

## De JPEG a PNG
Para el caso habitual de convertir JPEG a PNG, prueba este sitio: https://jpg2png.com/

## De WebP a PNG
FancyMenu no admite archivos WebP, por lo que tendrás que convertirlos a PNG: https://convertio.co/webp-png/

# Limitaciones de las texturas animadas

FancyMenu utiliza su propio [formato AFMA](/fma) para optimizar las animaciones, lo que permite que los [archivos AFMA](/fma) tengan muchos fotogramas a alta resolución. Sin embargo, para formatos de archivo animados antiguos, como GIF y APNG, deberías respetar los siguientes límites recomendados para no llenar demasiado la RAM ni empeorar excesivamente el rendimiento del juego:

- Utiliza un máximo de **200 fotogramas** por animación.
- Utiliza una resolución máxima de **1080p** para los fotogramas.
- No deberías superar un total de **1000 fotogramas entre TODAS las animaciones**, porque, aunque utilices solo 200 fotogramas por animación, todos se cargarán en la memoria. Por tanto, usar demasiadas animaciones a la vez seguirá llenando la RAM.

> [!IMPORTANT]
> Estos límites NO se aplican a los [archivos AFMA](/fma), porque los archivos AFMA no cargan todos sus fotogramas en la memoria y están mucho más optimizados, por lo que no tendrán tanto impacto en el rendimiento como los formatos de animación antiguos.
