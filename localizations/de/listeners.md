---
title: Listener
description: Wie man Listener in FancyMenu erstellt und verwendet.
---

# Listener

Listener führen [Action-Skripte](./action-scripts) aus, wenn bestimmte Ereignisse auftreten. Sie sind nicht an einen geöffneten Bildschirm gebunden, sodass sie auch während des Spielens oder Ladens ausgeführt werden können.

Listener können ihren Aktionen und Anforderungen `$$`-Werte bereitstellen, z. B. eine gedrückte Taste oder eine angeklickte Maustaste.

> [!CAUTION]
> Ein Listener kann Datei-, Netzwerk-, Befehls-, Zwischenablage-, Ressourcepaket- oder Link-Aktionen ausführen, ohne dass ein Bildschirm geöffnet ist. Importiere Listener nur aus Quellen, denen du vertraust.

# Listener verwenden

Öffne außerhalb des Layout-Editors **Menüleiste -> Anpassung -> Listener verwalten**, um Listener zu erstellen oder zu bearbeiten.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Listener verwalten" style="max-width:800px;width:100%;height:auto;">

# Listener-Variablen

Listener können ihren Aktionen und Anforderungen schreibgeschützte Werte bereitstellen. Verwende ihre `$$`-Namen in unterstützten Textfeldern.

Verwende zum Beispiel [**Bei Tastendruck**](#on-keyboard-key-pressed-keyboard_key_pressed) mit der [**In das Spiel-Log schreiben**-Aktion](./action-scripts#print-to-game-log-print_to_log). Der Wert `Taste gedrückt! Die Taste ist: $$key_name` fügt den Namen der gedrückten Taste ein.

> [!WARNING]
> Listener-Variablen sind getrennt von FancyMenus [gespeicherten Variablen](./variables). Aktionen, Anforderungen und Platzhalter für gespeicherte Variablen funktionieren nicht mit `$$`-Werten.

Listener-Variablennamen berücksichtigen Groß- und Kleinschreibung und funktionieren nur innerhalb des Skripts dieses Listeners.

Behandle Werte aus Chat, entfernten Servern, Dateien und Benutzereingaben als nicht vertrauenswürdig. Füge sie nicht direkt in Pfade, URLs oder Befehle ein.

Listener-Variablen sind Zeichenketten. Wenn Informationen nicht verfügbar sind, kann ein Listener einen dokumentierten Sentinel-Wert wie `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` oder eine leere Zeichenkette zurückgeben. Teste diese Werte, bevor du Listener-Daten in Pfade, Befehle oder URLs einfügst.

# Listener im Detail

Dieser Abschnitt listet die integrierten Listener von FancyMenu auf.

## Bei Markdown-Text angeklickt (`text_clicked`)
- Wird ausgelöst, wenn [Markdown-Text mit einem `click:`-Ereignis](./text-formatting#click-and-hover-events) angeklickt wird, zum Beispiel `[Öffnen](click:open_menu)`.
- Variablen:
  - `$$text_event_id` – Ereignis-ID aus dem Markdown-Link

## Bei Markdown-Text darübergefahren (`text_hovered`)
- Wird ausgelöst, wenn [Markdown-Text mit einem `hover:`-Ereignis](./text-formatting#click-and-hover-events) mit der Maus überfahren wird, zum Beispiel `[Hinweis](hover:show_hint)`.
- Variablen:
  - `$$text_event_id` – Ereignis-ID aus dem Markdown-Link

## Bei per Aktion extrahiertem ZIP (`zip_extracted_via_action`)
- Wird ausgelöst, wenn die [**ZIP-Datei im Spielverzeichnis extrahieren**-Aktion](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir) abgeschlossen ist.
- Variablen:
  - `$$source_zip_path` – normalisierter, benutzerfreundlicher Quellpfad; Pfade im Spielverzeichnis können als `/...` zurückgegeben werden, während herkömmliche Minecraft-Verzeichnispfade `.minecraft/...` verwenden können
  - `$$target_folder_path` – normalisierter, benutzerfreundlicher Zielpfad mit denselben Pfadformen
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – Fehlertext, wenn die Extraktion fehlgeschlagen ist

## Bei erzeugtem Element (`element_spawned_via_action`)
- Wird ausgelöst, wenn eine unterstützte FancyMenu-Funktion oder ein Add-on dynamisch eine Elementinstanz erzeugt.
- Variablen:
  - `$$element_type` – erzeugter Elementtyp
  - `$$element_identifier` – Kennung des erzeugten Elements
  - `$$target_screen` – Zielbildschirm-Kennung

## Bei Start der animierten Textur-Wiedergabe (`animated_texture_started_playing`)
- Wird ausgelöst, wenn eine [animierte Textur](./fma) zu spielen beginnt.
- Variablen:
  - `$$texture_source` – Texturquelle
  - `$$texture_source_type` – Quellentyp
  - `$$texture_will_restart` – true/false

## Bei Ende der animierten Textur-Wiedergabe (`animated_texture_finished_playing`)
- Wird ausgelöst, wenn eine animierte Textur fertig abgespielt wurde.
- Variablen:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## Bei geändertem Videowiedergabestatus (`video_playback_status_changed`)
- Wird ausgelöst, wenn ein [Video-Element oder Menü-Hintergrund](./video) den Wiedergabestatus ändert.
- Variablen:
  - `$$video_source` – Videoquelle
  - `$$video_source_type` – Quellentyp
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` oder `FINISHED`

## Bei empfangener Systemnachricht im Chat (`system_message_received_in_chat`)
- Wird ausgelöst, wenn der Client eine System-Chatnachricht empfängt, z. B. eine Befehlsrückmeldung.
- Variablen:
  - `$$system_message_string` – Klartextnachricht
  - `$$system_message_component` – JSON-Komponente

## Bei empfangenen FM-Daten (`fm_data_received`)
- Wird ausgelöst, wenn ein Server diesem Client über `/fmdata send` [FM-Daten](./fm-data) sendet.
- Variablen:
  - `$$data_identifier` – Datenkennungs-String
  - `$$data` – Datennutzlast
  - `$$sent_by` – Server-IP oder `integrated_server`

## Bei verbundener Remote-Server-Verbindung (`remote_server_connected`)
- Wird ausgelöst, nachdem eine [Remote-Server-Verbindung](./remote-server-communication) erfolgreich geöffnet wurde.
- Variablen:
  - `$$request_id` – zwischengespeicherte Anfrage-ID
  - `$$remote_server_url` – URL des Remote-Servers

## Bei empfangenen Remote-Server-Daten (`remote_server_data_received`)
- Wird ausgelöst, wenn Textdaten von einem verbundenen Remote-Server empfangen werden.
- Variablen:
  - `$$request_id` – Anfrage-ID
  - `$$remote_server_url` – URL des Remote-Servers
  - `$$data` – empfangene Nutzlast

## Bei geschlossener Remote-Server-Verbindung (`remote_server_connection_closed`)
- Wird ausgelöst, wenn eine Remote-Server-Verbindung geschlossen wird.
- Variablen:
  - `$$request_id` – Anfrage-ID
  - `$$remote_server_url` – URL des Remote-Servers
  - `$$intentionally_closed` – TRUE, wenn durch eine Aktion geschlossen
  - `$$crashed` – TRUE, wenn die Verbindung unerwartet abgestürzt ist
  - `$$unknown_close_reason` – TRUE, wenn kein bekannter Schließungsgrund verfügbar war

## Bei Tastendruck (`keyboard_key_pressed`)
- Wird jedes Mal ausgelöst, wenn eine Taste gedrückt wird (wiederholt, solange sie gehalten wird; funktioniert in Bildschirmen und im Spiel).
- Variablen:
  - `$$key_name` – Anzeigename der Taste
  - `$$key_keycode` – GLFW-Tastencode
  - `$$key_scancode` – GLFW-Scancode
  - `$$key_modifiers` – aktive Modifizierer-Bitmaske

## Bei Tastenfreigabe (`keyboard_key_released`)
- Wird ausgelöst, wenn eine Taste losgelassen wird (Bildschirme und im Spiel).
- Variablen:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## Bei eingegebenem Tastaturzeichen im Bildschirm (`keyboard_char_typed`)
- Wird ausgelöst, wenn ein Zeichen eingegeben wird, während ein Bildschirm geöffnet ist.
- Variablen:
  - `$$char` – eingegebenes Zeichen

## Bei Mausbewegung im Bildschirm (`mouse_moved`)
- Wird ausgelöst, wann immer sich die Maus bewegt, während ein Bildschirm geöffnet ist.
- Variablen:
  - `$$mouse_pos_x` – aktuelles X
  - `$$mouse_pos_y` – aktuelles Y
  - `$$mouse_move_delta_x` – X-Delta seit dem letzten Ereignis
  - `$$mouse_move_delta_y` – Y-Delta seit dem letzten Ereignis

## Bei Mausklick (`mouse_button_clicked`)
- Wird ausgelöst, wenn eine Maustaste gedrückt wird (Bildschirme und im Spiel).
- Variablen:
  - `$$button` – links/rechts/Mitte
  - `$$mouse_pos_x` – aktuelles X
  - `$$mouse_pos_y` – aktuelles Y

## Bei Maustastenfreigabe (`mouse_button_released`)
- Wird ausgelöst, wenn eine Maustaste losgelassen wird (Bildschirme und im Spiel).
- Variablen:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## Bei Mausradbewegung im Bildschirm (`mouse_scrolled`)
- Wird ausgelöst, wenn das Mausrad bewegt wird, während ein Bildschirm geöffnet ist.
- Variablen:
  - `$$scroll_delta_y` – vertikales Scrollen

## Bei geöffnetem Bildschirm (`screen_open`)
- Wird direkt ausgeführt, nachdem ein beliebiger Bildschirm aktiv wird; kann verwendet werden, um ihn zu überschreiben.
- Variablen:
  - `$$screen_identifier` – Kennung des geöffneten Bildschirms

## Bei geschlossenem Bildschirm (`screen_close`)
- Wird unmittelbar nach dem Schließen eines Bildschirms ausgeführt.
- Variablen:
  - `$$screen_identifier` – Kennung des geschlossenen Bildschirms

## Beim Beenden von Minecraft (`quit_minecraft`)
- Wird einmal ausgelöst, wenn der Client mit dem Herunterfahren beginnt.
- Variablen:
  - `$$timestamp_millis` – Epoch-Millis beim Beenden
  - `$$timestamp_iso` – ISO-8601-Zeitstempel des Beendigungszeitpunkts

## Bei Tod (`player_death`)
- Wird ausgeführt, wenn für den lokalen Spieler der Vanilla-Todesbildschirm geöffnet wird.
- Variablen:
  - `$$days_survived` – Tage seit dem letzten Tod
  - `$$death_reason_string` – Ursache als Klartext
  - `$$death_reason_component` – Ursache als JSON-Komponente
  - `$$death_pos_x` – Todes-X-Koordinate
  - `$$death_pos_y` – Todes-Y-Koordinate
  - `$$death_pos_z` – Todes-Z-Koordinate

## Bei aktualisierter Variable [FM-Variable] (`fm_variable_updated`)
- Wird ausgelöst, wenn eine [FancyMenu-Variable](./variables) gesetzt oder aktualisiert wird.
- Variablen:
  - `$$var_name` – Variablenname
  - `$$old_value` – vorheriger Wert
  - `$$new_value` – neuer Wert

## Bei per Aktion heruntergeladener Datei (`file_downloaded_via_action`)
- Wird ausgelöst, nachdem die [**Datei ins Spielverzeichnis herunterladen**-Aktion](./action-scripts#download-file-to-game-directory-download_file_to_game_dir) abgeschlossen ist.
- Variablen:
  - `$$download_url` – Downloadquelle
  - `$$target_file_path` – gespeicherter Dateipfad bei Erfolg; bei Fehlschlag kann dies nur das Zielverzeichnis enthalten, da kein endgültiger Dateiname ermittelt wurde
  - `$$download_succeeded` – true/false

## Bei ausgewählter Datei (`file_selected_via_action`)
- Wird ausgelöst, nachdem die [**Datei aus dem System auswählen**-Aktion](./action-scripts#select-file-from-system-select_file_to_game_dir) abgeschlossen ist.
- Variablen:
  - `$$selected_file_path` – absoluter ausgewählter Dateipfad oder leer bei Abbruch
  - `$$target_file_path` – aufgelöster Pfad innerhalb der Instanz
  - `$$selection_succeeded` – true, wenn das Kopieren erfolgreich war
  - `$$selection_cancelled` – true, wenn der Dialog geschlossen wurde
  - `$$failure_reason` – Fehlerinformationen bei einem Fehler

## Bei empfangener Chatnachricht (`chat_message_received`)
- Wird ausgelöst, wenn eine normale Spieler-Chatzeile beim Client erscheint.
- Variablen:
  - `$$chat_message_string` – Klartextzeile
  - `$$chat_message_component` – vollständige JSON-Komponente
  - `$$sender_uuid` – UUID des Absenders oder ERROR
  - `$$sender_name` – Name des Absenders oder ERROR

## Bei gesendeter Chatnachricht (`chat_message_sent`)
- Wird ausgelöst, wenn der lokale Spieler eine Chatnachricht sendet.
- Variablen:
  - `$$chat_message_string` – Klartextzeile
  - `$$chat_message_component` – vollständige JSON-Komponente

## Bei erhaltenem Effekt (`effect_gained`)
- Wird ausgelöst, wenn der Spieler einen Status-Effekt erhält.
- Variablen:
  - `$$effect_key` – Ressourcenort des Effekts
  - `$$effect_type` – positiv/negativ/neutral
  - `$$effect_duration` – verbleibende Ticks

## Bei verlorenenem Effekt (`effect_lost`)
- Wird ausgelöst, wenn der Spieler einen Status-Effekt verliert.
- Variablen:
  - `$$effect_key` – abgelaufener Effekt
  - `$$effect_type` – Kategorie

## Bei geänderter Erfahrung (`experience_changed`)
- Wird ausgelöst, wann immer sich die gesamte XP des Spielers ändert.
- Variablen:
  - `$$new_experience_amount` – nach der Änderung
  - `$$old_experience_amount` – vor der Änderung
  - `$$is_level_up` – TRUE, wenn das Level gestiegen ist

## Bei erlittenem Schaden (`damage_taken`)
- Wird einmal pro Treffer ausgelöst, wenn der Spieler Schaden erleidet.
- Variablen:
  - `$$damage_amount` – entfernte Lebenspunkte
  - `$$damage_type` – Ressourcenort des Schadenstyps
  - `$$is_fatal_damage` – TRUE, wenn tödlich
  - `$$damage_source` – Ressourcenort des Angreifers oder NONE

## Bei beginnendem Einfrieren (`started_freezing`)
- Wird ausgelöst, wenn der Spieler anfängt einzufrieren.
- Variablen:
  - `$$freezing_intensity` – 0.0 = kein Einfrieren, 1.0 = vollständig eingefroren

## Bei gestopptem Einfrieren (`stopped_freezing`)
- Wird ausgelöst, wenn der Spieler nicht mehr einfriert.
- Variablen:
  - (keine)

## Bei vollständig eingefroren (`fully_frozen`)
- Wird einmal ausgelöst, wenn der Spieler vollständig eingefroren ist.
- Variablen:
  - (keine)

## Bei Beginn, einen Block anzusehen (`start_looking_at_block`)
- Wird einmal ausgelöst, wenn das Fadenkreuz zum ersten Mal auf einen Block zeigt (maximal 20 Blöcke Entfernung).
- Variablen:
  - `$$block_key` – anvisierter Block
  - `$$block_pos_x` – Block-X
  - `$$block_pos_y` – Block-Y
  - `$$block_pos_z` – Block-Z
  - `$$distance_to_player` – von den Augen bis zur Trefferposition

## Bei Ende, einen Block anzusehen (`stop_looking_at_block`)
- Wird ausgelöst, wenn das Fadenkreuz nicht mehr auf einen Block zeigt (meldet den zuletzt anvisierten Block, maximal 20 Blöcke).
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## Bei Beginn, eine Entität anzusehen (`start_looking_at_entity`)
- Wird einmal ausgelöst, wenn das Fadenkreuz zum ersten Mal auf eine Entität zeigt (maximal 20 Blöcke).
- Variablen:
  - `$$entity_key` – anvisierter Entitätstyp
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei Ende, eine Entität anzusehen (`stop_looking_at_entity`)
- Wird ausgelöst, wenn das Fadenkreuz nicht mehr auf eine Entität zeigt (meldet die zuletzt anvisierte Entität, maximal 20 Blöcke).
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei gespawnter Entität (`entity_spawned`)
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, wenn irgendwo auf der verbundenen Welt/dem Server eine Entität spawnt.
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player` – −1 bei anderer Dimension
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## Bei gestorbener Entität (`entity_died`)
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, wenn irgendeine Entität auf der verbundenen Welt/dem Server stirbt.
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player` – −1 bei anderer Dimension
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## Bei Beginn, eine Entität im Sichtfeld zu haben (`entity_starts_being_in_sight`)
- Wird ausgelöst, wenn eine Entität zum ersten Mal innerhalb von 200 Blöcken sichtbar wird.
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei Ende, eine Entität im Sichtfeld zu haben (`entity_stops_being_in_sight`)
- Wird ausgelöst, wenn eine zuvor sichtbare Entität aus dem Blickfeld verschwindet oder sich weiter als 200 Blöcke entfernt.
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei Interaktion mit Entität (`entity_interacted`)
- Wird ausgelöst, wenn der Spieler erfolgreich mit einer Entität interagiert.
- Variablen:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei bestiegener Entität (`entity_mounted`)
- Wird ausgelöst, wenn der Spieler beginnt, eine Entität zu reiten.
- Variablen:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei abgestiegener Entität (`entity_unmounted`)
- Wird ausgelöst, wenn der Spieler nicht mehr auf seiner aktuellen Entität reitet.
- Variablen:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei zerbrochenem Block (`block_broke`)
- Wird ausgelöst, wenn der Spieler einen Block abbaut.
- Variablen:
  - `$$block_key`
  - `$$broke_with_item_key` – verwendetes Werkzeug oder EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Bei platziertem Block (`block_placed`)
- Wird ausgelöst, wenn der Spieler einen Block platziert.
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Bei Interaktion mit Block (`interacted_with_block`)
- Wird ausgelöst, wenn der Spieler erfolgreich mit einem Block interagiert.
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Bei Betreten eines Blocks (`stepping_on_block`)
- Wird ausgelöst, wenn der Spieler auf einen Block tritt.
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Bei Betreten eines Bioms (`enter_biome`)
- Wird ausgelöst, wenn der Spieler ein neues Biom betritt.
- Variablen:
  - `$$biome_key` – betretenes Biom

## Bei Verlassen eines Bioms (`leave_biome`)
- Wird ausgelöst, wenn der Spieler sein aktuelles Biom verlässt.
- Variablen:
  - `$$biome_key` – gerade verlassenes Biom

## Bei Betreten einer Struktur (`enter_structure`)
- **Erfordert FancyMenu auf dem Server.** Grobe Erkennung des Strukturgebiets; kann in der Nähe, oberhalb oder unterhalb der Struktur auslösen.
- Variablen:
  - `$$structure_key` – betretene Struktur

## Bei Verlassen einer Struktur (`leave_structure`)
- **Erfordert FancyMenu auf dem Server.** Grobe Erkennung; kann in der Nähe des Struktur-Footprints auslösen.
- Variablen:
  - `$$structure_key` – gerade verlassene Struktur

## Bei Betreten einer Struktur (hohe Präzision) (`enter_structure_high_precision`)
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, wenn der Spieler die Begrenzungsboxen einer Struktur betritt.
- Variablen:
  - `$$structure_key`

## Bei Verlassen einer Struktur (hohe Präzision) (`leave_structure_high_precision`)
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, nachdem der Spieler die Begrenzungsboxen einer Struktur verlässt.
- Variablen:
  - `$$structure_key`

## Bei betretenem Dimension (`enter_dimension`)
- Wird ausgelöst, wenn der Spieler eine neue Dimension betritt.
- Variablen:
  - `$$dimension_key` – betretene Dimension

## Bei Beginn des Schwimmens (`start_swimming`)
- Wird ausgelöst, wenn der Spieler anfängt zu schwimmen.
- Variablen:
  - `$$fluid_type` – Ressourcenort der Flüssigkeit

## Bei Ende des Schwimmens (`stop_swimming`)
- Wird ausgelöst, wenn der Spieler aufhört zu schwimmen.
- Variablen:
  - `$$fluid_type` – Flüssigkeit, in der das Schwimmen beendet wurde

## Bei Beginn des Berührens einer Flüssigkeit (`start_touching_fluid`)
- Wird ausgelöst, wenn der Spieler beginnt, eine Flüssigkeit zu berühren.
- Variablen:
  - `$$fluid_type` – berührte Flüssigkeit

## Bei Ende des Berührens einer Flüssigkeit (`stop_touching_fluid`)
- Wird ausgelöst, wenn der Spieler eine Flüssigkeit nicht mehr berührt.
- Variablen:
  - `$$fluid_type` – nicht mehr berührte Flüssigkeit

## Bei gestarteter Musikspur (`music_track_started`)
- Wird ausgelöst, wenn eine neue Musikspur beginnt.
- Variablen:
  - `$$track_resource_location` – Audiodatei
  - `$$track_display_name` – lesbarer Name oder UNKNOWN
  - `$$track_artist` – Künstler oder UNKNOWN
  - `$$track_duration_ms` – Millisekunden (0, wenn unbekannt)

## Bei gestoppter Musikspur (`music_track_stopped`)
- Wird ausgelöst, wenn die aktuelle Musikspur endet oder ersetzt wird.
- Variablen:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## Bei ausgelöstem Weltsound (`world_sound_triggered`)
- Wird ausgelöst, wenn ein positionsbezogener Weltsound in der Nähe des Spielers startet.
- Variablen:
  - `$$sound_resource_location` – Sounddatei
  - `$$sound_display_name` – Untertitelname, falls verfügbar
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – Grad 0–360 relativ zur Blickrichtung

## Bei geändertem Wetter (`weather_changed`)
- Wird ausgelöst, wenn sich das Wetter global oder lokal ändert (Biome-Wechsel oder Betreten von Innenräumen kann es erneut auslösen).
- Variablen:
  - `$$weather_type` – klar/Regen/Gewitter
  - `$$weather_can_snow` – TRUE, wenn Schnee gerendert wird
  - `$$weather_can_rain` – TRUE, wenn Regen gerendert wird

## Bei beginnendem Brennen (`started_burning`)
- Wird ausgelöst, wenn der Spieler anfängt zu brennen.
- Variablen:
  - (keine)

## Bei gestopptem Brennen (`stopped_burning`)
- Wird ausgelöst, wenn der Spieler nicht mehr brennt.
- Variablen:
  - (keine)

## Bei beginnendem Ertrinken (`started_drowning`)
- Wird ausgelöst, wenn der Spieler beginnt, Ertrinkungsschaden zu erleiden.
- Variablen:
  - (keine)

## Bei Positionsänderung (`position_changed`)
- Wird ausgelöst, wann immer sich die Blockposition des Spielers ändert.
- Variablen:
  - `$$old_pos_x` – vorheriges Block-X
  - `$$old_pos_y` – vorheriges Block-Y
  - `$$old_pos_z` – vorheriges Block-Z
  - `$$new_pos_x` – neues Block-X
  - `$$new_pos_y` – neues Block-Y
  - `$$new_pos_z` – neues Block-Z

## Bei begonnenem Rennen (`started_running`)
- Wird ausgelöst, wenn der Spieler zu sprinten beginnt.
- Variablen:
  - (keine)

## Bei beendetem Rennen (`stopped_running`)
- Wird ausgelöst, wenn der Spieler aufhört zu sprinten.
- Variablen:
  - (keine)

## Bei Sprung (`jump`)
- Wird ausgelöst, wann immer der Spieler springt.
- Variablen:
  - (keine)

## Bei Server beigetreten (`server_joined`)
- Wird ausgelöst, nachdem erfolgreich einem Multiplayer-Server beigetreten wurde.
- Variablen:
  - `$$server_ip` – Adresse des beigetretenen Servers

## Bei Server verlassen (`server_left`)
- Wird ausgelöst, nachdem die Verbindung zu einem Multiplayer-Server getrennt wurde.
- Variablen:
  - `$$server_ip` – Adresse des verlassenen Servers

## Einzelspielerwelt betreten (`world_entered`)
- Wird ausgelöst, nachdem eine Einzelspielerwelt fertig geladen wurde und die Kontrolle zurückgegeben wird.
- Variablen:
  - `$$world_name` – Anzeigename
  - `$$world_save_path` – absoluter Speicherordner
  - `$$world_difficulty` – Schwierigkeits-Kennung
  - `$$world_cheats_allowed` – TRUE, wenn Cheats aktiviert sind
  - `$$world_icon_path` – absoluter Symbolpfad
  - `$$world_is_first_join` – TRUE beim allerersten Besuch

## Einzelspielerwelt verlassen (`world_left`)
- Wird ausgelöst, nachdem eine Einzelspielerwelt geschlossen und das Speichern abgeschlossen wurde.
- Variablen:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## Bei anderem Spieler in Welt/Server beigetreten (`other_player_joined_world`)
- Wird ausgelöst, wenn ein anderer Spieler der aktuellen Welt/dem Server beitritt.
- Variablen:
  - `$$player_name` – Name des beitretenden Spielers
  - `$$player_uuid` – UUID

## Bei anderem Spieler aus Welt/Server verlassen (`other_player_left_world`)
- Wird ausgelöst, wenn ein anderer Spieler die aktuelle Welt/den Server verlässt.
- Variablen:
  - `$$player_name`
  - `$$player_uuid`

## Bei anderem Spieler gestorben (`other_player_died`)
- Wird ausgelöst, wenn ein anderer Spieler in der aktuellen Welt stirbt.
- Variablen:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## Bei aufgenommenem Gegenstand (`item_picked_up`)
- Wird ausgelöst, wenn der Spieler eine Gegenstands-Entität aufnimmt.
- Variablen:
  - `$$item_key` – Ressourcenort des aufgenommenen Gegenstands

## Bei gedropptem Gegenstand (`item_dropped`)
- Wird ausgelöst, wenn der Spieler einen Gegenstand aus seinem Inventar fallen lässt.
- Variablen:
  - `$$item_key` – Ressourcenort des gedroppten Gegenstands

## Bei verbrauchtem Gegenstand (`item_consumed`)
- Wird ausgelöst, wenn der Spieler das Verbrauchen eines Gegenstands abschließt.
- Variablen:
  - `$$item_key` – verbrauchter Gegenstand

## Bei überfahrenem Gegenstand im Inventar (`item_hovered_in_inventory`)
- Wird ausgelöst, wenn der Benutzer in einem beliebigen Inventarbildschirm über einen Gegenstand fährt.
- Variablen:
  - `$$item_key` – Ressourcenort des überfahrenen Gegenstands
  - `$$item_display_name_string` – Anzeigename des Gegenstands als Klartext
  - `$$item_display_name_json` – Anzeigename des Gegenstands als JSON-Komponente

## Bei verwendetem Gegenstand (`item_used`)
- Wird ausgelöst, wenn der Spieler einen Gegenstand verwendet.
- Variablen:
  - `$$item_key` – verwendeter Gegenstand
  - `$$used_on_type` – Block/Entität/Selbst/keiner
  - `$$used_on_entity_key` – Ziel-Entitätstyp oder leer
  - `$$used_on_block_key` – Zielblock oder leer
  - `$$target_pos_x` – Ziel-X oder -1
  - `$$target_pos_y` – Ziel-Y oder -1
  - `$$target_pos_z` – Ziel-Z oder -1

## Bei zerbrochenem Gegenstand (`item_broke`)
- Wird ausgelöst, wenn ein Gegenstand im Inventar des Spielers zerbricht.
- Variablen:
  - `$$item_key` – zerbrochener Gegenstand
  - `$$item_type` – Werkzeug/Rüstung/anderes
