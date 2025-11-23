---
title: Action Scripts
description: How to use action scripts with buttons, sliders, tickers and more.
published: true
date: 2025-11-23T08:43:54.029Z
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

# Actions in Detail

The following list contains most, if not all, actions available in FancyMenu. It is possible that the list is sometimes a bit outdated due to updates of the mod.

## Next Track (`audio_next_track`)
- **Description:** Goes to the next track in an audio element
- **Value Required:** Yes - `audio_element_identifier` (the ID of the audio element to control)

## Previous Track (`audio_previous_track`)
- **Description:** Goes to the previous track in an audio element
- **Value Required:** Yes - `audio_element_identifier` (the ID of the audio element to control)

## Set Audio Element Volume (`set_audio_element_volume`)
- **Description:** Sets the volume of an audio element
- **Value Required:** Yes - `element_identifier:1.0` (element ID and volume value between 0.0 and 1.0)

## Toggle Play Track (`audio_toggle_play`)
- **Description:** Toggles play/pause of an audio element's current track
- **Value Required:** Yes - `audio_element_identifier` (the ID of the audio element to control)

## Toggle Layout (`toggle_layout`)
- **Description:** Toggles a layout (Enable/Disable) by its name
- **Value Required:** Yes - `layout_name` (the name of the layout to toggle)

## Enable Layout (`enable_layout`)
- **Description:** Enables a layout by its name
- **Value Required:** Yes - `layout_name` (the name of the layout to enable)

## Disable Layout (`disable_layout`)
- **Description:** Disables a layout by its name
- **Value Required:** Yes - `layout_name` (the name of the layout to disable)

## Disconnect (`disconnect_server_or_world`)
- **Description:** Leaves a world or server and opens a specified screen
- **Value Required:** Yes - `screen_identifier` (identifier of screen to open after disconnecting)

## Enter World (`loadworld`)
- **Description:** Enters a Minecraft world
- **Value Required:** Yes - `world_folder_name` (folder name of the world to load)

## Join Last World/Server (`join_last_world`)
- **Description:** Enters/Joins the last world/server the player was in
- **Value Required:** No

## Join Server (`joinserver`)
- **Description:** Connects the player to a Minecraft server
- **Value Required:** Yes - `server_ip:port` (e.g., "exampleserver.com:25565")

## Back to Last Screen (`back_to_last_screen`)
- **Description:** Goes back to the previous screen (the one before the current)
- **Value Required:** No

## Close Screen (`closegui`)
- **Description:** Closes the active screen
- **Value Required:** No

## Open Screen or Custom GUI (`opengui`)
- **Description:** Opens a screen by its identifier (vanilla, mod, or custom GUI)
- **Value Required:** Yes - `screen_identifier` (identifier for the screen to open)

This action will not work for every screen, especially mod screens. If the action fails to open a screen, it will show an error. There is not much you can do in that case, because then it's probably a screen that is too complex to get opened automatically by FancyMenu.

Compatibility for mod screens will also not get added manually on FancyMenu's side anymore, because adding compatibility for all the mods out there would take ages, sorry. In most cases it is also not recommended to contact the dev of the other mod in that case, because if FancyMenu can't open the screen, there is not easy way to add support for it. The recommended workaround here is to try to use the "Mimic Button" action to mimic a button that opens the specific screen. If there is no button, then you're out of luck, sorry.

## Update Screen (`update_screen`)
- **Description:** Reinitializes the current screen
- **Value Required:** No

## Copy to Clipboard (`copytoclipboard`)
- **Description:** Copies text to the clipboard
- **Value Required:** Yes - `text_to_copy` (the text to copy)

## Edit Minecraft Option (`edit_minecraft_option`)
- **Description:** Edits a Minecraft config option
- **Value Required:** Yes - `option_name:set_to_value` (name of the option and the value to set)

## Mimic Button (`mimicbutton`)
- **Description:** Mimics the click action of a Vanilla or mod button
- **Value Required:** Yes - `screen_identifier:widget_id` (e.g., "example.menu.identifier:505280")

## Open URL in Browser (`openlink`)
- **Description:** Opens a link in your default browser
- **Value Required:** Yes - `https://example.com` (the URL to open)

## Paste to Chat (`paste_to_chat`)
- **Description:** Pastes text to the chat input field
- **Value Required:** Yes - `true:Text to paste` or `false:Text to paste` (true to append, false to replace existing text)

## Quit Minecraft (`quitgame`)
- **Description:** Quits Minecraft completely
- **Value Required:** No

## Reload FancyMenu (`reloadmenu`)
- **Description:** Reloads FancyMenu, including panoramas, slideshows, etc.
- **Value Required:** No

> This action has a **big impact on performance** and can cause lags if used in Tickers. It is not recommended to use this action in anything else than a button.
{.is-warning}

## Send Chat Message/Command (`sendmessage`)
- **Description:** Sends a chat message or executes a chat command
- **Value Required:** Yes - `message_text` or `/command_text` (if it starts with "/" it's treated as a command)

## Set Variable (`set_variable`)
- **Description:** Stores text content in a variable for use in placeholders, requirements, etc.
- **Value Required:** Yes - `variable_name:variable_value` (name and value separated by colon)

## Clear Variables (`clear_variables`)
- **Description:** Clears ALL of FancyMenu's stored variables
- **Value Required:** No

## Send HTTP Request (`send_http_request`)

Sends an HTTP request to a web target with configurable parameters.

This action allows you to send data to REST APIs, webhooks, or any HTTP endpoint.
Supports various authentication methods, custom headers, and different request types.

This action also allows you to store the response of the request in a FancyMenu variable for later use!

## Set Video Element Volume (`set_video_element_volume`)

Sets the volume of a Video menu background by its identifier.
The volume has to be a valid decimal between 0.0 (0%%) and 1.0 (100%%).

To get the identifier of a background, right-click the
editor background and click on 'Copy Background Identifier'.

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)

Toggles the paused state of a Video element.

## Set Video Background Volume (`set_video_menu_background_volume`)

Sets the volume of a Video element.
The volume has to be a valid decimal between 0.0 (0%%) and 1.0 (100%%).

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)

Toggles the paused state of a Video menu background by its identifier.

To get the identifier of a background, right-click the
editor background and click on 'Copy Background Identifier'.

# How to Set Up and Edit Actions

To add, edit, or remove actions (and statement blocks) for an element, simply **right-click the element** (whether it's a button, slider, ticker, or other interactive item) and then select **Manage Action Script**. This opens the Manage Actions screen, where you can:

- **Add new actions or statements:** Insert new action entries or control statements (if, else-if, else, while) to build your script.
- **Edit existing actions or statements:** Modify the action value or change the control logic.
- **Remove actions or statements:** Delete unwanted actions from the script.

For [listeners](/listeners) there is a special menu to manage and create listeners, including accessing their action scripts to have the same experience as when editing a button's or slider's action script for example.