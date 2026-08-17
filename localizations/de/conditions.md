---
title: Bedingungen (Anforderungen)
description: So verwendest du Ladeanforderungen.
---
# Anforderungen

Anforderungen (in manchen Menüs **Ladeanforderungen** genannt) zeigen Inhalte abhängig von Bedingungen wie dem Hover-Zustand, der Fenstergröße oder davon, ob eine Welt geladen ist, an oder blenden sie aus.

Du kannst sie auf [Elemente](./elements), ganze Layouts und [Aktionsskripte](./action-scripts) anwenden.

# Anforderungen zu Elementen hinzufügen

Um einem Element Anforderungen hinzuzufügen, klicke mit der rechten Maustaste darauf und wähle **Ladeanforderungen**.

Anforderungen werden geprüft, solange das Menü geöffnet ist. Daher werden Elemente aktualisiert, sobald sich eine Bedingung ändert.

# Layoutweite Anforderungen

Du kannst auch die Sichtbarkeit ganzer Layouts ändern, indem du mit der rechten Maustaste auf den **Editor-Hintergrund** klickst und anschließend **Ladeanforderungen [Layoutweit]** auswählst.

Wenn sich das Ergebnis einer layoutweiten Anforderung ändert, erstellt FancyMenu den aktuellen Bildschirm neu und wendet die Layouts an, deren Anforderungen nun erfüllt sind.

# Aktionsskripte

Anforderungen können auch in Aktionsskripten verwendet werden.
Du kannst sie im Editor für Aktionsskripte hinzufügen und damit bestimmte Aktionen nur ausführen, wenn die Bedingung der Anforderung erfüllt ist.

# Anforderungen kombinieren

- Anforderungen außerhalb von Gruppen verwenden **UND**; daher müssen alle erfüllt sein.
- Innerhalb einer Gruppe kannst du **UND** oder **ODER** auswählen.
- Verwende **WENN NICHT**, um eine einzelne Anforderung umzukehren.

Diese Regeln gelten gleichermaßen für Elemente, Layouts und Aktionsskripte.

# Anforderungswerte

Für Anforderungen, die einen Wert benötigen, verwende **Anforderungswert bearbeiten** und befolge die im Editor angezeigte Beschreibung. Einige Felder unterstützen die Vervollständigung per **TAB**.

Wenn eine importierte Anforderung nach einer Änderung von FancyMenu oder Add-ons nicht mehr funktioniert, bearbeite sie im Anforderungsbildschirm und überprüfe `logs/latest.log` auf Fehler.

Der Anforderungseditor unterstützt ein Kontextmenü per Rechtsklick, Tastaturnavigation, Suche, Rückgängig/Wiederholen (`Strg/Command + Z` / `Strg/Command + Y`) sowie `Strg/Command + S` zum Speichern.

# Anforderungen im Detail

In diesem Abschnitt werden die integrierten Anforderungen von FancyMenu aufgelistet.

## Ist ein Element im Hover-Zustand (`fancymenu_visibility_requirement_is_element_hovered`)

**Zweck:** Prüft, ob sich der Mauszeiger über einem bestimmten Element befindet.

**Wert:** Erforderlich – [Elementkennung](./element-identifiers) des Zielelements (z. B. `some_element_ID`).

## Hat ein Element den Fokus (`is_element_focused`)

**Zweck:** Prüft, ob ein bestimmtes Element derzeit den Tastaturfokus besitzt (zum Beispiel ein Textfeld oder eine fokussierte Schaltfläche).

**Wert:** Erforderlich – Element-ID des Zielelements (dieselbe ID, die im Editor angezeigt wird)

> [!NOTE]
> Fokus und Hover sind unterschiedliche Zustände. Ein Element kann sein fokussiertes Aussehen behalten, nachdem der Mauszeiger es verlassen hat; durch Klicken oder Tastaturnavigation kann es den Fokus erhalten.

## Ist ein beliebiges Element im Hover-Zustand (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Zweck:** Prüft sichtbare/renderbare Elemente in der aktuell aktiven Anpassungsebene, einschließlich Elementen aus gestapelten Layouts.

**Wert:** Nicht erforderlich

## Ist eine beliebige Schaltfläche im Hover-Zustand (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Zweck:** Prüft, ob sich der Mauszeiger über einer sichtbaren/renderbaren Vanilla- oder benutzerdefinierten Schaltfläche in der aktuell aktiven Anpassungsebene befindet, einschließlich Schaltflächen aus gestapelten Layouts.

**Wert:** Nicht erforderlich

## Ist ein Layout aktiviert (`fancymenu_visibility_requirement_is_layout_enabled`)

**Zweck:** Prüft, ob ein bestimmtes Layout derzeit aktiviert ist.

**Wert:** Erforderlich – Name des Layouts (z. B. `my_cool_main_menu_layout`)

## Läuft ein Scheduler (`fancymenu_visibility_requirement_is_scheduler_running`)

**Zweck:** Prüft, ob derzeit ein [Scheduler](./schedulers) läuft.

**Wert:** Erforderlich – Scheduler-ID (z. B. `my_scheduler`)

## Ist die GUI-Skalierung (`fancymenu_loading_requirement_is_gui_scale`)

**Zweck:** Prüft, ob die aktuelle GUI-Skalierung bestimmte Bedingungen erfüllt.

**Wert:** Erforderlich – Verwende eine Zahl für Gleichheit, `>` für größer als oder `<` für kleiner als.

Mehrere durch Kommas getrennte Bedingungen werden mit UND verknüpft. Beispielsweise ist `>1,<4` nur erfüllt, wenn die GUI-Skalierung größer als `1` und kleiner als `4` ist.

## Ist eine Schaltfläche aktiv (`fancymenu_visibility_requirement_is_button_active`)

**Zweck:** Prüft, ob eine bestimmte Schaltfläche aktiv (anklickbar) ist.

**Wert:** Erforderlich – Element-ID der Zielschaltfläche (z. B. "some_element_ID")

## Ist der Bildschirmtitel (`is_menu_title`)

**Zweck:** Prüft, ob der ANGEZEIGTE Titel des Bildschirms mit einem bestimmten Text oder Lokalisierungsschlüssel übereinstimmt. Es wird nur der Anzeigename/Titel des Bildschirms geprüft, etwa "Optionen" oder "Pause". Die Menü-/Bildschirmkennung (wie `title_screen`) wird NICHT geprüft!

**Wert:** Erforderlich – Exakter Titeltext oder Lokalisierungsschlüssel des Bildschirms

## Ist eine Taste gedrückt (`is_key_pressed`)

**Zweck:** Prüft, ob derzeit eine bestimmte Tastaturtaste gedrückt wird.

**Wert:** Erforderlich – Tastencode der Zieltaste. Bei der Bearbeitung des Anforderungswerts wird dieser über eine Benutzeroberfläche ausgewählt.

## Ist irgendein Bildschirm geöffnet (`is_any_screen_open`)

**Zweck:** Prüft, ob derzeit ein beliebiger Bildschirm/ein Menü geöffnet ist (gibt „false“ zurück, wenn kein Bildschirm angezeigt wird).

**Wert:** Nicht erforderlich

## Ist die MC-Debuganzeige aktiviert (`is_debug_overlay_enabled`)

**Zweck:** Prüft, ob die F3-Debuganzeige derzeit sichtbar ist.

**Wert:** Nicht erforderlich

## Ist der aktive Cursortyp (`is_active_cursor_type`)

**Zweck:** Prüft, ob der derzeit aktive Cursortyp von FancyMenu einem bestimmten Standard-Cursortyp entspricht.

**Wert:** Erforderlich – Cursortyp: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` oder `not_allowed`

## Ist die Anpassungsmenüleiste sichtbar (`is_customization_menu_bar_visible`)

**Zweck:** Prüft, ob die Anpassungsmenüleiste von FancyMenu derzeit sichtbar ist.

**Wert:** Nicht erforderlich

## Ist der Modpack-Modus aktiviert (`is_modpack_mode_enabled`)

**Zweck:** Prüft, ob der Modpack-Modus von FancyMenu aktiviert ist.

**Wert:** Nicht erforderlich

## Ist die Maustaste gedrückt (`mouse_click`)

**Zweck:** Gibt „true“ zurück, solange eine bestimmte Maustaste gedrückt gehalten wird. Dies ist kein einmaliges Klickereignis. Verwende den [Listener **Bei Maustastenklick**](./listeners#on-mouse-button-clicked-mouse_button_clicked), wenn eine Aktion einmal pro Klick ausgeführt werden soll.

**Wert:** Erforderlich – `left` oder `right`, um die zu prüfende Maustaste anzugeben

## Ist der Vollbildmodus aktiv (`fancymenu_loading_requirement_is_fullscreen`)

**Zweck:** Prüft, ob sich das Spiel derzeit im Vollbildmodus befindet.

**Wert:** Nicht erforderlich

## Ist die Fensterbreite (`fancymenu_loading_requirement_is_window_width`)

**Zweck:** Prüft, ob die Breite des Spielfensters bestimmten Werten entspricht.

**Wert:** Erforderlich – Fensterbreite in Pixeln (z. B. "1920"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist die Fensterhöhe (`fancymenu_loading_requirement_is_window_height`)

**Zweck:** Prüft, ob die Höhe des Spielfensters bestimmten Werten entspricht.

**Wert:** Erforderlich – Fensterhöhe in Pixeln (z. B. "1080"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist die Fensterbreite größer als (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Zweck:** Prüft, ob die Breite des Spielfensters größer als ein bestimmter Wert ist.

**Wert:** Erforderlich – Fensterbreite in Pixeln (z. B. "1920")

## Ist die Fensterhöhe größer als (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Zweck:** Prüft, ob die Höhe des Spielfensters größer als ein bestimmter Wert ist.

**Wert:** Erforderlich – Fensterhöhe in Pixeln (z. B. "1080")

## Ist Mehrspieler aktiv (`fancymenu_loading_requirement_is_multiplayer`)

**Zweck:** Prüft, ob sich der Spieler derzeit in einer Mehrspielerwelt befindet.

**Wert:** Nicht erforderlich

## Ist Einzelspieler aktiv (`fancymenu_loading_requirement_is_singpleplayer`)

**Zweck:** Prüft, ob sich der Spieler derzeit in einer Einzelspielerwelt befindet.

**Wert:** Nicht erforderlich

## Ist eine Welt geladen (`fancymenu_loading_requirement_is_world_loaded`)

**Zweck:** Prüft, ob derzeit eine Welt geladen ist.

**Wert:** Nicht erforderlich

## Ist der Spielmodus Abenteuer (`fancymenu_visibility_requirement_is_adventure`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Abenteuerspielmodus befindet.

**Wert:** Nicht erforderlich

## Ist der Spielmodus Kreativ (`fancymenu_visibility_requirement_is_creative`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Kreativspielmodus befindet.

**Wert:** Nicht erforderlich

## Ist der Spielmodus Zuschauer (`fancymenu_visibility_requirement_is_spectator`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Zuschauerspielmodus befindet.

**Wert:** Nicht erforderlich

## Ist der Spielmodus Überleben (`fancymenu_visibility_requirement_is_survival`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Überlebensspielmodus befindet.

**Wert:** Nicht erforderlich

## Ist der Spielmodus (`is_gamemode`)

**Zweck:** Prüft, ob sich der Spieler in einem bestimmten Spielmodus befindet.

**Wert:** Erforderlich – Name des Spielmodus (z. B. "creative", "survival", "adventure", "spectator")

## Ist der Schwierigkeitsgrad (`is_difficulty`)

**Zweck:** Prüft, ob der aktuelle Schwierigkeitsgrad einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Name des Schwierigkeitsgrads (z. B. "peaceful", "easy", "normal", "hard")

## Ist Hardcore aktiv (`is_hardcore`)

**Zweck:** Prüft, ob sich die aktuell geladene Welt im Hardcore-Modus befindet.

**Wert:** Nicht erforderlich

## Ist die Kameraperspektive (`is_camera_perspective`)

**Zweck:** Prüft, ob die aktuelle Kameraperspektive einer bestimmten Perspektive entspricht.

**Wert:** Erforderlich – `first_person`, `third_person_back` oder `third_person_front`

## Regnet es (`is_raining`)

**Zweck:** Prüft, ob es am Standort des Spielers derzeit regnet.

**Wert:** Nicht erforderlich

## Gibt es ein Gewitter (`is_thundering`)

**Zweck:** Prüft, ob in der Welt des Spielers derzeit ein Gewitter herrscht.

**Wert:** Nicht erforderlich

## Ist das Wetter klar (`is_clear_weather`)

**Zweck:** Prüft, ob das Wetter derzeit klar ist (kein Regen und kein Gewitter).

**Wert:** Nicht erforderlich

## Schneit es (`is_snowing`)

**Zweck:** Prüft, ob es am Standort des Spielers derzeit schneit.

**Wert:** Nicht erforderlich

## Rennt der Spieler (`is_player_running`)

**Zweck:** Prüft, ob der Spieler derzeit sprintet.

**Wert:** Nicht erforderlich

## Schleicht der Spieler (`is_player_sneaking`)

**Zweck:** Prüft, ob der Spieler derzeit schleicht/sich duckt.

**Wert:** Nicht erforderlich

## Benutzt der Spieler einen Gegenstand (`is_player_using_item`)

**Zweck:** Prüft, ob der Spieler derzeit einen Gegenstand benutzt.

**Wert:** Nicht erforderlich

## Schwimmt der Spieler (`is_player_swimming`)

**Zweck:** Prüft, ob der Spieler derzeit schwimmt.

**Wert:** Nicht erforderlich

## Springt oder fällt der Spieler (`is_player_jumping`)

**Zweck:** Gibt „true“ zurück, solange sich der Spieler bei einem normalen Sprung- oder Fallzustand in der Luft befindet. Schwimmen, Flüssigkeiten, Elytrenflug, Schlafen, visuelles Schwimmen und Kriechen werden ausgeschlossen.

**Wert:** Nicht erforderlich

## Ist der Spieler unter Wasser (`is_player_under_water`)

**Zweck:** Prüft, ob der Spieler vollständig unter Wasser ist.

**Wert:** Nicht erforderlich

## Ist der Spieler im Wasser (`is_player_in_water`)

**Zweck:** Prüft, ob sich der Spieler im Wasser befindet (er kann teilweise untergetaucht sein).

**Wert:** Nicht erforderlich

## Ist der Spieler in Lava (`is_player_in_lava`)

**Zweck:** Prüft, ob sich der Spieler in Lava befindet.

**Wert:** Nicht erforderlich

## Ist der Spieler in einer Flüssigkeit (`is_player_in_fluid`)

**Zweck:** Prüft, ob sich der Spieler in einer beliebigen Flüssigkeit befindet (Wasser, Lava usw.).

**Wert:** Nicht erforderlich

## Reitet der Spieler ein Wesen/Fahrzeug (`is_player_riding_entity`)

**Zweck:** Prüft, ob der Spieler ein beliebiges Wesen reitet.

**Wert:** Nicht erforderlich

## Reitet der Spieler ein springfähiges Wesen (`is_player_riding_jumpable_entity`)

**Zweck:** Prüft, ob der Spieler ein Wesen reitet, das springen kann (z. B. ein Pferd).

**Wert:** Nicht erforderlich

## Reitet der Spieler ein Wesen mit Lebenspunkten (`is_player_riding_entity_with_health`)

**Zweck:** Prüft, ob der Spieler ein lebendes Wesen mit Lebenspunkten reitet (z. B. Tiere, aber keine Boote).

**Wert:** Nicht erforderlich

## Befindet sich der Spieler in Pulverschnee (`is_player_in_powder_snow`)

**Zweck:** Prüft, ob sich der Spieler derzeit in Pulverschnee befindet.

**Wert:** Nicht erforderlich

## War der Spieler in Pulverschnee (`was_player_in_powder_snow`)

**Zweck:** Prüft, ob sich der Spieler in Pulverschnee befand (wird für Effekte verwendet, die nach dem Verlassen bestehen bleiben).

**Wert:** Nicht erforderlich

## Trägt der Spieler einen Kürbis (`is_player_wearing_pumpkin`)

**Zweck:** Prüft, ob der Spieler einen geschnitzten Kürbis auf dem Kopf trägt.

**Wert:** Nicht erforderlich

## Fliegt der Spieler mit einer Elytra (`is_player_flying_with_elytra`)

**Zweck:** Prüft, ob der Spieler derzeit mit einer Elytra fliegt.

**Wert:** Nicht erforderlich

## Fliegt der Spieler im Kreativmodus (`is_player_creative_flying`)

**Zweck:** Prüft, ob der Spieler im Kreativmodus fliegt.

**Wert:** Nicht erforderlich

## Hat der Spieler Absorptionsherzen (`has_player_absorption_hearts`)

**Zweck:** Prüft, ob der Spieler Absorptionsherzen (goldene Herzen) besitzt.

**Wert:** Nicht erforderlich

## Ist der Spieler verwelkt (`is_player_withered`)

**Zweck:** Prüft, ob der Spieler vom Wither-Effekt betroffen ist.

**Wert:** Nicht erforderlich

## Ist der Spieler vollständig eingefroren (`is_player_fully_frozen`)

**Zweck:** Prüft, ob der Spieler vollständig eingefroren ist (normalerweise durch Pulverschnee).

**Wert:** Nicht erforderlich

## Ist der Spieler vergiftet (`is_player_poisoned`)

**Zweck:** Prüft, ob der Spieler vom Vergiftungseffekt betroffen ist.

**Wert:** Nicht erforderlich

## Befindet sich der Spieler in einem Biom (`is_player_in_biome`)

**Zweck:** Prüft, ob sich der Spieler in einem bestimmten Biom befindet.

**Wert:** Erforderlich – Biomkennung (z. B. `minecraft:birch_forest`)

## Befindet sich der Spieler in einer Dimension (`is_player_in_dimension`)

**Zweck:** Prüft, ob sich der Spieler in einer bestimmten Dimension befindet.

**Wert:** Erforderlich – Dimensionskennung (z. B. `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Befindet sich der Spieler in einer Struktur (`is_player_in_structure`)

**Zweck:** Prüft, ob sich der Spieler derzeit innerhalb einer bestimmten Struktur befindet. Für Serverwelten muss FancyMenu auf dem Server installiert sein.

**Wert:** Erforderlich – Strukturerkennung (z. B. `minecraft:village`)

## Befindet sich ein Wesen in der Nähe (`is_entity_nearby`)

**Zweck:** Prüft, ob sich ein bestimmter Wesenstyp in einem bestimmten Radius um den Spieler befindet.

**Wert:** Erforderlich – Format: "radius:entity_id" (z. B. `10:minecraft:pig` – prüft, ob sich Schweine innerhalb von 10 Blöcken befinden)

## Ist ein Effekt aktiv (`is_effect_active`)

**Zweck:** Prüft, ob ein bestimmter Trankeffekt beim Spieler aktiv ist.

**Wert:** Erforderlich – Effektkennung (z. B. `minecraft:speed`, `minecraft:strength`)

## Ist irgendein Effekt aktiv (`is_any_effect_active`)

**Zweck:** Prüft, ob beim Spieler irgendein Trankeffekt aktiv ist.

**Wert:** Nicht erforderlich

## Ist der Spieler Linkshänder (`is_left_handed`)

**Zweck:** Prüft, ob der Spieler in den Spieloptionen auf Linkshänder eingestellt ist.

**Wert:** Nicht erforderlich

## Ist ein Inventarplatz belegt (`is_inventory_slot_filled`)

**Zweck:** Prüft, ob ein bestimmter Inventarplatz einen Gegenstand enthält.

**Wert:** Erforderlich – Platznummer (0–35 für das Hauptinventar; die Plätze 0–8 sind die Hotbar)

## Befindet sich der Mauszeiger über einem Gegenstand im Inventar (`is_item_hovered_in_inventory`)

**Zweck:** Prüft, ob sich der Mauszeiger über einem beliebigen Gegenstand in einem Inventarbildschirm befindet.

**Wert:** Nicht erforderlich

## Hält der Mauszeiger einen Inventargegenstand (`is_cursor_holding_inventory_item`)

**Zweck:** Prüft, ob der Mauszeiger derzeit einen Inventargegenstandsstapel hält.

**Wert:** Nicht erforderlich

## Ist ein Hotbarplatz ausgewählt (`is_hotbar_slot_active`)

**Zweck:** Prüft, ob derzeit ein bestimmter Hotbarplatz ausgewählt ist.

**Wert:** Erforderlich – Hotbarplatznummer (0–8)

## Hat der Spieler eine Berechtigungsstufe (`fancymenu_loading_requirement_has_player_permission_level`)

**Zweck:** Prüft, ob der Spieler mindestens die angegebene Berechtigungs-/OP-Stufe in der aktuellen Welt oder auf dem aktuellen Server besitzt.

**Wert:** Erforderlich – Berechtigungsstufe (0–4, wobei 4 einem Serveroperator entspricht)

## Ist die Angriffsstärke geschwächt (`is_attack_strength_weakened`)

**Zweck:** Prüft, ob die Angriffsstärke des Spielers derzeit geschwächt ist (nicht vollständig aufgeladen).

**Wert:** Nicht erforderlich

## Ist der Tag der Echtzeit (`fancymenu_visibility_requirement_is_realtime_day`)

**Zweck:** Prüft, ob der aktuelle Tag des Monats in der realen Welt einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Tagesnummer (1–31). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist die Stunde der Echtzeit (`fancymenu_visibility_requirement_is_realtime_hour`)

**Zweck:** Prüft, ob die aktuelle Stunde der realen Welt einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Stunde im 24-Stunden-Format (0–23). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist die Minute der Echtzeit (`fancymenu_visibility_requirement_is_realtime_minute`)

**Zweck:** Prüft, ob die aktuelle Minute der realen Welt einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Minute (0–59). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist der Monat der Echtzeit (`fancymenu_visibility_requirement_is_realtime_month`)

**Zweck:** Prüft, ob der aktuelle Monat der realen Welt einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Monatsnummer (1–12, wobei 1 für Januar steht). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist die Sekunde der Echtzeit (`fancymenu_visibility_requirement_is_realtime_second`)

**Zweck:** Prüft, ob die aktuelle Sekunde der realen Welt einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Sekunde (0–59). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist der Wochentag der Echtzeit (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Zweck:** Prüft, ob der aktuelle Wochentag der realen Welt einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Wochentag als Zahl (1–7, wobei 1 für Sonntag steht). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist das Jahr der Echtzeit (`fancymenu_visibility_requirement_is_realtime_year`)

**Zweck:** Prüft, ob das aktuelle Jahr der realen Welt einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Vollständiges Jahr (z. B. "2023"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Existiert eine Datei/ein Ordner (`fancymenu_loading_requirement_file_exists`)

**Zweck:** Prüft, ob eine Datei oder ein Verzeichnis existiert.

**Wert:** Erforderlich – Ein Pfad relativ zum aktiven Spielverzeichnis oder ein Pfad, der mit `.minecraft/` beginnt und das herkömmliche Minecraft-Verzeichnis bezeichnet. Dateien und Verzeichnisse gelten gleichermaßen als vorhanden.

## Ist das Betriebssystem Linux (`fancymenu_loading_requirement_is_os_linux`)

**Zweck:** Prüft, ob die aktuelle Plattform weder Windows noch macOS ist. Dies entspricht normalerweise Linux-Umgebungen.

**Wert:** Nicht erforderlich

## Ist das Betriebssystem macOS (`fancymenu_loading_requirement_is_os_macos`)

**Zweck:** Prüft, ob das Betriebssystem macOS ist.

**Wert:** Nicht erforderlich

## Ist das Betriebssystem Windows (`fancymenu_loading_requirement_is_os_windows`)

**Zweck:** Prüft, ob das Betriebssystem Windows ist.

**Wert:** Nicht erforderlich

## Ist eine Internetverbindung verfügbar (`is_internet_connection_available`)

**Zweck:** Prüft, ob eine aktive Internetverbindung verfügbar ist.

**Wert:** Nicht erforderlich

## Ist die Spiels Sprache (`fancymenu_loading_requirement_is_language`)

**Zweck:** Prüft, ob die aktuelle Spielsprache einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Sprachcode (z. B. `en_us` für Englisch)

## Ist ein Mod geladen (`fancymenu_loading_requirement_is_mod_loaded`)

**Zweck:** Prüft, ob ein bestimmter Mod geladen ist.

**Wert:** Erforderlich – Mod-ID (z. B. `fancymenu`, `jei`). OptiFine kann auch mit `optifine` geprüft werden. Mehrere durch Kommas getrennte Mod-IDs werden unterstützt; alle aufgeführten Mods müssen geladen sein.

## Ist Rinku geladen (`is_rinku_loaded`)

**Zweck:** Prüft, ob [Rinku](https://modrinth.com/mod/rinku) installiert und initialisiert ist. [Rinku](https://modrinth.com/mod/rinku) wird für das [Browser-Element](./elements#browser) und [veraltete Rinku-basierte Videotypen](./video#requirements) benötigt; [native Videofunktionen](./video) verwenden Watermedia.

**Wert:** Nicht erforderlich

## Ist eine Zahl (`fancymenu_visibility_requirement_is_number`)

**Zweck:** Ermöglicht einen erweiterten Zahlenvergleich mit verschiedenen Vergleichsmodi.

**Wert:** Erforderlich – Komplexes Format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`; `comparison_mode` kann `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` oder `smaller-than-or-equals` sein.

## Ist ein Text (`fancymenu_visibility_requirement_is_text`)

**Zweck:** Ermöglicht einen erweiterten Textvergleich mit verschiedenen Vergleichsmodi.

**Wert:** Erforderlich – Komplexes Format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`; `comparison_mode` kann `equals`, `contains`, `starts-with` oder `ends-with` sein.

## Ist die Server-IP (`fancymenu_visibility_requirement_is_server_ip`)

**Zweck:** Prüft, ob die IP des aktuellen Servers einem bestimmten Wert entspricht.

**Wert:** Erforderlich – Server-IP-Adresse (mit oder ohne Port)

## Ist der Server online (`fancymenu_loading_requirement_is_server_online`)

**Zweck:** Prüft, ob ein bestimmter Server online und erreichbar ist.

**Wert:** Erforderlich – Server-IP-Adresse (mit oder ohne Port)

## Ist ein Ressourcenpaket aktiviert (`is_resource_pack_enabled`)

**Zweck:** Prüft, ob ein bestimmtes Ressourcenpaket derzeit ausgewählt/aktiv ist.

**Wert:** Erforderlich – Titel des Ressourcenpakets oder Paket-ID (z. B. `Programmer Art` oder die ID des Pakets)

## Ist der Variablenwert (FM-Variable) (`fancymenu_visibility_requirement_is_variable_value`)

**Zweck:** Prüft, ob eine FancyMenu-Variable einen bestimmten Wert besitzt.

**Wert:** Erforderlich – Format: "variable_name:expected_value"

## Nur einmal pro Sitzung (`once_per_session`)

**Zweck:** Jede konfigurierte Instanz gibt einmal pro Spielsitzung „true“ zurück. Unterschiedliche Instanzen werden unabhängig voneinander verfolgt.

**Wert:** Nicht erforderlich
