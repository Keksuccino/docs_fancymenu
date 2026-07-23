---
title: Dragger
description: Let users move anchored elements outside the editor.
---
# Dragger

A Dragger is an invisible element that users can move with the mouse outside the layout editor. You can anchor other elements to it, so they get moved with the Dragger.

1. Add a [**Dragger** element](./elements#dragger).
2. Anchor the elements that should move to the Dragger.
3. Size and position the Dragger over the visible area users should grab.

Enable **Save User Drag Offset** to keep the dragged position across screen openings and game restarts. Disable it when the offset should reset.

The Dragger is visible only in the editor. Use an anchored [Image](./elements#image), [Shape](./elements#rectangle-shape), or other element as its visible body.
