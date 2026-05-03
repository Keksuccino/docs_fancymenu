---
title: Splash Text
description: How to make custom splash texts in FancyMenu.
published: true
date: 2025-10-28T03:51:27.263Z
tags: 
editor: markdown
dateCreated: 2025-10-28T03:51:27.263Z
---

# Custom Splash Text Element

The Splash Text element in FancyMenu is a fully customizable upgrade of Minecraft’s bouncing title splashes. It keeps the familiar bouncing while giving you control over what appears, how it looks, and when it updates.

> Keep in mind you can't really customize the original Vanilla Splash Text element in the Title screen, so you should **delete** it and use a custom Splash Text element instead.
{.is-warning}

## Adding & Selecting the Element
- Open the layout editor and add the element called `Splash Text`.
- Left-click it once to select it and show the bounding box, then right-click to open its context menu. Every configuration option lives in that menu.

## Choosing Where Splash Text Comes From
- `Source Mode: Vanilla` keeps the classic random splashes that Minecraft ships with.
- `Source Mode: Direct Input` lets you enter your own text through `Input Splash Text`. This only supports a single splash text line, but the line can contain placeholders.
- `Source Mode: Text File` pulls a random line from a `.txt` file you pick with `Set Source Text File`. Each non-empty line can become the active splash.
- Switching modes resets the active text so you can safely experiment. If the text feels stuck, toggle another mode or click `Refresh On Screen Load: Enabled` to force a reroll each time the menu opens.

## Example Text File
When using the "Text File" source mode, save your splash list as plain text (UTF-8 without BOM). Each line is a possible splash:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Replace `your_placeholder_id_here` with the placeholder you want to resolve at runtime. FancyMenu picks a random non-empty line every time the splash refreshes.

## Making It Look the Way You Want
- Use `Set Scale` and `Set Rotation` to control the size and rotation angle.
- `Set Text Color` accepts a hex value (for example `#FFFF00`) to match your theme.
- `Shadow: Enabled` adds Minecraft’s drop shadow; toggle it off for flat text.
- `Bouncing: Enabled` keeps the familiar bobbing motion; disable for a static label.
- FancyMenu renders the splash as a full Minecraft component, so color codes and other text decorations all work as expected.

## Dynamic Text Features
- Placeholders are resolved before rendering, so you can reference player names, dates, or other supported values inside the splash text.
- Because the element accepts Minecraft’s serialized component JSON, you can paste advanced JSON snippets into Direct Input or your text file. The element automatically deserializes them and falls back to literal text if something goes wrong.

## Troubleshooting
- Empty text in Direct Input shows `< empty splash element >` while editing. Enter anything (even a space) to clear the warning.
- If a text file contains no valid lines, the element displays `ERROR: SPLASH FILE IS EMPTY`. Add at least one non-empty line and reopen the screen.
- Serialized JSON errors fall back to plain text. Stick to Mojang’s standard JSON structure or test snippets with the vanilla `/tellraw` command before pasting.
