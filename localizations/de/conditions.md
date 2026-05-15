---
title: Bedingungen (Voraussetzungen)
description: Wie man Ladevoraussetzungen verwendet.
---

# Voraussetzungen
Voraussetzungen (auch „Ladevoraussetzungen“) ermöglichen es dir, Teile deiner Layouts je nach verschiedenen Bedingungen sichtbar oder unsichtbar zu machen, zum Beispiel wenn ein Element mit der Maus überfahren wird, das Fenster eine bestimmte Größe hat oder du dich gerade in einer Welt befindest.

Sie können auch in Aktionsskripten von Buttons, Schiebereglern, Tickern und allem anderen mit einem Eingabefeld für Aktionsskripte verwendet werden.

# Voraussetzungen zu Elementen hinzufügen
Um einem oder mehreren Elementen Voraussetzungen hinzuzufügen, klicke einfach mit der rechten Maustaste auf das Element und dann auf **Ladevoraussetzungen**.

# Layoutweite Voraussetzungen
Du kannst auch die Sichtbarkeit ganzer Layouts ändern, indem du mit der rechten Maustaste auf den **Editor-Hintergrund** klickst und dann auf **Ladevoraussetzungen [Layoutweit]**.

# Aktionsskripte
Voraussetzungen können auch in Aktionsskripten verwendet werden.
Du kannst sie im Aktionsskript-Editor hinzufügen und damit bestimmte Aktionen nur dann ausführen, wenn die Bedingung der Voraussetzung erfüllt ist.

# Voraussetzungswerte
Für einige Voraussetzungen musst du Werte festlegen, damit sie korrekt funktionieren. In diesem Fall sollte dich die Voraussetzungsansicht darauf hinweisen, zuerst alle Werte festzulegen. Wenn nicht, prüfe einfach, ob der Button **Voraussetzungswert bearbeiten** beim Hinzufügen der Voraussetzung anklickbar ist.
Sieh dir immer die Beschreibung der Voraussetzung an, wenn du dir unsicher bist, welcher Wert gesetzt werden muss.
Einige Werteingaben unterstützen sogar **TAB-Autovervollständigung**.

FancyMenu 3.9.0 überarbeitet das Fenster „Voraussetzungen verwalten“ und nutzt nun ein Rechtsklick-Kontextmenü, Tastaturnavigation, Suche, Rückgängig/Wiederholen (`CTRL + Z` / `CTRL + Y`) sowie `CTRL + S` als Shortcut für **Fertig**.

# Voraussetzungen im Detail
Die folgende Liste enthält die meisten, wenn nicht sogar alle in FancyMenu verfügbaren Voraussetzungen. Es ist möglich, dass die Liste durch Updates für das Mod manchmal etwas veraltet ist.

## Ist Element überfahren
Prüft, ob sich ein bestimmtes Element gerade unter dem Mauszeiger befindet.  
**Wert erforderlich**: Ja - Element-ID des Zielelements (z. B. `some_element_ID`). Die ID kannst du erhalten, indem du im Editor mit der rechten Maustaste auf ein Element klickst.

## Ist Element fokussiert
Prüft, ob ein bestimmtes Element aktuell den Tastaturfokus hat (zum Beispiel ein Textfeld oder ein fokussierter Button).
**Wert erforderlich**: Ja - Element-ID des Zielelements (dieselbe ID, die im Editor angezeigt wird)

> Das ist nicht dasselbe wie ein nur überfahrenes Element, auch wenn es ähnlich aussieht. Fokussierte Elemente sehen weiterhin „überfahren“ aus, selbst wenn sie nicht mehr überfahren werden. Elemente werden fokussiert, wenn man auf sie klickt oder wenn man die Tastatur benutzt, um durch Menüs zu navigieren.
{.is-info}

## Ist irgendein Element überfahren
Prüft, ob sich aktuell irgendein Element im Layout unter dem Mauszeiger befindet.  
**Wert erforderlich**: Nein

## Ist irgendein Button überfahren
Prüft, ob aktuell irgendein Button (Vanilla oder benutzerdefiniert) unter dem Mauszeiger liegt.  
**Wert erforderlich**: Nein

## Ist Layout aktiviert
Prüft, ob ein bestimmtes Layout aktuell aktiviert ist.  
**Wert erforderlich**: Ja - Name des Layouts (z. B. `my_cool_main_menu_layout`)

## Läuft der Scheduler
Prüft, ob aktuell ein Scheduler ausgeführt wird.
**Wert erforderlich**: Ja - Scheduler-ID (z. B. `my_scheduler`)

## Ist GUI-Skalierung
Prüft, ob die aktuelle GUI-Skalierung bestimmten Bedingungen entspricht.  
**Wert erforderlich**: Ja - Kann numerische Werte wie `1`, `2` usw. annehmen

## Ist Button aktiv
Prüft, ob ein bestimmter Button aktiv ist (anklickbar).  
**Wert erforderlich**: Ja - Element-ID des Ziel-Buttons (z. B. "some_element_ID")

## Ist Bildschirmtitel
Prüft, ob der ANZEIGETitel des Bildschirms mit einem bestimmten Text oder Lokalisierungsschlüssel übereinstimmt. Hier wird nur der Anzeigename/Titel des Bildschirms geprüft, wie „Optionen“ oder „Pause“. Der Menü-/Bildschirmbezeichner (z. B. `title_screen`) wird NICHT geprüft!

**Wert erforderlich**: Ja - Der genaue Titeltext oder Lokalisierungsschlüssel des Bildschirms

## Ist Taste gedrückt
Prüft, ob eine bestimmte Tastaturtaste aktuell gedrückt wird.  
**Wert erforderlich**: Ja - Der Tastencode der Zieltaste. Wird über eine UI beim Bearbeiten des Voraussetzungswerts ausgewählt.

## Ist irgendein Bildschirm offen
Prüft, ob aktuell ein Bildschirm/მენü geöffnet ist (gibt false zurück, wenn kein Bildschirm angezeigt wird).  
**Wert erforderlich**: Nein

## Ist MC-Debug-Overlay aktiviert
Prüft, ob das F3-Debug-Overlay derzeit sichtbar ist.
**Wert erforderlich**: Nein

## Ist aktiver Cursor-Typ
Prüft, ob der aktuell aktive Cursor-Typ von FancyMenu einem bestimmten Standard-Cursor-Typ entspricht.
**Wert erforderlich**: Ja - Cursor-Typ: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` oder `not_allowed`

## Ist die Anpassungs-Menüleiste sichtbar
Prüft, ob die Anpassungs-Menüleiste von FancyMenu derzeit sichtbar ist.
**Wert erforderlich**: Nein

## Ist Modpack-Modus aktiviert
Prüft, ob der Modpack-Modus von FancyMenu aktiviert ist.
**Wert erforderlich**: Nein

## Maus geklickt
Prüft, ob eine bestimmte Maustaste gedrückt wird.  
**Wert erforderlich**: Ja - `left` oder `right`, um anzugeben, welche Maustaste geprüft werden soll

## Ist Vollbild
Prüft, ob das Spiel derzeit im Vollbildmodus läuft.  
**Wert erforderlich**: Nein

## Ist Fensterbreite
Prüft, ob die Breite des Spielfensters bestimmten Werten entspricht.  
**Wert erforderlich**: Ja - Fensterbreite in Pixeln (z. B. "1920"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Fensterhöhe
Prüft, ob die Höhe des Spielfensters bestimmten Werten entspricht.  
**Wert erforderlich**: Ja - Fensterhöhe in Pixeln (z. B. "1080"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist Fensterbreite größer als
Prüft, ob die Breite des Spielfensters größer als ein bestimmter Wert ist.  
**Wert erforderlich**: Ja - Fensterbreite in Pixeln (z. B. "1920")

## Ist Fensterhöhe größer als
Prüft, ob die Höhe des Spielfensters größer als ein bestimmter Wert ist.  
**Wert erforderlich**: Ja - Fensterhöhe in Pixeln (z. B. "1080")

## Ist Multiplayer
Prüft, ob sich der Spieler aktuell in einer Multiplayer-Welt befindet.  
**Wert erforderlich**: Nein

## Ist Singleplayer
Prüft, ob sich der Spieler aktuell in einer Einzelspieler-Welt befindet.  
**Wert erforderlich**: Nein

## Ist Welt geladen
Prüft, ob aktuell eine Welt geladen ist.  
**Wert erforderlich**: Nein

## Ist Adventure
Prüft, ob sich der Spieler aktuell im Abenteuermodus befindet.  
**Wert erforderlich**: Nein

## Ist Kreativ
Prüft, ob sich der Spieler aktuell im Kreativmodus befindet.  
**Wert erforderlich**: Nein

## Ist Zuschauer
Prüft, ob sich der Spieler aktuell im Zuschauermodus befindet.  
**Wert erforderlich**: Nein

## Ist Überleben
Prüft, ob sich der Spieler aktuell im Überlebensmodus befindet.  
**Wert erforderlich**: Nein

## Ist Spielmodus
Prüft, ob sich der Spieler in einem bestimmten Spielmodus befindet.  
**Wert erforderlich**: Ja - Name des Spielmodus (z. B. "creative", "survival", "adventure", "spectator")

## Ist Schwierigkeit
Prüft, ob die aktuelle Spielschwierigkeit einem bestimmten Wert entspricht.  
**Wert erforderlich**: Ja - Name der Schwierigkeit (z. B. "peaceful", "easy", "normal", "hard")

## Ist Hardcore
Prüft, ob sich die aktuell geladene Welt im Hardcore-Modus befindet.
**Wert erforderlich**: Nein

## Ist Kameraperspektive
Prüft, ob die aktuelle Kameraperspektive einer bestimmten Perspektive entspricht.
**Wert erforderlich**: Ja - `first_person`, `third_person_back` oder `third_person_front`

## Regnet es
Prüft, ob es am aktuellen Standort des Spielers gerade regnet.  
**Wert erforderlich**: Nein

## Gewittert es
Prüft, ob es in der Welt des Spielers gerade ein Gewitter gibt.  
**Wert erforderlich**: Nein

## Ist klares Wetter
Prüft, ob das Wetter derzeit klar ist (kein Regen oder Gewitter).  
**Wert erforderlich**: Nein

## Schneit es
Prüft, ob es am aktuellen Standort des Spielers gerade schneit.  
**Wert erforderlich**: Nein

## Läuft der Spieler
Prüft, ob der Spieler gerade sprintet.  
**Wert erforderlich**: Nein

## Schleicht der Spieler
Prüft, ob der Spieler gerade schleicht/hockt.  
**Wert erforderlich**: Nein

## Verwendet der Spieler ein Item
Prüft, ob der Spieler derzeit ein Item verwendet.
**Wert erforderlich**: Nein

## Schwimmt der Spieler
Prüft, ob der Spieler gerade schwimmt.  
**Wert erforderlich**: Nein

## Springt oder fällt der Spieler
Prüft, ob der Spieler gerade springt.  
**Wert erforderlich**: Nein

## Ist der Spieler unter Wasser
Prüft, ob sich der Spieler vollständig unter Wasser befindet.  
**Wert erforderlich**: Nein

## Ist der Spieler im Wasser
Prüft, ob sich der Spieler im Wasser befindet (kann teilweise eingetaucht sein).  
**Wert erforderlich**: Nein

## Ist der Spieler in Lava
Prüft, ob sich der Spieler in Lava befindet.  
**Wert erforderlich**: Nein

## Ist der Spieler in einer Flüssigkeit
Prüft, ob sich der Spieler in irgendeiner Flüssigkeit befindet (Wasser, Lava usw.).  
**Wert erforderlich**: Nein

## Reitet der Spieler auf einer Entität/einem Fahrzeug
Prüft, ob der Spieler auf irgendeiner Entität reitet.  
**Wert erforderlich**: Nein

## Reitet der Spieler auf einer springbaren Entität
Prüft, ob der Spieler auf einer Entität reitet, die springen kann (z. B. ein Pferd).  
**Wert erforderlich**: Nein

## Reitet der Spieler auf einer Entität mit Gesundheit
Prüft, ob der Spieler auf einer lebenden Entität mit Gesundheit reitet (z. B. Tiere, keine Boote).  
**Wert erforderlich**: Nein

## Ist der Spieler in Pulverschnee
Prüft, ob sich der Spieler derzeit in Pulverschnee befindet.  
**Wert erforderlich**: Nein

## War der Spieler in Pulverschnee
Prüft, ob sich der Spieler in Pulverschnee befand (für Effekte, die nach dem Verlassen bestehen bleiben).  
**Wert erforderlich**: Nein

## Trägt der Spieler einen Kürbis
Prüft, ob der Spieler einen ausgehöhlten Kürbis auf dem Kopf trägt.  
**Wert erforderlich**: Nein

## Fliegt der Spieler mit Elytra
Prüft, ob der Spieler derzeit mit Elytra fliegt.  
**Wert erforderlich**: Nein

## Kreativflug des Spielers
Prüft, ob der Spieler im Kreativmodus fliegt.  
**Wert erforderlich**: Nein

## Hat der Spieler Absorptionsherzen
Prüft, ob der Spieler Absorptionsherzen (goldene Herzen) hat.  
**Wert erforderlich**: Nein

## Ist der Spieler vom Wither betroffen
Prüft, ob der Spieler vom Wither-Effekt betroffen ist.  
**Wert erforderlich**: Nein

## Ist der Spieler vollständig eingefroren
Prüft, ob der Spieler vollständig eingefroren ist (normalerweise durch Pulverschnee).  
**Wert erforderlich**: Nein

## Ist der Spieler vergiftet
Prüft, ob der Spieler vom Gift-Effekt betroffen ist.  
**Wert erforderlich**: Nein

## Ist der Spieler in einem Biom
Prüft, ob sich der Spieler in einem bestimmten Biom befindet.  
**Wert erforderlich**: Ja - Biom-Identifikator (z. B. `minecraft:birch_forest`)

## Ist der Spieler in einer Dimension
Prüft, ob sich der Spieler in einer bestimmten Dimension befindet.  
**Wert erforderlich**: Ja - Dimensions-Identifikator (z. B. `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Ist der Spieler in einer Struktur
Prüft, ob sich der Spieler derzeit innerhalb einer bestimmten Struktur befindet. Erfordert FancyMenu auf dem Server für Serverwelten.
**Wert erforderlich**: Ja - Struktur-Identifikator (z. B. `minecraft:village`)

## Ist eine Entität in der Nähe
Prüft, ob sich ein bestimmter Entitätstyp innerhalb eines bestimmten Radius um den Spieler befindet.  
**Wert erforderlich**: Ja - Format: "radius:entity_id" (z. B. `10:minecraft:pig` - prüft, ob sich Schweine innerhalb von 10 Blöcken befinden)

## Ist Effekt aktiv
Prüft, ob ein bestimmter Trankeffekt auf dem Spieler aktiv ist.  
**Wert erforderlich**: Ja - Effekt-Identifikator (z. B. `minecraft:speed`, `minecraft:strength`)

## Ist irgendein Effekt aktiv
Prüft, ob der Spieler irgendeinen aktiven Trankeffekt hat.  
**Wert erforderlich**: Nein

## Ist der Spieler linkshändig
Prüft, ob der Spieler in den Spieleinstellungen auf Linkshänder-Modus eingestellt ist.  
**Wert erforderlich**: Nein

## Ist Inventarslot gefüllt
Prüft, ob ein bestimmter Inventarslot ein Item enthält.  
**Wert erforderlich**: Ja - Slotnummer (0-35 für das Hauptinventar, Slots 0-8 sind die Hotbar)

## Ist Item im Inventar überfahren
Prüft, ob sich der Cursor über einem beliebigen Item in einem Inventarbildschirm befindet.
**Wert erforderlich**: Nein

## Hält der Cursor ein Inventar-Item
Prüft, ob der Cursor derzeit einen Inventar-Item-Stack hält.
**Wert erforderlich**: Nein

## Ist Hotbar-Slot ausgewählt
Prüft, ob ein bestimmter Hotbar-Slot aktuell ausgewählt ist.  
**Wert erforderlich**: Ja - Hotbar-Slotnummer (0-8)

## Hat der Spieler Berechtigungsstufe
Prüft, ob der Spieler auf der aktuellen Welt oder dem Server mindestens die angegebene Berechtigungs-/OP-Stufe hat.  
**Wert erforderlich**: Ja - Berechtigungsstufe (0-4, wobei 4 der Server-Operator ist)

## Ist Angriffsstärke abgeschwächt
Prüft, ob die Angriffsstärke des Spielers derzeit abgeschwächt ist (nicht vollständig aufgeladen).  
**Wert erforderlich**: Nein

## Ist reale Uhrzeit: Tag
Prüft, ob der aktuelle reale Kalendertag mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Tagesnummer (1-31). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist reale Uhrzeit: Stunde
Prüft, ob die aktuelle reale Stunde mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Stunde im 24-Stunden-Format (0-23). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist reale Uhrzeit: Minute
Prüft, ob die aktuelle reale Minute mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Minute (0-59). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist reale Uhrzeit: Monat
Prüft, ob der aktuelle reale Monat mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Monatsnummer (1-12, wobei 1 Januar ist). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist reale Uhrzeit: Sekunde
Prüft, ob die aktuelle reale Sekunde mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Sekunde (0-59). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist reale Uhrzeit: Wochentag
Prüft, ob der aktuelle reale Wochentag mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Wochentag als Zahl (1-7, wobei 1 Sonntag ist). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Ist reale Uhrzeit: Jahr
Prüft, ob das aktuelle reale Jahr mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Vollständiges Jahr (z. B. "2023"). Mehrere Werte können durch Kommas getrennt angegeben werden.

## Datei/Ordner existiert
Prüft, ob eine bestimmte Datei oder ein bestimmter Ordner auf dem System existiert.  
**Wert erforderlich**: Ja - Pfad zur Datei oder zum Ordner (absolut oder relativ zum Spielverzeichnis)

## Ist OS Linux
Prüft, ob das Betriebssystem Linux ist.  
**Wert erforderlich**: Nein

## Ist OS macOS
Prüft, ob das Betriebssystem macOS ist.  
**Wert erforderlich**: Nein

## Ist OS Windows
Prüft, ob das Betriebssystem Windows ist.  
**Wert erforderlich**: Nein

## Ist Internetverbindung verfügbar
Prüft, ob eine aktive Internetverbindung verfügbar ist.  
**Wert erforderlich**: Nein

## Ist Spielsprache
Prüft, ob die aktuelle Spielsprache einem bestimmten Wert entspricht.  
**Wert erforderlich**: Ja - Sprachcode (z. B. `en_us` für Englisch)

## Ist Mod geladen
Prüft, ob ein bestimmter Mod geladen ist.  
**Wert erforderlich**: Ja - Mod-ID (z. B. `fancymenu`, `jei`). Du kannst auch mit `optifine` nach Optifine prüfen. Mehrere Mod-IDs können durch Kommas getrennt angegeben werden.

## Ist MCEF geladen
Prüft, ob MCEF (Minecraft Chromium Embedded Framework) installiert und initialisiert ist.  
**Wert erforderlich**: Nein

## Ist Zahl
Bietet einen erweiterten Zahlenvergleich mit verschiedenen Vergleichsmodi.  
**Wert erforderlich**: Ja - Komplexes Format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` wobei `comparison_mode` `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` oder `smaller-than-or-equals` sein kann

## Ist Text
Bietet einen erweiterten Textvergleich mit verschiedenen Vergleichsmodi.  
**Wert erforderlich**: Ja - Komplexes Format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` wobei `comparison_mode` `equals`, `contains`, `starts-with` oder `ends-with` sein kann

## Ist Server-IP
Prüft, ob die aktuelle Server-IP mit einem bestimmten Wert übereinstimmt.  
**Wert erforderlich**: Ja - Server-IP-Adresse (mit oder ohne Port)

## Ist Server online
Prüft, ob ein bestimmter Server online und erreichbar ist.  
**Wert erforderlich**: Ja - Server-IP-Adresse (mit oder ohne Port)

## Ist Ressourcenpaket aktiviert
Prüft, ob ein bestimmtes Ressourcenpaket derzeit ausgewählt/aktiv ist.  
**Wert erforderlich**: Ja - Titel des Ressourcenpakets oder Paket-ID (z. B. `Programmer Art` oder die ID des Pakets)

## Ist Variablenwert (FM-Variable)
Prüft, ob eine FancyMenu-Variable einen bestimmten Wert hat.  
**Wert erforderlich**: Ja - Format: "variable_name:expected_value"

## Nur einmal pro Sitzung
Gibt nur einmal pro Spielsitzung true zurück. Nützlich für einmalige Ankündigungen oder Aktionen.  
**Wert erforderlich**: Nein
