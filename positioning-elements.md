---
title: Positioning Elements
description: How to correctly use anchor points.
published: true
date: 2024-04-20T09:49:13.361Z
tags: 
editor: markdown
dateCreated: 2024-04-20T09:49:13.361Z
---

# Positioning Elements

Every element in FancyMenu is connected to an **anchor point**.

Anchor points are necessary for calculating an element's position and if used correctly, they prevent elements from overlapping each other, going out-of-screen or move to the wrong place when resizing the window.

They are the origin point from where the element's position is getting calculated.

By default, elements are connected to the **"Center of Screen"** anchor point, which is basically just the exact center of the screen, no matter the window size.
So lets say an element is 2 centimetres away from the center of the screen while being connected to the **"Center of Screen"** anchor. In that case, the element will **always** be 2 centimetres away from the screen's center, no matter the window size.

You can see the anchor point an element is connected to when dragging it. This will (by default) also show all other anchor points. You can hover an anchor point while dragging an element to change the element's anchor to the hovered anchor point.

![anchor_points](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

# Move Elements with Vanilla Elements

**Elements itself can also work as an anchor point for other elements!** Just hover an element while dragging another and the dragged element's anchor point will get changed to the hovered element.

This makes it possible to move custom elements with Vanilla elements, which can help integrating custom elements into Vanilla layouts without moving all Vanilla elements!