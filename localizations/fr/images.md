---
title: Images
description: Tout ce qu’il faut savoir sur les ressources d’image dans FancyMenu.
---
# Images

FancyMenu prend en charge les ressources d’image à de nombreux endroits, comme les arrière-plans de menu, les textures des boutons et bien plus encore.

Vous pouvez utiliser des fichiers image PNG, JPEG, GIF et APNG dans FancyMenu, mais il est recommandé d’utiliser des PNG pour les images statiques chaque fois que possible. Pour les animations, au lieu d’utiliser des GIF ou des APNG, il vaut mieux utiliser [un fichier AFMA](/fma), le propre format d’image animé de FancyMenu, car les AFMA sont bien plus optimisés que les GIF/APNG, utilisent moins de RAM et ont un impact moindre sur les performances.

# Convertir des images dans des formats pris en charge

Lorsque vous devez convertir des images dans l’un des formats pris en charge par FancyMenu, ou simplement passer d’un format pris en charge à un autre pour diverses raisons, consultez la liste suivante de sites web qui permettent de convertir facilement des images en ligne, sans avoir besoin de télécharger de logiciel.

## GIF vers APNG
Pour convertir une image GIF en APNG, utilisez ce site : https://ezgif.com/gif-to-apng.

## APNG vers GIF
Pour convertir un APNG en GIF, utilisez ce site : https://ezgif.com/apng-to-gif.

## MP4 vers APNG
Si vous devez convertir une courte séquence vidéo en APNG, essayez ce site : https://ezgif.com/video-to-apng

## PNG vers JPEG
L’utilisation d’un JPEG peut parfois réduire la taille des ressources. Dans ce cas, il peut être préférable d’utiliser un JPEG plutôt qu’un PNG : https://www.freeconvert.com/png-to-jpeg. Gardez à l’esprit que les JPEG ne prennent pas en charge la transparence.

## JPEG vers PNG
Pour le cas courant de la conversion d’un JPEG en PNG, essayez ce site : https://jpg2png.com/

## WebP vers PNG
Les fichiers WebP ne sont pas pris en charge par FancyMenu. Vous devez donc les convertir en PNG : https://convertio.co/webp-png/

# Limitations des textures animées

FancyMenu utilise son propre [format AFMA](/fma) pour les animations optimisées. Celui-ci permet aux [fichiers AFMA](/fma) de contenir de nombreuses images à haute résolution. En revanche, pour les anciens formats de fichiers animés comme les GIF et les APNG, respectez les limites recommandées suivantes afin de ne pas remplir excessivement votre RAM ni trop dégrader les performances de votre jeu :

- Utilisez un maximum de **200 images** par animation.
- Utilisez une résolution maximale de **1080p** pour vos images.
- Ne dépassez pas un total de **1000 images pour TOUTES les animations combinées**, car même si vous utilisez seulement 200 images par animation, toutes les images seront chargées en mémoire. Utiliser trop d’animations simultanément remplira donc quand même votre RAM.

> [!IMPORTANT]
> Ces limites ne s’appliquent PAS aux [fichiers AFMA](/fma), car les AFMA ne chargent pas toutes leurs images en mémoire et sont bien plus optimisés. Ils ont donc un impact moindre sur les performances que les anciens formats d’animation.
