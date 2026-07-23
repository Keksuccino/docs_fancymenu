---
title: Elements
description: Everything to know about FancyMenu's element types.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-07-05T21:09:31.485Z
---

# Elements

Elements are the building blocks of your custom layouts in FancyMenu. You can add them to any layout to display information, add interactivity, or create stunning visual effects.

# Adding Elements to a Layout

You can add a new element to your layout from within the **Layout Editor**.

1.  **Right-click** on the editor's background to open the context menu.
2.  Hover over **New Element**.
3.  A list of all available element types will appear. Click on the one you want to add.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Once an element is added, you can move, resize, and customize it by **right-clicking** on it to open its specific context menu. To learn more about how to arrange elements, see [Positioning Elements](./positioning-elements) and [Element Identifiers](./element-identifiers).

# Elements in Detail

This section lists FancyMenu's built-in elements. Use [Layers and Groups](./layers-and-groups) to organize their render order.

## Button
A clickable button that can perform a wide variety of actions. This is one of the most powerful and versatile elements for creating interactive menus.

*   **Use Cases:**
    *   Creating a "Join Discord" or "Visit Website" button.
    *   Adding a quick-join button for a specific server.
    *   Building custom navigation between different menus.
    *   Creating buttons that toggle other layouts on or off.
*   **Key Features:**
    *   **Actions:** Can execute a sequence of [actions](./action-scripts), such as opening a URL, joining a server, sending a chat command, mimicking another button's function, or controlling variables.
    *   **Custom Appearance:** Fully customizable textures for normal, hovered, and inactive states. Supports transparent backgrounds, nine-slicing, custom label colors, hover label colors, label scale, label shadow toggles and button icon textures.
    *   **Sounds:** Custom click, hover and unhover sounds.
    *   **Template Mode:** Can apply its appearance and properties to other Vanilla or modded buttons in the menu. See [Button & Slider Templates](./button-slider-templates).
    *   **Automated Vanilla/Mod Widget Clicks:** Existing Vanilla and mod widgets have an **Automated Clicks** property that can invoke their original click behavior a chosen number of times when the screen loads. See [Vanilla Elements](./vanilla-elements#automated-clicks) for details.

## Slider
A slider that users can drag to select a value from a list or a range. It can execute actions whenever its value changes.

*   **Use Cases:**
    *   Creating a custom volume control.
    *   A slider to switch between different themes or background images (using the "List" type).
    *   Adjusting a specific Minecraft option, like brightness or render distance.
*   **Key Features:**
    *   **Types:** Can be a `Value List` (e.g., "Easy", "Normal", "Hard"), an `Integer Range` (e.g., 1-100), or a `Decimal Range` (e.g., 0.0-1.0).
    *   **Dynamic Actions:** Executes actions when its value changes. The current value can be used with [Variables](./variables).
    *   **Customization:** The slider's label can dynamically display its current value. The handle and background textures are fully customizable, including transparent backgrounds, label color/scale options, text shadow toggles and custom click/unhover sounds.

## Checkbox
A standard checkbox that can be toggled on or off. It can execute actions upon being toggled.

*   **Use Cases:**
    *   An "I agree to the rules" checkbox.
    *   A setting to enable or disable a specific feature in your custom menu.
    *   Toggling a layout or variable on/off.
*   **Key Features:**
    *   **Actions on Toggle:** Executes [Action Scripts](./action-scripts) when its state changes. The current state (`true` or `false`) is available to its actions.
    *   **Variable Mode:** Can be linked directly to a FancyMenu variable, making the checkbox state read from and write to that variable.
    *   **Persistent State:** When Variable Mode is disabled, the checkbox automatically saves its state by element identifier and restores it after restarting the game. These states are stored in `<game-directory>/checkbox_states.json`. In Variable Mode, the linked FancyMenu variable is the checkbox's state source instead.
    *   **Custom Appearance:** Supports custom textures for the background (in normal, hover, and inactive states) and the checkmark itself.

## Text Input Field
A field where users can type text. Its content can be linked to a FancyMenu variable, allowing you to capture and use user input.

*   **Use Cases:**
    *   A "Server IP" input field that works with a "Join Server" button.
    *   A field to enter a player's name for a custom skin preview.
    *   Creating a basic login-like interface.
*   **Key Features:**
    *   **Variable Linking:** Stores the entered text in a specified [variable](./variables).
    *   **Input Validation:** Can be configured to only accept specific character types, such as numbers, URLs, or plain text.
    *   **Max Length:** You can set a maximum character limit for the input.
    *   **Appearance and Sounds:** Supports custom background color, border colors, border rounding, text color, hint/placeholder text, hint color, hover sounds, unhover sounds and click sounds.

## Tooltip
A text box that can appear at a fixed position or follow the mouse cursor. Its visibility is normally controlled with [Loading Requirements](./conditions).

*   **Use Cases:**
    *   Displaying detailed information when a user hovers over a button or image.
    *   Creating context-sensitive help tips that appear under certain conditions.
    *   Showing dynamic information (like server status) next to the cursor.
*   **Key Features:**
    *   **Mouse Following:** Can be set to follow the mouse pointer.
    *   **Markdown Support:** The tooltip content supports full Markdown formatting.
    *   **Custom Background:** The background can be a solid color or a custom nine-sliced texture for a fully themed look.

## Item
Displays a single Minecraft item, either from vanilla or a mod.

*   **Use Cases:**
    *   Using items as icons for buttons or menu selections.
    *   Creating a shop or kit selection GUI.
    *   Displaying a player's held item or armor.
*   **Key Features:**
    *   **Custom Data:** Supports a custom name, lore, count, enchantment glint, and NBT data. See the [NBT Data Placeholder](./nbt-data-placeholder).
    *   **Tooltip Display:** Can be configured to show the item's standard tooltip on hover.

## Block/Item JSON Model
Renders a block or item JSON model from Minecraft resources or external sources.

*   **Use Cases:**
    *   Displaying a 3D resource-pack model in a menu.
    *   Showing item/block previews with custom textures.
    *   Building model-based decorative UI elements.
*   **Key Features:**
    *   **Model Source:** Can load model JSON from Minecraft resources or external sources.
    *   **Texture Overrides:** Supports setting a custom texture.
    *   **Rendering Controls:** Model offset, scale, three-axis rotation, translucent rendering, and the model GUI transform.
    *   **Lighting:** Two configurable lights with independent hue and rotation controls.

## Image
Displays a static image from a local file, a web URL, or a Minecraft resource location.

*   **Use Cases:**
    *   Adding a server logo or modpack brand.
    *   Creating decorative borders or UI frames.
    *   Using images as part of a more complex UI design.
*   **Key Features:**
    *   **Nine-Slicing:** Scales borders or panels without distorting their corners. See [Nine-Slicing & Tiling](./nine-slicing-and-tiling).
    *   **Texture Repeating:** The image can be tiled to fill the element's area.
    *   **Tinting:** You can apply a color tint to the image.
    *   **Rounded Corners:** Non-nine-sliced and non-repeated images can have rounded corners.
    *   **Parallax Effect:** Moves with the mouse to create visual depth. See [Parallax Effect](./parallax).

## Text
A highly versatile element for displaying text. It can be used for anything from single-line labels to multi-page, scrollable documents.

*   **Use Cases:**
    *   Displaying server rules, patch notes, or welcome messages.
    *   Creating dynamic info panels using [placeholders](./placeholders), for example `Welcome, {"placeholder":"playername"}!`.
    *   Adding labels and descriptions to your UI.
*   **Key Features:**
    *   **Content Sources:** Text can be entered directly, loaded from a local file, or fetched from a web URL.
    *   **Markdown Support:** Supports headers, lists, code blocks, tables, and other Markdown formatting. See [Text Formatting](./text-formatting).
    *   **Scrolling:** Automatically becomes scrollable if the content is larger than the element's area. Scrollbars can be customized or disabled.
    *   **Styling:** Full control over text color, scale, alignment, shadow, and line spacing.

## Video
Plays a video file. This is perfect for cinematic intros or decorative looping backgrounds.

> [!WARNING]
> The native Video element requires **Watermedia V3** and **Watermedia Binaries V3**. The old **Video [MCEF]** element is deprecated.

*   **Use Cases:**
    *   An animated modpack or server trailer.
    *   A looping, ambient video to add life to your menu.
    *   An in-game tutorial video.
*   **Key Features:**
    *   **Sources:** Supports local video files and web URLs. See [Videos](./video).
    *   **Playback Control:** Can be set to loop automatically. Its volume, sound channel and aspect-ratio preserving behavior are adjustable.
    *   **Interactive Control:** The video's playback, seek time and volume can be controlled via button actions.

## GLSL Shader
Renders a custom GLSL shader inside an element.

*   **Use Cases:**
    *   Animated shader panels.
    *   Procedural visual effects.
    *   Shadertoy-style menu effects clipped to an element rectangle.
*   **Key Features:**
    *   **Shader Runtime:** Supports single-pass and multipass shaders.
    *   **Shadertoy Support:** Can use Shadertoy-style `mainImage` shaders.
    *   **Uniforms:** Exposes FancyMenu and input uniforms. See the [GLSL Shader API](./glsl-shader-api).

## Slideshow
Displays a sequence of images. Its images and `properties.txt` configuration file live in the slideshow's own subdirectory under `<game-directory>/config/fancymenu/slideshows/`.

*   **Use Cases:**
    *   A rotating gallery of in-game screenshots.
    *   Showcasing key features of a modpack.
    *   A dynamic background that cycles through different scenes.
*   **Key Features:**
    *   Loads preconfigured [slideshows](./slideshows).
    *   Can be set to maintain the aspect ratio of the images.

## Rectangle Shape
A simple, solid-colored rectangle.

*   **Use Cases:**
    *   Creating a semi-transparent background behind text to improve readability.
    *   Designing simple UI panels and dividers.
    *   As a colored placeholder during layout design.
*   **Key Features:**
    *   Supports HEX RGBA colors, rounded corners and optional blur, allowing the shape to work as a simple panel, tint or blur background.

## Circle Shape
A simple, solid-colored circle/ellipse shape.

*   **Use Cases:**
    *   Creating circular accents, indicators or soft UI areas.
    *   Building themed UI decorations without a texture file.
*   **Key Features:**
    *   Supports color, blur, and a configurable roundness/exponent value.

## Splash Text
A recreation of Minecraft's iconic yellow, bouncing splash text from the title screen.

*   **Use Cases:**
    *   Replacing the vanilla splash text with your own custom messages.
    *   Adding an eye-catching, animated message to any menu.
*   **Key Features:**
    *   **Content Sources:** Can use the default vanilla splashes, a list of custom text entered directly, or text from a local file.
    *   **Customization:** You can toggle the bouncing effect and customize the text's color, scale, rotation, and shadow.

## Player Entity
Renders a player model in the menu.

*   **Use Cases:**
    *   Displaying the current player's character on the main menu.
    *   Creating a team selection or class preview screen.
    *   A "profile" section showing the player's skin and name.
*   **Key Features:**
    *   **Dynamic Appearance:** Can copy the current player's skin, cape, and name. See [Player Heads](./player-heads).
    *   **Custom Poses:** Offers fine-grained control over the rotation of the head, body, arms, and legs. The head and body can also be set to follow the mouse cursor.
    *   **Attributes:** Can be set to be a baby, crouching, or have a slim model.

## Browser
An element that renders a live web page inside the game.

This element requires the **MCEF (Minecraft Chromium Embedded Framework)** mod to be installed and working!

You can download MCEF from the official project pages on [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) and [Modrinth](https://modrinth.com/mod/mcef).

For newer Minecraft versions (1.21.5+), the official MCEF projects do not provide builds, but there is a fork with builds for latest Minecraft versions, which can be found [here](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) and [here](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). This fork is maintained by Keksuccino, to get builds for latest Minecraft versions out as fast as possible.

*   **Use Cases:**
    *   Displaying a server's live Dynmap.
    *   Embedding a YouTube video player.
    *   Showing a wiki or documentation page directly in-game.
*   **Key Features:**
    *   **Interactivity:** Can be made fully interactable, allowing users to click links, scroll, and type.
    *   **Media Control:** Offers options to mute media, loop videos, and hide video controls on the loaded page.

### Loading Local HTML Files
The Browser element can load local HTML documents from `<game-directory>/config/fancymenu/assets/`.

To load a local HTML file, start your URL with `file:///`, followed by the SHORT file path, for example `/config/fancymenu/assets/cool_changelog.html`, which makes it look like this: `file:///config/fancymenu/assets/cool_changelog.html`.

On **Linux**, use the [**Absolute File/Folder Path** placeholder](./placeholders#absolute-filefolder-path-absolute_path) instead of hardcoding an instance-specific absolute path: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

The Linux short path must begin with `/`, as shown in the example.

## Element Animator
A powerful tool for creating complex, keyframe-based animations. It can animate the position, size, and anchor point of one or multiple other elements.

*   **Use Cases:**
    *   Sliding elements into or out of view.
    *   Resizing panels or notifications.
    *   Animating position offsets and anchor transitions.
*   **Key Features:**
    *   **Keyframe Editor:** A dedicated editor for adding, editing, and sequencing keyframes on a timeline.
    *   **Multi-Target:** A single Animator can control multiple "target" elements at once.
    *   **Control:** Animations can be set to loop. You can also choose to animate only position or size.
    *   **Timing Offsets:** Target elements can use individual or randomized start timing offsets.
    *   See [Element Animator](./element-animator) for setup and keyframe editing.

## Ticker
An invisible element that executes a list of actions at a regular interval (every "tick").

> [!NOTE]
> For background automation, consider using [Schedulers](./schedulers). Schedulers are global and can run independently of a specific screen.

*   **Use Cases:**
    *   Periodically checking a server's online status and updating a text element.
    *   Creating a countdown timer that updates a text label.
    *   Running a script repeatedly to create custom behaviors.
*   **Key Features:**
    *   **Timing Control:** You can set the delay between ticks in milliseconds.
    *   **Tick Modes:** Can be set to tick continuously, only once per game session, or once every time the menu is loaded.
    *   **Asynchronous:** Can run its [actions](./action-scripts) separately, although some actions cannot run while this option is enabled.

## Audio
An invisible element that plays audio files. It can manage a playlist of tracks and offers various playback controls.

*   **Use Cases:**
    *   Adding custom background music to a menu.
    *   Creating a music player with buttons to control playback (next/previous track, volume).
    *   Playing ambient soundscapes.
*   **Key Features:**
    *   **Playlist:** Can manage multiple audio tracks.
    *   **Playback Modes:** Can play tracks in order or shuffle them (with support for track weighting to make some tracks more common than others).
    *   **Control:** Supports looping, volume adjustment, and sound-channel selection. See [Menu Background Music](./background-music).

## Music Controller
An invisible element used to control Minecraft's default music playback within a specific menu.

*   **Use Cases:**
    *   Disabling the default menu music on a screen where you want to play your own custom music via an [**Audio** element](#audio).
    *   Stopping in-world music from continuing to play when a menu is opened in-game.
*   **Key Features:**
    *   Separate toggles to control vanilla "Menu Music" and "World Music."

## Progress Bar
A customizable bar that visually represents a numerical value.

*   **Use Cases:**
    *   A loading bar that tracks world loading progress using `{"placeholder":"world_load_progress"}`.
    *   Visual health, hunger, or experience bars for an in-game HUD.
    *   A volume indicator that is controlled by a [**Slider** element](#slider).
*   **Key Features:**
    *   **Dynamic Value:** The progress value (0-100 or 0.0-1.0) is set via a text field that supports [placeholders](./placeholders).
    *   **Appearance:** The bar's direction (up, down, left, right), colors, textures and nine-slicing for bar/background textures are all customizable.
    *   **Animation:** Features a smooth filling animation to make progress changes look less jarring.
    *   **Progress-Based Element Anchor:** When another element uses the progress bar as its **Element** anchor, enable **Use Progress for Element Anchor** to move that anchor to the current edge of the filled area. Anchored elements then travel with the bar's progress instead of staying attached to the progress bar's static bounds.

## Dragger
An invisible element that the user can click and drag to move around. Other elements can be anchored to it to create movable widgets.

*   **Use Cases:**
    *   Creating a draggable clock or information panel.
    *   Allowing users to customize the position of UI elements to their preference.
*   **Key Features:**
    *   **Optional Persistence:** Enable **Save User Drag Offset** to keep the user's dragged position across screen openings and game restarts. Disable it to reset the offset.
    *   **Anchor Point:** Acts as a movable anchor for other elements, which is a key part of [Positioning Elements](./positioning-elements).

## Cursor
An invisible element that replaces the default system cursor with a custom image when a layout is active.

*   **Use Cases:**
    *   Creating a fully themed UI that matches your modpack's aesthetic.
*   **Key Features:**
    *   **Custom Texture:** Use any image for your cursor.
    *   **Hotspot:** Sets the exact image pixel used as the click point. See [Custom Cursor](./custom-cursor).
