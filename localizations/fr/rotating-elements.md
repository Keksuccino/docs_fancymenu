---
title: Rotation et inclinaison des éléments
description: >-
  Faites pivoter et inclinez les éléments et leurs poignées dans l’éditeur de
  mise en page, en définissant des valeurs exactes ou en utilisant des espaces
  réservés.
sourceBlobSha: e36d9f5b6a1f4253312e5eee56e1facc1551dcd3
---

# Rotation et inclinaison des éléments

La plupart des éléments peuvent être pivotés et inclinés. Ces transformations s’effectuent autour du centre de l’élément, qui conserve sa position et ses dimensions.

- **Rotation** fait tourner l’élément, comme les aiguilles d’une horloge.
- **Inclinaison verticale** le bascule vers l’arrière, tandis que l’**inclinaison horizontale** le tourne sur le côté. Les éléments inclinés s’affichent sans perspective : ils deviennent simplement plus bas ou plus étroits. Si les deux inclinaisons sont appliquées, ils deviennent aussi obliques.

<img width="800" alt="Quatre éléments Texte sur un arrière-plan de menu : le premier est pivoté de 15 degrés, le deuxième a une inclinaison verticale de 45 degrés et est plus bas, le troisième a une inclinaison horizontale de 45 degrés et est plus étroit, et le quatrième est oblique avec les deux inclinaisons. Des cadres clairs indiquent leur position sans rotation ni inclinaison." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_axes.png?raw=true">

# Dans l’éditeur de mise en page

<img width="800" alt="Dans l’éditeur de mise en page, un autocollant Saison 3 est pivoté à l’aide de la poignée située sur le cercle qui l’entoure, puis un panneau Notes de mise à jour est incliné à l’aide des poignées situées sur les lignes à sa droite et en dessous" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_editor.gif?raw=true">

Sélectionnez un élément dans l’[éditeur de mise en page](/layout-editor), puis faites glisser ses poignées :

- La poignée située sur le cercle autour de l’élément le fait pivoter.
- La poignée située sur la ligne à sa droite définit son **inclinaison verticale** ; celle sur la ligne en dessous définit son **inclinaison horizontale**. Le milieu d’une ligne correspond à l’absence d’inclinaison.

Pendant le glissement :

- Maintenez `Shift` pour aligner les valeurs sur des incréments : 45 degrés pour la rotation et 15 degrés pour l’inclinaison.
- Lorsque la valeur est proche de 0, les poignées s’alignent sur 0 pour vous permettre de redresser facilement l’élément.
- La rotation et les inclinaisons de l’élément s’affichent en haut à gauche de celui-ci.

À savoir :

- Le cadre de sélection reste droit. Cliquez à l’intérieur pour sélectionner ou déplacer l’élément.
- Les poignées ne s’affichent que lorsqu’un seul élément est sélectionné.
- Un élément sans cercle ni lignes ne peut pas être pivoté ni incliné. Consultez la section [Éléments ne pouvant pas être pivotés ni inclinés](#elements-without-rotation-or-tilt).
- **barre de menus -> Fenêtre -> Commandes de rotation des éléments** et **Commandes d’inclinaison des éléments** masquent les poignées de tous les éléments.

# Valeurs exactes

Faites un clic droit sur l’élément pour accéder à ces paramètres. Chacun propose les options **Définir avec le sélecteur numérique**, **Définir comme texte brut** et **Réinitialiser aux valeurs par défaut**.

| Paramètre | Fonction |
|---|---|
| **Rotation** | Nombre de degrés de rotation dans le sens horaire, par exemple `90` pour un quart de tour. Les valeurs négatives indiquent une rotation dans le sens antihoraire. |
| **Inclinaison verticale** | Angle de bascule vers l’arrière, de `-60` à `60` degrés. |
| **Inclinaison horizontale** | Angle de rotation sur le côté, de `-60` à `60` degrés. |

Une inclinaison seule a le même aspect, que sa valeur soit positive ou négative. Lorsque les deux inclinaisons sont appliquées, leur signe détermine le sens dans lequel l’élément devient oblique.

## Avec des espaces réservés

Pour faire pivoter ou incliner un élément à l’aide d’une [variable](/variables) ou d’un autre [espace réservé](/placeholders) :

1. Faites un clic droit sur l’élément, puis activez **Mode de rotation avancé**, **Mode d’inclinaison verticale avancé** ou **Mode d’inclinaison horizontale avancé**.
2. Cliquez sur **Rotation**, **Inclinaison verticale** ou **Inclinaison horizontale**, puis sur **Définir comme texte brut**, et saisissez l’espace réservé.

Les modes avancés conservent leur propre valeur et masquent la poignée, afin que le glissement ne puisse pas remplacer votre espace réservé. Lorsque vous désactivez un mode, l’élément retrouve son ancienne valeur.

Un logo qui effectue un tour complet toutes les 3,6 secondes, avec cette **Rotation** en **Mode de rotation avancé**. Divisez par une valeur supérieure à `10` pour ralentir la rotation :

```
{"placeholder":"calc","values":{"expression":"{"placeholder":"unix_time"} / 10 % 360"}}
```

Une aiguille qui pointe vers l’angle indiqué par la variable `needle_angle`, que des boutons ou un [curseur](/elements#slider) peuvent définir :

```
{"placeholder":"getvariable","values":{"name":"needle_angle"}}
```

# Clics et souris

<img width="800" alt="Pointeur sur un bouton Rejoindre le serveur pivoté : rien ne se passe aux emplacements où se trouveraient les coins du bouton droit, tandis que les extrémités visibles du bouton s’illuminent" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_hover.gif?raw=true">

Les boutons, les curseurs, ainsi que les liens et les barres de défilement des éléments Texte réagissent aux mouvements de la souris à l’endroit où ils s’affichent, même lorsqu’ils sont pivotés ou inclinés. Il en va de même pour les conditions [**L’élément est survolé**](/conditions#is-element-hovered), [**Un élément est survolé**](/conditions#is-any-element-hovered) et [**Un bouton est survolé**](/conditions#is-any-button-hovered).

> [!NOTE]
> Les cases à cocher, les champs de saisie de texte, les éléments déplaçables et les navigateurs réagissent toujours dans le cadre qu’ils auraient sans rotation ni inclinaison. Laissez-les droits.

# Éléments ne pouvant pas être pivotés ni inclinés

- Ni rotation ni inclinaison : [Zones défilantes](/scrollable-areas), [Shaders GLSL](/elements#glsl-shader), [Modèles JSON de blocs/objets](/elements#blockitem-json-model), [Entités de joueur](/player-entities) et [éléments vanilla](/vanilla-elements), comme les boutons de l’écran lui-même.
- Rotation possible, mais pas d’inclinaison : [Infobulles](/elements#tooltip) et [Objets](/elements#item).

Les éléments d’une zone défilante peuvent être pivotés et inclinés ; seule la zone elle-même ne le peut pas.

Les éléments [Texte d’accueil](/splash-text) possèdent également leur propre paramètre **Rotation**, plus bas dans leur menu contextuel, pour leur inclinaison habituelle. Il fonctionne avec la rotation décrite sur cette page.
