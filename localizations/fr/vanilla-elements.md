---
title: Éléments Vanilla
description: Comment personnaliser les éléments qui font partie des écrans par défaut.
---

# Éléments Vanilla

FancyMenu ne permet pas seulement d’ajouter de nouveaux éléments aux écrans, il permet aussi de personnaliser des éléments existants du jeu de base (Vanilla) et même d’autres mods.

## Boutons et curseurs Vanilla (widgets)

Pour personnaliser des widgets Vanilla/mod existants, créez simplement une nouvelle disposition **« pour l’écran actuel »** (PAS universelle !) et faites un **clic droit** sur les éléments dans l’éditeur, comme vous le feriez avec des éléments personnalisés.

Vous pouvez personnaliser leurs **libellés et textures** exactement comme vous le feriez avec des boutons et curseurs personnalisés.

La seule chose que vous **ne pouvez pas faire** avec les widgets Vanilla/mod, c’est personnaliser leur **script d’action** (par exemple changer ce qu’ils font lorsqu’on interagit avec eux). Cela n’est possible qu’avec des boutons et curseurs personnalisés.

Pour **déplacer** et **redimensionner** les widgets Vanilla/mod, vous devez d’abord leur attribuer un point d’ancrage. Pour cela, faites un **clic droit** dessus et cliquez sur **Point d’ancrage**. Réglez-le sur autre chose que **Original**, car c’est l’ancre par défaut des éléments Vanilla/mod.

Vous pouvez aussi **masquer** les widgets Vanilla/mod en faisant simplement un **clic droit** dessus puis en cliquant sur **Supprimer**. Ils ne sont pas réellement supprimés, mais cachés, et vous pouvez les restaurer en cliquant sur **barre de menu -> Élément -> Éléments Vanilla supprimés** puis en faisant un **clic gauche** sur le ou les éléments que vous souhaitez rendre visibles à nouveau.

> Le widget **Copyright** de l’écran titre est le seul que vous **NE POUVEZ PAS** masquer/supprimer. C’est volontaire. Merci de ne pas retirer les mentions de copyright.
{.is-warning}

## Éléments de l’écran titre

L’écran titre contient des éléments qui ne sont pas des widgets normaux (comme le logo, le texte du splash, etc.) et qui ne peuvent pas être déplacés ni personnalisés. Ils sont destinés à être supprimés et remplacés par des éléments personnalisés (comme un élément Image pour le logo ou un élément de texte de splash personnalisé pour le splash text Vanilla).

Pour les supprimer, faites simplement un clic droit dessus. Si vous souhaitez les restaurer plus tard, cliquez simplement sur **barre de menu -> Élément -> Éléments Vanilla supprimés** puis faites un **clic gauche** sur l’élément que vous voulez rendre visible à nouveau.

## Dépannage : les éléments Vanilla ne sont pas visibles dans l’éditeur

Si vous ne voyez pas les éléments Vanilla dans l’éditeur, c’est probablement parce que vous utilisez une **disposition universelle** au lieu d’une disposition **pour l’écran actuel**. Assurez-vous de créer une disposition pour l’écran actuel. Vous ne pouvez créer des dispositions pour l’écran actuel que lorsque les personnalisations sont activées pour cet écran.

## Dépannage : les personnalisations ne sont pas appliquées

Si les personnalisations apportées aux éléments Vanilla ne sont pas appliquées en dehors de l’éditeur, c’est généralement parce qu’un autre mod remplace ou modifie le menu parent des éléments Vanilla.

Un bon exemple de mod qui remplace un écran/menu est **Ice and Fire**, qui remplace l’écran titre.

Le fait que les personnalisations ne s’appliquent pas aux menus ne se limite pas aux éléments Vanilla. Les éléments personnalisés ajoutés aux écrans risquent eux aussi de ne pas être appliqués aux menus si un mod les remplace ou les modifie.
