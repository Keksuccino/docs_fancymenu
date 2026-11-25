---
title: Befehle
description: Die Befehle von FancyMenu und ihre Verwendung.
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# Befehle

FancyMenu fügt dem Spiel einige Befehle hinzu, die in Kombination mit anderen Mods wie FTB Quests sehr nützlich sein können.

> [!WARNING]
> Damit Befehle im Mehrspielermodus funktionieren, muss FancyMenu auf dem **SERVER** und auf dem Client installiert sein!

## Zielspieler und Berechtigungen

Das Argument für Zielspieler von `/openguiscreen`, `/closeguiscreen` und `/fmlayout` ist optional. Wird es weggelassen, wirkt sich der Befehl auf den Spieler aus, der ihn ausführt. Wird ein Ziel angegeben, können normale Spielernamen und Selektoren wie `@a` verwendet werden.

- Zum Übergeben des Zielarguments an `/openguiscreen` oder `/closeguiscreen` ist **Berechtigungsstufe 2** (Game Master / OP-Stufe 2) erforderlich, selbst wenn als Ziel der Spieler angegeben wird, der den Befehl ausführt.
- Zum Übergeben des Zielarguments an `/fmlayout` ist **Berechtigungsstufe 3** (Admin / OP-Stufe 3) erforderlich, selbst wenn als Ziel der Spieler angegeben wird, der den Befehl ausführt.
- Für jeden Unterbefehl von `/fmdata` ist **Berechtigungsstufe 2** (Game Master / OP-Stufe 2) erforderlich.

Bei den drei Befehlen mit optionalen Zielangaben funktioniert das Weglassen des Ziels nur, wenn der Befehl von einem Spieler ausgeführt wird. Über die Serverkonsole muss ein Ziel angegeben werden; außerdem muss die dafür erforderliche Berechtigungsstufe erfüllt sein.

## /openguiscreen

Der Befehl `/openguiscreen` öffnet eine Vanilla-, Mod- oder [benutzerdefinierte GUI](/custom-guis). Wenn FancyMenu auf dem Server und bei den jeweiligen Clients installiert ist, können auch andere Spieler als Ziel ausgewählt werden.

Siehe [GUIs per Befehl öffnen](/opengui-command) und [Bildschirmkennungen](/screen-identifiers).

Nicht jeder Mod-Bildschirm kann direkt erstellt werden. Wenn ein Zielbildschirm nicht unterstützt wird, zeigt FancyMenu eine Fehlermeldung an. Verwende in einem lokalen Layout beim Widget, das den Bildschirm normalerweise öffnet, die Option [**Vanilla-/Mod-Schaltfläche nachahmen**](/action-scripts#mimic-vanillamod-button).

**Verwendung:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

Der Befehl `/closeguiscreen` schließt den aktuellen Bildschirm für den Spieler, der den Befehl ausführt, oder für ausgewählte Spieler. Er ist nützlich in Verbindung mit Quests-, Ereignis- oder Automatisierungsmods, die Befehle ausführen können.

**Verwendung:** `/closeguiscreen [<target_players>]`

## /fmlayout

Mit dem Befehl `/fmlayout` wird festgelegt, ob ein Layout auf einem oder mehreren Clients aktiviert ist. Verwende den Namen des Layouts genau so, wie er in FancyMenu angezeigt wird, und setze Namen mit Leerzeichen in Anführungszeichen.

**Verwendung:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Beispiele:

- `/fmlayout quest_complete true` aktiviert `quest_complete` für den Spieler, der den Befehl ausführt.
- `/fmlayout quest_complete false @a` deaktiviert das Layout für alle Spieler, die online sind. Zum Übergeben des Zielarguments ist Berechtigungsstufe 3 erforderlich.

## /fmvariable

Mit dem Befehl `/fmvariable` kannst du [FancyMenu-Variablen](/variables) setzen und auslesen.

Um diesen Befehl als ein anderer Spieler auszuführen, verwende den Vanilla-Befehl `/execute as`:
`/execute as ExamplePlayer run fmvariable ...`

**Verwendung:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Auslesen

Um den **Wert einer Variable auszulesen**, verwende den Unterbefehl `get` wie folgt:
`/fmvariable get some_variable`

Der Wert der Variable wird anschließend im Chat ausgegeben.

### Setzen

Um eine **Variable zu setzen**, gib den booleschen Wert für die Chat-Rückmeldung vor dem neuen Wert an:
`/fmvariable set some_variable true new_value`

Das Argument `send_chat_feedback` legt fest, ob FancyMenu die Änderung im Chat bestätigt. Das Argument `set_to_value` umfasst den Rest des Befehls. Der Wert kann daher Leerzeichen enthalten. Beispielsweise speichert `/fmvariable set greeting false Hallo von FancyMenu` den Wert `Hallo von FancyMenu`, ohne eine Erfolgsmeldung auszugeben.

## /fmdata

Der Befehl `/fmdata` übermittelt benutzerdefinierte Daten zwischen dem Server und FancyMenu-Clients, verwaltet serverseitige Listener, konfiguriert die beim Beitritt von Spielern gesendeten Daten und exportiert diese Einrichtung für [KI-Chats](/export-for-ai#servers). Für jeden Unterbefehl von `/fmdata` ist Berechtigungsstufe 2 erforderlich.

Alle Unterbefehle, die Syntax und Beispiele findest du unter [FM Data](/fm-data).
