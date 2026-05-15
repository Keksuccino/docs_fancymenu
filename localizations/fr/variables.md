---
title: Variables
description: Comment créer et utiliser des variables.
---

# Variables dans FancyMenu

Les variables sont une fonctionnalité puissante de FancyMenu qui vous permet de stocker et de réutiliser des informations tout au long de vos personnalisations de menu. Elles fonctionnent comme des conteneurs dans lesquels vous pouvez placer différents types de données, donner un nom à chaque conteneur, puis accéder à ces données plus tard en utilisant le nom de la variable. Les variables ouvrent un monde de possibilités pour créer des menus dynamiques qui changent selon les conditions que vous définissez.

## Création de variables

Pour créer une variable dans FancyMenu :

1. Assurez-vous de ne pas être actuellement dans l'éditeur de disposition. 
2. Cliquez sur la barre de menu en haut de l'écran.
3. Allez dans **Personnalisation -> Variables -> Gérer les variables**.
4. Dans l'écran « Gérer les variables » qui apparaît, cliquez sur le bouton **Ajouter une variable**.
5. Saisissez un nom pour votre nouvelle variable, puis cliquez sur **OK**.

C'est tout ! Votre variable est prête à être utilisée. Vous pouvez la voir सूचीnée dans l'écran « Gérer les variables ».

FancyMenu 3.9.0 refond la fenêtre Gérer les variables. Les actions importantes sont disponibles via un menu contextuel au clic droit, la liste prend en charge la navigation au clavier, les variables peuvent être copiées/collées, les modifications peuvent être annulées/rétablies, la saisie lance une recherche, **DEL** supprime la variable sélectionnée et **CTRL + S** valide la fenêtre.

## Définir des valeurs de variable

Une variable vide n'est pas très utile à elle seule. Pour que les variables vous servent, vous devez y mettre des données. Dans FancyMenu, cela s'appelle « définir la valeur de la variable ». 

Il existe deux façons principales de définir la valeur d'une variable :

1. Dans l'écran « Gérer les variables », trouvez la variable dans la liste, cliquez dessus, puis cliquez sur **Définir la valeur**. Saisissez les données que vous souhaitez stocker.

2. Pendant la personnalisation de votre menu, utilisez l'action **Définir une variable** sur un élément Bouton, Curseur ou Défileur. Avec cette action, vous spécifiez le nom de la variable et la valeur à y stocker. Par exemple, lorsque quelqu'un clique sur un bouton doté de cette action, la variable se met à jour avec la nouvelle valeur.

Par exemple, supposons que vous créez une variable nommée `clicks` pour compter le nombre de fois qu'un bouton est pressé. Vous ajouteriez l'action **Définir une variable** au bouton et utiliseriez un placeholder dans la valeur de l'action pour incrémenter le compteur à chaque clic, comme ceci :

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Voici comment cela fonctionne :
1. Le placeholder **Obtenir la variable stockée** récupère la valeur actuelle de la variable `clicks`.
2. Le placeholder **Calculatrice** prend cette valeur et y ajoute 1.
3. Le résultat est ensuite stocké à nouveau dans la variable `clicks` à l'aide de l'action **Définir une variable**.

Ainsi, chaque fois que le bouton est cliqué, la variable `clicks` augmente de 1, ce qui compte efficacement le nombre total de clics.

## Utiliser des variables

Maintenant que vos variables contiennent des données, vous pouvez utiliser ces données dans différentes parties de la personnalisation de votre menu :

* **Conditions de chargement** : vous pouvez vérifier la valeur d'une variable dans une condition de chargement afin de contrôler quand certains éléments du menu apparaissent. Par exemple, vous pourriez faire en sorte qu'un élément s'affiche uniquement si la variable `clicks` est supérieure à 5 en utilisant une combinaison de la condition **Est un nombre** et du placeholder **Obtenir la variable stockée**.

* **Placeholders** : les variables peuvent être insérées dans du texte à l'aide du placeholder **Obtenir la variable stockée**. Si vous avez un élément texte, vous pouvez utiliser `{"placeholder":"getvariable","values":{"name":"clicks"}}` pour afficher la valeur actuelle de la variable « clicks ».

* **Placeholders imbriqués** : vous pouvez même utiliser des variables à l'intérieur d'autres placeholders ! L'exemple de comptage des clics ci-dessus l'a démontré en utilisant le placeholder **Obtenir la variable stockée** à l'intérieur du placeholder **Calculatrice**.

* **Actions** : les variables peuvent être utilisées dans des actions pour créer un comportement dynamique basé sur leurs valeurs. Voici quelques exemples :
    - Utilisez une instruction **IF** dans un script d'action pour vérifier la valeur d'une variable à l'aide d'une combinaison de la condition de chargement **Est un nombre** et de l'action **Obtenir la variable stockée**, puis effectuez différentes actions selon le résultat. Par exemple, vous pourriez avoir un bouton qui affiche « Vous m'avez cliqué X fois ! » et utiliser un bloc IF pour afficher un message spécial si le nombre de clics est supérieur à 10.
    - Combinez le placeholder **Obtenir la variable stockée** avec l'action **Copier dans le presse-papiers** pour permettre aux utilisateurs de copier la valeur d'une variable dans leur presse-papiers.
    - Utilisez des variables dans l'action **Ouvrir l'interface graphique** pour charger différents écrans selon la progression ou les préférences de l'utilisateur, que vous suivez avec des variables.

## Exemples de variables

Voici quelques exemples pour inspirer votre propre utilisation des variables :

1. **Score élevé** : créez une variable `highscore` et un bouton qui la définit sur le score actuel du joueur s'il est supérieur à la valeur existante. Affichez le score élevé dans le menu à l'aide du placeholder **Obtenir la variable stockée**.

2. **Sélecteur de difficulté** : créez des variables pour différentes difficultés de jeu, comme `easy`, `medium` et `hard`. Utilisez des boutons pour définir la variable de difficulté, puis affichez/masquez des éléments selon la difficulté sélectionnée.

3. **Progression du tutoriel** : ajoutez des variables pour suivre la progression du joueur dans un tutoriel, comme `tutorial_step`. Incrémentez la variable à mesure qu'il complète chaque étape, et utilisez des conditions de chargement pour révéler progressivement davantage de menu.

Les variables, combinées aux autres fonctionnalités de FancyMenu, vous offrent une flexibilité incroyable pour créer des menus adaptés aux actions et préférences de chaque joueur. Essayez différentes configurations de variables pour exploiter tout le potentiel de vos personnalisations de menu !
