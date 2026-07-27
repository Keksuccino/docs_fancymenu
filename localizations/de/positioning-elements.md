---
title: Elemente positionieren
description: Wie man Ankerpunkte korrekt verwendet.
---

# Elemente in FancyMenu positionieren

In FancyMenu wird die Position jedes Elements durch **Ankerpunkte** bestimmt. Diese Punkte werden benötigt, um zu berechnen, wo ein Element auf dem Bildschirm erscheinen soll. So wird sichergestellt, dass Elemente sich nicht überlappen, nicht aus dem Bildschirm rutschen und sich bei einer Größenänderung des Fensters nicht falsch verschieben.

## Ankerpunkte verstehen

Ankerpunkte dienen als Ursprung, von dem aus die Position eines Elements berechnet wird. Standardmäßig sind Elemente, die du zu Layouts hinzufügst, mit dem Ankerpunkt **„Bildschirmmitte“** verknüpft. Dieser Anker ist exakt die Mitte des Bildschirms, unabhängig von der Fenstergröße.

Wenn sich ein Element zum Beispiel 2 Zentimeter von der Bildschirmmitte entfernt befindet und mit dem Anker **„Bildschirmmitte“** verknüpft ist, behält es diesen Abstand unabhängig von Änderungen der Fenstergröße bei.

## Mit Ankerpunkten interagieren

Wenn du ein Element im Editor ziehst, wird der Ankerpunkt hervorgehoben, mit dem es verbunden ist. Standardmäßig werden dabei auch alle anderen verfügbaren Ankerpunkte angezeigt. Du kannst den Anker eines Elements ändern, indem du es auf einen anderen Ankerpunkt ziehst und wartest, bis der Ladebalken gefüllt ist.

![Illustration von Ankerpunkten](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Elemente an andere Elemente anheften

Elemente können auch als Ankerpunkte für andere Elemente dienen. Diese Funktion ist besonders nützlich, um benutzerdefinierte Elemente nahtlos in Vanilla-Menüdesigns zu integrieren, ohne jedes einzelne Vanilla-Element anpassen zu müssen.

Um ein Element an ein anderes anzuheften, ziehst du es einfach zum gewünschten Element. Wenn das gezogene Element über einem anderen schwebt, wird sein Ankerpunkt auf den darunterliegenden geändert – genau wie beim Überfahren eines echten Ankerpunkts.

Dadurch bewegt sich das Element zusammen mit seinem übergeordneten Element.

## Beispiel zum Anheften von Elementen

Der folgende Screenshot zeigt, wie du Anker für Elemente auswählen solltest.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Alle Elemente, die in der Bildschirmmitte bleiben sollen (Schaltflächen und Spieler-Entität), sind am Ankerpunkt **Bildschirmmitte** verankert.

Die Schaltflächen in der oberen linken Ecke sind am Anker **Obere linke Ecke** verankert, weil sie dort bleiben sollen.

Das Text-Element in der unteren linken Ecke ist am Ankerpunkt **Untere linke Ecke** verankert, weil es dort bleiben soll.

Das Bild-Element in der unteren rechten Ecke ist am Ankerpunkt **Untere rechte Ecke** verankert, weil es dort bleiben soll.

## Elemente aus dem Bildschirm bewegen

Standardmäßig ist es nicht möglich, Elemente aus dem Bildschirm zu bewegen. Das ist eine Art Sicherheitsmechanismus für den Fall, dass ein Layout in einer sehr kleinen oder ungewöhnlichen Fenstergröße geladen wird, damit die Elemente weiterhin sichtbar und bedienbar sind.

Sie bleiben immer auf dem Bildschirm und behalten einen kleinen Abstand zu den Bildschirmrändern.

Du kannst dies für einzelne Elemente **deaktivieren**, indem du sie mit der **rechten Maustaste** anklickst und dann **Auf Bildschirm bleiben** deaktivierst.

> [!WARNING]
> Das Deaktivieren kann manchmal dazu führen, dass das Element verschwindet, weil seine tatsächliche/echte Position außerhalb des Bildschirms lag, die Funktion es aber sichtbar gehalten hat. Falls das passiert, mache die letzte Aktion (**Auf Bildschirm bleiben** deaktivieren) mit der Rückgängig-Funktion oder über die **Menüleiste -> Bearbeiten -> Rückgängig** rückgängig. Bewege das Element dann manuell in die Mitte des Bildschirms und deaktiviere **Auf Bildschirm bleiben** erneut. Jetzt sollte es auch bei deaktivierter Funktion sichtbar bleiben.

## Elemente zentrieren

Solange Elemente eine feste Größe haben, ist das Zentrieren ganz einfach: Verankere sie an einem Ankerpunkt, der auf die Mitte bezogen ist.

Wenn das Element seine Größe dynamisch ändert, etwa abhängig von Bedingungen oder anderen Faktoren, wird es etwas komplizierter – aber FancyMenu hat dafür eine großartige Funktion! Verankere das Element in diesem Fall zuerst an einem auf die Mitte bezogenen Ankerpunkt und klicke dann mit der rechten Maustaste darauf. Aktiviere im Kontextmenü **Sticky Anchors**. Diese Funktion ändert, wie FancyMenu die Position des Elements berechnet, sodass es immer denselben Abstand zu seinem Ankerpunkt behält, unabhängig davon, ob sich seine Größe ändert. Bei mittig ausgerichteten Ankern bleibt der Abstand immer vom absoluten Mittelpunkt des Elements zum Anker gleich, wodurch es bei Verwendung mittiger Anker immer zentriert bleibt. (Bei linksbasierten Ankern bleibt der Abstand immer von der linken Seite des Elements zum Anker gleich, und bei rechtsbasierten Ankern bleibt er von der rechten Seite des Elements gleich.)

## Weitere Möglichkeiten zur Verbesserung der Elementpositionierung

Wenn **alle Ankerpunkte korrekt** sind, sich deine Elemente aber bei einem zu kleinen Fenster dennoch überlappen, ist dein Layout möglicherweise einfach zu voll für die normale GUI-Skalierungslogik von Minecraft.

### Erzwungene GUI-Skalierung

Eine Möglichkeit, die Positionierung der Layoutelemente zu verbessern, ist, eine GUI-Skalierung für das Menü zu erzwingen, indem du **den Hintergrund des Editors mit der rechten Maustaste anklickst** und **GUI-Skalierung erzwingen** auswählst. Dadurch hat das Menü immer dieselbe GUI-Skalierung, unabhängig davon, welche Skalierung in den Optionen von Minecraft eingestellt ist.

### Auto-Skalierung

Die letzte Möglichkeit, Überlappungen zu beheben, ist die Verwendung von **Auto-Skalierung**.
Diese Einstellung skaliert das Menü automatisch anhand der Fenstergröße, um die Elementpositionen beim Ändern der Fenstergröße so gut wie möglich beizubehalten. Um die Auto-Skalierung zu aktivieren, **klicke mit der rechten Maustaste auf den Hintergrund des Editors** und dann auf **Auto-Skalierung**.

> [!WARNING]
> **Auto-Skalierung** kann dazu führen, dass von Minecraft gerenderter **Text** **unschön aussieht**. Das ist kein Fehler, sondern einfach die Art, wie Minecraft Text rendert. Bei Schaltflächen ist ein guter Workaround, die Beschriftung Teil der Schaltflächen-Hintergrundtextur zu machen und eine leere normale Schaltflächenbeschriftung zu setzen.
