---
title: Export for AI
description: Turn parts of your FancyMenu setup into text for AI assistants like Alice, so they can help you faster.
---
# Export for AI

**Export for AI** turns a part of your FancyMenu setup into text that's made for AI assistants, like Alice, the helper bot on the [FancyMenu Discord](https://discord.gg/rhayah27GC). Paste it into your chat, and the AI sees exactly how things are set up, instead of guessing.

<img width="800" alt="A support chat where Alice asks for an export, finds the problem in it and helps the player fix their button" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/export_for_ai_chat.gif?raw=true">

# Why It Exists

A screenshot shows how something looks, but not how it's set up. Typing out an action script or a requirement by hand takes long, and the one detail that matters often gets lost on the way.

An export has everything the AI needs:

- Every setting, action, requirement and value of what you export.
- Your FancyMenu, Minecraft, mod loader, Java and system versions.
- Short explanations of how FancyMenu works, so the AI reads it right.

Exports are always in English, whatever language you play in. Your account name in file paths gets replaced with `<user>`, so you can share exports in public chats.

# When to Use It

- Something doesn't work like it should, like a button that does nothing or an element that never shows up.
- FancyMenu shows you an error or a warning.
- You want help building something, like an action script, a requirement or a whole menu.
- You want to know what's possible in your game. **Everything FancyMenu Can Do** lists all elements, backgrounds, actions, requirements, placeholders and listeners you have, including the ones of add-ons.

Export only what your question is about, like the one button that doesn't work. Smaller exports keep the AI focused. Then tell it what you expected and what happened instead.

# How to Export

Every place below opens a small menu:

- **Copy to Clipboard** copies the export, so you can paste it into your chat with `Ctrl + V` (`Cmd + V` on macOS).
- **Save as File** saves it as Markdown file in `<game-directory>/fancymenu_data/ai_exports/` and opens that folder, so you can drag the file into your chat. Use this for big exports that don't fit into a chat message.

Exports from the layout editor and from the listener and scheduler windows include changes you didn't save yet.

# Where You Can Export

## Menu Bar

| What gets exported | Where to find it |
|---|---|
| The current screen, with its widgets and what FancyMenu does on it | **menu bar -> Customization -> Export Current Screen for AI** |
| A layout | **menu bar -> Customization -> Layouts**, pick the layout, then **Export Layout for AI** |
| Your game, hardware and mods, and what FancyMenu can use, like video and browser support | **menu bar -> Help -> Export for AI -> System Info** |
| All settings of FancyMenu, including the [global customizations](/global-customizations) | **menu bar -> Help -> Export for AI -> FancyMenu Settings** |
| All [variables](/variables) | **menu bar -> Help -> Export for AI -> All Variables** |
| All [listeners](/listeners) | **menu bar -> Help -> Export for AI -> All Listeners** |
| All [schedulers](/schedulers) | **menu bar -> Help -> Export for AI -> All Schedulers** |
| All [Custom GUIs](/custom-guis) | **menu bar -> Help -> Export for AI -> Custom GUIs** |
| All [profiles](/profiles) | **menu bar -> Help -> Export for AI -> Profiles** |
| All elements, backgrounds, actions, requirements, placeholders and listeners of your game | **menu bar -> Help -> Export for AI -> Everything FancyMenu Can Do** |

## Layout Editor

| What gets exported | Where to find it |
|---|---|
| The layout you're editing | **Layout -> Export Layout for AI** in the editor's menu bar |
| Another layout of the screen | **Layout -> Open** in the editor's menu bar, pick the layout, then **Export Layout for AI** |
| One element | Right-click the element, then **Export for AI** |
| All selected elements | **Edit -> Export Selected Elements for AI** in the editor's menu bar |
| A [menu background](/menu-backgrounds) | Right-click the editor background, then **Menu Backgrounds**, pick the background, then **Export for AI** |
| A [decoration overlay](/decoration-overlays) | Right-click the editor background, then **Decoration Overlays**, pick the overlay, then **Export for AI** |

## Editors and Windows

| What gets exported | Where to find it |
|---|---|
| An [action script](/action-scripts) | Right-click in the action script editor, then **Export Action Script for AI** |
| [Requirements](/conditions) | Right-click in the **Manage Requirements** window, then **Export Requirements for AI** |
| A text, like the content of a Text element | Right-click in the text editor, then **Export Text for AI** |
| One variable or all variables | Open **menu bar -> Customization -> Manage Variables**, right-click, then **Export Variable for AI** or **Export All Variables for AI** |
| One listener or all listeners | Open **menu bar -> Customization -> Manage Listeners**, click **Export for AI**, then **Selected Listener** or **All Listeners** |
| One scheduler or all schedulers | Open **menu bar -> Customization -> Manage Schedulers**, click **Export for AI**, then **Selected Scheduler** or **All Schedulers** |

## Errors and Warnings

When FancyMenu shows an error or a warning, click **Export for AI** next to **OK** to export the message.

## Servers

The [FMData](/fm-data) setup of a server, with its server listeners and welcome data, can be exported with a command. It needs permission level 2, like all `/fmdata` commands.

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

- `copy` sends you a chat message. Click it to copy the export. In the server console, it shows the whole export instead.
- `file` saves the export on the server, in `fancymenu_data/ai_exports/`. Use it when the export is too big for the chat.
