---
title: Befehle
description: FancyMenus Befehle und wie man sie verwendet.
---
# Befehle

FancyMenu fügt dem Spiel einige Befehle hinzu, die sehr nützlich sein können, wenn man sie mit anderen Mods wie FTB Quests kombiniert.

> [!WARNING]
> FancyMenu muss im **SERVER** (und Client) installiert sein, um Befehle im Mehrspielermodus zu verwenden!

## Zielspieler und Berechtigungen

Das Zielspieler-Argument von `/openguiscreen`, `/closeguiscreen` und `/fmlayout` ist optional. Wenn ein Spieler es weglässt, wirkt sich der Befehl auf diesen Spieler aus. Wenn ein Ziel angegeben wird, können normale Spielernamen und Selektoren wie `@a` verwendet werden.

- Das Angeben des Zielarguments bei `/openguiscreen` oder `/closeguiscreen` erfordert **Berechtigungsstufe 2** (Game Master / OP Stufe 2), auch wenn damit die Befehlsquelle selbst gemeint ist.
- Das Angeben des Zielarguments bei `/fmlayout` erfordert **Berechtigungsstufe 3** (Admin / OP Stufe 3), auch wenn damit die Befehlsquelle selbst gemeint ist.
- Jeder `/fmdata`-Unterbefehl erfordert **Berechtigungsstufe 2** (Game Master / OP Stufe 2).

Bei den drei Befehlen mit optionalem Ziel funktioniert das Weglassen des Ziels nur, wenn die Befehlsquelle ein Spieler ist. Die Serverkonsole muss ein Ziel angeben und die Berechtigungsanforderung des Zielarguments erfüllen.

## /openguiscreen

Der Befehl `/openguiscreen` öffnet eine Vanilla-, Mod- oder [Benutzerdefinierte GUI](./custom-guis). Er kann andere Spieler ansteuern, wenn FancyMenu auf dem Server und auf deren Clients installiert ist.

Siehe [GUIs per Befehl öffnen](./opengui-command) und [Bildschirm-Identifikatoren](./screen-identifiers).

Nicht jeder Mod-Bildschirm kann direkt erstellt werden. FancyMenu zeigt einen Fehler an, wenn ein Zielbildschirm nicht unterstützt wird. Verwende in einem lokalen Layout [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) auf dem Widget, das ihn normalerweise öffnet.

**Verwendung:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

Der Befehl `/closeguiscreen` schließt den aktuellen Bildschirm für die Befehlsquelle oder ausgewählte Spieler. Er ist nützlich in Kombination mit Quest-, Event- oder Automatisierungsmods, die Befehle ausführen können.

**Verwendung:** `/closeguiscreen [<target_players>]`

## /fmlayout

Der Befehl `/fmlayout` legt fest, ob ein Layout auf einem oder mehreren Clients aktiviert ist. Verwende den Namen des Layouts genau so, wie er in FancyMenu angezeigt wird, und setze Namen mit Leerzeichen in Anführungszeichen.

**Verwendung:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Beispiele:

- `/fmlayout quest_complete true` aktiviert `quest_complete` für den Spieler, der den Befehl ausführt.
- `/fmlayout quest_complete false @a` deaktiviert es für alle online Spieler. Das Angeben des Zielarguments erfordert Berechtigungsstufe 3.

## /fmvariable

Der Befehl `/fmvariable` setzt und liest [FancyMenu-Variablen](./variables).

Um diesen Befehl als ein anderer Spieler auszuführen, verwende Vanillas `/execute as`-Befehl:
`/execute as ExamplePlayer run fmvariable ...`

**Verwendung:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Abrufen

Um einen **Variablenwert abzurufen**, verwende den Unterbefehl `get` so:
`/fmvariable get some_variable`

Dann wird der Wert dieser Variable in deinem Chat ausgegeben.

### Setzen

Um eine **Variable zu setzen**, setze den Booleschen Wert für das Chat-Feedback vor den neuen Wert:
`/fmvariable set some_variable true new_value`

Das Argument `send_chat_feedback` steuert, ob FancyMenu die Änderung im Chat bestätigt. Das Argument `set_to_value` verbraucht den Rest des Befehls, daher kann der Wert Leerzeichen enthalten. Zum Beispiel speichert `/fmvariable set greeting false Hello from FancyMenu` `Hello from FancyMenu`, ohne Erfolgsfeedback zu senden.

## /fmdata

Der Befehl `/fmdata` sendet benutzerdefinierte Daten zwischen dem Server und FancyMenu-Clients, verwaltet serverseitige Listener und konfiguriert Daten, die beim Beitritt von Spielern gesendet werden. Jeder `/fmdata`-Unterbefehl erfordert Berechtigungsstufe 2.

Siehe [FM Data](./fm-data) für alle Unterbefehle, die Syntax und Beispiele.
