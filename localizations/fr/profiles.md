---
title: Profils
description: >-
  Enregistrez, changez et partagez des configurations FancyMenu complètes avec
  des profils, et installez des modèles de mise en page créés par la communauté.
sourceBlobSha: 52348efde29798073477e572b59a7630f96013ad
---

# Profils

Un profil est une configuration FancyMenu complète : mises en page, ressources, variables, paramètres et tout le reste du dossier `config/fancymenu/` (voir [Emplacements de stockage des données](/data-storage-locations#your-setup)). Avec les profils, vous pouvez conserver plusieurs configurations dans une même instance Minecraft, passer de l’une à l’autre en quelques secondes et les partager dans un seul fichier.

<img width="800" alt="Création du profil My Menu Pack, importation du profil Wind Chimes en déposant son fichier .fmp dans la fenêtre Profils, suppression de My Menu Pack et chargement de Wind Chimes, ce qui modifie l’écran titre" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# La fenêtre Profils

Ouvrez-la avec **barre de menus -> Personnalisation -> Profils**.

- La liste à gauche affiche tous les profils. Celui qui est chargé apparaît en premier et porte la mention **Actif**. Toutes les modifications que vous apportez dans FancyMenu sont directement enregistrées dans celui-ci.
- La partie droite affiche le profil sélectionné : son icône, son titre, sa version, ses auteurs, le nombre de mises en page, sa taille, ses liens et sa description.
- Survolez les boutons sous la liste et les détails pour afficher leur nom. Faites un clic droit sur un profil pour afficher également ses actions.

Votre configuration devient automatiquement votre premier profil, nommé **Mon profil**.

# Charger un profil

Sélectionnez un profil, puis cliquez sur **Charger le profil**, double-cliquez dessus ou appuyez sur `Entrée`.

FancyMenu se recharge alors avec le profil, comme au démarrage du jeu. Toutes les autres fenêtres FancyMenu se ferment et, si vous n’êtes pas dans un monde, l’écran titre s’ouvre.

> [!NOTE]
> Le chargement ne supprime jamais rien. Votre configuration actuelle est d’abord enregistrée dans son propre profil, ce qui vous permet toujours de revenir en arrière.

# Créer des profils

- **Nouveau profil** (le bouton `+` sous la liste) crée un profil vide et ouvre immédiatement ses détails pour que vous puissiez le nommer. Il conserve vos préférences FancyMenu, comme l’échelle de l’interface et le thème, mais ne contient aucune mise en page ni autre personnalisation. Il n’est pas chargé automatiquement.
- **Dupliquer** copie le profil sélectionné, ce qui est pratique pour essayer quelque chose sans modifier l’original.

# Modifier les détails d’un profil

Sélectionnez un profil et cliquez sur **Modifier** pour changer ses détails :

- **Titre**, le seul élément obligatoire d’un profil.
- **Version** et **Auteurs**. Séparez plusieurs auteurs par des virgules.
- **Description**, avec la [syntaxe Markdown](/text-formatting#markdown), par exemple du texte en gras, des titres et des listes.
- **Suivi des problèmes**, un site web où les utilisateurs peuvent signaler les problèmes liés au profil. Il apparaît sous le nom **Signaler un problème**.
- **Liens** vers votre serveur Discord, votre chaîne YouTube, votre site web et plus encore. Cliquez sur **Ajouter un lien** et collez le lien : FancyMenu détecte automatiquement la plateforme.
- Une icône : **Choisir une icône** permet de sélectionner une image PNG, et **Supprimer l’icône** permet de la retirer. Les images qui ne sont pas carrées sont recadrées au centre.

Rien n’est enregistré tant que vous n’avez pas cliqué sur **Terminé**.

# Partager des profils

> [!CAUTION]
> Les profils peuvent exécuter des actions, comme ouvrir des liens ou lancer des commandes. N’importez des profils que depuis des sources fiables.

## Exporter

Sélectionnez un profil, cliquez sur **Exporter**, puis choisissez où l’enregistrer. Un fichier `.fmp` contenant le profil complet est créé, prêt à être partagé.

## Importer

Cliquez sur **Importer** sous la liste et choisissez un fichier `.fmp`, ou faites glisser le fichier dans la fenêtre Profils.

- Les profils importés ne sont pas chargés automatiquement. Chargez-les comme n’importe quel autre profil.
- Si vous possédez déjà le profil, par exemple une version plus ancienne, choisissez **Remplacer** ou **Conserver les deux**. Si vous remplacez le profil chargé, le profil importé est chargé immédiatement et vos modifications apportées à l’ancien profil sont perdues.
- Les profils créés avec une version plus récente de FancyMenu affichent d’abord un avertissement, car certaines de leurs parties pourraient ne pas fonctionner.
- Seuls les fichiers `.fmp` exportés par FancyMenu sont pris en charge. Pour un dossier ordinaire, consultez la section suivante.

## Ajouter des dossiers de configuration

Certaines configurations sont fournies sous la forme d’un simple dossier `fancymenu` (une copie du dossier `config/fancymenu/` de quelqu’un) plutôt que d’un fichier `.fmp`. Pour l’ajouter comme profil :

1. Décompressez-le s’il est fourni sous forme de fichier `.zip`.
2. Déplacez le dossier dans `<game-directory>/config/fancymenu/profiles/`. Créez le dossier `profiles` s’il n’existe pas encore.
3. Ouvrez la fenêtre Profils, ou fermez-la puis rouvrez-la. FancyMenu ajoute le dossier à vos profils.

Le dossier doit contenir directement les fichiers, comme `customization/` et `options.txt`, et non un autre dossier `fancymenu`. Le titre du profil correspond au nom du dossier, sauf si celui-ci contient ses propres détails de profil. Vous pouvez le modifier avec **Modifier**.

## Modèles de mise en page

Le salon [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) du [serveur Discord Kekscord](https://discord.gg/rhayah27GC) (le serveur Discord officiel de Keksuccino pour l’assistance sur ses mods) propose des configurations complètes créées par la communauté pour FancyMenu et ses extensions, comme SpiffyHUD et Drippy Loading Screen. Chaque publication contient un lien de téléchargement, soit vers un fichier `.fmp`, soit vers un dossier `fancymenu`.

Les modèles sont complexes : n’essayez donc pas de les fusionner avec votre propre configuration. Ajoutez-les plutôt en tant que profils distincts :

1. [Importez](#importing) le fichier `.fmp`, ou [ajoutez le dossier](#adding-setup-folders).
2. Sélectionnez le modèle dans la fenêtre Profils et cliquez sur **Charger le profil**.

Votre propre configuration reste disponible dans son profil distinct, et vous pouvez toujours y revenir.

La plupart des modèles peuvent être modifiés et utilisés dans vos propres projets, comme des modpacks, mais ce n’est pas le cas de tous. Consultez toujours la publication du modèle pour connaître les conditions d’utilisation.

# Supprimer des profils

Sélectionnez un profil et cliquez sur **Supprimer**, ou appuyez sur `Delete` (`Fn + Delete` sur macOS). La suppression est irréversible : exportez d’abord le profil si vous souhaitez en conserver une sauvegarde.

Le profil chargé ne peut pas être supprimé. Chargez d’abord un autre profil.

# Emplacement de stockage des profils

- Le profil chargé correspond au contenu de `<game-directory>/config/fancymenu/`.
- Tous les autres profils se trouvent dans `<game-directory>/config/fancymenu/profiles/`, chacun dans son propre dossier. **Ouvrir le dossier** ouvre celui du profil sélectionné.

`<game-directory>` désigne le dossier de votre instance, qui peut être différent de `.minecraft`. Les données du dossier `<game-directory>/fancymenu_data/` ne font pas partie des profils. Consultez [Emplacements de stockage des données](/data-storage-locations#instance-data).

# En cas de problème

- **Certains de ses fichiers sont encore utilisés :** le jeu est souvent en train de charger quelque chose, comme des fichiers audio. Attendez quelques secondes, puis réessayez. Si le problème persiste, fermez les programmes susceptibles d’utiliser les fichiers, comme votre antivirus, votre service de synchronisation cloud ou une fenêtre de l’explorateur de fichiers.
- **Le dernier changement de profil n’est pas encore terminé :** rien n’a été perdu. Chargez de nouveau un profil ou redémarrez le jeu pour terminer le changement.
- **Il n’y a pas assez d’espace disque disponible :** le message indique l’espace nécessaire au profil. Libérez de l’espace, puis réessayez.
- Les actions liées aux profils s’exécutent une par une. L’exportation, l’importation et la duplication de profils volumineux peuvent prendre un moment ; un bouton **Annuler** apparaît donc pendant leur exécution.
