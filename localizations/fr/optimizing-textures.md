---
title: Optimisation des textures
description: Comment optimiser les textures pour FancyMenu.
---

# Optimiser les textures pour FancyMenu

FancyMenu utilise les textures que vous fournissez telles quelles, ce qui signifie qu’il ne compresse, ne réduit ni n’agrandit vos fichiers image. Pour que vos menus soient nets et fonctionnent bien, il est important d’optimiser vos textures lorsque vous les utilisez dans votre interface.

# Conseils clés pour l’optimisation des textures

Les conseils suivants sont les étapes de base les plus importantes à garder à l’esprit lorsque vous travaillez avec des textures dans FancyMenu.

## 1. Utiliser la bonne résolution
- **Évitez les images trop basse résolution** : si une image est trop petite et est étirée pour remplir une zone plus grande, elle peut paraître floue.
- **Évitez l’excès de haute résolution** : des textures très grandes affichées à petite taille peuvent aussi paraître déformées ou « bizarres » et peuvent gaspiller des performances.

> 📌 **Conseil :** utilisez des textures à la résolution à laquelle elles apparaîtront dans le menu, ou à une résolution proche.
{.is-info}

## 2. Préserver le rapport hauteur/largeur
- Conservez toujours le rapport hauteur/largeur de l’image lors du redimensionnement.
- Étendre une image de manière disproportionnée peut provoquer des artefacts visuels et donner un mauvais rendu.

> 📌 **Conseil :** vous pouvez faire un clic droit sur les éléments Image et cliquer sur **Restaurer le rapport hauteur/largeur** pour les redimensionner selon leur rapport d’aspect correct ; ensuite, lorsque vous les redimensionnez manuellement, maintenez **SHIFT** enfoncé pendant le redimensionnement afin que celui-ci respecte le rapport hauteur/largeur de l’élément.
{.is-info}

## 3. Pensez au Nine-Slicing et au tiling
- Pour les éléments d’interface redimensionnables (comme les panneaux ou les boutons), utilisez les fonctionnalités de [Nine-Slicing & Tiling](/nine-slicing-and-tiling) de FancyMenu.
- Cela garantit que les bords des textures restent nets lorsqu’ils sont redimensionnés.
