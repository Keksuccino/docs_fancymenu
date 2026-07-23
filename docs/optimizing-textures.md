---
title: Optimizing Textures
description: How to optimize textures for FancyMenu.
published: true
date: 2025-05-17T18:59:42.199Z
tags: 
editor: markdown
dateCreated: 2025-05-17T18:59:39.559Z
---

# Optimizing Textures for FancyMenu

FancyMenu uses the textures you provide as-is, meaning it does **not** compress, downscale, or upscale your image files. To ensure your menus look sharp and perform well, it's important to optimize your textures when using them in your UI.

# Key Tips for Texture Optimization

The following tips are the most important basic steps you need to keep in mind when working with textures in FancyMenu.

## 1. Use the Right Resolution
- **Avoid low-res images**: If an image is too small and stretched to fit a larger area, it may appear blurry.
- **Avoid high-res overkill**: Very large textures displayed at a small size can also appear distorted or "weird" and may waste performance.

> [!NOTE]
> 📌 **Tip:** Use textures at or near the resolution they will appear in the menu.

## 2. Preserve Aspect Ratio
- Always maintain the image's aspect ratio when scaling.
- Stretching an image disproportionately can lead to visual artifacts and a poor appearance.

> [!NOTE]
> 📌 **Tip:** You can right-click Image elements and click on **Restore Aspect Ratio** to resize them to their correct aspect ratio, then when you further resize them manually, hold **SHIFT** while resizing, to make the resizing respect the element's aspect ratio.

## 3. Consider Nine-Slicing & Tiling
- For scalable UI elements (like panels or buttons), use FancyMenu’s [Nine-Slicing & Tiling](/nine-slicing-and-tiling) features.
- This ensures the edges of textures remain crisp when resized.
