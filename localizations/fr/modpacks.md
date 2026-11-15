---
title: Packs de mods
description: Comment inclure des configurations dans un pack de mods.
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# FancyMenu dans les packs de mods

Inclure votre configuration FancyMenu dans un pack de mods est très simple et ne nécessite que quelques étapes.

> [!CAUTION]
> Les configurations FancyMenu peuvent exécuter des actions. Importez-les uniquement depuis des sources de confiance.

> [!WARNING]
> Cette page concerne **UNIQUEMENT** les configurations FancyMenu entièrement créées avec **FancyMenu v3 ou version ultérieure**. Si vous utilisez une ancienne configuration (créée avec la v2 puis convertie vers la v3), certaines étapes peuvent être différentes.

# Importer votre configuration dans le pack de mods

La manière la plus simple de déplacer votre configuration depuis l’instance sur laquelle vous l’avez conçue vers l’instance de votre pack de mods consiste à utiliser un [profil](./profiles) :

1. Dans l’instance contenant votre configuration, ouvrez **barre de menu -> Personnalisation -> Profils**, sélectionnez votre configuration et [exportez-la](./profiles#exporting) au format `.fmp`.
2. Dans l’instance de votre pack de mods, ouvrez la fenêtre des profils et [importez](./profiles#importing) le fichier `.fmp`, par exemple en le faisant glisser sur la fenêtre.
3. Sélectionnez le profil importé et cliquez sur **Charger le profil**.

La configuration FancyMenu présente auparavant dans l’instance du pack de mods n’est pas supprimée. Elle reste disponible dans son propre profil, ce qui vous permet de revenir à tout moment à cette configuration.

# Inclure la configuration dans votre pack de mods

Le profil chargé correspond au contenu de `<game-directory>/config/fancymenu/`. Il est donc inclus dans le dossier `config` de votre pack de mods, comme les fichiers de configuration des autres mods.

Tous les autres profils de l’instance sont enregistrés dans `<game-directory>/config/fancymenu/profiles/`. Supprimez les profils que les joueurs ne doivent pas recevoir avant d’exporter votre pack de mods, ou excluez le dossier `profiles` de l’exportation du pack de mods.

> [!CAUTION]
> Veuillez garder à l’esprit que les anciennes configurations créées avec FancyMenu v2 (même si elles ont été converties vers la v3) permettaient de stocker des ressources de mise en page en dehors du dossier `<game-directory>/config/fancymenu/assets/` de FancyMenu. Les profils ne contiennent que le dossier de configuration de FancyMenu ; dans ce cas, vous devez donc également vous assurer d’inclure toutes vos ressources dans le pack de mods.

## Comment trouver le dossier de l’instance

Le dossier de l’instance est le dossier principal de votre ordinateur dans lequel sont stockés tous les fichiers d’une configuration Minecraft spécifique. Des lanceurs comme CurseForge et Modrinth appellent ces dossiers des « instances » ou des « profils » (à ne pas confondre avec les profils de FancyMenu).

### Si vous utilisez l’application CurseForge

1. Ouvrez CurseForge.
2. Trouvez votre profil/instance Minecraft dans la liste et ouvrez-le.
3. Cliquez sur les trois points.
4. Choisissez « Ouvrir le dossier ». Le dossier principal de cette instance Minecraft s’ouvrira.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si vous utilisez l’application Modrinth

1. Ouvrez l’application Modrinth.
2. Trouvez votre profil/instance Minecraft dans la liste et ouvrez-le.
3. Cliquez sur les trois points.
4. Choisissez « Ouvrir le dossier ». Le dossier principal de cette instance Minecraft s’ouvrira.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Pour les autres lanceurs

Recherchez une option similaire à « Ouvrir le dossier », « Ouvrir le dossier de l’instance » ou « Afficher les fichiers » pour votre configuration Minecraft.

# Désactiver la barre de menu et les raccourcis clavier

Vous ne souhaitez certainement pas que la barre de menu de FancyMenu reste visible dans votre pack de mods ; vous devriez donc la désactiver. Cependant, comme les utilisateurs peuvent toujours appuyer sur le raccourci clavier pour la rendre visible à nouveau, faisons quelque chose d’un peu plus *radical*.

Accédez à `<game-directory>/config/fancymenu/options.txt` et ouvrez le fichier dans un éditeur de texte.

Définissez maintenant `modpack_mode` sur `true`, puis enregistrez le fichier.
Cela désactivera complètement toutes les superpositions et tous les raccourcis clavier.

Pour pouvoir modifier à nouveau vos mises en page, redéfinissez cette option de configuration sur `false`.

# Désactiver l’écran d’accueil

Cela ne devrait pas être nécessaire dans la plupart des cas, mais si vous n’avez pas encore fermé l’écran d’accueil (l’écran qui vous invite à lire la documentation), assurez-vous de définir `show_welcome_screen` sur `false` dans `<game-directory>/config/fancymenu/options.txt`.

Cet écran ne s’affiche qu’une seule fois et se désactive lorsque vous cliquez sur le bouton **Ouvrir la documentation**. Une intervention manuelle ne devrait donc, là encore, pas être nécessaire dans la plupart des cas.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
