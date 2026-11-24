---
title: Layout Editor
description: How to open the layout editor, select, move and resize elements, save your layout, and all shortcuts of the editor.
---

# Layout Editor

The layout editor is where you build [layouts](/home#your-first-layout): you add elements, move and resize them, and change the menu around them. It shows the menu like players see it, so you see right away how it looks.

<img width="800" alt="Moving, widening and nudging a title, then selecting two buttons, copying and pasting them, dragging the copies down and undoing it" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_basics.gif?raw=true">

# Opening the Editor

1. Open the menu you want to change, like the title screen.
2. Click **menu bar -> Customization -> Current Screen Customization**, so it shows **Enabled**.
3. Click **menu bar -> Customization -> Layouts -> New -> For Current Screen**.

- **For All Screens [Universal]** makes a [Universal Layout](/universal-layouts), which shows in every menu.
- The layouts you already have are listed in **Layouts** too. Hover one and click **Edit Layout**.
- `Ctrl + Alt + L` opens the layout you edited last.

# The Editor at a Glance

<img width="800" alt="The layout editor with a selected Join Server button, the menu bar at the top and the Layers widget on the right" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Right-click the background for the settings of the whole layout, and to add elements with **New Element**.
- Right-click an element for its settings. See [Elements](/elements#settings-of-all-elements).
- **Layers** lists all elements of the layout. Drag them to change which one is on top, hide them while you edit, or put them in groups. See [Layers and Groups](/layers-and-groups). **Window -> Editor Widgets** shows and hides it.
- The menu bar at the top:

| Menu | What's in it |
|---|---|
| **Layout** | **New**, **Open**, **Save**, **Save As**, **Export Layout for AI**, **Layout Properties** (the same as the right-click menu of the background), **Settings** and **Close Editor** |
| **Edit** | **Undo**, **Redo**, **Copy**, **Paste** and **Select All** |
| **Element** | **New** to add elements, and **Deleted Vanilla Elements** to bring back [vanilla elements you deleted](/deleted-vanilla-elements) |
| **Window** | **Editor Widgets**, the [grid](#grid-and-anchor-overlay), the [anchor overlay](#grid-and-anchor-overlay), **Element Rotation Controls** and **Element Tilt Controls** |

## Layout Settings

The right-click menu of the background has everything about the layout itself, like:

- [**Menu Backgrounds**](/menu-backgrounds) and [**Decoration Overlays**](/decoration-overlays)
- **Header/Footer Customizations** for [scrollable screens](/customizing-scrollable-screens)
- **Layout Index [Multi-Layout Ordering]** and **Random Mode** for [several layouts in one menu](/randomize-layouts)
- **Loading Requirements [Layout-Wide]**, see [Requirements](/conditions#layout-wide-requirements)
- **Edit 'Open Screen' Action Script** and **Edit 'Close Screen' Action Script**, see [Action Scripts](/action-scripts)
- **Universal Layout Options**, in [Universal Layouts](/universal-layouts) only

# Working With Elements

## Selecting

- Click an element to select it. Click the background to unselect everything.
- Drag over the background to select all elements in the rectangle.
- `Ctrl` + click adds an element to the selection, or takes a selected one out of it.
- `Ctrl + A` selects all elements.

Elements you hid in **Layers** can't get selected.

## Moving

- Drag an element to move it. To move several selected elements, hold `Ctrl` while you start dragging them. Without `Ctrl`, the click selects only the element you clicked.
- The arrow keys move the selected elements by one pixel.
- While you drag, the anchor points show. Hold the element over another anchor point or element to anchor it there. See [Positioning Elements](/positioning-elements).
- Drop an element on a [Scrollable Area](/scrollable-areas) to put it inside.

## Resizing

Drag an edge or a corner of a selected element. Hold `Shift` to keep its aspect ratio.

Resizing only works while one element is selected.

## Rotating and Tilting

Selected elements that support it show controls for [rotating](/rotating-elements) and [tilting](/tilting-elements) them. Hold `Shift` while you drag them to snap to steps: 45° for rotation, 15° for tilt.

**Window -> Element Rotation Controls** and **Element Tilt Controls** hide the controls.

## Copying, Pasting and Deleting

- `Ctrl + C` copies the selected elements, `Ctrl + V` pastes them. The copies land on top of the originals and get selected, so you can drag them away right after.
- You can paste into another layout too, until the game closes.
- `Delete` deletes the selected elements. Vanilla elements only get hidden: bring them back with **Element -> Deleted Vanilla Elements**.
- Deleting a Scrollable Area asks if its content should get deleted too, or stay in the layout.

## Undo and Redo

`Ctrl + Z` takes back the last change, `Ctrl + Y` does it again. Both are in the **Edit** menu too.

# Grid and Anchor Overlay

The **Window** menu has the settings of the editor's helpers:

- **Grid** shows grid lines, `Ctrl + G` turns them on and off. **Grid Size** sets the space between them.
- **Grid Snapping** makes a dragged element snap to the grid lines, while the grid shows. **Grid Snapping Strength** sets how strongly it snaps.
- **Anchor Overlay Visibility** sets when the anchor points show:
  - **Show On Element Dragging**: while you drag elements.
  - **Always Visible**: all the time.
  - **Show On Key Press (Key "O")**: while you hold `O`.
  - **Disabled**: never.
- **Anchor Area Hovering** and **Anchor Element Hovering** set if holding an element over an anchor point or another element changes its anchor.

# Saving and Closing

- `Ctrl + S` or **Layout -> Save** saves the layout. The first time, FancyMenu asks for a file name.
- **Layout -> Save As** saves the layout as a new file.
- While there are changes that aren't saved, the menu bar shows **\* Unsaved Changes! \***.
- The X at the right of the menu bar, or **Layout -> Close Editor**, closes the editor. With unsaved changes, it asks you first.

# Shortcuts

On macOS, use `Cmd` instead of `Ctrl`.

| Shortcut | What it does |
|---|---|
| `Ctrl + S` | Save |
| `Ctrl + Z` | Undo |
| `Ctrl + Y` | Redo |
| `Ctrl + C` | Copy the selected elements |
| `Ctrl + V` | Paste |
| `Ctrl + A` | Select all elements |
| `Delete` | Delete the selected elements |
| Arrow keys | Move the selected elements by one pixel |
| `Ctrl` + click | Add an element to the selection, or take it out |
| `Ctrl` + drag | Move several selected elements |
| `Shift` + resize | Keep the aspect ratio |
| `Shift` + rotate or tilt | Snap to steps |
| `Ctrl + G` | Turn the grid on and off |
| Hold `O` | Show the anchor points, with **Show On Key Press (Key "O")** |

## Shortcuts in All Menus

These work in every menu, also outside of the editor, but not while Modpack Mode is on:

| Shortcut | What it does |
|---|---|
| `Ctrl + Alt + C` | Show or hide FancyMenu's menu bar |
| `Ctrl + Alt + L` | Open the layout you edited last |
| `Ctrl + Alt + R` | Reload FancyMenu |
| `Ctrl + Alt + D` | Show or hide the **Debug Overlay**, which shows the [identifier](/screen-identifiers) of the menu and more |

> [!TIP]
> The text editor has its own shortcuts, see [Text in Menus](/text-in-menus#the-text-editor). Windows like [Action Scripts](/action-scripts#shortcuts) list theirs on their pages.
