---
title: Découpage en neuf et répétition
description: >-
  Adaptez des textures encadrées à toutes les tailles sans les déformer, ou
  répétez un motif au lieu de l’étirer.
sourceBlobSha: 0dca8e7070606cdafccd9edc23a77535048d4ba3
---

# Découpage en neuf et répétition

Vos textures sont étirées pour s’adapter à la taille de l’élément. C’est parfait pour les photos, mais les cadres, panneaux et boutons avec bordures se déforment lorsqu’ils s’élargissent ou s’agrandissent. Deux réglages permettent d’y remédier :

- Le découpage en neuf préserve la forme des coins et des bords d’une texture et ne remplit que le milieu.
- La répétition reproduit une texture au lieu de l’étirer, afin que le motif conserve sa taille.

<img width="800" alt="Une texture de panneau carrée découpée en neuf parties par quatre lignes, et la même texture sous forme de panneau large dont les coins et les bords ont conservé leur forme" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png">

# Fonctionnement du découpage en neuf

Quatre lignes découpent la texture en neuf parties. Les quatre coins conservent toujours la même taille, les bords s’allongent et le milieu remplit l’espace restant.

1. Définissez votre texture.
2. Activez son réglage de découpage en neuf. Consultez la section [Éléments compatibles](#where-it-works) pour connaître son nom.
3. Définissez la taille des bordures en fonction de l’épaisseur du cadre de votre texture, en pixels de la texture. Pour un cadre de 4 pixels d’épaisseur, indiquez `4`.

À savoir :

- Les bordures s’affichent à l’écran à la même taille que dans la texture. Ainsi, une texture avec des bordures de 40 pixels paraîtra massive sur un petit bouton. Choisissez une texture dont la taille est proche de celle de l’élément.
- La plupart des textures utilisent une même taille pour les bordures gauche et droite (bordures X), et une autre pour les bordures du haut et du bas (bordures Y). Les barres de progression, les info-bulles et les personnalisations globales disposent d’un réglage pour chaque côté.
- Les bordures trop grandes pour la texture sont automatiquement réduites.

# Éléments compatibles

| Texture | Découpage en neuf | Répétition |
|---|---|---|
| Textures des [boutons](/elements#button), dans **Textures des boutons** | **Arrière-plan personnalisé découpé en neuf** | - |
| Textures des [curseurs](/elements#slider), dans **Textures des curseurs** | **Arrière-plan personnalisé découpé en neuf** et **Poignée personnalisée découpée en neuf** | - |
| Éléments [Image](/elements#image) | **Texture découpée en neuf** | **Répéter la texture** |
| **Arrière-plan** des éléments [Texte](/text-in-menus#background) et [Zones défilantes](/scrollable-areas#background) | **Arrière-plan personnalisé découpé en neuf** | **Répéter la texture** |
| **Arrière-plans des barres de défilement** des éléments Texte et des Zones défilantes | toujours activé | - |
| **Arrière-plan** des éléments [Info-bulle](/elements#tooltip) | toujours activé, tailles définies dans **Paramètres du découpage en neuf** | - |
| Textures des [barres de progression](/elements#progress-bar) | **Texture de barre découpée en neuf** et **Texture d’arrière-plan découpée en neuf** | - |
| [Textures globales des boutons et des curseurs](/global-customizations#buttons-and-sliders) | **Arrière-plans des boutons découpés en neuf**, **Arrière-plan du curseur découpé en neuf** et **Poignée du curseur découpée en neuf** | - |
| [Arrière-plans de menu en image](/menu-backgrounds#image) | - | **Répéter la texture** |
| En-tête et pied de page des [écrans défilants](/customizing-scrollable-screens) | - | **Répéter la texture de l’en-tête** et **Répéter la texture du pied de page** |

## Arrière-plans des éléments Texte et des Zones défilantes

Ouvrez **Arrière-plan** dans le menu contextuel d’un élément Texte ou d’une Zone défilante :

- **Texture d’arrière-plan personnalisée** remplace le panneau sombre intégré par votre propre texture. Réinitialisez ce réglage pour rétablir le panneau.
- **Arrière-plan personnalisé découpé en neuf** est activé par défaut. Définissez les bordures avec **Bordures X de l’arrière-plan découpé en neuf (gauche et droite)** et **Bordures Y de l’arrière-plan découpé en neuf (haut et bas)**.
- **Répéter la texture** répète votre texture au lieu de l’étirer. Avec le découpage en neuf, les bords et le milieu sont répétés, tandis que les coins conservent leur forme.
- **Afficher l’arrière-plan** désactive l’arrière-plan entier.

## Arrière-plans des barres de défilement

Ouvrez **Barres de défilement -> Arrière-plans des barres de défilement** pour un élément Texte ou une Zone défilante. **Texture de la barre verticale** et **Texture de la barre horizontale** affichent une texture le long du trajet de la poignée de défilement. Elles sont toujours découpées en neuf afin que leurs extrémités conservent leur forme, quelle que soit la longueur des barres. Définissez les bordures avec les deux réglages situés juste en dessous.

# Fonctionnement de la répétition

La répétition place la texture côte à côte autant de fois que possible, en conservant sa taille d’origine. Utilisez une texture sans raccord visible, dont le bord gauche s’aligne avec le bord droit et le bord supérieur avec le bord inférieur. Sinon, des lignes apparaîtront entre les répétitions.

Sur les éléments Image, **Répéter la texture** et **Texture découpée en neuf** ne fonctionnent pas ensemble. Si les deux sont activés, l’image est répétée.
