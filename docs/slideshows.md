---
title: Slideshows
description: How to make and use slideshows.
published: true
date: 2025-04-14T20:16:14.375Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:16:11.469Z
---

# Slideshows

FancyMenu allows you to add slideshows and display them in menus and as menu backgrounds.

> **IMPORTANT**: If you're on Windows, don't forget to turn on [file extensions](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10), because otherwise you will not be able to see important parts of file names later!
{.is-warning}

# Making a Slideshow

Every slideshow has to be in its own folder inside `<game-directory>/config/fancymenu/slideshows/`.

`<game-directory>` is the active launcher instance, which is not always the default `.minecraft` directory.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

To make a slideshow get recognized, it needs a properties file in its own folder. If the slideshow folder is named `myslideshow`, the file belongs at `<game-directory>/config/fancymenu/slideshows/myslideshow/properties.txt`.

**This file always needs to be named `properties.txt`!**
For now, only create the **empty** properties file and move on to the next step.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## Adding Images

A slideshow needs images, so let's add some.

Slideshow images must use `.png` or `.jpg`. Other image extensions, including `.jpeg`, are ignored.

All images of your slideshow go to an extra folder **inside** your slideshow folder (`myslideshow` in the example above).
This folder's name needs to be `images`.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Now place all slideshow images in the `images` folder.

When `randomize = false`, images play in alphabetical filename order. `image_10.png` comes before `image_2.png`, so use names such as `image_01.png`, `image_02.png`, and `image_10.png`.

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## Adding Content to the Properties File

At the beginning you've created an empty `properties.txt` file in your slideshow folder.
This file needs to be filled with some important stuff now.

The complete directory structure should look like this:

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # optional
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

Every slideshow properties file should look like this:

```
type = slideshow

slideshow-meta {
   name = cool_slideshow
   width = 1920
   height = 1080
   x = 0
   y = 0
   duration = 5.0
   fadespeed = 12.0
   randomize = false
}
```
Keep the `type = slideshow` line and the `slideshow-meta` section. Edit the listed values rather than the structural lines.

### name

This is the case-sensitive identifier used to select the slideshow. It is required and must be unique; duplicate names make only one slideshow available.

### width | height

The base width and height in GUI-scaled pixels. FancyMenu also uses them to calculate the aspect ratio.

### x | y

The base top-left position in GUI-scaled pixels. Standard Slideshow elements and menu backgrounds use their own position instead, so keep both values at `0`.

### duration

How many seconds an image stays visible before the next transition. Decimals use a period, for example `5.5`. Use a value greater than `0`.

### fadespeed

The fade-speed multiplier. `1.0` is the default, `2.0` is twice as fast, and `0.5` is half as fast. Use a value greater than `0`.

### randomize

Set this to `true` for random order or `false` for filename order. Random mode avoids showing the same image twice in a row.

# Using the Slideshow

All important steps are done and your slideshow should be ready now, so lets test it!

To load a new or edited slideshow into FancyMenu, use **Customization -> Reload FancyMenu** or restart the client.

Now you can use your slideshow in the **Slideshow** element or as menu background (right-click the layout editor background -> **Menu Background**).
