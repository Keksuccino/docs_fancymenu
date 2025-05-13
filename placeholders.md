---
title: Placeholders
description: How to use placeholders.
published: true
date: 2025-05-13T18:57:07.427Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:37.364Z
---

# Placeholders

Placeholders are dynamic values that get replaced with actual content when they are used. In FancyMenu, placeholders allow you to insert dynamic content into various elements like text, buttons, and loading requirements. Think of them as variables that get evaluated and replaced with their actual values when your layouts are displayed.

# General Information

## Basic Syntax
Placeholders in FancyMenu use a JSON-like syntax:
```
{"placeholder":"placeholder_id","values":{"value_name":"value"}}
```

For example, to display the player's name:
```
{"placeholder":"playername"}
```

## Nesting Placeholders
One of the most powerful features of FancyMenu's placeholder system is the ability to nest placeholders within other placeholders. This means you can use the output of one placeholder as an input for another.

Example of nested placeholders:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
This example takes the maximum RAM value and divides it by 1024 to convert it from MB to GB.

# Using Placeholders

Most elements that have text inputs support placeholders. You can see if a text input supports placeholders when editing it. If the full-screen **text editor** opens when editing the text, it supports placeholders. 

To find a **list of all placeholders**, just click on the **Placeholders** button in the **top-right corner** of the **text editor**.

Clicking on a placeholder in the placeholder list will paste it to the text content!

# Some Placeholders In Detail

## Player Information

### Player Name (`playername`)
Returns the current player's username.
```
{"placeholder":"playername"}
```
Example output: `Steve`

### Player UUID (`playeruuid`)
Returns the player's unique identifier.
```
{"placeholder":"playeruuid"}
```
Example output: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft Instance

### Minecraft Version (`mcversion`)
Returns the current Minecraft version.
```
{"placeholder":"mcversion"}
```
Example output: `1.19.2`

### Mod Loader Version (`loaderver`)
Returns the version of the mod loader (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Example output: `43.2.0`

### Mod Loader Name (`loadername`)
Returns the name of the mod loader.
```
{"placeholder":"loadername"}
```
Example output: `Forge`

### Mod Version (`modversion`)
Returns the version of a specific mod.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Example output: `2.14.9`

### Total Mods (`totalmods`)
Returns the total number of mods installed.
```
{"placeholder":"totalmods"}
```
Example output: `45`

### Loaded Mods (`loadedmods`)
Returns the number of currently loaded mods.
```
{"placeholder":"loadedmods"}
```
Example output: `43`

### World Load Progress (`world_load_progress`)
Returns the current world loading progress as a percentage.
```
{"placeholder":"world_load_progress"}
```
Example output: `75`

### Minecraft Option Value (`minecraft_option_value`)
Returns the value of a Minecraft option.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Example output: `70`

### Last World or Server (`last_world_server`)
Returns information about the last world or server accessed.
```
{"placeholder":"last_world_server","values":{"type":"both"}}
```
Possible types: `"both"`, `"server"`, `"world"`

## GUI (Screens / Menus)

### Screen Width (`guiwidth`)
Returns the current screen width.
```
{"placeholder":"guiwidth"}
```
Example output: `1920`

### Screen Height (`guiheight`)
Returns the current screen height.
```
{"placeholder":"guiheight"}
```
Example output: `1080`

### Screen Identifier (`screenid`)
Returns the identifier of the current screen.
```
{"placeholder":"screenid"}
```
Example output: `title_screen`

### Element Width (`elementwidth`)
Returns the width of a specific element.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Example output: `200`

### Element Height (`elementheight`)
Returns the height of a specific element.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Example output: `20`

### Element X Position (`elementposx`)
Returns the X position of a specific element.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Example output: `150`

### Element Y Position (`elementposy`)
Returns the Y position of a specific element.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Example output: `100`

### Mouse Position X (`mouseposx`)
Returns the current X position of the mouse.
```
{"placeholder":"mouseposx"}
```
Example output: `960`

### Mouse Position Y (`mouseposy`)
Returns the current Y position of the mouse.
```
{"placeholder":"mouseposy"}
```
Example output: `540`

### GUI Scale (`guiscale`)
Returns the current GUI scale.
```
{"placeholder":"guiscale"}
```
Example output: `2`

### Vanilla Button Label (`vanillabuttonlabel`)
Returns the label/text of a vanilla widget/button.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Example output: `Options...`

## Player Status

### Current Player Health (`current_player_health`)
Returns the player's current health points.
```
{"placeholder":"current_player_health"}
```
Example output: `20.0`

### Max Player Health (`max_player_health`)
Returns the player's maximum health points.
```
{"placeholder":"max_player_health"}
```
Example output: `20.0`

### Current Player Health Percentage (`current_player_health_percent`)
Returns the player's health as a percentage.
```
{"placeholder":"current_player_health_percent"}
```
Example output: `100`

### Current Player Absorption Health (`current_player_absorption_health`)
Returns the player's absorption health points (golden hearts).
```
{"placeholder":"current_player_absorption_health"}
```
Example output: `4.0`

### Max Player Absorption Health (`max_player_absorption_health`)
Returns the maximum absorption health.
```
{"placeholder":"max_player_absorption_health"}
```
Example output: `4.0`

### Current Player Absorption Health Percentage (`current_player_absorption_health_percentage`)
Returns the player's absorption health as a percentage.
```
{"placeholder":"current_player_absorption_health_percentage"}
```
Example output: `100`

### Current Player Hunger (`current_player_hunger`)
Returns the player's current hunger level.
```
{"placeholder":"current_player_hunger"}
```
Example output: `20`

### Max Player Hunger (`max_player_hunger`)
Returns the maximum hunger level.
```
{"placeholder":"max_player_hunger"}
```
Example output: `20`

### Current Player Hunger Percentage (`current_player_hunger_percentage`)
Returns the player's hunger as a percentage.
```
{"placeholder":"current_player_hunger_percentage"}
```
Example output: `100`

### Current Player Armor (`current_player_armor`)
Returns the player's current armor value.
```
{"placeholder":"current_player_armor"}
```
Example output: `20`

### Max Player Armor (`max_player_armor`)
Returns the maximum armor value.
```
{"placeholder":"max_player_armor"}
```
Example output: `20`

### Current Player Armor Percentage (`current_player_armor_percentage`)
Returns the player's armor as a percentage.
```
{"placeholder":"current_player_armor_percentage"}
```
Example output: `100`

### Current Player Oxygen (`current_player_oxygen`)
Returns the player's current oxygen level (air bubbles).
```
{"placeholder":"current_player_oxygen"}
```
Example output: `300`

### Max Player Oxygen (`max_player_oxygen`)
Returns the maximum oxygen level.
```
{"placeholder":"max_player_oxygen"}
```
Example output: `300`

### Current Player Oxygen Percentage (`current_player_oxygen_percentage`)
Returns the player's oxygen level as a percentage.
```
{"placeholder":"current_player_oxygen_percentage"}
```
Example output: `100`

### Current Player Level (`current_player_level`)
Returns the player's current experience level.
```
{"placeholder":"current_player_level"}
```
Example output: `30`

### Current Player Experience (`current_player_exp`)
Returns the player's total experience points.
```
{"placeholder":"current_player_exp"}
```
Example output: `1250`

### Current Player Experience Progress (`current_player_exp_progress`)
Returns the player's experience progress to the next level as a percentage.
```
{"placeholder":"current_player_exp_progress"}
```
Example output: `75`

### Player Attack Strength Percentage (`player_attack_strength`)
Returns the player's attack cooldown as a percentage.
```
{"placeholder":"player_attack_strength"}
```
Example output: `100`

### Player Gamemode (`player_gamemode`)
Returns the player's current game mode.
```
{"placeholder":"player_gamemode"}
```
Example output: `survival`

### Player View Direction (`player_view_direction`)
Returns the direction the player is facing.
```
{"placeholder":"player_view_direction"}
```
Example output: `north`

### Player X Coordinate (`player_x_coordinate`)
Returns the player's X position in the world.
```
{"placeholder":"player_x_coordinate"}
```
Example output: `125`

### Player Y Coordinate (`player_y_coordinate`)
Returns the player's Y position in the world.
```
{"placeholder":"player_y_coordinate"}
```
Example output: `64`

### Player Z Coordinate (`player_z_coordinate`)
Returns the player's Z position in the world.
```
{"placeholder":"player_z_coordinate"}
```
Example output: `-250`

## Mount Information

### Current Mount Health (`current_mount_health`)
Returns the current health of the entity the player is riding.
```
{"placeholder":"current_mount_health"}
```
Example output: `30.0`

### Max Mount Health (`max_mount_health`)
Returns the maximum health of the entity the player is riding.
```
{"placeholder":"max_mount_health"}
```
Example output: `30.0`

### Current Mount Health Percentage (`current_mount_health_percentage`)
Returns the mount's health as a percentage.
```
{"placeholder":"current_mount_health_percentage"}
```
Example output: `100`

### Current Mount Jump Meter (`current_mount_jump_meter`)
Returns the mount's jump power meter value.
```
{"placeholder":"current_mount_jump_meter"}
```
Example output: `75`

## Boss Information

### Current Boss Health (`current_boss_health`)
Returns the health of the active boss.
```
{"placeholder":"current_boss_health"}
```
Example output: `150.0`

### Boss Name (`boss_name`)
Returns the name of the active boss.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Example output: `Ender Dragon`

### Boss Count (`boss_count`)
Returns the number of active bosses.
```
{"placeholder":"boss_count"}
```
Example output: `1`

## Status Effects

### Active Effects Count (`effects_count`)
Returns the number of active potion effects.
```
{"placeholder":"effects_count"}
```
Example output: `3`

### Active Effect (`active_effect`)
Returns information about a specific active effect.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Example output: `minecraft:speed`

## Inventory & Items

### Active Hotbar Slot (`active_hotbar_slot`)
Returns the currently selected hotbar slot (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Example output: `4`

### Slot Item (`slot_item`)
Returns information about an item in a specific inventory slot.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Example output: `minecraft:diamond_sword`

## World Information

### Game Time (`gametime`)
Returns the current in-game time.
```
{"placeholder":"gametime"}
```
Example output: `18000`

### World Day Time (`world_day_time`)
Returns the current world day time.
```
{"placeholder":"world_day_time"}
```
Example output: `13000`

### World Day Time Hour (`world_daytime_hour`)
Returns the hour component of world time (00-23).
```
{"placeholder":"world_daytime_hour"}
```
Example output: `12`

### World Day Time Minute (`world_daytime_minute`)
Returns the minute component of world time (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Example output: `30`

### World Difficulty (`world_difficulty`)
Returns the current world difficulty.
```
{"placeholder":"world_difficulty"}
```
Example output: `normal`

### Current Title (`current_title`)
Returns the currently displayed title text.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Example output: `Game Over!`

### Current Server IP (`current_server_ip`)
Returns the IP of the connected server.
```
{"placeholder":"current_server_ip"}
```
Example output: `mc.hypixel.net`

## Server Information

### Server MOTD (`servermotd`)
Returns the Message of the Day of a server.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Example output: `Welcome to Hypixel!`

### Server Ping (`serverping`)
Returns the ping to a server in milliseconds.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Example output: `54`

### Server Player Count (`serverplayercount`)
Returns the player count of a server.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Example output: `25000/30000`

### Server Status (`serverstatus`)
Returns the online/offline status of a server.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Example output: `§aOnline` or `§cOffline`

### Server Version (`serverversion`)
Returns the Minecraft version of a server.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Example output: `1.19.2`

## Real-time Date & Time

### Year (`realtimeyear`)
Returns the current year.
```
{"placeholder":"realtimeyear"}
```
Example output: `2024`

### Month (`realtimemonth`)
Returns the current month (01-12).
```
{"placeholder":"realtimemonth"}
```
Example output: `01`

### Day (`realtimeday`)
Returns the current day of the month (01-31).
```
{"placeholder":"realtimeday"}
```
Example output: `27`

### Hour (`realtimehour`)
Returns the current hour (00-23).
```
{"placeholder":"realtimehour"}
```
Example output: `14`

### Minute (`realtimeminute`)
Returns the current minute (00-59).
```
{"placeholder":"realtimeminute"}
```
Example output: `30`

### Second (`realtimesecond`)
Returns the current second (00-59).
```
{"placeholder":"realtimesecond"}
```
Example output: `45`

### Unix Timestamp (`unix_time`)
Returns the current Unix timestamp in milliseconds.
```
{"placeholder":"unix_time"}
```
Example output: `1716552478123`

## System Information

### CPU Info (`cpuinfo`)
Returns information about the CPU.
```
{"placeholder":"cpuinfo"}
```
Example output: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

### JVM CPU Usage (`jvmcpu`)
Returns the JVM's CPU usage as a percentage.
```
{"placeholder":"jvmcpu"}
```
Example output: `25.5`

### OS CPU Usage (`oscpu`)
Returns the OS CPU usage as a percentage.
```
{"placeholder":"oscpu"}
```
Example output: `42.8`

### GPU Info (`gpuinfo`)
Returns information about the GPU.
```
{"placeholder":"gpuinfo"}
```
Example output: `NVIDIA GeForce RTX 3080`

### Java Version (`javaver`)
Returns the Java version.
```
{"placeholder":"javaver"}
```
Example output: `17.0.2`

### JVM Name (`jvmname`)
Returns the name of the Java Virtual Machine.
```
{"placeholder":"jvmname"}
```
Example output: `OpenJDK 64-Bit Server VM`

### OpenGL Version (`glver`)
Returns the OpenGL version.
```
{"placeholder":"glver"}
```
Example output: `4.6.0 NVIDIA 516.94`

### Operating System (`osname`)
Returns the operating system name.
```
{"placeholder":"osname"}
```
Example output: `Windows 10`

### FPS (`fps`)
Returns the current frames per second.
```
{"placeholder":"fps"}
```
Example output: `120`

## Memory Information

### Used RAM (`usedram`)
Returns the amount of RAM currently in use (MB).
```
{"placeholder":"usedram"}
```
Example output: `4096`

### Max RAM (`maxram`)
Returns the maximum allocated RAM (MB).
```
{"placeholder":"maxram"}
```
Example output: `8192`

### RAM Usage Percentage (`percentram`)
Returns the percentage of RAM currently in use.
```
{"placeholder":"percentram"}
```
Example output: `50`

## Audio

### Audio Element Volume (`audio_element_volume`)
Returns the volume of an audio element.
```
{"placeholder":"audio_element_volume","values":{"element_identifier":"background_music"}}
```
Example output: `0.5`

### Audio Element Track (`audio_element_current_track`)
Returns the track name of an audio element.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Example output: `Cool Track Name`

### Audio Element Duration (`audio_duration`)
Returns the total duration of an audio track in MM:SS format.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Example output: `03:45`

### Audio Element Playtime (`audio_element_playtime`)
Returns the current playtime of an audio track.
```
{"placeholder":"audio_element_playtime","values":{"element_identifier":"background_music"}}
```
Example output: `01:30`

### Audio Element Playing State (`audio_playing_state`)
Returns whether an audio element is playing (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Example output: `true`

## Math

### Calculator (`calc`)
The calculator placeholder is a powerful tool that allows you to perform mathematical calculations within your layouts. It supports a wide range of mathematical operations and can work with both decimal and integer numbers.

#### Basic Syntax
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

The calculator has two main parameters:
- `decimal`: Determines whether the result should include decimal places (`true`) or be rounded to integers (`false`)
- `expression`: The mathematical expression to evaluate

#### Supported Operations
The calculator supports these mathematical operations:
- Basic arithmetic: `+` (addition), `-` (subtraction), `*` (multiplication), `/` (division)
- Parentheses: `( )` for grouping operations
- Power: `^` for exponents
- Square root: `sqrt()`
- Trigonometric functions: `sin()`, `cos()`, `tan()`
- Mathematical constants: `pi`, `e`
- Absolute value: `abs()`
- Logarithms: `log()`, `ln()`

### Random Number (`random_number`)
Generates a random number within a specified range.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Example output: `42`

### Max Number (`maxnum`)
Returns the larger of two numbers.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Example output: `20`

### Min Number (`minnum`)
Returns the smaller of two numbers.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Example output: `10`

### Absolute Number (`absolute_number`)
Returns the absolute value of a number.
```
{"placeholder":"absolute_number","values":{"number":"-10.5"}}
```
Example output: `10.5`

### Negate Number (`negate_number`)
Returns the negated value of a number.
```
{"placeholder":"negate_number","values":{"number":"10.5"}}
```
Example output: `-10.5`

### Pi (`math_pi`)
Returns the value of π.
```
{"placeholder":"math_pi"}
```
Example output: `3.141592653589793`

### Sine (`math_sin`)
Returns the sine of an angle.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Example output: `0.7071067811865476`

### Cosine (`math_cos`)
Returns the cosine of an angle.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Example output: `0.7071067811865476`

### Tangent (`math_tan`)
Returns the tangent of an angle.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Example output: `1.0`

### Floor (`math_floor`)
Rounds a number down to the nearest integer.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Example output: `3`

### Ceiling (`math_ceil`)
Rounds a number up to the nearest integer.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Example output: `4`

### Round (`math_round`)
Rounds a number to the nearest integer.
```
{"placeholder":"math_round","values":{"num":"3.14"}}
```
Example output: `3`

### Sign (`math_sign`)
Returns the sign of a number (1 for positive, -1 for negative, 0 for zero).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Example output: `-1`

### Hyperbolic Sine (`math_sinh`)
Returns the hyperbolic sine of an angle.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Example output: `1.1752011936438014`

### Hyperbolic Cosine (`math_cosh`)
Returns the hyperbolic cosine of an angle.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Example output: `1.5430806348152437`

### Hyperbolic Tangent (`math_tanh`)
Returns the hyperbolic tangent of an angle.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Example output: `0.7615941559557649`

## Text

### Split Text (`split_text`)
Splits text using a specified delimiter.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Example output: `world`

### Trim Text (`trim_text`)
Removes leading and trailing whitespace.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Example output: `hello world`

### Crop Text (`crop_text`)
Removes characters from the start and end of text.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Example output: `ello worl`

### Stringify (`stringify`)
Stringifies a text by escaping all syntax characters.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Example output: `text with \{special\} \"characters\"`

### Localization (`local`)
Retrieves localized text for a key.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Example output: `Singleplayer`

### Web Text (`webtext`)
Retrieves text content from a web URL.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Example output: Text content from the URL

### Random Text (`randomtext`)
Returns a random line from a text file.
```
{"placeholder":"randomtext","values":{"path":"randomtexts.txt","interval":"10"}}
```
Example output: A random line from the file

### JSON Parser (`json`)
Parses JSON data from a file or URL.
```
{"placeholder":"json","values":{"source":"path_or_link_to_json","json_path":"$.some.json.path"}}
```
Example output: The value at the specified JSON path

### Absolute Path (`absolute_path`)
Returns the absolute path of a file.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Example output: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Switch Case

### Switch Case (`switch_case`)
Performs a switch-case operation based on a value.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Example output: `first case` (if value is 1)

## Variables

### Get Stored Variable (`getvariable`)
Retrieves the value of a previously stored variable.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Example output: Depends on the stored value

# Practical Examples

## Creating a Dynamic Memory Display
```
Used RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Making a Real-time Clock
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
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