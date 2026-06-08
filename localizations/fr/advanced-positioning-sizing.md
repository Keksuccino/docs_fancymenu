---
title: Positionnement et dimensionnement avancés
description: Comment utiliser le positionnement et le dimensionnement avancés des éléments.
---
# Positionnement et dimensionnement avancés

Le positionnement/dimensionnement avancé vous permet d’avoir **un contrôle total sur la position et la taille de vos éléments**. C’est très puissant, mais aussi **bien plus chronophage** que l’utilisation du dimensionnement et du positionnement automatiques de FancyMenu.

> Si vous souhaitez simplement que les éléments s’adaptent mieux à l’**échelle de l’interface graphique** de Minecraft, il est recommandé d’utiliser plutôt l’**auto-adaptation** à l’échelle de toute la disposition, que vous pouvez activer en imposant d’abord une échelle d’interface dans le menu qui s’ouvre en faisant un clic droit sur l’arrière-plan de l’éditeur, puis en activant **Auto-Scaling** dans ce même menu.
{.is-warning}


# Activer/désactiver le mode de positionnement/dimensionnement avancé

Pour **activer** le positionnement/dimensionnement avancé d’un élément, **faites un clic droit** dessus, puis cliquez sur **Advanced Positioning** ou **Advanced Sizing**.
L’élément passera automatiquement en mode avancé lorsque vous définirez une valeur de position ou de taille avancée.

Pour le **désactiver** et revenir au positionnement/dimensionnement normal, **supprimez toutes les valeurs de positionnement/dimensionnement**.

> Lorsqu’un élément est en mode Advanced Sizing/Positioning, le redimensionnement et/ou le déplacement de l’élément peut être désactivé ou limité.
{.is-warning}

# Calculer des positions/tailles

Si le positionnement/dimensionnement avancé est si puissant, c’est parce que vous pouvez utiliser des **placeholders** dans les valeurs de position/taille.

Cela vous permet d’utiliser le placeholder **Calculator** (situé dans la catégorie de placeholders **Advanced**) en combinaison avec des placeholders de la catégorie **GUI**, comme **Screen Width**, **GUI Scale**, **Element Width**, et bien d’autres.

> Vous pouvez ajouter des placeholders en cliquant sur le bouton **Placeholders** en haut à droite de l’éditeur de texte. Si vous ne voyez pas ce bouton, le contenu que vous souhaitez modifier ne prend **pas en charge** les placeholders.
{.is-info}

Pour calculer quelque chose avec le placeholder **Calculator**, remplacez l’expression d’exemple par la vôtre. Vous pouvez utiliser des placeholders imbriqués dans l’expression, ce qui vous permet d’y exploiter les placeholders de taille d’écran, de taille d’élément, etc.

Par exemple, ce placeholder résoudra simplement `1 + 1` et affichera ensuite `2` :

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

La variable `decimal` est définie sur `false`, ce qui est important pour la plupart des calculs de taille/position, donc laissez-la toujours sur `false` lorsque vous travaillez avec le positionnement/dimensionnement avancé.

Le calculateur suivant utilise le placeholder **Screen Width** et le divise par `2` :

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> Tant que le **Advanced Positioning** est activé, l’**ancrage** et tout autre type de fonctionnalité liée à la position de l’élément seront **ignorés**. Le positionnement avancé utilise toujours le coin supérieur gauche (X0 Y0) comme origine, tout comme le fait la logique par défaut de l’interface graphique de Minecraft. Le seul réglage respecté par le positionnement avancé est **Stay on Screen**.
