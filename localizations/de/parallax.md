---
title: Parallax-Effekt
description: Wie man einen Parallax-Effekt auf Menühintergründe und Elemente anwendet.
---
# Was ist der Parallax-Effekt?

Der Parallax-Effekt ist ein cooler visueller Trick, der dafür sorgt, dass deine Menühintergründe und Elemente Tiefe erhalten. Wenn du den Mauszeiger bewegst, verschieben sich Elemente mit aktiviertem Parallax-Effekt leicht und erzeugen so die Illusion von 3D-Raum in deinem 2D-Menü.

Stell es dir so vor, als würdest du in einem Auto mitfahren: Dinge, die näher bei dir sind (wie Straßenschilder), scheinen sich schneller zu bewegen als entfernte Dinge (wie Berge). In FancyMenu sorgt dieselbe Idee für ein dynamischeres und interaktiveres Erlebnis.

# Wo kannst du Parallax in FancyMenu verwenden?

In FancyMenu kannst du den Parallax-Effekt an zwei Hauptstellen verwenden:

1. **Menühintergründe**: Lasse deinen gesamten Menühintergrund sich leicht mit dem Mauszeiger bewegen
2. **Elemente**: Lasse einzelne Elemente (wie Bilder, Schaltflächen oder Text) unabhängig voneinander bewegen

# So verwendest du Parallax für Menühintergründe

Einen Parallax-Effekt zu deinem Menühintergrund hinzuzufügen ist super einfach:

1. Öffne den Menü-Editor, indem du **STRG+ALT+C** drückst, um die Menüleiste anzuzeigen, und gehe dann zu **Anpassung**
2. Erstelle ein neues Layout oder bearbeite ein vorhandenes
3. Klicke auf **Layout → Eigenschaften**
4. Öffne **Menühintergründe**
5. Wähle **Bild** als Hintergrundtyp
6. Konfiguriere deinen Bildhintergrund:
   - Wähle ein Bild aus (lokal oder aus dem Web)
   - Aktiviere **Parallax-Effekt**, indem du den Umschalter anklickst
   - Setze die **Parallax-Effekt-Intensität X** und **Parallax-Effekt-Intensität Y** (zwischen 0,0 und 1,0)
   - Optional kannst du **Parallax-Bewegung umkehren** aktivieren, um die Richtung zu ändern

> **Tipp**: Je höher der Intensitätswert, desto stärker bewegt sich dein Hintergrund. FancyMenu 3.9.0 erlaubt es dir, X- und Y-Intensität getrennt einzustellen, sodass du die Bewegung horizontal stärker als vertikal oder umgekehrt machen kannst.
{.is-info}

# So verwendest du Parallax für einzelne Elemente

Du kannst Parallax auch zu einzelnen Elementen hinzufügen, um Schichteffekte zu erzeugen:

1. Wähle im Editor ein beliebiges Element aus, indem du darauf klickst
2. Klicke mit der rechten Maustaste auf das Element, um das Kontextmenü zu öffnen
3. Scrolle nach unten und suche **Parallax-Effekt: Aktiviert/Deaktiviert**
4. Stelle es auf **Aktiviert**
5. Passe die Werte für **Parallax-Intensität X** und **Parallax-Intensität Y** an (zwischen 0,0 und 1,0)
6. Optional kannst du **Parallax umkehren** aktivieren, um die Bewegungsrichtung zu ändern

# Tipps für beeindruckende Parallax-Effekte

## Schichte deine Elemente

Erzeuge Tiefe, indem du für verschiedene Elemente unterschiedliche Parallax-Intensitätswerte verwendest. Du kannst X und Y getrennt anpassen:

- **Hintergrund**: Geringe Intensität (0,1–0,3)
- **Elemente der mittleren Ebene**: Mittlere Intensität (0,3–0,6)
- **Vordergrundelemente**: Höhere Intensität (0,6–0,9)

So entsteht ein überzeugender 3D-Effekt, wenn du die Maus bewegst!

## Normale und umgekehrte Parallax-Bewegung kombinieren

Versuche, einige Elemente auf **Parallax-Bewegung umkehren: Aktiviert** und andere auf **Deaktiviert** zu setzen. Dadurch bewegen sich Elemente in entgegengesetzte Richtungen, was den Tiefeneffekt verstärkt.

## Nicht übertreiben

Zu viel Bewegung kann ablenkend sein. Verwende den Parallax-Effekt sparsam, besonders bei hohen Intensitätswerten.

# Fehlerbehebung

## Parallax funktioniert nicht?

1. Stelle sicher, dass du den Parallax-Effekt aktiviert hast
2. Prüfe, ob deine Parallax-Intensität nicht auf 0 gesetzt ist
4. Bestätige, dass die Option "Breite Bilder von links nach rechts schieben" deaktiviert ist (diese Option steht im Konflikt mit Parallax)

## Parallax-Bewegung zu schnell/langsam?

Passe die Werte für **Parallax-Intensität X/Y** an:
- Niedrigere Werte (näher an 0) = langsamere, dezentere Bewegung
- Höhere Werte (näher an 1) = schnellere, deutlichere Bewegung

## Parallax fühlt sich ruckelig oder verzögert an?

Das ist eine Einschränkung des Parallax-Effekts, da Minecraft koordinatenbasiert mit ganzen Zahlen arbeitet. Daher kann es sein, dass sich der Effekt ein wenig so anfühlt, als würden Elemente "springen". Das sollte aber nicht zu auffällig sein, wenn du die "normalen" Parallax-Intensitäten verwendest und nicht extrem kleine oder große Werte.
