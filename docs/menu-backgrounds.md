---
title: Menu Backgrounds
description: Give a menu its own background, like an image, a panorama, a video, a color or a shader, and stack several of them.
---

# Menu Backgrounds

A layout can give its screen a background of its own: an image, an animation, a panorama, a slideshow, a video, a color, a website or a shader. It replaces the screen's normal background, like the panorama of the Title screen, the blur of other menus or the world behind the pause menu.

<img width="800" alt="The Title screen with a pixel art background of a snowy valley at night, with an aurora, a full moon and a cabin with lit windows" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_hero.png?raw=true">

> [!TIP]
> To give all menus the same background without making layouts, use the [Global Customizations](/global-customizations#menu-backgrounds).

# Setting a Background

<img width="800" alt="Right-clicking the editor background of the Title screen, opening Menu Backgrounds and Image, turning on Show Background and picking an image through Choose Image" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_image.gif?raw=true">

1. Open a layout of the screen in the [layout editor](/layout-editor).
2. Right-click the editor background and open **Menu Backgrounds**. It's also in **menu bar -> Layout -> Layout Properties**.
3. Open a background type, like **Image**.
4. Click **Show Background** to set it to **Enabled**.
5. Set up the background, like with **Choose Image** for an Image background.

<img width="800" alt="The Menu Backgrounds menu with a check mark in front of Image and a cross in front of all other types, and the settings for all backgrounds below them" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_menu.png?raw=true">

In **Menu Backgrounds**, every type that's on has a ✔ in front of it, and every type that's off a ✖. Hover over a type to see what it does.

To get the screen's normal background back, set **Show Background** of the type to **Disabled** again. Its settings stay, so you can turn it on again later.

# Background Types

## Image

An image from your files, a website or the game's resources, stretched over the whole screen. Animated images play too. Supported files are listed in [Images](/images).

- **Choose Image**: the image. Where it can come from: [Resources](/resources).
- **Choose Fallback Image**: shows while the image can't load, like a web image while you're offline.
- **Restart Animated Textures When Opening Screen**: starts an [animated image](/animations) over every time the screen opens. Otherwise it plays on from where it was.
- **Repeat Texture**: tiles the image over the screen instead of stretching it. See [Nine-Slicing and Tiling](/nine-slicing-and-tiling).
- **Slide Wide Images From Left To Right**: a wide image, like a photo of a whole landscape, fills the screen's height and slowly slides from side to side, with a short stop at each end.
- **Parallax Effect** and its settings: the image moves a bit with the mouse. See [Parallax Effect](/parallax#menu-backgrounds).

**Slide Wide Images From Left To Right** can't be on together with **Repeat Texture** or **Parallax Effect**.

## Color

One color over the whole screen.

- **Color [HEX]**: the color, like `#1B2440`. Two more digits make it see-through, like `#1B2440C8`. It can also be a [placeholder](/placeholders).

The Color is below all other backgrounds of the layout, so it fills their transparent parts. See [Stacking Backgrounds](#stacking-backgrounds).

## Cubic Panorama

A panorama that turns slowly, like the one of the Title screen. You make panoramas in `config/fancymenu/panoramas/`, see [Panoramas](/panoramas).

- **Panorama Name**: opens **Choose Panorama**, where you pick one of your panoramas and see a preview of it.
- **Clear Panorama**: removes the panorama.

Without a panorama, the background shows Minecraft's purple and black missing texture.

## Slideshow

Shows the images of a slideshow one after another. You make slideshows in `config/fancymenu/slideshows/`, see [Slideshows](/slideshows).

- **Slideshow Name**: opens **Choose Slideshow**, where you pick one of your slideshows.
- **Clear Slideshow**: removes the slideshow.

Without a slideshow, the background shows Minecraft's missing texture too.

## Video

Plays a video from your files, a website or the game's resources. It needs Watermedia: see [Videos](/video#requirements). Without it, the background shows a note with download links.

- **Video Source**: the video.
- **Loop Video**, **Volume** and **Sound Channel**: how it plays.
- **Parallax Effect** and its settings: like for Image backgrounds.
- **Play Video In Layout Editor**: turned off, the video stays paused in the layout editor.

[Actions](/video) can pause the video and change its volume and play time. They need the background's ID: click **Copy Background Identifier** in its settings.

## Browser

A website over the whole screen, like the [Browser element](/elements#browser).

> [!IMPORTANT]
> The Browser needs the mod [Rinku](https://modrinth.com/mod/rinku). Without it, the background is red and says that Rinku is missing.

- **URL**: the website. It can contain [placeholders](/placeholders).
- **Process Mouse Clicks**, **Process Mouse Scrolls** and **Process Keyboard Presses**: let players click, scroll and type on the website. It gets the keyboard right when the screen opens.
- **Consume Mouse Clicks**, **Consume Mouse Scrolls** and **Consume Keyboard Presses**: stop clicks, scrolling and keys at the website, so the screen itself doesn't react to them too.
- **Mute Browser**, **Audio/Video Volume**, **Loop Videos** and **Hide Video Controls**: media on the website.

Buttons and elements in front of the background always get clicks first. In the layout editor, the background shows stripes instead of the website.

## GLSL Shader

Draws a shader, a small program for the graphics card, like animated waves, stars or patterns. Shaders from Shadertoy work too.

- **Shader Source**: the code of the shader.
- **Show Compile Errors**: shows mistakes in the code on the screen. Turn it off for finished layouts.

All other settings, like the extra passes, textures and time, are explained in the [GLSL Shader API](/glsl-shader-api).

## Video [Rinku]

An older video background that needs Rinku. It's only in the list while it's on, like in layouts from older versions. Use **Video** instead.

# Settings for All Backgrounds

Below the types, **Menu Backgrounds** has settings that work for all backgrounds of the layout:

- **Preserve Background Aspect Ratio**: keeps the proportions of Image, Slideshow and Video backgrounds. They still fill the whole screen, and the parts that don't fit get cut off. Turned off, they get stretched to the screen.
- **Show Dark Overlay On Custom Background**: puts the dark, see-through layer of Minecraft's menus over the backgrounds, so buttons and text stand out more.
- **Apply Vanilla Background Blur**: blurs the backgrounds like Minecraft blurs the world behind menus. How strong it is depends on the player's **Menu Background Blur** in Minecraft's **Accessibility Settings**. At `0`, there's no blur.

<img width="800" alt="The same background three times side by side: as it is, darker with Show Dark Overlay On Custom Background, and blurry with Apply Vanilla Background Blur" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_effects.png?raw=true">

From left to right: no setting, **Show Dark Overlay On Custom Background** and **Apply Vanilla Background Blur**.

# Stacking Backgrounds

You can turn on several types in one layout. They get drawn over each other in this order, from the bottom to the top:

1. Color
2. Cubic Panorama
3. Image
4. Slideshow
5. Video
6. Video [Rinku]
7. Browser
8. GLSL Shader

Types that other mods add come last, on top.

FancyMenu draws black behind the backgrounds, so the transparent parts of an image show black. A Color background below it fills them with a color:

<img width="800" alt="A pixel art landscape whose sky is transparent. On the left half, the sky is black. On the right half, a blue Color background fills it" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_stacking.png?raw=true">

On the left, only the Image is on. On the right, a Color background fills its sky.

- A see-through Image, Slideshow or Shader on top of a Cubic Panorama works the same way, like a frame around a turning panorama.
- A Video background is never see-through. It covers everything below it, even where the video doesn't reach.

## Several Layouts

When several layouts are active on a screen, like a [universal layout](/universal-layouts) and a layout of the screen, their backgrounds stack too:

- The layout with the higher **Layout Index [Multi-Layout Ordering]** is on top. Set it in the right-click menu of the editor background.
- If one of the layouts turns on a [setting for all backgrounds](#settings-for-all-backgrounds), it's on for the backgrounds of all of them.
- The layout editor only shows the backgrounds of the layout you edit.

# Good to Know

- Elements of the layout are always in front of its backgrounds.
- **Copy Background Identifier**, in the settings of every type, copies the ID of the background for actions and placeholders that control it, like the ones of [Video backgrounds](/video).
- **Export for AI**, in the settings of every type, copies the background for an [AI chat](/export-for-ai).
- The header and footer of screens with lists, like the world list, have their own textures: right-click the editor background and open **Header/Footer Customizations**.
