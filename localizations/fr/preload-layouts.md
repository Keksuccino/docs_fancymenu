---
title: Préchargement des ressources
description: >-
  Comment précharger des ressources afin qu'elles soient prêtes à l'emploi une
  fois le jeu terminé de charger.
---

# Préchargement des ressources

Le préchargement prépare certaines ressources avant qu'un menu en ait besoin. Utilisez-le pour les ressources qui, autrement, clignotent, affichent une première image noire ou apparaissent trop tard.

# Ajouter des ressources au préchargeur

Ouvrez **Personnalisation -> Préchargement des ressources**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

La liste accepte les ressources prises en charge : images, animations, audio, vidéo et texte provenant de fichiers locaux, d'URL web ou de packs de ressources. Elle ne précharge pas une page [Browser](./elements#browser) en direct.

Le préchargeur démarre pendant le lancement du jeu et lors des rechargements des ressources de Minecraft. Il attend que chaque entrée se termine ou échoue avant de continuer, avec une limite de deux minutes par entrée.

Les ressources chargées restent mises en cache jusqu'à ce que FancyMenu libère les ressources lors d'un rechargement ou de la fermeture du client. **Personnalisation -> Recharger FancyMenu** libère le cache mais n'exécute pas à nouveau le préchargeur.

Le préchargement augmente le temps de chargement ainsi que l'utilisation de la RAM/VRAM. Ajoutez uniquement les ressources qui doivent être prêtes immédiatement ; supprimez les entrées volumineuses si le client manque de mémoire.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Préchargement des diaporamas et panoramas

L'ajout d'un [diaporama](./slideshows) charge toutes ses images ainsi que son superposition optionnelle. L'ajout d'un [panorama](./panoramas) charge ses six faces ainsi que sa superposition optionnelle.

**Personnalisation -> Recharger FancyMenu** n'exécute pas le préchargeur. Utilisez un rechargement des ressources de Minecraft ou redémarrez le jeu après avoir modifié la liste de préchargement.
