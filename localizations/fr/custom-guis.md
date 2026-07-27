---
title: GUI personnalisées
description: Créez et configurez de nouveaux écrans GUI.
---

# GUI personnalisées

Les GUI personnalisées sont de nouveaux écrans que vous pouvez remplir avec des [éléments](./elements) FancyMenu.

> [!CAUTION]
> Les GUI personnalisées peuvent exécuter des actions. Importez-les uniquement depuis des sources de confiance.

# Créer une GUI personnalisée

1. Ouvrez **Personnalisation -> GUI personnalisées -> Gérer les GUI personnalisées**.
2. Sélectionnez **Nouvelle GUI**.
3. Saisissez un identifiant et configurez les paramètres de l’écran.
4. Sélectionnez **Terminé**, puis ouvrez la nouvelle GUI depuis le gestionnaire.
5. Créez et modifiez sa disposition comme pour n’importe quel autre écran.

Les identifiants peuvent utiliser des lettres minuscules, des chiffres, `.`, `_` et `-`. Ils ne peuvent pas contenir d’espaces et doivent être uniques. Les identifiants vides, invalides ou en double ne peuvent pas être enregistrés.

Les GUI personnalisées ont toujours la personnalisation de l’écran activée ; leur bouton d’activation de la personnalisation ne peut pas être désactivé.

# Paramètres de l’écran

| Paramètre | Comportement |
|---|---|
| Autoriser ESC | Permet à Échap de fermer la GUI et de revenir à son écran parent |
| Mettre le jeu/monde en pause | Met en pause le mode solo pendant que la GUI est ouverte |
| Afficher l’arrière-plan du monde | Affiche le monde chargé derrière la GUI |
| Superposition d’arrière-plan du monde | Ajoute le flou/l’assombrissement standard au-dessus du monde |
| Mode popup | Conserve l’écran parent visible derrière la GUI personnalisée |
| Superposition d’arrière-plan du popup | Ajoute un flou/une teinte au-dessus de l’écran parent en mode popup |

Le mode popup ne fusionne pas les deux écrans. La GUI personnalisée reste l’écran actif tandis que son parent est rendu derrière elle. Fermer la GUI personnalisée revient à cet écran parent lorsqu’il en existe un.

# Ouvrir une GUI personnalisée

Utilisez l’identifiant exact de la GUI personnalisée avec l’une des méthodes suivantes :

- L’[**action Ouvrir un écran ou une GUI personnalisée**](./action-scripts#open-screen-or-custom-gui-opengui).
- La [commande `/openguiscreen`](./commands#openguiscreen).

# Remplacer un écran existant

Une GUI personnalisée peut remplacer un écran Vanilla ou de mod chaque fois que cet écran s’ouvre.

1. Créez la GUI personnalisée de remplacement.
2. Ouvrez l’écran que vous souhaitez remplacer.
3. Activez **Personnalisation -> Paramètres -> Mode de personnalisation avancée**.
4. Sélectionnez **Personnalisation -> GUI personnalisées -> Remplacer l’écran actuel par une GUI personnalisée**.
5. Choisissez la GUI personnalisée de remplacement.

Gérez les remplacements enregistrés via **Personnalisation -> GUI personnalisées -> Gérer les écrans remplacés**.

Un remplacement ignore l’écran d’origine, alors testez sa navigation ainsi que toute fonctionnalité qui dépend du comportement de l’écran d’origine.
