---
title: Getting Started
description: Your first steps with FancyMenu. The menu bar, your first layout from start to finish, and where to go from there.
---

# Getting Started

FancyMenu lets you change every menu of Minecraft, like the title screen, the pause menu and the menus of other mods. Give them your own backgrounds, logos, buttons, texts, sounds and animations, move or hide what's already there, make buttons do new things, or build whole new menus. All of it happens in the game, without code.

<img width="800" alt="The title screen of a modpack called Wildwood, made with FancyMenu: a pixel art valley at dusk with a cabin, a lake and the setting sun, whose layers move with the mouse, a golden logo, wooden buttons that glow when hovered, and fireflies" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_hero.gif?raw=true">

This page shows you the basics, step by step, and turns the normal title screen into this one.

# The Menu Bar

The menu bar at the top of every menu is where all of FancyMenu's features are.

<img width="800" alt="The menu bar at the top of the title screen, with its Customization menu open" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_menu_bar.png?raw=true">

- **Customization**: the layouts of the menu you're in, and everything for your whole setup, like [Global Customizations](/global-customizations), [Custom GUIs](/custom-guis), [Variables](/variables), [Listeners](/listeners), [Schedulers](/schedulers), [Profiles](/profiles) and FancyMenu's settings.
- **Tools**: helpers like [Dummy Screen Instances](/dummy-screen-instances), the [AFMA Creator](/animations#fma-and-afma), **Browse Game Resources** and **Open FancyMenu Directory**, which opens the folder of your setup (see [Data Storage Locations](/data-storage-locations)).
- **Help**: these docs, the Discord server, **Report a Bug** and [Export for AI](/export-for-ai).
- The door icon at the right closes the menu you're in, for menus that have no way out.
- The double arrows at the far right fold the menu bar up to a small button, and back.

Players of your modpack don't need the menu bar. See [Modpacks](/modpacks#disabling-the-menu-bar-and-hotkeys) for how to turn it off.

## Menu Bar Shortcuts

These work in every menu, but not in the layout editor and not while Modpack Mode is on. On macOS, use `Cmd + Option` instead of `Ctrl + Alt`.

| Shortcut | What it does |
|---|---|
| `Ctrl + Alt + C` | Show or hide the menu bar. If it's suddenly gone, this brings it back. |
| `Ctrl + Alt + R` | Reload FancyMenu, like **menu bar -> Customization -> Reload FancyMenu** |
| `Ctrl + Alt + D` | Show or hide the **Debug Overlay**, which shows the [identifier](/screen-identifiers) of the menu and more |
| `Ctrl + Alt + L` | Open the [layout editor](/layout-editor) with the layout you edited last |

# Your First Layout

A layout holds your changes to a menu: its background, the elements you add, and what you change about the buttons and texts that are already there. A menu can have several layouts, and you can turn each of them on and off.

## Making a Layout

<img width="800" alt="Opening Customization in the menu bar of the title screen, turning on Current Screen Customization, opening Customization again and clicking Layouts, New, For Current Screen, which opens the layout editor" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_new_layout.gif?raw=true">

1. Open the menu you want to change, like the title screen.
2. Click **menu bar -> Customization -> Current Screen Customization**, so it shows **Enabled**. FancyMenu only changes menus where it's on.
3. Click **menu bar -> Customization -> Layouts -> New -> For Current Screen**.

The layout editor opens. It shows the menu like players see it, so you see every change right away. See [Layout Editor](/layout-editor) for everything about it, like moving, resizing and copying elements.

**For All Screens [Universal]** makes a [Universal Layout](/universal-layouts) instead, which shows in every menu.

## Setting a Background

Put your images into the `config/fancymenu/assets` folder of your game first. **menu bar -> Tools -> Open FancyMenu Directory** opens `config/fancymenu`.

<img width="800" alt="Right-clicking the editor background, opening Menu Backgrounds, Image, turning on Show Background, then Choose Image, switching Source Type to Local and picking background.png from the wildwood folder, and the valley shows behind the buttons" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_background.gif?raw=true">

1. Right-click the background of the editor and open **Menu Backgrounds -> Image**.
2. Click **Show Background**, so it shows **Enabled**.
3. Click **Choose Image**, set **Source Type** to **Local** and click **Choose Local Resource File**.
4. Click your image and click **OK**. A double-click opens folders.

Backgrounds can also be panoramas, slideshows, videos, colors and more. See [Menu Backgrounds](/menu-backgrounds).

## Adding a Logo

<img width="800" alt="Deleting the Minecraft logo and the splash text, adding an Image element through Element, New, Image, and picking logo.png as its Image Source, which shows the logo squished into a square" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_add.gif?raw=true">

1. Click the Minecraft logo and press `Delete`. Do the same with the yellow splash text.
2. In the menu bar of the editor, click **Element -> New -> Image**.
3. Right-click the new element, click **Image Source** and pick your logo, like the background.

Deleted vanilla elements only get hidden. **Element -> Deleted Vanilla Elements** brings them back.

<img width="800" alt="Clicking Restore Aspect Ratio in the right-click menu of the logo, which gets its real width, closing the menu with Esc and dragging the Wildwood logo above the buttons" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_place.gif?raw=true">

4. Right-click it again and click **Restore Aspect Ratio**, so it isn't squished. `Esc` closes the menu.
5. Drag it to its place.

There's a lot more you can add, like buttons, texts, videos and players. See [Elements](/elements).

## Changing the Buttons

Right-click a button for its settings: its label, its textures, its sounds, what it does when clicked ([Action Scripts](/action-scripts)) and when it shows ([Element Visibility](/element-visibility)). Drag it to move it and drag its edges to resize it. See [Vanilla/Mod Elements](/vanilla-elements).

## Saving

<img width="800" alt="Pressing Ctrl + S, clicking Save in the Save File window, closing the editor with the X and the finished title screen with the valley and the Wildwood logo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_save.gif?raw=true">

1. Press `Ctrl + S` (`Cmd + S` on macOS), or click **Layout -> Save**.
2. The first time, FancyMenu asks for a file name. Keep it or type a new one, and click **Save**.
3. Close the editor with the X at the right of its menu bar.

The menu shows your layout right away. To change it later, hover it in **menu bar -> Customization -> Layouts** and click **Edit Layout**, or press `Ctrl + Alt + L`.

# How the Example Is Made

The title screen at the top of this page goes a few steps further:

- The sky, the hills and the trees are three images that move with the mouse, the trees the most. See [Parallax Effect](/parallax).
- The hills and the trees are Image elements as big as the screen. So they stay behind the buttons and texts, the right-click menu of the editor background has **Custom Elements Behind Vanilla** turned on.
- The buttons have wooden textures in their **Button Textures -> Set -> Normal Background**, and glowing ones in **Hover Background**. **Button Textures -> Nine-Slice Custom Background** keeps their corners sharp on every width. See [Nine-Slicing](/nine-slicing-and-tiling).
- The fireflies are a [Decoration Overlay](/decoration-overlays#fireflies).

# Where to Go Next

**Make it look great**

- [Elements](/elements): everything you can add to menus.
- [Positioning Elements](/positioning-elements): keep elements in place on every window size.
- [Menu Backgrounds](/menu-backgrounds), [Animations](/animations), [Videos](/video), [Decoration Overlays](/decoration-overlays) and [Background Music](/background-music).

**Make it do things**

- [Action Scripts](/action-scripts): what buttons and other elements do.
- [Element Visibility](/element-visibility) and [Requirements](/conditions): show things only sometimes.
- [Placeholders](/placeholders): live info in texts, like the player's name.
- [Variables](/variables), [Listeners](/listeners) and [Schedulers](/schedulers): remember things, react to the game and run things on a timer.

**Build more**

- [Custom GUIs](/custom-guis): whole new menus.
- [Universal Layouts](/universal-layouts): changes for every menu.
- [Global Customizations](/global-customizations): tweaks for the whole game, like the window title.
- [Loading Screen](/loading-screen) and [Game Intro](/game-intro).

**Share it**

- [Modpacks](/modpacks): put your setup into a modpack.
- [Profiles](/profiles): switch between setups, and export them.

# Getting Help

- The [FAQ](/faq) answers the most common questions.
- **menu bar -> Help -> Join the Discord** brings you to the FancyMenu Discord server.
- [Export for AI](/export-for-ai) turns your setup into text for AI chats, like the support bot on the Discord server.
- **menu bar -> Help -> Report a Bug** if something doesn't work like it should.

# For Developers

To make an add-on for FancyMenu or use it in your mod, see the [developer documentation](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki).
