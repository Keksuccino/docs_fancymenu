---
title: Bedingungen (Anforderungen)
description: So verwenden Sie Ladeanforderungen.
---

# Anforderungen

Anforderungen (in manchen Menüs **Loading Requirements** genannt) zeigen Inhalte basierend auf Bedingungen wie Hover-Zustand, Fenstergröße oder ob eine Welt geladen ist, an oder blenden sie aus.

Sie können sie auf [Elemente](./elements), ganze Layouts und [Aktionsskripte](./action-scripts) anwenden.

# Anforderungen zu Elementen hinzufügen

Um einem Element Anforderungen hinzuzufügen, klicken Sie mit der rechten Maustaste darauf und wählen Sie **Loading Requirements**.

Anforderungen werden geprüft, während das Menü geöffnet ist, sodass sich Elemente aktualisieren, wenn sich eine Bedingung ändert.

# Layout-weite Anforderungen

Sie können auch die Sichtbarkeit ganzer Layouts ändern, indem Sie mit der rechten Maustaste auf den **Editor-Hintergrund** klicken und dann auf **Loading Requirements [Layout-Wide]** klicken.

Wenn sich ein layoutweiter Wert ändert, baut FancyMenu den aktuellen Bildschirm neu auf und wendet die Layouts an, deren Anforderungen jetzt erfüllt sind.

# Aktionsskripte

Anforderungen können auch in Aktionsskripten verwendet werden.
Sie können sie im Editorbildschirm für Aktionsskripte hinzufügen und damit bestimmte Aktionen nur ausführen, wenn die Bedingung der Anforderung erfüllt ist.

# Anforderungen kombinieren

- Anforderungen außerhalb von Gruppen verwenden **UND**, daher müssen alle erfüllt sein.
- Innerhalb einer Gruppe wählen Sie **UND** oder **ODER**.
- Verwenden Sie **IF NOT**, um eine Anforderung zu invertieren.

Diese Regeln gelten gleichermaßen für Elemente, Layouts und Aktionsskripte.

# Anforderungswerte

Für Anforderungen, die einen Wert benötigen, verwenden Sie **Edit Requirement Value** und folgen Sie der im Editor angezeigten Beschreibung. Einige Felder unterstützen die **TAB**-Vervollständigung.

Wenn eine importierte Anforderung nach einer Änderung an FancyMenu oder Add-ons nicht mehr funktioniert, bearbeiten Sie sie im Anforderungsbildschirm und prüfen Sie `logs/latest.log` auf Fehler.

Der Anforderungseditor unterstützt ein Rechtsklick-Kontextmenü, Tastaturnavigation, Suche, Rückgängig/Wiederholen (`Ctrl/Command + Z` / `Ctrl/Command + Y`) und `Ctrl/Command + S` zum Speichern.

# Anforderungen im Detail

In diesem Abschnitt sind die in FancyMenu enthaltenen Standardanforderungen aufgeführt.

## Ist Element gehovert (`fancymenu_visibility_requirement_is_element_hovered`)

**Zweck:** Prüft, ob sich der Mauszeiger über einem bestimmten Element befindet.

**Wert:** Erforderlich — [Elementkennung](./element-identifiers) des Zielelements (z. B. `some_element_ID`).

## Ist Element fokussiert (`is_element_focused`)

**Zweck:** Prüft, ob ein bestimmtes Element derzeit den Tastaturfokus hat (z. B. ein Textfeld oder eine fokussierte Schaltfläche).

**Wert:** Erforderlich — Element-ID des Zielelements (dieselbe ID, die im Editor angezeigt wird)

> [!NOTE]
> Fokus und Hover sind unterschiedliche Zustände. Ein Element kann nach dem Verlassen durch den Mauszeiger sein fokussiertes Aussehen behalten; Klicken oder Tastaturnavigation können ihm den Fokus geben.

## Ist irgendein Element gehovert (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Zweck:** Prüft sichtbare/renderbare Elemente in der aktuell aktiven Anpassungsebene, einschließlich der von gestapelten Layouts beigesteuerten Elemente.

**Wert:** Nicht erforderlich

## Ist irgendeine Schaltfläche gehovert (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Zweck:** Prüft, ob irgendeine sichtbare/renderbare Vanilla- oder benutzerdefinierte Schaltfläche in der aktuell aktiven Anpassungsebene gehovert ist, einschließlich der von gestapelten Layouts beigesteuerten Schaltflächen.

**Wert:** Nicht erforderlich

## Ist Layout aktiviert (`fancymenu_visibility_requirement_is_layout_enabled`)

**Zweck:** Prüft, ob ein bestimmtes Layout derzeit aktiviert ist.

**Wert:** Erforderlich — Der Name des Layouts (z. B. `my_cool_main_menu_layout`)

## Läuft der Scheduler (`fancymenu_visibility_requirement_is_scheduler_running`)

**Zweck:** Prüft, ob ein [Scheduler](./schedulers) derzeit läuft.

**Wert:** Erforderlich — Scheduler-ID (z. B. `my_scheduler`)

## Ist GUI-Skalierung (`fancymenu_loading_requirement_is_gui_scale`)

**Zweck:** Prüft, ob die aktuelle GUI-Skalierung bestimmten Bedingungen entspricht.

**Wert:** Erforderlich — Verwenden Sie eine Zahl für Gleichheit, `>` für größer als oder `<` für kleiner als.

Mehrere durch Kommas getrennte Bedingungen werden mit UND verknüpft. Zum Beispiel gilt `>1,<4` nur dann, wenn die GUI-Skalierung größer als `1` und kleiner als `4` ist.

## Ist Schaltfläche aktiv (`fancymenu_visibility_requirement_is_button_active`)

**Zweck:** Prüft, ob eine bestimmte Schaltfläche aktiv (anklickbar) ist.

**Wert:** Erforderlich — Element-ID der Zielschaltfläche (z. B. "some_element_ID")

## Ist Bildschirmtitel (`is_menu_title`)

**Zweck:** Prüft, ob der ANGEZEIGTE Titel des Bildschirms mit einem bestimmten Text oder Lokalisierungsschlüssel übereinstimmt. Es wird nur der Anzeigename/Titel des Bildschirms geprüft, wie „Optionen“ oder „Pause“. Die Menü-/Bildschirm-ID (wie `title_screen`) wird NICHT geprüft!

**Wert:** Erforderlich — Der exakte Titeltext oder Lokalisierungsschlüssel des Bildschirms

## Ist Taste gedrückt (`is_key_pressed`)

**Zweck:** Prüft, ob eine bestimmte Tastaturtaste derzeit gedrückt wird.

**Wert:** Erforderlich — Der Tastencode der Zieltaste. Wird beim Bearbeiten des Anforderungswerts über eine UI ausgewählt.

## Ist irgendein Bildschirm offen (`is_any_screen_open`)

**Zweck:** Prüft, ob derzeit irgendein Bildschirm/მენü geöffnet ist (gibt false zurück, wenn kein Bildschirm angezeigt wird).

**Wert:** Nicht erforderlich

## Ist MC-Debug-Overlay aktiviert (`is_debug_overlay_enabled`)

**Zweck:** Prüft, ob das F3-Debug-Overlay derzeit sichtbar ist.

**Wert:** Nicht erforderlich

## Ist aktiver Cursor-Typ (`is_active_cursor_type`)

**Zweck:** Prüft, ob der aktuell aktive Cursor-Typ von FancyMenu mit einem bestimmten Standard-Cursortyp übereinstimmt.

**Wert:** Erforderlich — Cursortyp: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` oder `not_allowed`

## Ist die Anpassungs-Menüleiste sichtbar (`is_customization_menu_bar_visible`)

**Zweck:** Prüft, ob die Anpassungs-Menüleiste von FancyMenu derzeit sichtbar ist.

**Wert:** Nicht erforderlich

## Ist Modpack-Modus aktiviert (`is_modpack_mode_enabled`)

**Zweck:** Prüft, ob der Modpack-Modus von FancyMenu aktiviert ist.

**Wert:** Nicht erforderlich

## Maustaste ist gedrückt (`mouse_click`)

**Zweck:** Gibt true zurück, solange eine bestimmte Maustaste gedrückt gehalten wird. Dies ist kein einmaliges Klickereignis; verwenden Sie den [**On Mouse Button Clicked**-Listener](./listeners#on-mouse-button-clicked-mouse_button_clicked), wenn eine Aktion einmal pro Klick ausgeführt werden soll.

**Wert:** Erforderlich — `left` oder `right`, um die zu prüfende Maustaste anzugeben

## Ist Vollbild (`fancymenu_loading_requirement_is_fullscreen`)

**Zweck:** Prüft, ob sich das Spiel derzeit im Vollbildmodus befindet.

**Wert:** Nicht erforderlich

## Ist Fensterbreite (`fancymenu_loading_requirement_is_window_width`)

**Zweck:** Prüft, ob die Fensterbreite des Spiels bestimmten Werten entspricht.

**Wert:** Erforderlich — Fensterbreite in Pixeln (z. B. "1920"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Fensterhöhe (`fancymenu_loading_requirement_is_window_height`)

**Zweck:** Prüft, ob die Fensterhöhe des Spiels bestimmten Werten entspricht.

**Wert:** Erforderlich — Fensterhöhe in Pixeln (z. B. "1080"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Fensterbreite größer als (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Zweck:** Prüft, ob die Fensterbreite des Spiels größer als ein bestimmter Wert ist.

**Wert:** Erforderlich — Fensterbreite in Pixeln (z. B. "1920")

## Ist Fensterhöhe größer als (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Zweck:** Prüft, ob die Fensterhöhe des Spiels größer als ein bestimmter Wert ist.

**Wert:** Erforderlich — Fensterhöhe in Pixeln (z. B. "1080")

## Ist Mehrspieler (`fancymenu_loading_requirement_is_multiplayer`)

**Zweck:** Prüft, ob sich der Spieler derzeit in einer Mehrspielerwelt befindet.

**Wert:** Nicht erforderlich

## Ist Einzelspieler (`fancymenu_loading_requirement_is_singpleplayer`)

**Zweck:** Prüft, ob sich der Spieler derzeit in einer Einzelspielerwelt befindet.

**Wert:** Nicht erforderlich

## Ist Welt geladen (`fancymenu_loading_requirement_is_world_loaded`)

**Zweck:** Prüft, ob derzeit irgendeine Welt geladen ist.

**Wert:** Nicht erforderlich

## Ist im Abenteuer-Modus (`fancymenu_visibility_requirement_is_adventure`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Abenteuer-Spielmodus befindet.

**Wert:** Nicht erforderlich

## Ist im Kreativmodus (`fancymenu_visibility_requirement_is_creative`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Kreativ-Spielmodus befindet.

**Wert:** Nicht erforderlich

## Ist im Zuschauermodus (`fancymenu_visibility_requirement_is_spectator`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Zuschauermodus befindet.

**Wert:** Nicht erforderlich

## Ist im Überlebensmodus (`fancymenu_visibility_requirement_is_survival`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Überlebens-Spielmodus befindet.

**Wert:** Nicht erforderlich

## Ist Spielmodus (`is_gamemode`)

**Zweck:** Prüft, ob sich der Spieler in einem bestimmten Spielmodus befindet.

**Wert:** Erforderlich — Name des Spielmodus (z. B. "creative", "survival", "adventure", "spectator")

## Ist Schwierigkeit (`is_difficulty`)

**Zweck:** Prüft, ob die aktuelle Spielschwierigkeit einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Name der Schwierigkeit (z. B. "peaceful", "easy", "normal", "hard")

## Ist Hardcore (`is_hardcore`)

**Zweck:** Prüft, ob die aktuell geladene Welt im Hardcore-Modus ist.

**Wert:** Nicht erforderlich

## Ist Kameraperspektive (`is_camera_perspective`)

**Zweck:** Prüft, ob die aktuelle Kameraperspektive mit einer bestimmten Perspektive übereinstimmt.

**Wert:** Erforderlich — `first_person`, `third_person_back` oder `third_person_front`

## Regnet es (`is_raining`)

**Zweck:** Prüft, ob es an der Position des Spielers derzeit regnet.

**Wert:** Nicht erforderlich

## Donnert es (`is_thundering`)

**Zweck:** Prüft, ob es in der Welt des Spielers derzeit ein Gewitter gibt.

**Wert:** Nicht erforderlich

## Ist klares Wetter (`is_clear_weather`)

**Zweck:** Prüft, ob das Wetter derzeit klar ist (kein Regen oder Donner).

**Wert:** Nicht erforderlich

## Schneit es (`is_snowing`)

**Zweck:** Prüft, ob es an der Position des Spielers derzeit schneit.

**Wert:** Nicht erforderlich

## Läuft der Spieler (`is_player_running`)

**Zweck:** Prüft, ob der Spieler derzeit sprintet.

**Wert:** Nicht erforderlich

## Schleicht der Spieler (`is_player_sneaking`)

**Zweck:** Prüft, ob der Spieler derzeit schleicht/hockt.

**Wert:** Nicht erforderlich

## Verwendet der Spieler ein Item (`is_player_using_item`)

**Zweck:** Prüft, ob der Spieler derzeit ein Item verwendet.

**Wert:** Nicht erforderlich

## Schwimmt der Spieler (`is_player_swimming`)

**Zweck:** Prüft, ob der Spieler derzeit schwimmt.

**Wert:** Nicht erforderlich

## Springt oder fällt der Spieler (`is_player_jumping`)

**Zweck:** Gibt true zurück, solange sich der Spieler in der Luft in einem normalen Sprung- oder Fallzustand befindet. Schwimmen, Flüssigkeiten, Elytra-Flug, Schlafen, visuelles Schwimmen und Kriechen sind ausgeschlossen.

**Wert:** Nicht erforderlich

## Ist der Spieler unter Wasser (`is_player_under_water`)

**Zweck:** Prüft, ob der Spieler vollständig unter Wasser ist.

**Wert:** Nicht erforderlich

## Ist der Spieler im Wasser (`is_player_in_water`)

**Zweck:** Prüft, ob sich der Spieler im Wasser befindet (kann teilweise untergetaucht sein).

**Wert:** Nicht erforderlich

## Ist der Spieler in Lava (`is_player_in_lava`)

**Zweck:** Prüft, ob sich der Spieler in Lava befindet.

**Wert:** Nicht erforderlich

## Ist der Spieler in einer Flüssigkeit (`is_player_in_fluid`)

**Zweck:** Prüft, ob sich der Spieler in irgendeiner Flüssigkeit befindet (Wasser, Lava usw.).

**Wert:** Nicht erforderlich

## Reitet der Spieler auf einer Entität/Fahrzeug (`is_player_riding_entity`)

**Zweck:** Prüft, ob der Spieler auf irgendeiner Entität reitet.

**Wert:** Nicht erforderlich

## Reitet der Spieler auf einer springbaren Entität (`is_player_riding_jumpable_entity`)

**Zweck:** Prüft, ob der Spieler auf einer Entität reitet, die springen kann (wie ein Pferd).

**Wert:** Nicht erforderlich

## Reitet der Spieler auf einer Entität mit Gesundheit (`is_player_riding_entity_with_health`)

**Zweck:** Prüft, ob der Spieler auf einer lebenden Entität mit Gesundheit reitet (wie Tiere, nicht Boote).

**Wert:** Nicht erforderlich

## Ist der Spieler im Pulverschnee (`is_player_in_powder_snow`)

**Zweck:** Prüft, ob sich der Spieler derzeit im Pulverschnee befindet.

**Wert:** Nicht erforderlich

## War der Spieler im Pulverschnee (`was_player_in_powder_snow`)

**Zweck:** Prüft, ob sich der Spieler im Pulverschnee befand (für Effekte, die nach dem Verlassen fortbestehen).

**Wert:** Nicht erforderlich

## Trägt der Spieler einen Kürbis (`is_player_wearing_pumpkin`)

**Zweck:** Prüft, ob der Spieler einen ausgehöhlten Kürbis auf dem Kopf trägt.

**Wert:** Nicht erforderlich

## Fliegt der Spieler mit Elytra (`is_player_flying_with_elytra`)

**Zweck:** Prüft, ob der Spieler derzeit mit einer Elytra fliegt.

**Wert:** Nicht erforderlich

## Fliegt der Spieler im Kreativmodus (`is_player_creative_flying`)

**Zweck:** Prüft, ob der Spieler im Kreativmodus fliegt.

**Wert:** Nicht erforderlich

## Hat der Spieler Absorptionsherzen (`has_player_absorption_hearts`)

**Zweck:** Prüft, ob der Spieler Absorptionsherzen (goldene Herzen) hat.

**Wert:** Nicht erforderlich

## Ist der Spieler verwelkt (`is_player_withered`)

**Zweck:** Prüft, ob der Spieler vom Wither-Effekt betroffen ist.

**Wert:** Nicht erforderlich

## Ist der Spieler vollständig eingefroren (`is_player_fully_frozen`)

**Zweck:** Prüft, ob der Spieler vollständig eingefroren ist (normalerweise durch Pulverschnee).

**Wert:** Nicht erforderlich

## Ist der Spieler vergiftet (`is_player_poisoned`)

**Zweck:** Prüft, ob der Spieler vom Gift-Effekt betroffen ist.

**Wert:** Nicht erforderlich

## Ist der Spieler in einem Biom (`is_player_in_biome`)

**Zweck:** Prüft, ob sich der Spieler in einem bestimmten Biom befindet.

**Wert:** Erforderlich — Biom-Kennung (z. B. `minecraft:birch_forest`)

## Ist der Spieler in einer Dimension (`is_player_in_dimension`)

**Zweck:** Prüft, ob sich der Spieler in einer bestimmten Dimension befindet.

**Wert:** Erforderlich — Dimensionskennung (z. B. `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Ist der Spieler in einer Struktur (`is_player_in_structure`)

**Zweck:** Prüft, ob sich der Spieler derzeit in einer bestimmten Struktur befindet. Für Serverwelten ist FancyMenu auf dem Server erforderlich.

**Wert:** Erforderlich — Strukturkennung (z. B. `minecraft:village`)

## Ist Entität in der Nähe (`is_entity_nearby`)

**Zweck:** Prüft, ob sich ein bestimmter Entitätstyp in einem bestimmten Radius um den Spieler befindet.

**Wert:** Erforderlich — Format: "radius:entity_id" (z. B. `10:minecraft:pig` - prüft auf Schweine innerhalb von 10 Blöcken)

## Ist Effekt aktiv (`is_effect_active`)

**Zweck:** Prüft, ob ein bestimmter Trankeffekt auf dem Spieler aktiv ist.

**Wert:** Erforderlich — Effektkennung (z. B. `minecraft:speed`, `minecraft:strength`)

## Ist irgendein Effekt aktiv (`is_any_effect_active`)

**Zweck:** Prüft, ob der Spieler irgendeinen aktiven Trankeffekt hat.

**Wert:** Nicht erforderlich

## Ist der Spieler linkshändig (`is_left_handed`)

**Zweck:** Prüft, ob der Spieler in den Spieloptionen auf linkshändig eingestellt ist.

**Wert:** Nicht erforderlich

## Ist Inventarslot gefüllt (`is_inventory_slot_filled`)

**Zweck:** Prüft, ob ein bestimmter Inventarslot einen Gegenstand enthält.

**Wert:** Erforderlich — Slotnummer (0-35 für das Hauptinventar, Slots 0-8 sind die Schnellleiste)

## Ist Gegenstand im Inventar gehovert (`is_item_hovered_in_inventory`)

**Zweck:** Prüft, ob der Mauszeiger einen Gegenstand in einem Inventarbildschirm überfährt.

**Wert:** Nicht erforderlich

## Hält der Cursor einen Inventargegenstand (`is_cursor_holding_inventory_item`)

**Zweck:** Prüft, ob der Cursor derzeit einen Inventargegenstand-Stapel hält.

**Wert:** Nicht erforderlich

## Ist Schnellleisten-Slot ausgewählt (`is_hotbar_slot_active`)

**Zweck:** Prüft, ob ein bestimmter Slot der Schnellleiste derzeit ausgewählt ist.

**Wert:** Erforderlich — Slotnummer der Schnellleiste (0-8)

## Hat der Spieler Berechtigungsstufe (`fancymenu_loading_requirement_has_player_permission_level`)

**Zweck:** Prüft, ob der Spieler auf der aktuellen Welt oder dem aktuellen Server mindestens die angegebene Berechtigungs-/OP-Stufe hat.

**Wert:** Erforderlich — Berechtigungsstufe als Zahl (0-4, wobei 4 Server-Operator ist)

## Ist Angriffsstärke abgeschwächt (`is_attack_strength_weakened`)

**Zweck:** Prüft, ob die Angriffsstärke des Spielers derzeit abgeschwächt ist (nicht vollständig aufgeladen).

**Wert:** Nicht erforderlich

## Ist Echtzeit-Tag (`fancymenu_visibility_requirement_is_realtime_day`)

**Zweck:** Prüft, ob der aktuelle reale Tag des Monats einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Tagesnummer (1-31). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Echtzeit-Stunde (`fancymenu_visibility_requirement_is_realtime_hour`)

**Zweck:** Prüft, ob die aktuelle reale Stunde einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Stunde im 24-Stunden-Format (0-23). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Echtzeit-Minute (`fancymenu_visibility_requirement_is_realtime_minute`)

**Zweck:** Prüft, ob die aktuelle reale Minute einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Minute (0-59). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Echtzeit-Monat (`fancymenu_visibility_requirement_is_realtime_month`)

**Zweck:** Prüft, ob der aktuelle reale Monat einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Monatsnummer (1-12, wobei 1 für Januar steht). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Echtzeit-Sekunde (`fancymenu_visibility_requirement_is_realtime_second`)

**Zweck:** Prüft, ob die aktuelle reale Sekunde einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Sekunde (0-59). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Echtzeit-Wochentag (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Zweck:** Prüft, ob der aktuelle reale Wochentag einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Wochentag als Zahl (1-7, wobei 1 Sonntag ist). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Echtzeit-Jahr (`fancymenu_visibility_requirement_is_realtime_year`)

**Zweck:** Prüft, ob das aktuelle reale Jahr einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Vollständiges Jahr (z. B. "2023"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Datei/Ordner existiert (`fancymenu_loading_requirement_file_exists`)

**Zweck:** Prüft, ob eine Datei oder ein Verzeichnis existiert.

**Wert:** Erforderlich — Ein Pfad relativ zum aktiven Spielverzeichnis oder ein Pfad, der mit `.minecraft/` für das übliche Minecraft-Verzeichnis beginnt. Sowohl Dateien als auch Verzeichnisse zählen als vorhanden.

## Ist OS Linux (`fancymenu_loading_requirement_is_os_linux`)

**Zweck:** Prüft, ob die aktuelle Plattform weder Windows noch macOS ist. Dies entspricht normalerweise Linux-Umgebungen.

**Wert:** Nicht erforderlich

## Ist OS macOS (`fancymenu_loading_requirement_is_os_macos`)

**Zweck:** Prüft, ob das Betriebssystem macOS ist.

**Wert:** Nicht erforderlich

## Ist OS Windows (`fancymenu_loading_requirement_is_os_windows`)

**Zweck:** Prüft, ob das Betriebssystem Windows ist.

**Wert:** Nicht erforderlich

## Ist Internetverbindung verfügbar (`is_internet_connection_available`)

**Zweck:** Prüft, ob eine aktive Internetverbindung verfügbar ist.

**Wert:** Nicht erforderlich

## Ist Spielsprache (`fancymenu_loading_requirement_is_language`)

**Zweck:** Prüft, ob die aktuelle Spielsprache einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Sprachcode (z. B. `en_us` für Englisch)

## Ist Mod geladen (`fancymenu_loading_requirement_is_mod_loaded`)

**Zweck:** Prüft, ob ein bestimmter Mod geladen ist.

**Wert:** Erforderlich — Mod-ID (z. B. `fancymenu`, `jei`). Sie können auch `optifine` für OptiFine prüfen. Mehrere durch Kommas getrennte Mod-IDs werden unterstützt; alle aufgelisteten Mods müssen geladen sein.

## Ist MCEF geladen (`is_mcef_loaded`)

**Zweck:** Prüft, ob MCEF (Minecraft Chromium Embedded Framework) installiert und initialisiert ist. MCEF wird für das [Browser-Element](./elements#browser) und [veraltete MCEF-basierte Video-Typen](./video#requirements) benötigt; [native Video-Funktionen](./video) verwenden Watermedia.

**Wert:** Nicht erforderlich

## Ist Zahl (`fancymenu_visibility_requirement_is_number`)

**Zweck:** Bietet erweiterte Zahlenvergleiche mit verschiedenen Vergleichsmodi.

**Wert:** Erforderlich — Komplexes Format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`, wobei `comparison_mode` `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` oder `smaller-than-or-equals` sein kann

## Ist Text (`fancymenu_visibility_requirement_is_text`)

**Zweck:** Bietet erweiterte Textvergleiche mit verschiedenen Vergleichsmodi.

**Wert:** Erforderlich — Komplexes Format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`, wobei `comparison_mode` `equals`, `contains`, `starts-with` oder `ends-with` sein kann

## Ist Server-IP (`fancymenu_visibility_requirement_is_server_ip`)

**Zweck:** Prüft, ob die aktuelle Server-IP einem bestimmten Wert entspricht.

**Wert:** Erforderlich — Server-IP-Adresse (mit oder ohne Port)

## Ist Server online (`fancymenu_loading_requirement_is_server_online`)

**Zweck:** Prüft, ob ein bestimmter Server online und erreichbar ist.

**Wert:** Erforderlich — Server-IP-Adresse (mit oder ohne Port)

## Ist Ressourcenpaket aktiviert (`is_resource_pack_enabled`)

**Zweck:** Prüft, ob ein bestimmtes Ressourcenpaket derzeit ausgewählt/aktiv ist.

**Wert:** Erforderlich — Titel des Ressourcenpakets oder Paket-ID (z. B. `Programmer Art` oder die ID des Pakets)

## Ist Variablenwert (FM-Variable) (`fancymenu_visibility_requirement_is_variable_value`)

**Zweck:** Prüft, ob eine FancyMenu-Variable einen bestimmten Wert hat.

**Wert:** Erforderlich — Format: "variable_name:expected_value"

## Nur einmal pro Sitzung (`once_per_session`)

**Zweck:** Jede konfigurierte Instanz gibt einmal pro Spielesitzung true zurück. Verschiedene Instanzen werden unabhängig voneinander verfolgt.

**Wert:** Nicht erforderlich
