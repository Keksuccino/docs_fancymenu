---
title: Frames aus Videos extrahieren
description: Wie man Frames aus einer Videodatei erhält.
---

# So extrahierst du Frames aus einem Video mit FFmpeg

*Diese Seite wurde teilweise von der ChatGPT-KI erstellt.*

FFmpeg ist ein kostenloses Tool, mit dem du mit Video- und Audiodateien arbeiten kannst. Eine praktische Sache, die du damit machen kannst, ist, Bilder (Frames) aus einem Video zu extrahieren, zum Beispiel aus einer MP4-Datei. So geht’s Schritt für Schritt.

In den folgenden Befehlen wird MP4 verwendet, FFmpeg unterstützt aber auch andere Videoformate wie AVI, MOV, MKV und MPEG.

# Was du brauchst

Bevor du anfängst, stelle sicher, dass du Folgendes hast:

1. **FFmpeg installiert**:

   - Lade FFmpeg von der offiziellen [FFmpeg-Website](https://ffmpeg.org/download.html) herunter. Achte darauf, die „Full“-Version herunterzuladen.
   - Folge den Einrichtungsanweisungen für deinen Computer.

2. **Zugriff auf die Kommandozeile**:

   - Verwende das Terminal (Linux/macOS) oder die Eingabeaufforderung (Windows), um FFmpeg-Befehle auszuführen.

3. **Eine Videodatei**:

    - Halte eine MP4-, AVI-, MOV-, MKV- oder MPEG-Videodatei bereit.

# Vor dem Start

Bevor du irgendwelche Befehle ausführst, bereite bitte Folgendes vor:

## Dateiendungen anzeigen aktivieren

  - Es ist wichtig, Dateiendungen wie `.mp4` oder `.avi` zu sehen, wenn du deine Videodatei umbenennst.

    - **Unter Windows**:

      - Öffne den Datei-Explorer.
      - Klicke oben auf die Registerkarte „Ansicht“.
      - Aktiviere das Kontrollkästchen „Dateinamenerweiterungen“. 

    - **Unter macOS**:

      - Öffne den Finder.
      - Klicke in der Menüleiste auf „Finder“ und wähle „Einstellungen“.
      - Gehe zum Tab „Erweitert“ und aktiviere „Alle Dateinamenerweiterungen einblenden“.

## Einen Ausgabeordner erstellen

- Erstelle im Verzeichnis, in dem sich die FFmpeg-Programmdatei befindet, einen Ordner namens `output_frames`. Dort werden deine extrahierten Frames gespeichert.

## Deine Videodatei vorbereiten

- Lege die Videodatei, aus der du Frames extrahieren möchtest, in denselben Ordner wie die FFmpeg-Programmdatei.
- Benenne die Videodatei in `input` plus Dateiendung um (z. B. `input.mp4`, `input.avi` usw.). So funktionieren die folgenden Befehle ohne Änderungen.

<br>
<img width="579" alt="Screenshot_4" src="https://gist.github.com/user-attachments/assets/1cb4ddf9-a17a-4219-b7d4-aa344adaa87c" />

# So öffnest du FFmpeg

Bevor du FFmpeg verwenden kannst, musst du es über die Kommandozeile öffnen. So geht’s Schritt für Schritt unter Windows und macOS.

## Unter Windows:

1. **Die Eingabeaufforderung öffnen**:
   - Drücke gleichzeitig die `Windows`-Taste und die `R`-Taste, um das Ausführen-Fenster zu öffnen.
   - Gib `cmd` ein und drücke Enter. Dadurch wird die Eingabeaufforderung geöffnet.

2. **Zum FFmpeg-Ordner wechseln**:
   - Du musst dem Computer mitteilen, wo sich FFmpeg befindet. Verwende den Befehl `cd`, um in den Ordner zu wechseln, in dem du FFmpeg gespeichert hast.
   - Wenn sich FFmpeg zum Beispiel in einem Ordner namens `ffmpeg-2024\bin` auf deinem Desktop befindet, gib Folgendes ein:
     ```bash
     cd C:\Users\YourUsername\Desktop\ffmpeg-2024\bin
     ```
     (Ersetze „YourUsername“ durch deinen tatsächlichen Benutzernamen auf dem Computer.)

3. **Prüfen, ob FFmpeg funktioniert**:
   - Um sicherzustellen, dass FFmpeg funktioniert, gib diesen Befehl ein:
     ```bash
     ffmpeg -version
     ```
   - Wenn alles funktioniert, werden Informationen zu FFmpeg auf dem Bildschirm angezeigt.

## Unter macOS:

1. **Das Terminal öffnen**:
   - Drücke gleichzeitig `Command` und `Space`, um die Spotlight-Suche zu öffnen.
   - Gib `Terminal` ein und drücke Enter, um es zu öffnen.

2. **Zum FFmpeg-Ordner wechseln**:
   - Verwende den Befehl `cd`, um in den Ordner zu wechseln, in dem du FFmpeg gespeichert hast.
   - Wenn sich FFmpeg zum Beispiel in deinem `Downloads`-Ordner befindet, gib Folgendes ein:
     ```bash
     cd ~/Downloads/ffmpeg-2024/bin
     ```

3. **Prüfen, ob FFmpeg funktioniert**:
   - Um sicherzustellen, dass FFmpeg bereit ist, gib diesen Befehl ein:
     ```bash
     ./ffmpeg -version
     ```
   - Wenn FFmpeg funktioniert, werden Details dazu auf dem Bildschirm angezeigt.

# So speicherst du alle Frames

Um alle Frames aus einem Video zu speichern, verwende diesen Befehl:

```bash
ffmpeg -i input.mp4 output_frames/%d.png
```

## Was das bedeutet:

- `-i input.mp4`: Das ist deine Eingabedatei für das Video. Sie sollte sich im selben Verzeichnis wie die FFmpeg-Programmdatei befinden. Achte darauf, `input.mp4` durch den richtigen Dateinamen und die richtige Dateiendung zu ersetzen.
- `output_frames/frame_%04d.png`: So werden die Frames gespeichert:
- `output_frames/`: Speichert alle Frames in einem Ordner namens `output_frames`.
- `%d.png`: Die Frames werden mit Nummern wie `1.png`, `2.png` usw. benannt, sodass sie in der richtigen Reihenfolge bleiben.

# Frames zu bestimmten Zeitpunkten speichern

Wenn du nicht alle Frames möchtest, kannst du stattdessen einen Frame pro Sekunde (oder in anderen Intervallen) speichern. Verwende dafür diesen Befehl:

```bash
ffmpeg -i input.mp4 -vf "fps=1" output_frames/%d.png
```

## Was das bedeutet:

- `-i input.mp4`: Das ist deine Eingabedatei für das Video. Sie sollte sich im selben Verzeichnis wie die FFmpeg-Programmdatei befinden. Achte darauf, `input.mp4` durch den richtigen Dateinamen und die richtige Dateiendung zu ersetzen.
- `-vf "fps=1"`: Das speichert einen Frame pro Sekunde. Ändere die `1` in eine andere Zahl, wenn du Frames häufiger oder seltener speichern möchtest (z. B. speichert `fps=0.5` einen Frame alle zwei Sekunden, und `fps=2` speichert zwei Frames pro Sekunde).
- `output_frames/%d.png`: Speichert die Frames in einem Ordner namens `output_frames` mit Namen wie `1.png`, `2.png` usw.

# Größe und Qualität der Frames ändern

Du kannst auch Größe und Qualität der gespeicherten Frames anpassen. So geht’s:

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" -q:v 2 output_frames/%d.png
```

## Was das bedeutet:

- `-i input.mp4`: Das ist deine Eingabedatei für das Video. Sie sollte sich im selben Verzeichnis wie die FFmpeg-Programmdatei befinden. Achte darauf, `input.mp4` durch den richtigen Dateinamen und die richtige Dateiendung zu ersetzen.
- `-vf "scale=1280:720"`: Ändert die Frame-Größe auf 1280x720 Pixel.
- `-q:v 2`: Legt die Bildqualität fest (1 ist die beste Qualität, höhere Zahlen bedeuten geringere Qualität).
- `output_frames/%d.png`: Speichert die Frames in einem Ordner namens `output_frames` mit Namen wie `1.png`, `2.png` usw.

# Tipps zum Speichern von Frames

1. **Speicherplatz sparen**:

   - Wenn das Video lang ist, kannst du Frames in Abständen speichern, statt jeden einzelnen Frame zu sichern. Das ist besonders nützlich, wenn du sie als FMA-Animationsframes in FancyMenu verwenden möchtest.

2. **Mehr erfahren**:

   - Führe `ffmpeg -h` in deinem Terminal aus, um alle Funktionen von FFmpeg zu sehen.

<br>
Jetzt bist du bereit, mit FFmpeg Frames aus deinem Video zu speichern!&#x20;

