---
title: Positionnement des éléments
description: Comment utiliser correctement les points d’ancrage.
sourceBlobSha: c6c6b53374ed720fcdc32a3a0fbc1784f202cc5a
---

# Positionner des éléments dans FancyMenu

Dans FancyMenu, la position de chaque élément est déterminée par des **points d’ancrage**. Ils servent à calculer où un élément doit apparaître à l’écran et permettent d’éviter que les éléments se chevauchent, sortent de l’écran ou se déplacent de façon incorrecte lors du redimensionnement de la fenêtre.

## Comprendre les points d’ancrage

Les points d’ancrage servent d’origine pour calculer la position d’un élément. Par défaut, les éléments que vous ajoutez aux dispositions sont associés au point d’ancrage **« Centre de l’écran »**. Celui-ci correspond au milieu exact de l’écran, quelle que soit la taille de la fenêtre.

Par exemple, si un élément est situé à 2 centimètres du centre de l’écran et qu’il est associé au point d’ancrage **« Centre de l’écran »**, il conservera cette distance, même si la taille de la fenêtre change.

## Utiliser les points d’ancrage

Lorsque vous faites glisser un élément dans l’éditeur, le point d’ancrage auquel il est associé est mis en évidence. Par défaut, cette action affiche également tous les autres points d’ancrage disponibles. Vous pouvez modifier le point d’ancrage d’un élément en le faisant glisser sur un autre point d’ancrage, puis en attendant que la barre de progression se remplisse.

![Illustration des points d’ancrage](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Ancrer des éléments à d’autres éléments

Un élément peut utiliser un autre élément comme point d’ancrage. Il se déplace alors avec cet élément et conserve sa distance par rapport au coin supérieur gauche de celui-ci. C’est pratique pour les panneaux composés de plusieurs éléments, pour un libellé placé à côté d’un bouton vanilla et pour les [éléments déplaçables](/dragger).

Il existe deux façons de procéder. Dans les deux cas, l’élément conserve sa position.

### Par glisser-déposer

1. Faites glisser l’élément et maintenez le pointeur au-dessus de l’autre élément.
2. Attendez que la barre soit remplie, puis relâchez le bouton de la souris.

Si le pointeur se trouve déjà au-dessus de l’autre élément lorsque vous commencez à faire glisser l’élément, éloignez-le une fois de l’autre élément, puis ramenez-le. Les éléments qui se trouvent sous le pointeur dès le début ne sont pas pris en compte.

Les options **Survol de la zone d’ancrage** et **Survol de l’élément d’ancrage** du menu **Fenêtre** doivent être activées. Elles le sont par défaut. La première active ou désactive l’ancrage par maintien du pointeur, et la seconde ajoute les autres éléments aux points d’ancrage. L’option **Délai de maintien pour le survol de la zone/de l’élément d’ancrage (secondes)**, dans le même menu, définit la durée de maintien nécessaire. Elle est de 2 secondes par défaut.

### Par identifiant

1. Faites un clic droit sur l’autre élément, puis cliquez sur **Copier l’identifiant de l’élément**.
2. Faites un clic droit sur l’élément, puis cliquez sur **Point d’ancrage -> Autre élément**.
3. Collez l’identifiant dans le champ **Identifiant de l’élément**, puis cliquez sur **Terminé**.

Si plusieurs éléments sont sélectionnés, les étapes 2 et 3 les ancrent tous en même temps. Consultez la page [Identifiants des éléments](/element-identifiers) pour en savoir plus sur les identifiants.

## Points d’ancrage dans les zones défilantes

Les éléments d’une [zone défilante](/scrollable-areas) ont aussi des points d’ancrage, mais ceux-ci sont associés au contenu de la zone plutôt qu’à l’écran :

- Le **Coin supérieur gauche** correspond au coin supérieur gauche du contenu, le **Centre de l’écran** à son milieu, et les points d’ancrage du bas restent attachés à la fin du contenu. Un élément peut donc se trouver tout au bout d’une longue liste et y rester lorsque celle-ci s’allonge.
- Dans une zone, les éléments ne peuvent utiliser comme point d’ancrage que d’autres éléments de cette même zone.
- Lorsque vous déplacez un élément vers une zone ou hors d’une zone, les éléments qui étaient ancrés de l’autre côté de sa limite adoptent le point d’ancrage **Coin supérieur gauche** et conservent leur position.

Cela fonctionne avec le mode **Points d’ancrage** de la zone. Dans les autres modes, la zone positionne elle-même les éléments. Consultez la page [Zones défilantes](/scrollable-areas#anchors-mode).

## Exemple d’ancrage d’éléments

La capture d’écran ci-dessous montre comment choisir les points d’ancrage des éléments.

<br>
<img width="571" alt="Capture d’écran_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Tous les éléments qui doivent rester au milieu de l’écran (les boutons et l’entité du joueur) sont ancrés au point d’ancrage **Centre de l’écran**.

Les boutons situés dans le coin supérieur gauche sont ancrés au point **Coin supérieur gauche**, car ils doivent rester dans ce coin.

L’élément Texte situé dans le coin inférieur gauche est ancré au point **Coin inférieur gauche**, car il doit rester dans ce coin.

L’élément Image situé dans le coin inférieur droit est ancré au point **Coin inférieur droit**, car il doit rester dans ce coin.

## Déplacer des éléments hors de l’écran

Par défaut, il est impossible de déplacer des éléments hors de l’écran. Cette protection sert de filet de sécurité lorsqu’une disposition est chargée dans une fenêtre très petite ou de dimensions inhabituelles : les éléments restent visibles et peuvent toujours être utilisés.

Ils restent toujours à l’écran et gardent un petit espace par rapport aux bords de l’écran.

Vous pouvez **désactiver** cette fonction pour certains éléments en faisant un **clic droit** dessus, puis en désactivant **Rester à l’écran**.

> [!WARNING]
> La désactivation de cette fonction peut parfois faire disparaître l’élément, car sa position réelle se trouvait hors de l’écran, mais la fonction le maintenait visible. Si cela vous arrive, **annulez** la dernière action (la désactivation de **Rester à l’écran**) à l’aide du raccourci d’annulation ou via **barre de menus -> Édition -> Annuler**, puis déplacez manuellement l’élément au milieu de l’écran et désactivez à nouveau **Rester à l’écran**. Il devrait alors rester visible même si la fonction est désactivée.

## Centrer des éléments

Tant que les éléments ont une taille fixe, il suffit de les ancrer à un point d’ancrage centré pour les centrer.

Si la taille de l’élément change dynamiquement selon certaines conditions ou pour une autre raison, la tâche est un peu plus délicate, mais FancyMenu propose une fonctionnalité très pratique pour cela ! Dans ce cas, ancrez d’abord l’élément à un point d’ancrage centré, puis faites un clic droit dessus. Dans le menu contextuel, activez **Ancrage fixe**. Cette fonction modifie le calcul de la position de l’élément par FancyMenu : celui-ci conserve la même distance par rapport à son point d’ancrage, même si sa taille change. Avec les points d’ancrage centrés, l’élément conserve toujours la même distance entre son centre géométrique et le point d’ancrage, ce qui lui permet de rester centré. (Avec les points d’ancrage à gauche, il conserve la même distance entre son bord gauche et le point d’ancrage ; avec ceux de droite, il conserve la même distance entre son bord droit et le point d’ancrage.)

## Autres façons d’améliorer le positionnement des éléments

Si **tous les points d’ancrage sont corrects**, mais que vos éléments se chevauchent encore lorsque la fenêtre est trop petite, votre disposition est peut-être simplement trop chargée pour le système de mise à l’échelle normal de l’interface de Minecraft.

### Forcer l’échelle de l’interface

Vous pouvez améliorer le positionnement des éléments de la disposition en imposant une échelle de l’interface au menu. Pour cela, faites un **clic droit sur l’arrière-plan de l’éditeur**, puis sélectionnez **Forcer l’échelle de l’interface**. Le menu conservera alors la même échelle, quelle que soit celle définie dans les options de Minecraft.

### Mise à l’échelle automatique

La dernière option pour éviter les chevauchements consiste à utiliser la **mise à l’échelle automatique**.
Ce paramètre adapte automatiquement l’échelle du menu à la taille de la fenêtre afin de préserver autant que possible la position des éléments lors du redimensionnement. Pour activer la mise à l’échelle automatique, faites un **clic droit sur l’arrière-plan de l’éditeur**, puis cliquez sur **Mise à l’échelle automatique**.

> [!WARNING]
> La **mise à l’échelle automatique** peut rendre le **texte** affiché par Minecraft **illisible**. Ce n’est pas un bug : c’est simplement le fonctionnement du rendu du texte dans Minecraft. Pour les boutons, une bonne solution consiste à intégrer les libellés dans la texture d’arrière-plan du bouton et à laisser vide le libellé normal du bouton.
