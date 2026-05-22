---
title: Titelbildschirm-Glyph
description: >-
  Wie man das kleine Diamant- oder Smaragd-Symbol (grün oder blau) im
  Titelbildschirm ausblendet/entfernt.
---
# Smaragd-/Diamant-Symbol im Titelbildschirm

Wenn du Schwierigkeiten hast, das kleine Symbol auszublenden, das immer wieder in deinem Titelbildschirm erscheint und wie ein kleiner Diamant oder Smaragd aussieht (grünes oder blaues kleines Symbol), dann handelt es sich dabei meist um die Update-Benachrichtigung entweder von Mod Menu (Fabric-Mod) oder von Forge (integrierte Modloader-Funktion).

In manchen Fällen kann es auch Teil von Vanillas Realms-Schaltfläche sein (um Benachrichtigungen anzuzeigen).

# Das Mod-Menu-Symbol ausblenden

Um die Glyphe von Mod Menu auszublenden, musst du in den Einstellungen den "Update-Indikator" deaktivieren.

Klicke auf die **Mods**-Schaltfläche -> Fahre mit der Maus über das Symbol der Mod-Menu-Mod in der Mod-Liste -> Klicke darauf -> Setze den "Update Indicator" auf "Hidden".

# Das Forge-Symbol ausblenden

Forge verwendet einen integrierten Versionsprüfer, um das Smaragd-Symbol anzuzeigen, wenn Mods veraltet sind. Du kannst ihn deaktivieren:

1. Öffne deine Datei `/config/fml.toml`.
2. Suche die Einstellung `versionCheck`.
3. Setze sie auf `false`: `versionCheck = false`
4. Speichere und starte Minecraft neu.

Dadurch wird die Versionsprüfung vollständig deaktiviert, wodurch auch die Smaragd-Glyphe beim Start ausgeblendet wird.

Eine andere Möglichkeit, das Symbol auszublenden, besteht einfach darin, die gesamte Mods-Schaltfläche über FancyMenu zu verstecken. Wenn du die Schaltfläche versteckst, wird auch die Glyphe ausgeblendet.

# Das NeoForge-Symbol ausblenden

Bei NeoForge funktioniert es genau gleich wie bei klassischem Forge.

1. Öffne deine Datei `/config/fml.toml`.
2. Suche die Einstellung `versionCheck`.
3. Setze sie auf `false`: `versionCheck = false`
4. Speichere und starte Minecraft neu.

# Die Vanilla-Realms-Symbole ausblenden

Falls es weder das Mod-Menu- noch das Forge-Symbol ist, handelt es sich wahrscheinlich um die eigenen Realms-Benachrichtigungssymbole von Minecraft. Diese Symbole werden ungefähr an der Position der Realms-Schaltfläche angezeigt und können mit FancyMenu im Layout-Editor ausgeblendet werden. Du musst ein Layout „für den aktuellen Bildschirm“ erstellen (in diesem Fall der Titelbildschirm), und dann siehst du die Realms-Symbole als eigenes Element im Editor. Um sie auszublenden, klicke einfach mit der **rechten Maustaste** darauf und dann auf **Delete**.

Die Realms-Symbole können ein Zeitungssymbol, eine Diamant-Glyphe und andere Symbole sein, zum Beispiel ein roter Kreis mit einem Benachrichtigungszähler.
