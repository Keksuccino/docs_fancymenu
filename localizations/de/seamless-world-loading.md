---
title: Nahtloses Weltenladen
description: Verwende eine aktuelle Weltansicht als nächsten Ladebildschirm-Hintergrund.
---

# Nahtloses Weltenladen

Nahtloses Weltenladen verwendet eine aktuelle Ansicht einer Welt oder eines Servers als nächsten Hintergrund für den Ladebildschirm.

Aktiviere es über [**Anpassung -> Globale Anpassungen**](./global-customizations) -> **Nahtloses Weltenladen**.

# Wie es funktioniert

- FancyMenu erfasst in regelmäßigen Abständen das aktuelle Bild, während du dich in einer erfassten Welt oder auf einem erfassten Server befindest.
- Die neueste Aufnahme wird gespeichert, wenn du die Welt verlässt.
- Jede Welt und jeder Server hat einen eigenen gehashten PNG-Dateinamen.
- FancyMenu lädt bis zu fünf aktuelle Welt-Aufnahmen und fünf aktuelle Server-Aufnahmen vor.
- Für ein Ziel wird nichts angezeigt, bis die erste Aufnahme gespeichert wurde.

Aufnahmen werden gespeichert in:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Die Screenshots können alles enthalten, was zum Zeitpunkt der Aufnahme in der Welt sichtbar war. Das Deaktivieren von Nahtlosem Weltenladen beendet das Erfassen und die Verwendung, löscht jedoch keine vorhandenen PNG-Dateien. Lösche unerwünschte Aufnahmen aus dem Verzeichnis, während das Spiel geschlossen ist.
