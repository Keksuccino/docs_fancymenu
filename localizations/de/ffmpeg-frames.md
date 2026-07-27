---
title: Frames aus Videos extrahieren
description: PNG-Frames mit FFmpeg aus einem Video extrahieren.
---

# Video-Frames mit FFmpeg extrahieren

1. Installieren Sie [FFmpeg](https://ffmpeg.org/download.html) und stellen Sie sicher, dass der Befehl `ffmpeg` verfügbar ist.
2. Öffnen Sie ein Terminal im Verzeichnis, das Ihr Video enthält.
3. Erstellen Sie das Ausgabeverzeichnis:

   ```bash
   mkdir output_frames
   ```

4. Führen Sie den Befehl aus, der zu den benötigten Frames passt. Ersetzen Sie `input.mp4` durch den Dateinamen Ihres Videos.

## Jeden Frame extrahieren

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## Mit fester Framerate extrahieren

Dieses Beispiel erstellt 10 Frames pro Sekunde. Ändern Sie `10` nach Bedarf.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## Extrahierte Frames skalieren

Dieses Beispiel skaliert jeden Frame auf `1280×720`.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

Die nummerierten PNG-Dateien in `output_frames` können verwendet werden, um eine [AFMA- oder klassische FMA-Animation](./fma) zu erstellen. Weniger Frames und kleinere Abmessungen reduzieren die Dateigröße und den Speicherverbrauch.
