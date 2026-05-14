---
title: Listener
description: Wie man Listener in FancyMenu erstellt und verwendet.
---

# Listener

Ab FancyMenu v3.8.0 gibt es eine neue Funktion namens "Listener".

Listener führen Aktionsskripte aus, wenn bestimmte Client- oder Gameplay-Ereignisse auftreten.
Sie können Variablen für Aktionen, Platzhalter und Anforderungen bereitstellen, die im Listener verschachtelt sind.

Anders als die meisten Dinge in FancyMenu sind Listener nicht an einen Screen oder ein Overlay gebunden. Sie laufen ständig im Hintergrund und lauschen auf ihre Ereignisse. Sobald ein Listener ausgelöst wird, führt er sein Aktionsskript aus, auch wenn zu diesem Zeitpunkt kein Screen geöffnet ist.

# Listener verwenden

Um einen neuen Listener zu erstellen, der auf ein Ereignis lauscht und ein Aktionsskript ausführt, klicke im **Hauptmenü -> Anpassung -> Listener verwalten**, während du **NICHT** im Layout-Editor bist. Dort findest du eine einfach zu bedienende Oberfläche zum Erstellen und Verwalten von Listenern.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Listener verwalten" style="max-width:800px;width:100%;height:auto;">

# Listener-Variablen

Listener stellen für ihre verschachtelten Aktionen, Anforderungen und Platzhalter oft einen speziellen Variablentyp bereit.
Auf diese Variablen kann wie auf Platzhalter zugegriffen werden (sie sind effektiv Platzhalter).

Du verwendest diese Variablen, indem du einfach ihren Namen mit dem Präfix `$$` in Texteingaben nutzt, ähnlich wie bei einem normalen Platzhalter.

Wenn du zum Beispiel den Listener **Bei Tastendruck** verwendest und den Tastennamen über die Aktion **In Protokoll schreiben** ausgeben möchtest, könntest du als Eingabe für die Nachricht der Aktion etwas wie `Tastendruck! Die Taste ist: $$key_name` verwenden. Der Variablen-Platzhalter wird später durch den tatsächlichen Namen der Taste ersetzt.

> Auch wenn diese als "Variablen" bezeichnet werden, haben sie nichts mit FancyMenus normalem [Variablensystem](/variables) zu tun. Du kannst diese Variablen nicht setzen, da sie **nur lesbar** sind. Du kannst außerdem keine Aktionen, Anforderungen und Platzhalter aus FancyMenus Variablensystem mit diesen speziellen Listener-Variablen verwenden, daher funktionieren **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** oder **Set Variable Value [FM Variable]** nicht für Listener-Variablen.
{.is-warning}

# Listener im Detail

Diese Liste sollte die meisten, wenn nicht sogar alle Listener von FancyMenu enthalten. Es ist möglich, dass die Liste aufgrund von Mod-Updates nicht immer auf dem neuesten Stand ist.

## Auf Markdown-Text geklickt
- Wird ausgelöst, wenn auf Markdown-Text mit einem `click:`-Ereignis geklickt wird, zum Beispiel `[Öffnen](click:open_menu)`.
- Variablen:
  - `$$text_event_id` – Ereignis-ID aus dem Markdown-Link

## Auf Markdown-Text gehovert
- Wird ausgelöst, wenn über Markdown-Text mit einem `hover:`-Ereignis gehovert wird, zum Beispiel `[Hinweis](hover:show_hint)`.
- Variablen:
  - `$$text_event_id` – Ereignis-ID aus dem Markdown-Link

## Auf ZIP per Aktion entpackt
- Wird ausgelöst, wenn die Aktion **ZIP-Datei im Spielverzeichnis entpacken** abgeschlossen ist.
- Variablen:
  - `$$source_zip_path` – aufgelöster Quellpfad der ZIP-Datei
  - `$$target_folder_path` – aufgelöster Entpackzielpfad
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – Fehlertext, wenn das Entpacken fehlgeschlagen ist

## Bei erzeugtem Element
- Wird ausgelöst, wenn ein Element über einen Aktions-/Skript-Element-Erstellungsablauf erzeugt wird.
- Variablen:
  - `$$element_type` – erzeugter Elementtyp
  - `$$element_identifier` – Bezeichner des erzeugten Elements
  - `$$target_screen` – Ziel-Screen-Bezeichner

## Bei gestarteter Animationstextur
- Wird ausgelöst, wenn eine animierte Textur zu spielen beginnt.
- Variablen:
  - `$$texture_source` – Texturquelle
  - `$$texture_source_type` – Quellentyp
  - `$$texture_will_restart` – true/false

## Bei beendeter Animationstextur
- Wird ausgelöst, wenn eine animierte Textur fertig abgespielt wurde.
- Variablen:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## Bei geändertem Videowiedergabestatus
- Wird ausgelöst, wenn ein Video-Element oder Video-Menühintergrund den Wiedergabestatus ändert.
- Variablen:
  - `$$video_source` – Videoquelle
  - `$$video_source_type` – Quellentyp
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` oder `FINISHED`

## Bei im Chat empfangener Systemnachricht
- Wird ausgelöst, wenn der Client eine System-Chatnachricht empfängt, etwa Feedback zu einem Befehl.
- Variablen:
  - `$$system_message_string` – Nachricht als Klartext
  - `$$system_message_component` – JSON-Komponente

## Bei empfangenen FM-Daten
- Wird ausgelöst, wenn ein Server diesem Client über `/fmdata send` FM-Daten sendet.
- Variablen:
  - `$$data_identifier` – Datenbezeichner-String
  - `$$data` – Daten-Payload
  - `$$sent_by` – Server-IP oder `integrated_server`

## Bei verbundenem Remote-Server
- Wird ausgelöst, wenn FancyMenu eine Verbindung zu einem Remote-Server initialisiert.
- Variablen:
  - `$$request_id` – zwischengespeicherte Anfrage-ID
  - `$$remote_server_url` – URL des Remote-Servers

## Bei empfangenen Remote-Server-Daten
- Wird ausgelöst, wenn Textdaten von einem verbundenen Remote-Server empfangen werden.
- Variablen:
  - `$$request_id` – Anfrage-ID
  - `$$remote_server_url` – URL des Remote-Servers
  - `$$data` – empfangene Daten

## Bei geschlossener Remote-Server-Verbindung
- Wird ausgelöst, wenn eine Verbindung zu einem Remote-Server geschlossen wird.
- Variablen:
  - `$$request_id` – Anfrage-ID
  - `$$remote_server_url` – URL des Remote-Servers
  - `$$intentionally_closed` – TRUE, wenn durch eine Aktion geschlossen
  - `$$crashed` – TRUE, wenn die Verbindung unerwartet abgestürzt ist
  - `$$unknown_close_reason` – TRUE, wenn kein bekannter Schließungsgrund verfügbar war

## Bei Tastendruck
- Wird ausgelöst, sobald eine Taste gedrückt wird (wiederholt sich, solange sie gehalten wird; funktioniert in Screens und im Spiel).
- Variablen:
  - `$$key_name` – Anzeigename der Taste
  - `$$key_keycode` – GLFW-Keycode
  - `$$key_scancode` – GLFW-Scancode
  - `$$key_modifiers` – aktive Modifikator-Bitmaske

## Bei Loslassen einer Taste
- Wird ausgelöst, wenn eine Taste losgelassen wird (Screens und im Spiel).
- Variablen:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## Bei eingegebenem Tastaturzeichen im Screen
- Wird ausgelöst, wenn ein Zeichen eingegeben wird, während ein Screen geöffnet ist.
- Variablen:
  - `$$char` – eingegebenes Zeichen

## Bei Mausbewegung im Screen
- Wird ausgelöst, wenn sich die Maus bewegt, während ein Screen geöffnet ist.
- Variablen:
  - `$$mouse_pos_x` – aktuelles X
  - `$$mouse_pos_y` – aktuelles Y
  - `$$mouse_move_delta_x` – X-Delta seit dem letzten Ereignis
  - `$$mouse_move_delta_y` – Y-Delta seit dem letzten Ereignis

## Bei Mausklick
- Wird ausgelöst, wenn eine Maustaste gedrückt wird (Screens und im Spiel).
- Variablen:
  - `$$button` – links/rechts/Mitte
  - `$$mouse_pos_x` – aktuelles X
  - `$$mouse_pos_y` – aktuelles Y

## Bei Loslassen einer Maustaste
- Wird ausgelöst, wenn eine Maustaste losgelassen wird (Screens und im Spiel).
- Variablen:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## Bei Mausradbewegung im Screen
- Wird ausgelöst, wenn das Mausrad bewegt wird, während ein Screen geöffnet ist.
- Variablen:
  - `$$scroll_delta_y` – vertikale Scroll-Menge

## Bei geöffnetem Screen
- Wird direkt nach dem Aktivieren eines beliebigen Screens ausgeführt; kann verwendet werden, um ihn zu überschreiben.
- Variablen:
  - `$$screen_identifier` – Bezeichner des geöffneten Screens

## Bei geschlossenem Screen
- Wird unmittelbar nach dem Schließen eines Screens ausgeführt.
- Variablen:
  - `$$screen_identifier` – Bezeichner des geschlossenen Screens

## Bei Minecraft beenden
- Wird einmal ausgelöst, wenn der Client mit dem Herunterfahren beginnt.
- Variablen:
  - `$$timestamp_millis` – Epoch-Millis beim Beenden
  - `$$timestamp_iso` – ISO-8601-Zeitstempel des Beendungszeitpunkts

## Bei Tod
- Wird ausgelöst, wenn der Standard-Todesbildschirm für den lokalen Spieler geöffnet wird.
- Variablen:
  - `$$days_survived` – Tage seit dem letzten Tod
  - `$$death_reason_string` – Ursache als Klartext
  - `$$death_reason_component` – Ursache als JSON-Komponente
  - `$$death_pos_x` – Todes-X-Koordinate
  - `$$death_pos_y` – Todes-Y-Koordinate
  - `$$death_pos_z` – Todes-Z-Koordinate

## Bei aktualisierter Variable [FM Variable]
- Wird ausgelöst, wenn eine FancyMenu-Variable gesetzt/aktualisiert wird.
- Variablen:
  - `$$var_name` – Variablenname
  - `$$old_value` – vorheriger Wert
  - `$$new_value` – neuer Wert

## Bei per Aktion heruntergeladener Datei
- Wird ausgelöst, nachdem die Aktion „Datei in Spielverzeichnis herunterladen“ abgeschlossen ist.
- Variablen:
  - `$$download_url` – Download-Quelle
  - `$$target_file_path` – gespeicherter Dateipfad
  - `$$download_succeeded` – true/false

## Bei ausgewählter Datei
- Wird ausgelöst, nachdem die Aktion „Datei auswählen“ abgeschlossen ist.
- Variablen:
  - `$$selected_file_path` – absoluter ausgewählter Dateipfad oder leer, wenn abgebrochen
  - `$$target_file_path` – aufgelöster Pfad innerhalb der Instanz
  - `$$selection_succeeded` – true, wenn das Kopieren erfolgreich war
  - `$$selection_cancelled` – true, wenn der Dialog geschlossen wurde
  - `$$failure_reason` – Fehlerinformationen bei Fehlern

## Bei empfangener Chatnachricht
- Wird ausgelöst, wenn eine normale Spieler-Chatnachricht auf dem Client erscheint.
- Variablen:
  - `$$chat_message_string` – Textzeile als Klartext
  - `$$chat_message_component` – vollständige JSON-Komponente
  - `$$sender_uuid` – UUID des Absenders oder ERROR
  - `$$sender_name` – Name des Absenders oder ERROR

## Bei gesendeter Chatnachricht
- Wird ausgelöst, wenn der lokale Spieler eine Chatnachricht sendet.
- Variablen:
  - `$$chat_message_string` – Textzeile als Klartext
  - `$$chat_message_component` – vollständige JSON-Komponente

## Bei erhaltenem Effekt
- Wird ausgelöst, wenn der Spieler einen Status-Effekt erhält.
- Variablen:
  - `$$effect_key` – Ressourcenort des Effekts
  - `$$effect_type` – positiv/negativ/neutral
  - `$$effect_duration` – verbleibende Ticks

## Bei verlorenem Effekt
- Wird ausgelöst, wenn der Spieler einen Status-Effekt verliert.
- Variablen:
  - `$$effect_key` – abgelaufener Effekt
  - `$$effect_type` – Kategorie

## Bei geänderter Erfahrung
- Wird ausgelöst, wenn sich die gesamte XP des Spielers ändert.
- Variablen:
  - `$$new_experience_amount` – nach der Änderung
  - `$$old_experience_amount` – vor der Änderung
  - `$$is_level_up` – TRUE, wenn das Level gestiegen ist

## Bei erlittenem Schaden
- Wird einmal pro Treffer ausgelöst, wenn der Spieler Schaden erhält.
- Variablen:
  - `$$damage_amount` – entfernte Gesundheit
  - `$$damage_type` – Ressourcenort des Schadentyps
  - `$$is_fatal_damage` – TRUE, wenn tödlich
  - `$$damage_source` – Ressourcenort des Angreifers oder NONE

## Bei beginnendem Einfrieren
- Wird ausgelöst, wenn der Spieler zu frieren beginnt.
- Variablen:
  - `$$freezing_intensity` – 0.0 = kein Einfrieren, 1.0 = vollständig eingefroren

## Bei gestopptem Einfrieren
- Wird ausgelöst, wenn der Spieler nicht mehr friert.
- Variablen:
  - (keine)

## Bei vollständig eingefroren
- Wird einmal ausgelöst, wenn der Spieler vollständig eingefroren ist.
- Variablen:
  - (keine)

## Bei Beginn des Blicks auf einen Block
- Wird einmal ausgelöst, wenn das Fadenkreuz erstmals auf einen Block zeigt (maximale Entfernung 20 Blöcke).
- Variablen:
  - `$$block_key` – anvisierter Block
  - `$$block_pos_x` – Block-X
  - `$$block_pos_y` – Block-Y
  - `$$block_pos_z` – Block-Z
  - `$$distance_to_player` – von den Augen bis zur Trefferposition

## Bei Ende des Blicks auf einen Block
- Wird ausgelöst, wenn das Fadenkreuz nicht mehr auf einen Block zeigt (meldet den zuletzt anvisierten Block, max. 20 Blöcke).
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## Bei Beginn des Blicks auf ein Entity
- Wird einmal ausgelöst, wenn das Fadenkreuz erstmals auf ein Entity zeigt (max. 20 Blöcke).
- Variablen:
  - `$$entity_key` – Typ des anvisierten Entities
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei Ende des Blicks auf ein Entity
- Wird ausgelöst, wenn das Fadenkreuz nicht mehr auf ein Entity zeigt (meldet das zuletzt anvisierte Entity, max. 20 Blöcke).
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei gespawntem Entity
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, wenn irgendwo in der verbundenen Welt/dem Server ein Entity spawnt.
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player` – −1 bei anderer Dimension
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## Bei gestorbenem Entity
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, wenn irgendwo in der verbundenen Welt/dem Server ein Entity stirbt.
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

## Bei erstmals sichtbarem Entity
- Wird ausgelöst, wenn ein Entity innerhalb von 200 Blöcken erstmals sichtbar wird.
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei nicht mehr sichtbarem Entity
- Wird ausgelöst, wenn ein zuvor sichtbares Entity aus dem Sichtfeld verschwindet oder sich weiter als 200 Blöcke entfernt.
- Variablen:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei Interaktion mit Entity
- Wird ausgelöst, wenn der Spieler erfolgreich mit einem Entity interagiert.
- Variablen:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei bestiegenem Entity
- Wird ausgelöst, wenn der Spieler beginnt, ein Entity zu reiten.
- Variablen:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei abgestiegenem Entity
- Wird ausgelöst, wenn der Spieler aufhört, sein aktuelles Entity zu reiten.
- Variablen:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Bei zerbrochenem Block
- Wird ausgelöst, wenn der Spieler einen Block abbaut.
- Variablen:
  - `$$block_key`
  - `$$broke_with_item_key` – verwendetes Werkzeug oder EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Bei platziertem Block
- Wird ausgelöst, wenn der Spieler einen Block platziert.
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Bei Interaktion mit Block
- Wird ausgelöst, wenn der Spieler erfolgreich mit einem Block interagiert.
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Beim Betreten eines Blocks
- Wird ausgelöst, wenn der Spieler einen Block betritt.
- Variablen:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Bei Betreten eines Bioms
- Wird ausgelöst, wenn der Spieler ein neues Biom betritt.
- Variablen:
  - `$$biome_key` – betretenes Biom

## Bei Verlassen eines Bioms
- Wird ausgelöst, wenn der Spieler sein aktuelles Biom verlässt.
- Variablen:
  - `$$biome_key` – gerade verlassenes Biom

## Bei Betreten einer Struktur
- **Erfordert FancyMenu auf dem Server.** Grobe Erkennung des Strukturbereichs; kann in der Nähe, oberhalb oder unterhalb der Struktur auslösen.
- Variablen:
  - `$$structure_key` – betretene Struktur

## Bei Verlassen einer Struktur
- **Erfordert FancyMenu auf dem Server.** Grobe Erkennung; kann am Rand des Struktur-Footprints auslösen.
- Variablen:
  - `$$structure_key` – gerade verlassene Struktur

## Bei Betreten einer Struktur (hohe Genauigkeit)
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, wenn der Spieler die Bounding-Boxen einer Struktur betritt.
- Variablen:
  - `$$structure_key`

## Bei Verlassen einer Struktur (hohe Genauigkeit)
- **Erfordert FancyMenu auf dem Server.** Wird ausgelöst, nachdem der Spieler die Bounding-Boxen einer Struktur verlässt.
- Variablen:
  - `$$structure_key`

## Bei betretenem Dimension
- Wird ausgelöst, wenn der Spieler eine neue Dimension betritt.
- Variablen:
  - `$$dimension_key` – betretene Dimension

## Bei begonnenem Schwimmen
- Wird ausgelöst, wenn der Spieler zu schwimmen beginnt.
- Variablen:
  - `$$fluid_type` – Ressourcenort der Flüssigkeit

## Bei gestopptem Schwimmen
- Wird ausgelöst, wenn der Spieler aufhört zu schwimmen.
- Variablen:
  - `$$fluid_type` – Flüssigkeit, in der das Schwimmen beendet wurde

## Bei Beginn des Kontakts mit Flüssigkeit
- Wird ausgelöst, wenn der Spieler beginnt, eine Flüssigkeit zu berühren.
- Variablen:
  - `$$fluid_type` – berührte Flüssigkeit

## Bei Ende des Kontakts mit Flüssigkeit
- Wird ausgelöst, wenn der Spieler keine Flüssigkeit mehr berührt.
- Variablen:
  - `$$fluid_type` – nicht mehr berührte Flüssigkeit

## Bei gestarteter Musikspur
- Wird ausgelöst, wenn eine neue Musikspur beginnt.
- Variablen:
  - `$$track_resource_location` – Audiodatei
  - `$$track_display_name` – menschenlesbarer Name oder UNKNOWN
  - `$$track_artist` – Künstler oder UNKNOWN
  - `$$track_duration_ms` – Millisekunden (0, wenn unbekannt)

## Bei gestoppter Musikspur
- Wird ausgelöst, wenn die aktuelle Musikspur endet oder ersetzt wird.
- Variablen:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## Bei ausgelöstem Weltsound
- Wird ausgelöst, wenn ein positionsabhängiger Weltsound in der Nähe des Spielers beginnt.
- Variablen:
  - `$$sound_resource_location` – Sounddatei
  - `$$sound_display_name` – Untertitelname, falls verfügbar
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – Grad 0–360 relativ zur Blickrichtung

## Bei Wetteränderung
- Wird ausgelöst, wenn sich das Wetter global oder lokal ändert (ein Biomswechsel oder das Betreten eines Innenraums kann es erneut auslösen).
- Variablen:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE, wenn Schnee gerendert wird
  - `$$weather_can_rain` – TRUE, wenn Regen gerendert wird

## Bei begonnenem Brennen
- Wird ausgelöst, wenn der Spieler zu brennen beginnt.
- Variablen:
  - (keine)

## Bei gestopptem Brennen
- Wird ausgelöst, wenn der Spieler nicht mehr brennt.
- Variablen:
  - (keine)

## Bei begonnenem Ertrinken
- Wird ausgelöst, wenn der Spieler beginnt, Ertrinkungsschaden zu erleiden.
- Variablen:
  - (keine)

## Bei Positionsänderung
- Wird ausgelöst, wenn sich die Blockposition des Spielers ändert.
- Variablen:
  - `$$old_pos_x` – vorheriges Block-X
  - `$$old_pos_y` – vorheriges Block-Y
  - `$$old_pos_z` – vorheriges Block-Z
  - `$$new_pos_x` – neues Block-X
  - `$$new_pos_y` – neues Block-Y
  - `$$new_pos_z` – neues Block-Z

## Bei begonnener Laufbewegung
- Wird ausgelöst, wenn der Spieler zu sprinten beginnt.
- Variablen:
  - (keine)

## Bei gestoppter Laufbewegung
- Wird ausgelöst, wenn der Spieler aufhört zu sprinten.
- Variablen:
  - (keine)

## Bei Sprung
- Wird ausgelöst, wenn der Spieler springt.
- Variablen:
  - (keine)

## Bei Server beigetreten
- Wird ausgelöst, nachdem erfolgreich einem Multiplayer-Server beigetreten wurde.
- Variablen:
  - `$$server_ip` – beigetretene Serveradresse

## Bei Server verlassen
- Wird ausgelöst, nachdem die Verbindung zu einem Multiplayer-Server getrennt wurde.
- Variablen:
  - `$$server_ip` – verlassene Serveradresse

## Einzelspielerwelt betreten
- Wird ausgelöst, nachdem eine Einzelspielerwelt fertig geladen wurde und die Steuerung zurückgegeben wird.
- Variablen:
  - `$$world_name` – Anzeigename
  - `$$world_save_path` – absoluter Speicherordner
  - `$$world_difficulty` – Schwierigkeitsgrad-Schlüssel
  - `$$world_cheats_allowed` – TRUE, wenn Cheats aktiviert sind
  - `$$world_icon_path` – absoluter Symbolpfad
  - `$$world_is_first_join` – TRUE beim allerersten Besuch

## Einzelspielerwelt verlassen
- Wird ausgelöst, nachdem eine Einzelspielerwelt geschlossen wurde und das Speichern abgeschlossen ist.
- Variablen:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## Bei anderem Spieler, der Welt/Server beigetreten ist
- Wird ausgelöst, wenn ein anderer Spieler der aktuellen Welt/dem Server beitritt.
- Variablen:
  - `$$player_name` – Name des beitretenden Spielers
  - `$$player_uuid` – UUID

## Bei anderem Spieler, der Welt/Server verlassen hat
- Wird ausgelöst, wenn ein anderer Spieler die aktuelle Welt/den Server verlässt.
- Variablen:
  - `$$player_name`
  - `$$player_uuid`

## Bei anderem Spieler, der gestorben ist
- Wird ausgelöst, wenn ein anderer Spieler in der aktuellen Welt stirbt.
- Variablen:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## Bei aufgenommenem Gegenstand
- Wird ausgelöst, wenn der Spieler eine Gegenstands-Entität aufnimmt.
- Variablen:
  - `$$item_key` – Ressourcenort des aufgenommenen Gegenstands

## Bei fallen gelassenem Gegenstand
- Wird ausgelöst, wenn der Spieler einen Gegenstand aus seinem Inventar fallen lässt.
- Variablen:
  - `$$item_key` – Ressourcenort des fallengelassenen Gegenstands

## Bei verbrauchtem Gegenstand
- Wird ausgelöst, wenn der Spieler das Verbrauchen eines Gegenstands abschließt.
- Variablen:
  - `$$item_key` – verbrauchter Gegenstand

## Bei überfahrenem Gegenstand im Inventar
- Wird ausgelöst, wenn der Benutzer in einem beliebigen Inventar-Screen über einen Gegenstand fährt.
- Variablen:
  - `$$item_key` – Ressourcenort des überfahrenen Gegenstands
  - `$$item_display_name_string` – Anzeigename des Gegenstands als Klartext
  - `$$item_display_name_json` – Anzeigename des Gegenstands als JSON-Komponente

## Bei verwendetem Gegenstand
- Wird ausgelöst, wenn der Spieler einen Gegenstand verwendet.
- Variablen:
  - `$$item_key` – verwendeter Gegenstand
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – Ziel-Entity-Typ oder leer
  - `$$used_on_block_key` – Zielblock oder leer
  - `$$target_pos_x` – Ziel-X oder -1
  - `$$target_pos_y` – Ziel-Y oder -1
  - `$$target_pos_z` – Ziel-Z oder -1

## Bei zerbrochenem Gegenstand
- Wird ausgelöst, wenn ein Gegenstand im Inventar des Spielers zerbricht.
- Variablen:
  - `$$item_key` – zerbrochener Gegenstand
  - `$$item_type` – tool/armor/other
