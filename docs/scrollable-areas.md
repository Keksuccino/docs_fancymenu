---
title: Scrollable Areas
description: How to put elements into a Scrollable Area, arrange them and change how the area scrolls.
---
# Scrollable Areas

A **Scrollable Area** holds other elements and lets players scroll through them. It's great for long lists of buttons, world or server pickers, item showcases, news panels and everything else that doesn't fit on one screen.

Everything in the area scrolls with it and gets cut off at its edges.

<img width="800" alt="Putting buttons into a Scrollable Area and stacking them" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_showcase.gif?raw=true">

> [!NOTE]
> Only elements you added to the layout can go into an area. [Vanilla elements](./vanilla-elements) can't, because they belong to the menu itself.

# Adding a Scrollable Area

1. Open a layout in the layout editor.
2. Right-click the editor background and select **New Element -> Scrollable Area**.
3. Drag elements into the area.

# Putting Elements In and Out

- Drag an element onto the area to put it in. The area lights up when it takes the element. An element only goes in if a part of it is inside the area.
- To drag several selected elements at once, hold `Ctrl` (`Cmd` on macOS) when you start dragging.
- While you drag an element close to an edge of the area, the area scrolls, so you can reach every part of it. You can also scroll it with the mouse wheel in the editor.
- To take an element out, drag it out of the area, or right-click it and select **Move Out of Scrollable Area**. It stays where it is on the screen.
- Areas can go into other areas too.

## Layers

In the [Layers widget](./layers-and-groups), the elements of an area show up below it. Drag layers there to put them into or out of an area, or to change their order. The collapse button of an area's layer hides its elements in the list.

## Copying and Deleting

- Copying an area also copies everything in it.
- Deleting an area that still holds elements asks what to do with them: **Delete Elements** deletes them too, **Keep Elements** keeps them where they are on the screen.

# Arranging Elements

Right-click the area and open **Arrangement**. **Mode** sets how the area places its elements:

- **Anchors**: You place the elements yourself, like in the rest of the layout. New areas use this mode.
- **Stack**: The elements line up one after another.
- **Grid**: The elements line up in cells of the same size.
- **Flow**: The elements line up next to each other and start a new line when one is full.

<img width="800" alt="Scrollable Areas in Stack, Grid and Flow mode" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

## Anchors Mode

Elements in an area have anchors of their own, which refer to the content of the area instead of the screen. For example, the **Top-Left Corner** anchor is the top-left corner of the content, and the bottom anchors stick to the end of the content. See [Positioning Elements](./positioning-elements) for how anchors work.

- **Stretch Horizontally** and **Stretch Vertically** make an element as wide or as high as the content.
- Elements can only be anchored to other elements in the same area. When you move an element into or out of an area, elements that were anchored across the area's edge get the **Top-Left Corner** anchor and stay where they are.

### Content Size

In Anchors mode, you decide how big the content is, and so how far the area scrolls.

Select the area and drag the handle at the end of its content. Drag it past the edge of the area to keep going, and the area scrolls along.

<img width="698" alt="The content handle of a selected Scrollable Area" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_content_handle.png?raw=true">

You can also right-click the area and open **Content Size**:

- **Content Width** and **Content Height** set the size by number. They support [placeholders](./placeholders). With a placeholder, the handle can't be dragged.
- **Fit to Content** makes the content end right where the last element in it ends. Elements anchored to the middle or the end of the content move with it, so they don't count.

The content is never smaller than the area, and it only gets bigger in the directions the area scrolls in.

## Stack, Grid and Flow

- The area places the elements for you, and the content grows with them on its own.
- Drag an element to put it in another order. A line shows where it goes.
- Switching from Anchors to one of these modes keeps the elements in the order they had on the screen. Switching back to Anchors keeps every element where it was.
- Elements that are hidden by their [requirements](./conditions) leave no gap.
- Stretching doesn't work in these modes.
- These modes only scroll in one direction. An area set to **Both** scrolls vertically.

Open **Arrangement** to fine-tune them:

| Setting | What it does |
|---|---|
| **Alignment** | Where the elements sit across the direction they line up in: **Start**, **Center**, **End** or **Fill**. With **Fill**, they get as wide as the room they have (or as high, in areas that scroll sideways). Flow has no **Fill**. |
| **Spacing** | The space between the elements. |
| **Padding** | The space between the elements and the edges of the content. |
| **Elements per Line** | Grid only. How many elements go into one line. |
| **Fit as Many as Possible** | Grid only. Puts as many elements into a line as there's room for, instead of a fixed number. **Minimum Cell Size** decides how many that are. |

# Scrolling

Players scroll the area with the mouse wheel. Hold `Shift` to scroll sideways.

- **Scroll Direction** sets if the area scrolls **Vertical**, **Horizontal** or **Both**. Where it doesn't scroll, the content is exactly as big as the area.
- Text elements in an area scroll first. Once they reach their end, the area scrolls on.
- When players jump between buttons with `Tab`, the area scrolls to the selected one.

The **Scrolling**, **Auto-Scroll** and **Scroll Bars** menus have the same settings as for Text elements. See [Text in Menus](./text-in-menus#scrolling-settings) for all of them. The differences:

- **Snap** can rest the content **To Elements**, so an element always sits at the start of the area, or **To Pages**.
- Buttons and everything else in the area keep working with **Drag to Scroll** on.
- The scroll grabbers are pixel handles, unless you give them your own **Scroll Grabber Textures** or **Scroll Grabber Color [HEX]**.

# Background

Areas draw a panel behind their content. Open **Background** to change it. It works like the [background of Text elements](./text-in-menus#background): turn it off with **Show Background**, use your own texture with [nine-slicing](./nine-slicing-and-tiling) or tiling, and change how far it reaches with **Padding**.

# Scrolling With Actions

You can also control and watch areas from other parts of FancyMenu:

- The **Scroll an Element** [action](./action-scripts) scrolls an area to its start, its end, a position or one of the elements in it.
- The **Element Scroll Position**, **Element Scroll Percent** and **Element Scroll Content Size** [placeholders](./placeholders) tell you how far the area is scrolled and how big its content is.
- The **Is Element Scrolled to End** [requirement](./conditions) checks if the area got scrolled to its end.
- The **On Element Scrolled**, **On Element Scrolled to Start** and **On Element Scrolled to End** [listeners](./listeners) run actions while the area scrolls.

All of these need the [element identifier](./element-identifiers) of the area. For example, this shows how far an area is scrolled, from 0 to 100:

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"3f2a9c1e-7b4d-4e8a-9c2f-1d5e6a7b8c9d-1763950000000","axis":"vertical"}}
```

# Good to Know

- Hiding an area hides everything in it, and the opacity of an area also applies to everything in it.
- Areas can't be rotated or tilted, and parallax doesn't work for areas and the elements in them.
- Tooltip elements in an area get cut off at its edges, unless they follow the mouse.
