---
title: Positioning Elements
description: How to correctly use anchor points.
published: true
date: 2025-08-27T19:21:54.814Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:42.273Z
---

# Positioning Elements in FancyMenu

In FancyMenu, each element's position is determined by **anchor points**. These points are needed for calculating where an element should appear on the screen, ensuring elements don't overlap, stray off-screen, or move incorrectly when the window is resized.

## Understanding Anchor Points

Anchor points serve as the origin from which an element's position is calculated. By default, elements you add to layouts are linked to the **"Center of Screen"** anchor point. This anchor is the exact middle of the screen, irrespective of the window size.

For example, if an element is 2 centimeters from the center of the screen while being linked to the **"Center of Screen"** anchor, it will maintain this distance regardless of any changes in window size.

## Interacting with Anchor Points

When you drag an element in the editor, the anchor point to which it is connected is highlighted. By default, this action also displays all other available anchor points. You can change an element's anchor by dragging it over another anchor point and wait until the loading bar is filled.

![Illustration of anchor points](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Anchoring Elements to Other Elements

An element can use another element as its anchor. It then moves along with that element and keeps its distance to the other element's top-left corner. That's handy for panels made of several elements, for a label next to a vanilla button, and for [Draggers](/dragger).

There are two ways to do it. Both keep the element where it is.

### By Dragging

1. Drag the element and hold the pointer over the other element.
2. Wait until the bar is full, then let go.

If the pointer is already over the other element when you start dragging, move it off the other element once and back. Elements that are under the pointer from the start don't count.

It needs **Anchor Area Hovering** and **Anchor Element Hovering** in the **Window** menu, both on by default. The first turns anchoring by holding on and off, the second adds other elements to the anchor points. **Anchor Area/Element Hover Charging Time (Seconds)** in the same menu sets how long you have to hold, 2 seconds by default.

### By ID

1. Right-click the other element and click **Copy Element ID**.
2. Right-click the element and click **Anchor Point -> Other Element**.
3. Paste the ID into **Element ID** and click **Done**.

With several elements selected, step 2 and 3 anchor all of them at once. See [Element Identifiers](/element-identifiers) for more about IDs.

## Example for How to Anchor Elements

The following screenshot shows how you should choose anchors for elements.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

All elements that should stay in the middle of the screen (buttons and player entity) are anchored to the **Center of Screen** anchor point.

The buttons in the top-left corner are anchored to the **Top-Left Corner** anchor, because they should stay in the top-left corner.

The Text element in the bottom-left corner is anchored to the **Bottom-Left Corner** anchor point, because it should stay in the bottom-left corner.

The Image element in the bottom-right corner is anchored to the **Bottom-Right Corner** anchor point, because it should stay in the bottom-right corner.

## Moving Elements Out-Of-Screen

By default it is not possible to move elements out of screen, which is like a failsafe for when a layout gets loaded in a super small or weird window size, so elements are still visible and can be interacted with.

They will always stay on screen and keep a small gap between them and the screen's edges.

You can **disable** this for individual elements by **right-clicking** them and then disabling **Stay on Screen**.

> [!WARNING]
> Disabling this can sometimes cause the element to vanish, because its actual/real position was out-of-screen, but the feature made it stay visible. If that happens to you, **undo** the last action (disabling **Stay on Screen**) via the undo shortcut or in the **menu bar -> Edit -> Undo**, then manually move the element to the middle of the screen and disable **Stay on Screen** again. Now it should stay visible even with the feature disabled.

## Centering Elements

As long as elements have a fixed size, centering them is as easy as anchoring them to a center-based anchor point.

If the element dynamically changes its size based on conditions or something else, it's a bit more tricky, but FancyMenu has a great feature for that! In that case, first anchor the element to a center-based anchor point and then right-click it. In the context menu, turn on **Sticky Anchor**. This feature changes how FancyMenu calculates the position of the element, which makes it so it always keeps the same distance to its anchor point, no matter if its size changes. For center-based anchors it will always keep the same distance to the anchor from the element's absolute center, which makes it always stay centered when using center-based anchors. (For left-based anchors, it will always keep the same distance to the anchor from the element's left side and for right-based anchors it keeps the same distance from the element's right side.)

## More Ways to Improve Element Positioning

If **all anchor points are correct**, but your elements still overlap each other when the window is too small, it's possible that your layout is simply too full for Minecraft's normal GUI scaling logic.

### Forced GUI Scale

One way to improve the layout element positioning is to force a GUI scale to the menu by **right-clicking the editor background** and selecting **Force GUI Scale**. This will make the menu always have the same GUI scale, no matter what scale is set in Minecraft's options.

### Auto-Scaling

The last option to fix overlapping is to use **auto-scaling**.
This setting will automatically scale the menu based on the window size to try preserve element positions as good as possible when resizing the window. To enable auto-scaling, **right-click the editor background** and then click on **Auto-Scaling**.

> [!WARNING]
> **Auto-scaling** can make **text** rendered by Minecraft **look bad**. This is not a bug and is just how Minecraft text rendering works. In case of buttons, a good workaround for this is to make button labels part of the button background texture and set a blank normal button label.
