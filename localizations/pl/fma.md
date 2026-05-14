---
title: Animacje (FMA/AFMA)
description: Jak tworzyć i używać plików animacji FancyMenu.
---

# Animacje

Pliki AFMA/FMA to specjalne animowane pliki tekstur stworzone dla FancyMenu.
Są praktycznie takie same jak APNG, ale są znacznie lepiej zoptymalizowane pod kątem FancyMenu.

# Pliki AFMA

FancyMenu 3.9.0 dodaje **AFMA** (Advanced FancyMenu Animation), następcę klasycznych plików FMA.

Pliki AFMA nie są już plikami ZIP. Korzystają z nowszego formatu animacji FancyMenu, który oferuje mniejsze rozmiary plików, niższe zużycie pamięci i lepszą wydajność.

W przypadku nowych dużych lub złożonych animowanych tekstur używaj **AFMA** zamiast klasycznego FMA.

Aby utworzyć plik AFMA, wykonaj następujące kroki:

1. Otwórz pasek menu FancyMenu.
2. Przejdź do **Tools -> AFMA Creator**.
3. Zaimportuj/przekonwertuj swoje klatki za pomocą kreatora.

> [!IMPORTANT]
> Plików AFMA nie można pakować ręcznie, jak klasycznych plików FMA. Aby je utworzyć/spakować, musisz użyć **AFMA Creator**.

Klasyczne pliki FMA są nadal obsługiwane i zostały zoptymalizowane w FancyMenu 3.9.0, więc istniejących układów nie trzeba od razu konwertować.

# Klasyczne pliki FMA

## Tworzenie FMA

Utworzenie pliku FMA jest tak proste, jak stworzenie pliku ZIP! Cóż, to głównie dlatego, że pod spodem _jest_ to plik ZIP.

### Rozszerzenia plików

Aby móc korzystać z tej dokumentacji, musisz widzieć rozszerzenia plików, więc upewnij się, że **WŁĄCZYSZ ROZSZERZENIA PLIKÓW** zanim zaczniesz.

W systemie Windows zrobisz to, otwierając dowolny folder, a następnie klikając strzałkę w prawym górnym rogu, aby rozwinąć menu poniżej.

Następnie przejdź do zakładki **Widok** i włącz **Rozszerzenia nazw plików**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Przygotowanie

Zacznijmy od utworzenia nowego folderu na zawartość pliku FMA.
W tym przykładzie nazwijmy folder `fancymenu_animation`.

W tym folderze utwórz jeszcze dwa foldery. Pierwszy folder **musi** mieć nazwę `frames`, a drugi folder **musi** mieć nazwę `intro_frames`.

Następnie w tym samym folderze utwórz nowy plik TXT i zmień jego nazwę na `metadata.json`.
Upewnij się, że plik nadal nie jest plikiem TXT. **Musisz** zmienić rozszerzenie pliku na `json`.

Teraz powinieneś mieć folder o nazwie `fancymenu_animation`, a w nim folder `frames`, folder `intro_frames` oraz plik JSON o nazwie `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### Plik JSON z metadanymi

To jest plik, który mówi FancyMenu, jak ma obsługiwać Twoją teksturę FMA.
Zawiera informacje takie jak czas trwania klatek (jak długo klatka jest widoczna) oraz liczbę powtórzeń.

Otwórz plik `metadata.json` w edytorze tekstu.

Skopiuj ten tekst do pliku:

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

To jest podstawowy szablon tego, jak powinien wyglądać plik.
Teraz możesz dostosować go do własnych potrzeb.

#### `loop_count`

Służy do kontrolowania liczby powtórzeń tekstury (ponownego uruchomienia animacji).

Ustawienie wartości `0` oznacza, że animacja będzie zapętlana bez końca. **Nigdy** się nie zatrzyma.

Każda wartość większa od `0` oznacza liczbę odtworzeń tekstury. Na przykład ustawienie wartości `1` spowoduje, że tekstura odtworzy się tylko raz, a następnie zatrzyma się na ostatniej klatce, `2` oznacza dwa odtworzenia, po czym zatrzyma się na ostatniej klatce **i tak dalej**.

#### `frame_time`

To uniwersalny czas klatki w **milisekundach** dla klatek animowanej tekstury.
Czas klatki oznacza, jak długo klatka jest widoczna, zanim animacja przejdzie do następnej.

#### `frame_time_intro`

Jest to w zasadzie to samo co `frame_time`, ale dla klatek **intro** Twojej animowanej tekstury.
Klatki intro są **opcjonalne** i więcej informacji o nich znajdziesz później.

#### `custom_frame_times`

To pole jest **opcjonalne** i można je wykorzystać do nadpisania czasu trwania konkretnych klatek (nie-intro).
Na przykład chcesz, aby wszystkie klatki były wyświetlane przez `41` milisekund, więc ustawiasz `frame_time` na `41`, ale chcesz, aby pierwsza i druga klatka były wyświetlane przez `5000` milisekund.

W takim przypadku zrobisz to tak:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    0: 5000,
    1: 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Klatki są numerowane od zera, co oznacza, że pierwsza klatka animacji to `0`, druga to `1` i tak dalej.

Na końcu każdego wpisu niestandardowego czasu klatki musi znajdować się **przecinek**, **z wyjątkiem** ostatniego!

#### `custom_frame_times_intro`

To jest dokładnie to samo co `custom_frame_times`, ale w tym przypadku dotyczy klatek **intro**. Klatki intro są **opcjonalne** i więcej informacji o nich znajdziesz później.

To wszystko, jeśli chodzi o plik `metadata.json`. Zapisz go teraz i zamknij edytor tekstu.

### Klatki

> Zaleca się używanie **maksymalnie 200 klatek** przy **maksymalnej rozdzielczości 1080p** na jedną animację, ponieważ animacje zużywają dużo pamięci i nie są filmami. Mają służyć do krótkich zapętlonych animacji, a nie do odtwarzania pełnych filmów z 24 FPS.
{.is-danger}

Klatki Twojej animowanej tekstury umieść w folderze `frames`.

Klatki muszą być **PLIKAMI PNG**! **BRAK OBSŁUGI JPEG I INNYCH FORMATÓW**!

Każda klatka **musi** mieć nazwę składającą się wyłącznie z numeru klatki i rozszerzenia pliku.
Pierwsza klatka powinna nazywać się `0.png`, druga `1.png`, trzecia `2.png` i tak dalej.
Tekstura **NIE ZADZIAŁA**, jeśli klatki będą miały nieprawidłowe nazwy plików!

Aby **wyodrębnić klatki z filmów**, zajrzyj na [tę stronę dokumentacji](/ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### Intro

Ta funkcja jest **OPCJONALNA**.

Funkcja **intro** w plikach FMA to specjalny sposób odtwarzania kilku klatek **przed** rozpoczęciem odtwarzania właściwych klatek z folderu `frames`. 

Intro **nigdy** się nie zapętla i odtwarzane jest tylko za pierwszym razem, gdy animacja się uruchamia, co pozwala na przykład odtworzyć animację zanikania przed rozpoczęciem właściwej animacji w pętli.

Klatki intro umieszcza się w folderze `intro_frames` i działają one tak samo jak zwykłe klatki:

Klatki muszą być **PLIKAMI PNG**! **BRAK OBSŁUGI JPEG I INNYCH FORMATÓW**!

Każda klatka **musi** mieć nazwę składającą się wyłącznie z numeru klatki i rozszerzenia pliku.
Pierwsza klatka powinna nazywać się `0.png`, druga `1.png`, trzecia `2.png` i tak dalej.
Tekstura **NIE ZADZIAŁA**, jeśli klatki będą miały nieprawidłowe nazwy plików!

### Pakowanie pliku FMA

Teraz wszystko, co ważne, znajduje się w folderze `fancymenu_animation`, więc możesz teraz spakować swój plik FMA!

Pakowanie pliku FMA polega po prostu na spakowaniu zawartości folderu do pliku ZIP.
Zawartość musi znajdować się w **KORZENIU** pliku ZIP, więc nie może być umieszczona w dodatkowym folderze wewnątrz ZIP-a.

W systemie Windows najłatwiejszym sposobem spakowania zawartości FMA do pliku ZIP jest zaznaczenie wszystkiego w folderze `fancymenu_animation`, a następnie **kliknięcie prawym przyciskiem myszy** pliku `metadata.json`. W otwartym menu kontekstowym kliknij **Wyślij do -> Skompresowany folder ZIP**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Teraz w folderze `fancymenu_animation` powinien pojawić się nowy plik ZIP o nazwie `metadata.zip`, `frames.zip` lub `intro_frames.zip`.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Po otwarciu tego pliku jego zawartość powinna wyglądać tak:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Teraz musisz zmienić nazwę pliku na `fancymenu_animation.fma`. Upewnij się, że **ZASTĘPUJESZ** `.zip` przez `.fma`, aby plik nie był już ZIP-em.

Oczywiście możesz zmienić część `fancymenu_animation` na dowolną inną, ale upewnij się, że plik nadal ma rozszerzenie `.fma`!

To wszystko! Masz teraz (miejmy nadzieję) działający plik FMA!

# Korzystanie z plików AFMA i FMA w FancyMenu

> [!IMPORTANT]
> Pliki AFMA/FMA są traktowane jako **animowane tekstury**, więc dodaje się je za pomocą pól **Image**. Prawie wszystko, co obsługuje obrazy (PNG, JPEG, GIF itp.), będzie również akceptować pliki FMA i AFMA.

Możesz używać plików AFMA/FMA tak samo jak każdego innego formatu animowanej tekstury/obrazu. FancyMenu traktuje je jak zwykły obraz, więc możesz używać ich wszędzie tam, gdzie można ustawić teksturę, na przykład w **elementach Image lub tłach menu Image**.

Upewnij się, że plik AFMA/FMA znajduje się w folderze `/config/fancymenu/assets/`, ponieważ FancyMenu może pobierać tekstury i inne zasoby tylko ze swojego folderu `assets`.
