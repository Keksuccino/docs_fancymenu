---
title: Ressources
description: >-
  Comment fonctionnent les ressources dans FancyMenu. Couvre les emplacements
  des ressources, les ressources locales et les ressources web.
---

# Ressources

Le système de ressources de FancyMenu vous permet d’utiliser des ressources provenant du propre chargeur de ressources de Minecraft (**packs de ressources**), des ressources **locales** (fichiers présents sur le système du client) et des sources **web** (fichiers stockés en ligne).

La quasi-totalité des entrées de ressources, qu’il s’agisse d’images, d’audio, de vidéo ou de texte, se configure via le sélecteur de ressources de FancyMenu. Il existe quelques exceptions, par exemple lors de la définition d’un chemin de source pour un placeholder ou une action, mais dans la plupart des cas, vous définissez les ressources via la même interface de sélection de ressources.

Lorsque vous définissez une entrée de ressource via l’interface du sélecteur de ressources, vous choisissez en fait une soi-disant « source de ressource » (c’est ainsi que FancyMenu les appelle), qui peut être un chemin, un lien ou un emplacement de ressource, selon le type de source.

FancyMenu 3.9.0 ajoute un navigateur de ressources Minecraft au sélecteur de ressources. Cela vous permet de parcourir les ressources chargées via des packs de ressources comme dans un dossier, au lieu de devoir saisir chaque emplacement de ressource manuellement.

# Ressources Minecraft (packs de ressources)

Minecraft utilise des « emplacements de ressources » pour « pointer » vers une ressource.

Les emplacements de ressources écrits sous forme de texte se composent de deux parties, séparées par un deux-points (`:`).
La première partie est le **namespace** et la seconde partie est le reste du **chemin vers la ressource**, y compris le nom de la ressource avec son extension de fichier.

Le **namespace** d’un emplacement de ressource correspond toujours simplement au **dossier/répertoire de premier niveau** du chemin complet vers la ressource.

Supposons donc que vous chargiez un pack de ressources contenant une ressource appelée `image.png`, stockée dans `/assets/custom_resources/images/image.png`.
Dans ce cas, le **namespace** de l’emplacement de ressource serait `custom_resources`, car `/assets/` est simplement l’endroit à partir duquel Minecraft charge toutes ses ressources ; `custom_resources` est donc le **dossier de premier niveau** de la ressource.
Cela signifie que `images/image.png` est le **reste du chemin** vers la ressource.

L’emplacement de ressource correct pour la ressource `image.png` serait donc :
`custom_resources:images/image.png`

> **Fait amusant** : Comme Minecraft stocke la plupart de ses ressources dans `/assets/minecraft/`, le **namespace** de la plupart des ressources Minecraft est `minecraft`.
{.is-info}

# Ressources locales

La manière la plus simple de charger des ressources consiste simplement à utiliser des fichiers locaux stockés sur le client (et, dans la plupart des cas, fournis avec les modpacks).

FancyMenu ne permet de charger que des ressources locales stockées dans `/config/fancymenu/assets/`, alors assurez-vous d’y stocker toutes vos ressources !

Cela facilite également beaucoup l’[inclusion de ressources locales dans vos modpacks](./modpacks), puisque la plupart des systèmes de modpacks (CurseForge, Modrinth, etc.) prennent en charge l’inclusion des dossiers de configuration du mod par défaut.

# Ressources web

Lorsque vous devez modifier des ressources de manière dynamique sans avoir à mettre à jour votre modpack, les ressources **web** sont la meilleure option.

Une ressource web est en fait simplement l’**URL** d’un fichier stocké sur un serveur, par exemple `https://example-domain.net/image.png`.

Veillez à toujours utiliser des **URLs DIRECTES**, c’est-à-dire des URLs qui se terminent par le **nom de fichier et l’extension** de la ressource, comme dans l’exemple ci-dessus.
L’utilisation d’URLs non directes nuit aux performances et a davantage de chances d’échouer.

# Placeholders dans les sources de ressources

Il est possible d’utiliser les placeholders de FancyMenu dans les sources de ressources, comme le chemin d’une source locale, l’URL d’une source web ou l’emplacement de ressource d’une ressource Minecraft.

Cela permet de mettre à jour des sources de manière dynamique, par exemple en changeant la source d’image d’un arrière-plan de menu lors de la définition d’une variable FancyMenu, afin d’afficher un arrière-plan différent selon la valeur de la variable.

Vous pouvez modifier la source manuellement en cliquant sur le bouton **Ouvrir dans l’éditeur** à droite du champ de saisie de la source de ressource.

> Gardez à l’esprit que cela ne concerne que les entrées de ressources utilisant l’interface normale du sélecteur de ressources. Il est possible que *certaines* entrées de ressources qui n’utilisent pas le sélecteur ne prennent **PAS** en charge les placeholders, ou ne se mettent pas à jour dynamiquement lorsque le placeholder change.
{.is-warning}
