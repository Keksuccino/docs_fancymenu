---
title: Partage de données Client < - > Serveur
description: >-
  Envoyez et recevez des données personnalisées entre le serveur et le client
  avec FancyMenu.
---

# Données FM

Le système "FM Data" vous permet d’envoyer des données textuelles personnalisées entre le serveur et le client.

Chaque message FM Data contient :

1. Un **identifiant de donnée** (le type de message)
2. Une **valeur de donnée** (le contenu réel)

Exemple :

- Identifiant : `hud.food`
- Donnée : `18/20`

# Démarrage rapide

1. Le serveur envoie des données avec `/fmdata send ...`
2. Le client les reçoit avec l’écouteur FancyMenu **On FM Data Received**
3. Le client peut aussi renvoyer des données avec l’action **Send FM Data To Server**
4. Le serveur peut réagir automatiquement avec `/fmdata listener ...`
5. Le serveur peut envoyer automatiquement des données à la connexion avec `/fmdata welcome_data ...`

# Serveur -> Client

Utilisez :

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

Exemples :

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Remarques :

- `<target_player>` prend en charge les sélecteurs de joueurs standards comme `@a`, `@p`, `@s`
- Utilisez des guillemets pour les valeurs contenant des espaces

# Client : réception des données

Utilisez l’écouteur FancyMenu :

- **On FM Data Received**

Variables disponibles :

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` est :

- L’IP du serveur en multijoueur
- `integrated_server` en solo

Cas d’utilisation courants :

- Mettre à jour des éléments de texte
- Déclencher des actions de menu
- Exécuter une logique selon l’identifiant/la donnée reçue

# Client -> Serveur

Utilisez l’action FancyMenu :

- **Send FM Data To Server**

L’action possède 2 entrées :

1. Identifiant de donnée
2. Donnée

Le serveur peut ensuite traiter les données entrantes avec `/fmdata listener ...`.

# Écouteurs du serveur

Les écouteurs du serveur surveillent les données entrantes des clients et peuvent exécuter une ou plusieurs commandes lorsqu’ils sont déclenchés.

Les écouteurs du serveur sont enregistrés et restent actifs après un redémarrage.

Gérez-les avec :

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Syntaxe pour ajouter / modifier

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

- `ignore_case_identifier` et `ignore_case_data` sont des options vrai/faux
- `listen_for_identifier` prend en charge le joker `*` (correspond toujours)
- `listen_for_data` prend en charge le joker `*` (correspond toujours)
- `fire_for_player` utilise les sélecteurs de joueurs classiques (par exemple `@a`, `@p`, `Player761`)

## Commandes au déclenchement

`commands_to_execute_on_fire` est un seul champ texte.

- Séparez plusieurs commandes avec `|||`
- Échappez un séparateur littéral avec `\|\|\|`

Vous pouvez utiliser ici deux espaces réservés spéciaux, remplacés juste avant l’exécution des commandes :

- `%fm_sender%` -> joueur ayant envoyé les données FM
- `%fm_data%` -> valeur des données reçues du client

Les commandes sont exécutées en tant que commandes serveur.

## Exemples de commandes

Réagir à l’appui d’un bouton de n’importe quel joueur :

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% a appuyé sur le bouton\"}"
```

Exécuter plusieurs commandes lorsque les données contiennent `gold` :

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Récompense de %fm_sender% : %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Données de bienvenue

Les données de bienvenue envoient des FM Data aux joueurs correspondants lorsqu’ils rejoignent le serveur.

Gérez les entrées avec :

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Syntaxe pour ajouter / modifier

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

- `<target_player>` prend en charge les sélecteurs classiques comme `@a`, `@p`, `@s`
- Les données sont envoyées aux joueurs correspondants lorsqu’ils rejoignent le serveur
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
2. Gardez un format de données cohérent pour chaque identifiant.
3. Commencez simplement : testez avec `/fmdata send` avant de construire des écouteurs complexes.
4. Utilisez `@a` uniquement lorsque vous voulez vraiment un comportement global.
5. Utilisez `/fmdata listener list` et `/fmdata welcome_data list` pour garder une configuration propre.
