---
title: Nine-Slicing & Tiling
description: Scale bordered textures or repeat seamless textures.
published: true
date: 2026-05-03T11:01:52.000Z
tags:
editor: markdown
dateCreated: 2025-05-07T00:48:22.581Z
---

# Nine-Slicing and Tiling

Nine-slicing preserves a texture's corners and borders while stretching its center. Tiling repeats a texture instead of stretching it.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Nine-slice regions" style="max-width:500px;height:auto;" />

# Nine-Slicing Support

| Area | Supported targets |
|---|---|
| Widgets | [Button](./elements#button) and [Slider](./elements#slider) textures; [global button and slider styles](./global-customizations#button-visuals) |
| Images and panels | [Image elements](./elements#image) |
| Progress Bars | [Fill and background textures](./elements#progress-bar) |
| Tooltips | [Custom background textures](./elements#tooltip) |

# Configuring Nine-Slicing

1. Set the target texture.
2. Enable its **Nine-Slice** option.
3. Set the border sizes to match the fixed edge area in the source texture.
4. Resize the element and adjust the border values if the corners or edges distort.

Button and Image settings use X/Y border sizes. Progress Bars and Tooltips expose separate edge values where needed.

# Tiling Support

Repeating textures are available for:

- [Image elements](./elements#image).
- [Image menu backgrounds](./menu-backgrounds).
- [Scroll-list header and footer textures](./customizing-scrollable-screens).

Enable **Repeat Texture** on an Image element or Image background. For scrollable screens, use the repeat options in the header/footer customization menu.

Use a seamless source texture; mismatched edges create visible lines between tiles.

Nine-slicing and repeating are separate modes. If both options are shown for a target, choose the one that matches the intended scaling behavior.
