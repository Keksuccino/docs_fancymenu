---
title: Variables
description: Comment créer et utiliser des variables.
---
# Variables dans FancyMenu

Les variables stockent des valeurs textuelles que les mises en page, actions, espaces réservés, conditions, écouteurs, planificateurs et interfaces graphiques personnalisées peuvent réutiliser.

## Créer des variables

Pour créer une variable dans FancyMenu :

1. Assurez-vous de ne pas être actuellement dans l'Éditeur de mise en page.
2. Cliquez sur la barre de menu en haut de l'écran.
3. Allez dans **Personnalisation -> Variables -> Gérer les variables**.
4. Dans l'écran "Gérer les variables" qui apparaît, cliquez sur le bouton **Ajouter une variable**.
5. Saisissez un nom pour votre nouvelle variable et cliquez sur **OK**.

C'est tout ! Votre variable est prête à être utilisée. Vous pouvez la voir répertoriée dans l'écran "Gérer les variables".

La fenêtre Gérer les variables prend en charge un menu contextuel au clic droit, la navigation au clavier, copier/coller, annuler/rétablir, la recherche à la saisie, **Suppr** pour supprimer, et **Ctrl/Commande + S** pour enregistrer.

## Définir les valeurs des variables

Une variable vide n'est pas très utile en soi. Pour exploiter les variables, vous devez y placer des données. Dans FancyMenu, cela s'appelle "définir la valeur de la variable".

Il existe deux façons principales de définir la valeur d'une variable :

1. Dans l'écran "Gérer les variables", trouvez la variable dans la liste, cliquez dessus, puis cliquez sur **Définir la valeur**. Saisissez les données que vous souhaitez stocker.

2. Pendant la personnalisation de votre menu, utilisez l'[**action Définir la valeur de la variable**](./action-scripts#set-variable-value-fm-variable-set_variable) sur un élément [Bouton](./elements#button), [Curseur](./elements#slider) ou [Ticker](./elements#ticker).

Par exemple, créez une variable nommée `clicks` et ajoutez l'[**action Définir la valeur de la variable**](./action-scripts#set-variable-value-fm-variable-set_variable) à un bouton :

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Voici comment cela fonctionne :
1. L'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable) récupère la valeur actuelle de la variable `clicks`.
2. L'[**espace réservé Calculatrice**](./placeholders#calculator-calc) prend cette valeur et lui ajoute 1.
3. Le résultat est réenregistré dans `clicks` à l'aide de l'[**action Définir la valeur de la variable**](./action-scripts#set-variable-value-fm-variable-set_variable).

Ainsi, chaque fois que le bouton est cliqué, la variable `clicks` augmente de 1, comptant ainsi le nombre total de clics.

## Utiliser les variables

Maintenant que vos variables contiennent des données, vous pouvez utiliser ces données dans différentes parties de la personnalisation de votre menu :

* [**Conditions de chargement**](./conditions) : vérifiez la valeur d'une variable pour contrôler quand des éléments apparaissent. Par exemple, affichez un élément lorsque `clicks` est supérieur à 5 en combinant [**Est un nombre**](./conditions#is-number-fancymenu_visibility_requirement_is_number) avec l'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable).

* **Espaces réservés** : insérez une variable dans du texte avec l'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable), par exemple `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Espaces réservés imbriqués** : vous pouvez utiliser l'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable) à l'intérieur de l'[**espace réservé Calculatrice**](./placeholders#calculator-calc).

* **Actions** : les variables peuvent créer un comportement dynamique :
  - Utilisez une instruction **IF** dans un [script d'action](./action-scripts#what-are-statements) avec [**Est un nombre**](./conditions#is-number-fancymenu_visibility_requirement_is_number) et l'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Combinez l'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable) avec [**Copier le texte dans le presse-papiers**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Utilisez des variables dans [**Ouvrir un écran ou une interface graphique personnalisée**](./action-scripts#open-screen-or-custom-gui-opengui) pour sélectionner un écran à partir de la progression ou des préférences enregistrées.

## Exemples de variables

Voici quelques exemples pour vous inspirer dans l'utilisation des variables :

1. **Score maximal** : créez une variable `highscore` et un bouton qui la définit sur le score actuel du joueur s'il est supérieur à la valeur existante. Affichez-la avec l'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Sélecteur de difficulté** : créez des variables pour différentes difficultés de jeu, comme `easy`, `medium` et `hard`. Utilisez des boutons pour définir la variable de difficulté et afficher/masquer des éléments selon la difficulté sélectionnée.

3. **Progression du tutoriel** : ajoutez des variables pour suivre la progression du joueur dans un tutoriel, comme `tutorial_step`. Incrémentez la variable à chaque étape terminée, puis utilisez les conditions de chargement pour révéler progressivement davantage de l'interface.

## Persistance, portée et stockage

Les variables sont partagées à travers l'instance Minecraft actuelle. Elles ne sont pas séparées par mise en page, monde, serveur ou joueur.

Les valeurs sont enregistrées immédiatement dans `<game-directory>/config/fancymenu/user_variables.db` et persistent après les redémarrages.

- **Réinitialiser au lancement** vide cette variable au prochain démarrage du jeu.
- [**Effacer toutes les variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) supprime toutes les valeurs de variables stockées.
- Les noms sont sensibles à la casse. Utilisez des noms simples et uniques comme `tutorial_step`.

L'[**espace réservé Obtenir la variable stockée**](./placeholders#get-variable-value-fm-variable-getvariable) renvoie `0` lorsque la variable nommée n'existe pas ou lorsque sa valeur stockée est vide. Cette valeur de secours est importante dans les comparaisons et les expressions de calculatrice.

L'[**action Définir la valeur de la variable**](./action-scripts#set-variable-value-fm-variable-set_variable) utilise `nom_de_variable:valeur_de_variable` et se découpe au premier deux-points, donc la valeur peut contenir plusieurs deux-points.

Ne stockez pas de mots de passe, jetons ou autres secrets dans les variables FancyMenu. Ce sont des données de configuration lisibles.
