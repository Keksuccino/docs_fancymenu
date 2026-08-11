---
title: Menühintergründe
description: >-
  Wie man benutzerdefinierte Menühintergründe (Bilder, Animationen) für
  Bildschirme festlegt.
---
# Menühintergründe

FancyMenu ermöglicht es dir, benutzerdefinierte Hintergründe für Menüs festzulegen. Du kannst Bilder, animierte Texturen, Diashows, kubische Panoramen, Farben, Browser, Videos, GLSL-Shader und mehr verwenden.

# Einen Hintergrund festlegen

Die Anpassung des Menühintergrunds ist über das Kontextmenü des Layout-Editors verfügbar:

1. Öffne den Layout-Editor.
2. Klicke mit der rechten Maustaste auf den Hintergrund des Editors.
3. Öffne **Menühintergründe**.
4. Aktiviere und konfiguriere den/die gewünschte(n) Hintergrundtyp(en).

Zu den gängigen Hintergrundtypen gehören:

- Vanilla
- Bild
- Diashow
- Kubisches Panorama
- Farbe (HEX)
- Browser
- Video
- GLSL-Shader
- Video [Rinku] (veraltet)
- Zusätzliche Hintergrundtypen von Add-ons

Der alte Hintergrundtyp **Video [Rinku]** ist veraltet. Verwende für neue Layouts den [nativen **Video**-Hintergrund](./video), der von Watermedia V3 unterstützt wird.

# Den benutzerdefinierten Hintergrund entfernen

Öffne **Menühintergründe** erneut und deaktiviere bzw. entferne den benutzerdefinierten Hintergrundtyp, den du nicht mehr möchtest. Wenn kein benutzerdefinierter Hintergrundtyp aktiv ist, fällt der Bildschirm auf sein normales Vanilla-Hintergrundverhalten zurück.

# Hintergründe stapeln

Mehrere Menühintergrundtypen können in einem Layout aktiviert werden. Aktive Hintergründe werden als Stapel gerendert, sodass ein Basisbild oder Panorama mit transparenten Browser-, Shader-, Parallax- oder anderen Ebenen kombiniert werden kann.

Wenn du außerdem mehrere Layouts aktiv hast, können sich auch deren Hintergrundstapel kombinieren. Um Layouts zu sortieren und sie in einer bestimmten Reihenfolge anzuzeigen, klicke mit der rechten Maustaste auf den Hintergrund des Editors und dann auf **Layout-Index**.

# Transparente Hintergründe

FancyMenu rendert eine schwarze Hintergrundebene hinter aktiven benutzerdefinierten Hintergründen. Transparente Pixel im untersten Hintergrund zeigen daher Schwarz. Verwende einen deckenden Basis-Hintergrund und lege dann transparente Hintergründe darüber.

Um ein Hintergrundbild transparent zu machen, verwende einen Bildeditor deiner Wahl.

# Browser-Hintergründe

Der Hintergrundtyp **Browser** funktioniert wie das [Browser-Element](./elements#browser), füllt jedoch den gesamten Bildschirm und erhält automatisch den Fokus. Das ist nützlich für Webinhalte im Vollbild, lokale HTML-Seiten oder Web-Video-Ebenen.

# GLSL-Shader-Hintergründe

Der Hintergrundtyp **GLSL-Shader** rendert benutzerdefinierte GLSL-Shader und unterstützt eine Shadertoy-ähnliche Shader-Erstellung. Auf der Seite [GLSL Shader API](/glsl-shader-api) findest du die unterstützten Uniforms und die Shader-Struktur.
