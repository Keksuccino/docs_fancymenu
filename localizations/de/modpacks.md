---
title: Modpacks
description: Wie man Layouts in ein Modpack einbindet.
---

# FancyMenu in Modpacks

Es ist ganz einfach, dein FancyMenu-Setup in ein Modpack einzubinden, und es braucht nur ein paar einfache Schritte.

> Diese Seite ist **NUR** für FancyMenu-Setups gedacht, die vollständig in **FancyMenu v3+** erstellt wurden. Wenn du also ein Legacy-Setup verwendest (in v2 erstellt und auf v3 konvertiert), können einige Schritte anders sein.
{.is-warning}

# Das FancyMenu-Setup in dein Modpack einbinden

Das Wichtigste ist, dass du einen speziellen Ordner kopierst, den FancyMenu verwendet, um alle deine Designs zu speichern.

## Was du finden musst

1. **Dein "Minecraft-Instanz"-Ordner:** Das ist der Hauptordner auf deinem Computer, in dem alle Dateien für eine bestimmte Minecraft-Einrichtung gespeichert sind (also z. B. die, in der du deine Menüs erstellt hast). Launcher wie CurseForge und Modrinth nennen diese Ordner "Instanzen" oder "Profile".
2. **Der `config`-Ordner:** In deinem Minecraft-Instanzordner gibt es normalerweise einen Ordner namens `config`. Dort speichern viele Mods ihre Einstellungen.
3. **Der `fancymenu`-Ordner:** In diesem `config`-Ordner erstellt FancyMenu seinen eigenen Ordner namens `fancymenu`. Das ist der Goldordner, den wir brauchen!

## So findest du den Speicherort der Instanz

### Wenn du die CurseForge-App verwendest

1. Öffne CurseForge.
2. Suche in der Liste dein Minecraft-Profil/deine Instanz und öffne es.
3. Klicke auf die drei Punkte.
4. Wähle "Open Folder". Dadurch wird der Hauptordner dieser Minecraft-Instanz geöffnet.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Wenn du die Modrinth-App verwendest

1. Öffne die Modrinth-App.
2. Suche in der Liste dein Minecraft-Profil/deine Instanz und öffne es.
3. Klicke auf die drei Punkte.
4. Wähle "Open Folder". Dadurch wird der Hauptordner dieser Minecraft-Instanz geöffnet.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Für andere Launcher

Suche nach einer ähnlichen Option wie "Open Folder", "Open Instance Folder" oder "View Files" für deine spezielle Minecraft-Einrichtung.

## Das FancyMenu-Setup kopieren

1. Navigiere zum `config`-Ordner deiner MODPACK-Instanz (der Instanz, in die du dein Setup kopieren möchtest).
2. Falls darin bereits ein `fancymenu`-Ordner vorhanden ist, LÖSCHE ihn.
3. Öffne den `config`-Ordner der QUELL-Instanz (der Instanz, aus der du das Setup übernehmen möchtest).
4. Kopiere den `fancymenu`-Ordner aus dem `config`-Ordner deiner QUELL-Instanz in den `config`-Ordner deiner MODPACK-Instanz.
5. Fertig. Das war's. Starte deine Modpack-Instanz jetzt neu, und das Setup sollte geladen werden.

> Bitte beachte, dass alte Legacy-Setups aus FancyMenu v2 (selbst wenn sie auf v3 konvertiert wurden) es erlaubten, Layout-Assets außerhalb des Ordners `/config/fancymenu/assets/` zu speichern. In diesem Fall musst du sicherstellen, dass du auch alle deine Assets in das Modpack aufnimmst.
{.is-danger}

# Die Menüleiste und Hotkeys deaktivieren

Du möchtest sicher nicht, dass die Menüleiste von FancyMenu in deinem Modpack sichtbar bleibt, also solltest du sie deaktivieren. Aber da die Leute immer noch den Hotkey drücken könnten, um sie wieder sichtbar zu machen, machen wir etwas ein wenig *aggressiveres*.

Navigiere zu `/config/fancymenu/options.txt` und öffne die Datei in einem Texteditor.

Setze nun `modpack_mode` auf `true` und speichere die Datei.
Dadurch werden alle Overlays und Hotkeys vollständig deaktiviert.

Um deine Layouts später wieder bearbeiten zu können, setze die Konfigurationsoption einfach wieder auf `false`.

# Den Willkommensbildschirm deaktivieren

In den meisten Fällen sollte das nicht nötig sein. Falls du den Willkommensbildschirm aber noch nicht geschlossen hast (der Bildschirm, der dich auffordert, die Dokumentation zu lesen), stelle sicher, dass du `show_welcome_screen` in `/config/fancymenu/options.txt` auf `false` setzt.

Dieser Bildschirm wird nur einmal angezeigt und deaktiviert sich selbst, wenn du auf die Schaltfläche **Open Documentation** klickst. Auch hier sollte ein manuelles Ändern also in den meisten Fällen nicht nötig sein.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
