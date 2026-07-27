---
title: GUIs per Befehl öffnen
description: Wie man Vanilla- und benutzerdefinierte GUIs per Befehl öffnet.
---

# GUIs per Befehl öffnen

Der Befehl `/openguiscreen` öffnet Vanilla-, Mod- und [benutzerdefinierte GUIs](./custom-guis). Er kann andere Spieler ansprechen, wenn FancyMenu auf dem Server und auf deren Clients installiert ist.

Um ein GUI zu öffnen, verwende `/openguiscreen <screen_identifier> [<target_players>]`.

Ersetze `<screen_identifier>` durch den exakten, groß-/kleinschreibungssensitiven Bezeichner des benutzerdefinierten GUIs oder des Vanilla-/Mod-Bildschirms.

Um einen Bezeichner zu finden, öffne den gewünschten Bildschirm und aktiviere das Debug-Overlay mit **STRG + ALT + D**. Wähle den Bezeichner in der ersten Zeile aus, um ihn zu kopieren. Siehe [Bildschirm-Bezeichner](./screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Lasse `[<target_players>]` weg, um das GUI für dich selbst zu öffnen, oder verwende einen Spielernamen oder einen Selektor wie `@a`, um es für einen oder mehrere Spieler zu öffnen. Das Angeben des Ziel-Arguments erfordert Berechtigungsstufe 2 (Game Master / OP-Stufe 2), selbst wenn du dich selbst angibst, und jeder Zielspieler muss FancyMenu auf seinem Client installiert haben.

Nicht jeder Mod-Bildschirm kann direkt erstellt werden. FancyMenu zeigt einen Fehler an, wenn ein Zielbildschirm nicht unterstützt wird. Verwende in einem lokalen Layout [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) auf dem Widget, das ihn normalerweise öffnet.

# GUIs per Befehl schließen

Falls du es ausnahmsweise brauchst, schließt `/closeguiscreen [<target_players>]` den aktuellen Bildschirm. Ohne Zielangabe betrifft der Befehl dich selbst; das Angeben des Ziel-Arguments erfordert Berechtigungsstufe 2.
