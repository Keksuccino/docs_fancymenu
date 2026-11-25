---
title: Aktionsskripte
description: >-
  Mit Aktionsskripten kannst du Schaltflächen und Menüs Aktionen ausführen
  lassen. Hier findest du alle Aktionen von FancyMenu.
sourceBlobSha: 07ed5af6f189a91c518131cf3a7ab7a1e0a8305d
---

# Aktionsskripte

Ein Aktionsskript ist eine Liste von Dingen, die FancyMenu ausführt, wenn etwas passiert, zum Beispiel wenn eine Schaltfläche angeklickt oder ein Menü geöffnet wird. Jedes einzelne Element ist eine Aktion: ein Menü öffnen, einem Server beitreten, eine Nachricht anzeigen, einen Ton abspielen und vieles mehr. Anweisungen wie IF und WHILE legen fest, welche Aktionen ausgeführt werden und wie oft.

> [!CAUTION]
> Aktionsskripte können Dateien ändern, Server kontaktieren, Links öffnen und Befehle ausführen. Verwende nur Skripte aus Layouts, denen du vertraust.

<img width="800" alt="Das Aktionsskript einer Schaltfläche wird im Layout-Editor erstellt: Aktionsskript bearbeiten, die Aktionsauswahl mit Toast anzeigen sowie Titel und Nachricht des Toasts" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_make.gif?raw=true">

# Ein Aktionsskript erstellen

1. Klicke im Layout-Editor mit der rechten Maustaste auf eine Schaltfläche und wähle **Aktionsskript bearbeiten**.
2. Drücke `A`, um die Aktionsauswahl zu öffnen.
3. Suche nach der Aktion, klicke darauf und wähle **Nächster Schritt**.
4. Richte die Aktion im Fenster ein und klicke auf **Fertig**. Bei Aktionen ohne Einstellungen musst du nur in der Auswahl auf **Fertig** klicken.
5. Klicke im Skript-Editor auf **Fertig** und speichere anschließend das Layout.

Außerhalb des Editors wird das Skript der Schaltfläche ausgeführt, wenn du sie anklickst:

<img width="800" alt="Ein Klick auf die Schaltfläche Was gibt's Neues? auf dem Titelbildschirm zeigt einen Toast mit dem Titel und der Nachricht zum Update" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_use.gif?raw=true">

> [!TIP]
> Klicke mit der rechten Maustaste auf den Skriptbereich und wähle **Aktion hinzufügen**, um eine Liste aller Aktionen zu öffnen. Klicke in der Liste mit der rechten Maustaste auf eine Aktion, um sie zu den Favoriten hinzuzufügen. Sie wird dann oben angezeigt.

# Wo du Aktionsskripte verwenden kannst

| Wo | Wird ausgeführt, wenn | Wo du es bearbeiten kannst |
|---|---|---|
| [Schaltfläche](/elements#button) | Die Schaltfläche angeklickt wird. | Rechtsklick auf die Schaltfläche -> **Aktionsskript bearbeiten** |
| [Schieberegler](/elements#slider) | Der Wert des Schiebereglers geändert wird. `$$value` ist der neue Wert. | Rechtsklick auf den Schieberegler -> **Aktionsskript bearbeiten** |
| [Kontrollkästchen](/elements#checkbox) | Das Kontrollkästchen aktiviert oder deaktiviert wird. `$$value` ist der neue Zustand: `true` oder `false`. | Rechtsklick auf das Kontrollkästchen -> **Aktionsskript bearbeiten** |
| [Ticker](/elements#ticker) | Entsprechend dem **Tick-Modus**: immer wieder, einmal pro Spielsitzung oder einmal beim Laden des Menüs. | Rechtsklick auf den Ticker -> **Aktionsskript bearbeiten** |
| Menü öffnen | Das Menü des Layouts geöffnet wird. | Rechtsklick auf den Editor-Hintergrund -> **Aktionsskript „Bildschirm öffnen“ bearbeiten** |
| Menü schließen | Das Menü des Layouts geschlossen wird. | Rechtsklick auf den Editor-Hintergrund -> **Aktionsskript „Bildschirm schließen“ bearbeiten** |
| [Listener](/listeners) | Das zugehörige Ereignis eintritt, zum Beispiel ein Tastendruck oder eine Chatnachricht. | **Menüleiste -> Anpassung -> Listener verwalten** |
| [Scheduler](/schedulers) | Der Timer abläuft, auch wenn kein Menü geöffnet ist. | **Menüleiste -> Anpassung -> Scheduler verwalten** |

Die Skripte zum Öffnen und Schließen findest du auch im Menü **Layout -> Layouteigenschaften** des Editors.

# Der Skript-Editor

- Aktionen werden von oben nach unten ausgeführt. Einträge innerhalb einer Anweisung oder eines Ordners sind darunter eingerückt.
- Neue Einträge werden unter dem ausgewählten Eintrag eingefügt. Ist eine Anweisung oder ein Ordner ausgewählt, werden sie am Anfang eingefügt.
- Doppelklicke auf einen Wert, um ihn direkt in der Liste zu bearbeiten. Bei Werten, die eine kurze Zusammenfassung anzeigen, wird stattdessen das entsprechende Fenster geöffnet.
- Ziehe Einträge an eine andere Stelle, um sie zu verschieben. IF-Ketten, Schleifen und Ordner lassen sich über den kleinen Schalter davor einklappen. Das ändert nur die Ansicht.
- Die Leiste rechts zeigt eine Übersicht über das gesamte Skript. Klicke darauf, um zu einem Abschnitt zu springen.
- Über einen Rechtsklick im Skriptbereich findest du weitere Optionen, etwa zum Hinzufügen von Anweisungen und **Aktionsskript für KI exportieren** (siehe [Für KI exportieren](/export-for-ai)).
- Mit **Abbrechen** oder beim Schließen des Fensters werden deine Änderungen verworfen. Wenn du Änderungen vorgenommen hast, fragt der Editor vorher nach.

## Tastenkürzel

Unter macOS steht `Cmd` anstelle von `Ctrl`.

| Tastenkürzel | Funktion |
|---|---|
| `A` | Öffnet die Aktionsauswahl. |
| `Enter` | Bearbeitet den ausgewählten Eintrag. |
| `Delete` | Löscht den ausgewählten Eintrag. |
| `Up` / `Down` | Wählt den Eintrag darüber oder darunter aus. |
| `Shift + Up` / `Shift + Down` | Verschiebt den ausgewählten Eintrag nach oben oder unten. |
| `Ctrl + C` / `Ctrl + V` | Kopiert eine Aktion und fügt sie ein. Anweisungen und Blöcke lassen sich nicht kopieren. |
| `Ctrl + Z` | Macht den letzten Schritt rückgängig. |
| `Ctrl + Y` oder `Ctrl + Shift + Z` | Stellt den letzten Schritt wieder her. |
| `Ctrl + S` | Speichert das Skript und schließt den Editor, wie **Fertig**. |

# Anweisungen

Anweisungen legen fest, welche Aktionen ausgeführt werden und wie oft. Füge sie mit einem Rechtsklick auf den Skriptbereich hinzu.

## If, Else-If und Else

Bei **IF-Anweisung hinzufügen** wirst du nach [Bedingungen](/conditions) gefragt. Die Aktionen innerhalb von IF werden nur ausgeführt, wenn die Bedingungen erfüllt sind.

Klicke mit der rechten Maustaste auf eine IF-Anweisung, um die Kette zu erweitern:

- **ELSE-IF-Anweisung anhängen**: Prüft die eigenen Bedingungen, wenn die IF-Anweisung darüber nicht ausgeführt wurde.
- **ELSE-Anweisung anhängen**: Wird ausgeführt, wenn keine vorherige Anweisung in der Kette ausgeführt wurde.

Mit einer IF-Anweisung, die **Layout ist aktiviert** prüft, kannst du beispielsweise einen Toast nur anzeigen, solange das Winter-Layout aktiv ist, und andernfalls einen Ton abspielen lassen.

## While-Schleife

**WHILE-Schleife hinzufügen** wiederholt ihre Aktionen, solange die [Bedingungen](/conditions) erfüllt sind.

Jeder Durchlauf wird nach 3 Sekunden beendet, damit eine Endlosschleife das Spiel nicht einfrieren kann. Das ist kein Timer: Wenn etwas später oder immer wieder passieren soll, verwende [Später ausführen](#später-ausführen), einen [Ticker](/elements#ticker) oder einen [Scheduler](/schedulers).

## For-Each-Schleife

**FOR-EACH-Schleife hinzufügen** führt ihre Aktionen für jeden Eintrag einer [Listenvariable](/variables#text-and-list-variables) einmal aus, vom ersten bis zum letzten Eintrag.

- `$$list_entry` ist der aktuelle Eintrag und `$$list_index` sein Index. Der erste Eintrag hat den Index 0.
- Beide Variablen können in Aktionswerten und Bedingungen innerhalb der Schleife verwendet werden.
- Gib den Namen der Liste ohne `$$` ein, zum Beispiel `quest_log`. Platzhalter im Namen funktionieren ebenfalls.
- Die Schleife liest die Liste einmal beim Start ein. Aktionen innerhalb der Schleife können die Liste daher gefahrlos ändern.
- Wie bei WHILE-Schleifen wird jeder Durchlauf nach 3 Sekunden beendet.

Beispiele findest du unter [Eine Liste durchgehen](/variables#going-through-a-list).

# Blöcke

Blöcke ändern, wann Aktionen ausgeführt werden, oder helfen dabei, das Skript übersichtlich zu halten. Füge sie mit einem Rechtsklick auf den Skriptbereich hinzu.

## Verzögerungsblock

**VERZÖGERUNGSBLOCK hinzufügen** hält seine Aktionen für eine bestimmte Zeit in Millisekunden zurück (`1000` entspricht einer Sekunde).

- Wenn das Skript den Block zum ersten Mal erreicht, startet der Timer und die Aktionen werden übersprungen. Der Rest des Skripts wird sofort ausgeführt.
- Erreicht das Skript den Block erneut, bevor die Zeit abgelaufen ist, werden die Aktionen wieder übersprungen.
- Danach werden die Aktionen jedes Mal ausgeführt, wenn das Skript den Block erreicht.
- Bei Skripten von Elementen wird der Timer zurückgesetzt, wenn das Menü erneut geöffnet oder in der Größe verändert wird.

Das eignet sich gut für [Ticker](/elements#ticker), etwa um etwas erst anzuzeigen, wenn ein Menü bereits einige Sekunden geöffnet ist. Der Block führt selbst nichts aus: Verwende dafür „Später ausführen“.

## Später ausführen

Der Block **SPÄTER AUSFÜHREN hinzufügen** führt seine Aktionen nach einer bestimmten Zeit in Millisekunden einmal aus. Der Rest des Skripts wird sofort ausgeführt.

Jedes Mal, wenn das Skript den Block erreicht, startet ein neuer Countdown. Das eignet sich für Skripte, die nur einmal ausgeführt werden, zum Beispiel beim Anklicken einer Schaltfläche oder beim Öffnen eines Menüs.

## Ordner

**Ordner hinzufügen** gruppiert Aktionen unter einem Namen. Der Ordner führt alle darin enthaltenen Aktionen aus und dient nur dazu, lange Skripte übersichtlich zu halten. Doppelklicke auf den Namen, um ihn zu ändern.

## Kommentar

**Kommentar hinzufügen** fügt eine Notiz für dich selbst hinzu. Sie bewirkt nichts. Doppelklicke darauf, um sie zu bearbeiten.

# So werden Skripte ausgeführt

- Aktionen werden von oben nach unten ausgeführt. Wenn eine Aktion fehlschlägt, wird ein Fehler ins Spiellog geschrieben, aber der Rest des Skripts wird weiterhin ausgeführt.
- Platzhalter in Werten werden erst ausgewertet, wenn die Aktion ausgeführt wird. Daher sieht eine Aktion auch, was vorherige Aktionen geändert haben.
- Downloads, das Entpacken von ZIP-Dateien und Webanfragen werden im Hintergrund abgeschlossen. Die nächste Aktion wartet nicht darauf. Um Aktionen nach deren Abschluss auszuführen, verwende die Listener [**Bei Dateidownload über Aktion**](/listeners#on-file-downloaded-via-action) und [**Bei ZIP-Entpacken über Aktion**](/listeners#on-zip-extracted-via-action) oder eine Antwortvariable von [**HTTP-Anfrage senden**](#http-anfrage-senden).

# Werte von Aktionen

Die meisten Aktionen benötigen einen Wert, zum Beispiel die Adresse eines Servers. Einfache Werte sind Text, den du eingibst. Aktionen mit mehr Einstellungen haben ein eigenes Fenster.

## Platzhalter

Werte können [Platzhalter](/placeholders) enthalten, zum Beispiel den Namen des Spielers. Sie werden beim Ausführen der Aktion ersetzt:

```
/say Willkommen zurück, {"placeholder":"playername"}!
```

## $$-Variablen

Gib `$$` gefolgt vom Namen einer Variable ein, um ihren Wert in einer Aktion oder Bedingung zu verwenden. Bei Variablennamen wird zwischen Groß- und Kleinschreibung unterschieden. Das funktioniert mit zwei Arten von Variablen:

### Eigene Variablen

Jede Variable, die du unter **Menüleiste -> Anpassung -> Variablen verwalten** erstellst, kann mit `$$` und ihrem Namen verwendet werden. Eine Variable namens `coins` wird in jedem Skript zu `$$coins`. Mit dem Wert unten zeigt **Im Chat anzeigen [Clientseitig]** dem Spieler beispielsweise an, wie viele Münzen er hat:

```
&6Du hast $$coins Münzen!
```

Unter [Variablen](/variables) erfährst du, wie du sie erstellst und änderst.

### Skriptvariablen

Einige Funktionen stellen ihrem Skript eigene Variablen zur Verfügung:

- Ein [Schieberegler](/elements#slider) stellt `$$value` bereit: seinen neuen Wert.
- Ein [Kontrollkästchen](/elements#checkbox) stellt `$$value` bereit: seinen neuen Zustand, `true` oder `false`.
- Eine [For-Each-Schleife](#for-each-schleife) stellt `$$list_entry` und `$$list_index` bereit.
- Jeder [Listener](/listeners#listener-variables) führt die Variablen auf, die er bereitstellt, zum Beispiel die gedrückte Taste.

Diese Variablen sind nur verfügbar, während das Skript ausgeführt wird. Wenn eine davon denselben Namen wie eine deiner Variablen hat, steht `$$name` für die Skriptvariable.

# Alle Aktionen

Hier findest du alle Aktionen von FancyMenu, sortiert nach ihrer Funktion.

## Bildschirme und Menüs

### Bildschirm oder benutzerdefinierte GUI öffnen

**Kennung:** `opengui`

Öffnet ein Menü des Spiels, einer Mod oder eine [benutzerdefinierte GUI](/custom-guis).

**Wert:** die [Bildschirmkennung](/screen-identifiers), zum Beispiel `options_screen`

Bei Kennungen wird zwischen Groß- und Kleinschreibung unterschieden. Manche Mod-Menüs können auf diese Weise nicht geöffnet werden. Verwende in diesem Fall [**Schaltfläche von Vanilla/Mod nachahmen**](#vanilla--mod-schaltfläche-nachahmen) für eine Schaltfläche, die das Menü öffnet.

### Bildschirm schließen

**Kennung:** `closegui`

Schließt das geöffnete Menü. Wenn du dich nicht in einer Welt befindest, wird der Titelbildschirm geöffnet.

**Wert:** keiner

### Bildschirm aktualisieren

**Kennung:** `update_screen`

Baut das geöffnete Menü neu auf, so als würdest du die Fenstergröße ändern. Nützlich, nachdem du die GUI-Skalierung oder andere Optionen geändert hast.

**Wert:** keiner

### Zum vorherigen Bildschirm zurückkehren

**Kennung:** `back_to_last_screen`

Kehrt zum Menü zurück, das zuvor geöffnet war. Bei einer [benutzerdefinierten GUI](/custom-guis) ist das das Menü, von dem aus sie geöffnet wurde.

**Wert:** keiner

### Toast anzeigen

**Kennung:** `show_toast`

Zeigt eine Toast-Benachrichtigung oben rechts an. Die Einstellungen nimmst du im zugehörigen Fenster vor:

- **Toast-Breite**: 120 bis 320 Pixel.
- **Dauer (ms)**: Wie lange der Toast angezeigt wird, von 1 Sekunde (`1000`) bis 10 Minuten.
- **Titel** und **Nachricht**: Text mit [Formatierungscodes](/text-formatting#minecraft-text-formatting) oder Minecraft-Textkomponenten im JSON-Format.
- **Quelle der Symboltextur** und **Quelle der Hintergrundtextur**: Optionale [Bilder](/resources). Symbole sehen bei 20 × 20 Pixeln am besten aus. Hintergründe sollten 32 Pixel hoch und so breit wie der Toast sein.

### Vanilla-/Mod-Schaltfläche nachahmen

**Kennung:** `mimicbutton`

Klickt eine Schaltfläche des Spiels oder einer Mod an, als hätte der Spieler daraufgeklickt.

**Wert:** der [Widget-Locator](/widget-locators) der Schaltfläche, zum Beispiel `title_screen:mc_titlescreen_options_button`

Um ihn abzurufen, klicke im Editor mit der rechten Maustaste auf die Schaltfläche und wähle **Widget-Locator kopieren**.

## Layouts und Elemente

### Layout umschalten

**Kennung:** `toggle_layout`

Deaktiviert ein Layout, wenn es aktiviert ist, und aktiviert es, wenn es deaktiviert ist.

**Wert:** der Name des Layouts ohne `.txt`, zum Beispiel `winter_title_screen`

### Layout aktivieren

**Kennung:** `enable_layout`

Aktiviert ein Layout.

**Wert:** der Name des Layouts ohne `.txt`

### Layout deaktivieren

**Kennung:** `disable_layout`

Deaktiviert ein Layout.

**Wert:** der Name des Layouts ohne `.txt`

Alle drei Layout-Aktionen speichern die Änderung und aktualisieren das geöffnete Menü sofort. Beim Namen wird zwischen Groß- und Kleinschreibung unterschieden.

### Element-Animator umschalten

**Kennung:** `toggle_element_animator`

Aktiviert einen [Element-Animator](/element-animator), wenn er deaktiviert ist, und deaktiviert ihn, wenn er aktiviert ist. Die Animation beginnt von vorn. Der Zustand bleibt gespeichert.

**Wert:** die Kennung des Element-Animators

### Element-Animator aktivieren

**Kennung:** `enable_element_animator`

Aktiviert einen [Element-Animator](/element-animator). War er zuvor deaktiviert, beginnt seine Animation von vorn.

**Wert:** die Kennung des Element-Animators

### Element-Animator deaktivieren

**Kennung:** `disable_element_animator`

Deaktiviert einen [Element-Animator](/element-animator) und setzt seine Animation zurück.

**Wert:** die Kennung des Element-Animators

### Element-Animator zurücksetzen

**Kennung:** `reset_element_animator`

Startet die Animation eines [Element-Animators](/element-animator) von vorn, ohne ihn zu aktivieren oder zu deaktivieren.

**Wert:** die Kennung des Element-Animators

### Wert eines Texteingabefelds festlegen

**Kennung:** `set_text_input_field_value`

Legt den Text eines [Texteingabefelds](/elements#text-input-field) von FancyMenu oder dem Spiel fest.

**Wert:** `element_identifier|||text|||force`

Wenn `force` auf `true` gesetzt ist, wird der Text auch geändert, wenn das Feld deaktiviert (inaktiv) ist.

### Element scrollen

**Kennung:** `scroll_scroll_area`

Scrollt einen [scrollbaren Bereich](/scrollable-areas) oder ein [Textelement](/elements#text). Die Einstellungen nimmst du im zugehörigen Fenster vor:

- **Kennung des zu scrollenden Elements**: Der Bereich oder Text, durch den gescrollt werden soll.
- **Scrollen zu**:
  - **Anfang** oder **Ende**.
  - **Position**: Die **horizontale Position** und **vertikale Position** in Pixeln. Lass eines davon leer, um es unverändert zu lassen.
  - **Element** (nur Bereiche): Scrollt, bis sich das Element mit der **Kennung des Ziel-Elements** am Anfang befindet.
  - **Zeilennummer** (nur Texte): Die erste Zeile hat die Nummer `1`.
  - **Zeile mit Text** (nur Texte): Die erste Zeile, die den **Text in der Zeile** enthält. Die Groß- und Kleinschreibung spielt keine Rolle.
- **Sanft scrollen**: Gleitet zur Position, statt dorthin zu springen. Für das Element muss sanftes Scrollen aktiviert sein.

Funktioniert nur, wenn ein solches Element vorhanden ist.

## Audio und Video

### Nächsten Titel abspielen

**Kennung:** `audio_next_track`

Springt zum nächsten Titel eines [Audioelements](/elements#audio).

**Wert:** die Kennung des Audioelements, zum Beispiel `menu_music`

### Vorherigen Titel abspielen

**Kennung:** `audio_previous_track`

Springt zum vorherigen Titel eines [Audioelements](/elements#audio).

**Wert:** die Kennung des Audioelements

### Lautstärke des Titels festlegen

**Kennung:** `set_audio_element_volume`

Legt die Lautstärke eines [Audioelements](/elements#audio) fest: von `0.0` (0 %) bis `1.0` (100 %).

**Wert:** `element_identifier:volume`, zum Beispiel `menu_music:0.5`

### Titel wiedergeben/anhalten

**Kennung:** `audio_toggle_play`

Hält ein laufendes [Audioelement](/elements#audio) an oder gibt ein angehaltenes wieder.

**Wert:** die Kennung des Audioelements

### Audio abspielen

**Kennung:** `play_audio`

Spielt eine Audiodatei einmal ab. Die Einstellungen nimmst du im zugehörigen Fenster vor: **Audioquelle**, **Soundkanal** und **Basislautstärke** (bis zu 100 %).

- FancyMenu wartet bis zu zehn Sekunden, bis die Audiodatei geladen ist.
- Funktioniert nicht in einem [Ticker](/elements#ticker), der im Hintergrund (asynchron) ausgeführt wird. Stattdessen zeigt FancyMenu einen Fehler an.

[**Alle Aktions-Audios stoppen**](#alle-aktions-audios-stoppen) stoppt Audios, die mit dieser Aktion gestartet wurden.

### Alle Aktions-Audios stoppen

**Kennung:** `stop_all_action_audios`

Stoppt alle Audios, die mit [**Audio abspielen**](#audio-abspielen) gestartet wurden. Audioelemente, Menü-Sounds und Schaltflächen-Sounds werden weiter abgespielt.

**Wert:** keiner

### Lautstärke des Videoelements festlegen

**Kennung:** `set_video_element_volume`

Legt die Lautstärke eines [Videoelements](/video) fest: von `0.0` (0 %) bis `1.0` (100 %).

**Wert:** `video_element_identifier:volume`

### Wiedergabezeit des Videoelements festlegen

**Kennung:** `set_video_element_play_time`

Springt zu einer Position in einem [Videoelement](/video), angegeben in Millisekunden.

**Wert:** `video_element_identifier:time_in_ms`, zum Beispiel `intro_video:30000`

### Wiedergabestatus des Videoelements umschalten

**Kennung:** `toggle_video_element_pause_state`

Hält ein laufendes [Videoelement](/video) an oder setzt ein angehaltenes fort.

**Wert:** die Kennung des Videoelements

### Lautstärke des Videohintergrunds festlegen

**Kennung:** `set_video_menu_background_volume`

Legt die Lautstärke eines [Videomenü-Hintergrunds](/video) fest: von `0.0` (0 %) bis `1.0` (100 %).

**Wert:** `background_identifier:volume`

> [!NOTE]
> Um die Kennung eines Menühintergrunds abzurufen, klicke mit der rechten Maustaste auf den Editor-Hintergrund und wähle **Hintergrundkennung kopieren**.

### Wiedergabezeit des Videohintergrunds festlegen

**Kennung:** `set_video_menu_background_play_time`

Springt zu einer Position in einem [Videomenü-Hintergrund](/video), angegeben in Millisekunden.

**Wert:** `background_identifier:time_in_ms`

### Wiedergabestatus des Videohintergrunds umschalten

**Kennung:** `toggle_video_menu_background_pause_state`

Hält einen laufenden [Videomenü-Hintergrund](/video) an oder setzt einen angehaltenen fort.

**Wert:** die Kennung des Menühintergrunds

## Welten und Server

### Server beitreten

**Kennung:** `joinserver`

Verbindet sich mit einem Minecraft-Server.

**Wert:** `address` oder `address:port`, zum Beispiel `play.example.net`

Ohne Port wird `25565` verwendet. Wenn gerade eine Welt oder ein Server geladen ist, wird stattdessen ein Fehler angezeigt. Server, die noch nicht in der Serverliste stehen, werden hinzugefügt.

### Welt betreten

**Kennung:** `loadworld`

Lädt eine Einzelspielerwelt.

**Wert:** der Ordnername der Welt in `saves`, zum Beispiel `Survival Island`

Funktioniert nur, wenn die Welt vorhanden ist. Wenn gerade eine Welt oder ein Server geladen ist, wird stattdessen ein Fehler angezeigt.

### Letzte Welt / letzten Server betreten

**Kennung:** `join_last_world`

Lädt die Welt oder verbindet sich mit dem Server, auf dem der Spieler zuletzt gespielt hat.

**Wert:** keiner

Wenn gerade eine Welt oder ein Server geladen ist, wird stattdessen ein Fehler angezeigt. Server, die noch nicht in der Serverliste stehen, werden hinzugefügt.

### Welt oder Server verlassen

**Kennung:** `disconnect_server_or_world`

Verlässt die Welt oder den Server und öffnet ein Menü.

**Wert:** die [Bildschirmkennung](/screen-identifiers) des zu öffnenden Menüs, zum Beispiel `title_screen`

Funktioniert nur, wenn eine Welt geladen ist. Auch [benutzerdefinierte GUIs](/custom-guis) funktionieren. Kann das Menü nicht geöffnet werden, wird der Titelbildschirm geöffnet.

## Chat und Befehle

### Chatnachricht senden / Befehl ausführen

**Kennung:** `sendmessage`

Sendet eine Chatnachricht oder führt einen Befehl aus, als hätte der Spieler ihn eingegeben.

**Wert:** die Nachricht oder ein Befehl mit `/`, zum Beispiel `/spawn`

### Befehl als integrierten Server ausführen

**Kennung:** `execute_command_as_integrated_server`

Führt im Einzelspielermodus einen Befehl als Server aus, unabhängig von den Berechtigungen des Spielers oder der Cheat-Einstellung.

**Wert:** der Befehl, zum Beispiel `/give @p minecraft:diamond 1`

> [!WARNING]
> Funktioniert nur im Einzelspielermodus, wenn die Welt nicht für LAN geöffnet ist. In allen anderen Fällen passiert nichts.

### In den Chat einfügen

**Kennung:** `paste_to_chat`

Fügt Text in das Chat-Eingabefeld ein, während eine Welt geladen ist. Ist der Chat nicht geöffnet, wird er mit dem Text geöffnet.

**Wert:** `true:text` fügt den Text zum bereits eingegebenen hinzu; `false:text` ersetzt ihn

### Im Chat anzeigen [clientseitig]

**Kennung:** `display_in_chat_client_side`

Zeigt eine Chatnachricht an, die nur dieser Spieler sieht. Es wird nichts an den Server gesendet.

**Wert:** der Text mit [Formatierungscodes](/text-formatting#minecraft-text-formatting) oder als Minecraft-Textkomponenten im JSON-Format, zum Beispiel `&aWillkommen zurück!`

Funktioniert nur, wenn eine Welt geladen ist.

## Variablen und Listen

### Variablenwert festlegen (FM-Variable)

**Kennung:** `set_variable`

Legt eine [Variable](/variables) fest.

**Wert:** `variable_name:value`, zum Beispiel `coins:100`

- Nur das erste `:` trennt den Namen vom Wert.
- [Listenvariablen](/variables#text-and-list-variables) bleiben Listen: Ein JSON-Array wie `["a","b"]` wird zu ihren Einträgen, anderer Text wird zu ihrem einzigen Eintrag und leerer Text leert sie.

### Variable löschen (FM-Variable)

**Kennung:** `delete_variable`

Löscht eine [Variable](/variables) vollständig. Alle anderen Variablen bleiben erhalten. Um die Variable nur zu leeren, verwende [**Variablenwert festlegen (FM-Variable)**](#variablenwert-festlegen-fm-variable).

**Wert:** der Name der Variable

### Alle Variablen löschen (FM-Variable)

**Kennung:** `clear_variables`

Löscht alle [Variablen](/variables), sowohl Text- als auch Listenvariablen.

**Wert:** keiner

### Eintrag zur Liste hinzufügen (FM-Variable)

**Kennung:** `add_to_list`

Fügt einer [Listenvariable](/variables#list-actions) einen Eintrag hinzu.

- **Listenvariable**: der Name der Liste. Gibt es noch keine Variable mit diesem Namen, erstellt die Aktion die Liste.
- **Neuer Eintrag**: der Text des Eintrags.
- **Index (optional)**: die Position des Eintrags. Ist das Feld leer, wird er am Ende hinzugefügt. Die folgenden Einträge rücken um eine Stelle nach hinten.
- **Überspringen, wenn bereits in der Liste**: Fügt nichts hinzu, wenn die Liste bereits einen Eintrag mit demselben Text enthält. Mit **Groß-/Kleinschreibung ignorieren** wird `Apple` als Übereinstimmung mit `apple` erkannt.

### Listeneintrag festlegen (FM-Variable)

**Kennung:** `set_list_entry`

Ersetzt den Eintrag am angegebenen **Index** einer [Listenvariable](/variables#list-actions) durch einen **Neuen Wert**. Funktioniert nicht, wenn die Liste an dieser Stelle keinen Eintrag hat.

### Aus Liste entfernen (FM-Variable)

**Kennung:** `remove_from_list`

Entfernt Einträge aus einer [Listenvariable](/variables#list-actions). Mit **Entfernen** legst du fest, welche Einträge entfernt werden:

- **Eintrag am Index**: der Eintrag an einem bestimmten Index.
- **Erste Übereinstimmung**: der erste Eintrag, der genau dem **Zu entfernenden Wert** entspricht.
- **Alle Übereinstimmungen**: alle Einträge, die diesem Wert entsprechen.

Mit **Groß-/Kleinschreibung ignorieren** wird `Apple` als Übereinstimmung mit `apple` erkannt.

### Liste leeren (FM-Variable)

**Kennung:** `clear_list`

Entfernt alle Einträge einer [Listenvariable](/variables#list-actions). Die leere Liste bleibt erhalten.

### Liste festlegen (FM-Variable)

**Kennung:** `set_list`

Ersetzt alle Einträge einer [Listenvariable](/variables#list-actions). Unter **Einträge aus** legst du fest, woher sie stammen:

- **Text aufteilen**: Teilt den **Aufzuteilenden Text** am **Trennzeichen**, zum Beispiel `,`. Ein leeres Trennzeichen teilt den Text an Zeilenumbrüchen. **Einträge kürzen** entfernt Leerzeichen am Anfang und Ende, **Leere Einträge überspringen** lässt leere Einträge aus.
- **JSON-Array**: Verwendet die Einträge eines Arrays wie `["Diamonds","Emeralds"]` oder `$$other_list`, um eine andere Liste zu kopieren. Anderer Text wird zum einzigen Eintrag, leerer Text leert die Liste.

Das Fenster zeigt eine Vorschau der Einträge.

### Liste sortieren (FM-Variable)

**Kennung:** `arrange_list`

Ändert die Reihenfolge einer [Listenvariable](/variables#list-actions). Unter **Sortierung** findest du folgende Optionen:

- **A–Z sortieren** und **Z–A sortieren**: Sortiert alphabetisch.
- **Zahlen, kleinste zuerst** und **Zahlen, größte zuerst**: Sortiert nach Zahlen. Einträge, die keine Zahlen sind, kommen ans Ende.
- **Reihenfolge umkehren**: Der letzte Eintrag wird zum ersten.
- **Mischen**: Eine zufällige Reihenfolge.
- **Duplikate entfernen**: Behält von jedem Wert nur den ersten Eintrag.

Bei allen Listenaktionen hat der erste Eintrag den Index `0`, und `-1` steht für den letzten. Der Listenname kann Platzhalter enthalten. Steht `$$` davor, verwendet die Aktion den Wert dieser Variable als Listennamen. Textvariablen, die einen Wert enthalten, bleiben unverändert; die Aktion schreibt eine Warnung ins Spiellog.

## Web und Netzwerk

### URL im Browser öffnen

**Kennung:** `openlink`

Öffnet einen Link ohne Rückfrage im Standardbrowser.

**Wert:** der Link, zum Beispiel `https://discord.gg/example`

Verwende nur Links, denen du vertraust.

### HTTP-Anfrage senden

**Kennung:** `send_http_request`

Sendet eine Webanfrage im Hintergrund. Die Antwort kann ins Spiellog geschrieben oder in einer Variable gespeichert werden.

| Einstellung | Funktion |
|---|---|
| URL | Die HTTP- oder HTTPS-Adresse. |
| Methode | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` oder `OPTIONS`. |
| Inhalt | Die zu sendenden Daten. Wird bei `GET` und `HEAD` nicht gesendet. |
| Inhaltstyp | Der `Content-Type` des Inhalts, zum Beispiel `application/json`. |
| Zeitlimit | Die Zeit in Sekunden, die auf die Verbindung und die Antwort gewartet wird. |
| Antwort protokollieren | Schreibt die Antwort ins Spiellog. |
| Antwortvariable | Speichert die Antwort nach ihrem Eintreffen in dieser Variable. |
| Einzeilige Antwort | Entfernt Zeilenumbrüche aus der Antwort, bevor sie gespeichert wird. |
| Authentifizierung | Keine, Basic, Bearer oder API-Schlüssel. |
| Header | Zusätzliche Anfrage-Header. |

Die nächste Aktion wartet nicht auf die Antwort. Auch Fehlerantworten werden protokolliert und gespeichert. Gib keine Passwörter oder Zugriffstoken in der Aktion an: Jeder, der Zugriff auf das Layout hat, kann sie lesen.

### FM-Daten an Server senden

**Kennung:** `send_fm_data_to_server`

Sendet [FM-Daten](/fm-data) an den Server, auf dem ebenfalls FancyMenu installiert sein muss.

**Wert:** `data_identifier||data`

### Verbindung zu Remoteserver herstellen

**Kennung:** `connect_to_remote_server`

Verbindet sich mit einem Remoteserver oder verwendet die bereits bestehende Verbindung.

**Wert:** die Adresse des Servers, zum Beispiel `wss://example.com/ws`

Unter [Kommunikation mit Remoteservern](/remote-server-communication#url-modes) findest du gültige Adressen.

### Daten an Remoteserver senden

**Kennung:** `send_data_to_remote_server`

Sendet Text an einen Remoteserver und stellt bei Bedarf zuerst eine Verbindung her.

**Wert:** `server_address||data`

### Verbindung zu Remoteserver schließen

**Kennung:** `close_remote_server_connection`

Schließt eine Verbindung zu einem Remoteserver.

**Wert:** die Anforderungs-ID, normalerweise `$$request_id` aus [**Bei Verbindung mit Remoteserver**](/listeners#on-remote-server-connected)

### Alle Verbindungen zu Remoteservern schließen

**Kennung:** `close_all_remote_server_connections`

Schließt alle Verbindungen zu Remoteservern, die FancyMenu geöffnet hat.

**Wert:** keiner

## Dateien

### Datei im Spielverzeichnis erstellen

**Kennung:** `create_file_in_game_dir`

Erstellt eine leere Datei. Fehlende Ordner werden ebenfalls erstellt. Eine bereits vorhandene Datei bleibt unverändert.

**Wert:** der Dateipfad, zum Beispiel `config/mymodpack/first_start.txt`

Alle Dateiaktionen funktionieren nur innerhalb des Spielordners (Instanzordners). Pfade, die mit `.minecraft/` beginnen, verwenden stattdessen den Standardordner `.minecraft`, der sich an einem anderen Ort befinden kann.

### Datei/Ordner im Spielverzeichnis löschen

**Kennung:** `delete_file_in_game_dir`

Löscht eine Datei oder einen Ordner mitsamt seinem gesamten Inhalt.

**Wert:** der Pfad, zum Beispiel `config/mymodpack/cache.txt`

Mit einem `*` am Ende, zum Beispiel `config/downloads/*`, werden alle Dateien gelöscht, die direkt in diesem Ordner liegen. Der Ordner selbst und die darin enthaltenen Ordner bleiben erhalten.

### Datei/Ordner im Spielverzeichnis kopieren

**Kennung:** `copy_file_in_game_dir`

Kopiert eine Datei oder einen Ordner mitsamt seinem gesamten Inhalt.

**Wert:** `source||destination`, zum Beispiel `config/presets/default.json||config/mymod/settings.json`

- Endet die Quelle mit `*`, zum Beispiel `config/presets/*||config/mymod/`, werden alle Dateien kopiert, die direkt in diesem Ordner liegen, aber keine Ordner. Das Ziel ist dann ein Ordner und wird bei Bedarf erstellt.
- Vorhandene Dateien werden nicht überschrieben: Wenn das Ziel bereits existiert, schlägt die Aktion fehl.

### Datei/Ordner im Spielverzeichnis verschieben

**Kennung:** `move_file_in_game_dir`

Verschiebt eine Datei oder einen Ordner mitsamt seinem gesamten Inhalt.

**Wert:** `source||destination`

Ein `*` am Ende der Quelle funktioniert wie bei [**Datei/Ordner im Spielverzeichnis kopieren**](#dateiordner-im-spielverzeichnis-kopieren). Vorhandene Dateien werden nicht überschrieben.

### Datei/Ordner im Spielverzeichnis umbenennen

**Kennung:** `rename_file_in_game_dir`

Benennt eine Datei oder einen Ordner um. Die Aktion schlägt fehl, wenn bereits etwas mit dem neuen Namen existiert.

**Wert:** `path||new_name`, zum Beispiel `config/mymod/old_name.txt||new_name.txt`

### Datei ins Spielverzeichnis herunterladen

**Kennung:** `download_file_to_game_dir`

Lädt eine Datei im Hintergrund in einen Ordner herunter.

**Wert:** `url||target_folder`, zum Beispiel `https://example.com/pack.zip||downloads`

- Der zweite Teil ist ein Ordner, kein Dateiname. FancyMenu übernimmt den Namen aus dem Download oder dem Link.
- Eine Datei mit demselben Namen wird überschrieben.
- [**Bei Dateidownload über Aktion**](/listeners#on-file-downloaded-via-action) wird ausgeführt, wenn der Download abgeschlossen ist oder fehlschlägt. Bei Erfolg enthält `$$target_file_path` den Pfad der gespeicherten Datei.

### ZIP-Datei im Spielverzeichnis entpacken

**Kennung:** `extract_zip_file_in_game_dir`

Entpackt eine ZIP-Datei im Hintergrund in einen Ordner.

**Wert:** `zip_path||target_folder`, zum Beispiel `downloads/pack.zip||resourcepacks/MyPack`

Dateien mit denselben Namen werden ersetzt. Es wird kein zusätzlicher Ordner mit dem Namen der ZIP-Datei erstellt. [**Bei ZIP-Entpacken über Aktion**](/listeners#on-zip-extracted-via-action) wird ausgeführt, wenn der Vorgang abgeschlossen ist. Entpacke nur ZIP-Dateien, denen du vertraust.

### Datei/Ordner im Spielverzeichnis öffnen

**Kennung:** `open_file_folder_in_game_dir`

Öffnet eine Datei oder einen Ordner mit dem dafür vorgesehenen Programm des Systems.

**Wert:** der Pfad, zum Beispiel `screenshots`

### Datei im Spielverzeichnis beschreiben

**Kennung:** `write_file_in_game_dir`

Schreibt Text in eine Datei. Die Datei und ihre Ordner werden bei Bedarf erstellt.

**Wert:** `path|||text|||append`, zum Beispiel `config/mymodpack/log.txt|||Server beigetreten\n|||true`

Mit `\n` beginnst du eine neue Zeile. Wenn `append` auf `true` gesetzt ist, wird der Text an das Ende der Datei angehängt. Bei `false` wird der vorhandene Inhalt ersetzt.

### Datei auf dem System auswählen

**Kennung:** `select_file_to_game_dir`

Öffnet die Dateiauswahl des Systems und kopiert die ausgewählte Datei in den Spielordner.

**Wert:** `target_path|||filter_name|||extensions|||overwrite`, zum Beispiel `config/fancymenu/assets/background.png|||Bilder|||png;jpg|||true`

- `target_path` ist der vollständige Pfad der Kopie, einschließlich Dateiname.
- Trenne Dateiendungen mit `;` oder `,`. Ohne Dateiendungen können alle Dateien ausgewählt werden.
- Wenn `overwrite` auf `false` gesetzt ist, schlägt die Aktion fehl, falls die Datei bereits existiert.

[**Bei Dateiauswahl**](/listeners#on-file-selected) wird ausgeführt, wenn die Datei kopiert wurde, die Dateiauswahl abgebrochen wurde oder ein Fehler aufgetreten ist.

## Spiel und FancyMenu

### Minecraft beenden

**Kennung:** `quitgame`

Schließt das Spiel.

**Wert:** keiner

### Minecraft-Option festlegen

**Kennung:** `edit_minecraft_option`

Ändert eine Minecraft-Option, zum Beispiel die Sichtweite oder die GUI-Skalierung.

**Wert:** `option_name:value`, zum Beispiel `renderDistance:12`

Die verfügbaren Optionsnamen findest du unter [Minecraft-Optionen](/minecraft-options).

### Tastenbelegung nachahmen

**Kennung:** `mimic_keybind`

Drückt eine Minecraft-Tastenbelegung, zum Beispiel für Springen oder Schleichen, und kann sie gedrückt halten.

**Wert:** `keybind|||hold|||duration_ms`, zum Beispiel `key.jump|||false|||1000`

| Teil | Bedeutung |
|---|---|
| `keybind` | Die ID der Tastenbelegung, zum Beispiel `key.jump` oder `key.sneak`. |
| `hold` | `true` hält die Taste gedrückt, `false` drückt sie einmal. |
| `duration_ms` | Wie lange die Taste gedrückt gehalten wird, in Millisekunden. Standardmäßig `1000`. |

### Ressourcenpaket verwalten

**Kennung:** `manage_resource_pack`

Aktiviert oder deaktiviert ein Ressourcenpaket. Die Einstellungen nimmst du im zugehörigen Fenster vor:

- **Ziel-Ressourcenpaket**: Der Name des Pakets, wie er auf dem Bildschirm „Ressourcenpakete“ angezeigt wird. Die Groß- und Kleinschreibung spielt keine Rolle.
- **Aktionsmodus**: **Aktivieren**, **Deaktivieren** oder **Umschalten**.
- **Ressourcen neu laden**: Lädt die Ressourcenpakete direkt nach der Änderung neu. Deaktiviere diese Option, um sie später neu zu laden, zum Beispiel mit [**Ressourcenpakete neu laden**](#ressourcenpakete-neu-laden).

Ressourcenpakete, die das Spiel benötigt, können nicht deaktiviert werden.

### Ressourcenpakete neu laden

**Kennung:** `reload_resource_packs`

Lädt die Ressourcenpakete neu, wie bei `F3 + T`. Fünf Sekunden lang nach einem Neuladen hat die Aktion keine Wirkung, damit die Ressourcen nicht immer wieder neu geladen werden.

**Wert:** keiner

### FancyMenu neu laden

**Kennung:** `reloadmenu`

Lädt Layouts, [benutzerdefinierte GUIs](/custom-guis), [Panoramen](/panoramas), [Diashows](/slideshows), Einstellungen und Dateien von FancyMenu neu. Ressourcenpakete werden nicht neu geladen.

**Wert:** keiner

> [!WARNING]
> Das Neuladen dauert einen Moment. Verwende diese Aktion auf einer Schaltfläche, niemals in einem [Ticker](/elements#ticker) oder einem [Listener](/listeners), der häufig ausgeführt wird.

### Scheduler starten

**Kennung:** `start_scheduler`

Startet einen [Scheduler](/schedulers).

**Wert:** die Kennung des Schedulers

### Scheduler stoppen

**Kennung:** `stop_scheduler`

Stoppt einen [Scheduler](/schedulers).

**Wert:** die Kennung des Schedulers

### Text in die Zwischenablage kopieren

**Kennung:** `copytoclipboard`

Kopiert Text in die Zwischenablage.

**Wert:** der Text, zum Beispiel `play.example.net`

### Ins Spiellog schreiben

**Kennung:** `print_to_log`

Schreibt eine Zeile ins Spiellog. Nützlich, um herauszufinden, was ein Skript macht.

**Wert:** der Text
