---
title: Packs de mods
description: Comment inclure des mises en page dans un pack de mods.
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# FancyMenu dans les packs de mods

Inclure votre configuration FancyMenu dans un pack de mods est très simple et ne demande que quelques étapes.

> [!CAUTION]
> Les configurations FancyMenu peuvent exécuter des actions. N’importez que celles provenant de sources fiables.

> [!WARNING]
> Cette page concerne **UNIQUEMENT** les configurations FancyMenu créées entièrement avec **FancyMenu v3 ou une version ultérieure**. Si vous utilisez une ancienne configuration (créée avec la v2, puis convertie vers la v3), certaines étapes peuvent être différentes.

# Ajouter votre configuration au pack de mods

Le moyen le plus simple de transférer votre configuration de l’instance où vous l’avez créée vers celle de votre pack de mods est d’utiliser un [profil](/profiles) :

1. Dans l’instance contenant votre configuration, ouvrez **barre de menu -> Personnalisation -> Profils**, sélectionnez votre configuration, puis [exportez-la](/profiles#exporting) au format `.fmp`.
2. Dans l’instance de votre pack de mods, ouvrez la fenêtre Profils et [importez](/profiles#importing) le fichier `.fmp`, par exemple en le faisant glisser dans la fenêtre.
3. Sélectionnez le profil importé et cliquez sur **Charger le profil**.

La configuration FancyMenu qui se trouvait auparavant dans l’instance de votre pack de mods n’est pas perdue. Elle reste disponible sous la forme de son propre profil, et vous pouvez donc toujours y revenir.

# Inclure la configuration dans votre pack de mods

Le profil chargé correspond au contenu de `<game-directory>/config/fancymenu/`. Il sera donc inclus dans le dossier `config` de votre pack de mods, comme les fichiers de configuration des autres mods.

Tous les autres profils de l’instance sont stockés dans `<game-directory>/config/fancymenu/profiles/`. Avant d’exporter votre pack de mods, supprimez les profils que vous ne souhaitez pas distribuer aux joueurs, ou excluez le dossier `profiles` de l’exportation du pack.

> [!CAUTION]
> N’oubliez pas que les anciennes configurations créées avec FancyMenu v2 (même si elles ont été converties vers la v3) permettaient de stocker les ressources des mises en page en dehors du dossier `<game-directory>/config/fancymenu/assets/` de FancyMenu. Comme les profils ne contiennent que le dossier de configuration de FancyMenu, vous devez également inclure toutes vos ressources dans le pack de mods.

## Réinitialiser les cases à cocher avant l’exportation

Les [éléments de type case à cocher](/elements#checkbox) mémorisent leur état dans `config/fancymenu/checkbox_states.json`. Les cases sur lesquelles vous avez cliqué pendant vos tests seront donc aussi cochées pour vos joueurs.

Pour que les joueurs commencent avec une configuration vierge, fermez le jeu et supprimez `checkbox_states.json` avant d’exporter votre pack de mods ou votre profil. En l’absence de ce fichier, toutes les cases sont décochées au démarrage. Les cases qui utilisent une [variable](/variables) enregistrent leur état dans cette variable.

Cela s’applique également aux éléments modifiés par des actions pendant vos tests, comme le volume des [éléments vidéo](/video). Consultez [Emplacements de stockage des données](/data-storage-locations#your-setup) pour connaître les fichiers concernés.

## Trouver le dossier de l’instance

Le dossier de l’instance est le dossier principal de votre ordinateur où sont stockés tous les fichiers d’une configuration Minecraft donnée. Les lanceurs comme CurseForge et Modrinth appellent ces configurations des « instances » ou des « profils » (à ne pas confondre avec les profils de FancyMenu).

### Si vous utilisez l’application CurseForge

1. Ouvrez CurseForge.
2. Trouvez votre profil/instance Minecraft dans la liste et ouvrez-le.
3. Cliquez sur les trois points.
4. Choisissez « Ouvrir le dossier ». Le dossier principal de cette instance Minecraft s’ouvrira.

<img width="630" alt="Capture d’écran 1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si vous utilisez l’application Modrinth

1. Ouvrez l’application Modrinth.
2. Trouvez votre profil/instance Minecraft dans la liste et ouvrez-le.
3. Cliquez sur les trois points.
4. Choisissez « Ouvrir le dossier ». Le dossier principal de cette instance Minecraft s’ouvrira.

<img width="630" alt="Capture d’écran 1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Pour les autres lanceurs

Cherchez une option similaire, comme « Ouvrir le dossier », « Ouvrir le dossier de l’instance » ou « Afficher les fichiers », pour votre configuration Minecraft.

# Désactiver la barre de menu et les raccourcis clavier

Vous ne souhaitez sûrement pas que la barre de menu de FancyMenu reste visible dans votre pack de mods : vous devriez donc la désactiver. Mais comme les joueurs pourraient toujours appuyer sur le raccourci clavier pour la faire réapparaître, prenons une mesure un peu plus *radicale*.

Accédez à `<game-directory>/config/fancymenu/options.txt` et ouvrez le fichier dans un éditeur de texte.

Définissez ensuite `modpack_mode` sur `true` et enregistrez le fichier.
Cela désactivera complètement toutes les superpositions et tous les raccourcis clavier.

Pour pouvoir modifier à nouveau vos mises en page, remettez cette option de configuration sur `false`.

# Désactiver l’écran de bienvenue

Cela ne devrait généralement pas être nécessaire, mais si vous n’avez pas encore fermé l’écran de bienvenue (celui qui vous invite à lire la documentation), veillez à définir `show_welcome_screen` sur `false` dans `<game-directory>/config/fancymenu/options.txt`.

Cet écran ne s’affiche qu’une seule fois et se désactive lorsque vous cliquez sur le bouton **Ouvrir la documentation**. Il n’est donc généralement pas nécessaire de le faire manuellement.

<br>
<img width="630" alt="Capture d’écran 1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
