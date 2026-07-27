---
title: Nine-Slicing & Kachelung
description: Skaliert gerahmte Texturen oder wiederholt nahtlose Texturen.
---

# Nine-Slicing und Kachelung

Nine-Slicing bewahrt die Ecken und Ränder einer Textur, während ihre Mitte gestreckt wird. Kachelung wiederholt eine Textur, anstatt sie zu strecken.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Nine-slice regions" style="max-width:500px;height:auto;" />

# Unterstützung für Nine-Slicing

| Bereich | Unterstützte Ziele |
|---|---|
| Widgets | Texturen für [Button](./elements#button) und [Slider](./elements#slider); [globale Button- und Slider-Stile](./global-customizations#button-visuals) |
| Bilder und Panels | [Bildelemente](./elements#image) |
| Fortschrittsbalken | [Füll- und Hintergrundtexturen](./elements#progress-bar) |
| Tooltips | [Benutzerdefinierte Hintergrundtexturen](./elements#tooltip) |

# Nine-Slicing konfigurieren

1. Legen Sie die Zieltextur fest.
2. Aktivieren Sie die Option **Nine-Slice**.
3. Stellen Sie die Randgrößen so ein, dass sie dem festen Randbereich in der Quelltextur entsprechen.
4. Ändern Sie die Größe des Elements und passen Sie die Randwerte an, falls die Ecken oder Kanten verzerrt werden.

Die Einstellungen für Buttons und Bilder verwenden X-/Y-Randgrößen. Fortschrittsbalken und Tooltips bieten bei Bedarf separate Kantenwerte an.

# Unterstützung für Kachelung

Wiederholte Texturen sind verfügbar für:

- [Bildelemente](./elements#image).
- [Bild-Hintergründe von Menüs](./menu-backgrounds).
- [Header- und Footer-Texturen von Scroll-Listen](./customizing-scrollable-screens).

Aktivieren Sie **Textur wiederholen** bei einem Bildelement oder Bild-Hintergrund. Für scrollbare Bildschirme verwenden Sie die Wiederholungsoptionen im Anpassungsmenü für Header/Footer.

Verwenden Sie eine nahtlose Quelltextur; nicht passende Kanten erzeugen sichtbare Linien zwischen den Kacheln.

Nine-Slicing und Wiederholung sind getrennte Modi. Wenn für ein Ziel beide Optionen angezeigt werden, wählen Sie diejenige aus, die dem gewünschten Skalierungsverhalten entspricht.
