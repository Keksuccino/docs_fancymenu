---
title: Commandes
description: Les commandes de FancyMenu et comment les utiliser.
---

# Commandes

FancyMenu ajoute quelques commandes au jeu, qui peuvent être très utiles lorsqu’on les combine avec d’autres mods comme FTB Quests.

> FancyMenu doit être installé côté **SERVEUR** (et côté client) pour pouvoir utiliser les commandes en multijoueur !
{.is-warning}

## /openguiscreen

La commande `/openguiscreen` vous permet d’ouvrir une interface graphique (vanilla/mod et interfaces personnalisées).
Elle peut même ouvrir à distance des interfaces pour d’autres joueurs lorsque FancyMenu est installé à la fois sur le serveur et sur les clients.

Pour une description plus détaillée de cette commande, consultez la page [Ouvrir des GUI via commande](/opengui-command).

Cette commande ne fonctionnera pas avec tous les écrans, en particulier les écrans de mods. Si la commande échoue à ouvrir un écran, un message d’erreur s’affichera. Il n’y a pas grand-chose à faire dans ce cas, car il s’agit probablement d’un écran trop complexe pour être ouvert automatiquement par FancyMenu.

Je n’ajouterai plus manuellement de compatibilité pour les écrans de mods, car prendre en charge tous les mods existants me prendrait des années, désolé.

**Utilisation :** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

La commande `/closeguiscreen` vous permet de fermer l’interface graphique actuelle.

Hein ? C’est totalement inutile, dites-vous ?
Eh bien oui, mais en fait non.

Cette commande est utile lorsqu’on utilise des mods qui déclenchent des commandes lors d’actions spécifiques.
Donc oui, cette commande est absolument inutile si vous l’utilisez sans autres mods, mais elle peut être très pratique si vous avez les bons mods installés !

**Utilisation :** `/closeguiscreen <target_player>`

## /fmvariable

La commande `/fmvariable` vous permet de définir et de récupérer des variables FancyMenu.

Pour exécuter cette commande en tant qu’un autre joueur sur les serveurs, vous pouvez utiliser la commande vanilla `/execute as`.
Par exemple, si vous voulez exécuter la commande `/fmvariable` en tant que joueur `ExamplePlayer`, vous taperiez :
`/execute as ExamplePlayer run fmvariable...`.

**Utilisation :** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### Get
Pour **obtenir la valeur d’une variable**, utilisez la sous-commande `get` comme ceci :
`/fmvariable get some_variable`

La valeur de cette variable sera alors affichée dans votre chat.

### Set
Pour **définir une variable**, utilisez la sous-commande `set` comme ceci :
`/fmvariable set some_variable new_value true`

Le dernier argument sert à indiquer si vous souhaitez recevoir un retour dans le chat, c’est-à-dire si vous voulez que cette commande affiche des messages dans votre chat.
