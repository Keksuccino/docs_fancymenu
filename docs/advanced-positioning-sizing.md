---
title: Advanced Positioning & Sizing
description: How to use Advanced Positioning and Sizing of elements.
---
# Advanced Positioning & Sizing

Advanced positioning and sizing gives you direct control over element coordinates and dimensions.

> [!WARNING]
> For GUI-scale adaptation, try layout-wide **Auto-Scaling** first. Right-click the editor background, force a GUI scale, then enable **Auto-Scaling** in the same menu.


# Toggling Advanced Positioning/Sizing Mode

To enable advanced positioning or sizing for an element, **right-click** it and select **Advanced Positioning** or **Advanced Sizing**.
The element will automatically switch to the advanced mode when you set an advanced position or size value.

To **disable** it and switch back to normal positioning/sizing, **clear all positioning/sizing values**.

> [!WARNING]
> While an element is in Advanced Sizing/Positioning mode, resizing and/or moving the element could be disabled or restricted.

# Calculating Positions/Sizes

Advanced position and size values support [placeholders](./placeholders).

This allows you to combine the [**Calculator**](./placeholders#calculator-calc) placeholder with GUI placeholders such as [**Screen Width**](./placeholders#screen-width-guiwidth), [**GUI Scale**](./placeholders#gui-scale-guiscale), and [**Element Width**](./placeholders#element-width-elementwidth).

> [!NOTE]
> You can add placeholders by clicking on the **Placeholders** button at the top-right side of the text editor. If you don't see this button, the content you want to edit does **not support** placeholders.

To calculate something with the [**Calculator** placeholder](./placeholders#calculator-calc), replace the example expression with your own. Nested placeholders can supply screen or element dimensions.

This example returns `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Keep `decimal` set to `false` for whole-pixel position and size calculations.

The following calculator uses the [**Screen Width** placeholder](./placeholders#screen-width-guiwidth) and divides it by `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Advanced Positioning** ignores the element anchor and uses the top-left screen corner (`X0 Y0`) as its origin. **Stay on Screen** still applies.
