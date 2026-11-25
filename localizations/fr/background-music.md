---
title: Musique de fond des menus
description: Personnalisez la musique diffusée dans les menus.
sourceBlobSha: 46d219f5573b915991f23082cfbc42e6ed11d132
---

# Musique de fond des menus

FancyMenu peut désactiver la musique des menus de Minecraft, diffuser une liste globale de pistes ou utiliser des [éléments Audio](/elements#audio) pour définir une musique propre à chaque mise en page.

# Musique globale des menus

Ouvrez [**Personnalisations globales**](/global-customizations) via **Personnalisation -> Personnalisations globales**, en dehors de l’éditeur de mise en page.

Utilisez les paramètres suivants :

- **Lire la musique des menus de Minecraft** active ou désactive globalement la musique des menus de Minecraft.
- **Pistes musicales personnalisées des menus** permet de gérer la liste globale de pistes de remplacement.

> [!IMPORTANT]
> Les pistes personnalisées globales ne sont diffusées que lorsqu’aucun monde n’est chargé, par exemple sur l’écran titre. Pour diffuser de la musique dans les menus en jeu, utilisez un élément [**Audio**](/elements#audio).

Les pistes globales utilisent le canal sonore Musique. La première piste démarre après environ cinq secondes ; les suivantes sont diffusées après un délai aléatoire d’environ une à trente secondes. La sélection est aléatoire et évite de répéter immédiatement la piste précédente si plusieurs pistes sont configurées.

# Contrôle de la musique par écran

Ajoutez un élément [**Contrôleur musical**](/elements#music-controller) à une mise en page pour contrôler la musique de Minecraft sur cet écran :

1. Faites un clic droit sur l’arrière-plan de l’éditeur.
2. Sélectionnez **Nouvel élément -> Contrôleur musical**.
3. Configurez séparément la musique des menus et celle des mondes.

Cet élément prend en charge les [conditions de chargement](/conditions).

Désactiver la musique des menus avec un contrôleur musical empêche également la diffusion de la liste globale de pistes personnalisées sur cet écran.

# Musique personnalisée avec des éléments Audio

Utilisez un élément [**Audio**](/elements#audio) si vous avez besoin :

- D’une musique différente selon les écrans.
- De musique sur les écrans en jeu.
- De conditions de mise en page, de listes de lecture ordonnées, de paramètres de lecture aléatoire, de réglages du volume ou du contrôle des canaux.

Placez un [élément Audio](/elements#audio) dans une [mise en page universelle](/universal-layouts) pour conserver le même lecteur actif sur les écrans compatibles qui chargent cette mise en page. La personnalisation de l’écran doit être activée sur chaque écran ordinaire où la mise en page universelle doit s’appliquer.
