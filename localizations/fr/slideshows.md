---
title: Diaporamas
description: Comment créer et utiliser des diaporamas.
---

# Diaporamas

FancyMenu vous permet d’ajouter des diaporamas et de les afficher dans des menus ainsi qu’en arrière-plan de menu.

> **IMPORTANT** : Si vous êtes sous Windows, n’oubliez pas d’activer les [extensions de fichier](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10), sinon vous ne pourrez pas voir certaines parties importantes des noms de fichiers plus tard !
{.is-warning}

# Créer un diaporama

Chaque diaporama doit se trouver dans son propre dossier **à l’intérieur** du répertoire des diaporamas situé dans `/config/fancymenu/slideshows/`.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

Pour qu’un diaporama soit reconnu comme tel par le système, il doit contenir un fichier de propriétés dans son dossier de diaporama. Donc, si vous avez nommé votre dossier de diaporama `myslideshow`, le fichier de propriétés doit se trouver dans `/config/fancymenu/slideshows/myslideshow/properties.txt`.

**Ce fichier doit toujours s’appeler `properties.txt` !**
Pour l’instant, créez uniquement le fichier de propriétés **vide** et passez à l’étape suivante.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## Ajouter des images

Un diaporama a besoin d’images, évidemment, alors ajoutons-en !

> Les images de votre diaporama doivent être des fichiers **PNG** ! Pas de JPEG, GIF, APNG ni FMA !
{.is-danger}

Toutes les images de votre diaporama vont dans un dossier supplémentaire **à l’intérieur** de votre dossier de diaporama (`myslideshow` dans l’exemple ci-dessus).
Ce dossier doit s’appeler `images`.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Placez maintenant toutes les images de votre diaporama dans le dossier `images`.
Elles sont triées par ordre alphabétique (en tenant compte des nombres), donc nommez-les par exemple `image_1.png`, `image_2.png`, etc.
Dans mon exemple, `image_1.png` s’affichera en premier et `image_2.png` ensuite.

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## Ajouter du contenu au fichier de propriétés

Au début, vous avez créé un fichier `properties.txt` vide dans votre dossier de diaporama.
Il faut maintenant y ajouter quelques éléments importants.

Chaque fichier de propriétés de diaporama devrait ressembler à ceci :

```
type = slideshow

slideshow-meta {
   name = cool_slideshow
   width = 1920
   height = 1080
   x = 0
   y = 0
   duration = 5.0
   fadespeed = 12.0
   randomize = false
}
```
Seules les variables à l’intérieur de la section `slideshow-meta` peuvent être modifiées !

### name

C’est le nom, ou plus exactement l’identifiant, de votre diaporama.
Les noms de diaporama doivent être **uniques**, donc il n’est pas possible d’avoir deux diaporamas avec le même nom !

### width | height

La `width` et la `height` de base de votre diaporama.
Utilisées par FancyMenu pour calculer le ratio d’aspect.

### x | y

La position `x` et `y` de votre diaporama.
Plutôt à des fins de débogage, donc réglez simplement les deux sur `0`.

### duration

La durée en **secondes** pendant laquelle chaque image est affichée avant de passer à la suivante.
Prend en charge les valeurs décimales !

### fadespeed

La vitesse de l’animation de fondu lors du passage à l’image suivante.
Cette valeur est un multiplicateur de vitesse. Par exemple, `1.0` est la vitesse par défaut, `2.0` double la vitesse et `0.5` la rend deux fois plus lente que la valeur par défaut.
Les valeurs négatives ne sont pas prises en charge.

### randomize

Indique si les images du diaporama doivent être lues dans un ordre aléatoire (`true`) ou non (`false`).

# Utiliser le diaporama

Toutes les étapes importantes sont terminées et votre diaporama devrait maintenant être prêt, alors testons-le !

Pour charger votre diaporama nouveau (ou modifié) dans FancyMenu, rechargez le mod via **Personnalisation -> Recharger FancyMenu**.

Vous pouvez maintenant utiliser votre diaporama dans l’élément **Diaporama** ou comme arrière-plan de menu (clic droit sur l’arrière-plan de l’éditeur de mise en page -> **Arrière-plan du menu**).
