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

You can use them on elements, whole layouts, and action scripts.

# Adding Requirements to Elements

To add one or more requirements to elements, just right-click the element and click on **Loading Requirements**.

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

FancyMenu 3.9.0 reworks the Manage Requirements window to use a right-click context menu, keyboard navigation, search, undo/redo (`CTRL + Z` / `CTRL + Y`) and `CTRL + S` as the **Done** shortcut.

# Requirements in Detail

The following list contains most, if not all, requirements available in FancyMenu. It is possible that the list is sometimes a bit outdated due to updates for the mod.

## Is Element Hovered
Checks if a specific element is hovered by the mouse cursor.  
**Value required**: Yes - Element ID of the target element (e.g., `some_element_ID`). You can get the ID by right-clicking an element in the editor.

## Is Element Focused
Checks if a specific element currently has keyboard focus (for example, a text field or focused button).
**Value required**: Yes - Element ID of the target element (the same ID shown in the editor)

> This is not the same as when an element is just hovered, even tho it looks similar. Focused elements keep looking "hovered" even when they are not hovered anymore. Elements get focused when clicking them or when using the keyboard to navigate in menus.
{.is-info}

## Is Any Element Hovered
Checks if any element in the layout is currently being hovered by the mouse cursor.  
**Value required**: No

## Is Any Button Hovered
Checks if any button (vanilla or custom) is currently being hovered by the mouse cursor.  
**Value required**: No

## Is Layout Enabled
Checks if a specific layout is currently enabled.  
**Value required**: Yes - The name of the layout (e.g., `my_cool_main_menu_layout`)

## Is Scheduler Running
Checks if a scheduler is currently running.
**Value required**: Yes - Scheduler ID (e.g., `my_scheduler`)

## Is GUI Scale
Checks if the current GUI scale matches certain conditions.  
**Value required**: Yes - Can accept numeric values like `1`, `2`, etc.

## Is Button Active
Checks if a specific button is active (clickable).  
**Value required**: Yes - Element ID of the target button (e.g., "some_element_ID")

## Is Screen Title
Checks if the screen's DISPLAY title matches a specific text or localization key. This will only check for the display name/title of the screen, like "Options" or "Pause". It will NOT check for the menu/screen identifier (like `title_screen`)!

**Value required**: Yes - The exact title text or localization key of the screen

## Is Key Pressed
Checks if a specific keyboard key is currently being pressed.  
**Value required**: Yes - The key code of the target key. Selected via a UI when editing the requirement value.

## Is Any Screen Open
Checks if any screen/menu is currently open (returns false if no screen is showing).  
**Value required**: No

## Is MC Debug Overlay Enabled
Checks if the F3 debug overlay is currently visible.
**Value required**: No

## Is Active Cursor Type
Checks if FancyMenu's currently active cursor type matches a specific standard cursor type.
**Value required**: Yes - Cursor type: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all`, or `not_allowed`

## Is Customization Menu Bar Visible
Checks if FancyMenu's customization menu bar is currently visible.
**Value required**: No

## Is Modpack Mode Enabled
Checks if FancyMenu's Modpack Mode is enabled.
**Value required**: No

## Mouse Clicked
Checks if a specific mouse button is being pressed.  
**Value required**: Yes - `left` or `right` to indicate which mouse button to check

## Is Fullscreen
Checks if the game is currently in fullscreen mode.  
**Value required**: No

## Is Window Width
Checks if the game window width matches specific values.  
**Value required**: Yes - Window width in pixels (e.g., "1920"). Multiple values can be provided by separating with commas.

## Is Window Height
Checks if the game window height matches specific values.  
**Value required**: Yes - Window height in pixels (e.g., "1080"). Multiple values can be provided by separating with commas.

## Is Window Width Bigger Than
Checks if the game window width is bigger than a specific value.  
**Value required**: Yes - Window width in pixels (e.g., "1920")

## Is Window Height Bigger Than
Checks if the game window height is bigger than a specific value.  
**Value required**: Yes - Window height in pixels (e.g., "1080")

## Is Multiplayer
Checks if the player is currently in a multiplayer world.  
**Value required**: No

## Is Singleplayer
Checks if the player is currently in a singleplayer world.  
**Value required**: No

## Is World Loaded
Checks if any world is currently loaded.  
**Value required**: No

## Is Adventure
Checks if the player is currently in adventure game mode.  
**Value required**: No

## Is Creative
Checks if the player is currently in creative game mode.  
**Value required**: No

## Is Spectator
Checks if the player is currently in spectator game mode.  
**Value required**: No

## Is Survival
Checks if the player is currently in survival game mode.  
**Value required**: No

## Is Game Mode
Checks if the player is in a specific game mode.  
**Value required**: Yes - Game mode name (e.g., "creative", "survival", "adventure", "spectator")

## Is Difficulty
Checks if the current game difficulty matches a specific value.  
**Value required**: Yes - Difficulty name (e.g., "peaceful", "easy", "normal", "hard")

## Is Hardcore
Checks if the currently loaded world is in hardcore mode.
**Value required**: No

## Is Camera Perspective
Checks if the current camera perspective matches a specific perspective.
**Value required**: Yes - `first_person`, `third_person_back`, or `third_person_front`

## Is Raining
Checks if it's currently raining in the player's location.  
**Value required**: No

## Is Thundering
Checks if there's currently a thunderstorm in the player's world.  
**Value required**: No

## Is Clear Weather
Checks if the weather is currently clear (not raining or thundering).  
**Value required**: No

## Is Snowing
Checks if it's currently snowing at the player's location.  
**Value required**: No

## Is Player Running
Checks if the player is currently sprinting.  
**Value required**: No

## Is Player Sneaking
Checks if the player is currently sneaking/crouching.  
**Value required**: No

## Is Player Using Item
Checks if the player is currently using an item.
**Value required**: No

## Is Player Swimming
Checks if the player is currently swimming.  
**Value required**: No

## Is Player Jumping or Falling
Checks if the player is currently jumping.  
**Value required**: No

## Is Player Under Water
Checks if the player is completely under water.  
**Value required**: No

## Is Player In Water
Checks if the player is in water (can be partially submerged).  
**Value required**: No

## Is Player In Lava
Checks if the player is in lava.  
**Value required**: No

## Is Player In Fluid
Checks if the player is in any fluid (water, lava, etc.).  
**Value required**: No

## Is Player Riding Entity/Vehicle
Checks if the player is riding any entity.  
**Value required**: No

## Is Player Riding Jumpable Entity
Checks if the player is riding an entity that can jump (like a horse).  
**Value required**: No

## Is Player Riding Entity With Health
Checks if the player is riding a living entity with health (like animals, not boats).  
**Value required**: No

## Is Player In Powder Snow
Checks if the player is currently in powder snow.  
**Value required**: No

## Was Player In Powder Snow
Checks if the player was in powder snow (used for effects that persist after leaving).  
**Value required**: No

## Is Player Wearing Pumpkin
Checks if the player is wearing a carved pumpkin on their head.  
**Value required**: No

## Is Player Flying With Elytra
Checks if the player is currently flying with an elytra.  
**Value required**: No

## Is Player Creative Flying
Checks if the player is flying in creative mode.  
**Value required**: No

## Has Player Absorption Hearts
Checks if the player has any absorption hearts (golden hearts).  
**Value required**: No

## Is Player Withered
Checks if the player is affected by the wither effect.  
**Value required**: No

## Is Player Fully Frozen
Checks if the player is fully frozen (usually from powder snow).  
**Value required**: No

## Is Player Poisoned
Checks if the player is affected by the poison effect.  
**Value required**: No

## Is Player In Biome
Checks if the player is in a specific biome.  
**Value required**: Yes - Biome identifier (e.g., `minecraft:birch_forest`)

## Is Player In Dimension
Checks if the player is in a specific dimension.  
**Value required**: Yes - Dimension identifier (e.g., `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Is Player In Structure
Checks if the player is currently inside a specific structure. Requires FancyMenu on the server for server worlds.
**Value required**: Yes - Structure identifier (e.g., `minecraft:village`)

## Is Entity Nearby
Checks if a specific entity type is within a certain radius of the player.  
**Value required**: Yes - Format: "radius:entity_id" (e.g., `10:minecraft:pig` - checks for pigs within 10 blocks)

## Is Effect Active
Checks if a specific potion effect is active on the player.  
**Value required**: Yes - Effect identifier (e.g., `minecraft:speed`, `minecraft:strength`)

## Is Any Effect Active
Checks if the player has any potion effect active.  
**Value required**: No

## Is Player Left-Handed
Checks if the player is set to left-handed mode in the game options.  
**Value required**: No

## Is Inventory Slot Filled
Checks if a specific inventory slot contains an item.  
**Value required**: Yes - Slot number (0-35 for main inventory, slots 0-8 are hotbar)

## Is Item Hovered in Inventory
Checks if the cursor is hovering any item in an inventory screen.
**Value required**: No

## Is Cursor Holding Inventory Item
Checks if the cursor is currently holding an inventory item stack.
**Value required**: No

## Is Hotbar Slot Selected
Checks if a specific hotbar slot is currently selected.  
**Value required**: Yes - Hotbar slot number (0-8)

## Has Player Permission Level
Checks if the player has at least the specified permission/OP level on the current world or server.  
**Value required**: Yes - Permission level number (0-4, where 4 is server operator)

## Is Attack Strength Weakened
Checks if the player's attack strength is currently weakened (not fully charged).  
**Value required**: No

## Is Real Time Day
Checks if the current real-world day of the month matches a specific value.  
**Value required**: Yes - Day number (1-31). Multiple values can be provided by separating with commas.

## Is Real Time Hour
Checks if the current real-world hour matches a specific value.  
**Value required**: Yes - Hour in 24-hour format (0-23). Multiple values can be provided by separating with commas.

## Is Real Time Minute
Checks if the current real-world minute matches a specific value.  
**Value required**: Yes - Minute (0-59). Multiple values can be provided by separating with commas.

## Is Real Time Month
Checks if the current real-world month matches a specific value.  
**Value required**: Yes - Month number (1-12, where 1 is January). Multiple values can be provided by separating with commas.

## Is Real Time Second
Checks if the current real-world second matches a specific value.  
**Value required**: Yes - Second (0-59). Multiple values can be provided by separating with commas.

## Is Real Time Week Day
Checks if the current real-world day of the week matches a specific value.  
**Value required**: Yes - Day of week as number (1-7, where 1 is Sunday). Multiple values can be provided by separating with commas.

## Is Real Time Year
Checks if the current real-world year matches a specific value.  
**Value required**: Yes - Full year (e.g., "2023"). Multiple values can be provided by separating with commas.

## File/Folder Exists
Checks if a specific file or folder exists on the system.  
**Value required**: Yes - Path to the file or folder (absolute or relative to the game directory)

## Is OS Linux
Checks if the operating system is Linux.  
**Value required**: No

## Is OS macOS
Checks if the operating system is macOS.  
**Value required**: No

## Is OS Windows
Checks if the operating system is Windows.  
**Value required**: No

## Is Internet Connection Available
Checks if an active internet connection is available.  
**Value required**: No

## Is Game Language
Checks if the current game language matches a specific value.  
**Value required**: Yes - Language code (e.g., `en_us` for English)

## Is Mod Loaded
Checks if a specific mod is loaded.  
**Value required**: Yes - Mod ID (e.g., `fancymenu`, `jei`). You can also check for Optifine with `optifine`. Multiple mod IDs can be provided by separating with commas.

## Is MCEF Loaded
Checks if MCEF (Minecraft Chromium Embedded Framework) is installed and initialized.  
**Value required**: No

## Is Number
Provides advanced number comparison with different comparison modes.  
**Value required**: Yes - Complex format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` where `comparison_mode` can be `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals`, or `smaller-than-or-equals`

## Is Text
Provides advanced text comparison with different comparison modes.  
**Value required**: Yes - Complex format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` where `comparison_mode` can be `equals`, `contains`, `starts-with`, or `ends-with`

## Is Server IP
Checks if the current server IP matches a specific value.  
**Value required**: Yes - Server IP address (with or without port)

## Is Server Online
Checks if a specific server is online and reachable.  
**Value required**: Yes - Server IP address (with or without port)

## Is Resource Pack Enabled
Checks if a specific resource pack is currently selected/active.  
**Value required**: Yes - Resource pack title or pack ID (e.g., `Programmer Art` or the pack's ID)

## Is Variable Value (FM Variable)
Checks if a FancyMenu variable has a specific value.  
**Value required**: Yes - Format: "variable_name:expected_value"

## Only Once Per Session
Returns true only once per game session. Useful for one-time announcements or actions.  
**Value required**: No
