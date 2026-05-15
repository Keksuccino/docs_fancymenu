---
title: Pobieranie klatek z filmów
description: Jak pobrać klatki z pliku wideo.
---

# Jak pobierać klatki z filmu za pomocą FFmpeg

*Ta strona została częściowo wygenerowana przez AI ChatGPT.*

FFmpeg to darmowe narzędzie, które pomaga pracować z plikami wideo i audio. Jedną z przydatnych rzeczy, jakie można z nim zrobić, jest wyodrębnianie obrazów (klatek) z filmu, na przykład z pliku MP4. Oto jak zrobić to krok po kroku.

W poniższych poleceniach używany będzie format MP4, ale FFmpeg obsługuje też inne formaty wideo, takie jak AVI, MOV, MKV i MPEG.

# Czego potrzebujesz

Zanim zaczniesz, upewnij się, że masz:

1. **Zainstalowany FFmpeg**:

   - Pobierz FFmpeg z oficjalnej strony [FFmpeg](https://ffmpeg.org/download.html). Pamiętaj, aby pobrać pełną wersję („full build”).
   - Postępuj zgodnie z instrukcjami instalacji dla swojego komputera.

2. **Dostęp do wiersza poleceń**:

   - Użyj terminala (Linux/macOS) lub wiersza polecenia (Windows), aby uruchamiać polecenia FFmpeg.

3. **Plik wideo**:

    - Przygotuj plik wideo MP4, AVI, MOV, MKV lub MPEG.

# Zanim zaczniesz

Przed uruchomieniem jakichkolwiek poleceń przygotuj następujące rzeczy:

## Włącz rozszerzenia plików

  - Ważne jest, aby widzieć rozszerzenia plików, takie jak `.mp4` lub `.avi`, podczas zmieniania nazwy pliku wideo.

    - **W systemie Windows**:

      - Otwórz Eksplorator plików.
      - Kliknij kartę „Widok” u góry.
      - Zaznacz pole „Rozszerzenia nazw plików”.

    - **W systemie macOS**:

      - Otwórz Finder.
      - Kliknij „Finder” na pasku menu i wybierz „Ustawienia”.
      - Przejdź do karty „Zaawansowane” i zaznacz opcję „Pokaż wszystkie rozszerzenia nazw plików”.

## Utwórz folder wyjściowy

- Utwórz folder o nazwie `output_frames` w katalogu, w którym znajduje się plik wykonywalny FFmpeg. To właśnie tam zostaną zapisane wyodrębnione klatki.

## Przygotuj plik wideo

- Umieść plik wideo, z którego chcesz wyodrębnić klatki, w tym samym katalogu co plik wykonywalny FFmpeg.
- Zmień nazwę pliku wideo na `input`, a następnie dodaj jego rozszerzenie pliku (np. `input.mp4`, `input.avi` itd.). Dzięki temu poniższe polecenia będą działać bez zmian.

<br>
<img width="579" alt="Screenshot_4" src="https://gist.github.com/user-attachments/assets/1cb4ddf9-a17a-4219-b7d4-aa344adaa87c" />

# Jak uruchomić FFmpeg

Zanim będziesz mógł używać FFmpeg, musisz uruchomić go z wiersza poleceń. Oto jak zrobić to krok po kroku w systemach Windows i macOS.

## W systemie Windows:

1. **Otwórz Wiersz polecenia**:
   - Naciśnij jednocześnie klawisz `Windows` i `R`, aby otworzyć okno Uruchamianie.
   - Wpisz `cmd` i naciśnij Enter. Otworzy się Wiersz polecenia.

2. **Przejdź do folderu FFmpeg**:
   - Musisz wskazać komputerowi, gdzie znajduje się FFmpeg. Użyj polecenia `cd`, aby przejść do folderu, w którym zapisano FFmpeg.
   - Na przykład, jeśli FFmpeg znajduje się w folderze `ffmpeg-2024\bin` na pulpicie, wpisz:
     ```bash
     cd C:\Users\TwojaNazwaUżytkownika\Desktop\ffmpeg-2024\bin
     ```
     (Zastąp „TwojaNazwaUżytkownika” rzeczywistą nazwą użytkownika na komputerze.)

3. **Sprawdź, czy FFmpeg działa**:
   - Aby upewnić się, że FFmpeg działa, wpisz to polecenie:
     ```bash
     ffmpeg -version
     ```
   - Jeśli wszystko działa poprawnie, na ekranie pojawią się informacje o FFmpeg.

## W systemie macOS:

1. **Otwórz Terminal**:
   - Naciśnij jednocześnie `Command` i `Space`, aby otworzyć wyszukiwanie Spotlight.
   - Wpisz `Terminal` i naciśnij Enter, aby go otworzyć.

2. **Przejdź do folderu FFmpeg**:
   - Użyj polecenia `cd`, aby przejść do folderu, w którym zapisano FFmpeg.
   - Na przykład, jeśli FFmpeg znajduje się w folderze `Downloads`, wpisz:
     ```bash
     cd ~/Downloads/ffmpeg-2024/bin
     ```

3. **Sprawdź, czy FFmpeg działa**:
   - Aby upewnić się, że FFmpeg jest gotowy, wpisz to polecenie:
     ```bash
     ./ffmpeg -version
     ```
   - Jeśli FFmpeg działa poprawnie, na ekranie pojawią się szczegóły na jego temat.

# Jak zapisać wszystkie klatki

Aby zapisać wszystkie klatki z filmu, użyj tego polecenia:

```bash
ffmpeg -i input.mp4 output_frames/%d.png
```

## Co to oznacza:

- `-i input.mp4`: To jest plik wejściowy wideo. Powinien znajdować się w tym samym katalogu co plik wykonywalny FFmpeg. Pamiętaj, aby zmienić `input.mp4` na poprawną nazwę pliku i rozszerzenie.
- `output_frames/frame_%04d.png`: W ten sposób będą zapisywane klatki:
- `output_frames/`: Zapisuje wszystkie klatki w folderze o nazwie `output_frames`.
- `%d.png`: Klatki będą nazywane numerami, takimi jak `1.png`, `2.png` i tak dalej, zachowując kolejność.

# Zapisywanie klatek w określonych odstępach czasu

Jeśli nie chcesz zapisywać wszystkich klatek, możesz zapisywać jedną klatkę co sekundę (lub w innych odstępach). Użyj tego polecenia:

```bash
ffmpeg -i input.mp4 -vf "fps=1" output_frames/%d.png
```

## Co to oznacza:

- `-i input.mp4`: To jest plik wejściowy wideo. Powinien znajdować się w tym samym katalogu co plik wykonywalny FFmpeg. Pamiętaj, aby zmienić `input.mp4` na poprawną nazwę pliku i rozszerzenie.
- `-vf "fps=1"`: To zapisuje jedną klatkę na sekundę. Zmień `1` na inną wartość, jeśli chcesz zapisywać klatki częściej lub rzadziej (np. `fps=0.5` zapisuje jedną klatkę co dwie sekundy, a `fps=2` zapisuje dwie klatki na sekundę).
- `output_frames/%d.png`: Zapisuje klatki w folderze o nazwie `output_frames` pod nazwami takimi jak `1.png`, `2.png` i tak dalej.

# Zmiana rozmiaru i jakości klatek

Możesz także dostosować rozmiar i jakość zapisywanych klatek. Oto jak:

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" -q:v 2 output_frames/%d.png
```

## Co to oznacza:

- `-i input.mp4`: To jest plik wejściowy wideo. Powinien znajdować się w tym samym katalogu co plik wykonywalny FFmpeg. Pamiętaj, aby zmienić `input.mp4` na poprawną nazwę pliku i rozszerzenie.
- `-vf "scale=1280:720"`: Zmienia rozmiar klatki na 1280x720 pikseli.
- `-q:v 2`: Ustawia jakość obrazu (1 to najlepsza jakość, wyższe liczby oznaczają niższą jakość).
- `output_frames/%d.png`: Zapisuje klatki w folderze o nazwie `output_frames` pod nazwami takimi jak `1.png`, `2.png` i tak dalej.

# Wskazówki dotyczące zapisywania klatek

1. **Oszczędzaj miejsce**:

   - Jeśli film jest długi, możesz zapisywać klatki w odstępach zamiast zapisywać każdą klatkę. Jest to szczególnie przydatne, gdy używasz ich jako klatek animacji FMA w FancyMenu.

2. **Dowiedz się więcej**:

   - Uruchom `ffmpeg -h` w terminalu, aby zobaczyć wszystkie możliwości FFmpeg.

<br>
Teraz jesteś gotowy, aby używać FFmpeg do zapisywania klatek z filmu!&#x20;

