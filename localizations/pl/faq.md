---
title: FAQ
description: Często zadawane pytania.
---

# FAQ

### Potrzebuję pomocy z problemem. Jakie informacje powinienem podać?
Aby uzyskać jak najlepszą pomoc, podaj jak najwięcej kontekstu:
1.  **Jasny opis problemu:** Czego się spodziewałeś, a co faktycznie się stało?
2.  **Plik `latest.log`:** To najważniejszy plik do diagnozowania problemów. Znajdziesz go w folderze `/logs/` swojej instancji. **Nie wysyłaj pliku crash log**, chyba że wyraźnie o to poproszono; `latest.log` jest znacznie bardziej przydatny. Użyj strony takiej jak https://gist.github.com, aby go udostępnić.
3.  **Twoja wersja Minecrafta:** (np. 1.20.1)
4.  **Twój mod loader i jego wersja:** (np. Forge 47.2.0, Fabric 0.15.7)
5.  **Twoja wersja FancyMenu:** (np. 3.5.2)
6.  **Zrzuty ekranu lub filmy** przedstawiające problem również mogą być bardzo pomocne.

### Jak zmienić warstwę elementów (przesunąć coś przed lub za inny element)?
*   **Custom vs. Custom:** Aby zmienić kolejność renderowania własnych elementów niestandardowych, użyj widżetu **Layers**. Możesz go otworzyć przez pasek menu: **Window -> Widgets -> Layers**. Stamtąd możesz przeciągać elementy w górę lub w dół hierarchii. Możesz też kliknąć element prawym przyciskiem myszy i użyć opcji „Move One Layer Up/Down”.
*   **Custom vs. Vanilla:** Aby renderować wszystkie własne elementy niestandardowe za wszystkimi elementami vanilla (np. umieścić obraz tła za domyślnymi przyciskami), **kliknij prawym przyciskiem myszy tło edytora** i przełącz opcję **"Render Custom Elements Behind Vanilla"**.

### Czy mogę wykluczyć niektóre przyciski z uniwersalnego szablonu przycisku?
**Nie. Jeśli przycisk szablonu ma ustawione niestandardowe tekstury, tekstury te są zawsze współdzielone ze wszystkimi objętymi elementami. Nie można wykluczyć pojedynczych przycisków.**

### Jak sprawić, by przycisk coś robił po kliknięciu?
Użyj **Action Script**.
1.  Kliknij przycisk prawym przyciskiem myszy w edytorze.
2.  Wybierz **Edit Action Script**.
3.  Kliknij **Add Action** i wybierz z listy (np. `Open Screen or Custom GUI`, `Join Server`, `Set Variable Value`).
*   Więcej informacji: [Action Scripts](https://docs.fancymenu.net/en/action-scripts)

### Czy mogę utworzyć całkowicie nowy ekran menu od zera?
Tak, robi się to za pomocą **Custom GUIs**.
1.  Na pasku menu przejdź do **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Kliknij **"New GUI"** i nadaj mu unikalny identyfikator.
3.  Następnie możesz otworzyć ten nowy pusty ekran i stworzyć dla niego układ, dodając dowolne elementy.
4.  Ten Custom GUI można potem otwierać za pomocą akcji przycisku.
*   Więcej informacji: [Custom GUIs](https://docs.fancymenu.net/en/custom-guis)

### Gra bardzo długo się ładuje po włączeniu pre-loading.
To oczekiwane zachowanie. Wstępne ładowanie dużych zasobów, takich jak animacje lub dźwięki w wysokiej rozdzielczości, podczas początkowego uruchamiania naturalnie wydłuży czas ładowania gry.

### Moja animacja FMA zużywa za dużo RAM-u!
Klasyczne pliki FMA mogą zużywać dużo pamięci, gdy zawierają wiele klatek w wysokiej rozdzielczości. FancyMenu 3.9.0 dodaje AFMA, które jest znacznie lepsze dla dużych lub bardziej złożonych animowanych tekstur. W przypadku klasycznych plików FMA utrzymuj animacje krótkie i unikaj bardzo dużej liczby klatek oraz wysokich rozdzielczości. Animacje są przeznaczone do krótkich, dekoracyjnych pętli, a nie do odtwarzania pełnych filmów.

### Czy FancyMenu działa z OptiFine?
Nie. OptiFine **nie jest kompatybilny** i wiadomo, że psuje wiele modów, w tym FancyMenu. Zdecydowanie zaleca się używanie nowoczesnych alternatyw, takich jak Sodium/Embeddium + Iris/Oculus.
*   Więcej informacji: [OptiFine Alternatives](https://docs.fancymenu.net/en/optifine-alternatives)

### Gra się wyłącza. Jak sprawdzić, czy to konflikt modów?
Najlepszym sposobem na sprawdzenie konfliktu modów jest **uruchomienie gry tylko z FancyMenu i jego zależnościami** (Konkrete, Melody). Jeśli crash już nie występuje, możesz dodawać pozostałe mody z powrotem małymi grupami, aż problem pojawi się ponownie, aby zidentyfikować konfliktujący mod.

### Przycisk z innego moda znika albo nie działa, gdy próbuję go edytować.
Zwykle oznacza to, że inny mod dodaje swoje przyciski w niestandardowy, nievanillowy sposób, z którym FancyMenu nie może współpracować. To problem, który musi naprawić autor tamtego moda. FancyMenu nie może dostosowywać elementów, których nie potrafi „zobaczyć”.

### Czy mogę używać układów FancyMenu na serwerze?
FancyMenu jest modem po stronie klienta. Wszystkie układy i dostosowania znajdują się na kliencie gracza. Nie można umieścić układów na serwerze, aby zmusić graczy do ich wyświetlania. Możesz jednak dystrybuować folder `config/fancymenu` jako część modpacka. Jeśli chcesz używać na serwerze komend takich jak `/fmvariable` lub `/openguiscreen`, na serwerze musi być zainstalowane FancyMenu (lub jego wtyczka Spigot).

### Jaka jest różnica między FancyMenu v2 (dla starszych wersji MC) a v3?
FancyMenu v3 to kompletne przepisanie z wieloma nowymi funkcjami, bardziej stabilną architekturą i lepszą wydajnością. V2 jest przestarzałe, nie jest już wspierane i brakuje mu wielu funkcji, takich jak zaawansowane placeholdery i skryptowanie. Zdecydowanie zaleca się używanie v3 na nowoczesnej wersji Minecrafta (1.18.2+). Układy z v2 można automatycznie przekonwertować do v3 podczas ich wczytywania, ale może być potrzebna ręczna poprawka.

### Gdzie mogę znaleźć gotowe układy i szablony?
Społeczność FancyMenu udostępnia układy na kanale `#layout-templates` na oficjalnym serwerze Discord Keksuccino's Mods.

### Jak mogę sprawić, by Player Entity renderował się za innymi elementami?
Nie możesz. Ze względu na sposób renderowania encji w Minecraft, element Player Entity prawie zawsze będzie renderował się przed innymi elementami 2D, niezależnie od ustawień warstw.

### Mój Player Entity ma tylko jedną nogę! Co się stało?
To błąd wizualny, najpewniej spowodowany konfliktem z innym modem, który modyfikuje animacje lub modele gracza. Sprawdź ustawienia Poses elementu Player Entity, aby upewnić się, że nogi nie zostały przypadkowo obrócone lub przesunięte.

### Jak utworzyć opóźnienie między akcjami w skrypcie?
FancyMenu 3.9.0 dodaje bloki **Delay** i **Execute Later** do skryptów akcji. Używaj ich do większości logiki opóźnionych akcji. Do powtarzającej się logiki w tle użyj [Schedulers](https://docs.fancymenu.net/en/schedulers).

### Czy mogę dostosować menu z moda Create?
Nie. FancyMenu ma znane niekompatybilności ze złożonymi GUI Create. Personalizacja ekranów Create została celowo wyłączona, aby zapobiec crashom.

### Dlaczego przyciski z moda X znikają w edytorze?
Oznacza to, że mod dodaje swoje przyciski w niestandardowy, nievanillowy sposób. FancyMenu nie może tych elementów „zobaczyć” ani z nimi współpracować, więc nie może ich dostosować. Autor tamtego moda musiałby zmienić sposób dodawania przycisków, aby były kompatybilne.

### Jaka jest zalecana rozdzielczość obrazów tła i tekstur przycisków?
Tła: Standardowy obraz 1920x1080 (1080p) to świetny punkt wyjścia i dobrze skaluje się dla większości użytkowników.
Przyciski: Większość vanilla przycisków ma około 150–200 pikseli szerokości i 20 pikseli wysokości. Dopasowanie tej wielkości dla niestandardowych tekstur jest dobrą praktyką dla zachowania spójności.

### Czy istnieje sposób, aby automatycznie otworzyć menu lub uruchomić komendę, gdy gracz ukończy cel w grze (np. zadanie)?
Samo FancyMenu nie może wykrywać takich zdarzeń w grze. Możesz jednak zintegrować je z modem zadaniowym, takim jak FTB Quests. Większość modów questowych pozwala uruchomić komendę jako nagrodę za zadanie. Ustawiasz wtedy nagrodę tak, aby wykonywała komendę `/openguiscreen` lub `/fmvariable` w celu interakcji z menu.

### Jak sprawić, by przycisk był nieaktywny lub „wyszarzony”?
Możesz kontrolować stan aktywności przycisku za pomocą Loading Requirements.
Kliknij przycisk prawym przyciskiem myszy w edytorze i wybierz „Active State”.
Dodaj wymaganie, które musi zostać spełnione, aby przycisk był aktywny. Na przykład, aby trwale wyłączyć przycisk, możesz dodać wymaganie Is Number, które sprawdza, czy 0 równa się 1 (co zawsze jest fałszem).
Przycisk będzie teraz używał tekstury „Inactive Background” i nie będzie można go kliknąć.

### Jak mogę usunąć nagłówek i stopkę (paski z teksturą ziemi) na przewijalnych ekranach?
W FancyMenu v3 możesz je dostosować. W edytorze układu kliknij prawym przyciskiem myszy tło edytora i poszukaj opcji takich jak "Customize Header/Footer". Możesz ustawić ich tekstury na całkowicie przezroczyste, aby wizualnie je usunąć. Pamiętaj, że może to nie działać na wszystkich ekranach, zwłaszcza starszych lub mocno zmodyfikowanych.

### Nie mogę utworzyć układu „dla bieżącego ekranu”. Przycisk jest wyszarzony.
Najpierw musisz włączyć personalizację dla tego ekranu przez **menu bar -> Customization -> Current Screen Customizations -> toggle it to Enabled**.

### Nie mogę dostosować żadnych elementów ekranu, gdy otwieram go w edytorze. Jest wtedy po prostu pusty ekran.

Może to oznaczać, że przypadkowo utworzyłeś układ uniwersalny zamiast układu **dla bieżącego ekranu**.

Może to też oznaczać, że ekran, który dostosowujesz, jest ekranem przewijalnym, a FancyMenu domyślnie nie może go personalizować.

Trzecia możliwość to ekran z moda, który dodaje elementy w sposób nievanillowy, przez co FancyMenu nie może tych elementów dostosować.

### Przy moim elemencie Text pojawiają się dziwne szare prostokąty.

Te półprzezroczyste (o niskiej nieprzezroczystości) prostokąty mogą pojawiać się po prawej lub dolnej krawędzi elementu Text i nie są błędem. To uchwyty przewijania elementu Text, ponieważ element jest przewijalny.

Jeśli nie chcesz, aby były widoczne, możesz kliknąć element prawym przyciskiem myszy i całkowicie wyłączyć przewijanie ALBO ustawić tekstury uchwytów na całkowicie przezroczyste w tym samym menu kontekstowym, jeśli chcesz, aby element nadal był przewijalny.

### Jak mogę pokazać najnowszy changelog Minecrafta w moich menu?

Istnieje świetny [projekt GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), który konwertuje changelogi Minecrafta do Markdown kompatybilnego z FancyMenu, dzięki czemu możesz wyświetlać najnowszy changelog MC w swoich menu! Projekt aktualizuje się codziennie, aby pobierać nowe changelogi.

Na przykład, aby pokazać najnowszy changelog Minecrafta w elemencie Text, ustaw jego **Source Mode** na **Resource** i ustaw źródło zasobu na **Web**. Następnie użyj tego adresu URL jako źródła: `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`

### Jaki jest najprostszy sposób, aby rozciągnąć dowolny element do rozmiaru ekranu?

Większość elementów ma w menu kontekstowym po kliknięciu prawym przyciskiem opcję rozciągania ich poziomo i pionowo. Włączenie tej opcji sprawi, że będą one zawsze rozciągane na pełną szerokość i/lub wysokość ekranu. Rozciąganie poziome i pionowe można przełączać niezależnie.

### Nie mogę klikać przycisków ani wchodzić w interakcję z suwakami, gdy znajdują się za lub przed elementem Text.

Dzieje się tak, ponieważ elementy Text są domyślnie interaktywne (aby można było chwycić uchwyt przewijania lub kliknąć linki Markdown), co oznacza, że przechwytują kliknięcia myszy i zdarzenia przewijania. Najlepiej byłoby po prostu nie umieszczać przycisków za/przed elementami Text, ale jeśli nie da się tego uniknąć, możesz wyłączyć interaktywność elementu Text, **klikając go prawym przyciskiem myszy** i ustawiając **Interactable** na **Disabled**. Pamiętaj, że spowoduje to, iż element Text będzie statycznym, nieinteraktywnym tekstem, więc nie będzie można go przewijać ani klikać linków.

### Jak sprawić, by przyciski i suwaki nie były już wybierane/fokusowane podczas nawigacji w ekranach za pomocą klawiszy strzałek i Tab?

Aby przyciski i suwaki nie były nawigowalne, musisz **kliknąć je prawym przyciskiem myszy** i ustawić **Navigable** na **Disabled**. Przycisk/suwak nadal będzie można kliknąć, ale nie będzie można go już fokusem wybrać za pomocą nawigacji Strzałkami/Tab.

Jest to również przydatne, jeśli chcesz dodać przyciski/suwaki do ekranu czatu, ponieważ wtedy nadal możesz używać klawisza Strzałka w górę, aby przewijać starsze wiadomości, bez przypadkowego zaznaczania przycisków/suwaków na ekranie.

### Jedno z menu kontekstowych FancyMenu nie ma opcji, która powinna tam być.

Menu kontekstowe FancyMenu (menu otwierane po kliknięciu gdzieś prawym przyciskiem myszy lub podczas interakcji z paskami menu) są PRZEWIJALNE. Oznacza to, że możesz użyć kółka myszy, gdy kursor znajduje się nad menu, aby przewijać w górę lub w dół, co pozwala zobaczyć więcej opcji, które wcześniej nie były widoczne.
