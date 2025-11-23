---
title: Listeners
description: How to create and use listeners in FancyMenu.
published: true
date: 2025-11-23T08:25:12.146Z
tags: 
editor: markdown
dateCreated: 2025-11-23T08:24:21.102Z
---

# Listeners

Starting with FancyMenu v3.8.0, there is a new feature called "listeners".

Listeners execute action scripts when specific client or gameplay events happen.
They can supply variables for actions, placeholders, and requirements nested in the listener.

Other than most things in FancyMenu, listeners are not locked to a screen or overlay. They constantly run in the background, listening to their events. As soon as a listener gets fired, it executes its action script, even if there is no screen open at that time.

# Using Listeners

To create a new listener that listeners to an event and executes an action script, click on **menu bar -> Customization -> Manage Listeners** while **NOT** in the layout editor. There you can find an easy-to-use UI for creating and managing listeners.

# Listeners in Detail

This list should include most, if not all, of FancyMenu's listeners. It is possible that the list is not always up-to-date due to updates of the mod.

## On Keyboard Key Pressed
- Triggers whenever a key is pressed (repeats while held; works in screens and in-game).
- Variables:
  - `$$key_name` – display name of the key
  - `$$key_keycode` – GLFW key code
  - `$$key_scancode` – GLFW scan code
  - `$$key_modifiers` – active modifier bit mask

## On Keyboard Key Released
- Triggers when a key is released (screens and in-game).
- Variables:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- Fires when a character is typed while a screen is open.
- Variables:
  - `$$char` – typed character

## On Mouse Moved in Screen
- Fires whenever the mouse moves while a screen is open.
- Variables:
  - `$$mouse_pos_x` – current X
  - `$$mouse_pos_y` – current Y
  - `$$mouse_move_delta_x` – X delta since last event
  - `$$mouse_move_delta_y` – Y delta since last event

## On Mouse Button Clicked
- Fires when a mouse button is pressed (screens and in-game).
- Variables:
  - `$$button` – left/right/middle
  - `$$mouse_pos_x` – current X
  - `$$mouse_pos_y` – current Y

## On Mouse Button Released
- Fires when a mouse button is released (screens and in-game).
- Variables:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- Fires when the mouse wheel is scrolled while a screen is open.
- Variables:
  - `$$scroll_delta_y` – vertical scroll amount

## On Screen Opened
- Runs right after any screen becomes active; can be used to override it.
- Variables:
  - `$$screen_identifier` – identifier of the opened screen

## On Screen Closed
- Runs immediately after a screen closes.
- Variables:
  - `$$screen_identifier` – identifier of the closed screen

## On Quit Minecraft
- Fires once when the client begins shutting down.
- Variables:
  - `$$timestamp_millis` – epoch millis when quitting
  - `$$timestamp_iso` – ISO-8601 timestamp of quit moment

## On Death
- Runs when the vanilla death screen opens for the local player.
- Variables:
  - `$$days_survived` – days since last death
  - `$$death_reason_string` – plain-text cause
  - `$$death_reason_component` – JSON component cause
  - `$$death_pos_x` – death X coordinate
  - `$$death_pos_y` – death Y coordinate
  - `$$death_pos_z` – death Z coordinate

## On Variable Updated [FM Variable]
- Fires whenever a FancyMenu variable is set/updated.
- Variables:
  - `$$var_name` – variable name
  - `$$old_value` – previous value
  - `$$new_value` – new value

## On File Downloaded via Action
- Fires after the “Download File to Game Directory” action finishes.
- Variables:
  - `$$download_url` – download source
  - `$$target_file_path` – saved file path
  - `$$download_succeeded` – true/false

## On File Selected
- Fires after the “Select File” action completes.
- Variables:
  - `$$selected_file_path` – absolute chosen file path or empty if cancelled
  - `$$target_file_path` – resolved path inside instance
  - `$$selection_succeeded` – true if copy succeeded
  - `$$selection_cancelled` – true if dialog closed
  - `$$failure_reason` – error info on failure

## On Chat Message Received
- Fires when a normal player chat line appears on the client.
- Variables:
  - `$$chat_message_string` – plain text line
  - `$$chat_message_component` – full JSON component
  - `$$sender_uuid` – sender UUID or ERROR
  - `$$sender_name` – sender name or ERROR

## On Chat Message Sent
- Fires when the local player sends a chat message.
- Variables:
  - `$$chat_message_string` – plain text line
  - `$$chat_message_component` – full JSON component

## On Effect Gained
- Fires when the player gains a status effect.
- Variables:
  - `$$effect_key` – effect resource location
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – ticks remaining

## On Effect Lost
- Fires when the player loses a status effect.
- Variables:
  - `$$effect_key` – expired effect
  - `$$effect_type` – category

## On Experience Changed
- Fires whenever the player’s total XP changes.
- Variables:
  - `$$new_experience_amount` – after change
  - `$$old_experience_amount` – before change
  - `$$is_level_up` – TRUE if level increased

## On Damage Taken
- Fires once per hit when the player takes damage.
- Variables:
  - `$$damage_amount` – health removed
  - `$$damage_type` – damage type resource location
  - `$$is_fatal_damage` – TRUE if lethal
  - `$$damage_source` – attacker resource location or NONE

## On Started Freezing
- Fires when the player starts freezing.
- Variables:
  - `$$freezing_intensity` – 0.0 none, 1.0 fully frozen

## On Stopped Freezing
- Fires when the player stops freezing.
- Variables:
  - (none)

## On Fully Frozen
- Fires once when the player becomes fully frozen.
- Variables:
  - (none)

## On Start Looking At Block
- Fires once when the crosshair first points at a block (max 20 blocks distance).
- Variables:
  - `$$block_key` – targeted block
  - `$$block_pos_x` – block X
  - `$$block_pos_y` – block Y
  - `$$block_pos_z` – block Z
  - `$$distance_to_player` – eyes to hit position

## On Stop Looking At Block
- Fires when the crosshair stops pointing at a block (reports last targeted block, max 20 blocks).
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- Fires once when the crosshair first points at an entity (max 20 blocks).
- Variables:
  - `$$entity_key` – targeted entity type
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- Fires when the crosshair stops pointing at an entity (reports last targeted entity, max 20 blocks).
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **Requires FancyMenu on the server.** Fires when any entity spawns anywhere on the connected world/server.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player` – −1 if other dimension
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **Requires FancyMenu on the server.** Fires when any entity dies on the connected world/server.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player` – −1 if other dimension
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## On Entity Starts Being In Sight
- Fires when an entity first becomes visible within 200 blocks.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- Fires when a previously visible entity leaves view or moves beyond 200 blocks.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- Fires when the player successfully interacts with an entity.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- Fires when the player begins riding an entity.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- Fires when the player stops riding their current entity.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- Fires when the player breaks a block.
- Variables:
  - `$$block_key`
  - `$$broke_with_item_key` – tool used or EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- Fires when the player places a block.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- Fires when the player successfully interacts with a block.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- Fires when the player steps onto a block.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- Fires when the player enters a new biome.
- Variables:
  - `$$biome_key` – entered biome

## On Leave Biome
- Fires when the player leaves their current biome.
- Variables:
  - `$$biome_key` – biome just left

## On Enter Structure
- **Requires FancyMenu on the server.** Coarse structure-area detection; can trigger near/above/below the structure.
- Variables:
  - `$$structure_key` – entered structure

## On Leave Structure
- **Requires FancyMenu on the server.** Coarse detection; can trigger near the structure footprint.
- Variables:
  - `$$structure_key` – structure just left

## On Enter Structure (High Precision)
- **Requires FancyMenu on the server.** Fires when the player steps into a structure’s bounding boxes.
- Variables:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **Requires FancyMenu on the server.** Fires after the player exits a structure’s bounding boxes.
- Variables:
  - `$$structure_key`

## On Dimension Entered
- Fires when the player enters a new dimension.
- Variables:
  - `$$dimension_key` – entered dimension

## On Start Swimming
- Fires when the player starts swimming.
- Variables:
  - `$$fluid_type` – fluid resource location

## On Stop Swimming
- Fires when the player stops swimming.
- Variables:
  - `$$fluid_type` – fluid where swimming stopped

## On Start Touching Fluid
- Fires when the player starts touching a fluid.
- Variables:
  - `$$fluid_type` – touched fluid

## On Stop Touching Fluid
- Fires when the player stops touching a fluid.
- Variables:
  - `$$fluid_type` – fluid no longer touched

## On Music Track Started
- Fires when a new music track begins.
- Variables:
  - `$$track_resource_location` – audio file
  - `$$track_display_name` – human-readable name or UNKNOWN
  - `$$track_artist` – artist or UNKNOWN
  - `$$track_duration_ms` – milliseconds (0 if unknown)

## On Music Track Stopped
- Fires when the current music track ends or is replaced.
- Variables:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- Fires when a positional world sound starts near the player.
- Variables:
  - `$$sound_resource_location` – sound file
  - `$$sound_display_name` – subtitle name when available
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – degrees 0–360 relative to facing

## On Weather Changed
- Fires when weather changes globally or locally (biome change or going indoors can retrigger).
- Variables:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE if snow renders
  - `$$weather_can_rain` – TRUE if rain renders

## On Started Burning
- Fires when the player starts burning.
- Variables:
  - (none)

## On Stopped Burning
- Fires when the player stops burning.
- Variables:
  - (none)

## On Started Drowning
- Fires when the player begins taking drowning damage.
- Variables:
  - (none)

## On Position Changed
- Fires whenever the player’s block position changes.
- Variables:
  - `$old_pos_x` – previous block X
  - `$old_pos_y` – previous block Y
  - `$old_pos_z` – previous block Z
  - `$new_pos_x` – new block X
  - `$new_pos_y` – new block Y
  - `$new_pos_z` – new block Z

## On Started Running
- Fires when the player starts sprinting.
- Variables:
  - (none)

## On Stopped Running
- Fires when the player stops sprinting.
- Variables:
  - (none)

## On Jump
- Fires whenever the player jumps.
- Variables:
  - (none)

## On Server Joined
- Fires after successfully joining a multiplayer server.
- Variables:
  - `$$server_ip` – joined server address

## On Server Left
- Fires after disconnecting from a multiplayer server.
- Variables:
  - `$$server_ip` – left server address

## Singleplayer World Entered
- Fires after a singleplayer world finishes loading and control is returned.
- Variables:
  - `$$world_name` – display name
  - `$$world_save_path` – absolute save folder
  - `$$world_difficulty` – difficulty key
  - `$$world_cheats_allowed` – TRUE if cheats enabled
  - `$$world_icon_path` – absolute icon path
  - `$$world_is_first_join` – TRUE on very first visit

## Singleplayer World Left
- Fires after a singleplayer world closes and finishes saving.
- Variables:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- Fires when another player joins the current world/server.
- Variables:
  - `$$player_name` – name of joining player
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- Fires when another player leaves the current world/server.
- Variables:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- Fires when another player in the current world dies.
- Variables:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- Fires when the player picks up an item entity.
- Variables:
  - `$$item_key` – picked-up item resource location

## On Item Dropped
- Fires when the player drops an item from their inventory.
- Variables:
  - `$$item_key` – dropped item resource location

## On Item Consumed
- Fires when the player finishes consuming an item.
- Variables:
  - `$$item_key` – consumed item

## On Item Used
- Fires when the player uses an item.
- Variables:
  - `$$item_key` – used item
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – target entity type or empty
  - `$$used_on_block_key` – target block or empty
  - `$$target_pos_x` – target X or -1
  - `$$target_pos_y` – target Y or -1
  - `$$target_pos_z` – target Z or -1

## On Item Broke
- Fires when an item in the player’s inventory breaks.
- Variables:
  - `$$item_key` – broken item
  - `$$item_type` – tool/armor/other