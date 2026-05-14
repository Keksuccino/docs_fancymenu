---
title: Texturen optimieren
description: Wie man Texturen für FancyMenu optimiert.
---

# Texturen für FancyMenu optimieren

FancyMenu verwendet die von dir bereitgestellten Texturen unverändert. Das bedeutet, dass deine Bilddateien **nicht** komprimiert, herunterskaliert oder hochskaliert werden. Damit deine Menüs scharf aussehen und gut laufen, ist es wichtig, deine Texturen bei der Verwendung in deiner UI zu optimieren.

# Wichtige Tipps zur Texturoptimierung

Die folgenden Tipps sind die wichtigsten grundlegenden Schritte, die du beim Arbeiten mit Texturen in FancyMenu beachten solltest.

## 1. Die richtige Auflösung verwenden
- **Niedrig aufgelöste Bilder vermeiden**: Wenn ein Bild zu klein ist und auf eine größere Fläche gezogen wird, kann es unscharf wirken.
- **Übertriebene hohe Auflösungen vermeiden**: Sehr große Texturen, die in kleiner Größe angezeigt werden, können ebenfalls verzerrt oder „komisch“ aussehen und möglicherweise die Leistung beeinträchtigen.

> 📌 **Tipp:** Verwende Texturen in oder nahe der Auflösung, in der sie im Menü erscheinen werden.
{.is-info}

## 2. Das Seitenverhältnis beibehalten
- Behalte beim Skalieren immer das Seitenverhältnis des Bildes bei.
- Das unverhältnismäßige Strecken eines Bildes kann zu visuellen Artefakten und einem schlechten Erscheinungsbild führen.

> 📌 **Tipp:** Du kannst mit der rechten Maustaste auf Bildelemente klicken und auf **Seitenverhältnis wiederherstellen** klicken, um sie auf ihr korrektes Seitenverhältnis zurückzusetzen. Wenn du sie danach manuell weiter vergrößerst oder verkleinerst, halte dabei **SHIFT** gedrückt, damit die Skalierung das Seitenverhältnis des Elements berücksichtigt.
{.is-info}

## 3. Nine-Slicing & Kachelung berücksichtigen
- Für skalierbare UI-Elemente (wie Panels oder Buttons) solltest du die Funktionen [Nine-Slicing & Kachelung](/nine-slicing-and-tiling) von FancyMenu verwenden.
- Dadurch bleiben die Kanten der Texturen beim Skalieren scharf.
