---
title: Emplacements de stockage des données
description: >-
  Où FancyMenu enregistre les mises en page, les ressources, les paramètres et
  tout le reste, et quels fichiers appartiennent aux profils.
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# Emplacements de stockage des données

FancyMenu enregistre tout dans deux dossiers du répertoire de votre jeu. Il s'agit du dossier d'instance de votre launcher, qui peut être différent de `.minecraft`.

- `config/fancymenu/` contient votre configuration : mises en page, ressources, variables, paramètres et plus encore. Il s'agit du [profil](/profiles) chargé ; c'est pourquoi les modpacks incluent ce dossier.
- `fancymenu_data/` contient les données de cette instance de jeu, comme les positions de Dragger et les téléchargements. Ce dossier reste le même pour tous les profils.

**Barre de menus -> Outils -> Ouvrir le dossier FancyMenu** ouvre `config/fancymenu/`.

La plupart des fichiers et des dossiers n'apparaissent que lorsque vous utilisez la fonctionnalité correspondante. Fermez le jeu avant de modifier ou de supprimer des fichiers dans ces dossiers.

> [!TIP]
> Pour partager ces dossiers entre plusieurs instances, vous pouvez les déplacer ailleurs et créer à leur emplacement un lien symbolique (une jonction sous Windows).

# Votre configuration

Tout se trouve dans `<game-directory>/config/fancymenu/`. Tous ces éléments appartiennent au [profil](/profiles) chargé.

| Éléments | Emplacement |
| --- | --- |
| Mises en page, sous forme de fichiers `.txt`, y compris dans les sous-dossiers | `customization/` |
| [Ressources locales](/resources#local-resources), comme des images et des sons | `assets/` |
| Paramètres de FancyMenu | `options.txt` |
| Écrans pour lesquels **Personnalisation de l'écran actuel** est activée | `customizablemenus.txt` |
| [Interfaces graphiques personnalisées](/custom-guis) et écrans qu'elles remplacent | `custom_gui_screens.txt` |
| [Variables](/variables) | `user_variables.db` |
| [Écouteurs](/listeners) | `listener_instances.txt` |
| [Planificateurs](/schedulers) | `scheduler_instances.txt` |
| [Panoramas](/panoramas) | `panoramas/` |
| [Diaporamas](/slideshows) | `slideshows/` |
| [Fichiers de langue personnalisés](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Thèmes de l'interface de FancyMenu (**barre de menus -> Personnalisation -> Paramètres -> Interface de FancyMenu -> Thème de l'interface**) | `ui_themes/` |
| États des [éléments de case à cocher](/elements#checkbox) qui n'utilisent pas de variable | `checkbox_states.json` |
| Volume et état de pause définis par des actions pour les [éléments vidéo](/video) | `video_element_controller_metas.json` |
| Volume défini par des actions pour les [éléments audio](/elements#audio) | `audio_element_controller_metas.json` |
| État activé ou désactivé défini par des actions pour les [animateurs d'éléments](/element-animator) | `animation_controller_states.json` |
| Écrans pour lesquels **Exposer le contenu de la zone de défilement de l'écran actuel** est activé (voir [Personnaliser les écrans défilants](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| Écouteurs de serveur [FM Data](/fm-data) | `fmdata_server_listeners.json` |
| Données de bienvenue de [FM Data](/fm-data) | `fmdata_welcome_data.json` |
| Position, taille et visibilité des widgets de l'éditeur de mises en page | `layout_editor/widgets/` |
| Nom, icône et détails du profil chargé | `profile.json` et `profile_icon.png` |
| Tous les autres [profils](/profiles#where-profiles-are-stored) | `profiles/` |
| Mises à jour des anciens fichiers déjà effectuées par FancyMenu | `legacy_checklist.txt` |

`customizablemenus.txt` répertorie les écrans par nom de classe Java. Les [identifiants d'écran](/screen-identifiers) courts, comme `title_screen`, n'y figurent pas.

Sur un serveur dédié, FancyMenu utilise uniquement les deux fichiers [FM Data](/fm-data), dans le dossier `config/fancymenu/` du serveur.

# Données de l'instance

Tout se trouve dans `<game-directory>/fancymenu_data/`. Ces données ne font pas partie des profils et sont donc conservées lorsque vous changez de profil.

| Éléments | Emplacement |
| --- | --- |
| Positions des [éléments Dragger](/dragger) | `dragger_metas.json` |
| Dernier monde ou serveur, utilisé par l'action **Entrer/Rejoindre le dernier monde/serveur** et le paramètre fictif **Dernier monde ou serveur** | `last_world.fmdata` |
| Captures d'écran du [chargement transparent des mondes](/seamless-world-loading) | `seamless_world_loading/` |
| Sauvegardes de [Buddy](/decoration-overlays#buddy), deux fichiers par superposition Buddy | `buddy/` |
| Fichiers de l'[export pour l'IA](/export-for-ai) | `ai_exports/` |
| Vos actions favorites dans le sélecteur d'actions | `action_favorites.json` |
| Volume des aperçus audio et vidéo dans les sélecteurs de fichiers | `browser_audio_settings.json` et `browser_video_settings.json` |
| Image affichée par un [arrière-plan vidéo](/video) lorsqu'il est en pause | `video_thumbnails/` |
| FFmpeg, téléchargé par FancyMenu pour le [créateur AFMA](/animations#fma-and-afma) | `ffmpeg_cache/` |
| Indique que FancyMenu a déjà défini l'[**échelle de l'interface par défaut**](/global-customizations) | `default_scale_set.fm` |
| Fichiers temporaires, supprimés à chaque lancement du jeu | `fancymenu_temp/` |

- FancyMenu ne définit l'**échelle de l'interface par défaut** qu'une seule fois. Supprimez `default_scale_set.fm` pour qu'elle soit de nouveau définie au prochain lancement.
- Les captures d'écran du chargement transparent des mondes montrent tout ce qui était affiché à l'écran dans le monde. Supprimez-les lorsque le jeu est fermé si vous ne souhaitez pas les conserver.

# Fichiers des anciennes versions

Les anciennes versions de FancyMenu enregistraient certains fichiers à d'autres emplacements. FancyMenu les récupère au prochain lancement du jeu :

- `checkbox_states.json` et `normalized_scroll_screens.json` sont déplacés du répertoire du jeu lui-même vers `config/fancymenu/`.
- `dragger_metas.json` est déplacé de `config/fancymenu/` vers `fancymenu_data/`.
