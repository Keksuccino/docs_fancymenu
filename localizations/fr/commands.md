---
title: Commandes
description: Les commandes de FancyMenu et comment les utiliser.
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# Commandes

FancyMenu ajoute des commandes au jeu qui peuvent s’avérer très utiles lorsqu’elles sont combinées à d’autres mods, comme FTB Quests.

> [!WARNING]
> FancyMenu doit être installé sur le **SERVEUR** (et sur le client) pour utiliser les commandes en multijoueur !

## Joueurs ciblés et permissions

L’argument du joueur cible de `/openguiscreen`, `/closeguiscreen` et `/fmlayout` est facultatif. Si le joueur ne le précise pas, la commande s’applique à lui-même. Si une cible est indiquée, il est possible d’utiliser des noms de joueurs classiques ou des sélecteurs comme `@a`.

- Indiquer l’argument de cible pour `/openguiscreen` ou `/closeguiscreen` nécessite le **niveau de permission 2** (maître du jeu / OP niveau 2), même si la cible est la source de la commande.
- Indiquer l’argument de cible pour `/fmlayout` nécessite le **niveau de permission 3** (administrateur / OP niveau 3), même si la cible est la source de la commande.
- Chaque sous-commande de `/fmdata` nécessite le **niveau de permission 2** (maître du jeu / OP niveau 2).

Pour les trois commandes dont la cible est facultative, ne pas indiquer de cible ne fonctionne que si la source de la commande est un joueur. La console du serveur doit préciser une cible et disposer du niveau de permission requis pour l’argument de cible.

## /openguiscreen

La commande `/openguiscreen` ouvre un écran Vanilla, de mod ou une [interface personnalisée](/custom-guis). Elle peut cibler d’autres joueurs si FancyMenu est installé sur le serveur et sur leurs clients.

Consultez [Ouvrir des interfaces avec une commande](/opengui-command) et [Identifiants des écrans](/screen-identifiers).

Tous les écrans de mods ne peuvent pas être créés directement. FancyMenu affiche une erreur si l’écran cible n’est pas pris en charge. Dans une disposition locale, utilisez [**Imiter un bouton Vanilla/de mod**](/action-scripts#mimic-vanillamod-button) sur le widget qui ouvre normalement cet écran.

**Utilisation :** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

La commande `/closeguiscreen` ferme l’écran actuel de la source de la commande ou des joueurs sélectionnés. Elle est utile avec les mods de quêtes, d’événements ou d’automatisation qui peuvent exécuter des commandes.

**Utilisation :** `/closeguiscreen [<target_players>]`

## /fmlayout

La commande `/fmlayout` définit si une disposition est activée sur un ou plusieurs clients. Utilisez le nom de la disposition exactement tel qu’il apparaît dans FancyMenu, et mettez entre guillemets les noms qui contiennent des espaces.

**Utilisation :** `/fmlayout <layout_name> <true|false> [<target_players>]`

Exemples :

- `/fmlayout quest_complete true` active `quest_complete` pour le joueur qui exécute la commande.
- `/fmlayout quest_complete false @a` la désactive pour tous les joueurs connectés. Indiquer l’argument de cible nécessite le niveau de permission 3.

## /fmvariable

La commande `/fmvariable` permet de définir et de lire les [variables FancyMenu](/variables).

Pour exécuter cette commande en tant qu’un autre joueur, utilisez la commande Vanilla `/execute as` :
`/execute as ExamplePlayer run fmvariable ...`

**Utilisation :**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Lire une variable

Pour **lire la valeur d’une variable**, utilisez la sous-commande `get` comme ceci :
`/fmvariable get some_variable`

La valeur de cette variable sera alors affichée dans votre chat.

### Définir une variable

Pour **définir une variable**, indiquez le booléen de retour dans le chat avant la nouvelle valeur :
`/fmvariable set some_variable true new_value`

L’argument `send_chat_feedback` détermine si FancyMenu confirme la modification dans le chat. L’argument `set_to_value` englobe le reste de la commande ; la valeur peut donc contenir des espaces. Par exemple, `/fmvariable set greeting false Hello from FancyMenu` enregistre `Hello from FancyMenu` sans afficher de message de confirmation.

## /fmdata

La commande `/fmdata` envoie des données personnalisées entre le serveur et les clients FancyMenu, gère les écouteurs côté serveur, configure les données envoyées à la connexion des joueurs et exporte cette configuration pour les [conversations avec l’IA](/export-for-ai#servers). Chaque sous-commande de `/fmdata` nécessite le niveau de permission 2.

Consultez [Données FM](/fm-data) pour découvrir toutes les sous-commandes, leur syntaxe et des exemples.
