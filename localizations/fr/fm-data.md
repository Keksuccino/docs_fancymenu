---
title: Partage de données client < - > serveur
description: >-
  Envoyez et recevez des données personnalisées entre le serveur et le client
  avec FancyMenu.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM Data

Le système « FM Data » vous permet d'envoyer des données textuelles personnalisées entre le serveur et le client.

Chaque sous-commande `/fmdata` nécessite le **niveau de permission 2** (Game Master / niveau OP 2).

Chaque message FM Data contient :

1. Un **identifiant de données** (le type de message)
2. Une **valeur de données** (le contenu proprement dit)

Exemple :

- Identifiant : `hud.food`
- Données : `18/20`

# Démarrage rapide

1. Le serveur envoie des données avec `/fmdata send ...`
2. Le client les reçoit à l'aide du listener FancyMenu **On FM Data Received**
3. Le client peut également renvoyer des données à l'aide de l'action **Send FM Data To Server**
4. Le serveur peut réagir automatiquement avec `/fmdata listener ...`
5. Le serveur peut envoyer automatiquement des données à la connexion avec `/fmdata welcome_data ...`

# Serveur -> Client

Utilisez :

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Exemples :

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Remarques :

- `<target_players>` accepte les noms de joueurs et les sélecteurs tels que `@a`, `@p` et `@s`
- Utilisez des guillemets pour les valeurs contenant des espaces

# Client : recevoir des données

Utilisez le listener FancyMenu :

- **On FM Data Received**

Variables disponibles :

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` correspond à :

- L'adresse IP du serveur en multijoueur
- `integrated_server` en mode solo

Cas d'utilisation courants :

- Mettre à jour des éléments de texte
- Déclencher des actions de menu
- Exécuter une logique en fonction de l'identifiant ou des données reçues

# Client -> Serveur

Utilisez l'action FancyMenu :

- **Send FM Data To Server**

Cette action comporte 2 champs :

1. Identifiant de données
2. Données

Le serveur peut ensuite traiter les données reçues avec `/fmdata listener ...`.

# Listeners du serveur

Les listeners du serveur écoutent les données envoyées par les clients et peuvent exécuter une ou plusieurs commandes lorsqu'ils sont déclenchés.

Les listeners du serveur sont enregistrés et restent actifs après un redémarrage.

Gérez-les avec :

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Syntaxe d'ajout et de modification

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Syntaxe de suppression

```mcfunction
/fmdata listener remove <listener_name>
```

## Types de correspondance

`matching_type_identifier` et `matching_type_data` peuvent prendre les valeurs suivantes :

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Règles de correspondance

- `ignore_case_identifier` et `ignore_case_data` sont des options activées/désactivées (`true`/`false`)
- `listen_for_identifier` accepte le caractère générique `*` (correspond toujours)
- `listen_for_data` accepte le caractère générique `*` (correspond toujours)
- `fire_for_player` utilise les sélecteurs de joueur habituels (par exemple `@a`, `@p`, `Player761`)

## Commandes exécutées au déclenchement

`commands_to_execute_on_fire` est un champ de texte unique.

- Séparez plusieurs commandes avec `|||`
- Pour utiliser le séparateur tel quel, échappez-le ainsi : `\|\|\|`

Vous pouvez utiliser deux espaces réservés spéciaux qui seront remplacés juste avant l'exécution des commandes :

- `%fm_sender%` -> joueur ayant envoyé les données FM Data
- `%fm_data%` -> valeur reçue du client

Les commandes sont exécutées comme des commandes du serveur.

## Exemples de commandes

Réagir à l'appui sur un bouton par n'importe quel joueur :

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Exécuter plusieurs commandes lorsque les données contiennent `gold` :

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Données de bienvenue

Les données de bienvenue envoient des données FM Data aux joueurs correspondants lorsqu'ils rejoignent le serveur.

Gérez les entrées avec :

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Syntaxe d'ajout et de modification

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Syntaxe de suppression

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Remarques :

- `<target_player>` accepte les sélecteurs habituels comme `@a`, `@p` et `@s`
- Les données sont envoyées aux joueurs correspondants lorsqu'ils rejoignent le serveur
- Les entrées sont enregistrées et chargées automatiquement

## Exemples de commandes

Envoyer des données de bienvenue à tous les joueurs qui rejoignent le serveur :

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Envoyer des données de bienvenue à un seul joueur :

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Export pour l'IA

Pour demander de l'aide à Alice ou à une autre IA, exportez les listeners et les données de bienvenue du serveur avec [Export for AI](/export-for-ai#servers) :

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` envoie un message dans le chat qui copie l'export lorsque vous cliquez dessus. `file` l'enregistre sur le serveur dans `fancymenu_data/ai_exports/`.

# Bonnes pratiques

1. Utilisez des identifiants explicites comme `hud.food`, `menu.shop.open` et `quest.progress`.
2. Gardez un format de données cohérent pour chaque identifiant.
3. Commencez simplement : testez avec `/fmdata send` avant de créer des listeners complexes.
4. N'utilisez `@a` que si vous souhaitez réellement appliquer le comportement à tout le monde.
5. Utilisez `/fmdata listener list` et `/fmdata welcome_data list` pour garder vos configurations bien organisées.
