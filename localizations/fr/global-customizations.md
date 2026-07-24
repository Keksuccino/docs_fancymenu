---
title: Personnalisations globales
description: Appliquez des ajustements globaux de FancyMenu qui affectent tous les écrans.
---
# Personnalisations globales

Les personnalisations globales appliquent des paramètres partagés d’interface et de démarrage sans modifier la mise en page de chaque écran. Elles fonctionnent même lorsque la personnalisation normale des écrans est désactivée.

Exemples courants :

- Utiliser un style de bouton et de curseur partagé pour tous les écrans.
- Remplacer globalement l’arrière-plan du menu, le panorama et la musique du menu.
- Appliquer globalement le comportement au démarrage/de fenêtre (échelle de l’interface, plein écran, titre/icône de fenêtre).
- Remplacer globalement les textures des boutons vanilla sans pack de ressources.
- Remplacer globalement la musique de menu vanilla sans pack de ressources.

# Où les trouver

Ouvrez la **barre de menu** de FancyMenu pendant que vous **n’êtes pas** dans l’éditeur de mise en page, puis **Personnalisation -> Personnalisations globales**.

# Ce que vous pouvez personnaliser

## Comportement global et démarrage

- [**Game Intro**](./game-intro) (une vidéo ou animation d’introduction jouée avant l’écran Titre)
- **Icônes de monde de l’écran Solo**
- **Icônes de serveur de l’écran Multijoueur**
- [**Chargement fluide du monde**](./seamless-world-loading) (utilise une capture récente du monde comme arrière-plan de l’écran de chargement)
- [**Icône de fenêtre personnalisée**](./window-customization#custom-icon)
- [**Titre de fenêtre personnalisé**](./window-customization#custom-title)
- **Échelle d’interface par défaut**
- **Forcer le plein écran au lancement**

## Apparence des boutons

- **Textures de boutons personnalisées** (états Normal/Surligné/Inactif, mode transparent, [découpage en neuf](./nine-slicing-and-tiling) + tailles des bordures)
- **Libellés des boutons** (soulignement au survol, couleur de base/de survol, échelle, ombre)

## Apparence des curseurs

- **Textures de curseurs personnalisées**
- **Texture d’arrière-plan du curseur** (texture, mode transparent, [découpage en neuf](./nine-slicing-and-tiling) + tailles des bordures)
- **Textures de poignée du curseur** (états Normal/Surligné/Inactif, [découpage en neuf](./nine-slicing-and-tiling) + tailles des bordures)
- **Libellés des curseurs** (soulignement au survol, couleur de base/de survol, échelle, ombre)

## Apparence et audio du menu

- [**Texture d’arrière-plan de menu personnalisée**](./menu-backgrounds)
- [**Panorama d’arrière-plan de menu personnalisé**](./panoramas)
- **Jouer la musique de menu vanilla** (activer/désactiver la lecture de la musique de menu vanilla)
- [**Pistes musicales de menu personnalisées**](./background-music)
- **Son de clic personnalisé pour boutons/curseurs**

# Pistes musicales de menu personnalisées

Utilisez **Pistes musicales de menu personnalisées** pour créer une liste de pistes aléatoire pour les menus.

> [!IMPORTANT]
> Les pistes de menu personnalisées globales ne sont jouées que lorsqu’aucun monde n’est chargé, par exemple sur l’écran Titre. Utilisez un élément [**Audio**](./elements#audio) pour l’audio de menu en jeu.

Les pistes configurées utilisent le canal sonore Music et remplacent la musique de menu vanilla dans les menus non liés au monde pris en charge.

- La première piste commence après environ cinq secondes.
- Les pistes suivantes commencent après un délai aléatoire d’environ une à trente secondes.
- Les pistes sont sélectionnées aléatoirement.
- Avec plusieurs pistes, la piste précédente n’est pas sélectionnée deux fois de suite.

Gérez la liste des pistes depuis **Pistes musicales de menu personnalisées** :

- Ouvrez **Pistes musicales de menu personnalisées** pour ouvrir **Gérer les pistes musicales du menu**.
- Utilisez **Ajouter une piste** pour ajouter des sources audio.
- Utilisez **Supprimer une piste** pour retirer une entrée.
- Utilisez **Effacer les pistes** pour supprimer toutes les entrées.
