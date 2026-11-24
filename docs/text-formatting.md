---
title: Text Formatting
description: How to format text with Markdown, Minecraft formatting codes and text components.
---
# Text Formatting

FancyMenu gives you three ways to format text:

- **Markdown** for [Text and Tooltip elements](/text-in-menus): headlines, lists, colors, images, tables and more.
- **Minecraft formatting codes** like `&c` for quick colors. They work in almost every text field, Markdown text included.
- **Minecraft text components** for button and slider labels.

> [!TIP]
> This page is all about *how to write* formatted text. To learn how to add text to your menus, change its look or make it scroll, see [Text in Menus](/text-in-menus).

<img width="800" alt="Markdown in a Text element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_showcase.png?raw=true">

# Markdown

Markdown formats text with a few special characters around it. For example, `**bold**` turns into **bold** text.

Markdown works in [Text elements](/elements#text) and [Tooltip elements](/elements#tooltip). The characters you write decide *what* something is (a headline, a list, a quote). The element's [look](/text-in-menus#looks-and-styles) decides how it looks, like its colors and sizes.

## Quick Overview

| You write | You get |
|---|---|
| `**bold**` or `__bold__` | Bold text |
| `*italic*` or `_italic_` | Italic text |
| `++underlined++` | Underlined text |
| `~~crossed out~~` | Crossed out text |
| `` `code` `` | Inline code |
| `[Open Website](https://example.com)` | A clickable link |
| `%#ff5555%red text%#%` | Colored text |
| `# Headline` | A headline |
| `- Item` | A bullet list |
| `1. Item` | A numbered list |
| `> Text` | A quote |
| `> [!TIP]` | A callout box |
| `---` | A separator line |

## Text Styles

| Style | How to write it |
|---|---|
| **Bold** | `**text**` or `__text__` |
| **Italic** | `*text*` or `_text_` |
| **Underline** | `++text++` |
| **Strikethrough** | `~~text~~` (a single `~` on both sides works too) |

Styles can be combined, like `***bold and italic***`.

Single underscores inside words stay normal underscores, so `my_cool_layout` doesn't turn italic. Names like `C++` also stay as they are.

> [!TIP]
> In the text editor, select some text and press `Ctrl + B`, `Ctrl + I` or `Ctrl + U` (`Cmd` on macOS) to make it bold, italic or underlined. See [Formatting Shortcuts](/text-in-menus#formatting-shortcuts).

## Text Color (HEX)

Put `%<HEX color>%` in front of the text and `%#%` behind it:

```
%#77fc03%This text is green!%#%
```

The HEX color needs to start with `#`. You can also use color names:

```
%#red%This text is red!%#%
```

Supported names: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` and `transparent`.

## Fonts

To show text in another font, put `%!!<font name>%` in front of it and `%!!%` behind it. The font can come from Minecraft or a resource pack.

```
%!!uniform%This text uses the uniform font%!!%
```

## Text Alignment

Text is left-aligned by default. To center lines or align them right, put the alignment code on its own line before and after them:

- `^^^` centers the lines.
- `|||` aligns them right.

```
This line is left-aligned.

^^^
This line is centered.
This one too.
^^^

|||
This line is right-aligned.
|||
```

> [!TIP]
> In the text editor, `Ctrl + L`, `Ctrl + E` and `Ctrl + R` (`Cmd` on macOS) align the selected lines left, centered or right for you.

## Headlines

Start a line with `# ` (biggest), `## ` (big) or `### ` (small):

```
# Welcome!
## News
### Small Headline
```

## Lists

<img width="460" alt="Markdown lists" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_lists.png?raw=true">

### Bullet Lists

Start a line with `- `. Add two spaces in front of it for every level of nesting:

```
- First item
- Second item
  - Nested item
    - Even deeper
```

### Numbered Lists

Start a line with a number and a dot or a bracket:

```
1. Open the menu bar
2. Click on Customization
3) This works too
```

### Patch Note Markers

Lines can also start with `+`, `-`, `~` or `*`. Each of them gets its own marker, which is perfect for patch notes and changelogs:

```
+ Added a new main menu
- Removed the old logo
~ Changed the button colors
* Fixed a crash on startup
```

| Marker | Meaning |
|---|---|
| `+` | Something got added |
| `-` | Something got removed |
| `~` | Something got changed |
| `*` | Something worth highlighting |

A `-` item only gets the "removed" marker when its list also has a `+` item. Otherwise, it's a normal bullet list item. You can change that with **Markdown -> Lists -> Extra Markers (+ - ~ \*) -> - Marker Used**.

> [!NOTE]
> New Text and Tooltip elements have numbered lists, patch note markers and [callouts](#callouts) turned on. Elements from older layouts have them off, so their text doesn't suddenly change. Turn them on in the element's **Markdown** menu: **Lists -> Numbered Lists**, **Lists -> Extra Markers (+ - ~ \*)** and **Callouts**.

## Quotes

Start a line with `> ` to make it a quote. The quote goes on until the next empty line:

```
> This is a quote.
And this line belongs to it too.

This line is normal text again.
```

Lines inside a quote can start with `>` too, and a line with nothing but `>` adds an empty line to the quote:

```
> First paragraph of the quote.
>
> Second paragraph of the quote.
```

## Callouts

Callouts are colored boxes with an icon and a label, great for tips and warnings. Write a quote whose first line is the callout type:

```
> [!WARNING]
> Don't forget to save your layout!
```

<img width="640" alt="Markdown callouts" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_callouts.png?raw=true">

There are five types: `[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]` and `[!CAUTION]`.

## Hyperlinks

Wrap the text in `[ ]` and put the link behind it in `( )`:

```
[Visit our website](https://example.com)
```

Links can contain round brackets, like `https://en.wikipedia.org/wiki/Minecraft_(video_game)`. To show square brackets in the link text, put a `\` in front of them: `[Click \[here\]](https://example.com)`.

## Click and Hover Events

Text can also trigger [listeners](/listeners) instead of opening a website. Use the `click:` or `hover:` prefix with an ID of your choice:

```
[some clickable text](click:unique_text_click_event_id)
[some hoverable text](hover:unique_text_hover_event_id)
```

React to them with the [**On Markdown Text Clicked**](/listeners#on-markdown-text-clicked) and [**On Markdown Text Hovered**](/listeners#on-markdown-text-hovered) listeners. Both give you the ID as `$$text_event_id`.

## Images

Put an image on its own line with `![](` + the image source + `)`:

```
![](https://example.com/image.png)
```

The source can be a web URL, a local file like `/config/fancymenu/assets/image.png` or a resource pack image. See [Resources](/resources) for all source types.

Text between the square brackets becomes the caption of the image:

```
![My cool screenshot](/config/fancymenu/assets/screenshot.png)
```

Captions show below the image if the element's **Markdown -> Images -> Caption** option is on.

To make an image clickable, wrap it in a link:

```
[![](https://example.com/image.png)](https://example.com)
```

## Tables

Separate cells with `|`. The first row is the header, and the second row has `---` for every column:

```
| Item | Price |
|:---|---:|
| Diamond Sword | 10 |
| Golden Apple | 5 |
```

Colons in the second row align the column: `:---` left, `:---:` centered and `---:` right. To show a `|` inside a cell, write `\|`.

<img width="640" alt="Markdown table and code" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_table_code.png?raw=true">

## Separators

A line with nothing but `---` draws a separator across the text.

## Code

Code shows text as it is, without formatting it.

- **Inline code:** wrap a part of a line in `` ` ``, like `` `/spawn` ``.
- **Code blocks:** put a line with `` ``` `` before and after the lines. Code blocks don't wrap their lines.

````
```
/give @p minecraft:diamond 64
```
````

You can write a language name behind the first `` ``` ``, like `` ```json ``. FancyMenu accepts it, but it doesn't change how the code looks.

[Placeholders](/placeholders) still get replaced inside code.

## Plain Text

Plain text shows formatting characters as they are, but without the look of code. Wrap a part of a line in `;;`:

```
This shows ;;**stars**;; instead of bold text.
```

To do that for whole lines, put `;;;` on its own line before and after them:

```
;;;
**Not bold**, _not italic_.
;;;
```

## Escaping Characters

To show a formatting character as normal text, put a `\` in front of it. For example, `\*not italic\*` shows `*not italic*`.

This works for `\` `` ` `` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `.` `!` `|` `>` `~` and `^`.

# Minecraft Text Formatting

Minecraft formatting codes work in most text fields of FancyMenu. Use `&` instead of Minecraft's `§`. For example, `&cWarning` shows red text and `&l` makes text bold. `&r` resets the formatting.

See the [Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes) for all codes.

Formatting codes also work in Markdown text, except inside code and plain text. For styles like bold and italic, Markdown is usually easier to read, but codes are handy for quick colors.

# Minecraft Text Components (Raw Component System)

Minecraft text components are formatted text written as JSON. They work for **single-line** text like **button and slider labels**, but not in Text elements.

To use one, set nothing but the component as the label:

```
{"text":"Button Label Text","font":"uniform"}
```

This shows `Button Label Text` in the `uniform` font. You can use [placeholders](/placeholders) in the `text` value.

To learn more, see the Minecraft Wiki pages about the [text component format](https://minecraft.wiki/w/Raw_JSON_text_format) and [fonts](https://minecraft.wiki/w/Resource_pack#Fonts).
