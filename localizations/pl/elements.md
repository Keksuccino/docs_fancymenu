---
title: Elementy
description: 'Wszystko, co warto wiedzieć o typach elementów FancyMenu.'
---

# Elementy

Elementy są podstawowymi blokami Twoich własnych układów w FancyMenu. Możesz dodawać je do dowolnego układu, aby wyświetlać informacje, dodać interaktywność lub tworzyć efektowne efekty wizualne.

# Dodawanie elementów do układu

Nowy element możesz dodać do swojego układu w **Edytorze układu**.

1.  **Kliknij prawym przyciskiem myszy** tło edytora, aby otworzyć menu kontekstowe.
2.  Najedź kursorem na **Nowy element**.
3.  Pojawi się lista wszystkich dostępnych typów elementów. Kliknij ten, który chcesz dodać.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Po dodaniu elementu możesz go przesuwać, zmieniać jego rozmiar i dostosowywać, **klikając prawym przyciskiem myszy** na nim, aby otworzyć jego własne menu kontekstowe. Aby dowiedzieć się więcej o rozmieszczaniu elementów, zobacz [Pozycjonowanie elementów](./positioning-elements) i [Identyfikatory elementów](./element-identifiers).

# Elementy szczegółowo

Ta sekcja zawiera listę wbudowanych elementów FancyMenu. Użyj [Warstwy i grupy](./layers-and-groups), aby uporządkować kolejność ich renderowania.

## Przycisk
Klikalny przycisk, który może wykonywać bardzo różnorodne akcje. To jeden z najpotężniejszych i najbardziej wszechstronnych elementów do tworzenia interaktywnych menu.

*   **Przykłady użycia:**
    *   Tworzenie przycisku „Dołącz do Discorda” lub „Odwiedź stronę”.
    *   Dodanie przycisku szybkiego dołączania do konkretnego serwera.
    *   Budowanie własnej nawigacji między różnymi menu.
    *   Tworzenie przycisków przełączających inne układy włączone lub wyłączone.
*   **Najważniejsze funkcje:**
    *   **Akcje:** Może wykonywać sekwencję [akcji](./action-scripts), takich jak otwarcie adresu URL, dołączenie do serwera, wysłanie komendy na czacie, naśladowanie funkcji innego przycisku lub sterowanie zmiennymi.
    *   **Własny wygląd:** W pełni konfigurowalne tekstury dla stanów normalnego, po najechaniu i nieaktywnego. Obsługuje przezroczyste tła, nine-slicing, własne kolory etykiet, kolory etykiet po najechaniu, skalę etykiety, przełączniki cienia tekstu oraz tekstury ikony przycisku.
    *   **Dźwięki:** Własne dźwięki kliknięcia, najechania i opuszczenia.
    *   **Tryb szablonu:** Może zastosować swój wygląd i właściwości do innych przycisków vanilla lub modowanych w menu. Zobacz [Szablony przycisków i suwaków](./button-slider-templates).
    *   **Automatyczne kliknięcia widgetów Vanilla/modów:** Istniejące widgety vanilla i modów mają właściwość **Automatyczne kliknięcia**, która może wywołać ich oryginalne zachowanie kliknięcia określoną liczbę razy po załadowaniu ekranu. Szczegóły znajdziesz w sekcji [Elementy Vanilla](./vanilla-elements#automated-clicks).

## Suwak
Suwak, który użytkownicy mogą przeciągać, aby wybrać wartość z listy lub zakresu. Może wykonywać akcje za każdym razem, gdy jego wartość się zmieni.

*   **Przykłady użycia:**
    *   Tworzenie własnej kontroli głośności.
    *   Suwak do przełączania między różnymi motywami lub obrazami tła (z użyciem typu „Lista”).
    *   Dostosowywanie konkretnej opcji Minecrafta, takiej jak jasność lub dystans renderowania.
*   **Najważniejsze funkcje:**
    *   **Typy:** Może być `Lista wartości` (np. „Łatwy”, „Normalny”, „Trudny”), `Zakres całkowity` (np. 1-100) lub `Zakres dziesiętny` (np. 0.0-1.0).
    *   **Dynamiczne akcje:** Wykonuje akcje, gdy jego wartość się zmienia. Bieżącą wartość można wykorzystać z [Zmienne](./variables).
    *   **Personalizacja:** Etykieta suwaka może dynamicznie wyświetlać jego bieżącą wartość. Uchwyt i tekstury tła są w pełni konfigurowalne, w tym przezroczyste tła, opcje koloru/skali etykiety, przełączniki cienia tekstu oraz własne dźwięki kliknięcia/opuszczenia.

## Pole wyboru
Standardowe pole wyboru, które można włączać i wyłączać. Może wykonywać akcje po przełączeniu.

*   **Przykłady użycia:**
    *   Pole wyboru „Akceptuję zasady”.
    *   Ustawienie umożliwiające włączenie lub wyłączenie konkretnej funkcji w Twoim własnym menu.
    *   Przełączanie układu lub zmiennej włącz/wyłącz.
*   **Najważniejsze funkcje:**
    *   **Akcje przy przełączeniu:** Wykonuje [skrypty akcji](./action-scripts) przy zmianie stanu. Bieżący stan (`true` lub `false`) jest dostępny dla jego akcji.
    *   **Tryb zmiennej:** Może być bezpośrednio powiązane ze zmienną FancyMenu, dzięki czemu stan pola wyboru jest odczytywany z tej zmiennej i do niej zapisywany.
    *   **Trwały stan:** Gdy Tryb zmiennej jest wyłączony, pole wyboru automatycznie zapisuje swój stan według identyfikatora elementu i przywraca go po ponownym uruchomieniu gry. Stany te są przechowywane w pliku `<game-directory>/checkbox_states.json`. W Trybie zmiennej źródłem stanu pola wyboru jest powiązana zmienna FancyMenu.
    *   **Własny wygląd:** Obsługuje własne tekstury tła (w stanach normalnym, po najechaniu i nieaktywnym) oraz sam znacznik wyboru.

## Pole tekstowe
Pole, w którym użytkownicy mogą wpisywać tekst. Jego zawartość może być powiązana ze zmienną FancyMenu, co pozwala przechwytywać i wykorzystywać dane wprowadzone przez użytkownika.

*   **Przykłady użycia:**
    *   Pole wejściowe „IP serwera”, współpracujące z przyciskiem „Dołącz do serwera”.
    *   Pole do wpisania nazwy gracza do podglądu własnej skórki.
    *   Tworzenie podstawowego interfejsu przypominającego logowanie.
*   **Najważniejsze funkcje:**
    *   **Powiązanie ze zmienną:** Zapisuje wpisany tekst w określonej [zmiennej](./variables).
    *   **Walidacja danych wejściowych:** Można skonfigurować je tak, aby akceptowało tylko określone typy znaków, takie jak liczby, adresy URL lub zwykły tekst.
    *   **Maksymalna długość:** Możesz ustawić maksymalny limit znaków dla wpisu.
    *   **Wygląd i dźwięki:** Obsługuje własny kolor tła, kolory obramowania, zaokrąglenie obramowania, kolor tekstu, tekst podpowiedzi/placeholder, kolor podpowiedzi, dźwięki najechania, opuszczenia i kliknięcia.

## Podpowiedź
Pole tekstowe, które może pojawić się w stałym miejscu lub podążać za kursorem myszy. Jego widoczność jest zwykle kontrolowana za pomocą [Wymagań ładowania](./conditions).

*   **Przykłady użycia:**
    *   Wyświetlanie szczegółowych informacji, gdy użytkownik najedzie kursorem na przycisk lub obraz.
    *   Tworzenie kontekstowych podpowiedzi, które pojawiają się w określonych warunkach.
    *   Pokazywanie dynamicznych informacji (takich jak status serwera) obok kursora.
*   **Najważniejsze funkcje:**
    *   **Podążanie za myszą:** Może być ustawiona tak, aby podążała za wskaźnikiem myszy.
    *   **Obsługa Markdown:** Zawartość podpowiedzi obsługuje pełne formatowanie Markdown.
    *   **Własne tło:** Tło może być jednolitym kolorem lub własną teksturą nine-sliced, aby uzyskać w pełni dopasowany wygląd.

## Przedmiot
Wyświetla pojedynczy przedmiot Minecrafta, z vanilla lub z moda.

*   **Przykłady użycia:**
    *   Używanie przedmiotów jako ikon przycisków lub opcji menu.
    *   Tworzenie interfejsu sklepu lub wyboru zestawów.
    *   Wyświetlanie przedmiotu trzymanego przez gracza lub jego zbroi.
*   **Najważniejsze funkcje:**
    *   **Własne dane:** Obsługuje własną nazwę, lore, liczbę sztuk, połysk zaklęcia i dane NBT. Zobacz [Placeholder danych NBT](./nbt-data-placeholder).
    *   **Wyświetlanie podpowiedzi:** Można skonfigurować tak, aby po najechaniu pokazywał standardową podpowiedź przedmiotu.

## Model JSON bloku/przedmiotu
Renderuje model JSON bloku lub przedmiotu z zasobów Minecrafta lub z zewnętrznych źródeł.

*   **Przykłady użycia:**
    *   Wyświetlanie trójwymiarowego modelu z paczki zasobów w menu.
    *   Pokazywanie podglądu przedmiotów/bloków z własnymi teksturami.
    *   Tworzenie dekoracyjnych elementów interfejsu opartych na modelach.
*   **Najważniejsze funkcje:**
    *   **Źródło modelu:** Może wczytywać plik JSON modelu z zasobów Minecrafta lub z zewnętrznych źródeł.
    *   **Zastępowanie tekstur:** Obsługuje ustawienie własnej tekstury.
    *   **Kontrola renderowania:** Przesunięcie modelu, skala, obrót w trzech osiach, renderowanie przezroczyste oraz transformacja GUI modelu.
    *   **Oświetlenie:** Dwa konfigurowalne źródła światła z niezależną kontrolą odcienia i obrotu.

## Obraz
Wyświetla statyczny obraz z lokalnego pliku, adresu URL w internecie lub lokalizacji zasobu Minecrafta.

*   **Przykłady użycia:**
    *   Dodanie logo serwera lub identyfikacji moda/paczki modów.
    *   Tworzenie dekoracyjnych ramek lub obramowań interfejsu.
    *   Używanie obrazów jako części bardziej złożonego projektu interfejsu.
*   **Najważniejsze funkcje:**
    *   **Nine-slicing:** Skaluje obramowania lub panele bez zniekształcania narożników. Zobacz [Nine-slicing i kafelkowanie](./nine-slicing-and-tiling).
    *   **Powtarzanie tekstury:** Obraz może być kafelkowany, aby wypełnić obszar elementu.
    *   **Tintowanie:** Możesz nałożyć na obraz kolorowy tint.
    *   **Zaokrąglone rogi:** Obrazy bez nine-slicing i bez powtarzania mogą mieć zaokrąglone rogi.
    *   **Efekt paralaksy:** Porusza się wraz z myszą, tworząc wrażenie głębi. Zobacz [Efekt paralaksy](./parallax).

## Tekst
Bardzo wszechstronny element do wyświetlania tekstu. Może służyć do wszystkiego — od jednolinijkowych etykiet po wielostronicowe, przewijane dokumenty.

*   **Przykłady użycia:**
    *   Wyświetlanie zasad serwera, informacji o aktualizacji lub wiadomości powitalnych.
    *   Tworzenie dynamicznych paneli informacyjnych z użyciem [placeholderów](./placeholders), na przykład `Witaj, {"placeholder":"playername"}!`.
    *   Dodawanie etykiet i opisów do interfejsu.
*   **Najważniejsze funkcje:**
    *   **Źródła treści:** Tekst można wpisać bezpośrednio, wczytać z lokalnego pliku albo pobrać z adresu URL.
    *   **Obsługa Markdown:** Obsługuje nagłówki, listy, bloki kodu, tabele i inne formatowanie Markdown. Zobacz [Formatowanie tekstu](./text-formatting).
    *   **Przewijanie:** Automatycznie staje się przewijalny, jeśli zawartość jest większa niż obszar elementu. Paski przewijania można dostosować lub wyłączyć.
    *   **Stylizacja:** Pełna kontrola nad kolorem tekstu, skalą, wyrównaniem, cieniem i odstępami między wierszami.

## Wideo
Odtwarza plik wideo. To idealne rozwiązanie dla filmowych intro lub dekoracyjnych, zapętlonych tł w tle.

> [!WARNING]
> Natywny element Wideo wymaga **Watermedia V3** oraz **Watermedia Binaries V3**. Stary element **Video [MCEF]** jest przestarzały.

*   **Przykłady użycia:**
    *   Animowany trailer paczki modów lub serwera.
    *   Zapętlone, nastrojowe wideo, które ożywia menu.
    *   Wideo instruktażowe w grze.
*   **Najważniejsze funkcje:**
    *   **Źródła:** Obsługuje lokalne pliki wideo i adresy URL. Zobacz [Wideo](./video).
    *   **Sterowanie odtwarzaniem:** Może być ustawione na automatyczne zapętlanie. Głośność, kanał dźwięku i zachowanie zachowujące proporcje obrazu są regulowane.
    *   **Interaktywne sterowanie:** Odtwarzaniem wideo, czasem przewijania i głośnością można sterować za pomocą akcji przycisków.

## Shader GLSL
Renderuje własny shader GLSL wewnątrz elementu.

*   **Przykłady użycia:**
    *   Animowane panele shaderów.
    *   Proceduralne efekty wizualne.
    *   Efekty menu w stylu Shadertoy przycięte do prostokąta elementu.
*   **Najważniejsze funkcje:**
    *   **Środowisko uruchomieniowe shaderów:** Obsługuje shadery jedno- i wieloprzebiegowe.
    *   **Obsługa Shadertoy:** Może używać shaderów w stylu Shadertoy `mainImage`.
    *   **Uniformy:** Udostępnia uniformy FancyMenu i wejściowe. Zobacz [API shaderów GLSL](./glsl-shader-api).

## Pokaz slajdów
Wyświetla sekwencję obrazów. Jego obrazy i plik konfiguracyjny `properties.txt` znajdują się we własnym podkatalogu pokazu slajdów w `<game-directory>/config/fancymenu/slideshows/`.

*   **Przykłady użycia:**
    *   Rotująca galeria zrzutów ekranu z gry.
    *   Prezentowanie najważniejszych funkcji paczki modów.
    *   Dynamiczne tło, które cyklicznie przełącza się między różnymi scenami.
*   **Najważniejsze funkcje:**
    *   Wczytuje gotowe [pokazy slajdów](./slideshows).
    *   Można ustawić zachowanie proporcji obrazów.

## Prostokąt
Prosty, jednokolorowy prostokąt.

*   **Przykłady użycia:**
    *   Tworzenie półprzezroczystego tła za tekstem, aby poprawić czytelność.
    *   Projektowanie prostych paneli i separatorów interfejsu.
    *   Jako kolorowy placeholder podczas projektowania układu.
*   **Najważniejsze funkcje:**
    *   Obsługuje kolory HEX RGBA, zaokrąglone rogi i opcjonalne rozmycie, dzięki czemu kształt może służyć jako prosty panel, tint lub rozmyte tło.

## Koło
Prosty, jednokolorowy kształt koła/elipsy.

*   **Przykłady użycia:**
    *   Tworzenie okrągłych akcentów, wskaźników lub miękkich obszarów interfejsu.
    *   Budowanie dekoracji UI w wybranym stylu bez pliku tekstury.
*   **Najważniejsze funkcje:**
    *   Obsługuje kolor, rozmycie oraz konfigurowalną wartość zaokrąglenia/wykładnika.

## Tekst efektowy
Odtworzenie ikonicznego, żółtego, podskakującego tekstu efektowego z ekranu tytułowego Minecrafta.

*   **Przykłady użycia:**
    *   Zastąpienie vanilla tekstu efektowego własnymi wiadomościami.
    *   Dodanie przyciągającej wzrok, animowanej wiadomości do dowolnego menu.
*   **Najważniejsze funkcje:**
    *   **Źródła treści:** Może używać domyślnych vanilla splashów, listy własnego tekstu wpisanego bezpośrednio albo tekstu z lokalnego pliku.
    *   **Personalizacja:** Możesz włączyć lub wyłączyć efekt podskakiwania oraz dostosować kolor tekstu, skalę, obrót i cień.

## Encja gracza
Renderuje model gracza w menu.

*   **Przykłady użycia:**
    *   Wyświetlanie aktualnej postaci gracza w głównym menu.
    *   Tworzenie ekranu wyboru drużyny lub podglądu klasy.
    *   Sekcja „profil” pokazująca skórkę i nazwę gracza.
*   **Najważniejsze funkcje:**
    *   **Dynamiczny wygląd:** Może kopiować aktualną skórkę, pelerynę i nazwę gracza. Zobacz [Głowy graczy](./player-heads).
    *   **Własne pozy:** Oferuje precyzyjną kontrolę nad obrotem głowy, ciała, ramion i nóg. Głowa i ciało mogą też podążać za kursorem myszy.
    *   **Atrybuty:** Może być ustawione jako mały model, kucający lub slim.

## Przeglądarka
Element renderujący aktywną stronę internetową wewnątrz gry.

Ten element wymaga zainstalowanego i działającego moda **MCEF (Minecraft Chromium Embedded Framework)**!

Możesz pobrać MCEF z oficjalnych stron projektu na [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) i [Modrinth](https://modrinth.com/mod/mcef).

Dla nowszych wersji Minecrafta (1.21.5+) oficjalne projekty MCEF nie udostępniają kompilacji, ale istnieje fork z wersjami dla najnowszych wydań Minecrafta, który można znaleźć [tutaj](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) i [tutaj](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Ten fork jest utrzymywany przez Keksuccino, aby jak najszybciej udostępniać kompilacje dla najnowszych wersji Minecrafta.

*   **Przykłady użycia:**
    *   Wyświetlanie aktywnego Dynmap serwera.
    *   Osadzanie odtwarzacza wideo YouTube.
    *   Pokazywanie wiki lub strony dokumentacji bezpośrednio w grze.
*   **Najważniejsze funkcje:**
    *   **Interaktywność:** Może być w pełni interaktywny, pozwalając użytkownikom klikać linki, przewijać i pisać.
    *   **Kontrola mediów:** Oferuje opcje wyciszania multimediów, zapętlania filmów i ukrywania kontrolek wideo na wczytanej stronie.

### Ładowanie lokalnych plików HTML
Element Przeglądarka może wczytywać lokalne dokumenty HTML z `<game-directory>/config/fancymenu/assets/`.

Aby wczytać lokalny plik HTML, rozpocznij adres URL od `file:///`, a następnie podaj KRÓTKĄ ścieżkę pliku, na przykład `/config/fancymenu/assets/cool_changelog.html`, co da adres: `file:///config/fancymenu/assets/cool_changelog.html`.

Na **Linuxie** użyj [**placeholdera pełnej ścieżki pliku/folderu**](./placeholders#absolute-filefolder-path-absolute_path) zamiast wpisywania na sztywno pełnej ścieżki specyficznej dla danej instancji: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Krótka ścieżka w systemie Linux musi zaczynać się od `/`, jak pokazano w przykładzie.

## Animator elementów
Potężne narzędzie do tworzenia złożonych animacji opartych na klatkach kluczowych. Może animować pozycję, rozmiar i punkt zakotwiczenia jednego lub wielu innych elementów.

*   **Przykłady użycia:**
    *   Wysuwanie elementów na ekran lub poza niego.
    *   Zmiana rozmiaru paneli lub powiadomień.
    *   Animowanie przesunięć pozycji i przejść punktów zakotwiczenia.
*   **Najważniejsze funkcje:**
    *   **Edytor klatek kluczowych:** Dedykowany edytor do dodawania, edytowania i sekwencjonowania klatek kluczowych na osi czasu.
    *   **Wiele celów:** Jeden Animator może jednocześnie sterować wieloma elementami „docelowymi”.
    *   **Sterowanie:** Animacje mogą być zapętlone. Możesz też wybrać animowanie tylko pozycji lub tylko rozmiaru.
    *   **Przesunięcia czasowe:** Elementy docelowe mogą używać indywidualnych lub losowych przesunięć czasu startu.
    *   Zobacz [Animator elementów](./element-animator), aby uzyskać informacje o konfiguracji i edycji klatek kluczowych.

## Tykacz
Niewidoczny element, który wykonuje listę akcji w regularnych odstępach czasu (co „tick”).

> [!NOTE]
> Do automatyzacji w tle rozważ użycie [Harmonogramów](./schedulers). Harmonogramy są globalne i mogą działać niezależnie od konkretnego ekranu.

*   **Przykłady użycia:**
    *   Okresowe sprawdzanie statusu online serwera i aktualizowanie elementu tekstowego.
    *   Tworzenie licznika odliczającego czas, który aktualizuje etykietę tekstową.
    *   Wielokrotne uruchamianie skryptu, aby tworzyć własne zachowania.
*   **Najważniejsze funkcje:**
    *   **Kontrola czasu:** Możesz ustawić opóźnienie między tickami w milisekundach.
    *   **Tryby ticków:** Może działać ciągle, tylko raz na sesję gry albo raz za każdym razem, gdy menu jest ładowane.
    *   **Asynchroniczny:** Może wykonywać swoje [akcje](./action-scripts) osobno, choć niektóre akcje nie mogą działać, gdy ta opcja jest włączona.

## Dźwięk
Niewidoczny element odtwarzający pliki audio. Może zarządzać listą odtwarzania utworów i oferuje różne opcje sterowania odtwarzaniem.

*   **Przykłady użycia:**
    *   Dodanie własnej muzyki w tle do menu.
    *   Tworzenie odtwarzacza muzyki z przyciskami do sterowania odtwarzaniem (następny/poprzedni utwór, głośność).
    *   Odtwarzanie dźwięków otoczenia.
*   **Najważniejsze funkcje:**
    *   **Lista odtwarzania:** Może zarządzać wieloma ścieżkami audio.
    *   **Tryby odtwarzania:** Może odtwarzać utwory po kolei lub losowo (z obsługą ważenia utworów, aby niektóre pojawiały się częściej niż inne).
    *   **Sterowanie:** Obsługuje zapętlanie, regulację głośności i wybór kanału dźwięku. Zobacz [Muzyka w tle menu](./background-music).

## Kontroler muzyki
Niewidoczny element służący do sterowania domyślnym odtwarzaniem muzyki Minecrafta w konkretnym menu.

*   **Przykłady użycia:**
    *   Wyłączenie domyślnej muzyki menu na ekranie, na którym chcesz odtwarzać własną muzykę przez [**element Dźwięk**](#audio).
    *   Zatrzymanie muzyki z gry, aby nie była dalej odtwarzana po otwarciu menu w trakcie gry.
*   **Najważniejsze funkcje:**
    *   Oddzielne przełączniki do sterowania vanilla „Muzyka menu” i „Muzyka świata”.

## Pasek postępu
Konfigurowalny pasek, który wizualnie przedstawia wartość liczbową.

*   **Przykłady użycia:**
    *   Pasek ładowania pokazujący postęp wczytywania świata z użyciem `{"placeholder":"world_load_progress"}`.
    *   Wizualne paski zdrowia, głodu lub doświadczenia w HUDzie.
    *   Wskaźnik głośności sterowany przez [**element Suwak**](#slider).
*   **Najważniejsze funkcje:**
    *   **Dynamiczna wartość:** Wartość postępu (0-100 lub 0.0-1.0) ustawia się za pomocą pola tekstowego, które obsługuje [placeholdery](./placeholders).
    *   **Wygląd:** Kierunek paska (góra, dół, lewo, prawo), kolory, tekstury i nine-slicing dla tekstur paska/tła są w pełni konfigurowalne.
    *   **Animacja:** Posiada płynną animację wypełniania, dzięki czemu zmiany postępu wyglądają mniej gwałtownie.
    *   **Kotwiczenie elementu na podstawie postępu:** Gdy inny element używa paska postępu jako swojej kotwicy **Element**, włącz **Użyj postępu dla kotwicy elementu**, aby przesunąć tę kotwicę do aktualnej krawędzi wypełnionego obszaru. Zakotwiczone elementy poruszają się wtedy wraz z postępem paska zamiast pozostawać przypięte do jego statycznych granic.

## Przeciągacz
Niewidoczny element, który użytkownik może kliknąć i przeciągać, aby go przesuwać. Inne elementy mogą być do niego zakotwiczone, aby tworzyć ruchome widżety.

*   **Przykłady użycia:**
    *   Tworzenie przeciąganego zegara lub panelu informacyjnego.
    *   Umożliwienie użytkownikom dostosowania położenia elementów interfejsu do własnych preferencji.
*   **Najważniejsze funkcje:**
    *   **Opcjonalna trwałość:** Włącz **Zapisuj przesunięcie przeciągania użytkownika**, aby zachować pozycję ustaloną przez użytkownika między otwarciami ekranu i ponownymi uruchomieniami gry. Wyłącz tę opcję, aby resetować przesunięcie.
    *   **Punkt zakotwiczenia:** Działa jako ruchoma kotwica dla innych elementów, co stanowi ważną część [Pozycjonowania elementów](./positioning-elements).

## Kursor
Niewidoczny element, który zastępuje domyślny kursor systemowy własnym obrazem, gdy układ jest aktywny.

*   **Przykłady użycia:**
    *   Tworzenie w pełni tematycznego interfejsu, pasującego do estetyki Twojej paczki modów.
*   **Najważniejsze funkcje:**
    *   **Własna tekstura:** Użyj dowolnego obrazu jako kursora.
    *   **Hotspot:** Ustawia dokładny piksel obrazu używany jako punkt kliknięcia. Zobacz [Własny kursor](./custom-cursor).
