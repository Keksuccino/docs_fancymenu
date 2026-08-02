---
title: Éléments Vanilla
description: Comment personnaliser les éléments qui font partie des écrans par défaut.
---
# Éléments Vanilla

FancyMenu ne permet pas seulement d’ajouter de nouvelles choses aux écrans ; il permet aussi de personnaliser les éléments existants du jeu de base (Vanilla) et même d’autres mods.

## Boutons et curseurs Vanilla (widgets)

Pour personnaliser des widgets Vanilla/mod existants, créez simplement une nouvelle mise en page **« pour l’écran actuel »** (et **pas** une mise en page universelle !) puis **cliquez avec le bouton droit** sur les éléments dans l’éditeur, exactement comme vous le feriez avec des éléments personnalisés.

Vous pouvez personnaliser leurs **libellés et leurs textures** comme vous le feriez pour des boutons et des curseurs personnalisés.

La seule chose que vous **ne pouvez pas** faire avec les widgets Vanilla/mod, c’est personnaliser leur **script d’action** (par exemple, modifier ce qu’ils font lorsqu’on interagit avec eux). Cela n’est possible qu’avec des boutons et des curseurs personnalisés.

## Clics automatisés

Les widgets Vanilla et mod disposent d’une propriété **Clics automatisés**. Réglez-la sur un entier supérieur à `0` pour déclencher le comportement normal du widget au clic gauche autant de fois lors du chargement de l’écran. Par exemple, en réglant cette valeur sur `2`, le widget est cliqué deux fois lors de la première mise à jour de chaque nouvel écran ouvert. La valeur par défaut `0` désactive les clics automatisés.

Il s’agit de vrais clics sur le widget : chaque clic peut modifier la valeur d’un curseur ou d’un bouton à cycle, exécuter le rappel normal du widget, ou même ouvrir un autre écran. Testez le résultat avec attention, surtout si vous configurez plus d’un clic.

Pour **déplacer** et **redimensionner** les widgets Vanilla/mod, vous devez d’abord leur attribuer un point d’ancrage. Pour cela, **cliquez avec le bouton droit** dessus, puis cliquez sur **Point d’ancrage**. Réglez-le sur une valeur autre que **Original**, car c’est l’ancrage par défaut des éléments Vanilla/mod.

Vous pouvez aussi **masquer** des widgets Vanilla/mod en les **cliquant simplement avec le bouton droit** puis en cliquant sur **Supprimer**. Ils ne sont pas réellement supprimés, mais cachés, et vous pouvez les restaurer en cliquant sur **barre de menu -> Élément -> Éléments Vanilla supprimés** puis en **cliquant avec le bouton gauche** sur le ou les éléments que vous souhaitez rendre visibles à nouveau.

> [!WARNING]
> Le widget **Copyright** de l’écran titre est le seul que vous **NE POUVEZ PAS** masquer/supprimer. C’est intentionnel. Merci de ne pas retirer les mentions de copyright.

## Éléments de l’écran titre

L’écran titre contient des éléments qui ne sont pas des widgets normaux (comme le logo, le texte d’accroche, etc.) et qui ne peuvent pas être déplacés ou personnalisés. Ils sont destinés à être supprimés et remplacés par des éléments personnalisés (comme un élément Image pour le logo ou un élément de texte d’accroche personnalisé pour le texte d’accroche Vanilla).

Pour les supprimer, cliquez simplement dessus avec le bouton droit. Si vous souhaitez les restaurer plus tard, cliquez sur **barre de menu -> Élément -> Éléments Vanilla supprimés** puis **cliquez avec le bouton gauche** sur l’élément que vous voulez rendre visible à nouveau.

## Dépannage : les éléments Vanilla ne sont pas visibles dans l’éditeur

Si vous ne voyez pas les éléments Vanilla dans l’éditeur, cela est probablement dû au fait que vous utilisez une **mise en page universelle** au lieu d’une mise en page **pour l’écran actuel**. Assurez-vous de créer une mise en page pour l’écran actuel. Vous ne pouvez créer des mises en page pour l’écran actuel que lorsque les personnalisations sont activées pour cet écran.

## Dépannage : les personnalisations ne sont pas appliquées

Si les personnalisations des éléments Vanilla ne sont pas appliquées en dehors de l’éditeur, cela est généralement dû à un autre mod qui remplace ou modifie le menu parent des éléments Vanilla.

Un bon exemple de mod qui remplace un écran/menu est **Ice and Fire**, qui remplace l’écran titre.

Le fait que les personnalisations ne soient pas appliquées aux menus ne se limite pas aux éléments Vanilla. Les éléments personnalisés ajoutés aux écrans risquent également de ne pas être appliqués aux menus si un mod les remplace ou les modifie.
