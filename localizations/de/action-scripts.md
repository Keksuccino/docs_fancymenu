---
title: Action-Skripte
description: 'Wie man Action-Skripte mit Buttons, Slidern, Tickern und mehr verwendet.'
---
# Action-Skripte

Action-Skripte führen konfigurierte Aufgaben aus, wenn ein [Button](./elements#button) angeklickt wird, ein [Ticker](./elements#ticker) aktualisiert wird, ein [Slider](./elements#slider) sich ändert, ein Bildschirm geöffnet oder geschlossen wird oder ein anderes unterstütztes Ereignis eintritt. Anweisungen wie **if**, **else-if**, **else** und **while** sorgen für bedingte Steuerung.

> [!CAUTION]
> Importierte Action-Skripte können Dateien ändern, Server kontaktieren, Links öffnen oder Befehle ausführen. Verwende nur Quellen, denen du vertraust.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Action-Skript-Editor" style="max-width:800px;width:100%;height:auto;">

# Was sind Aktionen?

Eine **Aktion** ist eine Aufgabe oder ein Job, den FancyMenu bei Auslösung ausführt. Eine Aktion kann zum Beispiel einen neuen Bildschirm öffnen, eine Chatnachricht senden oder die Lautstärke eines [Audio-Elements](./elements#audio) anpassen. Im Editor von FancyMenu werden Aktionen mit einem Wert konfiguriert (falls erforderlich), der zusätzliche Details liefert — etwa eine URL oder eine Serveradresse.

# Anweisungen

Um komplexeres Verhalten zu erstellen, unterstützt FancyMenu Kontrollanweisungen in Action-Skripten:

| Anweisung | Verhalten |
|---|---|
| **If** | Führt seine Aktionen nur aus, wenn seine [Voraussetzungen](./conditions) erfüllt sind. |
| **Else-If** | Prüft einen weiteren Satz von [Voraussetzungen](./conditions), wenn das vorherige **If** oder **Else-If** nicht ausgeführt wurde. |
| **Else** | Wird ausgeführt, wenn keine der vorherigen **If**- oder **Else-If**-Voraussetzungen erfüllt sind. |
| **While** | Wiederholt seine Aktionen, solange seine [Voraussetzungen](./conditions) wahr bleiben. Es stoppt nach drei Sekunden, um Endlosschleifen zu verhindern; verwende es nicht als Timer. |

# Blöcke

Blöcke können zu Skripten hinzugefügt werden und bieten nützliche Funktionen, um mehr Kontrolle über den Ausführungsfluss bzw. das Timing des Skripts zu haben, sowie einige praktische QoL-Funktionen:

| Block | Verhalten |
|---|---|
| **Delay** | Startet einen Countdown, ohne den Rest des Skripts anzuhalten. Seine verschachtelten Aktionen werden nach Ablauf der Verzögerung ausführbar; eine Bildschirm-Neuinitialisierung setzt den Countdown zurück. |
| **Execute Later** | Plant jedes Mal, wenn der Block erreicht wird, eine neue Ausführung seiner verschachtelten Aktionen nach Ablauf der Verzögerung. |
| **Comment** | Fügt eine Notiz zur Organisation innerhalb des Skripts hinzu und führt keine Aktion aus. |

# Skriptausführung

Aktionen werden von oben nach unten ausgeführt. Eine fehlgeschlagene Aktion wird protokolliert, danach läuft das Skript weiter.

Downloads, ZIP-Extraktion und HTTP-Anfragen werden später abgeschlossen; die nächste Aktion wartet nicht. Verwende [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) oder eine HTTP-Antwortvariable, wenn spätere Arbeit vom Ergebnis abhängt.

# Wo kannst du Action-Skripte verwenden?

Action-Skripte sind vielseitig und können in deinem gesamten Layout verwendet werden. Du kannst sie zum Beispiel zuweisen an:

- [**Buttons**](./elements#button): Führt eine Aktion aus, wenn der Button angeklickt wird.
- [**Ticker**](./elements#ticker): Führt kontinuierlich ein Action-Skript aus, um On-Screen-Informationen innerhalb eines Layouts zu aktualisieren.
- [**Slider**](./elements#slider): Löst ein Action-Skript aus, wenn sich der Wert des Sliders ändert.
- **Bildschirmereignisse:** Führt Skripte aus, wenn ein Bildschirm geöffnet oder geschlossen wird (z. B. um einen Sound abzuspielen, wenn ein Menü erscheint).
- [**Listener**](./listeners): Wenn ein Listener sein konfiguriertes Ereignis empfängt, führt er sein Action-Skript aus.
- [**Scheduler**](./schedulers): Führt Aktionen zeitgesteuert aus, auch wenn kein Bildschirm geöffnet ist.

# Platzhalter in Aktionen verwenden

Aktionswerte unterstützen dynamische Inhalte über **Platzhalter**. Meist verwenden diese Platzhalter eine JSON-ähnliche Syntax und werden zur Laufzeit der Aktion durch Live-Daten ersetzt.

## JSON-ähnliche Platzhalter

Dies sind die normalen [Platzhalter](./placeholders), die an vielen Stellen innerhalb von Layouts verwendet werden können.

Sie folgen dieser Syntax:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Sie können Spieldaten abrufen, etwa den Spielernamen, Bildschirmabmessungen oder berechnete Werte mithilfe des [**Calculator**-Platzhalters](./placeholders#calculator-calc). Du kannst Platzhalter auch verschachteln, um fortgeschrittenere Anwendungsfälle zu ermöglichen.

## `$$`-Platzhalter (Variablen)

`$$`-Werte sind schreibgeschützte Werte, die einem bestimmten Action-Skript von der Funktion bereitgestellt werden, die es ausführt.

Zum Beispiel liefert ein [Slider](./elements#slider) seinen aktuellen Wert als `$$value`.

Jeder [Listener](./listeners) dokumentiert die `$$`-Werte, die er bereitstellt, etwa eine gedrückte Maustaste oder eine eingegebene Struktur.

`$$`-Namen sind case-sensitiv und funktionieren nur in dem Skript, das sie bereitstellt. Siehe [Listener](./listeners#listener-variables).

## Trennzeichen für Aktionswerte

Verwende genau das Trennzeichen, das für jede Aktion angezeigt wird: `:`, `||` oder `|||`. Es gibt keine Escape-Syntax für Trennzeichen innerhalb eines Feldes.

Platzhalter werden ersetzt, bevor der Wert aufgeteilt wird. Bei `set_variable` trennt nur der erste Doppelpunkt den Namen vom Wert, spätere Doppelpunkte bleiben also Teil des Werts.

## Textwerte

[FancyMenu-Formatierungscodes](./text-formatting#minecraft-text-formatting) verwenden `&` anstelle von Minecrafts `§`-Zeichen, überall dort, wo eine Aktion formatierten Text akzeptiert.

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) und [**Paste to Chat**](#paste-to-chat-paste_to_chat) unterstützen diese Formatierungscodes.
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) akzeptiert reinen Text oder serialisiertes Minecraft-Textkomponenten-JSON.
- [**Open URL in Browser**](#open-url-in-browser-openlink) wendet dieselbe Umwandlung der Formatierungscodes an, bevor die URL an das Betriebssystem übergeben wird.

# Aktionen einrichten und bearbeiten

Um die Aktionen und Anweisungsblöcke eines Elements zu bearbeiten, **klicke mit der rechten Maustaste auf das Element** und wähle **Manage Action Script**. Im Editor kannst du:

- **Neue Aktionen oder Anweisungen hinzufügen:** Neue Aktionseinträge oder Kontrollanweisungen (if, else-if, else, while) einfügen, um dein Skript aufzubauen.
- **Vorhandene Aktionen oder Anweisungen bearbeiten:** Den Aktionswert ändern oder die Steuerlogik anpassen.
- **Aktionen oder Anweisungen entfernen:** Unerwünschte Aktionen aus dem Skript löschen.

Erstelle und bearbeite Listener-Skripte über [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Tastenkürzel im Action-Skript-Editor

## Tastenkürzel

- `DEL` : Den ausgewählten Eintrag schnell löschen
- `ENTER` : Startet die Inline-Bearbeitung des ausgewählten Eintrags (oder öffnet den Bearbeitungsbildschirm, wenn für den ausgewählten Eintrag keine Inline-Bearbeitung verfügbar ist)
- `Ctrl/Command + C` : Die ausgewählte Aktion kopieren (funktioniert derzeit nur mit Aktionen)
- `Ctrl/Command + V` : Die zuvor kopierte Aktion einfügen
- `Ctrl/Command + Z` : Einen Schritt zurück (Undo)
- `Ctrl/Command + Y` : Einen Schritt vor (Redo)
- `PFEIL HOCH` : Einen Eintrag nach oben zum vorherigen Eintrag navigieren
- `PFEIL RUNTER` : Einen Eintrag nach unten zum nächsten Eintrag navigieren
- `SHIFT + PFEIL HOCH` : Den ausgewählten Eintrag um eins nach oben verschieben
- `SHIFT + PFEIL RUNTER` : Den ausgewählten Eintrag um eins nach unten verschieben
- `A` : Den Action-Auswahlbildschirm schnell öffnen, um eine neue Aktion hinzuzufügen
- `Ctrl/Command + S` : Im Editor-Fenster fertig / speichern

## Bearbeiten

- Durch Doppelklick auf den Wert einer Aktion kannst du den Wert bearbeiten, ohne in den vollständigen Werte-Bearbeitungsbildschirm zu wechseln.
- IF-Anweisungsketten (mit angehängten ELSE-/ELSE-IF-Anweisungen), WHILE-Schleifen und Ordner können eingeklappt werden (nur visuell, beeinflusst nicht die Skriptlogik).
- Der Editor fügt neue Aktionen immer unterhalb des ausgewählten Eintrags hinzu (oder verschachtelt in der ausgewählten Kette/Schleife/im ausgewählten Ordner).
- Ein Rechtsklick auf den dunkelgrauen Hintergrund des Skriptbereichs öffnet ein Kontextmenü mit Optionen zum Hinzufügen von Aktionen, Anweisungen und allem anderen Wichtigen.

# Aktionen im Detail

Dieser Abschnitt listet die eingebauten Aktionen von FancyMenu auf.

## Nächster Titel (`audio_next_track`)

**Zweck:** Wechselt zum nächsten Titel in einem [Audio-Element](./elements#audio)

**Wert:** Erforderlich — `audio_element_identifier` (die ID des zu steuernden Audio-Elements)

## Vorheriger Titel (`audio_previous_track`)

**Zweck:** Wechselt zum vorherigen Titel in einem [Audio-Element](./elements#audio)

**Wert:** Erforderlich — `audio_element_identifier` (die ID des zu steuernden Audio-Elements)

## Lautstärke des Titels setzen (`set_audio_element_volume`)

**Zweck:** Setzt die Lautstärke eines [Audio-Elements](./elements#audio) (`0.0` bis `1.0`)

**Wert:** Erforderlich — `element_identifier:volume`

## Titel abspielen/pausieren umschalten (`audio_toggle_play`)

**Zweck:** Schaltet den aktuellen Titel eines [Audio-Elements](./elements#audio) zwischen Abspielen und Pause um

**Wert:** Erforderlich — `audio_element_identifier`

## Audio abspielen (`play_audio`)

**Zweck:** Spielt eine Audioressource einmal ab. Audio, das durch diese Aktion gestartet wurde, kann später mit [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios) gestoppt werden.

**Wert:** Erforderlich — JSON-Konfiguration mit `audioSource`, `soundChannel` und `baseVolume`

**Beispiel:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Verhalten:**

- `baseVolume` wird auf `0.0`–`1.0` begrenzt.
- Ein unbekannter Sound-Kanal verwendet den Master-Kanal.
- Die Aktion kann nicht von einem asynchronen [Ticker](./elements#ticker) ausgeführt werden; FancyMenu zeigt stattdessen einen Fehler an.
- FancyMenu wartet bis zu zehn Sekunden, bis die Audioressource bereit ist.
- Erfolgreich gestartete Titel können mit [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios) gestoppt werden.

## Alle Action-Audios stoppen (`stop_all_action_audios`)

**Zweck:** Stoppt alle Audiospuren, die von der Aktion [**Play Audio**](#play-audio-play_audio) gestartet wurden. Dies stoppt keine [Audio-Elemente](./elements#audio), Menü-Öffnen-/Schließen-Sounds, Button-Sounds oder andere Audiosysteme.

**Wert:** Nicht erforderlich

## Lautstärke des Video-Elements setzen (`set_video_element_volume`)

**Zweck:** Setzt die Lautstärke eines [Video-Elements](./video) (`0.0` bis `1.0`)

**Wert:** Erforderlich — `video_element_identifier:volume`

## Wiedergabezeit des Video-Elements setzen (`set_video_element_play_time`)

**Zweck:** Springt in einem [Video-Element](./video) zu einem Zeitstempel in Millisekunden

**Wert:** Erforderlich — `video_element_identifier:timestamp_ms`

## Pausenzustand des Video-Elements umschalten (`toggle_video_element_pause_state`)

**Zweck:** Schaltet den Pausenzustand eines [Video-Elements](./video) um

**Wert:** Erforderlich — `video_element_identifier`

## Lautstärke des Video-Hintergrunds setzen (`set_video_menu_background_volume`)

**Zweck:** Setzt die Lautstärke eines [Video-Menühintergrunds](./video) (`0.0` bis `1.0`)

**Wert:** Erforderlich — `background_identifier:volume`

> [!NOTE]
> Um die Kennung eines Hintergrunds zu erhalten, klicke mit der rechten Maustaste auf den Editor-Hintergrund und dann auf „Background Identifier kopieren“.

## Wiedergabezeit des Video-Hintergrunds setzen (`set_video_menu_background_play_time`)

**Zweck:** Springt in einem [Video-Menühintergrund](./video) zu einem Zeitstempel in Millisekunden

**Wert:** Erforderlich — `background_identifier:timestamp_ms`

> [!NOTE]
> Um die Kennung eines Hintergrunds zu erhalten, klicke mit der rechten Maustaste auf den Editor-Hintergrund und dann auf „Background Identifier kopieren“.

## Pausenzustand des Video-Hintergrunds umschalten (`toggle_video_menu_background_pause_state`)

**Zweck:** Schaltet den Pausenzustand eines [Video-Menühintergrunds](./video) um

**Wert:** Erforderlich — `background_identifier`

> [!NOTE]
> Um die Kennung eines Hintergrunds zu erhalten, klicke mit der rechten Maustaste auf den Editor-Hintergrund und dann auf „Background Identifier kopieren“.

## Layout umschalten (`toggle_layout`)

**Zweck:** Schaltet ein Layout (aktivieren/deaktivieren) über seinen Dateinamen ohne `.txt` um

**Wert:** Erforderlich — `layout_name`

## Layout aktivieren (`enable_layout`)

**Zweck:** Aktiviert und speichert ein Layout über seinen Dateinamen ohne `.txt`

**Wert:** Erforderlich — `layout_name`

## Layout deaktivieren (`disable_layout`)

**Zweck:** Deaktiviert und speichert ein Layout über seinen Dateinamen ohne `.txt`

**Wert:** Erforderlich — `layout_name`

Alle drei Layout-Aktionen speichern den Zustand in der Layout-Datei und aktualisieren den aktuellen Bildschirm sofort. Verwende den Groß-/Kleinschreibung-sensitiven Dateinamen ohne `.txt`.

## Bildschirm oder benutzerdefinierte GUI öffnen (`opengui`)

**Zweck:** Öffnet einen Bildschirm über seine Kennung (Vanilla, Mod oder benutzerdefinierte GUI)

**Wert:** Erforderlich — `screen_identifier`

Kopiere die exakte, Groß-/Kleinschreibung-sensible Kennung aus dem Debug-Overlay [Screen Identifiers](./screen-identifiers).

Einige Mod-Bildschirme können nicht direkt erstellt werden. Wenn das Öffnen fehlschlägt, verwende [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) auf einem Widget, das normalerweise diesen Bildschirm öffnet.

## Bildschirm schließen (`closegui`)

**Zweck:** Schließt den aktiven Bildschirm

**Wert:** Nicht erforderlich

## Bildschirm aktualisieren (`update_screen`)

**Zweck:** Initialisiert den aktuellen Bildschirm neu

**Wert:** Nicht erforderlich

## Zurück zum letzten Bildschirm (`back_to_last_screen`)

**Zweck:** Kehrt zum Elternbildschirm einer [benutzerdefinierten GUI](./custom-guis) oder zur zuletzt geschlossenen Bildschirminstanz zurück

**Wert:** Nicht erforderlich

## Server beitreten (`joinserver`)

**Zweck:** Verbindet den Spieler mit einem Minecraft-Server

**Wert:** Erforderlich — `server_ip` oder `server_ip:port`

Diese Aktion kann nicht ausgeführt werden, während bereits eine Welt oder ein Server geladen ist. Wenn der Port weggelassen wird, wird `25565` verwendet. Wenn die Adresse nicht in Minecrafts gespeicherter Serverliste enthalten ist, fügt FancyMenu sie hinzu und speichert sie.

## Welt betreten (`loadworld`)

**Zweck:** Betritt eine Minecraft-Welt

**Wert:** Erforderlich — `world_folder_name`

Der Wert ist der Name des Speicherordners. Die Aktion hat keine Wirkung, wenn dieser Spielstand nicht existiert oder bereits eine andere Welt/ein anderer Server geladen ist.

## Letzte Welt/letzten Server betreten/joinen (`join_last_world`)

**Zweck:** Betritt/joint die letzte Welt oder den letzten Server, auf dem sich der Spieler befand

**Wert:** Nicht erforderlich

Diese Aktion kann nicht ausgeführt werden, während bereits eine andere Welt/ein anderer Server geladen ist. Ein gespeicherter Server, der nicht in Minecrafts gespeicherter Serverliste enthalten ist, wird vor dem Verbinden hinzugefügt und gespeichert.

## Welt oder Server verlassen (`disconnect_server_or_world`)

**Zweck:** Verlässt eine Welt oder einen Server und öffnet einen angegebenen Bildschirm

**Wert:** Erforderlich — `screen_identifier`

Diese Aktion wird nur ausgeführt, während eine Welt und ein Spieler geladen sind. Das Ziel kann eine Kennung einer [benutzerdefinierten GUI](./custom-guis) oder eine von FancyMenu konstruierbare [Bildschirmkennung](./screen-identifiers) sein. Wenn das Ziel nicht geöffnet werden kann, kehrt FancyMenu zum Titelbildschirm zurück.

## Minecraft beenden (`quitgame`)

**Zweck:** Beendet Minecraft vollständig

**Wert:** Nicht erforderlich

## Chatnachricht/Befehl senden (`sendmessage`)

**Zweck:** Sendet eine Chatnachricht oder führt einen Chatbefehl aus. Nachrichtentext unterstützt [FancyMenu-Formatierungscodes](./text-formatting#minecraft-text-formatting).

**Wert:** Erforderlich — `message_text` oder `/command_text`

## Befehl als integrierten Server ausführen (`execute_command_as_integrated_server`)

**Zweck:** Führt einen Befehl im Einzelspieler als integrierten Server erzwungen aus und ignoriert dabei Berechtigungen und die Cheat-Einstellung.

**Wert:** Erforderlich — Befehlstext, zum Beispiel `/give @p minecraft:diamond 1`

> [!WARNING]
> Diese Aktion funktioniert nur im Einzelspieler, solange die Welt **nicht für LAN geöffnet** ist. Sie tut absichtlich nichts, wenn kein integrierter Server existiert oder wenn der integrierte Server für LAN freigegeben ist.

## In den Chat einfügen (`paste_to_chat`)

**Zweck:** Fügt formatierten Text in das Chat-Eingabefeld ein, während ein Spieler/eine Welt geladen ist

**Wert:** Erforderlich — `true:Text` oder `false:Text`

Wenn der Chat nicht bereits offen ist, öffnet FancyMenu ihn und setzt den Eingabetext. Wenn der Chat bereits offen ist, fügt `true` an den vorhandenen Inhalt an und `false` ersetzt ihn.

## Im Chat anzeigen [Client-seitig] (`display_in_chat_client_side`)

**Zweck:** Zeigt eine clientseitige Chatnachricht an, während eine Welt oder ein Server geladen ist. Es wird nichts an den Server gesendet.

**Wert:** Erforderlich — `text_or_json`

Der Wert kann reiner Text oder eine serialisierte Minecraft-Textkomponente sein. Die Aktion hat keine Wirkung, wenn keine Welt geladen ist.

## FM-Daten an Server senden (`send_fm_data_to_server`)

**Zweck:** Sendet [FM-Daten](./fm-data) an den aktuellen FancyMenu-Server.

**Wert:** Erforderlich — `data_identifier||data`

## Mit Remote-Server verbinden (`connect_to_remote_server`)

**Zweck:** Öffnet oder verwendet erneut eine vom Client initiierte WebSocket-Verbindung zu einem externen Remote-Server.

**Wert:** Erforderlich — URL des Remote-Servers, zum Beispiel `wss://example.com/ws`

Siehe [Remote Server Communication](./remote-server-communication#url-modes) für zulässige URL-Formen.

## Daten an Remote-Server senden (`send_data_to_remote_server`)

**Zweck:** Öffnet oder verwendet erneut eine Remote-Server-Verbindung und sendet Textdaten dorthin.

**Wert:** Erforderlich — `remote_server_url||data`

## Verbindung zu Remote-Server schließen (`close_remote_server_connection`)

**Zweck:** Schließt eine bestimmte Remote-Server-Verbindung anhand der Request-ID.

**Wert:** Erforderlich — Request-ID, normalerweise `$$request_id` aus [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected)

## Alle Remote-Server-Verbindungen schließen (`close_all_remote_server_connections`)

**Zweck:** Schließt alle aktiven, von FancyMenu geöffneten Remote-Server-Verbindungen.

**Wert:** Nicht erforderlich

## URL im Browser öffnen (`openlink`)

**Zweck:** Übergibt eine URL an den Standard-Handler des Betriebssystems, ohne eine FancyMenu-Bestätigungsabfrage anzuzeigen

**Wert:** Erforderlich — `https://example.com`

Verwende vertrauenswürdige `https://`-Links. FancyMenu zeigt keine Bestätigungsabfrage an, bevor die URL an das Betriebssystem übergeben wird.

## Text in Zwischenablage kopieren (`copytoclipboard`)

**Zweck:** Kopiert Text in die Zwischenablage

**Wert:** Erforderlich — `text_to_copy`

## In das Spielprotokoll schreiben (`print_to_log`)

**Zweck:** Schreibt eine Zeile in das Spielprotokoll

**Wert:** Erforderlich — `text_to_log`

## Variablenwert setzen (FM-Variable) (`set_variable`)

**Zweck:** Speichert Textinhalt in einer [FancyMenu-Variable](./variables)

**Wert:** Erforderlich — `variable_name:variable_value`

Der erste Doppelpunkt trennt den Namen vom Wert. Spätere Doppelpunkte bleiben Teil des Werts. Änderungen werden sofort gespeichert.

## Alle Variablen löschen (FM-Variable) (`clear_variables`)

**Zweck:** Löscht alle gespeicherten Werte von [FancyMenu-Variablen](./variables)

**Wert:** Nicht erforderlich

## HTTP-Anfrage senden (`send_http_request`)

**Zweck:** Startet im Hintergrund eine HTTP/HTTPS-Anfrage; kann die Antwort protokollieren und/oder in einer Variable speichern

**Wert:** Erforderlich — HTTP-Anfragekonfiguration

| Einstellung | Verhalten |
|---|---|
| URL | HTTP- oder HTTPS-Endpunkt |
| Methode | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` oder `OPTIONS` |
| Body | Wird für Methoden außer `GET` und `HEAD` gesendet |
| Content type | `Content-Type`-Wert der Anfrage |
| Timeout | Sekunden für Verbindungs- und Antwortlesezeit |
| Log response | Liest die Antwort und schreibt sie ins Protokoll |
| Response variable | Liest die Antwort und speichert sie nach Abschluss der Anfrage |
| Single-line response | Entfernt Zeilenumbrüche der Antwort vor dem Speichern |
| Authentication | Keine, Basic, Bearer oder API-Schlüssel |
| Headers | Optionale benutzerdefinierte Request-Header |

Anfragen werden asynchron ausgeführt, daher wartet die nächste Aktion nicht. Antwortkörper werden nur gelesen, wenn die Protokollierung aktiviert ist oder eine Antwortvariable konfiguriert wurde; Fehlerantworten werden als Nicht-Erfolgs-Antwort gelesen. Speichere keine Passwörter oder Zugriffstoken in der Aktionskonfiguration.

## Ressourcenpaket verwalten (`manage_resource_pack`)

**Zweck:** Aktiviert, deaktiviert oder schaltet ein Ressourcenpaket um, optional mit Neuladen

**Wert:** Erforderlich — `pack_name_or_id|||MODE|||reload_bool`

Anzeigenamen und interne Paket-IDs werden ohne Beachtung der Groß-/Kleinschreibung verglichen. Als erforderlich markierte Pakete können nicht deaktiviert werden.

## Ressourcenpakete neu laden (`reload_resource_packs`)

**Zweck:** Lädt Minecrafts Ressourcenpakete neu. Eine eingebaute fünfsekündige Abklingzeit ignoriert wiederholte Auslöser während dieses Zeitraums, um Reload-Spam zu verhindern.

**Wert:** Nicht erforderlich

## FancyMenu neu laden (`reloadmenu`)

**Zweck:** Lädt Layouts, [benutzerdefinierte GUIs](./custom-guis), [Panoramen](./panoramas), [Diashows](./slideshows), Einstellungen und von FancyMenu verwaltete Ressourcen neu

**Wert:** Nicht erforderlich

Dies lädt Minecraft-Ressourcenpakete nicht neu. Verwende dafür [**Ressourcenpakete neu laden**](#ressourcenpakete-neu-laden-reload_resource_packs).

> [!WARNING]
> Das Neuladen ist teuer. Triggere es über eine bewusste Button-Aktion, nicht über einen [Ticker](./elements#ticker) oder einen häufig ausgelösten [Listener](./listeners).

## Element-Animator umschalten (`toggle_element_animator`)

**Zweck:** Schaltet den gespeicherten Wiedergabestatus um und setzt die passende aktive Animator-Zeitleiste zurück

**Wert:** Erforderlich — `animator_identifier`

Siehe [Element Animator](./element-animator) für Einrichtung und Kennungsdetails.

## Element-Animator aktivieren (`enable_element_animator`)

**Zweck:** Aktiviert die Wiedergabe; eine aktive Animator-Zeitleiste wird nur zurückgesetzt, wenn der Status von deaktiviert zu aktiviert wechselt

**Wert:** Erforderlich — `animator_identifier`

## Element-Animator deaktivieren (`disable_element_animator`)

**Zweck:** Deaktiviert die Wiedergabe und setzt die passende aktive Animator-Zeitleiste zurück

**Wert:** Erforderlich — `animator_identifier`

## Element-Animator zurücksetzen (`reset_element_animator`)

**Zweck:** Setzt die passende aktive Animator-Zeitleiste zurück, ohne zu ändern, ob die Wiedergabe aktiviert ist

**Wert:** Erforderlich — `animator_identifier`

## Vanilla-/Mod-Button nachahmen (`mimicbutton`)

**Zweck:** Imitiert die Klickaktion eines Vanilla- oder Mod-Buttons

**Wert:** Erforderlich — der vollständige [Widget-Locator](./widget-locators), zum Beispiel `example.menu.identifier:505280`

## Tastenkürzel nachahmen (`mimic_keybind`)

**Zweck:** Führt eine Minecraft-Tastatur- oder Maus-Tastenbelegung aus, optional mit gedrücktem Halten

**Wert:** Erforderlich — `keybind_id|||keep_pressed_bool|||duration_ms`

| Feld | Bedeutung |
|---|---|
| `keybind_id` | Minecraft-Keybind-Kennung, etwa `key.jump` |
| `keep_pressed_bool` | `true`, um die Taste zu halten; `false` für einen normalen Druck |
| `duration_ms` | Haltedauer, wenn `keep_pressed_bool` `true` ist; Standard ist `1000` |

## Wert eines Texteingabefelds setzen (`set_text_input_field_value`)

**Zweck:** Setzt den Wert eines benutzerdefinierten oder Vanilla-[Texteingabefelds](./elements#text-input-field) anhand der Elementkennung.

**Wert:** Erforderlich — `element_identifier|||new_value|||force_set_when_inactive`

Die drei Felder müssen mit dem Triple-Pipe-Trennzeichen `|||` getrennt werden. Setze `force_set_when_inactive` auf `true`, um auch ein deaktiviertes Eingabefeld zu aktualisieren; wenn es `false` ist, bleiben inaktive Felder unverändert.

## Datei im Spielverzeichnis erstellen (`create_file_in_game_dir`)

**Zweck:** Erstellt eine leere Datei relativ zum aktiven Spielverzeichnis. Akzeptiert das Präfix `.minecraft/`, um das herkömmliche Minecraft-Verzeichnis anzusprechen (das vom aktuellen Instanzverzeichnis abweichen kann).

**Wert:** Erforderlich — `file_path`

Beispiel: `config/some_mod_folder/new_file.txt`. Fehlende übergeordnete Verzeichnisse werden erstellt; eine vorhandene Datei bleibt unverändert.

## Datei/Ordner im Spielverzeichnis löschen (`delete_file_in_game_dir`)

**Zweck:** Löscht eine Datei oder löscht einen Ordner rekursiv relativ zum aktiven Spielverzeichnis. Akzeptiert `.minecraft/`, um das herkömmliche Minecraft-Verzeichnis anzusprechen. Füge `*` an, um **alle Dateien direkt in** einem Ordner zu löschen (ignoriert Unterverzeichnisse und lässt den Ordner bestehen).

**Wert:** Erforderlich — `target_path`

Zum Beispiel löscht `config/downloads/*` die Dateien direkt in `config/downloads/`, durchläuft aber weder Unterverzeichnisse noch löscht es diese.

## Datei/Ordner im Spielverzeichnis kopieren (`copy_file_in_game_dir`)

**Zweck:** Kopiert innerhalb des aktiven Spielverzeichnisses; `.minecraft/` zielt auf das herkömmliche Minecraft-Verzeichnis. Ein benannter Ordner wird rekursiv kopiert. Füge `*` an den **Quellpfad** an, um nur alle direkten Kinddateien zu kopieren; das Ziel muss ein Verzeichnis sein und darf kein `*` verwenden.

**Wert:** Erforderlich — `source||destination`

Zum Beispiel kopiert `config/source/*||config/destination/` nur die Dateien direkt in `config/source/`. Bei einer Wildcard-Quelle erstellt FancyMenu das Zielverzeichnis bei Bedarf, kopiert aber keine Quell-Unterverzeichnisse. Das Kopieren lehnt vorhandene Ziel-/Konfliktdaten statt Überschreiben ab.

## Datei/Ordner im Spielverzeichnis verschieben (`move_file_in_game_dir`)

**Zweck:** Verschiebt innerhalb des aktiven Spielverzeichnisses; `.minecraft/` zielt auf das herkömmliche Minecraft-Verzeichnis. Füge `*` an den **Quellpfad** an, um nur alle direkten Kinddateien zu verschieben; das Ziel muss ein Verzeichnis sein und darf kein `*` verwenden.

**Wert:** Erforderlich — `source||destination`

Zum Beispiel verschiebt `config/source/*||config/destination/` nur die Dateien direkt in `config/source/`. Bei einer Wildcard-Quelle erstellt FancyMenu das Zielverzeichnis bei Bedarf, lässt aber Quell-Unterverzeichnisse bestehen. Das Verschieben lehnt vorhandene Ziel-/Konfliktdaten statt Überschreiben ab.

## Datei/Ordner im Spielverzeichnis umbenennen (`rename_file_in_game_dir`)

**Zweck:** Benennt eine Datei oder einen Ordner innerhalb seines aktuellen Elternverzeichnisses um; `.minecraft/` zielt auf das herkömmliche Minecraft-Verzeichnis. Behält den Inhalt bei und lehnt einen bereits vorhandenen Zieldateinamen ab.

**Wert:** Erforderlich — `path||new_name`

## Datei in das Spielverzeichnis herunterladen (`download_file_to_game_dir`)

**Zweck:** Lädt im Hintergrund eine Datei in ein Verzeichnis relativ zum aktiven Spielverzeichnis herunter; `.minecraft/` zielt auf das herkömmliche Minecraft-Verzeichnis.

**Wert:** Erforderlich — `url||target_folder`

Das zweite Feld ist ein **Zielverzeichnis**, nicht ein vollständiger Zieldateipfad. FancyMenu erstellt das Verzeichnis bei Bedarf und bestimmt den Dateinamen aus dem `Content-Disposition`-Header der Antwort und weicht dann auf den URL-Pfad aus. Der aufgelöste Name wird vor der Verwendung URL-dekodiert und bereinigt; wenn keine Quelle einen verwendbaren Namen liefert, erzeugt FancyMenu einen. Eine vorhandene Datei mit demselben Namen wird überschrieben.

Der [**On File Downloaded via Action**-Listener](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) wird nach erfolgreichen und fehlgeschlagenen Downloadversuchen ausgelöst und stellt die URL, den aufgelösten Zielpfad und den Erfolgsstatus bereit.

Bei Erfolg ist `$$target_file_path` der gespeicherte Dateipfad. Bei Fehlschlag kann es nur das Zielverzeichnis enthalten, da kein endgültiger Dateiname aufgelöst wurde.

## ZIP-Datei im Spielverzeichnis extrahieren (`extract_zip_file_in_game_dir`)

**Zweck:** Extrahiert ein ZIP in einen Zielordner innerhalb des aktiven Spielverzeichnisses oder des herkömmlichen `.minecraft`-Verzeichnisses. Löst [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) aus, wenn fertig.

**Wert:** Erforderlich — `source_zip_path||target_folder_path`

Vorhandene Dateien mit übereinstimmenden Namen werden ersetzt. Extrahiere nur vertrauenswürdige ZIP-Dateien.

## Datei/Ordner im Spielverzeichnis öffnen (`open_file_folder_in_game_dir`)

**Zweck:** Öffnet eine Datei oder einen Ordner mit der Standardanwendung des Betriebssystems. Das Ziel muss aus Sicherheitsgründen innerhalb des Spielverzeichnisses oder des Standard-`.minecraft`-Verzeichnisses bleiben.

**Wert:** Erforderlich — `target_path`

## Datei im Spielverzeichnis schreiben (`write_file_in_game_dir`)

**Zweck:** Schreibt oder hängt Text relativ zum aktiven Spielverzeichnis an; `.minecraft/` zielt auf das herkömmliche Minecraft-Verzeichnis. Erstellt die Datei und übergeordnete Ordner, falls sie fehlen. `\n` fügt Zeilenumbrüche ein; `append_bool=false` ersetzt eine vorhandene Datei.

**Wert:** Erforderlich — `path|||content|||append_bool`

## Datei vom System auswählen (`select_file_to_game_dir`)

**Zweck:** Öffnet einen nativen Dateiauswahldialog und kopiert die ausgewählte Datei ins aktive Spielverzeichnis oder bei Präfix `.minecraft/` in das herkömmliche Verzeichnis. Unterstützt Erweiterungsfilter, ein benutzerdefiniertes Filterlabel und einen Überschreibungs-Schalter.

**Wert:** Erforderlich — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` ist der vollständige Zieldateipfad. Trenne mehrere Erweiterungen mit `;` oder `,`, zum Beispiel `png;jpg`; eine leere Erweiterungsliste erlaubt alle Dateien. Wenn `overwrite_bool` `false` ist, schlägt die Aktion fehl, anstatt eine vorhandene Zieldatei zu ersetzen.

Der [**On File Selected**-Listener](./listeners#on-file-selected-file_selected_via_action) wird ausgelöst, wenn die Datei kopiert wurde, der Dialog abgebrochen wurde oder die Auswahl fehlgeschlagen ist. Er stellt den ausgewählten Pfad, den aufgelösten Zielpfad, Erfolgs-/Abbruchstatus und einen Fehlergrund bereit.

## Toast anzeigen (`show_toast`)

**Zweck:** Zeigt eine konfigurierbare Toast-Benachrichtigung an

**Wert:** Erforderlich — JSON-Toast-Konfiguration

Der Editor speichert diese Aktion als JSON. Verwende nach Möglichkeit das Konfigurationsfenster statt den Wert manuell zu bearbeiten.

| Feld | Bedeutung |
|---|---|
| `width` | Auf `120`–`320` Pixel begrenzt |
| `durationMs` | Auf `1000`–`600000` Millisekunden begrenzt |
| `title` | Reiner Text, eine serialisierte Minecraft-Textkomponente oder leer |
| `message` | Reiner Text, eine serialisierte Textkomponente oder leer |
| `iconSource` | Optionale [Bildquelle](./resources) |
| `backgroundSource` | Optionale [Bildquelle](./resources) |

## Scheduler starten (`start_scheduler`)

**Zweck:** Startet einen Scheduler über seine Scheduler-ID.

**Wert:** Erforderlich — `scheduler_id`

Siehe [Schedulers](./schedulers) zum Erstellen und Verwalten von Scheduler-IDs.

## Scheduler stoppen (`stop_scheduler`)

**Zweck:** Stoppt einen Scheduler über seine Scheduler-ID.

**Wert:** Erforderlich — `scheduler_id`

## Minecraft-Option setzen (`edit_minecraft_option`)

**Zweck:** Bearbeitet eine Minecraft-Konfigurationsoption

**Wert:** Erforderlich — `option_name:set_to_value`
