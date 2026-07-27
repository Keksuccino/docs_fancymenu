---
title: Client < - > Server-Datenaustausch
description: >-
  Benutzerdefinierte Daten zwischen Server und Client mit FancyMenu senden und
  empfangen.
---

# FM Data

Das System „FM Data“ ermöglicht es dir, benutzerdefinierte Textdaten zwischen Server und Client zu senden.

Jeder Unterbefehl von `/fmdata` erfordert **Berechtigungsstufe 2** (Game Master / OP Stufe 2).

Jede FM-Data-Nachricht hat:

1. Eine **Datenkennung** (welche Art von Nachricht dies ist)
2. Einen **Datenwert** (der eigentliche Inhalt)

Beispiel:

- Kennung: `hud.food`
- Daten: `18/20`

# Schnellstart

1. Server sendet Daten mit `/fmdata send ...`
2. Client empfängt sie mit dem FancyMenu-Listener **On FM Data Received**
3. Client kann Daten auch mit der Aktion **Send FM Data To Server** zurücksenden
4. Server kann automatisch mit `/fmdata listener ...` reagieren
5. Server kann beim Beitreten automatisch Daten mit `/fmdata welcome_data ...` senden

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

- **On FM Data Received**

Verfügbare Variablen:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` ist:

- Server-IP im Mehrspieler
- `integrated_server` im Einzelspieler

Häufige Anwendungsfälle:

- Textelemente aktualisieren
- Menüaktionen auslösen
- Logik basierend auf eingehender Kennung / Daten ausführen

# Client -> Server

Verwende die FancyMenu-Aktion:

- **Send FM Data To Server**

Die Aktion hat 2 Eingaben:

1. Datenkennung
2. Daten

Der Server kann eingehende Daten dann mit `/fmdata listener ...` verarbeiten.

# Server-Listener

Server-Listener lauschen auf eingehende Daten von Clients und können beim Auslösen einen oder mehrere Befehle ausführen.

Server-Listener werden gespeichert und bleiben nach einem Neustart aktiv.

Verwalte sie mit:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Syntax zum Hinzufügen / Bearbeiten

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

## Abgleichtypen

`matching_type_identifier` und `matching_type_data` können sein:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Abgleichregeln

- `ignore_case_identifier` und `ignore_case_data` sind Umschalter mit true/false
- `listen_for_identifier` unterstützt Platzhalter `*` (passt immer)
- `listen_for_data` unterstützt Platzhalter `*` (passt immer)
- `fire_for_player` verwendet normale Spieler-Selektoren (zum Beispiel `@a`, `@p`, `Player761`)

## Befehle bei Auslösung

`commands_to_execute_on_fire` ist eine einzelne Texteingabe.

- Trenne mehrere Befehle mit `|||`
- Maskiere einen literalen Separator als `\|\|\|`

Hier kannst du zwei spezielle Platzhalter verwenden, die direkt vor der Ausführung der Befehle ersetzt werden:

- `%fm_sender%` -> Spieler, der die FM Data gesendet hat
- `%fm_data%` -> von Client empfangener Datenwert

Befehle werden als Serverbefehle ausgeführt.

## Beispielbefehle

Auf einen Tastendruck von einem beliebigen Spieler reagieren:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% hat den Knopf gedrückt\"}"
```

Mehrere Befehle ausführen, wenn Daten `gold` enthalten:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Belohnung von %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Willkommensdaten

Willkommensdaten senden FM Data an passende Spieler, wenn sie beitreten.

Verwalte Einträge mit:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Syntax zum Hinzufügen / Bearbeiten

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

- `<target_player>` unterstützt normale Selektoren wie `@a`, `@p`, `@s`
- Daten werden an passende Spieler gesendet, wenn sie beitreten
- Einträge werden automatisch gespeichert und geladen

## Beispielbefehle

Willkommensdaten an alle beitretenden Spieler senden:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Willkommen!"
```

Willkommensdaten nur an einen Spieler senden:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP-Vorteile aktiviert"
```

# Best Practices

1. Verwende klare Kennungen wie `hud.food`, `menu.shop.open`, `quest.progress`.
2. Halte das Datenformat für jede Kennung konsistent.
3. Fang einfach an: Teste zuerst mit `/fmdata send`, bevor du komplexe Listener baust.
4. Verwende `@a` nur, wenn du wirklich globales Verhalten willst.
5. Nutze `/fmdata listener list` und `/fmdata welcome_data list`, um Konfigurationen sauber zu halten.
