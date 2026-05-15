---
title: Elementy
description: 'Wszystko, co warto wiedzieć o typach elementów FancyMenu.'
---

# Elementy

Elementy są podstawowymi składnikami Twoich własnych układów w FancyMenu. Możesz dodawać je do dowolnego układu, aby wyświetlać informacje, dodać interaktywność lub tworzyć efektowne efekty wizualne.

# Dodawanie elementów do układu

Nowy element możesz dodać do swojego układu w **Edytorze układu**.

1.  **Kliknij prawym przyciskiem myszy** tło edytora, aby otworzyć menu kontekstowe.
2.  Najedź na **Nowy element**.
3.  Pojawi się lista wszystkich dostępnych typów elementów. Kliknij ten, który chcesz dodać.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Gdy element zostanie dodany, możesz go przesuwać, zmieniać jego rozmiar i dostosowywać go, **klikając prawym przyciskiem myszy** na nim, aby otworzyć jego własne menu kontekstowe. Aby dowiedzieć się więcej o rozmieszczaniu elementów, zobacz strony [Pozycjonowanie elementów](https://docs.fancymenu.net/en/positioning-elements) i [Identyfikatory elementów](https://docs.fancymenu.net/en/element-identifiers).

# Szczegóły elementów

Poniższa lista zawiera większość, jeśli nie wszystkie, elementy dostępne w FancyMenu. Lista może czasami być nieco nieaktualna z powodu aktualizacji FancyMenu.

## Przycisk
Klikalny przycisk, który może wykonywać szeroki zakres działań. To jeden z najmocniejszych i najbardziej wszechstronnych elementów do tworzenia interaktywnych menu.

*   **Zastosowania:**
    *   Tworzenie przycisku „Dołącz do Discorda” lub „Odwiedź stronę”.
    *   Dodanie przycisku szybkiego dołączania do konkretnego serwera.
    *   Budowanie własnej nawigacji między różnymi menu.
    *   Tworzenie przycisków, które włączają lub wyłączają inne układy.
*   **Najważniejsze funkcje:**
    *   **Akcje:** Może wykonywać sekwencję działań, takich jak otwieranie adresu URL, dołączanie do serwera, wysyłanie komendy na czat, naśladowanie działania innego przycisku, sterowanie zmiennymi i wiele więcej. Więcej informacji znajdziesz w dokumentacji [Skrypty akcji](https://docs.fancymenu.net/en/action-scripts).
    *   **Własny wygląd:** W pełni konfigurowalne tekstury dla stanów normalnego, podświetlonego i nieaktywnego. Obsługuje przezroczyste tła, nine-slicing, własne kolory etykiet, kolory etykiet po najechaniu, skalę etykiety, przełączanie cienia tekstu oraz tekstury ikon przycisku.
    *   **Dźwięki:** Własne dźwięki kliknięcia, najechania i opuszczenia.
    *   **Tryb szablonu:** Może działać jako szablon, aby zastosować swój wygląd i właściwości do wszystkich innych przycisków Vanilla lub modowanych w menu, zapewniając spójny wygląd. Więcej informacji znajdziesz na stronie [Szablony przycisków i suwaków](https://docs.fancymenu.net/en/button-slider-templates).

## Suwak
Suwak, który użytkownicy mogą przeciągać, aby wybrać wartość z listy lub zakresu. Może wykonywać akcje za każdym razem, gdy jego wartość się zmienia.

*   **Zastosowania:**
    *   Tworzenie własnej regulacji głośności.
    *   Suwak do przełączania między różnymi motywami lub obrazami tła (z użyciem typu „Lista”).
    *   Dostosowywanie konkretnej opcji Minecrafta, takiej jak jasność lub zasięg renderowania.
*   **Najważniejsze funkcje:**
    *   **Typy:** Może być `Lista wartości` (np. „Łatwy”, „Normalny”, „Trudny”), `Zakres liczb całkowitych` (np. 1–100) lub `Zakres dziesiętny` (np. 0.0–1.0).
    *   **Dynamiczne akcje:** Wykonuje akcje przy zmianie wartości. Bieżąca wartość suwaka może być używana w jego akcjach do wykonywania dynamicznych zadań, co można łączyć ze [Zmienne](https://docs.fancymenu.net/en/variables).
    *   **Dostosowanie:** Etykieta suwaka może dynamicznie wyświetlać jego bieżącą wartość. Tekstury uchwytu i tła są w pełni konfigurowalne, w tym przezroczyste tła, opcje koloru/skali etykiety, przełączanie cienia tekstu oraz własne dźwięki kliknięcia/opuszczenia.

## Checkbox
Standardowy checkbox, który można włączać i wyłączać. Może wykonywać akcje po zmianie stanu.

*   **Zastosowania:**
    *   Checkbox „Akceptuję zasady”.
    *   Ustawienie włączające lub wyłączające konkretną funkcję w Twoim własnym menu.
    *   Przełączanie układu lub zmiennej włącz/wyłącz.
*   **Najważniejsze funkcje:**
    *   **Akcje przy przełączeniu:** Wykonuje [Skrypty akcji](https://docs.fancymenu.net/en/action-scripts) po zmianie stanu. Bieżący stan (`true` lub `false`) jest dostępny w jego akcjach.
    *   **Tryb zmiennej:** Może być bezpośrednio powiązany ze zmienną FancyMenu, dzięki czemu stan checkboxa odczytuje i zapisuje do tej zmiennej.
    *   **Własny wygląd:** Obsługuje własne tekstury tła (w stanach normalnym, po najechaniu i nieaktywnym) oraz samego znacznika wyboru.

## Pole tekstowe
Pole, w którym użytkownicy mogą wpisywać tekst. Jego zawartość może być powiązana ze zmienną FancyMenu, co pozwala przechwytywać i wykorzystywać dane wprowadzane przez użytkownika.

*   **Zastosowania:**
    *   Pole „IP serwera” współpracujące z przyciskiem „Dołącz do serwera”.
    *   Pole do wpisania nazwy gracza dla własnego podglądu skina.
    *   Tworzenie prostego interfejsu przypominającego logowanie.
*   **Najważniejsze funkcje:**
    *   **Powiązanie ze zmienną:** Tekst wpisany przez użytkownika jest zapisywany w określonej [zmiennej](https://docs.fancymenu.net/en/variables).
    *   **Walidacja danych wejściowych:** Można skonfigurować tak, aby akceptowało tylko określone typy znaków, takie jak liczby, adresy URL lub zwykły tekst.
    *   **Maksymalna długość:** Możesz ustawić maksymalną liczbę znaków dla wpisywanego tekstu.
    *   **Wygląd i dźwięki:** Obsługuje własny kolor tła, kolory obramowania, zaokrąglenie obramowania, kolor tekstu, tekst podpowiedzi/placeholdera, kolor podpowiedzi, dźwięki najechania, opuszczenia i kliknięcia.

## Tooltip
Pole tekstowe, które można skonfigurować tak, aby pojawiało się w określonym miejscu lub podążało za kursorem myszy. Jego widoczność jest zwykle kontrolowana przez [Warunki (wymagania ładowania)](https://docs.fancymenu.net/en/conditions).

*   **Zastosowania:**
    *   Wyświetlanie szczegółowych informacji po najechaniu na przycisk lub obraz.
    *   Tworzenie podpowiedzi kontekstowych pojawiających się w określonych warunkach.
    *   Pokazywanie dynamicznych informacji (np. statusu serwera) obok kursora.
*   **Najważniejsze funkcje:**
    *   **Podążanie za myszą:** Może podążać za wskaźnikiem myszy.
    *   **Obsługa Markdown:** Treść tooltipa obsługuje pełne formatowanie Markdown.
    *   **Własne tło:** Tło może być jednolitym kolorem lub własną teksturą z nine-slicing, co pozwala uzyskać w pełni spójny motyw.

## Przedmiot
Wyświetla pojedynczy przedmiot Minecrafta, zarówno vanilla, jak i z moda.

*   **Zastosowania:**
    *   Używanie przedmiotów jako ikon przycisków lub wyborów w menu.
    *   Tworzenie GUI sklepu lub wyboru zestawu.
    *   Wyświetlanie przedmiotu trzymanego przez gracza lub zbroi.
*   **Najważniejsze funkcje:**
    *   **Własne dane:** Możesz ustawić nazwę przedmiotu, lore, ilość, efekt połysku zaklęcia, a nawet własne dane NBT. Więcej o używaniu NBT znajdziesz w dokumentacji [Placeholder danych NBT](https://docs.fancymenu.net/en/nbt-data-placeholder).
    *   **Wyświetlanie tooltipa:** Można skonfigurować tak, aby po najechaniu pokazywał standardowy tooltip przedmiotu.

## Model JSON bloku/przedmiotu
Renderuje model JSON bloku lub przedmiotu z zasobów Minecrafta albo zewnętrznych źródeł.

*   **Zastosowania:**
    *   Wyświetlanie modelu 3D z paczki zasobów w menu.
    *   Pokazywanie podglądów przedmiotów/bloków z własnymi teksturami.
    *   Budowanie dekoracyjnych elementów interfejsu opartych na modelach.
*   **Najważniejsze funkcje:**
    *   **Źródło modelu:** Może wczytywać JSON modelu z zasobów Minecrafta lub zewnętrznych źródeł.
    *   **Zastępowanie tekstur:** Obsługuje ustawienie własnej tekstury.
    *   **Kontrola renderowania:** Obejmuje kontrolę obrotu i oświetlenia.

## Obraz
Wyświetla statyczny obraz z lokalnego pliku, adresu URL w sieci lub lokalizacji zasobu Minecrafta.

*   **Zastosowania:**
    *   Dodanie logo serwera lub marki modpacka.
    *   Tworzenie dekoracyjnych ramek lub obramowań interfejsu.
    *   Używanie obrazów jako części bardziej złożonego projektu UI.
*   **Najważniejsze funkcje:**
    *   **Nine-slicing:** Pozwala używać obrazu jako skalowalnej ramki lub panelu bez zniekształcania rogów. Więcej informacji znajdziesz na stronie [Nine-Slicing i Tiling](https://docs.fancymenu.net/en/nine-slicing-and-tiling).
    *   **Powtarzanie tekstury:** Obraz może być kafelkowany, aby wypełnić obszar elementu.
    *   **Kolorowanie:** Możesz nałożyć na obraz kolorowy tint.
    *   **Zaokrąglone rogi:** Obrazy bez nine-slicing i bez powtarzania mogą mieć zaokrąglone rogi.
    *   **Efekt paralaksy:** Można go skonfigurować tak, aby poruszał się lekko wraz z myszą, dając efekt 3D. Więcej znajdziesz na stronie [Efekt paralaksy](https://docs.fancymenu.net/en/parallax).

## Tekst
Bardzo wszechstronny element do wyświetlania tekstu. Może służyć do wszystkiego — od jednowierszowych etykiet po wielostronicowe, przewijane dokumenty.

*   **Zastosowania:**
    *   Wyświetlanie zasad serwera, notatek z aktualizacji lub wiadomości powitalnych.
    *   Tworzenie dynamicznych paneli informacyjnych z użyciem [placeholderów](https://docs.fancymenu.net/en/placeholders), np. „Witaj, `{"placeholder":"playername"}`!”.
    *   Dodawanie etykiet i opisów do interfejsu.
*   **Najważniejsze funkcje:**
    *   **Źródła treści:** Tekst można wpisać bezpośrednio, wczytać z lokalnego pliku lub pobrać z adresu URL.
    *   **Obsługa Markdown:** Obsługuje szeroki zakres Markdown do formatowania bogatego tekstu, w tym nagłówki, listy, bloki kodu i tabele. Wygląd elementów Markdown jest w pełni konfigurowalny. Więcej informacji znajdziesz na stronie [Formatowanie tekstu](https://docs.fancymenu.net/en/text-formatting).
    *   **Przewijanie:** Automatycznie staje się przewijalny, jeśli treść jest większa niż obszar elementu. Paski przewijania można dostosować lub wyłączyć.
    *   **Stylizacja:** Pełna kontrola nad kolorem tekstu, skalą, wyrównaniem, cieniem i odstępami między liniami.

## Wideo
Odtwarza plik wideo. To idealne rozwiązanie do filmowych intro lub dekoracyjnych, zapętlonych teł.

> Nowy natywny element Video w FancyMenu 3.9.0 wymaga **Watermedia V3** oraz **Watermedia Binaries V3**. Stary element **Video [MCEF]** jest przestarzały.
{.is-warning}

*   **Zastosowania:**
    *   Animowany trailer modpacka lub serwera.
    *   Zapętlone, ambientowe wideo, które ożywi menu.
    *   Film instruktażowy w grze.
*   **Najważniejsze funkcje:**
    *   **Źródła:** Obsługuje zarówno lokalne pliki wideo, jak i adresy URL. Szczegóły znajdziesz na stronie [Wideo (MP4)](https://docs.fancymenu.net/en/video).
    *   **Sterowanie odtwarzaniem:** Może być ustawione na automatyczne zapętlanie. Głośność, kanał dźwięku i zachowanie zachowujące proporcje obrazu są konfigurowalne.
    *   **Sterowanie interaktywne:** Odtwarzaniem wideo, czasem przewijania i głośnością można sterować za pomocą akcji przycisków.

## Shader GLSL
Renderuje własny shader GLSL wewnątrz elementu.

*   **Zastosowania:**
    *   Animowane panele shaderów.
    *   Proceduralne efekty wizualne.
    *   Efekty menu w stylu Shadertoy przycięte do prostokąta elementu.
*   **Najważniejsze funkcje:**
    *   **Środowisko uruchomieniowe shaderów:** Obsługuje shadery jednoprzebiegowe i wieloprzebiegowe.
    *   **Obsługa Shadertoy:** Może używać shaderów `mainImage` w stylu Shadertoy.
    *   **Uniformy:** Udostępnia uniformy FancyMenu i wejściowe. Szczegóły znajdziesz na stronie [API shadera GLSL](https://docs.fancymenu.net/en/glsl-shader-api).

## Pokaz slajdów
Wyświetla sekwencję obrazów. Konfiguracja pokazu slajdów (obrazy, czas, przejścia) odbywa się w osobnym pliku `.properties` znajdującym się w katalogu `/config/fancymenu/assets/slideshows/`.

*   **Zastosowania:**
    *   Obracająca się galeria zrzutów ekranu z gry.
    *   Prezentowanie najważniejszych funkcji modpacka.
    *   Dynamiczne tło, które przełącza się między różnymi scenami.
*   **Najważniejsze funkcje:**
    *   Wczytuje wstępnie skonfigurowane pokazy slajdów. Instrukcje konfiguracji znajdziesz w dokumentacji [Pokazy slajdów](https://docs.fancymenu.net/en/slideshows).
    *   Można ustawić zachowanie proporcji obrazów.

## Prostokątna forma
Prosty prostokąt w jednolitym kolorze.

*   **Zastosowania:**
    *   Tworzenie półprzezroczystego tła za tekstem w celu poprawy czytelności.
    *   Projektowanie prostych paneli i separatorów UI.
    *   Jako kolorowy element zastępczy podczas projektowania układu.
*   **Najważniejsze funkcje:**
    *   Obsługuje kolory HEX RGBA, zaokrąglone rogi i opcjonalne rozmycie, dzięki czemu kształt może działać jako prosty panel, tint lub rozmyte tło.

## Okrągła forma
Prosty okrąg/owal w jednolitym kolorze.

*   **Zastosowania:**
    *   Tworzenie okrągłych akcentów, wskaźników lub miękkich obszarów UI.
    *   Budowanie dekoracji interfejsu o określonym motywie bez pliku tekstury.
*   **Najważniejsze funkcje:**
    *   Działa podobnie jak element Prostokątna forma i obsługuje wizualne dostosowanie koloru/rozmycia.

## Tekst „Splash”
Odtworzenie ikonicznego żółtego, podskakującego tekstu „splash” z ekranu tytułowego Minecrafta.

*   **Zastosowania:**
    *   Zastąpienie vanilla splash text własnymi, niestandardowymi wiadomościami.
    *   Dodanie przyciągającej uwagę, animowanej wiadomości do dowolnego menu.
*   **Najważniejsze funkcje:**
    *   **Źródła treści:** Może używać domyślnych vanilla splashy, listy własnych tekstów wpisanych bezpośrednio lub tekstu z lokalnego pliku.
    *   **Dostosowanie:** Możesz włączyć efekt podskakiwania i dostosować kolor tekstu, skalę, obrót oraz cień.

## Encja gracza
Renderuje model gracza w menu.

*   **Zastosowania:**
    *   Wyświetlanie aktualnej postaci gracza w menu głównym.
    *   Tworzenie ekranu wyboru drużyny lub klasy.
    *   Sekcja „profil” pokazująca skina i nazwę gracza.
*   **Najważniejsze funkcje:**
    *   **Dynamiczny wygląd:** Można skonfigurować tak, aby automatycznie kopiowała skina, pelerynę i nazwę aktualnego gracza. Więcej na ten temat znajdziesz w poradniku [Głowy graczy](https://docs.fancymenu.net/en/player-heads).
    *   **Własne pozy:** Oferuje precyzyjną kontrolę nad obrotem głowy, ciała, rąk i nóg. Głowę i ciało można również ustawić tak, aby podążały za kursorem myszy.
    *   **Atrybuty:** Można ustawić, aby była to wersja dziecięca, kucająca lub miała smukły model.

## Przeglądarka
Element renderujący aktywną stronę internetową wewnątrz gry.

Ten element wymaga zainstalowanego i działającego moda **MCEF (Minecraft Chromium Embedded Framework)**!

MCEF można pobrać z oficjalnych stron projektu na [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) i [Modrinth](https://modrinth.com/mod/mcef).

Dla nowszych wersji Minecrafta (1.21.5+) oficjalne projekty MCEF nie udostępniają buildów, ale istnieje fork z buildami dla najnowszych wersji Minecrafta, który można znaleźć [tutaj](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) i [tutaj](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Ten fork jest utrzymywany przez Keksuccino, aby jak najszybciej udostępniać buildy dla najnowszych wersji Minecrafta.

*   **Zastosowania:**
    *   Wyświetlanie na żywo Dynmapy serwera.
    *   Osadzanie odtwarzacza wideo z YouTube.
    *   Pokazywanie wiki lub strony dokumentacji bezpośrednio w grze.
*   **Najważniejsze funkcje:**
    *   **Interaktywność:** Może być w pełni interaktywny, pozwalając użytkownikom klikać linki, przewijać i pisać.
    *   **Kontrola multimediów:** Oferuje opcje wyciszania multimediów, zapętlania wideo oraz ukrywania kontrolek wideo na wczytanej stronie.

### Wczytywanie lokalnych plików HTML
Element Przeglądarka pozwala wczytywać lokalne dokumenty HTML z `/config/fancymenu/assets/`! Oznacza to, że możesz wyświetlać lokalnie renderowaną zawartość przeglądarkową dla efektownych changelogów i nie tylko.

Aby wczytać lokalny plik HTML, rozpocznij adres URL od `file:///`, a następnie podaj KRÓTĄ ścieżkę pliku, na przykład `/config/fancymenu/assets/cool_changelog.html`, co da taki adres: `file:///config/fancymenu/assets/cool_changelog.html`.

W **Linuksie** musisz podać bezwzględną ścieżkę do pliku, ale ponieważ wpisanie na sztywno bezwzględnej ścieżki zepsułoby układ, musisz pozwolić, aby placeholder dynamicznie przekształcił krótką ścieżkę w bezwzględną: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

BARDZO WAŻNE jest, aby na Linuksie krótka ścieżka zaczynała się od `/`, jak w przykładzie powyżej. Bez tego nie zadziała.

## Animator elementów
Potężne narzędzie do tworzenia złożonych animacji opartych na klatkach kluczowych. Może animować pozycję, rozmiar i punkt zakotwiczenia jednego lub wielu innych elementów.

*   **Zastosowania:**
    *   Tworzenie efektownej animacji intro, w której elementy menu wjeżdżają lub pojawiają się z zanikiem.
    *   Sprawianie, by elementy dekoracyjne pulsowały, obracały się lub poruszały po ścieżce.
    *   Animowanie powiadomienia tak, aby pojawiło się, a potem zniknęło.
*   **Najważniejsze funkcje:**
    *   **Edytor klatek kluczowych:** Dedykowany edytor do dodawania, edytowania i układania klatek kluczowych na osi czasu.
    *   **Wiele celów:** Jeden Animator może jednocześnie sterować wieloma elementami „docelowymi”.
    *   **Sterowanie:** Animacje mogą być zapętlone. Możesz też wybrać animowanie tylko pozycji albo rozmiaru.
    *   **Przesunięcia czasowe:** Elementy docelowe mogą używać indywidualnych lub losowych przesunięć czasu startu.
    *   **[Dowiedz się więcej o Animatorze elementów.](https://docs.fancymenu.net/en/element-animator)**

## Ticker
Niewidoczny element, który wykonuje listę akcji w regularnych odstępach czasu (co „tick”).

> Do nowej automatyzacji w tle w FancyMenu 3.9.0+ rozważ użycie [Harmonogramów](https://docs.fancymenu.net/en/schedulers). Harmonogramy są globalne, łatwiejsze do uporządkowania i mogą działać niezależnie od konkretnego ekranu.
{.is-info}

*   **Zastosowania:**
    *   Okresowe sprawdzanie statusu online serwera i aktualizowanie elementu tekstowego.
    *   Tworzenie odliczania, które aktualizuje etykietę tekstową.
    *   Wielokrotne uruchamianie skryptu w celu tworzenia własnych zachowań.
*   **Najważniejsze funkcje:**
    *   **Kontrola czasu:** Możesz ustawić opóźnienie między tickami w milisekundach.
    *   **Tryby tickowania:** Może działać ciągle, tylko raz na sesję gry albo raz za każdym razem, gdy menu jest ładowane.
    *   **Asynchroniczność:** Może uruchamiać swoje [akcje](https://docs.fancymenu.net/en/action-scripts) w osobnym wątku, aby nie wpływać na wydajność gry, choć niektórych akcji nie można w ten sposób uruchomić.

## Audio
Niewidoczny element odtwarzający pliki audio. Może zarządzać playlistą utworów i oferuje różne opcje sterowania odtwarzaniem.

*   **Zastosowania:**
    *   Dodawanie własnej muzyki w tle do menu.
    *   Tworzenie odtwarzacza muzyki z przyciskami do sterowania odtwarzaniem (następny/poprzedni utwór, głośność).
    *   Odtwarzanie ambientowych dźwięków.
*   **Najważniejsze funkcje:**
    *   **Playlista:** Może zarządzać wieloma ścieżkami audio.
    *   **Tryby odtwarzania:** Może odtwarzać utwory po kolei lub losowo (z obsługą wag utworów, aby niektóre były odtwarzane częściej niż inne).
    *   **Sterowanie:** Obsługuje zapętlanie, regulację głośności i może być przypisany do określonego kanału dźwięku (np. Master, Muzyka). Więcej informacji znajdziesz na stronie [Muzyka w tle menu](https://docs.fancymenu.net/en/background-music).

## Kontroler muzyki
Niewidoczny element służący do sterowania domyślnym odtwarzaniem muzyki Minecrafta w określonym menu.

*   **Zastosowania:**
    *   Wyłączenie domyślnej muzyki menu na ekranie, na którym chcesz odtwarzać własną muzykę za pomocą elementu **Audio**.
    *   Zatrzymanie muzyki z gry, aby nie odtwarzała się dalej po otwarciu menu w grze.
*   **Najważniejsze funkcje:**
    *   Osobne przełączniki do kontrolowania vanilla „Menu Music” i „World Music”.

## Pasek postępu
Konfigurowalny pasek, który wizualnie przedstawia wartość liczbową.

*   **Zastosowania:**
    *   Pasek ładowania śledzący postęp wczytywania świata za pomocą `{"placeholder":"world_load_progress"}`.
    *   Wizualne paski zdrowia, głodu lub doświadczenia dla HUD-u w grze.
    *   Wskaźnik głośności sterowany elementem **Suwak**.
*   **Najważniejsze funkcje:**
    *   **Dynamiczna wartość:** Wartość postępu (0–100 lub 0.0–1.0) ustawiana jest za pomocą pola tekstowego obsługującego [placeholdery](https://docs.fancymenu.net/en/placeholders).
    *   **Wygląd:** Kierunek paska (góra, dół, lewo, prawo), kolory, tekstury oraz nine-slicing tekstur paska/tła są w pełni konfigurowalne.
    *   **Animacja:** Oferuje płynne wypełnianie, dzięki czemu zmiany postępu wyglądają mniej gwałtownie.

## Przeciągacz
Niewidoczny element, który użytkownik może kliknąć i przeciągnąć, aby go przesunąć. Inne elementy można do niego zakotwiczyć, tworząc ruchome widżety.

*   **Zastosowania:**
    *   Tworzenie przeciągalnego zegara lub panelu informacyjnego.
    *   Umożliwienie użytkownikom dostosowania położenia elementów UI do własnych preferencji.
*   **Najważniejsze funkcje:**
    *   **Trwała pozycja:** Przesunięcie wynikające z przeciągania jest zapisywane, więc element pozostaje tam, gdzie użytkownik go zostawił, nawet po ponownym uruchomieniu gry.
    *   **Punkt zakotwiczenia:** Działa jako ruchomy punkt zakotwiczenia dla innych elementów, co jest kluczową częścią [Pozycjonowania elementów](https://docs.fancymenu.net/en/positioning-elements).

## Kursor
Niewidoczny element, który zastępuje domyślny kursor systemowy własnym obrazem, gdy układ jest aktywny.

*   **Zastosowania:**
    *   Tworzenie w pełni tematycznego UI pasującego do estetyki Twojego modpacka.
*   **Najważniejsze funkcje:**
    *   **Własna tekstura:** Możesz użyć dowolnego obrazu jako kursora.
    *   **Hotspot:** Możesz określić dokładny piksel na obrazie, który będzie pełnił funkcję „punktu kliknięcia”. Więcej informacji znajdziesz w poradniku [Własny kursor](https://docs.fancymenu.net/en/custom-cursor).
