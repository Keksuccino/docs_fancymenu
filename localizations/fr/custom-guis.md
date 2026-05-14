---
title: Interfaces graphiques personnalisées
description: Comment ajouter un nouvel écran d’interface graphique au jeu.
---

# Interfaces graphiques personnalisées

FancyMenu vous permet de personnaliser les écrans d’interface graphique existants, mais aussi d’en ajouter de complètement nouveaux et de les remplir d’éléments.

# Ajouter un nouvel écran

Pour ajouter un nouvel écran, allez dans **Personnalisation -> Interfaces graphiques personnalisées -> Gérer les interfaces graphiques personnalisées**.

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

Dans le menu suivant, cliquez sur **Nouvelle interface graphique**.

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

Ici, vous devez donner à votre nouvelle interface graphique un identifiant unique, et vous pouvez personnaliser d’autres aspects du comportement de base de l’écran.
Quand vous avez terminé, appuyez sur **Terminé**.

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

Vous avez maintenant une nouvelle interface graphique vide. Pour l’ouvrir, sélectionnez l’interface dans le menu **Gérer les interfaces graphiques personnalisées** et cliquez sur **Ouvrir l’interface**.

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

Cela ouvrira l’écran d’interface graphique encore assez vide. Pour le rendre moins vide, créez simplement une nouvelle mise en page comme vous le feriez pour n’importe quel autre écran.

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# Ouvrir l’interface via une action

La dernière étape consiste à donner aux utilisateurs normaux accès à votre interface. Le moyen le plus simple est d’utiliser l’action **Ouvrir un écran ou une interface graphique personnalisée** avec un bouton, un curseur ou un ticker.

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# Ouvrir l’interface via une commande

Vous pouvez également ouvrir votre interface graphique personnalisée via une [commande en jeu](./commands#openguiscreen).
Cela vous permet même d’ouvrir l’interface à distance pour d’autres utilisateurs !

# Mode popup

À partir de FancyMenu v3.8.0, les interfaces graphiques personnalisées prennent en charge un « mode popup » qui leur donne l’apparence d’une fenêtre contextuelle s’ouvrant au-dessus d’un autre écran (l’écran précédent depuis lequel l’interface graphique personnalisée a été ouverte). Ce réglage peut être activé ou désactivé individuellement pour chaque interface graphique personnalisée dans ses paramètres.

FancyMenu 3.9.0 ajoute également une option permettant d’activer ou de désactiver la superposition d’arrière-plan de l’écran pour les interfaces graphiques personnalisées en jeu. Utilisez-la si vous souhaitez désactiver ou conserver le flou / l’assombrissement derrière une interface graphique personnalisée ouverte pendant le jeu.
