---
title: Planificateurs
description: >-
  Exécutez des scripts d'action FancyMenu à intervalles réguliers, même en
  arrière-plan.
---

# Planificateurs

Les planificateurs exécutent un script d'action selon un minuteur.

Ils sont globaux (non liés à un écran spécifique), ce qui leur permet de continuer à s'exécuter même lorsqu'aucune interface graphique n'est ouverte.

Utilisez les planificateurs lorsque vous souhaitez une automatisation dans le temps plutôt qu'une action ponctuelle.
Ils sont utiles pour les tâches répétées, les tâches différées et la logique en arrière-plan.

Exemples courants :

- Mettre à jour des variables ou des éléments de texte toutes les quelques secondes (par exemple un affichage personnalisé de l'heure ou de l'état).
- Exécuter des vérifications périodiques et déclencher des actions lorsque certaines conditions sont réunies.
- Lancer des effets de menu, des sons ou d'autres comportements scriptés selon une boucle chronométrée.
- Retarder une action et l'exécuter plus tard sans qu'un écran doive rester ouvert.

# Où Les Trouver

Ouvrez la **barre de menu** de FancyMenu pendant que vous n'êtes **pas** dans l'éditeur de mise en page, puis allez dans **Personnalisation -> Gérer les planificateurs**.

# Démarrage Rapide

1. Ouvrez **Personnalisation -> Gérer les planificateurs**.
2. Cliquez sur **Ajouter un planificateur**.
3. Construisez le **Script d'action** du planificateur (c'est ce qui s'exécute à chaque tick du planificateur).
4. Sélectionnez le planificateur et cliquez sur **Modifier les paramètres**.
5. Configurez :
   - **ID du planificateur** (nom unique du planificateur ; utilisé par les actions Démarrer/Arrêter et les exigences ; autorisés : `a-z`, `0-9`, `.`, `_`, `-`)
   - **Délai de départ (ms)** (temps d'attente avant l'exécution du premier tick)
   - **Délai entre les ticks (ms)** (temps d'attente entre les ticks ; `0` = à chaque tick du jeu)
   - **Nombre de ticks à exécuter** (nombre de ticks à exécuter avant l'arrêt automatique ; `0` = permanent)
   - **Démarrer au lancement** (démarre automatiquement ce planificateur lorsque FancyMenu se charge)
6. Utilisez **Démarrer maintenant** pour l'exécuter immédiatement.
7. Utilisez **Arrêter maintenant** pour l'arrêter.

# Contrôler Et Surveiller Les Planificateurs

Il existe des actions et des exigences pour contrôler les planificateurs et vérifier leur état d'exécution.

## Actions

- **Démarrer le planificateur** prend l'ID du planificateur et le démarre s'il n'est pas déjà en cours d'exécution.
- **Arrêter le planificateur** prend également l'ID du planificateur et l'arrête.

## Exigence

Pour vérifier si un planificateur est actuellement en cours d'exécution, utilisez l'exigence **Le planificateur est en cours d'exécution**, qui prend l'ID du planificateur.

# Conseils

1. Utilisez des ID clairs comme `hud_update`, `menu_animation`, `music_fade`.
2. Commencez avec un délai entre les ticks plus élevé (par exemple `200` à `1000` ms), puis réduisez-le uniquement si nécessaire, afin d'économiser des performances.
3. Dans la liste des planificateurs, faites un clic droit sur un planificateur pour modifier rapidement ses actions.
4. Dans la liste des planificateurs, double-cliquez sur l'ID d'un planificateur pour le renommer.
