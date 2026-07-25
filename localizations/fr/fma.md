---
title: Animations (FMA/AFMA)
description: Comment créer et utiliser des fichiers d’animation FancyMenu.
---
# Animations

Les fichiers AFMA et FMA sont des formats de texture animée créés pour FancyMenu.

# Fichiers AFMA

**AFMA** (Advanced FancyMenu Animation) est le successeur des fichiers FMA classiques.

AFMA utilise un format non-ZIP avec des fichiers plus petits, une consommation mémoire réduite et de meilleures performances que le FMA classique.

Pour les textures animées volumineuses ou complexes, utilisez **AFMA** plutôt que le FMA classique.

Créez des fichiers AFMA avec l’outil intégré :

1. Ouvrez la barre de menu de FancyMenu.
2. Allez dans **Tools -> AFMA Creator**.
3. Importez/convertissez vos images avec l’outil.

> [!IMPORTANT]
> Les fichiers AFMA ne peuvent pas être empaquetés manuellement. Utilisez **Tools -> AFMA Creator**.

Les fichiers FMA classiques restent pris en charge, donc les mises en page existantes n’ont pas besoin d’être converties immédiatement.

# Fichiers FMA classiques

## Créer un FMA

Un fichier FMA classique est une archive ZIP avec l’extension `.fma`.

### Extensions de fichiers

Activez les extensions de fichiers dans votre gestionnaire de fichiers avant de créer ou de renommer les fichiers ci-dessous.

Sous Windows, ouvrez l’Explorateur de fichiers et activez **Affichage -> Extensions de noms de fichiers**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Préparation

Créez un dossier nommé `fancymenu_animation` pour le contenu de l’archive.

Créez à l’intérieur un dossier obligatoire `frames` et un dossier optionnel `intro_frames`.

Dans ce même dossier, créez `metadata.json`. Assurez-vous que son extension est bien `.json` et non `.txt`.

Le dossier doit maintenant contenir `frames/`, `intro_frames/` et `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### Le JSON de métadonnées

Ouvrez `metadata.json` dans un éditeur de texte et utilisez ce modèle :

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

Modifiez les valeurs selon vos besoins.

#### `loop_count`

Contrôle le nombre de fois que l’animation se joue. Utilisez `0` pour une boucle infinie. Une valeur positive la fait jouer ce nombre de fois, puis conserve la dernière image.

#### `frame_time`

Définit la durée d’affichage de chaque image normale, en millisecondes.

#### `frame_time_intro`

Définit la durée des images d’**intro** optionnelles.

#### `custom_frame_times`

Permet de remplacer optionnellement la durée d’images normales individuelles. Cet exemple laisse les images `0` et `1` visibles pendant `5000` millisecondes, tandis que les autres images utilisent `frame_time` :

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Les indices des images commencent à 0 : la première image est `0`, la deuxième est `1`, et ainsi de suite.

Ajoutez une virgule après chaque entrée de durée personnalisée, sauf la dernière.

#### `custom_frame_times_intro`

Utilise le même format que `custom_frame_times`, mais s’applique aux images d’intro optionnelles.

Enregistrez `metadata.json`.

### Les images

> [!CAUTION]
> Limitez les animations FMA classiques à 200 images maximum et au 1080p. Utilisez [Vidéo](./video) pour les contenus longs ou à haute fréquence d’images.

Placez les images normales dans `frames/`. Elles doivent être des fichiers PNG nommés séquentiellement à partir de `0.png`, comme `0.png`, `1.png` et `2.png`. Les autres formats et noms ne sont pas pris en charge.

Pour extraire des images d’une vidéo, voir [Extraction d’images avec FFmpeg](./ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### L’intro

Placez les images d’intro optionnelles dans `intro_frames/`. Elles suivent les mêmes règles de nommage PNG que les images normales, se jouent une fois avant la séquence normale et ne bouclent pas.

### Empaqueter le fichier FMA

Créez un ZIP contenant le contenu du dossier. `metadata.json`, `frames/` et le dossier optionnel `intro_frames/` doivent se trouver à la racine du ZIP, et non dans un autre dossier.

Sous Windows, sélectionnez le contenu de `fancymenu_animation`, faites un clic droit sur la sélection, puis choisissez **Envoyer vers -> Dossier compressé (zippé)**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Trouvez le fichier ZIP obtenu.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Le contenu à sa racine devrait ressembler à ceci :

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Renommez le fichier en `fancymenu_animation.fma`, en remplaçant l’extension `.zip`. Le nom de base peut être modifié, mais l’extension `.fma` est obligatoire.

L’archive renommée est maintenant prête à être utilisée comme fichier FMA.

# Utiliser les fichiers AFMA et FMA dans FancyMenu

> [!IMPORTANT]
> Les fichiers AFMA/FMA sont des textures animées, donc ajoutez-les via des entrées [**Image**](./elements#image). Presque tout ce qui accepte des images accepte aussi les fichiers AFMA et FMA.

Utilisez les fichiers AFMA/FMA partout où une image est acceptée, y compris dans les [éléments Image](./elements#image) et les [arrière-plans de menu Image](./menu-backgrounds).

Placez le fichier AFMA/FMA dans `<game-directory>/config/fancymenu/assets/` afin qu’il apparaisse dans le sélecteur de ressources locales de FancyMenu.
