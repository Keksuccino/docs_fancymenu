---
title: Rotating and Tilting Elements
description: Rotate and tilt elements with their grabbers in the layout editor, with exact values or with placeholders.
---

# Rotating and Tilting Elements

Most elements can be rotated and tilted. Both happen around the center of the element, and it keeps its place and size.

- **Rotation** turns the element, like the hand of a clock.
- **Vertical Tilt** tips it back, and **Horizontal Tilt** turns it to the side. Tilted elements show without perspective, so they only get lower or narrower. With both tilts, they also get slanted.

<img width="800" alt="Four Text elements on a menu background: one rotated by 15 degrees, one with a Vertical Tilt of 45 degrees that is lower, one with a Horizontal Tilt of 45 degrees that is narrower, and one with both tilts that is slanted. Light boxes behind them show where they would be without rotation and tilt." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_axes.png?raw=true">

# In the Layout Editor

<img width="800" alt="In the layout editor, a Season 3 sticker gets rotated with the grabber on the circle around it, then a Patch Notes panel gets tilted with the grabbers on the lines right of it and below it" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_editor.gif?raw=true">

Select an element in the [layout editor](/layout-editor) and drag its grabbers:

- The grabber on the circle around the element rotates it.
- The grabber on the line right of it sets its **Vertical Tilt**, the one on the line below it its **Horizontal Tilt**. The middle of a line is no tilt.

While you drag:

- Hold `Shift` to snap to steps: 45 degrees for rotation, 15 degrees for tilt.
- Close to 0, the grabbers snap to 0, so you can easily straighten an element again.
- The top left of the element shows its rotation and tilt.

Good to know:

- The selection frame stays straight. Click inside it to select or move the element.
- The grabbers only show while one element is selected.
- An element without a circle or lines can't be rotated or tilted. See [Elements Without Rotation or Tilt](#elements-without-rotation-or-tilt).
- **menu bar -> Window -> Element Rotation Controls** and **Element Tilt Controls** hide the grabbers of all elements.

# Exact Values

Right-click the element for these settings. Each one has **Set Via Number Picker**, **Set As Plain Text** and **Reset to Default**.

| Setting | What it does |
|---|---|
| **Rotation** | The degrees it turns clockwise, like `90` for a quarter turn. Negative values turn it counter-clockwise. |
| **Vertical Tilt** | How far it tips back, from `-60` to `60` degrees. |
| **Horizontal Tilt** | How far it turns to the side, from `-60` to `60` degrees. |

One tilt alone looks the same with a positive and a negative value. With both tilts, their signs decide which way the element slants.

## With Placeholders

To rotate or tilt an element by a [variable](/variables) or another [placeholder](/placeholders):

1. Right-click the element and turn on **Advanced Rotation Mode**, **Advanced Vertical Tilt Mode** or **Advanced Horizontal Tilt Mode**.
2. Click **Rotation**, **Vertical Tilt** or **Horizontal Tilt**, then **Set As Plain Text**, and enter the placeholder.

The advanced modes keep their own value and hide the grabber, so dragging can't replace your placeholder. When you turn one off, the element gets its old value back.

A logo that spins once every 3.6 seconds, with this **Rotation** in **Advanced Rotation Mode**. Divide by more than `10` to make it slower:

```
{"placeholder":"calc","values":{"expression":"{"placeholder":"unix_time"} / 10 % 360"}}
```

A needle that points where the variable `needle_angle` says, which buttons or a [Slider](/elements#slider) can set:

```
{"placeholder":"getvariable","values":{"name":"needle_angle"}}
```

# Clicks and the Mouse

<img width="800" alt="The pointer on a rotated Join Server button: where the corners of the straight button would be, nothing happens, and the ends of the button as it shows light it up" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_hover.gif?raw=true">

Buttons, sliders, and the links and scroll bars of Text elements react to the mouse where they show, also when they're rotated or tilted. So do the requirements [**Is Element Hovered**](/conditions#is-element-hovered), [**Is Any Element Hovered**](/conditions#is-any-element-hovered) and [**Is Any Button Hovered**](/conditions#is-any-button-hovered).

> [!NOTE]
> Checkboxes, Text Input Fields, Draggers and Browsers still react in the box they would have without rotation and tilt. Keep them straight.

# Elements Without Rotation or Tilt

- No rotation and no tilt: [Scrollable Areas](/scrollable-areas), [GLSL Shaders](/elements#glsl-shader), [Block/Item JSON Models](/elements#blockitem-json-model), [Player Entities](/player-entities) and [vanilla elements](/vanilla-elements), like the buttons of the screen itself.
- Rotation, but no tilt: [Tooltips](/elements#tooltip) and [Items](/elements#item).

Elements in a Scrollable Area can be rotated and tilted, only the area itself can't.

[Splash Text](/splash-text) elements also have their own **Rotation** further down in their right-click menu, for their typical slant. It works together with the rotation on this page.
