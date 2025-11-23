---
title: Action Scripts
description: How to use action scripts with buttons, sliders, tickers and more.
published: true
date: 2025-11-23T09:20:43.295Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:02:13.319Z
---

# Action Scripts

FancyMenu lets you add interactivity to your menus by assigning **actions** to elements. These actions run when a button is clicked, ticker is ticking, slider gets used, or when a screen opens or closes. You can also build advanced action scripts using simple control statements, such as **if**, **else-if**, **else**, and **while**, to control which actions run and when.

# What Are Actions?

An **action** is a task or job that FancyMenu runs when triggered. For example, an action might open a new screen, send a chat message, or adjust the volume of an audio element. In FancyMenu's editor, actions are configured with a value (if needed) that provides extra details—such as a URL or server address.

# What Are Statements?

To create more complex behavior, FancyMenu supports basic control statements in action scripts. These include:

- **If Statement:** Runs a block of actions only if a specified [condition](/en/conditions) is met.
- **Else-If Statement:** Checks another [condition](/en/conditions) if the preceding *if* (or earlier *else-if*) wasn't met.
- **Else Statement:** Runs if none of the preceding [conditions](/en/conditions) are met.
- **While Statement:** Repeats a block of actions continuously while a [condition](/en/conditions) remains true (with a built‑in timeout to prevent infinite loops).

By combining these statements with actions, you can build dynamic and conditional behavior, for example, checking if a player's health is low before sending a warning message or repeating an update until a condition changes.

# Where Can You Use Action Scripts?

Action scripts are versatile and can be used throughout your layout. You can assign them, for example, to:

- **Buttons:** Execute an action when the button is clicked.
- **Tickers:** Continuously run an action script to update on-screen information.
- **Sliders:** Trigger an action script whenever the slider's value changes.
- **Screen Events:** Run scripts when a screen opens or closes (for example, playing a sound when a menu appears).
- **Listeners:** When a listener that listeners to a specific event gets fired, it will execute its action script.

# Using Placeholders in Actions

Action values support dynamic content through **placeholders**. Most of the time these placeholders use a JSON-like syntax and are replaced with live data when the action runs.

## JSON-Like Placeholders

These are the normal [placeholders](/en/placeholders) that can be used in many places throughout layouts.

They follow this syntax:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

They can fetch game data like the player's name, screen dimensions, or calculated values using the **Calculator** placeholder. You can also nest placeholders for more advanced uses.

## `$$` Placeholders (Variables)

The `$$` placeholders are special. Some features of FancyMenu will provide these special placeholders for their nested actions, requirements and normal placeholders, so they can be used inside to get more information about the environment (element, listener, etc.) they are in.

For example, if actions are used within a slider, using `$$value` in the action will be replaced with the slider's current value.

When using actions in listeners, every listener will provide its own unique set of variables/placeholders for getting more information about the listener, like pressed mouse button, entered structure, etc.

# How to Set Up and Edit Actions

To add, edit, or remove actions (and statement blocks) for an element, simply **right-click the element** (whether it's a button, slider, ticker, or other interactive item) and then select **Manage Action Script**. This opens the Manage Actions screen, where you can:

- **Add new actions or statements:** Insert new action entries or control statements (if, else-if, else, while) to build your script.
- **Edit existing actions or statements:** Modify the action value or change the control logic.
- **Remove actions or statements:** Delete unwanted actions from the script.

For [listeners](/listeners) there is a special menu to manage and create listeners, including accessing their action scripts to have the same experience as when editing a button's or slider's action script for example.

# Actions in Detail

This list contains most, if not all, actions available in FancyMenu. It's possible that the list is a bit outdated sometimes due to updates of the mod.

## Next Track (`audio_next_track`)
- **Description:** Goes to the next track in an audio element
- **Value Required:** Yes - `audio_element_identifier` (the ID of the audio element to control)

## Previous Track (`audio_previous_track`)
- **Description:** Goes to the previous track in an audio element
- **Value Required:** Yes - `audio_element_identifier` (the ID of the audio element to control)

## Set Audio Element Volume (`set_audio_element_volume`)
- **Description:** Sets the volume of an audio element (0.0 to 1.0)
- **Value Required:** Yes - `element_identifier:volume`

## Toggle Play Track (`audio_toggle_play`)
- **Description:** Toggles play/pause of an audio element's current track
- **Value Required:** Yes - `audio_element_identifier`

## Set Video Element Volume (`set_video_element_volume`)
- **Description:** Sets the volume of a video element (0.0 to 1.0)
- **Value Required:** Yes - `video_element_identifier:volume`

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)
- **Description:** Toggles the paused state of a video element
- **Value Required:** Yes - `video_element_identifier`

## Set Video Background Volume (`set_video_menu_background_volume`)
- **Description:** Sets the volume of a video menu background (0.0 to 1.0)
- **Value Required:** Yes - `background_identifier:volume`

> To get the identifier of a background, right-click the editor background and click on 'Copy Background Identifier'.
{.is-info}

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)
- **Description:** Toggles the paused state of a video menu background
- **Value Required:** Yes - `background_identifier`

> To get the identifier of a background, right-click the editor background and click on 'Copy Background Identifier'.
{.is-info}

## Toggle Layout (`toggle_layout`)
- **Description:** Toggles a layout (Enable/Disable) by its name
- **Value Required:** Yes - `layout_name`

## Enable Layout (`enable_layout`)
- **Description:** Enables a layout by its name
- **Value Required:** Yes - `layout_name`

## Disable Layout (`disable_layout`)
- **Description:** Disables a layout by its name
- **Value Required:** Yes - `layout_name`

## Open Screen or Custom GUI (`opengui`)
- **Description:** Opens a screen by its identifier (vanilla, mod, or custom GUI)
- **Value Required:** Yes - `screen_identifier`

> This action **will not work for every screen**, especially mod screens. If the action fails to open a screen, it will show an error. There is not much you can do in that case, because then it's probably a screen that is too complex to get opened automatically by FancyMenu.
> 
> Compatibility for mod screens will also not get added manually on FancyMenu's side anymore, because adding compatibility for all the mods out there would take ages, sorry. In most cases it is also not recommended to contact the dev of the other mod in that case, because if FancyMenu can't open the screen, there is not easy way to add support for it. The recommended workaround here is to try to use the **"Mimic Button"** action to mimic a button that opens the specific screen. If there is no button, then you're out of luck, sorry.
{.is-info}

## Close Screen (`closegui`)
- **Description:** Closes the active screen
- **Value Required:** No

## Update Screen (`update_screen`)
- **Description:** Reinitializes the current screen
- **Value Required:** No

## Back to Last Screen (`back_to_last_screen`)
- **Description:** Goes back to the previous screen (the one before the current)
- **Value Required:** No

## Join Server (`joinserver`)
- **Description:** Connects the player to a Minecraft server
- **Value Required:** Yes - `server_ip:port`

## Enter World (`loadworld`)
- **Description:** Enters a Minecraft world
- **Value Required:** Yes - `world_folder_name`

## Join Last World/Server (`join_last_world`)
- **Description:** Enters/joins the last world or server the player was in
- **Value Required:** No

## Disconnect (`disconnect_server_or_world`)
- **Description:** Leaves a world or server and opens a specified screen
- **Value Required:** Yes - `screen_identifier`

## Quit Minecraft (`quitgame`)
- **Description:** Quits Minecraft completely
- **Value Required:** No

## Send Chat Message/Command (`sendmessage`)
- **Description:** Sends a chat message or executes a chat command
- **Value Required:** Yes - `message_text` or `/command_text`

## Paste to Chat (`paste_to_chat`)
- **Description:** Pastes text to the chat input field (append or replace)
- **Value Required:** Yes - `true:Text` or `false:Text`

## Display In Chat (Client-Side) (`display_in_chat_client_side`)
- **Description:** Prints text directly to local chat (no server)
- **Value Required:** Yes - `text_or_json`

## Open URL in Browser (`openlink`)
- **Description:** Opens a link in your default browser
- **Value Required:** Yes - `https://example.com`

## Copy to Clipboard (`copytoclipboard`)
- **Description:** Copies text to the clipboard
- **Value Required:** Yes - `text_to_copy`

## Print to Log (`print_to_log`)
- **Description:** Writes a line to the game log
- **Value Required:** Yes - `text_to_log`

## Set Variable (`set_variable`)
- **Description:** Stores text content in a FancyMenu variable
- **Value Required:** Yes - `variable_name:variable_value`

## Clear Variables (`clear_variables`)
- **Description:** Clears ALL of FancyMenu's stored variables
- **Value Required:** No

## Send HTTP Request (`send_http_request`)
- **Description:** Sends an HTTP request; can store the response in a variable
- **Value Required:** Yes - HTTP request configuration

This action allows you to send data to REST APIs, webhooks, or any HTTP endpoint.
Supports various authentication methods, custom headers, and different request types.

This action also allows you to store the response of the request in a FancyMenu variable for later use!

## Manage Resource Pack (`manage_resource_pack`)
- **Description:** Enable/disable/toggle a resource pack by display name (optional reload)
- **Value Required:** Yes - `pack_name|||MODE|||reload_bool`

## Reload Resource Packs (`reload_resource_packs`)
- **Description:** Reloads resource packs (5s cooldown)
- **Value Required:** No

## Reload FancyMenu (`reloadmenu`)
- **Description:** Reloads FancyMenu, including panoramas, slideshows and all resources (heavy)
- **Value Required:** No

> This action has a **big impact on performance** and can cause lags if used in Tickers. It is not recommended to use this action in anything else than a button.
{.is-warning}

## Toggle Element Animator (`toggle_element_animator`)
- **Description:** Toggles an element animator playback state
- **Value Required:** Yes - `animator_identifier`

## Enable Element Animator (`enable_element_animator`)
- **Description:** Enables an element animator
- **Value Required:** Yes - `animator_identifier`

## Disable Element Animator (`disable_element_animator`)
- **Description:** Disables an element animator
- **Value Required:** Yes - `animator_identifier`

## Reset Element Animator (`reset_element_animator`)
- **Description:** Resets an element animator timeline/state
- **Value Required:** Yes - `animator_identifier`

## Mimic Button (`mimicbutton`)
- **Description:** Mimics the click action of a vanilla or mod button
- **Value Required:** Yes - `screen_identifier:widget_locator`

## Mimic Keybind (`mimic_keybind`)
- **Description:** Runs a Minecraft keybind (optional hold)
- **Value Required:** Yes - `keybind_id|||keep_pressed_bool|||duration_ms`

## Create File (`create_file_in_game_dir`)
- **Description:** Creates an empty file in the game directory (instance root). Accepts the `.minecraft/` prefix to target the default launcher profile directory (may differ from the current instance dir).
- **Value Required:** Yes - `file_path`

## Delete File/Folder (`delete_file_in_game_dir`)
- **Description:** Deletes a file or folder in the game directory (instance root). Accepts `.minecraft/` prefix to hit the default launcher profile (can differ from the running instance). Append `*` to delete **all files directly inside** a folder (ignores sub-directories; keeps the folder).
- **Value Required:** Yes - `target_path`

## Copy File/Folder (`copy_file_in_game_dir`)
- **Description:** Copies within the game directory (instance root); `.minecraft/` prefix targets the default launcher profile (not always the current instance). Append `*` to the **source** path to copy every file directly inside that folder (ignores sub-directories); destination must be a directory and cannot use `*`.
- **Value Required:** Yes - `source||destination`

## Move File/Folder (`move_file_in_game_dir`)
- **Description:** Moves within the game directory (instance root); `.minecraft/` prefix targets the default launcher profile (may differ from the current instance). Append `*` to the **source** path to move every file directly inside that folder (ignores sub-directories); destination must be a directory and cannot use `*`.
- **Value Required:** Yes - `source||destination`

## Rename File/Folder (`rename_file_in_game_dir`)
- **Description:** Renames a file or folder inside the game directory (instance root); `.minecraft/` prefix targets the default launcher profile (may differ from current instance). Keeps contents intact, only the name changes.
- **Value Required:** Yes - `path||new_name`

## Download File (`download_file_to_game_dir`)
- **Description:** Downloads a file asynchronously into the game directory (instance root); `.minecraft/` prefix targets the default launcher profile (not necessarily the running instance). Provide the **target folder**; filename is derived from headers/URL automatically.
- **Value Required:** Yes - `url||target_folder`

## Write File (`write_file_in_game_dir`)
- **Description:** Writes or appends text inside the game directory (instance root); `.minecraft/` prefix targets the default launcher profile (may differ from this instance). Creates the file if missing. Supports `\n` in the value to insert line breaks; append mode controlled by the final boolean.
- **Value Required:** Yes - `path|||content|||append_bool`

## Select File from System (`select_file_to_game_dir`)
- **Description:** Opens a native file picker (any location) and copies the selected file into the game directory (instance root) or default `.minecraft/` when prefixed (that default may differ from this instance). Supports extension filters, custom filter label, and optional overwrite toggle.
- **Value Required:** Yes - selection configuration

## Show Toast (`show_toast`)
- **Description:** Displays a configurable toast notification
- **Value Required:** Yes - toast configuration

## Edit Minecraft Option (`edit_minecraft_option`)
- **Description:** Edits a Minecraft config option
- **Value Required:** Yes - `option_name:set_to_value`