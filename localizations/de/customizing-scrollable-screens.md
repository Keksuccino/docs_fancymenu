---
title: Scrollbare Bildschirme
description: Wie scrollbare Bildschirme angepasst werden.
---

# Scrollbare Bildschirme anpassen

Das Anpassen von scrollbaren Bildschirmen wie den Optionsbildschirmen kann etwas knifflig sein, da FancyMenu Inhalte innerhalb von Scrollbereichen nicht „sehen“ oder anpassen kann.

Seit FancyMenu v3.6.0+ ist es möglich, SOME dieser Bildschirme anpassbar zu machen, indem Widgets innerhalb von Scrollbereichen eines bestimmten Bildschirms automatisch sichtbar gemacht werden. Das ist sehr leistungsstark, aber auch noch recht experimentell, daher funktioniert es nicht auf allen Bildschirmen.

Um die Sichtbarmachungsfunktion für einen bestimmten Bildschirm zu aktivieren, klicke auf **Menüleiste -> Anpassung -> Inhalt des Scrollbereichs des aktuellen Bildschirms sichtbar machen**. Es ist nicht möglich, diese Funktion für alle Bildschirme auf einmal zu aktivieren, und einige Bildschirme erlauben sie überhaupt nicht, wie z. B. die Einzelspieler- und Mehrspieler-Menüs.

Wenn diese Funktion aktiviert wird, werden alle in Scrollbereichen gefundenen Widgets in der linken oberen Ecke des Bildschirms gestapelt. Das ist beabsichtigt und kein Fehler. Du kannst dann ein Layout **für den aktuellen Bildschirm** öffnen und solltest diese Widgets im Editor sehen und bearbeiten können (verschieben, Größe ändern usw.).

Das Wichtigste, das du bei der Verwendung dieser Funktion beachten solltest, ist, dass das Sichtbarmachen von Scrollbereich-Widgets den ursprünglichen Scrollbereich vom Bildschirm ENTFERNT, und alles innerhalb des Scrollbereichs, das kein normales Widget ist (Widgets sind Schaltflächen und Schieberegler), VERLOREN geht. Es wird also nicht sichtbar oder interaktiv sein, solange die Sichtbarmachungsfunktion aktiviert ist.
