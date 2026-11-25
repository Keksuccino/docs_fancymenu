---
title: Ressourcen vorladen
description: >-
  So lädst du Ressourcen vor, damit sie bereitstehen, sobald das Spiel
  vollständig geladen ist.
sourceBlobSha: 8eca400e05987468c1fd0dc29faa5267083e38d0
---

# Ressourcen vorladen

Beim Vorladen werden ausgewählte Ressourcen vorbereitet, bevor ein Menü sie benötigt. Verwende diese Funktion für Ressourcen, die andernfalls flackern, im ersten Bild schwarz sind oder verzögert starten.

# Ressourcen zum Vorlader hinzufügen

Öffne **Anpassung -> Ressourcen vorladen**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

Die Liste unterstützt Bild-, Animations-, Audio-, Video- und Textressourcen aus lokalen Dateien, Web-URLs oder Ressourcenpaketen. Eine aktive [Browser](/elements#browser)-Seite wird nicht vorgeladen.

Der Vorlader wird beim Spielstart und beim Neuladen der Minecraft-Ressourcen gestartet. Er wartet bei jedem Eintrag, bis dieser fertig geladen wurde oder ein Fehler aufgetreten ist, bevor er fortfährt. Das Zeitlimit pro Eintrag beträgt zwei Minuten.

Geladene Ressourcen bleiben im Cache, bis FancyMenu sie beim Neuladen oder beim Herunterfahren des Clients freigibt. **Anpassung -> FancyMenu neu laden** gibt den Cache frei, startet den Vorlader aber nicht erneut.

Das Vorladen verlängert die Ladezeit und erhöht den RAM-/VRAM-Verbrauch. Füge nur Ressourcen hinzu, die sofort bereitstehen müssen. Entferne große Einträge, wenn dem Client der Speicher ausgeht.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Diashows und Panoramen vorladen

Beim Hinzufügen einer [Diashow](/slideshows) werden alle Bilder und das optionale Overlay geladen. Beim Hinzufügen eines [Panoramas](/panoramas) werden alle sechs Seiten und das optionale Overlay geladen.

**Anpassung -> FancyMenu neu laden** startet den Vorlader nicht. Lade nach Änderungen an der Vorladeliste die Minecraft-Ressourcen neu oder starte das Spiel neu.
