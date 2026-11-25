---
title: Erweiterte Positionierung und Größenanpassung
description: >-
  So verwendest du die erweiterte Positionierung und Größenanpassung von
  Elementen.
sourceBlobSha: 205b887e844f770856bfd4836ea791e0acdca4b8
---
# Erweiterte Positionierung und Größenanpassung

Mit der erweiterten Positionierung und Größenanpassung kannst du die Koordinaten und Abmessungen von Elementen direkt steuern.

> [!WARNING]
> Für die Anpassung an verschiedene GUI-Skalierungen solltest du zuerst das layoutweite **Automatische Skalieren** ausprobieren. Klicke mit der rechten Maustaste auf den Editorhintergrund, erzwinge eine GUI-Skalierung und aktiviere anschließend im selben Menü **Automatisches Skalieren**.


# Erweiterten Positionierungs-/Größenanpassungsmodus umschalten

Um die erweiterte Positionierung oder Größenanpassung für ein Element zu aktivieren, klicke mit der **rechten Maustaste** darauf und wähle **Erweiterte Positionierung** oder **Erweiterte Größenanpassung**.
Das Element wechselt automatisch in den erweiterten Modus, sobald du einen erweiterten Positions- oder Größenwert festlegst.

Um den Modus zu **deaktivieren** und zur normalen Positionierung/Größenanpassung zurückzukehren, **lösche alle Positions-/Größenwerte**.

> [!WARNING]
> Wenn sich ein Element im Modus „Erweiterte Größenanpassung/Positionierung“ befindet, kann das Ändern seiner Größe und/oder Position deaktiviert oder eingeschränkt sein.

# Positionen/Größen berechnen

Erweiterte Positions- und Größenwerte unterstützen [Platzhalter](/placeholders).

So kannst du den Platzhalter [**Rechner**](/placeholders#calculator) mit GUI-Platzhaltern wie [**Bildschirmbreite**](/placeholders#screen-width), [**GUI-Skalierung**](/placeholders#gui-scale) und [**Elementbreite**](/placeholders#element-width) kombinieren.

> [!NOTE]
> Du kannst Platzhalter hinzufügen, indem du oben rechts im Texteditor auf die Schaltfläche **Platzhalter** klickst. Wenn diese Schaltfläche nicht angezeigt wird, **unterstützt** der Inhalt, den du bearbeiten möchtest, keine Platzhalter.

Um mit dem [Platzhalter **Rechner**](/placeholders#calculator) etwas zu berechnen, ersetze den Beispielausdruck durch deinen eigenen. Verschachtelte Platzhalter können Bildschirm- oder Elementabmessungen bereitstellen.

Dieses Beispiel gibt `2` zurück:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Lass `decimal` auf `false` gesetzt, damit Positionen und Größen in ganzen Pixeln berechnet werden.

Der folgende Rechner verwendet den Platzhalter [**Bildschirmbreite**](/placeholders#screen-width) und teilt den Wert durch `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Erweiterte Positionierung** ignoriert den Anker des Elements und verwendet die obere linke Bildschirmecke (`X0 Y0`) als Ursprung. **Auf dem Bildschirm halten** gilt weiterhin.
