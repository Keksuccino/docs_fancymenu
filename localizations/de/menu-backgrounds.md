---
title: Menühintergründe
description: >-
  Wie benutzerdefinierte Menühintergründe (Bilder, Animationen) für Bildschirme
  festgelegt werden.
---

# Menühintergründe

FancyMenu ermöglicht es dir, benutzerdefinierte Hintergründe für Menüs festzulegen. Du kannst Bilder, animierte Texturen, Diashows, kubische Panoramen, Farben, Browser, Videos, GLSL-Shader und mehr verwenden.

# Einen Hintergrund festlegen

In FancyMenu 3.9.0+ erfolgt die Anpassung des Menühintergrunds direkt über das Kontextmenü des Layout-Editors:

1. Öffne den Layout-Editor.
2. Klicke mit der rechten Maustaste auf den Hintergrund des Editors.
3. Öffne **Menühintergründe**.
4. Aktiviere und konfiguriere die gewünschten Hintergrundtypen.

Zu den gängigen Hintergrundtypen gehören:

- Vanilla
- Bild
- Diashow
- Kubisches Panorama
- Farbe (HEX)
- Browser
- Video
- GLSL Shader
- Video [MCEF] (veraltet)
- und mehr..

Der alte Hintergrundtyp **Video [MCEF]** ist in FancyMenu 3.9.0 veraltet. Verwende für neue Layouts den neuen nativen **Video**-Hintergrund, der von Watermedia V3 unterstützt wird.

# Den benutzerdefinierten Hintergrund entfernen

Öffne **Menühintergründe** erneut und deaktiviere/entferne den benutzerdefinierten Hintergrundtyp, den du nicht mehr möchtest. Wenn kein benutzerdefinierter Hintergrundtyp aktiv ist, fällt der Bildschirm auf das normale Vanilla-Hintergrundverhalten zurück.

# Hintergründe stapeln

FancyMenu 3.9.0 erlaubt es, mehrere Menühintergrundtypen im selben Layout zu aktivieren. Aktive Hintergründe werden als Stapel gerendert, sodass du ein Basisbild oder Panorama mit halbtransparenten Überlagerungen, Browser-Ebenen, Shader-Ebenen, Parallax-Ebenen und anderen Effekten kombinieren kannst.

Wenn du außerdem mehrere Layouts aktiv hast, können sich auch deren Hintergrundstapel kombinieren. Um Layouts zu sortieren und sie in einer bestimmten Reihenfolge anzuzeigen, klicke mit der rechten Maustaste auf den Hintergrund des Editors und dann auf **Layout-Index**.

# Transparente Hintergründe

Da sich hinter den Hintergründen nichts befindet, ist es nicht möglich, den ganz unten liegenden Hintergrund transparent zu machen, da dies zu grafischen Fehlern führen würde. Für gestapelte Hintergrund-Setups ist Transparenz jedoch absolut möglich, solange der unterste Hintergrund vollständig deckend bleibt. So kannst du halbtransparente Hintergrundebenen über dem untersten Hintergrund verwenden.

Um ein Hintergrundbild halbtransparent zu machen, verwende einen Bildeditor deiner Wahl.

# Browser-Hintergründe

Der Hintergrundtyp **Browser** funktioniert wie das Browser-Element, füllt jedoch den gesamten Bildschirm aus und ist automatisch fokussiert. Das ist nützlich für Webinhalte im Vollbild, lokale HTML-Seiten oder Web-Video-Ebenen.

# GLSL-Shader-Hintergründe

Der Hintergrundtyp **GLSL Shader** rendert benutzerdefinierte GLSL-Shader und unterstützt eine Shader-Erstellung im Shadertoy-Stil. Auf der Seite [GLSL Shader API](/glsl-shader-api) findest du Informationen zu den unterstützten Uniforms und zur Shader-Struktur.
