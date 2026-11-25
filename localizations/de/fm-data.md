---
title: Datenaustausch zwischen Client und Server
description: >-
  Sende und empfange mit FancyMenu benutzerdefinierte Daten zwischen Server und
  Client.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM Data

Mit dem System „FM Data“ kannst du benutzerdefinierte Textdaten zwischen Server und Client senden.

Für jeden `/fmdata`-Unterbefehl ist **Berechtigungsstufe 2** erforderlich (Game Master / OP-Stufe 2).

Jede FM-Data-Nachricht enthält:

1. Einen **Datenbezeichner** (gibt an, um welche Art von Nachricht es sich handelt)
2. Einen **Datenwert** (den eigentlichen Inhalt)

Beispiel:

- Bezeichner: `hud.food`
- Daten: `18/20`

# Schnellstart

1. Der Server sendet Daten mit `/fmdata send ...`
2. Der Client empfängt sie mit dem FancyMenu-Listener **Bei Empfang von FM Data**
3. Der Client kann mit der Aktion **FM Data an Server senden** auch Daten zurücksenden
4. Der Server kann mit `/fmdata listener ...` automatisch darauf reagieren
5. Der Server kann mit `/fmdata welcome_data ...` beim Beitritt automatisch Daten senden

# Server -> Client

Verwende:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Beispiele:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Hinweise:

- `<target_players>` unterstützt Spielernamen und Selektoren wie `@a`, `@p` und `@s`
- Verwende Anführungszeichen für Werte mit Leerzeichen

# Client: Daten empfangen

Verwende den FancyMenu-Listener:

- **Bei Empfang von FM Data**

Verfügbare Variablen:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` enthält:

- Bei Mehrspieler den Server-IP
- Bei Einzelspieler `integrated_server`

Typische Anwendungsfälle:

- Textelemente aktualisieren
- Menüaktionen auslösen
- Logik anhand des empfangenen Bezeichners oder der Daten ausführen

# Client -> Server

Verwende die FancyMenu-Aktion:

- **FM Data an Server senden**

Die Aktion hat zwei Eingabefelder:

1. Datenbezeichner
2. Daten

Der Server kann eingehende Daten anschließend mit `/fmdata listener ...` verarbeiten.

# Server-Listener

Server-Listener warten auf eingehende Daten von Clients und können beim Auslösen einen oder mehrere Befehle ausführen.

Server-Listener werden gespeichert und bleiben auch nach einem Neustart aktiv.

Verwalte sie mit:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Syntax zum Hinzufügen/Bearbeiten

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Syntax zum Entfernen

```mcfunction
/fmdata listener remove <listener_name>
```

## Übereinstimmungstypen

Für `matching_type_identifier` und `matching_type_data` sind folgende Werte möglich:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Regeln für Übereinstimmungen

- `ignore_case_identifier` und `ignore_case_data` sind Schalter mit den Werten true/false
- `listen_for_identifier` unterstützt den Platzhalter `*` (stimmt immer überein)
- `listen_for_data` unterstützt den Platzhalter `*` (stimmt immer überein)
- `fire_for_player` verwendet normale Spielerselektoren (zum Beispiel `@a`, `@p`, `Player761`)

## Befehle beim Auslösen

`commands_to_execute_on_fire` ist ein einzelnes Texteingabefeld.

- Trenne mehrere Befehle mit `|||`
- Schreibe einen literalen Trenner als `\|\|\|`

Du kannst hier zwei spezielle Platzhalter verwenden, die direkt vor der Ausführung der Befehle ersetzt werden:

- `%fm_sender%` -> Spieler, der die FM Data gesendet hat
- `%fm_data%` -> vom Client empfangener Datenwert

Die Befehle werden als Serverbefehle ausgeführt.

## Befehlsbeispiele

Auf einen Tastendruck eines beliebigen Spielers reagieren:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Mehrere Befehle ausführen, wenn die Daten `gold` enthalten:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Begrüßungsdaten

Begrüßungsdaten senden beim Beitritt FM Data an passende Spieler.

Verwalte Einträge mit:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Syntax zum Hinzufügen/Bearbeiten

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Syntax zum Entfernen

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Hinweise:

- `<target_player>` unterstützt normale Selektoren wie `@a`, `@p` und `@s`
- Daten werden beim Beitritt an passende Spieler gesendet
- Einträge werden automatisch gespeichert und geladen

## Befehlsbeispiele

Begrüßungsdaten an alle Spieler senden, die beitreten:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Begrüßungsdaten nur an einen Spieler senden:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Für KI exportieren

Um Alice oder eine andere KI um Hilfe zu bitten, exportiere die Listener und Begrüßungsdaten des Servers mit [Für KI exportieren](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` sendet eine Chatnachricht, über die der Export durch Anklicken kopiert werden kann. `file` speichert ihn auf dem Server unter `fancymenu_data/ai_exports/`.

# Bewährte Vorgehensweisen

1. Verwende aussagekräftige Bezeichner wie `hud.food`, `menu.shop.open` oder `quest.progress`.
2. Achte darauf, dass das Datenformat für jeden Bezeichner einheitlich bleibt.
3. Fange einfach an: Teste mit `/fmdata send`, bevor du komplexe Listener erstellst.
4. Verwende `@a` nur, wenn du wirklich ein globales Verhalten möchtest.
5. Verwende `/fmdata listener list` und `/fmdata welcome_data list`, damit deine Konfigurationen übersichtlich bleiben.
