---
title: Warunki (Wymagania)
description: Jak używać wymagań ładowania.
---

# Wymagania
Wymagania (czyli „wymagania ładowania”) pozwalają sprawiać, że części twoich układów są widoczne lub niewidoczne w zależności od różnych warunków, takich jak to, czy element jest pod kursorem, czy okno ma określony rozmiar albo czy aktualnie znajdujesz się w świecie.

Mogą być także używane w skryptach akcji przycisków, suwaków, tickerów i wszystkiego innego, co ma pole wejściowe skryptu akcji.

# Dodawanie wymagań do elementów
Aby dodać jedno lub więcej wymagań do elementów, po prostu kliknij element prawym przyciskiem myszy i wybierz **Wymagania ładowania**.

# Wymagania dla całego układu
Możesz również zmieniać widoczność całych układów, klikając prawym przyciskiem myszy **tło edytora**, a następnie wybierając **Wymagania ładowania [dla całego układu]**.

# Skrypty akcji
Wymagania można też używać w skryptach akcji.
Możesz dodać je w ekranie edytora skryptu akcji i używać do wykonywania określonych działań tylko wtedy, gdy warunek wymagania jest spełniony.

# Wartości wymagań
Niektóre wymagania wymagają ustawienia określonych wartości, aby działały poprawnie. Jeśli tak jest, ekran wymagania powinien poinformować cię, aby najpierw ustawić wszystkie wartości, ale jeśli nie, sprawdź po prostu, czy przycisk **Edytuj wartość wymagania** jest klikalny podczas dodawania wymagania.
Zawsze sprawdzaj opis wymagania, jeśli nie masz pewności, co ustawić jako wartość.
Niektóre pola wartości obsługują nawet **autouzupełnianie TAB**.

W FancyMenu 3.9.0 okno Zarządzaj wymaganiami zostało przebudowane tak, aby używało menu kontekstowego po kliknięciu prawym przyciskiem myszy, nawigacji klawiaturą, wyszukiwania, cofania/ponawiania (`CTRL + Z` / `CTRL + Y`) oraz `CTRL + S` jako skrótu **Gotowe**.

# Wymagania w szczegółach
Poniższa lista zawiera większość, jeśli nie wszystkie, wymagania dostępne w FancyMenu. Możliwe, że lista bywa czasem nieco nieaktualna z powodu aktualizacji moda.

## Czy element jest pod kursorem
Sprawdza, czy konkretny element znajduje się pod kursorem myszy.  
**Wymagana wartość**: Tak - ID elementu docelowego (np. `some_element_ID`). ID można uzyskać, klikając element prawym przyciskiem myszy w edytorze.

## Czy element ma fokus
Sprawdza, czy konkretny element ma obecnie fokus klawiatury (na przykład pole tekstowe lub przycisk z fokusem).
**Wymagana wartość**: Tak - ID elementu docelowego (to samo ID widoczne w edytorze)

> To nie to samo, co zwykłe najechanie kursorem, mimo że wygląda podobnie. Elementy z fokusem nadal wyglądają, jakby były „pod kursorem”, nawet gdy już nie są. Elementy otrzymują fokus po kliknięciu ich lub podczas nawigacji klawiaturą w menu.
{.is-info}

## Czy jakikolwiek element jest pod kursorem
Sprawdza, czy dowolny element w układzie jest aktualnie pod kursorem myszy.  
**Wymagana wartość**: Nie

## Czy jakikolwiek przycisk jest pod kursorem
Sprawdza, czy dowolny przycisk (vanilla lub niestandardowy) jest aktualnie pod kursorem myszy.  
**Wymagana wartość**: Nie

## Czy układ jest włączony
Sprawdza, czy konkretny układ jest obecnie włączony.  
**Wymagana wartość**: Tak - Nazwa układu (np. `my_cool_main_menu_layout`)

## Czy scheduler działa
Sprawdza, czy obecnie działa jakiś scheduler.
**Wymagana wartość**: Tak - ID schedulera (np. `my_scheduler`)

## Czy skala GUI
Sprawdza, czy bieżąca skala GUI spełnia określone warunki.  
**Wymagana wartość**: Tak - Może przyjmować wartości liczbowe, takie jak `1`, `2` itd.

## Czy przycisk jest aktywny
Sprawdza, czy konkretny przycisk jest aktywny (klikalny).  
**Wymagana wartość**: Tak - ID elementu docelowego przycisku (np. "some_element_ID")

## Czy tytuł ekranu pasuje
Sprawdza, czy WYŚWIETLANY tytuł ekranu pasuje do określonego tekstu lub klucza lokalizacji. Sprawdza tylko nazwę wyświetlaną/tytuł ekranu, np. „Opcje” lub „Pauza”. NIE sprawdza identyfikatora menu/ekranu (np. `title_screen`)!

**Wymagana wartość**: Tak - Dokładny tekst tytułu lub klucz lokalizacji ekranu

## Czy klawisz jest wciśnięty
Sprawdza, czy określony klawisz klawiatury jest aktualnie wciśnięty.  
**Wymagana wartość**: Tak - Kod klawisza docelowego. Wybierany przez interfejs podczas edycji wartości wymagania.

## Czy jakikolwiek ekran jest otwarty
Sprawdza, czy jakikolwiek ekran/menu jest obecnie otwarty (zwraca false, jeśli nie jest wyświetlany żaden ekran).  
**Wymagana wartość**: Nie

## Czy nakładka debugowania MC jest włączona
Sprawdza, czy nakładka debugowania F3 jest obecnie widoczna.
**Wymagana wartość**: Nie

## Czy aktywny jest typ kursora
Sprawdza, czy aktualnie aktywny typ kursora FancyMenu odpowiada określonemu standardowemu typowi kursora.
**Wymagana wartość**: Tak - Typ kursora: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` lub `not_allowed`

## Czy widoczny jest pasek menu dostosowywania
Sprawdza, czy pasek menu dostosowywania FancyMenu jest obecnie widoczny.
**Wymagana wartość**: Nie

## Czy włączony jest tryb Modpack Mode
Sprawdza, czy tryb Modpack Mode FancyMenu jest włączony.
**Wymagana wartość**: Nie

## Kliknięto myszą
Sprawdza, czy jest wciśnięty określony przycisk myszy.  
**Wymagana wartość**: Tak - `left` lub `right`, aby wskazać, który przycisk myszy sprawdzić

## Czy pełny ekran
Sprawdza, czy gra jest obecnie w trybie pełnoekranowym.  
**Wymagana wartość**: Nie

## Czy szerokość okna
Sprawdza, czy szerokość okna gry odpowiada określonym wartościom.  
**Wymagana wartość**: Tak - Szerokość okna w pikselach (np. "1920"). Można podać wiele wartości, oddzielając je przecinkami.

## Czy wysokość okna
Sprawdza, czy wysokość okna gry odpowiada określonym wartościom.  
**Wymagana wartość**: Tak - Wysokość okna w pikselach (np. "1080"). Można podać wiele wartości, oddzielając je przecinkami.

## Czy szerokość okna jest większa niż
Sprawdza, czy szerokość okna gry jest większa od określonej wartości.  
**Wymagana wartość**: Tak - Szerokość okna w pikselach (np. "1920")

## Czy wysokość okna jest większa niż
Sprawdza, czy wysokość okna gry jest większa od określonej wartości.  
**Wymagana wartość**: Tak - Wysokość okna w pikselach (np. "1080")

## Czy w grze wieloosobowej
Sprawdza, czy gracz znajduje się obecnie w świecie wieloosobowym.  
**Wymagana wartość**: Nie

## Czy w grze jednoosobowej
Sprawdza, czy gracz znajduje się obecnie w świecie jednoosobowym.  
**Wymagana wartość**: Nie

## Czy świat jest załadowany
Sprawdza, czy obecnie jest załadowany jakikolwiek świat.  
**Wymagana wartość**: Nie

## Czy tryb przygodowy
Sprawdza, czy gracz jest obecnie w trybie przygodowym.  
**Wymagana wartość**: Nie

## Czy tryb kreatywny
Sprawdza, czy gracz jest obecnie w trybie kreatywnym.  
**Wymagana wartość**: Nie

## Czy tryb widza
Sprawdza, czy gracz jest obecnie w trybie widza.  
**Wymagana wartość**: Nie

## Czy tryb przetrwania
Sprawdza, czy gracz jest obecnie w trybie przetrwania.  
**Wymagana wartość**: Nie

## Czy tryb gry
Sprawdza, czy gracz jest w określonym trybie gry.  
**Wymagana wartość**: Tak - Nazwa trybu gry (np. "creative", "survival", "adventure", "spectator")

## Czy poziom trudności
Sprawdza, czy bieżący poziom trudności gry odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Nazwa poziomu trudności (np. "peaceful", "easy", "normal", "hard")

## Czy hardcore
Sprawdza, czy aktualnie załadowany świat jest w trybie hardcore.
**Wymagana wartość**: Nie

## Czy perspektywa kamery
Sprawdza, czy bieżąca perspektywa kamery odpowiada określonej perspektywie.
**Wymagana wartość**: Tak - `first_person`, `third_person_back` lub `third_person_front`

## Czy pada deszcz
Sprawdza, czy obecnie pada deszcz w miejscu gracza.  
**Wymagana wartość**: Nie

## Czy grzmi
Sprawdza, czy obecnie trwa burza z piorunami w świecie gracza.  
**Wymagana wartość**: Nie

## Czy pogoda jest pogodna
Sprawdza, czy pogoda jest obecnie bezchmurna (nie pada deszcz ani nie grzmi).  
**Wymagana wartość**: Nie

## Czy pada śnieg
Sprawdza, czy obecnie pada śnieg w miejscu gracza.  
**Wymagana wartość**: Nie

## Czy gracz biegnie
Sprawdza, czy gracz aktualnie sprintuje.  
**Wymagana wartość**: Nie

## Czy gracz się skrada
Sprawdza, czy gracz aktualnie się skrada/kuca.  
**Wymagana wartość**: Nie

## Czy gracz używa przedmiotu
Sprawdza, czy gracz aktualnie używa przedmiotu.
**Wymagana wartość**: Nie

## Czy gracz pływa
Sprawdza, czy gracz aktualnie pływa.  
**Wymagana wartość**: Nie

## Czy gracz skacze lub spada
Sprawdza, czy gracz aktualnie skacze.  
**Wymagana wartość**: Nie

## Czy gracz jest całkowicie pod wodą
Sprawdza, czy gracz jest całkowicie pod wodą.  
**Wymagana wartość**: Nie

## Czy gracz jest w wodzie
Sprawdza, czy gracz znajduje się w wodzie (może być częściowo zanurzony).  
**Wymagana wartość**: Nie

## Czy gracz jest w lawie
Sprawdza, czy gracz znajduje się w lawie.  
**Wymagana wartość**: Nie

## Czy gracz jest w płynie
Sprawdza, czy gracz znajduje się w jakimkolwiek płynie (woda, lawa itd.).  
**Wymagana wartość**: Nie

## Czy gracz jedzie na encji/pojeździe
Sprawdza, czy gracz jedzie na jakiejkolwiek encji.  
**Wymagana wartość**: Nie

## Czy gracz jedzie na jeżdżącej encji
Sprawdza, czy gracz jedzie na encji, która może skakać (np. na koniu).  
**Wymagana wartość**: Nie

## Czy gracz jedzie na encji z punktami życia
Sprawdza, czy gracz jedzie na żywej encji mającej punkty życia (np. na zwierzęciu, a nie na łódce).  
**Wymagana wartość**: Nie

## Czy gracz jest w proszkowym śniegu
Sprawdza, czy gracz aktualnie znajduje się w proszkowym śniegu.  
**Wymagana wartość**: Nie

## Czy gracz był w proszkowym śniegu
Sprawdza, czy gracz był w proszkowym śniegu (używane dla efektów utrzymujących się po wyjściu).  
**Wymagana wartość**: Nie

## Czy gracz nosi dynię
Sprawdza, czy gracz ma na głowie wydrążoną dynię.  
**Wymagana wartość**: Nie

## Czy gracz lata z elytrą
Sprawdza, czy gracz aktualnie lata z użyciem elytry.  
**Wymagana wartość**: Nie

## Czy gracz lata w trybie kreatywnym
Sprawdza, czy gracz lata w trybie kreatywnym.  
**Wymagana wartość**: Nie

## Czy gracz ma serca absorpcji
Sprawdza, czy gracz ma jakiekolwiek serca absorpcji (złote serca).  
**Wymagana wartość**: Nie

## Czy gracz jest witherowany
Sprawdza, czy gracz jest pod wpływem efektu wither.
**Wymagana wartość**: Nie

## Czy gracz jest całkowicie zamrożony
Sprawdza, czy gracz jest całkowicie zamrożony (zwykle od proszkowego śniegu).  
**Wymagana wartość**: Nie

## Czy gracz jest zatruty
Sprawdza, czy gracz jest pod wpływem efektu trucizny.  
**Wymagana wartość**: Nie

## Czy gracz jest w biomie
Sprawdza, czy gracz znajduje się w określonym biomie.  
**Wymagana wartość**: Tak - Identyfikator biomu (np. `minecraft:birch_forest`)

## Czy gracz jest w wymiarze
Sprawdza, czy gracz znajduje się w określonym wymiarze.  
**Wymagana wartość**: Tak - Identyfikator wymiaru (np. `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Czy gracz jest w strukturze
Sprawdza, czy gracz aktualnie znajduje się wewnątrz określonej struktury. W przypadku światów serwerowych wymaga FancyMenu na serwerze.
**Wymagana wartość**: Tak - Identyfikator struktury (np. `minecraft:village`)

## Czy encja jest w pobliżu
Sprawdza, czy określony typ encji znajduje się w określonym promieniu od gracza.  
**Wymagana wartość**: Tak - Format: "promień:entity_id" (np. `10:minecraft:pig` - sprawdza, czy świnie znajdują się w promieniu 10 bloków)

## Czy efekt jest aktywny
Sprawdza, czy określony efekt mikstury jest aktywny na graczu.  
**Wymagana wartość**: Tak - Identyfikator efektu (np. `minecraft:speed`, `minecraft:strength`)

## Czy jakikolwiek efekt jest aktywny
Sprawdza, czy gracz ma aktywny jakikolwiek efekt mikstury.  
**Wymagana wartość**: Nie

## Czy gracz jest leworęczny
Sprawdza, czy gracz ma ustawiony tryb leworęczny w opcjach gry.  
**Wymagana wartość**: Nie

## Czy slot ekwipunku jest zajęty
Sprawdza, czy określony slot ekwipunku zawiera przedmiot.  
**Wymagana wartość**: Tak - Numer slotu (0-35 dla głównego ekwipunku, sloty 0-8 to pasek szybkiego dostępu)

## Czy element w ekwipunku jest pod kursorem
Sprawdza, czy kursor znajduje się nad jakimkolwiek przedmiotem w ekranie ekwipunku.
**Wymagana wartość**: Nie

## Czy kursor trzyma przedmiot z ekwipunku
Sprawdza, czy kursor aktualnie trzyma stos przedmiotów z ekwipunku.
**Wymagana wartość**: Nie

## Czy slot paska szybkiego dostępu jest wybrany
Sprawdza, czy określony slot paska szybkiego dostępu jest obecnie wybrany.  
**Wymagana wartość**: Tak - Numer slotu paska szybkiego dostępu (0-8)

## Czy gracz ma poziom uprawnień
Sprawdza, czy gracz ma co najmniej określony poziom uprawnień/OP w bieżącym świecie lub na serwerze.  
**Wymagana wartość**: Tak - Numer poziomu uprawnień (0-4, gdzie 4 oznacza operatora serwera)

## Czy siła ataku jest osłabiona
Sprawdza, czy siła ataku gracza jest aktualnie osłabiona (nie jest w pełni naładowana).  
**Wymagana wartość**: Nie

## Czy czas rzeczywisty: dzień
Sprawdza, czy bieżący rzeczywisty dzień miesiąca odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Numer dnia (1-31). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: godzina
Sprawdza, czy bieżąca rzeczywista godzina odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Godzina w formacie 24-godzinnym (0-23). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: minuta
Sprawdza, czy bieżąca rzeczywista minuta odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Minuta (0-59). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: miesiąc
Sprawdza, czy bieżący rzeczywisty miesiąc odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Numer miesiąca (1-12, gdzie 1 to styczeń). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: sekunda
Sprawdza, czy bieżąca rzeczywista sekunda odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Sekunda (0-59). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: dzień tygodnia
Sprawdza, czy bieżący rzeczywisty dzień tygodnia odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Dzień tygodnia jako liczba (1-7, gdzie 1 to niedziela). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: rok
Sprawdza, czy bieżący rzeczywisty rok odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Pełny rok (np. "2023"). Można podać wiele wartości, oddzielając je przecinkami.

## Istnieje plik/folder
Sprawdza, czy w systemie istnieje określony plik lub folder.  
**Wymagana wartość**: Tak - Ścieżka do pliku lub folderu (bezwzględna lub względna względem katalogu gry)

## Czy system operacyjny to Linux
Sprawdza, czy system operacyjny to Linux.  
**Wymagana wartość**: Nie

## Czy system operacyjny to macOS
Sprawdza, czy system operacyjny to macOS.  
**Wymagana wartość**: Nie

## Czy system operacyjny to Windows
Sprawdza, czy system operacyjny to Windows.  
**Wymagana wartość**: Nie

## Czy dostępne jest połączenie z internetem
Sprawdza, czy dostępne jest aktywne połączenie z internetem.  
**Wymagana wartość**: Nie

## Czy język gry
Sprawdza, czy bieżący język gry odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Kod języka (np. `en_us` dla angielskiego)

## Czy mod jest załadowany
Sprawdza, czy określony mod jest załadowany.  
**Wymagana wartość**: Tak - ID moda (np. `fancymenu`, `jei`). Możesz też sprawdzić Optifine za pomocą `optifine`. Można podać wiele ID modów, oddzielając je przecinkami.

## Czy MCEF jest załadowany
Sprawdza, czy MCEF (Minecraft Chromium Embedded Framework) jest zainstalowany i zainicjalizowany.  
**Wymagana wartość**: Nie

## Czy liczba
Zapewnia zaawansowane porównywanie liczb z różnymi trybami porównania.  
**Wymagana wartość**: Tak - Złożony format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`, gdzie `comparison_mode` może być `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` lub `smaller-than-or-equals`

## Czy tekst
Zapewnia zaawansowane porównywanie tekstu z różnymi trybami porównania.  
**Wymagana wartość**: Tak - Złożony format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`, gdzie `comparison_mode` może być `equals`, `contains`, `starts-with` lub `ends-with`

## Czy IP serwera
Sprawdza, czy bieżący adres IP serwera odpowiada określonej wartości.  
**Wymagana wartość**: Tak - Adres IP serwera (z portem lub bez)

## Czy serwer jest online
Sprawdza, czy określony serwer jest online i osiągalny.  
**Wymagana wartość**: Tak - Adres IP serwera (z portem lub bez)

## Czy pakiet zasobów jest włączony
Sprawdza, czy określony pakiet zasobów jest obecnie wybrany/aktywny.  
**Wymagana wartość**: Tak - Tytuł pakietu zasobów lub ID pakietu (np. `Programmer Art` albo ID pakietu)

## Czy wartość zmiennej (zmienna FM)
Sprawdza, czy zmienna FancyMenu ma określoną wartość.  
**Wymagana wartość**: Tak - Format: "variable_name:expected_value"

## Tylko raz na sesję
Zwraca true tylko raz na sesję gry. Przydatne do jednorazowych ogłoszeń lub działań.  
**Wymagana wartość**: Nie
