---
title: Musique de fond du menu
description: Personnalisez la musique jouée dans les menus.
---

# Musique de fond du menu

FancyMenu peut désactiver la musique des menus Vanilla, lire une liste de pistes globale, ou utiliser des [éléments Audio](./elements#audio) pour une musique spécifique à la disposition.

# Musique globale des menus

Ouvrez [**Personnalisations globales**](./global-customizations) via **Personnalisation -> Personnalisations globales** en dehors de l’éditeur de disposition.

Utilisez ces paramètres :

- **Lire la musique de menu Vanilla** active ou désactive globalement la musique de menu Vanilla.
- **Pistes de musique de menu personnalisées** gère la liste globale des pistes de remplacement.

> [!IMPORTANT]
> Les pistes de menu personnalisées globales ne jouent que lorsqu’aucun monde n’est chargé, par exemple sur l’écran titre. Utilisez un élément [**Audio**](./elements#audio) pour l’audio de menu en jeu.

Les pistes globales utilisent le canal sonore Music. La première piste démarre après environ cinq secondes ; les pistes suivantes utilisent un délai aléatoire d’environ une à trente secondes. La sélection est aléatoire et évite de répéter immédiatement la piste précédente lorsqu’il y a plus d’une piste configurée.

# Contrôle de la musique par écran

Ajoutez un élément [**Music Controller**](./elements#music-controller) à une disposition pour contrôler la musique Vanilla pour cet écran :

1. Faites un clic droit sur l’arrière-plan de l’éditeur.
2. Sélectionnez **Nouvel élément -> Music Controller**.
3. Configurez séparément la musique des menus et la musique du monde.

L’élément prend en charge les [conditions de chargement](./conditions).

Désactiver la musique de menu avec un Music Controller empêche également la lecture de la liste globale de pistes de menu personnalisées sur cet écran.

# Musique personnalisée avec des éléments Audio

Utilisez un élément [**Audio**](./elements#audio) lorsque vous avez besoin de :

- Musique différente selon les écrans.
- Musique dans les écrans en jeu.
- Conditions de disposition, listes de lecture ordonnées, réglages de lecture aléatoire, volume ou contrôle du canal.

Placez un élément [Audio](./elements#audio) dans une [Disposition universelle](./universal-layouts) pour conserver le même lecteur actif sur les écrans pris en charge qui chargent cette disposition. La personnalisation d’écran doit être activée sur chaque écran ordinaire où la disposition universelle doit s’appliquer.
