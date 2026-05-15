---
title: Arrière-plans du menu
description: >-
  Comment définir des arrière-plans personnalisés pour les menus (images,
  animations) pour les écrans.
---

# Arrière-plans du menu

FancyMenu vous permet de définir des arrière-plans personnalisés pour les menus. Vous pouvez utiliser des images, des textures animées, des diaporamas, des panoramas cubiques, des couleurs, des navigateurs, des vidéos, des shaders GLSL, et plus encore.

# Définir un arrière-plan

Dans FancyMenu 3.9.0+, la personnalisation de l’arrière-plan du menu se fait directement depuis le menu contextuel de l’éditeur de mise en page :

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
- Vidéo [MCEF] (obsolète)
- et plus encore..

L’ancien type d’arrière-plan **Vidéo [MCEF]** est obsolète dans FancyMenu 3.9.0. Utilisez le nouveau fond **Vidéo** natif, propulsé par Watermedia V3, pour les nouvelles mises en page.

# Supprimer l’arrière-plan personnalisé

Ouvrez à nouveau **Arrière-plans du menu** et désactivez/supprimez le type d’arrière-plan personnalisé que vous ne souhaitez plus. Si aucun type d’arrière-plan personnalisé n’est actif, l’écran reviendra à son comportement normal d’arrière-plan vanilla.

# Superposer des arrière-plans

FancyMenu 3.9.0 permet d’activer plusieurs types d’arrière-plan de menu dans une même mise en page. Les arrière-plans actifs sont rendus sous forme de pile, ce qui vous permet de combiner une image ou un panorama de base avec des superpositions translucides, des couches de navigateur, des couches de shader, des couches de parallaxe et d’autres effets.

Si plusieurs mises en page sont également actives, leurs piles d’arrière-plans peuvent aussi se combiner. Pour trier les mises en page et les afficher dans un ordre précis, faites un clic droit sur l’arrière-plan de l’éditeur, puis cliquez sur **Indice de mise en page**.

# Arrière-plans transparents

Comme il n’y a rien derrière les arrière-plans, il n’est pas possible de rendre transparent l’arrière-plan tout en bas, car cela entraînerait des problèmes graphiques. En revanche, il est tout à fait possible d’utiliser la transparence dans des configurations d’arrière-plans empilés, tant que celui du bas reste en pleine opacité. De cette façon, vous pouvez avoir des couches d’arrière-plan translucides au-dessus de la couche inférieure.

Pour rendre une image d’arrière-plan translucide, utilisez l’éditeur d’images de votre choix.

# Arrière-plans de navigateur

Le type d’arrière-plan **Navigateur** fonctionne comme l’élément Navigateur, mais remplit tout l’écran et est automatiquement focalisé. C’est utile pour du contenu web en plein écran, des pages HTML locales ou des couches de vidéos web.

# Arrière-plans de shader GLSL

Le type d’arrière-plan **Shader GLSL** rend des shaders GLSL personnalisés et prend en charge la création de shaders de type Shadertoy. Consultez la page [API Shader GLSL](/glsl-shader-api) pour connaître les uniformes pris en charge et la structure des shaders.
