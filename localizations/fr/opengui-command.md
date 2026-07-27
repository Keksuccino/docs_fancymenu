---
title: Ouvrir des interfaces via commande
description: Comment ouvrir des interfaces Vanilla et personnalisées via commande.
---

# Ouvrir des interfaces via commande

La commande `/openguiscreen` ouvre les interfaces Vanilla, des mods et les [interfaces personnalisées](./custom-guis). Elle peut cibler d’autres joueurs lorsque FancyMenu est installé sur le serveur et sur leurs clients.

Pour ouvrir une interface, utilisez `/openguiscreen <screen_identifier> [<target_players>]`.

Remplacez `<screen_identifier>` par l’identifiant exact, sensible à la casse, de l’interface personnalisée ou de l’écran Vanilla/du mod.

Pour trouver un identifiant, ouvrez l’écran cible et सक्रियez la superposition de débogage avec **CTRL + ALT + D**. Sélectionnez l’identifiant sur sa première ligne pour le copier. Consultez [Identifiants d’écran](./screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omettez `[<target_players>]` pour ouvrir l’interface pour vous-même, ou utilisez un nom de joueur ou un sélecteur tel que `@a` pour l’ouvrir pour un ou plusieurs joueurs. Fournir l’argument de cible nécessite le niveau de permission 2 (Game Master / OP niveau 2), même si la cible est vous-même, et chaque joueur ciblé doit avoir FancyMenu installé sur son client.

Tous les écrans de mods ne peuvent pas être créés directement. FancyMenu affiche une erreur lorsqu’un écran cible n’est pas pris en charge. Dans une configuration locale, utilisez [**Bouton Imiter Vanilla/Mod**](./action-scripts#mimic-vanillamod-button-mimicbutton) sur le widget qui l’ouvre normalement.

# Fermer des interfaces via commande

Dans le cas rare où vous en avez besoin, `/closeguiscreen [<target_players>]` ferme l’écran actuel. La commande vous affecte lorsque la cible est omise ; fournir l’argument de cible nécessite le niveau de permission 2.
