---
title: Ouvrir les interfaces par commande
description: Comment ouvrir des interfaces Vanilla et personnalisées via une commande.
---

# Ouvrir des interfaces par commande

FancyMenu est fourni avec une commande qui vous permet d’ouvrir des interfaces Vanilla et personnalisées via une commande.
Vous pouvez même ouvrir à distance des interfaces pour **d’autres joueurs** en installant FancyMenu à la fois sur le **serveur et les clients**.

Pour ouvrir une interface, utilisez simplement la commande `/openguiscreen <screen_identifier> <target_player>`.

Remplacez `<screen_identifier>` par l’identifiant réel du menu de l’interface que vous souhaitez ouvrir.
Il peut s’agir de l’identifiant de votre interface personnalisée (créée avec FancyMenu) ou de l’identifiant normal du menu d’une interface Vanilla/mod.

Pour obtenir **l’identifiant du menu des interfaces Vanilla/mod**, ouvrez le menu dont vous voulez connaître l’identifiant et সকtivez la **superposition de débogage** de FancyMenu via **Personnalisation -> Superposition de débogage**. Vous pouvez ensuite cliquer sur l’identifiant affiché sur la première ligne pour le copier dans votre presse-papiers.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Laissez l’argument `<target_player>` vide pour ouvrir l’interface pour votre client, ou choisissez un joueur (ou plusieurs joueurs) pour ouvrir l’interface.
Gardez à l’esprit que l’autre joueur doit avoir FancyMenu installé sur son client.

Cette commande ne fonctionnera pas pour tous les écrans, en particulier les écrans de mods. Si la commande échoue à ouvrir un écran, un message d’erreur s’affichera. Il n’y a pas grand-chose à faire dans ce cas, car il s’agit probablement d’un écran trop complexe pour être ouvert automatiquement par FancyMenu.

Je n’ajouterai plus non plus de compatibilité manuelle pour les écrans de mods, car ajouter une compatibilité pour tous les mods existants me prendrait une éternité, désolé.

# Fermer des interfaces par commande

Dans le cas rare où vous en auriez besoin, il existe aussi une commande `/closeguiscreen <target_player>` qui ferme l’écran actuel.
