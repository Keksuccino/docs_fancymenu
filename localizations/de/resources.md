---
title: Ressourcen
description: >-
  Wie Ressourcen in FancyMenu funktionieren. Behandelt Ressourcenspeicherorte,
  lokale Ressourcen und Web-Ressourcen.
---

# Ressourcen

Ressourcenfelder können Inhalte aus folgenden Quellen laden:

- **Minecraft:** ein von Minecraft oder einem Ressourcenpaket bereitgestellter Ressourcenpfad.
- **Lokal:** eine Datei in der aktiven Spielinstanz.
- **Web:** eine direkte Datei-URL.

Die meisten Bild-, Audio-, Video- und Textfelder verwenden denselben Ressourcenauswahldialog. Der Auswahldialog enthält einen Browser für Minecraft- und Ressourcenpaket-Inhalte.

# Minecraft-Ressourcen (Ressourcenpakete)

Ressourcenpfade verwenden `namespace:path`. Der Namespace ist das Verzeichnis direkt unter `assets`, und der Pfad umfasst alles unterhalb dieses Namespace.

Betrachten Sie zum Beispiel ein Bild in einem Ressourcenpaket, das unter `/assets/custom_resources/images/image.png` gespeichert ist.
Sein Ressourcenpfad ist `custom_resources:images/image.png`.

> [!NOTE]
> Die integrierten Ressourcen von Minecraft verwenden normalerweise den Namespace `minecraft`.

# Lokale Ressourcen

Speichern Sie lokale Ressourcen in `<game-directory>/config/fancymenu/assets/`. `<game-directory>` ist der Ordner der aktiven Instanz, der sich von `.minecraft` unterscheiden kann.

Ressourcenfelder können denselben Pfad als `/config/fancymenu/assets/example.png` anzeigen. In diesen Feldern bedeutet der führende `/` weiterhin `<game-directory>`; es ist kein Pfad zum Stammverzeichnis des Dateisystems.

Diese Dateien können über ihren Config-Ordner mit einem [Modpack mitgeliefert](./modpacks) werden.

Eine vollständige Übersicht über die Pfade von FancyMenu für Layout, Ressourcen, Konfiguration und generierten Status finden Sie unter [Datenspeicherorte](./data-storage-locations).

# Web-Ressourcen

Verwenden Sie eine direkte URL zur Datei, z. B. `https://example-domain.net/image.png`. Seiten und Weiterleitungslinks sind langsamer und fehleranfälliger als direkte URLs, die auf den Dateinamen und die Dateiendung der Ressource enden.

# Platzhalter in Ressourcenquellen

Ressourcenfelder mit Auswahldialog können [Platzhalter](./placeholders) in lokalen Pfaden, URLs und Minecraft-Ressourcenpfaden verwenden. Wählen Sie neben dem Quellenfeld **Im Editor öffnen**, um es direkt zu bearbeiten.

> [!WARNING]
> Ressourceneingaben, die nicht den normalen Auswahldialog verwenden, unterstützen möglicherweise keine Platzhalter oder Live-Quellenaktualisierungen.
