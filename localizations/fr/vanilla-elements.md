---
title: Éléments du jeu de base
description: Comment personnaliser les éléments présents par défaut dans les écrans.
sourceBlobSha: 3943106d1e4f0722aad0d1578908262b7c8d92ec
---

# Éléments du jeu de base

FancyMenu vous permet non seulement d'ajouter de nouveaux éléments aux écrans, mais aussi de personnaliser les éléments existants du jeu de base (Vanilla), voire ceux d'autres mods.

## Boutons et curseurs du jeu de base (widgets)

Pour personnaliser les boutons et les curseurs d'un écran, créez une disposition pour l'écran actuel (et non une [disposition universelle](/universal-layouts)), puis faites un clic droit sur les éléments dans l'éditeur.

Ils disposent des mêmes paramètres que vos propres [boutons](/elements#button) et [curseurs](/elements#slider), comme les textures, les sons et les infobulles. Seul leur script d'action ne peut pas être modifié : ils continuent à faire ce qu'ils faisaient auparavant.

Les éléments du jeu de base ne peuvent pas être placés dans des [zones défilantes](/scrollable-areas), car ils font partie du menu lui-même.

### Libellés

- **Libellé** et **Libellé au survol** remplacent le texte d'un bouton. Pour les autres widgets, comme les curseurs, ces options s'appellent **Texte du widget** et **Texte du widget au survol**. Sans ces options, le widget conserve son propre texte.
- **Alignement du libellé** place le libellé à **gauche**, au **centre** ou à **droite** du widget. Si les libellés sont trop larges pour le widget, ils défilent d'un côté à l'autre, quel que soit leur alignement.
- **Échelle du libellé**, **Couleur de base du libellé**, **Couleur du libellé au survol**, **Ombre du libellé** et **Souligner le libellé au survol** permettent de modifier la taille, les couleurs et l'ombre du libellé.

Pour aligner simultanément les libellés de plusieurs boutons, sélectionnez-les avec `Ctrl` + clic (voir [Sélectionner](/layout-editor#selecting)), faites un clic droit sur l'un d'eux, puis définissez **Alignement du libellé** pour tous. Pour les libellés de tous les menus, utilisez **Alignement du libellé** dans [Personnalisations globales](/global-customizations#labels). Un [modèle](/button-slider-templates) peut également appliquer son style de libellé à tous les boutons d'un écran.

## Clics automatisés

Les widgets du jeu de base et des mods possèdent une propriété **Clics automatisés**. Définissez-la sur un nombre entier supérieur à `0` pour déclencher autant de fois le comportement original du clic gauche du widget au chargement de l'écran. Par exemple, si vous la définissez sur `2`, le widget sera cliqué deux fois lors de la première mise à jour de chaque nouvel écran ouvert. La valeur par défaut `0` désactive les clics automatisés.

Il s'agit de véritables clics sur le widget : chaque clic peut modifier la valeur d'un curseur ou d'un bouton à cycle, exécuter la fonction de rappel habituelle du widget, voire ouvrir un autre écran. Vérifiez attentivement le résultat, surtout si vous configurez plusieurs clics.

Pour **déplacer** et **redimensionner** les widgets du jeu de base ou des mods, vous devez d'abord leur attribuer un point d'ancrage. Pour ce faire, faites un **clic droit** sur le widget, puis cliquez sur **Point d'ancrage**. Choisissez une valeur autre que **Original**, qui est le point d'ancrage par défaut des éléments du jeu de base et des mods.

Vous pouvez aussi **masquer** les widgets du jeu de base ou des mods en faisant simplement un **clic droit** dessus, puis en cliquant sur **Supprimer**. Ils ne sont pas réellement supprimés, mais masqués. Pour les restaurer, cliquez sur **barre de menu -> Élément -> Éléments du jeu de base supprimés**, puis faites un **clic gauche** sur le ou les éléments que vous souhaitez afficher à nouveau.

> [!WARNING]
> Le widget **Copyright** de l'écran titre est le seul que vous **NE POUVEZ PAS** masquer ni supprimer. C'est intentionnel. Veuillez ne pas supprimer les mentions de copyright.

## Éléments de l'écran titre

L'écran titre comporte des éléments qui ne sont pas des widgets classiques (comme le logo, le texte d'accroche, etc.) et qui ne peuvent être ni déplacés ni personnalisés. Ils sont destinés à être supprimés et remplacés par des éléments personnalisés (par exemple, un élément Image pour le logo ou un élément Texte d'accroche personnalisé pour le texte d'accroche du jeu de base).

Pour les supprimer, faites simplement un clic droit dessus. Si vous souhaitez les restaurer plus tard, cliquez sur **barre de menu -> Élément -> Éléments du jeu de base supprimés**, puis faites un **clic gauche** sur l'élément que vous souhaitez afficher à nouveau.

## Dépannage : les éléments du jeu de base ne sont pas visibles dans l'éditeur

Si vous ne voyez pas les éléments du jeu de base dans l'éditeur, il est probable que vous utilisiez une **disposition universelle** plutôt qu'une disposition **pour l'écran actuel**. Veillez à créer une disposition pour l'écran actuel. Vous ne pouvez en créer une que si les personnalisations sont activées pour cet écran.

## Dépannage : les personnalisations ne sont pas appliquées

Si les personnalisations des éléments du jeu de base ne sont pas appliquées en dehors de l'éditeur, c'est généralement parce qu'un autre mod remplace ou modifie le menu parent de ces éléments.

**Ice and Fire** est un bon exemple de mod qui remplace un écran ou un menu : il remplace l'écran titre.

Le problème des personnalisations qui ne sont pas appliquées aux menus ne concerne pas uniquement les éléments du jeu de base. Les éléments personnalisés ajoutés aux écrans risquent eux aussi de ne pas être appliqués aux menus si un mod les remplace ou les modifie.
