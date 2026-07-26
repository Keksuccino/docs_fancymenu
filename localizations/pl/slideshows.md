---
title: Pokazy slajdów
description: Twórz i używaj pokazów slajdów z obrazami.
---
# Pokazy slajdów

Każdy pokaz slajdów ma własny katalog poniżej:

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` to aktywna instancja launchera, która może różnić się od standardowego katalogu `.minecraft`.

# Struktura katalogów

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # opcjonalne
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

Obrazy muszą mieć rozszerzenie `.png` lub `.jpg`; inne rozszerzenia, w tym `.jpeg`, są ignorowane.

Gdy `randomize = false`, obrazy odtwarzane są w kolejności alfabetycznej nazw plików, bez rozróżniania wielkości liter. Używaj nazw z zerami wiodącymi, takich jak `image_01.png`, `image_02.png` i `image_10.png`.

# `properties.txt`

```text
type = slideshow

slideshow-meta {
  name = cool_slideshow
  width = 1920
  height = 1080
  x = 0
  y = 0
  duration = 5.0
  fadespeed = 12.0
  randomize = false
}
```

| Właściwość | Znaczenie |
|---|---|
| `name` | Wymagany, rozróżniany wielkością liter identyfikator używany w czasie działania; zachowaj jego unikalność |
| `width`, `height` | Bazowy rozmiar w pikselach skalowanych przez GUI oraz źródłowe proporcje obrazu |
| `x`, `y` | Bazowa pozycja lewego górnego rogu; zwykłe elementy i tła używają własnej pozycji, więc pozostaw je na `0` |
| `duration` | Minimalna liczba sekund między rozpoczęciami przejść; obejmuje czas zanikania i musi być większa od `0` |
| `fadespeed` | Mnożnik szybkości zanikania; `1.0` to wartość domyślna, wyższe wartości przyspieszają zanikanie, a wartość musi być większa od `0` |
| `randomize` | `true` dla losowego wyboru lub `false` dla kolejności według nazw plików |

Tylko `name` jest wymagane. Wartości domyślne to `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0` oraz `randomize = false`. Pozostaw `type = slideshow` i `slideshow-meta` bez zmian; zapisuj jedną parę `key = value` w każdej linii i używaj kropki jako separatora dziesiętnego.

Układy korzystają z wartości `name`, a nie z nazwy katalogu. Duplikaty nazw nie są odrzucane, a kolejność skanowania katalogów decyduje o tym, który pokaz slajdów pozostanie dostępny. Dbaj o unikalność nazw w obrębie katalogu slideshows.

Tryb losowy wybiera obraz niezależnie przy każdym przejściu i unika natychmiastowego powtórzenia, gdy dostępnych jest kilka obrazów. Czas jest liczony w czasie rzeczywistym; zanikanie trwające dłużej niż `duration` opóźnia następne przejście, a powrót do pokazu slajdów po jego ukryciu może od razu przejść do kolejnego slajdu.

# Korzystanie z pokazu slajdów

Załaduj ponownie FancyMenu przez **Dostosowywanie -> Załaduj ponownie FancyMenu** albo uruchom klienta ponownie. Użyj elementu [**Pokaz slajdów**](./elements#slideshow) albo kliknij prawym przyciskiem myszy tło edytora układu i wybierz [**Tła menu**](./menu-backgrounds) -> **Pokaz slajdów**.
