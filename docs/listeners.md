---
title: Listeners
description: How to create and use listeners in FancyMenu.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-11-23T08:24:21.102Z
---

# Listeners

Listeners run [action scripts](./action-scripts) when specific events happen. They are not tied to an open screen, so they can also run while playing or loading.

Listeners can provide `$$` values, such as a pressed key or clicked mouse button, to their actions and requirements.

> [!CAUTION]
> A listener can run file, network, command, clipboard, resource-pack, or link actions without a screen being open. Import listeners only from sources you trust.

# Using Listeners

Outside the Layout Editor, open **menu bar -> Customization -> Manage Listeners** to create or edit listeners.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Manage listeners" style="max-width:800px;width:100%;height:auto;">

# Listener Variables

Listeners can provide read-only values to their actions and requirements. Use their `$$` names in supported text fields.

For example, use [**On Keyboard Key Pressed**](#on-keyboard-key-pressed-keyboard_key_pressed) with the [**Print to Game Log** action](./action-scripts#print-to-game-log-print_to_log). The value `Key pressed! The key is: $$key_name` inserts the pressed key's name.

> [!WARNING]
> Listener variables are separate from FancyMenu's [stored variables](./variables). Stored-variable actions, requirements, and placeholders do not work with `$$` values.

Listener variable names are case-sensitive and only work inside that listener's script.

Treat values from chat, remote servers, files, and user input as untrusted. Do not insert them directly into paths, URLs, or commands.

Listener variables are strings. When information is unavailable, a listener may return a documented sentinel such as `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1`, or an empty string. Test these values before inserting listener data into paths, commands, or URLs.

# Listeners in Detail

This section lists FancyMenu's built-in listeners.

## On Markdown Text Clicked (`text_clicked`)
- Fires when [Markdown text with a `click:` event](./text-formatting#click-and-hover-events) is clicked, for example `[Open](click:open_menu)`.
- Variables:
  - `$$text_event_id` – event ID from the Markdown link

## On Markdown Text Hovered (`text_hovered`)
- Fires when [Markdown text with a `hover:` event](./text-formatting#click-and-hover-events) is hovered, for example `[Hint](hover:show_hint)`.
- Variables:
  - `$$text_event_id` – event ID from the Markdown link

## On ZIP Extracted via Action (`zip_extracted_via_action`)
- Fires when the [**Extract ZIP File In Game Directory** action](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir) finishes.
- Variables:
  - `$$source_zip_path` – normalized user-facing source path; game-directory paths may be returned as `/...`, while conventional Minecraft-directory paths may use `.minecraft/...`
  - `$$target_folder_path` – normalized user-facing target path using the same path forms
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – error text when extraction failed

## On Element Spawned (`element_spawned_via_action`)
- Fires when a supported FancyMenu feature or add-on dynamically spawns an element instance.
- Variables:
  - `$$element_type` – spawned element type
  - `$$element_identifier` – spawned element identifier
  - `$$target_screen` – target screen identifier

## On Animated Texture Started Playing (`animated_texture_started_playing`)
- Fires when an [animated texture](./fma) starts playing.
- Variables:
  - `$$texture_source` – texture source
  - `$$texture_source_type` – source type
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing (`animated_texture_finished_playing`)
- Fires when an animated texture finishes playing.
- Variables:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed (`video_playback_status_changed`)
- Fires when a [Video element or menu background](./video) changes playback status.
- Variables:
  - `$$video_source` – video source
  - `$$video_source_type` – source type
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED`, or `FINISHED`

## On System Message Received in Chat (`system_message_received_in_chat`)
- Fires when the client receives a system chat message, such as command feedback.
- Variables:
  - `$$system_message_string` – plain text message
  - `$$system_message_component` – JSON component

## On FM Data Received (`fm_data_received`)
- Fires when a server sends [FM Data](./fm-data) to this client via `/fmdata send`.
- Variables:
  - `$$data_identifier` – data identifier string
  - `$$data` – data payload
  - `$$sent_by` – server IP or `integrated_server`

## On Remote Server Connected (`remote_server_connected`)
- Fires after a [remote server connection](./remote-server-communication) successfully opens.
- Variables:
  - `$$request_id` – cached request ID
  - `$$remote_server_url` – remote server URL

## On Remote Server Data Received (`remote_server_data_received`)
- Fires when text data is received from a connected remote server.
- Variables:
  - `$$request_id` – request ID
  - `$$remote_server_url` – remote server URL
  - `$$data` – received payload

## On Remote Server Connection Closed (`remote_server_connection_closed`)
- Fires when a remote server connection closes.
- Variables:
  - `$$request_id` – request ID
  - `$$remote_server_url` – remote server URL
  - `$$intentionally_closed` – TRUE if closed by an action
  - `$$crashed` – TRUE if the connection crashed unexpectedly
  - `$$unknown_close_reason` – TRUE if no known close reason was available

## On Keyboard Key Pressed (`keyboard_key_pressed`)
- Triggers whenever a key is pressed (repeats while held; works in screens and in-game).
- Variables:
  - `$$key_name` – display name of the key
  - `$$key_keycode` – GLFW key code
  - `$$key_scancode` – GLFW scan code
  - `$$key_modifiers` – active modifier bit mask

## On Keyboard Key Released (`keyboard_key_released`)
- Triggers when a key is released (screens and in-game).
- Variables:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen (`keyboard_char_typed`)
- Fires when a character is typed while a screen is open.
- Variables:
  - `$$char` – typed character

## On Mouse Moved in Screen (`mouse_moved`)
- Fires whenever the mouse moves while a screen is open.
- Variables:
  - `$$mouse_pos_x` – current X
  - `$$mouse_pos_y` – current Y
  - `$$mouse_move_delta_x` – X delta since last event
  - `$$mouse_move_delta_y` – Y delta since last event

## On Mouse Button Clicked (`mouse_button_clicked`)
- Fires when a mouse button is pressed (screens and in-game).
- Variables:
  - `$$button` – left/right/middle
  - `$$mouse_pos_x` – current X
  - `$$mouse_pos_y` – current Y

## On Mouse Button Released (`mouse_button_released`)
- Fires when a mouse button is released (screens and in-game).
- Variables:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen (`mouse_scrolled`)
- Fires when the mouse wheel is scrolled while a screen is open.
- Variables:
  - `$$scroll_delta_y` – vertical scroll amount

## On Screen Opened (`screen_open`)
- Runs right after any screen becomes active; can be used to override it.
- Variables:
  - `$$screen_identifier` – identifier of the opened screen

## On Screen Closed (`screen_close`)
- Runs immediately after a screen closes.
- Variables:
  - `$$screen_identifier` – identifier of the closed screen

## On Quit Minecraft (`quit_minecraft`)
- Fires once when the client begins shutting down.
- Variables:
  - `$$timestamp_millis` – epoch millis when quitting
  - `$$timestamp_iso` – ISO-8601 timestamp of quit moment

## On Death (`player_death`)
- Runs when the vanilla death screen opens for the local player.
- Variables:
  - `$$days_survived` – days since last death
  - `$$death_reason_string` – plain-text cause
  - `$$death_reason_component` – JSON component cause
  - `$$death_pos_x` – death X coordinate
  - `$$death_pos_y` – death Y coordinate
  - `$$death_pos_z` – death Z coordinate

## On Variable Updated [FM Variable] (`fm_variable_updated`)
- Fires whenever a [FancyMenu variable](./variables) is set or updated.
- Variables:
  - `$$var_name` – variable name
  - `$$old_value` – previous value
  - `$$new_value` – new value

## On File Downloaded via Action (`file_downloaded_via_action`)
- Fires after the [**Download File to Game Directory** action](./action-scripts#download-file-to-game-directory-download_file_to_game_dir) finishes.
- Variables:
  - `$$download_url` – download source
  - `$$target_file_path` – saved file path on success; on failure, this may contain only the target directory because no final filename was resolved
  - `$$download_succeeded` – true/false

## On File Selected (`file_selected_via_action`)
- Fires after the [**Select File from System** action](./action-scripts#select-file-from-system-select_file_to_game_dir) completes.
- Variables:
  - `$$selected_file_path` – absolute chosen file path or empty if cancelled
  - `$$target_file_path` – resolved path inside instance
  - `$$selection_succeeded` – true if copy succeeded
  - `$$selection_cancelled` – true if dialog closed
  - `$$failure_reason` – error info on failure

## On Chat Message Received (`chat_message_received`)
- Fires when a normal player chat line appears on the client.
- Variables:
  - `$$chat_message_string` – plain text line
  - `$$chat_message_component` – full JSON component
  - `$$sender_uuid` – sender UUID or ERROR
  - `$$sender_name` – sender name or ERROR

## On Chat Message Sent (`chat_message_sent`)
- Fires when the local player sends a chat message.
- Variables:
  - `$$chat_message_string` – plain text line
  - `$$chat_message_component` – full JSON component

## On Effect Gained (`effect_gained`)
- Fires when the player gains a status effect.
- Variables:
  - `$$effect_key` – effect resource location
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – ticks remaining

## On Effect Lost (`effect_lost`)
- Fires when the player loses a status effect.
- Variables:
  - `$$effect_key` – expired effect
  - `$$effect_type` – category

## On Experience Changed (`experience_changed`)
- Fires whenever the player’s total XP changes.
- Variables:
  - `$$new_experience_amount` – after change
  - `$$old_experience_amount` – before change
  - `$$is_level_up` – TRUE if level increased

## On Damage Taken (`damage_taken`)
- Fires once per hit when the player takes damage.
- Variables:
  - `$$damage_amount` – health removed
  - `$$damage_type` – damage type resource location
  - `$$is_fatal_damage` – TRUE if lethal
  - `$$damage_source` – attacker resource location or NONE

## On Started Freezing (`started_freezing`)
- Fires when the player starts freezing.
- Variables:
  - `$$freezing_intensity` – 0.0 none, 1.0 fully frozen

## On Stopped Freezing (`stopped_freezing`)
- Fires when the player stops freezing.
- Variables:
  - (none)

## On Fully Frozen (`fully_frozen`)
- Fires once when the player becomes fully frozen.
- Variables:
  - (none)

## On Start Looking At Block (`start_looking_at_block`)
- Fires once when the crosshair first points at a block (max 20 blocks distance).
- Variables:
  - `$$block_key` – targeted block
  - `$$block_pos_x` – block X
  - `$$block_pos_y` – block Y
  - `$$block_pos_z` – block Z
  - `$$distance_to_player` – eyes to hit position

## On Stop Looking At Block (`stop_looking_at_block`)
- Fires when the crosshair stops pointing at a block (reports last targeted block, max 20 blocks).
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity (`start_looking_at_entity`)
- Fires once when the crosshair first points at an entity (max 20 blocks).
- Variables:
  - `$$entity_key` – targeted entity type
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity (`stop_looking_at_entity`)
- Fires when the crosshair stops pointing at an entity (reports last targeted entity, max 20 blocks).
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned (`entity_spawned`)
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

## On Entity Died (`entity_died`)
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

## On Entity Starts Being In Sight (`entity_starts_being_in_sight`)
- Fires when an entity first becomes visible within 200 blocks.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight (`entity_stops_being_in_sight`)
- Fires when a previously visible entity leaves view or moves beyond 200 blocks.
- Variables:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity (`entity_interacted`)
- Fires when the player successfully interacts with an entity.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted (`entity_mounted`)
- Fires when the player begins riding an entity.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted (`entity_unmounted`)
- Fires when the player stops riding their current entity.
- Variables:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke (`block_broke`)
- Fires when the player breaks a block.
- Variables:
  - `$$block_key`
  - `$$broke_with_item_key` – tool used or EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed (`block_placed`)
- Fires when the player places a block.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block (`interacted_with_block`)
- Fires when the player successfully interacts with a block.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block (`stepping_on_block`)
- Fires when the player steps onto a block.
- Variables:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome (`enter_biome`)
- Fires when the player enters a new biome.
- Variables:
  - `$$biome_key` – entered biome

## On Leave Biome (`leave_biome`)
- Fires when the player leaves their current biome.
- Variables:
  - `$$biome_key` – biome just left

## On Enter Structure (`enter_structure`)
- **Requires FancyMenu on the server.** Coarse structure-area detection; can trigger near/above/below the structure.
- Variables:
  - `$$structure_key` – entered structure

## On Leave Structure (`leave_structure`)
- **Requires FancyMenu on the server.** Coarse detection; can trigger near the structure footprint.
- Variables:
  - `$$structure_key` – structure just left

## On Enter Structure (High Precision) (`enter_structure_high_precision`)
- **Requires FancyMenu on the server.** Fires when the player steps into a structure’s bounding boxes.
- Variables:
  - `$$structure_key`

## On Leave Structure (High Precision) (`leave_structure_high_precision`)
- **Requires FancyMenu on the server.** Fires after the player exits a structure’s bounding boxes.
- Variables:
  - `$$structure_key`

## On Dimension Entered (`enter_dimension`)
- Fires when the player enters a new dimension.
- Variables:
  - `$$dimension_key` – entered dimension

## On Start Swimming (`start_swimming`)
- Fires when the player starts swimming.
- Variables:
  - `$$fluid_type` – fluid resource location

## On Stop Swimming (`stop_swimming`)
- Fires when the player stops swimming.
- Variables:
  - `$$fluid_type` – fluid where swimming stopped

## On Start Touching Fluid (`start_touching_fluid`)
- Fires when the player starts touching a fluid.
- Variables:
  - `$$fluid_type` – touched fluid

## On Stop Touching Fluid (`stop_touching_fluid`)
- Fires when the player stops touching a fluid.
- Variables:
  - `$$fluid_type` – fluid no longer touched

## On Music Track Started (`music_track_started`)
- Fires when a new music track begins.
- Variables:
  - `$$track_resource_location` – audio file
  - `$$track_display_name` – human-readable name or UNKNOWN
  - `$$track_artist` – artist or UNKNOWN
  - `$$track_duration_ms` – milliseconds (0 if unknown)

## On Music Track Stopped (`music_track_stopped`)
- Fires when the current music track ends or is replaced.
- Variables:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered (`world_sound_triggered`)
- Fires when a positional world sound starts near the player.
- Variables:
  - `$$sound_resource_location` – sound file
  - `$$sound_display_name` – subtitle name when available
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – degrees 0–360 relative to facing

## On Weather Changed (`weather_changed`)
- Fires when weather changes globally or locally (biome change or going indoors can retrigger).
- Variables:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE if snow renders
  - `$$weather_can_rain` – TRUE if rain renders

## On Started Burning (`started_burning`)
- Fires when the player starts burning.
- Variables:
  - (none)

## On Stopped Burning (`stopped_burning`)
- Fires when the player stops burning.
- Variables:
  - (none)

## On Started Drowning (`started_drowning`)
- Fires when the player begins taking drowning damage.
- Variables:
  - (none)

## On Position Changed (`position_changed`)
- Fires whenever the player’s block position changes.
- Variables:
  - `$$old_pos_x` – previous block X
  - `$$old_pos_y` – previous block Y
  - `$$old_pos_z` – previous block Z
  - `$$new_pos_x` – new block X
  - `$$new_pos_y` – new block Y
  - `$$new_pos_z` – new block Z

## On Started Running (`started_running`)
- Fires when the player starts sprinting.
- Variables:
  - (none)

## On Stopped Running (`stopped_running`)
- Fires when the player stops sprinting.
- Variables:
  - (none)

## On Jump (`jump`)
- Fires whenever the player jumps.
- Variables:
  - (none)

## On Server Joined (`server_joined`)
- Fires after successfully joining a multiplayer server.
- Variables:
  - `$$server_ip` – joined server address

## On Server Left (`server_left`)
- Fires after disconnecting from a multiplayer server.
- Variables:
  - `$$server_ip` – left server address

## Singleplayer World Entered (`world_entered`)
- Fires after a singleplayer world finishes loading and control is returned.
- Variables:
  - `$$world_name` – display name
  - `$$world_save_path` – absolute save folder
  - `$$world_difficulty` – difficulty key
  - `$$world_cheats_allowed` – TRUE if cheats enabled
  - `$$world_icon_path` – absolute icon path
  - `$$world_is_first_join` – TRUE on very first visit

## Singleplayer World Left (`world_left`)
- Fires after a singleplayer world closes and finishes saving.
- Variables:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server (`other_player_joined_world`)
- Fires when another player joins the current world/server.
- Variables:
  - `$$player_name` – name of joining player
  - `$$player_uuid` – UUID

## On Other Player Left World/Server (`other_player_left_world`)
- Fires when another player leaves the current world/server.
- Variables:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died (`other_player_died`)
- Fires when another player in the current world dies.
- Variables:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up (`item_picked_up`)
- Fires when the player picks up an item entity.
- Variables:
  - `$$item_key` – picked-up item resource location

## On Item Dropped (`item_dropped`)
- Fires when the player drops an item from their inventory.
- Variables:
  - `$$item_key` – dropped item resource location

## On Item Consumed (`item_consumed`)
- Fires when the player finishes consuming an item.
- Variables:
  - `$$item_key` – consumed item

## On Item Hovered in Inventory (`item_hovered_in_inventory`)
- Fires when the user hovers an item in any inventory screen.
- Variables:
  - `$$item_key` – hovered item resource location
  - `$$item_display_name_string` – plain text item display name
  - `$$item_display_name_json` – JSON component item display name

## On Item Used (`item_used`)
- Fires when the player uses an item.
- Variables:
  - `$$item_key` – used item
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – target entity type or empty
  - `$$used_on_block_key` – target block or empty
  - `$$target_pos_x` – target X or -1
  - `$$target_pos_y` – target Y or -1
  - `$$target_pos_z` – target Z or -1

## On Item Broke (`item_broke`)
- Fires when an item in the player’s inventory breaks.
- Variables:
  - `$$item_key` – broken item
  - `$$item_type` – tool/armor/other
