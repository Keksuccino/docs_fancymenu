---
title: Spieler-Köpfe
description: Wie man den Kopf eines Spielers als 2D- oder 3D-Bild in einem Menü anzeigt.
---

# Spieler-Köpfe in Menüs

Um den Kopf eines Spielers mithilfe eines Image-Elements als 2D- oder 3D-Bild anzuzeigen, kannst du eine Web-API eines Drittanbieters namens „Minotar“ verwenden.

## 2D-Bild

### 1. Ein Image-Element hinzufügen

Klicke im FancyMenu-Editor mit der rechten Maustaste auf den Hintergrund, wähle „New Element“ und dann „Image“ (oder „Picture“).

### 2. Die Web-Quelle festlegen

Klicke mit der rechten Maustaste auf das Image-Element, um auf seine Eigenschaften zuzugreifen. Wähle für den Quellentyp „Web“.

### 3. Die URL mit dem richtigen Platzhalter zusammenstellen

In das Feld „Source“ würdest du die folgende URL eingeben:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu verwendet `{"placeholder":"playername"}`, um den aktuellen Benutzernamen des Spielers dynamisch in die URL einzufügen. So kann das Image-Element den Kopf von Minotar abrufen und anzeigen.

## 3D-Bild

Das ist dem 2D-Format ziemlich ähnlich, aber hier müssen wir eine andere URL verwenden:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

Die `200` ist hier die Pixelgröße. Wenn du also eine kleinere Version möchtest, ersetze sie einfach zum Beispiel durch `100`; für eine größere Version nimmst du entsprechend `300` und so weiter.
