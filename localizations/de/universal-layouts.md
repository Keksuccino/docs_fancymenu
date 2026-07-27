---
title: Universelle Layouts
description: Wende ein Layout auf mehrere unterstützte Bildschirme an.
---

# Universelle Layouts

Ein universelles Layout wird für jeden unterstützten Bildschirm berücksichtigt, bei dem die Bildschirmanpassung aktiviert ist. Es wird nicht auf [blockierte](./incompatibility-list#screens-where-customization-is-intentionally-disabled) oder anderweitig ausgeschlossene Bildschirme angewendet.

Verwende universelle Layouts für gemeinsame Elemente wie Logos, Navigation, Overlays oder [Audio-Elemente](./elements#audio), die über mehrere Bildschirme hinweg bestehen bleiben sollen.

# Erstellung

1. Öffne einen unterstützten Bildschirm und zeige die FancyMenu-Menüleiste an.
2. Wähle **Layouts -> Neu -> Für alle Bildschirme [Universal]**.
3. Füge Elemente hinzu und konfiguriere sie.
4. Speichere das Layout.

Normale Bildschirme erfordern weiterhin, dass **Current Screen Customization** aktiviert ist. Es gibt keinen globalen Schalter zum Aktivieren für alle, da nicht unterstützte Mod-Bildschirme bei einer Anpassung beschädigt werden können.

# Eingrenzen von Bildschirmen

Öffne die Einstellungen für Universal Layouts über das Kontextmenü des Editor-Hintergrunds.

- **Whitelist:** Das Layout wird nur auf die aufgelisteten Bildschirm-IDs angewendet.
- **Blacklist:** Das Layout wird auf jeden geeigneten Bildschirm außer den aufgelisteten Bildschirm-IDs angewendet.

Verwende **Anpassung -> Kennung des aktuellen Bildschirms kopieren**, um eine [Bildschirm-ID](./screen-identifiers) zu kopieren.

Du kannst auch [layoutweite Anforderungen](./conditions#layout-wide-requirements) hinzufügen, um zu steuern, wann das Layout angewendet wird.

# Reihenfolge der Layouts

Geeignete universelle Layouts und bildschirmspezifische Layouts werden kombiniert und nach **Layout-Index** gestapelt. Niedrigere Indizes werden zuerst angewendet; spätere stapelbare Einstellungen können frühere überschreiben. Beim gleichen Index werden universelle Layouts vor bildschirmspezifischen Layouts gesammelt.
