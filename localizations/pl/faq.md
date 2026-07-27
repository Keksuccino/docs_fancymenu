---
title: FAQ
description: Często zadawane pytania.
---
# FAQ

### Potrzebuję pomocy z problemem. Jakie informacje powinienem podać?

Aby uzyskać najlepszą pomoc, podaj jak najwięcej kontekstu:
1.  **Jasny opis problemu:** Czego się spodziewałeś, a co faktycznie się stało?
2.  **Plik `latest.log`:** Znajdziesz go w `<game-directory>/logs/latest.log`. **Nie wysyłaj logu awarii** (crash log), chyba że zostaniesz o to wyraźnie poproszony; `latest.log` zwykle zawiera potrzebny kontekst. Do publikacji użyj strony takiej jak https://gist.github.com.
3.  **Twoja wersja Minecrafta:** (np. 1.20.1)
4.  **Twój mod loader i jego wersja:** (np. Forge 47.2.0, Fabric 0.15.7)
5.  **Twoja wersja FancyMenu:** (np. 3.5.2)
6.  **Zrzuty ekranu lub nagrania wideo** problemu również mogą być bardzo pomocne.

### Jak zmienić warstwowanie elementów (przesunąć coś przed lub za inny element)?

*   **Własny vs. własny:** Otwórz **Window -> Editor Widgets -> Layers** i przeciągnij elementy w hierarchii. Możesz też kliknąć element prawym przyciskiem myszy i użyć **Move One Layer Up/Down**. Zobacz [Warstwy i grupy](./layers-and-groups).
*   **Własny vs. Vanilla:** Aby renderować wszystkie własne elementy za wszystkimi elementami vanilla (np. umieścić obraz tła za domyślnymi przyciskami), **kliknij prawym przyciskiem myszy tło edytora** i włącz opcję **"Render Custom Elements Behind Vanilla"**.

### Czy mogę wykluczyć niektóre przyciski z uniwersalnego szablonu przycisku?

**Nie. Jeśli przycisk szablonu ma ustawione własne tekstury, są one zawsze współdzielone ze wszystkimi powiązanymi elementami. Nie można wykluczyć pojedynczych przycisków.**

### Jak sprawić, by przycisk coś robił po kliknięciu?

Użyj [**Skryptu akcji**](./action-scripts).
1.  Kliknij przycisk prawym przyciskiem myszy w edytorze.
2.  Wybierz **Edit Action Script**.
3. Kliknij **Add Action** i wybierz akcję, taką jak [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) lub [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Czy mogę utworzyć zupełnie nowy ekran menu od podstaw?

Użyj [**Custom GUI**](./custom-guis).
1.  Na pasku menu przejdź do **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Kliknij **"New GUI"** i nadaj mu unikalny identyfikator.
3.  Następnie możesz otworzyć ten nowy, pusty ekran i stworzyć dla niego układ, dodając dowolne elementy.
4. Otwórz Custom GUI za pomocą [**Open Screen or Custom GUI** action](./action-scripts#open-screen-or-custom-gui-opengui).

### Moja gra bardzo długo się ładuje po włączeniu wstępnego ładowania.

To oczekiwane zachowanie. Wstępne ładowanie dużych zasobów, takich jak animacje lub dźwięki w wysokiej rozdzielczości, podczas początkowego uruchamiania naturalnie wydłuży czas ładowania gry.

### Moja animacja FMA zużywa zbyt dużo RAM-u!

Klasyczne animacje [FMA](./fma) mogą zużywać dużo pamięci, gdy zawierają wiele klatek w wysokiej rozdzielczości. AFMA lepiej nadaje się do dużych lub bardziej złożonych animowanych tekstur. Klasyczne animacje FMA utrzymuj krótkie; do pełnego odtwarzania wideo używaj [Video](./video).

### Czy FancyMenu działa z OptiFine?

Nie. OptiFine **nie jest kompatybilny** i wiadomo, że psuje wiele modów, w tym FancyMenu. Zdecydowanie zaleca się używanie nowoczesnych alternatyw, takich jak Sodium/Embeddium + Iris/Oculus.
Zobacz [Alternatywy dla OptiFine](./optifine-alternatives).

### Moja gra się wyłącza. Jak sprawdzić, czy to konflikt modów?

Najlepszym sposobem na sprawdzenie konfliktu modów jest **uruchomienie gry tylko z FancyMenu i jego zależnościami** (Konkrete, Melody). Jeśli awaria już nie występuje, możesz dodawać pozostałe mody z powrotem małymi grupami, aż problem pojawi się ponownie — w ten sposób zidentyfikujesz konfliktowy mod.

### Przycisk z innego moda znika albo nie działa, gdy próbuję go edytować.

Niektóre mody dodają widżety w sposób, którego FancyMenu nie potrafi wykryć ani dostosować. Sprawdź [Vanilla/Mod Elements](./vanilla-elements) oraz, w przypadku ekranów opartych na listach, [Customizing Scrollable Screens](./customizing-scrollable-screens). Jeśli widżet nadal się nie pojawia, mod, który go dodaje, musi udostępnić go jako obsługiwany widżet ekranu.

### Czy mogę używać układów FancyMenu na serwerze?

Układy i dostosowania wizualne są przechowywane po stronie klienta gracza; serwer nie może wymusić ich na nie skonfigurowanym kliencie. Rozpowszechniaj je jako część modpacka. Zainstaluj FancyMenu na serwerze, jeśli potrzebujesz [komend serwerowych](./commands), [FM Data](./fm-data), [dostępu do NBT po stronie serwera](./nbt-data-placeholder#server-side-placeholder), gamerule, struktur lub nasłuchiwaczy serwera.

### Jaka jest różnica między FancyMenu v2 (dla starszych wersji MC) a v3?

FancyMenu v3 to całkowicie przepisana wersja z wieloma nowymi funkcjami, stabilniejszą architekturą i lepszą wydajnością. V2 jest przestarzałe, nie jest już wspierane i brakuje mu wielu funkcji, takich jak zaawansowane placeholdery i skrypty. Zdecydowanie zaleca się używanie v3 na nowoczesnej wersji Minecrafta (1.18.2+). Układy z V2 można automatycznie przekonwertować do v3 podczas ich wczytywania, ale może być potrzebne ręczne poprawienie niektórych elementów.

### Gdzie mogę znaleźć gotowe układy i szablony?

Społeczność FancyMenu udostępnia układy na kanale `#layout-templates` na oficjalnym serwerze Discord Keksuccino's Mods ("Kekscord").

### Jak mogę sprawić, by Player Entity renderował się za innymi elementami?

Zazwyczaj nie można wymusić, aby [element Player Entity](./elements#player-entity) znalazł się za zwykłymi elementami 2D za pomocą widżetu [Warstwy](./layers-and-groups). Jego renderer może ignorować zwykłą kolejność warstw GUI. Zaprojektuj układ z uwzględnieniem tego ograniczenia albo użyj wcześniej wyrenderowanego obrazu, jeśli wymagana jest ścisła kolejność warstw.

### Mój Player Entity ma tylko jedną nogę! Co się stało?

To błąd wizualny, prawdopodobnie spowodowany konfliktem z innym modem, który zmienia animacje lub modele gracza. Sprawdź ustawienia pozy Player Entity, aby zobaczyć, czy nogi nie zostały przypadkowo obrócone lub przesunięte.

### Jak utworzyć opóźnienie między akcjami w skrypcie?

Użyj bloków [**Delay** lub **Execute Later**](./action-scripts#what-are-statements) do logiki opóźnionych akcji. Do powtarzalnej logiki działającej w tle użyj [Schedulerów](./schedulers).

### Czy mogę dostosować menu z moda Create?

Nie. Dostosowywanie jest celowo wyłączone dla ekranów Create. Zobacz [Ekrany, dla których dostosowywanie jest celowo wyłączone](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Jaka jest zalecana rozdzielczość dla obrazów tła i tekstur przycisków?

Tła: Standardowy obraz 1920x1080 (1080p) to świetny punkt wyjścia i dobrze skaluje się u większości użytkowników.
Przyciski: Większość domyślnych przycisków ma około 150–200 pikseli szerokości i 20 pikseli wysokości. Dopasowanie własnych tekstur do tych rozmiarów jest dobrą praktyką dla zachowania spójności.

### Czy istnieje sposób, aby automatycznie otworzyć menu lub uruchomić komendę, gdy gracz ukończy zadanie w grze (np. quest)?
FancyMenu ma wiele [wbudowanych nasłuchiwaczy zdarzeń gry](./listeners), ale nie ma uniwersalnego nasłuchiwacza dla każdego zewnętrznego systemu questów. Jeśli mod od questów obsługuje nagrody w postaci komend, użyj jednej z nich, aby uruchomić [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) lub inną odpowiednią [komendę FancyMenu](./commands).

### Jak sprawić, by przycisk był nieaktywny albo „wyszarzony”?

Możesz kontrolować stan aktywności przycisku za pomocą [Loading Requirements](./conditions).
Kliknij przycisk prawym przyciskiem myszy w edytorze i wybierz **Control Active State**.
Dodaj wymaganie, które musi zostać spełnione, aby przycisk był aktywny. Aby wyłączyć go na stałe, użyj [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number), aby sprawdzić, czy 0 równa się 1.
Przycisk będzie teraz używać tekstury „Inactive Background” i nie będzie można go kliknąć.

### Jak mogę usunąć nagłówek i stopkę (paski z teksturą ziemi) na przewijalnych ekranach?

W edytorze układu otwórz **Layout Properties -> Header/Footer Customizations**. Ustaw tekstury jako przezroczyste. Ta opcja może być niedostępna na niektórych modowanych ekranach.

### Nie mogę utworzyć układu „dla bieżącego ekranu”. Przycisk jest wyszarzony.

Najpierw musisz włączyć dostosowywanie dla tego ekranu przez **menu bar -> Customization -> Current Screen Customizations -> Enabled**.

### Nie mogę dostosować żadnych elementów ekranu, gdy otwieram go w edytorze. Wtedy jest po prostu pusty ekran.

Może to oznaczać, że utworzyłeś [Universal Layout](./universal-layouts) zamiast układu **dla bieżącego ekranu**.

Może to też być [przewijalny ekran](./customizing-scrollable-screens), którego FancyMenu domyślnie nie potrafi dostosować.

Trzecia możliwość to ekran z moda, który dodaje elementy w sposób niezgodny z Vanilla, przez co FancyMenu nie może dostosować tych elementów.

### Przy moim elemencie Text pojawiają się dziwne szare prostokąty.

Te półprzezroczyste prostokąty to uchwyty przewijania elementu [Text](./elements#text), a nie błąd renderowania.

Jeśli nie chcesz, aby były widoczne, możesz albo kliknąć element prawym przyciskiem myszy i całkowicie wyłączyć przewijanie, albo ustawić tekstury uchwytów na całkowicie przezroczyste w tym samym menu kontekstowym, jeśli chcesz, by element nadal był przewijalny.

### Jak mogę wyświetlić najnowszy changelog Minecrafta w moich menu?

Istnieje świetny [projekt GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), który konwertuje changelogi Minecrafta do Markdown kompatybilnego z FancyMenu, dzięki czemu możesz wyświetlać najnowszy changelog MC w swoich menu! Projekt aktualizuje się codziennie, pobierając nowe changelogi.

Aby wyświetlić go w [elemencie Text](./elements#text), ustaw **Source Mode** na **Resource** i jako źródło zasobu wybierz **Web**. Użyj `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Jaki jest najprostszy sposób, aby rozciągnąć dowolny element do rozmiaru ekranu?

Większość elementów ma w menu kontekstowym dostępnym po kliknięciu prawym przyciskiem myszy opcję rozciągania poziomego i pionowego. Włączenie jej sprawi, że element będzie zawsze rozciągnięty na pełną szerokość i/lub wysokość ekranu. Rozciąganie poziome i pionowe można włączać niezależnie.

### Nie mogę kliknąć przycisków ani wchodzić w interakcję z suwakami, gdy znajdują się za lub przed elementem Text.

Dzieje się tak, ponieważ elementy Text są domyślnie interaktywne (aby można było chwytać uchwyt przewijania lub klikać hiperłącza Markdown), co oznacza, że przechwytują kliknięcia myszy i zdarzenia przewijania. Najlepiej po prostu nie przesuwać przycisków za/przed elementami Text, ale jeśli nie da się tego uniknąć, możesz wyłączyć interaktywność elementu Text, **klikając go prawym przyciskiem myszy**, a następnie ustawiając **Interactable** na **Disabled**. Pamiętaj, że spowoduje to, iż element Text stanie się statycznym, nieinteraktywnym tekstem, więc nie będzie można go przewijać ani klikać hiperłączy.

### Jak sprawić, by przyciski i suwaki nie były już zaznaczane/fokusowane podczas nawigacji po ekranach klawiszami strzałek i Tab?

Aby przyciski i suwaki nie były nawigowalne, musisz **kliknąć je prawym przyciskiem myszy** i ustawić **Navigable** na **Disabled**. Przycisk/suwak nadal będzie można kliknąć, ale nie będzie można już ustawić na nim fokusu za pomocą nawigacji klawiszami Arrow/Tab.

Jest to także przydatne, jeśli chcesz dodać przyciski/suwaki do ekranu czatu, aby nadal można było używać klawisza Arrow Up do przewijania starszych wiadomości bez przypadkowego zaznaczania przycisków/suwaków na ekranie.

### W jednym z menu kontekstowych FancyMenu brakuje opcji, która powinna tam być.

Menu kontekstowe FancyMenu (menu otwierane po kliknięciu prawym przyciskiem myszy w jakimś miejscu lub podczas interakcji z paskami menu) są PRZEWIJALNE. Oznacza to, że możesz użyć kółka przewijania, gdy kursor myszy znajduje się nad menu, aby przewijać w górę lub w dół, co pozwala zobaczyć więcej opcji, które wcześniej nie były widoczne.

### Nie mogę dostosować ekranu tytułowego, ciągle pokazuje oryginalny, gdy opuszczam edytor.

Inny mod zastępuje oryginalny `title_screen`. Wyłącz niestandardowy ekran tytułowy tego moda w jego ustawieniach. Jeśli nie ma takiej opcji, FancyMenu nie może zastosować układu do ekranu zastępczego.
