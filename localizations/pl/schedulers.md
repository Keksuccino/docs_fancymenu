---
title: Harmonogramy
description: >-
  Uruchamiaj skrypty akcji według harmonogramu — raz lub wielokrotnie — w każdym
  menu i podczas gry.
sourceBlobSha: 5abcc8450371fa0d23d67618db9cf27c9bd7de97
---

# Harmonogramy

Harmonogramy uruchamiają [skrypt akcji](/action-scripts) według harmonogramu: raz po upływie określonego czasu, kilka razy albo wielokrotnie, aż do ich zatrzymania. Działają w każdym menu i podczas gry, nawet gdy żadne menu nie jest otwarte, i nie są przypisane do układu.

Harmonogramy są zalecanym rozwiązaniem dla wszystkiego, co ma wydarzyć się później lub powtarzać się wielokrotnie. W miarę możliwości używaj ich zamiast [elementów Ticker](/elements#ticker).

<img width="800" alt="Okienko Porada survivalowa pokazuje kolejną poradę co 4 sekundy, ponieważ harmonogram losuje poradę z listy" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_tips.gif?raw=true">

> [!CAUTION]
> Harmonogram może uruchamiać akcje związane z plikami, siecią, poleceniami, schowkiem, paczkami zasobów i linkami, gdy żadne menu nie jest otwarte. Używaj wyłącznie harmonogramów z profili i plików osób, którym ufasz.

# Dodawanie harmonogramu

<img width="800" alt="Otwarcie okna Zarządzaj harmonogramami, kliknięcie Dodaj harmonogram i przypisanie mu akcji Arrange List with Shuffle dla listy tips" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_add.gif?raw=true">

1. Otwórz **pasek menu -> Dostosowywanie -> Zarządzaj harmonogramami**.
2. Kliknij **Dodaj harmonogram**. Otworzy się edytor skryptów akcji.
3. Dodaj akcje, które mają być uruchamiane za każdym razem, i kliknij **Gotowe**. Zobacz [Skrypty akcji](/action-scripts#making-an-action-script).

<img width="800" alt="Nadawanie nowemu harmonogramowi nazwy random_tip w oknie Edytuj ustawienia, ustawienie opóźnienia tyknięcia na 4000 i opcji Uruchom przy starcie, a następnie uruchomienie harmonogramu i zmiana porady w menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_start.gif?raw=true">

4. Nowy harmonogram pojawi się z losowym identyfikatorem. Kliknij go, a następnie **Edytuj ustawienia**.
5. Nadaj mu **Identyfikator harmonogramu**, na przykład `random_tip`, skonfiguruj [timer](#settings) i kliknij **Gotowe**.
6. Kliknij **Uruchom teraz**, aby go przetestować.

Wszystkie zmiany wprowadzone w oknie **Zarządzaj harmonogramami** są zapisywane od razu.

Harmonogram pokazany na GIF-ach co 4 sekundy uruchamia akcję [**Arrange List (FM Variable)**](/action-scripts#arrange-list-fm-variable) z opcją **Shuffle** dla listy `tips`. Element Tekst wyświetla pierwszy wpis z listy, więc pokazuje losową poradę. Więcej o działaniu listy i tekstu: [Akcje list](/variables#list-actions).

# Ustawienia

| Ustawienie | Działanie |
|---|---|
| **Identyfikator harmonogramu** | Nazwa używana przez akcje i wymagania. Dozwolone są tylko małe litery, cyfry, `.`, `_` i `-`. |
| **Opóźnienie startu (ms)** | Czas oczekiwania od uruchomienia do pierwszego wykonania. `0` oznacza natychmiastowe uruchomienie. |
| **Opóźnienie tyknięcia (ms)** | Czas między kolejnymi wykonaniami. `0` oznacza uruchamianie co każde tyknięcie, czyli 20 razy na sekundę. |
| **Liczba wykonań** | Liczba wykonań, po której harmonogram sam się zatrzyma. `0` oznacza, że działa do momentu zatrzymania. |
| **Uruchom przy starcie** | Uruchamia harmonogram przy każdym uruchomieniu gry. |

Czasy podawane są w milisekundach: `1000` to jedna sekunda, `60000` — jedna minuta, a `1800000` — pół godziny.

# Uruchamianie i zatrzymywanie

Harmonogram działa dopiero po uruchomieniu:

- Po włączeniu opcji **Uruchom przy starcie** — gdy gra się uruchamia oraz po przełączeniu [profili](/profiles).
- Po kliknięciu **Uruchom teraz** w oknie **Zarządzaj harmonogramami**. Gdy harmonogram działa, przycisk zmienia się na **Zatrzymaj teraz**.
- Za pomocą akcji [**Start Scheduler**](/action-scripts#start-scheduler) i identyfikatora harmonogramu, na przykład w skrypcie przycisku lub [nasłuchiwacza](/listeners).

Harmonogram zatrzymuje się:

- Samoczynnie po wykonaniu określonej **Liczby wykonań**.
- Po kliknięciu **Zatrzymaj teraz** lub użyciu akcji [**Stop Scheduler**](/action-scripts#stop-scheduler) z jego identyfikatorem.
- Po zmianie nazwy lub usunięciu, przełączeniu [profili](/profiles) albo zamknięciu gry. Po ponownym uruchomieniu działają tylko harmonogramy z włączoną opcją **Uruchom przy starcie**.

Działającego harmonogramu nie można uruchomić ponownie — akcja **Start Scheduler** nic nie zrobi, dopóki harmonogram się nie zatrzyma. Aby uruchomić go ponownie, użyj **Stop Scheduler**, a następnie **Start Scheduler**.

Wymaganie [**Scheduler Is Running**](/conditions#scheduler-is-running) sprawdza, czy harmonogram działa. Możesz go użyć na przykład po to, aby przycisk zatrzymywania był widoczny tylko wtedy, gdy harmonogram jest uruchomiony.

## Tylko przy otwartym ekranie

Aby harmonogram działał tylko wtedy, gdy otwarty jest określony ekran, na przykład ekran tytułowy:

1. Otwórz układ danego ekranu w edytorze układu.
2. Kliknij prawym przyciskiem myszy tło edytora, wybierz **Edytuj skrypt akcji „Otwórz ekran”** i dodaj akcję **Start Scheduler** z identyfikatorem harmonogramu.
3. Ponownie kliknij prawym przyciskiem myszy tło, wybierz **Edytuj skrypt akcji „Zamknij ekran”** i dodaj akcję **Stop Scheduler** z tym samym identyfikatorem.

# Zarządzanie harmonogramami

<img width="800" alt="Okno Zarządzaj harmonogramami z trzema harmonogramami, zaznaczonym random_tip, jego ustawieniami i stanem Running po prawej stronie" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_manage.png?raw=true">

- Kliknij harmonogram, aby po prawej stronie zobaczyć jego ustawienia, informację o tym, czy działa, oraz jego skrypt akcji.
- Kliknięcie **Edytuj akcje** lub kliknięcie harmonogramu prawym przyciskiem myszy otwiera jego skrypt akcji.
- Kliknij dwukrotnie identyfikator harmonogramu, aby zmienić jego nazwę. `Enter` zapisuje nazwę, a `Esc` anuluje zmianę. Zmiana nazwy zatrzymuje harmonogram, a akcje używające starego identyfikatora przestają go odnajdywać.
- **Usuń harmonogram** usuwa zaznaczony harmonogram po potwierdzeniu.
- **Eksportuj dla AI** kopiuje zaznaczony harmonogram lub wszystkie harmonogramy do wykorzystania w [czacie z AI](/export-for-ai).
- Pasek wyszukiwania pozwala znaleźć harmonogramy po ich identyfikatorze.

Harmonogramy są zapisywane w pliku `config/fancymenu/scheduler_instances.txt` (zobacz [Lokalizacje przechowywania danych](/data-storage-locations)). Każdy [profil](/profiles) ma własne harmonogramy.

# Przykład: przypomnienie o przerwie

Powiadomienie wyświetlane co 30 minut od uruchomienia gry:

1. Dodaj harmonogram z akcją [**Show Toast**](/action-scripts#show-toast). Ustaw **Tytuł** na `Time for a Break`, a **Wiadomość** na `Stand up, stretch and drink some water.`
2. W oknie **Edytuj ustawienia** ustaw **Identyfikator harmonogramu** na `break_reminder`, **Opóźnienie startu (ms)** i **Opóźnienie tyknięcia (ms)** na `1800000`, a opcję **Uruchom przy starcie** na **Włączone**.

Bez ustawienia **Opóźnienia startu (ms)** pierwsze powiadomienie pojawiłoby się zaraz po uruchomieniu gry.

# Warto wiedzieć

- Ustawiaj **Opóźnienie tyknięcia (ms)** na możliwie największą wartość, na jaką pozwala zadanie. Przy `0` akcje uruchamiają się 20 razy na sekundę, a wolne akcje powodują lagi.
- Gdy gra działa z opóźnieniem, kilka wykonań może nastąpić jedno po drugim.
- Zmiany w skrypcie akcji zaczynają działać od razu, nawet gdy harmonogram jest uruchomiony. Zmiany ustawień zaczną działać przy następnym uruchomieniu harmonogramu.
- Jeśli akcja się nie powiedzie, harmonogram nadal działa. Błąd trafia do logu gry: `logs/latest.log`.
- Jeśli potrzebujesz jednorazowego opóźnienia w skrypcie akcji, na przykład „otwórz ekran 2 sekundy po kliknięciu”, prostszym rozwiązaniem jest blok [Execute Later](/action-scripts#execute-later).
