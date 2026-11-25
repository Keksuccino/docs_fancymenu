---
title: Mises en page universelles
description: Appliquez une mise en page à plusieurs écrans compatibles.
sourceBlobSha: 2179fed92c6598b6e5c3ecfea354a4c853bc394b
---

# Mises en page universelles

Une mise en page universelle est prise en compte pour chaque écran compatible dont la personnalisation est activée. Elle ne s’applique pas aux écrans [bloqués](/incompatibility-list#screens-where-customization-is-intentionally-disabled) ni aux écrans exclus pour toute autre raison.

Utilisez les mises en page universelles pour les éléments partagés tels que les logos, la navigation, les superpositions ou les [éléments audio](/elements#audio) qui doivent apparaître sur plusieurs écrans.

# En créer une

1. Ouvrez un écran compatible et affichez la barre de menus de FancyMenu.
2. Sélectionnez **Mises en page -> Nouveau -> Pour tous les écrans [Universelle]**.
3. Ajoutez et configurez des éléments.
4. Enregistrez la mise en page.

La personnalisation de l’écran actuel doit tout de même être activée pour les écrans ordinaires. Il n’existe pas d’option globale pour tout activer, car la personnalisation peut entraîner des problèmes sur les écrans de mods non compatibles.

# Limiter les écrans

Ouvrez les paramètres de la mise en page universelle depuis le menu contextuel de l’arrière-plan de l’éditeur.

- **Liste blanche :** la mise en page s’applique uniquement aux identifiants d’écran répertoriés.
- **Liste noire :** la mise en page s’applique à tous les écrans éligibles, à l’exception des identifiants répertoriés.

Utilisez **Personnalisation -> Copier l’identifiant de l’écran actuel** pour copier un [identifiant d’écran](/screen-identifiers).

Vous pouvez également ajouter des [conditions propres à la mise en page](/conditions#layout-wide-requirements) pour déterminer quand la mise en page s’applique.

# Ordre des mises en page

Les mises en page universelles éligibles et les mises en page propres à un écran sont combinées et empilées selon leur **index de mise en page**. Les index les plus bas sont appliqués en premier ; les paramètres empilables appliqués ensuite peuvent remplacer les précédents. À index égal, les mises en page universelles sont chargées avant celles propres à un écran.
