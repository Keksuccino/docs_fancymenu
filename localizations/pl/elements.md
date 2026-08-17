---
title: Elementy
description: 'Wszystko, co warto wiedzieć o typach elementów FancyMenu.'
---
# Elementy

Elementy są podstawowymi składnikami niestandardowych układów w FancyMenu. Możesz dodawać je do dowolnego układu, aby wyświetlać informacje, dodawać interaktywność lub tworzyć zachwycające efekty wizualne.

# Dodawanie elementów do układu

Nowy element możesz dodać do układu w **Edytorze układu**.

1.  **Kliknij prawym przyciskiem myszy** tło edytora, aby otworzyć menu kontekstowe.
2.  Najedź kursorem na **Nowy element**.
3.  Pojawi się lista wszystkich dostępnych typów elementów. Kliknij ten, który chcesz dodać.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Po dodaniu elementu możesz go przesuwać, zmieniać jego rozmiar i dostosowywać go, **klikając go prawym przyciskiem myszy**, aby otworzyć jego menu kontekstowe. Więcej informacji o rozmieszczaniu elementów znajdziesz w sekcjach [Pozycjonowanie elementów](./positioning-elements) i [Identyfikatory elementów](./element-identifiers).

# Szczegółowe informacje o elementach

W tej sekcji wymieniono wbudowane elementy FancyMenu. Użyj sekcji [Warstwy i grupy](./layers-and-groups), aby uporządkować ich kolejność renderowania.

## Przycisk
Klikalny przycisk, który może wykonywać różnorodne akcje. Jest to jeden z najbardziej zaawansowanych i wszechstronnych elementów do tworzenia interaktywnych menu.

*   **Zastosowania:**
    *   Tworzenie przycisku „Dołącz do Discorda” lub „Odwiedź stronę internetową”.
    *   Dodawanie przycisku szybkiego dołączania do określonego serwera.
    *   Budowanie niestandardowej nawigacji między różnymi menu.
    *   Tworzenie przycisków włączających lub wyłączających inne układy.
*   **Najważniejsze funkcje:**
    *   **Akcje:** Może wykonywać sekwencję [akcji](./action-scripts), takich jak otwieranie adresu URL, dołączanie do serwera, wysyłanie polecenia czatu, naśladowanie funkcji innego przycisku lub sterowanie zmiennymi.
    *   **Niestandardowy wygląd:** W pełni konfigurowalne tekstury dla stanów normalnego, po najechaniu i nieaktywnego. Obsługuje przezroczyste tła, dziewięciokrotne skalowanie, niestandardowe kolory etykiet, kolory etykiet po najechaniu, skalę etykiet, przełączniki cienia etykiet oraz tekstury ikon przycisków.
    *   **Dźwięki:** Niestandardowe dźwięki kliknięcia, najechania i opuszczenia kursorem.
    *   **Tryb szablonu:** Może zastosować swój wygląd i właściwości do innych waniliowych lub zmodyfikowanych przycisków w menu. Zobacz [Szablony przycisków i suwaków](./button-slider-templates).
    *   **Automatyczne klikanie waniliowych/modyfikowanych widżetów:** Istniejące waniliowe i zmodyfikowane widżety mają właściwość **Automatyczne klikanie**, która może wywołać ich oryginalne działanie kliknięcia określoną liczbę razy podczas ładowania ekranu. Szczegóły znajdziesz w sekcji [Elementy waniliowe](./vanilla-elements#automated-clicks).

## Suwak
Suwak, który użytkownicy mogą przeciągać, aby wybrać wartość z listy lub zakresu. Może wykonywać akcje za każdym razem, gdy jego wartość się zmieni.

*   **Zastosowania:**
    *   Tworzenie niestandardowej regulacji głośności.
    *   Suwak do przełączania między różnymi motywami lub obrazami tła (przy użyciu typu „Lista”).
    *   Dostosowywanie konkretnej opcji Minecrafta, takiej jak jasność lub zasięg renderowania.
*   **Najważniejsze funkcje:**
    *   **Typy:** Może być `Listą wartości` (np. „Łatwy”, „Normalny”, „Trudny”), `Zakresem liczb całkowitych` (np. 1–100) lub `Zakresem liczb dziesiętnych` (np. 0.0–1.0).
    *   **Dynamiczne akcje:** Wykonuje akcje po zmianie wartości. Bieżąca wartość może być używana wraz ze [Zmiennymi](./variables).
    *   **Dostosowywanie:** Etykieta suwaka może dynamicznie wyświetlać jego bieżącą wartość. Tekstury uchwytu i tła można w pełni dostosować, w tym ustawić przezroczyste tło, kolor i skalę etykiety, przełącznik cienia tekstu oraz niestandardowe dźwięki kliknięcia i opuszczenia kursorem.

## Pole wyboru
Standardowe pole wyboru, które można włączać i wyłączać. Może wykonywać akcje po zmianie stanu.

*   **Zastosowania:**
    *   Pole wyboru „Zgadzam się z zasadami”.
    *   Ustawienie włączające lub wyłączające określoną funkcję w niestandardowym menu.
    *   Włączanie lub wyłączanie układu albo zmiennej.
*   **Najważniejsze funkcje:**
    *   **Akcje przy przełączaniu:** Wykonuje [skrypty akcji](./action-scripts), gdy jego stan się zmieni. Bieżący stan (`true` lub `false`) jest dostępny dla tych akcji.
    *   **Tryb zmiennej:** Może być bezpośrednio połączone ze zmienną FancyMenu, dzięki czemu stan pola wyboru jest odczytywany z tej zmiennej i zapisywany w niej.
    *   **Trwały stan:** Gdy tryb zmiennej jest wyłączony, pole wyboru automatycznie zapisuje swój stan według identyfikatora elementu i przywraca go po ponownym uruchomieniu gry. Stany te są przechowywane w `<game-directory>/checkbox_states.json`. W trybie zmiennej połączona zmienna FancyMenu jest źródłem stanu pola wyboru.
    *   **Niestandardowy wygląd:** Obsługuje niestandardowe tekstury tła (dla stanów normalnego, po najechaniu i nieaktywnego) oraz samego znacznika wyboru.

## Pole tekstowe
Pole, w którym użytkownicy mogą wpisywać tekst. Jego zawartość może być połączona ze zmienną FancyMenu, co pozwala przechwytywać i wykorzystywać dane wprowadzone przez użytkownika.

*   **Zastosowania:**
    *   Pole „Adres IP serwera” współpracujące z przyciskiem „Dołącz do serwera”.
    *   Pole do wpisania nazwy gracza na potrzeby podglądu niestandardowej skórki.
    *   Tworzenie podstawowego interfejsu przypominającego logowanie.
*   **Najważniejsze funkcje:**
    *   **Powiązanie ze zmienną:** Przechowuje wprowadzony tekst w określonej [zmiennej](./variables).
    *   **Walidacja danych wejściowych:** Można skonfigurować je tak, aby akceptowało tylko określone typy znaków, np. liczby, adresy URL lub zwykły tekst.
    *   **Maksymalna długość:** Możesz ustawić maksymalną liczbę znaków.
    *   **Wygląd i dźwięki:** Obsługuje niestandardowy kolor tła, kolory i zaokrąglenie obramowania, kolor tekstu, tekst podpowiedzi/elementu zastępczego, kolor podpowiedzi oraz dźwięki najechania, opuszczenia kursorem i kliknięcia.

## Podpowiedź
Pole tekstowe, które może pojawiać się w stałym miejscu lub podążać za kursorem myszy. Jego widoczność jest zwykle kontrolowana za pomocą [Wymagań ładowania](./conditions).

*   **Zastosowania:**
    *   Wyświetlanie szczegółowych informacji po najechaniu użytkownika na przycisk lub obraz.
    *   Tworzenie kontekstowych wskazówek pomocy pojawiających się w określonych warunkach.
    *   Wyświetlanie dynamicznych informacji (np. statusu serwera) obok kursora.
*   **Najważniejsze funkcje:**
    *   **Podążanie za myszą:** Można ustawić podążanie za wskaźnikiem myszy.
    *   **Obsługa Markdown:** Zawartość podpowiedzi obsługuje pełne formatowanie Markdown.
    *   **Niestandardowe tło:** Tło może mieć jednolity kolor lub być niestandardową teksturą z dziewięciokrotnym skalowaniem, zapewniając w pełni dopasowany wygląd.

## Przedmiot
Wyświetla pojedynczy przedmiot Minecrafta, pochodzący z gry podstawowej lub moda.

*   **Zastosowania:**
    *   Używanie przedmiotów jako ikon przycisków lub wyborów w menu.
    *   Tworzenie interfejsu sklepu lub wyboru zestawu.
    *   Wyświetlanie trzymanego przez gracza przedmiotu lub elementu zbroi.
*   **Najważniejsze funkcje:**
    *   **Niestandardowe dane:** Obsługuje niestandardową nazwę, opis, liczbę przedmiotów, połysk zaklęcia i dane NBT. Zobacz [Placeholder danych NBT](./nbt-data-placeholder).
    *   **Wyświetlanie podpowiedzi:** Można skonfigurować wyświetlanie standardowej podpowiedzi przedmiotu po najechaniu.

## Model JSON bloku/przedmiotu
Renderuje model JSON bloku lub przedmiotu z zasobów Minecrafta albo ze źródeł zewnętrznych.

*   **Zastosowania:**
    *   Wyświetlanie trójwymiarowego modelu z paczki zasobów w menu.
    *   Pokazywanie podglądów przedmiotów/bloków z niestandardowymi teksturami.
    *   Budowanie dekoracyjnych elementów interfejsu opartych na modelach.
*   **Najważniejsze funkcje:**
    *   **Źródło modelu:** Może ładować model JSON z zasobów Minecrafta lub źródeł zewnętrznych.
    *   **Nadpisywanie tekstury:** Obsługuje ustawianie niestandardowej tekstury.
    *   **Sterowanie renderowaniem:** Przesunięcie i skala modelu, obrót wokół trzech osi, renderowanie z przezroczystością oraz transformacja modelu GUI.
    *   **Oświetlenie:** Dwa konfigurowalne źródła światła z niezależnym sterowaniem odcieniem i obrotem.

## Obraz
Wyświetla statyczny obraz z pliku lokalnego, adresu URL lub lokalizacji zasobu Minecrafta.

*   **Zastosowania:**
    *   Dodawanie logo serwera lub marki paczki modów.
    *   Tworzenie dekoracyjnych obramowań lub ramek interfejsu.
    *   Wykorzystywanie obrazów jako części bardziej złożonego projektu interfejsu.
*   **Najważniejsze funkcje:**
    *   **Dziewięciokrotne skalowanie:** Skaluje obramowania lub panele bez zniekształcania ich narożników. Zobacz [Dziewięciokrotne skalowanie i kafelkowanie](./nine-slicing-and-tiling).
    *   **Powtarzanie tekstury:** Obraz może być kafelkowany, aby wypełnić obszar elementu.
    *   **Barwienie:** Możesz nałożyć na obraz kolorowy filtr.
    *   **Zaokrąglone narożniki:** Obrazy bez dziewięciokrotnego skalowania i powtarzania mogą mieć zaokrąglone narożniki.
    *   **Efekt paralaksy:** Obraz porusza się wraz z myszą, tworząc wrażenie głębi. Zobacz [Efekt paralaksy](./parallax).

## Tekst
Niezwykle wszechstronny element do wyświetlania tekstu. Można go używać zarówno do pojedynczych etykiet, jak i wielostronicowych, przewijanych dokumentów.

*   **Zastosowania:**
    *   Wyświetlanie zasad serwera, informacji o aktualizacji lub wiadomości powitalnych.
    *   Tworzenie dynamicznych paneli informacyjnych za pomocą [placeholderów](./placeholders), np. `Witaj, {"placeholder":"playername"}!`.
    *   Dodawanie etykiet i opisów do interfejsu.
*   **Najważniejsze funkcje:**
    *   **Źródła treści:** Tekst można wprowadzić bezpośrednio, załadować z pliku lokalnego lub pobrać z adresu URL.
    *   **Obsługa Markdown:** Obsługuje nagłówki, listy, bloki kodu, tabele i inne elementy formatowania Markdown. Zobacz [Formatowanie tekstu](./text-formatting).
    *   **Przewijanie:** Automatycznie staje się przewijalny, jeśli treść jest większa niż obszar elementu. Paski przewijania można dostosować lub wyłączyć.
    *   **Stylizacja:** Pełna kontrola nad kolorem, skalą, wyrównaniem i cieniem tekstu oraz odstępami między wierszami.

## Wideo
Odtwarza plik wideo. Doskonale nadaje się do filmowych wstępów lub dekoracyjnych, zapętlonych teł.

> [!WARNING]
> Natywny element Wideo wymaga **Watermedia V3** i **Watermedia Binaries V3**. Stary element **Wideo [Rinku]** jest przestarzały.

*   **Zastosowania:**
    *   Animowany zwiastun paczki modów lub serwera.
    *   Zapętlone, nastrojowe wideo ożywiające menu.
    *   Samouczek wideo wyświetlany w grze.
*   **Najważniejsze funkcje:**
    *   **Źródła:** Obsługuje lokalne pliki wideo i adresy URL. Zobacz [Wideo](./video).
    *   **Sterowanie odtwarzaniem:** Można włączyć automatyczne zapętlanie. Regulować można głośność, kanał dźwiękowy i zachowanie zachowujące proporcje obrazu.
    *   **Interaktywne sterowanie:** Odtwarzaniem wideo, czasem przewijania i głośnością można sterować za pomocą akcji przycisku.

## Shader GLSL
Renderuje niestandardowy shader GLSL wewnątrz elementu.

*   **Zastosowania:**
    *   Animowane panele shaderów.
    *   Proceduralne efekty wizualne.
    *   Efekty menu w stylu Shadertoy ograniczone do prostokąta elementu.
*   **Najważniejsze funkcje:**
    *   **Środowisko uruchomieniowe shadera:** Obsługuje shadery jedno- i wieloprzebiegowe.
    *   **Obsługa Shadertoy:** Może korzystać z shaderów w stylu Shadertoy z funkcją `mainImage`.
    *   **Uniformy:** Udostępnia uniformy FancyMenu i wejściowe. Zobacz [API shadera GLSL](./glsl-shader-api).

## Pokaz slajdów
Wyświetla sekwencję obrazów. Obrazy i plik konfiguracyjny `properties.txt` znajdują się we własnym podkatalogu pokazu slajdów w `<game-directory>/config/fancymenu/slideshows/`.

*   **Zastosowania:**
    *   Obracająca się galeria zrzutów ekranu z gry.
    *   Prezentowanie najważniejszych funkcji paczki modów.
    *   Dynamiczne tło zmieniające różne sceny.
*   **Najważniejsze funkcje:**
    *   Ładuje wstępnie skonfigurowane [pokazy slajdów](./slideshows).
    *   Można ustawić zachowywanie proporcji obrazów.

## Prostokąt
Prosty prostokąt o jednolitym kolorze.

*   **Zastosowania:**
    *   Tworzenie półprzezroczystego tła za tekstem w celu poprawy czytelności.
    *   Projektowanie prostych paneli interfejsu i separatorów.
    *   Używanie jako kolorowego elementu zastępczego podczas projektowania układu.
*   **Najważniejsze funkcje:**
    *   Obsługuje kolory HEX RGBA, zaokrąglone narożniki i opcjonalne rozmycie, dzięki czemu może pełnić funkcję prostego panelu, filtra lub rozmytego tła.

## Okrąg
Prosty okrąg lub elipsa o jednolitym kolorze.

*   **Zastosowania:**
    *   Tworzenie okrągłych akcentów, wskaźników lub delikatnych obszarów interfejsu.
    *   Budowanie stylizowanych dekoracji interfejsu bez pliku tekstury.
*   **Najważniejsze funkcje:**
    *   Obsługuje kolor, rozmycie oraz konfigurowalną wartość zaokrąglenia/wykładnika.

## Tekst powitalny
Rekreacja charakterystycznego, żółtego i podskakującego tekstu powitalnego Minecrafta z ekranu tytułowego.

*   **Zastosowania:**
    *   Zastępowanie waniliowego tekstu powitalnego własnymi wiadomościami.
    *   Dodawanie przyciągającej wzrok, animowanej wiadomości do dowolnego menu.
*   **Najważniejsze funkcje:**
    *   **Źródła treści:** Może korzystać z domyślnych waniliowych tekstów powitalnych, listy niestandardowych tekstów wprowadzonych bezpośrednio lub tekstu z pliku lokalnego.
    *   **Dostosowywanie:** Możesz włączyć lub wyłączyć efekt podskakiwania oraz dostosować kolor, skalę, obrót i cień tekstu.

## Postać gracza
Renderuje model gracza w menu.

*   **Zastosowania:**
    *   Wyświetlanie postaci bieżącego gracza w menu głównym.
    *   Tworzenie ekranu wyboru drużyny lub podglądu klasy.
    *   Sekcja „profilu” pokazująca skórkę i nazwę gracza.
*   **Najważniejsze funkcje:**
    *   **Dynamiczny wygląd:** Może kopiować skórkę, pelerynę i nazwę bieżącego gracza. Zobacz [Głowy graczy](./player-heads).
    *   **Niestandardowe pozy:** Zapewnia szczegółową kontrolę nad obrotem głowy, ciała, rąk i nóg. Głowę i ciało można również ustawić tak, aby podążały za kursorem myszy.
    *   **Atrybuty:** Można ustawić postać jako dziecko, kucającą lub korzystającą ze smukłego modelu.

## Przeglądarka
Element renderujący aktywną stronę internetową wewnątrz gry.

Ten element wymaga zainstalowanego i działającego moda **[Rinku](https://modrinth.com/mod/rinku)**!

Rinku możesz pobrać z oficjalnych stron projektu w serwisach [CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku) i [Modrinth](https://modrinth.com/mod/rinku).

*   **Zastosowania:**
    *   Wyświetlanie aktywnej mapy Dynmap serwera.
    *   Osadzanie odtwarzacza filmów YouTube.
    *   Wyświetlanie wiki lub dokumentacji bezpośrednio w grze.
*   **Najważniejsze funkcje:**
    *   **Interaktywność:** Może być w pełni interaktywna, umożliwiając klikanie odnośników, przewijanie i wpisywanie tekstu.
    *   **Sterowanie multimediami:** Oferuje opcje wyciszania multimediów, zapętlania filmów i ukrywania elementów sterujących wideo na załadowanej stronie.

### Ładowanie lokalnych plików HTML
Element Przeglądarka może ładować lokalne dokumenty HTML z `<game-directory>/config/fancymenu/assets/`.

Aby załadować lokalny plik HTML, rozpocznij adres URL od `file:///`, a następnie podaj KRÓTKĄ ścieżkę do pliku, np. `/config/fancymenu/assets/cool_changelog.html`, co da adres: `file:///config/fancymenu/assets/cool_changelog.html`.

W systemie **Linux** użyj [placeholdera **Absolute File/Folder Path**](./placeholders#absolute-filefolder-path-absolute_path) zamiast wpisywać na stałe ścieżkę bezwzględną zależną od konkretnej instancji: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Krótka ścieżka w systemie Linux musi zaczynać się od `/`, jak pokazano w przykładzie.

## Animator elementów
Zaawansowane narzędzie do tworzenia złożonych animacji opartych na klatkach kluczowych. Może animować położenie, rozmiar i punkt zakotwiczenia jednego lub wielu innych elementów.

*   **Zastosowania:**
    *   Wysuwanie elementów na ekran lub ich chowanie.
    *   Zmienianie rozmiaru paneli lub powiadomień.
    *   Animowanie przesunięć pozycji i przejść punktów zakotwiczenia.
*   **Najważniejsze funkcje:**
    *   **Edytor klatek kluczowych:** Dedykowany edytor do dodawania, edytowania i porządkowania klatek kluczowych na osi czasu.
    *   **Wiele celów:** Jeden Animator może jednocześnie sterować wieloma elementami „docelowymi”.
    *   **Sterowanie:** Animacje można zapętlać. Możesz też wybrać animowanie wyłącznie pozycji lub rozmiaru.
    *   **Przesunięcia czasowe:** Elementy docelowe mogą korzystać z indywidualnych lub losowych przesunięć czasu rozpoczęcia.
    *   Zobacz [Animator elementów](./element-animator), aby dowiedzieć się, jak go skonfigurować i edytować klatki kluczowe.

## Wyzwalacz czasowy
Niewidoczny element wykonujący listę akcji w regularnych odstępach (przy każdym „ticku”).

> [!NOTE]
> Do automatyzacji działającej w tle rozważ użycie [Harmonogramów](./schedulers). Harmonogramy są globalne i mogą działać niezależnie od konkretnego ekranu.

*   **Zastosowania:**
    *   Okresowe sprawdzanie statusu serwera i aktualizowanie elementu tekstowego.
    *   Tworzenie odliczania aktualizującego etykietę tekstową.
    *   Wielokrotne uruchamianie skryptu w celu tworzenia niestandardowych zachowań.
*   **Najważniejsze funkcje:**
    *   **Sterowanie czasem:** Możesz ustawić opóźnienie między tickami w milisekundach.
    *   **Tryby ticków:** Można ustawić ciągłe wykonywanie, jednokrotne wykonanie podczas sesji gry lub wykonanie raz przy każdym załadowaniu menu.
    *   **Asynchroniczność:** Może wykonywać swoje [akcje](./action-scripts) oddzielnie, choć niektóre akcje nie mogą działać przy włączonej tej opcji.

## Dźwięk
Niewidoczny element odtwarzający pliki dźwiękowe. Może zarządzać listą odtwarzania utworów i oferuje różne opcje sterowania odtwarzaniem.

*   **Zastosowania:**
    *   Dodawanie niestandardowej muzyki tła do menu.
    *   Tworzenie odtwarzacza muzyki z przyciskami sterującymi odtwarzaniem (następny/poprzedni utwór, głośność).
    *   Odtwarzanie nastrojowych pejzaży dźwiękowych.
*   **Najważniejsze funkcje:**
    *   **Lista odtwarzania:** Może zarządzać wieloma utworami dźwiękowymi.
    *   **Tryby odtwarzania:** Może odtwarzać utwory po kolei lub losowo (z obsługą wag utworów, dzięki czemu niektóre mogą pojawiać się częściej niż inne).
    *   **Sterowanie:** Obsługuje zapętlanie, regulację głośności i wybór kanału dźwiękowego. Zobacz [Muzyka tła menu](./background-music).

## Kontroler muzyki
Niewidoczny element służący do sterowania domyślnym odtwarzaniem muzyki Minecrafta w określonym menu.

*   **Zastosowania:**
    *   Wyłączanie domyślnej muzyki menu na ekranie, na którym chcesz odtwarzać własną muzykę za pomocą elementu [**Dźwięk**](#audio).
    *   Zatrzymywanie muzyki ze świata, aby nie była odtwarzana po otwarciu menu w grze.
*   **Najważniejsze funkcje:**
    *   Oddzielne przełączniki do sterowania waniliową „Muzyką menu” i „Muzyką świata”.

## Pasek postępu
Konfigurowalny pasek, który wizualnie przedstawia wartość liczbową.

*   **Zastosowania:**
    *   Pasek ładowania śledzący postęp ładowania świata za pomocą `{"placeholder":"world_load_progress"}`.
    *   Wizualne paski zdrowia, głodu lub doświadczenia w interfejsie gry.
    *   Wskaźnik głośności sterowany przez element [**Suwak**](#slider).
*   **Najważniejsze funkcje:**
    *   **Dynamiczna wartość:** Wartość postępu (0–100 lub 0.0–1.0) jest ustawiana w polu tekstowym obsługującym [placeholdery](./placeholders).
    *   **Wygląd:** Kierunek paska (góra, dół, lewo, prawo), kolory, tekstury oraz dziewięciokrotne skalowanie tekstur paska i tła można w pełni dostosować.
    *   **Animacja:** Płynna animacja wypełniania sprawia, że zmiany postępu są mniej gwałtowne.
    *   **Zakotwiczenie elementu zależne od postępu:** Gdy inny element używa paska postępu jako zakotwiczenia **Element**, włącz **Użyj postępu jako zakotwiczenia elementu**, aby przenieść to zakotwiczenie na bieżącą krawędź wypełnionego obszaru. Zakotwiczone elementy będą wtedy poruszać się wraz z postępem paska, zamiast pozostawać przy jego statycznych granicach.

## Przeciągacz
Niewidoczny element, który użytkownik może kliknąć i przeciągać. Inne elementy można do niego zakotwiczyć, aby tworzyć ruchome widżety.

*   **Zastosowania:**
    *   Tworzenie przeciąganego zegara lub panelu informacyjnego.
    *   Umożliwianie użytkownikom dostosowania położenia elementów interfejsu do własnych preferencji.
*   **Najważniejsze funkcje:**
    *   **Opcjonalna trwałość:** Włącz **Zapisuj przesunięcie przeciągnięcia użytkownika**, aby zachować pozycję przeciągniętego elementu po ponownym otwarciu ekranu i ponownym uruchomieniu gry. Wyłącz tę opcję, aby resetować przesunięcie.
    *   **Punkt zakotwiczenia:** Działa jako ruchomy punkt zakotwiczenia dla innych elementów, co jest kluczową częścią sekcji [Pozycjonowanie elementów](./positioning-elements).

## Kursor
Niewidoczny element, który zastępuje domyślny kursor systemowy niestandardowym obrazem, gdy układ jest aktywny.

*   **Zastosowania:**
    *   Tworzenie w pełni stylizowanego interfejsu pasującego do estetyki paczki modów.
*   **Najważniejsze funkcje:**
    *   **Niestandardowa tekstura:** Użyj dowolnego obrazu jako kursora.
    *   **Punkt aktywny:** Określa dokładny piksel obrazu używany jako punkt kliknięcia. Zobacz [Niestandardowy kursor](./custom-cursor).
