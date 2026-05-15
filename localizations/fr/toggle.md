---
title: Activer/Désactiver des parties de dispositions
description: >-
  Comment activer ou désactiver des parties de dispositions en fonction des
  saisies de l’utilisateur.
---

# Activer/Désactiver des parties de dispositions

Parfois, c’est bien d’avoir le choix ! Peut-être que certains de vos utilisateurs n’aiment pas entendre Rick Astley en boucle comme musique de menu, ou veulent une autre petite fille anime mignonne comme arrière-plan de menu.

Eh bien, aucun problème ! Vous pouvez faire en sorte que vos utilisateurs puissent activer/désactiver certaines parties de vos dispositions, ou faire défiler plusieurs variantes de ces parties.

# Activer/Désactiver

Pour activer/désactiver, par exemple, la visibilité d’un élément en cliquant sur un bouton, vous avez simplement besoin d’utiliser une variable qui est définie lors du clic sur le bouton, et l’élément que vous voulez activer/désactiver doit vérifier, dans ses critères de chargement, si cette variable a la bonne valeur.

## La variable

La première étape consiste à créer la variable que vous utiliserez pour stocker l’état de visibilité de l’élément que vous voulez activer/désactiver.

Pour ajouter une nouvelle variable, allez dans l’onglet **Personnalisation** de la barre de menus et cliquez sur **Variables -> Gérer les variables**, puis ajoutez une nouvelle variable avec un nom **unique** ! Assurez-vous d’utiliser un nom vraiment **unique** qui n’est pas déjà utilisé.

Après avoir créé la variable, définissez sa valeur sur `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## L’élément

L’étape suivante consiste à ajouter l’élément que vous voulez activer/désactiver.

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

Cliquez ensuite avec le bouton droit sur l’élément et cliquez sur **Critères de chargement**.
Cela ouvrira l’écran de gestion des critères. Cliquez sur **Ajouter un critère**.

Recherchez le critère **Is Variable Value**, sélectionnez-le puis cliquez sur **Modifier la valeur du critère**.

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

Saisissez maintenant le nom de la variable que vous avez créée plus tôt et faites en sorte que le critère vérifie `true` comme valeur.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

C’est tout pour cette partie. Votre élément sera maintenant visible lorsque la valeur de la variable est `true`.

## Le bouton

Nous devons maintenant ajouter un nouvel élément Button.

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

Après l’avoir ajouté, cliquez dessus avec le bouton droit puis sur **Modifier le script d’action**.
Cela ouvrira l’écran de gestion du script d’action du bouton.

Cliquez sur **Ajouter une instruction IF**, ajoutez-y le critère **Is Variable Value** et réglez le mode du critère sur **OPPOSITE**.

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

Cliquez maintenant sur **Modifier la valeur du critère**, comme vous l’avez fait précédemment avec l’élément, et saisissez exactement le même nom de variable ainsi que la même valeur à vérifier.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Comme nous avons défini le mode du critère sur **OPPOSITE**, il vérifiera maintenant si la valeur de la variable n’est PAS `true`, ce qui est exactement ce que nous voulons.

De retour dans l’écran Modifier le script d’action, vous verrez maintenant l’instruction IF que nous venons d’ajouter.

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

Cliquez maintenant sur **Ajouter une action**, recherchez l’action **Set Variable Value**, sélectionnez-la puis cliquez sur **Modifier la valeur de l’action**.

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

Comme valeur de l’action, saisissez d’abord le nom de votre variable, puis la valeur à lui attribuer après. Séparez le nom et la valeur par `:`.
Dans ce cas, nous voulons définir notre valeur sur `true`, car cette action sera exécutée plus tard lorsque la valeur n’est PAS `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

Ajoutez maintenant l’action à l’instruction IF en la faisant glisser et en la déposant au-dessus de l’instruction IF, afin qu’elle ne soit exécutée que lorsque la valeur de notre variable n’est PAS `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

Après cela, sélectionnez l’instruction IF puis cliquez sur **Ajouter une instruction ELSE**.

Ajoutez maintenant une autre action **Set Variable Value**, mais au lieu de définir la valeur de la variable sur `true`, définissez-la sur `false`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

Ajoutez maintenant la deuxième action à l’instruction ELSE, afin qu’elle soit exécutée si la valeur de la variable EST `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

Et voilà ! Cela peut sembler beaucoup d’étapes la première fois, mais c’est en réalité une opération assez simple et rapide une fois qu’on y est habitué.

Vous pouvez maintenant enregistrer votre disposition, quitter l’éditeur et appuyer sur le bouton pour voir si cela fonctionne !

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

N’hésitez pas à utiliser la même variable pour d’autres éléments, afin de **basculer plusieurs éléments à la fois** en appuyant sur le bouton.

Vous pouvez même activer/désactiver des dispositions entières en utilisant les **critères de chargement à l’échelle de la disposition**. Pour configurer des critères à l’échelle de la disposition, cliquez avec le bouton droit sur l’arrière-plan de l’éditeur. Veillez simplement à ajouter le bouton à une autre disposition, et non à celle que vous souhaitez basculer.

# Faire défiler les valeurs

Contrairement au basculement entre deux valeurs, le fait de faire défiler des valeurs nécessite que le script d’action puisse alterner entre plus de deux valeurs.

La logique du script d’action est très similaire à celle utilisée pour le basculement, donc je resterai très bref ici. Assurez-vous également de lire la partie sur le basculement.

J’ai ajouté 3 images. La première image est visible lorsque la valeur de la variable est `1`, la deuxième si la valeur est `2` et la troisième si la valeur est `3`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

Ensuite, j’ai ajouté le bouton de cycle et je l’ai fait faire défiler la valeur de la variable de `1` à `2` à `3` puis à `1`.

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

Et voilà. Enregistrez maintenant la disposition, quittez l’éditeur et vérifiez si le bouton de cycle fonctionne correctement.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
