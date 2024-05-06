---
title: Positioning Elements
description: How to correctly use anchor points.
published: true
date: 2024-05-06T06:01:46.678Z
tags: 
editor: markdown
dateCreated: 2024-04-20T09:49:13.361Z
---

# Positioning Elements in FancyMenu

In FancyMenu, each element's position is determined by **anchor points**. These points are critical for accurately calculating where an element should appear on the screen, ensuring elements don't overlap, stray off-screen, or move incorrectly when the window is resized.

## Understanding Anchor Points

Anchor points serve as the origin from which an element's position is calculated. By default, elements you add to layouts are linked to the **"Center of Screen"** anchor point. This anchor is the exact middle of the screen, irrespective of the window size.

For example, if an element is 2 centimeters from the center of the screen while being linked to the **"Center of Screen"** anchor, it will maintain this distance regardless of any changes in window size.

## Interacting with Anchor Points

When you drag an element in the editor, the anchor point to which it is connected is highlighted. By default, this action also displays all other available anchor points. You can change an element's anchor by dragging it over another anchor point and wait until the loading bar is filled.

![Illustration of anchor points](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Anchoring Elements to Other Elements

Elements can also serve as anchor points for other elements. This feature is particularly useful for integrating custom elements seamlessly into Vanilla menu designs without needing to adjust every Vanilla element.

To anchor an element to another, simply drag it towards the desired component. When the element you are dragging hovers over another, its anchor point gets changed to the hovered one, just like when hovering an actual anchor point.

This allows custom elements to align and move together with Vanilla elements, ensuring a seamless integration within the existing Vanilla menu design.
