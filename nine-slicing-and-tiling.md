---
title: Nine-Slicing & Tiling
description: How to use nine-slicing and tiling in FancyMenu.
published: true
date: 2025-05-07T00:48:25.757Z
tags: 
editor: markdown
dateCreated: 2025-05-07T00:48:22.581Z
---

# Nine-Slicing and Tiling

When you're designing cool menus in Minecraft with FancyMenu, you might want to use images that need to resize properly or repeat in patterns. This guide explains how to use **Nine-Slicing** and **Tiling** (also called repeating textures) to make your menus look awesome!

# What is Nine-Slicing?

Nine-slicing is a technique that lets you stretch an image to any size without making it look weird. It works by dividing your image into nine parts (like a tic-tac-toe board). The corners stay the same size, the edges stretch in one direction, and the middle stretches in both directions.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Nine-Slice Example" style="max-width: 500px; height: auto;" />

## Where can I use Nine-Slicing?

In FancyMenu, Nine-Slicing is available for:
- **Button Elements** (both custom buttons and when editing Vanilla buttons)

## How to Use Nine-Slicing with Buttons

1. **Create or select a Button Element** in your layout editor.
2. Right-click on the button and look for "Button Textures" option.
3. Set your button's background textures (normal, hover, inactive states).
4. Enable the "Nine-Slice Custom Background" option.
5. Set the **Nine-Slice Background X-Borders** (left and right border size).
6. Set the **Nine-Slice Background Y-Borders** (top and bottom border size).

### Tips for Button Nine-Slicing

- Use an image with clear borders and corners.
- The border values (X and Y) tell FancyMenu how many pixels from each edge should be treated as the border.
- A typical value might be 5 pixels for both X and Y borders.
- The corners will always stay the same size, while the middle parts will stretch to fill the button.

# What is Tiling?

Tiling (also called repeating textures) lets you fill a large area with a small image by repeating it like tiles on a floor. This is perfect for backgrounds or large images where you want a pattern to continue.

## Where can I use Tiling?

In FancyMenu, Tiling is available for:
- **Image Elements**
- **Image Menu Backgrounds**

## How to Use Tiling with Image Elements

1. **Create or select an Image Element** in your layout editor.
2. Right-click on the image and look for "Image Source" to set your texture.
3. Find and enable the **"Repeat Texture"** option.
4. Resize your image element to see the texture repeat to fill the space.

## How to Use Tiling with Menu Backgrounds

1. Go to "Set Background" in your layout properties.
2. Choose the **Image** background type.
3. Select your background image.
4. Enable the **"Repeat Texture"** option.
5. Your background will now repeat the texture to fill the entire screen.

# Creating Good Textures for Nine-Slicing and Tiling

## For Nine-Slicing:
- Create textures with distinct borders and corners.
- Make sure your borders are clear and have a consistent width.
- Test different border sizes to find what works best.
- Buttons usually work well with 3-5 pixel borders.

## For Tiling:
- Create seamless textures that can connect with themselves on all sides.
- Keep patterns simple to avoid visual confusion.
- Test your texture by repeating it in a small area first.

# Examples

## Nine-Sliced Button Example
A simple button might start as a 30x30 image with 5-pixel borders on all sides. When you make the button larger, the corners stay at 5x5 pixels, while the edges and center stretch to fit your button size.

## Tiled Background Example
A small 64x64 tile with a subtle pattern can be repeated to fill your entire menu background, no matter what the screen size is.

# Common Issues and Solutions

## My nine-sliced button looks stretched or distorted:
- Your border values may be too small or too large
- Try changing the border values to match your actual texture

## My tiled background has visible seams:
- Your texture isn't seamless
- Try editing your image to make sure the edges match perfectly

## My textures look blurry when scaled:
- Use higher resolution textures
- Keep your designs simple with clean lines

# Remember

- **Nine-Slicing** is perfect for UI elements that need to change size but keep their appearance (like buttons).
- **Tiling** is great for filling large areas with a pattern (like backgrounds).
- Both features help your UI look good at any resolution or screen size!

Now go create some amazing Minecraft menus with perfectly stretched buttons and beautiful tiled backgrounds!
