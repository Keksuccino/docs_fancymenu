---
title: Mises en page universelles
description: Appliquez une seule mise en page à plusieurs écrans pris en charge.
---
# Mises en page universelles

Une mise en page universelle est prise en compte pour chaque écran pris en charge sur lequel la personnalisation de l’écran est activée. Elle ne s’applique pas aux écrans [bloqués](./incompatibility-list#screens-where-customization-is-intentionally-disabled) ni à ceux exclus d’une autre manière.

Utilisez les mises en page universelles pour les éléments partagés tels que les logos, la navigation, les superpositions ou les [éléments audio](./elements#audio) qui doivent rester présents sur plusieurs écrans.

# En créer une

1. Ouvrez un écran pris en charge et affichez la barre de menu FancyMenu.
2. Sélectionnez **Layouts -> New -> For All Screens [Universal]**.
3. Ajoutez et configurez des éléments.
4. Enregistrez la mise en page.

Les écrans ordinaires nécessitent toujours que **Current Screen Customization** soit activé. Il n’existe pas d’option globale pour tout activer, car les écrans de mods non pris en charge peuvent se casser lorsqu’ils sont personnalisés.

# Limiter les écrans

Ouvrez les paramètres de la mise en page universelle depuis le menu contextuel de l’arrière-plan de l’éditeur.

- **Whitelist :** la mise en page s’applique uniquement aux identifiants d’écran listés.
- **Blacklist :** la mise en page s’applique à tous les écrans éligibles, sauf ceux dont les identifiants sont listés.

Utilisez **Customization -> Copy Identifier of Current Screen** pour copier un [identifiant d’écran](./screen-identifiers).

Vous pouvez également ajouter des [exigences à l’échelle de la mise en page](./conditions#layout-wide-requirements) pour contrôler quand la mise en page s’applique.

# Ordre des mises en page

Les mises en page universelles éligibles et les mises en page spécifiques à un écran sont combinées et empilées selon l’**indice de mise en page**. Les indices les plus bas sont appliqués en premier ; les paramètres empilables ajoutés ensuite peuvent écraser les précédents. À indice égal, les mises en page universelles sont collectées avant les mises en page spécifiques à un écran.
