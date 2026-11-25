---
title: Ouvrir des interfaces par commande
description: Comment ouvrir des interfaces Vanilla et personnalisées avec une commande.
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# Ouvrir des interfaces par commande

La commande `/openguiscreen` ouvre les interfaces Vanilla, celles des mods et les [interfaces personnalisées](/custom-guis). Elle peut cibler d’autres joueurs si FancyMenu est installé sur le serveur et sur leurs clients.

Pour ouvrir une interface, utilisez `/openguiscreen <screen_identifier> [<target_players>]`.

Remplacez `<screen_identifier>` par l’identifiant exact, sensible à la casse, de l’interface personnalisée ou de l’écran Vanilla/d’un mod.

Pour trouver un identifiant, ouvrez l’écran voulu et activez l’overlay de débogage avec **CTRL + ALT + D**. Sélectionnez l’identifiant sur la première ligne pour le copier. Consultez [Identifiants des écrans](/screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omettez `[<target_players>]` pour ouvrir l’interface pour vous-même, ou utilisez le nom d’un joueur ou un sélecteur comme `@a` pour l’ouvrir pour un ou plusieurs joueurs. L’argument de cible requiert le niveau d’autorisation 2 (Maître du jeu / niveau OP 2), même s’il désigne votre propre joueur, et chaque joueur ciblé doit avoir FancyMenu installé sur son client.

Tous les écrans de mods ne peuvent pas être créés directement. FancyMenu affiche une erreur si l’écran ciblé n’est pas pris en charge. Dans une disposition locale, utilisez [**Imiter un bouton Vanilla/d’un mod**](/action-scripts#mimic-vanillamod-button) sur le widget qui permet normalement de l’ouvrir.

# Fermer des interfaces par commande

Dans les rares cas où vous en avez besoin, `/closeguiscreen [<target_players>]` ferme l’écran actuel. Si la cible est omise, la commande agit sur vous ; fournir l’argument de cible requiert le niveau d’autorisation 2.
