---
title: Panoramen
description: >-
  Erstelle eigene, sich drehende Panorama-Hintergründe aus sechs Bildern – wie
  auf dem Titelbildschirm von Minecraft.
sourceBlobSha: e1f9ab155301f1b88df58dd8414eeee5714cfba6
---

# Panoramen

Ein Panorama ist ein Hintergrund, der sich langsam um dich dreht – wie auf dem Titelbildschirm von Minecraft. Es besteht aus sechs Bildern, die einen Würfel um die betrachtende Person bilden.

Du kannst eigene Panoramen als [Menühintergrund](/menu-backgrounds) eines Layouts anzeigen oder sie in allen Menüs anstelle des Minecraft-Panoramas verwenden.

<img width="800" alt="Der Titelbildschirm vor einem langsam rotierenden Panorama einer Blockhütte auf einer Waldlichtung bei Sonnenuntergang, mit Garten, Holzschuppen und Hühnerstall" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_title.gif?raw=true">

> [!TIP]
> Das Panorama auf dieser Seite kannst du kostenlos verwenden – zum Testen und in deinen eigenen Modpacks: [forest_homestead.zip](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/forest_homestead.zip) (4 MB). Entpacke es nach `config/fancymenu/panoramas/` und lade FancyMenu neu.

# Ein Panorama erstellen

1. Öffne im Spielverzeichnis den Ordner `panoramas` unter `config/fancymenu/`. Über **Menüleiste -> Tools -> Open FancyMenu Directory** kannst du `config/fancymenu/` öffnen.
2. Erstelle darin einen Ordner für dein Panorama, zum Beispiel `forest_homestead`. Der Name ist beliebig.
3. Lege eine `properties.txt` und einen Ordner namens `panorama` mit den [sechs Bildern](#die-sechs-bilder) darin ab. Eine `overlay.png` ist optional.
4. Lade FancyMenu über **Menüleiste -> Customization -> Reload FancyMenu** oder mit `Ctrl + Alt + R` (unter macOS `Cmd + Alt + R`) neu – oder starte das Spiel neu.

```text
config/fancymenu/panoramas/
└── forest_homestead/
    ├── properties.txt
    ├── overlay.png
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

# Die sechs Bilder

Jedes Bild bildet eine Seite des Würfels:

<img width="796" alt="Die sechs Bilder des Panoramas forest_homestead als aufgeklappter Würfel angeordnet: Das obere Bild über dem vorderen Bild, links, vorne, rechts und hinten in einer Reihe und das untere Bild unter dem vorderen Bild" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_cube.png?raw=true">

| Bild | Seite |
|---|---|
| `panorama_0.png` | Vorne |
| `panorama_1.png` | Rechts |
| `panorama_2.png` | Hinten |
| `panorama_3.png` | Links |
| `panorama_4.png` | Oben |
| `panorama_5.png` | Unten |

- Die vier Seiten umgeben dich in dieser Reihenfolge: Der rechte Rand jedes Bildes geht in den linken Rand des nächsten über. Der rechte Rand von `panorama_3.png` trifft auf den linken Rand von `panorama_0.png`.
- Der untere Rand des oberen Bildes berührt den oberen Rand des vorderen Bildes. Der obere Rand des unteren Bildes berührt den unteren Rand des vorderen Bildes.
- Alle sechs Bilder müssen PNG-Dateien mit denselben Abmessungen sein. Verwende quadratische Bilder, zum Beispiel mit 1024 × 1024 Pixeln.
- FancyMenu glättet die Bilder nicht, damit Pixelgrafiken scharf bleiben.

Minecraft verwendet dasselbe Layout für sein Panorama. Daher funktionieren auch für Minecraft erstellte Panoramen.

# properties.txt

```text
type = panorama

panorama-meta {
  name = forest_homestead
  speed = 2.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Einstellung | Funktion |
|---|---|
| `name` | Der Name, unter dem du das Panorama auswählst. Gib jedem Panorama einen eigenen Namen. |
| `speed` | Die Drehgeschwindigkeit. Bei `1.0` dreht es sich in etwa 4 Minuten einmal vollständig, bei `2.0` doppelt so schnell. Bei `0` bleibt es stehen. Werte über `10.0` erhöhen die Geschwindigkeit nicht weiter. |
| `fov` | Wie viel vom Panorama auf dem Bildschirm zu sehen ist, angegeben in Grad von der Ober- bis zur Unterkante des Bildschirms. Kleinere Werte vergrößern die Ansicht. |
| `angle` | Wie weit die Ansicht nach unten gerichtet ist, in Grad. Bei `0` blickst du gerade auf den Horizont, bei negativen Werten nach oben. |
| `start_rotation` | Die Startposition der Drehung, in Grad von `0` bis `360`. Bei `0` befindet sich das vordere Bild in der Mitte. |

Nur `name` ist erforderlich. Für nicht angegebene Einstellungen gelten `speed = 1.0`, `fov = 85.0`, `angle = 25.0` und `start_rotation = 0`. Lass die Zeilen `type = panorama` und `panorama-meta {` unverändert, schreibe pro Zeile eine Einstellung und verwende für Dezimalzahlen einen Punkt, zum Beispiel `1.5`.

# Overlay

Eine `overlay.png` neben der `properties.txt` wird über das Panorama gelegt und auf die gesamte Bildschirmfläche gestreckt. Sie dreht sich nicht mit dem Panorama und eignet sich daher zum Beispiel für eine Vignette, einen Rahmen oder eine Farbtönung. Durch transparente Bereiche ist das Panorama darunter sichtbar.

# Ein Panorama verwenden

## Als Menühintergrund

<img width="800" alt="Menüpunkt Menu Backgrounds öffnen, im Layout-Editor Cubic Panorama auswählen, Show Background einschalten und unter Choose Panorama forest_homestead auswählen; anschließend dreht es sich hinter den Schaltflächen des Titelbildschirms" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_background.gif?raw=true">

1. Klicke im [Layout-Editor](/layout-editor) mit der rechten Maustaste auf den Hintergrund und öffne **Menu Backgrounds -> Cubic Panorama**.
2. Klicke auf **Show Background**, um den Hintergrund einzuschalten.
3. Klicke auf **Panorama Name**, wähle dein Panorama aus und klicke auf **Done**. In der Vorschau rechts siehst du, wie es sich dreht.

Mit **Clear Panorama** entfernst du es wieder. Informationen dazu, wie du es mit anderen Hintergründen kombinierst, findest du unter [Menühintergründe](/menu-backgrounds).

## In allen Menüs

Über **Menüleiste -> Customization -> Global Customizations -> Custom Menu Background Panorama -> Choose Panorama** kannst du auf dem Titelbildschirm und in allen Menüs vor dem Betreten einer Welt dein Panorama anstelle des Minecraft-Panoramas anzeigen. Siehe [Globale Anpassungen](/global-customizations#menu-backgrounds).

## Vorabladen

Ein großes Panorama kann beim ersten Anzeigen einen Moment brauchen. Damit es während des Spielstarts geladen wird, füge es über **Add Cubic Panorama** unter **Menüleiste -> Customization -> Pre-Load Resources** hinzu. Siehe [Ressourcen vorladen](/preload-layouts#pre-loading-slideshows--panoramas).

# Wissenswertes

- Panoramen drehen sich nach rechts: Das vordere Bild bewegt sich nach links und das rechte Bild kommt ins Blickfeld.
- Alle Menüs, die dasselbe Panorama anzeigen, teilen sich dessen Drehung. Dadurch dreht es sich beim Wechsel zwischen den Menüs nahtlos weiter. Wenn es in keinem Menü angezeigt wird, hält es an.
- Wenn du FancyMenu neu lädst, beginnt jedes Panorama erneut bei seiner `start_rotation`.
- Panoramen gehören zum geladenen [Profil](/profiles).
- Wenn ein Panorama nicht unter **Choose Panorama** angezeigt wird, wurde es nicht geladen. Im Spielprotokoll `logs/latest.log` steht der Grund, zum Beispiel ein fehlender `name` oder ein fehlendes Bild.
- Ein violett-schwarzes Schachbrett bedeutet, dass noch kein Panorama ausgewählt wurde, die sechs Bilder unterschiedliche Abmessungen haben oder das Layout einen nicht mehr vorhandenen Panoramanamen verwendet.
- Wenn zwei Panoramen denselben `name` haben, wird nur eines davon angezeigt.
