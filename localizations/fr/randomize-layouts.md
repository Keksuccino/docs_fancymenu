---
title: Aléatoiriser les dispositions
description: Comment aléatoiriser des dispositions entières ou seulement certaines parties.
---

# Aléatoirisation

FancyMenu propose de nombreuses fonctionnalités qui vous aident à aléatoiriser des dispositions ou seulement certaines parties de celles-ci.

Cela peut être utile, par exemple, si vous voulez que les utilisateurs voient des arrière-plans différents à chaque fois qu’ils ouvrent un écran, ou des astuces aléatoires sur l’écran de chargement.

# Aléatoiriser des dispositions

FancyMenu dispose d’une fonctionnalité qui vous permet de créer un groupe de dispositions, et le système choisira automatiquement une disposition aléatoire dans ce groupe. Ainsi, vous pouvez afficher un menu entièrement différent et aléatoire à chaque lancement du jeu ou à chaque ouverture d’un écran, mais cela peut aussi servir à ne modifier que certaines parties de l’écran, par exemple l’arrière-plan.

## Mode aléatoire

Pour aléatoiriser des dispositions, vous devez activer le **Mode aléatoire** pour chaque disposition qui doit pouvoir être sélectionnée lors de l’aléatoirisation. Pour cela, faites un **clic droit** sur **l’arrière-plan de l’éditeur** et cherchez l’entrée **Mode aléatoire**.

<br>

<img width="351" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/ef0f22d5-2f48-47cd-b526-d12415d8e099">

## Identifiant du groupe aléatoire

Après avoir activé le mode aléatoire, vous devez définir son **Identifiant du groupe aléatoire**.
Ce numéro doit être **le même** pour toutes les dispositions qui doivent appartenir au **même groupe**.

<br>

<img width="301" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/dde0c94e-9729-4251-9aca-32a55c3dfd02">

<br>

<img width="377" alt="Screenshot_8" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/25e7777c-0503-4e54-b866-e85647241eee">

## Comportement de l’aléatoirisation

Si vous voulez que le système choisisse une disposition aléatoire du groupe **une seule fois par session de jeu**, सक्रियez **Aléatoiriser seulement la première fois**. Cela fera en sorte qu’une disposition soit choisie la première fois que l’écran est ouvert, puis que cette même disposition soit toujours utilisée ensuite. Si cette option est désactivée, une disposition aléatoire sera choisie à chaque ouverture de l’écran.

<br>

<img width="305" alt="Screenshot_9" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/355e49eb-73b0-4646-aeb2-c6f113f6ce3b">

# Exemple de scénario 1 : arrière-plan

Supposons que vous vouliez aléatoiriser l’arrière-plan de l’écran titre.

Pour cela, vous devez créer **une disposition par arrière-plan** et ne modifier _**QUE**_ l’arrière-plan pour ces dispositions, puis activer le mode aléatoire avec l’identifiant de groupe aléatoire correct.

Dans cet exemple, nous utilisons l’identifiant de groupe aléatoire **10**. Cet identifiant doit être défini pour chaque disposition de ce groupe de dispositions aléatoires.

La manière la plus simple de faire cela est de préparer une disposition avec le bon identifiant de groupe aléatoire, puis d’utiliser simplement **Enregistrer sous**. Changez l’arrière-plan à chaque fois que vous enregistrez la disposition sous un nouveau nom ; vous obtiendrez alors plusieurs dispositions avec des arrière-plans différents, et l’une de ces dispositions sera choisie à chaque ouverture de l’écran ou une fois par session de jeu.

# Exemple de scénario 2 : élément

Un autre cas d’utilisation courant consiste à aléatoiriser un élément de texte ou d’image.

Comme pour l’arrière-plan, créez une disposition par version de l’élément que vous souhaitez sélectionner aléatoirement. Ajoutez uniquement l’élément aux dispositions, et rien d’autre. Ne personnalisez rien et n’ajoutez pas d’autres éléments.

Ensuite, enregistrez simplement toutes les dispositions avec le même identifiant de groupe aléatoire, et une disposition du groupe sera choisie à l’ouverture de l’écran ou au lancement du jeu.
