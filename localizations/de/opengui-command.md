---
title: GUIs per Befehl öffnen
description: So öffnest du Vanilla- und benutzerdefinierte GUIs per Befehl.
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# GUIs per Befehl öffnen

Mit dem Befehl `/openguiscreen` lassen sich Vanilla-, Mod- und [benutzerdefinierte GUIs](/custom-guis) öffnen. Wenn FancyMenu auf dem Server und bei den jeweiligen Spielern installiert ist, kannst du damit auch GUIs für andere Spieler öffnen.

Um ein GUI zu öffnen, verwende `/openguiscreen <screen_identifier> [<target_players>]`.

Ersetze `<screen_identifier>` durch die exakte, groß-/kleinschreibungssensitive Kennung des benutzerdefinierten GUIs oder des Vanilla-/Mod-Bildschirms.

Um die Kennung herauszufinden, öffne den gewünschten Bildschirm und aktiviere mit **STRG + ALT + D** die Debug-Ansicht. Wähle die Kennung in der ersten Zeile aus, um sie zu kopieren. Weitere Informationen findest du unter [Bildschirmkennungen](/screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Lass `[<target_players>]` weg, um das GUI für dich selbst zu öffnen. Alternativ kannst du einen Spielernamen oder einen Selektor wie `@a` angeben, um das GUI für einen oder mehrere Spieler zu öffnen. Für das Zielargument ist die Berechtigungsstufe 2 (Spielleiter / OP-Stufe 2) erforderlich – auch wenn du dich selbst als Ziel angibst. Außerdem muss FancyMenu bei jedem Zielspieler auf dem Client installiert sein.

Nicht jeder Mod-Bildschirm kann direkt erstellt werden. FancyMenu zeigt eine Fehlermeldung an, wenn der Zielbildschirm nicht unterstützt wird. Verwende in einem lokalen Layout auf dem Widget, das den Bildschirm normalerweise öffnet, die Option [**Vanilla-/Mod-Schaltfläche nachahmen**](/action-scripts#mimic-vanillamod-button).

# GUIs per Befehl schließen

Falls du es einmal brauchst: Mit `/closeguiscreen [<target_players>]` wird der aktuelle Bildschirm geschlossen. Wenn du das Ziel weglässt, betrifft der Befehl dich selbst. Für das Zielargument ist die Berechtigungsstufe 2 erforderlich.
