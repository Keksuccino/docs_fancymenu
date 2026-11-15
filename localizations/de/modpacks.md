---
title: Modpacks
description: So bindest du Layouts in ein Modpack ein.
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# FancyMenu in Modpacks

Dein FancyMenu-Setup in ein Modpack einzubinden ist sehr einfach und erfordert nur wenige Schritte.

> [!CAUTION]
> FancyMenu-Setups können Aktionen ausführen. Importiere sie nur aus Quellen, denen du vertraust.

> [!WARNING]
> Diese Seite gilt **NUR** für FancyMenu-Setups, die vollständig in **FancyMenu v3+** erstellt wurden. Wenn du ein Legacy-Setup verwendest (in v2 erstellt und in v3 konvertiert), können einige Schritte abweichen.

# Dein Setup in das Modpack übernehmen

Am einfachsten verschiebst du dein Setup von der Instanz, in der du es erstellt hast, in die Instanz deines Modpacks, indem du ein [Profil](./profiles) verwendest:

1. Öffne in der Instanz mit deinem Setup **Menüleiste -> Anpassung -> Profile**, wähle dein Setup aus und [exportiere](./profiles#exporting) es als `.fmp`-Datei.
2. Öffne in deiner Modpack-Instanz das Profilfenster und [importiere](./profiles#importing) die `.fmp`-Datei, zum Beispiel indem du sie auf das Fenster ziehst.
3. Wähle das importierte Profil aus und klicke auf **Profil laden**.

Das FancyMenu-Setup, das zuvor in der Modpack-Instanz verwendet wurde, geht nicht verloren. Es bleibt als eigenes Profil verfügbar, sodass du jederzeit zurückwechseln kannst.

# Das Setup mit deinem Modpack ausliefern

Das geladene Profil entspricht dem Inhalt von `<game-directory>/config/fancymenu/`. Es wird daher zusammen mit dem `config`-Ordner deines Modpacks ausgeliefert, genau wie die Konfigurationsdateien anderer Mods.

Alle anderen Profile der Instanz werden in `<game-directory>/config/fancymenu/profiles/` gespeichert. Lösche die Profile, die Spieler nicht erhalten sollen, bevor du dein Modpack exportierst, oder lasse den Ordner `profiles` beim Export des Modpacks weg.

> [!CAUTION]
> Beachte, dass alte Legacy-Setups, die in FancyMenu v2 erstellt wurden (auch wenn sie in v3 konvertiert wurden), Layout-Assets außerhalb des Ordners `<game-directory>/config/fancymenu/assets/` von FancyMenu speichern konnten. Profile enthalten nur den Konfigurationsordner von FancyMenu. In diesem Fall musst du daher sicherstellen, dass du auch alle deine Assets in das Modpack aufnimmst.

## So findest du den Instanzordner

Der Instanzordner ist der Hauptordner auf deinem Computer, in dem alle Dateien einer bestimmten Minecraft-Konfiguration gespeichert sind. Launcher wie CurseForge und Modrinth bezeichnen diese als „Instanzen“ oder „Profile“ (nicht zu verwechseln mit den Profilen von FancyMenu).

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

Suche nach einer ähnlichen Option wie „Ordner öffnen“, „Instanzordner öffnen“ oder „Dateien anzeigen“ für deine jeweilige Minecraft-Konfiguration.

# Menüleiste und Tastenkürzel deaktivieren

Du möchtest die Menüleiste von FancyMenu in deinem Modpack sicherlich nicht dauerhaft sichtbar lassen, daher solltest du sie deaktivieren. Da sie jedoch weiterhin über das Tastenkürzel wieder eingeblendet werden kann, gehen wir einen etwas *aggressiveren* Schritt.

Navigiere zu `<game-directory>/config/fancymenu/options.txt` und öffne die Datei in einem Texteditor.

Setze nun `modpack_mode` auf `true` und speichere die Datei.
Dadurch werden alle Overlays und Tastenkürzel vollständig deaktiviert.

Um deine Layouts wieder bearbeiten zu können, setze diese Konfigurationsoption zurück auf `false`.

# Willkommensbildschirm deaktivieren

In den meisten Fällen ist dies nicht nötig. Wenn du den Willkommensbildschirm jedoch noch nicht geschlossen hast (den Bildschirm, der dich zum Lesen der Dokumentation auffordert), stelle sicher, dass `show_welcome_screen` in `<game-directory>/config/fancymenu/options.txt` auf `false` gesetzt ist.

Der Bildschirm wird nur einmal angezeigt und deaktiviert sich selbst, sobald du auf die Schaltfläche **Dokumentation öffnen** klickst. Daher sollte es in den meisten Fällen nicht nötig sein, dies manuell zu erledigen.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
