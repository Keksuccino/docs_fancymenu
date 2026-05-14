---
title: Animations (FMA/AFMA)
description: Comment créer et utiliser les fichiers d’animation FancyMenu.
---

# Animations

Les fichiers AFMA/FMA sont des fichiers de texture animée spéciaux créés pour FancyMenu.
Ils sont à peu près identiques aux APNG, mais beaucoup plus optimisés pour FancyMenu.

# Fichiers AFMA

FancyMenu 3.9.0 ajoute **AFMA** (Advanced FancyMenu Animation), le successeur des fichiers FMA classiques.

Les fichiers AFMA ne sont plus des fichiers ZIP. Ils utilisent le nouveau format d’animation de FancyMenu, avec des fichiers plus légers, moins d’utilisation mémoire et de meilleures performances.

Pour les nouvelles textures animées volumineuses ou complexes, utilisez **AFMA** plutôt que le FMA classique.

Pour créer un fichier AFMA, procédez comme suit :

1. Ouvrez la barre de menu de FancyMenu.
2. Allez dans **Tools -> AFMA Creator**.
3. Importez/convertissez vos images avec l’outil de création.

> [!IMPORTANT]
> Les fichiers AFMA ne peuvent pas être assemblés manuellement comme les fichiers FMA classiques. Vous devez utiliser le **AFMA Creator** pour les créer/packager.

Les fichiers FMA classiques sont toujours pris en charge et ont été optimisés dans FancyMenu 3.9.0, donc les dispositions existantes n’ont pas besoin d’être converties immédiatement.

# Fichiers FMA classiques

## Créer un FMA

Créer un fichier FMA est aussi simple que créer un fichier ZIP ! Enfin, c’est surtout parce qu’en interne, _c’est_ un fichier ZIP.

### Extensions de fichiers

Vous devez voir les extensions de fichiers pour pouvoir suivre cette documentation, alors assurez-vous d’**ACTIVER LES EXTENSIONS DE FICHIERS** avant de commencer.

Sous Windows, ouvrez un dossier quelconque, puis cliquez sur la flèche en haut à droite pour déployer le menu en dessous.

Ensuite, allez dans l’onglet **Affichage** et activez **Extensions de noms de fichiers**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Préparation

Commençons par créer un nouveau dossier pour le contenu du fichier FMA.
Dans cet exemple, appelons ce dossier `fancymenu_animation`.

Dans ce dossier, créez deux autres dossiers. Le premier dossier **doit** s’appeler `frames` et le second dossier **doit** s’appeler `intro_frames`.

Ensuite, dans le même dossier, créez un nouveau fichier TXT et renommez-le en `metadata.json`.
Veuillez vous assurer que le fichier n’est pas encore un fichier TXT. Vous **devez** changer l’extension du fichier en `json`.

Vous devriez maintenant avoir un dossier nommé `fancymenu_animation` contenant un dossier `frames`, un dossier `intro_frames` et un fichier JSON nommé `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### Le fichier JSON de métadonnées

C’est le fichier qui indique à FancyMenu comment gérer votre texture FMA.
Il contient des informations comme la durée des images (combien de temps une image reste visible) et le nombre de boucles.

Ouvrez le fichier `metadata.json` avec un éditeur de texte.

Copiez ce texte dans le fichier :

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

Voici le modèle de base de l’apparence du fichier.
Vous pouvez maintenant le personnaliser selon vos besoins.

#### `loop_count`

Cela permet de contrôler combien de fois la texture doit boucler (redémarrer son animation).

Le fait de mettre `0` signifie qu’elle bouclera indéfiniment. Elle ne s’arrêtera *jamais*.

Toute valeur supérieure à `0` correspond au nombre de fois que la texture sera lue. Par exemple, mettre la valeur à `1` signifie que la texture ne sera lue qu’une seule fois, puis s’arrêtera sur la dernière image, `2` signifie qu’elle sera lue deux fois, puis s’arrêtera sur la dernière image, *et ainsi de suite*.

#### `frame_time`

Il s’agit du temps d’image universel, en **millisecondes**, pour les images de la texture animée.
Le temps d’image correspond à la durée pendant laquelle une image reste visible avant que l’animation passe à l’image suivante.

#### `frame_time_intro`

C’est essentiellement la même chose que `frame_time`, mais pour les images d’**intro** de votre texture animée.
Les images d’intro sont **facultatives** et vous en apprendrez plus à leur sujet plus tard.

#### `custom_frame_times`

Cette section est **facultative** et peut être utilisée pour remplacer le temps d’image de certaines images spécifiques (hors intro).
Par exemple, vous voulez que toutes vos images s’affichent pendant `41` millisecondes, donc vous définissez `frame_time` sur `41`, mais vous voulez que la première et la deuxième image s’affichent pendant `5000` millisecondes.

Dans ce cas, vous feriez ceci :

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    0: 5000,
    1: 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Les images commencent à `0`, ce qui signifie que la première image de l’animation est `0`, la deuxième est `1`, et ainsi de suite.

Il doit y avoir une **virgule** à la fin de chaque entrée de temps d’image personnalisé, **sauf** à la dernière !

#### `custom_frame_times_intro`

C’est exactement la même chose que `custom_frame_times`, mais dans ce cas pour les images d’**intro**. Les images d’intro sont **facultatives** et vous en apprendrez plus à leur sujet plus tard.

Voilà pour le fichier `metadata.json`. Enregistrez-le maintenant et fermez l’éditeur de texte.

### Les images

> Il est recommandé d’utiliser **200 images maximum** à une **résolution maximale de 1080p** par animation, car les animations consomment beaucoup de mémoire et ne sont pas des vidéos. Elles sont destinées à de courtes boucles animées, pas à lire des vidéos complètes en 24 FPS.
{.is-danger}

Les images de votre texture animée vont dans le dossier `frames`.

Les images doivent être des **FICHIERS PNG** ! Il n’y a **AUCUN SUPPORT POUR LE JPEG ET LES AUTRES FORMATS** !

Chaque image **doit** être nommée uniquement avec le numéro de l’image et l’extension du fichier.
La première image doit s’appeler `0.png`, la deuxième `1.png`, la troisième `2.png`, et ainsi de suite.
La texture ne fonctionnera **PAS** si les fichiers des images ont des noms invalides !

Pour **extraire des images depuis des vidéos**, consultez [cette page de documentation](/ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### L’intro

Cette fonctionnalité est **FACULTATIVE**.

La fonctionnalité **intro** des fichiers FMA est une manière spéciale de lire certaines images **avant** que les images normales du dossier `frames` ne commencent à jouer.

L’intro ne bouclera **jamais** et ne joue qu’à la toute première lecture de l’animation, ce qui vous permet par exemple d’afficher une animation de fondu d’entrée avant que l’animation principale ne commence à boucler.

Les images d’intro vont dans le dossier `intro_frames` et fonctionnent comme les images normales :

Les images doivent être des **FICHIERS PNG** ! Il n’y a **AUCUN SUPPORT POUR LE JPEG ET LES AUTRES FORMATS** !

Chaque image **doit** être nommée uniquement avec le numéro de l’image et l’extension du fichier.
La première image doit s’appeler `0.png`, la deuxième `1.png`, la troisième `2.png`, et ainsi de suite.
La texture ne fonctionnera **PAS** si les fichiers des images ont des noms invalides !

### Packaging du fichier FMA

À présent, tout ce qui est important se trouve dans le dossier `fancymenu_animation`, vous pouvez donc maintenant empaqueter votre fichier FMA !

Empaqueter le fichier FMA signifie essentiellement compresser le contenu du dossier dans un fichier ZIP.
Le contenu doit se trouver à la **RACINE du fichier ZIP**, il ne peut donc pas être placé dans un dossier supplémentaire à l’intérieur du ZIP.

Sous Windows, le moyen le plus simple de compresser le contenu FMA en ZIP est de tout sélectionner dans le dossier `fancymenu_animation`, puis de faire un **clic droit** sur le fichier `metadata.json`. Dans le menu contextuel qui s’ouvre, cliquez sur **Envoyer vers -> Dossier compressé (zip)**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Il devrait maintenant y avoir un nouveau fichier ZIP dans le dossier `fancymenu_animation`, nommé `metadata.zip`, `frames.zip` ou `intro_frames.zip`.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Lorsque vous ouvrez ce fichier, son contenu devrait ressembler à ceci :

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Vous devez maintenant renommer le fichier en `fancymenu_animation.fma`. Assurez-vous de **REMPLACER** le `.zip` par `.fma`, afin qu’il ne s’agisse plus d’un fichier ZIP.

Bien sûr, vous pouvez changer la partie `fancymenu_animation` par ce que vous voulez, mais assurez-vous que le fichier reste bien un fichier `.fma` !

C’est tout ! Vous avez maintenant un fichier FMA qui fonctionne (espérons-le) !

# Utiliser les fichiers AFMA & FMA dans FancyMenu

> [!IMPORTANT]
> Les fichiers AFMA/FMA sont considérés comme des **textures animées**, donc vous les ajoutez via des entrées de type **Image**. Presque tout ce qui accepte des images (PNG, JPEG, GIF, etc.) acceptera aussi les fichiers FMA et AFMA.

Vous pouvez utiliser les fichiers AFMA/FMA comme n’importe quel autre format de texture/image animée. FancyMenu le considère comme une image normale, donc vous pouvez l’utiliser partout où vous pouvez définir une texture, par exemple dans des **éléments Image ou des arrière-plans de menu Image**.

Assurez-vous que le fichier AFMA/FMA se trouve dans le dossier `/config/fancymenu/assets/`, car FancyMenu ne peut récupérer les textures et autres ressources que depuis son dossier `assets`.
