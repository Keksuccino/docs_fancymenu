---
title: Profile
description: >-
  So speicherst, wechselst und teilst du vollständige FancyMenu-Setups mit
  Profilen.
sourceBlobSha: d0a07901ee271d802c7bc07ea6d787575f48d51c
---
# Profile

Ein Profil ist ein vollständiges FancyMenu-Setup: Es enthält alle Layouts, Assets, Variablen und FancyMenu-Einstellungen einer Instanz. Mit Profilen kannst du mehrere Setups in einer Minecraft-Instanz verwalten, innerhalb von Sekunden zwischen ihnen wechseln und sie als einzelne Datei mit anderen teilen.

<img width="800" alt="profiles" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Das Profilfenster öffnen

Öffne das Profilfenster über **menu bar -> Customization -> Profiles**.

Die Liste auf der linken Seite zeigt alle deine Profile, während die rechte Seite die Details des ausgewählten Profils anzeigt. Das geladene Profil ist als **Active** gekennzeichnet. Jede Änderung, die du in FancyMenu vornimmst, wird direkt im geladenen Profil gespeichert.

Dein bestehendes Setup wird automatisch zu deinem ersten Profil mit dem Namen **My Profile**.

> [!TIP]
> Klicke mit der rechten Maustaste auf ein Profil in der Liste, um alle verfügbaren Aktionen dafür anzuzeigen.

# Profile wechseln

Wähle ein Profil aus und klicke auf **Load Profile** oder doppelklicke darauf. FancyMenu wird anschließend mit dem ausgewählten Setup neu geladen.

> [!NOTE]
> Beim Wechseln wird niemals etwas gelöscht. Dein aktuelles Setup wird als eigenes Profil gespeichert, bevor das andere geladen wird. So kannst du jederzeit zurückwechseln.

# Profile erstellen

- **New Profile** (die **+**-Schaltfläche unter der Liste) erstellt ein leeres Profil und öffnet dessen Editor. Leere Profile behalten deine persönlichen FancyMenu-Einstellungen wie die UI-Skalierung und das Design.
- **Duplicate** erstellt eine Kopie des ausgewählten Profils. Das ist praktisch, wenn du etwas ausprobieren möchtest, ohne das Original zu verändern.

# Profile bearbeiten

Klicke auf **Edit**, um den Titel, die Version, die Autoren, die Beschreibung, das Symbol, den Issue-Tracker und die Links eines Profils zu ändern. Die Beschreibung unterstützt Markdown, und als Symbol kann jedes PNG-Bild verwendet werden.

Nichts wird gespeichert, bis du auf **Done** klickst.

# Profile teilen

> [!CAUTION]
> Profile können Aktionen ausführen. Importiere sie nur aus Quellen, denen du vertraust.

## Exportieren

Wähle ein Profil aus, klicke auf **Export** und wähle den Speicherort aus. Dadurch wird eine `.fmp`-Datei erstellt, die das vollständige Profil enthält.

## Importieren

Klicke unter der Liste auf **Import** und wähle eine `.fmp`-Datei aus oder ziehe die Datei einfach per Drag-and-drop auf das Profilfenster.

- Importierte Profile werden nicht automatisch geladen. Lade sie wie jedes andere Profil.
- Wenn du bereits dasselbe Profil besitzt (zum Beispiel eine ältere Version davon), kannst du auswählen, ob du es **Replace** oder **Keep Both** möchtest. Wenn du das geladene Profil ersetzt, wird die importierte Version sofort geladen.
- Profile, die mit einer neueren FancyMenu-Version erstellt wurden, zeigen eine Warnung an, da einige Bestandteile möglicherweise nicht funktionieren.

## Setup-Ordner hinzufügen

Manche Setups werden anstelle einer `.fmp`-Datei als einfacher `fancymenu`-Ordner bereitgestellt. Um einen solchen Ordner als Profil hinzuzufügen, benenne ihn in den gewünschten Profilnamen um, verschiebe ihn nach `<game-directory>/config/fancymenu/profiles/` (erstelle den Ordner `profiles`, falls er noch nicht existiert) und öffne das Profilfenster. FancyMenu fügt ihn automatisch zu deinen Profilen hinzu.

# Profile löschen

Wähle ein Profil aus und klicke auf **Delete**. Das Löschen kann nicht rückgängig gemacht werden. Exportiere das Profil daher vorher, wenn du eine Sicherungskopie behalten möchtest.

Das geladene Profil kann nicht gelöscht werden. Lade zuerst ein anderes Profil.

# Speicherort der Profile

- Das geladene Profil befindet sich wie jedes FancyMenu-Setup in `<game-directory>/config/fancymenu/`.
- Alle anderen Profile werden in `<game-directory>/config/fancymenu/profiles/` gespeichert. Klicke auf **Open Folder**, um den Ordner eines Profils zu öffnen.

`<game-directory>` ist der Ordner der aktiven Instanz und kann sich von `.minecraft` unterscheiden. Laufzeitdaten, die FancyMenu außerhalb von `config/fancymenu/` speichert, gehören nicht zu den Profilen. Siehe [Speicherorte von Daten](./data-storage-locations#persistent-runtime-state).
