---
title: Dekorations-Overlays
description: >-
  Füge Menüs im FancyMenu-Layout-Editor bildschirmfüllende visuelle Overlays
  hinzu.
---
# Dekorations-Overlays

Dekorations-Overlays sind bildschirmfüllende Effekte, die vor deinen Menüelementen gerendert werden.

Sie sind nützlich, wenn du einem Menü Atmosphäre oder Bewegung hinzufügen möchtest, ohne diese Effekte manuell zu erstellen.

# Wo du sie findest

Öffne ein Layout im Layout-Editor, klicke dann mit der rechten Maustaste auf den Hintergrund des Editors und öffne **Dekorations-Overlays**.

# Schnellstart

1. Öffne ein Layout im Layout-Editor.
2. Klicke mit der rechten Maustaste auf den Hintergrund (leere Fläche).
3. Öffne **Dekorations-Overlays**.
4. Wähle einen Overlay-Typ aus.
5. Setze **Overlay anzeigen** auf **Aktiviert**.
6. Konfiguriere die Overlay-Einstellungen.
7. Speichere das Layout und teste den Bildschirm.

# Wie Overlay-Typen funktionieren

Jeder Overlay-Typ hat ein eigenes Untermenü und einen eigenen **Overlay anzeigen**-Schalter.

- Du kannst nur die Typen aktivieren, die du möchtest.
- Du kannst mehrere aktivierte Typen in einem Layout kombinieren.
- Die Einstellungen gelten pro Overlay-Typ (z. B. Farbe, Intensität, Geschwindigkeit, Dichte, Skalierung, spezielles Verhalten).

> [!INFO]
> Es ist möglich, mehrere Instanzen desselben Overlay-Typs zu stapeln, indem du mehrere Layouts mit demselben aktivierten Typ verwendest.

# Overlay-Typen

- **Schneefall**: Schneefall mit optionaler Schneeansammlung auf Oberflächen/Schaltflächen.
- **Regenfall**: Regen mit optionalen Pfützen, Tropfen und optionalen Blitz-Effekten.
- **Glühwürmchen**: Bewegte Glühwürmchen-Gruppen mit konfigurierbarer Gruppenanzahl, Dichte, Größe und Farbe.
- **Lichterketten**: Konfigurierbare Lichtkombinationen, Lichtfarben, Wind-/Flackerverhalten und Farbmodus für Feiertage.
- **Blätter**: Fallende Blätter mit konfigurierbaren Farben, Wind, Geschwindigkeit, Skalierung und Dichte.
- **Feuerwerk**: Häufiges Feuerwerk mit konfigurierbarer Menge, Explosionsgröße und Skalierung.
- **Konfetti**: Konfettiregen mit optionalem Konfetti-Modus bei Mausklicks.
- **Buddy**: Ein interaktives virtuelles Haustier mit Hunger, Glück, Energie, Spaß, Aktivitäten, Leveln, Erfolgen und persistentem Zustand.
- **Browser**: Bildschirfüllendes Browser-Overlay mit URL- und Medieneinstellungen.
- **GLSL-Shader**: Bildschirfüllendes benutzerdefiniertes Shader-Overlay (für animierte oder statische shaderbasierte Visuals).

# Buddy virtuelles Haustier

Das **Buddy**-Overlay ist nicht nur eine visuelle Figur, sondern ein virtuelles Haustier im Tamagotchi-Stil. Es läuft am unteren Bildschirmrand entlang, zeigt Gedankenblasen für seine Bedürfnisse an, reagiert auf Interaktionen und behält seinen Zustand zwischen Spielsitzungen bei.

## Bedürfnisse und Steuerung

Buddy verfolgt vier Werte von `0` bis `100`:

- **Hunger** nimmt mit der Zeit ab und wird durch Futter wiederhergestellt.
- **Glück** nimmt mit der Zeit ab und steigt durch Pflege, einschließlich Streicheln und Spielen.
- **Energie** nimmt im Wachzustand und bei Aktivitäten ab und regeneriert sich beim Schlafen.
- **Spaß** nimmt mit der Zeit ab und steigt beim Spielen.

Verwende diese Maussteuerungen und den Statusbildschirm, um dich um ihn zu kümmern:

- **Linksklicke auf Buddy**, um ihn zu streicheln. Ein Linksklick, während er schläft, weckt ihn auf und verursacht einen kleinen Glücksabzug.
- **Rechtsklicke auf Buddy**, um seinen Statusbildschirm zu öffnen. Der Tab **Stats** zeigt alle vier Bedürfnisse, Level und XP; der Tab **Erfolge** zeigt den Fortschritt bei Erfolgen.
- Wähle im Statusbildschirm **Füttern** und ziehe dann das Futter zu Buddy. Futter stellt Hunger und Glück wieder her.
- Wähle im Statusbildschirm **Spielen** und ziehe dann den Ball und lasse ihn los. Der Ball nutzt die Bewegung der Maus, um die Wurfgeschwindigkeit zu berechnen, und Buddy kann ihm hinterherjagen, ihn fangen, halten und mit ihm spielen.
- Wähle **Schlafen**, wenn der Button verfügbar ist, um Energie wiederherzustellen. Buddy schläft außerdem automatisch ein, wenn seine Energie kritisch niedrig wird.
- Buddy hinterlässt gelegentlich Kot. **Linksklicke auf den Kot**, um ihn zu reinigen. Wenn mindestens drei Kothaufen auf dem Bildschirm bleiben, sinkt das Glück fortlaufend, bis weniger als drei übrig sind; die maximale Anzahl an Kothaufen ist konfigurierbar.

## XP, Level und Erfolge

Sich um Buddy zu kümmern, Kot zu reinigen, gute Werte aufrechtzuerhalten und andere Meilensteine zu erreichen, gewährt XP. Buddy startet auf Level 1 und kann Level 30 erreichen. Höhere Level verringern allmählich den Abbau von Hunger, Glück und Energie (bis zu 50 % auf Level 30) und verbessern mehrere Pflege- und XP-Effekte.

Erfolge verfolgen Interaktions-, Werte-, Level-, Sitzungs- und Spezial-Meilensteine. Öffne den Statusbildschirm per Rechtsklick, um beide Fortschrittssysteme anzusehen.

## Tod und Zurücksetzen des Saves

**Buddy Kann Sterben** ist standardmäßig aktiviert. Wenn entweder Hunger oder Glück für **10 reale Stunden** ununterbrochen bei `0` bleibt, stirbt Buddy und wird durch einen Grabstein ersetzt. Wenn du den auf `0` gesetzten Wert vor Ablauf des Timers erhöhst, wird der Timer dieses Werts zurückgesetzt; das Deaktivieren von **Buddy Kann Sterben** löscht beide Timer.

Um nach dem Tod neu zu beginnen, klicke mit der linken Maustaste auf den Grabstein. Du kannst außerdem jederzeit **Buddy-Save zurücksetzen** in den Buddy-Overlay-Einstellungen verwenden. Das Zurücksetzen entfernt sowohl den Save für den Haustierstatus als auch den separaten Save für Leveling/Erfolge für diese Overlay-Instanz.

> [!WARNING]
> Das Zurücksetzen eines Buddy-Saves entfernt dauerhaft seine Bedürfnisse, sein Level, seine XP, Erfolge, Aktivitätszähler und den gespeicherten Kot-Zustand.

## Persistenz und Anpassung

Der Buddy-Status wird automatisch etwa alle zwei Minuten und beim Schließen seines Bildschirms gespeichert. Der Haustierstatus und der Leveling-Status verwenden separate JSON-Dateien für jede Overlay-Instanz innerhalb von `<game-directory>/fancymenu_data/buddy/`. Siehe [Data Storage Locations](./data-storage-locations) für die vollständige FancyMenu-Pfadreferenz.

Die Overlay-Einstellungen ermöglichen es dir außerdem, Buddys Sprite-Atlas, Interaktionsgegenstände, Bedürfnis-Icons, Statusbildschirm-Texturen und den Grabstein zu ersetzen. Erweiterte Werteinstellungen steuern Abbau, Aktivitätskosten und -gewinne, Pflegeeffektivität, maximale Kothaufenanzahl und ob der Tod aktiviert ist.

# Browser-Overlay: Interaktiv vs. Passiv

Das Browser-Overlay kann entweder als interaktiver Browser oder als passive visuelle Ebene konfiguriert werden.

- Die Einstellungen **Maus/Tastatur verarbeiten** steuern, ob der Browser selbst Eingaben verarbeitet.
- Die Einstellungen **Maus/Tastatur verbrauchen** steuern, ob Eingaben vom dahinterliegenden Menü blockiert werden.

Praktische Einrichtungsbeispiele:

- Interaktiver Browser im Vordergrund: aktiviere sowohl **Verarbeiten** als auch **Verbrauchen**.
- Browser-Ebene nur zur Anzeige: deaktiviere **Verarbeiten** und deaktiviere **Verbrauchen**.

> [!IMPORTANT]
> Das Browser-Dekorations-Overlay erfordert das **MCEF**-Mod.
