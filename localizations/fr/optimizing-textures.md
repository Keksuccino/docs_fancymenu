---
title: Optimisation des textures
description: Comment optimiser les textures pour FancyMenu.
---
# Optimiser les textures pour FancyMenu

FancyMenu utilise les textures que vous fournissez telles quelles, ce qui signifie qu’il ne compresse, ne réduit ni n’agrandit vos fichiers image. Pour que vos menus restent nets et fonctionnent correctement, il est important d’optimiser vos textures lorsque vous les utilisez dans votre interface.

# Conseils clés pour l’optimisation des textures

Les conseils suivants sont les étapes de base les plus importantes à garder à l’esprit lorsque vous travaillez avec des textures dans FancyMenu.

## 1. Utiliser la bonne résolution
- **Évitez les images en basse résolution** : si une image est trop petite et étirée pour remplir une zone plus grande, elle peut apparaître floue.
- **Évitez l’excès de haute résolution** : des textures très grandes affichées à petite taille peuvent aussi sembler déformées ou « bizarres » et peuvent gaspiller des performances.

> [!NOTE]
> 📌 **Conseil :** utilisez des textures à la résolution à laquelle elles apparaîtront dans le menu, ou proche de celle-ci.

## 2. Préserver le ratio d’aspect
- Conservez toujours le ratio d’aspect de l’image lors du redimensionnement.
- Étendre une image de manière disproportionnée peut entraîner des artefacts visuels et un rendu médiocre.

> [!NOTE]
> 📌 **Conseil :** vous pouvez faire un clic droit sur les éléments Image puis cliquer sur **Restaurer le ratio d’aspect** pour les redimensionner selon leur ratio correct. Ensuite, lorsque vous les redimensionnez manuellement, maintenez **SHIFT** enfoncé pendant le redimensionnement pour que celui-ci respecte le ratio d’aspect de l’élément.

## 3. Pensez au nine-slicing et au tuilage
- Pour les éléments d’interface redimensionnables (comme les panneaux ou les boutons), utilisez les fonctionnalités de [Nine-Slicing & Tiling](/nine-slicing-and-tiling) de FancyMenu.
- Cela garantit que les bords des textures restent nets lorsqu’ils sont redimensionnés.
