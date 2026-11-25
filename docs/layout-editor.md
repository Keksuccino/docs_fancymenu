---
title: Layout Editor
description: How to open the layout editor, select, move and resize elements, order them with layers and groups, save your layout, and all shortcuts of the editor.
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
- In any menu, `Ctrl + Alt + L` opens the layout you edited last. See [the menu bar shortcuts](/home#menu-bar-shortcuts).

# The Editor at a Glance

<img width="800" alt="The layout editor with a selected Join Server button, the menu bar at the top and the Layers widget on the right" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Right-click the background for the settings of the whole layout, and to add elements with **New Element**.
- Right-click an element for its settings. See [Elements](/elements#settings-of-all-elements).
- **Layers** on the right lists all elements of the layout. See [Layers and Groups](#layers-and-groups).
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
- **Custom Screen Title** for the text at the top of some menus, like "Options". [Placeholders](/placeholders) work in it.
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

Clicks, rectangles and `Ctrl + A` skip elements you [hid in Layers](#hiding-and-renaming).

## Moving

- Drag an element to move it. To move several selected elements, hold `Ctrl` while you start dragging them. Without `Ctrl`, the click selects only the element you clicked.
- The arrow keys move the selected elements by one pixel.
- While you drag, the anchor points show. Hold the element over another anchor point or element to anchor it there. See [Positioning Elements](/positioning-elements).
- Drop an element on a [Scrollable Area](/scrollable-areas) to put it inside.

## Resizing

Drag an edge or a corner of a selected element. Hold `Shift` to keep its aspect ratio.

Resizing only works while one element is selected.

## Rotating and Tilting

Selected elements that support it show controls for [rotating and tilting](/rotating-elements) them. Hold `Shift` while you drag them to snap to steps: 45° for rotation, 15° for tilt.

**Window -> Element Rotation Controls** and **Element Tilt Controls** hide the controls.

## Copying, Pasting and Deleting

- `Ctrl + C` copies the selected elements, `Ctrl + V` pastes them. The copies land on top of the originals and get selected, so you can drag them away right after.
- You can paste into another layout too, until the game closes.
- `Delete` deletes the selected elements. Vanilla elements only get hidden: bring them back with **Element -> Deleted Vanilla Elements**.
- Deleting a Scrollable Area asks if its content should get deleted too, or stay in the layout.

## Undo and Redo

`Ctrl + Z` takes back the last change, `Ctrl + Y` does it again. Both are in the **Edit** menu too.

## Invisible Elements

Players can't see [Audio](/elements#audio), [Dragger](/dragger), [Element Animator](/element-animator), [Music Controller](/elements#music-controller) and [Ticker](/elements#ticker) elements. In the editor, they show as colored boxes with their name, so you can find, move and resize them.

- **In-Editor Color** in their right-click menu changes the color of the box, like to tell several Tickers apart. Colors are `#RRGGBB`, or `#RRGGBBAA` with transparency: a see-through color like `#E30E2366` shows what's behind the box.
- The name in the box is the element's layer name, see [Hiding and Renaming](#hiding-and-renaming).

Players never see the box, its color or its name.

# Layers and Groups

**Layers** lists all elements of the layout, the topmost first: an element shows in front of everything below it in the list. **Window -> Editor Widgets -> Layers** shows and hides it.

<img width="800" alt="Dragging the News Background layer below News Text, so the patch notes show after unselecting it, then adding a group, putting both layers into it, hiding and showing the group with its eye and folding it up" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_layers.gif?raw=true">

## Changing the Order

- Click a layer to select its element, then drag it up or down. A line shows where it lands. All selected layers move together.
- Or right-click an element or its layer and click **Move One Layer Up** or **Move One Layer Down**.

In the editor, selected elements always show in front of the others. Unselect them to see the real order.

In some Minecraft versions, [Player Entity](/elements#player-entity) and [Item](/elements#item) elements show in front of everything, no matter their layer. See [Known Issues](/known-issues#1-player-entity--item-elements-are-always-in-front-of-everything).

## Vanilla Elements

The **Vanilla Elements** row stands for all elements of the menu itself, like its buttons. Their order can't change, but the button on the right of the row puts all your elements behind or in front of them. It does the same as **Custom Elements Behind Vanilla** in the right-click menu of the background.

## Hiding and Renaming

- The eye of a layer hides its element in the editor, so it's out of your way while you work on the others. Click it again to show the element.
- Hidden elements can't get clicked, moved, copied or deleted. Players still see them, they only hide in the editor. The layout remembers which ones you hid.
- Right-click a layer and click **Rename Layer** to give it a name that's easier to find, like `News Panel`. It's the same as the element's **In-Editor Display Name**, and players don't see it.

## Groups

Groups keep layers that belong together under one name, like all parts of a news panel. They only sort the list: the elements show and work like before.

- Right-click inside Layers and click **Add Group**. The group shows up below the layers.
- Drag layers onto the group to put them into it. Drag them out of it to take them out.
- Click a group to select all its elements. Drag it to move all of them up or down at once.
- The arrow of a group folds its layers up or out, and its eye hides or shows all of them.
- Right-click a group to rename it, move it one layer up or down, or delete it. **Delete Group** keeps its elements.

**Move One Layer Up** and **Move One Layer Down** keep an element inside its group. To take it out, drag its layer out of the group.

The layout saves its groups and which ones are folded up.

## Scrollable Areas

The elements in a [Scrollable Area](/scrollable-areas) show up below the area's layer, indented.

- Drag a layer onto the lower half of an area's layer to put the element into the area. Drag it out between other layers to take it out. It stays where it is on the screen.
- The arrow of an area's layer folds its elements up or out.
- Elements in an area belong to no group. They move with the area.

# Grid and Anchor Overlay

The **Window** menu has the settings of the editor's helpers:

- **Grid** shows grid lines, `Ctrl + G` turns them on and off. **Grid Size** sets the space between them.
- **Grid Snapping** makes a dragged element snap to the grid lines, while the grid shows. **Grid Snapping Strength** sets how strongly it snaps.
- **Anchor Overlay Visibility** sets when the anchor points show:
  - **Show On Element Dragging**: while you drag elements.
  - **Always Visible**: all the time.
  - **Show On Key Press (Key "O")**: while you hold `O`.
  - **Disabled**: never.
- **Anchor Area Hovering** sets if holding an element over an anchor point changes its anchor. **Anchor Element Hovering** adds other elements to the anchor points, so it only works while **Anchor Area Hovering** is on too.

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

> [!TIP]
> The text editor has its own shortcuts, see [Text in Menus](/text-in-menus#the-text-editor). Windows like [Action Scripts](/action-scripts#shortcuts) list theirs on their pages.
