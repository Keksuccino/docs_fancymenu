---
title: Arrière-plans de menu
description: >-
  Comment définir des arrière-plans de menu personnalisés (images, animations)
  pour les écrans.
---
# Arrière-plans de menu

FancyMenu vous permet de définir des arrière-plans personnalisés pour les menus. Vous pouvez utiliser des images, des textures animées, des diaporamas, des panoramas cubiques, des couleurs, des navigateurs, des vidéos, des shaders GLSL et bien plus encore.

# Définir un arrière-plan

La personnalisation de l’arrière-plan du menu est disponible depuis le menu contextuel de l’éditeur de disposition :

1. Ouvrez l’éditeur de disposition.
2. Faites un clic droit sur l’arrière-plan de l’éditeur.
3. Ouvrez **Arrière-plans de menu**.
4. Activez et configurez le ou les types d’arrière-plan souhaités.

Les types d’arrière-plan courants incluent :

- Vanilla
- Image
- Diaporama
- Panorama cubique
- Couleur (HEX)
- Navigateur
- Vidéo
- Shader GLSL
- Vidéo [Rinku] (obsolète)
- Types d’arrière-plan supplémentaires fournis par des extensions

L’ancien type d’arrière-plan **Vidéo [Rinku]** est obsolète. Utilisez le [**Vidéo** natif](./video) alimenté par Watermedia V3 pour les nouvelles dispositions.

# Supprimer l’arrière-plan personnalisé

Ouvrez à nouveau **Arrière-plans de menu** et désactivez/supprimez le type d’arrière-plan personnalisé que vous ne souhaitez plus utiliser. Si aucun type d’arrière-plan personnalisé n’est actif, l’écran reviendra au comportement normal de l’arrière-plan vanilla.

# Superposer des arrière-plans

Plusieurs types d’arrière-plan de menu peuvent être activés dans une même disposition. Les arrière-plans actifs sont rendus sous forme de pile, ce qui permet de combiner une image ou un panorama de base avec des couches translucides de navigateur, de shader, de parallaxe ou d’autres éléments.

Si vous avez également plusieurs dispositions actives, leurs piles d’arrière-plans peuvent aussi se combiner. Pour trier les dispositions et les faire apparaître dans un ordre précis, faites un clic droit sur l’arrière-plan de l’éditeur puis cliquez sur **Index de disposition**.

# Arrière-plans transparents

FancyMenu affiche une couche de fond noire derrière les arrière-plans personnalisés actifs. Les pixels transparents dans l’arrière-plan le plus bas laissent donc apparaître du noir. Utilisez un arrière-plan de base opaque, puis superposez au-dessus des arrière-plans translucides.

Pour rendre une image d’arrière-plan translucide, utilisez l’éditeur d’images de votre choix.

# Arrière-plans de navigateur

Le type d’arrière-plan **Navigateur** fonctionne comme l’[élément Navigateur](./elements#browser), mais occupe tout l’écran et reçoit automatiquement le focus. C’est utile pour du contenu web en plein écran, des pages HTML locales ou des couches de vidéo web.

# Arrière-plans de shader GLSL

Le type d’arrière-plan **Shader GLSL** affiche des shaders GLSL personnalisés et prend en charge la création de shaders de style Shadertoy. Consultez la page [API Shader GLSL](/glsl-shader-api) pour connaître les uniforms pris en charge et la structure des shaders.
