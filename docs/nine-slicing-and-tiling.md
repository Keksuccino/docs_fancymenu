---
title: Nine-Slicing and Tiling
description: Make textures with frames fit every size without warping them, or repeat a pattern instead of stretching it.
---

# Nine-Slicing and Tiling

Your own textures get stretched to the size of the element. That's fine for photos, but frames, panels and buttons with borders look warped when they get wider or higher. Two settings fix that:

- Nine-slicing keeps the corners and edges of a texture in shape and only fills the middle.
- Tiling repeats a texture instead of stretching it, so a pattern keeps its size.

<img width="800" alt="A square panel texture cut into nine parts by four lines, and the same texture as a wide panel with corners and edges that kept their shape" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png">

# How Nine-Slicing Works

Four lines cut the texture into nine parts. The four corners always stay the same size, the edges only get longer, and the middle fills the rest.

1. Set your texture.
2. Turn on its nine-slice setting. See [Where It Works](#where-it-works) for its name.
3. Set the border sizes to how thick the frame of your texture is, in pixels of the texture. For a frame that's 4 pixels thick, use `4`.

Good to know:

- The borders show up as big on the screen as they are in the texture. So a texture with 40 pixel borders looks chunky on a small button. Make the texture about as big as the element.
- Most textures have one size for the left and right borders (X-Borders) and one for the top and bottom (Y-Borders). Progress Bars, Tooltips and Global Customizations have a size for every side.
- Borders that are too big for the texture get made smaller on their own.

# Where It Works

| Texture | Nine-slicing | Tiling |
|---|---|---|
| [Button](/elements#button) textures, in **Button Textures** | **Nine-Slice Custom Background** | - |
| [Slider](/elements#slider) textures, in **Slider Textures** | **Nine-Slice Custom Background** and **Nine-Slice Custom Handle** | - |
| [Image](/elements#image) elements | **Nine-Slice Texture** | **Repeat Texture** |
| The **Background** of [Text](/text-in-menus#background) elements and [Scrollable Areas](/scrollable-areas#background) | **Nine-Slice Custom Background** | **Tile Texture** |
| **Scroll Bar Backgrounds** of Text elements and Scrollable Areas | always on | - |
| The **Background** of [Tooltip](/elements#tooltip) elements | always on, sizes in **Nine-Slicing Settings** | - |
| [Progress Bar](/elements#progress-bar) textures | **Nine-Slice Bar Texture** and **Nine-Slice Background Texture** | - |
| [Global button and slider textures](/global-customizations#buttons-and-sliders) | **Nine-Slice Button Backgrounds**, **Nine-Slice Slider Background** and **Nine-Slice Slider Handle** | - |
| [Image menu backgrounds](/menu-backgrounds#image) | - | **Repeat Texture** |
| Header and footer of [scrollable screens](/customizing-scrollable-screens) | - | **Repeat Header Texture** and **Repeat Footer Texture** |

## Backgrounds of Text Elements and Scrollable Areas

Open **Background** in the right-click menu of a Text element or Scrollable Area:

- **Custom Background Texture** replaces the built-in dark panel with your own texture. Reset it to get the panel back.
- **Nine-Slice Custom Background** is on by default. Set the borders with **Nine-Slice Background X-Borders (Left & Right)** and **Nine-Slice Background Y-Borders (Top & Bottom)**.
- **Tile Texture** repeats your texture instead of stretching it. Together with nine-slicing, the edges and the middle get repeated, and the corners stay as they are.
- **Show Background** turns the whole background off.

## Scroll Bar Backgrounds

Open **Scroll Bars -> Scroll Bar Backgrounds** of a Text element or Scrollable Area. **Vertical Bar Texture** and **Horizontal Bar Texture** draw a texture along the way the scroll grabber moves. They always get nine-sliced, so their ends keep their shape on bars of every length. Set the borders with the two border settings below them.

# How Tiling Works

Tiling puts the texture next to itself as often as it fits, at its own size. Use a seamless texture, where the left edge fits the right edge and the top fits the bottom. Otherwise, you see lines between the tiles.

On Image elements, **Repeat Texture** and **Nine-Slice Texture** don't work together. With both on, the image gets repeated.
