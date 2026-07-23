---
title: Parallax Effect
description: Move backgrounds and elements with the mouse cursor.
---

# Parallax Effect

Parallax offsets a background or element based on mouse movement to create visual depth.

# Image Menu Background

1. Right-click the layout editor background.
2. Open [**Menu Backgrounds**](./menu-backgrounds) -> **Image**.
3. Set the image source.
4. Enable **Parallax Effect**.
5. Set the X and Y intensity values.
6. Optionally enable **Invert Parallax Movement**.

The X and Y values control horizontal and vertical movement independently. Use values from `0.0` (none) to `1.0` (maximum).

# Elements

1. Right-click an [element](./elements).
2. Enable **Parallax Effect**.
3. Set **Parallax Intensity X** and **Parallax Intensity Y**.
4. Optionally invert the movement.

Use lower intensity for distant layers and higher intensity for foreground layers. Large differences or inverted layers create a stronger depth effect.

# Troubleshooting

- An intensity of `0` produces no movement on that axis.
- **Slide Wide Images From Left To Right** conflicts with background parallax and must be disabled.
- Very small movement can appear stepped because GUI positions use whole pixels.
