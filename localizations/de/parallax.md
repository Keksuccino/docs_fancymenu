---
title: Parallax-Effekt
description: >-
  Lass Hintergründe und Elemente sich ein wenig mit der Maus bewegen, damit
  deine Menüs mehr Tiefe bekommen.
sourceBlobSha: f8481cfcc8d4f90bf2f261d436188763c8f23cba
---

# Parallax-Effekt

Beim Parallax-Effekt bewegt sich ein Menühintergrund oder ein Element ein wenig, wenn sich die Maus bewegt. Lass weiter entfernte Ebenen weniger und nähere stärker bewegen – so bekommt dein Menü mehr Tiefe.

<img width="640" alt="Ein Titelbildschirm mit einer Landschaft in der Abenddämmerung, die aus vier Ebenen besteht: Während sich die Maus bewegt, bewegt sich der Baum im Vordergrund am stärksten, die Hügel weniger und die Berge und der Himmel nur ein wenig" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_scene.gif?raw=true">

Der Effekt funktioniert für [Elemente](/elements) sowie für **Bilder** und **Videos** als [Menühintergrund](/menu-backgrounds).

# Elemente

<img width="640" alt="Auf einem Titelbildschirm mit einer Spalte aus Schaltflächen links werden im Layout-Editor die fünf Schaltflächen per Klick und Strg + Klick ausgewählt. Für alle wird der Parallax-Effekt auf Aktiviert und die Parallax-Intensität (X) auf 1.0 gesetzt. Anschließend wird gespeichert und der Editor geschlossen. Auf dem Titelbildschirm bewegen sich die Schaltflächen leicht, wenn die Maus nach links und rechts bewegt wird. Das Logo und die Landschaft bleiben still" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_element_settings.gif?raw=true">

1. Klicke im Layout-Editor mit der rechten Maustaste auf das Element und scrolle nach unten zu **Parallax-Effekt**.
2. Klicke auf **Parallax-Effekt**, um ihn auf **Aktiviert** zu setzen.
3. Klicke auf **Parallax-Intensität (X)** und **Parallax-Intensität (Y)**, um festzulegen, wie weit sich das Element bewegt.
4. Speichere das Layout und schließe den Editor. Elemente bewegen sich nur außerhalb des Editors.

Wenn du den Effekt gleichzeitig auf mehrere Elemente anwenden möchtest, [wähle](/layout-editor#selecting) sie zuerst aus (`Strg` + Klick fügt ein Element zur Auswahl hinzu) und klicke dann mit der rechten Maustaste auf eines davon.

| Einstellung | Funktion |
|---|---|
| **Parallax-Effekt** | Schaltet den Effekt ein. |
| **Parallax-Intensität (X)** | Legt fest, wie weit sich das Element nach links und rechts bewegt: von `0.0` (gar nicht) bis `1.0`. Neue Elemente haben den Wert `0.5`. |
| **Parallax-Intensität (Y)** | Dasselbe für die Bewegung nach oben und unten. |
| **Parallax-Bewegung umkehren** | Bewegt das Element in dieselbe Richtung wie die Maus. Ist die Option deaktiviert, bewegt es sich in die entgegengesetzte Richtung. |

Bei `1.0` bewegt sich ein Element bis zu 5 % der Bildschirmbreite zur Seite und bis zu 5 % der Bildschirmhöhe nach oben oder unten, wenn sich die Maus am Bildschirmrand befindet. In der Bildschirmmitte bleiben die Elemente an der Stelle, an der du sie platziert hast.

- Elemente, die an einem Element mit aktiviertem Effekt [verankert](/positioning-elements) sind, bewegen sich mit ihm. Ihr eigener Effekt kommt zusätzlich dazu.
- **Auf dem Bildschirm halten** hält Elemente mit aktiviertem Effekt nicht auf dem Bildschirm. Sie können sich also über dessen Ränder hinaus bewegen.
- Gestreckte Elemente bewegen sich nicht in die Richtung, in der sie gestreckt sind.
- [Vanilla-Schaltflächen und -Regler](/vanilla-elements) bewegen sich erst, nachdem du sie verschoben hast. Mit dem Ankerpunkt **Vanilla (Original)** bleiben sie dort, wo das Spiel sie platziert.
- Schaltflächen bleiben an der Stelle anklickbar, an der sie angezeigt werden.
- [Scrollbereiche](/scrollable-areas), die darin enthaltenen Elemente und Tooltip-Elemente haben keinen Parallax-Effekt.

# Menühintergründe

<img width="800" alt="Das Rechtsklickmenü des Layout-Editors mit den geöffneten Menüs Menühintergründe und Bild. Es zeigt Parallax-Effekt, Parallax-Effekt-Intensität (X) festlegen, Parallax-Effekt-Intensität (Y) festlegen und Parallax-Bewegung umkehren" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_background_settings.png?raw=true">

1. Klicke mit der rechten Maustaste auf den Hintergrund des Editors und öffne **Menühintergründe -> Bild** (oder **Video**).
2. Klicke auf **Parallax-Effekt**, um ihn auf **Aktiviert** zu setzen.
3. Lege **Parallax-Effekt-Intensität (X) festlegen** und **Parallax-Effekt-Intensität (Y) festlegen** fest.

Hintergründe reagieren deutlich stärker als Elemente. Der Hintergrund wird entsprechend seiner Intensität vergrößert, sodass seine Ränder nie sichtbar sind: Bei `1.0` ist er doppelt so groß wie der Bildschirm und bewegt sich bis zur Hälfte der Bildschirmbreite zur Seite. Halte die Werte niedrig: Neue Hintergründe haben den Wert `0.02`, und Werte zwischen `0.01` und `0.1` eignen sich gut.

- **Parallax-Bewegung umkehren** bewegt den Hintergrund in dieselbe Richtung wie die Maus.
- **Breite Bilder von links nach rechts verschieben** und **Parallax-Effekt** können nicht gleichzeitig aktiviert sein.
- **Textur wiederholen** und **Seitenverhältnis des Hintergrunds beibehalten** funktionieren zusammen mit dem Effekt.
- Hintergründe bewegen sich auch im Layout-Editor.

# Eine Szene mit Tiefenwirkung erstellen

Die Szene am Anfang dieser Seite besteht aus einem Himmel und drei Ebenen auf dem Titelbildschirm:

1. Zeichne deine Szene in Ebenen, von hinten nach vorne, zum Beispiel Himmel, Berge, Hügel und Vordergrund. Jede Ebene außer dem Himmel ist ein PNG-Bild mit transparenten Bereichen.
2. Lege den Himmel als Menühintergrund vom Typ **Bild** fest und aktiviere seinen Parallax-Effekt.
3. Füge jede weitere Ebene als [Bildelement](/elements#image) hinzu – von hinten nach vorne, sodass die vorderste Ebene oben liegt.
4. Mache die Ebenen etwas größer als den Bildschirm, damit ihre Ränder beim Bewegen nie sichtbar sind. Eine Ebene mit dem Wert `1.0` benötigt links und rechts jeweils 5 % der Bildschirmbreite sowie oben und unten jeweils 5 % der Bildschirmhöhe zusätzlich. Deaktiviere **Auf dem Bildschirm halten**, damit du sie über die Bildschirmränder hinaus platzieren kannst.
5. Aktiviere den Parallax-Effekt für jede Ebene: Verwende niedrige Intensitäten für weiter entfernte und hohe Intensitäten für nähere Ebenen.
6. Klicke mit der rechten Maustaste auf den Hintergrund des Editors und setze **Benutzerdefinierte Elemente hinter Vanilla** auf **Aktiviert**, damit die Ebenen hinter den Schaltflächen und dem Logo bleiben.

Dies sind die Intensitätswerte der Szene:

| Ebene | Intensität (X) | Intensität (Y) |
|---|---|---|
| Himmel (Menühintergrund) | `0.02` | `0.01` |
| Berge | `0.35` | `0.2` |
| Hügel | `0.6` | `0.3` |
| Vordergrund | `1.0` | `0.5` |

> [!TIP]
> Wähle für die Y-Intensität ungefähr die Hälfte der X-Intensität. So hüpft der Boden einer Landschaft nicht so stark auf und ab.

# Gut zu wissen

- Alles bewegt sich in ganzen GUI-Pixeln, daher führen niedrige Intensitäten zu kleinen Bewegungsschritten.
- Für die Intensitätseinstellungen können [Platzhalter](/placeholders) verwendet werden: Zeige auf einen Platzhalter und klicke im kleinen Menü daneben auf **Als reinen Text festlegen**. Mit einer [Variablen](/variables) kannst du Spieler die Effektstärke in deinem eigenen Einstellungsmenü verringern lassen.
