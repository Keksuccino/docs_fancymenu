---
title: Diashows
description: Bild-Diashows erstellen und verwenden.
---

# Diashows

Jede Diashow hat ihr eigenes Verzeichnis unter:

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` ist die aktive Launcher-Instanz und kann sich vom herkömmlichen `.minecraft`-Verzeichnis unterscheiden.

# Verzeichnisstruktur

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # optional
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

Bilder müssen die Endung `.png` oder `.jpg` haben; andere Erweiterungen, einschließlich `.jpeg`, werden ignoriert.

Wenn `randomize = false`, werden Bilder in alphabetischer Dateinamenreihenfolge ohne Beachtung von Groß-/Kleinschreibung abgespielt. Verwende mit Nullen aufgefüllte Namen wie `image_01.png`, `image_02.png` und `image_10.png`.

# `properties.txt`

```text
type = slideshow

slideshow-meta {
  name = cool_slideshow
  width = 1920
  height = 1080
  x = 0
  y = 0
  duration = 5.0
  fadespeed = 12.0
  randomize = false
}
```

| Eigenschaft | Bedeutung |
|---|---|
| `name` | Erforderlich, Laufzeitkennung mit Beachtung von Groß-/Kleinschreibung; eindeutig halten |
| `width`, `height` | Basisgröße in GUI-skalierten Pixeln und das Quell-Seitenverhältnis |
| `x`, `y` | Basis-Position oben links; normale Elemente und Hintergründe verwenden ihre eigene Position, daher diese auf `0` belassen |
| `duration` | Mindestanzahl an Sekunden zwischen Übergangsbeginn; enthält die Überblendzeit und muss über `0` liegen |
| `fadespeed` | Multiplikator für die Überblendgeschwindigkeit; `1.0` ist der Standard, höhere Werte blenden schneller aus, und der Wert muss über `0` liegen |
| `randomize` | `true` für zufällige Auswahl oder `false` für Dateinamensreihenfolge |

Nur `name` ist erforderlich. Standardwerte sind `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0` und `randomize = false`. Lass `type = slideshow` und `slideshow-meta` unverändert; schreibe pro Zeile genau ein `key = value` und verwende einen Punkt für Dezimalzahlen.

Layouts wählen den Wert von `name`, nicht den Namen des Verzeichnisses. Doppelte Namen werden nicht abgewiesen, und die Scan-Reihenfolge der Verzeichnisse bestimmt, welche Diashow verfügbar bleibt. Halte die Namen innerhalb des slideshows-Verzeichnisses eindeutig.

Der Zufallsmodus wählt bei jedem Übergang unabhängig und vermeidet eine direkte Wiederholung, wenn mehrere Bilder verfügbar sind. Das Timing verwendet Echtzeit; ein Überblenden, das länger als `duration` dauert, verzögert den nächsten Übergang, und das Zurückkehren zu einer Diashow, nachdem sie ausgeblendet wurde, kann sie sofort weiterschalten.

# Eine Diashow verwenden

Lade FancyMenu über **Anpassen -> FancyMenu neu laden** neu oder starte den Client neu. Verwende das [**Diashow**-Element](./elements#slideshow) oder klicke im Hintergrund des Layout-Editors mit der rechten Maustaste und wähle [**Menühintergründe**](./menu-backgrounds) -> **Diashow**.
