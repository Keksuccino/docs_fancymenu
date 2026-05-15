---
title: Modpacks
description: Comment inclure des mises en page dans un modpack.
---

# FancyMenu dans les modpacks

Inclure votre configuration FancyMenu dans un modpack est très simple et ne prend que quelques étapes.

> Cette page est **UNIQUEMENT** destinée aux configurations FancyMenu créées entièrement dans **FancyMenu v3+**. Si vous utilisez une ancienne configuration (créée en v2 puis convertie en v3), certaines étapes peuvent être différentes.
{.is-warning}

# Inclure la configuration FancyMenu dans votre modpack

L’essentiel à faire est de copier un dossier spécial que FancyMenu utilise pour enregistrer tous vos designs.

## Ce qu’il vous faut trouver

1. **Votre dossier « instance Minecraft » :** c’est le dossier principal sur votre ordinateur où sont stockés tous les fichiers d’une configuration Minecraft précise (par exemple celle dans laquelle vous avez créé vos menus). Les lanceurs comme CurseForge et Modrinth appellent cela des « instances » ou des « profils ».
2. **Le dossier `config` :** dans le dossier de votre instance Minecraft, il y a généralement un dossier nommé `config`. C’est ici que de nombreux mods enregistrent leurs paramètres.
3. **Le dossier `fancymenu` :** à l’intérieur de ce dossier `config`, FancyMenu crée son propre dossier appelé `fancymenu`. C’est le dossier en or qu’il nous faut !

## Comment trouver l’emplacement d’enregistrement de l’instance

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

Cherchez une option similaire comme « Open Folder », « Open Instance Folder » ou « View Files » pour votre configuration Minecraft spécifique.

## Copier la configuration FancyMenu

1. Accédez au dossier `config` de votre instance MODPACK (celle vers laquelle vous voulez copier votre configuration).
2. S’il y a déjà un dossier `fancymenu` à l’intérieur, SUPPRIMEZ-LE.
3. Ouvrez le dossier `config` de l’instance SOURCE (celle dont vous voulez utiliser la configuration).
4. Copiez le dossier `fancymenu` situé dans le dossier `config` de votre instance SOURCE vers le dossier `config` de votre instance MODPACK.
5. C’est fait. Redémarrez maintenant votre instance de modpack et vous devriez voir la configuration se charger.

> Veuillez garder à l’esprit que les anciennes configurations héritées créées avec FancyMenu v2 (même si elles ont été converties en v3) vous permettaient de stocker les ressources de mise en page en dehors du dossier `/config/fancymenu/assets/` de FancyMenu. Dans ce cas, vous devez donc vous assurer d’inclure aussi toutes vos ressources dans le modpack.
{.is-danger}

# Désactiver la barre de menu et les raccourcis clavier

Vous ne voulez sûrement pas garder la barre de menu de FancyMenu visible dans votre modpack, donc vous devriez la désactiver. Mais comme les gens peuvent toujours appuyer sur le raccourci clavier pour la faire réapparaître, faisons quelque chose d’un peu plus *agressif*.

Accédez à `/config/fancymenu/options.txt` et ouvrez le fichier dans un éditeur de texte.

Réglez maintenant `modpack_mode` sur `true` et enregistrez le fichier.
Cela désactivera complètement tous les overlays et les raccourcis clavier.

Pour pouvoir modifier à nouveau vos mises en page, remettez l’option de configuration sur `false`.

# Désactiver l’écran de bienvenue

Cela ne devrait pas être nécessaire dans la plupart des cas, mais si vous n’avez pas encore fermé l’écran de bienvenue (l’écran qui vous demande de lire la documentation), assurez-vous de définir `show_welcome_screen` sur `false` dans `/config/fancymenu/options.txt`.

Cet écran ne s’affiche qu’une seule fois et se désactive lorsqu’on clique sur le bouton **Open Documentation**, donc encore une fois, faire cela manuellement ne devrait généralement pas être nécessaire.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
