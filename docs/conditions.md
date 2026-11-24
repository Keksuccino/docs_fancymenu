---
title: Requirements
description: Show elements and layouts, make buttons clickable or run actions only when something is true, like the time, the window size or a variable.
---

# Requirements

Requirements are conditions, like "the mouse is over this button", "it's December" or "a world is loaded". Use them to:

- show an [element](/elements) only sometimes,
- load a whole layout only sometimes,
- make buttons, sliders and checkboxes clickable only sometimes,
- run parts of an [action script](/action-scripts) only sometimes.

FancyMenu checks requirements all the time while a menu is open, so things show, hide or change right away. This info box only shows while the mouse is over **Multiplayer**:

<img width="800" alt="Moving the mouse over the Multiplayer button of the title screen shows an info box with a server address next to it" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_hover.gif?raw=true">

# Where to Find Them

| Where | What the requirements do |
|---|---|
| Right-click an element -> **Loading Requirements** | The element only shows while they're met. Works for [Vanilla elements](/vanilla-elements) too. |
| Right-click the editor background -> **Loading Requirements [Layout-Wide]** | The whole layout only loads while they're met. See [Layout-Wide Requirements](#layout-wide-requirements). |
| Right-click a button, slider or checkbox -> **Control Active State** | It's only clickable while they're met. Otherwise it's greyed out. Vanilla buttons have it too. |
| IF, ELSE-IF and WHILE in [action scripts](/action-scripts#statements) | The actions inside only run while they're met. |

In the layout editor, elements always show, so you can still edit them. Requirements of elements work outside of the editor.

# Adding a Requirement

<img width="800" alt="Copying the ID of the Multiplayer button, then giving the info box the requirement Is Element Hovered with that ID in Manage Requirements" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_add.gif?raw=true">

1. Right-click the element and click **Loading Requirements**. **Manage Requirements** opens.
2. Right-click the empty list and click **Add Requirement**, or press `A`.
3. Click a category in **Available Requirements**, or start typing to search names and descriptions. **Requirement Description** explains the selected requirement.
4. Click **Next Step** to set its value. Requirements without a value have **Done** instead. Double-clicking a requirement does the same.
5. Fill in the value and click **Done**. For example, **Is Element Hovered** needs the ID of the element. Right-click an element and click **Copy Element ID** to get it.
6. Click **Done** in **Manage Requirements**.

## Requirement Mode

The **Requirement Mode** button in the requirement chooser switches between:

- **Normal**: met when its condition is true.
- **Opposite**: met when its condition is NOT true. **Is World Loaded** in Opposite mode is only met in the main menus, for example.

**Manage Requirements** shows the mode and value of every requirement.

## Values

- Values support [placeholders](/placeholders) and your [variables](/variables#showing-variables-in-text), like `$$coins`. FancyMenu fills them in every time it checks the requirement.
- Many value fields suggest values while you type, like biomes, mod IDs, languages or the names of your variables. Click a suggestion, or press `Tab`.
- Requirements with a simple value open a one-line text editor. Its title says what to type, like **Target Element ID**.

## Managing Requirements

Right-click the list, a requirement or a group in **Manage Requirements** for these options:

| Option | Shortcut | What it does |
|---|---|---|
| **Add Requirement** | `A` | Adds a requirement. |
| **Add Group** | `G` | Adds a group (see below). |
| **Edit Requirement** | `Enter` or double-click | Opens the requirement chooser with its type, mode and value. |
| **Remove Requirement** / **Remove Group** | `Delete` | Removes it. |
| **Undo** / **Redo** | `Ctrl + Z` / `Ctrl + Y` | Undoes and redoes changes in this window. |
| **Export Requirements for AI** | | Exports all requirements of the window for an [AI chat](/export-for-ai), with your unsaved changes. |

`Up` and `Down` select the requirement above or below. **Done** (`Ctrl + S`) saves, **Cancel** throws away everything you changed in the window. Use `Cmd` instead of `Ctrl` on macOS.

With several elements selected, **Loading Requirements** changes the requirements of all of them. When they have different requirements, FancyMenu asks first, because all of them get replaced.

# Combining Requirements

All requirements in **Manage Requirements** have to be met. To say "this OR that", use a group.

A group acts like one requirement:

- **And** mode: everything in the group has to be met. New groups start in this mode.
- **Or** mode: one thing in the group is enough.

1. Right-click the list and click **Add Group**, or press `G`. The group gets a name like `group_1`.
2. Right-click the group and click **Group Mode** to switch between **And** and **Or**.
3. Click **Edit Group Requirements**, or double-click the group. A window like **Manage Requirements** opens for the group.
4. Add the requirements of the group and click **Done**.

For example, a Christmas greeting that shows in December, or whenever the player turned on `xmas_lights`: an Or group with **Is Real Time Month** `12` and **Is Variable Value (FM Variable)** for the variable `xmas_lights` with the value `on`.

<img width="800" alt="Adding a group in Manage Requirements, switching it to Or, and adding Is Real Time Month and Is Variable Value (FM Variable) to it" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_group.gif?raw=true">

- Groups can hold other groups, for things like "(A and B) or (C and D)". The window title shows where you are, like `Edit Group: group_1 › group_2`.
- **Edit Group Identifier** renames a group. Every name can only be used once, also inside groups.
- An empty group in **Or** mode is never met.

# Layout-Wide Requirements

Layout-wide requirements decide if a whole layout loads. Use them for a night version of your title screen, a layout per language, or a layout that only shows in singleplayer.

Right-click the editor background and click **Loading Requirements [Layout-Wide]**. It's also in **menu bar -> Layout -> Layout Properties**.

- When the result changes while the menu is open, FancyMenu builds the screen again with the layouts that are met now.
- They work for [universal layouts](/universal-layouts) too.
- To turn a layout on and off with a button, put the button in another layout. See [Toggle Parts of Layouts](/toggle).

# Good to Know

- World and player requirements are never met while no world is loaded, like in the main menus.
- Requirements about elements, the mouse cursor, inventories, the player and the world don't work in a [Ticker](/elements#ticker) with **Async** on. FancyMenu shows an error with the name of the requirement then.
- Requirements of add-ons you removed get skipped. Saving the layout in the editor removes them for good.
- **menu bar -> Customization -> Settings -> Requirement Caching Duration [MS]** reuses the results of requirements for some milliseconds, which makes big layouts faster. `0` turns it off, which is the default. Caching can make action scripts and quick changes behave in unexpected ways.

# All Requirements

The requirements are sorted like in the requirement chooser: by category, then by name. Requirements without a category are at the bottom of the chooser, and in [Other](#other) here.

# GUI

## Is Active Cursor Type (`is_active_cursor_type`)

Met while the mouse cursor has a certain shape, like **Pointing Hand** over a link or **Writing Cursor** over a text field.

- Value: click **Cursor Type** to pick **Normal**, **Writing Cursor**, **Crosshair**, **Pointing Hand**, **Resize Horizontal**, **Resize Vertical**, **Resize NWSE**, **Resize NESW**, **Resize All** or **Not Allowed**.

## Is Any Button Hovered (`fancymenu_visibility_requirement_is_any_button_hovered`)

Met while the mouse is over any visible button, Vanilla or custom.

## Is Any Element Hovered (`fancymenu_visibility_requirement_is_any_element_hovered`)

Met while the mouse is over any visible element, not only buttons.

## Is Any Screen Open (`is_any_screen_open`)

Met while any menu is open, like the pause menu or the inventory. Not met while you play without a menu.

## Is Button Active (`fancymenu_visibility_requirement_is_button_active`)

Met while a button is clickable.

- Value: the [element ID](/element-identifiers) of the button. Right-click it in the editor and click **Copy Element ID**.

## Is Customization Menu Bar Visible (`is_customization_menu_bar_visible`)

Met while FancyMenu's menu bar shows. Not met in Modpack Mode or while the menu bar is off.

## Is Element Focused (`is_element_focused`)

Met while an element has the focus. Buttons and sliders get it when you click them, or when you move to them with the arrow keys or `Tab`. Moving there with keys doesn't count as hovering, so put this and **Is Element Hovered** in an [Or group](#combining-requirements) for players who use the keyboard.

- Value: the [element ID](/element-identifiers), like `mc_titlescreen_multiplayer_button`.

## Is Element Hovered (`fancymenu_visibility_requirement_is_element_hovered`)

Met while the mouse is over an element. The element has to be visible.

- Value: the [element ID](/element-identifiers), like `mc_titlescreen_multiplayer_button` for the Multiplayer button of the title screen. Right-click an element in the editor and click **Copy Element ID** to get it.

## Is Element Scrolled to End (`is_scroll_area_scrolled_to_end`)

Met when a [Scrollable Area](/scrollable-areas) or a Text element is scrolled all the way down. An element with nothing to scroll counts as scrolled to the end. Good for an **Accept** button that only works after the player scrolled through the rules.

- Value: the [element ID](/element-identifiers) of the Scrollable Area or Text element.

## Is GUI Scale (`fancymenu_loading_requirement_is_gui_scale`)

Met when the GUI scale of Minecraft matches.

- Value: a number like `2` for exactly that scale, `>2` for bigger than 2, `<4` for smaller than 4. Decimals work too, like `<3.5`.
- Separate several conditions with commas. Of the plain numbers, one has to match, like `2,3`. All `>` and `<` conditions have to match, like `>1,<4`.

## Is Key Pressed (`is_key_pressed`)

Met while a key is held down. To run actions once per key press, use the [**On Keyboard Key Pressed**](/listeners#on-keyboard-key-pressed-keyboard_key_pressed) listener instead.

- Value: click **Change Key** in **Key Selection** and press the key.

## Is Layout Enabled (`fancymenu_visibility_requirement_is_layout_enabled`)

Met while a layout is enabled.

- Value: the name of the layout, like `winter_title_screen`.

## Is MC Debug Overlay Enabled (`is_debug_overlay_enabled`)

Met while the F3 debug screen shows. Not met while the HUD is hidden with F1.

## Is Modpack Mode Enabled (`is_modpack_mode_enabled`)

Met while FancyMenu's Modpack Mode is on.

## Is Screen Title (`is_menu_title`)

Met when the title of the open screen matches, like "Options" or "Game Menu". That's the title players see, not the [screen identifier](/screen-identifiers).

- Value: the title text or its localization key, like `options.title`. The value window shows both for the screen you're editing, and suggests localization keys.
- Localization keys work in every language. Title texts have to match exactly.

# Realtime

These check the clock of the player's computer. Separate several values with commas: one of them has to match.

## Is Real Time Day (`fancymenu_visibility_requirement_is_realtime_day`)

Met on certain days of the month.

- Value: `1` to `31`, like `24,25,26`.

## Is Real Time Hour (`fancymenu_visibility_requirement_is_realtime_hour`)

Met during certain hours.

- Value: `0` to `23`, like `20,21,22,23` for the evening.

## Is Real Time Minute (`fancymenu_visibility_requirement_is_realtime_minute`)

Met during certain minutes of the hour.

- Value: `0` to `59`.

## Is Real Time Month (`fancymenu_visibility_requirement_is_realtime_month`)

Met in certain months.

- Value: `1` (January) to `12` (December), like `12` for Christmas.

## Is Real Time Second (`fancymenu_visibility_requirement_is_realtime_second`)

Met during certain seconds of the minute.

- Value: `0` to `59`.

## Is Real Time Week Day (`fancymenu_visibility_requirement_is_realtime_week_day`)

Met on certain days of the week.

- Value: `1` (Sunday) to `7` (Saturday), like `1,7` for weekends.

## Is Real Time Year (`fancymenu_visibility_requirement_is_realtime_year`)

Met in certain years.

- Value: the full year, like `2027`.

# System

## File/Folder Exists (`fancymenu_loading_requirement_file_exists`)

Met when a file or folder exists.

- Value: a path in the game folder, like `config/mymodpack/welcome_seen.txt`. Paths that start with `.minecraft/` point to the default `.minecraft` folder.

## Is Internet Connection Available (`is_internet_connection_available`)

Met while the computer is online. FancyMenu checks that in the background every now and then.

## Is OS Linux (`fancymenu_loading_requirement_is_os_linux`)

Met on Linux. Technically, on every system that's neither Windows nor macOS.

## Is OS macOS (`fancymenu_loading_requirement_is_os_macos`)

Met on macOS.

## Is OS Windows (`fancymenu_loading_requirement_is_os_windows`)

Met on Windows.

## Scheduler Is Running (`fancymenu_visibility_requirement_is_scheduler_running`)

Met while a [scheduler](/schedulers) runs.

- Value: the identifier of the scheduler, like `my_scheduler`.

# Window

Window sizes are in real pixels of the game window, not GUI pixels. The requirement description shows the current size.

## Is Fullscreen (`fancymenu_loading_requirement_is_fullscreen`)

Met while the game is in fullscreen.

## Is Window Height (`fancymenu_loading_requirement_is_window_height`)

Met when the window has a certain height.

- Value: the height, like `1080`. Separate several heights with commas: one of them has to match.

## Is Window Height Bigger Than (`fancymenu_loading_requirement_is_window_height_bigger_than`)

Met while the window is taller than a height.

- Value: the height, like `1080`.

## Is Window Width (`fancymenu_loading_requirement_is_window_width`)

Met when the window has a certain width.

- Value: the width, like `1920`. Separate several widths with commas: one of them has to match.

## Is Window Width Bigger Than (`fancymenu_loading_requirement_is_window_width_bigger_than`)

Met while the window is wider than a width.

- Value: the width, like `1920`.

# World

These are never met while no world is loaded. **Is Player In Structure** and **Is In Active Raid Area** need FancyMenu on the server. In singleplayer, they always work.

## Has Player Absorption Hearts (`has_player_absorption_hearts`)

Met while the player has golden absorption hearts.

## Has Player Permission Level (`fancymenu_loading_requirement_has_player_permission_level`)

Met while the player has at least a permission level in the world or on the server, like an operator.

- Value: `0` to `4`. `0` is always met, `2` is enough for commands like `/gamemode`, and `4` is the level the `/op` command gives.

## Is Adventure (`fancymenu_visibility_requirement_is_adventure`)

Met while the player is in Adventure mode.

## Is Any Effect Active (`is_any_effect_active`)

Met while the player has any effect, like Speed or Poison.

## Is Attack Strength Weakened (`is_attack_strength_weakened`)

Met while the player's attack isn't fully charged. That's when the attack indicator shows.

## Is Block/Item In Tag (`is_in_tag`)

Met when a block or item belongs to a tag, like `minecraft:logs` or `c:tools`. Tags only exist while a world is loaded.

- Value: click **Tag Type** to pick **Block** or **Item**, then type the **Block/Item Key** and the **Tag**. Both fields suggest values. The `#` in front of the tag is optional.
- The key works great with listener variables like `$$block_key`. For example, an IF statement in the script of the [**On Block Broke**](/listeners#on-block-broke-block_broke) listener can show a toast only for logs.

## Is Camera Perspective (`is_camera_perspective`)

Met while the camera has a certain perspective (F5).

- Value: click the button to pick **First Person**, **Third Person** or **Front View**.

## Is Clear Weather (`is_clear_weather`)

Met while it neither rains nor thunders.

## Is Creative (`fancymenu_visibility_requirement_is_creative`)

Met while the player is in Creative mode.

## Is Cursor Holding Inventory Item (`is_cursor_holding_inventory_item`)

Met while the mouse cursor carries an item in an inventory screen.

## Is Difficulty (`is_difficulty`)

Met when the world has a certain difficulty.

- Value: `peaceful`, `easy`, `normal` or `hard`.

## Is Effect Active (`is_effect_active`)

Met while the player has a certain effect.

- Value: the key of the effect, like `minecraft:speed`. The field suggests effects while you're in a world.

## Is Entity Nearby (`is_entity_nearby`)

Met while an entity of a certain type is near the player.

- Value: the **Entity Registry Key**, like `minecraft:creeper`, and the **Check Radius In Blocks**, like `10`. The key field suggests entities while you're in a world.

## Is Game Mode (`is_gamemode`)

Met while the player is in a certain game mode.

- Value: `survival`, `creative`, `adventure` or `spectator`.

## Is Hardcore (`is_hardcore`)

Met in Hardcore worlds.

## Is Hotbar Slot Selected (`is_hotbar_slot_active`)

Met while a certain hotbar slot is selected.

- Value: `0` (the left slot) to `8`.

## Is In Active Raid Area (`is_in_active_raid_area`)

Met while the player is in the area of a raid, where the raid bar shows. Needs FancyMenu on the server.

## Is Inventory Slot Filled (`is_inventory_slot_filled`)

Met while a slot of the player's inventory has an item.

- Value: the slot number. `0` to `8` are the hotbar, `9` to `35` the rest of the inventory.

## Is Item Hovered In Inventory (`is_item_hovered_in_inventory`)

Met while the mouse is over an item in an inventory screen, like the player's inventory or a chest.

## Is Multiplayer (`fancymenu_loading_requirement_is_multiplayer`)

Met while the player is on a server.

## Is Player Creative Flying (`is_player_creative_flying`)

Met while the player flies in Creative mode.

## Is Player Flying With Elytra (`is_player_flying_with_elytra`)

Met while the player glides with an elytra.

## Is Player Fully Frozen (`is_player_fully_frozen`)

Met while the player is fully frozen from powder snow, with frozen hearts in the health bar.

## Is Player In Biome (`is_player_in_biome`)

Met while the player is in a certain biome.

- Value: the key of the biome, like `minecraft:birch_forest`. The field suggests biomes while you're in a world.

## Is Player In Dimension (`is_player_in_dimension`)

Met while the player is in a certain dimension.

- Value: the key of the dimension: `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`, or one of a mod. The field suggests dimensions while you're in a world.

## Is Player In Fluid (`is_player_in_fluid`)

Met while the player is in any fluid, like water or lava.

## Is Player In Lava (`is_player_in_lava`)

Met while the player is in lava.

## Is Player In Powder Snow (`is_player_in_powder_snow`)

Met while the player is in powder snow.

## Is Player In Structure (`is_player_in_structure`)

Met while the player is inside a certain structure. Needs FancyMenu on the server.

- Value: the key of the structure, like `minecraft:village_plains`. The field suggests structures while you're in a world.

## Is Player In Water (`is_player_in_water`)

Met while the player is in water, even partly.

## Is Player Jumping or Falling (`is_player_jumping`)

Met while the player is in the air. Swimming, fluids, elytra flight, sleeping and crawling don't count.

## Is Player Left-Handed (`is_left_handed`)

Met when "Main Hand" in Minecraft's Skin Customization options is set to "Left".

## Is Player Poisoned (`is_player_poisoned`)

Met while the player has the Poison effect, with poisoned hearts in the health bar.

## Is Player Riding Entity With Health (`is_player_riding_entity_with_health`)

Met while the player rides a living entity, like a horse or a pig. Boats and minecarts don't count.

## Is Player Riding Entity/Vehicle (`is_player_riding_entity`)

Met while the player rides anything, like a horse, a boat or a minecart.

## Is Player Riding Jumpable Entity (`is_player_riding_jumpable_entity`)

Met while the player rides an entity that can jump, like a horse.

## Is Player Running (`is_player_running`)

Met while the player sprints.

## Is Player Sneaking (`is_player_sneaking`)

Met while the player sneaks.

## Is Player Swimming (`is_player_swimming`)

Met while the player swims.

## Is Player Under Water (`is_player_under_water`)

Met while the player's head is under water.

## Is Player Using Item (`is_player_using_item`)

Met while the player uses an item, like eating, drinking a potion or drawing a bow.

## Is Player Wearing Pumpkin (`is_player_wearing_pumpkin`)

Met while the player wears a carved pumpkin on their head.

## Is Player Withered (`is_player_withered`)

Met while the player has the Wither effect, with withered hearts in the health bar.

## Is Raining (`is_raining`)

Met while it rains where the player is.

## Is Singleplayer (`fancymenu_loading_requirement_is_singpleplayer`)

Met while the player is in a singleplayer world.

## Is Snowing (`is_snowing`)

Met while it snows where the player is.

## Is Spectator (`fancymenu_visibility_requirement_is_spectator`)

Met while the player is in Spectator mode.

## Is Survival (`fancymenu_visibility_requirement_is_survival`)

Met while the player is in Survival mode.

## Is Thundering (`is_thundering`)

Met during a thunderstorm.

## Is World Loaded (`fancymenu_loading_requirement_is_world_loaded`)

Met while the player is in a world, singleplayer or multiplayer.

## Was Player In Powder Snow (`was_player_in_powder_snow`)

Met while the player was in powder snow a moment ago.

# Other

## Is Game Language (`fancymenu_loading_requirement_is_language`)

Met when Minecraft uses a certain language.

- Value: the language code, like `en_us` or `de_de`. The field suggests all languages.

## Is Mod Loaded (`fancymenu_loading_requirement_is_mod_loaded`)

Met when certain mods are installed.

- Value: the mod ID, like `jei`. The field suggests the IDs of your mods. Separate several IDs with commas: all of them have to be installed. `optifine` checks for OptiFine.

## Is Number (`fancymenu_visibility_requirement_is_number`)

Compares two numbers. Put placeholders or variables in the fields, like `$$coins`.

- **Compare Mode**: **Equals**, **Bigger Than**, **Smaller Than**, **Bigger Than Or Equals** or **Smaller Than Or Equals**.
- **Number**: the number to check, like `$$coins`.
- **Compare to Number**: the number to compare it to, like `100`.

Decimals work, like `2.5`. When a field isn't a number, it's never met.

## Is Resource Pack Enabled (`is_resource_pack_enabled`)

Met while a resource pack is enabled.

- Value: the name of the pack like in the Resource Packs screen, like `Programmer Art`, or its ID. Upper and lower case don't matter.

## Is Rinku Loaded (`is_rinku_loaded`)

Met when the [Rinku](https://modrinth.com/mod/rinku) mod is installed. The [Browser element](/elements#browser) and the old [Rinku-based video types](/video#requirements) need it.

## Is Server IP (`fancymenu_visibility_requirement_is_server_ip`)

Met while the player is on a certain server.

- Value: the address of the server, like `play.example.net`. With a port, like `play.example.net:25566`, the port has to match too.

## Is Server Online (`fancymenu_loading_requirement_is_server_online`)

Met while a server is online. FancyMenu pings it in the background about every 30 seconds, so it can take a moment after the game starts.

- Value: the address of the server, like `play.example.net`.

## Is Text (`fancymenu_visibility_requirement_is_text`)

Compares two texts. Put placeholders or variables in the fields, like `$$key_name`.

- **Compare Mode**: **Equals**, **Contains**, **Starts With** or **Ends With**.
- **Text**: the text to check.
- **Compare to Text**: the text to compare it to.

Upper and lower case matter.

## Is Variable Value (FM Variable) (`fancymenu_visibility_requirement_is_variable_value`)

Met when one of your [variables](/variables) has a certain value.

- **Variable Name**: the name of the variable, without `$$`. The field suggests your variables.
- **Variable Value to Check For**: the value, like `on`. It has to match the whole value, with upper and lower case.

Never met when the variable doesn't exist. For a list variable, it compares the JSON array of all entries, like `["apple","banana"]`. To check for one entry, use **List Contains Entry (FM Variable)**.

## List Contains Entry (FM Variable) (`list_contains_entry`)

Met when a [list variable](/variables#text-and-list-variables) has a certain entry.

- **List Variable Name**: the name of the list, without `$$`. The field suggests your list variables, and warns you when you type the name of a text variable.
- **Entry to Look For**: the entry. It has to match a whole entry, not just a part of it.
- **Ignore Case**: when on, `Apple` also matches `apple`.

Never met when the list doesn't exist.

## Mouse Button Is Pressed (`mouse_click`)

Met while a mouse button is held down. To run actions once per click, use the [**On Mouse Button Clicked**](/listeners#on-mouse-button-clicked-mouse_button_clicked) listener instead.

- Value: `left` or `right`.

## Only Once Per Session (`once_per_session`)

Met the first time it gets checked, then never again until the game restarts. Every copy of it counts on its own.

For elements that should show only once per game session, the **Load Once Per Session** option of elements is easier: they stay until a new screen opens.
