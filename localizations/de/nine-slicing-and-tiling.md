---
title: 9-Slicing und Kachelung
description: >-
  Lass Texturen mit Rahmen in jede Größe passen, ohne sie zu verzerren, oder
  wiederhole ein Muster, statt es zu strecken.
sourceBlobSha: 0dca8e7070606cdafccd9edc23a77535048d4ba3
---

# 9-Slicing und Kachelung

Eigene Texturen werden auf die Größe des Elements gestreckt. Bei Fotos ist das in Ordnung, aber Rahmen, Bereiche und Schaltflächen mit Rändern wirken verzerrt, wenn sie breiter oder höher werden. Zwei Einstellungen schaffen Abhilfe:

- 9-Slicing erhält die Form der Ecken und Kanten einer Textur und füllt nur die Mitte aus.
- Kachelung wiederholt eine Textur, statt sie zu strecken, sodass ein Muster seine Größe behält.

<img width="800" alt="Eine quadratische Paneltextur, die durch vier Linien in neun Teile geteilt ist, und dieselbe Textur als breites Panel, bei dem Ecken und Kanten ihre Form behalten" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png">

# So funktioniert 9-Slicing

Vier Linien teilen die Textur in neun Teile. Die vier Ecken behalten immer dieselbe Größe, die Kanten werden nur länger und die Mitte füllt den übrigen Bereich aus.

1. Lege deine Textur fest.
2. Aktiviere die 9-Slice-Einstellung. Den Namen findest du unter [Wo es funktioniert](#where-it-works).
3. Lege die Randbreiten entsprechend der Dicke des Textrahmens fest, gemessen in Pixeln der Textur. Bei einem 4 Pixel dicken Rahmen verwendest du `4`.

Gut zu wissen:

- Die Ränder werden auf dem Bildschirm genauso groß dargestellt wie in der Textur. Eine Textur mit 40 Pixel breiten Rändern wirkt daher auf einer kleinen Schaltfläche klobig. Die Textur sollte ungefähr so groß sein wie das Element.
- Die meisten Texturen haben eine Einstellung für den linken und rechten Rand (X-Ränder) und eine für den oberen und unteren Rand (Y-Ränder). Bei Fortschrittsbalken, Tooltips und globalen Anpassungen gibt es für jede Seite eine eigene Einstellung.
- Ränder, die für die Textur zu groß sind, werden automatisch verkleinert.

# Wo es funktioniert

| Textur | 9-Slicing | Kachelung |
|---|---|---|
| [Schaltflächen](/elements#button), unter **Schaltflächentexturen** | **Benutzerdefinierten Hintergrund in 9-Slice aufteilen** | - |
| [Schieberegler](/elements#slider), unter **Schieberegler-Texturen** | **Benutzerdefinierten Hintergrund in 9-Slice aufteilen** und **Benutzerdefinierten Griff in 9-Slice aufteilen** | - |
| [Bildelemente](/elements#image) | **Textur in 9-Slice aufteilen** | **Textur wiederholen** |
| Der **Hintergrund** von [Textelementen](/text-in-menus#background) und [scrollbaren Bereichen](/scrollable-areas#background) | **Benutzerdefinierten Hintergrund in 9-Slice aufteilen** | **Textur kacheln** |
| **Hintergründe von Bildlaufleisten** bei Textelementen und scrollbaren Bereichen | immer aktiv | - |
| Der **Hintergrund** von [Tooltip-Elementen](/elements#tooltip) | immer aktiv; Größen unter **9-Slicing-Einstellungen** | - |
| [Fortschrittsbalken-Texturen](/elements#progress-bar) | **Balkentextur in 9-Slice aufteilen** und **Hintergrundtextur in 9-Slice aufteilen** | - |
| [Globale Texturen für Schaltflächen und Schieberegler](/global-customizations#buttons-and-sliders) | **Schaltflächenhintergründe in 9-Slice aufteilen**, **Schiebereglerhintergrund in 9-Slice aufteilen** und **Schiebereglergriff in 9-Slice aufteilen** | - |
| [Hintergründe von Bildmenüs](/menu-backgrounds#image) | - | **Textur wiederholen** |
| Kopf- und Fußzeilen von [scrollbaren Bildschirmen](/customizing-scrollable-screens) | - | **Kopfzeilentextur wiederholen** und **Fußzeilentextur wiederholen** |

## Hintergründe von Textelementen und scrollbaren Bereichen

Öffne **Hintergrund** im Rechtsklickmenü eines Textelements oder scrollbaren Bereichs:

- **Benutzerdefinierte Hintergrundtextur** ersetzt das integrierte dunkle Panel durch deine eigene Textur. Setze die Einstellung zurück, um das Panel wiederherzustellen.
- **Benutzerdefinierten Hintergrund in 9-Slice aufteilen** ist standardmäßig aktiviert. Lege die Ränder mit **9-Slice-Hintergrund: X-Ränder (links und rechts)** und **9-Slice-Hintergrund: Y-Ränder (oben und unten)** fest.
- **Textur kacheln** wiederholt deine Textur, statt sie zu strecken. Zusammen mit 9-Slicing werden die Kanten und die Mitte wiederholt, während die Ecken unverändert bleiben.
- **Hintergrund anzeigen** deaktiviert den gesamten Hintergrund.

## Hintergründe von Bildlaufleisten

Öffne **Bildlaufleisten -> Hintergründe von Bildlaufleisten** bei einem Textelement oder scrollbaren Bereich. **Textur der vertikalen Leiste** und **Textur der horizontalen Leiste** zeigen eine Textur entlang des Bewegungswegs des Bildlaufgriffs an. Sie werden immer in 9-Slice aufgeteilt, damit ihre Enden bei Leisten jeder Länge ihre Form behalten. Lege die Ränder mit den beiden darunterliegenden Randeinstellungen fest.

# So funktioniert die Kachelung

Bei der Kachelung wird die Textur in ihrer Originalgröße so oft nebeneinander platziert, wie es passt. Verwende eine nahtlose Textur, bei der die linke Kante zur rechten und die obere zur unteren passt. Andernfalls sind Linien zwischen den Kacheln zu sehen.

Bei Bildelementen funktionieren **Textur wiederholen** und **Textur in 9-Slice aufteilen** nicht gleichzeitig. Wenn beide aktiviert sind, wird das Bild wiederholt.
