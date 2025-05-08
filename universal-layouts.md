---
title: Universal Layouts
description: How to create and use universal layouts.
published: true
date: 2025-05-08T23:45:45.578Z
tags: 
editor: markdown
dateCreated: 2025-05-08T23:42:27.319Z
---

# What are Universal Layouts?

Universal Layouts are a powerful feature in FancyMenu that allows you to create layouts that can be applied to **multiple screens** instead of just a single specific screen. This makes them incredibly useful for creating consistent UI elements that appear across your entire game.

Think of Universal Layouts as "global" layouts that can show up everywhere in your game.

# Why Use Universal Layouts?

Universal Layouts are super helpful when you want to:

- Add the same background to all screens
- Create a logo or text that shows up on many screens
- Make Audio elements continue playing across multiple screens
- Build a consistent look and feel throughout your game

# How Universal Layouts Work

When you create a Universal Layout, it gets loaded with **every screen** in the game by default. This means any elements you add to a Universal Layout (like buttons, images, or text) will appear on all screens.

But don't worry! It is also possible to make the universal layout only load in specific screens! For that, scroll down to the **blacklist** and **whitelist** sections.

# Creating a Universal Layout

1. Open any screen in the game
2. Press **Ctrl+Alt+C** to show the customization menu
3. Go to **Layouts → New → For All Screens [Universal]**
4. Design your layout with elements like images, text, or buttons
5. Save your layout with a descriptive name

# Managing Which Screens Get Your Universal Layout

## Using the Blacklist

The blacklist lets you specify screens where you DON'T want your Universal Layout to appear:

1. In the Layout Editor, right-click on the background
2. Select **Layout Settings → Universal Layout Options**
3. Click **Add Screen To Blacklist**
4. Enter the screen identifier (like `title_screen` for the title screen)

Now your Universal Layout will show up on all screens EXCEPT the ones you blacklisted.

## Using the Whitelist

The whitelist is the opposite - it ONLY shows your Universal Layout on specific screens:

1. In the Layout Editor, right-click on the background
2. Select **Layout Settings → Universal Layout Options**
3. Click **Add Screen To Whitelist**
4. Enter the screen identifier for each screen where you want the layout to appear

When using a whitelist, your Universal Layout will ONLY show up on the screens you listed.

# Finding Screen Identifiers

To add screens to whitelist or blacklist, you need to know their identifiers:

1. Go to the screen you want to identify
2. Press **Ctrl+Alt+C** to open the customization menu
3. Click **Customization → Copy Identifier of Current Screen**
4. The identifier is now copied to your clipboard

You can paste this identifier into the whitelist or blacklist.

# Enabling Customization for All Screens

It is not possible to enable customization for all screens at once.
This is by design and prevents people from accidentally bricking their game because they enable customization for a modded screen that isn't supported.

# Advanced Tips

## Managing the Loading Order

When you have both Universal Layouts and screen-specific layouts, Universal Layouts are loaded FIRST. This means screen-specific layouts can override elements from Universal Layouts.

## Loading Requirements

You can add loading requirements to your Universal Layout so it only loads under certain conditions:

1. Right-click in the editor
2. Choose **Layout Settings → Layout-Wide Requirements**
3. Add conditions like time of day, operating system, or other requirements
