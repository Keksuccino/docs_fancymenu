---
title: Menu principal Ice & Fire
description: Comment désactiver le menu principal personnalisé d’Ice and Fire.
---
# Menu principal Ice & Fire

Pour désactiver l’écran titre personnalisé dans le mod Ice and Fire, vous devez modifier sa configuration. Voici comment procéder :

## 1. Localiser le fichier de configuration
- **Nom du fichier :** Le paramètre se trouve dans le fichier nommé **`iceandfire-client.toml`**.
- **Emplacement du dossier :** Ce fichier se trouve généralement dans **`<game-directory>/config/`**, où `<game-directory>` est le répertoire d’instance/profil actif du lanceur.

## 2. Modifier le fichier de configuration
- **Ouvrir le fichier :** Utilisez n’importe quel éditeur de texte simple (comme le Bloc-notes sur Windows ou TextEdit sur macOS) pour ouvrir `iceandfire-client.toml`.
- **Trouver le paramètre :** Faites défiler le fichier jusqu’à trouver une option liée au menu principal personnalisé. Elle peut être commentée et ressembler à ceci :
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Modifier la valeur :** Réglez cette option sur **false** en changeant la ligne en :
  ```toml
  B:"Custom main menu"=false
  ```
  Cette modification indique au mod de ne pas afficher son menu principal personnalisé (souvent avec un dragon ou d’autres visuels thématiques).

## 3. Enregistrer et redémarrer
- **Enregistrer le fichier :** Après avoir effectué la modification, enregistrez le fichier.
- **Redémarrer Minecraft :** Fermez puis relancez Minecraft pour que les changements prennent effet. Au chargement du jeu, vous devriez maintenant voir le menu principal par défaut au lieu de celui fourni par le mod.

## Conseils supplémentaires
- **Vérifiez bien que vous modifiez le bon fichier :** Il peut exister un autre fichier de configuration commun, alors assurez-vous de modifier **`iceandfire-client.toml`** (la configuration spécifique au client, et non la configuration commune).
- **Faites une sauvegarde au préalable :** Il est toujours recommandé de faire une copie de sauvegarde du fichier de configuration d’origine avant de le modifier.
- **Modpacks :** Si vous utilisez un modpack, le fichier de configuration peut se trouver dans l’arborescence du dossier du pack, mais le principe reste le même.

En suivant ces étapes, vous devriez désactiver le menu principal personnalisé fourni par le mod afin de pouvoir utiliser l’arrière-plan de menu principal de votre pack de textures.
