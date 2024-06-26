---
title: Positioning Elements
description: How to correctly use anchor points.
published: true
date: 2024-06-26T09:22:25.614Z
tags: 
editor: markdown
dateCreated: 2024-04-20T09:49:13.361Z
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

Elements can also serve as anchor points for other elements. This feature is particularly useful for integrating custom elements seamlessly into Vanilla menu designs without needing to adjust every Vanilla element.

To anchor an element to another, simply drag it towards the desired element. When the element you are dragging hovers over another, its anchor point gets changed to the hovered one, just like when hovering an actual anchor point.

This allows the element to align and move together with its parent element.

## More Ways to Improve Element Positioning

If **all anchor points are correct**, but your elements still overlap each other when the window is too small, it's possible that your layout is simply too full for Minecraft's normal GUI scaling logic.

### Forced GUI Scale

One way to improve the layout element positioning is to force a GUI scale to the menu by **right-clicking the editor background** and then clicking on **GUI Scale**. This will make the menu always have the same GUI scale, no matter what scale is set in Minecraft's options.

### Auto-Scaling

The last option to fix overlapping is to use **auto-scaling**.
This setting will automatically scale the menu based on the window size to try preserve element positions as good as possible when resizing the window. To enable auto-scaling, **right-click the editor background** and then click on **Auto-Scaling**.

> **Auto-scaling** can make **text** rendered by Minecraft **look bad**. This is not a bug and is just how Minecraft text rendering works. In case of buttons, a good workaround for this is to make button labels part of the button background texture and set a blank normal button label.
{.is-warning}
