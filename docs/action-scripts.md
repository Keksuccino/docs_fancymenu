---
title: Action Scripts
description: 'How to use action scripts with buttons, sliders, tickers and more.'
---

# Action Scripts

Action scripts run configured tasks when a [Button](./elements#button) is clicked, a [Ticker](./elements#ticker) updates, a [Slider](./elements#slider) changes, a screen opens or closes, or another supported event occurs. Statements such as **if**, **else-if**, **else**, and **while** add conditional control.

> [!CAUTION]
> Imported action scripts can modify files, contact servers, open links, or run commands. Use only sources you trust.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Action script editor" style="max-width:800px;width:100%;height:auto;">

# What Are Actions?

An **action** is a task or job that FancyMenu runs when triggered. For example, an action might open a new screen, send a chat message, or adjust the volume of an [Audio element](./elements#audio). In FancyMenu's editor, actions are configured with a value (if needed) that provides extra details—such as a URL or server address.

# What Are Statements?

To create more complex behavior, FancyMenu supports basic control statements in action scripts. These include:

- **If Statement:** Runs a block of actions only if its [requirements](./conditions) are met.
- **Else-If Statement:** Checks another set of [requirements](./conditions) if the preceding *if* or *else-if* was not met.
- **Else Statement:** Runs if none of the preceding requirements are met.
- **While Statement:** Repeats a block while its [requirements](./conditions) remain true. It stops after three seconds to prevent infinite loops; do not use it as a timer.
- **Delay Block:** Starts a timer when first reached. Its actions run the next time the script reaches the block after the delay. Reinitializing the screen resets the timer.
- **Execute Later Block:** Schedules its actions automatically after the configured millisecond delay every time the block is reached.
- **Comment:** Adds a note inside the script for organization. Comments do not run any action.

By combining these statements with actions, you can build dynamic and conditional behavior, for example, checking if a player's health is low before sending a warning message or repeating an update until a condition changes.

Actions run from top to bottom. A failed action is logged, then the script continues.

Downloads, ZIP extraction, and HTTP requests finish later; the next action does not wait. Use [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action), or an HTTP response variable when later work depends on the result.

# Where Can You Use Action Scripts?

Action scripts are versatile and can be used throughout your layout. You can assign them, for example, to:

- [**Buttons**](./elements#button): Execute an action when the button is clicked.
- [**Tickers**](./elements#ticker): Continuously run an action script to update on-screen information within a layout.
- [**Sliders**](./elements#slider): Trigger an action script whenever the slider's value changes.
- **Screen Events:** Run scripts when a screen opens or closes (for example, playing a sound when a menu appears).
- [**Listeners**](./listeners): When a listener receives its configured event, it runs its action script.
- [**Schedulers**](./schedulers): Execute actions on a timed basis, even when no screen is open.

# Using Placeholders in Actions

Action values support dynamic content through **placeholders**. Most of the time these placeholders use a JSON-like syntax and are replaced with live data when the action runs.

## JSON-Like Placeholders

These are the normal [placeholders](./placeholders) that can be used in many places throughout layouts.

They follow this syntax:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

They can fetch game data like the player's name, screen dimensions, or calculated values using the [**Calculator** placeholder](./placeholders#calculator-calc). You can also nest placeholders for more advanced uses.

## `$$` Placeholders (Variables)

`$$` values are read-only values supplied to a specific action script by the feature running it.

For example, a [Slider](./elements#slider) supplies its current value as `$$value`.

Each [listener](./listeners) documents the `$$` values it supplies, such as a pressed mouse button or entered structure.

`$$` names are case-sensitive and only work in the script that provides them. See [Listeners](./listeners#listener-variables).

## Action Value Delimiters

Use the exact delimiter shown for each action: `:`, `||`, or `|||`. There is no escape syntax for delimiters inside a field.

Placeholders are replaced before the value is split. For `set_variable`, only the first colon separates the name from the value, so later colons remain part of the value.

# How to Set Up and Edit Actions

To edit an element's actions and statement blocks, **right-click the element** and select **Manage Action Script**. In the editor, you can:

- **Add new actions or statements:** Insert new action entries or control statements (if, else-if, else, while) to build your script.
- **Edit existing actions or statements:** Modify the action value or change the control logic.
- **Remove actions or statements:** Delete unwanted actions from the script.

Create and edit listener scripts through [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Action Script Editor Shortcuts

## Shortcuts

- `DEL` : Quick-delete the selected entry
- `ENTER` : Starts the in-line editing of the selected entry (or opens the edit screen if there is not in-line edit for the selected entry)
- `CTRL + C` : Copy the selected action (only works with actions for now)
- `CTRL + V` : Paste the previously copied action
- `CTRL + Z` : One step back (undo)
- `CTRL + Y` : One step forward (redo)
- `ARROW UP` : Navigate one entry up from the currently selected one
- `ARROW DOWN` : Navigate one entry down from the currently selected one
- `SHIFT + ARROW UP` : Move the selected entry one up
- `SHIFT + ARROW DOWN` : Move the selected entry one down
- `A` : Quick-open the Action Chooser screen to add a new action
- `CTRL + S` : Done/save from the editor window

## Editing

- Double-clicking the value of an action lets you edit the value without going into the full value editing screen.
- IF statement chains (with appended ELSE/ELSE-IF statements), WHILE loops and Folders can be collapsed (only visual, does not affect script logic).
- The editor always adds new actions below the selected entry (or nested in the selected chain/loop/folder).
- Right-clicking the dark-grey script area background opens a context menu with options to add actions, statements and everything else important.

# Actions in Detail

This section lists FancyMenu's built-in actions.

## Next Track (`audio_next_track`)
- **Description:** Goes to the next track in an [Audio element](./elements#audio)
- **Value Required:** Yes - `audio_element_identifier` (the ID of the audio element to control)

## Previous Track (`audio_previous_track`)
- **Description:** Goes to the previous track in an [Audio element](./elements#audio)
- **Value Required:** Yes - `audio_element_identifier` (the ID of the audio element to control)

## Set Track Volume (`set_audio_element_volume`)
- **Description:** Sets the volume of an [Audio element](./elements#audio) (`0.0` to `1.0`)
- **Value Required:** Yes - `element_identifier:volume`

## Toggle Play/Pause Track (`audio_toggle_play`)
- **Description:** Toggles the current track of an [Audio element](./elements#audio) between playing and paused
- **Value Required:** Yes - `audio_element_identifier`

## Play Audio (`play_audio`)
- **Description:** Plays an audio resource once. Audio started by this action can later be stopped with [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).
- **Value Required:** Yes - JSON configuration with `audioSource`, `soundChannel`, and `baseVolume`
- **Example Value:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Behavior:**

- `baseVolume` is clamped to `0.0`–`1.0`.
- An unknown sound channel uses the Master channel.
- The action cannot run from an asynchronous [Ticker](./elements#ticker); FancyMenu shows an error instead.
- FancyMenu waits up to ten seconds for the audio resource to become ready.
- Successfully started tracks can be stopped with [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

## Stop All Action Audios (`stop_all_action_audios`)
- **Description:** Stops all audio tracks that were started by the [**Play Audio** action](#play-audio-play_audio). This does not stop [Audio elements](./elements#audio), menu open/close sounds, button sounds, or other audio systems.
- **Value Required:** No

## Set Video Element Volume (`set_video_element_volume`)
- **Description:** Sets the volume of a [Video element](./video) (`0.0` to `1.0`)
- **Value Required:** Yes - `video_element_identifier:volume`

## Set Video Element Play Time (`set_video_element_play_time`)
- **Description:** Seeks a [Video element](./video) to a millisecond timestamp
- **Value Required:** Yes - `video_element_identifier:timestamp_ms`

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)
- **Description:** Toggles the paused state of a [Video element](./video)
- **Value Required:** Yes - `video_element_identifier`

## Set Video Background Volume (`set_video_menu_background_volume`)
- **Description:** Sets the volume of a [Video menu background](./video) (`0.0` to `1.0`)
- **Value Required:** Yes - `background_identifier:volume`

> To get the identifier of a background, right-click the editor background and click on 'Copy Background Identifier'.
{.is-info}

## Set Video Background Play Time (`set_video_menu_background_play_time`)
- **Description:** Seeks a [Video menu background](./video) to a millisecond timestamp
- **Value Required:** Yes - `background_identifier:timestamp_ms`

> To get the identifier of a background, right-click the editor background and click on 'Copy Background Identifier'.
{.is-info}

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)
- **Description:** Toggles the paused state of a [Video menu background](./video)
- **Value Required:** Yes - `background_identifier`

> To get the identifier of a background, right-click the editor background and click on 'Copy Background Identifier'.
{.is-info}

## Toggle Layout (`toggle_layout`)
- **Description:** Toggles a layout (Enable/Disable) by its filename without `.txt`
- **Value Required:** Yes - `layout_name`

## Enable Layout (`enable_layout`)
- **Description:** Enables and saves a layout by its filename without `.txt`
- **Value Required:** Yes - `layout_name`

## Disable Layout (`disable_layout`)
- **Description:** Disables and saves a layout by its filename without `.txt`
- **Value Required:** Yes - `layout_name`

All three layout actions save the state in the layout file and update the current screen immediately. Use the case-sensitive filename without `.txt`.

## Open Screen or Custom GUI (`opengui`)
- **Description:** Opens a screen by its identifier (vanilla, mod, or custom GUI)
- **Value Required:** Yes - `screen_identifier`

Copy the exact, case-sensitive identifier from the [Screen Identifiers](./screen-identifiers) debug overlay.

Some mod screens cannot be created directly. If opening fails, use [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) on a widget that normally opens that screen.

## Close Screen (`closegui`)
- **Description:** Closes the active screen
- **Value Required:** No

## Update Screen (`update_screen`)
- **Description:** Reinitializes the current screen
- **Value Required:** No

## Back to Last Screen (`back_to_last_screen`)
- **Description:** Returns to a [Custom GUI](./custom-guis)'s parent or to the one most recently closed screen instance
- **Value Required:** No

## Join Server (`joinserver`)
- **Description:** Connects the player to a Minecraft server
- **Value Required:** Yes - `server_ip` or `server_ip:port`

This action cannot run while a world or server is already loaded. Port `25565` is used when omitted. If the address is not in Minecraft's saved server list, FancyMenu adds and saves it.

## Enter World (`loadworld`)
- **Description:** Enters a Minecraft world
- **Value Required:** Yes - `world_folder_name`

The value is the save folder name. The action does nothing if that save does not exist or another world/server is already loaded.

## Enter/Join Last World/Server (`join_last_world`)
- **Description:** Enters/joins the last world or server the player was in
- **Value Required:** No

This action cannot run while another world/server is loaded. A remembered server that is not in Minecraft's saved server list is added and saved before connecting.

## Leave World or Server (`disconnect_server_or_world`)
- **Description:** Leaves a world or server and opens a specified screen
- **Value Required:** Yes - `screen_identifier`

This action only runs while a world and player are loaded. The target may be a [Custom GUI](./custom-guis) identifier or a [screen identifier](./screen-identifiers) FancyMenu can construct. If the target cannot be opened, FancyMenu returns to the Title screen.

## Quit Minecraft (`quitgame`)
- **Description:** Quits Minecraft completely
- **Value Required:** No

## Send Chat Message/Command (`sendmessage`)
- **Description:** Sends a chat message or executes a chat command
- **Value Required:** Yes - `message_text` or `/command_text`

## Execute Command As Integrated Server (`execute_command_as_integrated_server`)
- **Description:** Force-executes a command in singleplayer as the integrated server, ignoring permissions and the cheats setting.
- **Value Required:** Yes - Command text, for example `/give @p minecraft:diamond 1`

> This action only works in singleplayer while the world is **not opened to LAN**. It intentionally does nothing when no integrated server exists or when the integrated server is published to LAN.
{.is-warning}

## Paste to Chat (`paste_to_chat`)
- **Description:** Pastes text to the chat input field (append or replace)
- **Value Required:** Yes - `true:Text` or `false:Text`

## Display In Chat [Client-Side] (`display_in_chat_client_side`)
- **Description:** Displays a client-side chat message while a world or server is loaded. It does not send anything to the server.
- **Value Required:** Yes - `text_or_json`

## Send FM Data To Server (`send_fm_data_to_server`)
- **Description:** Sends [FM Data](./fm-data) to the current FancyMenu server.
- **Value Required:** Yes - `data_identifier||data`

## Connect To Remote Server (`connect_to_remote_server`)
- **Description:** Opens or reuses a client-initiated WebSocket connection to an external remote server.
- **Value Required:** Yes - Remote server URL, for example `wss://example.com/ws`

See [Remote Server Communication](./remote-server-communication#url-modes) for accepted URL forms.

## Send Data To Remote Server (`send_data_to_remote_server`)
- **Description:** Opens or reuses a remote server connection and sends text data to it.
- **Value Required:** Yes - `remote_server_url||data`

## Close Remote Server Connection (`close_remote_server_connection`)
- **Description:** Closes a specific remote server connection by request ID.
- **Value Required:** Yes - Request ID, usually `$$request_id` from a [remote-server listener](./listeners#on-remote-server-connected)

## Close All Remote Server Connections (`close_all_remote_server_connections`)
- **Description:** Closes all active remote server connections opened by FancyMenu.
- **Value Required:** No

## Open URL in Browser (`openlink`)
- **Description:** Passes a URL to the operating system's default handler without a FancyMenu confirmation prompt
- **Value Required:** Yes - `https://example.com`

Use trusted `https://` links. FancyMenu does not show a confirmation prompt before passing the URL to the operating system.

## Copy Text to Clipboard (`copytoclipboard`)
- **Description:** Copies text to the clipboard
- **Value Required:** Yes - `text_to_copy`

## Print to Game Log (`print_to_log`)
- **Description:** Writes a line to the game log
- **Value Required:** Yes - `text_to_log`

## Set Variable Value (FM Variable) (`set_variable`)
- **Description:** Stores text content in a [FancyMenu variable](./variables)
- **Value Required:** Yes - `variable_name:variable_value`

The first colon separates the name from the value. Later colons remain part of the value. Changes are saved immediately.

## Clear All Variables (FM Variable) (`clear_variables`)
- **Description:** Clears all stored [FancyMenu variable](./variables) values
- **Value Required:** No

## Send HTTP Request (`send_http_request`)
- **Description:** Starts an HTTP/HTTPS request in the background; can log and/or store the response in a variable
- **Value Required:** Yes - HTTP request configuration

| Setting | Behavior |
|---|---|
| URL | HTTP or HTTPS endpoint |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD`, or `OPTIONS` |
| Body | Sent for methods other than `GET` and `HEAD` |
| Content type | Request `Content-Type` value |
| Timeout | Seconds used for both connection and response reads |
| Log response | Reads and writes the response to the log |
| Response variable | Reads the response and stores it after the request completes |
| Single-line response | Removes response line breaks before storing it |
| Authentication | None, Basic, Bearer, or API key |
| Headers | Optional custom request headers |

Requests run asynchronously, so the next action does not wait. Response bodies are read only when logging is enabled or a response variable is configured; non-success bodies are read from the error response. Do not store passwords or access tokens in the action configuration.

## Manage Resource Pack (`manage_resource_pack`)
- **Description:** Enables, disables, or toggles a resource pack, with an optional reload
- **Value Required:** Yes - `pack_name_or_id|||MODE|||reload_bool`

Display names and internal pack IDs are matched case-insensitively. Packs marked as required cannot be disabled.

## Reload Resource Packs (`reload_resource_packs`)
- **Description:** Reloads Minecraft's resource packs. A built-in five-second cooldown ignores repeated triggers during that period to prevent reload spam.
- **Value Required:** No

## Reload FancyMenu (`reloadmenu`)
- **Description:** Reloads layouts, [Custom GUIs](./custom-guis), [panoramas](./panoramas), [slideshows](./slideshows), settings, and FancyMenu-managed resources
- **Value Required:** No

This does not reload Minecraft resource packs. Use [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs) for that.

> Reloading is expensive. Trigger it from a deliberate button action, not a [Ticker](./elements#ticker) or frequently fired [listener](./listeners).
{.is-warning}

## Toggle Element Animator (`toggle_element_animator`)
- **Description:** Toggles the saved playback state and resets the matching active Animator timeline
- **Value Required:** Yes - `animator_identifier`

See [Element Animator](./element-animator) for setup and identifier details.

## Enable Element Animator (`enable_element_animator`)
- **Description:** Enables playback; an active Animator timeline resets only when the state changes from disabled to enabled
- **Value Required:** Yes - `animator_identifier`

## Disable Element Animator (`disable_element_animator`)
- **Description:** Disables playback and resets the matching active Animator timeline
- **Value Required:** Yes - `animator_identifier`

## Reset Element Animator (`reset_element_animator`)
- **Description:** Resets the matching active Animator timeline without changing whether playback is enabled
- **Value Required:** Yes - `animator_identifier`

## Mimic Vanilla/Mod Button (`mimicbutton`)
- **Description:** Mimics the click action of a vanilla or mod button
- **Value Required:** Yes - [`screen_identifier`](./screen-identifiers):[`widget_locator`](./widget-locators)

## Mimic Keybind (`mimic_keybind`)
- **Description:** Runs a Minecraft keybind (optional hold)
- **Value Required:** Yes - `keybind_id|||keep_pressed_bool|||duration_ms`

## Set Text Input Field Value (`set_text_input_field_value`)
- **Description:** Sets the value of a custom or Vanilla [Text Input Field](./elements#text-input-field) by element identifier.
- **Value Required:** Yes - `element_identifier|||new_value|||force_set_when_inactive`

The three fields must be separated with the triple-pipe delimiter `|||`. Set `force_set_when_inactive` to `true` to update a disabled input field too; when it is `false`, inactive fields are left unchanged.

## Create File in Game Directory (`create_file_in_game_dir`)
- **Description:** Creates an empty file relative to the active game directory. Accepts the `.minecraft/` prefix to target the conventional Minecraft directory (which may differ from the current instance).
- **Value Required:** Yes - `file_path`

Example: `config/some_mod_folder/new_file.txt`. Missing parent directories are created; an existing file is left unchanged.

## Delete File/Folder in Game Directory (`delete_file_in_game_dir`)
- **Description:** Deletes a file or recursively deletes a folder relative to the active game directory. Accepts `.minecraft/` to target the conventional Minecraft directory. Append `*` to delete **all files directly inside** a folder (ignores subdirectories and keeps the folder).
- **Value Required:** Yes - `target_path`

For example, `config/downloads/*` deletes the files directly inside `config/downloads/`, but it neither traverses nor deletes its sub-directories.

## Copy File/Folder in Game Directory (`copy_file_in_game_dir`)
- **Description:** Copies within the active game directory; `.minecraft/` targets the conventional Minecraft directory. A named directory is copied recursively. Append `*` to the **source** path to copy every direct child file only; destination must be a directory and cannot use `*`.
- **Value Required:** Yes - `source||destination`

For example, `config/source/*||config/destination/` copies only the files directly inside `config/source/`. With a wildcard source, FancyMenu creates the destination directory when needed but does not copy any source subdirectories. Copy refuses any existing destination/colliding file instead of overwriting it.

## Move File/Folder in Game Directory (`move_file_in_game_dir`)
- **Description:** Moves within the active game directory; `.minecraft/` targets the conventional Minecraft directory. Append `*` to the **source** path to move every direct child file only; destination must be a directory and cannot use `*`.
- **Value Required:** Yes - `source||destination`

For example, `config/source/*||config/destination/` moves only the files directly inside `config/source/`. With a wildcard source, FancyMenu creates the destination directory when needed but leaves source subdirectories in place. Move refuses an existing destination/colliding file instead of overwriting it.

## Rename File/Folder in Game Directory (`rename_file_in_game_dir`)
- **Description:** Renames a file or folder within its current parent directory; `.minecraft/` targets the conventional Minecraft directory. Keeps contents intact and refuses an existing target name.
- **Value Required:** Yes - `path||new_name`

## Download File to Game Directory (`download_file_to_game_dir`)
- **Description:** Downloads a file in the background to a directory relative to the active game directory; `.minecraft/` targets the conventional Minecraft directory.
- **Value Required:** Yes - `url||target_folder`

The second field is a **target directory**, not a complete destination file path. FancyMenu creates the directory when needed and determines the filename from the response's `Content-Disposition` header, then falls back to the URL path. The resolved name is URL-decoded and sanitized before use; if neither source provides a usable name, FancyMenu generates one. An existing file with the same name is overwritten.

The [**On File Downloaded via Action** listener](./listeners#on-file-downloaded-via-action) fires after both successful and failed download attempts and exposes the URL, resolved target path, and success state.

On success, `$$target_file_path` is the saved file path. On failure, it may contain only the target directory because no final filename was resolved.

## Extract ZIP File In Game Directory (`extract_zip_file_in_game_dir`)
- **Description:** Extracts a ZIP into a target folder inside the active game directory or conventional `.minecraft` directory. Triggers [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action) when finished.
- **Value Required:** Yes - `source_zip_path||target_folder_path`

Existing files with matching names are replaced. Extract only trusted ZIP files.

## Open File/Folder In Game Directory (`open_file_folder_in_game_dir`)
- **Description:** Opens a file or folder with the operating system's default app. The target must stay inside the game directory or the default `.minecraft` directory for safety reasons.
- **Value Required:** Yes - `target_path`

## Write File in Game Directory (`write_file_in_game_dir`)
- **Description:** Writes or appends text relative to the active game directory; `.minecraft/` targets the conventional Minecraft directory. Creates the file and parents if missing. `\n` inserts line breaks; `append_bool=false` replaces an existing file.
- **Value Required:** Yes - `path|||content|||append_bool`

## Select File from System (`select_file_to_game_dir`)
- **Description:** Opens a native file picker and copies the selected file inside the active game directory, or conventional `.minecraft/` when prefixed. Supports extension filters, a custom filter label, and an overwrite toggle.
- **Value Required:** Yes - `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` is the complete destination file path. Separate multiple extensions with `;` or `,`, for example `png;jpg`; a blank extension list allows all files. If `overwrite_bool` is `false`, the action fails instead of replacing an existing destination file.

The [**On File Selected** listener](./listeners#on-file-selected) fires when the file is copied, the picker is cancelled, or selection fails. It exposes the selected path, resolved target path, success/cancelled states, and a failure reason.

## Show Toast (`show_toast`)
- **Description:** Displays a configurable toast notification
- **Value Required:** Yes - toast configuration

| Field | Meaning |
|---|---|
| Width | Clamped to `120`–`320` pixels |
| Duration | Clamped to `1000`–`600000` milliseconds |
| Title | Plain text or a serialized Minecraft text component |
| Message | Optional plain text or serialized text component |
| Icon | Optional [image source](./resources) |
| Background | Optional [image source](./resources) |

## Start Scheduler (`start_scheduler`)
- **Description:** Starts a scheduler by its scheduler ID.
- **Value Required:** Yes - `scheduler_id`

See [Schedulers](./schedulers) for creating and managing scheduler IDs.

## Stop Scheduler (`stop_scheduler`)
- **Description:** Stops a scheduler by its scheduler ID.
- **Value Required:** Yes - `scheduler_id`

## Set Minecraft Option (`edit_minecraft_option`)
- **Description:** Edits a Minecraft config option
- **Value Required:** Yes - `option_name:set_to_value`
