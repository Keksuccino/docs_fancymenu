---
title: Panoramy
description: >-
  Twórz własne, obracające się panoramy w tle z sześciu obrazów — takie jak ta
  na ekranie tytułowym Minecrafta.
sourceBlobSha: e1f9ab155301f1b88df58dd8414eeee5714cfba6
---

# Panoramy

Panorama to tło, które powoli obraca się wokół widza, tak jak na ekranie tytułowym Minecrafta. Składa się z sześciu obrazów tworzących sześcian wokół widza.

Możesz wyświetlać własne panoramy jako [tło menu](/menu-backgrounds) układu albo zamiast panoramy Minecrafta we wszystkich menu.

<img width="800" alt="Ekran tytułowy na tle powoli obracającej się panoramy drewnianej chaty na leśnej polanie o zachodzie słońca, z ogrodem, szopą na drewno i kurnikiem" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_title.gif?raw=true">

> [!TIP]
> Panoramy z tej strony możesz używać bezpłatnie do testów i we własnych modpackach: [forest_homestead.zip](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/forest_homestead.zip) (4 MB). Rozpakuj plik do folderu `config/fancymenu/panoramas/` i przeładuj FancyMenu.

# Tworzenie panoramy

1. Otwórz folder `panoramas` w katalogu `config/fancymenu/` w folderze gry. **Pasek menu -> Tools -> Open FancyMenu Directory** otwiera folder `config/fancymenu/`.
2. Utwórz w nim folder na panoramę, na przykład `forest_homestead`. Jego nazwa nie ma znaczenia.
3. Umieść w nim plik `properties.txt` oraz folder o nazwie `panorama`, zawierający [sześć obrazów](#sześć-obrazów). Dodanie pliku `overlay.png` jest opcjonalne.
4. Przeładuj FancyMenu, wybierając **Pasek menu -> Customization -> Reload FancyMenu** lub naciskając `Ctrl + Alt + R` (`Cmd + Alt + R` w systemie macOS), albo uruchom ponownie grę.

```text
config/fancymenu/panoramas/
└── forest_homestead/
    ├── properties.txt
    ├── overlay.png
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

# Sześć obrazów

Każdy obraz przedstawia jedną ścianę sześcianu:

<img width="796" alt="Sześć obrazów panoramy leśnej chaty ułożonych w formie rozłożonego sześcianu: obraz górny nad przednim, obrazy lewej, przedniej, prawej i tylnej ściany w jednym rzędzie, a obraz dolny pod przednim" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_cube.png?raw=true">

| Obraz | Ściana |
|---|---|
| `panorama_0.png` | Przednia |
| `panorama_1.png` | Prawa |
| `panorama_2.png` | Tylna |
| `panorama_3.png` | Lewa |
| `panorama_4.png` | Górna |
| `panorama_5.png` | Dolna |

- Cztery ściany otaczają widza w podanej kolejności: prawa krawędź każdego obrazu łączy się z lewą krawędzią następnego, a prawa krawędź `panorama_3.png` łączy się z lewą krawędzią `panorama_0.png`.
- Dolna krawędź górnego obrazu styka się z górną krawędzią przedniego obrazu. Górna krawędź dolnego obrazu styka się z dolną krawędzią przedniego obrazu.
- Wszystkie sześć obrazów musi być plikami PNG o tych samych wymiarach. Użyj kwadratowych obrazów, na przykład 1024 × 1024.
- FancyMenu nie wygładza obrazów, więc grafika pikselowa pozostaje ostra.

Minecraft używa takiego samego układu dla własnej panoramy, więc działają również panoramy przygotowane do Minecrafta.

# properties.txt

```text
type = panorama

panorama-meta {
  name = forest_homestead
  speed = 2.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Ustawienie | Działanie |
|---|---|
| `name` | Nazwa, pod którą wybierasz panoramę. Każda panorama powinna mieć własną nazwę. |
| `speed` | Szybkość obrotu. Przy wartości `1.0` panorama obraca się raz na około 4 minuty, a przy `2.0` — dwa razy szybciej. Wartość `0` zatrzymuje panoramę. Wartości powyżej `10.0` nie zwiększają już szybkości. |
| `fov` | Określa, jaka część panoramy mieści się na ekranie, w stopniach od górnej do dolnej krawędzi ekranu. Mniejsze wartości przybliżają obraz. |
| `angle` | Określa kąt patrzenia w dół, w stopniach. Wartość `0` oznacza widok prosto na horyzont, a wartości ujemne — patrzenie w górę. |
| `start_rotation` | Określa początkowy kierunek obrotu, w stopniach od `0` do `360`. Wartość `0` ustawia przedni obraz na środku. |

Wymagane jest tylko ustawienie `name`. Pominięte ustawienia przyjmują wartości `speed = 1.0`, `fov = 85.0`, `angle = 25.0` i `start_rotation = 0`. Pozostaw linie `type = panorama` oraz `panorama-meta {` bez zmian, wpisuj po jednym ustawieniu w każdym wierszu i używaj kropki w liczbach dziesiętnych, na przykład `1.5`.

# Nakładka

Plik `overlay.png` umieszczony obok `properties.txt` zostanie wyświetlony na panoramie i rozciągnięty na cały ekran. Nie obraca się razem z panoramą, dlatego nadaje się do takich elementów jak winieta, ramka lub filtr kolorystyczny. Przezroczyste obszary nakładki odsłaniają panoramę.

# Używanie panoramy

## Jako tło menu

<img width="800" alt="Otwieranie opcji Menu Backgrounds, wybieranie Cubic Panorama w edytorze układu, włączanie Show Background i wybieranie forest_homestead w Choose Panorama; panorama obraca się następnie za przyciskami ekranu tytułowego" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_background.gif?raw=true">

1. W [edytorze układu](/layout-editor) kliknij prawym przyciskiem myszy tło i wybierz **Menu Backgrounds -> Cubic Panorama**.
2. Kliknij **Show Background**, aby włączyć tło.
3. Kliknij **Panorama Name**, wybierz panoramę i kliknij **Done**. Podgląd po prawej pokazuje, jak się obraca.

Kliknięcie **Clear Panorama** usuwa panoramę. Informacje o łączeniu jej z innymi tłami znajdziesz w sekcji [Tła menu](/menu-backgrounds).

## We wszystkich menu

Opcja **Pasek menu -> Customization -> Global Customizations -> Custom Menu Background Panorama -> Choose Panorama** wyświetla wybraną panoramę zamiast panoramy Minecrafta na ekranie tytułowym i we wszystkich menu przed wejściem do świata. Zobacz sekcję [Globalne ustawienia niestandardowe](/global-customizations#menu-backgrounds).

## Wstępne wczytywanie

Duża panorama może pojawić się z opóźnieniem przy pierwszym wyświetleniu. Aby wczytać ją podczas uruchamiania gry, dodaj ją za pomocą opcji **Add Cubic Panorama** w menu **Pasek menu -> Customization -> Pre-Load Resources**. Zobacz sekcję [Wstępne wczytywanie zasobów](/preload-layouts#pre-loading-slideshows--panoramas).

# Warto wiedzieć

- Panoramy obracają się w prawo: przedni obraz przesuwa się w lewo, a po prawej stronie pojawia się prawy obraz.
- Wszystkie menu wyświetlające tę samą panoramę korzystają z jej wspólnego obrotu, dzięki czemu obraca się ona płynnie przy przełączaniu między menu. Obrót zatrzymuje się, gdy nie wyświetla jej żadne menu.
- Przeładowanie FancyMenu rozpoczyna obrót każdej panoramy od jej wartości `start_rotation`.
- Panoramy należą do wczytanego [profilu](/profiles).
- Jeśli panoramy nie ma na liście **Choose Panorama**, nie została wczytana. W logu gry `logs/latest.log` znajdziesz przyczynę, na przykład brak ustawienia `name` lub obrazu.
- Fioletowo-czarna szachownica oznacza, że nie wybrano panoramy, jej sześć obrazów ma różne wymiary albo układ odwołuje się do nazwy panoramy, która już nie istnieje.
- Jeśli dwie panoramy mają tę samą wartość `name`, wyświetli się tylko jedna z nich.
