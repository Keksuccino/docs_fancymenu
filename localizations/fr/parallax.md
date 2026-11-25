---
title: Effet de parallaxe
description: >-
  Faites légèrement bouger les arrière-plans et les éléments avec la souris pour
  donner de la profondeur à vos menus.
sourceBlobSha: f8481cfcc8d4f90bf2f261d436188763c8f23cba
---

# Effet de parallaxe

L’effet de parallaxe fait légèrement bouger l’arrière-plan d’un menu ou un élément lorsque la souris se déplace. Faites moins bouger les couches éloignées et davantage les couches proches pour donner de la profondeur à votre menu.

<img width="640" alt="Un écran titre avec un paysage au crépuscule composé de quatre couches : lorsque la souris se déplace, l’arbre au premier plan bouge le plus, les collines un peu moins, et les montagnes et le ciel à peine" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_scene.gif?raw=true">

Cette fonctionnalité s’applique aux [éléments](/elements) ainsi qu’aux [arrière-plans de menu](/menu-backgrounds) de type **Image** et **Vidéo**.

# Éléments

<img width="640" alt="Sur un écran titre dont les boutons sont disposés en colonne à gauche, sélectionner les cinq boutons dans l’éditeur de mise en page en cliquant dessus et avec Ctrl + clic, régler Effet de parallaxe sur Activé et Intensité de parallaxe (X) sur 1.0 pour chacun, puis enregistrer et fermer l’éditeur. Sur l’écran titre, les boutons bougent légèrement lorsque la souris se déplace de gauche à droite, tandis que le logo et le paysage restent immobiles" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_element_settings.gif?raw=true">

1. Faites un clic droit sur l’élément dans l’éditeur de mise en page, puis faites défiler jusqu’à **Effet de parallaxe**.
2. Cliquez sur **Effet de parallaxe** pour le régler sur **Activé**.
3. Cliquez sur **Intensité de parallaxe (X)** et **Intensité de parallaxe (Y)** pour définir l’amplitude du mouvement.
4. Enregistrez la mise en page et fermez l’éditeur. Les éléments ne bougent qu’en dehors de l’éditeur.

Pour appliquer l’effet à plusieurs éléments à la fois, [sélectionnez-les](/layout-editor#selecting) d’abord (`Ctrl` + clic ajoute un élément à la sélection), puis faites un clic droit sur l’un d’eux.

| Paramètre | Fonction |
|---|---|
| **Effet de parallaxe** | Active l’effet. |
| **Intensité de parallaxe (X)** | Amplitude du mouvement horizontal, de `0.0` (aucun mouvement) à `1.0`. Les nouveaux éléments ont une valeur de `0.5`. |
| **Intensité de parallaxe (Y)** | Même réglage pour le mouvement vertical. |
| **Inverser le mouvement de parallaxe** | Fait bouger l’élément dans le même sens que la souris. Sinon, il bouge dans le sens opposé. |

À `1.0`, lorsque la souris se trouve au bord de l’écran, un élément peut se déplacer jusqu’à 5 % de la largeur de l’écran sur les côtés et jusqu’à 5 % de sa hauteur vers le haut ou le bas. Au centre de l’écran, les éléments restent à l’endroit où vous les avez placés.

- Les éléments [ancrés](/positioning-elements) à un élément auquel l’effet est appliqué bougent avec lui, et leur propre effet s’ajoute au sien.
- **Rester à l’écran** ne maintient pas à l’écran les éléments auxquels l’effet est appliqué : ils peuvent dépasser des bords.
- Les éléments étirés ne bougent pas dans la direction de leur étirement.
- Les [boutons et curseurs vanilla](/vanilla-elements) ne bougent qu’après que vous les avez déplacés. Avec le point d’ancrage **Vanilla (Original)**, ils restent à l’emplacement où le jeu les place.
- Les boutons restent cliquables à l’endroit où ils s’affichent.
- Les [zones défilantes](/scrollable-areas), les éléments qu’elles contiennent et les éléments d’info-bulle ne sont pas concernés par l’effet de parallaxe.

# Arrière-plans du menu

<img width="800" alt="Le menu contextuel de l’éditeur de mise en page, avec Arrière-plans du menu et Image ouverts, affichant Effet de parallaxe, Définir l’intensité de l’effet de parallaxe (X), Définir l’intensité de l’effet de parallaxe (Y) et Inverser le mouvement de parallaxe" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_background_settings.png?raw=true">

1. Faites un clic droit sur l’arrière-plan de l’éditeur, puis ouvrez **Arrière-plans du menu -> Image** (ou **Vidéo**).
2. Cliquez sur **Effet de parallaxe** pour le régler sur **Activé**.
3. Réglez **Définir l’intensité de l’effet de parallaxe (X)** et **Définir l’intensité de l’effet de parallaxe (Y)**.

Les arrière-plans réagissent beaucoup plus fortement que les éléments. Leur taille augmente en fonction de leur intensité afin que leurs bords ne soient jamais visibles : à `1.0`, ils font deux fois la taille de l’écran et peuvent se déplacer latéralement jusqu’à la moitié de l’écran. Gardez des valeurs faibles : les nouveaux arrière-plans ont une valeur de `0.02`, et des valeurs comprises entre `0.01` et `0.1` donnent de bons résultats.

- **Inverser le mouvement de parallaxe** fait bouger l’arrière-plan dans le même sens que la souris.
- **Faire défiler les images larges de gauche à droite** et **Effet de parallaxe** ne peuvent pas être activés en même temps.
- **Répéter la texture** et **Conserver les proportions de l’arrière-plan** sont compatibles avec cet effet.
- Les arrière-plans bougent également dans l’éditeur de mise en page.

# Créer une scène en profondeur

La scène affichée en haut de cette page se compose d’un ciel et de trois couches sur l’écran titre :

1. Dessinez votre scène en plusieurs couches, de l’arrière vers l’avant, par exemple le ciel, les montagnes, les collines et le premier plan. Toutes les couches, à l’exception du ciel, sont des images PNG comportant des zones transparentes.
2. Définissez le ciel comme arrière-plan de menu de type **Image**, puis activez son effet de parallaxe.
3. Ajoutez chaque autre couche comme [élément Image](/elements#image), de l’arrière vers l’avant, afin que la plus proche soit au premier plan.
4. Faites en sorte que les couches soient légèrement plus grandes que l’écran, pour que leurs bords ne soient jamais visibles lorsqu’elles bougent. Une couche réglée sur `1.0` doit dépasser de 5 % de la largeur de l’écran à gauche et à droite, et de 5 % de sa hauteur en haut et en bas. Désactivez **Rester à l’écran** pour pouvoir les placer au-delà des bords de l’écran.
5. Activez l’effet de parallaxe pour chaque couche : utilisez une faible intensité pour les couches éloignées et une forte intensité pour les couches proches.
6. Faites un clic droit sur l’arrière-plan de l’éditeur et réglez **Éléments personnalisés derrière les éléments vanilla** sur **Activé**, afin que les couches restent derrière les boutons et le logo.

Voici les intensités utilisées pour cette scène :

| Couche | Intensité (X) | Intensité (Y) |
|---|---|---|
| Ciel (arrière-plan du menu) | `0.02` | `0.01` |
| Montagnes | `0.35` | `0.2` |
| Collines | `0.6` | `0.3` |
| Premier plan | `1.0` | `0.5` |

> [!TIP]
> Réglez l’intensité Y à environ la moitié de l’intensité X. Le sol d’un paysage bougera ainsi beaucoup moins de haut en bas.

# Bon à savoir

- Tout se déplace par pixels entiers de l’interface graphique. Les faibles intensités entraînent donc de petits mouvements saccadés.
- Les paramètres d’intensité acceptent les [espaces réservés](/placeholders) : pointez sur l’un d’eux et cliquez sur **Définir comme texte brut** dans le petit menu qui apparaît à côté. Avec une [variable](/variables), vous pouvez permettre aux joueurs de réduire l’intensité de l’effet dans votre propre menu de paramètres.
