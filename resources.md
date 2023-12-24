---
title: * Resources
description: How resources work in FancyMenu. Covers resource locations, local resources and web resources.
published: true
date: 2023-12-24T02:06:52.072Z
tags: 
editor: markdown
dateCreated: 2023-12-23T10:12:20.794Z
---

# WIP ----

- Resource Locations explained
- Web & Local resources explained


# Resources

FancyMenu's resource system allows you to use resources from Minecraft's own resource loader (**Resource Packs**), **Local** resources (files from the client system) and **Web** sources (files stored online).

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


