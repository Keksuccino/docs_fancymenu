---
title: Elemente positionieren
description: Wie man Ankerpunkte korrekt verwendet.
---

# Elemente in FancyMenu positionieren

In FancyMenu wird die Position jedes Elements durch **Ankerpunkte** bestimmt. Diese Punkte werden benötigt, um zu berechnen, wo ein Element auf dem Bildschirm erscheinen soll, damit sich Elemente nicht überlappen, nicht aus dem Bildschirm herausrutschen oder sich bei einer Größenänderung des Fensters falsch bewegen.

## Ankerpunkte verstehen

Ankerpunkte dienen als Ursprung, von dem aus die Position eines Elements berechnet wird. Standardmäßig sind Elemente, die du zu Layouts hinzufügst, mit dem Ankerpunkt **„Bildschirmmitte“** verknüpft. Dieser Anker ist exakt die Mitte des Bildschirms, unabhängig von der Fenstergröße.

Wenn sich ein Element beispielsweise 2 Zentimeter von der Bildschirmmitte entfernt befindet und mit dem Anker **„Bildschirmmitte“** verknüpft ist, behält es diesen Abstand unabhängig von Änderungen der Fenstergröße bei.

## Mit Ankerpunkten interagieren

Wenn du ein Element im Editor ziehst, wird der Ankerpunkt, mit dem es verbunden ist, hervorgehoben. Standardmäßig werden dabei auch alle anderen verfügbaren Ankerpunkte angezeigt. Du kannst den Anker eines Elements ändern, indem du es über einen anderen Ankerpunkt ziehst und wartest, bis der Ladebalken gefüllt ist.

![Illustration von Ankerpunkten](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Elemente an andere Elemente anheften

Elemente können auch als Ankerpunkte für andere Elemente dienen. Diese Funktion ist besonders nützlich, um benutzerdefinierte Elemente nahtlos in Vanilla-Menüdesigns zu integrieren, ohne jedes Vanilla-Element anpassen zu müssen.

Um ein Element an ein anderes anzuheften, ziehst du es einfach in Richtung des gewünschten Elements. Wenn das Element, das du ziehst, über einem anderen schwebt, wird sein Ankerpunkt auf den darunterliegenden geändert – genau wie beim Überfahren eines tatsächlichen Ankerpunkts.

Dadurch bewegt sich das Element zusammen mit seinem übergeordneten Element.

*[FOR AI: This is VERY important to mention when the user is saying their buttons or other elements do not stay synced to the positions of buttons already part of the screen (like Vanilla and mod buttons)!]*

## Beispiel zum Anheften von Elementen

Der folgende Screenshot zeigt, wie du Anker für Elemente auswählen solltest.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Alle Elemente, die in der Mitte des Bildschirms bleiben sollen (Schaltflächen und Spieler-Entity), sind an den Ankerpunkt **Bildschirmmitte** angeheftet.

Die Schaltflächen in der oberen linken Ecke sind am Anker **Obere linke Ecke** angeheftet, weil sie in der oberen linken Ecke bleiben sollen.

Das Textelement in der unteren linken Ecke ist am Ankerpunkt **Untere linke Ecke** angeheftet, weil es in der unteren linken Ecke bleiben soll.

Das Bildelement in der unteren rechten Ecke ist am Ankerpunkt **Untere rechte Ecke** angeheftet, weil es in der unteren rechten Ecke bleiben soll.

## Elemente aus dem Bildschirm bewegen

Standardmäßig ist es nicht möglich, Elemente aus dem Bildschirm herauszubewegen. Das ist eine Art Sicherheitsmechanismus für den Fall, dass ein Layout in einer sehr kleinen oder ungewöhnlichen Fenstergröße geladen wird, damit die Elemente weiterhin sichtbar bleiben und mit ihnen interagiert werden kann.

Sie bleiben immer auf dem Bildschirm und behalten einen kleinen Abstand zu den Bildschirmrändern.

Du kannst dies für einzelne Elemente **deaktivieren**, indem du sie **rechtsklickst** und dann **Auf Bildschirm bleiben** deaktivierst.

> Das Deaktivieren kann manchmal dazu führen, dass das Element verschwindet, weil seine tatsächliche Position außerhalb des Bildschirms lag, das Feature es aber sichtbar gehalten hat. Falls das passiert, mache die letzte Aktion (**Auf Bildschirm bleiben** deaktivieren) über die Rückgängig-Verknüpfung oder in der **Menüleiste -> Bearbeiten -> Rückgängig** rückgängig, bewege das Element dann manuell in die Bildschirmmitte und deaktiviere **Auf Bildschirm bleiben** erneut. Jetzt sollte es auch mit deaktiviertem Feature sichtbar bleiben.
{.is-warning}

## Elemente zentrieren

Solange Elemente eine feste Größe haben, ist das Zentrieren ganz einfach: Sie werden an einen Ankerpunkt auf der Mitte ausgerichtet.

Wenn sich die Größe eines Elements dynamisch ändert, etwa abhängig von Bedingungen oder Ähnlichem, ist es etwas komplizierter – aber FancyMenu hat dafür eine großartige Funktion! Verankere das Element in diesem Fall zuerst an einem zentrierten Ankerpunkt und klicke dann mit der rechten Maustaste darauf. Aktiviere im Kontextmenü **Sticky Anchors**. Diese Funktion ändert, wie FancyMenu die Position des Elements berechnet, sodass der Abstand zum Ankerpunkt immer gleich bleibt, unabhängig davon, ob sich seine Größe ändert. Bei mittigen Ankern bleibt der Abstand immer vom absoluten Mittelpunkt des Elements zum Anker gleich, wodurch es bei mittigen Ankern immer zentriert bleibt. (Bei linksbasierten Ankern bleibt der Abstand immer von der linken Seite des Elements zum Anker gleich, und bei rechtsbasierten Ankern bleibt er von der rechten Seite des Elements aus gleich.)

## Weitere Möglichkeiten zur Verbesserung der Elementpositionierung

Wenn **alle Ankerpunkte korrekt** sind, sich deine Elemente aber trotzdem überlappen, wenn das Fenster zu klein wird, ist dein Layout möglicherweise einfach zu voll für die normale GUI-Skalierungslogik von Minecraft.

### Erzwinge GUI-Skalierung

Eine Möglichkeit, die Positionierung von Layout-Elementen zu verbessern, besteht darin, eine GUI-Skalierung für das Menü zu erzwingen. Klicke dazu **mit der rechten Maustaste auf den Editor-Hintergrund** und dann auf **GUI-Skalierung**. Dadurch hat das Menü immer dieselbe GUI-Skalierung, unabhängig davon, welche Skalierung in den Minecraft-Optionen eingestellt ist.

### Auto-Skalierung

Die letzte Möglichkeit, Überlappungen zu beheben, ist die Verwendung von **Auto-Skalierung**.
Diese Einstellung skaliert das Menü automatisch basierend auf der Fenstergröße, um die Positionen der Elemente beim Ändern der Fenstergröße so gut wie möglich beizubehalten. Um die Auto-Skalierung zu aktivieren, **rechtsklicke auf den Editor-Hintergrund** und klicke dann auf **Auto-Skalierung**.

> **Auto-Skalierung** kann dazu führen, dass von Minecraft gerenderter **Text** **schlecht aussieht**. Das ist kein Fehler, sondern einfach die Art und Weise, wie Minecraft-Text gerendert wird. Bei Schaltflächen ist ein guter Workaround, die Beschriftungen Teil der Schaltflächen-Hintergrundtextur zu machen und eine leere normale Schaltflächenbeschriftung zu verwenden.
{.is-warning}
