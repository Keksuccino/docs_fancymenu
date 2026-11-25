---
title: Elemente positionieren
description: So verwendest du Ankerpunkte richtig.
sourceBlobSha: c6c6b53374ed720fcdc32a3a0fbc1784f202cc5a
---

# Elemente in FancyMenu positionieren

In FancyMenu wird die Position jedes Elements durch **Ankerpunkte** bestimmt. Diese Punkte werden benötigt, um zu berechnen, wo ein Element auf dem Bildschirm erscheinen soll. So wird verhindert, dass sich Elemente überlappen, aus dem sichtbaren Bereich geraten oder sich beim Ändern der Fenstergröße falsch bewegen.

## Ankerpunkte verstehen

Ankerpunkte dienen als Ausgangspunkt, von dem aus die Position eines Elements berechnet wird. Standardmäßig sind Elemente, die du zu Layouts hinzufügst, mit dem Ankerpunkt **„Bildschirmmitte“** verknüpft. Dieser Anker liegt genau in der Mitte des Bildschirms, unabhängig von der Fenstergröße.

Wenn ein Element beispielsweise mit dem Anker **„Bildschirmmitte“** verknüpft ist und sich 2 Zentimeter von der Bildschirmmitte entfernt befindet, behält es diesen Abstand unabhängig von Änderungen der Fenstergröße bei.

## Mit Ankerpunkten arbeiten

Wenn du ein Element im Editor ziehst, wird der Ankerpunkt hervorgehoben, mit dem es verbunden ist. Standardmäßig werden dabei auch alle anderen verfügbaren Ankerpunkte angezeigt. Du kannst den Anker eines Elements ändern, indem du es über einen anderen Ankerpunkt ziehst und wartest, bis der Ladebalken vollständig gefüllt ist.

![Darstellung von Ankerpunkten](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Elemente an anderen Elementen verankern

Ein Element kann ein anderes Element als Anker verwenden. Es bewegt sich dann zusammen mit diesem Element und behält seinen Abstand zu dessen linker oberer Ecke bei. Das ist praktisch für aus mehreren Elementen bestehende Bedienfelder, für eine Beschriftung neben einer Vanilla-Schaltfläche und für [Draggers](/dragger).

Dafür gibt es zwei Möglichkeiten. Bei beiden bleibt das Element an seiner aktuellen Position.

### Durch Ziehen

1. Ziehe das Element und halte den Zeiger über dem anderen Element.
2. Warte, bis der Balken vollständig gefüllt ist, und lasse dann los.

Befindet sich der Zeiger schon über dem anderen Element, wenn du mit dem Ziehen beginnst, bewege ihn einmal vom Element weg und wieder zurück. Elemente, die sich bereits zu Beginn unter dem Zeiger befinden, werden nicht berücksichtigt.

Dafür müssen **Ankerbereich beim Darüberhalten** und **Ankerelement beim Darüberhalten** im Menü **Fenster** aktiviert sein. Beide Optionen sind standardmäßig eingeschaltet. Die erste aktiviert oder deaktiviert das Verankern durch Gedrückthalten, die zweite fügt andere Elemente zu den Ankerpunkten hinzu. Mit **Ladezeit für das Darüberhalten über Ankerbereich/-element (Sekunden)** im selben Menü legst du fest, wie lange du die Maustaste gedrückt halten musst. Der Standardwert beträgt 2 Sekunden.

### Über die ID

1. Klicke mit der rechten Maustaste auf das andere Element und wähle **Element-ID kopieren**.
2. Klicke mit der rechten Maustaste auf das Element und wähle **Ankerpunkt -> Anderes Element**.
3. Füge die ID in **Element-ID** ein und klicke auf **Fertig**.

Wenn mehrere Elemente ausgewählt sind, werden in Schritt 2 und 3 alle gleichzeitig verankert. Weitere Informationen zu IDs findest du unter [Elementkennungen](/element-identifiers).

## Anker in scrollbaren Bereichen

Elemente in einem [scrollbaren Bereich](/scrollable-areas) haben ebenfalls Anker, diese gehören jedoch zum Inhalt des Bereichs und nicht zum Bildschirm:

- Die **linke obere Ecke** ist die linke obere Ecke des Inhalts, die **Bildschirmmitte** dessen Mitte und die unteren Anker liegen am Ende des Inhalts. So kann ein Element ganz am Ende einer langen Liste platziert werden und dort bleiben, wenn die Liste länger wird.
- Elemente in einem Bereich können nur andere Elemente desselben Bereichs als Anker verwenden.
- Wenn du ein Element in einen Bereich hinein- oder aus ihm herausbewegst, erhalten Elemente, deren Anker über dessen Grenze hinweg verbunden waren, den Anker **Linke obere Ecke** und bleiben an ihrer Position.

Das funktioniert im Modus **Anker** des Bereichs. In den anderen Modi platziert der Bereich die Elemente selbst. Siehe [Scrollable Areas](/scrollable-areas#anchors-mode).

## Beispiel für das Verankern von Elementen

Der folgende Screenshot zeigt, wie du Anker für Elemente auswählen solltest.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Alle Elemente, die in der Bildschirmmitte bleiben sollen (Schaltflächen und Spielerfigur), sind am Ankerpunkt **Bildschirmmitte** verankert.

Die Schaltflächen in der linken oberen Ecke sind am Anker **Linke obere Ecke** verankert, da sie dort bleiben sollen.

Das Textelement in der linken unteren Ecke ist am Ankerpunkt **Linke untere Ecke** verankert, da es dort bleiben soll.

Das Bildelement in der rechten unteren Ecke ist am Ankerpunkt **Rechte untere Ecke** verankert, da es dort bleiben soll.

## Elemente aus dem sichtbaren Bereich bewegen

Standardmäßig können Elemente nicht aus dem sichtbaren Bereich bewegt werden. Das dient als Sicherheitsvorkehrung, falls ein Layout in einem extrem kleinen oder ungewöhnlich großen Fenster geladen wird. So bleiben die Elemente sichtbar und können weiterhin bedient werden.

Sie bleiben immer auf dem Bildschirm und halten einen kleinen Abstand zu dessen Rändern.

Du kannst diese Funktion für einzelne Elemente **deaktivieren**, indem du mit der **rechten Maustaste** darauf klickst und anschließend **Auf dem Bildschirm halten** deaktivierst.

> [!WARNING]
> Wenn du diese Option deaktivierst, kann das Element manchmal verschwinden, weil seine tatsächliche Position außerhalb des Bildschirms liegt und die Funktion es zuvor sichtbar gehalten hat. Sollte das passieren, **mache** die letzte Aktion (das Deaktivieren von **Auf dem Bildschirm halten**) über die Rückgängig-Tastenkombination oder über **Menüleiste -> Bearbeiten -> Rückgängig** rückgängig. Bewege das Element anschließend manuell in die Bildschirmmitte und deaktiviere **Auf dem Bildschirm halten** erneut. Nun sollte es auch bei deaktivierter Funktion sichtbar bleiben.

## Elemente zentrieren

Solange Elemente eine feste Größe haben, ist es ganz einfach, sie zu zentrieren: Verankere sie an einem Ankerpunkt, der auf der Mitte basiert.

Wenn sich die Größe eines Elements dynamisch abhängig von Bedingungen oder anderen Faktoren ändert, ist es etwas kniffliger. Dafür bietet FancyMenu jedoch eine praktische Funktion! Verankere das Element zunächst an einem Ankerpunkt, der auf der Mitte basiert, und klicke dann mit der rechten Maustaste darauf. Aktiviere im Kontextmenü **Anker fixieren**. Diese Funktion ändert, wie FancyMenu die Position des Elements berechnet. Dadurch behält das Element immer denselben Abstand zu seinem Ankerpunkt, unabhängig davon, ob sich seine Größe ändert. Bei Ankern, die auf der Mitte basieren, behält das Element immer denselben Abstand von seinem absoluten Mittelpunkt zum Anker bei und bleibt dadurch bei Verwendung solcher Anker stets zentriert. (Bei linksbasierten Ankern behält es immer denselben Abstand zwischen seiner linken Seite und dem Anker bei, bei rechtsbasierten Ankern denselben Abstand zwischen seiner rechten Seite und dem Anker.)

## Weitere Möglichkeiten zur Verbesserung der Elementpositionierung

Wenn **alle Ankerpunkte richtig gesetzt sind**, sich deine Elemente aber bei zu kleinem Fenster weiterhin überlappen, ist dein Layout möglicherweise einfach zu voll für die normale GUI-Skalierung von Minecraft.

### GUI-Skalierung erzwingen

Eine Möglichkeit, die Positionierung der Layoutelemente zu verbessern, besteht darin, für das Menü eine GUI-Skalierung zu erzwingen. Klicke dazu mit der **rechten Maustaste auf den Hintergrund des Editors** und wähle **GUI-Skalierung erzwingen**. Dadurch hat das Menü immer dieselbe GUI-Skalierung, unabhängig davon, welche Skalierung in den Minecraft-Optionen eingestellt ist.

### Automatische Skalierung

Die letzte Möglichkeit, Überlappungen zu beheben, ist die **automatische Skalierung**.
Diese Einstellung skaliert das Menü automatisch anhand der Fenstergröße, damit die Positionen der Elemente beim Ändern der Fenstergröße möglichst gut erhalten bleiben. Aktiviere die automatische Skalierung, indem du mit der **rechten Maustaste auf den Hintergrund des Editors** klickst und anschließend **Automatische Skalierung** auswählst.

> [!WARNING]
> Die **automatische Skalierung** kann dazu führen, dass von Minecraft gerenderter **Text schlecht aussieht**. Das ist kein Fehler, sondern liegt daran, wie Minecraft Text rendert. Bei Schaltflächen kannst du das umgehen, indem du die Beschriftung in die Hintergrundtextur der Schaltfläche integrierst und eine leere normale Schaltflächenbeschriftung festlegst.
