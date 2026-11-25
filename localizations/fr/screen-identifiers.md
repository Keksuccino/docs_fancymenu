---
title: Identifiants d’écran
description: >-
  À propos des identifiants d’écran et de la façon de trouver l’identifiant d’un
  écran.
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# Identifiants d’écran

FancyMenu utilise des identifiants d’écran pour les dispositions, les widgets Vanilla, les [actions d’écran](/action-scripts#open-screen-or-custom-gui) et les [remplacements d’interfaces graphiques personnalisées](/custom-guis#overriding-an-existing-screen). Les identifiants sont sensibles à la casse : copiez-les exactement depuis la superposition de débogage.

Les écrans intégrés utilisent généralement un identifiant universel court, comme `title_screen`. D’autres écrans de mods peuvent utiliser le nom de leur classe Java. Les interfaces graphiques personnalisées utilisent l’identifiant saisi dans leur gestionnaire. Il s’agit d’identifiants d’écran FancyMenu, et non d’emplacements de ressources Minecraft.

# Trouver l’identifiant d’un écran

La **superposition de débogage** permet de voir l’identifiant du menu actuellement actif.
Elle affiche l’identifiant de l’écran actuel et permet de le copier dans le presse-papiers en cliquant dessus avec le bouton gauche de la souris.

>[!TIP]
>Vous pouvez activer la **superposition de débogage** en appuyant sur **CTRL + ALT + D** lorsque vous n’êtes **pas** dans l’éditeur de dispositions.

<br>

<img width="553" alt="Capture d’écran_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Capture d’écran_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Ouvrir des écrans

L’[action **Ouvrir un écran ou une interface graphique personnalisée**](/action-scripts#open-screen-or-custom-gui) ne peut ouvrir que les écrans que FancyMenu est en mesure de créer dans l’état actuel du jeu. Certains écrans nécessitent qu’un monde soit chargé, une connexion active, un joueur ou un écran parent d’origine.

Si FancyMenu ne parvient pas à créer l’écran à partir de l’identifiant, un message d’erreur s’affiche. Utilisez l’action [**Imiter le bouton Vanilla/mod**](/action-scripts#mimic-vanillamod-button) sur le widget qui ouvre normalement cet écran.
