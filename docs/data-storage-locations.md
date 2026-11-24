---
title: Data Storage Locations
description: Where FancyMenu saves layouts, assets, settings and everything else, and which files belong to profiles.
---

# Data Storage Locations

FancyMenu saves everything in two folders of your game directory. That's the instance folder of your launcher, which can be a different one than `.minecraft`.

- `config/fancymenu/` holds your setup: layouts, assets, variables, settings and more. It's the loaded [profile](/profiles), so modpacks ship this folder.
- `fancymenu_data/` holds data of this game instance, like Dragger positions and downloads. It stays the same for all profiles.

**menu bar -> Tools -> Open FancyMenu Directory** opens `config/fancymenu/`.

Most files and folders only show up once you use their feature. Close the game before you change or delete files in them.

> [!TIP]
> To share these folders between instances, you can move them somewhere else and leave a symbolic link (a junction on Windows) in their place.

# Your Setup

Everything in `<game-directory>/config/fancymenu/`. It all belongs to the loaded [profile](/profiles).

| What | Where |
| --- | --- |
| Layouts, as `.txt` files, also in subfolders | `customization/` |
| [Local assets](/resources#local-resources), like images and sounds | `assets/` |
| FancyMenu's settings | `options.txt` |
| Screens with **Current Screen Customization** turned on | `customizablemenus.txt` |
| [Custom GUIs](/custom-guis), and the screens they replace | `custom_gui_screens.txt` |
| [Variables](/variables) | `user_variables.db` |
| [Listeners](/listeners) | `listener_instances.txt` |
| [Schedulers](/schedulers) | `scheduler_instances.txt` |
| [Panoramas](/panoramas) | `panoramas/` |
| [Slideshows](/slideshows) | `slideshows/` |
| [Custom localizations](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Themes of FancyMenu's own UI (**menu bar -> Customization -> Settings -> FancyMenu's UI -> UI Theme**) | `ui_themes/` |
| States of [Checkbox elements](/elements#checkbox) that don't use a variable | `checkbox_states.json` |
| Volume and pause state that actions gave [Video elements](/video) | `video_element_controller_metas.json` |
| Volume that actions gave [Audio elements](/elements#audio) | `audio_element_controller_metas.json` |
| On and off state that actions gave [Element Animators](/element-animator) | `animation_controller_states.json` |
| Screens with **Expose Scroll Area Content Of Current Screen** turned on | `normalized_scroll_screens.json` |
| [FM Data](/fm-data) server listeners | `fmdata_server_listeners.json` |
| [FM Data](/fm-data) welcome data | `fmdata_welcome_data.json` |
| Position, size and visibility of the layout editor's widgets | `layout_editor/widgets/` |
| Name, icon and details of the loaded profile | `profile.json` and `profile_icon.png` |
| All other [profiles](/profiles#where-profiles-are-stored) | `profiles/` |
| Which updates of old files FancyMenu did already | `legacy_checklist.txt` |

`customizablemenus.txt` lists screens by their Java class name. Short [screen identifiers](/screen-identifiers) like `title_screen` get skipped in it.

On a dedicated server, FancyMenu only uses the two [FM Data](/fm-data) files, in the `config/fancymenu/` folder of the server.

# Instance Data

Everything in `<game-directory>/fancymenu_data/`. It's not part of profiles, so it stays when you switch them.

| What | Where |
| --- | --- |
| Positions of [Dragger elements](/dragger) | `dragger_metas.json` |
| The last world or server, for the action **Enter/Join Last World/Server** and the placeholder **Last World or Server** | `last_world.fmdata` |
| Screenshots of [Seamless World Loading](/seamless-world-loading) | `seamless_world_loading/` |
| Saves of [Buddy](/decoration-overlays#buddy), two files per Buddy overlay | `buddy/` |
| Files of [Export for AI](/export-for-ai) | `ai_exports/` |
| Your favorite actions in the action chooser | `action_favorites.json` |
| The volume of audio and video previews in file choosers | `browser_audio_settings.json` and `browser_video_settings.json` |
| The frame a [video background](/video) shows while it's paused | `video_thumbnails/` |
| FFmpeg, which FancyMenu downloads for the [AFMA Creator](/animations#fma-and-afma) | `ffmpeg_cache/` |
| A note that FancyMenu set the **Default GUI Scale** already | `default_scale_set.fm` |
| Temporary files, deleted at every game start | `fancymenu_temp/` |

- FancyMenu sets the **Default GUI Scale** only once. Delete `default_scale_set.fm` to make it set the scale again at the next start.
- Seamless World Loading screenshots show anything that was on screen in the world. Delete them while the game is closed if you don't want to keep them.

# Files of Older Versions

Older FancyMenu versions saved some files in other places. FancyMenu takes them over at the next game start:

- `checkbox_states.json` and `normalized_scroll_screens.json` from the game directory itself into `config/fancymenu/`.
- `dragger_metas.json` from `config/fancymenu/` into `fancymenu_data/`.
