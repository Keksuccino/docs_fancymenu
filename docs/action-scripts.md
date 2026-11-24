---
title: Action Scripts
description: Make buttons and menus do things with action scripts, and every action FancyMenu has.
---

# Action Scripts

An action script is a list of things FancyMenu does when something happens, like a button getting clicked or a menu opening. Each thing is an action: open a menu, join a server, show a message, play a sound and more. Statements like IF and WHILE decide which actions run and how often.

> [!CAUTION]
> Action scripts can change files, contact servers, open links and run commands. Only use scripts from layouts you trust.

<img width="800" alt="A button's action script gets made in the layout editor: Edit Action Script, the action chooser with Show Toast, and the toast's title and message" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_make.gif?raw=true">

# Making an Action Script

1. In the layout editor, right-click a button and click **Edit Action Script**.
2. Press `A` to open the action chooser.
3. Search the action, click it and click **Next Step**.
4. Set up the action in its window and click **Done**. Actions without settings only need **Done** in the chooser.
5. Click **Done** in the script editor, then save the layout.

Outside the editor, the button runs its script when it gets clicked:

<img width="800" alt="Clicking the What's New? button on the title screen shows a toast with the update title and message" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_use.gif?raw=true">

> [!TIP]
> Right-click the script area and open **Add Action** for a list of all actions. Right-click an action in that list to make it a favorite, so it shows at the top.

# Where You Can Use Action Scripts

| Where | Runs when | Where to edit it |
|---|---|---|
| [Button](/elements#button) | The button gets clicked. | Right-click the button -> **Edit Action Script** |
| [Slider](/elements#slider) | The slider's value changes. `$$value` is the new value. | Right-click the slider -> **Edit Action Script** |
| [Checkbox](/elements#checkbox) | The checkbox gets ticked or unticked. `$$value` is its new state, `true` or `false`. | Right-click the checkbox -> **Edit Action Script** |
| [Ticker](/elements#ticker) | As its **Tick Mode** says: over and over, once per game session, or once when the menu loads. | Right-click the ticker -> **Edit Action Script** |
| Opening a menu | The menu of the layout opens. | Right-click the editor background -> **Edit 'Open Screen' Action Script** |
| Closing a menu | The menu of the layout closes. | Right-click the editor background -> **Edit 'Close Screen' Action Script** |
| [Listeners](/listeners) | Their event happens, like a key press or a chat message. | **menu bar -> Customization -> Manage Listeners** |
| [Schedulers](/schedulers) | On their timer, even when no menu is open. | **menu bar -> Customization -> Manage Schedulers** |

The open and close scripts are also in the editor's **Layout -> Layout Properties** menu.

# The Script Editor

- Actions run from top to bottom. Entries inside a statement or folder are indented below it.
- New entries go below the selected entry. When a statement or folder is selected, they go to its start.
- Double-click a value to edit it right in the list. Values that show a short summary open their window instead.
- Drag entries to move them. IF chains, loops and folders fold up with the small toggle in front of them. That only changes the view.
- The bar on the right is a map of the whole script. Click it to jump to a part.
- Right-click the script area for everything else, like adding statements and **Export Action Script for AI** (see [Export for AI](/export-for-ai)).
- **Cancel** or closing the window throws away your changes. If there are any, the editor asks first.

## Shortcuts

`Ctrl` is `Cmd` on macOS.

| Shortcut | What it does |
|---|---|
| `A` | Opens the action chooser. |
| `Enter` | Edits the selected entry. |
| `Delete` | Deletes the selected entry. |
| `Up` / `Down` | Selects the entry above or below. |
| `Shift + Up` / `Shift + Down` | Moves the selected entry up or down. |
| `Ctrl + C` / `Ctrl + V` | Copies and pastes an action. Statements and blocks can't be copied. |
| `Ctrl + Z` | Undo. |
| `Ctrl + Y` or `Ctrl + Shift + Z` | Redo. |
| `Ctrl + S` | Saves the script and closes the editor, like **Done**. |

# Statements

Statements decide which actions run and how often. Add them by right-clicking the script area.

## If, Else-If and Else

**Add IF Statement** asks for [requirements](/conditions). The actions inside the IF only run when they're met.

Right-click an IF to add more to its chain:

- **Append ELSE-IF Statement**: checks its own requirements when the IF above didn't run.
- **Append ELSE Statement**: runs when nothing above it in the chain ran.

For example, an IF with **Is Layout Enabled** can show a toast only while the winter layout is on, and an ELSE plays a sound otherwise.

## While Loop

**Add WHILE Loop** repeats its actions as long as its [requirements](/conditions) are met.

Every run stops after 3 seconds, so a loop that never ends can't freeze the game. It's no timer: for things that should happen later or over and over, use [Execute Later](#execute-later), a [Ticker](/elements#ticker) or a [Scheduler](/schedulers).

## For Each Loop

**Add FOR EACH Loop** runs its actions once for every entry of a [list variable](/variables#text-and-list-variables), from the first entry to the last.

- `$$list_entry` is the current entry and `$$list_index` its index. The first entry has index 0.
- Both work in action values and requirements inside the loop.
- Type the list's name without `$$`, like `quest_log`. Placeholders in the name work too.
- The loop reads the list once when it starts, so actions inside it can change the list safely.
- Like WHILE loops, every run stops after 3 seconds.

See [Going Through a List](/variables#going-through-a-list) for examples.

# Blocks

Blocks change when actions run or keep your script tidy. Add them by right-clicking the script area.

## Delay Gate

**Add DELAY GATE Block** holds its actions back for a time in milliseconds (`1000` is one second).

- The first time the script reaches the gate, it starts its timer and skips its actions. The rest of the script runs on right away.
- Every time the script reaches it again before the time is over, it skips them again.
- From then on, its actions run every time the script reaches it.
- In scripts of elements, the timer starts over when the menu opens again or gets resized.

That makes it good for [Tickers](/elements#ticker), like showing something only after a menu was open for a few seconds. It never runs anything on its own: use Execute Later for that.

## Execute Later

**Add EXECUTE LATER Block** runs its actions once after a time in milliseconds. The rest of the script runs on right away.

Every time the script reaches the block, it starts a new countdown. That's good for scripts that only run once, like a button click or opening a menu.

## Folder

**Add Folder** groups actions under a name. It runs everything inside it and only helps to keep long scripts tidy. Double-click its name to rename it.

## Comment

**Add Comment** adds a note for yourself. It does nothing. Double-click it to edit it.

# How Scripts Run

- Actions run from top to bottom. An action that fails writes an error to the game log, and the rest of the script still runs.
- Placeholders in values get their current value right when the action runs, so an action sees what the actions before it changed.
- Downloads, extracting ZIP files and web requests finish in the background. The next action doesn't wait for them. To run actions when they're done, use the listeners [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action-file_downloaded_via_action) and [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action-zip_extracted_via_action), or a response variable of [**Send HTTP Request**](#send-http-request-send_http_request).

# Values of Actions

Most actions need a value, like the address of a server. Simple values are text you type. Actions with more settings have their own window.

## Placeholders

Values can contain [placeholders](/placeholders), like the player's name. They get replaced when the action runs:

```
/say Welcome back, {"placeholder":"playername"}!
```

## $$ Variables

`$$` and a name gives the value of a variable, like `$$coins`. Besides your own [variables](/variables#showing-variables-in-text), some features give their script variables of their own:

- A [Slider](/elements#slider) gives `$$value`, its new value.
- A [Checkbox](/elements#checkbox) gives `$$value`, its new state: `true` or `false`.
- A [For Each Loop](#for-each-loop) gives `$$list_entry` and `$$list_index`.
- Each [listener](/listeners#listener-variables) lists the variables it gives, like the key that got pressed.

These only exist in the script that gets them. Upper and lower case of names matter.

# Actions in Detail

This section lists FancyMenu's built-in actions.

## Next Track (`audio_next_track`)

Skips to the next track of an [Audio element](/elements#audio).

**Value:** the identifier of the Audio element, like `menu_music`

## Previous Track (`audio_previous_track`)

Goes back to the previous track of an [Audio element](/elements#audio).

**Value:** the identifier of the Audio element

## Set Track Volume (`set_audio_element_volume`)

Sets the volume of an [Audio element](/elements#audio), from `0.0` (0%) to `1.0` (100%).

**Value:** `element_identifier:volume`, like `menu_music:0.5`

## Toggle Play/Pause Track (`audio_toggle_play`)

Pauses a playing [Audio element](/elements#audio), or plays a paused one.

**Value:** the identifier of the Audio element

## Play Audio (`play_audio`)

Plays an audio file once, set up in its window: the **Audio Source**, the **Sound Channel** and the **Base Volume** (up to 100%).

- FancyMenu waits up to ten seconds for the audio to load.
- Doesn't work in a [Ticker](/elements#ticker) that runs in the background (asynchronous). FancyMenu shows an error instead.

[**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios) stops audios started by this action.

## Stop All Action Audios (`stop_all_action_audios`)

Stops every audio started by [**Play Audio**](#play-audio-play_audio). Audio elements, menu sounds and button sounds keep playing.

**Value:** none

## Set Video Element Volume (`set_video_element_volume`)

Sets the volume of a [Video element](/video), from `0.0` (0%) to `1.0` (100%).

**Value:** `video_element_identifier:volume`

## Set Video Element Play Time (`set_video_element_play_time`)

Jumps to a time of a [Video element](/video), in milliseconds.

**Value:** `video_element_identifier:time_in_ms`, like `intro_video:30000`

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)

Pauses a playing [Video element](/video), or plays a paused one.

**Value:** the identifier of the Video element

## Set Video Background Volume (`set_video_menu_background_volume`)

Sets the volume of a [Video menu background](/video), from `0.0` (0%) to `1.0` (100%).

**Value:** `background_identifier:volume`

> [!NOTE]
> To get the identifier of a menu background, right-click the editor background and click **Copy Background Identifier**.

## Set Video Background Play Time (`set_video_menu_background_play_time`)

Jumps to a time of a [Video menu background](/video), in milliseconds.

**Value:** `background_identifier:time_in_ms`

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)

Pauses a playing [Video menu background](/video), or plays a paused one.

**Value:** the identifier of the menu background

## Toggle Layout (`toggle_layout`)

Turns a layout off when it's on, and on when it's off.

**Value:** the layout's name, without `.txt`, like `winter_title_screen`

## Enable Layout (`enable_layout`)

Turns a layout on.

**Value:** the layout's name, without `.txt`

## Disable Layout (`disable_layout`)

Turns a layout off.

**Value:** the layout's name, without `.txt`

All three layout actions save the change and update the open menu right away. Upper and lower case of the name matter.

## Open Screen or Custom GUI (`opengui`)

Opens a menu of the game, a mod or a [Custom GUI](/custom-guis).

**Value:** the [screen identifier](/screen-identifiers), like `options_screen`

Upper and lower case matter. Some mod menus can't get opened this way. Then use [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) on a button that opens it.

## Close Screen (`closegui`)

Closes the open menu. Outside of worlds, the title screen opens.

**Value:** none

## Update Screen (`update_screen`)

Rebuilds the open menu, like resizing the window does. Useful after changing the GUI scale or other options.

**Value:** none

## Back to Last Screen (`back_to_last_screen`)

Goes back to the menu that was open before. For a [Custom GUI](/custom-guis), that's the menu it got opened from.

**Value:** none

## Join Server (`joinserver`)

Connects to a Minecraft server.

**Value:** `address` or `address:port`, like `play.example.net`

Without a port, `25565` is used. While a world or server is loaded, it shows an error instead. Servers that aren't in the server list get added to it.

## Enter World (`loadworld`)

Loads a singleplayer world.

**Value:** the world's folder name in `saves`, like `Survival Island`

Does nothing if there's no such world. While a world or server is loaded, it shows an error instead.

## Enter/Join Last World/Server (`join_last_world`)

Loads the world or joins the server the player played last.

**Value:** none

While a world or server is loaded, it shows an error instead. A server that isn't in the server list gets added to it.

## Leave World or Server (`disconnect_server_or_world`)

Leaves the world or server and opens a menu.

**Value:** the [screen identifier](/screen-identifiers) of the menu to open, like `title_screen`

Only works while a world is loaded. [Custom GUIs](/custom-guis) work too. If the menu can't get opened, the title screen opens.

## Quit Minecraft (`quitgame`)

Closes the game.

**Value:** none

## Send Chat Message/Command (`sendmessage`)

Sends a chat message or runs a command, like the player typed it.

**Value:** the message, or a command with `/`, like `/spawn`

## Execute Command As Integrated Server (`execute_command_as_integrated_server`)

Runs a command in singleplayer as the server, no matter the player's permissions or the cheats setting.

**Value:** the command, like `/give @p minecraft:diamond 1`

> [!WARNING]
> Only works in singleplayer while the world is not open to LAN. Everywhere else, it does nothing.

## Paste to Chat (`paste_to_chat`)

Puts text into the chat input field while a world is loaded. If chat isn't open, it opens with the text.

**Value:** `true:text` adds the text to what's already typed, `false:text` replaces it

## Display In Chat [Client-Side] (`display_in_chat_client_side`)

Shows a chat message only this player sees. Nothing gets sent to the server.

**Value:** the text, with [formatting codes](/text-formatting#minecraft-text-formatting) or as Minecraft text component JSON, like `&aWelcome back!`

Does nothing when no world is loaded.

## Send FM Data To Server (`send_fm_data_to_server`)

Sends [FM Data](/fm-data) to the server, which needs FancyMenu too.

**Value:** `data_identifier||data`

## Connect To Remote Server (`connect_to_remote_server`)

Connects to a remote server, or uses the connection that's already open.

**Value:** the server's address, like `wss://example.com/ws`

See [Remote Server Communication](/remote-server-communication#url-modes) for the addresses that work.

## Send Data To Remote Server (`send_data_to_remote_server`)

Sends text to a remote server, and connects first if needed.

**Value:** `server_address||data`

## Close Remote Server Connection (`close_remote_server_connection`)

Closes one remote server connection.

**Value:** its request ID, usually `$$request_id` from [**On Remote Server Connected**](/listeners#on-remote-server-connected-remote_server_connected)

## Close All Remote Server Connections (`close_all_remote_server_connections`)

Closes every remote server connection FancyMenu opened.

**Value:** none

## Open URL in Browser (`openlink`)

Opens a link in the default browser, without asking first.

**Value:** the link, like `https://discord.gg/example`

Only use links you trust.

## Copy Text to Clipboard (`copytoclipboard`)

Copies text to the clipboard.

**Value:** the text, like `play.example.net`

## Print to Game Log (`print_to_log`)

Writes a line to the game log. Useful to find out what a script does.

**Value:** the text

## Set Variable Value (FM Variable) (`set_variable`)

Sets a [variable](/variables).

**Value:** `variable_name:value`, like `coins:100`

- Only the first `:` separates the name from the value.
- [List variables](/variables#text-and-list-variables) stay lists: a JSON array like `["a","b"]` becomes their entries, other text their only entry, and empty text empties them.

## Delete Variable (FM Variable) (`delete_variable`)

Deletes a [variable](/variables) completely. All other variables stay. To only empty it, use [**Set Variable Value (FM Variable)**](#set-variable-value-fm-variable-set_variable).

**Value:** the variable's name

## Clear All Variables (FM Variable) (`clear_variables`)

Deletes all [variables](/variables), text and list variables.

**Value:** none

## Add to List (FM Variable) (`add_to_list`)

Adds an entry to a [list variable](/variables#list-actions).

- **List Variable**: the list's name. If there's no variable with that name yet, the action creates the list.
- **New Entry**: the text of the entry.
- **Index (Optional)**: where the entry goes. Empty adds it at the end. The entries from there on move back by one.
- **Skip If Already in List**: adds nothing when the list already has an entry with the same text. **Ignore Case** makes `Apple` match `apple`.

## Set List Entry (FM Variable) (`set_list_entry`)

Replaces the entry at an **Index** of a [list variable](/variables#list-actions) with a **New Value**. Does nothing if the list has no entry there.

## Remove from List (FM Variable) (`remove_from_list`)

Removes entries from a [list variable](/variables#list-actions). **Remove** picks which:

- **Entry at Index**: the entry at an index.
- **First Match**: the first entry with exactly the **Value to Remove**.
- **All Matches**: every entry with it.

**Ignore Case** makes `Apple` match `apple`.

## Clear List (FM Variable) (`clear_list`)

Removes all entries of a [list variable](/variables#list-actions). The empty list stays.

## Set List (FM Variable) (`set_list`)

Replaces all entries of a [list variable](/variables#list-actions). **Entries From** picks where they come from:

- **Split Text**: cuts the **Text to Split** at the **Separator**, like `,`. An empty separator splits at line breaks. **Trim Entries** removes spaces at their start and end, **Skip Empty Entries** leaves out empty ones.
- **JSON Array**: the entries of an array like `["Diamonds","Emeralds"]`, or `$$other_list` to copy another list. Other text becomes the only entry, and empty text empties the list.

The window shows a preview of the entries.

## Arrange List (FM Variable) (`arrange_list`)

Changes the order of a [list variable](/variables#list-actions). **Arrangement**:

- **Sort A–Z** and **Sort Z–A**: sorts alphabetically.
- **Numbers, Smallest First** and **Numbers, Biggest First**: sorts by number. Entries that aren't numbers go to the end.
- **Reverse Order**: the last entry becomes the first.
- **Shuffle**: a random order.
- **Remove Duplicates**: keeps only the first entry of every value.

In all list actions, the first entry has index `0` and `-1` is the last one. The list name can contain placeholders, and with `$$` in front, the action uses the value of that variable as the list's name. Text variables that have a value stay as they are, and the action writes a warning to the game log.

## Send HTTP Request (`send_http_request`)

Sends a web request in the background. It can write the answer to the game log or store it in a variable.

| Setting | What it does |
|---|---|
| URL | The HTTP or HTTPS address. |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` or `OPTIONS`. |
| Body | The data to send. Not sent with `GET` and `HEAD`. |
| Content type | The `Content-Type` of the body, like `application/json`. |
| Timeout | Seconds to wait for the connection and the answer. |
| Log response | Writes the answer to the game log. |
| Response variable | Stores the answer in this variable when it arrives. |
| Single-line response | Removes line breaks from the answer before storing it. |
| Authentication | None, Basic, Bearer or API key. |
| Headers | Extra request headers. |

The next action doesn't wait for the answer. Error answers get logged and stored too. Don't put passwords or access tokens in the action: anyone with the layout can read them.

## Manage Resource Pack (`manage_resource_pack`)

Turns a resource pack on or off, set up in its window:

- **Target Resource Pack**: the pack's name as the Resource Packs screen shows it. Upper and lower case don't matter.
- **Action Mode**: **Enable**, **Disable** or **Toggle**.
- **Reload Resources**: reloads the resource packs right after the change. Turn it off to reload later, like with [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs).

Packs the game needs can't get turned off.

## Reload Resource Packs (`reload_resource_packs`)

Reloads the resource packs, like `F3 + T`. For five seconds after a reload, the action does nothing, so it can't reload over and over.

**Value:** none

## Reload FancyMenu (`reloadmenu`)

Reloads layouts, [Custom GUIs](/custom-guis), [panoramas](/panoramas), [slideshows](/slideshows), settings and files of FancyMenu. Resource packs don't get reloaded.

**Value:** none

> [!WARNING]
> Reloading takes a moment. Use it on a button, never in a [Ticker](/elements#ticker) or a [listener](/listeners) that runs often.

## Toggle Element Animator (`toggle_element_animator`)

Turns an [Element Animator](/element-animator) on when it's off, and off when it's on. The animation starts from the beginning. The state stays saved.

**Value:** the identifier of the Element Animator

## Enable Element Animator (`enable_element_animator`)

Turns an [Element Animator](/element-animator) on. When it was off, its animation starts from the beginning.

**Value:** the identifier of the Element Animator

## Disable Element Animator (`disable_element_animator`)

Turns an [Element Animator](/element-animator) off and resets its animation.

**Value:** the identifier of the Element Animator

## Reset Element Animator (`reset_element_animator`)

Starts the animation of an [Element Animator](/element-animator) from the beginning, without turning it on or off.

**Value:** the identifier of the Element Animator

## Mimic Vanilla/Mod Button (`mimicbutton`)

Clicks a button of the game or a mod, like the player did.

**Value:** the button's [widget locator](/widget-locators), like `title_screen:mc_titlescreen_options_button`

To get it, right-click the button in the editor and click **Copy Widget Locator**.

## Mimic Keybind (`mimic_keybind`)

Presses a key binding of Minecraft, like jump or sneak, and can hold it down.

**Value:** `keybind|||hold|||duration_ms`, like `key.jump|||false|||1000`

| Part | What it is |
|---|---|
| `keybind` | The key binding's ID, like `key.jump` or `key.sneak`. |
| `hold` | `true` holds the key, `false` presses it once. |
| `duration_ms` | How long it gets held, in milliseconds. Without it, `1000`. |

## Set Text Input Field Value (`set_text_input_field_value`)

Sets the text of a [Text Input Field](/elements#text-input-field), from FancyMenu or the game.

**Value:** `element_identifier|||text|||force`

With `force` set to `true`, the text also changes when the field is turned off (inactive).

## Scroll an Element (`scroll_scroll_area`)

Scrolls a [Scrollable Area](/scrollable-areas) or a [Text](/elements#text) element, set up in its window:

- **Identifier of the Element to Scroll**: the area or Text to scroll.
- **Scroll To**:
  - **Start** or **End**.
  - **Position**: the **Horizontal Position** and **Vertical Position** in pixels. Leave one empty to keep it.
  - **Element** (only areas): scrolls until the element with the **Identifier of the Element to Scroll To** is at the start.
  - **Line Number** (only Texts): the first line is `1`.
  - **Line with Text** (only Texts): the first line that contains the **Text in the Line**. Upper and lower case don't matter.
- **Glide There**: glides there instead of jumping. Needs smooth scrolling on for the element.

Does nothing when there's no such element.

## Create File in Game Directory (`create_file_in_game_dir`)

Creates an empty file. Missing folders get created too. An existing file stays as it is.

**Value:** the file's path, like `config/mymodpack/first_start.txt`

All file actions only work inside the game folder (instance folder). Paths that start with `.minecraft/` use the default `.minecraft` folder instead, which can be a different folder.

## Delete File/Folder in Game Directory (`delete_file_in_game_dir`)

Deletes a file, or a folder with everything in it.

**Value:** the path, like `config/mymodpack/cache.txt`

With `*` at the end, like `config/downloads/*`, it deletes all files directly in that folder, but keeps the folder and the folders in it.

## Copy File/Folder in Game Directory (`copy_file_in_game_dir`)

Copies a file, or a folder with everything in it.

**Value:** `source||destination`, like `config/presets/default.json||config/mymod/settings.json`

- With `*` at the end of the source, like `config/presets/*||config/mymod/`, it copies all files directly in that folder, but no folders. The destination is a folder then, and gets created when needed.
- Nothing gets overwritten: when the destination already exists, the action fails.

## Move File/Folder in Game Directory (`move_file_in_game_dir`)

Moves a file, or a folder with everything in it.

**Value:** `source||destination`

The `*` at the end of the source works like in [**Copy File/Folder in Game Directory**](#copy-filefolder-in-game-directory-copy_file_in_game_dir). Nothing gets overwritten.

## Rename File/Folder in Game Directory (`rename_file_in_game_dir`)

Renames a file or folder. Fails when something with the new name already exists.

**Value:** `path||new_name`, like `config/mymod/old_name.txt||new_name.txt`

## Download File to Game Directory (`download_file_to_game_dir`)

Downloads a file into a folder, in the background.

**Value:** `url||target_folder`, like `https://example.com/pack.zip||downloads`

- The second part is a folder, not a file name. FancyMenu takes the name from the download or the link.
- A file with the same name gets overwritten.
- [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action-file_downloaded_via_action) runs when the download is done or failed. On success, its `$$target_file_path` is the saved file.

## Extract ZIP File In Game Directory (`extract_zip_file_in_game_dir`)

Extracts a ZIP file into a folder, in the background.

**Value:** `zip_path||target_folder`, like `downloads/pack.zip||resourcepacks/MyPack`

Files with the same names get replaced, and no extra folder named like the ZIP gets made. [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action-zip_extracted_via_action) runs when it's done. Only extract ZIP files you trust.

## Open File/Folder In Game Directory (`open_file_folder_in_game_dir`)

Opens a file or folder with the program the system uses for it.

**Value:** the path, like `screenshots`

## Write File in Game Directory (`write_file_in_game_dir`)

Writes text into a file. The file and its folders get created when needed.

**Value:** `path|||text|||append`, like `config/mymodpack/log.txt|||Joined the server\n|||true`

`\n` starts a new line. `append` set to `true` adds the text at the end of the file, `false` replaces what's in it.

## Select File from System (`select_file_to_game_dir`)

Opens the system's file picker, and copies the picked file into the game folder.

**Value:** `target_path|||filter_name|||extensions|||overwrite`, like `config/fancymenu/assets/background.png|||Images|||png;jpg|||true`

- `target_path` is the full path of the copy, file name included.
- Separate extensions with `;` or `,`. Without extensions, all files can be picked.
- With `overwrite` set to `false`, the action fails when the file already exists.

[**On File Selected**](/listeners#on-file-selected-file_selected_via_action) runs when the file got copied, the picker got cancelled or something failed.

## Show Toast (`show_toast`)

Shows a toast notification in the top-right corner, set up in its window:

- **Toast Width**: from 120 to 320 pixels.
- **Duration (ms)**: how long it stays, from 1 second (`1000`) to 10 minutes.
- **Title** and **Message**: text with [formatting codes](/text-formatting#minecraft-text-formatting), or Minecraft text component JSON.
- **Icon Texture Source** and **Background Texture Source**: optional [images](/resources). Icons look best at 20x20 pixels, backgrounds should be 32 pixels tall and as wide as the toast.

## Start Scheduler (`start_scheduler`)

Starts a [scheduler](/schedulers).

**Value:** the scheduler's identifier

## Stop Scheduler (`stop_scheduler`)

Stops a [scheduler](/schedulers).

**Value:** the scheduler's identifier

## Set Minecraft Option (`edit_minecraft_option`)

Changes an option of Minecraft, like the render distance or the GUI scale.

**Value:** `option_name:value`, like `renderDistance:12`

See [Minecraft Options](/minecraft-options) for the option names.
