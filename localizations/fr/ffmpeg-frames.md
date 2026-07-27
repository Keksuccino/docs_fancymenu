---
title: Extraire des images d’une vidéo
description: Extraire des images PNG d’une vidéo avec FFmpeg.
---

# Extraire des images vidéo avec FFmpeg

1. Installez [FFmpeg](https://ffmpeg.org/download.html) et assurez-vous que la commande `ffmpeg` est disponible.
2. Ouvrez un terminal dans le répertoire contenant votre vidéo.
3. Créez le répertoire de sortie :

   ```bash
   mkdir output_frames
   ```

4. Exécutez la commande correspondant aux images dont vous avez besoin. Remplacez `input.mp4` par le nom de fichier de votre vidéo.

## Extraire chaque image

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## Extraire à une fréquence d’images fixe

Cet exemple crée 10 images par seconde. Modifiez `10` selon vos besoins.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## Redimensionner les images extraites

Cet exemple met à l’échelle chaque image à `1280×720`.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

Les fichiers PNG numérotés dans `output_frames` peuvent être utilisés pour créer une [animation AFMA ou FMA classique](./fma). Réduire le nombre d’images et les dimensions diminue la taille du fichier et l’utilisation de la mémoire.
