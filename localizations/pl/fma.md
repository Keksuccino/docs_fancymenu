---
title: Animacje (FMA/AFMA)
description: Jak tworzyć i używać plików animacji FancyMenu.
---

# Animacje

Pliki AFMA i FMA to animowane formaty tekstur stworzone dla FancyMenu.

# Pliki AFMA

**AFMA** (Advanced FancyMenu Animation) to następca klasycznych plików FMA.

AFMA używa formatu innego niż ZIP, dzięki czemu pliki są mniejsze, zużywają mniej pamięci i działają wydajniej niż klasyczne FMA.

W przypadku dużych lub złożonych animowanych tekstur używaj **AFMA** zamiast klasycznego FMA.

Twórz pliki AFMA za pomocą wbudowanego kreatora:

1. Otwórz pasek menu FancyMenu.
2. Przejdź do **Tools -> AFMA Creator**.
3. Zaimportuj/konwertuj swoje klatki w kreatorze.

> [!IMPORTANT]
> Plików AFMA nie można pakować ręcznie. Użyj **Tools -> AFMA Creator**.

Klasyczne pliki FMA są nadal obsługiwane, więc istniejących układów nie trzeba od razu konwertować.

# Klasyczne pliki FMA

## Tworzenie FMA

Klasyczny plik FMA to archiwum ZIP z rozszerzeniem `.fma`.

### Rozszerzenia plików

Włącz wyświetlanie rozszerzeń plików w menedżerze plików, zanim utworzysz lub zmienisz nazwy poniższych plików.

W systemie Windows otwórz Eksplorator plików i włącz **Widok -> Rozszerzenia nazw plików**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Przygotowanie

Utwórz folder o nazwie `fancymenu_animation` na zawartość archiwum.

W jego wnętrzu utwórz wymagany katalog `frames` oraz opcjonalny katalog `intro_frames`.

W tym samym folderze utwórz `metadata.json`. Upewnij się, że jego rozszerzenie to `.json`, a nie `.txt`.

Folder powinien teraz zawierać `frames/`, `intro_frames/` oraz `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### Plik JSON metadanych

Otwórz `metadata.json` w edytorze tekstu i użyj tego szablonu:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

Edytuj wartości według potrzeb.

#### `loop_count`

Określa, ile razy animacja ma się odtworzyć. Użyj `0`, aby zapętlać bez końca. Wartość dodatnia odtwarza animację tyle razy, po czym zatrzymuje się na ostatniej klatce.

#### `frame_time`

Ustawia, jak długo każda zwykła klatka pozostaje widoczna, w milisekundach.

#### `frame_time_intro`

Ustawia czas klatki dla opcjonalnych klatek **intro**.

#### `custom_frame_times`

Opcjonalnie nadpisuje czas trwania poszczególnych zwykłych klatek. Ten przykład utrzymuje klatki `0` i `1` widoczne przez `5000` milisekund, podczas gdy pozostałe klatki używają wartości `frame_time`:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Indeksy klatek zaczynają się od zera: pierwsza klatka to `0`, druga to `1` itd.

Dodaj przecinek po każdym wpisie niestandardowego czasu klatki, z wyjątkiem ostatniego.

#### `custom_frame_times_intro`

Używa tego samego formatu co `custom_frame_times`, ale dotyczy opcjonalnych klatek intro.

Zapisz `metadata.json`.

### Klatki

> [!CAUTION]
> Utrzymuj klasyczne animacje FMA na poziomie maksymalnie 200 klatek i 1080p. Do długich materiałów lub materiałów o wysokiej liczbie klatek użyj [Video](./video).

Umieść zwykłe klatki w `frames/`. Muszą to być pliki PNG nazwane kolejno od `0.png`, na przykład `0.png`, `1.png` i `2.png`. Inne formaty i nazwy nie są obsługiwane.

Aby wyodrębnić klatki z wideo, zobacz [Wyodrębnianie klatek za pomocą FFmpeg](./ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### Intro

Umieść opcjonalne klatki intro w `intro_frames/`. Podlegają tym samym zasadom nazewnictwa plików PNG co zwykłe klatki, odtwarzają się raz przed zwykłą sekwencją i nie zapętlają się.

### Pakowanie pliku FMA

Utwórz ZIP zawierający zawartość folderu. `metadata.json`, `frames/` oraz opcjonalny katalog `intro_frames/` muszą znajdować się w katalogu głównym ZIP-a, a nie wewnątrz innego folderu.

W systemie Windows zaznacz zawartość `fancymenu_animation`, kliknij prawym przyciskiem myszy zaznaczenie i wybierz **Wyślij do -> Folder skompresowany (zip)**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Znajdź utworzony plik ZIP.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Jego zawartość w katalogu głównym powinna wyglądać tak:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Zmień nazwę pliku na `fancymenu_animation.fma`, zastępując rozszerzenie `.zip`. Nazwę bazową można zmienić, ale wymagane jest rozszerzenie `.fma`.

Przemianowane archiwum jest teraz gotowe do użycia jako plik FMA.

# Używanie plików AFMA i FMA w FancyMenu

> [!IMPORTANT]
> Pliki AFMA/FMA są animowanymi teksturami, więc dodawaj je przez wejścia [**Image**](./elements#image). Prawie wszystko, co akceptuje obrazy, akceptuje też pliki AFMA i FMA.

Używaj plików AFMA/FMA wszędzie tam, gdzie można podać obraz, w tym w [elementach Image](./elements#image) oraz [Tłach menu Image](./menu-backgrounds).

Umieść plik AFMA/FMA w `<game-directory>/config/fancymenu/assets/`, aby pojawiał się w lokalnym selektorze zasobów FancyMenu.
