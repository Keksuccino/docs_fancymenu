---
title: Effet de parallaxe
description: Déplacez les arrière-plans et les éléments avec le curseur de la souris.
---

# Effet de parallaxe

La parallaxe décale un arrière-plan ou un élément en fonction du mouvement de la souris afin de créer une sensation de profondeur visuelle.

# Arrière-plan du menu image

1. Faites un clic droit sur l’arrière-plan de l’éditeur de disposition.
2. Ouvrez [**Arrière-plans du menu**](./menu-backgrounds) -> **Image**.
3. Définissez la source de l’image.
4. Activez **Effet de parallaxe**.
5. Définissez les valeurs d’intensité X et Y.
6. Vous pouvez également activer **Inverser le mouvement de parallaxe**.

Les valeurs X et Y contrôlent indépendamment le mouvement horizontal et vertical. Utilisez des valeurs de `0.0` (aucun) à `1.0` (maximum).

# Éléments

1. Faites un clic droit sur un [élément](./elements).
2. Activez **Effet de parallaxe**.
3. Définissez **Intensité de parallaxe X** et **Intensité de parallaxe Y**.
4. Vous pouvez également inverser le mouvement.

Utilisez une intensité plus faible pour les couches éloignées et plus élevée pour les couches de premier plan. De grandes différences ou des couches inversées créent un effet de profondeur plus marqué.

# Dépannage

- Une intensité de `0` ne produit aucun mouvement sur cet axe.
- **Faire défiler les images larges de gauche à droite** entre en conflit avec la parallaxe d’arrière-plan et doit être désactivé.
- Un mouvement très faible peut sembler saccadé, car les positions de l’interface graphique utilisent des pixels entiers.
