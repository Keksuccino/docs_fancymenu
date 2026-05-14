---
title: Befehle
description: FancyMenus Befehle und wie man sie verwendet.
---

# Befehle

FancyMenu fügt dem Spiel einige Befehle hinzu, die sehr nützlich sein können, wenn man sie mit anderen Mods wie FTB Quests kombiniert.

> FancyMenu muss im **SERVER** (und auf dem Client) installiert sein, um Befehle im Multiplayer verwenden zu können!
{.is-warning}

## /openguiscreen

Der Befehl `/openguiscreen` ermöglicht es dir, eine GUI zu öffnen (Vanilla/Mod und benutzerdefinierte GUIs).
Er kann sogar aus der Ferne GUIs für andere Spieler öffnen, wenn FancyMenu sowohl auf dem Server als auch auf den Clients installiert ist.

Eine genauere Beschreibung dieses Befehls findest du auf der Seite [GUIs per Befehl öffnen](/opengui-command).

Dieser Befehl funktioniert nicht für jeden Bildschirm, insbesondere nicht für Mod-Bildschirme. Wenn der Befehl einen Bildschirm nicht öffnen kann, wird eine Fehlermeldung angezeigt. In diesem Fall kannst du nicht viel tun, da es sich wahrscheinlich um einen Bildschirm handelt, der zu komplex ist, um von FancyMenu automatisch geöffnet zu werden.

Ich werde außerdem keine manuelle Kompatibilität mehr für Mod-Bildschirme hinzufügen, da es ewig dauern würde, für alle vorhandenen Mods Unterstützung einzubauen, sorry.

**Verwendung:** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

Der Befehl `/closeguiscreen` ermöglicht es dir, die aktuelle GUI zu schließen.

Hä? Das ist doch völlig nutzlos, sagst du?
Nun ja, eigentlich nicht.

Dieser Befehl ist nützlich, wenn du Mods verwendest, die Befehle durch bestimmte Aktionen auslösen.
Also ja, ohne andere Mods ist dieser Befehl absolut nutzlos, kann aber sehr hilfreich sein, wenn du die richtigen Mods installiert hast!

**Verwendung:** `/closeguiscreen <target_player>`

## /fmvariable

Der Befehl `/fmvariable` ermöglicht es dir, FancyMenu-Variablen zu setzen und auszulesen.

Um diesen Befehl auf Servern als ein anderer Spieler auszuführen, kannst du den Vanilla-Befehl `/execute as` verwenden.
Wenn du also den Befehl `/fmvariable` als der Spieler `ExamplePlayer` ausführen möchtest, würdest du Folgendes eingeben:
`/execute as ExamplePlayer run fmvariable...`.

**Verwendung:** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### Auslesen
Um einen **Variablenwert auszulesen**, verwende den Unterbefehl `get` wie hier:
`/fmvariable get some_variable`

Dann wird der Wert dieser Variablen in deinem Chat ausgegeben.

### Setzen
Um eine **Variable zu setzen**, verwende den Unterbefehl `set` wie hier:
`/fmvariable set some_variable new_value true`

Das letzte Argument legt fest, ob du Chat-Rückmeldung erhalten möchtest, also ob dieser Befehl Nachrichten in deinem Chat ausgeben soll.
