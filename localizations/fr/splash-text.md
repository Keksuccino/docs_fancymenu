---
title: Texte de splash
description: Comment créer des textes de splash personnalisés dans FancyMenu.
---

# Élément de texte de splash personnalisé

L’élément de texte de splash dans FancyMenu est une version entièrement personnalisable des textes de splash rebondissants de Minecraft. Il conserve l’effet de rebond familier tout en vous donnant le contrôle sur ce qui s’affiche, son apparence et le moment de sa mise à jour.

> Gardez à l’esprit que vous ne pouvez pas vraiment personnaliser l’élément de texte de splash Vanilla d’origine dans l’écran Titre, donc vous devriez le **supprimer** et utiliser à la place un élément de texte de splash personnalisé.
{.is-warning}

## Ajouter et sélectionner l’élément
- Ouvrez l’éditeur de mise en page et ajoutez l’élément appelé `Splash Text`.
- Faites un clic gauche dessus une fois pour le sélectionner et afficher la boîte englobante, puis faites un clic droit pour ouvrir son menu contextuel. Toutes les options de configuration se trouvent dans ce menu.

## Choisir d’où vient le texte de splash
- `Source Mode: Vanilla` conserve les splashes aléatoires classiques fournis avec Minecraft.
- `Source Mode: Direct Input` vous permet de saisir votre propre texte via `Input Splash Text`. Cela ne prend en charge qu’une seule ligne de texte de splash, mais la ligne peut contenir des variables de remplacement.
- `Source Mode: Text File` tire une ligne aléatoire depuis un fichier `.txt` que vous choisissez avec `Set Source Text File`. Chaque ligne non vide peut devenir le splash actif.
- Changer de mode réinitialise le texte actif, afin que vous puissiez expérimenter en toute sécurité. Si le texte semble bloqué, basculez vers un autre mode ou cliquez sur `Refresh On Screen Load: Enabled` pour forcer un nouveau tirage à chaque ouverture du menu.

## Exemple de fichier texte
Lorsque vous utilisez le mode de source "Text File", enregistrez votre liste de splashes comme texte brut (UTF-8 sans BOM). Chaque ligne est un splash possible :

```
Bienvenue dans FancyMenu !
{"placeholder":"your_placeholder_id_here"}
{"text":"Ceci est un texte doré et en gras.","color":"gold","bold":true}
&6Utilisez les codes de formatage &lMinecraft !
```

Remplacez `your_placeholder_id_here` par la variable de remplacement que vous souhaitez résoudre à l’exécution. FancyMenu choisit une ligne non vide aléatoire à chaque actualisation du splash.

## Le rendre comme vous le souhaitez
- Utilisez `Set Scale` et `Set Rotation` pour contrôler la taille et l’angle de rotation.
- `Set Text Color` accepte une valeur hexadécimale (par exemple `#FFFF00`) pour correspondre à votre thème.
- `Shadow: Enabled` ajoute l’ombre portée de Minecraft ; désactivez-la pour un texte plat.
- `Bouncing: Enabled` conserve le mouvement de rebond familier ; désactivez-le pour une étiquette statique.
- FancyMenu affiche le splash comme un composant Minecraft complet, donc les codes de couleur et les autres décorations de texte fonctionnent comme prévu.

## Fonctionnalités de texte dynamique
- Les variables de remplacement sont résolues avant le rendu, vous pouvez donc référencer des noms de joueurs, des dates ou d’autres valeurs prises en charge à l’intérieur du texte de splash.
- Comme l’élément accepte le JSON de composant sérialisé de Minecraft, vous pouvez coller des extraits JSON avancés dans Direct Input ou dans votre fichier texte. L’élément les désérialise automatiquement et revient au texte littéral si quelque chose ne va pas.

## Dépannage
- Un texte vide dans Direct Input affiche `< empty splash element >` pendant l’édition. Entrez n’importe quoi (même un espace) pour supprimer l’avertissement.
- Si un fichier texte ne contient aucune ligne valide, l’élément affiche `ERROR: SPLASH FILE IS EMPTY`. Ajoutez au moins une ligne non vide et rouvrez l’écran.
- Les erreurs de JSON sérialisé reviennent au texte brut. Restez sur la structure JSON standard de Mojang ou testez vos extraits avec la commande vanilla `/tellraw` avant de les coller.
