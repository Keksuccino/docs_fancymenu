---
title: Resources
description: How resources work in FancyMenu. Covers resource locations, local resources and web resources.
published: true
date: 2025-07-06T14:40:29.444Z
tags: 
editor: markdown
dateCreated: 2025-04-14T20:15:54.572Z
---

# Resources

FancyMenu's resource system allows you to use resources from Minecraft's own resource loader (**Resource Packs**), **Local** resources (files from the client system) and **Web** sources (files stored online).

Almost all resource inputs, be it images, audio, video or text, gets set via FancyMenu's resource chooser. There are some exceptions, like when setting a source path for a placeholder or action, but in most places, you set resources via the same resource chooser interface.

# Minecraft Resources (Resource Packs)

Minecraft uses so called "resource locations" to "point" to a resource.

Resource locations written as text consist of two parts, separated by colon (`:`).
The first part is the **namespace** and the second path is the rest of the **path to the resource**, including the resource name with file extension.

The **namespace** of a resource location is always just the **top-level directory/folder** of the full path to the resource.

So lets say you load a resource pack with a resource called `image.png` that is stored in `/assets/custom_resources/images/image.png`.
In this case, the **namespace** of the resource location would be `custom_resources`, because `/assets/` is just where Minecraft loads all its resources from, so `custom_resources` is the **top-level directory** of the resource.
This means that `images/image.png` is the **rest of the path** to the resource.

So the correct resource location to the `image.png` resource would be:
`custom_resources:images/image.png`

> **Fun fact**: Since Minecraft has most of its resources stored in `/assets/minecraft/`, the **namespace** of most Minecraft resources is `minecraft`.
{.is-info}

# Local Resources

The easiest way to load resources is to simply use local files stored on the client (and in most cases shipped with modpacks).

FancyMenu only allows loading local resources stored in `/config/fancymenu/assets/`, so make sure to store all your resources there!

This also makes it really easy to [ship local resource with your modpacks](./modpacks), since most modpack systems (CurseForge, Modrinth, etc.) support shipping mod config folders by default.

# Web Resources

When you need to dynamically change resources without the need to update your modpack, **web** resources would be the best option.

A web resource is basically just the **URL** to a file stored on a server, so let's say `https://example-domain.net/image.png`.

Make sure to always use **DIRECT URLs**, which means URLs that end with the resource's **file name and extension**, just like the example URL above.
Using non-direct URLs hurts performance and is more likely to fail.

# Placeholders in Resource Sources

It is possible to use FancyMenu's placeholders in resource sources, like the path to a local source, the URL to a web source or the resource location to a Minecraft resource.

This makes it possible to dynamically update sources, like changing the image source of a menu background when setting a FancyMenu variable, to show a different background based on the variable's value.

You can manually edit the source by clicking on the **Open in Editor** button at the right side of the resource source input field.

> Keep in mind this is only for resource inputs that use the normal resource chooser interface. It is possible that *some* resource inputs that do not use the chooser do **NOT** support placeholders or do not update dynamically when the placeholder changes.
{.is-warning}

