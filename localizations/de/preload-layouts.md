---
title: Ressourcen vorladen
description: >-
  Wie man Ressourcen vorlädt, damit sie sofort einsatzbereit sind, sobald das
  Spiel fertig geladen ist.
---

# Ressourcen vorladen

Das Vorladen bereitet ausgewählte Ressourcen vor, bevor ein Menü sie benötigt. Verwende es für Ressourcen, die sonst flackern, zuerst einen schwarzen Frame anzeigen oder zu spät starten.

# Ressourcen zum Vorlader hinzufügen

Öffne **Anpassung -> Ressourcen vorladen**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

Die Liste akzeptiert unterstützte Bild-, Animations-, Audio-, Video- und Textressourcen aus lokalen Dateien, Web-URLs oder Ressource-Paketen. Eine live geladene [Browser](./elements#browser)-Seite wird nicht vorab geladen.

Der Vorlader startet während des Spielstarts und bei Minecraft-Ressourcenaktualisierungen. Er wartet, bis jeder Eintrag fertig ist oder fehlschlägt, bevor er fortfährt, mit einem Limit von zwei Minuten pro Eintrag.

Geladene Ressourcen bleiben im Cache, bis FancyMenu Ressourcen während eines Reloads oder beim Beenden des Clients freigibt. **Anpassung -> FancyMenu neu laden** gibt den Cache frei, startet den Vorlader jedoch nicht erneut.

Das Vorladen erhöht die Ladezeit sowie die RAM-/VRAM-Nutzung. Füge nur Ressourcen hinzu, die sofort bereit sein müssen; entferne große Einträge, wenn dem Client der Speicher ausgeht.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Slideshows und Panoramen vorladen

Das Hinzufügen einer [Slideshow](./slideshows) lädt alle ihre Bilder und das optionale Overlay. Das Hinzufügen eines [Panoramas](./panoramas) lädt alle sechs Seiten und das optionale Overlay.

**Anpassung -> FancyMenu neu laden** führt den Vorlader nicht aus. Verwende ein Minecraft-Ressourcen-Reload oder starte das Spiel neu, nachdem du die Vorlade-Liste geändert hast.
