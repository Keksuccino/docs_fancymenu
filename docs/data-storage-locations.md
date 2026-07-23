---
title: Data Storage Locations
description: Where FancyMenu stores layouts, resources, configuration, and persistent runtime state.
---

# Data Storage Locations

This reference lists the files and directories used by FancyMenu. `<game_root>` means the root directory of the active Minecraft instance. Depending on the launcher and profile, that directory is not necessarily the default `.minecraft` directory.

Directories and files are usually created only after the related feature is initialized or used. Close Minecraft before manually editing generated state files, and keep a backup when migrating or resetting data.

# Layouts, Resources, and Configuration

These paths live in the instance's `config/fancymenu/` directory. Some are authored layout or feature configuration, while others are databases or metadata that FancyMenu updates at runtime.

| System / Feature | File or Directory |
| --- | --- |
| Customizable screens | `config/fancymenu/customizablemenus.txt` |
| Custom GUIs and screen-override rules | `config/fancymenu/custom_gui_screens.txt` |
| Layouts | `config/fancymenu/customization/` |
| Local assets | `config/fancymenu/assets/` |
| Panoramas | `config/fancymenu/panoramas/` |
| Slideshows | `config/fancymenu/slideshows/` |
| FancyMenu variables | `config/fancymenu/user_variables.db` |
| Video element controller metadata | `config/fancymenu/video_element_controller_metas.json` |
| Audio element controller metadata | `config/fancymenu/audio_element_controller_metas.json` |
| FM Data server listeners | `config/fancymenu/fmdata_server_listeners.json` |
| FM Data welcome data | `config/fancymenu/fmdata_welcome_data.json` |
| Schedulers | `config/fancymenu/scheduler_instances.txt` |

On a dedicated server, the two FM Data files are relative to that server's game root. Other client-owned configuration and resources belong in each player's instance.

# Persistent Runtime State

FancyMenu keeps additional generated, per-instance state outside `config/fancymenu/`. Include these paths in a backup only when you want to preserve the related user/runtime state; they are not layout definitions or source assets.

| System / Feature | File or Directory |
| --- | --- |
| Non-variable checkbox states | `<game_root>/checkbox_states.json` |
| Dragger element positions/metadata | `<game_root>/fancymenu_data/dragger_metas.json` |
| Last world state | `<game_root>/fancymenu_data/last_world.fmdata` |
| Seamless World Loading state | `<game_root>/fancymenu_data/seamless_world_loading/` |
| Buddy pet and leveling saves | `<game_root>/fancymenu_data/buddy/` |

Buddy keeps the pet state and leveling/achievement state in separate JSON files within its directory. Each Buddy overlay instance uses its own pair of files.
