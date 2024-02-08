---
title: Randomize Layouts
description: How to randomize full layouts or parts of it.
published: true
date: 2024-02-08T05:42:41.613Z
tags: 
editor: markdown
dateCreated: 2024-02-08T05:19:14.757Z
---

# Randomization

FancyMenu has lots of features that help you randomize layouts or parts of it.

This can be useful for example if you want users to see different screen backgrounds every time they open a screen or randomized tips in the loading screen.

# Randomizing Layouts

There's a feature in FancyMenu that allows you to make a group of layouts and the system will automatically pick a random layout out of this group. By doing that you can basically show a completely different randomized menu design every time the user launches the game or opens a screen, but it can also be used to only change parts of the screen, for example the background.

## Random Mode

To randomize layouts you need to enable the **Random Mode** for every layout that should be a possible pick for the randomization. To do that, **right-click** the editor background and search for the **Random Mode** entry.

<br>

<img width="351" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/ef0f22d5-2f48-47cd-b526-d12415d8e099">

## Random Group Identifier

After enabling the random mode you need to set its **Random Group Identifier**.
This number needs to be **the same** for every layout that should be in the **same group**.

<br>

<img width="301" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/dde0c94e-9729-4251-9aca-32a55c3dfd02">

<br>

<img width="377" alt="Screenshot_8" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/25e7777c-0503-4e54-b866-e85647241eee">

## Randomizing Behavior

If you only want the system to pick a random layout of the group **once per game session**, enable **Randomize Only First Time**. This will make it pick a layout the first time the screen gets opened and then always uses the layout it picked the first time. If this is disabled it will pick a random layout every time the screen gets opened.

<br>

<img width="305" alt="Screenshot_9" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/355e49eb-73b0-4646-aeb2-c6f113f6ce3b">