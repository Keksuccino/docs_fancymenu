---
title: Scrollbereiche
description: >-
  So fügst du Elemente in einen Scrollbereich ein, ordnest sie an und änderst
  das Scrollverhalten des Bereichs.
sourceBlobSha: a424c5e8680ece5f25846de0399fc8e78f375e15
---
# Scrollbereiche

Ein **Scrollbereich** enthält andere Elemente und ermöglicht es Spielern, durch sie zu scrollen. Er eignet sich hervorragend für lange Button-Listen, Welt- oder Serverauswahlen, Item-Präsentationen, Nachrichtenbereiche und alles andere, was nicht auf einen Bildschirm passt.

Alle Elemente im Bereich scrollen mit ihm und werden an seinen Rändern abgeschnitten.

<img width="800" alt="Buttons in einen Scrollbereich einfügen und stapeln" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_showcase.gif?raw=true">

> [!NOTE]
> Nur Elemente, die du dem Layout hinzugefügt hast, können in einen Bereich eingefügt werden. [Vanilla-Elemente](/vanilla-elements) können das nicht, da sie zum Menü selbst gehören.

# Scrollbereich hinzufügen

1. Öffne ein Layout im Layout-Editor.
2. Klicke mit der rechten Maustaste auf den Editor-Hintergrund und wähle **Neues Element -> Scrollbereich**.
3. Ziehe Elemente in den Bereich.

# Elemente hinein- und herausziehen

- Ziehe ein Element auf den Bereich, um es hineinzulegen. Der Bereich leuchtet auf, wenn er das Element übernimmt. Ein Element wird nur eingefügt, wenn sich ein Teil davon innerhalb des Bereichs befindet.
- Um mehrere ausgewählte Elemente gleichzeitig zu ziehen, halte beim Beginn des Ziehens `Ctrl` (`Cmd` unter macOS) gedrückt.
- Wenn du ein Element nahe an den Rand des Bereichs ziehst, scrollt der Bereich, sodass du jeden Teil erreichen kannst. Du kannst auch im Editor mit dem Mausrad scrollen.
- Um ein Element herauszunehmen, ziehe es aus dem Bereich oder klicke mit der rechten Maustaste darauf und wähle **Aus Scrollbereich verschieben**. Es bleibt an seiner Position auf dem Bildschirm.
- Bereiche können auch in andere Bereiche eingefügt werden.

## Ebenen

Im [Ebenen-Widget](/layout-editor#scrollable-areas) werden die Elemente eines Bereichs darunter angezeigt. Ziehe Ebenen dorthin, um sie in einen Bereich hinein- oder aus ihm herauszubewegen oder ihre Reihenfolge zu ändern. Mit der Einklapp-Schaltfläche einer Bereichsebene kannst du die zugehörigen Elemente in der Liste ausblenden.

## Kopieren und Löschen

- Beim Kopieren eines Bereichs werden auch alle darin enthaltenen Elemente kopiert.
- Wenn du einen Bereich löschst, in dem sich noch Elemente befinden, wirst du gefragt, was mit ihnen geschehen soll: **Elemente löschen** löscht auch diese, **Elemente behalten** belässt sie an ihrer Position auf dem Bildschirm.

# Elemente anordnen

Klicke mit der rechten Maustaste auf den Bereich und öffne **Anordnung**. Unter **Modus** legst du fest, wie der Bereich seine Elemente platziert:

- **Anker**: Du platzierst die Elemente selbst, wie im restlichen Layout. Neue Bereiche verwenden diesen Modus.
- **Stapel**: Die Elemente werden nacheinander angeordnet.
- **Raster**: Die Elemente werden in gleich großen Zellen angeordnet.
- **Fluss**: Die Elemente werden nebeneinander angeordnet. Wenn eine Zeile voll ist, beginnt eine neue.

<img width="800" alt="Scrollbereiche im Stapel-, Raster- und Flussmodus" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

## Anker-Modus

Elemente in einem Bereich haben eigene Anker, die sich auf den Inhalt des Bereichs statt auf den Bildschirm beziehen. Der Anker **Obere linke Ecke** bezeichnet zum Beispiel die obere linke Ecke des Inhalts; die unteren Anker bleiben am Ende des Inhalts verankert. Unter [Elemente positionieren](/positioning-elements) erfährst du, wie Anker funktionieren.

- **Horizontal strecken** und **Vertikal strecken** passen die Breite beziehungsweise Höhe eines Elements an den Inhalt an.
- Elemente können nur an anderen Elementen im selben Bereich verankert werden. Wenn du ein Element in einen Bereich hinein- oder aus ihm herausbewegst, erhalten Elemente, deren Anker über den Rand des Bereichs hinweg verknüpft waren, den Anker **Obere linke Ecke** und bleiben an ihrer Position.

### Inhaltsgröße

Im Anker-Modus bestimmst du die Größe des Inhalts und damit, wie weit der Bereich scrollt.

Wähle den Bereich aus und ziehe den Ziehpunkt am Ende seines Inhalts. Ziehe ihn über den Rand des Bereichs hinaus, um weiterzumachen; dabei scrollt der Bereich mit.

<img width="698" alt="Der Ziehpunkt für den Inhalt eines ausgewählten Scrollbereichs" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_content_handle.png?raw=true">

Du kannst auch mit der rechten Maustaste auf den Bereich klicken und **Inhaltsgröße** öffnen:

- **Inhaltsbreite** und **Inhaltshöhe** legen die Größe anhand eines Zahlenwerts fest. Sie unterstützen [Platzhalter](/placeholders). Mit einem Platzhalter lässt sich der Ziehpunkt nicht ziehen.
- **An Inhalt anpassen** lässt den Inhalt genau dort enden, wo das letzte Element darin endet. Elemente, die an der Mitte oder am Ende des Inhalts verankert sind, bewegen sich mit ihm und werden daher nicht mitgezählt.

Der Inhalt ist nie kleiner als der Bereich und wird nur in den Richtungen größer, in die der Bereich scrollt.

## Stapel, Raster und Fluss

- Der Bereich platziert die Elemente für dich und vergrößert den Inhalt automatisch entsprechend.
- Ziehe ein Element an eine andere Stelle, um die Reihenfolge zu ändern. Eine Linie zeigt, wo es eingefügt wird.
- Beim Wechsel vom Anker-Modus zu einem dieser Modi bleibt die Reihenfolge erhalten, in der die Elemente auf dem Bildschirm angeordnet waren. Beim Zurückwechseln zum Anker-Modus bleibt jedes Element an seiner Position.
- Elemente, die aufgrund ihrer [Anforderungen](/conditions) ausgeblendet sind, lassen keine Lücke.
- Strecken funktioniert in diesen Modi nicht.
- In diesen Modi wird nur in eine Richtung gescrollt. Ein Bereich mit der Einstellung **Beides** scrollt vertikal.

Öffne **Anordnung**, um die Modi genauer einzustellen:

| Einstellung | Funktion |
|---|---|
| **Ausrichtung** | Legt fest, wo die Elemente quer zur Anordnungsrichtung platziert werden: **Anfang**, **Mitte**, **Ende** oder **Ausfüllen**. Bei **Ausfüllen** werden sie so breit wie der verfügbare Platz (oder so hoch, wenn der Bereich horizontal scrollt). Im Flussmodus gibt es **Ausfüllen** nicht. |
| **Abstand** | Der Abstand zwischen den Elementen. |
| **Innenabstand** | Der Abstand zwischen den Elementen und den Rändern des Inhalts. |
| **Elemente pro Zeile** | Nur im Rastermodus. Legt fest, wie viele Elemente in eine Zeile passen. |
| **So viele wie möglich einpassen** | Nur im Rastermodus. Platziert so viele Elemente wie möglich in einer Zeile, statt eine feste Anzahl zu verwenden. **Mindestzellengröße** legt fest, wie viele Elemente hineinpassen. |

# Scrollen

Spieler scrollen mit dem Mausrad durch den Bereich. Halte `Shift` gedrückt, um horizontal zu scrollen.

- **Scrollrichtung** legt fest, ob der Bereich **Vertikal**, **Horizontal** oder **Beides** scrollt. In den Richtungen, in die nicht gescrollt wird, ist der Inhalt genau so groß wie der Bereich.
- Textelemente in einem Bereich scrollen zuerst. Sobald sie ihr Ende erreichen, scrollt der Bereich weiter.
- Wenn Spieler mit `Tab` zwischen Buttons wechseln, scrollt der Bereich zum ausgewählten Button.

Die Menüs **Scrollen**, **Automatisches Scrollen** und **Scrollleisten** bieten dieselben Einstellungen wie für Textelemente. Unter [Text in Menüs](/text-in-menus#scrolling-settings) findest du alle Einstellungen. Die Unterschiede:

- Bei **Einrasten** kann der Inhalt **An Elementen** ausgerichtet werden, sodass ein Element immer am Anfang des Bereichs steht, oder **An Seiten**.
- Buttons und alle anderen Elemente im Bereich bleiben auch dann funktionsfähig, wenn **Zum Scrollen ziehen** aktiviert ist.
- Die Scrollgriffe sind Pixel-Griffe, sofern du ihnen keine eigenen **Scrollgriff-Texturen** oder eine **Scrollgriff-Farbe [HEX]** zuweist.

# Hintergrund

Bereiche zeichnen hinter ihrem Inhalt ein Panel. Öffne **Hintergrund**, um es zu ändern. Die Einstellungen funktionieren wie beim [Hintergrund von Textelementen](/text-in-menus#background): Du kannst ihn mit **Hintergrund anzeigen** deaktivieren, eine eigene Textur mit [Neunerteilung](/nine-slicing-and-tiling) oder Kachelung verwenden und mit **Innenabstand** festlegen, wie weit er reicht.

# Mit Aktionen scrollen

Du kannst Bereiche auch von anderen Teilen von FancyMenu aus steuern und ihren Zustand abfragen:

- Die [Aktion](/action-scripts) **Element scrollen** scrollt einen Bereich zum Anfang, zum Ende, zu einer Position oder zu einem der darin enthaltenen Elemente.
- Die [Platzhalter](/placeholders) **Element-Scrollposition**, **Element-Scrollprozentsatz** und **Element-Inhaltsgröße** geben an, wie weit der Bereich gescrollt ist und wie groß sein Inhalt ist.
- Die [Anforderung](/conditions) **Ist Element bis zum Ende gescrollt** prüft, ob der Bereich bis zum Ende gescrollt wurde.
- Die [Listener](/listeners) **Bei Scrollen des Elements**, **Bei Scrollen des Elements zum Anfang** und **Bei Scrollen des Elements zum Ende** führen Aktionen aus, während der Bereich scrollt.

Für all diese Funktionen brauchst du den [Elementbezeichner](/element-identifiers) des Bereichs. Dieses Beispiel zeigt, wie weit ein Bereich gescrollt ist, als Wert zwischen 0 und 100:

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"3f2a9c1e-7b4d-4e8a-9c2f-1d5e6a7b8c9d-1763950000000","axis":"vertical"}}
```

# Gut zu wissen

- Wenn du einen Bereich ausblendest, wird alles darin ebenfalls ausgeblendet. Die Deckkraft eines Bereichs gilt auch für alle darin enthaltenen Elemente.
- Bereiche können nicht gedreht oder geneigt werden. Parallaxe funktioniert weder für Bereiche noch für die darin enthaltenen Elemente.
- Tooltip-Elemente in einem Bereich werden an dessen Rändern abgeschnitten, sofern sie nicht der Maus folgen.
