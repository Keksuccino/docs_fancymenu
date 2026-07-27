---
title: Obtener cuadros de videos
description: Extrae cuadros PNG de un video con FFmpeg.
---

# Extraer cuadros de video con FFmpeg

1. Instala [FFmpeg](https://ffmpeg.org/download.html) y asegúrate de que el comando `ffmpeg` esté disponible.
2. Abre una terminal en el directorio que contiene tu video.
3. Crea el directorio de salida:

   ```bash
   mkdir output_frames
   ```

4. Ejecuta el comando que coincida con los cuadros que necesitas. Reemplaza `input.mp4` con el nombre de archivo de tu video.

## Extraer todos los cuadros

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## Extraer a una tasa de cuadros fija

Este ejemplo crea 10 cuadros por segundo. Cambia `10` según sea necesario.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## Cambiar el tamaño de los cuadros extraídos

Este ejemplo escala cada cuadro a `1280×720`.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

Los archivos PNG numerados en `output_frames` se pueden usar para crear una [animación AFMA o FMA clásica](./fma). Menos cuadros y dimensiones más pequeñas reducen el tamaño del archivo y el uso de memoria.
