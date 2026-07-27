---
title: Obtener fotogramas de vídeos
description: Extrae fotogramas PNG de un vídeo con FFmpeg.
---

# Extraer fotogramas de vídeo con FFmpeg

1. Instala [FFmpeg](https://ffmpeg.org/download.html) y asegúrate de que el comando `ffmpeg` esté disponible.
2. Abre una terminal en el directorio que contiene tu vídeo.
3. Crea el directorio de salida:

   ```bash
   mkdir output_frames
   ```

4. Ejecuta el comando que corresponda a los fotogramas que necesitas. Sustituye `input.mp4` por el nombre de archivo de tu vídeo.

## Extraer todos los fotogramas

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## Extraer a una velocidad de fotogramas fija

Este ejemplo crea 10 fotogramas por segundo. Cambia `10` según necesites.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## Redimensionar los fotogramas extraídos

Este ejemplo escala cada fotograma a `1280×720`.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

Los archivos PNG numerados en `output_frames` se pueden usar para crear una [animación AFMA o FMA clásica](./fma). Cuantos menos fotogramas y menores sean las dimensiones, menor será el tamaño del archivo y el uso de memoria.
