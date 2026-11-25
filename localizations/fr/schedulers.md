---
title: Planificateurs
description: >-
  Exécutez des scripts d’action à intervalles définis, une seule fois ou en
  boucle, dans tous les menus et pendant le jeu.
sourceBlobSha: 5abcc8450371fa0d23d67618db9cf27c9bd7de97
---

# Planificateurs

Les planificateurs exécutent un [script d’action](/action-scripts) à intervalles définis : une seule fois après un délai, plusieurs fois ou en boucle jusqu’à ce qu’on les arrête. Ils fonctionnent dans tous les menus et pendant le jeu, même lorsqu’aucun menu n’est ouvert, et ne sont associés à aucune disposition.

Les planificateurs sont la méthode recommandée pour tout ce qui doit se produire plus tard ou de façon répétée. Utilisez-les plutôt que les [éléments Ticker](/elements#ticker) dans la mesure du possible.

<img width="800" alt="Un encadré Conseil de survie affiche un nouveau conseil toutes les 4 secondes, car un planificateur mélange la liste de conseils" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_tips.gif?raw=true">

> [!CAUTION]
> Un planificateur peut exécuter des actions liées aux fichiers, au réseau, aux commandes, au presse-papiers, aux packs de ressources et aux liens lorsqu’aucun menu n’est ouvert. N’utilisez que les planificateurs provenant de profils et de fichiers de personnes de confiance.

# Ajouter un planificateur

<img width="800" alt="Ouverture de Manage Schedulers, clic sur Add Scheduler et ajout de l’action Arrange List avec Shuffle pour la liste tips" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_add.gif?raw=true">

1. Ouvrez **menu bar -> Customization -> Manage Schedulers**.
2. Cliquez sur **Add Scheduler**. L’éditeur de scripts d’action s’ouvre.
3. Ajoutez les actions à exécuter à chaque fois, puis cliquez sur **Done**. Consultez la page [Scripts d’action](/action-scripts#making-an-action-script).

<img width="800" alt="Nommer le nouveau planificateur random_tip dans Edit Settings, définir un Tick Delay de 4000 et activer Start on Launch, puis le démarrer : le conseil affiché dans le menu change" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_start.gif?raw=true">

4. Le nouveau planificateur apparaît avec un identifiant aléatoire. Cliquez dessus, puis sur **Edit Settings**.
5. Attribuez-lui un **Scheduler ID**, par exemple `random_tip`, configurez son [minuteur](#settings), puis cliquez sur **Done**.
6. Cliquez sur **Start Now** pour l’essayer.

Toutes les modifications effectuées dans **Manage Schedulers** sont enregistrées immédiatement.

Dans les GIF, le planificateur exécute [**Arrange List (FM Variable)**](/action-scripts#arrange-list-fm-variable) avec l’option **Shuffle** sur la liste `tips` toutes les 4 secondes. Un élément Texte affiche la première entrée de la liste, ce qui permet d’afficher un conseil aléatoire. En savoir plus sur le fonctionnement des listes et du texte : [Actions sur les listes](/variables#list-actions).

# Paramètres

| Paramètre | Fonction |
|---|---|
| **Scheduler ID** | Le nom utilisé par les actions et les conditions. Seules les lettres minuscules, les chiffres, `.`, `_` et `-` sont autorisés. |
| **Start Delay (ms)** | Le temps d’attente après le démarrage avant la première exécution. `0` lance le planificateur immédiatement. |
| **Tick Delay (ms)** | Le délai entre deux exécutions. `0` le lance à chaque tick, soit 20 fois par seconde. |
| **Ticks to Run** | Le nombre d’exécutions avant l’arrêt automatique. `0` le laisse fonctionner jusqu’à ce qu’on l’arrête. |
| **Start on Launch** | Le démarre à chaque lancement du jeu. |

Les durées sont exprimées en millisecondes : `1000` correspond à une seconde, `60000` à une minute et `1800000` à une demi-heure.

# Démarrer et arrêter

Un planificateur ne s’exécute qu’après avoir été démarré :

- Avec **Start on Launch**, au démarrage du jeu et après un changement de [profil](/profiles).
- Avec **Start Now** dans **Manage Schedulers**. Tant que le planificateur est en cours d’exécution, le bouton devient **Stop Now**.
- Avec l’action [**Start Scheduler**](/action-scripts#start-scheduler) et l’identifiant du planificateur, par exemple dans le script d’un bouton ou d’un [écouteur](/listeners).

Il s’arrête :

- Automatiquement, après le nombre d’exécutions défini dans **Ticks to Run**.
- Avec **Stop Now**, ou avec l’action [**Stop Scheduler**](/action-scripts#stop-scheduler) et son identifiant.
- Lorsqu’il est renommé ou supprimé, lors d’un changement de [profil](/profiles) et à la fermeture du jeu. Après un redémarrage, seuls les planificateurs pour lesquels **Start on Launch** est activé sont relancés.

Un planificateur en cours d’exécution ne peut pas être démarré une deuxième fois : **Start Scheduler** ne fait rien tant qu’il n’est pas arrêté. Pour le relancer, utilisez **Stop Scheduler**, puis **Start Scheduler**.

La condition [**Scheduler Is Running**](/conditions#scheduler-is-running) vérifie si un planificateur est en cours d’exécution. Vous pouvez par exemple l’utiliser pour n’afficher un bouton d’arrêt que pendant son exécution.

## Uniquement lorsqu’un écran est ouvert

Pour qu’un planificateur s’exécute uniquement lorsqu’un écran donné est ouvert, comme l’écran titre :

1. Ouvrez la disposition de cet écran dans l’éditeur de disposition.
2. Faites un clic droit sur l’arrière-plan de l’éditeur, cliquez sur **Edit 'Open Screen' Action Script**, puis ajoutez **Start Scheduler** avec l’identifiant du planificateur.
3. Faites de nouveau un clic droit sur l’arrière-plan, cliquez sur **Edit 'Close Screen' Action Script**, puis ajoutez **Stop Scheduler** avec le même identifiant.

# Gérer les planificateurs

<img width="800" alt="Fenêtre Manage Schedulers avec trois planificateurs, random_tip sélectionné, et ses paramètres ainsi que son état Running affichés à droite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_manage.png?raw=true">

- Cliquez sur un planificateur pour voir ses paramètres, savoir s’il est en cours d’exécution et consulter son script d’action à droite.
- **Edit Actions**, ou un clic droit sur un planificateur, ouvre son script d’action.
- Double-cliquez sur l’identifiant d’un planificateur pour le renommer. Appuyez sur `Enter` pour enregistrer le nom ou sur `Esc` pour annuler. Le renommage arrête le planificateur, et les actions utilisant l’ancien identifiant ne le retrouveront plus.
- **Remove Scheduler** supprime le planificateur sélectionné après confirmation.
- **Export for AI** copie le planificateur sélectionné ou tous les planificateurs pour une [conversation avec une IA](/export-for-ai).
- La barre de recherche permet de trouver des planificateurs par leur identifiant.

Les planificateurs sont enregistrés dans `config/fancymenu/scheduler_instances.txt` (voir [Emplacements de stockage des données](/data-storage-locations)). Chaque [profil](/profiles) possède ses propres planificateurs.

# Exemple : rappel de pause

Une notification toutes les 30 minutes après le démarrage du jeu :

1. Ajoutez un planificateur avec [**Show Toast**](/action-scripts#show-toast). Définissez **Title** sur `Time for a Break` et **Message** sur `Stand up, stretch and drink some water.`
2. Dans **Edit Settings**, définissez **Scheduler ID** sur `break_reminder`, **Start Delay (ms)** et **Tick Delay (ms)** sur `1800000`, puis réglez **Start on Launch** sur **Enabled**.

Sans **Start Delay (ms)**, la première notification apparaîtrait dès le démarrage du jeu.

# Bon à savoir

- Réglez **Tick Delay (ms)** sur la valeur la plus élevée compatible avec la tâche. À `0`, les actions s’exécutent 20 fois par seconde, et les actions lentes peuvent faire ralentir le jeu.
- Si le jeu ralentit, plusieurs exécutions peuvent se produire à la suite.
- Les modifications apportées au script d’action prennent effet immédiatement, même lorsque le planificateur est en cours d’exécution. Les modifications de ses paramètres prennent effet au prochain démarrage.
- Si une action échoue, le planificateur continue de fonctionner. L’erreur est consignée dans le journal du jeu, `logs/latest.log`.
- Pour une attente unique au sein d’un même script d’action, par exemple « ouvrir l’écran 2 secondes après le clic », le bloc [Execute Later](/action-scripts#execute-later) est plus simple.
