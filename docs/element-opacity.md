---
title: Element Opacity
description: How to control the opacity of elements.
published: true
date: 2025-09-03T17:05:25.530Z
tags: 
editor: markdown
dateCreated: 2025-08-04T19:13:04.533Z
---

# Element Opacity

Most elements in FancyMenu (with some exceptions) support setting their opacity via their right-click menu.

The opacity value of elements supports placeholders, which makes it possible to dynamically update their opacity based on the placeholder.

This makes it possible to create custom fading logic when used in combination with Ticker elements to update variable values and then apply it as opacity via placeholders.

To set the opacity of elements, **right-click the element -> Opacity -> Set**.

# Fading In/Out Elements

If you simply want to fade-in or -out elements, it's probably easier to just use the built-in fading feature of elements. You can enable fading in the right-click menu of elements.

This feature makes elements fade-in every time they load, be it the initial load when opening a menu or when the element's loading requirements make it load. They will fade-out whenever their loading requirements make it unload/invisible.

The fading feature supports setting a fading speed to control how fast and element should fade in or out.