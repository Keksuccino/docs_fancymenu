---
title: Emplacements de stockage des données
description: >-
  Où FancyMenu stocke les mises en page, les ressources, la configuration et
  l’état persistant à l’exécution.
---

# Emplacements de stockage des données

`<game-directory>` désigne le dossier de l’instance Minecraft active, qui peut différer de `.minecraft`.

Les répertoires et fichiers ne sont généralement créés qu’après l’initialisation ou l’utilisation de la fonctionnalité correspondante. Fermez Minecraft avant de modifier manuellement les fichiers d’état générés, et conservez une sauvegarde lors d’une migration ou d’une réinitialisation des données.

# Mises en page, ressources et configuration

Certaines entrées sont des configurations ou des ressources créées par l’auteur ; d’autres sont des états que FancyMenu met à jour à l’exécution.

| Système / Fonctionnalité | Fichier ou répertoire |
| --- | --- |
| Écrans personnalisables | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [GUI personnalisées](./custom-guis) et règles de remplacement d’écran | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| Mises en page | `<game-directory>/config/fancymenu/customization/` |
| [Ressources locales](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [Fichiers de localisation personnalisés](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [Panoramas](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [Diaporamas](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [Variables FancyMenu](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| Métadonnées du contrôleur de l’[élément vidéo](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| Métadonnées du contrôleur de l’[élément audio](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| Serveurs écoutés par [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| Données de bienvenue [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| Instances d’[écouteurs](./listeners) et scripts d’action | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Planificateurs](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` est géré par le bouton bascule **Current Screen Customization** et stocke des identifiants concrets de classes d’écran. N’ajoutez pas d’identifiants [Universal Layout](./universal-layouts) ; FancyMenu les ignore lors du chargement du fichier.

Sur un serveur dédié, les deux fichiers FM Data sont relatifs à la racine du jeu de ce serveur. Les autres configurations et ressources appartenant au client se trouvent dans l’instance de chaque joueur.

# État persistant à l’exécution

FancyMenu conserve des données d’état supplémentaires générées, propres à l’instance, en dehors de `config/fancymenu/`. Incluez ces chemins dans une sauvegarde uniquement lorsque vous souhaitez conserver l’état utilisateur ou d’exécution associé ; il ne s’agit ni de définitions de mise en page ni de ressources स्रोत.

| Système / Fonctionnalité | Fichier ou répertoire |
| --- | --- |
| États non variables des [cases à cocher](./elements#checkbox) | `<game-directory>/checkbox_states.json` |
| Positions/métadonnées de l’élément [Dragger](./dragger) | `<game-directory>/fancymenu_data/dragger_metas.json` |
| Dernier état du monde | `<game-directory>/fancymenu_data/last_world.fmdata` |
| État du [chargement transparent du monde](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Sauvegardes du familier Buddy et de sa progression | `<game-directory>/fancymenu_data/buddy/` |
| Positions et visibilité des widgets de l’éditeur de mise en page | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| Marqueur d’initialisation de l’échelle GUI par défaut | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy conserve l’état du familier ainsi que l’état de progression/réussites dans des fichiers JSON séparés au sein de son répertoire. Chaque instance de superposition Buddy utilise sa propre paire de fichiers.

Les fichiers des widgets de l’éditeur de mise en page enregistrent pour chaque widget sa position, sa taille, sa visibilité, son état développé et son côté d’ancrage. Supprimer `default_scale_set.fm` amène FancyMenu à considérer, au lancement suivant, que l’échelle GUI par défaut configurée n’a pas encore été appliquée.
