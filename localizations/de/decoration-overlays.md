---
title: Dekorations-Overlays
description: Füge Menüs im FancyMenu-Layout-Editor fullscreen visuelle Overlays hinzu.
---
# Dekorations-Overlays

Dekorations-Overlays sind Vollbild-Effekte, die vor deinen Menüelementen gerendert werden.

Sie sind nützlich, wenn du einem Menü Atmosphäre oder Bewegung hinzufügen möchtest, ohne diese Effekte manuell zu erstellen.

# Wo du es findest

Öffne ein Layout im Layout-Editor, klicke dann mit der rechten Maustaste auf den Editor-Hintergrund und öffne **Dekorations-Overlays**.

# Schnellstart

1. Öffne ein Layout im Layout-Editor.
2. Klicke mit der rechten Maustaste auf den Hintergrund (leerer Bereich).
3. Öffne **Dekorations-Overlays**.
4. Wähle einen Overlay-Typ aus.
5. Setze **Show Overlay** auf **Enabled**.
6. Konfiguriere die Overlay-Einstellungen.
7. Speichere das Layout und teste den Bildschirm.

# Wie Overlay-Typen funktionieren

Jeder Overlay-Typ hat ein eigenes Untermenü und einen eigenen **Show Overlay**-Schalter.

- Du kannst nur die Typen aktivieren, die du möchtest.
- Du kannst mehrere aktivierte Typen in einem Layout kombinieren.
- Die Einstellungen gelten pro Overlay-Typ (zum Beispiel Farbe, Intensität, Geschwindigkeit, Dichte, Skalierung, spezielles Verhalten).

> [!INFO]
> Es ist möglich, mehrere Instanzen desselben Overlay-Typs zu stapeln, indem du mehrere Layouts mit demselben aktivierten Typ verwendest.

# Overlay-Typen

- **Snowfall**: Schneefall mit optionaler Schneesammlung auf Oberflächen/Buttons.
- **Rainfall**: Regen mit optionalen Pfützen, Tropfen und optionalen Blitz-Effekten.
- **Fireflies**: Bewegte Glühwürmchen-Gruppen mit konfigurierbarer Gruppenanzahl, Dichte, Größe und Farbe.
- **String Lights**: Konfigurierbare Lichterketten-Kombinationen, Lichtfarben, Wind-/Flackerverhalten und Feiertags-Farbmodus.
- **Leaves**: Fallende Blätter mit konfigurierbaren Farben, Wind, Geschwindigkeit, Skalierung und Dichte.
- **Fireworks**: Häufige Feuerwerke mit konfigurierbarer Menge, Explosionsgröße und Skalierung.
- **Confetti**: Konfetti-Regen mit optionalem Konfetti-Modus beim Mausklick.
- **Buddy**: Ein interaktives virtuelles Haustier mit Hunger, Glück, Energie, Spaß, Aktivitäten, Leveln, Erfolgen und persistentem Zustand.
- **Browser**: Vollbild-Browser-Overlay mit URL- und Medieneinstellungen.
- **GLSL Shader**: Benutzerdefiniertes Vollbild-Shader-Overlay (für animierte oder statische shaderbasierte Visuals).

# Buddy Virtuelles Haustier

Das **Buddy**-Overlay ist nicht nur eine visuelle Figur, sondern ein virtuelles Haustier im Tamagotchi-Stil. Es läuft am unteren Bildschirmrand entlang, zeigt Gedankenblasen für seine Bedürfnisse, reagiert auf Interaktionen und behält seinen Zustand zwischen Spielsitzungen bei.

## Bedürfnisse und Steuerung

Buddy verfolgt vier Werte von `0` bis `100`:

- **Hunger** sinkt mit der Zeit und wird durch Futter wieder aufgefüllt.
- **Happiness** sinkt mit der Zeit und steigt durch Pflege, einschließlich Streicheln und Spielen.
- **Energy** sinkt, während Buddy wach ist und bei Aktivitäten, und regeneriert sich dann beim Schlafen.
- **Fun** sinkt mit der Zeit und steigt beim Spielen.

Verwende diese Maussteuerungen und den Statusbildschirm, um dich um Buddy zu kümmern:

- **Linksklicke Buddy**, um ihn zu streicheln. Wenn du links klickst, während er schläft, weckst du ihn und verursachst einen kleinen Glücksverlust.
- **Rechtsklicke Buddy**, um seinen Statusbildschirm zu öffnen. Der Tab **Stats** zeigt alle vier Bedürfnisse, Level und XP; der Tab **Achievements** zeigt den Fortschritt der Erfolge.
- Wähle im Statusbildschirm **Feed** und ziehe dann das Futter zu Buddy. Futter stellt Hunger und Happiness wieder her.
- Wähle im Statusbildschirm **Play** und ziehe dann den Ball und lasse ihn los. Der Ball verwendet die Mausbewegung, um die Wurfgeschwindigkeit zu berechnen, und Buddy kann ihm hinterherjagen, ihn fangen, halten und mit ihm spielen.
- Wähle **Sleep**, wenn die Schaltfläche verfügbar ist, um Energie wiederherzustellen. Buddy schläft auch automatisch ein, wenn seine Energie kritisch niedrig wird.
- Buddy lässt gelegentlich Kot zurück. **Linksklicke auf den Kot**, um ihn zu entfernen. Wenn mindestens drei Kothaufen auf dem Bildschirm verbleiben, sinkt die Happiness kontinuierlich, bis weniger als drei übrig sind; die maximale Kotanzahl ist konfigurierbar.

## XP, Level und Erfolge

Für die Pflege von Buddy, das Entfernen von Kot, das Aufrechterhalten guter Werte und das Erreichen anderer Meilensteine gibt es XP. Buddy beginnt auf Level 1 und kann Level 30 erreichen. Höhere Level verringern schrittweise den Abbau von Hunger, Happiness und Energy (bis zu 50 % auf Level 30) und verbessern mehrere Pflege- und XP-Effekte.

Erfolge verfolgen Interaktions-, Statistik-, Level-, Sitzungs- und besondere Meilensteine. Öffne den Statusbildschirm per Rechtsklick, um beide Fortschrittssysteme zu prüfen.

## Tod und Zurücksetzen des Speichers

**Buddy Can Die** ist standardmäßig aktiviert. Wenn entweder Hunger oder Happiness für **10 reale Stunden** kontinuierlich bei `0` bleibt, stirbt Buddy und wird durch einen Grabstein ersetzt. Wenn du den Wert vor Ablauf des Timers wieder erhöhst, wird der Timer für diesen Wert zurückgesetzt; wenn du **Buddy Can Die** deaktivierst, werden beide Timer gelöscht.

Um nach dem Tod neu zu beginnen, klicke mit der linken Maustaste auf den Grabstein. Du kannst außerdem jederzeit **Reset Buddy Save** in den Buddy-Overlay-Einstellungen verwenden. Beim Zurücksetzen werden sowohl der Speicherstand des Haustiers als auch der separate Speicherstand für Level und Erfolge dieser Overlay-Instanz entfernt.

> [!WARNING]
> Das Zurücksetzen eines Buddy-Speichers entfernt dauerhaft seine Bedürfnisse, sein Level, seine XP, seine Erfolge, Aktivitätszähler und den gespeicherten Kot-Zustand.

## Persistenz und Anpassung

Der Buddy-Zustand wird automatisch etwa alle zwei Minuten und beim Schließen seines Bildschirms gespeichert. Der Haustier-Zustand und der Level-Zustand verwenden separate JSON-Dateien für jede Overlay-Instanz innerhalb von `<game-directory>/fancymenu_data/buddy/`. Siehe [Data Storage Locations](./data-storage-locations) für die vollständige FancyMenu-Pfadreferenz.

Die Overlay-Einstellungen erlauben dir außerdem, Buddys Sprite-Atlas, Interaktionsgegenstände, Bedürfnis-Icons, Statusbildschirm-Texturen und den Grabstein zu ersetzen. Erweiterte Statistikeinstellungen steuern den Abbau, Aktivitätskosten und -gewinne, die Wirksamkeit von Pflege, die maximale Kotanzahl und ob der Tod aktiviert ist.

# Browser-Overlay: Interaktiv vs. passiv

Das Browser-Overlay kann entweder als interaktiver Browser oder als passive visuelle Ebene konfiguriert werden.

- Die Einstellungen **Process Mouse/Keyboard** steuern, ob der Browser selbst Eingaben verarbeitet.
- Die Einstellungen **Consume Mouse/Keyboard** steuern, ob Eingaben vom dahinterliegenden Menü blockiert werden.

Praktische Einrichtungsbeispiele:

- Interaktiver Browser im Vordergrund: sowohl **Process** als auch **Consume** aktivieren.
- Browser-Ebene nur für die Darstellung: **Process** deaktivieren und **Consume** deaktivieren.

> [!IMPORTANT]
> Das Browser-Dekorations-Overlay benötigt das Mod **[Rinku](https://modrinth.com/mod/rinku)**.
