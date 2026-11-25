---
title: FAQ
description: Najczęściej zadawane pytania.
sourceBlobSha: 4ae872e8e4a54fc6a89de7c87c8a137a89292455
---
# FAQ

### Potrzebuję pomocy z pewnym problemem. Jakie informacje podać?

Aby uzyskać jak najlepszą pomoc, podaj jak najwięcej kontekstu:
1.  **Jasny opis problemu:** Czego się spodziewasz, a co faktycznie się dzieje?
2.  **Plik `latest.log`:** Znajdziesz go w `<game-directory>/logs/latest.log`. **Nie wysyłaj raportu z awarii**, chyba że ktoś wyraźnie o niego poprosi; plik `latest.log` zazwyczaj zawiera potrzebne informacje. Opublikuj go na przykład w serwisie https://gist.github.com.
3.  **Wersja Minecrafta:** (np. 1.20.1)
4.  **Mod loader i jego wersja:** (np. Forge 47.2.0, Fabric 0.15.7)
5.  **Wersja FancyMenu:** (np. 3.5.2)
6.  **Zrzuty ekranu lub nagrania** przedstawiające problem również mogą być bardzo pomocne.

> [!TIP]
> Potrzebujesz pomocy Alice lub innej sztucznej inteligencji? Dodaj [eksport dla AI](/export-for-ai) tego, co nie działa. Dzięki niemu AI zobaczy dokładnie, jak wszystko jest skonfigurowane. Eksport zawiera już wersje Minecrafta, mod loadera i FancyMenu.

### Jak zmienić kolejność warstw elementów (przenieść coś przed inny element lub za niego)?

- **Własne elementy:** przeciągnij ich warstwy w widżecie Warstwy edytora układu albo kliknij element prawym przyciskiem myszy i wybierz **Przenieś o jedną warstwę wyżej** lub **Przenieś o jedną warstwę niżej**. Zobacz [Warstwy i grupy](/layout-editor#layers-and-groups).
- **Własne elementy i elementy vanilla:** nie można zmienić kolejności elementów vanilla. Aby umieścić wszystkie własne elementy za nimi, na przykład obraz tła za domyślnymi przyciskami, kliknij prawym przyciskiem myszy tło edytora i ustaw **Własne elementy za elementami vanilla** na **Włączone**.

### Czy mogę wykluczyć niektóre przyciski z uniwersalnego szablonu przycisku?

**Nie. Jeśli dla przycisku szablonu ustawiono niestandardowe tekstury, są one zawsze współdzielone przez wszystkie objęte nim elementy. Nie można wykluczyć pojedynczych przycisków.**

### Jak sprawić, żeby kliknięcie przycisku coś robiło?

Użyj [**skryptu akcji**](/action-scripts).
1.  Kliknij przycisk w edytorze prawym przyciskiem myszy.
2.  Wybierz **Edytuj skrypt akcji**.
3. Kliknij **Dodaj akcję** i wybierz akcję, na przykład [**Otwórz ekran lub niestandardowe GUI**](/action-scripts#open-screen-or-custom-gui), [**Dołącz do serwera**](/action-scripts#join-server) lub [**Ustaw wartość zmiennej**](/action-scripts#set-variable-value-fm-variable).

### Czy mogę stworzyć zupełnie nowy ekran menu od podstaw?

Tak, za pomocą [niestandardowego GUI](/custom-guis):

1. Otwórz **pasek menu -> Dostosowywanie -> Niestandardowe GUI -> Zarządzaj niestandardowymi GUI** i kliknij **Nowe GUI**.
2. Nadaj mu identyfikator, na przykład `modpack_info`, i kliknij **Gotowe**.
3. Otwórz je przyciskiem **Otwórz GUI** i utwórz dla niego układ tak jak dla każdego innego menu.
4. Otwórz je z poziomu przycisku, używając akcji [**Otwórz ekran lub niestandardowe GUI**](/action-scripts#open-screen-or-custom-gui) i podając jego identyfikator.

### Po włączeniu wstępnego ładowania moja gra uruchamia się bardzo długo.

To normalne. Wstępne ładowanie dużych zasobów, takich jak animacje w wysokiej rozdzielczości czy dźwięki, podczas uruchamiania gry naturalnie wydłuża czas ładowania.

### Moja animacja zużywa dużo pamięci RAM albo spowalnia grę!

Duże klatki i wysoka liczba klatek na sekundę wymagają więcej pamięci i mocy obliczeniowej. Dostosuj rozmiar klatek do tego, jak duże mają być wyświetlane na ekranie, i użyj mniejszej liczby klatek na sekundę. Zobacz [Animacje](/animations#performance). W przypadku długich nagrań z dźwiękiem użyj funkcji [Wideo](/video).

### Czy FancyMenu współpracuje z OptiFine?

Nie. OptiFine **nie jest kompatybilne** i wiadomo, że powoduje problemy z wieloma modami, w tym FancyMenu. Zdecydowanie zalecamy używanie nowoczesnych alternatyw, takich jak Sodium/Embeddium + Iris/Oculus.
Zobacz [Alternatywy dla OptiFine](/optifine-alternatives).

### Gra się zawiesza. Jak sprawdzić, czy przyczyną jest konflikt modów?

Najlepszym sposobem sprawdzenia, czy występuje konflikt modów, jest **uruchomienie gry wyłącznie z FancyMenu i jego zależnościami** (Konkrete, Melody). Jeśli problem przestanie występować, dodawaj pozostałe mody z powrotem małymi grupami, aż awaria wystąpi ponownie. W ten sposób ustalisz, który mod powoduje konflikt.

### Przycisk z innego moda znika albo nie działa, gdy próbuję go edytować.

Niektóre mody dodają widżety w sposób, który uniemożliwia FancyMenu ich wykrycie lub dostosowanie. Zobacz [Elementy vanilla/modów](/vanilla-elements), a w przypadku ekranów z listami — [Dostosowywanie przewijanych ekranów](/customizing-scrollable-screens). Jeśli widżet nadal się nie pojawia, mod, który go dodaje, musi udostępniać go jako obsługiwany widżet ekranu.

### Czy mogę używać układów FancyMenu na serwerze?

Układy i ustawienia wyglądu są przechowywane po stronie klienta gracza, więc serwer nie może narzucić ich klientowi, który nie jest odpowiednio skonfigurowany. Udostępniaj je jako część paczki modów. Zainstaluj FancyMenu na serwerze, jeśli potrzebujesz [komend serwerowych](/commands), [FM Data](/fm-data), [dostępu po stronie serwera do NBT](/nbt-data-placeholder#server-side-placeholder), reguł gry, struktur lub nasłuchiwaczy serwerowych.

### Czym różni się FancyMenu v2 (dla starszych wersji MC) od v3?

FancyMenu v3 to całkowicie przepisana wersja, która zawiera wiele nowych funkcji, ma stabilniejszą architekturę i działa wydajniej. V2 jest przestarzała, nie jest już wspierana i nie zawiera wielu funkcji, takich jak zaawansowane symbole zastępcze i skrypty. Zdecydowanie zalecamy używanie v3 na nowoczesnej wersji Minecrafta (1.18.2+). Układy v2 można automatycznie przekonwertować do v3 podczas ich wczytywania, ale może być konieczne ręczne poprawienie niektórych elementów.

### Gdzie znajdę gotowe układy i szablony?

Społeczność FancyMenu udostępnia kompletne konfiguracje na kanale [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) na oficjalnym serwerze Discord („Kekscord”). Zainstaluj je jako osobny profil — zobacz [Szablony układów](/profiles#layout-templates).

### Jak umieścić element postaci gracza za innymi elementami?

Zazwyczaj nie można wymusić, aby [element postaci gracza](/elements#player-entity) znalazł się za zwykłymi elementami 2D, korzystając z widżetu [Warstwy](/layout-editor#layers-and-groups). Renderer postaci może ignorować standardową kolejność warstw interfejsu. Zaprojektuj układ z uwzględnieniem tego ograniczenia albo użyj wcześniej wyrenderowanego obrazu, jeśli wymagana jest ścisła kolejność warstw.

### Moja postać gracza ma tylko jedną nogę! Co się stało?

To błąd wizualny, najpewniej spowodowany konfliktem z modem, który zmienia animacje lub modele gracza. Sprawdź ustawienia pozy elementu postaci gracza i upewnij się, że nogi nie zostały przypadkowo obrócone lub przesunięte.

### Jak utworzyć opóźnienie między akcjami w skrypcie?

Kliknij prawym przyciskiem myszy obszar skryptu w edytorze skryptów akcji, kliknij **Dodaj blok WYKONAJ PÓŹNIEJ** i umieść w nim akcje, które mają poczekać. Wykonają się raz po upływie podanego czasu w milisekundach, a reszta skryptu będzie działać dalej bez oczekiwania. Zobacz [Wykonaj później](/action-scripts#execute-later).

Jeśli coś ma się powtarzać, użyj [harmonogramów](/schedulers).

### Czy mogę dostosowywać menu z moda Create?

Nie. Możliwość dostosowywania ekranów Create została celowo wyłączona. Zobacz [Ekrany, dla których celowo wyłączono możliwość dostosowywania](/incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Jaka rozdzielczość jest zalecana dla obrazów tła i tekstur przycisków?

Tła: standardowy obraz o rozdzielczości 1920×1080 (1080p) to dobry punkt wyjścia i będzie dobrze skalować się u większości użytkowników.
Przyciski: większość przycisków vanilla ma około 150–200 pikseli szerokości i 20 pikseli wysokości. Dopasowanie niestandardowych tekstur do tych wymiarów to dobra praktyka, która zapewnia spójny wygląd.

### Czy można automatycznie otworzyć menu albo wykonać komendę, gdy gracz ukończy zadanie w grze (na przykład misję)?
FancyMenu ma wiele [wbudowanych nasłuchiwaczy zdarzeń gry](/listeners), ale nie ma ogólnego nasłuchiwacza obsługującego wszystkie zewnętrzne systemy zadań. Jeśli mod z zadaniami obsługuje nagrody w postaci komend, użyj takiej komendy, aby uruchomić [`/openguiscreen`](/commands#openguiscreen), [`/fmvariable`](/commands#fmvariable) lub inną odpowiednią [komendę FancyMenu](/commands).

### Jak dezaktywować przycisk albo sprawić, by był „wyszarzony”?

Możesz kontrolować stan aktywności przycisku za pomocą [warunków](/conditions).
Kliknij przycisk w edytorze prawym przyciskiem myszy i wybierz **Kontroluj stan aktywności**.
Dodaj warunek, który musi być spełniony, aby przycisk był aktywny. Aby wyłączyć go na stałe, użyj warunku [**Czy liczba**](/conditions#is-number), który sprawdza, czy 0 jest równe 1.
Przycisk będzie teraz używał tekstury „Nieaktywne tło” i nie będzie można go kliknąć.

### Jak usunąć nagłówek i stopkę (paski z teksturą ziemi) z przewijanych ekranów?

W edytorze układu otwórz **Właściwości układu -> Dostosowywanie nagłówka/stopki**. Ustaw tekstury na przezroczyste. Ta opcja może być niedostępna na niektórych ekranach z modów.

### Nie mogę utworzyć układu „dla bieżącego ekranu”. Przycisk jest wyszarzony.

Najpierw włącz możliwość dostosowywania tego ekranu: kliknij **pasek menu -> Dostosowywanie -> Dostosowywanie bieżącego ekranu**, aby wyświetlał się stan **Włączone**.

### Nie mogę dostosować żadnych elementów ekranu po otwarciu go w edytorze. Ekran jest pusty.

Być może utworzono [układ uniwersalny](/universal-layouts) zamiast układu **dla bieżącego ekranu**.

Może to być również [przewijany ekran](/customizing-scrollable-screens), którego FancyMenu domyślnie nie może dostosowywać.

Inną możliwością jest ekran z moda, który dodaje elementy w sposób inny niż vanilla. W takiej sytuacji FancyMenu nie może ich dostosować.

### Przy moim elemencie tekstowym pojawiają się dziwne szare pola.

To paski przewijania [elementu tekstowego](/elements#text). Pojawiają się, gdy tekst nie mieści się w elemencie, aby umożliwić graczom jego przewijanie.

- Powiększ element albo skróć tekst — wtedy paski znikną.
- Kliknij element prawym przyciskiem myszy i otwórz **Paski przewijania**. Opcja **Wyświetlanie** pozwala ustawić, kiedy mają się pojawiać: **Zawsze**, tylko **Podczas przewijania** lub **Nigdy**. Przy ustawieniu **Nigdy** nadal można przewijać tekst kółkiem myszy.
- W tym samym menu opcje **Styl uchwytu przewijania**, **Tekstury uchwytu przewijania** i **Kolor uchwytu przewijania [HEX]** pozwalają zmienić ich wygląd.

Zobacz [Tekst w menu](/text-in-menus#scroll-bars), aby poznać wszystkie ustawienia pasków przewijania.

### Jak wyświetlić w menu najnowszy wykaz zmian w Minecraftcie?

Dostępny jest świetny [projekt na GitHubie](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), który konwertuje wykazy zmian Minecrafta do formatu Markdown obsługiwanego przez FancyMenu. Dzięki temu możesz wyświetlić w menu najnowszy wykaz zmian MC! Projekt aktualizuje się codziennie, aby pobierać nowe wykazy zmian.

Aby wyświetlić go w [elemencie tekstowym](/elements#text), ustaw **Tryb źródła** na **Zasób**, a źródło zasobu na **Sieć**. Użyj adresu `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Jak najłatwiej rozciągnąć dowolny element do rozmiaru ekranu?

W menu kontekstowym otwieranym prawym przyciskiem myszy większości elementów znajduje się opcja rozciągania ich w poziomie i w pionie. Po jej włączeniu element będzie zawsze rozciągany na pełną szerokość i/lub wysokość ekranu. Rozciąganie w poziomie i pionie można włączać niezależnie.

### Nie mogę klikać przycisków ani używać suwaków, gdy znajdują się za elementem tekstowym lub przed nim.

Dzieje się tak, ponieważ elementy tekstowe są domyślnie interaktywne (umożliwiają chwytanie uchwytu przewijania i klikanie hiperłączy w Markdown), więc przechwytują kliknięcia myszy i zdarzenia przewijania. Najlepiej po prostu nie umieszczać przycisków za elementami tekstowymi ani przed nimi. Jeśli jednak nie da się tego uniknąć, możesz wyłączyć interaktywność elementu tekstowego: **kliknij go prawym przyciskiem myszy**, a następnie ustaw opcję **Interaktywny** na **Wyłączone**. Pamiętaj, że element tekstowy stanie się wtedy statyczny i nieinteraktywny — nie będzie można przewijać jego zawartości ani klikać hiperłączy.

### Jak sprawić, żeby przyciski i suwaki nie były zaznaczane ani aktywowane podczas poruszania się po ekranach za pomocą klawiszy strzałek i Tab?

Aby uniemożliwić nawigowanie do przycisków i suwaków, **kliknij je prawym przyciskiem myszy** i ustaw opcję **Możliwość nawigacji** na **Wyłączone**. Nadal będzie można je klikać, ale nie da się ich zaznaczyć za pomocą klawiszy strzałek ani Tab.

Jest to też przydatne, jeśli chcesz dodać przyciski lub suwaki do ekranu czatu. Dzięki temu nadal można używać klawisza strzałki w górę do przeglądania starszych wiadomości, nie zaznaczając przypadkowo przycisków ani suwaków na ekranie.

### W jednym z menu kontekstowych FancyMenu brakuje opcji, która powinna się tam znajdować.

Menu kontekstowe FancyMenu (otwierane po kliknięciu czegoś prawym przyciskiem myszy lub podczas korzystania z pasków menu) są PRZEWIJANE. Oznacza to, że można przewijać menu w górę lub w dół kółkiem myszy, gdy kursor znajduje się nad nim, aby zobaczyć więcej wcześniej niewidocznych opcji.

### Nie mogę dostosować ekranu tytułowego — po wyjściu z edytora znów widzę oryginalny ekran.

Inny mod zastępuje oryginalny `title_screen`. Wyłącz niestandardowy ekran tytułowy tego moda w jego ustawieniach. Jeśli nie ma takiej opcji, FancyMenu nie może zastosować układu do zastępczego ekranu.

### Podczas dostosowywania ekranu ekwipunku nie mogę edytować jego zawartości.

To normalne. FancyMenu nie obsługuje edytowania właściwej zawartości żadnego rodzaju ekranu ekwipunku (ekwipunku gracza, skrzyni, stołu rzemieślniczego itp.), ponieważ dodanie takiej obsługi byłoby bardzo trudne.

Nadal można dodawać nowe elementy do tych ekranów — nie można jedynie edytować ich zawartości.

Przy okazji: SpiffyHUD również nie pomoże, ponieważ służy do edytowania HUD-u (na przykład paska przedmiotów), a nie ekranów (takich jak ekrany ekwipunku).
