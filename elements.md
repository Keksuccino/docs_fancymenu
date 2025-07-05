---
title: Elements
description: Everything to know about FancyMenu's element types.
published: true
date: 2025-07-05T21:11:38.893Z
tags: 
editor: markdown
dateCreated: 2025-07-05T21:09:31.485Z
---

# Element Types

Elements are the building blocks of your custom layouts in FancyMenu. You can add them to any layout to display information, add interactivity, or create stunning visual effects.

# Adding Elements to a Layout

You can add a new element to your layout from within the **Layout Editor**.

1.  **Right-click** on the editor's background to open the context menu.
2.  Hover over **New Element**.
3.  A list of all available element types will appear. Click on the one you want to add.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Once an element is added, you can move, resize, and customize it by **right-clicking** on it to open its specific context menu. To learn more about how to arrange elements, see the [Positioning Elements](https://docs.fancymenu.net/en/positioning-elements) and [Element Identifiers](https://docs.fancymenu.net/en/element-identifiers) pages.

# All Element Types

The following list contains many of FancyMenu's element types, but it is possible that it does not contain all of them due to the site not being updated yet for the latest FancyMenu release or similar.

## Button
A clickable button that can perform a wide variety of actions. This is one of the most powerful and versatile elements for creating interactive menus.

*   **Use Cases:**
    *   Creating a "Join Discord" or "Visit Website" button.
    *   Adding a quick-join button for a specific server.
    *   Building custom navigation between different menus.
    *   Creating buttons that toggle other layouts on or off.
*   **Key Features:**
    *   **Actions:** Can execute a sequence of actions, such as opening a URL, joining a server, sending a chat command, mimicking another button's function, controlling variables, and much more. Learn more at the [Action Scripts](https://docs.fancymenu.net/en/action-scripts) documentation.
    *   **Custom Appearance:** Fully customizable textures for normal, hovered, and inactive states. Supports nine-slicing for scalable button backgrounds.
    *   **Sounds:** Custom click and hover sounds.
    *   **Template Mode:** Can act as a template to apply its appearance and properties to all other Vanilla or modded buttons in the menu, ensuring a consistent look. Read more at the [Button & Slider Templates](https://docs.fancymenu.net/en/button-slider-templates) page.

## Slider
A slider that users can drag to select a value from a list or a range. It can execute actions whenever its value changes.

*   **Use Cases:**
    *   Creating a custom volume control.
    *   A slider to switch between different themes or background images (using the "List" type).
    *   Adjusting a specific Minecraft option, like brightness or render distance.
*   **Key Features:**
    *   **Types:** Can be a `Value List` (e.g., "Easy", "Normal", "Hard"), an `Integer Range` (e.g., 1-100), or a `Decimal Range` (e.g., 0.0-1.0).
    *   **Dynamic Actions:** Executes actions on value change. The slider's current value can be used within its actions to perform dynamic tasks, which can be used with [Variables](https://docs.fancymenu.net/en/variables).
    *   **Customization:** The slider's label can dynamically display its current value. The handle and background textures are fully customizable.

## Checkbox
A standard checkbox that can be toggled on or off. It can execute actions upon being toggled.

*   **Use Cases:**
    *   An "I agree to the rules" checkbox.
    *   A setting to enable or disable a specific feature in your custom menu.
    *   Toggling a layout or variable on/off.
*   **Key Features:**
    *   **Actions on Toggle:** Executes [Action Scripts](https://docs.fancymenu.net/en/action-scripts) when its state changes. The current state (`true` or `false`) can be accessed within its actions.
    *   **Custom Appearance:** Supports custom textures for the background (in normal, hover, and inactive states) and the checkmark itself.

## Text Input Field
A field where users can type text. Its content can be linked to a FancyMenu variable, allowing you to capture and use user input.

*   **Use Cases:**
    *   A "Server IP" input field that works with a "Join Server" button.
    *   A field to enter a player's name for a custom skin preview.
    *   Creating a basic login-like interface.
*   **Key Features:**
    *   **Variable Linking:** The text entered by the user is stored in a specified [variable](https://docs.fancymenu.net/en/variables).
    *   **Input Validation:** Can be configured to only accept specific character types, such as numbers, URLs, or plain text.
    *   **Max Length:** You can set a maximum character limit for the input.

## Tooltip
A text box that can be configured to appear at a specific location or follow the mouse cursor. Its visibility is typically controlled by [Conditions (Loading Requirements)](https://docs.fancymenu.net/en/conditions).

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
    *   **Custom Data:** You can set the item's name, lore, count, enchantment glint, and even custom NBT data. You can learn more about using NBT with the [NBT Data Placeholder](https://docs.fancymenu.net/en/nbt-data-placeholder) documentation.
    *   **Tooltip Display:** Can be configured to show the item's standard tooltip on hover.

## Image
Displays a static image from a local file, a web URL, or a Minecraft resource location.

*   **Use Cases:**
    *   Adding a server logo or modpack brand.
    *   Creating decorative borders or UI frames.
    *   Using images as part of a more complex UI design.
*   **Key Features:**
    *   **Nine-Slicing:** Allows the image to be used as a scalable border or panel without distorting the corners. Learn more at the [Nine-Slicing & Tiling](https://docs.fancymenu.net/en/nine-slicing-tiling) page.
    *   **Texture Repeating:** The image can be tiled to fill the element's area.
    *   **Tinting:** You can apply a color tint to the image.
    *   **Parallax Effect:** Can be configured to move slightly with the mouse for a 3D effect. See the [Parallax Effect](https://docs.fancymenu.net/en/parallax-effect) page for more.

## Text
A highly versatile element for displaying text. It can be used for anything from single-line labels to multi-page, scrollable documents.

*   **Use Cases:**
    *   Displaying server rules, patch notes, or welcome messages.
    *   Creating dynamic info panels using [placeholders](https://docs.fancymenu.net/en/placeholders), e.g., "Welcome, `{"placeholder":"playername"}`!".
    *   Adding labels and descriptions to your UI.
*   **Key Features:**
    *   **Content Sources:** Text can be entered directly, loaded from a local file, or fetched from a web URL.
    *   **Markdown Support:** Supports a wide range of Markdown for rich text formatting, including headers, lists, code blocks, and tables. The appearance of Markdown elements is fully customizable. See the [Text Formatting](https://docs.fancymenu.net/en/text-formatting) page for more info.
    *   **Scrolling:** Automatically becomes scrollable if the content is larger than the element's area. Scrollbars can be customized or disabled.
    *   **Styling:** Full control over text color, scale, alignment, shadow, and line spacing.

## Video
Plays a video file. This is perfect for cinematic intros or decorative looping backgrounds.

> This element requires the **[MCEF (Minecraft Chromium Embedded Framework)](https://www.curseforge.com/minecraft/mc-mods/mcef)** mod to be installed and working.
{.is-warning}

*   **Use Cases:**
    *   An animated modpack or server trailer.
    *   A looping, ambient video to add life to your menu.
    *   An in-game tutorial video.
*   **Key Features:**
    *   **Sources:** Supports both local video files and web URLs. See the [Videos (MP4)](https://docs.fancymenu.net/en/videos-mp4) page for details.
    *   **Playback Control:** Can be set to loop automatically. Its volume and sound channel are adjustable.
    *   **Interactive Control:** The video's playback (pause/play) and volume can be controlled via button actions.

## Slideshow
Displays a sequence of images. The configuration for the slideshow (images, timing, transitions) is done in a separate `.properties` file located in the `/config/fancymenu/assets/slideshows/` directory.

*   **Use Cases:**
    *   A rotating gallery of in-game screenshots.
    *   Showcasing key features of a modpack.
    *   A dynamic background that cycles through different scenes.
*   **Key Features:**
    *   Loads pre-configured slideshows. See the [Slideshows](https://docs.fancymenu.net/en/slideshows) documentation for setup instructions.
    *   Can be set to maintain the aspect ratio of the images.

## Rectangle Shape
A simple, solid-colored rectangle.

*   **Use Cases:**
    *   Creating a semi-transparent background behind text to improve readability.
    *   Designing simple UI panels and dividers.
    *   As a colored placeholder during layout design.
*   **Key Features:**
    *   Supports HEX RGBA colors, allowing for full control over color and transparency.

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
    *   **Dynamic Appearance:** Can be configured to automatically copy the current player's skin, cape, and name. For more on this, check out the [Player Heads](https://docs.fancymenu.net/en/player-heads) guide.
    *   **Custom Poses:** Offers fine-grained control over the rotation of the head, body, arms, and legs. The head and body can also be set to follow the mouse cursor.
    *   **Attributes:** Can be set to be a baby, crouching, or have a slim model.

## Browser
An element that renders a live web page inside the game.

> This element requires the **[MCEF (Minecraft Chromium Embedded Framework)](https://www.curseforge.com/minecraft/mc-mods/mcef)** mod to be installed and working.
{.is-warning}

*   **Use Cases:**
    *   Displaying a server's live Dynmap.
    *   Embedding a YouTube video player.
    *   Showing a wiki or documentation page directly in-game.
*   **Key Features:**
    *   **Interactivity:** Can be made fully interactable, allowing users to click links, scroll, and type.
    *   **Media Control:** Offers options to mute media, loop videos, and hide video controls on the loaded page.

## Element Animator
A powerful tool for creating complex, keyframe-based animations. It can animate the position, size, and anchor point of one or multiple other elements.

*   **Use Cases:**
    *   Creating a sophisticated intro animation where menu elements slide or fade into view.
    *   Making decorative elements pulsate, rotate, or move along a path.
    *   Animating a notification to pop up and then disappear.
*   **Key Features:**
    *   **Keyframe Editor:** A dedicated editor for adding, editing, and sequencing keyframes on a timeline.
    *   **Multi-Target:** A single Animator can control multiple "target" elements at once.
    *   **Control:** Animations can be set to loop. You can also choose to animate only position or size.
    *   **[Learn more about the Element Animator.](https://docs.fancymenu.net/en/element-animator)**

## Ticker
An invisible element that executes a list of actions at a regular interval (every "tick").

*   **Use Cases:**
    *   Periodically checking a server's online status and updating a text element.
    *   Creating a countdown timer that updates a text label.
    *   Running a script repeatedly to create custom behaviors.
*   **Key Features:**
    *   **Timing Control:** You can set the delay between ticks in milliseconds.
    *   **Tick Modes:** Can be set to tick continuously, only once per game session, or once every time the menu is loaded.
    *   **Asynchronous:** Can run its [actions](https://docs.fancymenu.net/en/action-scripts) in a separate thread to avoid impacting game performance, though some actions cannot be run this way.

## Audio
An invisible element that plays audio files. It can manage a playlist of tracks and offers various playback controls.

*   **Use Cases:**
    *   Adding custom background music to a menu.
    *   Creating a music player with buttons to control playback (next/previous track, volume).
    *   Playing ambient soundscapes.
*   **Key Features:**
    *   **Playlist:** Can manage multiple audio tracks.
    *   **Playback Modes:** Can play tracks in order or shuffle them (with support for track weighting to make some tracks more common than others).
    *   **Control:** Supports looping, volume adjustment, and can be assigned to a specific sound channel (e.g., Master, Music). For more info, see the [Menu Background Music](https://docs.fancymenu.net/en/menu-background-music) page.

## Music Controller
An invisible element used to control Minecraft's default music playback within a specific menu.

*   **Use Cases:**
    *   Disabling the default menu music on a screen where you want to play your own custom music via an **Audio** element.
    *   Stopping in-world music from continuing to play when a menu is opened in-game.
*   **Key Features:**
    *   Separate toggles to control vanilla "Menu Music" and "World Music."

## Progress Bar
A customizable bar that visually represents a numerical value.

*   **Use Cases:**
    *   A loading bar that tracks world loading progress using `{"placeholder":"world_load_progress"}`.
    *   Visual health, hunger, or experience bars for an in-game HUD.
    *   A volume indicator that is controlled by a **Slider** element.
*   **Key Features:**
    *   **Dynamic Value:** The progress value (0-100 or 0.0-1.0) is set via a text field that supports [placeholders](https://docs.fancymenu.net/en/placeholders).
    *   **Appearance:** The bar's direction (up, down, left, right), colors, and textures are all customizable.
    *   **Animation:** Features a smooth filling animation to make progress changes look less jarring.

## Dragger
An invisible element that the user can click and drag to move around. Other elements can be anchored to it to create movable widgets.

*   **Use Cases:**
    *   Creating a draggable clock or information panel.
    *   Allowing users to customize the position of UI elements to their preference.
*   **Key Features:**
    *   **Persistent Position:** The dragged offset is saved, so the element stays where the user left it, even after restarting the game.
    *   **Anchor Point:** Acts as a movable anchor for other elements, which is a key part of [Positioning Elements](https://docs.fancymenu.net/en/positioning-elements).

## Cursor
An invisible element that replaces the default system cursor with a custom image when a layout is active.

*   **Use Cases:**
    *   Creating a fully themed UI that matches your modpack's aesthetic.
*   **Key Features:**
    *   **Custom Texture:** Use any image for your cursor.
    *   **Hotspot:** You can define the exact pixel on the image that serves as the "click point". See the [Custom Cursor](https://docs.fancymenu.net/en/custom-cursor) guide for more.