---
title: Visibilité des éléments
description: >-
  Comment afficher et masquer des éléments selon des conditions, avec un délai,
  un fondu ou une opacité, et comment les basculer à l’aide d’un bouton.
sourceBlobSha: 819fbc2639734fc8658f6fb65e9df6b1234e9cc5
---

# Visibilité des éléments

Les éléments ne sont pas obligés d’être affichés en permanence. Ils peuvent apparaître uniquement dans certaines situations, un peu plus tard, en fondu, ou être activés et désactivés à l’aide d’un bouton.

<img width="800" alt="Un texte de bienvenue apparaît en fondu quelques secondes après l’ouverture de l’écran, puis un bouton Règles du serveur fait apparaître et disparaître un panneau de règles en fondu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_visibility_toggle.gif?raw=true">

Dans l’éditeur de mise en page, les éléments sont toujours affichés pour que vous puissiez les modifier. Tout ce qui est décrit sur cette page fonctionne en dehors de l’éditeur.

> [!TIP]
> Toutes les conditions sont répertoriées dans [Conditions](/conditions).

# Afficher des éléments uniquement dans certaines situations

Faites un clic droit sur un élément, puis cliquez sur **Conditions de chargement**. L’élément s’affiche uniquement lorsque toutes ses [conditions](/conditions) sont remplies, par exemple « la souris survole ce bouton », « nous sommes en décembre » ou « une variable a cette valeur ». FancyMenu les vérifie en permanence ; l’élément apparaît ou disparaît donc immédiatement.

- **Mode de condition** Opposé inverse une condition, par exemple « PAS en décembre ».
- Les groupes permettent de définir des conditions de type « ceci OU cela ».
- Les éléments vanilla disposent eux aussi de **Conditions de chargement**. Pour en supprimer un complètement, consultez [Éléments vanilla supprimés](/deleted-vanilla-elements).

Pour savoir comment ajouter et combiner des conditions, consultez [Conditions](/conditions#adding-a-requirement).

## Charger une seule fois par session

Faites un clic droit sur un élément et activez **Charger une seule fois par session**. L’élément s’affiche à la première ouverture de son écran. Dès que le joueur passe à un autre écran, il reste masqué jusqu’au redémarrage du jeu.

Cette option est pratique pour les conseils à afficher une seule fois par démarrage du jeu, comme « Appuyez sur F1 pour voir les commandes ». Pour obtenir le même résultat dans des scripts d’action, utilisez la condition [**Une seule fois par session**](/conditions#only-once-per-session).

# Retarder l’affichage des éléments

## Retarder l’apparition

Faites un clic droit sur un élément, puis cliquez sur **Retarder l’apparition** :

- **Délai** :
  - **Aucun délai** : l’élément s’affiche immédiatement.
  - **La première fois** : le délai ne s’applique qu’à la première apparition de l’élément après le démarrage du jeu.
  - **À chaque fois** : le délai s’applique à chaque ouverture de l’écran et chaque fois que ses conditions sont à nouveau remplies.
- **Délai en secondes** : durée d’attente, par exemple `1.5`.

Le redimensionnement de la fenêtre ne relance pas le délai.

## Retarder la disparition

Faites un clic droit sur un élément, puis cliquez sur **Retarder la disparition**. Lorsque ses conditions ne sont plus remplies, l’élément reste affiché pendant la durée définie dans **Délai en secondes**, puis disparaît. Les options de **Délai** sont les mêmes que ci-dessus.

Par exemple, une boîte d’information dont la condition est [**L’élément est survolé**](/conditions#is-element-hovered) pour un bouton reste affichée pendant 1 seconde après que la souris a quitté le bouton.

# Apparition et disparition en fondu

Faites un clic droit sur un élément, puis cliquez sur **Apparition/disparition en fondu** :

- **Fondu d’apparition** et **Fondu de disparition** :
  - **Aucun fondu** : l’élément apparaît ou disparaît immédiatement.
  - **Une seule fois** : le fondu se produit uniquement la première fois après le démarrage du jeu.
  - **À chaque fois** : le fondu se produit à chaque fois.
- **Vitesse du fondu d’apparition** et **Vitesse du fondu de disparition** : à `1`, un fondu dure 2,5 secondes. `2` est deux fois plus rapide.

Les éléments apparaissent en fondu à l’ouverture de l’écran et lorsque leurs conditions sont remplies. Si **Retarder l’apparition** est activé, le fondu commence après le délai.

Le fondu de disparition se produit uniquement lorsque les conditions masquent l’élément, et non à la fermeture de l’écran.

# Opacité

Faites un clic droit sur un élément, puis cliquez sur **Opacité** : `1.0` signifie que l’élément est entièrement visible, `0.5` qu’il est à moitié transparent et `0.0` qu’il est invisible. La plupart des éléments disposent de cette option.

L’opacité prend en charge les [espaces réservés](/placeholders) et les [variables](/variables), par exemple `$$panel_opacity`. Les fondus d’apparition s’arrêtent à l’opacité définie pour l’élément.

# Basculer l’affichage des éléments à l’aide d’un bouton

Un bouton peut afficher et masquer des éléments, comme le panneau de règles dans le GIF ci-dessus. Une [variable](/variables) mémorise si le panneau est affiché.

1. Faites un clic droit sur le panneau, puis cliquez sur **Conditions de chargement**. Ajoutez [**La valeur de la variable (variable FM) est**](/conditions#is-variable-value-fm-variable) avec la variable `show_rules` et la valeur `true`.
2. Faites un clic droit sur le bouton, puis cliquez sur **Modifier le script d’action**.
3. Faites un clic droit dans la zone du script, puis cliquez sur **Ajouter une instruction IF**. Donnez-lui la même condition que celle du panneau.
4. Dans l’instruction IF, ajoutez [**Définir la valeur de la variable (variable FM)**](/action-scripts#set-variable-value-fm-variable) avec cette valeur :

   ```
   show_rules:false
   ```

5. Faites un clic droit sur l’instruction IF, puis cliquez sur **Ajouter une instruction ELSE**. Dans l’instruction ELSE, ajoutez **Définir la valeur de la variable (variable FM)** avec cette valeur :

   ```
   show_rules:true
   ```

Ainsi, chaque clic inverse la valeur de la variable : les panneaux affichés sont masqués et les panneaux masqués sont affichés. Tous les éléments ayant la même condition apparaissent et disparaissent ensemble. Pour un rendu fluide, réglez **Fondu d’apparition** et **Fondu de disparition** du panneau sur **À chaque fois**.

Pour en savoir plus sur IF et ELSE, consultez [Scripts d’action](/action-scripts#if-else-if-and-else).

> [!NOTE]
> Les variables sont conservées après la fermeture du jeu ; le panneau sera donc toujours ouvert au prochain démarrage. Pour le fermer à chaque démarrage, faites un clic droit sur la variable dans **Gérer les variables**, puis activez **Effacer la variable au lancement du jeu**.

## Passer d’une version à l’autre

Un bouton peut aussi faire défiler plus de deux versions, par exemple trois arrière-plans :

1. Dans **barre de menus -> Personnalisation -> Gérer les variables**, ajoutez la variable texte `background` avec la valeur `0`.
2. Ajoutez aux trois [éléments Image](/elements#image) la condition **La valeur de la variable (variable FM) est** pour `background`, avec les valeurs `0`, `1` et `2`.
3. Attribuez au bouton l’action **Définir la valeur de la variable (variable FM)** avec cette valeur. Elle fait défiler `0`, `1`, `2`, puis revient à `0` :

   ```
   background:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"getvariable","values":{"name":"background"}} + 1) % 3"}}
   ```

Pour ajouter des versions, modifiez le `3` à la fin. Consultez [**Calculatrice**](/placeholders#calculator) pour en savoir plus sur les calculs.

# Activer et désactiver des mises en page

Pour afficher ou masquer une mise en page entière :

- **Conditions de chargement [pour toute la mise en page]** dans le menu du clic droit sur l’arrière-plan de l’éditeur fonctionne comme les conditions des éléments. Consultez [Conditions pour toute la mise en page](/conditions#layout-wide-requirements).
- Les actions [**Basculer la mise en page**](/action-scripts#toggle-layout), [**Activer la mise en page**](/action-scripts#enable-layout) et [**Désactiver la mise en page**](/action-scripts#disable-layout) activent ou désactivent une mise en page par son nom.

Placez le bouton dans une autre mise en page que celle qu’il désactive. Sinon, le bouton disparaîtra avec elle et il sera impossible de réactiver la mise en page.
