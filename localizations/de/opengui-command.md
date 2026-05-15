---
title: GUIs per Befehl öffnen
description: Wie Vanilla- und benutzerdefinierte GUIs per Befehl geöffnet werden.
---

# GUIs per Befehl öffnen

FancyMenu bringt einen Befehl mit, mit dem du Vanilla- und benutzerdefinierte GUIs per Befehl öffnen kannst.
Wenn FancyMenu sowohl auf dem **Server** als auch auf den **Clients** installiert ist, kannst du GUIs sogar aus der Ferne für **andere Spieler** öffnen.

Um ein GUI zu öffnen, verwende einfach den Befehl `/openguiscreen <screen_identifier> <target_player>`.

Ersetze `<screen_identifier>` durch die tatsächliche Menü-ID des GUIs, das du öffnen möchtest.
Das kann die ID deines benutzerdefinierten GUIs (erstellt mit FancyMenu) oder die normale Menü-ID eines Vanilla-/Mod-GUIs sein.

Um die **Menü-ID von Vanilla-/Mod-GUIs** herauszufinden, öffne das gewünschte Menü und aktiviere dann das **Debug-Overlay** von FancyMenu über **Customization -> Debug Overlay**. Anschließend kannst du auf die als erste Zeile angezeigte ID klicken, um sie in die Zwischenablage zu kopieren.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Lasse das Argument `<target_player>` leer, um das GUI für deinen Client zu öffnen, oder wähle einen Spieler (oder mehrere Spieler) aus, für den bzw. die das GUI geöffnet werden soll.
Beachte, dass der andere Spieler FancyMenu auf seinem Client installiert haben muss.

Dieser Befehl funktioniert nicht für jeden Bildschirm, insbesondere nicht für Mod-Bildschirme. Wenn der Befehl einen Bildschirm nicht öffnen kann, wird ein Fehler angezeigt. In diesem Fall kannst du leider nicht viel tun, da es sich dann wahrscheinlich um einen Bildschirm handelt, der zu komplex ist, um von FancyMenu automatisch geöffnet zu werden.

Ich werde auch keine manuelle Kompatibilität mehr für Mod-Bildschirme hinzufügen, da es ewig dauern würde, für all die Mods da draußen Unterstützung einzubauen, sorry.

# GUIs per Befehl schließen

Falls du es einmal brauchst, gibt es auch den Befehl `/closeguiscreen <target_player>`, der den aktuellen Bildschirm schließt.
