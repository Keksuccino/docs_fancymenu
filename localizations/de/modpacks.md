---
title: Modpacks
description: So bindest du Layouts in ein Modpack ein.
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# FancyMenu in Modpacks

Dein FancyMenu-Setup in ein Modpack einzubinden ist ganz einfach und erfordert nur wenige Schritte.

> [!CAUTION]
> FancyMenu-Setups können Aktionen ausführen. Importiere sie nur aus Quellen, denen du vertraust.

> [!WARNING]
> Diese Seite gilt **NUR** für FancyMenu-Setups, die vollständig mit **FancyMenu v3+** erstellt wurden. Wenn du also ein älteres Setup verwendest (erstellt mit v2 und zu v3 konvertiert), können sich einige Schritte unterscheiden.

# Dein Setup ins Modpack übernehmen

Am einfachsten überträgst du dein Setup von der Instanz, in der du es erstellt hast, in deine Modpack-Instanz mithilfe eines [Profils](/profiles):

1. Öffne in der Instanz mit deinem Setup **Menüleiste -> Anpassung -> Profile**, wähle dein Setup aus und [exportiere](/profiles#exporting) es als `.fmp`-Datei.
2. Öffne in deiner Modpack-Instanz das Profilfenster und [importiere](/profiles#importing) die `.fmp`-Datei, zum Beispiel, indem du sie auf das Fenster ziehst.
3. Wähle das importierte Profil aus und klicke auf **Profil laden**.

Das FancyMenu-Setup, das zuvor in der Modpack-Instanz vorhanden war, geht dabei nicht verloren. Es bleibt als eigenes Profil verfügbar, sodass du jederzeit zurückwechseln kannst.

# Das Setup mit deinem Modpack bereitstellen

Das geladene Profil entspricht dem Inhalt von `<game-directory>/config/fancymenu/`. Es wird also wie die Konfigurationsdateien anderer Mods im `config`-Ordner deines Modpacks mitgeliefert.

Alle anderen Profile der Instanz werden unter `<game-directory>/config/fancymenu/profiles/` gespeichert. Lösche vor dem Export deines Modpacks die Profile, die Spieler nicht erhalten sollen, oder lasse den Ordner `profiles` beim Export des Modpacks weg.

> [!CAUTION]
> Beachte, dass ältere Setups, die mit FancyMenu v2 erstellt wurden (auch wenn sie zu v3 konvertiert wurden), Layout-Ressourcen außerhalb des Ordners `<game-directory>/config/fancymenu/assets/` von FancyMenu speichern konnten. Profile enthalten nur den Konfigurationsordner von FancyMenu. In diesem Fall musst du also sicherstellen, dass du auch alle deine Ressourcen in das Modpack aufnimmst.

## Kontrollkästchen vor dem Export zurücksetzen

[Kontrollkästchen-Elemente](/elements#checkbox) speichern in `config/fancymenu/checkbox_states.json`, ob sie angekreuzt sind. Daher wären auch bei deinen Spielern die Kontrollkästchen angekreuzt, die du beim Testen angeklickt hast.

Damit Spieler mit einem sauberen Zustand starten, schließe das Spiel und lösche `checkbox_states.json`, bevor du dein Modpack oder Profil exportierst. Ohne diese Datei sind alle Kontrollkästchen zunächst nicht angekreuzt. Kontrollkästchen, die eine [Variable](/variables) verwenden, speichern ihren Zustand stattdessen in dieser Variable.

Dasselbe gilt für Dinge, die während des Testens durch Aktionen geändert wurden, zum Beispiel die Lautstärke von [Video-Elementen](/video). Weitere Informationen zu diesen Dateien findest du unter [Speicherorte für Daten](/data-storage-locations#your-setup).

## Den Instanzordner finden

Der Instanzordner ist der Hauptordner auf deinem Computer, in dem alle Dateien einer bestimmten Minecraft-Konfiguration gespeichert sind. Launcher wie CurseForge und Modrinth nennen diese „Instanzen“ oder „Profile“ (nicht zu verwechseln mit den Profilen von FancyMenu).

### Wenn du die CurseForge-App verwendest

1. Öffne CurseForge.
2. Suche dein Minecraft-Profil/deine Instanz in der Liste und öffne es.
3. Klicke auf die drei Punkte.
4. Wähle „Ordner öffnen“. Dadurch wird der Hauptordner dieser Minecraft-Instanz geöffnet.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Wenn du die Modrinth-App verwendest

1. Öffne die Modrinth-App.
2. Suche dein Minecraft-Profil/deine Instanz in der Liste und öffne es.
3. Klicke auf die drei Punkte.
4. Wähle „Ordner öffnen“. Dadurch wird der Hauptordner dieser Minecraft-Instanz geöffnet.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Bei anderen Launchern

Suche nach einer ähnlichen Option wie „Ordner öffnen“, „Instanzordner öffnen“ oder „Dateien anzeigen“ für deine jeweilige Minecraft-Konfiguration.

# Menüleiste und Tastenkürzel deaktivieren

Du möchtest die Menüleiste von FancyMenu in deinem Modpack sicher nicht sichtbar lassen, also solltest du sie deaktivieren. Da Spieler sie aber weiterhin über das Tastenkürzel wieder einblenden könnten, gehen wir etwas *radikaler* vor.

Navigiere zu `<game-directory>/config/fancymenu/options.txt` und öffne die Datei in einem Texteditor.

Setze nun `modpack_mode` auf `true` und speichere die Datei.
Dadurch werden alle Overlays und Tastenkürzel vollständig deaktiviert.

Um deine Layouts wieder bearbeiten zu können, setze die Konfigurationsoption zurück auf `false`.

# Willkommensbildschirm deaktivieren

In den meisten Fällen ist das nicht nötig. Wenn du den Willkommensbildschirm (der dich zum Lesen der Dokumentation auffordert) aber noch nicht geschlossen hast, setze `show_welcome_screen` in `<game-directory>/config/fancymenu/options.txt` auf `false`.

Der Bildschirm wird nur einmal angezeigt und deaktiviert sich, sobald du auf die Schaltfläche **Dokumentation öffnen** klickst. Daher sollte es in den meisten Fällen nicht nötig sein, dies manuell zu erledigen.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
