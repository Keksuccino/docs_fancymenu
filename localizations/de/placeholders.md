---
title: Platzhalter
description: Wie man Platzhalter verwendet.
---
# Platzhalter

Platzhalter sind dynamische Werte, die beim Verwenden durch tatsächliche Inhalte ersetzt werden. In FancyMenu ermöglichen Platzhalter, dynamische Inhalte in verschiedene Elemente wie Text, Schaltflächen und Ladebedingungen einzufügen. Betrachte sie als Variablen, die ausgewertet und durch ihre tatsächlichen Werte ersetzt werden, wenn deine Layouts angezeigt werden.

# Allgemeine Informationen

## Grundsyntax
Platzhalter in FancyMenu verwenden eine JSON-ähnliche Syntax:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Zum Beispiel, um den Namen des Spielers anzuzeigen:
```
{"placeholder":"playername"}
```

## Platzhalter verschachteln
Eine der leistungsstärksten Funktionen des Platzhalter-Systems von FancyMenu ist die Möglichkeit, Platzhalter innerhalb anderer Platzhalter zu verschachteln. Das bedeutet, dass du die Ausgabe eines Platzhalters als Eingabe für einen anderen verwenden kannst.

Beispiel für verschachtelte Platzhalter:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Dieses Beispiel nimmt den maximalen RAM-Wert und teilt ihn durch 1024, um ihn von MB in GB umzuwandeln.

> [!IMPORTANT]
> Anders als echtes JSON werden verschachtelte Platzhalter **nicht** durch `\` **escaped**. Das ist sehr wichtig, denn Platzhalter funktionieren nicht mehr, wenn sie escaped werden (offensichtlich). Platzhalter verwenden nur eine JSON-ähnliche Syntax. Es ist kein echtes JSON.

# Platzhalter verwenden

Die meisten Elemente mit Texteingaben unterstützen Platzhalter. Beim Bearbeiten kannst du sehen, ob eine Texteingabe Platzhalter unterstützt. Wenn beim Bearbeiten des Textes der Vollbild-**Texteditor** geöffnet wird, unterstützt er Platzhalter.

Um eine **Liste aller Platzhalter** zu finden, klicke einfach auf die Schaltfläche **Platzhalter** in der **oberen rechten Ecke** des **Texteditors**.

Oben in der Platzhalterliste befindet sich eine **Suchleiste**, mit der du Platzhalter suchen kannst.

Wenn du in der Platzhalterliste auf einen Platzhalter klickst, wird er in den Textinhalt eingefügt.

# Platzhalter im Detail

Diese Liste enthält die meisten, wenn nicht sogar alle, in FancyMenu verfügbaren Platzhalter. Die Liste kann durch Mod-Updates manchmal etwas veraltet sein.

## Spielername (playername)
Gibt den Benutzernamen des aktuellen Spielers zurück.
```
{"placeholder":"playername"}
```
Beispielausgabe: `Steve`

## Spieler-UUID (playeruuid)
Gibt die eindeutige Kennung des Spielers zurück.
```
{"placeholder":"playeruuid"}
```
Beispielausgabe: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Minecraft-Version (mcversion)
Gibt die aktuelle Minecraft-Version zurück.
```
{"placeholder":"mcversion"}
```
Beispielausgabe: `1.19.2`

## Mod-Loader-Version (loaderver)
Gibt die Version des Mod-Loaders (Forge/Fabric) zurück.
```
{"placeholder":"loaderver"}
```
Beispielausgabe: `43.2.0`

## Mod-Loader-Name (loadername)
Gibt den Namen des Mod-Loaders zurück.
```
{"placeholder":"loadername"}
```
Beispielausgabe: `Forge`

## Mod-Version (modversion)
Gibt die Version eines bestimmten Mods zurück.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Beispielausgabe: `2.14.9`

## Gesamtzahl der Mods (totalmods)
Gibt die Gesamtzahl der installierten Mods zurück.
```
{"placeholder":"totalmods"}
```
Beispielausgabe: `45`

## Anzahl aktiver Mods (loadedmods)
Gibt die Anzahl der aktuell geladenen Mods zurück.
```
{"placeholder":"loadedmods"}
```
Beispielausgabe: `43`

## Fortschritt beim Laden der Welt (world_load_progress)
Gibt den aktuellen Ladefortschritt der Welt in Prozent zurück.
```
{"placeholder":"world_load_progress"}
```
Beispielausgabe: `75`

## Minecraft-Optionswert (minecraft_option_value)
Gibt den Wert einer Minecraft-Option zurück.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Beispielausgabe: `70`

## Letzte Welt oder letzter Server (last_world_server)
Gibt Informationen über die zuletzt geöffnete Welt oder den zuletzt verwendeten Server zurück.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parameter:
- `type`: Bestimmt, welche Art von Information zurückgegeben wird
  - `"both"`: Gibt die zuletzt geöffnete Welt oder den zuletzt verwendeten Server zurück (Standard)
  - `"server"`: Gibt nur zurück, wenn zuletzt ein Server verwendet wurde
  - `"world"`: Gibt nur zurück, wenn zuletzt eine Welt verwendet wurde
- `full_world_path`: Steuert, wie Weltpfade angezeigt werden
  - `"true"`: Gibt den vollständigen Weltpfad zurück (Standard)
  - `"false"`: Gibt nur den Weltnamen ohne Pfad zurück (betrifft Server nicht)

Beispiele:
- Server: `mc.hypixel.net`
- Welt mit vollständigem Pfad: `saves/New World`
- Welt ohne vollständigen Pfad: `New World`

## Bildschirmbreite (guiwidth)
Gibt die aktuelle Bildschirmbreite zurück.
```
{"placeholder":"guiwidth"}
```
Beispielausgabe: `1920`

## Bildschirmhöhe (guiheight)
Gibt die aktuelle Bildschirmhöhe zurück.
```
{"placeholder":"guiheight"}
```
Beispielausgabe: `1080`

## Aktuelle Bildschirm-ID (screenid)
Gibt die Kennung des aktuellen Bildschirms zurück.
```
{"placeholder":"screenid"}
```
Beispielausgabe: `title_screen`

## Elementbreite (elementwidth)
Gibt die Breite eines bestimmten Elements zurück.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Beispielausgabe: `200`

## Elementhöhe (elementheight)
Gibt die Höhe eines bestimmten Elements zurück.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Beispielausgabe: `20`

## X-Position des Elements (elementposx)
Gibt die X-Position eines bestimmten Elements zurück.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Beispielausgabe: `150`

## Y-Position des Elements (elementposy)
Gibt die Y-Position eines bestimmten Elements zurück.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Beispielausgabe: `100`

## Maus-X-Position (mouseposx)
Gibt die aktuelle X-Position der Maus zurück.
```
{"placeholder":"mouseposx"}
```
Beispielausgabe: `960`

## Maus-Y-Position (mouseposy)
Gibt die aktuelle Y-Position der Maus zurück.
```
{"placeholder":"mouseposy"}
```
Beispielausgabe: `540`

## Klicks pro Sekunde (clicks_per_second)
Gibt die aktuellen Klicks pro Sekunde für eine Maustaste zurück.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parameter:
- `mouse_button`: `left` oder `right`

Beispielausgabe: `8`

## GUI-Skalierung (guiscale)
Gibt die aktuelle GUI-Skalierung zurück.
```
{"placeholder":"guiscale"}
```
Beispielausgabe: `2`

## Beschriftung/Text eines Vanilla-Widgets (vanillabuttonlabel)
Gibt die Beschriftung/den Text eines Vanilla-Widgets/einer Vanilla-Schaltfläche zurück.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Beispielausgabe: `Options...`

## Wert eines Texteingabefelds (text_input_field_value)
Gibt den aktuellen Wert eines benutzerdefinierten oder Vanilla-Texteingabefelds anhand der Element-ID zurück.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Beispielausgabe: `Hello World`

## Aktuelle Gesundheit des Spielers (current_player_health)
Gibt die aktuellen Lebenspunkte des Spielers zurück.
```
{"placeholder":"current_player_health"}
```
Beispielausgabe: `20.0`

## Maximale Gesundheit des Spielers (max_player_health)
Gibt die maximalen Lebenspunkte des Spielers zurück.
```
{"placeholder":"max_player_health"}
```
Beispielausgabe: `20.0`

## Aktuelle Gesundheit des Spielers (Prozent) (current_player_health_percent)
Gibt die Gesundheit des Spielers in Prozent zurück.
```
{"placeholder":"current_player_health_percent"}
```
Beispielausgabe: `100`

## Aktuelle Absorptionsgesundheit des Spielers (current_player_absorption_health)
Gibt die Absorptions-Lebenspunkte des Spielers zurück (goldene Herzen).
```
{"placeholder":"current_player_absorption_health"}
```
Beispielausgabe: `4.0`

## Maximale Absorptionsgesundheit des Spielers (max_player_absorption_health)
Gibt die maximale Absorptionsgesundheit zurück.
```
{"placeholder":"max_player_absorption_health"}
```
Beispielausgabe: `4.0`

## Aktuelle Absorptionsgesundheit des Spielers (Prozent) (current_player_absorption_health_percent)
Gibt die Absorptionsgesundheit des Spielers in Prozent zurück.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Beispielausgabe: `100`

## Aktueller Hunger des Spielers (current_player_hunger)
Gibt den aktuellen Hungerwert des Spielers zurück.
```
{"placeholder":"current_player_hunger"}
```
Beispielausgabe: `20`

## Maximaler Hunger des Spielers (max_player_hunger)
Gibt den maximalen Hungerwert zurück.
```
{"placeholder":"max_player_hunger"}
```
Beispielausgabe: `20`

## Aktueller Hunger des Spielers (Prozent) (current_player_hunger_percent)
Gibt den Hunger des Spielers in Prozent zurück.
```
{"placeholder":"current_player_hunger_percent"}
```
Beispielausgabe: `100`

## Aktuelle Hungersättigung des Spielers (current_player_hunger_saturation)
Gibt den aktuellen Sättigungswert des Spielers zurück.
```
{"placeholder":"current_player_hunger_saturation"}
```
Beispielausgabe: `5.0`

## Aktuelle Rüstung des Spielers (current_player_armor)
Gibt den aktuellen Rüstungswert des Spielers zurück.
```
{"placeholder":"current_player_armor"}
```
Beispielausgabe: `20`

## Rüstungshärte des Spielers (player_armor_toughness)
Gibt den gesamten Rüstungshärtewert des Spielers zurück.
```
{"placeholder":"player_armor_toughness"}
```
Beispielausgabe: `8.0`

## Maximale Rüstung des Spielers (max_player_armor)
Gibt den maximalen Rüstungswert zurück.
```
{"placeholder":"max_player_armor"}
```
Beispielausgabe: `20`

## Aktuelle Rüstung des Spielers (Prozent) (current_player_armor_percent)
Gibt die Rüstung des Spielers in Prozent zurück.
```
{"placeholder":"current_player_armor_percent"}
```
Beispielausgabe: `100`

## Aktueller Sauerstoffwert des Spielers (current_player_oxygen)
Gibt den aktuellen Sauerstoffwert des Spielers zurück (Luftblasen).
```
{"placeholder":"current_player_oxygen"}
```
Beispielausgabe: `300`

## Maximaler Sauerstoffwert des Spielers (max_player_oxygen)
Gibt den maximalen Sauerstoffwert zurück.
```
{"placeholder":"max_player_oxygen"}
```
Beispielausgabe: `300`

## Aktueller Sauerstoffwert des Spielers (Prozent) (current_player_oxygen_percent)
Gibt den Sauerstoffwert des Spielers in Prozent zurück.
```
{"placeholder":"current_player_oxygen_percent"}
```
Beispielausgabe: `100`

## Aktuelle Spielerstufe (current_player_level)
Gibt die aktuelle Erfahrungsstufe des Spielers zurück.
```
{"placeholder":"current_player_level"}
```
Beispielausgabe: `30`

## Aktuelle Erfahrung des Spielers (current_player_exp)
Gibt die gesamten Erfahrungspunkte des Spielers zurück.
```
{"placeholder":"current_player_exp"}
```
Beispielausgabe: `1250`

## Erfahrungsfortschritt des Spielers (Prozent) (current_player_exp_progress)
Gibt den Erfahrungsfortschritt des Spielers bis zur nächsten Stufe in Prozent zurück.
```
{"placeholder":"current_player_exp_progress"}
```
Beispielausgabe: `75`

## Angriffsstärke des Spielers (Prozent) (player_attack_strength)
Gibt die Angriffs-Abklingzeit des Spielers in Prozent zurück.
```
{"placeholder":"player_attack_strength"}
```
Beispielausgabe: `100`

## Spielmodus des Spielers (player_gamemode)
Gibt den aktuellen Spielmodus des Spielers zurück.
```
{"placeholder":"player_gamemode"}
```
Beispielausgabe: `survival`

## Blickrichtung des Spielers (player_view_direction)
Gibt die Richtung zurück, in die der Spieler blickt.
```
{"placeholder":"player_view_direction"}
```
Beispielausgabe: `north`

## X-Koordinate des Spielers (player_x_coordinate)
Gibt die X-Position des Spielers in der Welt zurück.
```
{"placeholder":"player_x_coordinate"}
```
Beispielausgabe: `125`

## Y-Koordinate des Spielers (player_y_coordinate)
Gibt die Y-Position des Spielers in der Welt zurück.
```
{"placeholder":"player_y_coordinate"}
```
Beispielausgabe: `64`

## Z-Koordinate des Spielers (player_z_coordinate)
Gibt die Z-Position des Spielers in der Welt zurück.
```
{"placeholder":"player_z_coordinate"}
```
Beispielausgabe: `-250`

## Aktuelle Reittier-Gesundheit (current_mount_health)
Gibt die aktuelle Gesundheit des Wesens zurück, auf dem der Spieler reitet.
```
{"placeholder":"current_mount_health"}
```
Beispielausgabe: `30.0`

## Maximale Reittier-Gesundheit (max_mount_health)
Gibt die maximale Gesundheit des Wesens zurück, auf dem der Spieler reitet.
```
{"placeholder":"max_mount_health"}
```
Beispielausgabe: `30.0`

## Aktuelle Reittier-Gesundheit (Prozent) (current_mount_health_percent)
Gibt die Gesundheit des Reittiers in Prozent zurück.
```
{"placeholder":"current_mount_health_percent"}
```
Beispielausgabe: `100`

## Aktueller Reittier-Sprungbalken (Prozent) (current_mount_jump_meter)
Gibt den Wert des Sprungbalkens des Reittiers zurück.
```
{"placeholder":"current_mount_jump_meter"}
```
Beispielausgabe: `75`

## Aktuelle Boss-Gesundheit (Prozent) (current_boss_health)
Gibt die Gesundheit des aktiven Bosses zurück.
```
{"placeholder":"current_boss_health"}
```
Beispielausgabe: `150.0`

## Bossname (boss_name)
Gibt den Namen des aktiven Bosses zurück.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Beispielausgabe: `Ender Dragon`

## Anzahl der Bosse (boss_count)
Gibt die Anzahl aktiver Bosse zurück.
```
{"placeholder":"boss_count"}
```
Beispielausgabe: `1`

## Anzahl aktiver Effekte (effects_count)
Gibt die Anzahl aktiver Trankeffekte zurück.
```
{"placeholder":"effects_count"}
```
Beispielausgabe: `3`

## Aktiver Effekt (active_effect)
Gibt Informationen über einen bestimmten aktiven Effekt zurück.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Beispielausgabe: `minecraft:speed`

## Ausgewählter Hotbar-Slot (active_hotbar_slot)
Gibt den aktuell ausgewählten Hotbar-Slot zurück (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Beispielausgabe: `4`

## Slot-Gegenstand (slot_item)
Gibt Informationen über einen Gegenstand in einem bestimmten Inventarslot zurück.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Beispielausgabe: `minecraft:diamond_sword`

## Anzahl des Slot-Gegenstands (slot_item_count)
Gibt die Stapelgröße des Gegenstands in einem bestimmten Spieler-Inventarslot zurück.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Beispielausgabe: `64`

## Haltbarkeit des Slot-Gegenstands (slot_item_durability)
Gibt Informationen zur Haltbarkeit des Gegenstands in einem bestimmten Spieler-Inventarslot zurück.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parameter:
- `slot`: Inventarslot-Nummer des Spielers.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` oder `percent`.

Beispielausgabe: `87`

## Anzeigename des Slot-Gegenstands (slot_item_display_name_fm)
Gibt den Anzeigenamen des Gegenstands in einem bestimmten Slot als JSON-Textkomponente zurück. Im Zuschauermodus können Hotbar-Slots Namen von Zuschauermenü-Gegenständen auflösen, sofern `ignore_spectator` nicht `true` ist.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Beispielausgabe: `{"text":"Diamond Sword","color":"aqua"}`

## Anzahl von Inventargegenständen (inventory_item_count)
Gibt die Gesamtanzahl eines Gegenstandstyps im Spielerinventar zurück. Wenn `item` leer ist, werden alle Gegenstandsstapel im Inventar gezählt.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Beispielausgabe: `12`

## Menge an Hungerpunkten, die ein Inventarslot wiederherstellt (inventory_slot_food_point_restore_amount)
Gibt die Hungerpunkte zurück, die das Essen im angegebenen Spieler-Inventarslot wiederherstellt.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Beispielausgabe: `4.0`

## Über dem Inventar schwebender Gegenstand (hovered_inventory_item)
Gibt den Gegenstands-Key des aktuell in einem Inventarbildschirm anvisierten Gegenstands zurück.
```
{"placeholder":"hovered_inventory_item"}
```
Beispielausgabe: `minecraft:apple`

## Spielzeit der Welt (game_time)
Gibt den aktuellen Tick-Zähler der Spielzeit zurück.
```
{"placeholder":"game_time"}
```
Beispielausgabe: `18000`

## Welt-Tageszeit (world_daytime)
Gibt die aktuelle Tageszeit der Welt zurück.
```
{"placeholder":"world_daytime"}
```
Beispielausgabe: `13000`

## Stunde der Welt-Tageszeit (world_daytime_hour)
Gibt die Stundenkomponente der Weltzeit zurück. Standardmäßig wird das 24-Stunden-Format verwendet; setze `twelve_hour_format` auf `"true"` für das 12-Stunden-Format.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Beispielausgabe: `12`

## Minute der Welt-Tageszeit (world_daytime_minute)
Gibt die Minutenkomponente der Weltzeit zurück (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Beispielausgabe: `30`

## Welt-Schwierigkeitsgrad (world_difficulty)
Gibt den aktuellen Schwierigkeitsgrad der Welt zurück.
```
{"placeholder":"world_difficulty"}
```
Beispielausgabe: `normal`

## Aktueller Welt-Seed (current_world_seed)
Gibt den Seed der aktuellen Einzelspielerwelt zurück. Gibt einen leeren Wert zurück, wenn der Seed nicht verfügbar ist.
```
{"placeholder":"current_world_seed"}
```
Beispielausgabe: `123456789`

## Aktuelles Biom (current_biome)
Gibt das Biom zurück, in dem sich der Spieler aktuell befindet. Setze `as_key` auf `"false"`, um einen übersetzten/angezeigten Namen zurückzugeben, sofern verfügbar.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Beispielausgabe: `minecraft:plains`

## Aktuelle Dimension (current_dimension)
Gibt die Dimension zurück, in der sich der Spieler aktuell befindet. Setze `as_key` auf `"false"`, um einen übersetzten/angezeigten Namen zurückzugeben, sofern verfügbar.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Beispielausgabe: `minecraft:overworld`

## Gamerule-Wert (gamerule_value)
Gibt den aktuellen Wert einer Gamerule in der geladenen Welt/im Server zurück. Serverwelten erfordern FancyMenu auf dem Server.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Beispielausgabe: `true`

## Gegenstandskategorie (item_category)
Gibt die Kreativtab-Kategorie eines Gegenstands zurück. Setze `as_key` auf `"true"`, um den Kategorienamen statt des Anzeigenamens zurückzugeben.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Beispielausgabe: `Combat`

## Aktueller HUD-Titel/Untertitel (current_title)
Gibt den aktuell angezeigten Titeltext zurück.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Beispielausgabe: `Game Over!`

## Action-Bar-Nachricht (action_bar_message_fm)
Gibt die aktuelle Vanilla-Action-Bar-Nachricht über der Hotbar zurück.
```
{"placeholder":"action_bar_message_fm"}
```
Beispielausgabe: `You may not rest now`

## Anzeigezeit der Action-Bar-Nachricht (action_bar_message_time_fm)
Gibt an, wie viele Ticks die aktuelle Vanilla-Action-Bar-Nachricht noch angezeigt wird.
```
{"placeholder":"action_bar_message_time_fm"}
```
Beispielausgabe: `42`

## Kamerarotation X (camera_rotation_x_fm)
Gibt die aktuelle Kameraneigung in Grad zurück.
```
{"placeholder":"camera_rotation_x_fm"}
```
Beispielausgabe: `12.5`

## Kamerarotation Y (camera_rotation_y_fm)
Gibt den aktuellen Kamera-Yaw in Grad zurück.
```
{"placeholder":"camera_rotation_y_fm"}
```
Beispielausgabe: `-90.0`

## Delta der Kamerarotation X (camera_rotation_delta_x_fm)
Gibt die Änderung der Kameraneigung pro Tick zurück.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Beispielausgabe: `0.4`

## Delta der Kamerarotation Y (camera_rotation_delta_y_fm)
Gibt die Änderung des Kamera-Yaw pro Tick zurück.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Beispielausgabe: `-1.2`

## Anzeigezeit des hervorgehobenen Gegenstands (highlighted_item_time_fm)
Gibt an, wie viele Ticks der Name des hervorgehobenen Gegenstands noch über der Hotbar angezeigt wird.
```
{"placeholder":"highlighted_item_time_fm"}
```
Beispielausgabe: `30`

## Nutzungsfortschritt des Spielergegenstands (player_item_use_progress_fm)
Gibt den aktuellen Fortschritt der Gegenstandsnutzung von `0.0` bis `1.0` zurück.
```
{"placeholder":"player_item_use_progress_fm"}
```
Beispielausgabe: `0.65`

## Positions-Delta des Spielers X (player_position_delta_x_fm)
Gibt die Positionsänderung des Spielers auf der X-Achse pro Tick zurück.
```
{"placeholder":"player_position_delta_x_fm"}
```
Beispielausgabe: `0.0`

## Positions-Delta des Spielers Y (player_position_delta_y_fm)
Gibt die Positionsänderung des Spielers auf der Y-Achse pro Tick zurück.
```
{"placeholder":"player_position_delta_y_fm"}
```
Beispielausgabe: `-0.08`

## Positions-Delta des Spielers Z (player_position_delta_z_fm)
Gibt die Positionsänderung des Spielers auf der Z-Achse pro Tick zurück.
```
{"placeholder":"player_position_delta_z_fm"}
```
Beispielausgabe: `0.12`

## Aktuelle Server-IP (current_server_ip)
Gibt die IP des verbundenen Servers zurück.
```
{"placeholder":"current_server_ip"}
```
Beispielausgabe: `mc.hypixel.net`

## Spielerliste der Welt (world_players_list)
Gibt eine Liste aller Spieler zurück, die sich aktuell in der Welt befinden.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Beispielausgabe: `Steve, Alex, Notch`

## Server-MOTD (servermotd)
Gibt die Message of the Day eines Servers zurück.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Beispielausgabe: `Welcome to Hypixel!`

## Server-PING (serverping)
Gibt den Ping zu einem Server in Millisekunden zurück.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Beispielausgabe: `54`

## Server-Spielerzahl (serverplayercount)
Gibt die Spielerzahl eines Servers zurück.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Beispielausgabe: `25000/30000`

## Serverstatus (serverstatus)
Gibt den Online-/Offline-Status eines Servers zurück.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Beispielausgabe: `§aOnline` oder `§cOffline`

## Server-Version (serverversion)
Gibt die Minecraft-Version eines Servers zurück.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Beispielausgabe: `1.19.2`

## Jahr (realtimeyear)
Gibt das aktuelle Jahr zurück.
```
{"placeholder":"realtimeyear"}
```
Beispielausgabe: `2024`

## Monat (realtimemonth)
Gibt den aktuellen Monat zurück (01-12).
```
{"placeholder":"realtimemonth"}
```
Beispielausgabe: `01`

## Tag (realtimeday)
Gibt den aktuellen Tag des Monats zurück (01-31).
```
{"placeholder":"realtimeday"}
```
Beispielausgabe: `27`

## Stunde (realtimehour)
Gibt die aktuelle Stunde zurück. Standardmäßig wird das 24-Stunden-Format verwendet; setze `twelve_hour_format` auf `"true"`, um das 12-Stunden-Format zu verwenden.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Beispielausgabe: `14`

## Minute (realtimeminute)
Gibt die aktuelle Minute zurück (00-59).
```
{"placeholder":"realtimeminute"}
```
Beispielausgabe: `30`

## Sekunde (realtimesecond)
Gibt die aktuelle Sekunde zurück (00-59).
```
{"placeholder":"realtimesecond"}
```
Beispielausgabe: `45`

## Aktuelle Zeit in Millisekunden (Unix-Zeitstempel) (unix_time)
Gibt den aktuellen Unix-Zeitstempel in Millisekunden zurück.
```
{"placeholder":"unix_time"}
```
Beispielausgabe: `1716552478123`

> Realtime-Platzhalter (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` und `unix_time`) unterstützen einen `timezone`-Wert. Verwende normale Java-Zeitzonen-IDs wie `UTC`, `Europe/Berlin` oder `America/New_York`; lasse ihn weg oder verwende `system` für die Systemzeitzone.
{.is-info}

## CPU-Info (cpuinfo)
Gibt Informationen über die CPU zurück.
```
{"placeholder":"cpuinfo"}
```
Beispielausgabe: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## CPU-Auslastung (JVM) (jvmcpu)
Gibt die CPU-Auslastung der JVM in Prozent zurück.
```
{"placeholder":"jvmcpu"}
```
Beispielausgabe: `25.5`

## CPU-Auslastung (OS) (oscpu)
Gibt die CPU-Auslastung des Betriebssystems in Prozent zurück.
```
{"placeholder":"oscpu"}
```
Beispielausgabe: `42.8`

## GPU-Info (gpuinfo)
Gibt Informationen über die GPU zurück.
```
{"placeholder":"gpuinfo"}
```
Beispielausgabe: `NVIDIA GeForce RTX 3080`

## Java-Version (javaver)
Gibt die Java-Version zurück.
```
{"placeholder":"javaver"}
```
Beispielausgabe: `17.0.2`

## Java Virtual Machine (jvmname)
Gibt den Namen der Java Virtual Machine zurück.
```
{"placeholder":"jvmname"}
```
Beispielausgabe: `OpenJDK 64-Bit Server VM`

## OpenGL-Version (glver)
Gibt die OpenGL-Version zurück.
```
{"placeholder":"glver"}
```
Beispielausgabe: `4.6.0 NVIDIA 516.94`

## Name des Betriebssystems (osname)
Gibt den Namen des Betriebssystems zurück.
```
{"placeholder":"osname"}
```
Beispielausgabe: `Windows 10`

## FPS (Bilder pro Sekunde) (fps)
Gibt die aktuellen Bilder pro Sekunde zurück.
```
{"placeholder":"fps"}
```
Beispielausgabe: `120`

## Verwendeter RAM in MB (usedram)
Gibt die aktuell verwendete RAM-Menge in MB zurück.
```
{"placeholder":"usedram"}
```
Beispielausgabe: `4096`

## Maximaler RAM in MB (maxram)
Gibt den maximal zugewiesenen RAM in MB zurück.
```
{"placeholder":"maxram"}
```
Beispielausgabe: `8192`

## Verwendeter RAM in %% (percentram)
Gibt den aktuell verwendeten RAM-Anteil in Prozent zurück.
```
{"placeholder":"percentram"}
```
Beispielausgabe: `50`

## Lautstärke eines Audio-Elements (audio_element_vol)
Gibt die Lautstärke eines Audio-Elements zurück.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Beispielausgabe: `0.5`

## Aktueller Audiotrack (audio_element_current_track)
Gibt den Track-Namen eines Audio-Elements zurück.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Beispielausgabe: `Cool Track Name`

## Audiodauer (audio_duration)
Gibt die Gesamtdauer eines Audiotracks im Format MM:SS zurück.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Beispielausgabe: `03:45`

## Audiowiedergabezeit (audio_playtime)
Gibt die aktuelle Wiedergabezeit eines Audiotracks zurück. Setze `show_percentage` auf `"true"`, um statt `MM:SS` einen Fortschrittswert von 0-100 zu erhalten.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Beispielausgabe: `01:30` (oder `45` wenn `show_percentage` `"true"` ist)

## Audiowiedergabestatus (audio_playing_state)
Gibt zurück, ob ein Audio-Element abgespielt wird (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Beispielausgabe: `true`

## Lautstärke eines Video-Elements (video_element_vol)
Gibt den Lautstärkepegel eines Video-Elements zurück (0.0 bis 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Beispielausgabe: `0.5`

## Dauer eines Video-Elements (video_element_duration)
Gibt die Gesamtdauer eines Video-Elements im Format `MM:SS` zurück. Setze `output_as_timestamp` auf `"true"`, um einen Millisekunden-Zeitstempel zurückzugeben.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Beispielausgabe: `02:00` (oder `120000` wenn `output_as_timestamp` `"true"` ist)

## Wiedergabezeit eines Video-Elements (video_element_playtime)
Gibt die aktuelle Wiedergabezeit (den Fortschritt) eines Video-Elements im Format `MM:SS` zurück. Setze `show_percentage` auf `"true"` für einen Fortschrittswert von 0-100 oder `output_as_timestamp` auf `"true"` für Millisekunden.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Beispielausgabe: `00:45` (oder `38` als Prozentwert oder `45200` als Zeitstempel)

## Pausierter Status eines Video-Elements (video_element_paused_state)
Gibt zurück, ob ein Video-Element pausiert ist (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Beispielausgabe: `false`

## Lautstärke des Video-Hintergrunds (video_background_vol)
Gibt den Lautstärkepegel eines Video-Menühintergrunds zurück (0.0 bis 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Beispielausgabe: `0.7`

## Dauer des Video-Hintergrunds (video_background_duration)
Gibt die Gesamtdauer eines Video-Menühintergrunds im Format `MM:SS` zurück. Setze `output_as_timestamp` auf `"true"`, um einen Millisekunden-Zeitstempel zurückzugeben.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Beispielausgabe: `03:00` (oder `180000` wenn `output_as_timestamp` `"true"` ist)

## Wiedergabezeit des Video-Hintergrunds (video_background_playtime)
Gibt die aktuelle Wiedergabezeit (den Fortschritt) eines Video-Menühintergrunds im Format `MM:SS` zurück. Setze `show_percentage` auf `"true"` für einen Fortschrittswert von 0-100 oder `output_as_timestamp` auf `"true"` für Millisekunden.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Beispielausgabe: `01:00` (oder `33` als Prozentwert oder `60500` als Zeitstempel)

## Pausierter Status des Video-Hintergrunds (video_background_paused_state)
Gibt zurück, ob ein Video-Menühintergrund pausiert ist (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Beispielausgabe: `true`

## Rechner (calc)
Der Rechner-Platzhalter ist ein leistungsstarkes Werkzeug, mit dem du mathematische Berechnungen innerhalb deiner Layouts durchführen kannst. Er unterstützt eine breite Palette mathematischer Operationen und kann sowohl mit Dezimal- als auch mit Ganzzahlen arbeiten.

### Grundsyntax
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"dein_ausdruck"}}
```

Der Rechner hat zwei Hauptparameter:
- `decimal`: Legt fest, ob das Ergebnis Dezimalstellen enthalten soll (`true`) oder auf ganze Zahlen gerundet wird (`false`)
- `expression`: Der mathematische Ausdruck, der ausgewertet werden soll

### Unterstützte Operationen
Der Rechner unterstützt diese mathematischen Operationen:
- Grundrechenarten: `+` (Addition), `-` (Subtraktion), `*` (Multiplikation), `/` (Division)
- Klammern: `( )` zum Gruppieren von Operationen
- Potenzen: `^` für Exponenten
- Quadratwurzel: `sqrt()`
- Trigonometrische Funktionen: `sin()`, `cos()`, `tan()`
- Mathematische Konstanten: `pi`, `e`
- Absolutwert: `abs()`
- Logarithmen: `log()`, `ln()`

## Zufallszahl (random_number)
Erzeugt eine Zufallszahl innerhalb eines angegebenen Bereichs.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Beispielausgabe: `42`

## Größte Zahl (maxnum)
Gibt die größere von zwei Zahlen zurück.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Beispielausgabe: `20`

## Kleinste Zahl (minnum)
Gibt die kleinere von zwei Zahlen zurück.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Beispielausgabe: `10`

## Absolutwert (absnum)
Gibt den Absolutwert einer Zahl zurück.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Beispielausgabe: `10.5`

## Zahl negieren (negnum)
Gibt den negierten Wert einer Zahl zurück.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Beispielausgabe: `-10.5`

## *pi* (Mathematik) (math_pi)
Gibt den Wert von π zurück.
```
{"placeholder":"math_pi"}
```
Beispielausgabe: `3.141592653589793`

## Trigonometrischer Sinus (Mathematik) (math_sin)
Gibt den Sinus eines Winkels zurück.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Beispielausgabe: `0.7071067811865476`

## Trigonometrischer Kosinus (Mathematik) (math_cos)
Gibt den Kosinus eines Winkels zurück.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Beispielausgabe: `0.7071067811865476`

## Trigonometrischer Tangens (Mathematik) (math_tan)
Gibt den Tangens eines Winkels zurück.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Beispielausgabe: `1.0`

## Abrunden (Mathematik) (math_floor)
Rundet eine Zahl auf die nächstkleinere ganze Zahl ab.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Beispielausgabe: `3`

## Aufrunden (Mathematik) (math_ceil)
Rundet eine Zahl auf die nächstgrößere ganze Zahl auf.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Beispielausgabe: `4`

## Runden (Mathematik) (math_round)
Rundet eine Zahl. Standardmäßig wird auf die nächstgelegene ganze Zahl gerundet; setze `decimals` auf eine nichtnegative Zahl, um auf so viele Dezimalstellen zu runden.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Beispielausgabe: `3.14` (mit `decimals:-1` oder weggelassen → `3`)

## Vorzeichen (Mathematik) (math_sign)
Gibt das Vorzeichen einer Zahl zurück (1 für positiv, -1 für negativ, 0 für null).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Beispielausgabe: `-1`

## Hyperbolischer Sinus (Mathematik) (math_sinh)
Gibt den hyperbolischen Sinus eines Winkels zurück.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Beispielausgabe: `1.1752011936438014`

## Hyperbolischer Kosinus (Mathematik) (math_cosh)
Gibt den hyperbolischen Kosinus eines Winkels zurück.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Beispielausgabe: `1.5430806348152437`

## Hyperbolischer Tangens (Mathematik) (math_tanh)
Gibt den hyperbolischen Tangens eines Winkels zurück.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Beispielausgabe: `0.7615941559557649`

## Text teilen (split_text)
Teilt Text anhand eines angegebenen Trennzeichens.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Beispielausgabe: `world`

## Text trimmen (trim_text)
Entfernt führende und abschließende Leerzeichen.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Beispielausgabe: `hello world`

## Text beschneiden (crop_text)
Entfernt Zeichen vom Anfang und Ende des Textes.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Beispielausgabe: `ello worl`

## Stringify (stringify)
Macht einen Text zu einem String, indem alle Syntaxzeichen escaped werden.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Beispielausgabe: `text with \{special\} \"characters\"`

## Text lokalisieren (local)
Ruft lokalisierten Text für einen Schlüssel ab.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Beispielausgabe: `Singleplayer`

## Web-Text (webtext)
Ruft Textinhalt von einer Web-URL ab.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Beispielausgabe: Textinhalt von der URL

## Zufälliger Text (randomtext)
Gibt eine zufällige Zeile aus einer Textdatei, einer URL oder direkt eingegebenem Klartext zurück. Der Text ändert sich in festgelegten Intervallen.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parameter:
- `source`: Die Quelle der Textzeilen (ersetzt den alten `path`-Parameter)
  - Dateipfad: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Klartext: `Line 1\nLine 2\nLine 3`
- `interval`: Zeit in Sekunden zwischen Textänderungen

Der Platzhalter unterstützt jetzt drei Quellentypen:
1. **Lokale Dateien**: Textdateien aus deinem Spielverzeichnis
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: Entfernte Textdateien aus dem Internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Klartext**: Direkte Texteingabe mit Zeilen, getrennt durch `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Hinweis: Alte Platzhalter, die `path` statt `source` verwenden, funktionieren weiterhin.

## JSON-Parser (json)
Parst JSON-Daten aus einer Datei, einer URL oder direktem JSON-Inhalt und extrahiert Werte mithilfe von JSON-Pfad-Ausdrücken.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parameter:
- `source`: Die Quelle der JSON-Daten
  - Dateipfad: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Direktes JSON: `{"name":"Steve","level":42}`
- `json_path`: Der JSON-Pfad-Ausdruck zum Extrahieren von Daten

Der Platzhalter unterstützt jetzt drei Quellentypen:
1. **Lokale Dateien**: JSON-Dateien aus deinem Spielverzeichnis
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: Entfernte JSON-Daten von APIs oder Webdiensten
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Direktes JSON**: Eingebetteter JSON-Inhalt
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Beispiel-JSON-Pfade:
- `$.name` - Holt das Feld „name“ aus der Wurzel
- `$.player.level` - Holt das verschachtelte Feld „level“ innerhalb von „player“
- `$.items[0].id` - Holt die „id“ des ersten Elements in einem Array
- `$.scores.*` - Holt alle Werte aus dem Objekt „scores“

## Absoluter Datei-/Ordnerpfad (absolute_path)
Gibt den absoluten Pfad einer Datei zurück.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Beispielausgabe: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Anzahl der Textzeichen (text_character_count)
Gibt die Anzahl der Zeichen im angegebenen Text zurück.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Beispielausgabe: `12`

## Textbreite (text_width)
Gibt die Breite des angegebenen Textes in Pixeln zurück, wenn er gerendert wird.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Beispielausgabe: `66`

## Text in Großbuchstaben (uppercase_text)
Wandelt den Eingabetext in Großbuchstaben um.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Beispielausgabe: `HELLO WORLD`

## Text in Kleinbuchstaben (lowercase_text)
Wandelt den Eingabetext in Kleinbuchstaben um.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Beispielausgabe: `hello world`

## Titel-Schreibweise (title_case_text)
Wandelt den Eingabetext in Titel-Schreibweise um.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Beispielausgabe: `Hello World`

## Satz-Schreibweise (sentence_case_text)
Wandelt den Eingabetext in Satz-Schreibweise um.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Beispielausgabe: `Hello world. This is fancymenu!`

## Snake-Case-Text (snake_case_text)
Wandelt den Eingabetext in `snake_case` um.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Beispielausgabe: `hello_world`

## Kebab-Case-Text (kebab_case_text)
Wandelt den Eingabetext in `kebab-case` um.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Beispielausgabe: `hello-world`

## Wechselnde Groß-/Kleinschreibung (alternating_case_text)
Wandelt den Eingabetext in abwechselnde Groß-/Kleinschreibung um.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Beispielausgabe: `aLtErNaTiNg CaSe`

## Groß-/Kleinschreibung umkehren (toggle_case_text)
Ändert die Groß-/Kleinschreibung jedes Buchstabens im Eingabetext.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Beispielausgabe: `tOGGLE cASE`

## In Base64 kodieren (base64_encode)
Kodiert den angegebenen Text als Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Beispielausgabe: `SGVsbG8gV29ybGQ=`

## Aus Base64 dekodieren (base64_decode)
Dekodiert eine Base64-Zeichenkette wieder in Klartext.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Beispielausgabe: `Hello World`

## Datei-Text (file_text)
Gibt Textzeilen aus einer Datei oder URL zurück. Kann alle Zeilen oder nur die letzten X Zeilen zurückgeben.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parameter:
- `path_or_url`: Datei- oder URL-Pfad, aus dem gelesen wird
- `mode`: Entweder `"all"` (gibt alle Zeilen zurück) oder `"last"` (gibt nur die letzten X Zeilen zurück)
- `separator`: Text, mit dem Zeilen verbunden werden (Standard: `"\n"`)
- `last_lines`: Anzahl der zurückzugebenden Zeilen, wenn `mode` `"last"` ist (Standard: `"1"`)

Beispielausgabe: Hängt vom Dateiinhalt ab

## Zwischenablage-Inhalt (clipboard_content)
Gibt den aktuellen Textinhalt zurück, der in der Systemzwischenablage gespeichert ist.
```
{"placeholder":"clipboard_content"}
```
Beispielausgabe: Beliebiger Text, der sich gerade in der Zwischenablage befindet

## Text ersetzen (replace_text)
Ersetzt Text in einer Zeichenkette mithilfe von Literaltext oder regulären Ausdrücken.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parameter:
- `text`: Der zu verarbeitende Eingabetext
- `search`: Der zu suchende Text oder Regex-Ausdruck
- `replacement`: Der Ersetzungstext
- `use_regex`: Ob Regex verwendet werden soll (`"true"`) oder wörtliche Übereinstimmung (`"false"`)
- `replace_all`: Alle Vorkommen ersetzen (`"true"`) oder nur das erste (`"false"`)

Beispielausgabe: `Hello FancyMenu! This is a test.`

## Switch-Case (switch_case)
Führt eine Switch-Case-Operation basierend auf einem Wert aus.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Beispielausgabe: `first case` (wenn der Wert 1 ist)

## Variablenwert abrufen (FM Variable) (getvariable)
Ruft den Wert einer zuvor gespeicherten Variable ab.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Beispielausgabe: Hängt vom gespeicherten Wert ab

## NBT-Daten abrufen (nbt_data_get)
Ruft NBT-Daten auf dem Client ab (ähnlich dem Befehl `/data get`). Verwende die Server-Variante `nbt_data_get_server`, wenn du mit einem Server verbunden bist und autoritative Serverwerte benötigst.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parameter:
- `source_type`: Entweder `"entity"` oder `"block"`
- `entity_selector`: Entity-Selektor wie `@s`, `@p`, `@e` oder UUID/Name (für Entitäten)
- `block_pos`: Blockposition im Format `"x y z"` (für Blöcke)
- `nbt_path`: Der abzurufende NBT-Pfad
- `scale`: Optionaler Skalierungsfaktor für numerische Werte (Standard: `"1.0"`)
- `return_type`: Wie die Daten zurückgegeben werden:
  - `"value"`: Standard, gibt den Wert zurück (mit optionaler Skalierung für Zahlen)
  - `"string"`: Gibt die eigentlichen NBT-Daten als String zurück
  - `"snbt"`: Gibt als SNBT zurück (formatiertes NBT)
  - `"json"`: Gibt als JSON-formatierte Komponente zurück (für Compound-Tags)

Beispielausgabe: `20` (für den Hungerwert)

## NBT-Daten abrufen (Server-seitig) (nbt_data_get_server)
Fragt NBT-Daten auf der Serverseite ab (über ein Paket) und speichert Ergebnisse kurzzeitig im Cache. Die Werte entsprechen dem clientseitigen Platzhalter.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Beispielausgabe: `minecraft:diamond_sword`

## Letzte Todesnachricht (lastdeathmessage)
Gibt die zuletzt aufgezeichnete Todesnachricht des lokalen Spielers zurück. Setze `as_json_component` auf `"true"`, um die rohe JSON-Textkomponente zu erhalten.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Beispielausgabe: `Steve was slain by Zombie`

## Laufzeitdauer (uptime_duration)
Gibt zurück, wie lange FancyMenu bereits geladen ist. Standardmäßig ist der Wert in Sekunden; setze `output_as_millis` auf `"true"`, um Millisekunden zu erhalten.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Beispielausgabe: `742` (Sekunden seit dem Laden)

## Welt-Speichernamen (level_save_names)
Listet alle lokalen Weltspeichernamen auf, verbunden durch das gewählte Trennzeichen. Läuft im Client-Thread.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Beispielausgabe: `Creative Test, Survival World, Hardcore`

## Welt-Speicherdaten (level_save_data)
Gibt serialisierte Level-Daten für den angegebenen Weltnamen zurück (muss mit dem angezeigten Namen in der Speicherliste übereinstimmen).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Beispielausgabe: `{"name":"Survival World","gameMode":"survival",...}`

## Zahlensystem-Konverter (number_base_convert)
Konvertiert eine Zahl (ganzzahlig oder mit Nachkommastellen) von einem Zahlensystem in ein anderes (2–36). Standardmäßig Dezimal, wenn keine Basen angegeben sind.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Beispielausgabe: `43.8`

## Dateigröße (file_size)
Gibt die Größe einer lokalen Datei in Bytes zurück. Es sind nur lokale Pfade erlaubt.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Beispielausgabe: `1284`

## Datei-MD5 (file_md5)
Gibt den MD5-Hash einer lokalen Datei als Hex-String in Kleinbuchstaben zurück.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Beispielausgabe: `d41d8cd98f00b204e9800998ecf8427e`

# Praktische Beispiele

## Eine dynamische Anzeige für den Speicher erstellen
```
Verwendeter RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Eine Echtzeituhr erstellen
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
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

1. **Teure Operationen cachen**: Manche Platzhalter (z. B. solche, die Systeminformationen lesen) können ressourcenintensiv sein. Überlege, ihre Werte in Variablen zu speichern, wenn du sie mehrfach verwenden möchtest.

2. **Geeignete Dezimal-Einstellungen verwenden**: Bei Berechnungen solltest du den Parameter `decimal` passend einsetzen. Setze ihn auf `false`, wenn du Ganzzahlen brauchst, und auf `true`, wenn du genaue Dezimalwerte benötigst.

3. **Fehlende Werte behandeln**: Überlege immer, was passieren soll, wenn ein Platzhalter keinen Wert zurückgibt. Möglicherweise möchtest du in solchen Fällen Standardwerte angeben.

4. **Leistung testen**: Wenn du viele Platzhalter oder komplexe verschachtelte Strukturen verwendest, teste die Auswirkungen auf die Performance, besonders auf schwächeren Systemen.

5. **Erweiterte Größen- und Positionsangaben verwenden**: Für dynamische UI-Elemente kannst du Platzhalter mit erweiterter Größen- und Positionssteuerung kombinieren, um responsive Layouts zu erstellen.

6. **Mit Variablen kombinieren**: Verwende Platzhalter zusammen mit Variablen für noch dynamischere Inhalte, die über Aktionen aktualisiert werden können.

# Häufige Probleme und Lösungen

## Platzhalter wird nicht aktualisiert
Wenn sich der Wert eines Platzhalters nicht wie erwartet aktualisiert, prüfe:
- Ob der Platzhalter korrekt formatiert ist
- Ob du die richtige Groß-/Kleinschreibung für die Platzhalter-IDs verwendest
- Ob der Platzhalter unter bestimmten Bedingungen überhaupt aktualisiert werden muss

## Verschachtelte Platzhalter funktionieren nicht
Beim Verschachteln von Platzhaltern:
- Stelle sicher, dass Anführungszeichen korrekt escaped sind
- Prüfe, ob jeder verschachtelte Platzhalter für sich allein gültig ist

## Performance-Probleme
Wenn du Performance-Probleme bemerkst:
- Reduziere die Anzahl verwendeter Platzhalter
- Vermeide unnötige Verschachtelungen
- Erwäge, Variablen für häufig abgefragte Werte zu verwenden
- Nutze den passenden Platzhalter für deinen Bedarf (z. B. keine Realtime-Platzhalter, wenn statische Werte ausreichen)
