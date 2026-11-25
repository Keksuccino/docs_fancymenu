---
title: Parallax Effect
description: Let backgrounds and elements move a bit with the mouse, so your menus get depth.
---

# Parallax Effect

The Parallax Effect moves a menu background or an element a little when the mouse moves. Let far layers move less and near ones more, and your menu gets depth.

<img width="640" alt="A title screen with a landscape at dusk in four layers: while the mouse moves around, the foreground tree moves the most, the hills less and the mountains and the sky only a little" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_scene.gif?raw=true">

It works for [elements](/elements) and for **Image** and **Video** [menu backgrounds](/menu-backgrounds).

# Elements

<img width="640" alt="In the layout editor, right-clicking the foreground layer of a title screen, setting Parallax Effect to Enabled and Parallax Intensity (X) to 1.0, then saving and closing the editor. On the title screen, only the foreground layer moves while the mouse goes left and right" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_element_settings.gif?raw=true">

1. Right-click the element in the layout editor and scroll down to **Parallax Effect**.
2. Click **Parallax Effect** to set it to **Enabled**.
3. Click **Parallax Intensity (X)** and **Parallax Intensity (Y)** to set how far it moves.
4. Save the layout and close the editor. Elements only move outside of the editor.

| Setting | What it does |
|---|---|
| **Parallax Effect** | Turns the effect on. |
| **Parallax Intensity (X)** | How far the element moves left and right, from `0.0` (not at all) to `1.0`. New elements have `0.5`. |
| **Parallax Intensity (Y)** | The same for up and down. |
| **Invert Parallax Movement** | Moves the element in the same direction as the mouse. Without it, it moves the opposite way. |

At `1.0`, an element moves up to 5% of the screen width to the side and 5% of the screen height up or down, when the mouse is at the edge of the screen. In the middle of the screen, elements are where you put them.

- Elements that are [anchored](/positioning-elements) to an element with the effect move along with it, and their own effect adds to that.
- **Stay on Screen** doesn't keep elements with the effect on the screen, so they can move past its edges.
- Stretched elements don't move in the direction they're stretched in.
- Buttons stay clickable where they show.
- [Scrollable Areas](/scrollable-areas), the elements in them and Tooltip elements have no Parallax Effect.

# Menu Backgrounds

<img width="800" alt="The right-click menu of the layout editor with Menu Backgrounds and Image open, showing Parallax Effect, Set Parallax Effect Intensity (X), Set Parallax Effect Intensity (Y) and Invert Parallax Movement" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_background_settings.png?raw=true">

1. Right-click the editor background and open **Menu Backgrounds -> Image** (or **Video**).
2. Click **Parallax Effect** to set it to **Enabled**.
3. Set **Set Parallax Effect Intensity (X)** and **Set Parallax Effect Intensity (Y)**.

Backgrounds react much stronger than elements. The background gets bigger by its intensity, so its edges never show: at `1.0`, it's twice the size of the screen and moves up to half a screen to the side. Keep the values low: new backgrounds have `0.02`, and `0.01` to `0.1` works well.

- **Invert Parallax Movement** moves the background in the same direction as the mouse.
- **Slide Wide Images From Left To Right** and **Parallax Effect** can't be on at the same time.
- **Repeat Texture** and **Preserve Background Aspect Ratio** work together with it.
- Backgrounds move in the layout editor too.

# Making a Scene with Depth

The scene at the top of this page is a sky and three layers on the title screen:

1. Draw your scene in layers, from far to near, like sky, mountains, hills and a foreground. Every layer except the sky is a PNG image with transparent parts.
2. Set the sky as **Image** menu background and turn on its Parallax Effect.
3. Add every other layer as an [Image element](/elements#image), from far to near, so the nearest one is on top.
4. Make the layers a bit bigger than the screen, so their edges never show when they move. A layer with `1.0` needs 5% of the screen width more on the left and on the right, and 5% of the screen height more on the top and on the bottom. Turn off **Stay on Screen** to place them past the screen edges.
5. Turn on the Parallax Effect of every layer: low intensities for far layers and high ones for near layers.
6. Right-click the editor background and set **Custom Elements Behind Vanilla** to **Enabled**, so the layers stay behind the buttons and the logo.

These are the intensities of the scene:

| Layer | Intensity (X) | Intensity (Y) |
|---|---|---|
| Sky (menu background) | `0.02` | `0.01` |
| Mountains | `0.35` | `0.2` |
| Hills | `0.6` | `0.3` |
| Foreground | `1.0` | `0.5` |

> [!TIP]
> Give the Y intensity about half the X intensity. The ground of a landscape then doesn't bounce up and down so much.

# Good to Know

- Everything moves in whole pixels of the GUI, so low intensities move in small steps.
- The intensity settings accept [placeholders](/placeholders): point at one and click **Set As Plain Text** in the small menu next to it. With a [variable](/variables), you can let players turn the effect down in your own settings menu.
