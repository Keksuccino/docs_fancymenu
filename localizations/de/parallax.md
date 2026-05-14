---
title: Parallax-Effekt
description: Wie man einen Parallax-Effekt auf Menü-Hintergründe und Elemente anwendet.
---

# Was ist der Parallax-Effekt?

Der Parallax-Effekt ist ein cooler visueller Trick, der dafür sorgt, dass deine Menü-Hintergründe und Elemente Tiefe zu haben scheinen. Wenn du deinen Mauszeiger bewegst, verschieben sich Elemente mit aktiviertem Parallax-Effekt leicht und erzeugen so die Illusion von 3D-Raum in deinem 2D-Menü.

Stell dir das so vor, als würdest du in einem Auto fahren: Dinge, die näher bei dir sind (wie Straßenschilder), scheinen sich schneller zu bewegen als weit entfernte Dinge (wie Berge). In FancyMenu erzeugt dieselbe Idee ein dynamischeres und interaktiveres Erlebnis.

# Wo kannst du Parallax in FancyMenu verwenden?

In FancyMenu kannst du den Parallax-Effekt an zwei Hauptstellen einsetzen:

1. **Menü-Hintergründe**: Lässt deinen gesamten Menü-Hintergrund leicht mit deinem Mauszeiger mitbewegen
2. **Elemente**: Lässt einzelne Elemente (wie Bilder, Schaltflächen oder Text) unabhängig voneinander bewegen

# So verwendest du Parallax für Menü-Hintergründe

Das Hinzufügen eines Parallax-Effekts zu deinem Menü-Hintergrund ist ganz einfach:

1. Öffne den Menü-Editor, indem du **STRG+ALT+C** drückst, um die Menüleiste einzublenden, und gehe dann zu **Anpassung**
2. Erstelle ein neues Layout oder bearbeite ein vorhandenes
3. Klicke auf **Layout → Eigenschaften**
4. Öffne **Menü-Hintergründe**
5. Wähle **Bild** als Hintergrundtyp aus
6. Konfiguriere deinen Bild-Hintergrund:
   - Wähle ein Bild aus (lokal oder aus dem Internet)
   - Aktiviere **Parallax-Effekt**, indem du den Umschalter anklickst
   - Stelle die **Parallax-Effekt-Intensität X** und **Parallax-Effekt-Intensität Y** ein (zwischen 0,0 und 1,0)
   - Optional kannst du **Parallax-Bewegung umkehren** aktivieren, um die Richtung zu ändern

> **Tipp**: Je höher der Intensitätswert, desto stärker bewegt sich dein Hintergrund. FancyMenu 3.9.0 ermöglicht es dir, X- und Y-Intensität separat einzustellen, sodass du die Bewegung horizontal stärker als vertikal machen kannst oder umgekehrt.
{.is-info}

# So verwendest du Parallax für einzelne Elemente

Du kannst Parallax auch zu einzelnen Elementen hinzufügen, um Layer-Effekte zu erzeugen:

1. Wähle ein beliebiges Element im Editor aus, indem du darauf klickst
2. Klicke mit der rechten Maustaste auf das Element, um das Kontextmenü zu öffnen
3. Scrolle nach unten und suche nach **Parallax-Effekt: Aktiviert/Deaktiviert**
4. Schalte es auf **Aktiviert**
5. Passe die Werte für **Parallax-Intensität X** und **Parallax-Intensität Y** an (zwischen 0,0 und 1,0)
6. Optional kannst du **Parallax umkehren** aktivieren, um die Bewegungsrichtung zu ändern

# Tipps für großartige Parallax-Effekte

## Schichte deine Elemente

Erzeuge Tiefe, indem du für verschiedene Elemente unterschiedliche Parallax-Intensitätswerte verwendest. Du kannst X und Y separat anpassen:

- **Hintergrund**: Niedrige Intensität (0,1–0,3)
- **Elemente der mittleren Ebene**: Mittlere Intensität (0,3–0,6)
- **Elemente im Vordergrund**: Höhere Intensität (0,6–0,9)

So entsteht ein überzeugender 3D-Effekt, wenn du deine Maus bewegst!

## Normales und umgekehrtes Parallax kombinieren

Versuche, einige Elemente auf **Parallax-Bewegung umkehren: Aktiviert** und andere auf **Deaktiviert** zu setzen. Dadurch bewegen sich Elemente in entgegengesetzte Richtungen, was den Tiefeneffekt verstärkt.

## Nicht übertreiben

Zu viel Bewegung kann ablenkend wirken. Setze den Parallax-Effekt sparsam ein, besonders bei hohen Intensitätswerten.

# Fehlerbehebung

## Parallax funktioniert nicht?

1. Stelle sicher, dass du den Parallax-Effekt aktiviert hast
2. Prüfe, ob deine Parallax-Intensität nicht auf 0 gesetzt ist
4. Stelle sicher, dass die Option "Breite Bilder von links nach rechts verschieben" deaktiviert ist (diese Option steht im Konflikt mit Parallax)

## Parallax-Bewegung zu schnell/langsam?

Passe die Werte für **Parallax-Intensität X/Y** an:
- Niedrigere Werte (näher an 0) = langsamere, dezentere Bewegung
- Höhere Werte (näher an 1) = schnellere, auffälligere Bewegung

# Abschließende Gedanken

Der Parallax-Effekt ist eine wunderbare Möglichkeit, deine Minecraft-Menüs lebendiger und interaktiver wirken zu lassen. Experimentiere mit verschiedenen Kombinationen aus Hintergrund- und Element-Parallax, um beeindruckende, dynamische Layouts zu erstellen, die auf deine Mausbewegungen reagieren!

Denke daran: Die besten Effekte sind oft dezent – schon eine kleine Bewegung reicht aus, um ein immersives Erlebnis zu schaffen.
