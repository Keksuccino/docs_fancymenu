---
title: Parallax-Effekt
description: Hintergründe und Elemente mit dem Mauszeiger bewegen.
---

# Parallax-Effekt

Parallax verschiebt einen Hintergrund oder ein Element basierend auf der Mausbewegung, um visuelle Tiefe zu erzeugen.

# Hintergrund des Bildmenüs

1. Klicken Sie mit der rechten Maustaste auf den Hintergrund des Layout-Editors.
2. Öffnen Sie [**Menü-Hintergründe**](./menu-backgrounds) -> **Bild**.
3. Legen Sie die Bildquelle fest.
4. Aktivieren Sie **Parallax-Effekt**.
5. Stellen Sie die X- und Y-Intensitätswerte ein.
6. Aktivieren Sie optional **Parallax-Bewegung invertieren**.

Die X- und Y-Werte steuern die horizontale und vertikale Bewegung unabhängig voneinander. Verwenden Sie Werte von `0.0` (keine) bis `1.0` (maximal).

# Elemente

1. Klicken Sie mit der rechten Maustaste auf ein [Element](./elements).
2. Aktivieren Sie **Parallax-Effekt**.
3. Stellen Sie **Parallax-Intensität X** und **Parallax-Intensität Y** ein.
4. Optional können Sie die Bewegung invertieren.

Verwenden Sie eine niedrigere Intensität für entfernte Ebenen und eine höhere Intensität für Vordergrundebenen. Große Unterschiede oder invertierte Ebenen erzeugen einen stärkeren Tiefeneffekt.

# Fehlerbehebung

- Eine Intensität von `0` erzeugt keine Bewegung auf dieser Achse.
- **Breite Bilder von links nach rechts einblenden** steht in Konflikt mit dem Hintergrund-Parallax-Effekt und muss deaktiviert werden.
- Sehr kleine Bewegungen können stufenweise erscheinen, da GUI-Positionen ganze Pixel verwenden.
