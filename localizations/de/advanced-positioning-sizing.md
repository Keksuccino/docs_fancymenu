---
title: Erweiterte Positionierung & Größenanpassung
description: Wie man erweiterte Positionierung und Größenanpassung von Elementen verwendet.
---

# Erweiterte Positionierung & Größenanpassung

Die erweiterte Positionierung/Größenanpassung ermöglicht es dir, **volle Kontrolle über die Position und Größe deiner Elemente** zu haben. Das ist sehr leistungsfähig, aber auch **deutlich zeitaufwendiger** als die automatische Größen- und Positionsanpassung von FancyMenu.

> Wenn du nur möchtest, dass Elemente besser mit der **GUI-Skalierung** von Minecraft mitwachsen, empfiehlt es sich stattdessen, die bereichsweite **Auto-Skalierung** zu verwenden. Diese kannst du aktivieren, indem du zuerst eine GUI-Skalierung im Menü erzwingst, das sich per Rechtsklick auf den Editor-Hintergrund öffnet, und dann im selben Menü **Auto-Skalierung** aktivierst.
{.is-warning}


# Erweiterte Positionierungs-/Größenanpassungsmodus umschalten

Um die erweiterte Positionierung/Größenanpassung für ein Element zu **aktivieren**, klicke mit **Rechtsklick** darauf und dann auf **Erweiterte Positionierung** oder **Erweiterte Größenanpassung**.
Das Element wechselt automatisch in den erweiterten Modus, wenn du einen erweiterten Positions- oder Größenwert festlegst.

Um sie zu **deaktivieren** und zur normalen Positionierung/Größenanpassung zurückzukehren, **lösche alle Positions-/Größenwerte**.

> Während sich ein Element im Modus für erweiterte Größenanpassung/Positionierung befindet, kann das Ändern der Größe und/oder das Verschieben des Elements deaktiviert oder eingeschränkt sein.
{.is-warning}

# Positionen/Größen berechnen

Der Grund, warum die erweiterte Positionierung/Größenanpassung so leistungsfähig ist, liegt darin, dass du **Platzhalter** in den Positions-/Größenwerten verwenden kannst.

Dadurch kannst du den Platzhalter **Calculator** (in der Platzhalterkategorie **Erweitert**) zusammen mit Platzhaltern aus der Kategorie **GUI** verwenden, wie **Bildschirmbreite**, **GUI-Skalierung**, **Elementbreite** und mehr.

> Du kannst Platzhalter hinzufügen, indem du oben rechts im Texteditor auf die Schaltfläche **Platzhalter** klickst. Wenn du diese Schaltfläche nicht siehst, unterstützt der Inhalt, den du bearbeiten möchtest, **keine** Platzhalter.
{.is-info}

Um mit dem Platzhalter **Calculator** etwas zu berechnen, ersetze den Beispielausdruck durch deinen eigenen. Du kannst im Ausdruck verschachtelte Platzhalter verwenden und dort also Bildschirmgröße, Elementgröße usw. einbeziehen.

Zum Beispiel löst dieser Platzhalter einfach `1 + 1` und wird später als `2` angezeigt:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Die Variable `decimal` ist auf `false` gesetzt, was für die meisten Berechnungen von Größen und Positionen wichtig ist. Setze sie daher bei der Arbeit mit erweiterter Positionierung/Größenanpassung immer auf `false`.

Der folgende Calculator verwendet den Platzhalter **Bildschirmbreite** und teilt ihn durch `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`
