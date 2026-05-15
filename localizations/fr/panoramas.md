---
title: Panoramas
description: Comment créer et utiliser des panoramas d’arrière-plan personnalisés.
---

# Panoramas cubiques

FancyMenu prend en charge le chargement de panoramas cubiques personnalisés composés de 6 images comme arrière-plan pour les menus.

Ces panoramas sont un format spécial de panorama cubique utilisé par Minecraft comme arrière-plan de l’écran titre et sont constitués de 6 images (faces) rendues comme un cube (ou plus précisément comme un skybox).

> **IMPORTANT** : Si vous êtes sous Windows, n’oubliez pas d’activer les [extensions de fichiers](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png), sinon vous ne pourrez pas voir des parties importantes des noms de fichiers plus tard !
{.is-warning}

# Créer un panorama

Si vous ne savez pas comment Minecraft gère ses panoramas d’arrière-plan et comment en créer, vous devriez regarder [cette vidéo](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t).
Elle vous donnera une très bonne compréhension du fonctionnement des panoramas de Minecraft et de la manière d’en créer un !

Après avoir regardé la vidéo, vous remarquerez que la création de ces panoramas peut être un peu longue.
Pour vous faire gagner du temps, pensez peut-être à utiliser un mod qui les crée pour vous.
Vous pouvez en trouver en recherchant `minecraft panorama mod`, mais l’un d’eux est [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica) (créé par moi).

# Préparer le panorama

Après avoir obtenu vos 6 images de panorama, vous devrez les déplacer au bon endroit !

Le répertoire des panoramas de FancyMenu se trouve dans `.minecraft/config/fancymenu/panoramas`.
C’est le dossier de tous les panoramas que vous souhaitez utiliser dans le mod.

## Le dossier du panorama

Chaque panorama possède son propre dossier.
Vous devrez créer un nouveau dossier dans `.minecraft/config/fancymenu/panoramas` si vous voulez ajouter un nouveau panorama.
Dans mon exemple, je vais nommer le dossier `mypanorama`.

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## Contenu du dossier

Après avoir créé le dossier, vous devrez le remplir.

### Fichier de propriétés
Chaque panorama a besoin d’un fichier de propriétés pour fonctionner.
Ce fichier doit toujours s’appeler `properties.txt` et contenir certaines informations importantes.

Le contenu d’un fichier de propriétés de panorama doit toujours ressembler à ceci :
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
Seules les variables à l’intérieur de la section `panorama-meta` peuvent être modifiées !

#### name
Cela doit être le nom **unique** de votre panorama.
Il n’est pas possible de charger deux panoramas ayant le même nom !
Vous utiliserez ce nom plus tard pour identifier votre panorama.

#### speed
La vitesse à laquelle votre panorama tourne.
Cette valeur est un multiplicateur de vitesse. Par exemple, `1.0` est la vitesse par défaut, `2.0` double la vitesse et `0.5` la divise par deux.
Les valeurs négatives ne sont pas prises en charge ; utilisez des valeurs décimales pour ralentir la vitesse.

#### fov
Le champ de vision.
Le FOV par défaut est `85.0`.
Des valeurs trop grandes ou trop petites casseront le panorama. Ajustez-le simplement pour trouver le FOV souhaité.

#### angle
L’angle vertical sous lequel le panorama est visualisé.
L’angle par défaut est `25.0`.

#### start_rotation
L’angle de rotation (horizontal) auquel le panorama doit commencer. Valeur comprise entre 0 et 360.

<br>

### Dossier des images du panorama

Le deuxième élément obligatoire dont votre dossier de panorama a besoin est le dossier d’images proprement dit contenant vos images de panorama.

Le nom de ce dossier doit être `panorama`.

Placez-y toutes vos images de panorama, mais n’oubliez pas de les nommer correctement comme indiqué dans la [vidéo](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t) ci-dessus !

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> Seuls les PNG sont pris en charge comme images de panorama !
{.is-warning}

### Superposition du panorama

La dernière étape est **facultative** et peut être ignorée si vous ne voulez pas de superposition sur votre panorama.

Si vous souhaitez ajouter un vignettage ou d’autres types de superpositions à votre panorama, vous pouvez en ajouter une nommée `overlay.png`.
Gardez à l’esprit que seul le format PNG est pris en charge pour la superposition et que le nom du fichier doit toujours être `overlay.png` !

### Vérifier à nouveau

Vous devriez maintenant avoir un dossier situé dans `.minecraft/config/fancymenu/panoramas`, contenant un fichier `properties.txt`, un autre dossier nommé `panorama` et éventuellement une superposition nommée `overlay.png`.

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# Utiliser le panorama

Après avoir (re)démarré le jeu ou rechargé FancyMenu via **Customization -> Reload FancyMenu**, vous devriez maintenant pouvoir définir votre panorama comme arrière-plan de menu. Pour ce faire, faites un clic droit sur l’arrière-plan de l’éditeur de mise en page, puis cliquez sur **Menu Background**.
