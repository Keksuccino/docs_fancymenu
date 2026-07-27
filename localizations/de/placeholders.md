---
title: Platzhalter
description: Wie man Platzhalter verwendet.
---
# Platzhalter

Platzhalter fügen Live-Werte in Text, Schaltflächen, Anforderungen und andere unterstützte Felder ein.

# Allgemeine Informationen

## Grundlegende Syntax
Platzhalter in FancyMenu verwenden eine JSON-ähnliche Syntax:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Um zum Beispiel den Spielernamen anzuzeigen:
```
{"placeholder":"playername"}
```

## Platzhalter verschachteln
Du kannst einen Platzhalter innerhalb des Werts eines anderen Platzhalters verwenden.

Beispiel für verschachtelte Platzhalter:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Dieses Beispiel nimmt den maximalen RAM-Wert und teilt ihn durch 1024, um ihn von MB in GB umzuwandeln.

> [!IMPORTANT]
> Dies ist FancyMenu-Syntax, nicht JSON. Verschachtelte Platzhalter verwenden die exakt unmaskierte Form wie oben gezeigt, daher werden JSON-Formatierer sie ablehnen oder umschreiben. Platzhalternamen sind groß-/kleinschreibungssensitiv; fehlerhafte oder unbekannte Platzhalter bleiben als Text sichtbar und werden protokolliert.

# Platzhalter verwenden

Die meisten Elemente mit Texteingaben unterstützen Platzhalter. Beim Bearbeiten siehst du, ob eine Texteingabe Platzhalter unterstützt. Wenn beim Bearbeiten des Textes der Vollbild-**Texteditor** geöffnet wird, unterstützt das Feld Platzhalter.

Um eine **Liste aller Platzhalter** zu finden, klicke einfach im **Texteditor** auf die Schaltfläche **Platzhalter** in der **oberen rechten Ecke**.

Oben in der Platzhalterliste gibt es eine **Suchleiste**, mit der du nach Platzhaltern suchen kannst.

Wenn du in der Platzhalterliste auf einen Platzhalter klickst, wird er in den Textinhalt eingefügt.

# Platzhalter im Detail

In diesem Abschnitt sind die integrierten Platzhalter von FancyMenu aufgeführt.

## Nicht verfügbare Ergebnisse
Die Ausgabe von Platzhaltern ist immer Text. Wenn Daten nicht verfügbar sind, hängt das Ergebnis vom Platzhalter ab: Häufige Fallbacks sind eine leere Zeichenfolge, `0`, `0.0`, `00:00`, `false`, `UNKNOWN` oder `ERROR`. Einträge mit einem spezifischen Fallback nennen diesen direkt; teste den Fallback, bevor du umgebungsabhängige Ausgaben in einer [Anforderung](./conditions), einem Pfad, Befehl oder einer URL verwendest.

## Spielername (`playername`)

**Zweck:** Gibt den Benutzernamen des aktuellen Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"playername"}
```

**Ausgabe:** `Steve`

## Spieler-UUID (`playeruuid`)

**Zweck:** Gibt die eindeutige Kennung des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"playeruuid"}
```

**Ausgabe:** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft-Version (`mcversion`)

**Zweck:** Gibt die aktuelle Minecraft-Version zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"mcversion"}
```

**Ausgabe:** `1.21.1`

## Mod-Loader-Version (`loaderver`)

**Zweck:** Gibt die Version des Mod-Loaders (Fabric/NeoForge) zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"loaderver"}
```

**Ausgabe:** `0.16.14`

## Mod-Loader-Name (`loadername`)

**Zweck:** Gibt den Namen des Mod-Loaders zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"loadername"}
```

**Ausgabe:** `Fabric`

## Mod-Version (`modversion`)

**Zweck:** Gibt die Version eines bestimmten Mods zurück.

**Werte:** `modid`

**Beispiel:**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**Ausgabe:** `1.2.3`

## Gesamtanzahl der Mods (`totalmods`)

**Zweck:** Gibt eine ungefähre Anzahl von Mod-Dateien zurück, basierend auf dem `mods`-Verzeichnis und der Anzahl geladener Mods. Deaktivierte Mods werden dabei nicht zuverlässig mitgezählt.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"totalmods"}
```

**Ausgabe:** `45`

## Anzahl aktiver Mods (`loadedmods`)

**Zweck:** Gibt die Anzahl der aktuell geladenen Mods zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"loadedmods"}
```

**Ausgabe:** `43`

## Ladefortschritt der Welt (`world_load_progress`)

**Zweck:** Gibt den aktuellen Ladefortschritt der Welt als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"world_load_progress"}
```

**Ausgabe:** `75`

## Minecraft-Optionswert (`minecraft_option_value`)

**Zweck:** Gibt den Wert einer Minecraft-Option zurück.

**Werte:** `name`

**Beispiel:**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**Ausgabe:** `70`

## Letzte Welt oder letzter Server (`last_world_server`)

**Zweck:** Gibt Informationen über die zuletzt aufgerufene Welt oder den zuletzt aufgerufenen Server zurück.

**Werte:** `type`, `full_world_path`

**Beispiel:**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parameter:
- `type`: Legt fest, welche Art von Information zurückgegeben wird
  - `"both"`: Gibt die zuletzt aufgerufene Welt oder den letzten Server zurück (Standard)
  - `"server"`: Gibt nur etwas zurück, wenn zuletzt ein Server aufgerufen wurde
  - `"world"`: Gibt nur etwas zurück, wenn zuletzt eine Welt aufgerufen wurde
- `full_world_path`: Steuert, wie Weltpfade angezeigt werden
  - `"true"`: Gibt den vollständigen Weltpfad zurück (Standard)
  - `"false"`: Gibt nur den Weltnamen ohne Pfad zurück (betrifft Server nicht)

Beispiele:
- Server: `mc.hypixel.net`
- Welt mit vollständigem Pfad: `saves/New World`
- Welt ohne vollständigen Pfad: `New World`

## Bildschirmbreite (`guiwidth`)

**Zweck:** Gibt die aktuelle Bildschirmbreite in GUI-skalierten Pixeln zurück, nicht in physischen Monitorpixeln.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"guiwidth"}
```

**Ausgabe:** `960`

## Bildschirmhöhe (`guiheight`)

**Zweck:** Gibt die aktuelle Bildschirmhöhe in GUI-skalierten Pixeln zurück, nicht in physischen Monitorpixeln.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"guiheight"}
```

**Ausgabe:** `540`

## Kennung des aktuellen Bildschirms (`screenid`)

**Zweck:** Gibt die Kennung des aktuellen Bildschirms zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"screenid"}
```

**Ausgabe:** `title_screen`

## Elementbreite (`elementwidth`)

**Zweck:** Gibt die Breite eines bestimmten Elements zurück.

**Werte:** `id`

**Beispiel:**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**Ausgabe:** `200`

## Elementhöhe (`elementheight`)

**Zweck:** Gibt die Höhe eines bestimmten Elements zurück.

**Werte:** `id`

**Beispiel:**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**Ausgabe:** `20`

## X-Position des Elements (`elementposx`)

**Zweck:** Gibt die X-Position eines bestimmten Elements zurück.

**Werte:** `id`

**Beispiel:**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**Ausgabe:** `150`

## Y-Position des Elements (`elementposy`)

**Zweck:** Gibt die Y-Position eines bestimmten Elements zurück.

**Werte:** `id`

**Beispiel:**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**Ausgabe:** `100`

## X-Position der Maus (`mouseposx`)

**Zweck:** Gibt die aktuelle X-Position der Maus zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"mouseposx"}
```

**Ausgabe:** `960`

## Y-Position der Maus (`mouseposy`)

**Zweck:** Gibt die aktuelle Y-Position der Maus zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"mouseposy"}
```

**Ausgabe:** `540`

## Klicks pro Sekunde (`clicks_per_second`)

**Zweck:** Gibt die aktuellen Klicks pro Sekunde für eine Maustaste zurück.

**Werte:** `mouse_button`

**Beispiel:**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parameter:
- `mouse_button`: `left` oder `right`

**Ausgabe:** `8`

## GUI-Skalierung (`guiscale`)

**Zweck:** Gibt die aktuelle GUI-Skalierung zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"guiscale"}
```

**Ausgabe:** `2`

## Beschriftung/Text eines Vanilla-Widgets (`vanillabuttonlabel`)

**Zweck:** Gibt die Beschriftung bzw. den Text eines Vanilla-Widgets/einer Schaltfläche zurück.

**Werte:** `locator`

**Beispiel:**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**Ausgabe:** `Options...`

## Wert eines Texteingabefelds (`text_input_field_value`)

**Zweck:** Gibt den aktuellen Wert eines benutzerdefinierten oder Vanilla-Texteingabefelds anhand der Elementkennung zurück.

**Werte:** `element_identifier`

**Beispiel:**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**Ausgabe:** `Hello World`

## Aktuelle Gesundheit des Spielers (`current_player_health`)

**Zweck:** Gibt die aktuellen Lebenspunkte des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_health"}
```

**Ausgabe:** `20.0`

## Maximale Gesundheit des Spielers (`max_player_health`)

**Zweck:** Gibt die maximale Gesundheit des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"max_player_health"}
```

**Ausgabe:** `20.0`

## Aktuelle Gesundheit des Spielers (Prozent) (`current_player_health_percent`)

**Zweck:** Gibt die Gesundheit des Spielers als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_health_percent"}
```

**Ausgabe:** `100`

## Aktuelle Absorptionsgesundheit des Spielers (`current_player_absorption_health`)

**Zweck:** Gibt die Absorptionsgesundheit des Spielers zurück (goldene Herzen).

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_absorption_health"}
```

**Ausgabe:** `4.0`

## Maximale Absorptionsgesundheit des Spielers (`max_player_absorption_health`)

**Zweck:** Gibt die maximale Absorptionsgesundheit zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"max_player_absorption_health"}
```

**Ausgabe:** `4.0`

## Aktuelle Absorptionsgesundheit des Spielers (Prozent) (`current_player_absorption_health_percent`)

**Zweck:** Gibt die Absorptionsgesundheit des Spielers als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**Ausgabe:** `100`

## Aktueller Hungerwert des Spielers (`current_player_hunger`)

**Zweck:** Gibt den aktuellen Hungerwert des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_hunger"}
```

**Ausgabe:** `20`

## Maximaler Hungerwert des Spielers (`max_player_hunger`)

**Zweck:** Gibt den maximalen Hungerwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"max_player_hunger"}
```

**Ausgabe:** `20`

## Aktueller Hungerwert des Spielers (Prozent) (`current_player_hunger_percent`)

**Zweck:** Gibt den Hunger des Spielers als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_hunger_percent"}
```

**Ausgabe:** `100`

## Aktuelle Hunger-Sättigung des Spielers (`current_player_hunger_saturation`)

**Zweck:** Gibt den aktuellen Sättigungswert des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_hunger_saturation"}
```

**Ausgabe:** `5.0`

## Aktuelle Rüstung des Spielers (`current_player_armor`)

**Zweck:** Gibt den aktuellen Rüstungswert des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_armor"}
```

**Ausgabe:** `20`

## Rüstungshärte des Spielers (`player_armor_toughness`)

**Zweck:** Gibt den gesamten Wert der Rüstungshärte des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_armor_toughness"}
```

**Ausgabe:** `8.0`

## Maximale Rüstung des Spielers (`max_player_armor`)

**Zweck:** Gibt den maximalen Rüstungswert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"max_player_armor"}
```

**Ausgabe:** `20`

## Aktuelle Rüstung des Spielers (Prozent) (`current_player_armor_percent`)

**Zweck:** Gibt die Rüstung des Spielers als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_armor_percent"}
```

**Ausgabe:** `100`

## Aktueller Sauerstoffwert des Spielers (`current_player_oxygen`)

**Zweck:** Gibt den aktuellen Sauerstoffwert des Spielers zurück (Luftblasen).

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_oxygen"}
```

**Ausgabe:** `300`

## Maximaler Sauerstoffwert des Spielers (`max_player_oxygen`)

**Zweck:** Gibt den maximalen Sauerstoffwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"max_player_oxygen"}
```

**Ausgabe:** `300`

## Aktueller Sauerstoffwert des Spielers (Prozent) (`current_player_oxygen_percent`)

**Zweck:** Gibt den Sauerstoffwert des Spielers als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_oxygen_percent"}
```

**Ausgabe:** `100`

## Aktuelle Spielerstufe (`current_player_level`)

**Zweck:** Gibt die aktuelle Erfahrungsstufe des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_level"}
```

**Ausgabe:** `30`

## Aktuelle Spielererfahrung (`current_player_exp`)

**Zweck:** Gibt die gesamten Erfahrungspunkte des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_exp"}
```

**Ausgabe:** `1250`

## Erfahrungsfortschritt des Spielers (Prozent) (`current_player_exp_progress`)

**Zweck:** Gibt den Erfahrungsfortschritt des Spielers zur nächsten Stufe als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_player_exp_progress"}
```

**Ausgabe:** `75`

## Angriffsstärke des Spielers (Prozent) (`player_attack_strength`)

**Zweck:** Gibt den Angriffs-Cooldown des Spielers als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_attack_strength"}
```

**Ausgabe:** `100`

## Spielmodus des Spielers (`player_gamemode`)

**Zweck:** Gibt den aktuellen Spielmodus des Spielers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_gamemode"}
```

**Ausgabe:** `survival`

## Blickrichtung des Spielers (`player_view_direction`)

**Zweck:** Gibt die Richtung zurück, in die der Spieler schaut.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_view_direction"}
```

**Ausgabe:** `north`

## X-Koordinate des Spielers (`player_x_coordinate`)

**Zweck:** Gibt die X-Position des Spielers in der Welt zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_x_coordinate"}
```

**Ausgabe:** `125`

## Y-Koordinate des Spielers (`player_y_coordinate`)

**Zweck:** Gibt die Y-Position des Spielers in der Welt zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_y_coordinate"}
```

**Ausgabe:** `64`

## Z-Koordinate des Spielers (`player_z_coordinate`)

**Zweck:** Gibt die Z-Position des Spielers in der Welt zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_z_coordinate"}
```

**Ausgabe:** `-250`

## Aktuelle Gesundheit des Reittiers (`current_mount_health`)

**Zweck:** Gibt die aktuelle Gesundheit der Entität zurück, auf der der Spieler reitet.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_mount_health"}
```

**Ausgabe:** `30.0`

## Maximale Gesundheit des Reittiers (`max_mount_health`)

**Zweck:** Gibt die maximale Gesundheit der Entität zurück, auf der der Spieler reitet.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"max_mount_health"}
```

**Ausgabe:** `30.0`

## Aktuelle Gesundheit des Reittiers (Prozent) (`current_mount_health_percent`)

**Zweck:** Gibt die Gesundheit des Reittiers als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_mount_health_percent"}
```

**Ausgabe:** `100`

## Aktuelle Sprunganzeige des Reittiers (Prozent) (`current_mount_jump_meter`)

**Zweck:** Gibt den aktuellen Sprungkraftmesser des Reittiers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_mount_jump_meter"}
```

**Ausgabe:** `75`

## Aktuelle Boss-Gesundheit (Prozent) (`current_boss_health`)

**Zweck:** Gibt die Gesundheit eines ausgewählten aktiven Bosses als Ganzzahl zwischen `0` und `100` zurück. `boss_index` beginnt bei 0; `0` wählt die erste Bossleiste aus.

**Werte:** `boss_index`

**Beispiel:**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**Ausgabe:** `75`

## Boss-Name (`boss_name`)

**Zweck:** Gibt den Namen des aktiven Bosses zurück.

**Werte:** `boss_index`, `as_json`

**Beispiel:**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**Ausgabe:** `Ender Dragon`

## Anzahl der Bosse (`boss_count`)

**Zweck:** Gibt die Anzahl aktiver Bosse zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"boss_count"}
```

**Ausgabe:** `1`

## Anzahl aktiver Effekte (`effects_count`)

**Zweck:** Gibt die Anzahl aktiver Trankeffekte zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"effects_count"}
```

**Ausgabe:** `3`

## Aktiver Effekt (`active_effect`)

**Zweck:** Gibt Informationen über einen bestimmten aktiven Effekt zurück.

**Werte:** `effect_index`

**Beispiel:**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**Ausgabe:** `minecraft:speed`

## Ausgewählter Hotbar-Slot (`active_hotbar_slot`)

**Zweck:** Gibt den aktuell ausgewählten Hotbar-Slot (0-8) zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"active_hotbar_slot"}
```

**Ausgabe:** `4`

## Slot-Item (`slot_item`)

**Zweck:** Gibt Informationen über ein Item in einem bestimmten Inventarslot zurück.

**Werte:** `slot`

**Beispiel:**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**Ausgabe:** `minecraft:diamond_sword`

## Anzahl des Slot-Items (`slot_item_count`)

**Zweck:** Gibt die Stapelgröße des Items in einem bestimmten Spielerinventarslot zurück.

**Werte:** `slot`

**Beispiel:**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**Ausgabe:** `64`

## Haltbarkeit des Slot-Items (`slot_item_durability`)

**Zweck:** Gibt Informationen zur Haltbarkeit des Items in einem bestimmten Spielerinventarslot zurück.

**Werte:** `slot`, `format`

**Beispiel:**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parameter:
- `slot`: Inventarslot-Nummer des Spielers.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` oder `percent`.

**Ausgabe:** `87`

## Anzeigename des Slot-Items (`slot_item_display_name_fm`)

**Zweck:** Gibt den Anzeigenamen des Items in einem bestimmten Slot als JSON-Textkomponente zurück. Im Zuschauermodus können Hotbar-Slots Namen von Zuschauermenü-Items auflösen, sofern `ignore_spectator` nicht `true` ist.

**Werte:** `slot`, `ignore_spectator`

**Beispiel:**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**Ausgabe:** `{"text":"Diamond Sword","color":"aqua"}`

## Anzahl von Inventarobjekten (`inventory_item_count`)

**Zweck:** Gibt die Gesamtanzahl passender Items im Inventar des Spielers zurück. Wenn `item` leer ist, werden die Stapelgrößen aller belegten Inventarslots addiert.

**Werte:** `item`

**Beispiel:**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**Ausgabe:** `12`

## Wiederherstellungswert eines Essens im Inventarslot (`inventory_slot_food_point_restore_amount`)

**Zweck:** Gibt die Hungerpunkte zurück, die das Essensitem im angegebenen Spielerinventarslot wiederherstellt.

**Werte:** `slot`

**Beispiel:**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**Ausgabe:** `4.0`

## Überfahrenes Inventar-Item (`hovered_inventory_item`)

**Zweck:** Gibt den Item-Schlüssel des aktuell im Inventarbildschirm überfahrenen Items zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"hovered_inventory_item"}
```

**Ausgabe:** `minecraft:apple`

## Spielzeit der Welt (`game_time`)

**Zweck:** Gibt den aktuellen In-Game-Zeit-Tickzähler zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"game_time"}
```

**Ausgabe:** `18000`

## Tageszeit der Welt (`world_daytime`)

**Zweck:** Gibt die aktuelle Tageszeit der Welt zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"world_daytime"}
```

**Ausgabe:** `13000`

## Stunde der Tageszeit (`world_daytime_hour`)

**Zweck:** Gibt die Stundenkomponente der Weltzeit zurück. Standardmäßig wird das 24-Stunden-Format verwendet; setze `twelve_hour_format` auf `"true"`, um das 12-Stunden-Format zu verwenden.

**Werte:** `twelve_hour_format`

**Beispiel:**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**Ausgabe:** `12`

## Minute der Tageszeit (`world_daytime_minute`)

**Zweck:** Gibt die Minutenkomponente der Weltzeit zurück (00-59).

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"world_daytime_minute"}
```

**Ausgabe:** `30`

## Weltschwierigkeit (`world_difficulty`)

**Zweck:** Gibt die aktuelle Schwierigkeit der Welt zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"world_difficulty"}
```

**Ausgabe:** `normal`

## Aktueller Welt-Seed (`current_world_seed`)

**Zweck:** Gibt den Seed der aktuellen Einzelspielerwelt zurück. Gibt einen leeren Wert zurück, wenn der Seed nicht verfügbar ist.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_world_seed"}
```

**Ausgabe:** `123456789`

## Aktuelles Biom (`current_biome`)

**Zweck:** Gibt das Biom zurück, in dem sich der Spieler aktuell befindet. Setze `as_key` auf `"false"`, um sofern verfügbar einen übersetzten/angezeigten Namen zurückzugeben.

**Werte:** `as_key`

**Beispiel:**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**Ausgabe:** `minecraft:plains`

## Aktive Dimension (`current_dimension`)

**Zweck:** Gibt die Dimension zurück, in der sich der Spieler aktuell befindet. Setze `as_key` auf `"false"`, um sofern verfügbar einen übersetzten/angezeigten Namen zurückzugeben.

**Werte:** `as_key`

**Beispiel:**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**Ausgabe:** `minecraft:overworld`

## Gamerule-Wert (`gamerule_value`)

**Zweck:** Gibt den aktuellen Wert einer Gamerule in der geladenen Welt bzw. auf dem Server zurück. Serverwelten erfordern FancyMenu auf dem Server.

**Werte:** `name`

**Beispiel:**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**Ausgabe:** `true`

## Item-Kategorie (`item_category`)

**Zweck:** Gibt die Kreativtab-Kategorie eines Items zurück. Setze `as_key` auf `"true"`, um statt des Anzeigenamens den Kategorienamen zurückzugeben.

**Werte:** `item`, `as_key`

**Beispiel:**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**Ausgabe:** `Combat`

## Aktueller HUD-Titel/Untertitel (`current_title`)

**Zweck:** Gibt den aktuell angezeigten Titeltext zurück.

**Werte:** `is_subtitle`, `as_json`

**Beispiel:**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**Ausgabe:** `Game Over!`

## Actionbar-Nachricht (`action_bar_message_fm`)

**Zweck:** Gibt die aktuelle Vanilla-Actionbar-Nachricht als serialisierte Minecraft-Textkomponente zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"action_bar_message_fm"}
```

**Ausgabe:** `{"text":"You may not rest now","color":"red"}`

## Anzeigezeit der Actionbar-Nachricht (`action_bar_message_time_fm`)

**Zweck:** Gibt an, wie viele Ticks die aktuelle Vanilla-Actionbar-Nachricht noch angezeigt wird.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"action_bar_message_time_fm"}
```

**Ausgabe:** `42`

## Kamerarotation X (`camera_rotation_x_fm`)

**Zweck:** Gibt die aktuelle Kameraneigung in Grad zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"camera_rotation_x_fm"}
```

**Ausgabe:** `12.5`

## Kamerarotation Y (`camera_rotation_y_fm`)

**Zweck:** Gibt den aktuellen Kamera-Yaw in Grad zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"camera_rotation_y_fm"}
```

**Ausgabe:** `-90.0`

## Kamerarotations-Delta X (`camera_rotation_delta_x_fm`)

**Zweck:** Gibt die Änderung der Kameraneigung pro Tick zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**Ausgabe:** `0.4`

## Kamerarotations-Delta Y (`camera_rotation_delta_y_fm`)

**Zweck:** Gibt die Änderung des Kamera-Yaw pro Tick zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**Ausgabe:** `-1.2`

## Zeit für hervorgehobenes Item (`highlighted_item_time_fm`)

**Zweck:** Gibt an, wie viele Ticks der Name des hervorgehobenen Items noch über der Hotbar angezeigt wird.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"highlighted_item_time_fm"}
```

**Ausgabe:** `30`

## Nutzungsfortschritt des Spieler-Items (`player_item_use_progress_fm`)

**Zweck:** Gibt den aktuellen Nutzungsfortschritt eines Items von `0.0` bis `1.0` zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_item_use_progress_fm"}
```

**Ausgabe:** `0.65`

## Positions-Delta X des Spielers (`player_position_delta_x_fm`)

**Zweck:** Gibt die Positionsänderung des Spielers pro Tick auf der X-Achse zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_position_delta_x_fm"}
```

**Ausgabe:** `0.0`

## Positions-Delta Y des Spielers (`player_position_delta_y_fm`)

**Zweck:** Gibt die Positionsänderung des Spielers pro Tick auf der Y-Achse zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_position_delta_y_fm"}
```

**Ausgabe:** `-0.08`

## Positions-Delta Z des Spielers (`player_position_delta_z_fm`)

**Zweck:** Gibt die Positionsänderung des Spielers pro Tick auf der Z-Achse zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"player_position_delta_z_fm"}
```

**Ausgabe:** `0.12`

## Aktuelle Server-IP (`current_server_ip`)

**Zweck:** Gibt die IP des verbundenen Servers zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"current_server_ip"}
```

**Ausgabe:** `mc.hypixel.net`

## Liste der Spieler in der Welt (`world_players_list`)

**Zweck:** Gibt eine Liste aller Spieler zurück, die sich aktuell in der Welt befinden.

**Werte:** `separator`

**Beispiel:**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**Ausgabe:** `Steve, Alex, Notch`

## Server-MOTD (`servermotd`)

**Zweck:** Gibt die Message of the Day eines Servers zurück.

**Werte:** `ip`, `line`

**Beispiel:**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**Ausgabe:** `Welcome to Hypixel!`

## Server-Ping (`serverping`)

**Zweck:** Gibt den Ping zu einem Server in Millisekunden zurück.

**Werte:** `ip`

**Beispiel:**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**Ausgabe:** `54`

## Spieleranzahl des Servers (`serverplayercount`)

**Zweck:** Gibt die Spieleranzahl eines Servers zurück.

**Werte:** `ip`

**Beispiel:**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**Ausgabe:** `25000/30000`

## Serverstatus (`serverstatus`)

**Zweck:** Gibt den Online-/Offline-Status eines Servers zurück.

**Werte:** `ip`

**Beispiel:**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**Ausgabe:** `§aOnline` oder `§cOffline`

## Server-Version (`serverversion`)

**Zweck:** Gibt die Minecraft-Version eines Servers zurück.

**Werte:** `ip`

**Beispiel:**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**Ausgabe:** `1.21.1`

> [!NOTE]
> Die unten aufgeführten Echtzeit-Platzhalter akzeptieren einen `timezone`-Wert. Verwende eine Java-Zeitzonen-ID wie `UTC`, `Europe/Berlin` oder `America/New_York`; lasse den Wert weg oder verwende `system` für die Systemzeitzone. `unix_time` gibt immer den Unix-Zeitstempel zurück und hat keinen `timezone`-Wert.

## Jahr (`realtimeyear`)

**Zweck:** Gibt das aktuelle Jahr zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"realtimeyear"}
```

**Ausgabe:** `2024`

## Monat (`realtimemonth`)

**Zweck:** Gibt den aktuellen Monat zurück (01-12).

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"realtimemonth"}
```

**Ausgabe:** `01`

## Tag (`realtimeday`)

**Zweck:** Gibt den aktuellen Tag des Monats zurück (01-31).

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"realtimeday"}
```

**Ausgabe:** `27`

## Stunde (`realtimehour`)

**Zweck:** Gibt die aktuelle Stunde zurück. Standardmäßig wird das 24-Stunden-Format verwendet; setze `twelve_hour_format` auf `"true"`, um das 12-Stunden-Format zu verwenden.

**Werte:** `twelve_hour_format`, `timezone`

**Beispiel:**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**Ausgabe:** `14`

## Minute (`realtimeminute`)

**Zweck:** Gibt die aktuelle Minute zurück (00-59).

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"realtimeminute"}
```

**Ausgabe:** `30`

## Sekunde (`realtimesecond`)

**Zweck:** Gibt die aktuelle Sekunde zurück (00-59).

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"realtimesecond"}
```

**Ausgabe:** `45`

## Aktuelle Zeit in Millisekunden (Unix-Zeitstempel) (`unix_time`)

**Zweck:** Gibt den aktuellen Unix-Zeitstempel in Millisekunden zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"unix_time"}
```

**Ausgabe:** `1716552478123`

## CPU-Info (`cpuinfo`)

**Zweck:** Gibt Informationen über die CPU zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"cpuinfo"}
```

**Ausgabe:** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU-Auslastung (JVM) (`jvmcpu`)

**Zweck:** Gibt die CPU-Auslastung der JVM als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"jvmcpu"}
```

**Ausgabe:** `25.5`

## CPU-Auslastung (OS) (`oscpu`)

**Zweck:** Gibt die CPU-Auslastung des Betriebssystems als Prozentwert zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"oscpu"}
```

**Ausgabe:** `42.8`

## GPU-Info (`gpuinfo`)

**Zweck:** Gibt den Namen des von Minecraft verwendeten aktiven Rendering-Geräts zurück. Dies identifiziert nicht zwangsläufig eine bestimmte physische GPU.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"gpuinfo"}
```

**Ausgabe:** `NVIDIA GeForce RTX 3080`

## Java-Version (`javaver`)

**Zweck:** Gibt die Java-Version zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"javaver"}
```

**Ausgabe:** `17.0.2`

## Java Virtual Machine (`jvmname`)

**Zweck:** Gibt den Namen der Java Virtual Machine zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"jvmname"}
```

**Ausgabe:** `OpenJDK 64-Bit Server VM`

## OpenGL-Version (`glver`)

**Zweck:** Gibt Treiberinformationen für das aktive Rendering-Gerät von Minecraft zurück. Trotz des alten Namens `glver` ist nicht garantiert, dass der Wert nur eine OpenGL-Versionszeichenfolge enthält.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"glver"}
```

**Ausgabe:** `4.6.0 NVIDIA 516.94`

## Name des Betriebssystems (`osname`)

**Zweck:** Gibt den Namen des Betriebssystems zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"osname"}
```

**Ausgabe:** `Windows 10`

## FPS (Bilder pro Sekunde) (`fps`)

**Zweck:** Gibt die aktuellen Bilder pro Sekunde zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"fps"}
```

**Ausgabe:** `120`

## Verwendeter RAM in MB (`usedram`)

**Zweck:** Gibt die aktuell verwendete RAM-Menge in MB zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"usedram"}
```

**Ausgabe:** `4096`

## Maximaler RAM in MB (`maxram`)

**Zweck:** Gibt den maximal zugewiesenen RAM in MB zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"maxram"}
```

**Ausgabe:** `8192`

## Verwendeter RAM in %% (`percentram`)

**Zweck:** Gibt den aktuell verwendeten RAM-Anteil in Prozent zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"percentram"}
```

**Ausgabe:** `50`

## Lautstärke eines Audio-Elements (`audio_element_vol`)

**Zweck:** Gibt die Lautstärke eines Audio-Elements zurück.

**Werte:** `element_identifier`

**Beispiel:**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**Ausgabe:** `0.5`

## Aktueller Audiotrack (`audio_element_current_track`)

**Zweck:** Gibt den Tracknamen eines Audio-Elements zurück.

**Werte:** `element_identifier`, `display_name_mappings`

**Beispiel:**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

In `display_name_mappings` trennt `=>` den Dateinamen vom Anzeigenamen und `%:%` trennt Zuordnungen.

**Ausgabe:** `Menu Theme`

## Audiodauer (`audio_duration`)

**Zweck:** Gibt die Dauer des aktuell geladenen Tracks des [Audio-Elements](./elements#audio) im Format `MM:SS` zurück. Der Track kann abgespielt, pausiert oder gestoppt sein.

**Werte:** `element_identifier`

**Beispiel:**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**Ausgabe:** `03:45`

## Audio-Abspielzeit (`audio_playtime`)

**Zweck:** Gibt die aktuelle Abspielzeit eines Audiotracks zurück. Setze `show_percentage` auf `"true"`, um einen Fortschrittswert von 0-100 statt `MM:SS` zu erhalten.

**Werte:** `element_identifier`, `show_percentage`

**Beispiel:**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**Ausgabe:** `01:30` (oder `45` wenn `show_percentage` `"true"` ist)

**Nicht verfügbare Ausgabe:** `00:00` oder `0` im Prozentmodus. Der aktuelle Wert ist verfügbar, solange der Track abgespielt oder pausiert wird; gestoppte, fehlende und noch nicht bereitstehende Tracks verwenden die nicht verfügbare Ausgabe.

## Audio-Wiedergabestatus (`audio_playing_state`)

**Zweck:** Gibt zurück, ob ein Audio-Element abgespielt wird (true/false).

**Werte:** `element_identifier`

**Beispiel:**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**Ausgabe:** `true`

## Lautstärke eines Video-Elements (`video_element_vol`)

**Zweck:** Gibt die Lautstärke eines Video-Elements zurück (0.0 bis 1.0).

**Werte:** `element_identifier`

**Beispiel:**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**Ausgabe:** `0.5`

## Dauer eines Video-Elements (`video_element_duration`)

**Zweck:** Gibt die Gesamtdauer eines Video-Elements im Format `MM:SS` zurück. Setze `output_as_timestamp` auf `"true"`, um einen Millisekunden-Zeitstempel zurückzugeben.

**Werte:** `element_identifier`, `output_as_timestamp`

**Beispiel:**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**Ausgabe:** `02:00` (oder `120000` wenn `output_as_timestamp` `"true"` ist)

## Video-Element Abspielzeit (`video_element_playtime`)

**Zweck:** Gibt die aktuelle Abspielzeit (Fortschritt) eines Video-Elements im Format `MM:SS` zurück. Setze `show_percentage` auf `"true"` für einen Fortschrittswert von 0-100 oder `output_as_timestamp` auf `"true"` für Millisekunden.

**Werte:** `element_identifier`, `show_percentage`, `output_as_timestamp`

**Beispiel:**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**Ausgabe:** `00:45` (oder `38` als Prozentwert oder `45200` als Zeitstempel)

## Pausenstatus eines Video-Elements (`video_element_paused_state`)

**Zweck:** Gibt zurück, ob ein Video-Element pausiert ist (true/false).

**Werte:** `element_identifier`

**Beispiel:**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**Ausgabe:** `false`

## Lautstärke eines Video-Hintergrunds (`video_background_vol`)

**Zweck:** Gibt die Lautstärke eines Video-Menühintergrunds zurück (0.0 bis 1.0).

**Werte:** `background_identifier`

**Beispiel:**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**Ausgabe:** `0.7`

## Dauer eines Video-Hintergrunds (`video_background_duration`)

**Zweck:** Gibt die Gesamtdauer eines Video-Menühintergrunds im Format `MM:SS` zurück. Setze `output_as_timestamp` auf `"true"`, um einen Millisekunden-Zeitstempel zurückzugeben.

**Werte:** `background_identifier`, `output_as_timestamp`

**Beispiel:**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**Ausgabe:** `03:00` (oder `180000` wenn `output_as_timestamp` `"true"` ist)

## Abspielzeit eines Video-Hintergrunds (`video_background_playtime`)

**Zweck:** Gibt die aktuelle Abspielzeit (Fortschritt) eines Video-Menühintergrunds im Format `MM:SS` zurück. Setze `show_percentage` auf `"true"` für einen Fortschrittswert von 0-100 oder `output_as_timestamp` auf `"true"` für Millisekunden.

**Werte:** `background_identifier`, `show_percentage`, `output_as_timestamp`

**Beispiel:**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**Ausgabe:** `01:00` (oder `33` als Prozentwert oder `60500` als Zeitstempel)

## Pausenstatus eines Video-Hintergrunds (`video_background_paused_state`)

**Zweck:** Gibt zurück, ob ein Video-Menühintergrund pausiert ist (true/false).

**Werte:** `background_identifier`

**Beispiel:**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**Ausgabe:** `true`

## Rechner (`calc`)

**Zweck:** Der Platzhalter für den Rechner ist ein leistungsstarkes Werkzeug, mit dem du mathematische Berechnungen innerhalb deiner Layouts durchführen kannst. Er unterstützt eine breite Palette mathematischer Operationen und kann sowohl mit Dezimal- als auch mit Ganzzahlen arbeiten.

**Werte:** `decimal`, `expression`

### Grundlegende Syntax

**Beispiel:**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

Der Rechner hat zwei Hauptparameter:
- `decimal`: Bestimmt, ob das Ergebnis Dezimalstellen enthalten soll (`true`) oder auf ganze Zahlen gerundet wird (`false`)
- `expression`: Der auszuwertende mathematische Ausdruck

### Unterstützte Operationen
Der Rechner unterstützt folgende mathematische Operationen:
- Grundrechenarten: `+` (Addition), `-` (Subtraktion), `*` (Multiplikation), `/` (Division)
- Klammern: `( )` zum Gruppieren von Operationen
- Potenz: `^` für Exponenten
- Quadratwurzel: `sqrt()`
- Trigonometrische Funktionen: `sin()`, `cos()`, `tan()`
- Mathematische Konstanten: `pi`, `e`
- Absolutwert: `abs()`
- Logarithmen: `log()`, `ln()`

## Zufallszahl (`random_number`)

**Zweck:** Erzeugt eine Zufallszahl innerhalb eines angegebenen Bereichs.

**Werte:** `min`, `max`

**Beispiel:**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**Ausgabe:** `42`

## Maximalzahl (`maxnum`)

**Zweck:** Gibt die größere von zwei Zahlen zurück.

**Werte:** `first`, `second`

**Beispiel:**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**Ausgabe:** `20`

## Minimalzahl (`minnum`)

**Zweck:** Gibt die kleinere von zwei Zahlen zurück.

**Werte:** `first`, `second`

**Beispiel:**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**Ausgabe:** `10`

## Absolutwert (`absnum`)

**Zweck:** Gibt den Absolutwert einer Zahl zurück.

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**Ausgabe:** `10.5`

## Zahl negativ machen (`negnum`)

**Zweck:** Macht eine positive Zahl negativ. Null und bereits negative Werte werden unverändert zurückgegeben.

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**Ausgabe:** `-10.5`

## *pi* (Mathe) (`math_pi`)

**Zweck:** Gibt den Wert von π zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"math_pi"}
```

**Ausgabe:** `3.141592653589793`

## Trigonometrischer Sinus (Mathe) (`math_sin`)

**Zweck:** Gibt den Sinus eines Winkels in Radiant zurück. Gradwerte müssen zuerst in Radiant umgerechnet werden.

**Werte:** `angle`

**Beispiel:**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**Ausgabe:** `1.0`

## Trigonometrischer Kosinus (Mathe) (`math_cos`)

**Zweck:** Gibt den Kosinus eines Winkels in Radiant zurück. Gradwerte müssen zuerst in Radiant umgerechnet werden.

**Werte:** `angle`

**Beispiel:**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**Ausgabe:** `1.0`

## Trigonometrischer Tangens (Mathe) (`math_tan`)

**Zweck:** Gibt den Tangens eines Winkels in Radiant zurück. Gradwerte müssen zuerst in Radiant umgerechnet werden.

**Werte:** `angle`

**Beispiel:**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**Ausgabe:** `0.0`

## Abrunden (Mathe) (`math_floor`)

**Zweck:** Gibt die mathematische Abrundung einer Zahl zurück, formatiert mit einem `.0`-Dezimalsuffix.

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**Ausgabe:** `3.0`

## Aufrunden (Mathe) (`math_ceil`)

**Zweck:** Gibt die mathematische Aufrundung einer Zahl zurück, formatiert mit einem `.0`-Dezimalsuffix.

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**Ausgabe:** `4.0`

Verwende [**Runden**](#round-math-math_round) oder den [**Rechner**](#rechner-calc) mit deaktivierter Dezimalausgabe, wenn du ganze Zahlen ohne `.0` benötigst.

## Runden (Mathe) (`math_round`)

**Zweck:** Rundet eine Zahl. Standardmäßig wird auf die nächste ganze Zahl gerundet; setze `decimals` auf eine nichtnegative Zahl, um auf diese Anzahl Dezimalstellen zu runden.

**Werte:** `num`, `decimals`

**Beispiel:**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**Ausgabe:** `3.14` (bei `decimals:-1` oder wenn der Wert fehlt → `3`)

## Vorzeichen (Mathe) (`math_sign`)

**Zweck:** Gibt das Vorzeichen einer Zahl zurück (1 für positiv, -1 für negativ, 0 für null).

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**Ausgabe:** `-1`

## Hyperbolischer Sinus (Mathe) (`math_sinh`)

**Zweck:** Gibt den hyperbolischen Sinus einer Zahl zurück.

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**Ausgabe:** `1.1752011936438014`

## Hyperbolischer Kosinus (Mathe) (`math_cosh`)

**Zweck:** Gibt den hyperbolischen Kosinus einer Zahl zurück.

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**Ausgabe:** `1.5430806348152437`

## Hyperbolischer Tangens (Mathe) (`math_tanh`)

**Zweck:** Gibt den hyperbolischen Tangens einer Zahl zurück.

**Werte:** `num`

**Beispiel:**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**Ausgabe:** `0.7615941559557649`

## Text teilen (`split_text`)

**Zweck:** Teilt Text anhand eines angegebenen Trennzeichens.

**Werte:** `input`, `regex`, `max_parts`, `split_index`

**Beispiel:**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**Ausgabe:** `world`

## Text trimmen (`trim_text`)

**Zweck:** Entfernt führende und nachfolgende Leerzeichen.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**Ausgabe:** `hello world`

## Text zuschneiden (`crop_text`)

**Zweck:** Entfernt Zeichen vom Anfang und Ende eines Textes.

**Werte:** `text`, `remove_from_start`, `remove_from_end`

**Beispiel:**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**Ausgabe:** `ello worl`

## Stringify (`stringify`)

**Zweck:** Wandelt Text in eine Zeichenkette um, indem alle Syntaxzeichen maskiert werden.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**Ausgabe:** `text with \{special\} \"characters\"`

## Text lokalisieren (`local`)

**Zweck:** Ruft lokalisierten Text für einen Schlüssel ab.

**Werte:** `key`

**Beispiel:**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**Ausgabe:** `Singleplayer`

## Web-Text (`webtext`)

**Zweck:** Ruft Textinhalt von einer Web-URL ab.

**Werte:** `link`

**Beispiel:**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**Ausgabe:** `Welcome to the server!`

## Zufallstext (`randomtext`)

**Zweck:** Gibt eine zufällige Zeile aus einer Textdatei, einer URL oder direktem Klartext zurück. Der Text wechselt in festgelegten Intervallen. Datei- und URL-Inhalte werden ungefähr alle 30 Sekunden neu geladen; direkter Klartext bleibt zwischengespeichert, da kein Neuladen erforderlich ist.

**Werte:** `source`, `interval`

In Platzhalterwerten bedeutet `/config/...` `<game-directory>/config/...`; es ist kein Pfad zum Dateisystem-Stamm. Siehe [Ressourcen](./resources#local-resources).

**Beispiel:**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parameter:
- `source`: Die Quelle der Textzeilen (ersetzt den alten `path`-Parameter)
  - Dateipfad: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Klartext: `Line 1\nLine 2\nLine 3`
- `interval`: Zeit in Sekunden zwischen Textwechseln

Der Platzhalter unterstützt nun drei Quelltypen:
1. **Lokale Dateien**: Textdateien aus deinem Spielverzeichnis
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: Entfernte Textdateien aus dem Internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Klartext**: Direkte Texteingabe mit durch `\n` getrennten Zeilen
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Hinweis: Alte Platzhalter, die `path` statt `source` verwenden, funktionieren weiterhin.

## JSON-Parser (`json`)

**Zweck:** Parst JSON-Daten aus einer Datei, einer URL oder direktem JSON-Inhalt und extrahiert Werte mithilfe von JSON-Pfad-Ausdrücken.

**Werte:** `source`, `json_path`

**Beispiel:**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parameter:
- `source`: Die Quelle der JSON-Daten
  - Dateipfad: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Direktes JSON: `{"name":"Steve","level":42}`
- `json_path`: Der JSON-Pfad-Ausdruck zum Extrahieren der Daten

Der Platzhalter unterstützt nun drei Quelltypen:
1. **Lokale Dateien**: JSON-Dateien aus deinem Spielverzeichnis
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: Entfernte JSON-Daten von APIs oder Webdiensten
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Direktes JSON**: Inline-JSON-Inhalt
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Beispielhafte JSON-Pfade:
- `$.name` - Holt das Feld "name" aus der Wurzel
- `$.player.level` - Holt das verschachtelte Feld "level" innerhalb von "player"
- `$.items[0].id` - Holt die "id" des ersten Elements in einem Array
- `$.scores.*` - Holt alle Werte aus dem Objekt "scores"

## Absoluter Datei-/Ordnerpfad (`absolute_path`)

**Zweck:** Gibt den absoluten Pfad einer Datei zurück.

**Werte:** `short_path`

**Beispiel:**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**Ausgabe:** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## Anzahl der Textzeichen (`text_character_count`)

**Zweck:** Gibt die Anzahl der Zeichen im angegebenen Text zurück.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**Ausgabe:** `12`

## Textbreite (`text_width`)

**Zweck:** Gibt die Breite des angegebenen Textes in Pixeln zurück, wenn er gerendert wird.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**Ausgabe:** `66`

## Text in Großbuchstaben (`uppercase_text`)

**Zweck:** Wandelt den Eingabetext vollständig in Großbuchstaben um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**Ausgabe:** `HELLO WORLD`

## Text in Kleinbuchstaben (`lowercase_text`)

**Zweck:** Wandelt den Eingabetext vollständig in Kleinbuchstaben um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**Ausgabe:** `hello world`

## Text in Titel-Schreibweise (`title_case_text`)

**Zweck:** Wandelt den Eingabetext in Title Case um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**Ausgabe:** `Hello World`

## Text in Satz-Schreibweise (`sentence_case_text`)

**Zweck:** Wandelt den Eingabetext in Satzschreibung um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**Ausgabe:** `Hello world. This is fancymenu!`

## Text in Snake Case (`snake_case_text`)

**Zweck:** Wandelt den Eingabetext in `snake_case` um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**Ausgabe:** `hello_world`

## Text in Kebab Case (`kebab_case_text`)

**Zweck:** Wandelt den Eingabetext in `kebab-case` um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**Ausgabe:** `hello-world`

## Text in abwechselnder Groß-/Kleinschreibung (`alternating_case_text`)

**Zweck:** Wandelt den Eingabetext in abwechselnde Groß-/Kleinschreibung um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**Ausgabe:** `aLtErNaTiNg CaSe`

## Groß-/Kleinschreibung umkehren (`toggle_case_text`)

**Zweck:** Kehrt die Groß-/Kleinschreibung jedes Buchstabens im Eingabetext um.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**Ausgabe:** `tOGGLE cASE`

## In Base64 kodieren (`base64_encode`)

**Zweck:** Kodiert den angegebenen Text als Base64.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**Ausgabe:** `SGVsbG8gV29ybGQ=`

## Aus Base64 dekodieren (`base64_decode`)

**Zweck:** Dekodiert eine Base64-Zeichenfolge wieder in Klartext.

**Werte:** `text`

**Beispiel:**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**Ausgabe:** `Hello World`

## Datei-Text (`file_text`)

**Zweck:** Gibt Textzeilen aus einer Datei oder URL zurück. Kann alle Zeilen oder nur die letzten X Zeilen zurückgeben.

**Werte:** `path_or_url`, `mode`, `separator`, `last_lines`

**Beispiel:**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parameter:
- `path_or_url`: Datei- oder URL-Pfad, aus dem gelesen werden soll
- `mode`: Entweder `"all"` (gibt alle Zeilen zurück) oder `"last"` (gibt nur die letzten X Zeilen zurück)
- `separator`: Text zwischen den Zeilen (Standard: `"\n"`)
- `last_lines`: Anzahl der zurückzugebenden Zeilen, wenn `mode` `"last"` ist (Standard: `"1"`)

**Ausgabe:**

```text
First line
Second line
```

## Zwischenablageninhalt (`clipboard_content`)

**Zweck:** Gibt den aktuellen in der Systemzwischenablage gespeicherten Textinhalt zurück.

**Werte:** Keine

**Beispiel:**

```
{"placeholder":"clipboard_content"}
```

**Ausgabe:** `Hello from the clipboard`

## Text ersetzen (`replace_text`)

**Zweck:** Ersetzt Text in einer Zeichenfolge mithilfe von wörtlichem Text oder regulären Ausdrücken.

**Werte:** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**Beispiel:**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parameter:
- `text`: Der zu verarbeitende Eingabetext
- `search`: Der zu suchende Text oder Regex-Ausdruck
- `replacement`: Der Ersetzungstext
- `use_regex`: Ob Regex (`"true"`) oder exakte Textsuche (`"false"`) verwendet wird
- `replace_all`: Alle Vorkommen ersetzen (`"true"`) oder nur das erste (`"false"`)

**Ausgabe:** `Hello FancyMenu! This is a test.`

## Switch-Case (`switch_case`)

**Zweck:** Führt eine Switch-Case-Operation auf Basis eines Werts aus.

**Werte:** `value`, `cases`, `default`

**Beispiel:**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**Ausgabe:** `first case` (wenn der Wert 1 ist)

## Variablenwert abrufen (FM-Variable) (`getvariable`)

**Zweck:** Ruft den Wert einer zuvor gespeicherten Variablen ab.

**Werte:** `name`

**Beispiel:**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**Ausgabe:** `42`

## NBT-Daten abrufen (`nbt_data_get`)

**Zweck:** Ruft NBT-Daten auf dem Client ab (ähnlich dem Befehl `/data get`). Verwende die Server-Variante `nbt_data_get_server`, wenn du mit einem Server verbunden bist und maßgebliche serverseitige Werte benötigst.

**Werte:** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**Beispiel:**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parameter:
- `source_type`: Entweder `"entity"` oder `"block"`
- `entity_selector`: Entitätsselektor wie `@s`, `@p`, `@e` oder UUID/Name (für Entitäten)
- `block_pos`: Blockposition im Format `"x y z"` (für Blöcke)
- `nbt_path`: Der abzurufende NBT-Pfad
- `scale`: Optionaler Skalierungsfaktor für numerische Werte (Standard: `"1.0"`)
- `return_type`: Wie die Daten zurückgegeben werden:
  - `"value"`: Standard, gibt den Wert zurück (bei Zahlen mit optionaler Skalierung)
  - `"string"`: Gibt die eigentlichen NBT-Daten als Zeichenkette zurück
  - `"snbt"`: Gibt SNBT zurück (formatiertes NBT)
  - `"json"`: Gibt als JSON-formatierte Komponente zurück (für Compound-Tags)

**Ausgabe:** `20` (für Hungerwert)

## NBT-Daten abrufen (serverseitig) (`nbt_data_get_server`)

**Zweck:** Fragt NBT-Daten serverseitig ab (über ein Paket) und speichert Ergebnisse kurzzeitig im Cache. Die Werte entsprechen dem clientseitigen Platzhalter.

**Werte:** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**Beispiel:**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**Ausgabe:** `minecraft:diamond_sword`

## Letzte Todesnachricht (`lastdeathmessage`)

**Zweck:** Gibt die zuletzt aufgezeichnete Todesnachricht des Client-Spielers zurück. Setze `as_json_component` auf `"true"`, um die rohe JSON-Textkomponente zu erhalten.

**Werte:** `as_json_component`

**Beispiel:**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**Ausgabe:** `Steve was slain by Zombie`

## Laufzeitdauer (`uptime_duration`)

**Zweck:** Gibt an, wie lange FancyMenu geladen ist. Standardmäßig wird der Wert in Sekunden angegeben; setze `output_as_millis` auf `"true"`, um Millisekunden zu erhalten.

**Werte:** `output_as_millis`

**Beispiel:**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**Ausgabe:** `742` (Sekunden seit dem Laden)

## Speicherstand-Namen der Welt (`level_save_names`)

**Zweck:** Listet alle lokalen Weltspeicherstände mit dem gewählten Trennzeichen auf. Läuft im Client-Thread.

**Werte:** `separator`

**Beispiel:**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**Ausgabe:** `Creative Test, Survival World, Hardcore`

## Speicherstandsdaten der Welt (`level_save_data`)

**Zweck:** Gibt serialisierte Level-Daten für den angegebenen Weltnamen zurück (muss mit dem Anzeigenamen in der Speicherstandsliste übereinstimmen).

**Werte:** `level_name`

**Beispiel:**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**Ausgabe:** `{"name":"Survival World","gameMode":"survival",...}`

## Zahlensystem-Konverter (`number_base_convert`)

**Zweck:** Wandelt eine Zahl (ganz oder mit Nachkommastellen) von einer Basis in eine andere um (2–36). Standardmäßig Dezimal, wenn keine Basen angegeben sind.

**Werte:** `input`, `from_base`, `to_base`

**Beispiel:**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**Ausgabe:** `43.8`

## Dateigröße (`file_size`)

**Zweck:** Gibt die Größe einer lokalen Datei in Bytes zurück. Es sind nur lokale Pfade erlaubt.

**Werte:** `path`

**Beispiel:**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Ausgabe:** `1284`

## Datei-MD5 (`file_md5`)

**Zweck:** Gibt den MD5-Hash einer lokalen Datei als Kleinbuchstaben-Hexzeichenfolge zurück.

**Werte:** `path`

**Beispiel:**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Ausgabe:** `d41d8cd98f00b204e9800998ecf8427e`

# Praxisbeispiele

## Dynamische Speicheranzeige erstellen
```
Verwendeter RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Eine Echtzeituhr erstellen
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

## Eine Systeminformationsanzeige erstellen
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## Spielerstatus-HUD
```
Gesundheit: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Rüstung: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
XP-Stufe: {"placeholder":"current_player_level"}
```

## Komplexe Berechnung mit verschachtelten Platzhaltern
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Koordinatenanzeige mit Rundung
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Best Practices

1. **Teure Operationen zwischenspeichern**: Einige Platzhalter (z. B. solche, die Systeminformationen lesen) können ressourcenintensiv sein. Erwäge, ihre Werte in Variablen zu speichern, wenn du sie mehrfach verwenden musst.

2. **Geeignete Dezimaleinstellungen verwenden**: Wenn du mit Berechnungen arbeitest, verwende den Parameter `decimal` passend. Setze ihn auf `false`, wenn du Ganzzahlen benötigst, und auf `true`, wenn du genaue Dezimalwerte brauchst.

3. **Fehlende Werte behandeln**: Berücksichtige immer, was passieren soll, wenn ein Platzhalter keinen Wert zurückgibt. Möglicherweise möchtest du in solchen Fällen Standardwerte bereitstellen.

4. **Leistung testen**: Wenn du viele Platzhalter oder komplexe verschachtelte Strukturen verwendest, teste die Auswirkungen auf die Leistung, insbesondere auf Systemen mit geringerer Leistung.

5. **Erweiterte Größen-/Positionssteuerung verwenden**: Kombiniere für dynamische UI-Elemente Platzhalter mit erweiterter Größen- und Positionssteuerung, um reaktionsfähige Layouts zu erstellen.

6. **Mit Variablen kombinieren**: Verwende Platzhalter zusammen mit Variablen für noch dynamischere Inhalte, die über Aktionen aktualisiert werden können.

# Häufige Probleme und Lösungen

## Platzhalter wird nicht aktualisiert
Wenn sich der Wert eines Platzhalters nicht wie erwartet aktualisiert, prüfe:
- ob der Platzhalter korrekt formatiert ist
- ob du die richtige Groß-/Kleinschreibung für die Platzhalter-IDs verwendest
- ob der Platzhalter bestimmte Bedingungen benötigt, um sich zu aktualisieren

## Verschachtelte Platzhalter funktionieren nicht
Beim Verschachteln von Platzhaltern:
- sicherstellen, dass Anführungszeichen korrekt maskiert sind
- prüfen, ob jeder verschachtelte Platzhalter für sich allein gültig ist

## Leistungsprobleme
Wenn du Leistungsprobleme bemerkst:
- die Anzahl verwendeter Platzhalter reduzieren
- unnötige Verschachtelung vermeiden
- für häufig abgefragte Werte Variablen verwenden
- den passenden Platzhalter für deinen Anwendungsfall nutzen (z. B. keine Echtzeit-Platzhalter verwenden, wenn statische Werte ausreichen)
