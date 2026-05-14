---
title: Dekorations-Overlays
description: Füge Menüs im FancyMenu-Layout-Editor vollflächige visuelle Overlays hinzu.
---

# Dekorations-Overlays

Dekorations-Overlays sind Vollbild-Effekte, die vor deinen Menüelementen gerendert werden.

Sie sind nützlich, wenn du einem Menü Atmosphäre oder Bewegung hinzufügen möchtest, ohne diese Effekte manuell zu erstellen.

Typische Beispiele:

- Füge **Schneefall** für ein Wintermenü mit Schneeansammlung hinzu.
- Füge **Regenfall** für einen stürmischen Look mit Pfützen und Tropfen hinzu.
- Füge **Glühwürmchen** für ein ruhiges, nächtliches Menü hinzu.
- Füge **Lichterketten** für festliche oder dekorative Menü-Themen hinzu.
- Füge **Blätter**, **Feuerwerk** oder **Konfetti** für saisonale/Event-Menüs hinzu.
- Füge das **Browser**-Overlay hinzu, um eine Vollbild-Webseiten-/Video-Ebene anzuzeigen.

# Wo du es findest

Öffne ein Layout im Layout-Editor, klicke dann mit der rechten Maustaste auf den Editor-Hintergrund und öffne **Dekorations-Overlays**.

# Schnellstart

1. Öffne ein Layout im Layout-Editor.
2. Klicke mit der rechten Maustaste auf den Hintergrund (leerer Bereich).
3. Öffne **Dekorations-Overlays**.
4. Wähle einen Overlay-Typ aus.
5. Setze **Overlay anzeigen** auf **Aktiviert**.
6. Konfiguriere die Overlay-Einstellungen.
7. Speichere das Layout und teste den Bildschirm.

# Wie Overlay-Typen funktionieren

Jeder Overlay-Typ hat sein eigenes Untermenü und seinen eigenen **Overlay anzeigen**-Schalter.

- Du kannst nur die Typen aktivieren, die du möchtest.
- Du kannst mehrere aktivierte Typen in einem Layout kombinieren.
- Die Einstellungen gelten pro Overlay-Typ (zum Beispiel Farbe, Intensität, Geschwindigkeit, Dichte, Skalierung, besonderes Verhalten).

> [!INFO]
> Es ist möglich, mehrere Instanzen desselben Overlay-Typs zu stapeln, indem du mehrere Layouts mit demselben aktivierten Typ verwendest.

# Overlay-Typen

- **Schneefall**: Schneefall mit optionaler Schneeansammlung auf Oberflächen/Buttons.
- **Regenfall**: Regen mit optionalen Pfützen, Tropfen und optionalen Gewitterblitzen.
- **Glühwürmchen**: Bewegliche Glühwürmchengruppen mit konfigurierbarer Gruppenzahl, Dichte, Größe und Farbe.
- **Lichterketten**: Konfigurierbare Lichterketten-Kombinationen, Lichtfarben, Wind-/Flackerverhalten und Feiertags-Farbmodus.
- **Blätter**: Fallende Blätter mit konfigurierbaren Farben, Wind, Geschwindigkeit, Skalierung und Dichte.
- **Feuerwerk**: Häufiges Feuerwerk mit konfigurierbarer Anzahl, Explosionsgröße und Skalierung.
- **Konfetti**: Konfetti-Regen mit optionalem Konfetti-Modus per Mausklick.
- **Browser**: Vollbild-Browser-Overlay mit URL- und Medien-Einstellungen.
- **GLSL-Shader**: Vollbild-Overlay für benutzerdefinierte Shader (für animierte oder statische shaderbasierte Visuals).

# Browser-Overlay: Interaktiv vs. Passiv

Das Browser-Overlay kann entweder als interaktiver Browser oder als passive visuelle Ebene konfiguriert werden.

- Die Einstellungen **Maus/Tastatur verarbeiten** steuern, ob der Browser selbst Eingaben verarbeitet.
- Die Einstellungen **Maus/Tastatur abfangen** steuern, ob Eingaben vom Menü dahinter blockiert werden.

Praktische Beispielkonfigurationen:

- Interaktiver Browser im Vordergrund: sowohl **Verarbeiten** als auch **Abfangen** aktivieren.
- Browser-Ebene nur zur Anzeige: **Verarbeiten** deaktivieren und **Abfangen** deaktivieren.

> [!IMPORTANT]
> Das Browser-Dekorations-Overlay erfordert das **MCEF**-Mod.
