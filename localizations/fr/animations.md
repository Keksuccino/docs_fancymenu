---
title: Animations
description: Comment utiliser des images animées dans FancyMenu et comment les créer.
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# Animations

FancyMenu lit les images animées presque partout où vous pouvez utiliser une image : dans les [éléments Image](/elements#image), les [arrière-plans de menu sous forme d’image](/menu-backgrounds#image), les textures des boutons et des curseurs, l’[intro du jeu](/game-intro), et bien plus encore.

Utilisez des fichiers **APNG** ou **GIF** pour vos animations :

- **APNG** (PNG animé) offre une meilleure qualité : toutes les couleurs d’un PNG classique et une transparence correcte avec des contours adoucis. C’est le meilleur choix pour les logos, les arrière-plans et tout ce qui comporte de la transparence.
- **GIF** est plus répandu, et il existe donc davantage d’outils pour créer et modifier des GIF. En revanche, un GIF ne dispose que de 256 couleurs par image, et ses pixels sont soit entièrement transparents, soit entièrement opaques.

> [!NOTE]
> Les formats d’animation propres à FancyMenu, FMA et AFMA, sont obsolètes. Vos fichiers existants fonctionnent toujours, mais utilisez APNG ou GIF pour vos nouvelles animations. Voir [FMA et AFMA](#fma-and-afma).

# Utiliser des animations

1. Placez le fichier dans `<game-directory>/config/fancymenu/assets/` pour qu’il apparaisse dans le sélecteur de fichiers de FancyMenu. Les URL Web et les fichiers de packs de ressources fonctionnent également ; consultez la page [Ressources](/resources).
2. Sélectionnez-le comme n’importe quelle autre image, par exemple dans **Source de l’image** d’un élément Image.

> [!WARNING]
> Les fichiers APNG doivent avoir l’extension `.apng`. De nombreux outils enregistrent les APNG avec l’extension `.png` : renommez le fichier, sinon FancyMenu l’affichera comme une image fixe. Il en va de même pour les URL Web : elles doivent se terminer par `.apng`.

## Lecture des animations

- Une animation est lue le nombre de fois indiqué dans son fichier, puis reste sur sa dernière image. Vous définissez le nombre de boucles lors de la création du fichier.
- Les animations ne sont lues que lorsqu’elles sont à l’écran. Lorsqu’elles réapparaissent, elles reprennent là où elles s’étaient arrêtées.
- **Redémarrer les textures animées à l’ouverture de l’écran** fait recommencer l’animation des éléments Image et des arrière-plans de menu sous forme d’image à chaque ouverture de l’écran.
- **Redémarrer les textures animées au survol** fait recommencer les textures des boutons et des curseurs chaque fois que la souris les survole.
- Les écouteurs [**L’animation de la texture a démarré**](/listeners#animated-texture-started-playing) et [**L’animation de la texture est terminée**](/listeners#animated-texture-finished-playing) exécutent des actions au démarrage ou à la fin d’une animation.

## Performances

FancyMenu décode les APNG et les GIF pendant leur lecture, en ne traitant que quelques images à l’avance. Même les animations longues nécessitent donc peu de mémoire.

Les grandes images et les fréquences d’images élevées ont toutefois un coût en performances. Faites en sorte que vos images soient à peu près aussi grandes que leur taille à l’écran ; consultez la page [Optimiser les textures](/optimizing-textures). Pour les clips longs avec du son, utilisez plutôt une [vidéo](/video).

# Créer des animations

Ces outils gratuits permettent de créer des APNG et des GIF à partir d’images individuelles ou de vidéos :

- [ScreenToGif](https://www.screentogif.com/) (Windows) : cliquez sur **Éditeur**, déposez-y vos images PNG, définissez la durée d’affichage des images et enregistrez l’animation au format APNG ou GIF. Vous pouvez définir le bouclage dans le menu d’enregistrement.
- [ezgif](https://ezgif.com/) (en ligne, sans téléchargement) : créez un [GIF](https://ezgif.com/maker) ou un [APNG](https://ezgif.com/apng-maker) à partir d’images, convertissez une vidéo en [GIF](https://ezgif.com/video-to-gif) ou en [APNG](https://ezgif.com/video-to-apng), ou convertissez un [GIF en APNG](https://ezgif.com/gif-to-apng) et un [APNG en GIF](https://ezgif.com/apng-to-gif).
- [FFmpeg](https://ffmpeg.org/download.html) (ligne de commande) : voir ci-dessous.

## Avec FFmpeg

Convertissez des images PNG numérotées, comme `frame_0001.png`, `frame_0002.png`, etc., en un APNG qui boucle indéfiniment. `-framerate 20` lit 20 images par seconde :

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

Convertissez une vidéo en APNG. `fps=20` conserve une fréquence de 20 images par seconde, et `scale=960:-1` définit une largeur de 960 pixels :

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

Convertissez une vidéo en GIF qui boucle indéfiniment. La partie `palettegen` choisit les 256 couleurs les mieux adaptées :

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

Convertissez un GIF en APNG :

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA et AFMA

FMA et AFMA sont les formats d’animation propres à FancyMenu. Ils sont tous deux obsolètes : ils sont toujours lus, mais APNG et GIF sont de meilleurs choix pour les nouvelles animations.

Pour créer malgré tout un AFMA :

1. Placez vos images dans un dossier sous forme de fichiers PNG. Elles sont lues dans l’ordre de leur nom, par exemple `frame_1.png`, `frame_2.png`, ..., `frame_10.png`.
2. Ouvrez **Barre de menus -> Outils -> Créateur AFMA**.
3. Définissez **Dossier des images principales** sur le dossier. Les images du **Dossier des images d’introduction** sont lues une fois avant les images principales.
4. Définissez **Durée d’affichage des images principales (ms)** et **Nombre de boucles**. Un nombre de boucles égal à `0` signifie que l’animation boucle indéfiniment.
5. Définissez **Fichier AFMA de sortie**, puis cliquez sur **Exporter**.
