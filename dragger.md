---
title: Dragger
description: How to drag elements in menus by using the Dragger element.
published: true
date: 2025-07-05T19:19:37.358Z
tags: 
editor: markdown
dateCreated: 2025-07-05T19:19:37.358Z
---

# Dragger

The Dragger element is an element in FancyMenu that allows you to make menus interactive in a rather uncommon way. The Dragger is an element that can be dragged with the mouse OUTSIDE the editor, which means users can basically grab the element and move it around.

This is cool and all, but moving around an element that does nothing else is pretty pointless, right? Well, no, because you can attach other elements to it by setting the Dragger element as anchor point for the other elements that should move with the Dragger.

The position offset of Dragger elements is persistent and gets saved across game restarts, which basically just means that when a user moves the Dragger, it stays at this "custom" position, even when restarting the game.

The Dragger element is only visible in the editor and invisible outside, so make sure to use another element as "body" for it, if you want the user to see where the dragable area is.