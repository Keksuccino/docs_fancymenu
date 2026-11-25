---
title: Animacje
description: Jak używać animowanych obrazów w FancyMenu i jak je tworzyć.
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# Animacje

FancyMenu odtwarza animowane obrazy niemal wszędzie tam, gdzie można użyć obrazu: w [elementach obrazu](/elements#image), [obrazach tła menu](/menu-backgrounds#image), teksturach przycisków i suwaków, [wstępie do gry](/game-intro) i nie tylko.

Do animacji używaj plików **APNG** lub **GIF**:

- **APNG** (animowany PNG) zapewnia lepszą jakość: wszystkie kolory zwykłego PNG i poprawną przezroczystość z miękkimi krawędziami. To najlepszy wybór dla logo, teł i wszystkiego, co ma przezroczystość.
- **GIF** jest popularniejszy, więc dostępnych jest więcej narzędzi do tworzenia i edycji plików GIF. Ma jednak tylko 256 kolorów na klatkę, a jego piksele są albo całkowicie przezroczyste, albo całkowicie nieprzezroczyste.

> [!NOTE]
> Własne formaty animacji FancyMenu, FMA i AFMA, są przestarzałe. Istniejące pliki nadal działają, ale do nowych animacji używaj APNG lub GIF. Zobacz [FMA i AFMA](#fma-and-afma).

# Używanie animacji

1. Umieść plik w `<game-directory>/config/fancymenu/assets/`, aby pojawił się w oknie wyboru plików FancyMenu. Działają też adresy URL i pliki z paczek zasobów — zobacz [Zasoby](/resources).
2. Wybierz go tak jak każdy inny obraz, na przykład jako **Image Source** elementu obrazu.

> [!WARNING]
> Pliki APNG muszą mieć rozszerzenie `.apng`. Wiele narzędzi zapisuje pliki APNG z rozszerzeniem `.png`, więc zmień nazwę pliku. W przeciwnym razie FancyMenu wyświetli go jako nieruchomy obraz. To samo dotyczy adresów URL — muszą kończyć się na `.apng`.

## Odtwarzanie animacji

- Animacja odtwarza się tyle razy, ile określono w pliku, a następnie zatrzymuje się na ostatniej klatce. Liczbę powtórzeń ustawia się podczas tworzenia pliku.
- Animacje są odtwarzane tylko wtedy, gdy są widoczne na ekranie. Gdy znów się pojawią, będą kontynuowane od miejsca, w którym zostały zatrzymane.
- **Restart Animated Textures When Opening Screen** sprawia, że animacje w elementach obrazu i obrazach tła menu zaczynają się od początku przy każdym otwarciu ekranu.
- **Restart Animated Textures On Hover** sprawia, że tekstury przycisków i suwaków zaczynają się od początku za każdym razem, gdy kursor myszy znajdzie się nad nimi.
- Nasłuchiwacze [**Animated Texture Started Playing**](/listeners#animated-texture-started-playing) i [**Animated Texture Finished Playing**](/listeners#animated-texture-finished-playing) wykonują akcje po rozpoczęciu lub zakończeniu animacji.

## Wydajność

FancyMenu dekoduje pliki APNG i GIF podczas odtwarzania, z wyprzedzeniem przetwarzając tylko kilka klatek, dzięki czemu nawet długie animacje zajmują niewiele pamięci.

Duże klatki i wysoka liczba klatek na sekundę nadal obciążają wydajność. Twórz klatki mniej więcej tak duże, jak będą wyświetlane na ekranie — zobacz [Optymalizacja tekstur](/optimizing-textures). W przypadku długich klipów z dźwiękiem użyj funkcji [Wideo](/video).

# Tworzenie animacji

Te bezpłatne narzędzia pozwalają tworzyć pliki APNG i GIF z pojedynczych klatek lub filmów:

- [ScreenToGif](https://www.screentogif.com/) (Windows): kliknij **Editor**, przeciągnij do niego klatki PNG, ustaw czas wyświetlania klatki i zapisz animację jako APNG lub GIF. Liczbę powtórzeń można ustawić w menu zapisu.
- [ezgif](https://ezgif.com/) (online, bez pobierania): utwórz [GIF](https://ezgif.com/maker) lub [APNG](https://ezgif.com/apng-maker) z obrazów, przekonwertuj film na [GIF](https://ezgif.com/video-to-gif) lub [APNG](https://ezgif.com/video-to-apng), albo przekonwertuj [GIF na APNG](https://ezgif.com/gif-to-apng) i [APNG na GIF](https://ezgif.com/apng-to-gif).
- [FFmpeg](https://ffmpeg.org/download.html) (wiersz poleceń): zobacz poniżej.

## Za pomocą FFmpeg

Połącz ponumerowane klatki PNG, takie jak `frame_0001.png`, `frame_0002.png` i tak dalej, w plik APNG odtwarzany w pętli bez końca. `-framerate 20` oznacza odtwarzanie 20 klatek na sekundę:

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

Przekonwertuj film na APNG. `fps=20` ustawia 20 klatek na sekundę, a `scale=960:-1` — szerokość 960 pikseli:

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

Przekonwertuj film na GIF odtwarzany w pętli bez końca. Część `palettegen` dobiera 256 najlepszych kolorów:

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

Przekonwertuj GIF na APNG:

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA i AFMA

FMA i AFMA to własne formaty animacji FancyMenu. Oba są przestarzałe: nadal można je odtwarzać, ale do nowych animacji lepiej używać APNG lub GIF.

Aby mimo to utworzyć plik AFMA:

1. Umieść klatki w postaci plików PNG w jednym folderze. Będą odtwarzane w kolejności nazw, na przykład `frame_1.png`, `frame_2.png`, ..., `frame_10.png`.
2. Otwórz **menu bar -> Tools -> AFMA Creator**.
3. Ustaw **Main Frames Directory** na ten folder. Klatki z folderu **Intro Frames Directory** zostaną odtworzone raz przed klatkami głównymi.
4. Ustaw **Main Frame Time (ms)** i **Loop Count**. Wartość `0` oznacza odtwarzanie w pętli bez końca.
5. Ustaw **Output AFMA File** i kliknij **Export**.
