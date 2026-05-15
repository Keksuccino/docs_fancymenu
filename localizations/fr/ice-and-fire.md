---
title: Menu principal Ice & Fire
description: Comment désactiver le menu principal personnalisé d’Ice and Fire.
---

Pour désactiver l’écran titre personnalisé dans le mod Ice and Fire, vous devez modifier sa configuration. Voici comment procéder :

## 1. Localiser le fichier de configuration
- **Nom du fichier :** Le paramètre se trouve dans le fichier nommé **`iceandfire-client.toml`**.
- **Emplacement du dossier :** Ce fichier se trouve généralement dans votre dossier **`.minecraft/config`** (ou dans le répertoire de configuration équivalent si vous utilisez un launcher personnalisé ou un modpack).

## 2. Modifier le fichier de configuration
- **Ouvrir le fichier :** Utilisez n’importe quel éditeur de texte brut (comme le Bloc-notes sous Windows ou TextEdit sur macOS) pour ouvrir `iceandfire-client.toml`.
- **Trouver le paramètre :** Faites défiler le fichier jusqu’à trouver une option liée au menu principal personnalisé. Elle peut être commentée et ressembler à ceci :
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Changer la valeur :** Définissez cette option sur **false** en modifiant la ligne comme suit :
  ```toml
  B:"Custom main menu"=false
  ```
  Cette modification indique au mod de ne plus afficher son menu principal personnalisé (souvent avec le dragon ou d’autres visuels thématiques).

## 3. Enregistrer et redémarrer
- **Enregistrer le fichier :** Après avoir effectué la modification, enregistrez le fichier.
- **Redémarrer Minecraft :** Fermez puis relancez Minecraft pour que les changements prennent effet. Au chargement du jeu, le menu principal par défaut devrait maintenant s’afficher à la place de celui du mod.

## Conseils supplémentaires
- **Vérifiez que vous modifiez le bon fichier :** Il peut exister un autre fichier de configuration commun, alors assurez-vous de modifier bien **`iceandfire-client.toml`** (la configuration spécifique au client, et non la configuration commune).
- **Faites une sauvegarde au préalable :** Il est toujours recommandé de faire une copie de sauvegarde du fichier de configuration original avant toute modification.
- **Modpacks :** Si vous utilisez un modpack, le fichier de configuration peut se trouver dans l’arborescence du dossier du pack, mais le principe reste le même.

Cette méthode a été confirmée par des utilisateurs de la communauté — par exemple, plusieurs utilisateurs sur les forums Feed The Beast ont indiqué avoir trouvé puis modifié l’option `"Custom main menu"` dans **`iceandfire-client.toml`**, ce qui a résolu leur problème. (Voir la discussion où un utilisateur a indiqué : « définissez la config d’Ice and Fire pour ne pas l’afficher dans iceandfire-client.toml » et précisé que le fichier se trouve dans le dossier config.) citeturn0search1

En suivant ces étapes, vous devriez désactiver le menu principal personnalisé fourni par le mod afin de pouvoir utiliser l’arrière-plan de menu principal de votre pack de textures.
