---
title: Précharger les ressources
description: >-
  Comment précharger des ressources pour qu’elles soient prêtes à l’emploi une
  fois le chargement du jeu terminé.
sourceBlobSha: 8eca400e05987468c1fd0dc29faa5267083e38d0
---

# Précharger les ressources

Le préchargement prépare certaines ressources avant qu’un menu en ait besoin. Utilisez-le pour les ressources qui, autrement, clignotent, affichent une première image noire ou se lancent en retard.

# Ajouter des ressources au préchargeur

Ouvrez **Personnalisation -> Précharger les ressources**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

La liste accepte les ressources image, animation, audio, vidéo et texte compatibles provenant de fichiers locaux, d’URL Web ou de packs de ressources. Elle ne précharge pas une page [Navigateur](/elements#browser) en direct.

Le préchargeur démarre au lancement du jeu et lors du rechargement des ressources de Minecraft. Il attend que chaque entrée soit chargée ou qu’une erreur survienne avant de passer à la suivante, avec une limite de deux minutes par entrée.

Les ressources chargées restent en cache jusqu’à ce que FancyMenu les libère lors d’un rechargement ou de la fermeture du client. **Personnalisation -> Recharger FancyMenu** libère le cache, mais ne relance pas le préchargeur.

Le préchargement augmente le temps de chargement et l’utilisation de la RAM et de la VRAM. N’ajoutez que les ressources qui doivent être prêtes immédiatement ; supprimez les entrées volumineuses si le client manque de mémoire.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Précharger des diaporamas et des panoramas

L’ajout d’un [diaporama](/slideshows) charge toutes ses images ainsi que sa superposition facultative. L’ajout d’un [panorama](/panoramas) charge ses six faces ainsi que sa superposition facultative.

**Personnalisation -> Recharger FancyMenu** ne lance pas le préchargeur. Après avoir modifié la liste de préchargement, rechargez les ressources de Minecraft ou redémarrez le jeu.
