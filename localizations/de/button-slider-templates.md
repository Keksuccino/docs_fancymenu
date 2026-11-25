---
title: Vorlagen für Buttons und Schieberegler
description: >-
  Übertrage Texturen, Sounds und Beschriftungsstil eines Vorlagen-Buttons auf
  alle Buttons oder Schieberegler eines Bildschirms.
sourceBlobSha: 805a2ae3221a644c78cd5eafebc5579bc8d60815
---

# Vorlagen für Buttons und Schieberegler

Eine Vorlage ist ein [Button-Element](/elements#button), das sein Aussehen an alle anderen Buttons oder Schieberegler auf dem Bildschirm weitergibt – sowohl an die standardmäßigen als auch an deine eigenen. Änderst du die Vorlage, ändern sie sich alle mit.

> [!TIP]
> Wenn alle Menüs im Spiel gleich aussehen sollen, verwende stattdessen [globale Anpassungen](/global-customizations). Vorlagen gelten für einen einzelnen Bildschirm oder für alle Bildschirme, die ein [universelles Layout](/universal-layouts) lädt.

# Eine Vorlage erstellen

1. Füge dem Layout ein Button-Element hinzu.
2. Klicke mit der rechten Maustaste darauf, öffne **Vorlageneinstellungen** und aktiviere den **Vorlagenmodus**.
3. Setze **Einstellungen teilen mit** auf **Buttons** oder **Schieberegler**.
4. Weise der Vorlage wie jedem anderen Button die gewünschten Texturen, Sounds und Beschriftungseinstellungen zu. Bei **Schieberegler** gelten die Textureinstellungen für Schieberegler.

Außerhalb des Editors wird die Vorlage nicht angezeigt. Platziere sie also so, dass sie nicht im Weg ist. Im Editor sieht eine Vorlage für Schieberegler wie ein Schieberegler aus.

# Was Vorlagen weitergeben

## Immer

- Ihre Button-Texturen (oder Schieberegler-Texturen) samt [Neun-Slice-Einstellungen](/nine-slicing-and-tiling).
- Ihre Sounds für Hover, Hover-Ende und Klick.

Solange eine Vorlage aktiv ist, verwenden die Buttons deren Texturen und Sounds statt ihrer eigenen. Hat die Vorlage keine Texturen, verwenden die Buttons ebenfalls nicht ihre eigenen.

## Wenn du die Option aktivierst

Aktiviere diese Optionen in den **Vorlageneinstellungen** der Vorlage:

| Einstellung | Was die Buttons von der Vorlage übernehmen |
|---|---|
| **Beschriftung im Vorlagenmodus teilen** | **Beschriftung** und **Hover-Beschriftung** sowie den gesamten Beschriftungsstil: **Beschriftungsausrichtung**, **Beschriftungsgröße**, **Grundfarbe der Beschriftung**, **Hover-Farbe der Beschriftung**, **Beschriftungsschatten** und **Beschriftung beim Hover unterstreichen**. |
| **X-Position im Vorlagenmodus teilen** und **Y-Position im Vorlagenmodus teilen** | Die Position. Standardmäßige Buttons werden erst verschoben, wenn ihr **Ankerpunkt** nicht mehr auf **Standard (Original)** gesetzt ist. |
| **Deckkraft im Vorlagenmodus teilen** | Die Deckkraft. |

## Beschriftungsausrichtung für alle Buttons

Mit **Beschriftung im Vorlagenmodus teilen** übernehmen alle Buttons auch den Text der Vorlage. Diese Option ist daher für Bildschirme gedacht, auf denen alle Buttons denselben Text anzeigen sollen.

So richtest du nur die Beschriftungen aus und behältst ihre Texte bei:

- Für einen einzelnen Bildschirm wählst du die Buttons mit `Ctrl` + Klick aus (siehe [Auswählen](/layout-editor#selecting)), klickst mit der rechten Maustaste auf einen davon und legst **Beschriftungsausrichtung** einmal für alle fest.
- Für alle Menüs verwendest du **Beschriftungsausrichtung** unter [globalen Anpassungen](/global-customizations#labels).

# Gut zu wissen

- Nur Button-Elemente können Vorlagen sein, sie funktionieren aber mit standardmäßigen und benutzerdefinierten Buttons und Schiebereglern.
- Ein Bildschirm kann gleichzeitig eine Vorlage für Buttons und eine für Schieberegler haben. Gibt es mehrere Vorlagen derselben Art, ist nur eine davon aktiv.
- Eine Vorlage funktioniert nur, solange sie sichtbar ist. Mit [Anforderungen](/element-visibility) für die Vorlage kannst du sie ein- und ausschalten.
