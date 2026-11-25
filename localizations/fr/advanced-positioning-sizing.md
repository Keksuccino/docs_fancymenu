---
title: Positionnement et dimensionnement avancés
description: Comment utiliser le positionnement et le dimensionnement avancés des éléments.
sourceBlobSha: 205b887e844f770856bfd4836ea791e0acdca4b8
---
# Positionnement et dimensionnement avancés

Le positionnement et le dimensionnement avancés vous permettent de contrôler directement les coordonnées et les dimensions des éléments.

> [!WARNING]
> Pour adapter l’interface à différentes échelles, essayez d’abord la **Mise à l’échelle automatique** de l’ensemble de la disposition. Faites un clic droit sur l’arrière-plan de l’éditeur, forcez une échelle d’interface, puis activez la **Mise à l’échelle automatique** dans le même menu.


# Activer ou désactiver le mode de positionnement/dimensionnement avancé

Pour activer le positionnement ou le dimensionnement avancé d’un élément, faites un **clic droit** dessus, puis sélectionnez **Positionnement avancé** ou **Dimensionnement avancé**.
L’élément passe automatiquement en mode avancé lorsque vous définissez une valeur de position ou de taille avancée.

Pour le **désactiver** et revenir au positionnement/dimensionnement normal, **effacez toutes les valeurs de positionnement/dimensionnement**.

> [!WARNING]
> Lorsqu’un élément est en mode de dimensionnement/positionnement avancé, son redimensionnement et/ou son déplacement peuvent être désactivés ou limités.

# Calculer les positions et les tailles

Les valeurs de position et de taille avancées acceptent les [placeholders](/placeholders).

Vous pouvez ainsi combiner le placeholder [**Calculatrice**](/placeholders#calculator) avec des placeholders d’interface, tels que [**Largeur de l’écran**](/placeholders#screen-width), [**Échelle de l’interface**](/placeholders#gui-scale) et [**Largeur de l’élément**](/placeholders#element-width).

> [!NOTE]
> Vous pouvez ajouter des placeholders en cliquant sur le bouton **Placeholders** en haut à droite de l’éditeur de texte. Si ce bouton n’apparaît pas, le contenu que vous souhaitez modifier **n’accepte pas** les placeholders.

Pour effectuer un calcul avec le [placeholder **Calculatrice**](/placeholders#calculator), remplacez l’expression donnée en exemple par la vôtre. Les placeholders imbriqués peuvent fournir les dimensions de l’écran ou de l’élément.

Cet exemple renvoie `2` :

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Laissez `decimal` défini sur `false` pour effectuer des calculs de position et de taille en pixels entiers.

Le calcul suivant utilise le placeholder [**Largeur de l’écran**](/placeholders#screen-width) et divise sa valeur par `2` :

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> Le **Positionnement avancé** ignore le point d’ancrage de l’élément et utilise le coin supérieur gauche de l’écran (`X0 Y0`) comme origine. L’option **Rester à l’écran** reste applicable.
