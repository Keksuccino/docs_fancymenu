---
title: Titelbildschirm-Symbol
description: >-
  Wie man das kleine Diamant- oder Smaragd-Symbol (grün oder blau) im
  Titelbildschirm ausblendet/entfernt.
---

# Smaragd-/Diamant-Symbol im Titelbildschirm

Wenn du Schwierigkeiten hast, das kleine Symbol auszublenden, das immer wieder in deinem Titelbildschirm erscheint und wie ein kleiner Diamant oder Smaragd aussieht (ein kleines grünes oder blaues Symbol), dann handelt es sich meistens um die Update-Benachrichtigung eines Mods, entweder von Mod Menu (Fabric-Mod) oder Forge (integrierte Modloader-Funktion).

In manchen Fällen kann es auch Teil von Vanilla-Minecrafts Realms-Schaltfläche sein (um Benachrichtigungen anzuzeigen).

# Das Mod-Menu-Symbol ausblenden

Um das Symbol von Mod Menu auszublenden, musst du den "Update Indicator" in den Einstellungen deaktivieren.

Klicke auf die **Mods**-Schaltfläche -> Fahre mit der Maus über das Symbol des Mod-Menu-Mods in der Mod-Liste -> Klicke darauf -> Setze den "Update Indicator" auf "Hidden".

# Das Forge-Symbol ausblenden

Forge verwendet einen eingebauten Versionsprüfer, um das Smaragd-Symbol anzuzeigen, wenn Mods veraltet sind. Du kannst ihn deaktivieren:

1. Öffne deine Datei `config/fml.toml`.
2. Suche die Einstellung `versionCheck`.
3. Setze sie auf `false`: `versionCheck = false`
4. Speichere die Datei und starte Minecraft neu.

Dadurch wird die Versionsprüfung vollständig deaktiviert, wodurch das Smaragd-Symbol beim Start ebenfalls ausgeblendet wird.

Eine andere Möglichkeit, das Symbol auszublenden, besteht einfach darin, die gesamte Mods-Schaltfläche mit FancyMenu zu verstecken. Wenn du die Schaltfläche ausblendest, wird auch das Symbol ausgeblendet.

# Die Vanilla-Realms-Symbole ausblenden

Falls es weder das Mod-Menu- noch das Forge-Symbol ist, handelt es sich wahrscheinlich um die eigenen Realms-Benachrichtigungssymbole von Minecraft. Diese Symbole erscheinen ungefähr an der Position der Realms-Schaltfläche und können mit FancyMenu im Layout-Editor ausgeblendet werden. Du musst ein Layout "für den aktuellen Bildschirm" erstellen (in diesem Fall den Titelbildschirm), und dann siehst du die Realms-Symbole als eigenes Element im Editor. Um sie auszublenden, mache einfach einen **Rechtsklick** darauf und klicke auf **Delete**.

Die Realms-Symbole können ein Zeitungssymbol, ein Diamant-Symbol und andere sein, zum Beispiel ein roter Kreis mit einem Benachrichtigungszähler.
