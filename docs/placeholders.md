---
title: Placeholders
description: How to use placeholders.
---
# Placeholders

Placeholders insert live values into text, buttons, requirements, and other supported fields.

# General Information

## Basic Syntax
Placeholders in FancyMenu use a JSON-like syntax:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

For example, to display the player's name:
```
{"placeholder":"playername"}
```

## Nesting Placeholders
You can use one placeholder inside another placeholder's value.

Example of nested placeholders:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
This example takes the maximum RAM value and divides it by 1024 to convert it from MB to GB.

> [!IMPORTANT]
> This is FancyMenu syntax, not JSON. Nested placeholders use the exact unescaped form shown above, so JSON formatters will reject or rewrite them. Placeholder names are case-sensitive; malformed or unknown placeholders remain visible as text and are logged.

# Using Placeholders

Most elements that have text inputs support placeholders. You can see if a text input supports placeholders when editing it. If the full-screen **text editor** opens when editing the text, it supports placeholders. 

To find a **list of all placeholders**, just click on the **Placeholders** button in the **top-right corner** of the **text editor**.

There is a **search bar** at the top of the placeholders list that lets you search for placeholders.

Clicking on a placeholder in the placeholder list will paste it to the text content.

# Placeholders In Detail

This section lists FancyMenu's built-in placeholders.

## Unavailable Results

Placeholder output is always text. When data is unavailable, the result depends on the placeholder: common fallbacks are an empty string, `0`, `0.0`, `00:00`, `false`, `UNKNOWN`, or `ERROR`. Entries with a specific fallback state it directly; test the fallback before using environment-dependent output in a [requirement](./conditions), path, command, or URL.

## Player Name (`playername`)

**Purpose:** Returns the current player's username.

**Values:** None

**Example:**

```
{"placeholder":"playername"}
```

**Output:** `Steve`

## Player UUID (`playeruuid`)

**Purpose:** Returns the player's unique identifier.

**Values:** None

**Example:**

```
{"placeholder":"playeruuid"}
```

**Output:** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft Version (`mcversion`)

**Purpose:** Returns the current Minecraft version.

**Values:** None

**Example:**

```
{"placeholder":"mcversion"}
```

**Output:** `1.21.1`

## Mod Loader Version (`loaderver`)

**Purpose:** Returns the version of the mod loader (Fabric/NeoForge).

**Values:** None

**Example:**

```
{"placeholder":"loaderver"}
```

**Output:** `0.16.14`

## Mod Loader Name (`loadername`)

**Purpose:** Returns the name of the mod loader.

**Values:** None

**Example:**

```
{"placeholder":"loadername"}
```

**Output:** `Fabric`

## Mod Version (`modversion`)

**Purpose:** Returns the version of a specific mod.

**Values:** `modid`

**Example:**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**Output:** `1.2.3`

## Total Mods Count (`totalmods`)

**Purpose:** Returns an approximate mod-file count based on the `mods` directory and loaded-mod count. It does not reliably count every disabled mod.

**Values:** None

**Example:**

```
{"placeholder":"totalmods"}
```

**Output:** `45`

## Active Mods Count (`loadedmods`)

**Purpose:** Returns the number of currently loaded mods.

**Values:** None

**Example:**

```
{"placeholder":"loadedmods"}
```

**Output:** `43`

## World Loading Progress (`world_load_progress`)

**Purpose:** Returns the current world loading progress as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"world_load_progress"}
```

**Output:** `75`

## Minecraft Option Value (`minecraft_option_value`)

**Purpose:** Returns the value of a Minecraft option.

**Values:** `name`

**Example:**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**Output:** `70`

## Last World or Server (`last_world_server`)

**Purpose:** Returns information about the last world or server accessed.

**Values:** `type`, `full_world_path`

**Example:**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parameters:
- `type`: Determines what type of information to return
  - `"both"`: Returns the last accessed world or server (default)
  - `"server"`: Only returns if the last accessed was a server
  - `"world"`: Only returns if the last accessed was a world
- `full_world_path`: Controls how world paths are displayed
  - `"true"`: Returns the full world path (default)
  - `"false"`: Returns only the world name without path (does not affect servers)

Examples:
- Server: `mc.hypixel.net`
- World with full path: `saves/New World`
- World without full path: `New World`

## Screen Width (`guiwidth`)

**Purpose:** Returns the current screen width in GUI-scaled pixels, not physical monitor pixels.

**Values:** None

**Example:**

```
{"placeholder":"guiwidth"}
```

**Output:** `960`

## Screen Height (`guiheight`)

**Purpose:** Returns the current screen height in GUI-scaled pixels, not physical monitor pixels.

**Values:** None

**Example:**

```
{"placeholder":"guiheight"}
```

**Output:** `540`

## Current Screen Identifier (`screenid`)

**Purpose:** Returns the identifier of the current screen.

**Values:** None

**Example:**

```
{"placeholder":"screenid"}
```

**Output:** `title_screen`

## Element Width (`elementwidth`)

**Purpose:** Returns the width of a specific element.

**Values:** `id`

**Example:**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**Output:** `200`

## Element Height (`elementheight`)

**Purpose:** Returns the height of a specific element.

**Values:** `id`

**Example:**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**Output:** `20`

## Element X Position (`elementposx`)

**Purpose:** Returns the X position of a specific element.

**Values:** `id`

**Example:**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**Output:** `150`

## Element Y Position (`elementposy`)

**Purpose:** Returns the Y position of a specific element.

**Values:** `id`

**Example:**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**Output:** `100`

## Mouse X Position (`mouseposx`)

**Purpose:** Returns the current X position of the mouse.

**Values:** None

**Example:**

```
{"placeholder":"mouseposx"}
```

**Output:** `960`

## Mouse Y Position (`mouseposy`)

**Purpose:** Returns the current Y position of the mouse.

**Values:** None

**Example:**

```
{"placeholder":"mouseposy"}
```

**Output:** `540`

## Clicks Per Second (`clicks_per_second`)

**Purpose:** Returns the current clicks per second for a mouse button.

**Values:** `mouse_button`

**Example:**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parameters:
- `mouse_button`: `left` or `right`

**Output:** `8`

## GUI Scale (`guiscale`)

**Purpose:** Returns the current GUI scale.

**Values:** None

**Example:**

```
{"placeholder":"guiscale"}
```

**Output:** `2`

## Vanilla Widget Label/Text (`vanillabuttonlabel`)

**Purpose:** Returns the label/text of a vanilla widget/button.

**Values:** `locator`

**Example:**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**Output:** `Options...`

## Text Input Field Value (`text_input_field_value`)

**Purpose:** Returns the current value of a custom or vanilla text input field by element identifier.

**Values:** `element_identifier`

**Example:**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**Output:** `Hello World`

## Current Player Health (`current_player_health`)

**Purpose:** Returns the player's current health points.

**Values:** None

**Example:**

```
{"placeholder":"current_player_health"}
```

**Output:** `20.0`

## Max Player Health (`max_player_health`)

**Purpose:** Returns the player's maximum health points.

**Values:** None

**Example:**

```
{"placeholder":"max_player_health"}
```

**Output:** `20.0`

## Current Player Health (Percent) (`current_player_health_percent`)

**Purpose:** Returns the player's health as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"current_player_health_percent"}
```

**Output:** `100`

## Current Player Absorption Health (`current_player_absorption_health`)

**Purpose:** Returns the player's absorption health points (golden hearts).

**Values:** None

**Example:**

```
{"placeholder":"current_player_absorption_health"}
```

**Output:** `4.0`

## Max Player Absorption Health (`max_player_absorption_health`)

**Purpose:** Returns the maximum absorption health.

**Values:** None

**Example:**

```
{"placeholder":"max_player_absorption_health"}
```

**Output:** `4.0`

## Current Player Absorption Health (Percent) (`current_player_absorption_health_percent`)

**Purpose:** Returns the player's absorption health as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**Output:** `100`

## Current Player Food Level (`current_player_hunger`)

**Purpose:** Returns the player's current hunger level.

**Values:** None

**Example:**

```
{"placeholder":"current_player_hunger"}
```

**Output:** `20`

## Max Player Food Level (`max_player_hunger`)

**Purpose:** Returns the maximum hunger level.

**Values:** None

**Example:**

```
{"placeholder":"max_player_hunger"}
```

**Output:** `20`

## Current Player Food Level (Percent) (`current_player_hunger_percent`)

**Purpose:** Returns the player's hunger as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"current_player_hunger_percent"}
```

**Output:** `100`

## Current Player Hunger Saturation (`current_player_hunger_saturation`)

**Purpose:** Returns the player's current hunger saturation value.

**Values:** None

**Example:**

```
{"placeholder":"current_player_hunger_saturation"}
```

**Output:** `5.0`

## Current Player Armor (`current_player_armor`)

**Purpose:** Returns the player's current armor value.

**Values:** None

**Example:**

```
{"placeholder":"current_player_armor"}
```

**Output:** `20`

## Player Armor Toughness (`player_armor_toughness`)

**Purpose:** Returns the player's total armor toughness value.

**Values:** None

**Example:**

```
{"placeholder":"player_armor_toughness"}
```

**Output:** `8.0`

## Max Player Armor (`max_player_armor`)

**Purpose:** Returns the maximum armor value.

**Values:** None

**Example:**

```
{"placeholder":"max_player_armor"}
```

**Output:** `20`

## Current Player Armor (Percent) (`current_player_armor_percent`)

**Purpose:** Returns the player's armor as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"current_player_armor_percent"}
```

**Output:** `100`

## Current Player Oxygen Level (`current_player_oxygen`)

**Purpose:** Returns the player's current oxygen level (air bubbles).

**Values:** None

**Example:**

```
{"placeholder":"current_player_oxygen"}
```

**Output:** `300`

## Max Player Oxygen Level (`max_player_oxygen`)

**Purpose:** Returns the maximum oxygen level.

**Values:** None

**Example:**

```
{"placeholder":"max_player_oxygen"}
```

**Output:** `300`

## Current Player Oxygen Level (Percent) (`current_player_oxygen_percent`)

**Purpose:** Returns the player's oxygen level as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"current_player_oxygen_percent"}
```

**Output:** `100`

## Current Player Level (`current_player_level`)

**Purpose:** Returns the player's current experience level.

**Values:** None

**Example:**

```
{"placeholder":"current_player_level"}
```

**Output:** `30`

## Current Player Experience (`current_player_exp`)

**Purpose:** Returns the player's total experience points.

**Values:** None

**Example:**

```
{"placeholder":"current_player_exp"}
```

**Output:** `1250`

## Player Experience Progress (Percent) (`current_player_exp_progress`)

**Purpose:** Returns the player's experience progress to the next level as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"current_player_exp_progress"}
```

**Output:** `75`

## Player Attack Strength (Percent) (`player_attack_strength`)

**Purpose:** Returns the player's attack cooldown as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"player_attack_strength"}
```

**Output:** `100`

## Player Game Mode (`player_gamemode`)

**Purpose:** Returns the player's current game mode.

**Values:** None

**Example:**

```
{"placeholder":"player_gamemode"}
```

**Output:** `survival`

## Player View Direction (`player_view_direction`)

**Purpose:** Returns the direction the player is facing.

**Values:** None

**Example:**

```
{"placeholder":"player_view_direction"}
```

**Output:** `north`

## Player X Coordinate (`player_x_coordinate`)

**Purpose:** Returns the player's X position in the world.

**Values:** None

**Example:**

```
{"placeholder":"player_x_coordinate"}
```

**Output:** `125`

## Player Y Coordinate (`player_y_coordinate`)

**Purpose:** Returns the player's Y position in the world.

**Values:** None

**Example:**

```
{"placeholder":"player_y_coordinate"}
```

**Output:** `64`

## Player Z Coordinate (`player_z_coordinate`)

**Purpose:** Returns the player's Z position in the world.

**Values:** None

**Example:**

```
{"placeholder":"player_z_coordinate"}
```

**Output:** `-250`

## Current Mount Health (`current_mount_health`)

**Purpose:** Returns the current health of the entity the player is riding.

**Values:** None

**Example:**

```
{"placeholder":"current_mount_health"}
```

**Output:** `30.0`

## Max Mount Health (`max_mount_health`)

**Purpose:** Returns the maximum health of the entity the player is riding.

**Values:** None

**Example:**

```
{"placeholder":"max_mount_health"}
```

**Output:** `30.0`

## Current Mount Health (Percent) (`current_mount_health_percent`)

**Purpose:** Returns the mount's health as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"current_mount_health_percent"}
```

**Output:** `100`

## Current Mount Jump Meter (Percent) (`current_mount_jump_meter`)

**Purpose:** Returns the mount's jump power meter value.

**Values:** None

**Example:**

```
{"placeholder":"current_mount_jump_meter"}
```

**Output:** `75`

## Current Boss Health (Percent) (`current_boss_health`)

**Purpose:** Returns a selected active boss's health as an integer percentage from `0` to `100`. `boss_index` is zero-based; `0` selects the first boss bar.

**Values:** `boss_index`

**Example:**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**Output:** `75`

## Boss Name (`boss_name`)

**Purpose:** Returns the name of the active boss.

**Values:** `boss_index`, `as_json`

**Example:**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**Output:** `Ender Dragon`

## Bosses Count (`boss_count`)

**Purpose:** Returns the number of active bosses.

**Values:** None

**Example:**

```
{"placeholder":"boss_count"}
```

**Output:** `1`

## Active Effects Count (`effects_count`)

**Purpose:** Returns the number of active potion effects.

**Values:** None

**Example:**

```
{"placeholder":"effects_count"}
```

**Output:** `3`

## Active Effect (`active_effect`)

**Purpose:** Returns information about a specific active effect.

**Values:** `effect_index`

**Example:**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**Output:** `minecraft:speed`

## Selected Hotbar Slot (`active_hotbar_slot`)

**Purpose:** Returns the currently selected hotbar slot (0-8).

**Values:** None

**Example:**

```
{"placeholder":"active_hotbar_slot"}
```

**Output:** `4`

## Slot Item (`slot_item`)

**Purpose:** Returns information about an item in a specific inventory slot.

**Values:** `slot`

**Example:**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**Output:** `minecraft:diamond_sword`

## Slot Item Count (`slot_item_count`)

**Purpose:** Returns the stack size of the item in a specific player inventory slot.

**Values:** `slot`

**Example:**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**Output:** `64`

## Slot Item Durability (`slot_item_durability`)

**Purpose:** Returns durability information for the item in a specific player inventory slot.

**Values:** `slot`, `format`

**Example:**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parameters:
- `slot`: Player inventory slot number.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage`, or `percent`.

**Output:** `87`

## Slot Item Display Name (`slot_item_display_name_fm`)

**Purpose:** Returns the display name of the item in a specific slot as a JSON text component. In spectator mode, hotbar slots can resolve spectator menu item names unless `ignore_spectator` is `true`.

**Values:** `slot`, `ignore_spectator`

**Example:**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**Output:** `{"text":"Diamond Sword","color":"aqua"}`

## Inventory Item Count (`inventory_item_count`)

**Purpose:** Returns the total number of matching items across the player's inventory. When `item` is empty, it sums the stack counts of all occupied inventory slots.

**Values:** `item`

**Example:**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**Output:** `12`

## Inventory Slot Food Point Restore Amount (`inventory_slot_food_point_restore_amount`)

**Purpose:** Returns the hunger points restored by the food item in the given player inventory slot.

**Values:** `slot`

**Example:**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**Output:** `4.0`

## Hovered Inventory Item (`hovered_inventory_item`)

**Purpose:** Returns the item key of the item currently hovered in an inventory screen.

**Values:** None

**Example:**

```
{"placeholder":"hovered_inventory_item"}
```

**Output:** `minecraft:apple`

## World Game Time (`game_time`)

**Purpose:** Returns the current in-game time tick counter.

**Values:** None

**Example:**

```
{"placeholder":"game_time"}
```

**Output:** `18000`

## World Day Time (`world_daytime`)

**Purpose:** Returns the current world day time.

**Values:** None

**Example:**

```
{"placeholder":"world_daytime"}
```

**Output:** `13000`

## World Day Time Hour (`world_daytime_hour`)

**Purpose:** Returns the hour component of world time. By default this uses 24-hour format; set `twelve_hour_format` to `"true"` for 12-hour format.

**Values:** `twelve_hour_format`

**Example:**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**Output:** `12`

## World Day Time Minute (`world_daytime_minute`)

**Purpose:** Returns the minute component of world time (00-59).

**Values:** None

**Example:**

```
{"placeholder":"world_daytime_minute"}
```

**Output:** `30`

## World Difficulty (`world_difficulty`)

**Purpose:** Returns the current world difficulty.

**Values:** None

**Example:**

```
{"placeholder":"world_difficulty"}
```

**Output:** `normal`

## Current World Seed (`current_world_seed`)

**Purpose:** Returns the seed of the current singleplayer world. Returns an empty value when the seed is not available.

**Values:** None

**Example:**

```
{"placeholder":"current_world_seed"}
```

**Output:** `123456789`

## Current Biome (`current_biome`)

**Purpose:** Returns the biome the player is currently in. Set `as_key` to `"false"` to return a translated/display name where available.

**Values:** `as_key`

**Example:**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**Output:** `minecraft:plains`

## Current Dimension (`current_dimension`)

**Purpose:** Returns the dimension the player is currently in. Set `as_key` to `"false"` to return a translated/display name where available.

**Values:** `as_key`

**Example:**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**Output:** `minecraft:overworld`

## Gamerule Value (`gamerule_value`)

**Purpose:** Returns the current value of a gamerule in the loaded world/server. Server worlds require FancyMenu on the server.

**Values:** `name`

**Example:**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**Output:** `true`

## Item Category (`item_category`)

**Purpose:** Returns the creative tab category of an item. Set `as_key` to `"true"` to return the category key instead of the display name.

**Values:** `item`, `as_key`

**Example:**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**Output:** `Combat`

## Current HUD Title/Subtitle (`current_title`)

**Purpose:** Returns the currently displayed title text.

**Values:** `is_subtitle`, `as_json`

**Example:**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**Output:** `Game Over!`

## Action Bar Message (`action_bar_message_fm`)

**Purpose:** Returns the current vanilla action-bar message as a serialized Minecraft text component.

**Values:** None

**Example:**

```
{"placeholder":"action_bar_message_fm"}
```

**Output:** `{"text":"You may not rest now","color":"red"}`

## Action Bar Message Time (`action_bar_message_time_fm`)

**Purpose:** Returns how many ticks the current vanilla action bar message will still be shown.

**Values:** None

**Example:**

```
{"placeholder":"action_bar_message_time_fm"}
```

**Output:** `42`

## Camera Rotation X (`camera_rotation_x_fm`)

**Purpose:** Returns the current camera pitch in degrees.

**Values:** None

**Example:**

```
{"placeholder":"camera_rotation_x_fm"}
```

**Output:** `12.5`

## Camera Rotation Y (`camera_rotation_y_fm`)

**Purpose:** Returns the current camera yaw in degrees.

**Values:** None

**Example:**

```
{"placeholder":"camera_rotation_y_fm"}
```

**Output:** `-90.0`

## Camera Rotation Delta X (`camera_rotation_delta_x_fm`)

**Purpose:** Returns the per-tick change in camera pitch.

**Values:** None

**Example:**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**Output:** `0.4`

## Camera Rotation Delta Y (`camera_rotation_delta_y_fm`)

**Purpose:** Returns the per-tick change in camera yaw.

**Values:** None

**Example:**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**Output:** `-1.2`

## Highlighted Item Time (`highlighted_item_time_fm`)

**Purpose:** Returns how many ticks the highlighted item name will still be shown above the hotbar.

**Values:** None

**Example:**

```
{"placeholder":"highlighted_item_time_fm"}
```

**Output:** `30`

## Player Item Use Progress (`player_item_use_progress_fm`)

**Purpose:** Returns the current item-use progress from `0.0` to `1.0`.

**Values:** None

**Example:**

```
{"placeholder":"player_item_use_progress_fm"}
```

**Output:** `0.65`

## Player Position Delta X (`player_position_delta_x_fm`)

**Purpose:** Returns the per-tick change in player position on the X axis.

**Values:** None

**Example:**

```
{"placeholder":"player_position_delta_x_fm"}
```

**Output:** `0.0`

## Player Position Delta Y (`player_position_delta_y_fm`)

**Purpose:** Returns the per-tick change in player position on the Y axis.

**Values:** None

**Example:**

```
{"placeholder":"player_position_delta_y_fm"}
```

**Output:** `-0.08`

## Player Position Delta Z (`player_position_delta_z_fm`)

**Purpose:** Returns the per-tick change in player position on the Z axis.

**Values:** None

**Example:**

```
{"placeholder":"player_position_delta_z_fm"}
```

**Output:** `0.12`

## Current Server IP (`current_server_ip`)

**Purpose:** Returns the IP of the connected server.

**Values:** None

**Example:**

```
{"placeholder":"current_server_ip"}
```

**Output:** `mc.hypixel.net`

## World Players List (`world_players_list`)

**Purpose:** Returns a list of all players currently in the world.

**Values:** `separator`

**Example:**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**Output:** `Steve, Alex, Notch`

## Server MOTD (`servermotd`)

**Purpose:** Returns the Message of the Day of a server.

**Values:** `ip`, `line`

**Example:**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**Output:** `Welcome to Hypixel!`

## Server PING (`serverping`)

**Purpose:** Returns the ping to a server in milliseconds.

**Values:** `ip`

**Example:**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**Output:** `54`

## Server Player Count (`serverplayercount`)

**Purpose:** Returns the player count of a server.

**Values:** `ip`

**Example:**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**Output:** `25000/30000`

## Server Status (`serverstatus`)

**Purpose:** Returns the online/offline status of a server.

**Values:** `ip`

**Example:**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**Output:** `§aOnline` or `§cOffline`

## Server Version (`serverversion`)

**Purpose:** Returns the Minecraft version of a server.

**Values:** `ip`

**Example:**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**Output:** `1.21.1`

> [!NOTE]
> The realtime placeholders below accept a `timezone` value. Use a Java time-zone ID such as `UTC`, `Europe/Berlin`, or `America/New_York`; omit it or use `system` for the system timezone. `unix_time` always returns the Unix timestamp and has no `timezone` value.

## Year (`realtimeyear`)

**Purpose:** Returns the current year.

**Values:** None

**Example:**

```
{"placeholder":"realtimeyear"}
```

**Output:** `2024`

## Month (`realtimemonth`)

**Purpose:** Returns the current month (01-12).

**Values:** None

**Example:**

```
{"placeholder":"realtimemonth"}
```

**Output:** `01`

## Day (`realtimeday`)

**Purpose:** Returns the current day of the month (01-31).

**Values:** None

**Example:**

```
{"placeholder":"realtimeday"}
```

**Output:** `27`

## Hour (`realtimehour`)

**Purpose:** Returns the current hour. By default this uses 24-hour format; set `twelve_hour_format` to `"true"` for 12-hour format.

**Values:** `twelve_hour_format`, `timezone`

**Example:**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**Output:** `14`

## Minute (`realtimeminute`)

**Purpose:** Returns the current minute (00-59).

**Values:** None

**Example:**

```
{"placeholder":"realtimeminute"}
```

**Output:** `30`

## Second (`realtimesecond`)

**Purpose:** Returns the current second (00-59).

**Values:** None

**Example:**

```
{"placeholder":"realtimesecond"}
```

**Output:** `45`

## Current Time in Millis (Unix Timestamp) (`unix_time`)

**Purpose:** Returns the current Unix timestamp in milliseconds.

**Values:** None

**Example:**

```
{"placeholder":"unix_time"}
```

**Output:** `1716552478123`

## CPU Info (`cpuinfo`)

**Purpose:** Returns information about the CPU.

**Values:** None

**Example:**

```
{"placeholder":"cpuinfo"}
```

**Output:** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU Usage (JVM) (`jvmcpu`)

**Purpose:** Returns the JVM's CPU usage as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"jvmcpu"}
```

**Output:** `25.5`

## CPU Usage (OS) (`oscpu`)

**Purpose:** Returns the OS CPU usage as a percentage.

**Values:** None

**Example:**

```
{"placeholder":"oscpu"}
```

**Output:** `42.8`

## GPU Info (`gpuinfo`)

**Purpose:** Returns the name reported for Minecraft's active rendering device. This is not guaranteed to identify a specific physical GPU.

**Values:** None

**Example:**

```
{"placeholder":"gpuinfo"}
```

**Output:** `NVIDIA GeForce RTX 3080`

## Java Version (`javaver`)

**Purpose:** Returns the Java version.

**Values:** None

**Example:**

```
{"placeholder":"javaver"}
```

**Output:** `17.0.2`

## Java Virtual Machine (`jvmname`)

**Purpose:** Returns the name of the Java Virtual Machine.

**Values:** None

**Example:**

```
{"placeholder":"jvmname"}
```

**Output:** `OpenJDK 64-Bit Server VM`

## OpenGL Version (`glver`)

**Purpose:** Returns driver information for Minecraft's active rendering device. Despite the legacy `glver` name, the value is not guaranteed to be only an OpenGL version string.

**Values:** None

**Example:**

```
{"placeholder":"glver"}
```

**Output:** `4.6.0 NVIDIA 516.94`

## Operating System Name (`osname`)

**Purpose:** Returns the operating system name.

**Values:** None

**Example:**

```
{"placeholder":"osname"}
```

**Output:** `Windows 10`

## FPS (Frames Per Second) (`fps`)

**Purpose:** Returns the current frames per second.

**Values:** None

**Example:**

```
{"placeholder":"fps"}
```

**Output:** `120`

## Used RAM in MB (`usedram`)

**Purpose:** Returns the amount of RAM currently in use (MB).

**Values:** None

**Example:**

```
{"placeholder":"usedram"}
```

**Output:** `4096`

## Max RAM in MB (`maxram`)

**Purpose:** Returns the maximum allocated RAM (MB).

**Values:** None

**Example:**

```
{"placeholder":"maxram"}
```

**Output:** `8192`

## Used RAM in %% (`percentram`)

**Purpose:** Returns the percentage of RAM currently in use.

**Values:** None

**Example:**

```
{"placeholder":"percentram"}
```

**Output:** `50`

## Audio Element Volume (`audio_element_vol`)

**Purpose:** Returns the volume of an audio element.

**Values:** `element_identifier`

**Example:**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**Output:** `0.5`

## Current Audio Track (`audio_element_current_track`)

**Purpose:** Returns the track name of an audio element.

**Values:** `element_identifier`, `display_name_mappings`

**Example:**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

In `display_name_mappings`, `=>` separates a filename from its display name and `%:%` separates mappings.

**Output:** `Menu Theme`

## Audio Duration (`audio_duration`)

**Purpose:** Returns the duration of the [Audio element](./elements#audio)'s current loaded track in `MM:SS` format. The track may be playing, paused, or stopped.

**Values:** `element_identifier`

**Example:**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**Output:** `03:45`

## Audio Play Time (`audio_playtime`)

**Purpose:** Returns the current playtime of an audio track. Set `show_percentage` to `"true"` to get a 0-100 progress value instead of `MM:SS`.

**Values:** `element_identifier`, `show_percentage`

**Example:**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**Output:** `01:30` (or `45` when `show_percentage` is `"true"`)

**Unavailable result:** `00:00`, or `0` in percentage mode. The current value is available while the track is playing or paused; stopped, missing, and unready tracks use the unavailable result.

## Audio Playing State (`audio_playing_state`)

**Purpose:** Returns whether an audio element is playing (true/false).

**Values:** `element_identifier`

**Example:**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**Output:** `true`

## Video Element Volume (`video_element_vol`)

**Purpose:** Returns the volume level of a video element (0.0 to 1.0).

**Values:** `element_identifier`

**Example:**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**Output:** `0.5`

## Video Element Duration (`video_element_duration`)

**Purpose:** Returns the total duration of a video element in `MM:SS` format. Set `output_as_timestamp` to `"true"` to return a millisecond timestamp.

**Values:** `element_identifier`, `output_as_timestamp`

**Example:**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**Output:** `02:00` (or `120000` when `output_as_timestamp` is `"true"`)

## Video Element Play Time (`video_element_playtime`)

**Purpose:** Returns the current playback time (progress) of a video element in `MM:SS` format. Set `show_percentage` to `"true"` for a 0-100 progress value, or `output_as_timestamp` to `"true"` for milliseconds.

**Values:** `element_identifier`, `show_percentage`, `output_as_timestamp`

**Example:**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**Output:** `00:45` (or `38` as percentage, or `45200` as timestamp)

## Video Element Paused State (`video_element_paused_state`)

**Purpose:** Returns whether a video element is paused (true/false).

**Values:** `element_identifier`

**Example:**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**Output:** `false`

## Video Background Volume (`video_background_vol`)

**Purpose:** Returns the volume level of a video menu background (0.0 to 1.0).

**Values:** `background_identifier`

**Example:**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**Output:** `0.7`

## Video Background Duration (`video_background_duration`)

**Purpose:** Returns the total duration of a video menu background in `MM:SS` format. Set `output_as_timestamp` to `"true"` to return a millisecond timestamp.

**Values:** `background_identifier`, `output_as_timestamp`

**Example:**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**Output:** `03:00` (or `180000` when `output_as_timestamp` is `"true"`)

## Video Background Play Time (`video_background_playtime`)

**Purpose:** Returns the current playback time (progress) of a video menu background in `MM:SS` format. Set `show_percentage` to `"true"` for a 0-100 progress value, or `output_as_timestamp` to `"true"` for milliseconds.

**Values:** `background_identifier`, `show_percentage`, `output_as_timestamp`

**Example:**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**Output:** `01:00` (or `33` as percentage, or `60500` as timestamp)

## Video Background Paused State (`video_background_paused_state`)

**Purpose:** Returns whether a video menu background is paused (true/false).

**Values:** `background_identifier`

**Example:**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**Output:** `true`

## Calculator (`calc`)

**Purpose:** The calculator placeholder is a powerful tool that allows you to perform mathematical calculations within your layouts. It supports a wide range of mathematical operations and can work with both decimal and integer numbers.

**Values:** `decimal`, `expression`

### Basic Syntax

**Example:**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

The calculator has two main parameters:
- `decimal`: Determines whether the result should include decimal places (`true`) or be rounded to integers (`false`)
- `expression`: The mathematical expression to evaluate

### Supported Operations
The calculator supports these mathematical operations:
- Basic arithmetic: `+` (addition), `-` (subtraction), `*` (multiplication), `/` (division)
- Parentheses: `( )` for grouping operations
- Power: `^` for exponents
- Square root: `sqrt()`
- Trigonometric functions: `sin()`, `cos()`, `tan()`
- Mathematical constants: `pi`, `e`
- Absolute value: `abs()`
- Logarithms: `log()`, `ln()`

## Random Number (`random_number`)

**Purpose:** Generates a random number within a specified range.

**Values:** `min`, `max`

**Example:**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**Output:** `42`

## Max Number (`maxnum`)

**Purpose:** Returns the larger of two numbers.

**Values:** `first`, `second`

**Example:**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**Output:** `20`

## Min Number (`minnum`)

**Purpose:** Returns the smaller of two numbers.

**Values:** `first`, `second`

**Example:**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**Output:** `10`

## Absolute Number (`absnum`)

**Purpose:** Returns the absolute value of a number.

**Values:** `num`

**Example:**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**Output:** `10.5`

## Make Number Negative (`negnum`)

**Purpose:** Makes a positive number negative. Zero and already-negative values are returned unchanged.

**Values:** `num`

**Example:**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**Output:** `-10.5`

## *pi* (Math) (`math_pi`)

**Purpose:** Returns the value of π.

**Values:** None

**Example:**

```
{"placeholder":"math_pi"}
```

**Output:** `3.141592653589793`

## Trigonometric Sine (Math) (`math_sin`)

**Purpose:** Returns the sine of an angle in radians. Convert degree values to radians first.

**Values:** `angle`

**Example:**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**Output:** `1.0`

## Trigonometric Cosine (Math) (`math_cos`)

**Purpose:** Returns the cosine of an angle in radians. Convert degree values to radians first.

**Values:** `angle`

**Example:**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**Output:** `1.0`

## Trigonometric Tangent (Math) (`math_tan`)

**Purpose:** Returns the tangent of an angle in radians. Convert degree values to radians first.

**Values:** `angle`

**Example:**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**Output:** `0.0`

## Floor (Math) (`math_floor`)

**Purpose:** Returns the mathematical floor of a number, formatted with a `.0` decimal suffix.

**Values:** `num`

**Example:**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**Output:** `3.0`

## Ceiling (Math) (`math_ceil`)

**Purpose:** Returns the mathematical ceiling of a number, formatted with a `.0` decimal suffix.

**Values:** `num`

**Example:**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**Output:** `4.0`

Use [**Round**](#round-math-math_round) or [**Calculator**](#calculator-calc) with decimal output disabled when you need integer text without `.0`.

## Round (Math) (`math_round`)

**Purpose:** Rounds a number. By default it rounds to the nearest integer; set `decimals` to a non-negative number to round to that many decimal places.

**Values:** `num`, `decimals`

**Example:**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**Output:** `3.14` (with `decimals:-1` or omitted → `3`)

## Sign (Math) (`math_sign`)

**Purpose:** Returns the sign of a number (1 for positive, -1 for negative, 0 for zero).

**Values:** `num`

**Example:**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**Output:** `-1`

## Hyperbolic Sine (Math) (`math_sinh`)

**Purpose:** Returns the hyperbolic sine of a number.

**Values:** `num`

**Example:**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**Output:** `1.1752011936438014`

## Hyperbolic Cosine (Math) (`math_cosh`)

**Purpose:** Returns the hyperbolic cosine of a number.

**Values:** `num`

**Example:**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**Output:** `1.5430806348152437`

## Hyperbolic Tangent (Math) (`math_tanh`)

**Purpose:** Returns the hyperbolic tangent of a number.

**Values:** `num`

**Example:**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**Output:** `0.7615941559557649`

## Split Text (`split_text`)

**Purpose:** Splits text using a specified delimiter.

**Values:** `input`, `regex`, `max_parts`, `split_index`

**Example:**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**Output:** `world`

## Trim Text (`trim_text`)

**Purpose:** Removes leading and trailing whitespace.

**Values:** `text`

**Example:**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**Output:** `hello world`

## Crop Text (`crop_text`)

**Purpose:** Removes characters from the start and end of text.

**Values:** `text`, `remove_from_start`, `remove_from_end`

**Example:**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**Output:** `ello worl`

## Stringify (`stringify`)

**Purpose:** Stringifies a text by escaping all syntax characters.

**Values:** `text`

**Example:**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**Output:** `text with \{special\} \"characters\"`

## Localize Text (`local`)

**Purpose:** Retrieves localized text for a key.

**Values:** `key`

**Example:**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**Output:** `Singleplayer`

## Web Text (`webtext`)

**Purpose:** Retrieves text content from a web URL.

**Values:** `link`

**Example:**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**Output:** `Welcome to the server!`

## Random Text (`randomtext`)

**Purpose:** Returns a random line from a text file, URL, or direct plain text. The text changes at specified intervals. File and URL content is refreshed approximately every 30 seconds; direct plain-text content remains cached because it does not require reloading.

**Values:** `source`, `interval`

In placeholder values, `/config/...` means `<game-directory>/config/...`; it is not a filesystem-root path. See [Resources](./resources#local-resources).

**Example:**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parameters:
- `source`: The source of the text lines (replaces the old `path` parameter)
  - File path: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Plain text: `Line 1\nLine 2\nLine 3`
- `interval`: Time in seconds between text changes

The placeholder now supports three source types:
1. **Local files**: Text files from your game directory
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: Remote text files from the internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Plain text**: Direct text input with lines separated by `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Note: Old placeholders using `path` instead of `source` will continue to work.

## JSON Parser (`json`)

**Purpose:** Parses JSON data from a file, URL, or direct JSON content and extracts values using JSON path expressions.

**Values:** `source`, `json_path`

**Example:**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parameters:
- `source`: The source of the JSON data
  - File path: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Direct JSON: `{"name":"Steve","level":42}`
- `json_path`: The JSON path expression to extract data

The placeholder now supports three source types:
1. **Local files**: JSON files from your game directory
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: Remote JSON data from APIs or web services
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Direct JSON**: Inline JSON content
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Example JSON paths:
- `$.name` - Gets the "name" field from root
- `$.player.level` - Gets nested "level" field inside "player"
- `$.items[0].id` - Gets the "id" of the first item in an array
- `$.scores.*` - Gets all values from the "scores" object

## Absolute File/Folder Path (`absolute_path`)

**Purpose:** Returns the absolute path of a file.

**Values:** `short_path`

**Example:**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**Output:** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## Text Character Count (`text_character_count`)

**Purpose:** Returns the number of characters in the given text.

**Values:** `text`

**Example:**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**Output:** `12`

## Text Width (`text_width`)

**Purpose:** Returns the width in pixels of the given text when rendered.

**Values:** `text`

**Example:**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**Output:** `66`

## Uppercase Text (`uppercase_text`)

**Purpose:** Converts the input text to all uppercase letters.

**Values:** `text`

**Example:**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**Output:** `HELLO WORLD`

## Lowercase Text (`lowercase_text`)

**Purpose:** Converts the input text to all lowercase letters.

**Values:** `text`

**Example:**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**Output:** `hello world`

## Title Case Text (`title_case_text`)

**Purpose:** Converts the input text to title case.

**Values:** `text`

**Example:**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**Output:** `Hello World`

## Sentence Case Text (`sentence_case_text`)

**Purpose:** Converts the input text to sentence case.

**Values:** `text`

**Example:**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**Output:** `Hello world. This is fancymenu!`

## Snake Case Text (`snake_case_text`)

**Purpose:** Converts the input text to `snake_case`.

**Values:** `text`

**Example:**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**Output:** `hello_world`

## Kebab Case Text (`kebab_case_text`)

**Purpose:** Converts the input text to `kebab-case`.

**Values:** `text`

**Example:**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**Output:** `hello-world`

## Alternating Case Text (`alternating_case_text`)

**Purpose:** Converts the input text to alternating case.

**Values:** `text`

**Example:**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**Output:** `aLtErNaTiNg CaSe`

## Toggle Case Text (`toggle_case_text`)

**Purpose:** Toggles the case of every letter in the input text.

**Values:** `text`

**Example:**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**Output:** `tOGGLE cASE`

## Encode To Base64 (`base64_encode`)

**Purpose:** Encodes the given text as Base64.

**Values:** `text`

**Example:**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**Output:** `SGVsbG8gV29ybGQ=`

## Decode From Base64 (`base64_decode`)

**Purpose:** Decodes a Base64 string back to plain text.

**Values:** `text`

**Example:**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**Output:** `Hello World`

## File Text (`file_text`)

**Purpose:** Returns text lines from a file or URL. Can return all lines or just the last X lines.

**Values:** `path_or_url`, `mode`, `separator`, `last_lines`

**Example:**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parameters:
- `path_or_url`: File path or URL to read from
- `mode`: Either `"all"` (returns all lines) or `"last"` (returns only the last X lines)
- `separator`: Text used between lines (default: `"\n"`)
- `last_lines`: Number of lines to return when mode is `"last"` (default: `"1"`)

**Output:**

```text
First line
Second line
```

## Clipboard Content (`clipboard_content`)

**Purpose:** Returns the current text content stored in the system's clipboard.

**Values:** None

**Example:**

```
{"placeholder":"clipboard_content"}
```

**Output:** `Hello from the clipboard`

## Replace Text (`replace_text`)

**Purpose:** Replaces text in a string using literal text or regular expressions.

**Values:** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**Example:**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parameters:
- `text`: The input text to process
- `search`: The text or regex pattern to search for
- `replacement`: The replacement text
- `use_regex`: Whether to use regex (`"true"`) or literal matching (`"false"`)
- `replace_all`: Replace all occurrences (`"true"`) or just the first (`"false"`)

**Output:** `Hello FancyMenu! This is a test.`

## Switch Case (`switch_case`)

**Purpose:** Performs a switch-case operation based on a value.

**Values:** `value`, `cases`, `default`

**Example:**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**Output:** `first case` (if value is 1)

## Get Variable Value (FM Variable) (`getvariable`)

**Purpose:** Retrieves the value of a previously stored variable.

**Values:** `name`

**Example:**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**Output:** `42`

## Get NBT Data (`nbt_data_get`)

**Purpose:** Retrieves NBT data on the client (similar to the `/data get` command). Use the server variant `nbt_data_get_server` when connected to a server and you need authoritative server-side values.

**Values:** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**Example:**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parameters:
- `source_type`: Either `"entity"` or `"block"`
- `entity_selector`: Entity selector like `@s`, `@p`, `@e`, or UUID/name (for entities)
- `block_pos`: Block position in format `"x y z"` (for blocks)
- `nbt_path`: The NBT path to retrieve
- `scale`: Optional scaling factor for numeric values (default: `"1.0"`)
- `return_type`: How to return the data:
  - `"value"`: Default, returns the value (with optional scaling for numbers)
  - `"string"`: Returns the actual NBT data as string
  - `"snbt"`: Returns as SNBT (formatted NBT)
  - `"json"`: Returns as JSON-formatted component (for compound tags)

**Output:** `20` (for food level)

## Get NBT Data (Server-Side) (`nbt_data_get_server`)

**Purpose:** Queries NBT data on the server side (using a packet) and caches results briefly. Values mirror the client-side placeholder.

**Values:** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**Example:**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**Output:** `minecraft:diamond_sword`

## Last Death Message (`lastdeathmessage`)

**Purpose:** Returns the last recorded death message of the client player. Set `as_json_component` to `"true"` to get the raw JSON text component.

**Values:** `as_json_component`

**Example:**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**Output:** `Steve was slain by Zombie`

## Uptime Duration (`uptime_duration`)

**Purpose:** Returns how long FancyMenu has been loaded. By default the value is in seconds; set `output_as_millis` to `"true"` to receive milliseconds.

**Values:** `output_as_millis`

**Example:**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**Output:** `742` (seconds since load)

## World Save Names (`level_save_names`)

**Purpose:** Lists all local world save names joined by the chosen separator. Runs on the client thread.

**Values:** `separator`

**Example:**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**Output:** `Creative Test, Survival World, Hardcore`

## World Save Data (`level_save_data`)

**Purpose:** Returns serialized level data for the given world name (must match the display name shown in the saves list).

**Values:** `level_name`

**Example:**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**Output:** `{"name":"Survival World","gameMode":"survival",...}`

## Number Base Converter (`number_base_convert`)

**Purpose:** Converts a number (integer or fractional) from one base to another (2–36). Defaults to decimal if bases are not provided.

**Values:** `input`, `from_base`, `to_base`

**Example:**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**Output:** `43.8`

## File Size (`file_size`)

**Purpose:** Returns the size of a local file in bytes. Only local paths are allowed.

**Values:** `path`

**Example:**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Output:** `1284`

## File MD5 (`file_md5`)

**Purpose:** Returns the MD5 hash of a local file as a lowercase hex string.

**Values:** `path`

**Example:**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Output:** `d41d8cd98f00b204e9800998ecf8427e`

# Practical Examples

## Creating a Dynamic Memory Display
```
Used RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Making a Real-time Clock
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

## Creating a System Info Display
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## Player Status HUD
```
Health: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armor: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
XP Level: {"placeholder":"current_player_level"}
```

## Complex Calculation with Nested Placeholders
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Coordinate Display with Rounding
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Best Practices

1. **Cache Expensive Operations**: Some placeholders (like those that read system information) can be resource-intensive. Consider using variables to store their values if you need to use them multiple times.

2. **Use Appropriate Decimal Settings**: When working with calculations, use the `decimal` parameter appropriately. Set it to `false` when you need integers and `true` when you need precise decimal values.

3. **Handle Missing Values**: Always consider what should happen if a placeholder returns no value. You might want to provide default values in such cases.

4. **Test Performance**: When using many placeholders or complex nested structures, test the performance impact, especially on lower-end systems.

5. **Use Advanced Sizing/Positioning**: For dynamic UI elements, combine placeholders with advanced sizing and positioning to create responsive layouts.

6. **Combine with Variables**: Use placeholders together with variables for even more dynamic content that can be updated through actions.

# Common Issues and Solutions

## Placeholder Not Updating
If a placeholder's value isn't updating as expected, check:
- Whether the placeholder is properly formatted
- If you're using the correct case for placeholder IDs
- Whether the placeholder requires specific conditions to update

## Nested Placeholders Not Working
When nesting placeholders:
- Ensure proper escaping of quotes
- Verify that each nested placeholder is valid on its own

## Performance Issues
If you notice performance issues:
- Reduce the number of placeholders used
- Avoid unnecessary nesting
- Consider using variables for frequently accessed values
- Use the appropriate placeholder for your needs (e.g., don't use real-time placeholders when static values would suffice)
