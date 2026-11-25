---
title: Profile
description: >-
  Speichere, wechsle und teile komplette FancyMenu-Konfigurationen mit Profilen
  und installiere Layoutvorlagen aus der Community.
sourceBlobSha: 52348efde29798073477e572b59a7630f96013ad
---

# Profile

Ein Profil ist eine vollständige FancyMenu-Konfiguration: Layouts, Ressourcen, Variablen, Einstellungen und alles andere in `config/fancymenu/` (siehe [Speicherorte der Daten](/data-storage-locations#your-setup)). Mit Profilen kannst du mehrere Konfigurationen in einer Minecraft-Instanz speichern, in Sekundenschnelle zwischen ihnen wechseln und sie als einzelne Datei teilen.

<img width="800" alt="Das Profil My Menu Pack erstellen, das Profil Wind Chimes importieren, indem dessen .fmp-Datei auf das Profile-Fenster gezogen wird, My Menu Pack löschen und Wind Chimes laden, wodurch sich der Titelbildschirm ändert" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Das Profile-Fenster

Öffne es über **Menüleiste -> Anpassung -> Profile**.

- Die Liste links zeigt alle Profile. Das geladene Profil steht ganz oben und ist mit **Aktiv** markiert. Alle Änderungen, die du in FancyMenu vornimmst, werden direkt darin gespeichert.
- Rechts wird das ausgewählte Profil angezeigt: sein Symbol, Titel, Version, Autoren, Anzahl der Layouts, Größe, Links und Beschreibung.
- Wenn du mit der Maus über die Schaltflächen unter der Liste und den Details fährst, wird ihr Name angezeigt. Mit einem Rechtsklick auf ein Profil werden ebenfalls die zugehörigen Aktionen angezeigt.

Deine Konfiguration wird automatisch zu deinem ersten Profil und heißt **My Profile**.

# Ein Profil laden

Wähle ein Profil aus und klicke auf **Profil laden**, doppelklicke darauf oder drücke `Enter`.

FancyMenu wird dann mit dem Profil neu geladen – wie nach dem Start des Spiels. Alle anderen FancyMenu-Fenster werden geschlossen. Außerhalb einer Welt wird der Titelbildschirm geöffnet.

> [!NOTE]
> Beim Laden wird nichts gelöscht. Deine aktuelle Konfiguration wird zuerst als eigenes Profil gespeichert, sodass du jederzeit zurückwechseln kannst.

# Profile erstellen

- **Neues Profil** (die Schaltfläche `+` unter der Liste) erstellt ein leeres Profil und öffnet sofort dessen Details, damit du ihm einen Namen geben kannst. Deine FancyMenu-Einstellungen, etwa die UI-Skalierung und das Design, bleiben erhalten, aber es enthält keine Layouts oder sonstigen Anpassungen. Es wird nicht automatisch geladen.
- **Duplizieren** kopiert das ausgewählte Profil. So kannst du bequem etwas ausprobieren, ohne das Original anzutasten.

# Profildetails bearbeiten

Wähle ein Profil aus und klicke auf **Bearbeiten**, um dessen Details zu ändern:

- **Titel** – das Einzige, was ein Profil unbedingt benötigt.
- **Version** und **Autoren**. Trenne mehrere Autoren durch Kommas.
- **Beschreibung** mit [Markdown](/text-formatting#markdown), zum Beispiel für Fettdruck, Überschriften und Listen.
- **Problemtracker** – eine Website, auf der andere Probleme mit dem Profil melden können. Sie wird als **Problem melden** angezeigt.
- **Links** zu deinem Discord-Server, YouTube-Kanal, deiner Website und mehr. Klicke auf **Link hinzufügen** und füge den Link ein: FancyMenu erkennt die Plattform automatisch.
- Ein Symbol: Über **Symbol auswählen** kannst du ein PNG-Bild auswählen, mit **Symbol entfernen** wird es entfernt. Nicht quadratische Bilder werden mittig zugeschnitten.

Änderungen werden erst gespeichert, wenn du auf **Fertig** klickst.

# Profile teilen

> [!CAUTION]
> Profile können Aktionen ausführen, zum Beispiel Links öffnen oder Befehle ausführen. Importiere sie nur aus Quellen, denen du vertraust.

## Exportieren

Wähle ein Profil aus, klicke auf **Exportieren** und wähle aus, wo du es speichern möchtest. Dadurch wird eine `.fmp`-Datei erstellt, die das gesamte Profil enthält und sofort geteilt werden kann.

## Importieren

Klicke unter der Liste auf **Importieren** und wähle eine `.fmp`-Datei aus, oder ziehe die Datei auf das Profile-Fenster.

- Importierte Profile werden nicht automatisch geladen. Lade sie wie jedes andere Profil.
- Wenn du das Profil bereits hast, zum Beispiel eine ältere Version davon, wähle **Ersetzen** oder **Beide behalten**. Wenn du das geladene Profil ersetzt, wird das importierte Profil sofort geladen und deine Änderungen am alten Profil gehen verloren.
- Bei Profilen, die mit einer neueren FancyMenu-Version erstellt wurden, wird zunächst eine Warnung angezeigt, da einige Bestandteile möglicherweise nicht funktionieren.
- Es funktionieren nur `.fmp`-Dateien, die mit FancyMenu exportiert wurden. Informationen zu einfachen Ordnern findest du im nächsten Abschnitt.

## Setup-Ordner hinzufügen

Manche Konfigurationen werden als einfacher `fancymenu`-Ordner (eine Kopie des Ordners `config/fancymenu/` einer anderen Person) statt als `.fmp`-Datei bereitgestellt. So fügst du einen solchen Ordner als Profil hinzu:

1. Entpacke ihn, falls er als `.zip`-Datei vorliegt.
2. Verschiebe den Ordner nach `<game-directory>/config/fancymenu/profiles/`. Erstelle den Ordner `profiles`, falls er noch nicht vorhanden ist.
3. Öffne das Profile-Fenster oder schließe es und öffne es erneut. FancyMenu fügt den Ordner zu deinen Profilen hinzu.

Der Ordner muss die Dateien direkt enthalten, zum Beispiel `customization/` und `options.txt`, und nicht noch einen weiteren `fancymenu`-Ordner. Das Profil erhält den Namen des Ordners als Titel, sofern der Ordner keine eigenen Profildetails enthält. Ändere den Titel über **Bearbeiten**.

## Layoutvorlagen

Im Kanal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) des [Kekscord-Discord-Servers](https://discord.gg/rhayah27GC) (Keksuccinos offiziellem Discord-Server für Mod-Support) findest du vollständige, von der Community erstellte Konfigurationen für FancyMenu und dessen Add-ons wie SpiffyHUD und Drippy Loading Screen. Jeder Beitrag enthält einen Download-Link zu einer `.fmp`-Datei oder einem `fancymenu`-Ordner.

Vorlagen sind komplex. Versuche daher nicht, sie mit deiner eigenen Konfiguration zusammenzuführen. Füge sie stattdessen als eigenes Profil hinzu:

1. [Importiere](#importieren) die `.fmp`-Datei oder [füge den Ordner hinzu](#setup-ordner-hinzufügen).
2. Wähle die Vorlage im Profile-Fenster aus und klicke auf **Profil laden**.

Deine eigene Konfiguration bleibt als eigenes Profil verfügbar, sodass du jederzeit zurückwechseln kannst.

Die meisten Vorlagen darfst du bearbeiten und in deinen eigenen Projekten, zum Beispiel Modpacks, verwenden. Das gilt jedoch nicht für alle. Prüfe immer im Beitrag zur Vorlage, was du damit tun darfst.

# Profile löschen

Wähle ein Profil aus und klicke auf **Löschen**, oder drücke `Delete` (auf macOS `Fn + Delete`). Das Löschen kann nicht rückgängig gemacht werden. Exportiere das Profil daher vorher, wenn du ein Backup haben möchtest.

Das geladene Profil kann nicht gelöscht werden. Lade zuerst ein anderes Profil.

# Speicherort der Profile

- Das geladene Profil entspricht dem Inhalt von `<game-directory>/config/fancymenu/`.
- Alle anderen Profile befinden sich jeweils in einem eigenen Ordner unter `<game-directory>/config/fancymenu/profiles/`. Mit **Ordner öffnen** wird der Ordner des ausgewählten Profils geöffnet.

`<game-directory>` ist der Ordner deiner Instanz, der sich von `.minecraft` unterscheiden kann. Die Daten unter `<game-directory>/fancymenu_data/` gehören nicht zu den Profilen. Siehe [Speicherorte der Daten](/data-storage-locations#instance-data).

# Wenn etwas schiefgeht

- **Einige Dateien werden noch verwendet:** Oft lädt das Spiel selbst noch etwas, zum Beispiel Audiodaten. Warte ein paar Sekunden und versuche es erneut. Tritt das Problem weiterhin auf, schließe Programme, die auf die Dateien zugreifen könnten, zum Beispiel dein Antivirenprogramm, einen Cloud-Synchronisierungsdienst oder ein Dateimanager-Fenster.
- **Der letzte Profilwechsel ist noch nicht abgeschlossen:** Es ist nichts verloren gegangen. Lade erneut ein Profil oder starte das Spiel neu, um den Wechsel abzuschließen.
- **Es ist nicht genügend Speicherplatz verfügbar:** Die Meldung gibt an, wie viel Speicherplatz das Profil benötigt. Schaffe etwas Platz und versuche es erneut.
- Profilaktionen werden nacheinander ausgeführt. Das Exportieren, Importieren und Duplizieren großer Profile kann einen Moment dauern. Währenddessen wird eine Schaltfläche **Abbrechen** angezeigt.
