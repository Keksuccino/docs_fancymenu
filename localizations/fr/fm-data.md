---
title: Partage de données Client < - > Serveur
description: >-
  Envoyez et recevez des données personnalisées entre le serveur et le client
  avec FancyMenu.
---

# FM Data

Le système « FM Data » vous permet d’envoyer des données textuelles personnalisées entre le serveur et le client.

Chaque sous-commande `/fmdata` nécessite un **niveau de permission 2** (Game Master / niveau OP 2).

Chaque message FM Data comporte :

1. Un **identifiant de données** (le type de message)
2. Une **valeur de données** (le contenu réel)

Exemple :

- Identifiant : `hud.food`
- Données : `18/20`

# Démarrage rapide

1. Le serveur envoie des données avec `/fmdata send ...`
2. Le client les reçoit avec le listener FancyMenu **On FM Data Received**
3. Le client peut aussi renvoyer des données avec l’action **Send FM Data To Server**
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

- `<target_players>` prend en charge les noms de joueurs et les sélecteurs tels que `@a`, `@p` et `@s`
- Utilisez des guillemets pour les valeurs contenant des espaces

# Client : réception des données

Utilisez le listener FancyMenu :

- **On FM Data Received**

Variables disponibles :

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` est :

- l’IP du serveur en multijoueur
- `integrated_server` en solo

Cas d’utilisation courants :

- Mettre à jour des éléments de texte
- Déclencher des actions de menu
- Exécuter une logique selon l’identifiant / les données reçus

# Client -> Serveur

Utilisez l’action FancyMenu :

- **Send FM Data To Server**

L’action comporte 2 entrées :

1. Identifiant de données
2. Données

Le serveur peut ensuite traiter les données reçues avec `/fmdata listener ...`.

# Listeners serveur

Les listeners serveur écoutent les données entrantes des clients et peuvent exécuter une ou plusieurs commandes lorsqu’ils sont déclenchés.

Les listeners serveur sont enregistrés et restent actifs après redémarrage.

Gérez-les avec :

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Syntaxe d’ajout / modification

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

`matching_type_identifier` et `matching_type_data` peuvent être :

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Règles de correspondance

- `ignore_case_identifier` et `ignore_case_data` sont des bascules vrai/faux
- `listen_for_identifier` prend en charge le caractère générique `*` (correspond toujours)
- `listen_for_data` prend en charge le caractère générique `*` (correspond toujours)
- `fire_for_player` utilise les sélecteurs de joueurs standards (par exemple `@a`, `@p`, `Player761`)

## Commandes à l’activation

`commands_to_execute_on_fire` est un unique champ de texte.

- Séparez plusieurs commandes avec `|||`
- Échappez un séparateur littéral avec `\|\|\|`

Vous pouvez utiliser ici deux espaces réservés spéciaux, remplacés juste avant l’exécution des commandes :

- `%fm_sender%` -> joueur ayant envoyé les données FM
- `%fm_data%` -> valeur de données reçue du client

Les commandes s’exécutent comme des commandes serveur.

## Exemples de commandes

Réagir à l’appui d’un bouton par n’importe quel joueur :

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% a appuyé sur le bouton\"}"
```

Exécuter plusieurs commandes lorsque les données contiennent `gold` :

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Récompense de %fm_sender% : %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Données de bienvenue

Les données de bienvenue envoient des FM Data aux joueurs correspondants lorsqu’ils rejoignent la partie.

Gérez les entrées avec :

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Syntaxe d’ajout / modification

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

- `<target_player>` prend en charge les sélecteurs standards comme `@a`, `@p`, `@s`
- Les données sont envoyées aux joueurs correspondants lorsqu’ils rejoignent la partie
- Les entrées sont enregistrées et chargées automatiquement

## Exemples de commandes

Envoyer des données de bienvenue à tous les joueurs qui rejoignent :

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Bienvenue !"
```

Envoyer des données de bienvenue à un seul joueur :

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Avantages VIP activés"
```

# Bonnes pratiques

1. Utilisez des identifiants clairs comme `hud.food`, `menu.shop.open`, `quest.progress`.
2. Conservez un format de données cohérent pour chaque identifiant.
3. Commencez simplement : testez avec `/fmdata send` avant de créer des listeners complexes.
4. Utilisez `@a` uniquement lorsque vous souhaitez réellement un comportement global.
5. Utilisez `/fmdata listener list` et `/fmdata welcome_data list` pour garder une configuration propre.
