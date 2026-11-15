---
title: Profils
description: >-
  Comment enregistrer, changer et partager des configurations FancyMenu
  complètes avec des profils.
sourceBlobSha: d0a07901ee271d802c7bc07ea6d787575f48d51c
---
# Profils

Un profil est une configuration FancyMenu complète : toutes les dispositions, ressources, variables et options FancyMenu d'une instance. Les profils vous permettent de conserver plusieurs configurations dans une même instance Minecraft, de passer de l'une à l'autre en quelques secondes et de les partager avec d'autres utilisateurs sous la forme d'un seul fichier.

<img width="800" alt="profils" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Ouvrir la fenêtre des profils

Ouvrez la fenêtre des profils via **barre de menus -> Personnalisation -> Profils**.

La liste à gauche affiche tous vos profils, tandis que le côté droit affiche les détails de celui qui est sélectionné. Le profil chargé est marqué comme **Actif**. Chaque modification effectuée dans FancyMenu est directement enregistrée dans le profil chargé.

Votre configuration existante devient automatiquement votre premier profil, nommé **Mon profil**.

> [!TIP]
> Faites un clic droit sur un profil dans la liste pour voir toutes les actions disponibles.

# Changer de profil

Sélectionnez un profil et cliquez sur **Charger le profil**, ou double-cliquez dessus. FancyMenu se recharge alors avec la configuration sélectionnée.

> [!NOTE]
> Changer de profil ne supprime jamais rien. Votre configuration actuelle est enregistrée dans son propre profil avant le chargement de l'autre, vous pouvez donc toujours revenir en arrière.

# Créer des profils

- **Nouveau profil** (le bouton **+** situé sous la liste) crée un profil vide et ouvre son éditeur. Les profils vides conservent vos préférences personnelles FancyMenu, comme l'échelle de l'interface et le thème.
- **Dupliquer** crée une copie du profil sélectionné, ce qui est pratique pour faire des essais sans modifier l'original.

# Modifier les profils

Cliquez sur **Modifier** pour changer le titre, la version, les auteurs, la description, l'icône, le gestionnaire de problèmes et les liens d'un profil. La description prend en charge Markdown et l'icône peut être n'importe quelle image PNG.

Rien n'est enregistré tant que vous n'avez pas cliqué sur **Terminé**.

# Partager des profils

> [!CAUTION]
> Les profils peuvent exécuter des actions. Importez-les uniquement depuis des sources fiables.

## Exporter

Sélectionnez un profil, cliquez sur **Exporter**, puis choisissez l'emplacement où l'enregistrer. Cela crée un fichier `.fmp` contenant l'intégralité du profil.

## Importer

Cliquez sur **Importer** sous la liste et sélectionnez un fichier `.fmp`, ou faites simplement glisser le fichier dans la fenêtre des profils.

- Les profils importés ne sont pas chargés automatiquement. Chargez-les comme n'importe quel autre profil.
- Si vous possédez déjà le même profil (par exemple une version plus ancienne), vous pouvez choisir de le **Remplacer** ou de **Conserver les deux**. Si vous remplacez le profil chargé, la version importée est chargée immédiatement.
- Les profils créés avec une version plus récente de FancyMenu affichent un avertissement, car certaines de leurs parties pourraient ne pas fonctionner.

## Ajouter des dossiers de configuration

Certaines configurations sont fournies sous la forme d'un simple dossier `fancymenu` plutôt que d'un fichier `.fmp`. Pour ajouter un tel dossier en tant que profil, renommez-le avec le nom de profil souhaité, déplacez-le dans `<game-directory>/config/fancymenu/profiles/` (créez le dossier `profiles` s'il n'existe pas encore), puis ouvrez la fenêtre des profils. FancyMenu l'ajoute automatiquement à vos profils.

# Supprimer des profils

Sélectionnez un profil et cliquez sur **Supprimer**. La suppression est irréversible : exportez donc d'abord le profil si vous souhaitez conserver une sauvegarde.

Le profil chargé ne peut pas être supprimé. Chargez d'abord un autre profil.

# Emplacement de stockage des profils

- Le profil chargé correspond au contenu de `<game-directory>/config/fancymenu/`, comme pour toute configuration FancyMenu.
- Tous les autres profils sont stockés dans `<game-directory>/config/fancymenu/profiles/`. Cliquez sur **Ouvrir le dossier** pour ouvrir le dossier d'un profil.

`<game-directory>` est le dossier de l'instance active, qui peut être différent de `.minecraft`. L'état d'exécution que FancyMenu conserve en dehors de `config/fancymenu/` ne fait pas partie des profils. Consultez [Emplacements de stockage des données](./data-storage-locations#persistent-runtime-state).
