---
title: Animationen
description: So verwendest und erstellst du animierte Bilder in FancyMenu.
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# Animationen

FancyMenu spielt animierte Bilder fast überall ab, wo du ein Bild verwenden kannst: in [Bildelementen](/elements#image), [Bild-Menühintergründen](/menu-backgrounds#image), Button- und Slider-Texturen, dem [Spielintro](/game-intro) und mehr.

Verwende **APNG**- oder **GIF**-Dateien für deine Animationen:

- **APNG** (animiertes PNG) bietet die bessere Qualität: alle Farben eines normalen PNGs und korrekte Transparenz mit weichen Kanten. Es ist die beste Wahl für Logos, Hintergründe und alles mit Transparenz.
- **GIF** ist weiter verbreitet, daher gibt es mehr Tools zum Erstellen und Bearbeiten von GIFs. Ein GIF hat jedoch nur 256 Farben pro Frame, und seine Pixel sind entweder vollständig transparent oder gar nicht.

> [!NOTE]
> Die eigenen Animationsformate von FancyMenu, FMA und AFMA, sind veraltet. Deine vorhandenen Dateien funktionieren weiterhin, aber verwende für neue Animationen APNG oder GIF. Siehe [FMA und AFMA](#fma-and-afma).

# Animationen verwenden

1. Lege die Datei in `<game-directory>/config/fancymenu/assets/` ab, damit sie in der Dateiauswahl von FancyMenu angezeigt wird. Auch Web-URLs und Dateien aus Ressourcenpaketen funktionieren; siehe [Ressourcen](/resources).
2. Wähle sie wie jedes andere Bild aus, zum Beispiel als **Bildquelle** eines Bildelements.

> [!WARNING]
> APNG-Dateien müssen auf `.apng` enden. Viele Tools speichern APNGs mit der Endung `.png`. Benenne die Datei daher um, sonst zeigt FancyMenu sie als Standbild an. Das gilt auch für Web-URLs: Sie müssen auf `.apng` enden.

## So werden Animationen abgespielt

- Eine Animation wird so oft abgespielt, wie es in der Datei festgelegt ist, und bleibt dann auf ihrem letzten Frame stehen. Wie oft sie wiederholt wird, legst du beim Erstellen der Datei fest.
- Animationen werden nur abgespielt, solange sie auf dem Bildschirm zu sehen sind. Wenn sie wieder angezeigt werden, laufen sie an der Stelle weiter, an der sie angehalten wurden.
- **Animierte Texturen beim Öffnen des Bildschirms neu starten** sorgt dafür, dass Bildelemente und Bild-Menühintergründe ihre Animation jedes Mal von vorn beginnen, wenn der Bildschirm geöffnet wird.
- **Animierte Texturen beim Darüberfahren neu starten** sorgt dafür, dass die Texturen von Buttons und Slidern jedes Mal von vorn beginnen, wenn die Maus darüber bewegt wird.
- Die Listener [**Wiedergabe animierter Textur gestartet**](/listeners#animated-texture-started-playing) und [**Wiedergabe animierter Textur beendet**](/listeners#animated-texture-finished-playing) führen Aktionen aus, wenn eine Animation startet oder endet.

## Leistung

FancyMenu dekodiert APNGs und GIFs während der Wiedergabe und lädt dabei nur einige wenige Frames im Voraus. Daher benötigen selbst lange Animationen nur wenig Speicher.

Große Frames und hohe Bildraten beeinträchtigen dennoch die Leistung. Achte darauf, dass deine Frames ungefähr so groß sind, wie sie auf dem Bildschirm angezeigt werden. Siehe [Texturen optimieren](/optimizing-textures). Für lange Clips mit Ton solltest du stattdessen ein [Video](/video) verwenden.

# Animationen erstellen

Mit diesen kostenlosen Tools kannst du aus einzelnen Frames oder Videos APNGs und GIFs erstellen:

- [ScreenToGif](https://www.screentogif.com/) (Windows): Klicke auf **Editor**, ziehe deine PNG-Frames hinein, stelle die Frame-Dauer ein und speichere die Animation als APNG oder GIF. Im Speichermenü kannst du die Wiederholung festlegen.
- [ezgif](https://ezgif.com/) (online, kein Download nötig): Erstelle aus Bildern ein [GIF](https://ezgif.com/maker) oder ein [APNG](https://ezgif.com/apng-maker), wandle ein Video in ein [GIF](https://ezgif.com/video-to-gif) oder ein [APNG](https://ezgif.com/video-to-apng) um oder konvertiere [GIF in APNG](https://ezgif.com/gif-to-apng) und [APNG in GIF](https://ezgif.com/apng-to-gif).
- [FFmpeg](https://ffmpeg.org/download.html) (Kommandozeile): siehe unten.

## Mit FFmpeg

Wandle nummerierte PNG-Frames wie `frame_0001.png`, `frame_0002.png` und so weiter in ein endlos wiederholtes APNG um. Mit `-framerate 20` werden 20 Frames pro Sekunde abgespielt:

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

Wandle ein Video in ein APNG um. `fps=20` sorgt für 20 Frames pro Sekunde, und `scale=960:-1` setzt die Breite auf 960 Pixel:

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

Wandle ein Video in ein endlos wiederholtes GIF um. Der Teil `palettegen` wählt die besten 256 Farben dafür aus:

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

Wandle ein GIF in ein APNG um:

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA und AFMA

FMA und AFMA sind die eigenen Animationsformate von FancyMenu. Beide sind veraltet: Sie werden weiterhin abgespielt, aber für neue Animationen sind APNG und GIF die bessere Wahl.

So erstellst du trotzdem eine AFMA:

1. Lege deine Frames als PNG-Dateien in einem Ordner ab. Sie werden in der Reihenfolge ihrer Dateinamen abgespielt, zum Beispiel `frame_1.png`, `frame_2.png`, ..., `frame_10.png`.
2. Öffne **Menüleiste -> Werkzeuge -> AFMA-Ersteller**.
3. Lege unter **Haupt-Frame-Verzeichnis** den Ordner fest. Frames im **Intro-Frame-Verzeichnis** werden einmal vor den Hauptframes abgespielt.
4. Lege **Dauer des Hauptframes (ms)** und **Anzahl der Wiederholungen** fest. Bei einer Anzahl von `0` wird die Animation endlos wiederholt.
5. Lege **AFMA-Ausgabedatei** fest und klicke auf **Exportieren**.
