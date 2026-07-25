---
title: Arrière-plans du menu
description: >-
  Comment définir des arrière-plans personnalisés pour les menus (images,
  animations) pour les écrans.
---
# Arrière-plans du menu

FancyMenu vous permet de définir des arrière-plans personnalisés pour les menus. Vous pouvez utiliser des images, des textures animées, des diaporamas, des panoramas cubiques, des couleurs, des navigateurs, des vidéos, des shaders GLSL et plus encore.

# Définir un arrière-plan

La personnalisation de l’arrière-plan du menu est accessible depuis le menu contextuel de l’éditeur de mise en page :

1. Ouvrez l’éditeur de mise en page.
2. Faites un clic droit sur l’arrière-plan de l’éditeur.
3. Ouvrez **Arrière-plans du menu**.
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
- Vidéo [MCEF] (déprécié)
- Types d’arrière-plan supplémentaires fournis par des extensions

L’ancien type d’arrière-plan **Vidéo [MCEF]** est déprécié. Utilisez le [nouvel arrière-plan **Vidéo** natif](./video), propulsé par Watermedia V3, pour les nouvelles mises en page.

# Supprimer l’arrière-plan personnalisé

Ouvrez à nouveau **Arrière-plans du menu** et désactivez/supprimez le type d’arrière-plan personnalisé que vous ne চান plus. Si aucun type d’arrière-plan personnalisé n’est actif, l’écran reviendra à son comportement d’arrière-plan vanilla habituel.

# Empiler les arrière-plans

Plusieurs types d’arrière-plan de menu peuvent être activés dans une même mise en page. Les arrière-plans actifs s’affichent en pile, ce qui permet de combiner une image ou un panorama de base avec des couches translucides de navigateur, de shader, de parallaxe ou autres.

Si plusieurs mises en page sont également actives, leurs piles d’arrière-plans peuvent aussi se combiner. Pour trier les mises en page et les afficher dans un ordre précis, faites un clic droit sur l’arrière-plan de l’éditeur puis cliquez sur **Index de mise en page**.

# Arrière-plans transparents

FancyMenu affiche une couche de fond noire derrière les arrière-plans personnalisés actifs. Les pixels transparents de l’arrière-plan le plus bas laissent donc apparaître du noir. Utilisez un arrière-plan de base opaque, puis empilez au-dessus des arrière-plans translucides.

Pour rendre une image d’arrière-plan translucide, utilisez l’éditeur d’images de votre choix.

# Arrière-plans de navigateur

Le type d’arrière-plan **Navigateur** fonctionne comme l’[élément Navigateur](./elements#browser), mais remplit tout l’écran et reçoit automatiquement le focus. C’est utile pour du contenu web en plein écran, des pages HTML locales ou des calques vidéo web.

# Arrière-plans de shader GLSL

Le type d’arrière-plan **Shader GLSL** rend des shaders GLSL personnalisés et prend en charge l’écriture de shaders de type Shadertoy. Consultez la page [API du shader GLSL](/glsl-shader-api) pour connaître les uniformes pris en charge et la structure des shaders.
