---
title: Slideshows
description: How to make and use slideshows.
published: true
date: 2023-12-24T09:02:04.247Z
tags: 
editor: markdown
dateCreated: 2023-12-24T09:02:04.247Z
---

# Slideshows

FancyMenu allows you to add slideshows and display them in menus and as menu backgrounds.

> **IMPORTANT**: If you're on Windows, don't forget to turn on [file extensions](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png), because otherwise you will not be able to see important parts of file names later!
{.is-warning}

# Getting Started

Every slideshow has to be in its own folder **inside** the slideshows directory located at `.minecraft/config/fancymenu/slideshows/`.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

To make an slideshow getting recognized as this by the system, it needs to have a properties file located in its home directory.
So if you've named your slideshow folder "myslideshow" (this is your slideshow home directory), the properties file should be located at `.minecraft/config/fancymenu/slideshows/myslideshow/properties.txt`.
**This file always need to be named `properties.txt`!**
For now, only create the **empty** properties file and move on to the next step.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

# 2. Adding Images
Sure, the most important part of a slideshow is..well..the images of the slideshow, so it isn't just a cool looking folder.

All images of your slideshow go to an extra folder **inside** the **home directory** of your slideshow.
This folder **have to** be named `images`.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Now place all your slideshow images in the `images` folder.
They are being ordered alphabetically (respecting numbers), so just name them something like `image_1`, `image_2` and so on.
In my example, `image_1` would be displayed first and `image_2` after.

![4](https://user-images.githubusercontent.com/35544624/105211270-58c6d580-5b4c-11eb-851c-46aa31edcdb7.png)

# 3. Filling the Properties File
Yes, images are a very important part for your slideshow, but now comes the **really** most important part.

At the beginning, you've created an empty `properties.txt` file in your slideshow home directory.
This file needs to be filled with important stuff now.

Just like with [panoramas](./panoramas), you need to add informations about your slideshow to this file.

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

## name
This is the name of your slideshow. You need it to identify your slideshow when using it.
The name needs to be **unique**! It's not possible to have two slideshows with the same name!

## width | height
The base width and base height of your slideshow. Used by FancyMenu to calculate the aspect ratio.

## x | y
The x and y position of your slideshow. More for debugging purposes, just set both to 0.

## duration
The duration in **seconds** every image is displayed before switching to the next one.
**Suppports decimal values!**

## fadespeed
The speed of the fade animation when switching to the next image.
This value is a speed multiplicator. For example, `1.0` is default speed, `2.0` doubles the speed and `0.5` will half it.
Negative values are not supported, use decimal values to slow down the speed.

# 4. Using the Slideshow
All important steps are now done and your slideshow is finished! It should now contain a `properties.txt` file and an `images` folder with all your slideshow images.

To load your new or edited slideshow into FancyMenu, just press the [Reload](./customization-helper#h-1-the-reload-button) button to reload your slideshows.

Now you can use your slideshow in the [Layout Editor](./layout-editor) as element and as menu background!