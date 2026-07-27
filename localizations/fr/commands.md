---
title: Commandes
description: Les commandes de FancyMenu et comment les utiliser.
---

# Commandes

FancyMenu ajoute quelques commandes au jeu, qui peuvent être très utiles lorsqu'on les combine avec d'autres mods comme FTB Quests.

> [!WARNING]
> FancyMenu doit être présent sur le **SERVEUR** (et sur le client) pour utiliser les commandes en multijoueur !

## Joueurs cibles et permissions

L'argument joueur cible de `/openguiscreen`, `/closeguiscreen` et `/fmlayout` est facultatif. Lorsqu'un joueur l'omitted, la commande affecte ce joueur. Lorsqu'une cible est fournie, les noms de joueurs classiques et des sélecteurs comme `@a` peuvent être utilisés.

- Fournir l'argument cible à `/openguiscreen` ou `/closeguiscreen` nécessite le **niveau de permission 2** (Game Master / niveau OP 2), même s'il désigne la source de la commande.
- Fournir l'argument cible à `/fmlayout` nécessite le **niveau de permission 3** (Admin / niveau OP 3), même s'il désigne la source de la commande.
- Chaque sous-commande de `/fmdata` nécessite le **niveau de permission 2** (Game Master / niveau OP 2).

Pour les trois commandes avec cible facultative, omettre la cible ne fonctionne que lorsque la source de la commande est un joueur. La console du serveur doit fournir une cible et respecter l'exigence de permission de l'argument cible.

## /openguiscreen

La commande `/openguiscreen` ouvre une GUI Vanilla, d'un mod ou [GUI personnalisée](./custom-guis). Elle peut cibler d'autres joueurs lorsque FancyMenu est installé sur le serveur et sur leurs clients.

Voir [Ouverture des GUI par commande](./opengui-command) et [Identifiants d'écran](./screen-identifiers).

Toutes les interfaces de mod ne peuvent pas être créées directement. FancyMenu affiche une erreur lorsqu'un écran cible n'est pas pris en charge. Dans une disposition locale, utilisez [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) sur le widget qui l'ouvre normalement.

**Utilisation :** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

La commande `/closeguiscreen` ferme l'écran actuel pour la source de la commande ou pour les joueurs sélectionnés. Elle est utile avec les mods de quêtes, d'événements ou d'automatisation capables d'exécuter des commandes.

**Utilisation :** `/closeguiscreen [<target_players>]`

## /fmlayout

La commande `/fmlayout` définit si une disposition est সক্টivée sur un ou plusieurs clients. Utilisez exactement le nom tel qu'il apparaît dans FancyMenu, et mettez entre guillemets les noms contenant des espaces.

**Utilisation :** `/fmlayout <layout_name> <true|false> [<target_players>]`

Exemples :

- `/fmlayout quest_complete true` active `quest_complete` pour le joueur qui exécute la commande.
- `/fmlayout quest_complete false @a` la désactive pour tous les joueurs en ligne. Fournir l'argument cible nécessite le niveau de permission 3.

## /fmvariable

La commande `/fmvariable` définit et lit les [variables FancyMenu](./variables).

Pour exécuter cette commande en tant qu'un autre joueur, utilisez la commande Vanilla `/execute as` :
`/execute as ExamplePlayer run fmvariable ...`

**Utilisation :**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Get

Pour **obtenir la valeur d'une variable**, utilisez la sous-commande `get` comme ceci :
`/fmvariable get some_variable`

La valeur de cette variable sera alors affichée dans votre chat.

### Set

Pour **définir une variable**, placez le booléen de retour dans le chat avant la nouvelle valeur :
`/fmvariable set some_variable true new_value`

L'argument `send_chat_feedback` contrôle si FancyMenu confirme la modification dans le chat. L'argument `set_to_value` consomme le reste de la commande, donc la valeur peut contenir des espaces. Par exemple, `/fmvariable set greeting false Hello from FancyMenu` stocke `Hello from FancyMenu` sans envoyer de message de succès.

## /fmdata

La commande `/fmdata` envoie des données personnalisées entre le serveur et les clients FancyMenu, gère les écouteurs côté serveur et configure les données envoyées lorsque les joueurs rejoignent. Chaque sous-commande `/fmdata` nécessite le niveau de permission 2.

Voir [FM Data](./fm-data) pour toutes les sous-commandes, la syntaxe et des exemples.
