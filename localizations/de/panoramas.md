---
title: Panoramen
description: Erstelle und verwende kubische Panoramen aus sechs Bildern.
---

# Kubische Panoramen

Jedes Panorama hat sein eigenes Verzeichnis unter:

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` ist die aktive Launcher-Instanz und kann sich vom üblichen `.minecraft`-Verzeichnis unterscheiden.

# Verzeichnisstruktur

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # optional
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

Die sechs Flächenbilder müssen PNG-Dateien mit genau den oben gezeigten Namen sein, und alle sechs müssen identische Abmessungen haben. Die Groß-/Kleinschreibung von Dateinamen kann auf manchen Betriebssystemen eine Rolle spielen.

Füge optional neben `properties.txt` eine `overlay.png` für eine Vignette oder ein anderes Overlay über das gesamte Panorama hinzu.

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Eigenschaft | Bedeutung |
|---|---|
| `name` | Erforderliche, zur Laufzeit verwendete Kennung mit Berücksichtigung der Groß-/Kleinschreibung; halte sie eindeutig |
| `speed` | Multiplikator für die Rotationsgeschwindigkeit; `1.0` ist der Standard |
| `fov` | Sichtfeld in Grad |
| `angle` | Vertikaler Betrachtungswinkel in Grad |
| `start_rotation` | Anfangs-Horizontaldrehung in Grad |

Nur `name` ist erforderlich. Fehlende optionale Werte verwenden die im Beispiel gezeigten Standardwerte. Lasse `type = panorama` und `panorama-meta` unverändert; schreibe eine `key = value`-Zeile pro Zeile und verwende einen Punkt für Dezimalzahlen.

Doppelte Namen werden nicht abgelehnt, und die Scan-Reihenfolge des Verzeichnisses entscheidet, welches Panorama verfügbar bleibt. Halte die Namen innerhalb des Panoramen-Verzeichnisses eindeutig. Panorama- und Slideshow-Namen verwenden separate Listen.

# Ein Panorama verwenden

Lade FancyMenu über **Anpassung -> FancyMenu neu laden** neu oder starte den Client neu. Klicke dann mit der rechten Maustaste auf den Hintergrund des Layout-Editors und wähle [**Menühintergründe**](./menu-backgrounds) -> **Kubisches Panorama**.
