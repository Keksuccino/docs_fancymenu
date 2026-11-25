---
title: Chargement fluide des mondes
description: Utilisez une vue récente d’un monde comme prochain arrière-plan de chargement.
sourceBlobSha: 2b8e960b11ea70fca33b317a7c14815ce5844e13
---

# Chargement fluide des mondes

Le chargement fluide des mondes utilise une vue récente d’un monde ou d’un serveur comme prochain arrière-plan d’écran de chargement.

Activez cette fonctionnalité dans [**Personnalisation -> Personnalisations globales**](/global-customizations) -> **Chargement fluide des mondes**.

# Fonctionnement

- FancyMenu capture périodiquement l’image actuelle lorsque vous vous trouvez dans un monde ou sur un serveur suivi.
- La capture la plus récente est enregistrée lorsque vous quittez.
- Chaque monde et chaque serveur possède son propre fichier PNG au nom haché.
- FancyMenu précharge jusqu’à cinq captures récentes de mondes et cinq captures récentes de serveurs.
- Rien ne s’affiche pour une destination tant que sa première capture n’a pas été enregistrée.

Les captures sont stockées dans :

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Les captures d’écran peuvent contenir tout ce qui est visible dans le monde au moment de la capture. Désactiver le chargement fluide des mondes arrête les captures et leur utilisation, mais ne supprime pas les fichiers PNG existants. Pour supprimer les captures inutiles, supprimez-les du répertoire lorsque le jeu est fermé.
