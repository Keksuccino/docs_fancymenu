---
title: Mises en page universelles
description: Comment créer et utiliser des mises en page universelles.
---

# Que sont les mises en page universelles ?

Les mises en page universelles sont une fonctionnalité puissante de FancyMenu qui vous permet de créer des mises en page applicables à **plusieurs écrans** au lieu d’un seul écran spécifique. Cela les rend incroyablement utiles pour créer des éléments d’interface cohérents qui apparaissent dans tout votre jeu.

Voyez les mises en page universelles comme des mises en page « globales » qui peuvent apparaître partout dans votre jeu.

# Pourquoi utiliser des mises en page universelles ?

Les mises en page universelles sont très pratiques lorsque vous souhaitez :

- Ajouter le même arrière-plan à tous les écrans
- Créer un logo ou un texte qui apparaît sur de nombreux écrans
- Faire en sorte que les éléments audio continuent de jouer sur plusieurs écrans
- Construire une apparence cohérente dans tout votre jeu

# Comment fonctionnent les mises en page universelles

Lorsque vous créez une mise en page universelle, elle est chargée avec **chaque écran** du jeu par défaut. Cela signifie que tous les éléments que vous ajoutez à une mise en page universelle (comme des boutons, des images ou du texte) apparaîtront sur tous les écrans.

Mais pas d’inquiétude ! Il est aussi possible de faire en sorte que la mise en page universelle ne se charge que sur certains écrans ! Pour cela, faites défiler jusqu’aux sections **liste noire** et **liste blanche**.

# Créer une mise en page universelle

1. Ouvrez n’importe quel écran dans le jeu
2. Appuyez sur **Ctrl+Alt+C** pour afficher le menu de personnalisation
3. Allez dans **Mises en page → Nouveau → Pour tous les écrans [Universel]**
4. Concevez votre mise en page avec des éléments comme des images, du texte ou des boutons
5. Enregistrez votre mise en page avec un nom explicite

# Gérer les écrans qui reçoivent votre mise en page universelle

## Utiliser la liste noire

La liste noire vous permet de spécifier les écrans sur lesquels vous ne voulez PAS que votre mise en page universelle apparaisse :

1. Dans l’éditeur de mise en page, faites un clic droit sur l’arrière-plan
2. Sélectionnez **Paramètres de la mise en page → Options de mise en page universelle**
3. Cliquez sur **Ajouter un écran à la liste noire**
4. Entrez l’identifiant de l’écran (par exemple `title_screen` pour l’écran titre)

Votre mise en page universelle s’affichera désormais sur tous les écrans SAUF ceux que vous avez placés dans la liste noire.

## Utiliser la liste blanche

La liste blanche est l’inverse : elle n’affiche votre mise en page universelle QUE sur des écrans spécifiques :

1. Dans l’éditeur de mise en page, faites un clic droit sur l’arrière-plan
2. Sélectionnez **Paramètres de la mise en page → Options de mise en page universelle**
3. Cliquez sur **Ajouter un écran à la liste blanche**
4. Entrez l’identifiant de l’écran pour chaque écran où vous souhaitez que la mise en page apparaisse

Lorsque vous utilisez une liste blanche, votre mise en page universelle s’affichera UNIQUEMENT sur les écrans que vous avez listés.

# Trouver les identifiants d’écran

Pour ajouter des écrans à la liste blanche ou noire, vous devez connaître leurs identifiants :

1. Allez sur l’écran que vous voulez identifier
2. Appuyez sur **Ctrl+Alt+C** pour ouvrir le menu de personnalisation
3. Cliquez sur **Personnalisation → Copier l’identifiant de l’écran actuel**
4. L’identifiant est maintenant copié dans votre presse-papiers

Vous pouvez coller cet identifiant dans la liste blanche ou noire.

# Activer la personnalisation pour tous les écrans

Il n’est pas possible d’activer la personnalisation pour tous les écrans en une seule fois.
C’est volontaire et cela évite que des personnes cassent accidentellement leur jeu en activant la personnalisation pour un écran moddé non pris en charge.

# Conseils avancés

## Gérer l’ordre de chargement

Lorsque vous avez à la fois des mises en page universelles et des mises en page spécifiques à un écran, les mises en page universelles sont chargées EN PREMIER. Cela signifie que les mises en page spécifiques à un écran peuvent remplacer des éléments des mises en page universelles.

## Conditions de chargement

Vous pouvez ajouter des conditions de chargement à votre mise en page universelle afin qu’elle ne se charge que dans certaines conditions :

1. Faites un clic droit dans l’éditeur
2. Choisissez **Paramètres de la mise en page → Conditions globales de la mise en page**
3. Ajoutez des conditions comme l’heure de la journée, le système d’exploitation ou d’autres exigences
