---
title: Localiser des mises en page
description: Comment localiser le contenu des mises en page.
---

# Localiser des mises en page

FancyMenu vous permet de localiser du texte et même des éléments ou des mises en page entiers !

# Contenu textuel

FancyMenu vous permet d’ajouter vos propres localisations au jeu.
Elles peuvent ensuite être utilisées avec l’espace réservé **Localize Text** pour localiser le texte dans la langue actuelle du jeu.

## Utiliser les clés de localisation vanille de Minecraft

Avant de créer des localisations personnalisées, vous voudrez peut-être utiliser les clés de localisation Minecraft existantes. Cela fait gagner du temps et garantit une cohérence avec le texte vanille de Minecraft.

### Trouver les clés de localisation vanille

Le moyen le plus simple de trouver les clés de localisation de Minecraft est de parcourir en ligne les fichiers de ressources du jeu :

1. **Visitez MCAsset.cloud :**  
   Rendez-vous sur [https://mcasset.cloud/](https://mcasset.cloud/) - ce site vous permet de parcourir les ressources de Minecraft sans les extraire du jeu.

2. **Accédez aux fichiers de langue :**  
   - Sélectionnez votre version de Minecraft dans la liste déroulante
   - Accédez à : `assets` → `minecraft` → `lang`
   - Ouvrez `en_us.json` pour voir toutes les localisations en anglais

3. **Trouvez la clé dont vous avez besoin :**  
   - Utilisez la fonction de recherche de votre navigateur (Ctrl+F ou Cmd+F) pour trouver un texte précis
   - Le format est `"key": "text"` - la première partie entre guillemets avant les deux-points (`:`) est la clé
   - Par exemple : `"menu.singleplayer": "Singleplayer"` - la clé est `menu.singleplayer`

### Utiliser les clés de localisation des mods

Si d’autres mods sont installés, vous pouvez aussi utiliser leurs clés de localisation :

1. Consultez la documentation du mod pour connaître les clés disponibles
2. Parcourez les fichiers de langue du mod s’ils sont open source

## Fichiers de localisation personnalisés

Les fichiers de localisation sont des fichiers texte contenant tout le contenu textuel devant être disponible dans plusieurs langues. Chaque texte traduisible possède une clé unique, afin que Minecraft puisse trouver le bon texte traduisible dans les fichiers de localisation.

- **Fichier par défaut (en_us.json) :**  
  Anglais (États-Unis). Ce fichier est utilisé lorsqu’aucune autre langue n’est choisie. Il sert de fichier de langue de secours.

- **Autres fichiers de langue :**  
  Par exemple, vous pouvez créer un fichier allemand appelé `de_de.json` pour les joueurs qui utilisent l’allemand.

### Comment créer un fichier de localisation personnalisé

Vous avez toujours besoin d’un fichier `en_us.json` ! Sans lui, le jeu n’a aucun repli lorsque quelque chose se passe mal ou lorsqu’une langue non prise en charge est sélectionnée.

1. **Ouvrez un éditeur de texte :**  
   Utilisez le Bloc-notes (Windows), TextEdit (Mac) ou tout éditeur de texte simple.

2. **Écrivez votre code JSON :**  
   Créez votre fichier avec vos clés personnalisées. Une clé est un nom unique que Minecraft utilise pour trouver le texte. Par exemple :
   
   ```json
   {
     "modpack_name.custom.localization.key": "Votre texte personnalisé ici",
     "modpack_name.another.key": "Un autre message"
   }
   ```

3. **Enregistrez le fichier :**  
   Enregistrez le fichier sous le nom `en_us.json` pour le texte anglais par défaut.

Si vous voulez maintenant ajouter des versions traduites, comme l’allemand, copiez le contenu du fichier `en_us.json` vers le nouveau fichier et traduisez uniquement le texte réel, PAS les clés ! Les clés doivent rester identiques, afin que le jeu puisse toujours trouver le texte.

Pour l’allemand, vous enregistreriez alors le fichier sous le nom `de_de.json`. Pour les autres langues, veuillez consulter [cette page du wiki Minecraft](https://minecraft.wiki/w/Language) pour connaître le code de langue correct et nommer le fichier en conséquence. Recherchez le **« in-game locale code »** de votre langue.

## Créer un pack de ressources Minecraft pour MC 1.21.4

Maintenant que vos fichiers de localisation sont prêts, nous avons besoin d’un moyen de les charger dans Minecraft. Pour cela, nous allons utiliser un pack de ressources. Nous allons faire en sorte que le pack soit activé par défaut, et nous pouvons même le masquer si nous ne voulons pas que les utilisateurs du modpack le modifient.

Un **pack de ressources** est un fichier ZIP qui contient des fichiers modifiant l’apparence et le rendu du jeu.

### Étapes pour créer votre pack de ressources

1. **Créez un nouveau dossier :**  
   Créez un dossier nommé par exemple `my_custom_pack`, dans lequel vous ajouterez vos fichiers de localisation personnalisés.

2. **Créez le fichier du pack (`pack.mcmeta`) :**  
   À l’intérieur de votre dossier, créez un fichier appelé `pack.mcmeta` avec le contenu suivant :
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "Mon pack personnalisé avec localisations"
     }
   }
   ```
   
   *Remarque : `pack_format` 16 correspond à Minecraft 1.21.4.*

3. **Ajoutez vos fichiers de localisation :**  
   À l’intérieur du dossier de votre pack de ressources, créez la structure de dossiers suivante :
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   Placez votre `en_us.json` personnalisé (et tout autre fichier de langue comme `de_de.json`) dans le dossier `lang`.

4. **Compressez le pack de ressources :**  
   Une fois votre dossier prêt, **compressez tout le dossier en un fichier ZIP**. Nommez le fichier ZIP **my_custom_pack.zip**. C’est le nom d’exemple utilisé tout au long du guide.

## Où placer le pack de ressources

Placez votre fichier **my_custom_pack.zip** dans le dossier **Minecraft Resourcepacks**. Ce dossier se trouve généralement à l’emplacement suivant :

- **Windows :** `%appdata%\.minecraft\resourcepacks`
- **Mac :** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux :** `~/.minecraft/resourcepacks`

> Pour les modpacks, le dossier `resourcepacks` se trouve dans le répertoire d’instance de votre pack.
{.is-warning}

## Chargement automatique du pack avec "Resource Pack Overrides"

Le mod **Resource Pack Overrides** permet d’activer les packs de ressources par défaut.

### Étapes pour charger automatiquement votre pack

1. **Installez le mod :**  
   Téléchargez et installez le mod depuis [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) ou [Modrinth](https://modrinth.com/mod/resource-pack-overrides).

2. **Localisez le fichier de configuration :**  
   Trouvez le fichier à l’emplacement `.minecraft/config/resourcepackoverrides.json`.  
   *Si le fichier n’existe pas, créez-le manuellement.*

3. **Modifiez le fichier de configuration :**  
   Ouvrez le fichier et ajoutez votre pack de ressources à la liste `default_packs` en utilisant son nom de fichier :
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   Cela indique à Minecraft de charger automatiquement votre pack de ressources au démarrage du jeu.

   **Il est important d’ajouter le préfixe `file/` !**


*Remarque : les packs de ressources dans la liste sont appliqués dans l’ordre inverse. Cela signifie que le pack en haut de la liste apparaîtra en dessous des autres dans le menu des packs de ressources du jeu.*

## Masquer le pack de ressources dans l’écran de sélection

Vous pouvez masquer votre pack de ressources pour que les joueurs ne le voient pas dans l’écran de sélection des packs de ressources.

### Comment le masquer

1. **Modifiez à nouveau le fichier de configuration :**  
   Dans le même fichier `.minecraft/config/resourcepackoverrides.json`, ajoutez une surcharge pour votre pack :
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   Cette configuration masquera **my_custom_pack.zip** de l’écran de sélection tout en le chargeant automatiquement.

## Utiliser vos nouvelles clés de localisation avec FancyMenu

Maintenant que vos fichiers de localisation personnalisés sont chargés, vous pouvez utiliser vos nouvelles clés dans les mises en page FancyMenu.

1. **Modifiez un élément textuel :**  
   Ouvrez FancyMenu et choisissez un élément comme un bouton ou un élément de texte.

2. **Cliquez sur le bouton Placeholders :**  
   Cherchez le bouton Placeholders en haut à droite de l’éditeur de texte. (Si vous ne le voyez pas, il se peut que l’élément ne prenne pas en charge les placeholders.)

3. **Insérez l’espace réservé Localize Text :**  
   L’espace réservé Localize Text apparaît sous forme d’extrait JSON. Il ressemble à ceci :
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   Remplacez `localization.key` par votre propre clé personnalisée. Par exemple, si vous voulez utiliser votre clé du fichier de localisation, remplacez-la par :
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

Et voilà, c’est essentiellement tout ! L’espace réservé doit être remplacé par le contenu localisé réel lorsque vous ne l’éditez pas dans l’éditeur de texte.

Gardez à l’esprit que l’espace réservé localisera toujours le texte vers la langue actuelle du jeu.

# Contenu non textuel (images, etc.)

FancyMenu vous permet aussi de localiser des images et, en gros, n’importe quel élément que vous voulez.

Pour cela, vous devrez utiliser des **conditions de chargement**.
Plus précisément, la condition **Is Game Language**.

La condition **Is Game Language** permet d’afficher des éléments ou des mises en page uniquement si une langue de jeu spécifique est définie. Vous pouvez ainsi, par exemple, créer deux éléments Image contenant du texte et localiser cette image vers une version avec du texte japonais lorsque la langue est réglée sur le japonais, ou vers une version avec du texte anglais si la langue est réglée sur l’anglais.

Pour définir des conditions de chargement sur un **élément**, faites un clic droit dessus et cliquez sur **Loading Requirements**.

Pour définir des conditions de chargement sur des **mises en page entières**, faites un clic droit sur l’arrière-plan de l’éditeur de mise en page et cliquez sur **Loading Requirements [Layout-Wide]**.
