---
title: Positionnement des éléments
description: Comment utiliser correctement les points d’ancrage.
---

# Positionnement des éléments dans FancyMenu

Dans FancyMenu, la position de chaque élément est déterminée par des **points d’ancrage**. Ces points servent à calculer où un élément doit apparaître à l’écran, en veillant à ce que les éléments ne se chevauchent pas, ne sortent pas de l’écran et ne se déplacent pas incorrectement lorsque la fenêtre est redimensionnée.

## Comprendre les points d’ancrage

Les points d’ancrage servent d’origine à partir de laquelle la position d’un élément est calculée. Par défaut, les éléments que vous ajoutez aux dispositions sont liés au point d’ancrage **« Centre de l’écran »**. Cet ancrage correspond au milieu exact de l’écran, quelle que soit la taille de la fenêtre.

Par exemple, si un élément se trouve à 2 centimètres du centre de l’écran tout en étant lié au point d’ancrage **« Centre de l’écran »**, il conservera cette distance quelle que soit la modification de la taille de la fenêtre.

## Interagir avec les points d’ancrage

Lorsque vous faites glisser un élément dans l’éditeur, le point d’ancrage auquel il est connecté est mis en surbrillance. Par défaut, cette action affiche aussi tous les autres points d’ancrage disponibles. Vous pouvez modifier l’ancrage d’un élément en le faisant glisser vers un autre point d’ancrage et en attendant que la barre de chargement soit remplie.

![Illustration des points d’ancrage](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Ancrer des éléments à d’autres éléments

Les éléments peuvent aussi servir de points d’ancrage pour d’autres éléments. Cette fonctionnalité est particulièrement utile pour intégrer des éléments personnalisés de manière fluide dans des menus Vanilla, sans avoir à ajuster chaque élément Vanilla.

Pour ancrer un élément à un autre, faites simplement glisser l’élément vers l’élément souhaité. Lorsque l’élément que vous déplacez survole un autre élément, son point d’ancrage est remplacé par celui survolé, comme lorsque vous survolez un véritable point d’ancrage.

Cela permet à l’élément de se déplacer avec son élément parent.

## Exemple d’ancrage des éléments

La capture d’écran suivante montre comment vous devriez choisir les ancres pour les éléments.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Tous les éléments qui doivent rester au centre de l’écran (boutons et entité du joueur) sont ancrés au point d’ancrage **Centre de l’écran**.

Les boutons dans le coin supérieur gauche sont ancrés au point d’ancrage **Coin supérieur gauche**, car ils doivent rester dans le coin supérieur gauche.

L’élément de texte dans le coin inférieur gauche est ancré au point d’ancrage **Coin inférieur gauche**, car il doit rester dans le coin inférieur gauche.

L’élément d’image dans le coin inférieur droit est ancré au point d’ancrage **Coin inférieur droit**, car il doit rester dans le coin inférieur droit.

## Faire sortir les éléments de l’écran

Par défaut, il n’est pas possible de déplacer des éléments hors de l’écran, ce qui sert de sécurité au cas où une disposition serait chargée dans une fenêtre très petite ou d’une taille inhabituelle, afin que les éléments restent visibles et puissent toujours être utilisés.

Ils resteront toujours à l’écran et conserveront un petit espace entre eux et les bords de l’écran.

Vous pouvez **désactiver** cela pour des éléments individuels en **faisant un clic droit** dessus, puis en désactivant **Rester à l’écran**.

> [!WARNING]
> Désactiver cette option peut parfois faire disparaître l’élément, car sa position réelle était hors de l’écran, mais la fonctionnalité le forçait à rester visible. Si cela vous arrive, **annulez** la dernière action (la désactivation de **Rester à l’écran**) via le raccourci d’annulation ou dans la **barre de menu -> Édition -> Annuler**, puis déplacez manuellement l’élément au milieu de l’écran et désactivez à nouveau **Rester à l’écran**. Il devrait maintenant rester visible même avec la fonctionnalité désactivée.

## Centrer des éléments

Tant que les éléments ont une taille fixe, les centrer est aussi simple que de les ancrer à un point d’ancrage basé sur le centre.

Si l’élément modifie dynamiquement sa taille en fonction de conditions ou d’autre chose, c’est un peu plus compliqué, mais FancyMenu dispose d’une excellente fonctionnalité pour cela ! Dans ce cas, ancrez d’abord l’élément à un point d’ancrage basé sur le centre, puis faites un clic droit dessus. Dans le menu contextuel, activez **Ancrages collants**. Cette fonctionnalité modifie la manière dont FancyMenu calcule la position de l’élément, ce qui lui permet de conserver toujours la même distance par rapport à son point d’ancrage, quelle que soit l’évolution de sa taille. Pour les ancrages centrés, il conservera toujours la même distance par rapport à l’ancrage depuis le centre absolu de l’élément, ce qui lui permet de rester toujours centré lorsqu’il est utilisé avec des ancrages centrés. (Pour les ancrages basés à gauche, il conservera toujours la même distance par rapport à l’ancrage depuis le côté gauche de l’élément, et pour les ancrages basés à droite, il conservera la même distance depuis le côté droit de l’élément.)

## Autres moyens d’améliorer le positionnement des éléments

Si **tous les points d’ancrage sont corrects**, mais que vos éléments se chevauchent toujours lorsque la fenêtre est trop petite, il est possible que votre disposition soit simplement trop chargée pour la logique habituelle de mise à l’échelle de l’interface de Minecraft.

### Échelle de l’interface forcée

Une façon d’améliorer le positionnement des éléments de la disposition consiste à forcer une échelle d’interface pour le menu en **faisant un clic droit sur l’arrière-plan de l’éditeur** et en sélectionnant **Forcer l’échelle de l’interface**. Cela fera en sorte que le menu utilise toujours la même échelle d’interface, quelle que soit celle définie dans les options de Minecraft.

### Mise à l’échelle automatique

La dernière option pour corriger les chevauchements est d’utiliser la **mise à l’échelle automatique**.
Ce réglage redimensionnera automatiquement le menu en fonction de la taille de la fenêtre afin de préserver au mieux la position des éléments lors du redimensionnement de la fenêtre. Pour activer la mise à l’échelle automatique, **faites un clic droit sur l’arrière-plan de l’éditeur** puis cliquez sur **Mise à l’échelle automatique**.

> [!WARNING]
> La **mise à l’échelle automatique** peut faire paraître **le texte** rendu par Minecraft **de mauvaise qualité**. Ce n’est pas un bug, c’est simplement ainsi que le rendu du texte de Minecraft fonctionne. Dans le cas des boutons, une bonne solution consiste à intégrer les libellés des boutons dans la texture d’arrière-plan du bouton et à définir un libellé de bouton normal vide.
