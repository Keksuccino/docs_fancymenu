---
title: Global Customizations
description: Change the buttons, sliders, menu backgrounds, music and window of every screen at once, without layouts.
---

# Global Customizations

Global Customizations change every screen at once: buttons, sliders, menu backgrounds, music, the game window and more. They need no layout, and they also work on screens whose customization is turned off.

Open them through **menu bar -> Customization -> Global Customizations**, on any screen outside the layout editor. Changes apply right away and get saved on their own.

<img width="800" alt="The Title screen, Options and Music & Sounds without any layout, all with the same wooden buttons, brass slider handles, labels that turn gold on hover and a night background" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/global_customizations_tour.gif?raw=true">

> [!TIP]
> To change only some screens, use [layouts](/layout-editor). To give the buttons of certain layouts their own look, use [Button and Slider Templates](/button-slider-templates).

# Buttons and Sliders

These settings change all buttons and sliders of all screens, also the ones of other mods.

- Buttons and sliders that got their own textures or label settings from a [layout](/layout-editor) or a [template](/button-slider-templates) keep them.
- Buttons that are only an image, like the recipe book button, keep their look.

## Button Textures

**Custom Button Textures** has one texture for each state of a button:

- **Normal**
- **Hover**: while the mouse is on the button, or it's selected with the keyboard.
- **Inactive**: while the button can't be clicked.

Set all three. A state without a texture shows Minecraft's own button.

More settings in the same menu:

- **Transparent Background** hides the background of all buttons, so only their labels show. It wins over the textures.
- **Nine-Slice Button Backgrounds** keeps the edges of the textures sharp at every button size, with the four border sizes below it. See [Nine-Slicing and Tiling](/nine-slicing-and-tiling).

> [!TIP]
> Without nine-slicing, textures get stretched to the size of each button. Minecraft's buttons are 20 pixels high and mostly 200 or 150 pixels wide. With nine-slicing, one small texture fits all of them.

## Slider Textures

**Custom Slider Textures** has two parts:

- **Slider Background Texture**: the bar of the slider. Set it with **Set Texture**. **Transparent Background** and **Nine-Slice Slider Background** work like the ones of buttons.
- **Slider Handle Textures**: the part you drag, with **Normal**, **Hover** and **Inactive** textures and **Nine-Slice Slider Handle**.

The handle of Minecraft's sliders is 8 pixels wide and as high as the slider, mostly 20 pixels. Without nine-slicing, handle textures get stretched to that size.

## Labels

**Button Labels** and **Slider Labels** have the same settings:

| Setting | What it does |
|---|---|
| **Underline Label On Hover** | Underlines the label while the mouse is on it. |
| **Label Base Color** | The color of the label. Set it with the color picker or as a HEX code, like `#FFF1D6`. |
| **Label Hover Color** | The color while the mouse is on the label. |
| **Label Scale** | The size of the label. `1` is the normal size. |
| **Label Alignment** | **Left**, **Centered** or **Right**. |
| **Label Shadow** | The dark shadow behind the label. Turned off, no label has a shadow, not even ones from layouts. |

Labels with their own settings from a layout or template keep them. For **Label Scale** and **Label Alignment**, only labels at the normal size and **Centered** use the global setting.

## Click Sound

- **Custom Button Click Sound** replaces Minecraft's click sound of buttons and sliders. Buttons with their own click sound from a layout keep it.
- **Custom Button Click Sound Volume** goes from 0% to 100%. The volume slider of its sound channel in Minecraft's sound settings applies on top.
- **Custom Button Click Sound Channel** is the sound channel it plays on, like Music. By default, it's Master Volume, the channel of all sounds.

# Menu Backgrounds

**Custom Menu Background Texture** is an image behind all menus, except the Title screen:

- It's also behind the pause menu and the Options while you play, so it hides the world there. Inventories, signs and books stay see-through.
- **Preserve Background Texture Aspect Ratio** keeps the image's proportions. It still fills the whole screen, and the parts that don't fit get cut off. Turned off, the image gets stretched to the screen.

**Custom Menu Background Panorama** replaces Minecraft's panorama, on the Title screen and in all menus before you join a world:

- **Choose Panorama** picks one of your [panoramas](/panoramas).
- **Clear Panorama** brings back Minecraft's panorama.
- **Current Panorama** shows which one is set.

With both set, the texture covers the panorama, so the panorama only shows on the Title screen.

Screens whose layout has its own [menu background](/menu-backgrounds) show that one instead.

# Menu Music

- **Play Vanilla Menu Music** turns Minecraft's music in menus on and off.
- **Custom Menu Music Tracks** opens **Manage Menu Music Tracks**. **Add Track** adds a sound, **Remove Track** removes the selected one, **Clear Tracks** removes all of them, and **Done** saves the list.

The tracks play in random order in menus before you join a world, instead of Minecraft's menu music. More about them, and about music in single screens: [Menu Background Music](/background-music).

# Screens and Popups

| Setting | What it does |
|---|---|
| [**Game Intro**](/game-intro) | Plays an animation or video before the Title screen shows up. |
| **Singleplayer Screen World Icons** | The icons of worlds in the world list. Turned off, they're hidden. |
| **Multiplayer Screen Server Icons** | The icons of servers in the server list. Turned off, they're hidden. |
| [**Seamless World Loading**](/seamless-world-loading) | Takes a screenshot when you leave a world or server, and shows it as the loading background when you join it again. |
| **Achievement Toasts** | The popups in the top-right corner when you unlock an achievement, and their sounds. Turned off, they're hidden. Achievement messages in the chat stay, and the listener [On Achievement Unlocked](/listeners#on-achievement-unlocked) still works. |

# Window and Game Start

| Setting | What it does |
|---|---|
| [**Custom Window Icon**](/window-customization#custom-icon) | The icon of the game window. It needs a 16x16 and a 32x32 PNG icon and a macOS icon. |
| [**Custom Window Title**](/window-customization#custom-title) | Replaces Minecraft's window title. [Placeholders](/placeholders) work, and the title updates when they change. |
| **Default GUI Scale** | Sets Minecraft's GUI scale once, at the first start of the game instance, like `2` or `3`. `-1` turns it off. Made for modpacks. |
| **Force Fullscreen on Launch** | Switches the game to fullscreen at every start. |

FancyMenu remembers that it set the **Default GUI Scale** in `fancymenu_data/default_scale_set.fm`. Delete that file to make it set the scale again at the next start (see [Data Storage Locations](/data-storage-locations#instance-data)).

# Good to Know

- Global Customizations get saved in FancyMenu's `options.txt`, so they belong to the loaded [profile](/profiles) and ship with modpacks that include `config/fancymenu/`.
- Textures and sounds can be files of your instance, web links or files of resource packs. See [Resources](/resources).
- **menu bar -> Help -> Export for AI -> FancyMenu Settings** includes them, for questions to an [AI chat](/export-for-ai).
