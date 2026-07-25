---
title: Texte d’accueil
description: Comment créer des textes d’accueil personnalisés dans FancyMenu.
---
# Élément de texte d’accueil personnalisé

L’élément de texte d’accueil dans FancyMenu est une version entièrement personnalisable des textes d’accueil rebondissants de Minecraft. Il conserve le mouvement rebondissant familier tout en vous permettant de contrôler ce qui s’affiche, son apparence et quand il se met à jour.

> [!WARNING]
> Gardez à l’esprit que vous ne pouvez pas vraiment personnaliser l’élément de texte d’accueil Vanilla d’origine dans l’écran de titre. Vous devriez donc le **supprimer** et utiliser à la place un élément de texte d’accueil personnalisé.

## Ajouter et sélectionner l’élément
- Ouvrez l’éditeur de mise en page et ajoutez l’élément appelé `Splash Text`.
- Faites un clic gauche dessus une fois pour le sélectionner et afficher la boîte englobante, puis faites un clic droit pour ouvrir son menu contextuel. Toutes les options de configuration se trouvent dans ce menu.

## Choisir la source du texte d’accueil
- `Source Mode: Vanilla` conserve les textes d’accueil aléatoires classiques fournis avec Minecraft.
- `Source Mode: Direct Input` vous permet de saisir votre propre texte via `Input Splash Text`. Cela ne prend en charge qu’une seule ligne de texte d’accueil, mais cette ligne peut contenir des variables.
- `Source Mode: Text File` récupère une ligne aléatoire depuis un fichier `.txt` que vous choisissez avec `Set Source Text File`. Chaque ligne non vide peut devenir le texte d’accueil actif.
- Changer de mode réinitialise le texte actif, vous pouvez donc faire des essais en toute sécurité. Si le texte semble bloqué, basculez vers un autre mode ou cliquez sur `Refresh On Screen Load: Enabled` pour forcer un nouveau tirage à chaque ouverture du menu.

## Exemple de fichier texte
Lors de l’utilisation du mode source "Text File", enregistrez votre liste de textes d’accueil en texte brut (UTF-8 sans BOM). Chaque ligne est un texte d’accueil possible :

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Remplacez `your_placeholder_id_here` par la variable que vous souhaitez résoudre à l’exécution. FancyMenu choisit une ligne non vide aléatoire à chaque actualisation du texte d’accueil.

## Le rendre comme vous le souhaitez
- Utilisez `Set Scale` et `Set Rotation` pour contrôler la taille et l’angle de rotation.
- `Set Text Color` accepte une valeur hexadécimale (par exemple `#FFFF00`) pour correspondre à votre thème.
- `Shadow: Enabled` ajoute l’ombre portée de Minecraft ; désactivez-la pour un texte plat.
- `Bouncing: Enabled` conserve le mouvement de rebond familier ; désactivez-le pour une étiquette statique.
- FancyMenu affiche le texte d’accueil comme un composant Minecraft complet, donc les codes de couleur et autres décorations de texte fonctionnent comme prévu.

## Fonctionnalités de texte dynamique
- Les variables sont résolues avant l’affichage, vous pouvez donc faire référence à des noms de joueurs, des dates ou d’autres valeurs prises en charge directement dans le texte d’accueil.
- Comme l’élément accepte le JSON sérialisé des composants Minecraft, vous pouvez coller des extraits JSON avancés dans `Direct Input` ou dans votre fichier texte. L’élément les désérialise automatiquement et revient au texte littéral si quelque chose ne va pas.

## Dépannage
- Un texte vide dans `Direct Input` affiche `< empty splash element >` pendant l’édition. Entrez n’importe quoi (même un espace) pour faire disparaître l’avertissement.
- Si un fichier texte ne contient aucune ligne valide, l’élément affiche `ERROR: SPLASH FILE IS EMPTY`. Ajoutez au moins une ligne non vide et rouvrez l’écran.
- Les erreurs de JSON sérialisé reviennent au texte brut. Restez sur la structure JSON standard de Mojang ou testez vos extraits avec la commande vanilla `/tellraw` avant de les coller.
