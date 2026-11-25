---
title: Zmienne
description: >-
  Jak przechowywać teksty i listy w zmiennych oraz używać ich w tekstach,
  akcjach i wymaganiach.
sourceBlobSha: 2f0d48fd6cc100f976d4fdf1bceb28fe1a540a52
---

# Zmienne

Zmienne to wartości zapamiętywane przez FancyMenu, nawet po zamknięciu gry. Używaj ich do zliczania kliknięć, zapamiętywania wyborów, śledzenia postępów lub przechowywania list, takich jak wskazówki wyświetlane podczas ładowania. Teksty, akcje, wymagania, nasłuchiwacze i niektóre elementy mogą odczytywać zmienne i zmieniać ich wartości.

> [!TIP]
> Akcje dotyczące zmiennych są wymienione w sekcji [Skrypty akcji](/action-scripts), wymagania w sekcji [Wymagania](/conditions), a nasłuchiwacz w sekcji [Nasłuchiwacze](/listeners#on-variable-updated-fm-variable).

# Zmienne tekstowe i listowe

Istnieją dwa rodzaje zmiennych:

- Zmienne tekstowe przechowują jeden tekst, na przykład `dark`, `5` lub `true`.
- Zmienne listowe przechowują listę wpisów, na przykład wskazówki wyświetlane podczas ładowania lub nazwy serwerów. Każdy wpis jest osobnym tekstem.

Pozycja wpisu na liście to jego indeks. Pierwszy wpis ma indeks `0`, drugi `1` i tak dalej. Ujemne indeksy liczy się od końca, więc `-1` oznacza ostatni wpis.

Elementy, które obsługują tylko tekst, takie jak `$$name` lub **Czy wartość zmiennej jest równa (FM Variable)**, pobierają listę w postaci tablicy JSON zawierającej jej wpisy, na przykład `["Przygotuj łóżko przed pierwszą nocą.","Pochodnie odstraszają większość mobów."]`.

# Zarządzanie zmiennymi

Otwórz **pasek menu -> Dostosowywanie -> Zarządzaj zmiennymi**. Ta opcja jest dostępna na pasku menu tylko poza edytorem układu.

<img width="800" alt="Dodawanie w sekcji Zarządzaj zmiennymi zmiennej tekstowej menu_theme o wartości dark oraz zmiennej listowej tips zawierającej trzy wskazówki" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_manage.gif?raw=true">

## Dodawanie zmiennych

1. Kliknij listę prawym przyciskiem myszy i wybierz **Dodaj zmienną tekstową** lub **Dodaj zmienną listową**.
2. Wpisz nazwę i kliknij **Gotowe**.

Nazwy mogą zawierać małe litery, cyfry oraz znaki `.`, `_` i `-`. Każda nazwa może wystąpić tylko raz.

## Zmienianie zmiennych

Kliknij zmienną prawym przyciskiem myszy, aby wyświetlić następujące opcje:

| Opcja | Działanie |
|---|---|
| **Ustaw wartość** | Ustawia tekst zmiennej tekstowej. |
| **Edytuj listę** | Otwiera edytor listy dla zmiennej listowej (patrz poniżej). |
| **Konwertuj na listę…** | Zmienia zmienną tekstową w listową. **Separator** dzieli tekst na wpisy: wpisz `\n`, aby podzielić tekst w miejscach podziału wiersza. Opcja **Usuń spacje z wpisów** usuwa spacje wokół każdego wpisu, a **Pomiń puste wpisy** pomija puste wpisy. Tekst będący już tablicą JSON, na przykład `["a","b"]`, zostanie odczytany jako taka tablica (**Odczytaj jako tablicę JSON**). |
| **Konwertuj na tekst…** | Zmienia zmienną listową w tekstową. **Separator** jest wstawiany między wpisy, a opcja **Zachowaj tekst JSON** zachowuje listę jako tablicę JSON. |
| **Czyść zmienną przy uruchomieniu gry** | Opróżnia zmienną przy każdym uruchomieniu gry. Przydatne w przypadku wartości, które powinny być przechowywane tylko przez jedną sesję. |
| **Usuń zmienną** | Usuwa zmienną. |
| **Kopiuj** i **Wklej** | Tworzy kopię zmiennej. |
| **Eksportuj zmienną dla AI** | Eksportuje zmienną na potrzeby [czatów AI](/export-for-ai). |

Zmiany są wprowadzane od razu. Cofaj je za pomocą `Ctrl + Z`, a ponawiaj za pomocą `Ctrl + Y` (`Cmd` w systemie macOS). Zacznij pisać, aby wyszukiwać, naciśnij `Enter`, aby edytować zaznaczoną zmienną, lub `Delete`, aby ją usunąć.

## Edytowanie list

Edytor listy wyświetla każdy wpis wraz z jego indeksem.

- Aby dodać wpisy, kliknij **Dodaj wpis** pod listą, wpisz treść i naciśnij `Enter`. Od razu rozpoczniesz dodawanie kolejnego wpisu. Naciśnij `Enter` w pustym polu wpisu lub `Esc`, aby zakończyć dodawanie.
- Aby edytować wpis, kliknij go dwukrotnie. `Shift + Enter` otwiera go w edytorze tekstu, w którym można dodawać podziały wiersza.
- Aby zmienić kolejność wpisów, przeciągnij je lub naciśnij `Alt + Up` i `Alt + Down`.
- Kliknij wpis prawym przyciskiem myszy, aby wybrać **Duplikuj wpis** (`Ctrl + D`), **Usuń wpis** (`Delete`), **Kopiuj**, **Wklej**, **Przenieś w górę** lub **Przenieś w dół**.
- Opcja **Edytuj jako tekst** pozwala edytować wszystkie wpisy naraz, po jednym w każdym wierszu.

Przycisk **Gotowe** zapisuje listę. Przycisk **Anuluj** odrzuca wszystkie zmiany wprowadzone w edytorze listy.

# Wyświetlanie zmiennych w tekście

Wpisz `$$` i nazwę zmiennej, aby wyświetlić jej wartość: zmienna o nazwie `menu_theme` będzie zapisana jako `$$menu_theme`. Działa to w każdym tekście obsługującym [symbole zastępcze](/placeholders), na przykład w [elementach tekstowych](/text-in-menus), etykietach przycisków, podpowiedziach oraz wartościach akcji i wymagań. Tekst aktualizuje się automatycznie po zmianie zmiennej.

```
Aktualny motyw: $$menu_theme
```

- `$$name` odnoszące się do nieistniejącej zmiennej pozostaje bez zmian.
- Gdy nazwy zaczynają się tak samo, na przykład `coins` i `coins_record`, zapis `$$coins_record` zawsze odnosi się do dłuższej nazwy.
- Lista jest wyświetlana jako tablica JSON. Te symbole zastępcze pozwalają wyświetlać listy w czytelniejszy sposób:

| Symbol zastępczy | Przykład | Wynik |
|---|---|---|
| **Pobierz wartość zmiennej (FM Variable)** | `{"placeholder":"getvariable","values":{"name":"clicks"}}` | Wartość lub `0`, gdy zmienna jest pusta albo nie istnieje. Najlepsze rozwiązanie dla liczb. |
| **Pobierz wpis z listy (FM Variable)** | `{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"Na razie brak wskazówek"}}` | Wpis o podanym indeksie lub wartość `fallback`, jeśli takiego wpisu nie ma. |
| **Liczba wpisów na liście (FM Variable)** | `{"placeholder":"list_size","values":{"name":"tips"}}` | Liczba wpisów na liście. |
| **Indeks wpisu na liście (FM Variable)** | `{"placeholder":"list_index_of","values":{"name":"tips","value":"Pochodnie odstraszają większość mobów.","ignore_case":"false"}}` | Indeks pierwszego wpisu dokładnie pasującego do całej wartości `value` lub `-1`. |
| **Połącz wpisy listy (FM Variable)** | `{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}` | Wszystkie wpisy połączone w jeden tekst, z wartością `separator` między nimi (domyślnie `, `). `\n` oznacza podział wiersza. |

# Zmienianie zmiennych za pomocą akcji

[Skrypty akcji](/action-scripts) zmieniają zmienne po kliknięciu przycisku, uruchomieniu licznika, wywołaniu nasłuchiwacza i w innych sytuacjach.

## Zmienne tekstowe

Akcja [**Ustaw wartość zmiennej (FM Variable)**](/action-scripts#set-variable-value-fm-variable) przyjmuje nazwę i nową wartość rozdzielone znakiem `:`. Jeśli zmienna jeszcze nie istnieje, zostanie utworzona.

```
menu_theme:dark
```

Tylko pierwszy znak `:` oddziela nazwę, więc wartość może zawierać kolejne, na przykład `last_server:play.example.net:25565`.

Aby zliczać kliknięcia przycisku, dodaj 1 do poprzedniej wartości:

```
clicks:{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

**Pobierz wartość zmiennej (FM Variable)** zwraca `0`, gdy `clicks` jest jeszcze puste, więc pierwsze kliknięcie ustawia wartość na `1`.

Akcja Ustaw wartość zmiennej nigdy nie zmienia listy w tekst. Tablica JSON staje się wpisami listy, pusty tekst ją opróżnia, a każdy inny tekst staje się jej jedynym wpisem.

Akcja [**Usuń zmienną (FM Variable)**](/action-scripts#delete-variable-fm-variable) usuwa jedną zmienną, a akcja [**Wyczyść wszystkie zmienne (FM Variable)**](/action-scripts#clear-all-variables-fm-variable) usuwa je wszystkie.

## Akcje list

Każda akcja listy ma własne okno. Wszystkie jej pola obsługują symbole zastępcze.

| Akcja | Działanie |
|---|---|
| [**Dodaj do listy (FM Variable)**](/action-scripts#add-to-list-fm-variable) | Dodaje wpis na końcu listy lub pod określonym indeksem. Opcja **Pomiń, jeśli wpis już znajduje się na liście** nie dodaje wpisu, jeśli lista już go zawiera. |
| [**Ustaw wpis na liście (FM Variable)**](/action-scripts#set-list-entry-fm-variable) | Zastępuje wpis pod określonym indeksem. |
| [**Usuń z listy (FM Variable)**](/action-scripts#remove-from-list-fm-variable) | Usuwa **wpis o indeksie**, **pierwsze dopasowanie** wartości lub **wszystkie dopasowania**. |
| [**Wyczyść listę (FM Variable)**](/action-scripts#clear-list-fm-variable) | Usuwa wszystkie wpisy. Lista pozostaje, ale jest pusta. |
| [**Ustaw listę (FM Variable)**](/action-scripts#set-list-fm-variable) | Zastępuje wszystkie wpisy częściami **tekstu do podziału** lub wpisami z **tablicy JSON**. Zapis `$$other_list` jako tablica JSON kopiuje inną listę. |
| [**Uporządkuj listę (FM Variable)**](/action-scripts#arrange-list-fm-variable) | **Sortuj A–Z**, **Sortuj Z–A**, **Liczby: od najmniejszej**, **Liczby: od największej**, **Odwróć kolejność**, **Losowo** lub **Usuń duplikaty**. |

- Akcje list tworzą nieistniejącą listę i zmieniają puste zmienne tekstowe w listy. Nigdy nie zmieniają zmiennej tekstowej zawierającej wartość: najpierw [przekonwertuj ją](#changing-variables).
- Wpisz nazwę listy bez `$$`. Jeśli użyjesz `$$`, akcja potraktuje wartość tej zmiennej jako nazwę.

Na przykład element tekstowy wyświetla pierwszy wpis z listy `tips`:

```
{"placeholder":"list_get","values":{"name":"tips","index":"0"}}
```

Przycisk Dalej podpowiedź ma w skrypcie akcji przypisaną akcję **Uporządkuj listę (FM Variable)** z opcją **Losowo**:

<img width="800" alt="Dodawanie akcji Uporządkuj listę z listą tips i opcją Losowo do skryptu akcji przycisku Dalej podpowiedź w edytorze układu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_script.gif?raw=true">

Każde kliknięcie losowo miesza kolejność listy, więc tekst wyświetla losową wskazówkę:

<img width="800" alt="Kliknięcie przycisku Dalej podpowiedź wyświetla inną wskazówkę dnia" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_result.gif?raw=true">

## Przechodzenie przez listę

Pętla [FOR EACH](/action-scripts#for-each-loop) wykonuje zawarte w niej akcje raz dla każdego wpisu na liście, od pierwszego do ostatniego.

1. Kliknij prawym przyciskiem myszy obszar skryptu w edytorze skryptów akcji i wybierz **Dodaj pętlę FOR EACH**.
2. Wpisz nazwę zmiennej listowej bez `$$` i kliknij **Gotowe**.
3. Dodaj akcje wewnątrz pętli. W ich wartościach `$$list_entry` oznacza bieżący wpis, a `$$list_index` — jego indeks.

Na przykład lista `starter_commands` zawierająca wpisy `/time set day` i `/weather clear` wraz z akcją [**Wyślij wiadomość/polecenie na czacie**](/action-scripts#send-chat-messagecommand) umieszczoną w pętli i mającą poniższą wartość wykona oba polecenia:

```
$$list_entry
```

- Pętla odczytuje listę tylko raz, przy uruchomieniu. Akcje w jej wnętrzu mogą zmieniać listę, ale nie wpłynie to na wpisy, przez które przejdzie pętla.
- Zmienna tekstowa lub nieistniejąca lista sprawia, że pętla nie wykona się ani razu.
- Podobnie jak pętle WHILE, pętla zatrzymuje się po 3 sekundach, aby nie mogła zawiesić gry.

# Sprawdzanie zmiennych

[Wymagania](/conditions) pozwalają wyświetlać elementy lub wykonywać części skryptów akcji tylko wtedy, gdy zmienna ma określoną wartość.

- [**Czy wartość zmiennej jest równa (FM Variable)**](/conditions#is-variable-value-fm-variable) sprawdza całą wartość. W przypadku list porównuje tablicę JSON zawierającą wszystkie wpisy.
- [**Lista zawiera wpis (FM Variable)**](/conditions#list-contains-entry-fm-variable) sprawdza, czy lista zawiera dany wpis. Musi on dokładnie pasować do całego wpisu. Opcja **Ignoruj wielkość liter** sprawia, że `Apple` pasuje do `apple`.
- [**Czy jest liczbą**](/conditions#is-number) porównuje liczby, na przykład sprawdza, czy `$$clicks` jest większe niż `5`.

Na przykład przycisk otwiera najnowszy wpis z wiadomościami i dodaje `news_42` do listy `read_news` za pomocą akcji **Dodaj do listy (FM Variable)**. Odznaka „Nowość!” obok przycisku ma wymaganie **Lista zawiera wpis (FM Variable)** dla `news_42`, a **Tryb wymagania** ustawiono na **Przeciwny**. Odznaka znika po przeczytaniu wpisu przez gracza.

# Łączenie zmiennych z elementami

- [Pole tekstowe](/elements#text-input-field): opcja **Połącz ze zmienną** zapisuje wpisywany przez gracza tekst w zmiennej, a pole wyświetla jej wartość. Jeśli pole jest połączone z listą, wpisany tekst zastępuje całą listę.
- [Pole wyboru](/elements#checkbox): włącz **Tryb zmiennej** i ustaw **Połącz ze zmienną**. Pole wyboru zapisuje w zmiennej wartość `true` lub `false`.
- [Suwak](/elements#slider) typu **Lista wartości**: opcja **Wartości ze zmiennej listowej** pobiera wartości suwaka z listy. Wpisy dodane do listy lub z niej usunięte pojawiają się od razu.

# Reagowanie na zmiany

- Nasłuchiwacz [**Po aktualizacji zmiennej [FM Variable]**](/listeners#on-variable-updated-fm-variable) uruchamia skrypt akcji za każdym razem, gdy zostanie ustawiona zmienna.
- Polecenie [`/fmvariable`](/commands#fmvariable) pozwala ustawiać i odczytywać zmienne na czacie, w blokach poleceń oraz w innych modach.

# Gdzie są zapisywane zmienne

FancyMenu zapisuje zmienne od razu w pliku `<game-directory>/config/fancymenu/user_variables.db`, dzięki czemu są zachowywane po ponownym uruchomieniu gry.

- Zmienne dotyczą całej instancji Minecrafta i jej aktywnego [profilu](/profiles). Nie są oddzielne dla poszczególnych układów, światów, serwerów ani graczy.
- W nazwach rozróżniana jest wielkość liter.
- Nie przechowuj w zmiennych haseł, tokenów ani innych poufnych danych. Każdy, kto ma dostęp do folderu gry, może je odczytać.
