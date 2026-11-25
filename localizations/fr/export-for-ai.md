---
title: Exporter pour l’IA
description: >-
  Transformez des parties de votre configuration FancyMenu en texte pour les
  assistants IA comme Alice, afin qu’ils puissent vous aider plus rapidement.
sourceBlobSha: 37ce2fdd6cf8d770ca3f6f31528ac6076fe46922
---
# Exporter pour l’IA

**Exporter pour l’IA** transforme une partie de votre configuration FancyMenu en texte conçu pour les assistants IA, comme Alice, le bot d’aide du [Discord FancyMenu](https://discord.gg/rhayah27GC). Collez-le dans votre conversation : l’IA voit exactement comment les choses sont configurées, au lieu de devoir le deviner.

<img width="800" alt="Une publication d’assistance sur Discord où Alice demande un export, y trouve le problème et aide le joueur à corriger son bouton" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/export_for_ai_chat.gif?raw=true">

# Pourquoi cette fonction existe

Une capture d’écran montre l’apparence d’un élément, mais pas sa configuration. Saisir manuellement un script d’action ou une condition prend du temps, et le détail important se perd souvent en chemin.

Un export contient tout ce dont l’IA a besoin :

- Chaque paramètre, action, condition et valeur de l’élément exporté.
- Les versions de FancyMenu, Minecraft, du chargeur de mods, de Java et de votre système.
- De brèves explications sur le fonctionnement de FancyMenu, pour que l’IA l’interprète correctement.

Les exports sont toujours en anglais, quelle que soit la langue dans laquelle vous jouez. Le nom de votre compte dans les chemins de fichiers est remplacé par `<user>`, afin que vous puissiez partager les exports dans des salons publics.

# Quand l’utiliser

- Quelque chose ne fonctionne pas comme prévu, par exemple un bouton qui ne fait rien ou un élément qui ne s’affiche jamais.
- FancyMenu affiche une erreur ou un avertissement.
- Vous souhaitez de l’aide pour créer quelque chose, comme un script d’action, une condition ou un menu complet.
- Vous voulez savoir ce qui est possible dans votre jeu. **Tout ce que FancyMenu peut faire** répertorie tous les éléments, arrière-plans, actions, conditions, espaces réservés et écouteurs disponibles, y compris ceux des extensions.

N’exportez que les éléments liés à votre question, comme le bouton qui ne fonctionne pas. Les exports plus petits aident l’IA à rester concentrée. Expliquez-lui ensuite ce à quoi vous vous attendiez et ce qui s’est réellement passé.

# Comment exporter

Chacune des options ci-dessous ouvre un petit menu :

- **Copier dans le presse-papiers** copie l’export pour que vous puissiez le coller dans votre conversation avec `Ctrl + V` (`Cmd + V` sur macOS).
- **Enregistrer dans un fichier** l’enregistre en tant que fichier Markdown dans `<game-directory>/fancymenu_data/ai_exports/` et ouvre ce dossier, afin que vous puissiez faire glisser le fichier dans votre conversation. Utilisez cette option pour les exports trop volumineux pour tenir dans un message.

Les exports effectués depuis l’éditeur de mise en page, ainsi que depuis les fenêtres des écouteurs et des planificateurs, incluent les modifications que vous n’avez pas encore enregistrées.

# Où exporter

## Barre de menus

| Contenu exporté | Emplacement |
|---|---|
| L’écran actuel, avec ses widgets et les actions de FancyMenu sur cet écran | **barre de menus -> Personnalisation -> Exporter l’écran actuel pour l’IA** |
| Une mise en page | **barre de menus -> Personnalisation -> Mises en page**, sélectionnez la mise en page, puis **Exporter la mise en page pour l’IA** |
| Votre jeu, votre matériel et vos mods, ainsi que les fonctionnalités utilisables par FancyMenu, comme la prise en charge de la vidéo et du navigateur | **barre de menus -> Aide -> Exporter pour l’IA -> Informations système** |
| Tous les paramètres de FancyMenu, y compris les [personnalisations globales](/global-customizations) | **barre de menus -> Aide -> Exporter pour l’IA -> Paramètres de FancyMenu** |
| Toutes les [variables](/variables) | **barre de menus -> Aide -> Exporter pour l’IA -> Toutes les variables** |
| Tous les [écouteurs](/listeners) | **barre de menus -> Aide -> Exporter pour l’IA -> Tous les écouteurs** |
| Tous les [planificateurs](/schedulers) | **barre de menus -> Aide -> Exporter pour l’IA -> Tous les planificateurs** |
| Toutes les [interfaces personnalisées](/custom-guis) | **barre de menus -> Aide -> Exporter pour l’IA -> Interfaces personnalisées** |
| Tous les [profils](/profiles) | **barre de menus -> Aide -> Exporter pour l’IA -> Profils** |
| Tous les éléments, arrière-plans, actions, conditions, espaces réservés et écouteurs de votre jeu | **barre de menus -> Aide -> Exporter pour l’IA -> Tout ce que FancyMenu peut faire** |

## Éditeur de mise en page

| Contenu exporté | Emplacement |
|---|---|
| La mise en page que vous modifiez | **Mise en page -> Exporter la mise en page pour l’IA** dans la barre de menus de l’éditeur |
| Une autre mise en page de l’écran | **Mise en page -> Ouvrir** dans la barre de menus de l’éditeur, sélectionnez la mise en page, puis **Exporter la mise en page pour l’IA** |
| Un élément | Faites un clic droit sur l’élément, puis sélectionnez **Exporter pour l’IA** |
| Tous les éléments sélectionnés | **Modifier -> Exporter les éléments sélectionnés pour l’IA** dans la barre de menus de l’éditeur |
| Un [arrière-plan de menu](/menu-backgrounds) | Faites un clic droit sur l’arrière-plan de l’éditeur, puis sélectionnez **Arrière-plans de menu**, choisissez l’arrière-plan, puis **Exporter pour l’IA** |
| Une [superposition décorative](/decoration-overlays) | Faites un clic droit sur l’arrière-plan de l’éditeur, puis sélectionnez **Superpositions décoratives**, choisissez la superposition, puis **Exporter pour l’IA** |

## Éditeurs et fenêtres

| Contenu exporté | Emplacement |
|---|---|
| Un [script d’action](/action-scripts) | Faites un clic droit dans l’éditeur de scripts d’action, puis sélectionnez **Exporter le script d’action pour l’IA** |
| Des [conditions](/conditions) | Faites un clic droit dans la fenêtre **Gérer les conditions**, puis sélectionnez **Exporter les conditions pour l’IA** |
| Un texte, comme le contenu d’un élément Texte | Faites un clic droit dans l’éditeur de texte, puis sélectionnez **Exporter le texte pour l’IA** |
| Une variable ou toutes les variables | Ouvrez **barre de menus -> Personnalisation -> Gérer les variables**, faites un clic droit, puis sélectionnez **Exporter la variable pour l’IA** ou **Exporter toutes les variables pour l’IA** |
| Un écouteur ou tous les écouteurs | Ouvrez **barre de menus -> Personnalisation -> Gérer les écouteurs**, cliquez sur **Exporter pour l’IA**, puis sélectionnez **Écouteur sélectionné** ou **Tous les écouteurs** |
| Un planificateur ou tous les planificateurs | Ouvrez **barre de menus -> Personnalisation -> Gérer les planificateurs**, cliquez sur **Exporter pour l’IA**, puis sélectionnez **Planificateur sélectionné** ou **Tous les planificateurs** |

## Erreurs et avertissements

Lorsque FancyMenu affiche une erreur ou un avertissement, cliquez sur **Exporter pour l’IA**, à côté de **OK**, pour exporter le message.

## Serveurs

La configuration [FMData](/fm-data) d’un serveur, avec ses écouteurs de serveur et ses données de bienvenue, peut être exportée à l’aide d’une commande. Le niveau d’autorisation 2 est requis, comme pour toutes les commandes `/fmdata`.

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

- `copy` vous envoie un message dans le chat. Cliquez dessus pour copier l’export. Dans la console du serveur, l’export complet s’affiche à la place.
- `file` enregistre l’export sur le serveur, dans `fancymenu_data/ai_exports/`. Utilisez cette option lorsque l’export est trop volumineux pour le chat.
