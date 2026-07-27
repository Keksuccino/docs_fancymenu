---
title: Chargement fluide du monde
description: >-
  Utilisez une vue récente d’un monde comme arrière-plan du prochain écran de
  chargement.
---

# Chargement fluide du monde

Le chargement fluide du monde utilise une vue récente d’un monde ou d’un serveur comme arrière-plan du prochain écran de chargement.

Activez-le via [**Personnalisation -> Personnalisations globales**](./global-customizations) -> **Chargement fluide du monde**.

# Fonctionnement

- FancyMenu capture périodiquement l’image actuelle pendant que vous êtes dans un monde ou un serveur suivi.
- La dernière capture est enregistrée lorsque vous quittez.
- Chaque monde et chaque serveur possède son propre nom de fichier PNG haché.
- FancyMenu précharge jusqu’à cinq captures récentes de mondes et cinq captures récentes de serveurs.
- Rien n’est affiché pour une cible tant que sa première capture n’a pas été enregistrée.

Les captures sont stockées dans :

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Les captures d’écran peuvent contenir tout ce qui est visible dans le monde au moment de la capture. Désactiver le Chargement fluide du monde arrête la capture et son utilisation, mais ne supprime pas les fichiers PNG existants. Supprimez les captures indésirables du dossier pendant que le jeu est fermé.
