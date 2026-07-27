---
title: Erweiterte Positionierung & Größenanpassung
description: >-
  Wie man die erweiterte Positionierung und Größenanpassung von Elementen
  verwendet.
---
# Erweiterte Positionierung & Größenanpassung

Die erweiterte Positionierung und Größenanpassung gibt dir direkte Kontrolle über die Koordinaten und Abmessungen von Elementen.

> [!WARNING]
> Für die Anpassung an die GUI-Skalierung probiere zuerst die layoutweite **Auto-Skalierung**. Klicke mit der rechten Maustaste auf den Hintergrund des Editors, erzwinge eine GUI-Skalierung und aktiviere dann **Auto-Skalierung** im selben Menü.


# Erweiterte Positionierungs-/Größenanpassungsmodus umschalten

Um die erweiterte Positionierung oder Größenanpassung für ein Element zu aktivieren, klicke **mit der rechten Maustaste** darauf und wähle **Erweiterte Positionierung** oder **Erweiterte Größenanpassung**.
Das Element wechselt automatisch in den erweiterten Modus, wenn du einen erweiterten Positions- oder Größenwert festlegst.

Um es zu **deaktivieren** und zur normalen Positionierung/Größenanpassung zurückzukehren, **lösche alle Positions-/Größenwerte**.

> [!WARNING]
> Während sich ein Element im Modus für erweiterte Größenanpassung/Positionierung befindet, kann das Ändern der Größe und/oder das Verschieben des Elements deaktiviert oder eingeschränkt sein.

# Positionen/Größen berechnen

Erweiterte Positions- und Größenwerte unterstützen [Platzhalter](./placeholders).

Dadurch kannst du den [**Rechner**](./placeholders#calculator-calc)-Platzhalter mit GUI-Platzhaltern wie [**Bildschirmbreite**](./placeholders#screen-width-guiwidth), [**GUI-Skalierung**](./placeholders#gui-scale-guiscale) und [**Elementbreite**](./placeholders#element-width-elementwidth) kombinieren.

> [!NOTE]
> Du kannst Platzhalter hinzufügen, indem du oben rechts im Texteditor auf die Schaltfläche **Platzhalter** klickst. Wenn du diese Schaltfläche nicht siehst, unterstützt der Inhalt, den du bearbeiten möchtest, **keine** Platzhalter.

Um etwas mit dem [**Rechner-Platzhalter**](./placeholders#calculator-calc) zu berechnen, ersetze den Beispielausdruck durch deinen eigenen. Verschachtelte Platzhalter können Bildschirm- oder Elementabmessungen liefern.

Dieses Beispiel gibt `2` zurück:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Lasse `decimal` auf `false`, um Berechnungen für ganze Pixel bei Position und Größe zu erhalten.

Der folgende Rechner verwendet den [**Bildschirmbreite**-Platzhalter](./placeholders#screen-width-guiwidth) und teilt ihn durch `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Erweiterte Positionierung** ignoriert den Anker des Elements und verwendet die obere linke Bildschirmecke (`X0 Y0`) als Ursprung. **Auf dem Bildschirm bleiben** gilt weiterhin.
