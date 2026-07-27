---
title: Identifiants d’écran
description: >-
  À propos des identifiants d’écran et de la manière de trouver l’identifiant
  d’un écran.
---
# Identifiants d’écran

FancyMenu utilise des identifiants d’écran pour les dispositions, les widgets Vanilla, les [actions d’écran](./action-scripts#open-screen-or-custom-gui-opengui) et les [remplacements de GUI personnalisés](./custom-guis#overriding-an-existing-screen). Les identifiants sont sensibles à la casse, donc copiez-les exactement depuis la superposition de débogage.

Les écrans intégrés utilisent normalement un identifiant universel court, comme `title_screen`. D’autres écrans de mods peuvent utiliser le nom de leur classe Java. Les GUI personnalisées utilisent l’identifiant saisi dans leur gestionnaire. Il s’agit d’identifiants d’écran FancyMenu, et non de localisations de ressources Minecraft.

# Trouver l’identifiant d’un écran

Vous pouvez voir l’identifiant du menu actuellement actif à l’aide de la **superposition de débogage**.
Elle contient l’identifiant de l’écran actuel et vous permet de le copier dans le presse-papiers en cliquant dessus avec le bouton gauche.

>[!TIP]
>Vous pouvez activer la **superposition de débogage** en appuyant sur **CTRL + ALT + D** lorsque vous **n’êtes pas** dans l’éditeur de disposition.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Ouvrir des écrans

L’[**action Ouvrir un écran ou un GUI personnalisé**](./action-scripts#open-screen-or-custom-gui-opengui) peut ouvrir uniquement les écrans que FancyMenu peut construire dans l’état actuel du jeu. Certains écrans nécessitent un monde chargé, une connexion, un joueur ou l’écran parent d’origine.

Si FancyMenu ne peut pas construire l’identifiant, un message d’erreur s’affiche. Utilisez [**Imiter le bouton Vanilla/Mod**](./action-scripts#mimic-vanillamod-button-mimicbutton) sur le widget qui ouvre normalement l’écran.
