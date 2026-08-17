---
title: FAQ
description: Najczęściej zadawane pytania.
---
# FAQ

### Potrzebuję pomocy z problemem. Jakie informacje powinienem podać?

Aby uzyskać najlepszą pomoc, podaj jak najwięcej szczegółów:
1.  **Jasny opis problemu:** Czego oczekiwałeś, że się stanie, i co faktycznie się stało?
2.  **Plik `latest.log`:** Znajdziesz go w `<game-directory>/logs/latest.log`. **Nie wysyłaj pliku crash log**, chyba że zostaniesz o to wyraźnie poproszony; `latest.log` zwykle zawiera potrzebne informacje. Do opublikowania pliku użyj na przykład strony https://gist.github.com.
3.  **Wersja Minecrafta:** (np. 1.20.1)
4.  **Loader modów i jego wersja:** (np. Forge 47.2.0, Fabric 0.15.7)
5.  **Wersja FancyMenu:** (np. 3.5.2)
6.  **Zrzuty ekranu lub nagrania wideo** problemu również mogą być bardzo pomocne.

### Jak zmienić kolejność warstw elementów (przenieść coś przed inny element lub za niego)?

*   **Niestandardowe vs. niestandardowe:** Otwórz **Window -> Editor Widgets -> Layers** i przeciągaj elementy w hierarchii. Możesz też kliknąć element prawym przyciskiem myszy i użyć opcji **Move One Layer Up/Down**. Zobacz [Warstwy i grupy](./layers-and-groups).
*   **Niestandardowe vs. waniliowe:** Aby renderować wszystkie niestandardowe elementy za wszystkimi elementami waniliowymi (np. umieścić obraz tła za domyślnymi przyciskami), **kliknij prawym przyciskiem myszy tło edytora** i włącz opcję **„Render Custom Elements Behind Vanilla”**.

### Czy mogę wykluczyć niektóre przyciski z uniwersalnego szablonu przycisku?

**Nie. Jeśli dla przycisku szablonu ustawiono niestandardowe tekstury, są one zawsze współdzielone przez wszystkie objęte nim elementy. Nie można wykluczyć pojedynczych przycisków.**

### Jak sprawić, aby przycisk coś robił po kliknięciu?

Użyj [**Action Script**](./action-scripts).
1.  Kliknij przycisk w edytorze prawym przyciskiem myszy.
2.  Wybierz **Edit Action Script**.
3.  Kliknij **Add Action** i wybierz akcję, taką jak [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) lub [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Czy mogę stworzyć całkowicie nowy ekran menu od zera?

Użyj [**Custom GUI**](./custom-guis).
1.  Na pasku menu przejdź do **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Kliknij **„New GUI”** i nadaj mu unikalny identyfikator.
3.  Następnie możesz otworzyć ten nowy, pusty ekran i utworzyć dla niego układ, dodając dowolne elementy.
4.  Otwórz Custom GUI za pomocą akcji [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui).

### Po włączeniu wstępnego ładowania gra długo się uruchamia.

Jest to oczekiwane zachowanie. Wstępne ładowanie dużych zasobów, takich jak animacje w wysokiej rozdzielczości lub dźwięki, podczas pierwszego uruchamiania naturalnie wydłuża czas ładowania gry.

### Moja animacja FMA zużywa zbyt dużo pamięci RAM!

Klasyczne [animacje FMA](./fma) mogą zużywać dużo pamięci, jeśli zawierają wiele klatek w wysokiej rozdzielczości. AFMA lepiej nadaje się do dużych lub złożonych animowanych tekstur. Klasyczne animacje FMA powinny być krótkie; do odtwarzania pełnych nagrań wideo używaj [Video](./video).

### Czy FancyMenu działa z OptiFine?

Nie. OptiFine **nie jest kompatybilny** i wiadomo, że powoduje problemy z wieloma modami, w tym z FancyMenu. Zdecydowanie zaleca się korzystanie z nowoczesnych alternatyw, takich jak Sodium/Embeddium + Iris/Oculus.
Zobacz [Alternatywy dla OptiFine](./optifine-alternatives).

### Gra się zawiesza. Jak sprawdzić, czy przyczyną jest konflikt modów?

Najlepszym sposobem sprawdzenia konfliktu modów jest **uruchomienie gry tylko z FancyMenu i jego zależnościami** (Konkrete, Melody). Jeśli gra przestanie się zawieszać, dodawaj pozostałe mody małymi grupami, aż problem wystąpi ponownie. W ten sposób zidentyfikujesz konfliktujący mod.

### Przycisk z innego moda znika lub nie działa, gdy próbuję go edytować.

Niektóre mody dodają widżety w sposób, którego FancyMenu nie potrafi wykryć ani dostosować. Sprawdź [Elementy waniliowe/modowane](./vanilla-elements), a w przypadku ekranów opartych na listach także [Dostosowywanie ekranów przewijanych](./customizing-scrollable-screens). Jeśli widżet nadal się nie pojawia, mod, który go dodaje, musi udostępniać go jako obsługiwany widżet ekranu.

### Czy mogę używać układów FancyMenu na serwerze?

Układy i dostosowania wyglądu są przechowywane na kliencie gracza; serwer nie może wymusić ich na nie skonfigurowanym kliencie. Rozprowadzaj je jako część modpacka. Zainstaluj FancyMenu na serwerze, gdy potrzebujesz [komend serwerowych](./commands), [FM Data](./fm-data), [serwerowego dostępu do NBT](./nbt-data-placeholder#server-side-placeholder), gameruli, struktur lub nasłuchiwania zdarzeń serwera.

### Jaka jest różnica między FancyMenu v2 (dla starszych wersji MC) a v3?

FancyMenu v3 to całkowicie przepisana wersja z wieloma nowymi funkcjami, stabilniejszą architekturą i lepszą wydajnością. V2 jest przestarzała, nie jest już wspierana i nie oferuje wielu funkcji, takich jak zaawansowane placeholdery i skrypty. Zdecydowanie zaleca się używanie v3 na nowoczesnej wersji Minecrafta (1.18.2+). Układy V2 mogą zostać automatycznie przekonwertowane do v3 podczas ich ładowania, ale może być konieczne ręczne wprowadzenie poprawek.

### Gdzie mogę znaleźć gotowe układy i szablony?

Społeczność FancyMenu udostępnia układy na kanale [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) oficjalnego serwera Discord Keksuccino's Mods („Kekscord”).

### Jak sprawić, aby encja gracza renderowała się za innymi elementami?

Zasadniczo nie można wymusić, aby [element encji gracza](./elements#player-entity) znajdował się za zwykłymi elementami 2D za pomocą [widżetu Layers](./layers-and-groups). Renderer encji może ignorować zwykłą kolejność warstw GUI. Zaprojektuj układ z uwzględnieniem tego ograniczenia albo użyj wcześniej wyrenderowanego obrazu, gdy wymagana jest ścisła kolejność warstw.

### Moja encja gracza ma tylko jedną nogę! Co się stało?

To błąd wizualny, najprawdopodobniej spowodowany konfliktem z innym modem zmieniającym animacje lub modele graczy. Sprawdź ustawienia pozy encji gracza, aby upewnić się, że nogi nie zostały przypadkowo obrócone lub przesunięte.

### Jak utworzyć opóźnienie między akcjami w skrypcie?

Użyj bloków [**Delay** lub **Execute Later**](./action-scripts#what-are-statements) do obsługi opóźnionych akcji. W przypadku powtarzającej się logiki działającej w tle użyj [harmonogramów](./schedulers).

### Czy mogę dostosowywać menu z moda Create?

Nie. Dostosowywanie ekranów Create jest celowo wyłączone. Zobacz [Ekrany, na których dostosowywanie jest celowo wyłączone](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Jaka rozdzielczość jest zalecana dla obrazów tła i tekstur przycisków?

Tła: Standardowy obraz 1920×1080 (1080p) to dobry punkt wyjścia i będzie odpowiednio skalowany u większości użytkowników.
Przyciski: Większość waniliowych przycisków ma około 150–200 pikseli szerokości i 20 pikseli wysokości. Dopasowanie niestandardowych tekstur do tego rozmiaru to dobra praktyka zapewniająca spójność.

### Czy można automatycznie otworzyć menu lub wykonać komendę, gdy gracz ukończy cel w grze (np. zadanie)?
FancyMenu ma wiele [wbudowanych nasłuchiwaczy zdarzeń gry](./listeners), ale nie istnieje uniwersalny nasłuchiwacz obsługujący każdy zewnętrzny system zadań. Jeśli mod z zadaniami obsługuje nagrody w postaci komend, użyj jednej z nich do wykonania [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) lub innej odpowiedniej [komendy FancyMenu](./commands).

### Jak sprawić, aby przycisk był nieaktywny lub „wyszarzony”?

Stan aktywności przycisku możesz kontrolować za pomocą [wymagań ładowania](./conditions).
Kliknij przycisk w edytorze prawym przyciskiem myszy i wybierz **Control Active State**.
Dodaj wymaganie, które musi zostać spełnione, aby przycisk był aktywny. Aby trwale go wyłączyć, użyj [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number), sprawdzając, czy 0 jest równe 1.
Przycisk będzie teraz używać tekstury „Inactive Background” i nie będzie można go kliknąć.

### Jak usunąć nagłówek i stopkę (paski z teksturą ziemi) z ekranów przewijanych?

W edytorze układu otwórz **Layout Properties -> Header/Footer Customizations**. Ustaw tekstury jako przezroczyste. Ta opcja może być niedostępna na niektórych ekranach modowanych.

### Nie mogę utworzyć układu „dla bieżącego ekranu”. Przycisk jest wyszarzony.

Najpierw musisz włączyć dostosowywanie tego ekranu przez **pasek menu -> Customization -> Current Screen Customizations -> Enabled**.

### Nie mogę dostosować żadnych elementów ekranu po otwarciu go w edytorze. Ekran jest wtedy pusty.

Może to oznaczać, że utworzyłeś [Universal Layout](./universal-layouts), a nie układ **dla bieżącego ekranu**.

Może to być również [ekran przewijany](./customizing-scrollable-screens), którego FancyMenu domyślnie nie potrafi dostosowywać.

Trzecią możliwością jest ekran z moda, który dodaje elementy w sposób inny niż waniliowy, przez co FancyMenu nie może ich dostosować.

### Przy moim elemencie tekstowym znajdują się dziwne szare pola.

Te półprzezroczyste pola to uchwyty przewijania elementu [Text](./elements#text), a nie błąd renderowania.

Jeśli nie chcesz, aby pola były widoczne, możesz kliknąć element prawym przyciskiem myszy i całkowicie wyłączyć przewijanie LUB ustawić tekstury uchwytów jako całkowicie przezroczyste w tym samym menu kontekstowym, jeśli element ma nadal umożliwiać przewijanie.

### Jak wyświetlać w menu najnowszą listę zmian Minecrafta?

Istnieje świetny [projekt na GitHubie](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), który konwertuje listy zmian Minecrafta do formatu Markdown kompatybilnego z FancyMenu, dzięki czemu możesz wyświetlać w menu najnowszą listę zmian MC! Projekt aktualizuje się codziennie, aby pobierać nowe listy zmian.

Aby wyświetlić ją w [elemencie tekstowym](./elements#text), ustaw **Source Mode** na **Resource**, a źródło zasobu na **Web**. Użyj adresu `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Jaki jest najłatwiejszy sposób na rozciągnięcie dowolnego elementu do rozmiaru ekranu?

Większość elementów ma w menu kontekstowym otwieranym prawym przyciskiem myszy opcję rozciągania w poziomie i w pionie. Włączenie tej opcji sprawi, że element będzie zawsze rozciągany do pełnej szerokości i/lub wysokości ekranu. Rozciąganie poziome i pionowe można włączać niezależnie.

### Nie mogę klikać przycisków ani używać suwaków, gdy znajdują się za elementem tekstowym lub przed nim.

Dzieje się tak, ponieważ elementy tekstowe są domyślnie interaktywne (aby umożliwić przeciąganie uchwytu przewijania lub klikanie hiperłączy Markdown), przez co przechwytują kliknięcia myszy i zdarzenia przewijania. Najlepiej po prostu nie umieszczać przycisków za elementami tekstowymi ani przed nimi, ale jeśli nie da się tego uniknąć, możesz wyłączyć interaktywność elementu tekstowego, **klikając go prawym przyciskiem myszy**, a następnie ustawiając **Interactable** na **Disabled**. Pamiętaj, że element tekstowy stanie się wtedy statycznym, nieinteraktywnym tekstem, więc nie będzie można go przewijać ani klikać jego hiperłączy.

### Jak sprawić, aby przyciski i suwaki nie były już zaznaczane ani fokusowane podczas poruszania się po ekranach za pomocą klawiszy strzałek i Tab?

Aby przyciski i suwaki nie były uwzględniane w nawigacji, kliknij je **prawym przyciskiem myszy** i ustaw **Navigable** na **Disabled**. Przycisk lub suwak nadal będzie można kliknąć, ale nie da się go już fokusować za pomocą nawigacji klawiszami strzałek i Tab.

Jest to również przydatne, jeśli chcesz dodać przyciski lub suwaki do ekranu czatu, aby nadal używać klawisza strzałki w górę do przeglądania starszych wiadomości bez przypadkowego zaznaczania przycisków lub suwaków na ekranie.

### W jednym z menu kontekstowych FancyMenu brakuje opcji, która powinna się tam znajdować.

Menu kontekstowe FancyMenu (menu otwierane po kliknięciu prawym przyciskiem myszy w danym miejscu lub podczas korzystania z pasków menu) są PRZEWIJANE. Oznacza to, że gdy kursor myszy znajduje się nad menu, możesz użyć kółka myszy, aby przewijać je w górę lub w dół i wyświetlać dodatkowe opcje, które wcześniej nie były widoczne.

### Nie mogę dostosować ekranu tytułowego — po wyjściu z edytora wciąż wyświetla się oryginalny ekran.

Inny mod zastępuje oryginalny `title_screen`. Wyłącz niestandardowy ekran tytułowy tego moda w jego ustawieniach. Jeśli mod nie ma takiej opcji, FancyMenu nie może zastosować układu do zastępczego ekranu.
