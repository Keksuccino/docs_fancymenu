---
title: Diashows
description: >-
  Zeige deine eigenen Bilder nacheinander mit sanften Überblendungen als
  Menü-Hintergrund oder in einem Bildschirmbereich an.
sourceBlobSha: 24ba0cbe9184108453b9829b8e6cd48d49a48b12
---

# Diashows

Eine Diashow zeigt Bilder nacheinander an und blendet sanft von einem zum nächsten über – zum Beispiel Screenshots aus der Welt deines Modpacks.

Du kannst sie als [Menü-Hintergrund](/menu-backgrounds) eines Layouts oder mit einem [Diashow-Element](/elements#slideshow) in einem Bildschirmbereich anzeigen.

<img width="800" alt="Der Titelbildschirm mit einer Diashow als Hintergrund, die von einem Flusstal über einen Kirschhain zu einer Küste überblendet – Screenshots aus einer Minecraft-Welt" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_title.gif?raw=true">

# Eine Diashow erstellen

1. Öffne im Spielverzeichnis den Ordner `slideshows` unter `config/fancymenu/`. Über **Menüleiste -> Tools -> FancyMenu-Verzeichnis öffnen** gelangst du zu `config/fancymenu/`.
2. Erstelle darin einen Ordner für deine Diashow, zum Beispiel `world_tour`. Der Name spielt keine Rolle.
3. Lege darin eine [`properties.txt`](#propertiestxt) und einen Ordner namens `images` mit [deinen Bildern](#die-bilder) ab. Eine [`overlay.png`](#overlay) ist optional.
4. Lade FancyMenu über **Menüleiste -> Anpassung -> FancyMenu neu laden** oder mit `Ctrl + Alt + R` (unter macOS `Cmd + Alt + R`) neu, oder starte das Spiel neu.

```text
config/fancymenu/slideshows/
└── world_tour/
    ├── properties.txt
    ├── overlay.png
    └── images/
        ├── 01_river_valley.png
        ├── 02_cherry_grove.png
        └── 03_coast.png
```

# Die Bilder

- Es zählen nur PNG- und JPG-Dateien, deren Namen auf `.png` oder `.jpg` enden. Benenne `.jpeg`-Dateien in `.jpg` um.
- Die Bilder werden nach Dateinamen von A bis Z angezeigt. Zahlen werden wie Buchstaben sortiert, daher kommt `10.png` vor `2.png`. Beginne die Nummerierung mit Nullen, zum Beispiel `01`, `02` … `10`.
- Verwende für alle Bilder dieselbe Größe. Das erste Bild bestimmt das Seitenverhältnis der Diashow; die übrigen Bilder werden daran angepasst.
- Dateien in Unterordnern von `images` werden nicht berücksichtigt.

# properties.txt

```text
type = slideshow

slideshow-meta {
  name = world_tour
  duration = 5.0
  fadespeed = 5.0
  randomize = false
}
```

| Einstellung | Funktion |
|---|---|
| `name` | Der Name, unter dem du die Diashow auswählst. Jede Diashow braucht einen eigenen Namen. |
| `duration` | Sekunden zwischen den Bildwechseln, einschließlich der Überblendung. Dauert eine Überblendung länger, verzögert sich der nächste Wechsel, bis sie abgeschlossen ist. |
| `fadespeed` | Legt fest, wie schnell ein Bild ins nächste überblendet wird. Bei `1.0` dauert eine Überblendung etwa 6 Sekunden, bei `3.0` etwa 2 Sekunden. Der Wert muss größer als `0` sein. |
| `randomize` | Bei `true` werden die Bilder in zufälliger Reihenfolge angezeigt, ohne dass zweimal hintereinander dasselbe Bild erscheint. Bei `false` werden sie nach ihren Dateinamen sortiert angezeigt. |

Nur `name` ist erforderlich. Für nicht angegebene Einstellungen gelten die Standardwerte `duration = 10.0`, `fadespeed = 1.0` und `randomize = false`. Lass die Zeilen `type = slideshow` und `slideshow-meta {` unverändert, schreibe pro Zeile eine Einstellung und verwende für Dezimalzahlen einen Punkt, zum Beispiel `2.5`.

Diashows aus älteren Versionen können die Zeilen `width`, `height`, `x` und `y` enthalten. Sie haben keine Funktion: Der Hintergrund oder das Element bestimmt, wo und in welcher Größe die Diashow angezeigt wird.

# Overlay

Eine `overlay.png` neben der `properties.txt` wird über jedes Bild gelegt und auf die Größe der Diashow gestreckt. Sie wird nicht mit den Bildern überblendet und eignet sich daher für Rahmen, Vignetten oder ein Logo in einer Ecke. Durch transparente Bereiche scheinen die Bilder hindurch.

Das Overlay gehört zur Diashow und wird überall angezeigt, wo die Diashow zu sehen ist. Wenn du dieselben Bilder mit und ohne Rahmen verwenden möchtest, erstelle zwei Diashows.

# Eine Diashow verwenden

## Als Menü-Hintergrund

<img width="800" alt="Menü-Hintergründe öffnen, im Layout-Editor Diashow auswählen, Hintergrund anzeigen aktivieren und unter Diashow auswählen world_tour auswählen. Die Vorschau blendet zum nächsten Bild über; anschließend ist die Diashow hinter den Schaltflächen des Titelbildschirms zu sehen." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_background.gif?raw=true">

1. Klicke im [Layout-Editor](/layout-editor) mit der rechten Maustaste auf den Hintergrund und öffne **Menü-Hintergründe -> Diashow**.
2. Klicke auf **Hintergrund anzeigen**, um die Funktion einzuschalten.
3. Klicke auf **Diashow-Name**, wähle deine Diashow aus und klicke auf **Fertig**. Rechts siehst du eine Vorschau der laufenden Diashow.

Mit **Diashow entfernen** kannst du sie wieder entfernen. Wie du sie mit anderen Hintergründen kombinierst, erfährst du unter [Menü-Hintergründe](/menu-backgrounds).

Die Diashow wird auf den gesamten Bildschirm gestreckt. Wenn das Seitenverhältnis der Bilder erhalten bleiben soll, aktiviere unter **Menü-Hintergründe** die Option **Seitenverhältnis des Hintergrunds beibehalten**. Das Bild füllt dann den Bildschirm aus und wird an den Seiten oder oben und unten abgeschnitten.

## Als Element

<img width="800" alt="Der Titelbildschirm mit Schaltflächen auf der linken Seite und einem Diashow-Element auf der rechten Seite, das zwischen Screenshots einer Minecraft-Welt überblendet" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_element.gif?raw=true">

1. Klicke im Layout-Editor mit der rechten Maustaste auf eine freie Stelle und füge über **Neues Element** eine Diashow hinzu.
2. Klicke mit der rechten Maustaste auf das Element, klicke auf **Diashow** und wähle deine Diashow aus. Das Element übernimmt das Seitenverhältnis der Bilder.
3. Verschiebe und ändere die Größe wie bei jedem anderen Element. Mit **Seitenverhältnis wiederherstellen** wird die Breite an die Höhe angepasst, damit die Bilder nicht verzerrt werden.

## Vorladen

Eine Diashow lädt jedes Bild, wenn es zum ersten Mal angezeigt wird. Bei großen Bildern kann es daher beim ersten Mal zu einer kurzen Verzögerung kommen. Um alle Bilder und das Overlay beim Spielstart zu laden, füge die Diashow über **Diashow hinzufügen** unter **Menüleiste -> Anpassung -> Ressourcen vorladen** hinzu. Weitere Informationen findest du unter [Ressourcen vorladen](/preload-layouts#pre-loading-slideshows--panoramas).

# Gut zu wissen

- Überall, wo dieselbe Diashow angezeigt wird, ist zur gleichen Zeit dasselbe Bild zu sehen – auch in verschiedenen Menüs.
- Eine Diashow läuft nur, solange sie angezeigt wird. Wird sie nach einer Pause von mehr als `duration` wieder eingeblendet, wechselt sie sofort mit einer Überblendung zum nächsten Bild.
- Wenn du FancyMenu neu lädst, beginnen alle Diashows von vorn. Das erste Bild nach dem Start wird nur halb so lange angezeigt wie die übrigen.
- Diashows gehören zum geladenen [Profil](/profiles).
- Wenn eine Diashow unter **Diashow auswählen** fehlt, wurde sie nicht geladen. Im Spielprotokoll `logs/latest.log` steht der Grund, zum Beispiel ein fehlender `name`, eine fehlende `properties.txt` oder ein fehlender `images`-Ordner.
- Aktiviere unter Windows im Datei-Explorer die Dateinamenerweiterungen, damit nicht versehentlich eine Datei namens `properties.txt.txt` entsteht.
- Ein lila-schwarzes Schachbrettmuster bedeutet, dass keine Diashow ausgewählt ist oder das Layout einen Diashow-Namen verwendet, der nicht mehr existiert.
- Haben zwei Diashows denselben `name`, wird nur eine davon angezeigt.
- Das **Debug-Overlay** (`Ctrl + Alt + D`) zeigt an, wie viele Diashows und Bilder FancyMenu geladen hat.
