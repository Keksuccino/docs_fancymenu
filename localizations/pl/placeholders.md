---
title: Symbole zastępcze
description: >-
  Wyświetlaj w tekstach aktualne wartości, takie jak nazwa gracza, godzina czy
  liczba graczy na serwerze, oraz wszystkie symbole zastępcze dostępne w
  FancyMenu.
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# Symbole zastępcze

Symbole zastępcze to krótkie kody, które FancyMenu zastępuje aktualną wartością, taką jak nazwa gracza, godzina czy liczba graczy na serwerze. Można ich używać w tekstach elementów, etykietach przycisków, podpowiedziach, wartościach akcji i wymagań oraz w większości innych tekstów, które można wpisać.

<img width="800" alt="Dodawanie symbolu zastępczego Player Name do elementu Text w edytorze układu: symbole zastępcze w edytorze tekstu, kategoria Player i tekst witający gracza po imieniu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> W tych samych tekstach działają też własne [zmienne](/variables), zapisywane jako `$$` i ich nazwa, na przykład `$$coins`.

# Dodawanie symboli zastępczych

1. Otwórz tekst w edytorze tekstu, na przykład **Text Content** elementu [Text](/text-in-menus). Pola tekstowe w oknach, takie jak wartości akcji, mają obok przycisk **Open in Editor**.
2. Kliknij miejsce, w którym ma się pojawić symbol zastępczy.
3. Kliknij **Placeholders** w prawym górnym rogu edytora tekstu.
4. Kliknij kategorię lub wyszukaj symbol według nazwy, identyfikatora albo opisu. Przycisk **BACK** wraca do listy kategorii. Symbole bez kategorii są wyświetlane poniżej kategorii.
5. Najedź kursorem na symbol zastępczy, aby sprawdzić, do czego służy, i kliknij go, aby go dodać.
6. Zastąp przykładowe wartości, takie jak identyfikator moda w **Mod Version**.

Edytory tekstu, które nie mają przycisku **Placeholders**, nie obsługują symboli zastępczych.

# Jak działają symbole zastępcze

Symbol zastępczy wygląda tak:

```
{"placeholder":"playername"}
```

Symbole zastępcze z ustawieniami zawierają je w polu `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- Identyfikator, na przykład `playername`, rozróżnia wielkie i małe litery. Przy każdym z poniższych symboli podano jego identyfikator i wartości.
- Kolejność wartości nie ma znaczenia. Wartości oznaczone jako opcjonalne można pominąć.
- Jeśli FancyMenu nie może zastąpić symbolu, na przykład z powodu literówki, pozostaje on w tekście w niezmienionej postaci.
- Symbole zastępcze zawsze zwracają tekst. Jeśli nie ma nic do wyświetlenia, zwracają wartość zastępczą, na przykład `0`, `0.0`, `---` albo pusty tekst.
- [Kody formatowania](/text-formatting) działają wokół symboli zastępczych: `&6{"placeholder":"playername"}` wyświetla nazwę na złoto.

> [!IMPORTANT]
> Symbole zastępcze przypominają JSON, ale nim nie są. Nie przepuszczaj ich przez formatery ani walidatory JSON, ponieważ symbole zagnieżdżone w innych symbolach zastępczych nie są poprawnym JSON-em.

## Symbole zastępcze w symbolach zastępczych

Wartości mogą zawierać inne symbole zastępcze i [zmienne](/variables#showing-variables-in-text). FancyMenu zastępuje najpierw te wewnętrzne. Cudzysłowów w wartościach nie trzeba poprzedzać znakami ucieczki.

Ten przykład przelicza maksymalną ilość pamięci RAM z MB na GB:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

Ten przykład wyświetla zmienną `rank` wielkimi literami:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

Jeśli symbol zastępczy zwraca tekst zawierający inne symbole, na przykład tekst pliku odczytany przez [**File Text**](#file-text), FancyMenu również je zastępuje.

# Warto wiedzieć

- Symbole zastępcze aktualizują się automatycznie. FancyMenu przechowuje zastąpiony tekst przez 30 milisekund, a następnie ponownie zastępuje zawarte w nim symbole. Zmień ten czas za pomocą opcji **Placeholder Caching Duration [MS]** w **menu bar -> Customization -> Settings**. Wartość `0` powoduje zastępowanie symboli w każdej klatce, co zwiększa obciążenie.
- Symbole odczytujące strony internetowe, pliki lub serwery, takie jak **Web Text** czy **Server Status**, są wczytywane w tle. Do tego czasu nie zwracają niczego albo pokazują wartość zastępczą.
- W [akcjach](/action-scripts) symbole zastępcze otrzymują aktualną wartość w chwili uruchomienia akcji.
- Symbole dotyczące świata, ekranu i elementów działają tylko w głównym wątku gry. Jeśli [Ticker](/elements#ticker) działa w tle (asynchronicznie), FancyMenu wyświetli zamiast tego błąd.
- **Random Number** generuje nową liczbę przy każdej aktualizacji tekstu. Aby zachować tę samą liczbę, zapisz ją w [zmiennej](/variables) za pomocą akcji [**Set Variable Value (FM Variable)**](/action-scripts#set-variable-value-fm-variable).

> [!CAUTION]
> Symbole takie jak **JSON Parser**, **File Text** i **Clipboard Content** mogą odczytywać pliki z folderu gry oraz zawartość schowka. W połączeniu z akcjami łączącymi się ze stronami internetowymi układ może wysyłać te dane na zewnątrz. Używaj tylko zaufanych układów.

# Przykłady

## Panel powitalny

<img width="800" alt="Element Text wita gracza po imieniu i wyświetla wersję Minecrafta, liczbę modów oraz godzinę" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### Welcome back, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"} with {"placeholder":"loadedmods"} mods
It's {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Status serwera i liczba graczy

```
Survival: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}} players
```

## Data i godzina

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}, {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Użycie pamięci RAM

```
RAM: {"placeholder":"usedram"} / {"placeholder":"maxram"} MB ({"placeholder":"percentram"}%)
```

# Wszystkie symbole zastępcze

Poniżej znajduje się lista wszystkich symboli zastępczych dostępnych w FancyMenu. Duże kategorie **Advanced** i **World** z menu symboli zastępczych podzielono tu na mniejsze grupy.

## Zmienne i listy

Znajdują się w kategorii **Advanced**. Informacje o tworzeniu zmiennych i list znajdziesz w sekcji [Zmienne](/variables).

### Get Variable Value (FM Variable)

**Identyfikator:** `getvariable`

Wartość jednej ze zmiennych. Jeśli zmienna jest pusta lub nie istnieje, zwracane jest `0`, dlatego symbol dobrze sprawdza się w przypadku liczb. Lista zwraca wszystkie swoje elementy w postaci tablicy JSON, na przykład `["Steve","Alex"]`.

- `name`: nazwa zmiennej, bez `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Get List Entry (FM Variable)

**Identyfikator:** `list_get`

Jeden element zmiennej typu lista.

- `name`: nazwa listy
- `index`: pozycja elementu. Pierwszy element ma indeks `0`, a liczby ujemne liczą od końca, więc `-1` oznacza ostatni element.
- `fallback` (opcjonalnie): wartość zwracana, gdy pod danym indeksem nie ma elementu albo lista o tej nazwie nie istnieje. Domyślnie pusty tekst.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### List Size (FM Variable)

**Identyfikator:** `list_size`

Liczba elementów listy. Zwraca `0`, jeśli lista o tej nazwie nie istnieje.

- `name`: nazwa listy

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Index of List Entry (FM Variable)

**Identyfikator:** `list_index_of`

Indeks pierwszego elementu, który jest równy całej wartości `value`, albo `-1`, jeśli lista jej nie zawiera.

- `name`: nazwa listy
- `value`: wyszukiwana wartość
- `ignore_case` (opcjonalnie): wartość `true` sprawia, że `Apple` pasuje do `apple`. Domyślnie `false`.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Join List Entries (FM Variable)

**Identyfikator:** `list_join`

Wszystkie elementy listy połączone w jeden tekst. Zwraca pusty tekst, jeśli lista o tej nazwie nie istnieje.

- `name`: nazwa listy
- `separator` (opcjonalnie): tekst umieszczany między elementami. `\n` oznacza nowy wiersz. Domyślnie `, `.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Matematyka

Znajdują się w kategorii **Advanced**. Jako separatora dziesiętnego używają kropki, na przykład `2.5`.

### Calculator

**Identyfikator:** `calc`

Oblicza wyrażenie matematyczne, na przykład `2 + 3 * 4`.

- `expression`: wyrażenie do obliczenia
- `decimal` (opcjonalnie): `false` zaokrągla wynik do liczby całkowitej. Domyślne `true` pozwala otrzymywać wyniki takie jak `14.0`.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| W wyrażeniach | Działanie |
|---|---|
| `+` `-` `*` `/` | Dodawanie, odejmowanie, mnożenie, dzielenie |
| `^` | Potęgowanie, na przykład `2 ^ 3` daje 8 |
| `%` | Reszta z dzielenia, na przykład `7 % 3` daje 1 |
| `( )` | Grupowanie części wyrażenia, na przykład `(2 + 3) * 4` |
| `pi`, `e` | Liczby π i e |
| `abs(x)` | Wartość bezwzględna liczby |
| `sqrt(x)`, `cbrt(x)` | Pierwiastek kwadratowy i sześcienny |
| `pow(x, y)` | x do potęgi y |
| `floor(x)`, `ceil(x)` | Zaokrąglenie w dół i w górę |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Funkcje trygonometryczne; kąty podaje się w radianach |
| `asin(x)`, `acos(x)`, `atan(x)` | Odwrotne funkcje trygonometryczne |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Funkcje hiperboliczne |
| `log(x)`, `log2(x)`, `log10(x)` | Logarytmy o podstawach e, 2 i 10 |
| `exp(x)` | e do potęgi x |
| `signum(x)` | `1`, `-1` lub `0`, podobnie jak w [**Sign (Math)**](#sign-math) |

### Random Number

**Identyfikator:** `random_number`

Losowa liczba całkowita z zakresu od `min` do `max`. Zmienia się przy każdej aktualizacji tekstu.

- `min`, `max`: najmniejsza i największa liczba

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Max Number

**Identyfikator:** `maxnum`

Większa z dwóch liczb.

- `first`, `second`: liczby

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Min Number

**Identyfikator:** `minnum`

Mniejsza z dwóch liczb.

- `first`, `second`: liczby

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Absolute Number

**Identyfikator:** `absnum`

Liczba bez znaku minus, więc `-10.5` daje `10.5`.

- `num`: liczba

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Negate Number

**Identyfikator:** `negnum`

Zmienia liczbę dodatnią na ujemną, więc `10.5` daje `-10.5`. Zero i liczby ujemne pozostają bez zmian.

- `num`: liczba

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Round (Math)

**Identyfikator:** `math_round`

Zaokrągla liczbę. `2.5` jest zaokrąglane w górę do `3`.

- `num`: liczba
- `decimals` (opcjonalnie): liczba miejsc po przecinku. Wartość `2` zamienia `3.14159` na `3.14`. Wartość `0`, `-1` lub brak wartości zaokrągla do liczby całkowitej.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Floor (Math)

**Identyfikator:** `math_floor`

Zaokrągla liczbę w dół do liczby całkowitej, więc `3.7` daje `3`, a `-3.2` daje `-4`.

- `num`: liczba

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Ceiling (Math)

**Identyfikator:** `math_ceil`

Zaokrągla liczbę w górę do liczby całkowitej, więc `3.2` daje `4`, a `-3.7` daje `-3`.

- `num`: liczba

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Sign (Math)

**Identyfikator:** `math_sign`

Zwraca `1` dla liczb dodatnich, `-1` dla ujemnych i `0` dla zera.

- `num`: liczba

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Math)

**Identyfikator:** `math_pi`

Liczba π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Trigonometric Sine (Math)

**Identyfikator:** `math_sin`

Sinus kąta podanego w radianach. Aby użyć stopni, najpierw pomnóż je przez π / 180 za pomocą **Calculator**.

- `angle`: kąt w radianach

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Trigonometric Cosine (Math)

**Identyfikator:** `math_cos`

Cosinus kąta podanego w radianach.

- `angle`: kąt w radianach

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Trigonometric Tangent (Math)

**Identyfikator:** `math_tan`

Tangens kąta podanego w radianach.

- `angle`: kąt w radianach

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Hyperbolic Sine (Math)

**Identyfikator:** `math_sinh`

Sinus hiperboliczny liczby.

- `num`: liczba

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Hyperbolic Cosine (Math)

**Identyfikator:** `math_cosh`

Cosinus hiperboliczny liczby.

- `num`: liczba

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Hyperbolic Tangent (Math)

**Identyfikator:** `math_tanh`

Tangens hiperboliczny liczby.

- `num`: liczba

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Number Base Converter

**Identyfikator:** `number_base_convert`

Konwertuje liczbę na inny system liczbowy, na przykład z dziesiętnego na binarny lub szesnastkowy. Obsługuje też ułamki dziesiętne, maksymalnie 16 cyfr po kropce. Litery w wyniku są wielkie, na przykład `FF`.

- `input`: liczba
- `from_base` (opcjonalnie): podstawa systemu liczby `input`, od `2` do `36`. Domyślnie `10`.
- `to_base` (opcjonalnie): podstawa systemu wyniku, od `2` do `36`. Domyślnie `10`.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Tekst

Znajdują się w kategorii **Advanced**.

### Uppercase Text

**Identyfikator:** `uppercase_text`

Tekst zapisany wielkimi literami: `Hello World` daje `HELLO WORLD`. [Kody formatowania](/text-formatting), takie jak `&a`, pozostają bez zmian.

- `text`: tekst

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Lowercase Text

**Identyfikator:** `lowercase_text`

Tekst zapisany małymi literami: `HELLO WORLD` daje `hello world`. Kody formatowania pozostają bez zmian.

- `text`: tekst

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Title Case Text

**Identyfikator:** `title_case_text`

Każde słowo zaczyna się wielką literą: `hello world` daje `Hello World`. Kody formatowania pozostają bez zmian.

- `text`: tekst

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Sentence Case Text

**Identyfikator:** `sentence_case_text`

Każde zdanie zaczyna się wielką literą: `hello world. this is fancymenu!` daje `Hello world. This is fancymenu!`. Kody formatowania pozostają bez zmian.

- `text`: tekst

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Snake Case Text

**Identyfikator:** `snake_case_text`

Małe litery i znak `_` między słowami: `Hello World` daje `hello_world`. Kody formatowania są usuwane.

- `text`: tekst

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Kebab Case Text

**Identyfikator:** `kebab_case_text`

Małe litery i znak `-` między słowami: `Hello World` daje `hello-world`. Kody formatowania są usuwane.

- `text`: tekst

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Alternating Case Text

**Identyfikator:** `alternating_case_text`

Małe i wielkie litery występują naprzemiennie: `alternating case` daje `aLtErNaTiNg CaSe`.

- `text`: tekst

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Toggle Case Text

**Identyfikator:** `toggle_case_text`

Zamienia małe litery na wielkie, a wielkie na małe: `Toggle Case` daje `tOGGLE cASE`.

- `text`: tekst

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Trim Text

**Identyfikator:** `trim_text`

Usuwa spacje z początku i końca tekstu. Spacje w środku pozostają.

- `text`: tekst

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Crop Text

**Identyfikator:** `crop_text`

Usuwa określoną liczbę znaków z początku i końca tekstu. Z tekstu `hello world` po usunięciu jednego znaku z obu końców zostanie `ello worl`.

- `text`: tekst
- `remove_from_start`: liczba znaków do usunięcia z początku
- `remove_from_end`: liczba znaków do usunięcia z końca

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Split Text

**Identyfikator:** `split_text`

Dzieli tekst i zwraca jedną z jego części. Podział tekstu `Steve,Alex,Notch` przy znaku `,` zwróci `Alex` jako część o indeksie `1`.

- `input`: tekst
- `regex`: wyrażenie regularne określające miejsce podziału. Znaki takie jak `.`, `|` i `?` trzeba poprzedzić `\`, na przykład `\.`.
- `max_parts` (opcjonalnie): maksymalna liczba części. Domyślne `-1` dzieli tekst przy każdym dopasowaniu.
- `split_index`: indeks zwracanej części. Pierwsza część ma indeks `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Replace Text

**Identyfikator:** `replace_text`

Zastępuje fragmenty tekstu: w `Hello World!` zamiana `World` na `FancyMenu` daje `Hello FancyMenu!`.

- `text`: tekst
- `search`: wyszukiwany tekst
- `replacement` (opcjonalnie): tekst, którym należy go zastąpić. Domyślnie pusty, co usuwa znaleziony tekst.
- `use_regex` (opcjonalnie): `true` traktuje `search` jako wyrażenie regularne. W takim przypadku `$1`, `$2` i kolejne oznaczają grupy znalezione przez wyrażenie. Domyślnie `false`.
- `replace_all` (opcjonalnie): `false` zastępuje tylko pierwsze dopasowanie. Domyślnie `true`.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Switch Case

**Identyfikator:** `switch_case`

Zwraca wynik dla przypadku pasującego do podanej wartości. Jeśli zmienna `difficulty_level` ma wartość `2`, przykład zwróci `Hard Mode`.

- `value`: sprawdzana wartość
- `cases`: pary wartości i wyniku, na przykład `1:Easy Mode,2:Hard Mode`. Wartości i wyniki nie mogą zawierać `,` ani `:`.
- `default` (opcjonalnie): wynik zwracany, gdy żaden przypadek nie pasuje. Jeśli go nie podano, symbol zastępczy pozostaje bez zmian.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localize Text

**Identyfikator:** `local`

Tekst odpowiadający kluczowi lokalizacji w aktualnym języku gry, na przykład `Singleplayer` dla `menu.singleplayer`. Działa z kluczami Minecrafta, modów i własnymi kluczami (zobacz [Lokalizacja](/localization)).

- `key`: klucz lokalizacji

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Stringify

**Identyfikator:** `stringify`

Najpierw zastępuje symbole w tekście, a następnie wstawia `\` przed każdym znakiem `"`, `{` i `}`. Dzięki temu tekst z zewnętrznego źródła, na przykład strony internetowej, nie może zostać potraktowany jako symbole zastępcze.

- `text`: tekst

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Dane i pliki

Znajdują się w kategorii **Advanced**. Ścieżki lokalne zaczynają się w folderze gry, na przykład `/config/fancymenu/assets/news.txt`, i nie mogą prowadzić poza ten folder (zobacz [Zasoby](/resources#local-resources)).

### JSON Parser

**Identyfikator:** `json`

Odczytuje wartość z JSON-a. Jeśli wyniki jest kilka, każdy z nich pojawia się w osobnym wierszu.

- `source`: tekst JSON, plik JSON w folderze gry albo adres URL pliku JSON
- `json_path`: ścieżka do wartości, na przykład `$.name` lub `$.players[0].name`. Więcej informacji o ścieżkach JSON znajdziesz na stronie [json.fancymenu.net](https://json.fancymenu.net).

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

Dane JSON z internetu są wczytywane raz, a następnie ponownie po przeładowaniu FancyMenu. Zmiany w plikach są widoczne od razu.

| Ścieżka | Zwracana wartość |
|---|---|
| `$.name` | Wartość `name` na najwyższym poziomie |
| `$.player.level` | Wartość `level` w obiekcie `player` |
| `$.items[0].id` | Wartość `id` pierwszego elementu `items` |
| `$.scores.*` | Wszystkie wartości w obiekcie `scores` |

### File Text

**Identyfikator:** `file_text`

Tekst z pliku lub adresu URL. Pliki są odczytywane ponownie co sekundę, a adresy URL co 10 sekund. Podczas wczytywania tekstu lub gdy nie można go odczytać, symbol nie zwraca niczego.

- `path_or_url`: plik w folderze gry albo adres URL. Ścieżki zaczynające się od `.minecraft/` wskazują domyślny folder Minecrafta.
- `mode` (opcjonalnie): `all` zwraca cały tekst, a `last` — ostatnie wiersze. Domyślnie `all`.
- `separator` (opcjonalnie): tekst umieszczany między wierszami. Domyślnie `\n` (nowy wiersz).
- `last_lines` (opcjonalnie): liczba wierszy zwracanych przez tryb `last`. Domyślnie `1`.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### File Size

**Identyfikator:** `file_size`

Rozmiar pliku w bajtach. Zwraca `0`, jeśli plik nie istnieje. Ścieżki zaczynające się od `.minecraft/` wskazują domyślny folder Minecrafta.

- `path`: plik

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### File MD5

**Identyfikator:** `file_md5`

Skrót MD5 pliku, na przykład `d41d8cd98f00b204e9800998ecf8427e`. Jeśli plik nie istnieje, zwracany jest pusty tekst. Ścieżki zaczynające się od `.minecraft/` wskazują domyślny folder Minecrafta.

- `path`: plik

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Encode To Base64

**Identyfikator:** `base64_encode`

Tekst zakodowany w Base64: `Hello World` daje `SGVsbG8gV29ybGQ=`.

- `text`: tekst

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decode From Base64

**Identyfikator:** `base64_decode`

Dekoduje tekst z Base64: `SGVsbG8gV29ybGQ=` daje `Hello World`.

- `text`: tekst w Base64

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Get NBT Data (Client-Side)

**Identyfikator:** `nbt_data_get`

Odczytuje dane NBT, podobnie jak `/data get`, z tego, co gra wie o świecie. Działa szybko, ale serwery nie wysyłają graczom wszystkich danych.

- `source_type`: `entity` (byt) albo `block` (blok)
- `entity_selector`: dla `entity` selektor, taki jak `@s` (ty), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]` albo nazwa lub UUID bytu. Selektory mogą zawierać `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` i `dz`. Liczy się pierwsze dopasowanie.
- `block_pos`: dla `block` pozycja bloku będącego bytem, na przykład skrzyni: `120 64 -35`
- `nbt_path`: ścieżka NBT, na przykład `foodLevel` lub `Inventory[0].id`
- `scale` (opcjonalnie): mnożnik liczb. Domyślnie `1.0`.
- `return_type` (opcjonalnie): `value` (liczby i tekst bez zmian), `string`, `snbt` albo `json`. Domyślnie `value`.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Get NBT Data (Server-Side)

**Identyfikator:** `nbt_data_get_server`

Odczytuje dane NBT bezpośrednio z serwera, dokładnie tak jak `/data get`. Wymaga FancyMenu na serwerze. W trybie jednoosobowym zawsze działa. Nie zwraca niczego do czasu odpowiedzi serwera, a następnie aktualizuje dane mniej więcej co 100 milisekund.

- `source_type`: `entity` (byt), `block` (blok) albo `storage` (magazyn)
- `entity_selector`: dla `entity` dowolny selektor z `/data get`, który wybiera jeden byt, na przykład `@s` lub `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: dla `block` pozycja, na przykład `120 64 -35`, `~ ~-1 ~` lub `^ ^ ^1`
- `storage_id`: dla `storage` identyfikator magazynu danych komend, na przykład `mypack:quests`
- `nbt_path` (opcjonalnie): ścieżka NBT. Jeśli jej nie podasz, zwracane są wszystkie dane.
- `scale` (opcjonalnie): mnożnik liczb. Domyślnie `1.0`.
- `return_type` (opcjonalnie): `value`, `string`, `snbt` albo `json`. Domyślnie `value`.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Dźwięk

Odczytują [elementy Audio](/elements#audio) w otwartym menu. Aby skopiować identyfikator elementu Audio, kliknij go prawym przyciskiem myszy w edytorze układu i wybierz **Copy Element ID**.

### Audio Element Volume

**Identyfikator:** `audio_element_vol`

Głośność elementu Audio w zakresie od `0.0` (0%) do `1.0` (100%).

- `element_identifier`: identyfikator elementu Audio

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Current Audio Track

**Identyfikator:** `audio_element_current_track`

Nazwa pliku aktualnie odtwarzanego utworu, na przykład `menu_theme.ogg`. Gdy żaden utwór nie jest odtwarzany, zwraca `---`.

- `element_identifier`: identyfikator elementu Audio
- `display_name_mappings` (opcjonalnie): nazwy wyświetlane zamiast nazw plików. `=>` oddziela nazwę pliku od wyświetlanej nazwy, a `%:%` — poszczególne pary.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Audio Duration

**Identyfikator:** `audio_duration`

Długość aktualnego utworu, na przykład `03:45`. Podczas wczytywania zwraca `00:00`.

- `element_identifier`: identyfikator elementu Audio

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Audio Play Time

**Identyfikator:** `audio_playtime`

Pozycja w aktualnym utworze, na przykład `01:30`. Gdy utwór jest zatrzymany, zwraca `00:00` (lub `0`).

- `element_identifier`: identyfikator elementu Audio
- `show_percentage` (opcjonalnie): `true` zwraca zamiast tego postęp od `0` do `100`. Domyślnie `false`.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Audio Playing State

**Identyfikator:** `audio_playing_state`

Zwraca `true`, gdy element Audio odtwarza dźwięk, i `false`, gdy jest wstrzymany lub zatrzymany.

- `element_identifier`: identyfikator elementu Audio

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Klient

Informacje o grze i jej modach.

### Minecraft Version

**Identyfikator:** `mcversion`

Wersja Minecrafta, na przykład `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Mod Loader Name

**Identyfikator:** `loadername`

Nazwa loadera modów, na przykład `Fabric` lub `NeoForge`.

```
{"placeholder":"loadername"}
```

### Mod Loader Version

**Identyfikator:** `loaderver`

Wersja loadera modów, na przykład `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Mod Version

**Identyfikator:** `modversion`

Wersja zainstalowanego moda, na przykład `3.11.0`. Jeśli mod nie jest zainstalowany, zwraca `0.0.0`.

- `modid`: identyfikator moda, na przykład `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Active Mods Count

**Identyfikator:** `loadedmods`

Liczba wczytanych modów. Wliczane są też biblioteki i mody zawarte w innych modach, dlatego wynik często przewyższa liczbę plików modów.

```
{"placeholder":"loadedmods"}
```

### Total Mods Count

**Identyfikator:** `totalmods`

Przybliżona liczba zainstalowanych modów, obliczana na podstawie plików `.jar` w folderze `mods` raz na każde uruchomienie gry. Wynik nigdy nie jest niższy niż **Active Mods Count**.

```
{"placeholder":"totalmods"}
```

### World Loading Progress

**Identyfikator:** `world_load_progress`

Postęp wczytywania świata od `0` do `100`, wyświetlany podczas ekranu wczytywania. Przydaje się do pasków postępu. Na pozostałych ekranach zwraca `0`.

```
{"placeholder":"world_load_progress"}
```

### Minecraft Option Value

**Identyfikator:** `minecraft_option_value`

Wartość opcji Minecrafta zapisana w pliku `options.txt` w folderze gry, na przykład `12` dla `renderDistance`. Jeśli opcja o podanej nazwie nie istnieje, zwraca pusty tekst.

- `name`: nazwa opcji w pliku `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Keybind Key

**Identyfikator:** `keybind_key`

Aktualnie przypisany klawisz, taki jak na ekranie sterowania: na przykład `Space` dla skoku. Jeśli przypisanie o podanej nazwie nie istnieje, zwraca pusty tekst.

- `keybind`: nazwa przypisania, na przykład `key.jump` lub `key.inventory`. Nazwy są zapisane w `options.txt` bez początkowego `key_`: `key_key.jump` to `key.jump`.

```
Press {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} to open your inventory!
```

### Last World or Server

**Identyfikator:** `last_world_server`

Świat lub serwer, do którego gracz dołączył ostatnio. Serwery są wyświetlane jako `play.example.net:25565`.

- `type`: `both` oznacza światy i serwery, `world` — tylko światy, a `server` — tylko serwery. Przy wartości `world` lub `server` wynik jest pusty, jeśli ostatnio wybrano drugi typ.
- `full_world_path` (opcjonalnie): `false` zwraca tylko nazwę świata, na przykład `New World`. `true` zwraca ścieżkę do jego folderu. Domyślnie `true`.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## GUI

Informacje o otwartym ekranie i jego elementach. Symbole dotyczące elementów przyjmują identyfikator elementu. Kliknij element prawym przyciskiem myszy w edytorze układu i wybierz **Copy Element ID**.

### Screen Width

**Identyfikator:** `guiwidth`

Szerokość ekranu w pikselach GUI. Jest to rozmiar używany przez elementy, a nie liczba pikseli monitora.

```
{"placeholder":"guiwidth"}
```

### Screen Height

**Identyfikator:** `guiheight`

Wysokość ekranu w pikselach GUI.

```
{"placeholder":"guiheight"}
```

### GUI Scale

**Identyfikator:** `guiscale`

Skala GUI w grze, na przykład `2`.

```
{"placeholder":"guiscale"}
```

### Current Screen Identifier

**Identyfikator:** `screenid`

[Identyfikator](/screen-identifiers) otwartego ekranu, na przykład `title_screen`. Gdy żaden ekran nie jest otwarty, zwraca pusty tekst.

```
{"placeholder":"screenid"}
```

### Element Width

**Identyfikator:** `elementwidth`

Szerokość elementu w pikselach GUI. Jeśli nie ma elementu o podanym identyfikatorze, zwraca `1`.

- `id`: identyfikator elementu

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Height

**Identyfikator:** `elementheight`

Wysokość elementu w pikselach GUI. Jeśli nie ma elementu o podanym identyfikatorze, zwraca `1`.

- `id`: identyfikator elementu

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element X Position

**Identyfikator:** `elementposx`

Położenie lewej krawędzi elementu w pikselach GUI, liczone od lewej krawędzi ekranu. Jeśli nie ma elementu o podanym identyfikatorze, zwraca `1`.

- `id`: identyfikator elementu

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Y Position

**Identyfikator:** `elementposy`

Położenie górnej krawędzi elementu w pikselach GUI, liczone od górnej krawędzi ekranu. Jeśli nie ma elementu o podanym identyfikatorze, zwraca `1`.

- `id`: identyfikator elementu

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Text Element Content Height

**Identyfikator:** `text_element_content_height`

Wysokość potrzebna, aby element [Text](/text-in-menus) wyświetlił cały tekst bez przewijania, w pikselach GUI. Uwzględnia zawinięte wiersze, skalę tekstu i odstępy między wierszami, więc przydaje się do dopasowania tła do tekstu. Zwraca `0`, jeśli element nie jest typu Text.

- `element_identifier`: identyfikator elementu Text

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Element Scroll Position

**Identyfikator:** `scroll_area_scroll_position`

Pozycja przewinięcia zawartości [Scrollable Area](/scrollable-areas) lub elementu Text, w pikselach GUI liczonych od początku. Dla innych elementów zwraca `0`.

- `element_identifier`: identyfikator elementu
- `axis`: `vertical` (pionowa) lub `horizontal` (pozioma). Każda inna wartość oznacza kierunek przewijania elementu.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Percent

**Identyfikator:** `scroll_area_scroll_percent`

Pozycja przewinięcia zawartości Scrollable Area lub elementu Text w zakresie od `0` (początek) do `100` (koniec). Dla innych elementów oraz gdy nie ma czego przewijać, zwraca `0`.

- `element_identifier`: identyfikator elementu
- `axis`: `vertical` (pionowa) lub `horizontal` (pozioma). Każda inna wartość oznacza kierunek przewijania elementu.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Element Scroll Content Size

**Identyfikator:** `scroll_area_content_size`

Rozmiar zawartości Scrollable Area lub elementu Text: wysokość przy `vertical`, a szerokość przy `horizontal`. Dla innych elementów zwraca `0`.

- `element_identifier`: identyfikator elementu
- `axis`: `vertical` (pionowa) lub `horizontal` (pozioma). Każda inna wartość oznacza kierunek przewijania elementu.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Text Input Field Value

**Identyfikator:** `text_input_field_value`

Tekst wpisany w [pole tekstowe](/elements#text-input-field) lub w pole tekstowe oryginalnego ekranu. Jeśli element nie jest polem tekstowym, zwraca pusty tekst.

- `element_identifier`: identyfikator elementu

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Vanilla Widget Label/Text

**Identyfikator:** `vanillabuttonlabel`

Etykieta przycisku lub innego widżetu z oryginalnego ekranu, na przykład `Options...`. Aby skopiować lokalizator widżetu, kliknij go prawym przyciskiem myszy w edytorze układu i wybierz **Copy Widget Locator**.

- `locator`: lokalizator widżetu

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Mouse X Position

**Identyfikator:** `mouseposx`

Położenie myszy w pikselach GUI, liczone od lewej krawędzi ekranu. W edytorze układu zawsze zwraca `10`, dzięki czemu elementy podążające za kursorem pozostają w miejscu, w którym można je edytować.

```
{"placeholder":"mouseposx"}
```

### Mouse Y Position

**Identyfikator:** `mouseposy`

Położenie myszy w pikselach GUI, liczone od górnej krawędzi ekranu. W edytorze układu zawsze zwraca `10`.

```
{"placeholder":"mouseposy"}
```

### Clicks Per Second

**Identyfikator:** `clicks_per_second`

Liczba kliknięć przycisku myszy w ciągu ostatniej sekundy.

- `mouse_button` (opcjonalnie): `left` (lewy) lub `right` (prawy). Domyślnie `left`.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Gracz

### Player Name

**Identyfikator:** `playername`

Nazwa gracza, na przykład `Steve`.

```
{"placeholder":"playername"}
```

### Player UUID

**Identyfikator:** `playeruuid`

UUID gracza, na przykład `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Last Death Message

**Identyfikator:** `lastdeathmessage`

Ostatni komunikat o śmierci gracza od uruchomienia gry, na przykład `Steve was slain by Zombie`. Przed pierwszą śmiercią zwraca pusty tekst.

- `as_json_component` (opcjonalnie): `true` zwraca komunikat jako komponent tekstowy JSON wraz z kolorami. Domyślnie `false`.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Czas rzeczywisty

Informacje o czasie na komputerze. Symbole dotyczące daty i godziny przyjmują opcjonalną wartość `timezone`: `system` oznacza strefę czasową komputera (ustawienie domyślne), można też podać identyfikator, na przykład `UTC`, `Europe/Berlin` lub `America/New_York`. Lista wszystkich identyfikatorów znajduje się na stronie [nodatime.org/TimeZones](https://nodatime.org/TimeZones).

### Realtime Year

**Identyfikator:** `realtimeyear`

Rok, na przykład `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Realtime Month

**Identyfikator:** `realtimemonth`

Miesiąc w zakresie od `01` do `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Realtime Day

**Identyfikator:** `realtimeday`

Dzień miesiąca w zakresie od `01` do `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Realtime Hour

**Identyfikator:** `realtimehour`

Godzina w zakresie od `00` do `23`.

- `twelve_hour_format` (opcjonalnie): `true` zwraca zamiast tego wartości od `01` do `12`. Domyślnie `false`.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Realtime Minute

**Identyfikator:** `realtimeminute`

Minuta w zakresie od `00` do `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Realtime Second

**Identyfikator:** `realtimesecond`

Sekunda w zakresie od `00` do `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Current Time in Millis (Unix Timestamp)

**Identyfikator:** `unix_time`

Liczba milisekund od 1 stycznia 1970 r. (UTC), na przykład `1732456789012`. Przydatna do tworzenia liczników czasu: zapisz wartość w zmiennej, a następnie odejmij ją w **Calculator** od późniejszej wartości.

```
{"placeholder":"unix_time"}
```

## Serwer

Symbole sprawdzają status serwera podobnie jak lista serwerów. Gdy otwarty jest ekran z własnym układem, FancyMenu wysyła zapytanie co 30 sekund. Do otrzymania pierwszej odpowiedzi serwer jest traktowany jako offline.

- `ip`: adres serwera, z portem, jeśli nie jest to port domyślny, na przykład `play.example.net` lub `play.example.net:25566`

### Server Status

**Identyfikator:** `serverstatus`

Zwraca `Online` na zielono albo `Offline` na czerwono.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Server Player Count

**Identyfikator:** `serverplayercount`

Liczba graczy online i maksymalna liczba graczy, na przykład `12/100`. Do czasu odpowiedzi serwera zwraca `0/0`.

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### Server MOTD

**Identyfikator:** `servermotd`

Jeden wiersz wiadomości dnia serwera.

- `line`: `1` lub `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Server PING

**Identyfikator:** `serverping`

Ping serwera w milisekundach, na przykład `54`. Gdy serwer jest offline, zwraca `-1`.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Server Version

**Identyfikator:** `serverversion`

Wersja Minecrafta na serwerze, na przykład `1.21.1`. Niektóre serwery wyświetlają tu własny tekst. Do czasu odpowiedzi serwera zwraca `---`.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Wideo

Odczytują informacje z [elementów Video i wideo w tle menu](/video) w otwartym menu. W przypadku elementu Video kliknij go prawym przyciskiem myszy w edytorze układu i wybierz **Copy Element ID**. W przypadku tła kliknij prawym przyciskiem myszy tło edytora i wybierz **Copy Background Identifier**.

### Video Element Volume

**Identyfikator:** `video_element_vol`

Głośność elementu Video w zakresie od `0.0` (0%) do `1.0` (100%).

- `element_identifier`: identyfikator elementu Video

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Element Duration

**Identyfikator:** `video_element_duration`

Długość wideo elementu Video, na przykład `02:00`. Podczas wczytywania zwraca `00:00` (lub `0`).

- `element_identifier`: identyfikator elementu Video
- `output_as_timestamp` (opcjonalnie): `true` zwraca zamiast tego liczbę milisekund, na przykład `120000`. Domyślnie `false`.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Video Element Play Time

**Identyfikator:** `video_element_playtime`

Pozycja w wideo elementu Video, na przykład `00:45`. Podczas wczytywania zwraca `00:00` (lub `0`).

- `element_identifier`: identyfikator elementu Video
- `show_percentage` (opcjonalnie): `true` zwraca postęp od `0` do `100`. Domyślnie `false`.
- `output_as_timestamp` (opcjonalnie): `true` zwraca liczbę milisekund. Jeśli obie opcje mają wartość `true`, pierwszeństwo ma `show_percentage`. Domyślnie `false`.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Video Element Paused State

**Identyfikator:** `video_element_paused_state`

Zwraca `true`, gdy wideo elementu Video jest wstrzymane, a w pozostałych przypadkach `false`.

- `element_identifier`: identyfikator elementu Video

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Video Background Volume

**Identyfikator:** `video_background_vol`

Głośność wideo w tle menu w zakresie od `0.0` (0%) do `1.0` (100%).

- `background_identifier`: identyfikator tła menu

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Video Background Duration

**Identyfikator:** `video_background_duration`

Długość wideo w tle menu, na przykład `03:00`. Podczas wczytywania zwraca `00:00` (lub `0`).

- `background_identifier`: identyfikator tła menu
- `output_as_timestamp` (opcjonalnie): `true` zwraca zamiast tego liczbę milisekund. Domyślnie `false`.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Video Background Play Time

**Identyfikator:** `video_background_playtime`

Pozycja w wideo stanowiącym tło menu, na przykład `01:00`. Podczas wczytywania zwraca `00:00` (lub `0`).

- `background_identifier`: identyfikator tła menu
- `show_percentage` (opcjonalnie): `true` zwraca postęp od `0` do `100`. Domyślnie `false`.
- `output_as_timestamp` (opcjonalnie): `true` zwraca liczbę milisekund. Jeśli obie opcje mają wartość `true`, pierwszeństwo ma `show_percentage`. Domyślnie `false`.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Video Background Paused State

**Identyfikator:** `video_background_paused_state`

Zwraca `true`, gdy wideo w tle menu jest wstrzymane, a w pozostałych przypadkach `false`.

- `background_identifier`: identyfikator tła menu

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## Świat: statystyki gracza

Kategoria **World** dotyczy świata, w którym grasz. Większość jej symboli wymaga wczytanego świata. Poza nim zwracają `0`, `0.0` albo pusty tekst.

### Current Player Health

**Identyfikator:** `current_player_health`

Zdrowie gracza, na przykład `20.0`. Każde serce odpowiada wartości `2.0`.

```
{"placeholder":"current_player_health"}
```

### Max Player Health

**Identyfikator:** `max_player_health`

Maksymalne zdrowie gracza, na przykład `20.0`.

```
{"placeholder":"max_player_health"}
```

### Current Player Health (Percent)

**Identyfikator:** `current_player_health_percent`

Zdrowie gracza w procentach, od `0` do `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Current Player Absorption Health

**Identyfikator:** `current_player_absorption_health`

Punkty absorpcji gracza (złote serca), na przykład `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Max Player Absorption Health

**Identyfikator:** `max_player_absorption_health`

Maksymalna liczba punktów absorpcji gracza, na przykład `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Current Player Absorption Health (Percent)

**Identyfikator:** `current_player_absorption_health_percent`

Punkty absorpcji gracza w procentach, od `0` do `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Current Player Food Level

**Identyfikator:** `current_player_hunger`

Poziom głodu gracza w zakresie od `0.0` do `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Max Player Food Level

**Identyfikator:** `max_player_hunger`

Maksymalny poziom głodu gracza, zawsze `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Current Player Food Level (Percent)

**Identyfikator:** `current_player_hunger_percent`

Poziom głodu gracza w procentach, od `0` do `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Current Player Hunger Saturation

**Identyfikator:** `current_player_hunger_saturation`

Nasycenie gracza, na przykład `5.0`. Poziom głodu zaczyna spadać dopiero po wyczerpaniu nasycenia.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Current Player Armor

**Identyfikator:** `current_player_armor`

Punkty pancerza gracza w zakresie od `0.0` do `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Max Player Armor

**Identyfikator:** `max_player_armor`

Maksymalna liczba punktów na pasku pancerza, zawsze `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Current Player Armor (Percent)

**Identyfikator:** `current_player_armor_percent`

Punkty pancerza gracza w procentach, od `0` do `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Player Armor Toughness

**Identyfikator:** `player_armor_toughness`

Wytrzymałość pancerza gracza, na przykład `8.0` przy pełnym diamentowym pancerzu.

```
{"placeholder":"player_armor_toughness"}
```

### Current Player Oxygen Level

**Identyfikator:** `current_player_oxygen`

Ilość powietrza gracza pod wodą w zakresie od `0.0` do `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Max Player Oxygen Level

**Identyfikator:** `max_player_oxygen`

Maksymalna ilość powietrza gracza, na przykład `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Current Player Oxygen Level (Percent)

**Identyfikator:** `current_player_oxygen_percent`

Ilość powietrza gracza w procentach, od `0` do `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Current Player Level

**Identyfikator:** `current_player_level`

Poziom doświadczenia gracza, na przykład `30`.

```
{"placeholder":"current_player_level"}
```

### Current Player Experience

**Identyfikator:** `current_player_exp`

Łączna liczba punktów doświadczenia gracza, na przykład `1395.0`. Nie jest to poziom.

```
{"placeholder":"current_player_exp"}
```

### Player Experience Progress (Percent)

**Identyfikator:** `current_player_exp_progress`

Stopień zapełnienia paska doświadczenia w zakresie od `0` do `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Player Attack Strength (Percent)

**Identyfikator:** `player_attack_strength`

Stopień naładowania następnego ataku w zakresie od `0` do `100`, tak jak na wskaźniku ataku.

```
{"placeholder":"player_attack_strength"}
```

### Player Game Mode

**Identyfikator:** `player_gamemode`

Zwraca `survival`, `creative`, `adventure` albo `spectator`.

```
{"placeholder":"player_gamemode"}
```

### Player Item Use Progress (FM)

**Identyfikator:** `player_item_use_progress_fm`

Postęp używania przedmiotu przez gracza, na przykład jedzenia, picia lub naciągania łuku, w zakresie od `0.0` do `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Current Mount Health

**Identyfikator:** `current_mount_health`

Zdrowie dosiadanego przez gracza moba, na przykład konia, w formacie `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Max Mount Health

**Identyfikator:** `max_mount_health`

Maksymalne zdrowie dosiadanego przez gracza moba.

```
{"placeholder":"max_mount_health"}
```

### Current Mount Health (Percent)

**Identyfikator:** `current_mount_health_percent`

Zdrowie dosiadanego przez gracza moba w procentach, od `0` do `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Current Mount Jump Meter (Percent)

**Identyfikator:** `current_mount_jump_meter`

Stopień naładowania skoku konia w zakresie od `0` do `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Active Effects Count

**Identyfikator:** `effects_count`

Liczba efektów działających obecnie na gracza.

```
{"placeholder":"effects_count"}
```

### Active Effect

**Identyfikator:** `active_effect`

Identyfikator efektu działającego na gracza, na przykład `minecraft:speed`, w kolejności ikon efektów w prawym górnym rogu. Jeśli pod danym indeksem nie ma efektu, zwraca pusty tekst.

- `effect_index`: pozycja efektu. Pierwszy ma indeks `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## Świat: ekwipunek i przedmioty

Znajdują się w kategorii **World**. Numery miejsc: `0`–`8` to pasek szybkiego dostępu, `9`–`35` to pozostała część ekwipunku, `36`–`39` to elementy pancerza od butów do hełmu, a `40` to druga ręka.

### Selected Hotbar Slot

**Identyfikator:** `active_hotbar_slot`

Wybrane miejsce na pasku szybkiego dostępu, od `0` do `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Slot Item

**Identyfikator:** `slot_item`

Identyfikator przedmiotu w danym miejscu, na przykład `minecraft:diamond_sword`. Puste miejsca zwracają `minecraft:air`.

- `slot`: numer miejsca

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Slot Item Count

**Identyfikator:** `slot_item_count`

Liczba przedmiotów w danym miejscu, na przykład `64`.

- `slot`: numer miejsca

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Slot Item Durability

**Identyfikator:** `slot_item_durability`

Wytrzymałość przedmiotu w danym miejscu. Dla przedmiotów bez wytrzymałości zwraca `0`.

- `slot`: numer miejsca
- `format` (opcjonalnie): `current` (pozostała wytrzymałość), `max` (maksymalna), `damage` (utracona wytrzymałość) albo `percentage` (pozostała wartość w procentach, od `0` do `100`). Domyślnie `current`.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Slot Item Display Name (FM)

**Identyfikator:** `slot_item_display_name_fm`

Nazwa przedmiotu w danym miejscu jako komponent tekstowy JSON z kolorem odpowiadającym rzadkości, na przykład `{"text":"Diamond Sword","color":"aqua"}`. W trybie obserwatora miejsca paska szybkiego dostępu zwracają nazwy elementów menu obserwatora.

- `slot`: numer miejsca
- `ignore_spectator` (opcjonalnie): `true` zwraca również nazwy przedmiotów w trybie obserwatora. Domyślnie `false`.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Inventory Item Count

**Identyfikator:** `inventory_item_count`

Liczba przedmiotów danego typu w całym ekwipunku gracza.

- `item`: identyfikator przedmiotu, na przykład `minecraft:diamond`. Pusta wartość oznacza zliczanie wszystkich przedmiotów.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Inventory Slot Food Point Restore Amount

**Identyfikator:** `inventory_slot_food_point_restore_amount`

Liczba punktów głodu przywracanych przez zjedzenie przedmiotu w danym miejscu, na przykład `4.0` dla jabłka. Przedmioty niejadalne zwracają `0.0`.

- `slot`: numer miejsca

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Item Category

**Identyfikator:** `item_category`

Karta ekwipunku trybu kreatywnego, w której znajduje się przedmiot, na przykład `Combat`. W przypadku przedmiotów bez karty zwraca `UNKNOWN`.

- `item`: identyfikator przedmiotu
- `as_key` (opcjonalnie): `true` zwraca identyfikator karty, na przykład `minecraft:combat`. Domyślnie `false`.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Hovered Inventory Item

**Identyfikator:** `hovered_inventory_item`

Identyfikator przedmiotu wskazywanego kursorem na ekranie ekwipunku, na przykład `minecraft:apple`. Jeśli żaden przedmiot nie jest wskazywany, zwraca pusty tekst.

```
{"placeholder":"hovered_inventory_item"}
```

## Świat: HUD i bossowie

Znajdują się w kategorii **World**. Symbole dotyczące najazdów odczytują najazd, którego pasek jest widoczny u góry ekranu, i wymagają FancyMenu na serwerze. W trybie jednoosobowym zawsze działają. Jeśli nie trwa najazd, zwracają `0` albo pusty tekst.

### Action Bar Message (FM)

**Identyfikator:** `action_bar_message_fm`

Wiadomość nad paskiem szybkiego dostępu jako komponent tekstowy JSON, na przykład `{"text":"You may not rest now","color":"red"}`. Jeśli nie ma wiadomości, zwraca pusty tekst.

```
{"placeholder":"action_bar_message_fm"}
```

### Action Bar Message Time (FM)

**Identyfikator:** `action_bar_message_time_fm`

Liczba tików, przez które wiadomość nad paskiem szybkiego dostępu będzie jeszcze widoczna. 20 tików to jedna sekunda.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Highlighted Item Time (FM)

**Identyfikator:** `highlighted_item_time_fm`

Liczba tików, przez które nazwa wybranego przedmiotu będzie jeszcze widoczna nad paskiem szybkiego dostępu.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Current HUD Title/Subtitle

**Identyfikator:** `current_title`

Aktualnie wyświetlany tytuł lub podtytuł, na przykład ustawiony poleceniem `/title`. Jeśli nie ma żadnego, zwraca pusty tekst.

- `is_subtitle` (opcjonalnie): `true` zwraca podtytuł. Domyślnie `false`.
- `as_json` (opcjonalnie): `true` zwraca wynik jako komponent tekstowy JSON. Domyślnie `false`.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Bosses Count

**Identyfikator:** `boss_count`

Liczba aktualnie widocznych pasków bossów.

```
{"placeholder":"boss_count"}
```

### Boss Name

**Identyfikator:** `boss_name`

Nazwa paska bossa, na przykład `Ender Dragon`. Jeśli pod danym indeksem nie ma paska bossa, zwraca pusty tekst.

- `boss_index`: pozycja paska bossa. Górny pasek ma indeks `0`.
- `as_json` (opcjonalnie): `true` zwraca nazwę jako komponent tekstowy JSON. Domyślnie `false`.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Current Boss Health (Percent)

**Identyfikator:** `current_boss_health`

Stopień zapełnienia paska bossa w zakresie od `0` do `100`.

- `boss_index`: pozycja paska bossa. Górny pasek ma indeks `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Total Active Raid Waves

**Identyfikator:** `active_raid_total_waves`

Liczba fal najazdu wraz z dodatkową falą.

```
{"placeholder":"active_raid_total_waves"}
```

### Remaining Active Raid Waves

**Identyfikator:** `active_raid_remaining_waves`

Liczba fal najazdu, które jeszcze się nie rozpoczęły.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Current Active Raid Wave

**Identyfikator:** `active_raid_current_wave`

Numer ostatniej fali, czyli `1`, gdy atakuje pierwsza fala. Przed pierwszą falą zwraca `0`.

```
Wave {"placeholder":"active_raid_current_wave"} of {"placeholder":"active_raid_total_waves"}
```

### Active Raid Alive Raiders Count

**Identyfikator:** `active_raid_alive_raiders_count`

Liczba najeźdźców z najazdu, którzy nadal żyją.

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Active Raid Alive Raiders List

**Identyfikator:** `active_raid_alive_raiders_list`

Lista wszystkich żyjących najeźdźców rozdzielonych przecinkami. Każdy element zawiera identyfikator moba i UUID najeźdźcy, na przykład `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`.

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## Świat: pozycja i kamera

Znajdują się w kategorii **World**.

### Player X Coordinate

**Identyfikator:** `player_x_coordinate`

Współrzędna X bloku, w którym stoi gracz, na przykład `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Player Y Coordinate

**Identyfikator:** `player_y_coordinate`

Współrzędna Y bloku, w którym stoi gracz, na przykład `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Player Z Coordinate

**Identyfikator:** `player_z_coordinate`

Współrzędna Z bloku, w którym stoi gracz, na przykład `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Player View Direction

**Identyfikator:** `player_view_direction`

Kierunek, w którym patrzy gracz: `north`, `east`, `south` albo `west`.

```
{"placeholder":"player_view_direction"}
```

### Player Position Delta X (FM)

**Identyfikator:** `player_position_delta_x_fm`

Odległość przebytą przez gracza wzdłuż osi X od poprzedniego tiku, w blokach, na przykład `0.12`. Wartość jest ujemna, jeśli gracz porusza się w przeciwnym kierunku.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Player Position Delta Y (FM)

**Identyfikator:** `player_position_delta_y_fm`

Odległość przebytą przez gracza wzdłuż osi Y od poprzedniego tiku, na przykład `-0.08` podczas spadania.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Player Position Delta Z (FM)

**Identyfikator:** `player_position_delta_z_fm`

Odległość przebytą przez gracza wzdłuż osi Z od poprzedniego tiku.

```
{"placeholder":"player_position_delta_z_fm"}
```

### Camera Rotation X (FM)

**Identyfikator:** `camera_rotation_x_fm`

Kąt, pod jakim kamera jest skierowana w górę lub w dół, w stopniach od `-90.0` (prosto w górę) do `90.0` (prosto w dół).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Camera Rotation Y (FM)

**Identyfikator:** `camera_rotation_y_fm`

Kierunek, w którym skierowana jest kamera, w stopniach od `-180.0` do `180.0`. `0.0` oznacza południe.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Camera Rotation Delta X (FM)

**Identyfikator:** `camera_rotation_delta_x_fm`

O ile stopni kamera obróciła się w górę lub w dół od poprzedniego tiku.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Camera Rotation Delta Y (FM)

**Identyfikator:** `camera_rotation_delta_y_fm`

O ile stopni kamera obróciła się w lewo lub w prawo od poprzedniego tiku.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## Świat: informacje o świecie

Znajdują się w kategorii **World**.

### World Day Time

**Identyfikator:** `world_daytime`

Pora dnia w świecie wyrażona w tikach. Doba trwa 24000 tików i zaczyna się o 6:00 rano. Licznik nie zeruje się między dniami, więc użycie `{"placeholder":"world_daytime"} % 24000` w **Calculator** pozwala uzyskać godzinę bieżącego dnia.

```
{"placeholder":"world_daytime"}
```

### World Day Time Hour

**Identyfikator:** `world_daytime_hour`

Godzina w świecie w zakresie od `00` do `23`.

- `twelve_hour_format` (opcjonalnie): `true` zwraca zamiast tego wartości od `01` do `12`. Domyślnie `false`.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### World Day Time Minute

**Identyfikator:** `world_daytime_minute`

Minuta w świecie w zakresie od `00` do `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### World Game Time

**Identyfikator:** `game_time`

Łączna liczba tików, przez które działał świat. W przeciwieństwie do pory dnia nie zmienia się po użyciu poleceń takich jak `/time set`.

```
{"placeholder":"game_time"}
```

### World Difficulty

**Identyfikator:** `world_difficulty`

Zwraca `peaceful`, `easy`, `normal` albo `hard`.

```
{"placeholder":"world_difficulty"}
```

### Current Dimension

**Identyfikator:** `current_dimension`

Wymiar, w którym znajduje się gracz, na przykład `minecraft:overworld`.

- `as_key` (opcjonalnie): `false` zwraca nazwę, na przykład `Overworld`. Jeśli wymiar nie ma nazwy, zwraca jego identyfikator. Domyślnie `true`.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Current Biome

**Identyfikator:** `current_biome`

Biom, w którym znajduje się gracz, na przykład `minecraft:plains`.

- `as_key` (opcjonalnie): `false` zwraca nazwę, na przykład `Plains`. Domyślnie `true`.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Current World Seed

**Identyfikator:** `current_world_seed`

Ziarno świata jednoosobowego, na przykład `-4172144997902289642`. Na serwerach zwraca pusty tekst.

```
{"placeholder":"current_world_seed"}
```

### Gamerule Value

**Identyfikator:** `gamerule_value`

Wartość reguły gry, na przykład `true` lub `3`. W trybie jednoosobowym symbol zawsze działa. Na serwerach wymaga FancyMenu po stronie serwera. Jeśli reguła o podanej nazwie nie istnieje, zwraca pusty tekst.

- `name`: nazwa reguły gry, na przykład `keep_inventory`. W Minecraft 1.21.10 i starszych wersjach reguły mają nazwy takie jak `keepInventory`; te starsze nazwy działają również w nowszych wersjach.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### Current Server IP

**Identyfikator:** `current_server_ip`

Adres serwera, na którym gra gracz, na przykład `play.example.net`. W trybie jednoosobowym zwraca pusty tekst.

```
{"placeholder":"current_server_ip"}
```

### World Players List

**Identyfikator:** `world_players_list`

Nazwy graczy w świecie, o których wie gra, posortowane alfabetycznie, na przykład `Alex, Notch, Steve`.

- `separator` (opcjonalnie): tekst rozdzielający nazwy. Domyślnie `, `.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## Świat: zapisane światy

Znajdują się w kategorii **World** i działają w każdym menu, nawet jeśli żaden świat nie jest wczytany.

### World Save Count

**Identyfikator:** `level_save_count`

Liczba światów jednoosobowych.

```
{"placeholder":"level_save_count"}
```

### World Save Names

**Identyfikator:** `level_save_names`

Nazwy wszystkich światów jednoosobowych w kolejności z listy światów, na przykład `Survival World, Creative Test`.

- `separator` (opcjonalnie): tekst rozdzielający nazwy. Domyślnie `, `.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### World Save Data

**Identyfikator:** `level_save_data`

Wszystkie dane świata jednoosobowego jako JSON, na przykład `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`. Zawiera między innymi pola `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (jako znacznik czasu Unix) i `minecraft_version_name`. Pojedyncze wartości można odczytywać za pomocą [**JSON Parser**](#json-parser).

- `level_name`: nazwa świata dokładnie taka, jak na liście światów

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## Inne

Te symbole nie mają kategorii, dlatego menu symboli zastępczych wyświetla je poniżej listy kategorii.

### FPS (Frames Per Second)

**Identyfikator:** `fps`

Liczba klatek na sekundę, na przykład `120`.

```
{"placeholder":"fps"}
```

### Used RAM in MB

**Identyfikator:** `usedram`

Aktualna ilość pamięci RAM używana przez grę w MB, na przykład `4096`.

```
{"placeholder":"usedram"}
```

### Max RAM in MB

**Identyfikator:** `maxram`

Maksymalna ilość pamięci RAM, której może użyć gra, w MB, na przykład `8192`.

```
{"placeholder":"maxram"}
```

### Used RAM in %

**Identyfikator:** `percentram`

Używana przez grę pamięć RAM jako procent maksymalnej ilości, na przykład `50`.

```
{"placeholder":"percentram"}
```

### CPU Usage (JVM)

**Identyfikator:** `jvmcpu`

Procent mocy procesora używany przez grę, na przykład `25.5`.

```
{"placeholder":"jvmcpu"}
```

### CPU Usage (OS)

**Identyfikator:** `oscpu`

Procent mocy procesora używany przez cały komputer, na przykład `42.8`.

```
{"placeholder":"oscpu"}
```

### CPU Info

**Identyfikator:** `cpuinfo`

Nazwa procesora, na przykład `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### GPU Info

**Identyfikator:** `gpuinfo`

Nazwa urządzenia graficznego używanego przez grę, na przykład `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### OpenGL Version

**Identyfikator:** `glver`

Informacje o sterowniku urządzenia graficznego używanego przez grę, na przykład `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Java Version

**Identyfikator:** `javaver`

Wersja Javy, na której działa gra, na przykład `21.0.5`.

```
{"placeholder":"javaver"}
```

### Java Virtual Machine

**Identyfikator:** `jvmname`

Nazwa wirtualnej maszyny Javy, na przykład `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Operating System Name

**Identyfikator:** `osname`

Nazwa systemu operacyjnego, na przykład `Windows 11`.

```
{"placeholder":"osname"}
```

### Uptime Duration

**Identyfikator:** `uptime_duration`

Czas działania gry w sekundach, na przykład `742`.

- `output_as_millis` (opcjonalnie): `true` zwraca zamiast tego milisekundy. Domyślnie `false`.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Random Text

**Identyfikator:** `randomtext`

Losowy wiersz z pliku tekstowego, strony internetowej lub wpisanego tekstu, na przykład losowa wskazówka. Pliki i strony są odczytywane ponownie co 30 sekund.

- `source`: plik `.txt` w folderze gry, adres URL albo wiersze rozdzielone przez `\n`, na przykład `Tip 1\nTip 2\nTip 3`
- `interval` (opcjonalnie): po ilu sekundach ma zostać wybrany nowy wiersz. Wartość `0` wybiera jeden wiersz na sesję gry. Domyślnie `10`.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Web Text

**Identyfikator:** `webtext`

Pierwszy wiersz tekstu ze strony internetowej, na przykład pliku tekstowego na własnej stronie. Jest wczytywany raz, a następnie ponownie po przeładowaniu FancyMenu. Podczas wczytywania zwraca pusty tekst.

- `link`: adres URL strony

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Absolute File/Folder Path

**Identyfikator:** `absolute_path`

Pełna ścieżka do pliku lub folderu w folderze gry, na przykład `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: ścieżka w obrębie folderu gry

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Text Character Count

**Identyfikator:** `text_character_count`

Liczba znaków w tekście: `Hello World!` ma ich `12`.

- `text`: tekst

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Text Width

**Identyfikator:** `text_width`

Szerokość tekstu w pikselach GUI: `Hello World!` ma szerokość `57`. Kody formatowania, takie jak `&l`, są uwzględniane tak samo jak w grze, dlatego pogrubiony tekst jest szerszy.

- `text`: tekst

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Text Height

**Identyfikator:** `text_height`

Wysokość tekstu w pikselach GUI, z uwzględnieniem wszystkich wierszy. Nowy wiersz zapisuje się jako `\n`. Aby dopasować wysokość do elementu Text, użyj [**Text Element Content Height**](#text-element-content-height), który uwzględnia także skalę tekstu, odstępy między wierszami i zawijanie wierszy.

- `text`: tekst

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Clipboard Content

**Identyfikator:** `clipboard_content`

Tekst ze schowka komputera. Jeśli schowek jest pusty, zwraca pusty tekst.

```
{"placeholder":"clipboard_content"}
```
