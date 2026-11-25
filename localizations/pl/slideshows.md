---
title: Pokazy slajdów
description: >-
  Wyświetlaj własne obrazy jeden po drugim, z delikatnym przejściem między nimi
  — jako tło menu lub w części ekranu.
sourceBlobSha: 24ba0cbe9184108453b9829b8e6cd48d49a48b12
---

# Pokazy slajdów

Pokaz slajdów wyświetla obrazy jeden po drugim i płynnie przechodzi od jednego do następnego, na przykład pokazując zrzuty ekranu ze świata Twojej paczki modów.

Możesz wyświetlić go jako [tło menu](/menu-backgrounds) układu lub w części ekranu za pomocą [elementu pokazu slajdów](/elements#slideshow).

<img width="800" alt="Ekran tytułowy z pokazem slajdów w tle, który płynnie przechodzi od doliny rzecznej przez wiśniowy gaj do wybrzeża; zrzuty ekranu ze świata Minecrafta" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_title.gif?raw=true">

# Tworzenie pokazu slajdów

1. Otwórz folder `slideshows` w katalogu `config/fancymenu/` folderu gry. Opcja **Pasek menu -> Narzędzia -> Otwórz katalog FancyMenu** otwiera folder `config/fancymenu/`.
2. Utwórz w nim folder swojego pokazu slajdów, na przykład `world_tour`. Jego nazwa nie ma znaczenia.
3. Umieść w nim plik [`properties.txt`](#propertiestxt) oraz folder `images` zawierający [Twoje obrazy](#obrazy). Dodanie pliku [`overlay.png`](#nakładka) jest opcjonalne.
4. Przeładuj FancyMenu za pomocą opcji **Pasek menu -> Dostosowywanie -> Przeładuj FancyMenu** lub skrótu `Ctrl + Alt + R` (`Cmd + Alt + R` w systemie macOS), albo uruchom grę ponownie.

```text
config/fancymenu/slideshows/
└── world_tour/
    ├── properties.txt
    ├── overlay.png
    └── images/
        ├── 01_river_valley.png
        ├── 02_cherry_grove.png
        └── 03_coast.png
```

# Obrazy

- Uwzględniane są tylko pliki PNG i JPG, których nazwy kończą się na `.png` lub `.jpg`. Zmień rozszerzenie plików `.jpeg` na `.jpg`.
- Obrazy są wyświetlane w kolejności nazw plików, od A do Z. Cyfry są sortowane jak litery, więc `10.png` pojawi się przed `2.png`. Dodawaj zera na początku nazw, na przykład `01`, `02` … `10`.
- Wszystkie obrazy powinny mieć ten sam rozmiar. Pierwszy obraz określa proporcje pokazu slajdów, a pozostałe zostaną do nich rozciągnięte.
- Pliki znajdujące się w podfolderach folderu `images` nie są uwzględniane.

# properties.txt

```text
type = slideshow

slideshow-meta {
  name = world_tour
  duration = 5.0
  fadespeed = 5.0
  randomize = false
}
```

| Ustawienie | Działanie |
|---|---|
| `name` | Nazwa, według której wybierasz pokaz slajdów. Każdy pokaz powinien mieć własną nazwę. |
| `duration` | Liczba sekund między zmianami obrazów, łącznie z czasem przejścia. Jeśli przejście trwa dłużej, kolejna zmiana poczeka na jego zakończenie. |
| `fadespeed` | Szybkość przejścia z jednego obrazu na następny. Przy wartości `1.0` przejście trwa około 6 sekund, a przy `3.0` — około 2 sekund. Wartość musi być większa od `0`. |
| `randomize` | Wartość `true` wyświetla obrazy w losowej kolejności, bez powtarzania tego samego obrazu dwa razy z rzędu. Wartość `false` wyświetla je w kolejności nazw plików. |

Wymagane jest tylko ustawienie `name`. Pominięte ustawienia przyjmują wartości `duration = 10.0`, `fadespeed = 1.0` i `randomize = false`. Pozostaw wiersze `type = slideshow` oraz `slideshow-meta {` bez zmian, wpisuj po jednym ustawieniu w każdym wierszu i używaj kropki jako separatora dziesiętnego, na przykład `2.5`.

Pokazy slajdów utworzone dla starszych wersji mogą zawierać wiersze `width`, `height`, `x` i `y`. Nie mają one żadnego działania: o miejscu wyświetlania i rozmiarze pokazu decyduje tło lub element.

# Nakładka

Plik `overlay.png` umieszczony obok `properties.txt` jest rysowany na każdym obrazie i rozciągany do rozmiaru pokazu slajdów. Nie przechodzi płynnie wraz z obrazami, dlatego nadaje się do ramek, winiet lub logo w rogu. Przezroczyste obszary pozwalają widzieć obrazy.

Nakładka jest przypisana do pokazu slajdów, więc pojawia się wszędzie tam, gdzie jest on wyświetlany. Aby używać tych samych obrazów z ramką i bez niej, utwórz dwa pokazy slajdów.

# Korzystanie z pokazu slajdów

## Jako tło menu

<img width="800" alt="Otwieranie opcji Tła menu, wybór Pokazu slajdów w edytorze układu, włączanie opcji Pokaż tło i wybieranie world_tour w polu Wybierz pokaz slajdów; podgląd przechodzi do następnego obrazu, a pokaz wyświetla się za przyciskami ekranu tytułowego" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_background.gif?raw=true">

1. W [edytorze układu](/layout-editor) kliknij prawym przyciskiem myszy tło i otwórz **Tła menu -> Pokaz slajdów**.
2. Kliknij **Pokaż tło**, aby je włączyć.
3. Kliknij **Nazwa pokazu slajdów**, wybierz pokaz i kliknij **Gotowe**. Podgląd po prawej stronie pokazuje go w działaniu.

Opcja **Wyczyść pokaz slajdów** usuwa go. Informacje o łączeniu go z innymi tłami znajdziesz na stronie [Tła menu](/menu-backgrounds).

Pokaz slajdów jest rozciągany na cały ekran. Aby zachować proporcje obrazów, włącz opcję **Zachowaj proporcje tła** w sekcji **Tła menu**. Obraz wypełni wtedy ekran, a jego boki lub góra i dół zostaną przycięte.

## Jako element

<img width="800" alt="Ekran tytułowy z przyciskami po lewej stronie i elementem pokazu slajdów po prawej, który płynnie przechodzi między zrzutami ekranu ze świata Minecrafta" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_element.gif?raw=true">

1. W edytorze układu kliknij prawym przyciskiem myszy wolne miejsce i dodaj pokaz slajdów za pomocą opcji **Nowy element**.
2. Kliknij element prawym przyciskiem myszy, wybierz **Pokaz slajdów** i wskaż swój pokaz. Element dopasuje kształt do jego obrazów.
3. Przesuwaj i zmieniaj jego rozmiar tak jak w przypadku każdego innego elementu. Opcja **Przywróć proporcje** ponownie dopasowuje szerokość do wysokości, aby obrazy nie były rozciągnięte.

## Wstępne ładowanie

Pokaz slajdów wczytuje każdy obraz przy pierwszym wyświetleniu, dlatego w przypadku dużych obrazów pierwsze wyświetlenie może się nieco opóźnić. Aby wczytać wszystkie obrazy i nakładkę podczas uruchamiania gry, dodaj pokaz slajdów za pomocą opcji **Dodaj pokaz slajdów** w sekcji **Pasek menu -> Dostosowywanie -> Wstępne ładowanie zasobów**. Zobacz [Wstępne ładowanie zasobów](/preload-layouts#pre-loading-slideshows--panoramas).

# Warto wiedzieć

- Wszystkie miejsca wyświetlające ten sam pokaz slajdów pokazują jednocześnie ten sam obraz, także w różnych menu.
- Pokaz slajdów działa tylko wtedy, gdy jest wyświetlany. Jeśli pojawi się ponownie po przerwie dłuższej niż jego `duration`, od razu przejdzie do następnego obrazu.
- Ponowne wczytanie FancyMenu uruchamia od nowa każdy pokaz slajdów. Pierwszy obraz po uruchomieniu jest wyświetlany tylko przez połowę czasu, przez jaki wyświetlane są pozostałe.
- Pokazy slajdów należą do wczytanego [profilu](/profiles).
- Jeśli pokazu slajdów brakuje na liście **Wybierz pokaz slajdów**, nie został wczytany. W dzienniku gry `logs/latest.log` znajdziesz przyczynę, na przykład brak nazwy `name`, pliku `properties.txt` lub folderu `images`.
- W systemie Windows włącz wyświetlanie rozszerzeń nazw plików w Eksploratorze plików, aby przez pomyłkę nie utworzyć pliku `properties.txt.txt`.
- Fioletowo-czarna szachownica oznacza, że nie wybrano pokazu slajdów albo układ korzysta z nazwy pokazu, który już nie istnieje.
- Jeśli dwa pokazy slajdów mają tę samą wartość `name`, wyświetlony zostanie tylko jeden z nich.
- **Nakładka debugowania** (`Ctrl + Alt + D`) pokazuje liczbę pokazów slajdów i obrazów wczytanych przez FancyMenu.
