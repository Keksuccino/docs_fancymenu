---
title: Modpacks
description: Wie man Layouts in ein Modpack einbindet.
---

# FancyMenu in Modpacks

Dein FancyMenu-Setup in ein Modpack einzubinden ist ganz einfach und erfordert nur wenige Schritte.

> [!CAUTION]
> FancyMenu-Setups können Aktionen ausführen. Importiere sie nur aus Quellen, denen du vertraust.

> [!WARNING]
> Diese Seite ist **NUR** für FancyMenu-Setups gedacht, die vollständig in **FancyMenu v3+** erstellt wurden. Wenn du also ein Legacy-Setup verwendest (in v2 erstellt und auf v3 konvertiert), können einige Schritte anders sein.

# Das FancyMenu-Setup in dein Modpack einbinden

Das Wichtigste ist, einen speziellen Ordner zu kopieren, den FancyMenu verwendet, um alle deine Designs zu speichern.

## Was du finden musst

1. **Dein Ordner der „Minecraft-Instanz“:** Das ist der Hauptordner auf deinem Computer, in dem alle Dateien für eine bestimmte Minecraft-Einrichtung gespeichert sind (z. B. die, in der du deine Menüs erstellt hast). Launcher wie CurseForge und Modrinth nennen diese „Instanzen“ oder „Profile“.
2. **Den `config`-Ordner:** In deinem Minecraft-Instanzordner gibt es normalerweise einen Ordner namens `config`. Dort speichern viele Mods ihre Einstellungen.
3. **Den `fancymenu`-Ordner:** In diesem `config`-Ordner erstellt FancyMenu seinen eigenen Ordner namens `fancymenu`. Das ist der goldene Ordner, den wir brauchen!

## So findest du den Speicherort der Instanz

### Wenn du die CurseForge-App verwendest

1. Öffne CurseForge.
2. Suche dein Minecraft-Profil/deine Minecraft-Instanz in der Liste und öffne sie.
3. Klicke auf die drei Punkte.
4. Wähle „Ordner öffnen“. Dadurch wird der Hauptordner dieser Minecraft-Instanz geöffnet.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Wenn du die Modrinth-App verwendest

1. Öffne die Modrinth-App.
2. Suche dein Minecraft-Profil/deine Minecraft-Instanz in der Liste und öffne sie.
3. Klicke auf die drei Punkte.
4. Wähle „Ordner öffnen“. Dadurch wird der Hauptordner dieser Minecraft-Instanz geöffnet.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Für andere Launcher

Suche nach einer ähnlichen Option wie „Ordner öffnen“, „Instanzordner öffnen“ oder „Dateien anzeigen“ für deine jeweilige Minecraft-Einrichtung.

## Das FancyMenu-Setup kopieren

1. Navigiere zum `config`-Ordner deiner MODPACK-Instanz (die Instanz, in die du dein Setup kopieren möchtest).
2. Falls dort bereits ein `fancymenu`-Ordner vorhanden ist, LÖSCHE ihn.
3. Öffne den `config`-Ordner der QUELL-Instanz (die Instanz, aus der du das Setup verwenden möchtest).
4. Kopiere den `fancymenu`-Ordner aus dem `config`-Ordner deiner QUELL-Instanz in den `config`-Ordner deiner MODPACK-Instanz.
5. Fertig. Das war’s. Starte jetzt deine Modpack-Instanz neu und du solltest sehen, wie das Setup geladen wird.

> [!CAUTION]
> Bitte beachte, dass alte Legacy-Setups aus FancyMenu v2 (selbst wenn sie auf v3 konvertiert wurden) es ermöglichten, Layout-Assets außerhalb des Ordners `<game-directory>/config/fancymenu/assets/` zu speichern. In diesem Fall musst du also sicherstellen, dass du auch alle deine Assets in das Modpack aufnimmst.

# Menüleiste und Hotkeys deaktivieren

Du möchtest natürlich nicht, dass FancyMenus Menüleiste in deinem Modpack sichtbar bleibt, also solltest du sie deaktivieren. Aber da Spieler sie trotzdem mit dem Hotkey wieder einblenden könnten, machen wir etwas etwas *radikaleres*.

Navigiere zu `<game-directory>/config/fancymenu/options.txt` und öffne die Datei in einem Texteditor.

Setze nun `modpack_mode` auf `true` und speichere die Datei.
Dadurch werden alle Overlays und Hotkeys vollständig deaktiviert.

Um deine Layouts später wieder bearbeiten zu können, setze die Konfigurationsoption wieder auf `false`.

# Den Willkommensbildschirm deaktivieren

In den meisten Fällen sollte das nicht nötig sein. Falls du den Willkommensbildschirm jedoch noch nicht geschlossen hast (der Bildschirm, der dich auffordert, die Dokumentation zu lesen), stelle sicher, dass `show_welcome_screen` in `<game-directory>/config/fancymenu/options.txt` auf `false` gesetzt ist.

Der Bildschirm wird nur einmal angezeigt und deaktiviert sich selbst, wenn du auf die Schaltfläche **Dokumentation öffnen** klickst. Daher sollte ein manuelles Ändern auch hier in den meisten Fällen nicht nötig sein.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
