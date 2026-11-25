---
title: Intro du jeu
description: >-
  Lancez une animation ou une vidéo à chaque démarrage du jeu, avant
  l’apparition de l’écran-titre.
sourceBlobSha: 2f40eb874b4aebaf4b32ffa2b8980310d71510b7
---

# Intro du jeu

L’intro du jeu lance une animation ou une vidéo au démarrage du jeu, juste après l’écran de chargement de Minecraft. À la fin, elle laisse place à l’écran-titre avec un fondu. Elle est conçue pour les modpacks : logo, intro de studio ou courte bande-annonce.

<img width="800" alt="L’intro de Skyhaven : la nuit fait place à l’aube au-dessus d’une île flottante et le logo apparaît lettre par lettre, puis l’intro laisse place à l’écran-titre, dont l’arrière-plan représente la même île" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

Les joueurs peuvent passer l’intro en appuyant sur n’importe quelle touche ou en cliquant. L’intro du jeu fait partie des [personnalisations globales](/global-customizations) : elle ne nécessite donc aucune disposition.

# Configurer l’intro

<img width="800" alt="Ouvrir Personnalisations globales puis Intro du jeu dans la barre de menus, choisir skyhaven_intro.apng avec Définir l’intro du jeu, la lancer avec Relancer l’intro du jeu et la passer avec la barre d’espace" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. Placez votre animation ou votre vidéo dans `<game-directory>/config/fancymenu/assets/`.
2. Ouvrez **barre de menus -> Personnalisation -> Personnalisations globales -> Intro du jeu**.
3. Cliquez sur **Définir l’intro du jeu**. Avec **Type de source** réglé sur **Locale**, cliquez sur **Choisir un fichier de ressource local**, sélectionnez votre fichier, puis cliquez sur **OK**.
4. Cliquez sur **Relancer l’intro du jeu** pour la visionner immédiatement.

Pour supprimer l’intro, placez le curseur sur **Définir l’intro du jeu** et cliquez sur **Rétablir les valeurs par défaut**.

## Animations et vidéos

- **Animations :** fichiers APNG ou GIF. Pour apprendre à en créer : [Animations](/animations).
- **Vidéos :** fichiers MP4. Elles nécessitent les mods Watermedia V3 et Watermedia Binaries V3. Consultez [Vidéos](/video#requirements). Sans ces mods, l’intro vidéo affiche uniquement une note rouge avec des liens de téléchargement pendant quelques secondes.
- Les fichiers de votre instance et des packs de ressources sont compatibles, contrairement aux liens Web. Consultez [Ressources](/resources).

L’intro remplit tout l’écran en conservant ses proportions : une partie de l’image sera donc coupée sur les écrans ayant d’autres proportions. La plupart des écrans sont au format 16:9 ; créez donc votre intro dans ce format, par exemple en 1920x1080. Les parties transparentes s’affichent en noir.

> [!TIP]
> Les joueurs voient l’intro à chaque démarrage du jeu : faites-la courte, environ 5 à 10 secondes.

## Exemple d’intro gratuit

L’intro de Skyhaven visible dans les GIF de cette page peut être utilisée gratuitement, pour vos tests comme dans vos modpacks :

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true) : l’intro, en 1280x720, d’une durée de 5,4 secondes. Elle est lue une seule fois.
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true) : la dernière scène sans le logo, en 1280x720. Définissez-la comme [arrière-plan image](/menu-backgrounds#image) d’une disposition d’écran-titre. L’intro laissera alors place à un menu assorti, comme dans le premier GIF.

# Paramètres

Tous les paramètres se trouvent dans **barre de menus -> Personnalisation -> Personnalisations globales -> Intro du jeu** :

| Paramètre | Fonction |
|---|---|
| **Définir l’intro du jeu** | L’animation ou la vidéo. |
| **Passage de l’intro du jeu** | Une pression sur n’importe quelle touche ou un clic permet de passer l’intro, et le message **Appuyez sur n’importe quelle touche pour passer** s’affiche en bas de l’écran. Si vous passez l’intro, elle se termine immédiatement, sans fondu. Si cette option est désactivée, l’intro est toujours lue jusqu’à la fin. |
| **Fondu de l’intro du jeu** | Fait apparaître l’écran-titre avec un fondu à la fin de l’intro. Si cette option est désactivée, l’écran-titre apparaît immédiatement. |
| **Ignorer les boucles de l’intro du jeu** | Termine l’intro après une seule lecture de l’animation, même si celle-ci est en boucle. Si cette option est désactivée, l’intro lit toutes les boucles de l’animation. Les vidéos ne sont toujours lues qu’une seule fois. |
| **Texte personnalisé pour passer l’intro** | Remplace **Appuyez sur n’importe quelle touche pour passer**, par exemple par `Appuyez sur n’importe quelle touche pour commencer votre aventure`. Une clé de traduction d’un pack de ressources, comme `skyhaven.intro.skip`, affiche le texte dans la langue du joueur. |
| **Volume de l’intro du jeu** | Règle le volume d’une intro vidéo, de 0 % à 100 %. |
| **Canal audio de l’intro du jeu** | Définit le canal audio des intros vidéo, par exemple Musique. Le volume de ce canal et le volume général définis dans les paramètres audio de Minecraft s’appliquent également. |
| **Relancer l’intro du jeu** | Lance immédiatement l’intro par-dessus l’écran actuellement affiché. |

Les options **Passage de l’intro du jeu**, **Fondu de l’intro du jeu** et **Ignorer les boucles de l’intro du jeu** sont activées par défaut.

> [!WARNING]
> Si **Passage de l’intro du jeu** et **Ignorer les boucles de l’intro du jeu** sont toutes deux désactivées, une animation qui tourne en boucle indéfiniment ne se termine jamais, et les joueurs ne peuvent pas accéder à l’écran-titre.

# Bon à savoir

- L’intro est lue une fois à chaque démarrage du jeu, avant le premier écran qui suit l’écran de chargement. Il s’agit normalement de l’écran-titre.
- Pour modifier l’écran de chargement de Minecraft qui s’affiche avant l’intro, consultez [Écran de chargement](/loading-screen).
- La source de l’intro peut contenir des [espaces réservés](/resources#placeholders-in-resource-sources).
- Les paramètres de l’intro du jeu sont enregistrés dans le fichier `options.txt` de FancyMenu et sont donc associés au [profil](/profiles) chargé. Les modpacks qui incluent `config/fancymenu/` sont fournis avec l’intro et son fichier dans `assets/`. Consultez [Modpacks](/modpacks).
