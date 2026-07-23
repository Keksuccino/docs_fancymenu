---
title: Conditions (Requirements)
description: How to use loading requirements.
published: true
date: 2026-05-03T11:01:52.000Z
tags: loading requirements, loading requirement, requirement, requirements
editor: markdown
dateCreated: 2025-04-14T20:14:22.175Z
---

# Requirements

Requirements (called **Loading Requirements** in some menus) show or hide content based on conditions such as hover state, window size, or whether a world is loaded.

You can use them on [elements](./elements), whole layouts, and [action scripts](./action-scripts).

# Adding Requirements to Elements

To add requirements to an element, right-click it and select **Loading Requirements**.

Requirements are checked while the menu is open, so elements update when a condition changes.

# Layout-wide Requirements

You can also change the visibility of whole layouts by right-clicking the **editor background** and then clicking on **Loading Requirements [Layout-Wide]**.

When a layout-wide result changes, FancyMenu rebuilds the current screen and applies the layouts whose requirements now pass.

# Action Scripts

Requirements can also be used in action scripts.
You can add them in the action script editor screen and use them to execute specific actions only if the condition of the requirement is met.

# Combining Requirements

- Requirements outside groups use **AND**, so all of them must pass.
- Inside a group, choose **AND** or **OR**.
- Use **IF NOT** to invert one requirement.

These rules are the same for elements, layouts, and action scripts.

# Requirement Values

For requirements that need a value, use **Edit Requirement Value** and follow the description shown in the editor. Some fields support **TAB** completion.

If an imported requirement no longer works after changing FancyMenu or add-ons, edit it in the requirements screen and check `logs/latest.log` for errors.

The requirements editor supports a right-click context menu, keyboard navigation, search, undo/redo (`Ctrl/Command + Z` / `Ctrl/Command + Y`), and `Ctrl/Command + S` to save.

# Requirements in Detail

This section lists FancyMenu's built-in requirements.

## Is Element Hovered (`fancymenu_visibility_requirement_is_element_hovered`)

**Purpose:** Checks if a specific element is hovered by the mouse cursor.

**Value:** Required — [Element identifier](./element-identifiers) of the target element (e.g., `some_element_ID`).

## Is Element Focused (`is_element_focused`)

**Purpose:** Checks if a specific element currently has keyboard focus (for example, a text field or focused button).

**Value:** Required — Element ID of the target element (the same ID shown in the editor)

> [!NOTE]
> Focus and hover are different states. An element can keep its focused appearance after the pointer leaves it; clicking or keyboard navigation can give it focus.

## Is Any Element Hovered (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Purpose:** Checks visible/renderable elements in the current active customization layer, including elements contributed by stacked layouts.

**Value:** Not required

## Is Any Button Hovered (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Purpose:** Checks whether any visible/renderable vanilla or custom button in the current active customization layer is hovered, including buttons contributed by stacked layouts.

**Value:** Not required

## Is Layout Enabled (`fancymenu_visibility_requirement_is_layout_enabled`)

**Purpose:** Checks if a specific layout is currently enabled.

**Value:** Required — The name of the layout (e.g., `my_cool_main_menu_layout`)

## Is Scheduler Running (`fancymenu_visibility_requirement_is_scheduler_running`)

**Purpose:** Checks if a [scheduler](./schedulers) is currently running.

**Value:** Required — Scheduler ID (e.g., `my_scheduler`)

## Is GUI Scale (`fancymenu_loading_requirement_is_gui_scale`)

**Purpose:** Checks if the current GUI scale matches certain conditions.

**Value:** Required — Use a number for equality, `>` for greater than, or `<` for less than.

Multiple comma-separated conditions are combined with AND. For example, `>1,<4` passes only when the GUI scale is greater than `1` and smaller than `4`.

## Is Button Active (`fancymenu_visibility_requirement_is_button_active`)

**Purpose:** Checks if a specific button is active (clickable).

**Value:** Required — Element ID of the target button (e.g., "some_element_ID")

## Is Screen Title (`is_menu_title`)

**Purpose:** Checks if the screen's DISPLAY title matches a specific text or localization key. This will only check for the display name/title of the screen, like "Options" or "Pause". It will NOT check for the menu/screen identifier (like `title_screen`)!

**Value:** Required — The exact title text or localization key of the screen

## Is Key Pressed (`is_key_pressed`)

**Purpose:** Checks if a specific keyboard key is currently being pressed.

**Value:** Required — The key code of the target key. Selected via a UI when editing the requirement value.

## Is Any Screen Open (`is_any_screen_open`)

**Purpose:** Checks if any screen/menu is currently open (returns false if no screen is showing).

**Value:** Not required

## Is MC Debug Overlay Enabled (`is_debug_overlay_enabled`)

**Purpose:** Checks if the F3 debug overlay is currently visible.

**Value:** Not required

## Is Active Cursor Type (`is_active_cursor_type`)

**Purpose:** Checks if FancyMenu's currently active cursor type matches a specific standard cursor type.

**Value:** Required — Cursor type: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all`, or `not_allowed`

## Is Customization Menu Bar Visible (`is_customization_menu_bar_visible`)

**Purpose:** Checks if FancyMenu's customization menu bar is currently visible.

**Value:** Not required

## Is Modpack Mode Enabled (`is_modpack_mode_enabled`)

**Purpose:** Checks if FancyMenu's Modpack Mode is enabled.

**Value:** Not required

## Mouse Button Is Pressed (`mouse_click`)

**Purpose:** Returns true while a specific mouse button is held. This is not a one-shot click event; use the [**On Mouse Button Clicked** listener](./listeners#on-mouse-button-clicked-mouse_button_clicked) when an action should run once per click.

**Value:** Required — `left` or `right` to indicate which mouse button to check

## Is Fullscreen (`fancymenu_loading_requirement_is_fullscreen`)

**Purpose:** Checks if the game is currently in fullscreen mode.

**Value:** Not required

## Is Window Width (`fancymenu_loading_requirement_is_window_width`)

**Purpose:** Checks if the game window width matches specific values.

**Value:** Required — Window width in pixels (e.g., "1920"). Multiple values can be provided by separating with commas.

## Is Window Height (`fancymenu_loading_requirement_is_window_height`)

**Purpose:** Checks if the game window height matches specific values.

**Value:** Required — Window height in pixels (e.g., "1080"). Multiple values can be provided by separating with commas.

## Is Window Width Bigger Than (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Purpose:** Checks if the game window width is bigger than a specific value.

**Value:** Required — Window width in pixels (e.g., "1920")

## Is Window Height Bigger Than (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Purpose:** Checks if the game window height is bigger than a specific value.

**Value:** Required — Window height in pixels (e.g., "1080")

## Is Multiplayer (`fancymenu_loading_requirement_is_multiplayer`)

**Purpose:** Checks if the player is currently in a multiplayer world.

**Value:** Not required

## Is Singleplayer (`fancymenu_loading_requirement_is_singpleplayer`)

**Purpose:** Checks if the player is currently in a singleplayer world.

**Value:** Not required

## Is World Loaded (`fancymenu_loading_requirement_is_world_loaded`)

**Purpose:** Checks if any world is currently loaded.

**Value:** Not required

## Is Adventure (`fancymenu_visibility_requirement_is_adventure`)

**Purpose:** Checks if the player is currently in adventure game mode.

**Value:** Not required

## Is Creative (`fancymenu_visibility_requirement_is_creative`)

**Purpose:** Checks if the player is currently in creative game mode.

**Value:** Not required

## Is Spectator (`fancymenu_visibility_requirement_is_spectator`)

**Purpose:** Checks if the player is currently in spectator game mode.

**Value:** Not required

## Is Survival (`fancymenu_visibility_requirement_is_survival`)

**Purpose:** Checks if the player is currently in survival game mode.

**Value:** Not required

## Is Game Mode (`is_gamemode`)

**Purpose:** Checks if the player is in a specific game mode.

**Value:** Required — Game mode name (e.g., "creative", "survival", "adventure", "spectator")

## Is Difficulty (`is_difficulty`)

**Purpose:** Checks if the current game difficulty matches a specific value.

**Value:** Required — Difficulty name (e.g., "peaceful", "easy", "normal", "hard")

## Is Hardcore (`is_hardcore`)

**Purpose:** Checks if the currently loaded world is in hardcore mode.

**Value:** Not required

## Is Camera Perspective (`is_camera_perspective`)

**Purpose:** Checks if the current camera perspective matches a specific perspective.

**Value:** Required — `first_person`, `third_person_back`, or `third_person_front`

## Is Raining (`is_raining`)

**Purpose:** Checks if it's currently raining in the player's location.

**Value:** Not required

## Is Thundering (`is_thundering`)

**Purpose:** Checks if there's currently a thunderstorm in the player's world.

**Value:** Not required

## Is Clear Weather (`is_clear_weather`)

**Purpose:** Checks if the weather is currently clear (not raining or thundering).

**Value:** Not required

## Is Snowing (`is_snowing`)

**Purpose:** Checks if it's currently snowing at the player's location.

**Value:** Not required

## Is Player Running (`is_player_running`)

**Purpose:** Checks if the player is currently sprinting.

**Value:** Not required

## Is Player Sneaking (`is_player_sneaking`)

**Purpose:** Checks if the player is currently sneaking/crouching.

**Value:** Not required

## Is Player Using Item (`is_player_using_item`)

**Purpose:** Checks if the player is currently using an item.

**Value:** Not required

## Is Player Swimming (`is_player_swimming`)

**Purpose:** Checks if the player is currently swimming.

**Value:** Not required

## Is Player Jumping or Falling (`is_player_jumping`)

**Purpose:** Returns true while the player is airborne in a normal jumping or falling state. Swimming, fluids, elytra flight, sleeping, visual swimming, and crawling are excluded.

**Value:** Not required

## Is Player Under Water (`is_player_under_water`)

**Purpose:** Checks if the player is completely under water.

**Value:** Not required

## Is Player In Water (`is_player_in_water`)

**Purpose:** Checks if the player is in water (can be partially submerged).

**Value:** Not required

## Is Player In Lava (`is_player_in_lava`)

**Purpose:** Checks if the player is in lava.

**Value:** Not required

## Is Player In Fluid (`is_player_in_fluid`)

**Purpose:** Checks if the player is in any fluid (water, lava, etc.).

**Value:** Not required

## Is Player Riding Entity/Vehicle (`is_player_riding_entity`)

**Purpose:** Checks if the player is riding any entity.

**Value:** Not required

## Is Player Riding Jumpable Entity (`is_player_riding_jumpable_entity`)

**Purpose:** Checks if the player is riding an entity that can jump (like a horse).

**Value:** Not required

## Is Player Riding Entity With Health (`is_player_riding_entity_with_health`)

**Purpose:** Checks if the player is riding a living entity with health (like animals, not boats).

**Value:** Not required

## Is Player In Powder Snow (`is_player_in_powder_snow`)

**Purpose:** Checks if the player is currently in powder snow.

**Value:** Not required

## Was Player In Powder Snow (`was_player_in_powder_snow`)

**Purpose:** Checks if the player was in powder snow (used for effects that persist after leaving).

**Value:** Not required

## Is Player Wearing Pumpkin (`is_player_wearing_pumpkin`)

**Purpose:** Checks if the player is wearing a carved pumpkin on their head.

**Value:** Not required

## Is Player Flying With Elytra (`is_player_flying_with_elytra`)

**Purpose:** Checks if the player is currently flying with an elytra.

**Value:** Not required

## Is Player Creative Flying (`is_player_creative_flying`)

**Purpose:** Checks if the player is flying in creative mode.

**Value:** Not required

## Has Player Absorption Hearts (`has_player_absorption_hearts`)

**Purpose:** Checks if the player has any absorption hearts (golden hearts).

**Value:** Not required

## Is Player Withered (`is_player_withered`)

**Purpose:** Checks if the player is affected by the wither effect.

**Value:** Not required

## Is Player Fully Frozen (`is_player_fully_frozen`)

**Purpose:** Checks if the player is fully frozen (usually from powder snow).

**Value:** Not required

## Is Player Poisoned (`is_player_poisoned`)

**Purpose:** Checks if the player is affected by the poison effect.

**Value:** Not required

## Is Player In Biome (`is_player_in_biome`)

**Purpose:** Checks if the player is in a specific biome.

**Value:** Required — Biome identifier (e.g., `minecraft:birch_forest`)

## Is Player In Dimension (`is_player_in_dimension`)

**Purpose:** Checks if the player is in a specific dimension.

**Value:** Required — Dimension identifier (e.g., `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Is Player In Structure (`is_player_in_structure`)

**Purpose:** Checks if the player is currently inside a specific structure. Requires FancyMenu on the server for server worlds.

**Value:** Required — Structure identifier (e.g., `minecraft:village`)

## Is Entity Nearby (`is_entity_nearby`)

**Purpose:** Checks if a specific entity type is within a certain radius of the player.

**Value:** Required — Format: "radius:entity_id" (e.g., `10:minecraft:pig` - checks for pigs within 10 blocks)

## Is Effect Active (`is_effect_active`)

**Purpose:** Checks if a specific potion effect is active on the player.

**Value:** Required — Effect identifier (e.g., `minecraft:speed`, `minecraft:strength`)

## Is Any Effect Active (`is_any_effect_active`)

**Purpose:** Checks if the player has any potion effect active.

**Value:** Not required

## Is Player Left-Handed (`is_left_handed`)

**Purpose:** Checks if the player is set to left-handed mode in the game options.

**Value:** Not required

## Is Inventory Slot Filled (`is_inventory_slot_filled`)

**Purpose:** Checks if a specific inventory slot contains an item.

**Value:** Required — Slot number (0-35 for main inventory, slots 0-8 are hotbar)

## Is Item Hovered in Inventory (`is_item_hovered_in_inventory`)

**Purpose:** Checks if the cursor is hovering any item in an inventory screen.

**Value:** Not required

## Is Cursor Holding Inventory Item (`is_cursor_holding_inventory_item`)

**Purpose:** Checks if the cursor is currently holding an inventory item stack.

**Value:** Not required

## Is Hotbar Slot Selected (`is_hotbar_slot_active`)

**Purpose:** Checks if a specific hotbar slot is currently selected.

**Value:** Required — Hotbar slot number (0-8)

## Has Player Permission Level (`fancymenu_loading_requirement_has_player_permission_level`)

**Purpose:** Checks if the player has at least the specified permission/OP level on the current world or server.

**Value:** Required — Permission level number (0-4, where 4 is server operator)

## Is Attack Strength Weakened (`is_attack_strength_weakened`)

**Purpose:** Checks if the player's attack strength is currently weakened (not fully charged).

**Value:** Not required

## Is Real Time Day (`fancymenu_visibility_requirement_is_realtime_day`)

**Purpose:** Checks if the current real-world day of the month matches a specific value.

**Value:** Required — Day number (1-31). Multiple values can be provided by separating with commas.

## Is Real Time Hour (`fancymenu_visibility_requirement_is_realtime_hour`)

**Purpose:** Checks if the current real-world hour matches a specific value.

**Value:** Required — Hour in 24-hour format (0-23). Multiple values can be provided by separating with commas.

## Is Real Time Minute (`fancymenu_visibility_requirement_is_realtime_minute`)

**Purpose:** Checks if the current real-world minute matches a specific value.

**Value:** Required — Minute (0-59). Multiple values can be provided by separating with commas.

## Is Real Time Month (`fancymenu_visibility_requirement_is_realtime_month`)

**Purpose:** Checks if the current real-world month matches a specific value.

**Value:** Required — Month number (1-12, where 1 is January). Multiple values can be provided by separating with commas.

## Is Real Time Second (`fancymenu_visibility_requirement_is_realtime_second`)

**Purpose:** Checks if the current real-world second matches a specific value.

**Value:** Required — Second (0-59). Multiple values can be provided by separating with commas.

## Is Real Time Week Day (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Purpose:** Checks if the current real-world day of the week matches a specific value.

**Value:** Required — Day of week as number (1-7, where 1 is Sunday). Multiple values can be provided by separating with commas.

## Is Real Time Year (`fancymenu_visibility_requirement_is_realtime_year`)

**Purpose:** Checks if the current real-world year matches a specific value.

**Value:** Required — Full year (e.g., "2023"). Multiple values can be provided by separating with commas.

## File/Folder Exists (`fancymenu_loading_requirement_file_exists`)

**Purpose:** Checks whether a file or directory exists.

**Value:** Required — A path relative to the active game directory, or a path beginning with `.minecraft/` for the conventional Minecraft directory. Files and directories both count as existing.

## Is OS Linux (`fancymenu_loading_requirement_is_os_linux`)

**Purpose:** Checks whether the current platform is neither Windows nor macOS. This normally corresponds to Linux environments.

**Value:** Not required

## Is OS macOS (`fancymenu_loading_requirement_is_os_macos`)

**Purpose:** Checks if the operating system is macOS.

**Value:** Not required

## Is OS Windows (`fancymenu_loading_requirement_is_os_windows`)

**Purpose:** Checks if the operating system is Windows.

**Value:** Not required

## Is Internet Connection Available (`is_internet_connection_available`)

**Purpose:** Checks if an active internet connection is available.

**Value:** Not required

## Is Game Language (`fancymenu_loading_requirement_is_language`)

**Purpose:** Checks if the current game language matches a specific value.

**Value:** Required — Language code (e.g., `en_us` for English)

## Is Mod Loaded (`fancymenu_loading_requirement_is_mod_loaded`)

**Purpose:** Checks if a specific mod is loaded.

**Value:** Required — Mod ID (e.g., `fancymenu`, `jei`). You can also check for OptiFine with `optifine`. Multiple comma-separated mod IDs are supported; all listed mods must be loaded.

## Is MCEF Loaded (`is_mcef_loaded`)

**Purpose:** Checks if MCEF (Minecraft Chromium Embedded Framework) is installed and initialized. MCEF is required for the [Browser element](./elements#browser) and [deprecated MCEF-based video types](./video#requirements); [native Video features](./video) use Watermedia.

**Value:** Not required

## Is Number (`fancymenu_visibility_requirement_is_number`)

**Purpose:** Provides advanced number comparison with different comparison modes.

**Value:** Required — Complex format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` where `comparison_mode` can be `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals`, or `smaller-than-or-equals`

## Is Text (`fancymenu_visibility_requirement_is_text`)

**Purpose:** Provides advanced text comparison with different comparison modes.

**Value:** Required — Complex format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` where `comparison_mode` can be `equals`, `contains`, `starts-with`, or `ends-with`

## Is Server IP (`fancymenu_visibility_requirement_is_server_ip`)

**Purpose:** Checks if the current server IP matches a specific value.

**Value:** Required — Server IP address (with or without port)

## Is Server Online (`fancymenu_loading_requirement_is_server_online`)

**Purpose:** Checks if a specific server is online and reachable.

**Value:** Required — Server IP address (with or without port)

## Is Resource Pack Enabled (`is_resource_pack_enabled`)

**Purpose:** Checks if a specific resource pack is currently selected/active.

**Value:** Required — Resource pack title or pack ID (e.g., `Programmer Art` or the pack's ID)

## Is Variable Value (FM Variable) (`fancymenu_visibility_requirement_is_variable_value`)

**Purpose:** Checks if a FancyMenu variable has a specific value.

**Value:** Required — Format: "variable_name:expected_value"

## Only Once Per Session (`once_per_session`)

**Purpose:** Each configured instance returns true once per game session. Different instances are tracked independently.

**Value:** Not required
