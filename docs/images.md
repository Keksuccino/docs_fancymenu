---
title: Images
description: Everything important about image resources in FancyMenu.
---
# Images

FancyMenu supports image resources in many places, like menu backgrounds, button textures, and so much more.

You can use PNG, JPEG, GIF, and APNG image files in FancyMenu, but it is recommended to use PNG for static images whenever possible, and instead of using GIF and APNG for animations, better use [an AFMA file](./afma), which is FancyMenu's own animated image type, because AFMAs are so much more optimized than GIF/APNG, use less RAM, and have a smaller impact on performance.

# Converting Images to Supported Formats

When you need to convert images to one of the formats supprted by FancyMenu, or you just want to convert from one supported format to another one for various reasons, take a look at the following list of websites that work well for converting images online, without the need to download any software.

## GIF to APNG
For converting a GIF image to an APNG, use this: https://ezgif.com/gif-to-apng.

## APNG to GIF
For converting and APNG to a GIF, this is what you need: https://ezgif.com/apng-to-gif.

## MP4 to APNG
In case you need to convert a short video sequence to an APNG, try this one: https://ezgif.com/video-to-apng

## PNG to JPEG
Sometimes using a JPEG can make resources smaller, so in that case it can be good to use a JPEG instead of PNG: https://www.freeconvert.com/png-to-jpeg. Keep in mind JPEGs do not support transparency.

## JPEG to PNG
For the common JPEG to PNG case, try this: https://jpg2png.com/

## WebP to PNG
WebP files are not supported by FancyMenu, so you need to convert them to PNG: https://convertio.co/webp-png/

# Limiations of Animated Textures

FancyMenu uses its own [AFMA format](./afma) format for optimized animations, which allows [AFMA files](./afma) to have lots of frames at a high resolution, but for legacy animated file types like GIF and APNG, you should stick to the following recommended limits, to not fill your RAM too much or worsen your game's performance too much:

- Use a maximum for **200 frames** per animation.
- Use a maximum resolution of **1080p** for your frames.
- You should not exceed a total of **1000 frames for ALL animations combined**, because even if you use only 200 frames per animation, it will load all of them in memory, so using too many animations at once will still fill your RAM.

> [!IMPORTANT]
> These limits do NOT apply to [AFMA files](./afma), because AFMAs don't load all their frames into memory, and are a lot more optimized, so they won't have as much impact on performance as legacy animation types.
