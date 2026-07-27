---
title: Texturen optimieren
description: Wie man Texturen für FancyMenu optimiert.
---

# Texturen für FancyMenu optimieren

FancyMenu verwendet die von dir bereitgestellten Texturen unverändert. Das bedeutet, dass die Bilddateien **nicht** komprimiert, herunterskaliert oder hochskaliert werden. Damit deine Menüs scharf aussehen und gut performen, ist es wichtig, deine Texturen bei der Verwendung in deiner UI zu optimieren.

# Wichtige Tipps zur Texturoptimierung

Die folgenden Tipps sind die wichtigsten grundlegenden Schritte, die du bei der Arbeit mit Texturen in FancyMenu beachten solltest.

## 1. Die richtige Auflösung verwenden
- **Vermeide Bilder mit zu niedriger Auflösung**: Wenn ein Bild zu klein ist und auf einen größeren Bereich gestreckt wird, kann es unscharf wirken.
- **Vermeide zu hohe Auflösung ohne Nutzen**: Sehr große Texturen, die in kleiner Größe angezeigt werden, können ebenfalls verzerrt oder "seltsam" aussehen und möglicherweise unnötig Leistung verbrauchen.

> [!NOTE]
> 📌 **Tipp:** Verwende Texturen in oder nahe der Auflösung, in der sie im Menü angezeigt werden.

## 2. Das Seitenverhältnis beibehalten
- Behalte beim Skalieren immer das Seitenverhältnis des Bildes bei.
- Ein Bild unverhältnismäßig zu strecken kann zu visuellen Artefakten und einem schlechten Erscheinungsbild führen.

> [!NOTE]
> 📌 **Tipp:** Du kannst mit der rechten Maustaste auf Bildelemente klicken und auf **Seitenverhältnis wiederherstellen** klicken, um sie auf ihr korrektes Seitenverhältnis zurückzusetzen. Wenn du sie danach manuell weiter skalierst, halte beim Skalieren **SHIFT** gedrückt, damit die Skalierung das Seitenverhältnis des Elements beibehält.

## 3. Nine-Slicing & Tiling berücksichtigen
- Für skalierbare UI-Elemente (wie Panels oder Buttons) solltest du die Funktionen von FancyMenu für [Nine-Slicing & Tiling](/nine-slicing-and-tiling) verwenden.
- So bleiben die Kanten der Texturen auch beim Ändern der Größe scharf.
