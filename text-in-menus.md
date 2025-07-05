---
title: Text in Menus
description: How to add text content to menus.
published: true
date: 2025-07-05T19:44:08.696Z
tags: 
editor: markdown
dateCreated: 2025-07-05T19:40:17.459Z
---

# Text in Menus

FancyMenu allows you to add text content to menus/screens via the **Text** element.

This element is scrollable, has full Markdown support and line wrapping, which makes it very powerful for displaying even complex text content, but it's also great for simple one-liners.

## Customizing or Disabling Markdown

If you want to customize the colors for headlines or other things related to Markdown, just **right-click** the Text element and click on **Markdown**. In the sub context menu that opens, you will see lots of options for customizing the appearance and behaviour of the Markdown parser.

In case you don't want Markdown parsing at all, which can improve performance for long text content, you can disable Markdown completely in the **Markdown** menu when **right-clicking** the Text element.

## Disabling Line Wrapping

If you don't want line wrapping, you can disable it by **right-clicking** the Text element.

## Disabling Scrolling

Text elements are scrollable by default and if the element thinks the user needs to scroll for seeing all of its content, it will show its scroll bars, which are small, grey bars at the right and bottom sides of the Text element (vertical and horizontal scroll bars).

You can disable these bars by toggling off **Scrolling** in the menu that opens when **right-clicking** the element. This will disable scrolling in general, not just the bars. If you want the bars to be invisible instead, you can set custom scroll bar textures by right-clicking the element. Just set a fully transparent texture there.

## Minecraft's Raw Component Text Format (Serialized JSON Components)

The Text element does NOT have support for Minecraft's raw component format. This format is only supported by button and slider labels.