---
title: Modpacks
description: Comment inclure des mises en page dans un modpack.
---

# FancyMenu dans les modpacks

Inclure votre configuration FancyMenu dans un modpack est très facile et ne prend que quelques étapes simples.

> [!CAUTION]
> Les configurations FancyMenu peuvent exécuter des actions. N’importez-les que depuis des sources en lesquelles vous avez confiance.

> [!WARNING]
> Cette page est **UNIQUEMENT** destinée aux configurations FancyMenu créées entièrement dans **FancyMenu v3+**. Si vous utilisez une ancienne configuration (créée en v2 puis convertie en v3), certaines étapes peuvent être différentes.

# Inclure la configuration FancyMenu dans votre modpack

La principale chose à faire est de copier un dossier spécial que FancyMenu utilise pour enregistrer tous vos designs.

## Ce qu’il vous faut trouver

1. **Votre dossier « instance Minecraft » :** c’est le dossier principal sur votre ordinateur où sont stockés tous les fichiers d’une configuration Minecraft spécifique (comme celle avec laquelle vous avez créé vos menus). Des lanceurs comme CurseForge et Modrinth appellent cela des « instances » ou des « profils ».
2. **Le dossier `config` :** à l’intérieur du dossier de votre instance Minecraft, il y a généralement un dossier nommé `config`. C’est là que de nombreux mods enregistrent leurs paramètres.
3. **Le dossier `fancymenu` :** à l’intérieur de ce dossier `config`, FancyMenu crée son propre dossier appelé `fancymenu`. C’est le dossier précieux dont nous avons besoin !

## Comment trouver l’emplacement de sauvegarde de l’instance

### Si vous utilisez l’application CurseForge

1. Ouvrez CurseForge.
2. Trouvez votre profil/instance Minecraft dans la liste et ouvrez-le.
3. Cliquez sur les trois points.
4. Choisissez « Open Folder ». Cela ouvrira le dossier principal de cette instance Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si vous utilisez l’application Modrinth

1. Ouvrez l’application Modrinth.
2. Trouvez votre profil/instance Minecraft dans la liste et ouvrez-le.
3. Cliquez sur les trois points.
4. Choisissez « Open Folder ». Cela ouvrira le dossier principal de cette instance Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Pour les autres lanceurs

Recherchez une option similaire « Open Folder », « Open Instance Folder » ou « View Files » pour votre configuration Minecraft spécifique.

## Copier la configuration FancyMenu

1. Accédez au dossier `config` de votre instance du MODPACK (celle vers laquelle vous voulez copier votre configuration).
2. S’il existe un dossier `fancymenu` à l’intérieur, SUPPRIMEZ-le.
3. Ouvrez le dossier `config` de l’instance SOURCE (celle dont vous voulez utiliser la configuration).
4. Copiez le dossier `fancymenu` du dossier `config` de votre instance SOURCE vers le dossier `config` de votre instance du MODPACK.
5. C’est terminé. Voilà tout. Redémarrez maintenant votre instance du modpack et vous devriez voir la configuration se charger.

> [!CAUTION]
> Gardez à l’esprit que les anciennes configurations héritées créées dans FancyMenu v2 (même si elles ont été converties en v3) permettaient de stocker des ressources de mise en page en dehors du dossier `<game-directory>/config/fancymenu/assets/` de FancyMenu. Dans ce cas, vous devez vous assurer d’inclure également toutes vos ressources dans le modpack.

# Désactiver la barre de menu et les raccourcis clavier

Vous ne voulez sûrement pas laisser la barre de menu de FancyMenu visible dans votre modpack, donc vous devriez la désactiver. Mais comme les gens peuvent toujours appuyer sur le raccourci clavier pour la faire réapparaître, faisons quelque chose d’un peu plus *agressif*.

Accédez à `<game-directory>/config/fancymenu/options.txt` et ouvrez le fichier dans un éditeur de texte.

Réglez maintenant `modpack_mode` sur `true` et enregistrez le fichier.
Cela désactivera complètement toutes les superpositions et tous les raccourcis clavier.

Pour pouvoir modifier à nouveau vos mises en page, remettez l’option de configuration sur `false`.

# Désactiver l’écran d’accueil

Cela ne devrait pas être nécessaire dans la plupart des cas, mais si vous n’avez pas encore fermé l’écran d’accueil (l’écran qui vous demande de lire la documentation), assurez-vous de régler `show_welcome_screen` sur `false` dans `<game-directory>/config/fancymenu/options.txt`.

Cet écran ne s’affiche qu’une seule fois et se désactive en cliquant sur le bouton **Open Documentation**. Encore une fois, cela ne devrait donc généralement pas être nécessaire de le faire manuellement.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
