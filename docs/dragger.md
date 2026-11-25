---
title: Dragger
description: Let players grab a panel, a note or anything else in your menus and move it where they like.
---

# Dragger

A Dragger is an invisible area that players can grab with the mouse and move around. Everything anchored to it moves along, like a panel with patch notes or a note with server rules. The menu remembers where players left it, even after a restart.

<img width="800" alt="A player grabs a Patch Notes banner by the leather grip of its rod and pulls it from the left to the right side of the title screen, opens Options, comes back, and the banner is still on the right" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_hero.gif?raw=true">

Players can only drag it outside the layout editor. In the editor, the Dragger is a red box with its name (**In-Editor Color** in its right-click menu changes the red), and everything stays where the layout puts it.

# Making Something Movable

<img width="800" alt="Adding a Dragger through New Element, resizing it to the size of the banner, dragging it onto the banner and moving it two layers down, then dragging the banner off the Dragger and back and holding it there until the bar is full, which anchors the banner to it" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_setup.gif?raw=true">

1. Build what should move, like a banner image with a Text element on it.
2. Right-click a free spot in the layout editor and click **New Element -> Dragger**.
3. Make the Dragger as big as the banner and move it onto the banner.
4. Right-click the Dragger and click **Move One Layer Down** until it's below everything of the banner. Selected elements always show on top, so click a free spot to see the change.
5. Anchor the banner to the Dragger: drag the banner a bit off the Dragger and back, and hold it there until the bar is full. More in [Positioning Elements](/positioning-elements#anchoring-elements-to-other-elements).
6. Save the layout and try it outside the editor.

Elements anchored to something that moves move along too. In the GIF, the text is anchored to the banner, so the banner is the only element that needs the Dragger.

To anchor several elements at once, right-click the Dragger and click **Copy Element ID** before step 4. Then select the elements, right-click one of them, click **Anchor Point -> Other Element** and paste the ID.

> [!TIP]
> Players can't see the Dragger, so show them where to grab, like with a title bar or a grip.

# Saving the Position

**Save User Drag Offset** in the Dragger's right-click menu is enabled for new Draggers.

- **Enabled**: the position gets saved when the player lets go. It stays after closing the screen and restarting the game.
- **Disabled**: everything goes back to its place in the layout when the screen opens again, and when the window size or the GUI scale changes.

Turning it off in the editor also forgets the position players saved for this Dragger.

Positions get saved for each Dragger by its [element ID](/element-identifiers), in `fancymenu_data/dragger_metas.json`. That folder isn't part of [profiles](/profiles), so the positions you dragged while testing don't end up in the `config/fancymenu/` folder of your modpack. See [Data Storage Locations](/data-storage-locations#instance-data).

To put all Draggers back to their place in the layout, delete `dragger_metas.json` while the game is closed.

# What Players Can Grab

Players grab the Dragger where nothing on top of it takes the click:

- Images on top of it let the click through, so players grab the banner itself.
- Buttons and the words of Text elements on top of it take the click, so they keep working on a movable panel.
- Where the Dragger is on top of a button, the button gets no clicks. That's why the Dragger goes below the banner in the steps above.

While its [requirements](/element-visibility#showing-elements-only-sometimes) hide the Dragger, players can't grab it.

# Staying on the Screen

**Stay on Screen** is on for new elements. It stops the Dragger at the edges of the screen, so players can't drag it out of sight. With the Dragger as big as the whole banner, the banner stops at the edge with it.

A Dragger that only covers a part, like a title bar, works too. But the elements anchored to it have their own **Stay on Screen**: at the edge, they stop on their own while the Dragger moves on, and the panel falls apart. Turn off **Stay on Screen** for them, so they move on with the Dragger and only the title bar stays on the screen.
