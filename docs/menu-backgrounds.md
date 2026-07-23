---
title: Menu Backgrounds
description: How to set custom menu backgrounds (images, animations) for screens.
published: true
date: 2026-05-03T11:01:52.000Z
tags: 
editor: markdown
dateCreated: 2025-06-10T00:20:13.298Z
---

# Menu Backgrounds

FancyMenu lets you set custom backgrounds for menus. You can use images, animated textures, slideshows, cubic panoramas, colors, browsers, videos, GLSL shaders and more.

# Setting a Background

Menu background customization is available from the layout editor context menu:

1. Open the layout editor.
2. Right-click the editor background.
3. Open **Menu Backgrounds**.
4. Enable and configure the background type(s) you want.

Common background types include:

- Vanilla
- Image
- Slideshow
- Cubic Panorama
- Color (HEX)
- Browser
- Video
- GLSL Shader
- Video [MCEF] (deprecated)
- Additional add-on background types

The old **Video [MCEF]** background type is deprecated. Use the [native **Video** background](./video) powered by Watermedia V3 for new layouts.

# Removing the Custom Background

Open **Menu Backgrounds** again and disable/remove the custom background type you no longer want. If no custom background type is active, the screen will fall back to its normal vanilla background behavior.

# Stacking Backgrounds

Multiple menu background types can be enabled in one layout. Active backgrounds render as a stack, so a base image or panorama can be combined with translucent browser, shader, parallax, or other layers.

If you also have multiple layouts active, their background stacks can combine too. To sort layouts and make them show up in a specific order, right-click the editor background and click on **Layout Index**.

# Transparent Backgrounds

FancyMenu renders a black backing layer behind active custom backgrounds. Transparent pixels in the bottom-most background therefore reveal black. Use an opaque base background, then stack translucent backgrounds above it.

To make a background image translucent, use an image editor of your choice.

# Browser Backgrounds

The **Browser** background type works like the [Browser element](./elements#browser), but fills the whole screen and is auto-focused. This is useful for fullscreen web content, local HTML pages, or web-video layers.

# GLSL Shader Backgrounds

The **GLSL Shader** background type renders custom GLSL shaders and supports Shadertoy-style shader authoring. See the [GLSL Shader API](/glsl-shader-api) page for supported uniforms and shader structure.
