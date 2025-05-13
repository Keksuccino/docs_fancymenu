---
title: Conditions (Loading Requirements)
description: How to use loading requirements.
published: true
date: 2025-05-13T19:33:23.730Z
tags: loading requirements, loading requirement, requirement, requirements
editor: markdown
dateCreated: 2025-04-14T20:14:22.175Z
---

# Loading Requirements
Loading requirements allow you to make parts of your layouts visible or invisible based on various conditions like if an element is hovered, the window has a specific size or if you're currently in a world.
They can also be used in action scripts of buttons, sliders, tickers and everything else with an action script input.

# Adding Requirements to Elements
To add one or more loading requirements to elements, just right-click the element and click on **Loading Requirements**.

# Layout-wide Requirements
You can also change the visibity of whole layouts by right-clicking the **editor background** and then clicking on **Loading Requirements [Layout-Wide]**.

# Action Scripts
Loading requirements can also be used in action scripts of elements with an action script input, like buttons, sliders or tickers.
You can add them in the action script screen and use them to execute specific actions only if the condition of the loading requirement is met.

# Requirement Values
Some loading requirements need you to set some values to work properly. If that's the case, the loading requirement screen should tell you to set all values first, but if not, just check if the **Edit Requirement Value** button is clickable when adding the requirement.
Always check the requirement's description if you're not sure what to set as value.
Some value inputs even support **TAB auto completion**.

# Available Requirements

The following list contains many of the available requirements, but it's possible that some are missing, so always check FancyMenu's requirement UI for a full list of all available requirements.

## GUI Category Requirements

### Is Element Hovered
Checks if a specific element is hovered by the mouse cursor.  
**Value required**: Yes - Element ID of the target element (e.g., `some_element_ID`). You can get the ID by right-clicking an element in the editor.

### Is ANY Element Hovered
Checks if any element in the layout is currently being hovered by the mouse cursor.  
**Value required**: No

### Is ANY Button Hovered
Checks if any button (vanilla or custom) is currently being hovered by the mouse cursor.  
**Value required**: No

### Is Layout Enabled
Checks if a specific layout is currently enabled.  
**Value required**: Yes - The name of the layout (e.g., `my_cool_main_menu_layout`)

### Is GUI Scale
Checks if the current GUI scale matches certain conditions.  
**Value required**: Yes - Can accept numeric values like `1`, `2`, etc.

### Is Button Active
Checks if a specific button is active (clickable).  
**Value required**: Yes - Element ID of the target button (e.g., "some_element_ID")

### Is Menu Title
Checks if the screen title matches a specific text or localization key.  
**Value required**: Yes - The exact title text or localization key of the screen

### Is Key Pressed
Checks if a specific keyboard key is currently being pressed.  
**Value required**: Yes - The key code of the target key. Selected via a UI when editing the requirement value.

## Window Category Requirements

### Is Fullscreen
Checks if the game is currently in fullscreen mode.  
**Value required**: No

### Is Window Width
Checks if the game window width matches specific values.  
**Value required**: Yes - Window width in pixels (e.g., "1920"). Multiple values can be provided by separating with commas.

### Is Window Height
Checks if the game window height matches specific values.  
**Value required**: Yes - Window height in pixels (e.g., "1080"). Multiple values can be provided by separating with commas.

### Is Window Width Bigger Than
Checks if the game window width is bigger than a specific value.  
**Value required**: Yes - Window width in pixels (e.g., "1920")

### Is Window Height Bigger Than
Checks if the game window height is bigger than a specific value.  
**Value required**: Yes - Window height in pixels (e.g., "1080")

## World Category Requirements

### Is Multiplayer
Checks if the player is currently in a multiplayer world.  
**Value required**: No

### Is Singleplayer
Checks if the player is currently in a singleplayer world.  
**Value required**: No

### Is World Loaded
Checks if any world is currently loaded.  
**Value required**: No

### Is Adventure
Checks if the player is currently in adventure game mode.  
**Value required**: No

### Is Creative
Checks if the player is currently in creative game mode.  
**Value required**: No

### Is Spectator
Checks if the player is currently in spectator game mode.  
**Value required**: No

### Is Survival
Checks if the player is currently in survival game mode.  
**Value required**: No

### Is Game Mode
Checks if the player is in a specific game mode.  
**Value required**: Yes - Game mode name (e.g., "creative", "survival", "adventure", "spectator")

### Is Difficulty
Checks if the current game difficulty matches a specific value.  
**Value required**: Yes - Difficulty name (e.g., "peaceful", "easy", "normal", "hard")

### Is Raining
Checks if it's currently raining in the player's location.  
**Value required**: No

### Is Thundering
Checks if there's currently a thunderstorm in the player's world.  
**Value required**: No

### Is Clear Weather
Checks if the weather is currently clear (not raining or thundering).  
**Value required**: No

### Is Snowing
Checks if it's currently snowing at the player's location.  
**Value required**: No

## Player State Requirements

### Is Player Running
Checks if the player is currently sprinting.  
**Value required**: No

### Is Player Sneaking
Checks if the player is currently sneaking/crouching.  
**Value required**: No

### Is Player Swimming
Checks if the player is currently swimming.  
**Value required**: No

### Is Player Jumping
Checks if the player is currently jumping.  
**Value required**: No

### Is Player Under Water
Checks if the player is completely under water.  
**Value required**: No

### Is Player In Water
Checks if the player is in water (can be partially submerged).  
**Value required**: No

### Is Player In Lava
Checks if the player is in lava.  
**Value required**: No

### Is Player In Fluid
Checks if the player is in any fluid (water, lava, etc.).  
**Value required**: No

### Is Player Riding Entity
Checks if the player is riding any entity.  
**Value required**: No

### Is Player Riding Jumpable Entity
Checks if the player is riding an entity that can jump (like a horse).  
**Value required**: No

### Is Player Riding Entity With Health
Checks if the player is riding a living entity with health (like animals, not boats).  
**Value required**: No

### Is Player In Powder Snow
Checks if the player is currently in powder snow.  
**Value required**: No

### Was Player In Powder Snow
Checks if the player was in powder snow (used for effects that persist after leaving).  
**Value required**: No

### Is Player Wearing Pumpkin
Checks if the player is wearing a carved pumpkin on their head.  
**Value required**: No

### Is Player Flying With Elytra
Checks if the player is currently flying with an elytra.  
**Value required**: No

### Is Player Creative Flying
Checks if the player is flying in creative mode.  
**Value required**: No

### Has Player Absorption Hearts
Checks if the player has any absorption hearts (golden hearts).  
**Value required**: No

### Is Player Withered
Checks if the player is affected by the wither effect.  
**Value required**: No

### Is Player Fully Frozen
Checks if the player is fully frozen (usually from powder snow).  
**Value required**: No

### Is Player Poisoned
Checks if the player is affected by the poison effect.  
**Value required**: No

### Is Player In Biome
Checks if the player is in a specific biome.  
**Value required**: Yes - Biome identifier (e.g., `minecraft:birch_forest`)

### Is Player In Dimension
Checks if the player is in a specific dimension.  
**Value required**: Yes - Dimension identifier (e.g., `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

### Is Entity Nearby
Checks if a specific entity type is within a certain radius of the player.  
**Value required**: Yes - Format: "radius:entity_id" (e.g., `10:minecraft:pig` - checks for pigs within 10 blocks)

### Is Effect Active
Checks if a specific potion effect is active on the player.  
**Value required**: Yes - Effect identifier (e.g., `minecraft:speed`, `minecraft:strength`)

### Is Any Effect Active
Checks if the player has any potion effect active.  
**Value required**: No

### Is Player Left Handed
Checks if the player is set to left-handed mode in the game options.  
**Value required**: No

### Is Inventory Slot Filled
Checks if a specific inventory slot contains an item.  
**Value required**: Yes - Slot number (0-35 for main inventory, slots 0-8 are hotbar)

### Is Hotbar Slot Active
Checks if a specific hotbar slot is currently selected.  
**Value required**: Yes - Hotbar slot number (0-8)

### Is Attack Strength Weakened
Checks if the player's attack strength is currently weakened (not fully charged).  
**Value required**: No

## Realtime Category Requirements

### Is Real Time Day
Checks if the current real-world day of the month matches a specific value.  
**Value required**: Yes - Day number (1-31). Multiple values can be provided by separating with commas.

### Is Real Time Hour
Checks if the current real-world hour matches a specific value.  
**Value required**: Yes - Hour in 24-hour format (0-23). Multiple values can be provided by separating with commas.

### Is Real Time Minute
Checks if the current real-world minute matches a specific value.  
**Value required**: Yes - Minute (0-59). Multiple values can be provided by separating with commas.

### Is Real Time Month
Checks if the current real-world month matches a specific value.  
**Value required**: Yes - Month number (1-12, where 1 is January). Multiple values can be provided by separating with commas.

### Is Real Time Second
Checks if the current real-world second matches a specific value.  
**Value required**: Yes - Second (0-59). Multiple values can be provided by separating with commas.

### Is Real Time Week Day
Checks if the current real-world day of the week matches a specific value.  
**Value required**: Yes - Day of week as number (1-7, where 1 is Sunday). Multiple values can be provided by separating with commas.

### Is Real Time Year
Checks if the current real-world year matches a specific value.  
**Value required**: Yes - Full year (e.g., "2023"). Multiple values can be provided by separating with commas.

## System Category Requirements

### File/Folder Exists
Checks if a specific file or folder exists on the system.  
**Value required**: Yes - Path to the file or folder (absolute or relative to the game directory)

### Is OS Linux
Checks if the operating system is Linux.  
**Value required**: No

### Is OS macOS
Checks if the operating system is macOS.  
**Value required**: No

### Is OS Windows
Checks if the operating system is Windows.  
**Value required**: No

### Is Internet Connection Available
Checks if an active internet connection is available.  
**Value required**: No

## Other Requirements

### Is Game Language
Checks if the current game language matches a specific value.  
**Value required**: Yes - Language code (e.g., `en_us` for English)

### Is Mod Loaded
Checks if a specific mod is loaded.  
**Value required**: Yes - Mod ID (e.g., `fancymenu`, `jei`). You can also check for Optifine with `optifine`. Multiple mod IDs can be provided by separating with commas.

### Is Number
Provides advanced number comparison with different comparison modes.  
**Value required**: Yes - Complex format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` where `comparison_mode` can be `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals`, or `smaller-than-or-equals`

### Is Text
Provides advanced text comparison with different comparison modes.  
**Value required**: Yes - Complex format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` where `comparison_mode` can be `equals`, `contains`, `starts-with`, or `ends-with`

### Is Server IP
Checks if the current server IP matches a specific value.  
**Value required**: Yes - Server IP address (with or without port)

### Is Server Online
Checks if a specific server is online and reachable.  
**Value required**: Yes - Server IP address (with or without port)

### Is Variable Value
Checks if a FancyMenu variable has a specific value.  
**Value required**: Yes - Format: "variable_name:expected_value"

### Only Once Per Session
Returns true only once per game session. Useful for one-time announcements or actions.  
**Value required**: No

### Mouse Clicked
Checks if a specific mouse button is being pressed.  
**Value required**: Yes - `left` or `right` to indicate which mouse button to check