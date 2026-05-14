---
title: Obtenir des images à partir de vidéos
description: Comment extraire des images d'un fichier vidéo.
---

# Comment obtenir des images à partir d'une vidéo avec FFmpeg

*Cette page a été en partie générée par l'IA ChatGPT.*

FFmpeg est un outil gratuit qui vous aide à travailler avec des fichiers vidéo et audio. L’une des choses pratiques que vous pouvez faire avec lui est d’extraire des images (des frames) d’une vidéo, comme un fichier MP4. Voici comment procéder, étape par étape.

MP4 sera utilisé dans les commandes suivantes, mais FFmpeg prend également en charge d’autres formats vidéo comme AVI, MOV, MKV et MPEG.

# Ce dont vous avez besoin

Avant de commencer, assurez-vous d’avoir :

1. **FFmpeg installé** :

   - Téléchargez FFmpeg depuis le site officiel [FFmpeg](https://ffmpeg.org/download.html). Assurez-vous de télécharger la version complète (« full »).
   - Suivez les instructions d’installation correspondant à votre ordinateur.

2. **Accès à la ligne de commande** :

   - Utilisez le terminal (Linux/macOS) ou l’invite de commandes (Windows) pour exécuter les commandes FFmpeg.

3. **Un fichier vidéo** :

    - Ayez un fichier vidéo MP4, AVI, MOV, MKV ou MPEG prêt à être utilisé.

# Avant de commencer

Avant d’exécuter des commandes, assurez-vous de préparer les éléments suivants :

## Activer les extensions de fichiers

  - Il est important de voir les extensions de fichiers comme `.mp4` ou `.avi` lorsque vous renommez votre fichier vidéo.

    - **Sur Windows** :

      - Ouvrez l’Explorateur de fichiers.
      - Cliquez sur l’onglet « Affichage » en haut.
      - Cochez la case « Extensions de noms de fichiers ».

    - **Sur macOS** :

      - Ouvrez le Finder.
      - Cliquez sur « Finder » dans la barre de menus, puis sélectionnez « Préférences ».
      - Allez dans l’onglet « Avancé » et cochez la case « Afficher toutes les extensions de nom de fichier ».

## Créer un dossier de sortie

- Créez un dossier nommé `output_frames` dans le répertoire où se trouve l’exécutable FFmpeg. C’est là que seront enregistrées les images extraites.

## Préparer votre fichier vidéo

- Placez le fichier vidéo dont vous voulez extraire les images dans le même répertoire que l’exécutable FFmpeg.
- Renommez le fichier vidéo en `input` suivi de son extension de fichier (par exemple, `input.mp4`, `input.avi`, etc.). Cela garantit que les commandes ci-dessous fonctionneront sans modification.

<br>
<img width="579" alt="Screenshot_4" src="https://gist.github.com/user-attachments/assets/1cb4ddf9-a17a-4219-b7d4-aa344adaa87c" />

# Comment ouvrir FFmpeg

Avant de pouvoir utiliser FFmpeg, vous devez l’ouvrir via la ligne de commande. Voici comment procéder étape par étape sous Windows et macOS.

## Sous Windows :

1. **Ouvrir l’invite de commandes** :
   - Appuyez simultanément sur la touche `Windows` et la touche `R` pour ouvrir la boîte Exécuter.
   - Tapez `cmd` puis appuyez sur Entrée. Cela ouvre l’invite de commandes.

2. **Aller au dossier FFmpeg** :
   - Vous devez indiquer à l’ordinateur où se trouve FFmpeg. Utilisez la commande `cd` pour aller dans le dossier où vous avez enregistré FFmpeg.
   - Par exemple, si FFmpeg se trouve dans un dossier appelé `ffmpeg-2024\bin` sur votre bureau, tapez :
     ```bash
     cd C:\Users\VotreNomDUtilisateur\Desktop\ffmpeg-2024\bin
     ```
     (Remplacez « VotreNomDUtilisateur » par votre vrai nom d’utilisateur sur l’ordinateur.)

3. **Vérifier que FFmpeg fonctionne** :
   - Pour vous assurer que FFmpeg fonctionne, tapez cette commande :
     ```bash
     ffmpeg -version
     ```
   - S’il fonctionne, des informations sur FFmpeg apparaîtront à l’écran.

## Sur macOS :

1. **Ouvrir le Terminal** :
   - Appuyez simultanément sur `Command` et `Space` pour ouvrir Spotlight.
   - Tapez `Terminal` puis appuyez sur Entrée pour l’ouvrir.

2. **Aller au dossier FFmpeg** :
   - Utilisez la commande `cd` pour aller dans le dossier où vous avez enregistré FFmpeg.
   - Par exemple, si FFmpeg se trouve dans votre dossier `Downloads`, tapez :
     ```bash
     cd ~/Downloads/ffmpeg-2024/bin
     ```

3. **Vérifier que FFmpeg fonctionne** :
   - Pour vous assurer que FFmpeg est prêt, tapez cette commande :
     ```bash
     ./ffmpeg -version
     ```
   - Si FFmpeg fonctionne, des détails à son sujet apparaîtront à l’écran.

# Comment enregistrer toutes les images

Pour enregistrer toutes les images d’une vidéo, utilisez cette commande :

```bash
ffmpeg -i input.mp4 output_frames/%d.png
```

## Ce que cela signifie :

- `-i input.mp4` : C’est votre fichier vidéo d’entrée. Il doit se trouver dans le même répertoire que l’exécutable FFmpeg. Veillez à remplacer `input.mp4` par le bon nom de fichier et la bonne extension.
- `output_frames/frame_%04d.png` : Voici comment les images seront enregistrées :
- `output_frames/` : Enregistre toutes les images dans un dossier appelé `output_frames`.
- `%d.png` : Les images seront nommées avec des numéros comme `1.png`, `2.png`, et ainsi de suite, en respectant l’ordre.

# Enregistrer des images à certains moments

Si vous ne voulez pas toutes les images, vous pouvez enregistrer une image par seconde (ou à d’autres intervalles). Utilisez cette commande :

```bash
ffmpeg -i input.mp4 -vf "fps=1" output_frames/%d.png
```

## Ce que cela signifie :

- `-i input.mp4` : C’est votre fichier vidéo d’entrée. Il doit se trouver dans le même répertoire que l’exécutable FFmpeg. Veillez à remplacer `input.mp4` par le bon nom de fichier et la bonne extension.
- `-vf "fps=1"` : Cela enregistre une image par seconde. Modifiez le `1` pour un autre nombre si vous voulez des images plus ou moins souvent (par exemple, `fps=0.5` enregistre une image toutes les deux secondes, et `fps=2` enregistre deux images par seconde).
- `output_frames/%d.png` : Enregistre les images dans un dossier nommé `output_frames` avec des noms comme `1.png`, `2.png`, et ainsi de suite.

# Modifier la taille et la qualité des images

Vous pouvez aussi ajuster la taille et la qualité des images que vous enregistrez. Voici comment :

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" -q:v 2 output_frames/%d.png
```

## Ce que cela signifie :

- `-i input.mp4` : C’est votre fichier vidéo d’entrée. Il doit se trouver dans le même répertoire que l’exécutable FFmpeg. Veillez à remplacer `input.mp4` par le bon nom de fichier et la bonne extension.
- `-vf "scale=1280:720"` : Modifie la taille de l’image en 1280x720 pixels.
- `-q:v 2` : Définit la qualité de l’image (1 est la meilleure qualité, les nombres plus élevés indiquent une qualité plus faible).
- `output_frames/%d.png` : Enregistre les images dans un dossier nommé `output_frames` avec des noms comme `1.png`, `2.png`, et ainsi de suite.

# Conseils pour enregistrer des images

1. **Économiser de l’espace** :

   - Si la vidéo est longue, vous pouvez enregistrer des images à intervalles réguliers plutôt que d’enregistrer chaque image. C’est particulièrement utile si vous les utilisez comme images d’animation FMA dans FancyMenu.

2. **En savoir plus** :

   - Exécutez `ffmpeg -h` dans votre terminal pour voir toutes les possibilités de FFmpeg.

<br>
Vous êtes maintenant prêt à utiliser FFmpeg pour enregistrer des images à partir de votre vidéo !&#x20;

