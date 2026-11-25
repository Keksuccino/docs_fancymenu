---
title: Nahtloses Laden von Welten
description: Verwende eine aktuelle Weltansicht als nächsten Ladehintergrund.
sourceBlobSha: 2b8e960b11ea70fca33b317a7c14815ce5844e13
---

# Nahtloses Laden von Welten

Beim nahtlosen Laden von Welten wird eine aktuelle Ansicht einer Welt oder eines Servers als Hintergrund für den nächsten Ladebildschirm verwendet.

Aktiviere die Funktion unter [**Anpassung -> Globale Anpassungen**](/global-customizations) -> **Nahtloses Laden von Welten**.

# Funktionsweise

- FancyMenu nimmt regelmäßig das aktuelle Bild auf, während du dich in einer erfassten Welt oder auf einem erfassten Server befindest.
- Die neueste Aufnahme wird gespeichert, wenn du die Welt oder den Server verlässt.
- Für jede Welt und jeden Server gibt es eine eigene PNG-Datei mit gehashtem Dateinamen.
- FancyMenu lädt bis zu fünf aktuelle Weltaufnahmen und fünf aktuelle Serveraufnahmen vor.
- Für ein Ziel wird erst dann etwas angezeigt, wenn die erste Aufnahme gespeichert wurde.

Die Aufnahmen werden hier gespeichert:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Die Screenshots können alles enthalten, was zum Aufnahmezeitpunkt in der Welt sichtbar ist. Wenn du das nahtlose Laden von Welten deaktivierst, werden keine Aufnahmen mehr erstellt oder verwendet. Vorhandene PNG-Dateien werden jedoch nicht gelöscht. Lösche unerwünschte Aufnahmen bei geschlossenem Spiel aus dem Verzeichnis.
