---
title: Aktionsskripte
description: 'Wie man Aktionsskripte mit Buttons, Slidern, Tickern und mehr verwendet.'
---

# Aktionsskripte

FancyMenu ermöglicht es dir, Menüs durch das Zuweisen von **Aktionen** zu Elementen interaktiv zu machen. Diese Aktionen werden ausgeführt, wenn auf einen Button geklickt wird, ein Ticker tickt, ein Slider verwendet wird oder wenn ein Bildschirm geöffnet oder geschlossen wird. Du kannst außerdem erweiterte Aktionsskripte mit einfachen Kontrollanweisungen wie **if**, **else-if**, **else** und **while** erstellen, um zu steuern, welche Aktionen wann ausgeführt werden.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Action script editor" style="max-width:800px;width:100%;height:auto;">

# Was sind Aktionen?

Eine **Aktion** ist eine Aufgabe oder Funktion, die FancyMenu ausführt, wenn sie ausgelöst wird. Zum Beispiel kann eine Aktion einen neuen Bildschirm öffnen, eine Chatnachricht senden oder die Lautstärke eines Audioelements anpassen. Im Editor von FancyMenu werden Aktionen mit einem Wert konfiguriert (falls nötig), der zusätzliche Details bereitstellt — zum Beispiel eine URL oder Serveradresse.

# Was sind Anweisungen?

Um komplexeres Verhalten zu erstellen, unterstützt FancyMenu grundlegende Kontrollanweisungen in Aktionsskripten. Dazu gehören:

- **If-Anweisung:** Führt einen Aktionsblock nur aus, wenn eine bestimmte [Bedingung](/en/conditions) erfüllt ist.
- **Else-If-Anweisung:** Prüft eine weitere [Bedingung](/en/conditions), wenn das vorherige *if* (oder ein früheres *else-if*) nicht erfüllt wurde.
- **Else-Anweisung:** Wird ausgeführt, wenn keine der vorherigen [Bedingungen](/en/conditions) erfüllt sind.
- **While-Anweisung:** Wiederholt einen Aktionsblock fortlaufend, solange eine [Bedingung](/en/conditions) wahr bleibt (mit einem eingebauten Timeout, um endlose Schleifen zu verhindern).
- **Verzögerungsblock:** Wartet die angegebene Zeit, bevor die darin enthaltenen Aktionen ausgeführt werden. Der Rest des Skripts läuft während des Countdowns weiter.
- **Später ausführen-Block:** Wartet Aktionen zur Ausführung auf dem Hauptthread nach einer Millisekunden-Verzögerung ein.
- **Kommentar:** Fügt eine Notiz innerhalb des Skripts zur besseren Organisation hinzu. Kommentare führen keine Aktion aus.

Durch die Kombination dieser Anweisungen mit Aktionen kannst du dynamisches und bedingtes Verhalten erstellen, zum Beispiel prüfen, ob die Gesundheit eines Spielers niedrig ist, bevor eine Warnmeldung gesendet wird, oder ein Update wiederholen, bis sich eine Bedingung ändert.

# Wo kannst du Aktionsskripte verwenden?

Aktionsskripte sind vielseitig und können in deinem gesamten Layout verwendet werden. Du kannst sie beispielsweise zuweisen an:

- **Buttons:** Führt eine Aktion aus, wenn auf den Button geklickt wird.
- **Ticker:** Führt fortlaufend ein Aktionsskript aus, um Informationen auf dem Bildschirm innerhalb eines Layouts zu aktualisieren.
- **Slider:** Löst ein Aktionsskript aus, sobald sich der Wert des Sliders ändert.
- **Bildschirmereignisse:** Führt Skripte aus, wenn ein Bildschirm geöffnet oder geschlossen wird (zum Beispiel, um einen Sound abzuspielen, wenn ein Menü erscheint).
- **Listener:** Wenn ein Listener, der auf ein bestimmtes Ereignis hört, ausgelöst wird, führt er sein Aktionsskript aus.
- **Scheduler:** Führt Aktionen zeitgesteuert aus, auch wenn kein Bildschirm geöffnet ist.

# Platzhalter in Aktionen verwenden

Aktionswerte unterstützen dynamische Inhalte durch **Platzhalter**. Meistens verwenden diese Platzhalter eine JSON-ähnliche Syntax und werden zur Laufzeit durch aktuelle Daten ersetzt.

## JSON-ähnliche Platzhalter

Das sind die normalen [Platzhalter](/en/placeholders), die an vielen Stellen innerhalb von Layouts verwendet werden können.

Sie folgen dieser Syntax:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Damit können Spieldaten wie der Name des Spielers, die Bildschirmabmessungen oder berechnete Werte über den **Calculator**-Platzhalter abgerufen werden. Du kannst Platzhalter auch verschachteln, um fortgeschrittenere Anwendungen zu ermöglichen.

## `$$`-Platzhalter (Variablen)

Die `$$`-Platzhalter sind speziell. Einige Funktionen von FancyMenu stellen diese speziellen Platzhalter für ihre verschachtelten Aktionen, Anforderungen und normalen Platzhalter bereit, sodass sie darin verwendet werden können, um mehr Informationen über die Umgebung (Element, Listener usw.) zu erhalten, in der sie sich befinden.

Wenn Aktionen beispielsweise innerhalb eines Sliders verwendet werden, wird `$$value` in der Aktion durch den aktuellen Wert des Sliders ersetzt.

Wenn Aktionen in Listenern verwendet werden, stellt jeder Listener seine eigene einzigartige Menge an Variablen/Platzhaltern bereit, um mehr Informationen über den Listener zu erhalten, wie gedrückte Maustaste, eingegebene Struktur usw.

# So richtest du Aktionen ein und bearbeitest sie

Um Aktionen (und Anweisungsblöcke) für ein Element hinzuzufügen, zu bearbeiten oder zu entfernen, **klicke einfach mit der rechten Maustaste auf das Element** (egal ob Button, Slider, Ticker oder anderes interaktives Element) und wähle dann **Aktionsskript verwalten**. Dadurch öffnet sich der Bildschirm „Aktionen verwalten“, in dem du:

- **Neue Aktionen oder Anweisungen hinzufügen:** Neue Aktionseinträge oder Kontrollanweisungen (if, else-if, else, while) einfügen, um dein Skript aufzubauen.
- **Vorhandene Aktionen oder Anweisungen bearbeiten:** Den Aktionswert ändern oder die Kontrolllogik anpassen.
- **Aktionen oder Anweisungen entfernen:** Unerwünschte Aktionen aus dem Skript löschen.

Für [Listener](/listeners) gibt es ein spezielles Menü zum Verwalten und Erstellen von Listenern, einschließlich des Zugriffs auf deren Aktionsskripte, damit du dieselbe Erfahrung hast wie beim Bearbeiten des Aktionsskripts eines Buttons oder Sliders.

> Wenn du dich im Bildschirm des Aktionsskript-Editors befindest, klicke einfach mit der rechten Maustaste auf den großen dunkelgrauen Bereich, um ein Kontextmenü zum Hinzufügen von Aktionen, Anweisungen und mehr zu öffnen.
{.is-info}


# Tastenkürzel und mehr im Aktionsskript-Editor

Der Aktionsskript-Editor bietet einige praktische QoL-Funktionen, die das Bearbeiten von Skripten super einfach machen.

## Tastenkürzel

- `DEL` : Entfernt den ausgewählten Eintrag sofort
- `ENTER` : Startet die Inline-Bearbeitung des ausgewählten Eintrags (oder öffnet den Bearbeitungsbildschirm, wenn für den ausgewählten Eintrag keine Inline-Bearbeitung vorhanden ist)
- `CTRL + C` : Kopiert die ausgewählte Aktion (funktioniert derzeit nur mit Aktionen)
- `CTRL + V` : Fügt die zuvor kopierte Aktion ein
- `CTRL + Z` : Einen Schritt zurück (Rückgängig)
- `CTRL + Y` : Einen Schritt vorwärts (Wiederholen)
- `ARROW UP` : Einen Eintrag nach oben zum aktuell ausgewählten navigieren
- `ARROW DOWN` : Einen Eintrag nach unten zum aktuell ausgewählten navigieren
- `SHIFT + ARROW UP` : Verschiebt den ausgewählten Eintrag um einen nach oben
- `SHIFT + ARROW DOWN` : Verschiebt den ausgewählten Eintrag um einen nach unten
- `A` : Öffnet den Action Chooser schnell, um eine neue Aktion hinzuzufügen
- `CTRL + S` : Fertig/Speichern aus dem Editorfenster

## Weitere QoL-Funktionen

- Ein Doppelklick auf den Wert einer Aktion ermöglicht es dir, den Wert zu bearbeiten, ohne den vollständigen Wert-Bearbeitungsbildschirm zu öffnen.
- IF-Anweisungsketten (mit angehängten ELSE-/ELSE-IF-Anweisungen), WHILE-Schleifen und Ordner können eingeklappt werden (nur visuell, beeinflusst nicht die Skriptlogik).
- Der Editor fügt neue Aktionen immer unter dem ausgewählten Eintrag hinzu (oder verschachtelt in der ausgewählten Kette/Schleife/im ausgewählten Ordner).
- Ein Rechtsklick auf den dunkelgrauen Hintergrundbereich des Skripts öffnet ein Kontextmenü mit Optionen zum Hinzufügen von Aktionen, Anweisungen und allem anderen Wichtigen.

# Aktionen im Detail

Diese Liste enthält die meisten, wenn nicht sogar alle in FancyMenu verfügbaren Aktionen. Es ist möglich, dass die Liste durch Updates des Mods manchmal etwas veraltet ist.

## Nächster Titel (`audio_next_track`)
- **Beschreibung:** Wechselt zum nächsten Titel in einem Audioelement
- **Wert erforderlich:** Ja - `audio_element_identifier` (die ID des zu steuernden Audioelements)

## Vorheriger Titel (`audio_previous_track`)
- **Beschreibung:** Wechselt zum vorherigen Titel in einem Audioelement
- **Wert erforderlich:** Ja - `audio_element_identifier` (die ID des zu steuernden Audioelements)

## Titel-Lautstärke setzen (`set_audio_element_volume`)
- **Beschreibung:** Setzt die Lautstärke eines Audioelements (0.0 bis 1.0)
- **Wert erforderlich:** Ja - `element_identifier:volume`

## Titel abspielen/Pause umschalten (`audio_toggle_play`)
- **Beschreibung:** Schaltet Wiedergabe/Pause des aktuellen Titels eines Audioelements um
- **Wert erforderlich:** Ja - `audio_element_identifier`

## Audio abspielen (`play_audio`)
- **Beschreibung:** Spielt eine Audioressource einmal ab. Die Aktion verfolgt das von ihr gestartete Audio, damit es später mit `stop_all_action_audios` gestoppt werden kann.
- **Wert erforderlich:** Ja - JSON-Konfiguration mit `audioSource`, `soundChannel` und `baseVolume`
- **Beispielwert:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

## Alle Aktions-Audios stoppen (`stop_all_action_audios`)
- **Beschreibung:** Stoppt alle Audiotracks, die durch die Aktion **Audio abspielen** gestartet wurden. Dies stoppt keine Audio-Elemente, keine Menü-Öffnen/Schließen-Sounds, keine Button-Sounds oder andere Audiosysteme.
- **Wert erforderlich:** Nein

## Videoelement-Lautstärke setzen (`set_video_element_volume`)
- **Beschreibung:** Setzt die Lautstärke eines Videoelements (0.0 bis 1.0)
- **Wert erforderlich:** Ja - `video_element_identifier:volume`

## Videoelement-Abspielzeit setzen (`set_video_element_play_time`)
- **Beschreibung:** Springt ein Videoelement zu einem Zeitstempel in Millisekunden
- **Wert erforderlich:** Ja - `video_element_identifier:timestamp_ms`

## Pausenzustand des Videoelements umschalten (`toggle_video_element_pause_state`)
- **Beschreibung:** Schaltet den Pausenzustand eines Videoelements um
- **Wert erforderlich:** Ja - `video_element_identifier`

## Video-Menühintergrund-Lautstärke setzen (`set_video_menu_background_volume`)
- **Beschreibung:** Setzt die Lautstärke eines Video-Menühintergrunds (0.0 bis 1.0)
- **Wert erforderlich:** Ja - `background_identifier:volume`

> Um die Kennung eines Hintergrunds zu erhalten, klicke mit der rechten Maustaste auf den Editor-Hintergrund und dann auf „Hintergrund-Kennung kopieren“.
{.is-info}

## Video-Menühintergrund-Abspielzeit setzen (`set_video_menu_background_play_time`)
- **Beschreibung:** Springt einen Video-Menühintergrund zu einem Zeitstempel in Millisekunden
- **Wert erforderlich:** Ja - `background_identifier:timestamp_ms`

> Um die Kennung eines Hintergrunds zu erhalten, klicke mit der rechten Maustaste auf den Editor-Hintergrund und dann auf „Hintergrund-Kennung kopieren“.
{.is-info}

## Pausenzustand des Video-Menühintergrunds umschalten (`toggle_video_menu_background_pause_state`)
- **Beschreibung:** Schaltet den Pausenzustand eines Video-Menühintergrunds um
- **Wert erforderlich:** Ja - `background_identifier`

> Um die Kennung eines Hintergrunds zu erhalten, klicke mit der rechten Maustaste auf den Editor-Hintergrund und dann auf „Hintergrund-Kennung kopieren“.
{.is-info}

## Layout umschalten (`toggle_layout`)
- **Beschreibung:** Schaltet ein Layout anhand seines Namens um (Aktivieren/Deaktivieren)
- **Wert erforderlich:** Ja - `layout_name`

## Layout aktivieren (`enable_layout`)
- **Beschreibung:** Aktiviert ein Layout anhand seines Namens
- **Wert erforderlich:** Ja - `layout_name`

## Layout deaktivieren (`disable_layout`)
- **Beschreibung:** Deaktiviert ein Layout anhand seines Namens
- **Wert erforderlich:** Ja - `layout_name`

## Bildschirm oder benutzerdefinierte GUI öffnen (`opengui`)
- **Beschreibung:** Öffnet einen Bildschirm anhand seiner Kennung (Vanilla, Mod oder benutzerdefinierte GUI)
- **Wert erforderlich:** Ja - `screen_identifier`

> Diese Aktion **funktioniert nicht für jeden Bildschirm**, insbesondere nicht für Mod-Bildschirme. Wenn die Aktion einen Bildschirm nicht öffnen kann, wird ein Fehler angezeigt. In diesem Fall kannst du nicht viel tun, denn wahrscheinlich ist der Bildschirm zu komplex, um von FancyMenu automatisch geöffnet zu werden.
> 
> Eine manuelle Kompatibilität für Mod-Bildschirme wird von FancyMenu-Seite aus ebenfalls nicht mehr hinzugefügt, da die Unterstützung für alle Mods da draußen ewig dauern würde, sorry. In den meisten Fällen ist es in diesem Fall auch nicht empfehlenswert, den Entwickler des anderen Mods zu kontaktieren, da es, wenn FancyMenu den Bildschirm nicht öffnen kann, keinen einfachen Weg gibt, Unterstützung dafür hinzuzufügen. Die empfohlene Umgehungslösung ist, die Aktion **„Vanilla/Mod-Button nachahmen“** zu verwenden, um einen Button nachzuahmen, der den jeweiligen Bildschirm öffnet. Wenn es keinen Button gibt, hast du leider Pech.
{.is-info}

## Bildschirm schließen (`closegui`)
- **Beschreibung:** Schließt den aktiven Bildschirm
- **Wert erforderlich:** Nein

## Bildschirm aktualisieren (`update_screen`)
- **Beschreibung:** Initialisiert den aktuellen Bildschirm neu
- **Wert erforderlich:** Nein

## Zurück zum letzten Bildschirm (`back_to_last_screen`)
- **Beschreibung:** Geht zum vorherigen Bildschirm zurück (dem vor dem aktuellen)
- **Wert erforderlich:** Nein

## Server beitreten (`joinserver`)
- **Beschreibung:** Verbindet den Spieler mit einem Minecraft-Server
- **Wert erforderlich:** Ja - `server_ip:port`

## Welt betreten (`loadworld`)
- **Beschreibung:** Betritt eine Minecraft-Welt
- **Wert erforderlich:** Ja - `world_folder_name`

## Letzte Welt/letzten Server betreten/beitreten (`join_last_world`)
- **Beschreibung:** Betritt/beitritt der letzten Welt oder dem letzten Server, in dem der Spieler war
- **Wert erforderlich:** Nein

## Welt oder Server verlassen (`disconnect_server_or_world`)
- **Beschreibung:** Verlässt eine Welt oder einen Server und öffnet einen angegebenen Bildschirm
- **Wert erforderlich:** Ja - `screen_identifier`

## Minecraft beenden (`quitgame`)
- **Beschreibung:** Beendet Minecraft vollständig
- **Wert erforderlich:** Nein

## Chatnachricht/Befehl senden (`sendmessage`)
- **Beschreibung:** Sendet eine Chatnachricht oder führt einen Chatbefehl aus
- **Wert erforderlich:** Ja - `message_text` oder `/command_text`

## Befehl als integrierter Server ausführen (`execute_command_as_integrated_server`)
- **Beschreibung:** Führt in Einzelspieler den Befehl zwangsweise als integrierten Server aus und ignoriert dabei Berechtigungen und die Cheat-Einstellung.
- **Wert erforderlich:** Ja - Befehlstext, zum Beispiel `/give @p minecraft:diamond 1`

> Diese Aktion funktioniert nur im Einzelspieler, solange die Welt nicht für LAN geöffnet ist. In Mehrspieler-Servern tut sie absichtlich nichts.
{.is-warning}

## In Chat einfügen (`paste_to_chat`)
- **Beschreibung:** Fügt Text in das Chat-Eingabefeld ein (anhängen oder ersetzen)
- **Wert erforderlich:** Ja - `true:Text` oder `false:Text`

## Im Chat anzeigen [Clientseitig] (`display_in_chat_client_side`)
- **Beschreibung:** Gibt Text direkt im lokalen Chat aus (kein Server)
- **Wert erforderlich:** Ja - `text_or_json`

## FM-Daten an Server senden (`send_fm_data_to_server`)
- **Beschreibung:** Sendet benutzerdefinierte Textdaten über den FM-Data-Paketkanal an den aktuellen FancyMenu-Server.
- **Wert erforderlich:** Ja - `data_identifier||data`

## Mit Remote-Server verbinden (`connect_to_remote_server`)
- **Beschreibung:** Öffnet oder verwendet erneut eine vom Client initiierte WebSocket-Verbindung zu einem externen Remote-Server.
- **Wert erforderlich:** Ja - Remote-Server-URL, zum Beispiel `wss://example.com/ws`

## Daten an Remote-Server senden (`send_data_to_remote_server`)
- **Beschreibung:** Öffnet oder verwendet erneut eine Verbindung zum Remote-Server und sendet Textdaten dorthin.
- **Wert erforderlich:** Ja - `remote_server_url||data`

## Verbindung zu Remote-Server trennen (`close_remote_server_connection`)
- **Beschreibung:** Schließt eine bestimmte Remote-Server-Verbindung anhand der Request-ID.
- **Wert erforderlich:** Ja - Request-ID, meist aus einer Remote-Server-Listener-Variable wie `$$request_id`

## Alle Remote-Server-Verbindungen schließen (`close_all_remote_server_connections`)
- **Beschreibung:** Schließt alle aktiven, von FancyMenu geöffneten Remote-Server-Verbindungen.
- **Wert erforderlich:** Nein

## URL im Browser öffnen (`openlink`)
- **Beschreibung:** Öffnet einen Link in deinem Standardbrowser
- **Wert erforderlich:** Ja - `https://example.com`

## Text in die Zwischenablage kopieren (`copytoclipboard`)
- **Beschreibung:** Kopiert Text in die Zwischenablage
- **Wert erforderlich:** Ja - `text_to_copy`

## In das Spiel-Log schreiben (`print_to_log`)
- **Beschreibung:** Schreibt eine Zeile in das Spiel-Log
- **Wert erforderlich:** Ja - `text_to_log`

## Variablenwert setzen (FM-Variable) (`set_variable`)
- **Beschreibung:** Speichert Textinhalt in einer FancyMenu-Variable
- **Wert erforderlich:** Ja - `variable_name:variable_value`

## Alle Variablen löschen (FM-Variable) (`clear_variables`)
- **Beschreibung:** Löscht ALLE von FancyMenu gespeicherten Variablen
- **Wert erforderlich:** Nein

## HTTP-Anfrage senden (`send_http_request`)
- **Beschreibung:** Sendet eine HTTP-Anfrage; kann die Antwort in einer Variable speichern
- **Wert erforderlich:** Ja - HTTP-Anfrage-Konfiguration

> Mit dieser Aktion kannst du Daten an REST-APIs, Webhooks oder jeden beliebigen HTTP-Endpunkt senden.
> Unterstützt verschiedene Authentifizierungsmethoden, benutzerdefinierte Header und unterschiedliche Anfragearten.
> 
> Mit dieser Aktion kannst du außerdem die Antwort der Anfrage in einer FancyMenu-Variable für die spätere Verwendung speichern!
{.is-info}

## Ressourcenpaket verwalten (`manage_resource_pack`)
- **Beschreibung:** Ein Ressourcenpaket anhand des Anzeigenamens aktivieren/deaktivieren/umschalten (optional mit Neuladen)
- **Wert erforderlich:** Ja - `pack_name|||MODE|||reload_bool`

## Ressourcenpakete neu laden (`reload_resource_packs`)
- **Beschreibung:** Lädt Ressourcenpakete neu (5s Abklingzeit)
- **Wert erforderlich:** Nein

## FancyMenu neu laden (`reloadmenu`)
- **Beschreibung:** Lädt FancyMenu neu, einschließlich Panoramen, Diashows und aller Ressourcen (aufwendig)
- **Wert erforderlich:** Nein

> Diese Aktion hat **große Auswirkungen auf die Leistung** und kann Lags verursachen, wenn sie in Tickern verwendet wird. Es wird nicht empfohlen, diese Aktion in etwas anderem als einem Button zu verwenden.
{.is-warning}

## Element-Animator umschalten (`toggle_element_animator`)
- **Beschreibung:** Schaltet den Wiedergabestatus eines Element-Animators um
- **Wert erforderlich:** Ja - `animator_identifier`

## Element-Animator aktivieren (`enable_element_animator`)
- **Beschreibung:** Aktiviert einen Element-Animator
- **Wert erforderlich:** Ja - `animator_identifier`

## Element-Animator deaktivieren (`disable_element_animator`)
- **Beschreibung:** Deaktiviert einen Element-Animator
- **Wert erforderlich:** Ja - `animator_identifier`

## Element-Animator zurücksetzen (`reset_element_animator`)
- **Beschreibung:** Setzt die Zeitleiste/den Zustand eines Element-Animators zurück
- **Wert erforderlich:** Ja - `animator_identifier`

## Vanilla/Mod-Button nachahmen (`mimicbutton`)
- **Beschreibung:** Imitiert die Klickaktion eines Vanilla- oder Mod-Buttons
- **Wert erforderlich:** Ja - `screen_identifier:widget_locator`

## Keybind nachahmen (`mimic_keybind`)
- **Beschreibung:** Führt eine Minecraft-Tastenkombination aus (optional gedrückt halten)
- **Wert erforderlich:** Ja - `keybind_id|||keep_pressed_bool|||duration_ms`

## Wert eines Texteingabefelds setzen (`set_text_input_field_value`)
- **Beschreibung:** Setzt den Wert eines benutzerdefinierten oder Vanilla-Eingabefelds anhand der Elementkennung.
- **Wert erforderlich:** Ja - `element_identifier|||new_value|||force_set_when_inactive`

## Datei im Spielverzeichnis erstellen (`create_file_in_game_dir`)
- **Beschreibung:** Erstellt eine leere Datei im Spielverzeichnis (Instanz-Root). Akzeptiert das Präfix `.minecraft/`, um das Standardverzeichnis des Launcher-Profils anzusprechen (kann vom aktuellen Instanzverzeichnis abweichen).
- **Wert erforderlich:** Ja - `file_path`

## Datei/Ordner im Spielverzeichnis löschen (`delete_file_in_game_dir`)
- **Beschreibung:** Löscht eine Datei oder einen Ordner im Spielverzeichnis (Instanz-Root). Akzeptiert das Präfix `.minecraft/`, um das Standard-Launcher-Profil anzusprechen (kann vom laufenden Instanzverzeichnis abweichen). Hänge `*` an, um **alle Dateien direkt innerhalb** eines Ordners zu löschen (ignoriert Unterordner; behält den Ordner).
- **Wert erforderlich:** Ja - `target_path`

## Datei/Ordner im Spielverzeichnis kopieren (`copy_file_in_game_dir`)
- **Beschreibung:** Kopiert innerhalb des Spielverzeichnisses (Instanz-Root); das Präfix `.minecraft/` zielt auf das Standard-Launcher-Profil (nicht immer die aktuelle Instanz). Hänge `*` an den **Quellpfad** an, um jede Datei direkt innerhalb dieses Ordners zu kopieren (ignoriert Unterordner); das Ziel muss ein Verzeichnis sein und darf kein `*` verwenden.
- **Wert erforderlich:** Ja - `source||destination`

## Datei/Ordner im Spielverzeichnis verschieben (`move_file_in_game_dir`)
- **Beschreibung:** Verschiebt innerhalb des Spielverzeichnisses (Instanz-Root); das Präfix `.minecraft/` zielt auf das Standard-Launcher-Profil (kann von der aktuellen Instanz abweichen). Hänge `*` an den **Quellpfad** an, um jede Datei direkt innerhalb dieses Ordners zu verschieben (ignoriert Unterordner); das Ziel muss ein Verzeichnis sein und darf kein `*` verwenden.
- **Wert erforderlich:** Ja - `source||destination`

## Datei/Ordner im Spielverzeichnis umbenennen (`rename_file_in_game_dir`)
- **Beschreibung:** Benennt eine Datei oder einen Ordner innerhalb des Spielverzeichnisses (Instanz-Root) um; das Präfix `.minecraft/` zielt auf das Standard-Launcher-Profil (kann von der aktuellen Instanz abweichen). Der Inhalt bleibt erhalten, nur der Name ändert sich.
- **Wert erforderlich:** Ja - `path||new_name`

## Datei ins Spielverzeichnis herunterladen (`download_file_to_game_dir`)
- **Beschreibung:** Lädt eine Datei asynchron in das Spielverzeichnis (Instanz-Root) herunter; das Präfix `.minecraft/` zielt auf das Standard-Launcher-Profil (nicht unbedingt die laufende Instanz). Gib den **Zielordner** an; der Dateiname wird automatisch aus Headern/URL abgeleitet.
- **Wert erforderlich:** Ja - `url||target_folder`

## ZIP-Datei im Spielverzeichnis entpacken (`extract_zip_file_in_game_dir`)
- **Beschreibung:** Entpackt eine ZIP-Datei in einen Zielordner innerhalb des Spielverzeichnisses oder des Standardverzeichnisses `.minecraft`. Löst beim Abschluss den Listener **On ZIP Extracted via Action** aus.
- **Wert erforderlich:** Ja - `source_zip_path||target_folder_path`

## Datei/Ordner im Spielverzeichnis öffnen (`open_file_folder_in_game_dir`)
- **Beschreibung:** Öffnet eine Datei oder einen Ordner mit der Standardanwendung des Betriebssystems. Der Zielpfad muss aus Sicherheitsgründen innerhalb des Spielverzeichnisses oder des Standardverzeichnisses `.minecraft` liegen.
- **Wert erforderlich:** Ja - `target_path`

## Datei im Spielverzeichnis schreiben (`write_file_in_game_dir`)
- **Beschreibung:** Schreibt Text in das Spielverzeichnis oder hängt ihn dort an (Instanz-Root); das Präfix `.minecraft/` zielt auf das Standard-Launcher-Profil (kann von dieser Instanz abweichen). Erstellt die Datei, falls sie fehlt. Unterstützt `\n` im Wert für Zeilenumbrüche; der Anfügemodus wird durch den letzten booleschen Wert gesteuert.
- **Wert erforderlich:** Ja - `path|||content|||append_bool`

## Datei aus dem System auswählen (`select_file_to_game_dir`)
- **Beschreibung:** Öffnet einen nativen Dateiauswahldialog (beliebiger Ort) und kopiert die ausgewählte Datei in das Spielverzeichnis (Instanz-Root) oder in das Standardverzeichnis `.minecraft/` bei Präfix (dieses Standardverzeichnis kann von dieser Instanz abweichen). Unterstützt Filter für Dateiendungen, ein benutzerdefiniertes Filter-Label und optionales Überschreiben.
- **Wert erforderlich:** Ja - Auswahlkonfiguration

## Toast anzeigen (`show_toast`)
- **Beschreibung:** Zeigt eine konfigurierbare Toast-Benachrichtigung an
- **Wert erforderlich:** Ja - Toast-Konfiguration

## Scheduler starten (`start_scheduler`)
- **Beschreibung:** Startet einen Scheduler anhand seiner Scheduler-ID.
- **Wert erforderlich:** Ja - `scheduler_id`

## Scheduler stoppen (`stop_scheduler`)
- **Beschreibung:** Stoppt einen Scheduler anhand seiner Scheduler-ID.
- **Wert erforderlich:** Ja - `scheduler_id`

## Minecraft-Option setzen (`edit_minecraft_option`)
- **Beschreibung:** Bearbeitet eine Minecraft-Konfigurationsoption
- **Wert erforderlich:** Ja - `option_name:set_to_value`
