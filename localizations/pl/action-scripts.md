---
title: Skrypty akcji
description: >-
  Spraw, by przyciski i menu wykonywały różne czynności za pomocą skryptów
  akcji. Poznaj wszystkie akcje FancyMenu.
sourceBlobSha: 07ed5af6f189a91c518131cf3a7ab7a1e0a8305d
---

# Skrypty akcji

Skrypt akcji to lista czynności wykonywanych przez FancyMenu po wystąpieniu określonego zdarzenia, takiego jak kliknięcie przycisku lub otwarcie menu. Każda pozycja na liście to akcja: otwarcie menu, dołączenie do serwera, wyświetlenie wiadomości, odtworzenie dźwięku i wiele innych. Instrukcje takie jak IF i WHILE decydują o tym, które akcje zostaną wykonane i jak często.

> [!CAUTION]
> Skrypty akcji mogą zmieniać pliki, łączyć się z serwerami, otwierać linki i wykonywać polecenia. Korzystaj wyłącznie ze skryptów pochodzących z zaufanych układów.

<img width="800" alt="Skrypt akcji przycisku tworzony w edytorze układu: Edytuj skrypt akcji, wybór akcji z opcją Pokaż powiadomienie oraz tytuł i wiadomość powiadomienia" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_make.gif?raw=true">

# Tworzenie skryptu akcji

1. W edytorze układu kliknij prawym przyciskiem myszy przycisk i wybierz **Edytuj skrypt akcji**.
2. Naciśnij `A`, aby otworzyć wybór akcji.
3. Wyszukaj akcję, kliknij ją, a następnie kliknij **Następny krok**.
4. Skonfiguruj akcję w jej oknie i kliknij **Gotowe**. W przypadku akcji bez ustawień wystarczy kliknąć **Gotowe** w oknie wyboru.
5. Kliknij **Gotowe** w edytorze skryptów, a następnie zapisz układ.

Poza edytorem skrypt przycisku jest wykonywany po jego kliknięciu:

<img width="800" alt="Kliknięcie przycisku Co nowego? na ekranie tytułowym wyświetla powiadomienie z tytułem aktualizacji i wiadomością" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_use.gif?raw=true">

> [!TIP]
> Kliknij prawym przyciskiem myszy obszar skryptu i otwórz **Dodaj akcję**, aby zobaczyć listę wszystkich akcji. Kliknij prawym przyciskiem myszy akcję na liście, aby dodać ją do ulubionych i wyświetlać na górze.

# Gdzie można używać skryptów akcji

| Gdzie | Kiedy jest wykonywany | Gdzie go edytować |
|---|---|---|
| [Przycisk](/elements#button) | Po kliknięciu przycisku. | Kliknij przycisk prawym przyciskiem myszy -> **Edytuj skrypt akcji** |
| [Suwak](/elements#slider) | Gdy zmieni się wartość suwaka. `$$value` to nowa wartość. | Kliknij suwak prawym przyciskiem myszy -> **Edytuj skrypt akcji** |
| [Pole wyboru](/elements#checkbox) | Gdy pole wyboru zostanie zaznaczone lub odznaczone. `$$value` to jego nowy stan: `true` lub `false`. | Kliknij pole wyboru prawym przyciskiem myszy -> **Edytuj skrypt akcji** |
| [Licznik](/elements#ticker) | Zgodnie z ustawieniem **Tryb taktowania**: wielokrotnie, raz na sesję gry lub raz po załadowaniu menu. | Kliknij licznik prawym przyciskiem myszy -> **Edytuj skrypt akcji** |
| Otwieranie menu | Gdy otwiera się menu układu. | Kliknij tło edytora prawym przyciskiem myszy -> **Edytuj skrypt akcji „Otwórz ekran”** |
| Zamykanie menu | Gdy zamyka się menu układu. | Kliknij tło edytora prawym przyciskiem myszy -> **Edytuj skrypt akcji „Zamknij ekran”** |
| [Nasłuchiwacze](/listeners) | Gdy wystąpi ich zdarzenie, na przykład naciśnięcie klawisza lub wiadomość na czacie. | **Pasek menu -> Dostosowywanie -> Zarządzaj nasłuchiwaczami** |
| [Harmonogramy](/schedulers) | Zgodnie z ich harmonogramem, nawet gdy żadne menu nie jest otwarte. | **Pasek menu -> Dostosowywanie -> Zarządzaj harmonogramami** |

Skrypty otwierania i zamykania są również dostępne w menu edytora **Układ -> Właściwości układu**.

# Edytor skryptów

- Akcje są wykonywane od góry do dołu. Wpisy wewnątrz instrukcji lub folderu są wcięte.
- Nowe wpisy są dodawane poniżej zaznaczonego wpisu. Jeśli zaznaczona jest instrukcja lub folder, wpisy są dodawane na jego początku.
- Kliknij dwukrotnie wartość, aby edytować ją bezpośrednio na liście. Wartości, przy których wyświetla się krótkie podsumowanie, otwierają osobne okno.
- Przeciągaj wpisy, aby je przenosić. Łańcuchy IF, pętle i foldery można zwinąć za pomocą małego przełącznika przed nimi. Zmienia to tylko widok.
- Pasek po prawej stronie to mapa całego skryptu. Kliknij go, aby przejść do wybranej części.
- Kliknij obszar skryptu prawym przyciskiem myszy, aby uzyskać dostęp do pozostałych opcji, takich jak dodawanie instrukcji czy **Eksportuj skrypt akcji dla AI** (zobacz [Eksport dla AI](/export-for-ai)).
- Kliknięcie **Anuluj** lub zamknięcie okna odrzuca zmiany. Jeśli wprowadzono zmiany, edytor najpierw zapyta o potwierdzenie.

## Skróty klawiszowe

Na macOS klawisz `Ctrl` oznacza `Cmd`.

| Skrót | Działanie |
|---|---|
| `A` | Otwiera wybór akcji. |
| `Enter` | Edytuje zaznaczony wpis. |
| `Delete` | Usuwa zaznaczony wpis. |
| `Up` / `Down` | Zaznacza wpis powyżej lub poniżej. |
| `Shift + Up` / `Shift + Down` | Przesuwa zaznaczony wpis w górę lub w dół. |
| `Ctrl + C` / `Ctrl + V` | Kopiuje i wkleja akcję. Nie można kopiować instrukcji ani bloków. |
| `Ctrl + Z` | Cofa. |
| `Ctrl + Y` lub `Ctrl + Shift + Z` | Ponawia. |
| `Ctrl + S` | Zapisuje skrypt i zamyka edytor, tak jak **Gotowe**. |

# Instrukcje

Instrukcje decydują o tym, które akcje zostaną wykonane i jak często. Dodaj je, klikając obszar skryptu prawym przyciskiem myszy.

## If, Else-If i Else

Opcja **Dodaj instrukcję IF** pyta o [warunki](/conditions). Akcje wewnątrz IF są wykonywane tylko wtedy, gdy warunki są spełnione.

Kliknij IF prawym przyciskiem myszy, aby dodać kolejne instrukcje do łańcucha:

- **Dodaj instrukcję ELSE-IF**: sprawdza własne warunki, jeśli powyższa instrukcja IF nie została wykonana.
- **Dodaj instrukcję ELSE**: jest wykonywana, jeśli nie została wykonana żadna wcześniejsza instrukcja z łańcucha.

Na przykład IF z warunkiem **Układ jest włączony** może wyświetlać powiadomienie tylko wtedy, gdy włączony jest zimowy układ, a ELSE może w przeciwnym razie odtworzyć dźwięk.

## Pętla While

Opcja **Dodaj pętlę WHILE** powtarza zawarte w niej akcje tak długo, jak spełnione są jej [warunki](/conditions).

Każde uruchomienie kończy się po 3 sekundach, więc nieskończona pętla nie może zawiesić gry. To nie jest timer: jeśli coś ma się wydarzyć później lub wielokrotnie, użyj [Wykonaj później](#execute-later), [licznika](/elements#ticker) lub [harmonogramu](/schedulers).

## Pętla For Each

Opcja **Dodaj pętlę FOR EACH** wykonuje zawarte w niej akcje raz dla każdego wpisu na [liście zmiennej](/variables#text-and-list-variables), od pierwszego do ostatniego wpisu.

- `$$list_entry` oznacza bieżący wpis, a `$$list_index` — jego indeks. Pierwszy wpis ma indeks 0.
- Obie zmienne działają w wartościach akcji i warunkach wewnątrz pętli.
- Wpisz nazwę listy bez `$$`, na przykład `quest_log`. W nazwie mogą być używane placeholdery.
- Pętla odczytuje listę tylko raz, na początku, dlatego akcje wewnątrz niej mogą bezpiecznie zmieniać listę.
- Podobnie jak pętle WHILE, każde uruchomienie kończy się po 3 sekundach.

Przykłady znajdziesz w sekcji [Przechodzenie przez listę](/variables#going-through-a-list).

# Bloki

Bloki zmieniają sposób wykonywania akcji lub pomagają uporządkować skrypt. Dodaj je, klikając obszar skryptu prawym przyciskiem myszy.

## Blok opóźnienia

Opcja **Dodaj blok DELAY GATE** wstrzymuje zawarte w nim akcje na określony czas w milisekundach (`1000` to jedna sekunda).

- Gdy skrypt po raz pierwszy dotrze do bloku, uruchamia on timer, ale pomija swoje akcje. Pozostała część skryptu jest od razu wykonywana dalej.
- Jeśli skrypt ponownie dotrze do bloku przed upływem czasu, akcje znów zostaną pominięte.
- Od tej chwili akcje bloku są wykonywane za każdym razem, gdy skrypt do niego dotrze.
- W skryptach elementów timer uruchamia się ponownie po ponownym otwarciu menu lub zmianie jego rozmiaru.

Blok przydaje się w przypadku [liczników](/elements#ticker), na przykład do wyświetlenia czegoś dopiero po kilku sekundach od otwarcia menu. Sam z siebie niczego nie uruchamia — do tego służy opcja Wykonaj później.

## Wykonaj później

Opcja **Dodaj blok EXECUTE LATER** wykonuje zawarte w nim akcje jeden raz po upływie określonego czasu w milisekundach. Pozostała część skryptu jest od razu wykonywana dalej.

Za każdym razem, gdy skrypt dotrze do bloku, rozpoczyna się nowe odliczanie. To dobre rozwiązanie w przypadku skryptów uruchamianych tylko raz, takich jak skrypt kliknięcia przycisku lub otwarcia menu.

## Folder

Opcja **Dodaj folder** grupuje akcje pod określoną nazwą. Folder wykonuje wszystkie zawarte w nim akcje i służy jedynie do porządkowania długich skryptów. Kliknij dwukrotnie jego nazwę, aby ją zmienić.

## Komentarz

Opcja **Dodaj komentarz** dodaje notatkę dla siebie. Nie wykonuje żadnej czynności. Kliknij komentarz dwukrotnie, aby go edytować.

# Jak działają skrypty

- Akcje są wykonywane od góry do dołu. Jeśli akcja się nie powiedzie, do dziennika gry zostanie zapisany błąd, ale pozostała część skryptu będzie nadal wykonywana.
- Wartości placeholderów są pobierane w chwili wykonywania akcji, dlatego akcja widzi zmiany wprowadzone przez wcześniejsze akcje.
- Pobieranie plików, rozpakowywanie plików ZIP i żądania internetowe są realizowane w tle. Następna akcja na nie nie czeka. Aby wykonać akcje po ich zakończeniu, użyj nasłuchiwaczy [**Po pobraniu pliku za pomocą akcji**](/listeners#on-file-downloaded-via-action) i [**Po rozpakowaniu ZIP za pomocą akcji**](/listeners#on-zip-extracted-via-action) albo zmiennej odpowiedzi akcji [**Wyślij żądanie HTTP**](#send-http-request).

# Wartości akcji

Większość akcji wymaga wartości, na przykład adresu serwera. Proste wartości to wpisywany tekst. Akcje z większą liczbą ustawień mają własne okno.

## Placeholdery

Wartości mogą zawierać [placeholdery](/placeholders), na przykład nazwę gracza. Są one zastępowane w chwili wykonywania akcji:

```
/say Witaj ponownie, {"placeholder":"playername"}!
```

## Zmienne $$

Wpisz `$$` i nazwę zmiennej, aby użyć jej wartości w akcji lub warunku. Wielkość liter w nazwach ma znaczenie. Działa to z dwoma rodzajami zmiennych:

### Własne zmienne

Każda zmienna utworzona w **Pasek menu -> Dostosowywanie -> Zarządzaj zmiennymi** działa z `$$` i swoją nazwą. Zmienna o nazwie `coins` to `$$coins` w każdym skrypcie. Na przykład akcja **Wyświetl na czacie [po stronie klienta]** z taką wartością informuje gracza, ile ma monet:

```
&6Masz $$coins monet!
```

Zobacz [Zmienne](/variables), aby dowiedzieć się, jak je tworzyć i zmieniać.

### Zmienne skryptu

Niektóre funkcje udostępniają skryptowi własne zmienne:

- [Suwak](/elements#slider) udostępnia `$$value`, czyli nową wartość.
- [Pole wyboru](/elements#checkbox) udostępnia `$$value`, czyli nowy stan: `true` lub `false`.
- [Pętla For Each](#for-each-loop) udostępnia `$$list_entry` i `$$list_index`.
- Każdy [nasłuchiwacz](/listeners#listener-variables) wymienia udostępniane przez siebie zmienne, na przykład naciśnięty klawisz.

Zmienne te istnieją tylko podczas wykonywania skryptu. Jeśli zmienna skryptu ma taką samą nazwę jak jedna z własnych zmiennych, `$$name` oznacza zmienną skryptu.

# Wszystkie akcje

Wszystkie akcje dostępne w FancyMenu, pogrupowane według przeznaczenia.

## Ekrany i menu

### Otwórz ekran lub niestandardowy interfejs

**Identyfikator:** `opengui`

Otwiera menu gry, moda lub [niestandardowy interfejs](/custom-guis).

**Wartość:** [identyfikator ekranu](/screen-identifiers), na przykład `options_screen`

Wielkość liter ma znaczenie. Niektórych menu modów nie można w ten sposób otworzyć. W takim przypadku użyj akcji [**Naśladuj przycisk gry/moda**](#mimic-vanillamod-button) dla przycisku, który otwiera to menu.

### Zamknij ekran

**Identyfikator:** `closegui`

Zamyka otwarte menu. Poza światem gry otwiera ekran tytułowy.

**Wartość:** brak

### Odśwież ekran

**Identyfikator:** `update_screen`

Przebudowuje otwarte menu, tak jak przy zmianie rozmiaru okna. Przydatne po zmianie skali interfejsu lub innych opcji.

**Wartość:** brak

### Wróć do poprzedniego ekranu

**Identyfikator:** `back_to_last_screen`

Wraca do wcześniej otwartego menu. W przypadku [niestandardowego interfejsu](/custom-guis) jest to menu, z którego został on otwarty.

**Wartość:** brak

### Pokaż powiadomienie

**Identyfikator:** `show_toast`

Wyświetla powiadomienie w prawym górnym rogu. Skonfiguruj je w osobnym oknie:

- **Szerokość powiadomienia**: od 120 do 320 pikseli.
- **Czas wyświetlania (ms)**: jak długo powiadomienie jest widoczne — od 1 sekundy (`1000`) do 10 minut.
- **Tytuł** i **Wiadomość**: tekst z [kodami formatowania](/text-formatting#minecraft-text-formatting) lub w formacie JSON komponentu tekstowego Minecrafta.
- **Źródło tekstury ikony** i **Źródło tekstury tła**: opcjonalne [obrazy](/resources). Ikony najlepiej wyglądają w rozmiarze 20 × 20 pikseli, a tła powinny mieć 32 piksele wysokości i szerokość równą szerokości powiadomienia.

### Naśladuj przycisk gry/moda

**Identyfikator:** `mimicbutton`

Kliknie przycisk gry lub moda tak, jak zrobiłby to gracz.

**Wartość:** [lokalizator widżetu](/widget-locators) przycisku, na przykład `title_screen:mc_titlescreen_options_button`

Aby go uzyskać, kliknij przycisk w edytorze prawym przyciskiem myszy i wybierz **Kopiuj lokalizator widżetu**.

## Układy i elementy

### Przełącz układ

**Identyfikator:** `toggle_layout`

Wyłącza włączony układ lub włącza wyłączony.

**Wartość:** nazwa układu bez `.txt`, na przykład `winter_title_screen`

### Włącz układ

**Identyfikator:** `enable_layout`

Włącza układ.

**Wartość:** nazwa układu bez `.txt`

### Wyłącz układ

**Identyfikator:** `disable_layout`

Wyłącza układ.

**Wartość:** nazwa układu bez `.txt`

Wszystkie trzy akcje układu zapisują zmianę i natychmiast aktualizują otwarte menu. Wielkość liter w nazwie ma znaczenie.

### Przełącz animator elementu

**Identyfikator:** `toggle_element_animator`

Włącza [animator elementu](/element-animator), jeśli jest wyłączony, lub go wyłącza, jeśli jest włączony. Animacja rozpoczyna się od początku. Zmiana stanu zostaje zapisana.

**Wartość:** identyfikator animatora elementu

### Włącz animator elementu

**Identyfikator:** `enable_element_animator`

Włącza [animator elementu](/element-animator). Jeśli był wyłączony, jego animacja rozpoczyna się od początku.

**Wartość:** identyfikator animatora elementu

### Wyłącz animator elementu

**Identyfikator:** `disable_element_animator`

Wyłącza [animator elementu](/element-animator) i resetuje jego animację.

**Wartość:** identyfikator animatora elementu

### Zresetuj animator elementu

**Identyfikator:** `reset_element_animator`

Rozpoczyna animację [animatora elementu](/element-animator) od początku, nie włączając go ani nie wyłączając.

**Wartość:** identyfikator animatora elementu

### Ustaw wartość pola tekstowego

**Identyfikator:** `set_text_input_field_value`

Ustawia tekst w [polu tekstowym](/elements#text-input-field) FancyMenu lub gry.

**Wartość:** `element_identifier|||text|||force`

Jeśli `force` ma wartość `true`, tekst zostanie zmieniony również wtedy, gdy pole jest wyłączone (nieaktywne).

### Przewiń element

**Identyfikator:** `scroll_scroll_area`

Przewija [obszar przewijania](/scrollable-areas) lub element [Tekst](/elements#text). Skonfiguruj akcję w osobnym oknie:

- **Identyfikator przewijanego elementu**: obszar lub element Tekst do przewinięcia.
- **Przewiń do**:
  - **Początku** lub **Końca**.
  - **Pozycji**: **Pozycja pozioma** i **Pozycja pionowa** w pikselach. Zostaw jedno pole puste, aby zachować jego bieżącą wartość.
  - **Elementu** (tylko obszary): przewija do chwili, gdy element o **Identyfikatorze elementu docelowego** znajdzie się na początku.
  - **Numeru wiersza** (tylko elementy Tekst): pierwszy wiersz ma numer `1`.
  - **Wiersza z tekstem** (tylko elementy Tekst): pierwszego wiersza zawierającego **Tekst w wierszu**. Wielkość liter nie ma znaczenia.
- **Płynnie przewiń**: przewija płynnie zamiast przeskakiwać. Wymaga włączonego płynnego przewijania dla danego elementu.

Nie robi nic, jeśli wskazany element nie istnieje.

## Dźwięk i wideo

### Następny utwór

**Identyfikator:** `audio_next_track`

Przechodzi do następnego utworu w elemencie [Audio](/elements#audio).

**Wartość:** identyfikator elementu Audio, na przykład `menu_music`

### Poprzedni utwór

**Identyfikator:** `audio_previous_track`

Wraca do poprzedniego utworu w elemencie [Audio](/elements#audio).

**Wartość:** identyfikator elementu Audio

### Ustaw głośność utworu

**Identyfikator:** `set_audio_element_volume`

Ustawia głośność elementu [Audio](/elements#audio) w zakresie od `0.0` (0%) do `1.0` (100%).

**Wartość:** `element_identifier:volume`, na przykład `menu_music:0.5`

### Wstrzymaj/wznów utwór

**Identyfikator:** `audio_toggle_play`

Wstrzymuje odtwarzany element [Audio](/elements#audio) lub wznawia jego odtwarzanie.

**Wartość:** identyfikator elementu Audio

### Odtwórz dźwięk

**Identyfikator:** `play_audio`

Odtwarza plik audio jeden raz. Skonfiguruj akcję w osobnym oknie, określając **Źródło dźwięku**, **Kanał dźwięku** i **Głośność bazową** (maksymalnie 100%).

- FancyMenu czeka do dziesięciu sekund na załadowanie dźwięku.
- Nie działa w [liczniku](/elements#ticker) działającym w tle (asynchronicznie). Zamiast tego FancyMenu wyświetli błąd.

Akcja [**Zatrzymaj wszystkie dźwięki akcji**](#stop-all-action-audios) zatrzymuje dźwięki uruchomione tą akcją.

### Zatrzymaj wszystkie dźwięki akcji

**Identyfikator:** `stop_all_action_audios`

Zatrzymuje wszystkie dźwięki uruchomione akcją [**Odtwórz dźwięk**](#play-audio). Odtwarzanie elementów Audio, dźwięki menu i dźwięki przycisków są kontynuowane.

**Wartość:** brak

### Ustaw głośność elementu wideo

**Identyfikator:** `set_video_element_volume`

Ustawia głośność elementu [Wideo](/video) w zakresie od `0.0` (0%) do `1.0` (100%).

**Wartość:** `video_element_identifier:volume`

### Ustaw czas odtwarzania elementu wideo

**Identyfikator:** `set_video_element_play_time`

Przechodzi do określonego czasu w elemencie [Wideo](/video), wyrażonego w milisekundach.

**Wartość:** `video_element_identifier:time_in_ms`, na przykład `intro_video:30000`

### Wstrzymaj/wznów element wideo

**Identyfikator:** `toggle_video_element_pause_state`

Wstrzymuje odtwarzany element [Wideo](/video) lub wznawia jego odtwarzanie.

**Wartość:** identyfikator elementu Wideo

### Ustaw głośność tła wideo

**Identyfikator:** `set_video_menu_background_volume`

Ustawia głośność [tła menu wideo](/video) w zakresie od `0.0` (0%) do `1.0` (100%).

**Wartość:** `background_identifier:volume`

> [!NOTE]
> Aby uzyskać identyfikator tła menu, kliknij tło edytora prawym przyciskiem myszy i wybierz **Kopiuj identyfikator tła**.

### Ustaw czas odtwarzania tła wideo

**Identyfikator:** `set_video_menu_background_play_time`

Przechodzi do określonego czasu [tła menu wideo](/video), wyrażonego w milisekundach.

**Wartość:** `background_identifier:time_in_ms`

### Wstrzymaj/wznów tło wideo

**Identyfikator:** `toggle_video_menu_background_pause_state`

Wstrzymuje odtwarzane [tło menu wideo](/video) lub wznawia jego odtwarzanie.

**Wartość:** identyfikator tła menu

## Światy i serwery

### Dołącz do serwera

**Identyfikator:** `joinserver`

Łączy z serwerem Minecrafta.

**Wartość:** `adres` lub `adres:port`, na przykład `play.example.net`

Jeśli nie podano portu, używany jest `25565`. Gdy świat lub serwer jest już wczytany, zamiast tego wyświetlany jest błąd. Serwery, których nie ma na liście serwerów, zostają do niej dodane.

### Wejdź do świata

**Identyfikator:** `loadworld`

Wczytuje świat dla jednego gracza.

**Wartość:** nazwa folderu świata w katalogu `saves`, na przykład `Survival Island`

Nie robi nic, jeśli taki świat nie istnieje. Gdy świat lub serwer jest już wczytany, zamiast tego wyświetlany jest błąd.

### Wejdź do ostatniego świata/dołącz do ostatniego serwera

**Identyfikator:** `join_last_world`

Wczytuje świat lub łączy z serwerem, na którym gracz grał ostatnio.

**Wartość:** brak

Gdy świat lub serwer jest już wczytany, zamiast tego wyświetlany jest błąd. Serwer, którego nie ma na liście serwerów, zostaje do niej dodany.

### Opuść świat lub serwer

**Identyfikator:** `disconnect_server_or_world`

Opuszcza świat lub serwer i otwiera menu.

**Wartość:** [identyfikator ekranu](/screen-identifiers) menu do otwarcia, na przykład `title_screen`

Działa tylko wtedy, gdy świat jest wczytany. Obsługiwane są również [niestandardowe interfejsy](/custom-guis). Jeśli nie można otworzyć menu, otwierany jest ekran tytułowy.

## Czat i polecenia

### Wyślij wiadomość na czacie/wykonaj polecenie

**Identyfikator:** `sendmessage`

Wysyła wiadomość na czacie lub wykonuje polecenie tak, jakby wpisał je gracz.

**Wartość:** wiadomość lub polecenie rozpoczynające się od `/`, na przykład `/spawn`

### Wykonaj polecenie na zintegrowanym serwerze

**Identyfikator:** `execute_command_as_integrated_server`

Wykonuje polecenie w trybie dla jednego gracza jako serwer, niezależnie od uprawnień gracza i ustawienia oszustw.

**Wartość:** polecenie, na przykład `/give @p minecraft:diamond 1`

> [!WARNING]
> Działa tylko w trybie dla jednego gracza, gdy świat nie jest otwarty dla sieci LAN. W pozostałych przypadkach nie robi nic.

### Wklej do czatu

**Identyfikator:** `paste_to_chat`

Wstawia tekst do pola wpisywania wiadomości na czacie, gdy świat jest wczytany. Jeśli czat nie jest otwarty, otwiera się z tym tekstem.

**Wartość:** `true:text` dodaje tekst do tego, co już wpisano, a `false:text` zastępuje dotychczasowy tekst

### Wyświetl na czacie [po stronie klienta]

**Identyfikator:** `display_in_chat_client_side`

Wyświetla wiadomość na czacie widoczną tylko dla tego gracza. Nic nie jest wysyłane na serwer.

**Wartość:** tekst z [kodami formatowania](/text-formatting#minecraft-text-formatting) lub w formacie JSON komponentu tekstowego Minecrafta, na przykład `&aWitaj ponownie!`

Nie robi nic, jeśli żaden świat nie jest wczytany.

## Zmienne i listy

### Ustaw wartość zmiennej (zmienna FM)

**Identyfikator:** `set_variable`

Ustawia [zmienną](/variables).

**Wartość:** `variable_name:value`, na przykład `coins:100`

- Tylko pierwszy znak `:` oddziela nazwę od wartości.
- [Zmienne listowe](/variables#text-and-list-variables) pozostają listami: tablica JSON, taka jak `["a","b"]`, staje się ich wpisami; inny tekst staje się ich jedynym wpisem, a pusty tekst je opróżnia.

### Usuń zmienną (zmienna FM)

**Identyfikator:** `delete_variable`

Całkowicie usuwa [zmienną](/variables). Pozostałe zmienne nie ulegają zmianie. Aby tylko ją opróżnić, użyj akcji [**Ustaw wartość zmiennej (zmienna FM)**](#set-variable-value-fm-variable).

**Wartość:** nazwa zmiennej

### Wyczyść wszystkie zmienne (zmienna FM)

**Identyfikator:** `clear_variables`

Usuwa wszystkie [zmienne](/variables), tekstowe i listowe.

**Wartość:** brak

### Dodaj do listy (zmienna FM)

**Identyfikator:** `add_to_list`

Dodaje wpis do [zmiennej listowej](/variables#list-actions).

- **Zmienna listowa**: nazwa listy. Jeśli zmienna o tej nazwie jeszcze nie istnieje, akcja utworzy listę.
- **Nowy wpis**: tekst wpisu.
- **Indeks (opcjonalnie)**: miejsce dodania wpisu. Jeśli pole jest puste, wpis zostanie dodany na końcu. Kolejne wpisy zostaną przesunięte o jedno miejsce.
- **Pomiń, jeśli wpis już znajduje się na liście**: nie dodaje wpisu, jeśli na liście jest już taki sam tekst. Opcja **Ignoruj wielkość liter** sprawia, że `Apple` i `apple` są traktowane jako takie same.

### Ustaw wpis listy (zmienna FM)

**Identyfikator:** `set_list_entry`

Zastępuje wpis pod wskazanym **Indeksem** w [zmiennej listowej](/variables#list-actions) nową **Wartością**. Nie robi nic, jeśli lista nie zawiera wpisu pod tym indeksem.

### Usuń z listy (zmienna FM)

**Identyfikator:** `remove_from_list`

Usuwa wpisy ze [zmiennej listowej](/variables#list-actions). Opcja **Usuń** określa, które wpisy zostaną usunięte:

- **Wpis pod indeksem**: wpis o wskazanym indeksie.
- **Pierwsze dopasowanie**: pierwszy wpis dokładnie zgodny z **Wartością do usunięcia**.
- **Wszystkie dopasowania**: wszystkie zgodne wpisy.

Opcja **Ignoruj wielkość liter** sprawia, że `Apple` i `apple` są traktowane jako takie same.

### Wyczyść listę (zmienna FM)

**Identyfikator:** `clear_list`

Usuwa wszystkie wpisy ze [zmiennej listowej](/variables#list-actions). Pusta lista pozostaje.

### Ustaw listę (zmienna FM)

**Identyfikator:** `set_list`

Zastępuje wszystkie wpisy [zmiennej listowej](/variables#list-actions). Opcja **Wpisy z** określa ich źródło:

- **Podziel tekst**: dzieli **Tekst do podziału** w miejscach występowania **Separatora**, na przykład `,`. Pusty separator dzieli tekst w miejscach podziału wierszy. Opcja **Usuń spacje z wpisów** usuwa spacje z początku i końca wpisów, a **Pomiń puste wpisy** pomija puste wpisy.
- **Tablica JSON**: wpisy z tablicy, takiej jak `["Diamonds","Emeralds"]`, lub z `$$other_list`, aby skopiować inną listę. Inny tekst staje się jedynym wpisem, a pusty tekst opróżnia listę.

W oknie wyświetlany jest podgląd wpisów.

### Uporządkuj listę (zmienna FM)

**Identyfikator:** `arrange_list`

Zmienia kolejność wpisów w [zmiennej listowej](/variables#list-actions). Opcja **Kolejność**:

- **Sortuj A–Z** i **Sortuj Z–A**: sortuje alfabetycznie.
- **Liczby, od najmniejszej** i **Liczby, od największej**: sortuje według wartości liczbowej. Wpisy, które nie są liczbami, trafiają na koniec.
- **Odwróć kolejność**: ostatni wpis staje się pierwszym.
- **Pomieszaj**: ustawia losową kolejność.
- **Usuń duplikaty**: pozostawia tylko pierwszy wpis każdej wartości.

We wszystkich akcjach list pierwszy wpis ma indeks `0`, a `-1` oznacza ostatni wpis. Nazwa listy może zawierać placeholdery, a jeśli poprzedzisz ją `$$`, akcja użyje wartości tej zmiennej jako nazwy listy. Zmienne tekstowe, które mają już wartość, pozostają bez zmian, a akcja zapisuje ostrzeżenie w dzienniku gry.

## Sieć i połączenia

### Otwórz adres URL w przeglądarce

**Identyfikator:** `openlink`

Otwiera link w domyślnej przeglądarce bez wcześniejszego pytania.

**Wartość:** link, na przykład `https://discord.gg/example`

Korzystaj tylko z zaufanych linków.

### Wyślij żądanie HTTP

**Identyfikator:** `send_http_request`

Wysyła żądanie internetowe w tle. Odpowiedź można zapisać w dzienniku gry lub w zmiennej.

| Ustawienie | Działanie |
|---|---|
| URL | Adres HTTP lub HTTPS. |
| Metoda | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` lub `OPTIONS`. |
| Treść | Wysyłane dane. Nie jest wysyłana w przypadku `GET` i `HEAD`. |
| Typ zawartości | Nagłówek `Content-Type` treści, na przykład `application/json`. |
| Limit czasu | Liczba sekund oczekiwania na połączenie i odpowiedź. |
| Zapisz odpowiedź w dzienniku | Zapisuje odpowiedź w dzienniku gry. |
| Zmienna odpowiedzi | Zapisuje odpowiedź w tej zmiennej po jej otrzymaniu. |
| Odpowiedź w jednym wierszu | Usuwa podziały wierszy z odpowiedzi przed jej zapisaniem. |
| Uwierzytelnianie | Brak, Basic, Bearer lub klucz API. |
| Nagłówki | Dodatkowe nagłówki żądania. |

Następna akcja nie czeka na odpowiedź. Odpowiedzi o błędach również są zapisywane w dzienniku i zmiennej. Nie umieszczaj haseł ani tokenów dostępu w akcji — każdy, kto ma dostęp do układu, może je odczytać.

### Wyślij dane FM na serwer

**Identyfikator:** `send_fm_data_to_server`

Wysyła [dane FM](/fm-data) na serwer, który również musi mieć FancyMenu.

**Wartość:** `data_identifier||data`

### Połącz z serwerem zdalnym

**Identyfikator:** `connect_to_remote_server`

Łączy z serwerem zdalnym lub korzysta z już otwartego połączenia.

**Wartość:** adres serwera, na przykład `wss://example.com/ws`

Zobacz [Komunikacja z serwerem zdalnym](/remote-server-communication#url-modes), aby poznać obsługiwane adresy.

### Wyślij dane na serwer zdalny

**Identyfikator:** `send_data_to_remote_server`

Wysyła tekst na serwer zdalny, w razie potrzeby najpierw nawiązując połączenie.

**Wartość:** `server_address||data`

### Zamknij połączenie z serwerem zdalnym

**Identyfikator:** `close_remote_server_connection`

Zamyka jedno połączenie z serwerem zdalnym.

**Wartość:** identyfikator żądania, zwykle `$$request_id` z nasłuchiwacza [**Po połączeniu z serwerem zdalnym**](/listeners#on-remote-server-connected)

### Zamknij wszystkie połączenia z serwerami zdalnymi

**Identyfikator:** `close_all_remote_server_connections`

Zamyka wszystkie połączenia z serwerami zdalnymi otwarte przez FancyMenu.

**Wartość:** brak

## Pliki

### Utwórz plik w katalogu gry

**Identyfikator:** `create_file_in_game_dir`

Tworzy pusty plik. W razie potrzeby tworzy również brakujące foldery. Istniejący plik pozostaje bez zmian.

**Wartość:** ścieżka do pliku, na przykład `config/mymodpack/first_start.txt`

Wszystkie akcje plików działają wyłącznie w folderze gry (folderze instancji). Ścieżki rozpoczynające się od `.minecraft/` wskazują domyślny folder `.minecraft`, który może być innym folderem.

### Usuń plik/folder z katalogu gry

**Identyfikator:** `delete_file_in_game_dir`

Usuwa plik lub folder wraz z całą jego zawartością.

**Wartość:** ścieżka, na przykład `config/mymodpack/cache.txt`

Jeśli ścieżka kończy się znakiem `*`, na przykład `config/downloads/*`, usuwane są wszystkie pliki bezpośrednio w tym folderze, ale sam folder i znajdujące się w nim foldery pozostają.

### Kopiuj plik/folder w katalogu gry

**Identyfikator:** `copy_file_in_game_dir`

Kopiuje plik lub folder wraz z całą jego zawartością.

**Wartość:** `source||destination`, na przykład `config/presets/default.json||config/mymod/settings.json`

- Jeśli ścieżka źródłowa kończy się znakiem `*`, na przykład `config/presets/*||config/mymod/`, kopiowane są wszystkie pliki bezpośrednio w tym folderze, ale nie foldery. Ścieżka docelowa jest wtedy folderem i w razie potrzeby zostanie utworzona.
- Istniejące pliki nie są nadpisywane: jeśli plik docelowy już istnieje, akcja kończy się niepowodzeniem.

### Przenieś plik/folder w katalogu gry

**Identyfikator:** `move_file_in_game_dir`

Przenosi plik lub folder wraz z całą jego zawartością.

**Wartość:** `source||destination`

Znak `*` na końcu ścieżki źródłowej działa tak samo jak w przypadku akcji [**Kopiuj plik/folder w katalogu gry**](#copy-filefolder-in-game-directory). Istniejące pliki nie są nadpisywane.

### Zmień nazwę pliku/folderu w katalogu gry

**Identyfikator:** `rename_file_in_game_dir`

Zmienia nazwę pliku lub folderu. Akcja kończy się niepowodzeniem, jeśli istnieje już coś o nowej nazwie.

**Wartość:** `path||new_name`, na przykład `config/mymod/old_name.txt||new_name.txt`

### Pobierz plik do katalogu gry

**Identyfikator:** `download_file_to_game_dir`

Pobiera plik do folderu w tle.

**Wartość:** `url||target_folder`, na przykład `https://example.com/pack.zip||downloads`

- Druga część to folder, a nie nazwa pliku. FancyMenu pobiera nazwę z pliku lub linku.
- Plik o tej samej nazwie zostanie nadpisany.
- Nasłuchiwacz [**Po pobraniu pliku za pomocą akcji**](/listeners#on-file-downloaded-via-action) jest uruchamiany po zakończeniu lub niepowodzeniu pobierania. W razie powodzenia jego zmienna `$$target_file_path` zawiera ścieżkę zapisanego pliku.

### Rozpakuj plik ZIP w katalogu gry

**Identyfikator:** `extract_zip_file_in_game_dir`

Rozpakowuje plik ZIP do folderu w tle.

**Wartość:** `zip_path||target_folder`, na przykład `downloads/pack.zip||resourcepacks/MyPack`

Pliki o tych samych nazwach zostaną zastąpione. Nie jest tworzony dodatkowy folder o nazwie pliku ZIP. Po zakończeniu operacji uruchamiany jest nasłuchiwacz [**Po rozpakowaniu ZIP za pomocą akcji**](/listeners#on-zip-extracted-via-action). Rozpakowuj tylko zaufane pliki ZIP.

### Otwórz plik/folder w katalogu gry

**Identyfikator:** `open_file_folder_in_game_dir`

Otwiera plik lub folder za pomocą przypisanego do niego programu systemowego.

**Wartość:** ścieżka, na przykład `screenshots`

### Zapisz tekst w pliku w katalogu gry

**Identyfikator:** `write_file_in_game_dir`

Zapisuje tekst w pliku. W razie potrzeby plik i jego foldery zostaną utworzone.

**Wartość:** `path|||text|||append`, na przykład `config/mymodpack/log.txt|||Dołączono do serwera\n|||true`

`\n` rozpoczyna nowy wiersz. Jeśli `append` ma wartość `true`, tekst zostanie dodany na końcu pliku. Jeśli ma wartość `false`, zastąpi jego zawartość.

### Wybierz plik z systemu

**Identyfikator:** `select_file_to_game_dir`

Otwiera systemowe okno wyboru pliku i kopiuje wybrany plik do folderu gry.

**Wartość:** `target_path|||filter_name|||extensions|||overwrite`, na przykład `config/fancymenu/assets/background.png|||Images|||png;jpg|||true`

- `target_path` to pełna ścieżka kopii wraz z nazwą pliku.
- Rozszerzenia oddziel średnikiem `;` lub przecinkiem `,`. Jeśli nie podano rozszerzeń, można wybrać wszystkie pliki.
- Jeśli `overwrite` ma wartość `false`, akcja kończy się niepowodzeniem, gdy plik już istnieje.

Nasłuchiwacz [**Po wybraniu pliku**](/listeners#on-file-selected) jest uruchamiany po skopiowaniu pliku, anulowaniu wyboru lub wystąpieniu błędu.

## Gra i FancyMenu

### Zamknij Minecrafta

**Identyfikator:** `quitgame`

Zamyka grę.

**Wartość:** brak

### Ustaw opcję Minecrafta

**Identyfikator:** `edit_minecraft_option`

Zmienia opcję Minecrafta, na przykład odległość renderowania lub skalę interfejsu.

**Wartość:** `option_name:value`, na przykład `renderDistance:12`

Nazwy opcji znajdziesz w sekcji [Opcje Minecrafta](/minecraft-options).

### Naśladuj klawisz

**Identyfikator:** `mimic_keybind`

Naciska przypisany klawisz Minecrafta, na przykład skoku lub skradania, i może przytrzymać go wciśniętego.

**Wartość:** `keybind|||hold|||duration_ms`, na przykład `key.jump|||false|||1000`

| Część | Znaczenie |
|---|---|
| `keybind` | Identyfikator przypisanego klawisza, na przykład `key.jump` lub `key.sneak`. |
| `hold` | `true` przytrzymuje klawisz, `false` naciska go raz. |
| `duration_ms` | Czas przytrzymania klawisza w milisekundach. Wartość domyślna to `1000`. |

### Zarządzaj paczką zasobów

**Identyfikator:** `manage_resource_pack`

Włącza lub wyłącza paczkę zasobów. Skonfiguruj akcję w osobnym oknie:

- **Docelowa paczka zasobów**: nazwa paczki wyświetlana na ekranie Paczek zasobów. Wielkość liter nie ma znaczenia.
- **Tryb akcji**: **Włącz**, **Wyłącz** lub **Przełącz**.
- **Przeładuj zasoby**: od razu przeładowuje paczki zasobów po zmianie. Wyłącz tę opcję, aby przeładować je później, na przykład za pomocą akcji [**Przeładuj paczki zasobów**](#reload-resource-packs).

Nie można wyłączyć paczek wymaganych przez grę.

### Przeładuj paczki zasobów

**Identyfikator:** `reload_resource_packs`

Przeładowuje paczki zasobów, tak jak skrót `F3 + T`. Przez pięć sekund po przeładowaniu akcja nic nie robi, aby zapobiec wielokrotnemu uruchamianiu.

**Wartość:** brak

### Przeładuj FancyMenu

**Identyfikator:** `reloadmenu`

Przeładowuje układy, [niestandardowe interfejsy](/custom-guis), [panoramy](/panoramas), [pokazy slajdów](/slideshows), ustawienia i pliki FancyMenu. Paczki zasobów nie są przeładowywane.

**Wartość:** brak

> [!WARNING]
> Przeładowanie zajmuje chwilę. Używaj tej akcji na przycisku, nigdy w [liczniku](/elements#ticker) ani [nasłuchiwaczu](/listeners), które są często uruchamiane.

### Uruchom harmonogram

**Identyfikator:** `start_scheduler`

Uruchamia [harmonogram](/schedulers).

**Wartość:** identyfikator harmonogramu

### Zatrzymaj harmonogram

**Identyfikator:** `stop_scheduler`

Zatrzymuje [harmonogram](/schedulers).

**Wartość:** identyfikator harmonogramu

### Kopiuj tekst do schowka

**Identyfikator:** `copytoclipboard`

Kopiuje tekst do schowka.

**Wartość:** tekst, na przykład `play.example.net`

### Zapisz w dzienniku gry

**Identyfikator:** `print_to_log`

Zapisuje wiersz w dzienniku gry. Przydatne do sprawdzania, co robi skrypt.

**Wartość:** tekst
