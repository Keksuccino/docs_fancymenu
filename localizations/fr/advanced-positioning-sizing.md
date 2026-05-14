---
title: Positionnement et dimensionnement avancés
description: Comment utiliser le positionnement et le dimensionnement avancés des éléments.
---

# Positionnement et dimensionnement avancés

Le positionnement/dimensionnement avancé vous permet d’avoir **un contrôle total sur la position et la taille de vos éléments**. C’est très puissant, mais aussi **beaucoup plus chronophage** que le dimensionnement et le positionnement automatisés de FancyMenu.

> Si vous souhaitez simplement que les éléments s’adaptent mieux à l’**échelle de l’interface (GUI)** de Minecraft, il est recommandé d’utiliser plutôt l’**auto-ajustement** à l’échelle du layout, que vous pouvez activer en forçant d’abord une échelle de GUI dans le menu qui s’ouvre en faisant un clic droit sur l’arrière-plan de l’éditeur, puis en activant **Auto-Scaling** dans le même menu.
{.is-warning}


# Activer/désactiver le mode de positionnement/dimensionnement avancé

Pour **activer** le positionnement/dimensionnement avancé d’un élément, faites **un clic droit** dessus, puis cliquez sur **Advanced Positioning** ou **Advanced Sizing**.
L’élément passera automatiquement en mode avancé lorsque vous définirez une valeur de position ou de taille avancée.

Pour le **désactiver** et revenir au positionnement/dimensionnement normal, **effacez toutes les valeurs de positionnement/dimensionnement**.

> Lorsqu’un élément est en mode Advanced Sizing/Positioning, le redimensionnement et/ou le déplacement de l’élément peut être désactivé ou limité.
{.is-warning}

# Calculer des positions/dimensions

Si le positionnement/dimensionnement avancé est si puissant, c’est parce que vous pouvez utiliser des **placeholders** dans les valeurs de position/taille.

Cela vous permet d’utiliser le placeholder **Calculator** (situé dans la catégorie de placeholders **Advanced**) en combinaison avec des placeholders de la catégorie **GUI**, comme **Screen Width**, **GUI Scale**, **Element Width**, et bien plus encore.

> Vous pouvez ajouter des placeholders en cliquant sur le bouton **Placeholders** en haut à droite de l’éditeur de texte. Si vous ne voyez pas ce bouton, le contenu que vous souhaitez modifier ne **prend pas en charge** les placeholders.
{.is-info}

Pour calculer quelque chose avec le placeholder **Calculator**, remplacez l’expression d’exemple par la vôtre. Vous pouvez utiliser des placeholders imbriqués dans l’expression, ce qui vous permet d’y utiliser la taille de l’écran, la taille de l’élément, etc.

Par exemple, ce placeholder calculera simplement `1 + 1` et affichera ensuite `2` :

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

La variable `decimal` est définie sur `false`, ce qui est important pour la plupart des calculs de positionnement/dimensionnement. Définissez donc toujours cette valeur sur `false` lorsque vous travaillez avec le positionnement/dimensionnement avancé.

Le calculateur suivant utilise le placeholder **Screen Width** et le divise par `2` :

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`
