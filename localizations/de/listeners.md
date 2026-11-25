---
title: Listener
description: >-
  Führe Aktionsskripte aus, wenn im Spiel etwas passiert, etwa ein Tastendruck,
  eine Chatnachricht oder ein neuer Erfolg.
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# Listener

Listener führen ein [Aktionsskript](/action-scripts) aus, wenn im Spiel etwas passiert: eine Taste wird gedrückt, ein Bildschirm wird geöffnet, du schaltest einen Erfolg frei und vieles mehr. Sie funktionieren in jedem Menü und während des Spielens und gehören zu keinem Layout.

Die meisten Listener geben ihrem Skript außerdem Variablen darüber, was passiert ist, zum Beispiel den Namen der gedrückten Taste.

<img width="800" alt="Auf dem Titelbildschirm werden Tasten gedrückt und ein Toast zeigt den Namen jeder gedrückten Taste an" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> Ein Listener kann Datei-, Netzwerk-, Befehls-, Zwischenablage-, Ressourcenpaket- und Link-Aktionen ausführen, während kein Menü geöffnet ist. Verwende nur Listener aus Profilen und Dateien von Personen, denen du vertraust.

# Listener hinzufügen

<img width="800" alt="Manage Listeners öffnen, einen Listener On Keyboard Key Pressed mit der Aktion Show Toast hinzufügen und H drücken, um ihn auszuprobieren" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. Öffne **Menüleiste -> Anpassung -> Listener verwalten**.
2. Klicke auf **Listener hinzufügen**.
3. Klicke unter **Verfügbare Listener** auf das Ereignis. Über die Suchleiste kannst du Listener anhand ihres Namens und ihrer Beschreibung finden.
   - **Listener-Beschreibung** zeigt, was der Listener macht und welche Variablen er bereitstellt.
   - **Variablen in Zwischenablage kopieren** kopiert die Namen seiner Variablen.
   - **Beschreibung ausklappen** öffnet die Beschreibung in einem eigenen Fenster.
4. Klicke auf **Fertig** oder doppelklicke auf den Listener. Der Aktionsskript-Editor wird geöffnet.
5. Füge die auszuführenden Aktionen hinzu und klicke auf **Fertig**. Siehe [Aktionsskripte](/action-scripts#making-an-action-script).
6. Klicke unter **Listener verwalten** auf **Fertig**, um zu speichern. Der Listener ist sofort einsatzbereit.

Mit **Abbrechen** werden nach einer Rückfrage alle Änderungen verworfen, die du unter **Listener verwalten** vorgenommen hast.

# Listener verwalten

<img width="800" alt="Das Fenster Manage Listeners mit fünf Listenern, von denen einer ausgewählt ist und dessen Aktionsskript rechts angezeigt wird" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- Klicke auf einen Listener, um rechts seinen Typ und sein Aktionsskript zu sehen.
- **Aktionen bearbeiten** oder ein Rechtsklick auf einen Listener öffnet sein Aktionsskript.
- Doppelklicke auf den Namen eines Listeners, um ihn umzubenennen, zum Beispiel in `Hilfetaste`. Mit `Enter` speicherst du den Namen, mit `Esc` brichst du ab. Bei einem leeren Namen wird wieder der Listener-Typ angezeigt.
- **Listener entfernen** löscht den ausgewählten Listener.
- **Für KI exportieren** kopiert den ausgewählten Listener oder alle Listener für einen [KI-Chat](/export-for-ai), einschließlich deiner ungespeicherten Änderungen.

Listener werden in `config/fancymenu/listener_instances.txt` gespeichert (siehe [Speicherorte der Daten](/data-storage-locations)). Jedes [Profil](/profiles) hat eigene Listener.

# Listener-Variablen

Die Variablen eines Listeners beginnen mit `$$` und funktionieren überall in seinem Skript: in jedem Aktionswert und in den Bedingungen von [IF-Anweisungen](/action-scripts#if-else-if-and-else). Groß- und Kleinschreibung sind wichtig. Die Variablen jedes Listeners sind unten aufgeführt und auch in seiner Beschreibung bei der Listener-Auswahl.

<img width="800" alt="Die Listener-Auswahl mit On Achievement Unlocked ausgewählt und einer Beschreibung, in der die Variablen aufgeführt sind" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

Zum Beispiel öffnet dieser Listener einen Hilfebildschirm, wenn `H` gedrückt wird:

1. Füge einen Listener **On Keyboard Key Pressed** hinzu.
2. Verwende in seinem Skript **IF-Anweisung hinzufügen** mit der Bedingung [**Is Text**](/conditions#is-text). Setze **Vergleichsmodus** auf **Equals**, **Text** auf `$$key_name` und **Vergleichstext** auf `H`.
3. Füge innerhalb der IF-Anweisung [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui) mit deinem Hilfebildschirm hinzu.

Weitere Informationen zu Listener-Variablen:

- Listener-Variablen sind immer Text. Wenn ein Listener einen Wert nicht ermitteln kann, erhält die Variable einen Ersatzwert wie `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` oder nichts.
- Listener-Variablen werden vor [Platzhaltern](/placeholders) eingesetzt und funktionieren daher auch innerhalb von Platzhaltern.
- Listener-Variablen gibt es nur, solange ihr Skript ausgeführt wird. Um einen Wert zu behalten, speichere ihn mit [**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable) in einer deiner [Variablen](/variables).
- Eigene Variablen aus **Menüleiste -> Anpassung -> Variablen verwalten** funktionieren ebenfalls in Listener-Skripten: Verwende `$$` gefolgt vom Namen, zum Beispiel `$$coins`. Wenn eine eigene Variable denselben Namen wie eine Listener-Variable hat, steht `$$name` für die Listener-Variable. Eigene Variablen mit längeren Namen, zum Beispiel `key_name_log`, funktionieren weiterhin.
- Text aus Chats, von Servern, aus Dateien und von anderen Spielern kann beliebigen Inhalt haben. Füge ihn niemals direkt in Befehle, Dateipfade oder Links ein.

# Gut zu wissen

- Einige Listener benötigen FancyMenu auf dem Server. Das ist unten angegeben. Im Einzelspielermodus funktionieren sie immer.
- Einige Listener werden sehr häufig ausgeführt, etwa **On Mouse Moved in Screen**, **On Element Scrolled**, **On Position Changed** und **On World Sound Triggered**. Halte ihre Skripte kurz und verwende darin niemals langsame Aktionen wie [**Reload FancyMenu**](/action-scripts#reload-fancymenu).
- Wenn du mit **On Screen Opened** einen Bildschirm ersetzen möchtest, prüfe zuerst `$$screen_identifier` mit einer IF-Anweisung. Andernfalls wird jeder Bildschirm ersetzt, auch der, den du selbst öffnest.

# Alle Listener

Alle Listener von FancyMenu, sortiert nach dem Ereignis, auf das sie reagieren.

## Tastatur und Maus

Um herauszufinden, welche Taste gedrückt wurde, verwende `$$key_name`. Die Tastencodes sind nicht in allen Minecraft-Versionen gleich.

### On Keyboard Key Pressed

**Kennung:** `keyboard_key_pressed`

Wird ausgeführt, wenn eine Taste gedrückt wird, sowohl in Menüs als auch während des Spielens. Solange eine Taste gedrückt gehalten wird, wird der Listener immer wieder ausgeführt.

- `$$key_name`: der Name der Taste, zum Beispiel `H` oder `Left Shift`
- `$$key_keycode`: der Tastencode
- `$$key_scancode`: der Scancode der Taste
- `$$key_modifiers`: eine Zahl für gleichzeitig gedrückte Zusatztasten wie `Shift` und `Ctrl`

### On Keyboard Key Released

**Kennung:** `keyboard_key_released`

Wird ausgeführt, wenn eine Taste losgelassen wird, sowohl in Menüs als auch während des Spielens.

Stellt dieselben Variablen wie **On Keyboard Key Pressed** bereit: `$$key_name`, `$$key_keycode`, `$$key_scancode` und `$$key_modifiers`.

### On Keyboard Character Typed in Screen

**Kennung:** `keyboard_char_typed`

Wird für jedes Zeichen ausgeführt, das bei geöffnetem Bildschirm eingegeben wird.

- `$$char`: das eingegebene Zeichen

### On Mouse Moved in Screen

**Kennung:** `mouse_moved`

Wird jedes Mal ausgeführt, wenn sich die Maus bei geöffnetem Bildschirm bewegt.

- `$$mouse_pos_x`, `$$mouse_pos_y`: die Mausposition in GUI-Pixeln
- `$$mouse_move_delta_x`, `$$mouse_move_delta_y`: die seit der letzten Ausführung zurückgelegte Strecke

### On Mouse Button Clicked

**Kennung:** `mouse_button_clicked`

Wird einmal ausgeführt, wenn eine Maustaste gedrückt wird, sowohl in Menüs als auch während des Spielens.

- `$$button`: `left`, `right` oder `middle`. Für andere Tasten wird ihre Nummer angegeben.
- `$$mouse_pos_x`, `$$mouse_pos_y`: die Mausposition in GUI-Pixeln

### On Mouse Button Released

**Kennung:** `mouse_button_released`

Wird einmal ausgeführt, wenn eine Maustaste losgelassen wird, sowohl in Menüs als auch während des Spielens.

Stellt dieselben Variablen wie **On Mouse Button Clicked** bereit: `$$button`, `$$mouse_pos_x` und `$$mouse_pos_y`.

### On Mouse Scrolled in Screen

**Kennung:** `mouse_scrolled`

Wird ausgeführt, wenn bei geöffnetem Bildschirm das Mausrad bewegt wird.

- `$$scroll_delta_y`: wie weit das Mausrad bewegt wurde. Bei Scrollen nach oben größer als `0`, bei Scrollen nach unten kleiner als `0`.

## Bildschirme und Elemente

### On Screen Opened

**Kennung:** `screen_open`

Wird direkt nach dem Öffnen eines Bildschirms ausgeführt. Eine Aktion [**Open Screen or Custom GUI**](/action-scripts#open-screen-or-custom-gui) in diesem Skript kann den Bildschirm durch einen anderen ersetzen.

- `$$screen_identifier`: die [Kennung](/screen-identifiers) des Bildschirms

### On Screen Closed

**Kennung:** `screen_close`

Wird direkt nach dem Schließen eines Bildschirms ausgeführt.

- `$$screen_identifier`: die [Kennung](/screen-identifiers) des geschlossenen Bildschirms

### On Markdown Text Clicked

**Kennung:** `text_clicked`

Wird ausgeführt, wenn jemand auf ein [Klickereignis](/text-formatting#click-and-hover-events) in einem Text klickt, zum Beispiel auf `[Regeln lesen](click:open_rules)`.

- `$$text_event_id`: die ID des Ereignisses, zum Beispiel `open_rules`

### On Markdown Text Hovered

**Kennung:** `text_hovered`

Wird ausgeführt, wenn die Maus auf ein [Hover-Ereignis](/text-formatting#click-and-hover-events) in einem Text bewegt wird, zum Beispiel auf `[Was ist das?](hover:show_hint)`.

- `$$text_event_id`: die ID des Ereignisses, zum Beispiel `show_hint`

### On Element Scrolled

**Kennung:** `scroll_area_scrolled`

Wird jedes Mal ausgeführt, wenn sich der Inhalt eines [Scrollbereichs](/scrollable-areas) oder eines [Textelements](/text-in-menus) bewegt. Beim fließenden Scrollen geschieht das in jedem Frame. Im Layout-Editor wird der Listener nicht ausgeführt.

- `$$element_identifier`: die [Kennung](/element-identifiers) des Elements
- `$$scroll_x`: wie weit der Inhalt horizontal gescrollt ist, in Pixeln
- `$$scroll_y`: wie weit der Inhalt nach unten gescrollt ist, in Pixeln
- `$$scroll_percent`: wie weit der Inhalt in seiner Hauptrichtung gescrollt ist, von `0` (Anfang) bis `100` (Ende)

### On Element Scrolled to Start

**Kennung:** `scroll_area_reached_start`

Wird ausgeführt, wenn der Inhalt eines Scrollbereichs oder eines Textelements zurück an den Anfang gescrollt wird.

Stellt dieselben Variablen wie **On Element Scrolled** bereit: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` und `$$scroll_percent`.

### On Element Scrolled to End

**Kennung:** `scroll_area_reached_end`

Wird ausgeführt, wenn der Inhalt eines Scrollbereichs oder eines Textelements bis zum Ende gescrollt wird, etwa wenn jemand alle Regeln durchgelesen hat.

Stellt dieselben Variablen wie **On Element Scrolled** bereit: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` und `$$scroll_percent`.

### Animated Texture Started Playing

**Kennung:** `animated_texture_started_playing`

Wird ausgeführt, wenn eine [animierte Textur](/animations) (GIF, APNG oder FMA) abgespielt wird, und jedes Mal, wenn sie von vorn beginnt.

- `$$texture_source`: Quelle der Textur: Dateipfad, Weblink oder Ressourcenpfad
- `$$texture_source_type`: `LOCAL`, `WEB` oder `RESOURCE_LOCATION`
- `$$texture_will_restart`: `true`, wenn sie nach diesem Durchlauf erneut startet, andernfalls `false`

### Animated Texture Finished Playing

**Kennung:** `animated_texture_finished_playing`

Wird ausgeführt, wenn ein Durchlauf einer animierten Textur endet. Bei einer Schleife geschieht das direkt vor dem Neustart.

Stellt dieselben Variablen wie **Animated Texture Started Playing** bereit: `$$texture_source`, `$$texture_source_type` und `$$texture_will_restart`.

### Video Playback Status Changed

**Kennung:** `video_playback_status_changed`

Wird ausgeführt, wenn ein [Video](/video)-Element oder ein Menühintergrund startet, pausiert, angehalten wird oder endet.

- `$$video_source`: Quelle des Videos: Dateipfad, Weblink oder Ressourcenpfad
- `$$video_source_type`: `LOCAL`, `WEB` oder `RESOURCE_LOCATION`
- `$$is_looping`: `true`, wenn das Video in einer Schleife läuft, andernfalls `false`
- `$$new_status`:
  - `PLAYING`: Das Video wurde gestartet oder fortgesetzt.
  - `PAUSED`: Das Video wurde pausiert.
  - `STOPPED`: Das Video wurde angehalten.
  - `FINISHED`: Das Video hat sein Ende erreicht. Bei Videos in einer Schleife wird dies ebenfalls direkt vor dem Neustart gemeldet.

## Variablen, Dateien und Daten

### On Variable Updated [FM Variable]

**Kennung:** `fm_variable_updated`

Wird jedes Mal ausgeführt, wenn eine [Variable](/variables) festgelegt wird.

- `$$var_name`: der Name der Variable
- `$$old_value`: ihr vorheriger Wert
- `$$new_value`: ihr neuer Wert

Bei Listenvariablen sind beide Werte die gesamte Liste als JSON-Array, zum Beispiel `["Diamonds","Emeralds"]`.

### On File Download Started via Action

**Kennung:** `file_download_started_via_action`

Wird ausgeführt, wenn der Download von [**Download File to Game Directory**](/action-scripts#download-file-to-game-directory) beginnt, sobald der Dateiname bekannt ist. Die Datei erscheint erst nach Abschluss des Downloads an ihrem Pfad. Verwende daher **On File Downloaded via Action**, um zu erfahren, wann sie bereit ist.

- `$$download_url`: der Link zur Datei
- `$$target_file_path`: der Speicherort der Datei

### On File Downloaded via Action

**Kennung:** `file_downloaded_via_action`

Wird ausgeführt, wenn der Download von [**Download File to Game Directory**](/action-scripts#download-file-to-game-directory) abgeschlossen ist oder fehlschlägt.

- `$$download_url`: der Link zur Datei
- `$$target_file_path`: der Speicherort der Datei. Bei einem fehlgeschlagenen Download kann hier nur der Ordner angegeben sein.
- `$$download_succeeded`: `true` oder `false`

### On File Selected

**Kennung:** `file_selected_via_action`

Wird ausgeführt, wenn [**Select File from System**](/action-scripts#select-file-from-system) abgeschlossen ist: Die Datei wurde kopiert, der Dateiauswahldialog wurde abgebrochen oder ein Fehler ist aufgetreten.

- `$$selected_file_path`: der vollständige Pfad der ausgewählten Datei. Leer, wenn der Dialog abgebrochen wurde.
- `$$target_file_path`: der Speicherort der kopierten Datei im Spielordner
- `$$selection_succeeded`: `true`, wenn die Datei kopiert wurde
- `$$selection_cancelled`: `true`, wenn der Dialog ohne Dateiauswahl geschlossen wurde
- `$$failure_reason`: die Fehlerursache. Leer, wenn kein Fehler aufgetreten ist.

### On ZIP Extracted via Action

**Kennung:** `zip_extracted_via_action`

Wird ausgeführt, wenn [**Extract ZIP File In Game Directory**](/action-scripts#extract-zip-file-in-game-directory) abgeschlossen ist.

- `$$source_zip_path`: die ZIP-Datei
- `$$target_folder_path`: der Ordner, in den sie entpackt wurde
- `$$extract_succeeded`: `true` oder `false`
- `$$failure_reason`: die Fehlerursache. Leer, wenn kein Fehler aufgetreten ist.

Pfade im Spielordner beginnen mit `/`, zum Beispiel `/config/fancymenu/assets/pack.zip`. Pfade im Ordner `.minecraft` beginnen mit `.minecraft/`.

### On FM Data Received

**Kennung:** `fm_data_received`

Wird ausgeführt, wenn der Server diesem Spieler mit `/fmdata send` Daten sendet. Siehe [FM-Daten](/fm-data).

- `$$data_identifier`: die Kennung, mit der die Daten gesendet wurden
- `$$data`: die Daten
- `$$sent_by`: die IP-Adresse des Servers oder im Einzelspielermodus `integrated_server`

### On Remote Server Connected

**Kennung:** `remote_server_connected`

Wird ausgeführt, wenn eine [Verbindung zu einem Remoteserver](/remote-server-communication) hergestellt wird.

- `$$request_id`: die Anfrage-ID der Verbindung
- `$$remote_server_url`: der Link zum Remoteserver

### On Remote Server Data Received

**Kennung:** `remote_server_data_received`

Wird jedes Mal ausgeführt, wenn ein verbundener Remoteserver Text sendet.

- `$$request_id`: die Anfrage-ID der Verbindung
- `$$remote_server_url`: der Link zum Remoteserver
- `$$data`: der gesendete Text

### On Remote Server Connection Closed

**Kennung:** `remote_server_connection_closed`

Wird ausgeführt, wenn eine Verbindung zu einem Remoteserver geschlossen wird.

- `$$request_id`: die Anfrage-ID der Verbindung
- `$$remote_server_url`: der Link zum Remoteserver
- `$$intentionally_closed`: `true`, wenn sie durch [**Close Remote Server Connection**](/action-scripts#close-remote-server-connection) geschlossen wurde
- `$$crashed`: `true`, wenn die Verbindung abgestürzt ist
- `$$unknown_close_reason`: `true`, wenn sie aus unbekanntem Grund geschlossen wurde

## Spiel, Welten und Server

### On Quit Minecraft

**Kennung:** `quit_minecraft`

Wird einmal ausgeführt, wenn das Spiel heruntergefahren wird.

- `$$timestamp_millis`: die Zeit in Millisekunden seit 1970
- `$$timestamp_iso`: die Zeit als ISO-8601-Text, zum Beispiel `2026-11-24T18:30:00.123Z`

### On Screenshot Taken

**Kennung:** `screenshot_taken`

Wird ausgeführt, wenn ein Screenshot aufgenommen und gespeichert wird, etwa mit der Screenshot-Taste.

- `$$screenshot_path`: der Pfad des Screenshots im Spielordner, zum Beispiel `/screenshots/2026-10-29_14.30.00.png`

### Singleplayer World Entered

**Kennung:** `world_entered`

Wird ausgeführt, wenn das Laden einer Einzelspielerwelt abgeschlossen ist und du dich bewegen kannst.

- `$$world_name`: der Name der Welt
- `$$world_save_path`: der vollständige Pfad des Speicherordners der Welt
- `$$world_difficulty`: der Schwierigkeitsgrad der Welt
- `$$world_cheats_allowed`: `true`, wenn Cheats aktiviert sind
- `$$world_icon_path`: der vollständige Pfad zum Symbol der Welt
- `$$world_is_first_join`: `true` beim allerersten Betreten nach dem Erstellen der Welt

### Singleplayer World Left

**Kennung:** `world_left`

Wird ausgeführt, wenn eine Einzelspielerwelt geschlossen und gespeichert wird.

Stellt dieselben Variablen wie **Singleplayer World Entered** bereit, außer `$$world_is_first_join`: `$$world_name`, `$$world_save_path`, `$$world_difficulty`, `$$world_cheats_allowed` und `$$world_icon_path`.

### On Start Joining Server

**Kennung:** `start_joining_server`

Wird ausgeführt, wenn das Spiel eine Verbindung zu einem Server oder Realm herstellt, bevor der Beitritt abgeschlossen ist. Der Listener wird auch ausgeführt, wenn die Verbindung fehlschlägt oder abgebrochen wird. So kann er sich den Server merken, zum Beispiel für eine Schaltfläche zum erneuten Verbinden auf dem Bildschirm „Verbindung getrennt“.

- `$$server_ip`: die IP-Adresse des Servers

### On Server Joined

**Kennung:** `server_joined`

Wird ausgeführt, nachdem du einem Mehrspielerserver beigetreten bist.

- `$$server_ip`: die IP-Adresse des Servers

### On Server Left

**Kennung:** `server_left`

Wird ausgeführt, nachdem du einen Mehrspielerserver verlassen hast.

- `$$server_ip`: die IP-Adresse des Servers

### On Other Player Joined World/Server

**Kennung:** `other_player_joined_world`

Wird ausgeführt, wenn ein anderer Spieler deiner Welt oder deinem Server beitritt.

- `$$player_name`: der Name des Spielers
- `$$player_uuid`: die UUID des Spielers

### On Other Player Left World/Server

**Kennung:** `other_player_left_world`

Wird ausgeführt, wenn ein anderer Spieler deine Welt oder deinen Server verlässt.

- `$$player_name`: der Name des Spielers
- `$$player_uuid`: die UUID des Spielers

### On Other Player Died

**Kennung:** `other_player_died`

Wird ausgeführt, wenn ein anderer Spieler in deiner Welt stirbt.

- `$$player_name`: der Name des Spielers
- `$$player_uuid`: die UUID des Spielers
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: die Position, an der der Spieler gestorben ist

## Chat

### On Chat Message Received

**Kennung:** `chat_message_received`

Wird ausgeführt, wenn eine Chatnachricht eines Spielers in deinem Chat angezeigt wird.

- `$$chat_message_string`: die Nachricht als einfacher Text
- `$$chat_message_component`: die Nachricht als JSON-Textkomponente
- `$$sender_uuid`: die UUID des Absenders oder `ERROR`, wenn sie unbekannt ist
- `$$sender_name`: der Name des Absenders oder `ERROR`, wenn er unbekannt ist

### On Chat Message Sent

**Kennung:** `chat_message_sent`

Wird ausgeführt, wenn du eine Chatnachricht sendest. Befehle zählen nicht.

- `$$chat_message_string`: die Nachricht als einfacher Text
- `$$chat_message_component`: die Nachricht als JSON-Textkomponente

### On System Message Received in Chat

**Kennung:** `system_message_received_in_chat`

Wird ausgeführt, wenn eine Nachricht angezeigt wird, die nicht von einem Spieler stammt, zum Beispiel die Rückmeldung zu einem Befehl.

- `$$system_message_string`: die Nachricht als einfacher Text
- `$$system_message_component`: die Nachricht als JSON-Textkomponente

## Spieler

### On Death

**Kennung:** `player_death`

Wird direkt nach dem Öffnen des Todesbildschirms ausgeführt.

- `$$days_survived`: die Ingame-Tage seit deinem letzten Tod, abgerundet
- `$$death_reason_string`: die Todesnachricht als einfacher Text
- `$$death_reason_component`: die Todesnachricht als JSON-Textkomponente
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: die Position, an der du gestorben bist

### On Damage Taken

**Kennung:** `damage_taken`

Wird für jeden Treffer, den du erleidest, einmal ausgeführt.

- `$$damage_amount`: wie viel Gesundheit der Treffer abgezogen hat
- `$$damage_type`: die Schadensart, zum Beispiel `minecraft:fall`
- `$$is_fatal_damage`: `true`, wenn der Treffer dich getötet hat
- `$$damage_source`: der Typ der Entität, die den Schaden verursacht hat, zum Beispiel `minecraft:zombie`, oder `NONE`

### On Effect Gained

**Kennung:** `effect_gained`

Wird einmal ausgeführt, wenn du einen Statuseffekt erhältst.

- `$$effect_key`: der Effekt, zum Beispiel `minecraft:speed`
- `$$effect_type`: `positive`, `negative` oder `neutral`
- `$$effect_duration`: die Dauer in Ticks (20 Ticks entsprechen 1 Sekunde)

### On Effect Lost

**Kennung:** `effect_lost`

Wird einmal ausgeführt, wenn ein Statuseffekt endet.

- `$$effect_key`: der Effekt, zum Beispiel `minecraft:speed`
- `$$effect_type`: `positive`, `negative` oder `neutral`

### On Experience Changed

**Kennung:** `experience_changed`

Wird jedes Mal ausgeführt, wenn deine Erfahrungspunkte steigen oder sinken.

- `$$new_experience_amount`: deine aktuelle Gesamtzahl an Erfahrungspunkten
- `$$old_experience_amount`: deine vorherige Gesamtzahl an Erfahrungspunkten
- `$$is_level_up`: `true`, wenn du eine neue Stufe erreicht hast

### On Achievement Unlocked

**Kennung:** `achievement_unlocked`

Wird einmal ausgeführt, wenn du einen Erfolg (Fortschritt) freischaltest. Erfolge, die bereits abgeschlossen waren, zum Beispiel beim Betreten einer Welt, zählen nicht.

- `$$achievement_key`: der Erfolg, zum Beispiel `minecraft:story/mine_diamond`
- `$$achievement_label`: sein Titel in der Spielsprache
- `$$achievement_description`: seine Beschreibung in der Spielsprache
- `$$achievement_icon_item_key`: der Gegenstand des Symbols, zum Beispiel `minecraft:diamond`
- `$$achievement_type`: `advancement`, `goal` oder `challenge`

### On Jump

**Kennung:** `jump`

Wird jedes Mal ausgeführt, wenn du springst. Es gibt keine Variablen.

### On Started Running

**Kennung:** `started_running`

Wird einmal ausgeführt, wenn du zu sprinten beginnst. Es gibt keine Variablen.

### On Stopped Running

**Kennung:** `stopped_running`

Wird einmal ausgeführt, wenn du aufhörst zu sprinten. Es gibt keine Variablen.

### On Position Changed

**Kennung:** `position_changed`

Wird jedes Mal ausgeführt, wenn du dich zu einem anderen Block bewegst.

- `$$old_pos_x`, `$$old_pos_y`, `$$old_pos_z`: die vorherige Blockposition
- `$$new_pos_x`, `$$new_pos_y`, `$$new_pos_z`: die neue Blockposition

### On Started Burning

**Kennung:** `started_burning`

Wird einmal ausgeführt, wenn du anfängst zu brennen. Es gibt keine Variablen.

### On Stopped Burning

**Kennung:** `stopped_burning`

Wird einmal ausgeführt, wenn du nicht mehr brennst. Es gibt keine Variablen.

### On Started Drowning

**Kennung:** `started_drowning`

Wird einmal ausgeführt, wenn du anfängst, Ertrinkungsschaden zu erleiden. Es gibt keine Variablen.

### On Started Freezing

**Kennung:** `started_freezing`

Wird einmal ausgeführt, wenn du anfängst zu frieren, zum Beispiel in Pulverschnee.

- `$$freezing_intensity`: wie stark du gefroren bist, von `0.0` (gar nicht) bis `1.0` (vollständig gefroren)

### On Stopped Freezing

**Kennung:** `stopped_freezing`

Wird einmal ausgeführt, wenn du nicht mehr frierst. Es gibt keine Variablen.

### On Fully Frozen

**Kennung:** `fully_frozen`

Wird einmal ausgeführt, wenn du vollständig gefroren bist. Es gibt keine Variablen.

### On Start Swimming

**Kennung:** `start_swimming`

Wird einmal ausgeführt, wenn du zu schwimmen beginnst.

- `$$fluid_type`: die Flüssigkeit, zum Beispiel `minecraft:water`

### On Stop Swimming

**Kennung:** `stop_swimming`

Wird einmal ausgeführt, wenn du aufhörst zu schwimmen.

- `$$fluid_type`: die Flüssigkeit, zum Beispiel `minecraft:water`

### On Start Touching Fluid

**Kennung:** `start_touching_fluid`

Wird einmal ausgeführt, wenn du eine Flüssigkeit wie Wasser oder Lava berührst.

- `$$fluid_type`: die Flüssigkeit, zum Beispiel `minecraft:lava`

### On Stop Touching Fluid

**Kennung:** `stop_touching_fluid`

Wird einmal ausgeführt, wenn du eine Flüssigkeit nicht mehr berührst.

- `$$fluid_type`: die Flüssigkeit, zum Beispiel `minecraft:lava`

## Gegenstände

### On Item Picked Up

**Kennung:** `item_picked_up`

Wird einmal ausgeführt, wenn du einen Gegenstand aufhebst.

- `$$item_key`: der Gegenstand, zum Beispiel `minecraft:diamond`

### On Item Dropped

**Kennung:** `item_dropped`

Wird einmal ausgeführt, wenn du einen Gegenstand aus deinem Inventar fallen lässt.

- `$$item_key`: der Gegenstand, zum Beispiel `minecraft:diamond`

### On Item Consumed

**Kennung:** `item_consumed`

Wird einmal ausgeführt, wenn du einen Gegenstand vollständig gegessen oder getrunken hast.

- `$$item_key`: der Gegenstand, zum Beispiel `minecraft:golden_apple`

### On Item Used

**Kennung:** `item_used`

Wird einmal ausgeführt, wenn du einen Gegenstand verwendest.

- `$$item_key`: der Gegenstand, zum Beispiel `minecraft:flint_and_steel`
- `$$used_on_type`: worauf er angewendet wurde: `block`, `entity`, `self` oder `none`
- `$$used_on_entity_key`: der Typ der Entität, auf die er angewendet wurde. Leer, wenn keine vorhanden ist.
- `$$used_on_block_key`: der Block, auf den er angewendet wurde. Leer, wenn keiner vorhanden ist.
- `$$target_pos_x`, `$$target_pos_y`, `$$target_pos_z`: die Position, auf die er angewendet wurde, oder `-1`

### On Item Broke

**Kennung:** `item_broke`

Wird einmal ausgeführt, wenn ein Gegenstand in deinem Inventar kaputtgeht.

- `$$item_key`: der Gegenstand, zum Beispiel `minecraft:iron_pickaxe`
- `$$item_type`: `tool`, `armor` oder `other`

### On Item Hovered In Inventory

**Kennung:** `item_hovered_in_inventory`

Wird einmal ausgeführt, wenn die Maus in einem beliebigen Inventar auf einen Gegenstand bewegt wird, zum Beispiel in deinem Inventar oder in einer Truhe.

- `$$item_key`: der Gegenstand, zum Beispiel `minecraft:diamond_sword`
- `$$item_display_name_string`: der Name des Gegenstands als einfacher Text
- `$$item_display_name_json`: der Name des Gegenstands als JSON-Textkomponente

## Blöcke

### On Start Looking At Block

**Kennung:** `start_looking_at_block`

Wird einmal ausgeführt, wenn dein Fadenkreuz auf einen Block zeigt, der höchstens 20 Blöcke entfernt ist.

- `$$block_key`: der Block, zum Beispiel `minecraft:oak_log`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: die Position des Blocks
- `$$distance_to_player`: die Entfernung von deinen Augen zu dem Punkt, auf den das Fadenkreuz zeigt

### On Stop Looking At Block

**Kennung:** `stop_looking_at_block`

Wird einmal ausgeführt, wenn dein Fadenkreuz nicht mehr auf einen Block zeigt.

Stellt dieselben Variablen wie **On Start Looking At Block** für den Block bereit, den du zuvor angesehen hast: `$$block_key`, `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` und `$$distance_to_player`.

### On Block Broke

**Kennung:** `block_broke`

Wird einmal ausgeführt, wenn du einen Block abbaust.

- `$$block_key`: der Block, zum Beispiel `minecraft:stone`
- `$$broke_with_item_key`: der Gegenstand in deiner Hand, zum Beispiel `minecraft:iron_pickaxe`, oder `EMPTY`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: die Position des Blocks

### On Block Placed

**Kennung:** `block_placed`

Wird einmal ausgeführt, wenn du einen Block platzierst.

- `$$block_key`: der Block, zum Beispiel `minecraft:torch`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: die Position des Blocks

### On Interacted With Block

**Kennung:** `interacted_with_block`

Wird einmal ausgeführt, wenn du einen Block verwendest, zum Beispiel eine Truhe öffnest oder einen Knopf drückst.

- `$$block_key`: der Block, zum Beispiel `minecraft:chest`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: die Position des Blocks

### On Stepping On Block

**Kennung:** `stepping_on_block`

Wird einmal ausgeführt, wenn du einen Block betrittst.

- `$$block_key`: der Block, zum Beispiel `minecraft:grass_block`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: die Position des Blocks

## Entitäten

### On Start Looking At Entity

**Kennung:** `start_looking_at_entity`

Wird einmal ausgeführt, wenn dein Fadenkreuz auf eine Entität zeigt, die höchstens 20 Blöcke entfernt ist.

- `$$entity_key`: der Typ der Entität, zum Beispiel `minecraft:villager`
- `$$distance_to_player`: die Entfernung von deinen Augen zu dem Punkt, auf den das Fadenkreuz zeigt
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: die Position der Entität
- `$$entity_uuid`: die UUID der Entität

### On Stop Looking At Entity

**Kennung:** `stop_looking_at_entity`

Wird einmal ausgeführt, wenn dein Fadenkreuz nicht mehr auf eine Entität zeigt.

Stellt dieselben Variablen wie **On Start Looking At Entity** für die Entität bereit, die du zuvor angesehen hast: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` und `$$entity_uuid`.

### On Entity Starts Being In Sight

**Kennung:** `entity_starts_being_in_sight`

Wird einmal ausgeführt, wenn eine Entität auf deinem Bildschirm sichtbar wird, sofern sie höchstens 200 Blöcke entfernt ist.

- `$$entity_key`: der Typ der Entität, zum Beispiel `minecraft:creeper`
- `$$distance_to_player`: die Entfernung von deinen Augen zur Entität
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: die Position der Entität
- `$$entity_uuid`: die UUID der Entität

### On Entity Stops Being In Sight

**Kennung:** `entity_stops_being_in_sight`

Wird einmal ausgeführt, wenn eine sichtbare Entität deinen Bildschirm verlässt oder mehr als 200 Blöcke entfernt ist.

Stellt dieselben Variablen wie **On Entity Starts Being In Sight** bereit: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` und `$$entity_uuid`.

### On Interacted With Entity

**Kennung:** `entity_interacted`

Wird einmal ausgeführt, wenn du eine Entität verwendest, zum Beispiel mit einem Dorfbewohner handelst.

- `$$entity_key`: der Typ der Entität, zum Beispiel `minecraft:villager`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: die Position der Entität
- `$$entity_uuid`: die UUID der Entität

### On Entity Mounted

**Kennung:** `entity_mounted`

Wird einmal ausgeführt, wenn du beginnst, auf einer Entität zu reiten, zum Beispiel auf einem Pferd oder in einem Boot.

- `$$entity_key`: der Typ der Entität, zum Beispiel `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: die Position der Entität
- `$$entity_uuid`: die UUID der Entität

### On Entity Unmounted

**Kennung:** `entity_unmounted`

Wird einmal ausgeführt, wenn du aufhörst, auf einer Entität zu reiten.

- `$$entity_key`: der Typ der Entität, zum Beispiel `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: die Position der Entität
- `$$entity_uuid`: die UUID der Entität

### On Entity Spawned

**Kennung:** `entity_spawned`

Benötigt FancyMenu auf dem Server. Wird ausgeführt, wenn irgendwo in der Welt eine Entität erscheint, auch weit entfernt oder in einer anderen Dimension.

- `$$entity_key`: der Typ der Entität, zum Beispiel `minecraft:zombie`
- `$$distance_to_player`: die Entfernung zu dir oder `-1` in einer anderen Dimension
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: der Ort, an dem sie erschienen ist
- `$$entity_uuid`: die UUID der Entität
- `$$dimension_key`: die Dimension, zum Beispiel `minecraft:overworld`
- `$$is_same_dimension_as_player`: `true`, wenn sie in deiner Dimension erschienen ist

### On Entity Died

**Kennung:** `entity_died`

Benötigt FancyMenu auf dem Server. Wird ausgeführt, wenn irgendwo in der Welt eine Entität stirbt, auch weit entfernt oder in einer anderen Dimension.

- `$$entity_key`: der Typ der Entität, zum Beispiel `minecraft:ender_dragon`
- `$$distance_to_player`: die Entfernung zu dir oder `-1` in einer anderen Dimension
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: die Position, an der sie gestorben ist
- `$$entity_uuid`: die UUID der Entität
- `$$dimension_key`: die Dimension, zum Beispiel `minecraft:the_end`
- `$$damage_type`: die Art des Schadens, an dem sie gestorben ist, zum Beispiel `minecraft:player_attack`
- `$$is_same_dimension_as_player`: `true`, wenn sie in deiner Dimension gestorben ist
- `$$entity_killed_by_name`: der Name des Angreifers oder `NONE`
- `$$entity_killed_by_key`: der Typ des Angreifers, zum Beispiel `minecraft:player`, oder `NONE`
- `$$entity_killed_by_uuid`: die UUID des Angreifers oder `NONE`

## Welt und Orte

### On Enter Biome

**Kennung:** `enter_biome`

Wird einmal ausgeführt, wenn du ein anderes Biom betrittst.

- `$$biome_key`: das Biom, zum Beispiel `minecraft:cherry_grove`

### On Leave Biome

**Kennung:** `leave_biome`

Wird einmal ausgeführt, wenn du ein Biom verlässt.

- `$$biome_key`: das Biom, das du verlassen hast, zum Beispiel `minecraft:cherry_grove`

### On Enter Structure

**Kennung:** `enter_structure`

Benötigt FancyMenu auf dem Server. Wird einmal ausgeführt, wenn du den Bereich einer Struktur betrittst. Die Erkennung ist ungenau, daher kann der Listener auch in der Nähe oder oberhalb einer Struktur ausgelöst werden, etwa bei einem Minenschacht unter dir. Für die Erkennung nur im Inneren verwende **On Enter Structure (High Precision)**.

- `$$structure_key`: die Struktur, zum Beispiel `minecraft:village_plains`

### On Leave Structure

**Kennung:** `leave_structure`

Benötigt FancyMenu auf dem Server. Wird einmal ausgeführt, wenn du den Bereich einer Struktur verlässt. Die Erkennung ist genauso ungenau wie bei **On Enter Structure**.

- `$$structure_key`: die Struktur, die du verlassen hast

### On Enter Structure (High Precision)

**Kennung:** `enter_structure_high_precision`

Benötigt FancyMenu auf dem Server. Wird einmal ausgeführt, wenn du das Innere einer Struktur betrittst.

- `$$structure_key`: die Struktur, zum Beispiel `minecraft:stronghold`

### On Leave Structure (High Precision)

**Kennung:** `leave_structure_high_precision`

Benötigt FancyMenu auf dem Server. Wird einmal ausgeführt, wenn du eine Struktur vollständig verlassen hast.

- `$$structure_key`: die Struktur, die du verlassen hast

### On Dimension Entered

**Kennung:** `enter_dimension`

Wird einmal ausgeführt, wenn du eine andere Dimension betrittst.

- `$$dimension_key`: die Dimension, zum Beispiel `minecraft:the_nether`

### On Weather Changed

**Kennung:** `weather_changed`

Wird einmal ausgeführt, wenn sich das Wetter ändert. Der Listener wird auch ausgelöst, wenn sich das Wetter an deinem Standort ändert: Während es regnet, zählt auch der Wechsel in eine Wüste, ein verschneites Biom oder ein Gebäude.

- `$$weather_type`: `clear`, `rain` oder `thunder`
- `$$weather_can_snow`: `true`, wenn es an deinem Standort schneien würde
- `$$weather_can_rain`: `true`, wenn es an deinem Standort regnen würde

### On Raid Started

**Kennung:** `raid_started`

Benötigt FancyMenu auf dem Server. Wird ausgeführt, wenn ein Überfall beginnt, während du dich in seinem Gebiet befindest, sodass die Überfallleiste angezeigt wird. Es gibt keine Variablen.

Das Betreten eines bereits laufenden Überfalls zählt nicht. Verwende dafür **On Enter Active Raid Area**.

### On Enter Active Raid Area

**Kennung:** `enter_active_raid_area`

Benötigt FancyMenu auf dem Server. Wird ausgeführt, wenn du das Gebiet eines bereits laufenden Überfalls betrittst, sodass die Überfallleiste angezeigt wird. Es gibt keine Variablen.

### On Leave Active Raid Area

**Kennung:** `leave_active_raid_area`

Benötigt FancyMenu auf dem Server. Wird ausgeführt, wenn du das Gebiet eines Überfalls verlässt und die Überfallleiste verschwindet. Auch ein Tod oder Dimensionswechsel dort zählt, das Ende des Überfalls jedoch nicht. Es gibt keine Variablen.

### On Raid Finished

**Kennung:** `raid_finished`

Benötigt FancyMenu auf dem Server. Wird ausgeführt, wenn ein Überfall endet, während du dich in seinem Gebiet befindest.

- `$$raid_result`: `victory` oder `defeat`

## Geräusche und Musik

### On Music Track Started

**Kennung:** `music_track_started`

Wird einmal ausgeführt, wenn die Wiedergabe eines Musikstücks beginnt.

- `$$track_resource_location`: die Audiodatei des Musikstücks
- `$$track_display_name`: der Name des Musikstücks oder `UNKNOWN`
- `$$track_artist`: der Interpret des Musikstücks oder `UNKNOWN`
- `$$track_duration_ms`: die Dauer in Millisekunden oder `0`, wenn sie unbekannt ist

### On Music Track Stopped

**Kennung:** `music_track_stopped`

Wird einmal ausgeführt, wenn die Wiedergabe des Musikstücks endet, weil es zu Ende ist oder durch ein anderes ersetzt wurde.

Stellt dieselben Variablen wie **On Music Track Started** bereit: `$$track_resource_location`, `$$track_display_name`, `$$track_artist` und `$$track_duration_ms`.

### On World Sound Triggered

**Kennung:** `world_sound_triggered`

Wird jedes Mal ausgeführt, wenn in deiner Nähe ein Geräusch in der Welt beginnt, zum Beispiel eine Tür oder ein Creeper.

- `$$sound_resource_location`: die Audiodatei
- `$$sound_display_name`: der Untertitel des Geräuschs oder `UNKNOWN`
- `$$sound_origin_pos_x`, `$$sound_origin_pos_y`, `$$sound_origin_pos_z`: der Ursprung des Geräuschs
- `$$sound_origin_distance_to_player`: die Entfernung zum Geräusch
- `$$sound_origin_direction_from_player`: die Richtung in Grad (0 bis 360), relativ zu deiner Blickrichtung
