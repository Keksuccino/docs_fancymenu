---
title: Pobieranie klatek z wideo
description: Wyodrębnij klatki PNG z wideo za pomocą FFmpeg.
---

# Wyodrębnianie klatek wideo za pomocą FFmpeg

1. Zainstaluj [FFmpeg](https://ffmpeg.org/download.html) i upewnij się, że polecenie `ffmpeg` jest dostępne.
2. Otwórz terminal w katalogu zawierającym Twój plik wideo.
3. Utwórz katalog wyjściowy:

   ```bash
   mkdir output_frames
   ```

4. Uruchom polecenie odpowiadające klatkom, których potrzebujesz. Zastąp `input.mp4` nazwą pliku wideo.

## Wyodrębnij każdą klatkę

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## Wyodrębnij z ustaloną liczbą klatek na sekundę

Ten przykład tworzy 10 klatek na sekundę. W razie potrzeby zmień `10`.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## Zmień rozmiar wyodrębnionych klatek

Ten przykład skaluje każdą klatkę do `1280×720`.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

Ponumerowane pliki PNG w `output_frames` można wykorzystać do utworzenia [animacji AFMA lub klasycznej FMA](./fma). Mniejsza liczba klatek i mniejsze wymiary zmniejszają rozmiar pliku oraz zużycie pamięci.
