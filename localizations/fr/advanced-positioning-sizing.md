---
title: Positionnement et dimensionnement avancés
description: Comment utiliser le positionnement et le dimensionnement avancés des éléments.
---
# Positionnement et dimensionnement avancés

Le positionnement et le dimensionnement avancés vous donnent un contrôle direct sur les coordonnées et les dimensions des éléments.

> [!WARNING]
> Pour l’adaptation à l’échelle de l’interface graphique, essayez d’abord **Mise à l’échelle automatique** à l’échelle de la mise en page. Faites un clic droit sur l’arrière-plan de l’éditeur, forcez une échelle de l’interface graphique, puis ակտիվez **Mise à l’échelle automatique** dans le même menu.


# Activer/Désactiver le mode de positionnement/dimensionnement avancé

Pour activer le positionnement ou le dimensionnement avancé d’un élément, faites un **clic droit** dessus et sélectionnez **Positionnement avancé** ou **Dimensionnement avancé**.
L’élément passera automatiquement en mode avancé lorsque vous définirez une valeur avancée de position ou de taille.

Pour le **désactiver** et revenir au positionnement/dimensionnement normal, **effacez toutes les valeurs de positionnement/dimensionnement**.

> [!WARNING]
> Lorsqu’un élément est en mode Dimensionnement/Positionnement avancé, le redimensionnement et/ou le déplacement de l’élément peut être désactivé ou limité.

# Calcul des positions/dimensions

Les valeurs de position et de taille avancées prennent en charge les [placeholders](./placeholders).

Cela vous permet de combiner le placeholder [**Calculator**](./placeholders#calculator-calc) avec des placeholders d’interface graphique tels que [**Screen Width**](./placeholders#screen-width-guiwidth), [**GUI Scale**](./placeholders#gui-scale-guiscale) et [**Element Width**](./placeholders#element-width-elementwidth).

> [!NOTE]
> Vous pouvez ajouter des placeholders en cliquant sur le bouton **Placeholders** en haut à droite de l’éditeur de texte. Si vous ne voyez pas ce bouton, le contenu que vous souhaitez modifier ne prend **pas** en charge les placeholders.

Pour effectuer un calcul avec le [placeholder **Calculator**](./placeholders#calculator-calc), remplacez l’expression d’exemple par la vôtre. Des placeholders imbriqués peuvent fournir les dimensions de l’écran ou de l’élément.

Cet exemple renvoie `2` :

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Conservez `decimal` sur `false` pour des calculs de position et de taille sur des pixels entiers.

Le calculateur suivant utilise le [placeholder **Screen Width**](./placeholders#screen-width-guiwidth) et le divise par `2` :

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Le positionnement avancé** ignore l’ancre de l’élément et utilise le coin supérieur gauche de l’écran (`X0 Y0`) comme origine. **Rester à l’écran** s’applique toujours.
