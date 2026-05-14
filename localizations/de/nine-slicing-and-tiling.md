---
title: Nine-Slicing und Kacheln
description: Wie man Nine-Slicing und Kacheln in FancyMenu verwendet.
---

# Nine-Slicing und Kacheln

Wenn du in Minecraft mit FancyMenu coole Menüs gestaltest, möchtest du vielleicht Bilder verwenden, die sich korrekt skalieren oder in Mustern wiederholen lassen. Dieser Leitfaden erklärt, wie du **Nine-Slicing** und **Kacheln** (auch als sich wiederholende Texturen bezeichnet) verwendest, damit deine Menüs großartig aussehen!

# Was ist Nine-Slicing?

Nine-Slicing ist eine Technik, mit der du ein Bild auf jede beliebige Größe strecken kannst, ohne dass es seltsam aussieht. Dabei wird dein Bild in neun Teile unterteilt (wie ein Tic-Tac-Toe-Feld). Die Ecken bleiben gleich groß, die Kanten werden nur in eine Richtung gestreckt und die Mitte wird in beide Richtungen gestreckt.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Nine-Slice-Beispiel" style="max-width: 500px; height: auto;" />

## Wo kann ich Nine-Slicing verwenden?

In FancyMenu ist Nine-Slicing verfügbar für:
- **Button-Elemente** (sowohl benutzerdefinierte Buttons als auch beim Bearbeiten von Vanilla-Buttons)
- **Fortschrittsbalken-Texturen** (Balken- und Hintergrundtexturen)

## So verwendest du Nine-Slicing bei Buttons

1. **Erstelle oder wähle ein Button-Element** in deinem Layout-Editor aus.
2. Klicke mit der rechten Maustaste auf den Button und suche nach der Option „Button Textures“.
3. Lege die Hintergrundtexturen deines Buttons fest (Normal-, Hover- und Inaktiv-Zustand).
4. Aktiviere die Option „Nine-Slice Custom Background“.
5. Setze die **Nine-Slice Background X-Borders** (linke und rechte Randgröße).
6. Setze die **Nine-Slice Background Y-Borders** (obere und untere Randgröße).

### Tipps für Nine-Slicing bei Buttons

- Verwende ein Bild mit klaren Rändern und Ecken.
- Die Randwerte (X und Y) teilen FancyMenu mit, wie viele Pixel von jeder Kante als Rand behandelt werden sollen.
- Ein typischer Wert könnte bei X- und Y-Rändern jeweils 5 Pixel sein.
- Die Ecken bleiben immer gleich groß, während sich die mittleren Bereiche ausdehnen, um den Button zu füllen.

# Was ist Kacheln?

Kacheln (auch als sich wiederholende Texturen bezeichnet) ermöglichen es dir, einen großen Bereich mit einem kleinen Bild zu füllen, indem es wie Fliesen auf einem Boden wiederholt wird. Das ist perfekt für Hintergründe oder große Bilder, bei denen du möchtest, dass ein Muster fortgesetzt wird.

## Wo kann ich Kacheln verwenden?

In FancyMenu ist Kacheln verfügbar für:
- **Bild-Elemente**
- **Bild-Menühintergründe**

## So verwendest du Kacheln bei Bild-Elementen

1. **Erstelle oder wähle ein Bild-Element** in deinem Layout-Editor aus.
2. Klicke mit der rechten Maustaste auf das Bild und suche nach „Image Source“, um deine Textur festzulegen.
3. Finde die Option **„Repeat Texture“** und aktiviere sie.
4. Skaliere dein Bild-Element, um zu sehen, wie sich die Textur wiederholt und den Bereich füllt.

## So verwendest du Kacheln bei Menühintergründen

1. Öffne **Menu Backgrounds** über das Kontextmenü für Hintergründe im Layout-Editor.
2. Wähle den Hintergrundtyp **Image**.
3. Wähle dein Hintergrundbild aus.
4. Aktiviere die Option **„Repeat Texture“**.
5. Dein Hintergrund wiederholt nun die Textur, um den gesamten Bildschirm zu füllen.

# Gute Texturen für Nine-Slicing und Kacheln erstellen

## Für Nine-Slicing:
- Erstelle Texturen mit klar erkennbaren Rändern und Ecken.
- Achte darauf, dass deine Ränder deutlich und gleich breit sind.
- Teste verschiedene Randgrößen, um herauszufinden, was am besten funktioniert.
- Buttons funktionieren meist gut mit Rändern von 3 bis 5 Pixeln.

## Für Kacheln:
- Erstelle nahtlose Texturen, die an allen Seiten mit sich selbst verbunden werden können.
- Halte Muster einfach, um visuelle Unruhe zu vermeiden.
- Teste deine Textur zunächst, indem du sie in einem kleinen Bereich wiederholen lässt.

# Beispiele

## Beispiel für einen Nine-Sliced-Button
Ein einfacher Button könnte zunächst ein 30x30-Bild mit 5-Pixel-Rändern auf allen Seiten sein. Wenn du den Button größer machst, bleiben die Ecken bei 5x5 Pixeln, während sich die Kanten und die Mitte an die Größe des Buttons anpassen.

## Beispiel für einen gekachelten Hintergrund
Eine kleine 64x64-Kachel mit einem dezenten Muster kann wiederholt werden, um deinen gesamten Menühintergrund zu füllen, unabhängig von der Bildschirmgröße.

# Häufige Probleme und Lösungen

## Mein nine-sliced Button wirkt gestreckt oder verzerrt:
- Deine Randwerte sind möglicherweise zu klein oder zu groß
- Ändere die Randwerte so, dass sie zu deiner tatsächlichen Textur passen

## Mein gekachelter Hintergrund hat sichtbare Nähte:
- Deine Textur ist nicht nahtlos
- Bearbeite dein Bild so, dass die Kanten perfekt zusammenpassen

## Meine Texturen sehen beim Skalieren unscharf aus:
- Verwende Texturen mit höherer Auflösung
- Halte deine Designs einfach und mit klaren Linien

# Merke dir

- **Nine-Slicing** ist perfekt für UI-Elemente, die ihre Größe ändern müssen, dabei aber ihr Aussehen behalten sollen (wie Buttons).
- **Kacheln** ist ideal, um große Bereiche mit einem Muster zu füllen (wie Hintergründe).
- Beide Funktionen helfen dabei, dass deine UI bei jeder Auflösung und Bildschirmgröße gut aussieht!

Jetzt kannst du fantastische Minecraft-Menüs mit perfekt gestreckten Buttons und schönen gekachelten Hintergründen erstellen!
