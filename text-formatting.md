---
title: * Text Formatting
description: How to format text with Markdown and Minecraft's formatting codes.
published: true
date: 2023-12-24T05:46:33.973Z
tags: 
editor: markdown
dateCreated: 2023-12-23T10:10:33.171Z
---

# Text Formatting

FancyMenu has lots of features to make text content in layouts *fancier*!

Text elements have full **Markdown** support with some cool extras and most other text content supports **Minecraft's text formatting** system and button labels even have support for **Minecraft's text components** that allow you to use custom Fonts and more.

# Markdown

FancyMenu's **Text elements** have full Markdown support, which means you can format text content by adding special characters to it.

For example, to make text look bold, you add `**` before and after the bold text, so `**Some bold text that's very bold.**` will look like that:
**Some bold text that's very bold.**

FancyMenu's Markdown even has some special stuff that makes it even more powerful!

## Fonts

You can show text in a custom font loaded via resource pack by adding `%!!<font_name>%` before the text and `%!!%` after.

A valid font included in the base game is `uniform`, so to display text in the `uniform` font, do this:
`%!!uniform%this is a custom font%!!%`

This will display `this is a custom font` in the `uniform` font.

## Text Color (HEX)

Showing text in a specific HEX color is possible by adding `%<HEX_color>%` before the text and `%#%` after.

A valid HEX color for green is `#77fc03`, so to show text in this color, do this:
`%#77fc03%this text is green!%#%`

This will show `this text is green!` as `#77fc03` (green).

Make sure that the HEX color is starting with `#`!

## Headlines

To show **a line of text** as headline (bigger and underlined), add `# ` (very big), `## ` (big) or `### ` (small) before the text line.

Example:
`## Big Headline`

## Bold

Add `**` before and after text to make it look **bold**.

Example:
`**bold text content**`

## Italic

Add `_` OR `*` before and after text to make it look *italic*.

Example:
`*italic text content*`

## Strikethrough

Add `~` before and after text to make it look ~~strikethrough~~.

Example:
`~strikethrough text content~`

## Hyperlinks

You can add hyperlinks to text content that open a website when clicked.

Text that should appear as [hyperlink](https://google.com) needs to get wrapped in `[ ]`, followed by the actual link wrapped in `( )`.

So if you want to make `example text content` clickable and open `https://example-website.net`, do this:
`[example text content](https://example-website.net)`

## Images

Markdown supports displaying images in text content.

FancyMenu supports Minecraft resources, local resources and web resources in Markdown.

To add an image, start a text line with `![](`, then the [URL, Resource Location or Path to the resource](/resources) and then `)`.

So to show the Web resource `https://example-website.net/image.png`, do this:
`![](https://example-website.net/image.png)`

Images can also be **hyperlinks** by wrapping the whole image text line in a **hyperlink** like that:
`[![](https://example-website.net/image.png)](https://example-website.net)`

## 

