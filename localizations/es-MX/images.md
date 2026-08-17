---
title: Imágenes
description: Todo lo importante sobre los recursos de imagen en FancyMenu.
---
# Imágenes

FancyMenu admite recursos de imagen en muchos lugares, como fondos de menú, texturas de botones y mucho más.

Puedes usar archivos de imagen PNG, JPEG, GIF y APNG en FancyMenu, pero se recomienda usar PNG para imágenes estáticas siempre que sea posible. En lugar de usar GIF y APNG para animaciones, es mejor usar [un archivo AFMA](/fma), el tipo de imagen animada propio de FancyMenu, ya que los AFMA están mucho más optimizados que GIF/APNG, usan menos RAM y tienen un menor impacto en el rendimiento.

# Convertir imágenes a formatos compatibles

Cuando necesites convertir imágenes a uno de los formatos compatibles con FancyMenu, o simplemente quieras convertir de un formato compatible a otro por diversos motivos, consulta la siguiente lista de sitios web que funcionan bien para convertir imágenes en línea, sin necesidad de descargar ningún software.

## GIF a APNG
Para convertir una imagen GIF a APNG, usa este sitio: https://ezgif.com/gif-to-apng.

## APNG a GIF
Para convertir un APNG a GIF, esto es lo que necesitas: https://ezgif.com/apng-to-gif.

## MP4 a APNG
Si necesitas convertir una secuencia de video corta a APNG, prueba este sitio: https://ezgif.com/video-to-apng

## PNG a JPEG
A veces usar JPEG puede hacer que los recursos sean más pequeños, así que en esos casos puede ser conveniente usar JPEG en lugar de PNG: https://www.freeconvert.com/png-to-jpeg. Ten en cuenta que los archivos JPEG no admiten transparencia.

## JPEG a PNG
Para el caso común de convertir JPEG a PNG, prueba este sitio: https://jpg2png.com/

## WebP a PNG
FancyMenu no admite archivos WebP, por lo que debes convertirlos a PNG: https://convertio.co/webp-png/

# Limitaciones de las texturas animadas

FancyMenu utiliza su propio [formato AFMA](/fma) para optimizar las animaciones, lo que permite que los [archivos AFMA](/fma) tengan muchos fotogramas en alta resolución. Sin embargo, para tipos de archivo animados antiguos, como GIF y APNG, debes respetar los siguientes límites recomendados para no llenar demasiado la RAM ni afectar demasiado el rendimiento del juego:

- Usa un máximo de **200 fotogramas** por animación.
- Usa una resolución máxima de **1080p** para tus fotogramas.
- No debes superar un total de **1000 fotogramas para TODAS las animaciones combinadas**, ya que, aunque uses solo 200 fotogramas por animación, todos se cargarán en la memoria. Por lo tanto, usar demasiadas animaciones a la vez seguirá llenando la RAM.

> [!IMPORTANT]
> Estos límites NO se aplican a los [archivos AFMA](/fma), ya que los AFMA no cargan todos sus fotogramas en la memoria y están mucho más optimizados, por lo que no afectarán tanto el rendimiento como los tipos de animación antiguos.
