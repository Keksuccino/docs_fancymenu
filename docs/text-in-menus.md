---
title: Text in Menus
description: How to show text in menus with Text and Tooltip elements, and how to style and scroll it.
---
# Text in Menus

FancyMenu has two elements for text:

- **Text** shows text right in your menu, from a single line to long, scrollable pages like changelogs, rules or news.
- **Tooltip** shows a text box at a fixed spot or next to the mouse, for example while a button is hovered.

Both support [Markdown](/text-formatting) and [placeholders](/placeholders), and they share the same look and style settings.

<img width="800" alt="Editing a Text element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/text_editor_showcase.gif?raw=true">

> [!TIP]
> This page is about the elements and their settings. For everything you can write in your text, like headlines, lists, links and colors, see [Text Formatting](/text-formatting).

# Adding Text

1. Open a layout in the layout editor.
2. Right-click the editor background and select **New Element -> Text**.
3. Right-click the new element and select **Text Content**.
4. Write your text and click **Done**.

# Text Content

## Source Mode

Right-click the element and set **Source Mode**:

- **Direct**: You type the text yourself in the text editor.
- **Resource**: The text comes from a text file. Click **Text Source** to choose a local file from `<game-directory>/config/fancymenu/assets/`, a web URL or a resource pack file. See [Resources](/resources).

Web sources are great for things like a changelog or news that are always up to date, without updating your modpack.

FancyMenu remembers the text of files and web sources until the game closes. To load it again, reload FancyMenu with **menu bar -> Customization -> Reload FancyMenu**.

## Dynamic Text

Text can show live values with [placeholders](/placeholders), for example `Welcome, {"placeholder":"playername"}!`. It can also show the values of [variables](/variables). The text updates by itself when these values change.

## The Text Editor

Clicking **Text Content** opens the text editor. Click **Placeholders** in its top-right corner to browse all placeholders and add them to your text.

### Formatting Shortcuts

The text editor of Text and Tooltip elements has shortcuts for common formatting. On macOS, use `Cmd` instead of `Ctrl`.

| Shortcut | What it does |
|---|---|
| `Ctrl + B` | Bold |
| `Ctrl + I` | Italic |
| `Ctrl + U` | Underline |
| `Ctrl + L` | Align left |
| `Ctrl + E` | Align center |
| `Ctrl + R` | Align right |

- Select text first to format it. Press the same shortcut again to remove the format.
- Without a selection, the shortcut adds the formatting characters and puts the cursor between them, so you can just keep typing.
- The alignment shortcuts work on the selected lines, or on the line of the cursor. `Ctrl + E` or `Ctrl + R` on lines that already have that alignment aligns them left again.
- Right-click in the editor and open **Formatting** to see all of these in a menu.

See [Shortcuts](/shortcuts#text-editor) for all other shortcuts of the text editor.

# Looks and Styles

Right-click the element and open **Markdown** to change how the text looks.

## Looks

A **Look** sets every style option of the text in one go:

- **Pixel**: Pixel art made for the Minecraft font, with warm colors, golden details and hand-drawn markers.
- **Classic**: The classic FancyMenu look, with white text, gray boxes and gray lines.
- **Neutral**: A clean look in the colors of your current FancyMenu UI theme. The colors get saved with the element, so they stay the same when you switch themes later.

<img width="800" alt="The three Markdown looks" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_looks.png?raw=true">

New elements start with the Pixel look. Elements from older layouts keep the Classic look they always had.

> [!NOTE]
> Picking a look replaces your own style changes. Changed your mind? Just undo it with `Ctrl + Z`.

## Style Options

After picking a look, you can still fine-tune every part of it. The **Markdown** menu has options for the **Text**, **Headlines**, **Lists**, **Links**, **Code**, **Quotes**, **Callouts**, **Tables**, **Images** and **Separators**. Hover an option to see what it does.

**Markdown -> Text** holds the basics, like the text color, text shadow, line spacing and the padding between the text and the edges of the element.

## Turning Markdown Off

If you don't need Markdown at all, turn off **Markdown -> Markdown Parser**. The text then shows exactly as you typed it, which is also a bit faster for very long texts.

## Other Text Settings

Right-click the element to find these too:

- **Text Scale** makes the text bigger or smaller.
- **Case Mode** shows the text normally, in all upper-case or in all lower-case.
- **Auto Line Wrapping** wraps lines that are too long for the element. When it's off, long lines just keep going.
- **Remove HTML Line Breaks** removes HTML line breaks (`<br>`) from the text, which is handy for text from websites.

# Background

Text elements can draw a panel behind their text. Open **Background** in the element's right-click menu:

- **Show Background** turns the panel on or off. New Text elements have it on.
- By default, it's a built-in dark panel. You can use your own texture instead, with [nine-slicing](/nine-slicing-and-tiling) and tiling to keep its edges in shape.
- **Padding** sets how far the background reaches beyond the text.
- **Reach Behind Scroll Bars** lets the background cover the scroll bars too. When it's off, the scroll bars sit right next to it.

Tooltips have their own **Background** menu, where you can set a texture and its nine-slicing.

# Scrolling

A Text element scrolls when its text doesn't fit into it. Use the mouse wheel to scroll. Hold `Shift` to scroll sideways.

**Scroll Direction** sets if the text scrolls **Vertical**, **Horizontal** or **Both**. Where it doesn't scroll, everything that doesn't fit gets cut off.

## Scrolling Settings

Open **Scrolling** in the element's right-click menu:

| Setting | What it does |
|---|---|
| **Let Players Scroll** | If players can scroll the text themselves. When it's off, the text only scrolls on its own and through actions. |
| **Scroll Speed** | How far one step of the mouse wheel scrolls. |
| **Smooth Scrolling** | Lets the text glide instead of jumping. |
| **Drag to Scroll** | Lets players grab the text with the mouse and drag it, like on a touch screen. |
| **Scroll with Keyboard** | While the mouse is over the text, `Page Up` and `Page Down` scroll a page, and `Home` and `End` jump to the start and the end. |
| **Snap** | Where the text comes to rest: anywhere (**Off**), with a whole line at the top (**To Lines**), with a headline at the top (**To Headlines**) or a whole page at a time (**To Pages**). |
| **Start At** | If the text starts at its **Start** or its **End**. The end is handy for things like logs, where the newest stuff is last. |
| **Reset When Screen Opens** | Puts the text back to its start every time the screen opens. When it's off, the text remembers where it was scrolled to until the game closes. |

## Auto-Scroll

Open **Auto-Scroll** to let the text scroll on its own, slowly, like credits or a news ticker:

- **Scroll on Its Own** turns it on.
- **Speed [Pixels per Second]** sets how fast it scrolls.
- **Start Over at the End** starts again from the top once the end is reached.
- **Pause While Hovered** stops scrolling while the mouse is over the text, so players can read in peace.

## Scroll Bars

Open **Scroll Bars** to change the bars:

- **Show** sets when the bars show up: **Always**, only **While Scrolling**, or **Never**. With **Never**, the mouse wheel still scrolls.
- **Thickness** sets how thick the bars are.
- **Vertical Bar on the Left** and **Horizontal Bar on Top** move the bars to the other side.
- **Scroll Grabber Style** picks the look of the grabbers: **Theme Bar** (in the colors of your FancyMenu UI theme) or **Pixel Handle** (pixel art that goes great with the Pixel look).
- **Scroll Grabber Textures** and **Scroll Grabber Color [HEX]** replace the grabbers with your own textures or colors.
- **Scroll Bar Backgrounds** add textures behind the grabbers, along the way they move.

## Scrolling With Actions

You can also control and watch scrolling from other parts of FancyMenu:

- The **Scroll an Element** [action](/action-scripts) scrolls a Text element to its start, its end, a position, a line number or the first line that contains a text.
- The **Element Scroll Position**, **Element Scroll Percent** and **Element Scroll Content Size** [placeholders](/placeholders) tell you how far the text is scrolled and how big it is.
- The **Is Element Scrolled to End** [requirement](/conditions) checks if the text got scrolled to its end, for example to only enable an "Accept" button after the rules got read.
- The **On Element Scrolled**, **On Element Scrolled to Start** and **On Element Scrolled to End** [listeners](/listeners) run actions while the text scrolls.

All of these need the [element identifier](/element-identifiers) of the Text element.

# Clicking Through Text Elements

Text elements react to the mouse, so their links and scroll bars work. That also means they catch clicks, so buttons behind or in front of a Text element might not get them.

If that's a problem, right-click the Text element and turn off **Interactable**. The text then can't be scrolled and its links can't be clicked anymore.

# Tooltips

Tooltip elements work like Text elements without scrolling:

- Their text, look and style settings are the same as for Text elements.
- **Follow Mouse** makes the tooltip follow the mouse.
- Use [requirements](/conditions) to decide when the tooltip shows up, like the [**Is Element Hovered**](/conditions#is-element-hovered) requirement to show it while a button is hovered.
