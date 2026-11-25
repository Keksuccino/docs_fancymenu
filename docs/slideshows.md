---
title: Slideshows
description: Show your own images one after another, with a soft fade between them, as menu background or in a part of the screen.
---

# Slideshows

A slideshow shows images one after another and fades softly from one to the next, like screenshots of the world of your modpack.

You can show it as the [menu background](/menu-backgrounds) of a layout, or with a [Slideshow element](/elements#slideshow) in a part of the screen.

<img width="800" alt="The Title screen with a slideshow as background that fades from a river valley to a cherry grove and a coast, screenshots of a Minecraft world" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_title.gif?raw=true">

# Making a Slideshow

1. Open the `slideshows` folder in `config/fancymenu/` of your game directory. **menu bar -> Tools -> Open FancyMenu Directory** opens `config/fancymenu/`.
2. Make a folder for your slideshow in it, like `world_tour`. Its name doesn't matter.
3. Put a [`properties.txt`](#propertiestxt) and a folder called `images` with [your images](#the-images) into it. An [`overlay.png`](#overlay) is optional.
4. Reload FancyMenu with **menu bar -> Customization -> Reload FancyMenu** or `Ctrl + Alt + R` (`Cmd + Alt + R` on macOS), or restart the game.

```text
config/fancymenu/slideshows/
└── world_tour/
    ├── properties.txt
    ├── overlay.png
    └── images/
        ├── 01_river_valley.png
        ├── 02_cherry_grove.png
        └── 03_coast.png
```

# The Images

- Only PNG and JPG files count, with names that end in `.png` or `.jpg`. Rename `.jpeg` files to `.jpg`.
- They show in the order of their file names, from A to Z. Numbers count like letters, so `10.png` comes before `2.png`. Start them with zeros, like `01`, `02` … `10`.
- Give all images the same size. The first one decides the shape of the slideshow, and the others get stretched to it.
- Files in folders inside `images` don't count.

# properties.txt

```text
type = slideshow

slideshow-meta {
  name = world_tour
  duration = 5.0
  fadespeed = 5.0
  randomize = false
}
```

| Setting | What it does |
|---|---|
| `name` | The name you pick the slideshow by. Give every slideshow its own name. |
| `duration` | Seconds from one image change to the next, with the fade. A fade that takes longer makes the next change wait for it. |
| `fadespeed` | How fast one image fades into the next. At `1.0`, a fade takes about 6 seconds, at `3.0` about 2. Has to be above `0`. |
| `randomize` | `true` shows the images in a random order, never the same one twice in a row. `false` shows them in the order of their file names. |

Only `name` is required. Settings you leave out use `duration = 10.0`, `fadespeed = 1.0` and `randomize = false`. Keep the `type = slideshow` and `slideshow-meta {` lines as they are, write one setting per line and use a point for decimals, like `2.5`.

Slideshows made for older versions can have `width`, `height`, `x` and `y` lines. They don't do anything: the background or the element decides where the slideshow shows and how big.

# Overlay

An `overlay.png` next to `properties.txt` gets drawn over every image, stretched to the size of the slideshow. It doesn't fade with the images, so it's made for frames, vignettes or a logo in a corner. Its transparent parts let the images show through.

The overlay belongs to the slideshow, so it shows everywhere the slideshow does. For the same images with and without a frame, make two slideshows.

# Using a Slideshow

## As Menu Background

<img width="800" alt="Opening Menu Backgrounds, Slideshow in the layout editor, turning on Show Background and picking world_tour in Choose Slideshow, whose preview fades to the next image, then the slideshow shows behind the Title screen buttons" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_background.gif?raw=true">

1. In the [layout editor](/layout-editor), right-click the background and open **Menu Backgrounds -> Slideshow**.
2. Click **Show Background** to turn it on.
3. Click **Slideshow Name**, pick your slideshow and click **Done**. The preview on the right shows it running.

**Clear Slideshow** takes it out again. To combine it with other backgrounds, see [Menu Backgrounds](/menu-backgrounds).

The slideshow gets stretched to the whole screen. To keep the shape of its images, turn on **Preserve Background Aspect Ratio** in **Menu Backgrounds**. It then fills the screen and gets cut off at its sides or at its top and bottom.

## As Element

<img width="800" alt="The Title screen with its buttons on the left and a Slideshow element on the right that fades through screenshots of a Minecraft world" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_element.gif?raw=true">

1. In the layout editor, right-click a free spot and add a Slideshow with **New Element**.
2. Right-click the element, click **Slideshow** and pick your slideshow. The element takes the shape of its images.
3. Move and resize it like any other element. **Restore Aspect Ratio** changes its width to fit its height again, so the images aren't stretched.

## Pre-Loading

A slideshow loads each image the first time it shows, so big images can show up a moment late the first time. To load all images and the overlay while the game starts, add the slideshow with **Add Slideshow** in **menu bar -> Customization -> Pre-Load Resources**. See [Pre-Load Resources](/preload-layouts#pre-loading-slideshows--panoramas).

# Good to Know

- Everything that shows the same slideshow shows the same image at the same time, also in different menus.
- A slideshow only runs while something shows it. When it shows up again after a break longer than its `duration`, it fades to its next image right away.
- Reloading FancyMenu starts every slideshow over. The first image after the start stays only half as long as the others.
- Slideshows belong to the loaded [profile](/profiles).
- A slideshow that's missing from **Choose Slideshow** didn't load. The game's log, `logs/latest.log`, says why, like a missing `name`, `properties.txt` or `images` folder.
- On Windows, turn on file name extensions in File Explorer, so `properties.txt` doesn't end up as `properties.txt.txt` by accident.
- A purple and black checkerboard means that no slideshow is picked, or that the layout uses a slideshow name that doesn't exist anymore.
- If two slideshows have the same `name`, only one of them shows up.
- The **Debug Overlay** (`Ctrl + Alt + D`) shows how many slideshows and images FancyMenu loaded.
