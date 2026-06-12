---
title: Erweiterte Positionierung & Größenanpassung
description: >-
  Wie man die erweiterte Positionierung und Größenanpassung von Elementen
  verwendet.
---
# Erweiterte Positionierung & Größenanpassung

Die erweiterte Positionierung/Größenanpassung ermöglicht dir, **volle Kontrolle über Position und Größe deiner Elemente** zu haben. Das ist sehr leistungsstark, aber auch **deutlich zeitaufwändiger** als die automatische Größenanpassung und Positionierung von FancyMenu.

> Wenn du nur möchtest, dass Elemente besser mit der **GUI-Skalierung** von Minecraft mitwachsen, wird empfohlen, stattdessen das layoutweite **Auto-Scaling** zu verwenden. Dies kann aktiviert werden, indem du zuerst eine GUI-Skalierung im Menü erzwingst, das sich öffnet, wenn du mit der rechten Maustaste auf den Hintergrund des Editors klickst, und dann im selben Menü **Auto-Scaling** aktivierst.
{.is-warning}


# Erweiterte Positionierungs-/Größenanpassungsmodus umschalten

Um die **erweiterte Positionierung/Größenanpassung** für ein Element zu **aktivieren**, klicke es mit der **rechten Maustaste** an und wähle **Erweiterte Positionierung** oder **Erweiterte Größenanpassung**.
Das Element wechselt automatisch in den erweiterten Modus, wenn du einen erweiterten Positions- oder Größenwert setzt.

Um sie zu **deaktivieren** und zur normalen Positionierung/Größenanpassung zurückzukehren, **entferne alle Werte für Positionierung/Größenanpassung**.

> Während sich ein Element im Modus für erweiterte Größenanpassung/Positionierung befindet, kann das Ändern der Größe und/oder das Verschieben des Elements deaktiviert oder eingeschränkt sein.
{.is-warning}

# Positionen/Größen berechnen

Der Grund, warum die erweiterte Positionierung/Größenanpassung so leistungsstark ist, liegt darin, dass du **Platzhalter** in den Positions-/Größenwerten verwenden kannst.

Dadurch kannst du den **Calculator**-Platzhalter (zu finden in der Platzhalterkategorie **Erweitert**) zusammen mit Platzhaltern der Kategorie **GUI** verwenden, wie z. B. **Bildschirmbreite**, **GUI-Skalierung**, **Elementbreite** und mehr.

> Du kannst Platzhalter hinzufügen, indem du oben rechts im Texteditor auf die Schaltfläche **Platzhalter** klickst. Wenn du diese Schaltfläche nicht siehst, unterstützt der Inhalt, den du bearbeiten möchtest, **keine** Platzhalter.
{.is-info}

Um mit dem **Calculator**-Platzhalter etwas zu berechnen, ersetze den Beispielausdruck durch deinen eigenen. Du kannst im Ausdruck verschachtelte Platzhalter verwenden, sodass du dort die Bildschirmgröße, Elementgröße usw. einsetzen kannst.

Zum Beispiel löst dieser Platzhalter einfach `1 + 1` und wird später als `2` angezeigt:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Die Variable `decimal` ist auf `false` gesetzt, was für die meisten Berechnungen von Größen/Positionen wichtig ist. Setze sie daher bei der Arbeit mit erweiterter Positionierung/Größenanpassung immer auf `false`.

Der folgende Calculator verwendet den Platzhalter **Bildschirmbreite** und teilt ihn durch `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> Während **Erweiterte Positionierung** aktiviert ist, werden der **Anker** und alle anderen positionsbezogenen Funktionen des Elements **ignoriert**. Die erweiterte Positionierung verwendet immer die linke obere Ecke (X0 Y0) als Ursprung, genau so, wie es die standardmäßige Minecraft-GUI-Logik tut. Die einzige Einstellung, die die erweiterte Positionierung berücksichtigt, ist **Auf dem Bildschirm bleiben**.
