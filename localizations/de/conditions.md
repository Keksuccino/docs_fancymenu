---
title: Voraussetzungen
description: >-
  Blende Elemente und Layouts ein und mache Schaltflächen anklickbar oder führe
  Aktionen nur dann aus, wenn etwas zutrifft, etwa die Uhrzeit, die Fenstergröße
  oder eine Variable.
sourceBlobSha: 8d7cc9e0182f8478f3a7ab86391e90cae12c626b
---

# Voraussetzungen

Voraussetzungen sind Bedingungen wie „die Maus befindet sich über dieser Schaltfläche“, „es ist Dezember“ oder „eine Welt ist geladen“. Verwende sie, um:

- ein [Element](/elements) nur manchmal anzuzeigen,
- ein ganzes Layout nur manchmal zu laden,
- Schaltflächen, Schieberegler und Kontrollkästchen nur manchmal anklickbar zu machen,
- Teile eines [Aktionsskripts](/action-scripts) nur manchmal auszuführen.

FancyMenu überprüft Voraussetzungen ständig, solange ein Menü geöffnet ist. Dadurch werden Dinge sofort ein- oder ausgeblendet oder geändert. Dieses Infokästchen wird nur angezeigt, wenn sich die Maus über „Mehrspieler“ befindet:

<img width="800" alt="Wenn die Maus über die Schaltfläche Mehrspieler auf dem Titelbildschirm bewegt wird, erscheint daneben ein Infokästchen mit einer Serveradresse" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_hover.gif?raw=true">

# Wo du sie findest

| Wo | Was die Voraussetzungen bewirken |
|---|---|
| Rechtsklick auf ein Element -> **Ladeanforderungen** | Das Element wird nur angezeigt, wenn sie erfüllt sind. Funktioniert auch mit [Vanilla-Elementen](/vanilla-elements). |
| Rechtsklick auf den Editorhintergrund -> **Ladeanforderungen [Layoutweit]** | Das ganze Layout wird nur geladen, wenn sie erfüllt sind. Siehe [Layoutweite Voraussetzungen](#layoutweite-voraussetzungen). |
| Rechtsklick auf eine Schaltfläche, einen Schieberegler oder ein Kontrollkästchen -> **Aktivzustand der Steuerung** | Das Element ist nur anklickbar, wenn sie erfüllt sind. Andernfalls ist es ausgegraut. Gibt es auch für Vanilla-Schaltflächen. |
| IF, ELSE-IF und WHILE in [Aktionsskripten](/action-scripts#statements) | Die darin enthaltenen Aktionen werden nur ausgeführt, wenn sie erfüllt sind. |

Im Layouteditor werden Elemente immer angezeigt, damit du sie weiterhin bearbeiten kannst. Voraussetzungen von Elementen gelten auch außerhalb des Editors.

> [!TIP]
> Unter [Element-Sichtbarkeit](/element-visibility) findest du weitere Möglichkeiten, Elemente ein- und auszublenden, etwa mit Verzögerungen, Überblendungen oder per Schaltfläche.

# Eine Voraussetzung hinzufügen

<img width="800" alt="Die ID der Schaltfläche Mehrspieler wird kopiert. Anschließend erhält das Infokästchen unter Voraussetzungen verwalten die Voraussetzung Element wird mit der Maus überfahren mit dieser ID" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_add.gif?raw=true">

1. Klicke mit der rechten Maustaste auf das Element und wähle **Ladeanforderungen**. **Voraussetzungen verwalten** wird geöffnet.
2. Klicke mit der rechten Maustaste auf die leere Liste und wähle **Voraussetzung hinzufügen** oder drücke `A`.
3. Klicke unter **Verfügbare Voraussetzungen** auf eine Kategorie oder beginne zu tippen, um Namen und Beschreibungen zu durchsuchen. Unter **Beschreibung der Voraussetzung** wird die ausgewählte Voraussetzung erklärt.
4. Klicke auf **Nächster Schritt**, um ihren Wert festzulegen. Voraussetzungen ohne Wert bieten stattdessen die Schaltfläche **Fertig**. Ein Doppelklick auf eine Voraussetzung hat dieselbe Wirkung.
5. Gib den Wert ein und klicke auf **Fertig**. Für **Element wird mit der Maus überfahren** benötigst du beispielsweise die ID des Elements. Klicke im Editor mit der rechten Maustaste auf ein Element und wähle **Element-ID kopieren**, um sie abzurufen.
6. Klicke unter **Voraussetzungen verwalten** auf **Fertig**.

## Voraussetzungsmodus

Mit der Schaltfläche **Voraussetzungsmodus** im Voraussetzungsfenster kannst du zwischen folgenden Modi wechseln:

- **Normal**: erfüllt, wenn die Bedingung zutrifft.
- **Umgekehrt**: erfüllt, wenn die Bedingung NICHT zutrifft. **Welt ist geladen** im umgekehrten Modus ist zum Beispiel nur im Hauptmenü erfüllt.

Unter **Voraussetzungen verwalten** werden der Modus und der Wert jeder Voraussetzung angezeigt.

## Werte

- Werte unterstützen [Platzhalter](/placeholders) und deine [Variablen](/variables#showing-variables-in-text), etwa `$$coins`. FancyMenu setzt sie bei jeder Überprüfung der Voraussetzung ein.
- Viele Wertfelder schlagen während der Eingabe passende Werte vor, etwa Biome, Mod-IDs, Sprachen oder die Namen deiner Variablen. Klicke auf einen Vorschlag oder drücke `Tab`.
- Bei Voraussetzungen mit einem einfachen Wert öffnet sich ein einzeiliger Texteditor. Sein Titel gibt an, was du eingeben sollst, etwa **Ziel-Element-ID**.

## Voraussetzungen verwalten

Klicke unter **Voraussetzungen verwalten** mit der rechten Maustaste auf die Liste, eine Voraussetzung oder eine Gruppe, um folgende Optionen aufzurufen:

| Option | Tastenkürzel | Funktion |
|---|---|---|
| **Voraussetzung hinzufügen** | `A` | Fügt eine Voraussetzung hinzu. |
| **Gruppe hinzufügen** | `G` | Fügt eine Gruppe hinzu (siehe unten). |
| **Voraussetzung bearbeiten** | `Enter` oder Doppelklick | Öffnet die Voraussetzungs-Auswahl mit Typ, Modus und Wert der Voraussetzung. |
| **Voraussetzung entfernen** / **Gruppe entfernen** | `Delete` | Entfernt die Voraussetzung oder Gruppe. |
| **Rückgängig** / **Wiederholen** | `Ctrl + Z` / `Ctrl + Y` | Macht Änderungen in diesem Fenster rückgängig oder stellt sie wieder her. |
| **Voraussetzungen für KI exportieren** | | Exportiert alle Voraussetzungen dieses Fensters für einen [KI-Chat](/export-for-ai), einschließlich deiner nicht gespeicherten Änderungen. |

Mit `Up` und `Down` wählst du die Voraussetzung darüber oder darunter aus. **Fertig** (`Ctrl + S`) speichert deine Änderungen, **Abbrechen** verwirft alle Änderungen, die du in diesem Fenster vorgenommen hast. Verwende unter macOS `Cmd` statt `Ctrl`.

Wenn mehrere Elemente ausgewählt sind, ändert **Ladeanforderungen** die Voraussetzungen für alle. Wenn sie unterschiedliche Voraussetzungen haben, fragt FancyMenu vorher nach, da alle Voraussetzungen ersetzt werden.

# Voraussetzungen kombinieren

Alle Voraussetzungen unter **Voraussetzungen verwalten** müssen erfüllt sein. Für eine Bedingung im Sinne von „dieses ODER jenes“ verwendest du eine Gruppe.

Eine Gruppe verhält sich wie eine einzelne Voraussetzung:

- **Und**-Modus: Alle Bedingungen in der Gruppe müssen erfüllt sein. Neue Gruppen beginnen in diesem Modus.
- **Oder**-Modus: Eine erfüllte Bedingung in der Gruppe genügt.

1. Klicke mit der rechten Maustaste auf die Liste und wähle **Gruppe hinzufügen** oder drücke `G`. Die Gruppe erhält einen Namen wie `group_1`.
2. Klicke mit der rechten Maustaste auf die Gruppe und wähle **Gruppenmodus**, um zwischen **Und** und **Oder** zu wechseln.
3. Klicke auf **Gruppen-Voraussetzungen bearbeiten** oder doppelklicke auf die Gruppe. Ein Fenster ähnlich wie **Voraussetzungen verwalten** wird geöffnet.
4. Füge die Voraussetzungen der Gruppe hinzu und klicke auf **Fertig**.

Ein Beispiel: Ein Weihnachtsgruß, der im Dezember oder dann angezeigt wird, wenn der Spieler `xmas_lights` aktiviert hat. Dafür brauchst du eine Oder-Gruppe mit **Echtzeitmonat ist** `12` und **Variablenwert ist (FM Variable)** für die Variable `xmas_lights` mit dem Wert `on`.

<img width="800" alt="Unter Voraussetzungen verwalten wird eine Gruppe hinzugefügt, auf Oder umgestellt und mit Echtzeitmonat ist sowie Variablenwert ist (FM Variable) ergänzt" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_group.gif?raw=true">

- Gruppen können weitere Gruppen enthalten, zum Beispiel für „(A und B) oder (C und D)“. Der Fenstertitel zeigt deine aktuelle Position an, etwa `Gruppe bearbeiten: group_1 › group_2`.
- Mit **Gruppenkennung bearbeiten** kannst du eine Gruppe umbenennen. Jeder Name darf nur einmal verwendet werden, auch innerhalb von Gruppen.
- Eine leere Gruppe im **Oder**-Modus ist nie erfüllt.

# Layoutweite Voraussetzungen

Layoutweite Voraussetzungen entscheiden, ob ein ganzes Layout geladen wird. Verwende sie für eine Nachtversion deines Titelbildschirms, ein Layout pro Sprache oder ein Layout, das nur im Einzelspieler angezeigt wird.

Klicke mit der rechten Maustaste auf den Editorhintergrund und wähle **Ladeanforderungen [Layoutweit]**. Du findest die Option auch unter **Menüleiste -> Layout -> Layouteigenschaften**.

- Ändert sich das Ergebnis, solange das Menü geöffnet ist, baut FancyMenu den Bildschirm mit den Layouts neu auf, deren Voraussetzungen jetzt erfüllt sind.
- Sie funktionieren auch mit [universellen Layouts](/universal-layouts).
- Um ein Layout per Schaltfläche ein- und auszuschalten, füge die Schaltfläche in ein anderes Layout ein. Siehe [Layouts ein- und ausschalten](/element-visibility#turning-layouts-on-and-off).

# Wissenswertes

- Welt- und Spielervoraussetzungen sind nie erfüllt, wenn keine Welt geladen ist, etwa im Hauptmenü.
- Voraussetzungen für Elemente, den Mauszeiger, Inventare, den Spieler und die Welt funktionieren nicht in einem [Ticker](/elements#ticker), wenn **Asynchron** aktiviert ist. FancyMenu zeigt dann eine Fehlermeldung mit dem Namen der Voraussetzung an.
- Voraussetzungen von entfernten Add-ons werden übersprungen. Wenn du das Layout im Editor speicherst, werden sie endgültig entfernt.
- Unter **Menüleiste -> Anpassung -> Einstellungen -> Dauer der Voraussetzungszwischenspeicherung [MS]** kannst du die Ergebnisse von Voraussetzungen für einige Millisekunden wiederverwenden. Das beschleunigt große Layouts. `0` deaktiviert die Zwischenspeicherung; dies ist die Standardeinstellung. Die Zwischenspeicherung kann dazu führen, dass sich Aktionsskripte und schnelle Änderungen unerwartet verhalten.

# Alle Voraussetzungen

Die Voraussetzungen sind wie im Voraussetzungsfenster sortiert: zuerst nach Kategorie, dann nach Name. Voraussetzungen ohne Kategorie stehen dort ganz unten und hier unter [Sonstiges](#sonstiges).

## GUI

### Aktiver Cursortyp ist

**Kennung:** `is_active_cursor_type`

Erfüllt, solange der Mauszeiger eine bestimmte Form hat, zum Beispiel **Zeigehand** über einem Link oder **Textcursor** über einem Textfeld.

- Wert: Klicke auf **Cursortyp**, um **Normal**, **Textcursor**, **Fadenkreuz**, **Zeigehand**, **Horizontal skalieren**, **Vertikal skalieren**, **NW-SE skalieren**, **NE-SW skalieren**, **In alle Richtungen skalieren** oder **Nicht erlaubt** auszuwählen.

### Beliebige Schaltfläche wird mit der Maus überfahren

**Kennung:** `fancymenu_visibility_requirement_is_any_button_hovered`

Erfüllt, solange sich die Maus über einer beliebigen sichtbaren Schaltfläche befindet, egal ob Vanilla oder benutzerdefiniert.

### Beliebiges Element wird mit der Maus überfahren

**Kennung:** `fancymenu_visibility_requirement_is_any_element_hovered`

Erfüllt, solange sich die Maus über einem beliebigen sichtbaren Element befindet, nicht nur über Schaltflächen.

### Beliebiger Bildschirm ist geöffnet

**Kennung:** `is_any_screen_open`

Erfüllt, solange ein beliebiges Menü geöffnet ist, etwa das Pausenmenü oder das Inventar. Nicht erfüllt, wenn du ohne geöffnetes Menü spielst.

### Schaltfläche ist aktiv

**Kennung:** `fancymenu_visibility_requirement_is_button_active`

Erfüllt, solange eine Schaltfläche anklickbar ist.

- Wert: die [Element-ID](/element-identifiers) der Schaltfläche. Klicke im Editor mit der rechten Maustaste darauf und wähle **Element-ID kopieren**.

### Menüleiste der Anpassung ist sichtbar

**Kennung:** `is_customization_menu_bar_visible`

Erfüllt, solange die Menüleiste von FancyMenu angezeigt wird. Nicht erfüllt im Modpack-Modus oder wenn die Menüleiste ausgeschaltet ist.

### Element hat Fokus

**Kennung:** `is_element_focused`

Erfüllt, solange ein Element den Fokus hat. Schaltflächen und Schieberegler erhalten den Fokus, wenn du darauf klickst oder sie mit den Pfeiltasten oder `Tab` auswählst. Die Auswahl per Tastatur gilt nicht als Überfahren mit der Maus. Füge diese Voraussetzung und **Element wird mit der Maus überfahren** daher für Spieler, die die Tastatur verwenden, in eine [Oder-Gruppe](#voraussetzungen-kombinieren) ein.

- Wert: die [Element-ID](/element-identifiers), etwa `mc_titlescreen_multiplayer_button`.

### Element wird mit der Maus überfahren

**Kennung:** `fancymenu_visibility_requirement_is_element_hovered`

Erfüllt, solange sich die Maus über einem Element befindet. Das Element muss sichtbar sein.

- Wert: die [Element-ID](/element-identifiers), etwa `mc_titlescreen_multiplayer_button` für die Mehrspieler-Schaltfläche auf dem Titelbildschirm. Klicke im Editor mit der rechten Maustaste auf ein Element und wähle **Element-ID kopieren**, um sie abzurufen.

### Element ist bis zum Ende gescrollt

**Kennung:** `is_scroll_area_scrolled_to_end`

Erfüllt, wenn ein [scrollbarer Bereich](/scrollable-areas) oder ein Textelement ganz nach unten gescrollt wurde. Ein Element, in dem nicht gescrollt werden kann, gilt als bis zum Ende gescrollt. Nützlich für eine **Akzeptieren**-Schaltfläche, die erst funktioniert, nachdem der Spieler die Regeln durchgescrollt hat.

- Wert: die [Element-ID](/element-identifiers) des scrollbaren Bereichs oder Textelements.

### GUI-Skalierung ist

**Kennung:** `fancymenu_loading_requirement_is_gui_scale`

Erfüllt, wenn die GUI-Skalierung von Minecraft übereinstimmt.

- Wert: eine Zahl wie `2` für genau diese Skalierung, `>2` für größer als 2, `<4` für kleiner als 4. Dezimalzahlen funktionieren ebenfalls, etwa `<3.5`.
- Trenne mehrere Bedingungen durch Kommas. Bei einfachen Zahlen muss eine davon übereinstimmen, etwa `2,3`. Alle Bedingungen mit `>` und `<` müssen erfüllt sein, etwa `>1,<4`.

### Taste wird gedrückt

**Kennung:** `is_key_pressed`

Erfüllt, solange eine Taste gedrückt gehalten wird. Um Aktionen einmal pro Tastendruck auszuführen, verwende stattdessen den Listener [**Bei Tastendruck**](/listeners#on-keyboard-key-pressed).

- Wert: Klicke unter **Tastenauswahl** auf **Taste ändern** und drücke die gewünschte Taste.

### Layout ist aktiviert

**Kennung:** `fancymenu_visibility_requirement_is_layout_enabled`

Erfüllt, solange ein Layout aktiviert ist.

- Wert: der Name des Layouts, etwa `winter_title_screen`.

### Minecraft-Debug-Overlay ist aktiviert

**Kennung:** `is_debug_overlay_enabled`

Erfüllt, solange der Debugbildschirm mit F3 angezeigt wird. Nicht erfüllt, wenn die HUD-Anzeige mit F1 ausgeblendet ist.

### Modpack-Modus ist aktiviert

**Kennung:** `is_modpack_mode_enabled`

Erfüllt, solange der Modpack-Modus von FancyMenu aktiviert ist.

### Bildschirmtitel ist

**Kennung:** `is_menu_title`

Erfüllt, wenn der Titel des geöffneten Bildschirms übereinstimmt, etwa „Optionen“ oder „Spielmenü“. Gemeint ist der Titel, den Spieler sehen, nicht die [Bildschirmkennung](/screen-identifiers).

- Wert: der Titeltext oder sein Lokalisierungsschlüssel, etwa `options.title`. Das Wertefenster zeigt beides für den Bildschirm, den du bearbeitest, und schlägt Lokalisierungsschlüssel vor.
- Lokalisierungsschlüssel funktionieren in jeder Sprache. Titeltexte müssen exakt übereinstimmen.

## Echtzeit

Diese Voraussetzungen überprüfen die Uhr des Computers des Spielers. Trenne mehrere Werte durch Kommas: Einer davon muss übereinstimmen.

### Echtzeittag ist

**Kennung:** `fancymenu_visibility_requirement_is_realtime_day`

Erfüllt an bestimmten Tagen des Monats.

- Wert: `1` bis `31`, etwa `24,25,26`.

### Echtzeitstunde ist

**Kennung:** `fancymenu_visibility_requirement_is_realtime_hour`

Erfüllt zu bestimmten Stunden.

- Wert: `0` bis `23`, etwa `20,21,22,23` für den Abend.

### Echtzeitminute ist

**Kennung:** `fancymenu_visibility_requirement_is_realtime_minute`

Erfüllt zu bestimmten Minuten einer Stunde.

- Wert: `0` bis `59`.

### Echtzeitmonat ist

**Kennung:** `fancymenu_visibility_requirement_is_realtime_month`

Erfüllt in bestimmten Monaten.

- Wert: `1` (Januar) bis `12` (Dezember), etwa `12` für Weihnachten.

### Echtzeitsekunde ist

**Kennung:** `fancymenu_visibility_requirement_is_realtime_second`

Erfüllt zu bestimmten Sekunden einer Minute.

- Wert: `0` bis `59`.

### Echtzeitwochentag ist

**Kennung:** `fancymenu_visibility_requirement_is_realtime_week_day`

Erfüllt an bestimmten Wochentagen.

- Wert: `1` (Sonntag) bis `7` (Samstag), etwa `1,7` für das Wochenende.

### Echtzeitjahr ist

**Kennung:** `fancymenu_visibility_requirement_is_realtime_year`

Erfüllt in bestimmten Jahren.

- Wert: das vollständige Jahr, etwa `2027`.

## System

### Datei/Ordner existiert

**Kennung:** `fancymenu_loading_requirement_file_exists`

Erfüllt, wenn eine Datei oder ein Ordner vorhanden ist.

- Wert: ein Pfad im Spielordner, etwa `config/mymodpack/welcome_seen.txt`. Pfade, die mit `.minecraft/` beginnen, verweisen auf den standardmäßigen `.minecraft`-Ordner.

### Internetverbindung ist verfügbar

**Kennung:** `is_internet_connection_available`

Erfüllt, solange der Computer online ist. FancyMenu überprüft dies regelmäßig im Hintergrund.

### Betriebssystem ist Linux

**Kennung:** `fancymenu_loading_requirement_is_os_linux`

Erfüllt unter Linux. Technisch gesehen gilt dies für alle Systeme, die weder Windows noch macOS sind.

### Betriebssystem ist macOS

**Kennung:** `fancymenu_loading_requirement_is_os_macos`

Erfüllt unter macOS.

### Betriebssystem ist Windows

**Kennung:** `fancymenu_loading_requirement_is_os_windows`

Erfüllt unter Windows.

### Scheduler läuft

**Kennung:** `fancymenu_visibility_requirement_is_scheduler_running`

Erfüllt, solange ein [Scheduler](/schedulers) läuft.

- Wert: die Kennung des Schedulers, etwa `my_scheduler`.

## Fenster

Fenstergrößen werden in tatsächlichen Pixeln des Spielfensters angegeben, nicht in GUI-Pixeln. Die Beschreibung der Voraussetzung zeigt die aktuelle Größe an.

### Vollbild ist aktiviert

**Kennung:** `fancymenu_loading_requirement_is_fullscreen`

Erfüllt, solange das Spiel im Vollbildmodus läuft.

### Fensterhöhe ist

**Kennung:** `fancymenu_loading_requirement_is_window_height`

Erfüllt, wenn das Fenster eine bestimmte Höhe hat.

- Wert: die Höhe, etwa `1080`. Trenne mehrere Höhen durch Kommas: Eine davon muss übereinstimmen.

### Fensterhöhe ist größer als

**Kennung:** `fancymenu_loading_requirement_is_window_height_bigger_than`

Erfüllt, solange das Fenster höher als eine bestimmte Höhe ist.

- Wert: die Höhe, etwa `1080`.

### Fensterbreite ist

**Kennung:** `fancymenu_loading_requirement_is_window_width`

Erfüllt, wenn das Fenster eine bestimmte Breite hat.

- Wert: die Breite, etwa `1920`. Trenne mehrere Breiten durch Kommas: Eine davon muss übereinstimmen.

### Fensterbreite ist größer als

**Kennung:** `fancymenu_loading_requirement_is_window_width_bigger_than`

Erfüllt, solange das Fenster breiter als eine bestimmte Breite ist.

- Wert: die Breite, etwa `1920`.

## Welt

Diese Voraussetzungen sind nie erfüllt, wenn keine Welt geladen ist. **Spieler befindet sich in Struktur** und **Spieler befindet sich in aktivem Plünderungsgebiet** setzen FancyMenu auf dem Server voraus. Im Einzelspieler funktionieren sie immer.

### Spieler hat Absorptionsherzen

**Kennung:** `has_player_absorption_hearts`

Erfüllt, solange der Spieler goldene Absorptionsherzen hat.

### Spieler hat Berechtigungsstufe

**Kennung:** `fancymenu_loading_requirement_has_player_permission_level`

Erfüllt, wenn der Spieler in der Welt oder auf dem Server mindestens die angegebene Berechtigungsstufe hat, etwa als Operator.

- Wert: `0` bis `4`. `0` ist immer erfüllt, `2` reicht für Befehle wie `/gamemode`, und `4` ist die Stufe, die der Befehl `/op` vergibt.

### Spielmodus ist Abenteuer

**Kennung:** `fancymenu_visibility_requirement_is_adventure`

Erfüllt, solange sich der Spieler im Abenteuermodus befindet.

### Beliebiger Effekt ist aktiv

**Kennung:** `is_any_effect_active`

Erfüllt, solange der Spieler einen beliebigen Effekt hat, etwa Schnelligkeit oder Vergiftung.

### Angriffsstärke ist geschwächt

**Kennung:** `is_attack_strength_weakened`

Erfüllt, solange der Angriff des Spielers nicht vollständig aufgeladen ist. Dann wird die Angriffsanzeige eingeblendet.

### Block/Item ist in Tag

**Kennung:** `is_in_tag`

Erfüllt, wenn ein Block oder Item zu einem Tag gehört, etwa `minecraft:logs` oder `c:tools`. Tags sind nur vorhanden, solange eine Welt geladen ist.

- Wert: Klicke auf **Tag-Typ**, um **Block** oder **Item** auszuwählen. Gib dann den **Block-/Item-Schlüssel** und den **Tag** ein. Beide Felder schlagen Werte vor. Das `#` vor dem Tag ist optional.
- Der Schlüssel funktioniert gut mit Listener-Variablen wie `$$block_key`. So kann eine IF-Anweisung im Skript des Listeners [**Bei Blockzerstörung**](/listeners#on-block-broke) beispielsweise nur für Holzstämme eine Einblendung anzeigen.

### Kameraperspektive ist

**Kennung:** `is_camera_perspective`

Erfüllt, solange die Kamera eine bestimmte Perspektive hat (F5).

- Wert: Klicke auf die Schaltfläche, um **Ego-Perspektive**, **Dritte Person** oder **Ansicht von vorne** auszuwählen.

### Wetter ist klar

**Kennung:** `is_clear_weather`

Erfüllt, solange es weder regnet noch gewittert.

### Spielmodus ist Kreativ

**Kennung:** `fancymenu_visibility_requirement_is_creative`

Erfüllt, solange sich der Spieler im Kreativmodus befindet.

### Cursor hält Inventargegenstand

**Kennung:** `is_cursor_holding_inventory_item`

Erfüllt, solange der Mauszeiger in einem Inventarbildschirm einen Gegenstand trägt.

### Schwierigkeitsgrad ist

**Kennung:** `is_difficulty`

Erfüllt, wenn die Welt den angegebenen Schwierigkeitsgrad hat.

- Wert: `peaceful`, `easy`, `normal` oder `hard`.

### Effekt ist aktiv

**Kennung:** `is_effect_active`

Erfüllt, solange der Spieler einen bestimmten Effekt hat.

- Wert: der Schlüssel des Effekts, etwa `minecraft:speed`. Wenn du dich in einer Welt befindest, schlägt das Feld Effekte vor.

### Entität ist in der Nähe

**Kennung:** `is_entity_nearby`

Erfüllt, solange sich eine Entität eines bestimmten Typs in der Nähe des Spielers befindet.

- Wert: der **Entitäts-Registrierungsschlüssel**, etwa `minecraft:creeper`, und der **Prüfradius in Blöcken**, etwa `10`. Wenn du dich in einer Welt befindest, schlägt das Schlüsselfeld Entitäten vor.

### Spielmodus ist

**Kennung:** `is_gamemode`

Erfüllt, solange sich der Spieler in einem bestimmten Spielmodus befindet.

- Wert: `survival`, `creative`, `adventure` oder `spectator`.

### Hardcore ist aktiviert

**Kennung:** `is_hardcore`

Erfüllt in Hardcore-Welten.

### Hotbar-Slot ist ausgewählt

**Kennung:** `is_hotbar_slot_active`

Erfüllt, solange ein bestimmter Hotbar-Slot ausgewählt ist.

- Wert: `0` (der linke Slot) bis `8`.

### Spieler befindet sich in aktivem Plünderungsgebiet

**Kennung:** `is_in_active_raid_area`

Erfüllt, solange sich der Spieler im Gebiet eines Plünderungszugs befindet, in dem die Fortschrittsleiste angezeigt wird. Setzt FancyMenu auf dem Server voraus.

### Inventar-Slot ist belegt

**Kennung:** `is_inventory_slot_filled`

Erfüllt, solange sich in einem Slot des Spielerinventars ein Gegenstand befindet.

- Wert: die Slotnummer. `0` bis `8` sind die Hotbar, `9` bis `35` der Rest des Inventars.

### Gegenstand im Inventar wird mit der Maus überfahren

**Kennung:** `is_item_hovered_in_inventory`

Erfüllt, solange sich die Maus in einem Inventarbildschirm über einem Gegenstand befindet, etwa im Spielerinventar oder in einer Truhe.

### Mehrspieler ist aktiviert

**Kennung:** `fancymenu_loading_requirement_is_multiplayer`

Erfüllt, solange der Spieler auf einem Server ist.

### Spieler fliegt im Kreativmodus

**Kennung:** `is_player_creative_flying`

Erfüllt, solange der Spieler im Kreativmodus fliegt.

### Spieler fliegt mit Elytren

**Kennung:** `is_player_flying_with_elytra`

Erfüllt, solange der Spieler mit einer Elytra gleitet.

### Spieler ist vollständig gefroren

**Kennung:** `is_player_fully_frozen`

Erfüllt, solange der Spieler durch Pulverschnee vollständig gefroren ist und gefrorene Herzen in der Lebensanzeige angezeigt werden.

### Spieler befindet sich in Biom

**Kennung:** `is_player_in_biome`

Erfüllt, solange sich der Spieler in einem bestimmten Biom befindet.

- Wert: der Schlüssel des Bioms, etwa `minecraft:birch_forest`. Wenn du dich in einer Welt befindest, schlägt das Feld Biome vor.

### Spieler befindet sich in Dimension

**Kennung:** `is_player_in_dimension`

Erfüllt, solange sich der Spieler in einer bestimmten Dimension befindet.

- Wert: der Schlüssel der Dimension: `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end` oder der Schlüssel einer Mod-Dimension. Wenn du dich in einer Welt befindest, schlägt das Feld Dimensionen vor.

### Spieler befindet sich in Flüssigkeit

**Kennung:** `is_player_in_fluid`

Erfüllt, solange sich der Spieler in einer beliebigen Flüssigkeit wie Wasser oder Lava befindet.

### Spieler befindet sich in Lava

**Kennung:** `is_player_in_lava`

Erfüllt, solange sich der Spieler in Lava befindet.

### Spieler befindet sich in Pulverschnee

**Kennung:** `is_player_in_powder_snow`

Erfüllt, solange sich der Spieler in Pulverschnee befindet.

### Spieler befindet sich in Struktur

**Kennung:** `is_player_in_structure`

Erfüllt, solange sich der Spieler in einer bestimmten Struktur befindet. Setzt FancyMenu auf dem Server voraus.

- Wert: der Schlüssel der Struktur, etwa `minecraft:village_plains`. Wenn du dich in einer Welt befindest, schlägt das Feld Strukturen vor.

### Spieler befindet sich in Wasser

**Kennung:** `is_player_in_water`

Erfüllt, solange sich der Spieler ganz oder teilweise im Wasser befindet.

### Spieler springt oder fällt

**Kennung:** `is_player_jumping`

Erfüllt, solange sich der Spieler in der Luft befindet. Schwimmen, Flüssigkeiten, Elytrenflug, Schlafen und Kriechen zählen nicht dazu.

### Spieler ist Linkshänder

**Kennung:** `is_left_handed`

Erfüllt, wenn unter den Skin-Anpassungsoptionen von Minecraft für „Haupthand“ die Einstellung „Links“ ausgewählt ist.

### Spieler ist vergiftet

**Kennung:** `is_player_poisoned`

Erfüllt, solange der Spieler den Effekt Vergiftung hat und vergiftete Herzen in der Lebensanzeige angezeigt werden.

### Spieler reitet Entität mit Lebensanzeige

**Kennung:** `is_player_riding_entity_with_health`

Erfüllt, solange der Spieler auf einer Kreatur reitet, etwa einem Pferd oder Schwein. Boote und Loren zählen nicht dazu.

### Spieler reitet Entität/Fahrzeug

**Kennung:** `is_player_riding_entity`

Erfüllt, solange der Spieler auf etwas reitet, etwa einem Pferd, Boot oder einer Lore.

### Spieler reitet springfähige Entität

**Kennung:** `is_player_riding_jumpable_entity`

Erfüllt, solange der Spieler auf einer Entität reitet, die springen kann, etwa einem Pferd.

### Spieler rennt

**Kennung:** `is_player_running`

Erfüllt, solange der Spieler sprintet.

### Spieler schleicht

**Kennung:** `is_player_sneaking`

Erfüllt, solange der Spieler schleicht.

### Spieler schwimmt

**Kennung:** `is_player_swimming`

Erfüllt, solange der Spieler schwimmt.

### Spieler ist unter Wasser

**Kennung:** `is_player_under_water`

Erfüllt, solange sich der Kopf des Spielers unter Wasser befindet.

### Spieler benutzt Gegenstand

**Kennung:** `is_player_using_item`

Erfüllt, solange der Spieler einen Gegenstand benutzt, etwa isst, einen Trank trinkt oder einen Bogen spannt.

### Spieler trägt Kürbis

**Kennung:** `is_player_wearing_pumpkin`

Erfüllt, solange der Spieler einen geschnitzten Kürbis auf dem Kopf trägt.

### Spieler ist vom Wither-Effekt betroffen

**Kennung:** `is_player_withered`

Erfüllt, solange der Spieler den Wither-Effekt hat und Wither-Herzen in der Lebensanzeige angezeigt werden.

### Es regnet

**Kennung:** `is_raining`

Erfüllt, solange es am Standort des Spielers regnet.

### Einzelspieler ist aktiviert

**Kennung:** `fancymenu_loading_requirement_is_singpleplayer`

Erfüllt, solange sich der Spieler in einer Einzelspielerwelt befindet.

### Es schneit

**Kennung:** `is_snowing`

Erfüllt, solange es am Standort des Spielers schneit.

### Spielmodus ist Zuschauermodus

**Kennung:** `fancymenu_visibility_requirement_is_spectator`

Erfüllt, solange sich der Spieler im Zuschauermodus befindet.

### Spielmodus ist Überleben

**Kennung:** `fancymenu_visibility_requirement_is_survival`

Erfüllt, solange sich der Spieler im Überlebensmodus befindet.

### Es gewittert

**Kennung:** `is_thundering`

Erfüllt während eines Gewitters.

### Welt ist geladen

**Kennung:** `fancymenu_loading_requirement_is_world_loaded`

Erfüllt, solange sich der Spieler in einer Welt befindet, egal ob im Einzel- oder Mehrspieler.

### Spieler befand sich in Pulverschnee

**Kennung:** `was_player_in_powder_snow`

Erfüllt, wenn sich der Spieler kurz zuvor in Pulverschnee befand.

## Sonstiges

### Spielsprache ist

**Kennung:** `fancymenu_loading_requirement_is_language`

Erfüllt, wenn Minecraft eine bestimmte Sprache verwendet.

- Wert: der Sprachcode, etwa `en_us` oder `de_de`. Das Feld schlägt alle Sprachen vor.

### Mod ist geladen

**Kennung:** `fancymenu_loading_requirement_is_mod_loaded`

Erfüllt, wenn bestimmte Mods installiert sind.

- Wert: die Mod-ID, etwa `jei`. Das Feld schlägt die IDs deiner Mods vor. Trenne mehrere IDs durch Kommas: Alle angegebenen Mods müssen installiert sein. `optifine` prüft, ob OptiFine installiert ist.

### Zahl ist

**Kennung:** `fancymenu_visibility_requirement_is_number`

Vergleicht zwei Zahlen. Füge Platzhalter oder Variablen in die Felder ein, etwa `$$coins`.

- **Vergleichsmodus**: **Ist gleich**, **Ist größer als**, **Ist kleiner als**, **Ist größer oder gleich** oder **Ist kleiner oder gleich**.
- **Zahl**: die zu prüfende Zahl, etwa `$$coins`.
- **Vergleichen mit Zahl**: die Zahl, mit der verglichen wird, etwa `100`.

Dezimalzahlen funktionieren ebenfalls, etwa `2.5`. Wenn ein Feld keine Zahl enthält, ist die Voraussetzung nie erfüllt.

### Ressourcenpaket ist aktiviert

**Kennung:** `is_resource_pack_enabled`

Erfüllt, solange ein Ressourcenpaket aktiviert ist.

- Wert: der Name des Pakets, wie er im Bildschirm „Ressourcenpakete“ angezeigt wird, etwa `Programmer Art`, oder seine ID. Groß- und Kleinschreibung werden nicht berücksichtigt.

### Rinku ist geladen

**Kennung:** `is_rinku_loaded`

Erfüllt, wenn die Mod [Rinku](https://modrinth.com/mod/rinku) installiert ist. Das [Browser-Element](/elements#browser) und die älteren [videobasierten Rinku-Typen](/video#requirements) benötigen sie.

### Server-IP ist

**Kennung:** `fancymenu_visibility_requirement_is_server_ip`

Erfüllt, solange sich der Spieler auf einem bestimmten Server befindet.

- Wert: die Adresse des Servers, etwa `play.example.net`. Bei einer Adresse mit Port, etwa `play.example.net:25566`, muss auch der Port übereinstimmen.

### Server ist online

**Kennung:** `fancymenu_loading_requirement_is_server_online`

Erfüllt, solange ein Server online ist. FancyMenu sendet etwa alle 30 Sekunden eine Ping-Anfrage im Hintergrund. Daher kann es nach dem Spielstart einen Moment dauern.

- Wert: die Adresse des Servers, etwa `play.example.net`.

### Text ist

**Kennung:** `fancymenu_visibility_requirement_is_text`

Vergleicht zwei Texte. Füge Platzhalter oder Variablen in die Felder ein, etwa `$$key_name`.

- **Vergleichsmodus**: **Ist gleich**, **Enthält**, **Beginnt mit** oder **Endet mit**.
- **Text**: der zu prüfende Text.
- **Vergleichen mit Text**: der Text, mit dem verglichen wird.

Groß- und Kleinschreibung werden berücksichtigt.

### Variablenwert ist (FM Variable)

**Kennung:** `fancymenu_visibility_requirement_is_variable_value`

Erfüllt, wenn eine deiner [Variablen](/variables) einen bestimmten Wert hat.

- **Variablenname**: der Name der Variable ohne `$$`. Das Feld schlägt deine Variablen vor.
- **Zu prüfender Variablenwert**: der Wert, etwa `on`. Er muss vollständig übereinstimmen; Groß- und Kleinschreibung werden berücksichtigt.

Nicht erfüllt, wenn die Variable nicht existiert. Bei einer Listenvariable wird das JSON-Array aller Einträge verglichen, etwa `["apple","banana"]`. Um einen einzelnen Eintrag zu prüfen, verwende **Liste enthält Eintrag (FM Variable)**.

### Liste enthält Eintrag (FM Variable)

**Kennung:** `list_contains_entry`

Erfüllt, wenn eine [Listenvariable](/variables#text-and-list-variables) einen bestimmten Eintrag enthält.

- **Name der Listenvariable**: der Name der Liste ohne `$$`. Das Feld schlägt deine Listenvariablen vor und warnt dich, wenn du den Namen einer Textvariable eingibst.
- **Zu suchender Eintrag**: der Eintrag. Er muss vollständig mit einem Eintrag übereinstimmen, nicht nur mit einem Teil davon.
- **Groß-/Kleinschreibung ignorieren**: Wenn diese Option aktiviert ist, stimmt `Apple` auch mit `apple` überein.

Nicht erfüllt, wenn die Liste nicht existiert.

### Maustaste wird gedrückt

**Kennung:** `mouse_click`

Erfüllt, solange eine Maustaste gedrückt gehalten wird. Um Aktionen einmal pro Klick auszuführen, verwende stattdessen den Listener [**Bei Mausklick**](/listeners#on-mouse-button-clicked).

- Wert: `left` oder `right`.

### Nur einmal pro Sitzung

**Kennung:** `once_per_session`

Beim ersten Überprüfen erfüllt, danach bis zum nächsten Spielstart nie wieder. Jede Kopie dieser Voraussetzung wird separat behandelt.

Für Elemente, die nur einmal pro Spielsitzung angezeigt werden sollen, ist die Option [**Einmal pro Sitzung laden**](/element-visibility#load-once-per-session) einfacher: Die Elemente bleiben sichtbar, bis ein neuer Bildschirm geöffnet wird.
