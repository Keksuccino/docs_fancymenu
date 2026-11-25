---
title: Ressourcen
description: >-
  So funktionieren Ressourcen in FancyMenu. Behandelt Ressourcenpfade, lokale
  Ressourcen und Webressourcen.
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# Ressourcen

Ressourcenfelder können Inhalte aus folgenden Quellen laden:

- **Minecraft:** ein von Minecraft oder einem Ressourcenpaket bereitgestellter Ressourcenpfad.
- **Lokal:** eine Datei in der aktiven Spielinstanz.
- **Web:** eine direkte Datei-URL.

Die meisten Bild-, Audio-, Video- und Textfelder verwenden dieselbe Ressourcenauswahl. Sie enthält einen Browser für Inhalte von Minecraft und Ressourcenpaketen.

# Minecraft-Ressourcen (Ressourcenpakete)

Ressourcenpfade verwenden das Format `namespace:path`. Der Namespace ist das Verzeichnis direkt unterhalb von `assets`, und der Pfad umfasst alles unterhalb dieses Namespace.

Nehmen wir zum Beispiel an, ein Bild eines Ressourcenpakets liegt unter `/assets/custom_resources/images/image.png`.
Sein Ressourcenpfad lautet `custom_resources:images/image.png`.

> [!NOTE]
> Die integrierten Ressourcen von Minecraft verwenden normalerweise den Namespace `minecraft`.

# Lokale Ressourcen

Speichere lokale Ressourcen unter `<game-directory>/config/fancymenu/assets/`. `<game-directory>` ist der Ordner der aktiven Spielinstanz und kann sich von `.minecraft` unterscheiden.

Ressourcenfelder zeigen möglicherweise denselben Pfad in der Form `/config/fancymenu/assets/example.png` an. In diesen Feldern steht der führende `/` weiterhin für `<game-directory>` und nicht für den Stammordner des Dateisystems.

Diese Dateien können über den Konfigurationsordner eines Modpacks [mitgeliefert werden](/modpacks).

Eine vollständige Übersicht über die Speicherorte von Layouts, Ressourcen, Konfigurationen und generierten Daten von FancyMenu findest du unter [Speicherorte von Daten](/data-storage-locations).

# Webressourcen

Verwende eine direkte URL zur Datei, zum Beispiel `https://example-domain.net/image.png`. Seiten und Weiterleitungslinks sind langsamer und können häufiger fehlschlagen als direkte URLs, die mit dem Dateinamen und der Dateiendung der Ressource enden.

# Platzhalter in Ressourcenquellen

Ressourcenfelder mit Ressourcenauswahl können [Platzhalter](/placeholders) in lokalen Pfaden, URLs und Minecraft-Ressourcenpfaden verwenden. Wähle neben dem Quellfeld **Im Editor öffnen**, um es direkt zu bearbeiten.

> [!WARNING]
> Ressourcenfelder, die nicht die normale Ressourcenauswahl verwenden, unterstützen möglicherweise weder Platzhalter noch Live-Aktualisierungen der Quelle.
