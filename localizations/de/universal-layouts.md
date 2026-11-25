---
title: Universelle Layouts
description: Wende ein Layout auf mehrere unterstützte Bildschirme an.
sourceBlobSha: 2179fed92c6598b6e5c3ecfea354a4c853bc394b
---

# Universelle Layouts

Ein universelles Layout wird auf jedem unterstützten Bildschirm berücksichtigt, für den die Bildschirmanpassung aktiviert ist. Es gilt nicht für [blockierte](/incompatibility-list#screens-where-customization-is-intentionally-disabled) oder anderweitig ausgeschlossene Bildschirme.

Verwende universelle Layouts für gemeinsame Elemente wie Logos, Navigation, Overlays oder [Audioelemente](/elements#audio), die auf mehreren Bildschirmen angezeigt werden sollen.

# Ein Layout erstellen

1. Öffne einen unterstützten Bildschirm und blende die FancyMenu-Menüleiste ein.
2. Wähle **Layouts -> Neu -> Für alle Bildschirme [Universell]**.
3. Füge Elemente hinzu und konfiguriere sie.
4. Speichere das Layout.

Für gewöhnliche Bildschirme muss **Anpassung des aktuellen Bildschirms** weiterhin aktiviert sein. Es gibt keine globale Option zum Aktivieren für alle Bildschirme, da nicht unterstützte Mod-Bildschirme durch Anpassungen beeinträchtigt werden können.

# Bildschirme einschränken

Öffne die Einstellungen des universellen Layouts über das Kontextmenü des Editorhintergrunds.

- **Positivliste:** Das Layout gilt nur für die aufgeführten Bildschirmkennungen.
- **Negativliste:** Das Layout gilt für alle geeigneten Bildschirme mit Ausnahme der aufgeführten Kennungen.

Verwende **Anpassung -> Kennung des aktuellen Bildschirms kopieren**, um eine [Bildschirmkennung](/screen-identifiers) zu kopieren.

Du kannst außerdem [layoutweite Voraussetzungen](/conditions#layout-wide-requirements) hinzufügen, um festzulegen, wann das Layout angewendet wird.

# Layout-Reihenfolge

Geeignete universelle Layouts und bildschirmspezifische Layouts werden kombiniert und anhand des **Layout-Index** gestapelt. Niedrigere Indizes werden zuerst angewendet; spätere stapelbare Einstellungen können frühere überschreiben. Bei gleichem Index werden universelle Layouts vor bildschirmspezifischen Layouts erfasst.
