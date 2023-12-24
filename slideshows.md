---
title: Slideshows
description: How to make and use slideshows.
published: true
date: 2023-12-24T09:28:40.536Z
tags: 
editor: markdown
dateCreated: 2023-12-24T09:02:04.247Z
---

# Slideshows

FancyMenu allows you to add slideshows and display them in menus and as menu backgrounds.

> **IMPORTANT**: If you're on Windows, don't forget to turn on [file extensions](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png), because otherwise you will not be able to see important parts of file names later!
{.is-warning}

# Making a Slideshow

Every slideshow has to be in its own folder **inside** the slideshows directory located at `/config/fancymenu/slideshows/`.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

To make a slideshow get recognized as one by the system, it needs to have a properties file located in its slideshow folder, so if you've named your slideshow folder `myslideshow`, the properties file should be located at `/config/fancymenu/slideshows/myslideshow/properties.txt`.

**This file always needs to be named `properties.txt`!**
For now, only create the **empty** properties file and move on to the next step.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## Adding Images

A slideshow needs images (duh), so let's add some!

All images of your slideshow go to an extra folder **inside** your slideshow folder (`myslideshow` in the example above).
This folder's name needs to be `images`.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Now place all your slideshow images in the `images` folder.
They get ordered alphabetically (respecting numbers), so just name them something like `image_1.jpg`, `image_2.jpg` and so on.
In my example, `image_1.jpg` would be displayed first and `image_2.jpg` after.

![4](https://user-images.githubusercontent.com/35544624/105211270-58c6d580-5b4c-11eb-851c-46aa31edcdb7.png)

## Adding Content to the Properties File

At the beginning, you've created an empty `properties.txt` file in your slideshow folder.
This file needs to be filled with some important stuff now.

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
}
```
Only the variables inside the `slideshow-meta` section can be changed!

### name

This is the name, or better the identifier, of your slideshow.
Slideshow names need to be **unique**, so it's not possible to have two slideshows with the same name!

### width | height

The base `width` and base `height` of your slideshow.
Used by FancyMenu to calculate the aspect ratio.

### x | y

The `x` and `y` position of your slideshow.
More for debugging purposes, so just set both to `0`.

### duration

The duration in **seconds** for how long every image is displayed before switching to the next one.
Suppports decimal values!

### fadespeed

The speed of the fade animation when switching to the next image.
This value is a speed multiplicator. For example, `1.0` is default speed, `2.0` doubles the speed and `0.5` will make it half as fast as default.
Negative values are not supported.

# Using the Slideshow

All important steps are done and your slideshow should be ready now, so lets test it!

To load your new (or edited) slideshow into FancyMenu, reload the mod via **Customization -> Reload FancyMenu**.

Now you can use your slideshow in the **Slideshow** element or as menu background (right-click the layout editor background -> **Menu Background**).