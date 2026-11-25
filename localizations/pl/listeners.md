---
title: Nasłuchiwacze
description: >-
  Uruchamiaj skrypty akcji, gdy coś dzieje się w grze, na przykład po
  naciśnięciu klawisza, otrzymaniu wiadomości na czacie lub zdobyciu
  osiągnięcia.
sourceBlobSha: b8417f6287ac413d2d44e0fc5c2383c0b0fa6e1e
---

# Nasłuchiwacze

Nasłuchiwacze uruchamiają [skrypt akcji](/action-scripts), gdy coś dzieje się w grze: zostaje naciśnięty klawisz, otwiera się ekran, zdobywasz osiągnięcie i wiele więcej. Działają w każdym menu i podczas gry, a także nie są przypisane do układu.

Większość nasłuchiwaczy przekazuje też skryptowi zmienne opisujące zdarzenie, na przykład nazwę naciśniętego klawisza.

<img width="800" alt="Naciskanie klawiszy na ekranie tytułowym i powiadomienie pokazujące nazwę każdego naciśniętego klawisza" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_trigger.gif?raw=true">

> [!CAUTION]
> Nasłuchiwacz może uruchamiać akcje dotyczące plików, sieci, poleceń, schowka, paczek zasobów i linków, nawet gdy żadne menu nie jest otwarte. Korzystaj tylko z nasłuchiwaczy pochodzących z profili i plików osób, którym ufasz.

# Dodawanie nasłuchiwacza

<img width="800" alt="Otwieranie okna Zarządzaj nasłuchiwaczami, dodawanie nasłuchiwacza Po naciśnięciu klawisza z akcją Pokaż powiadomienie i naciskanie H, aby go przetestować" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_make.gif?raw=true">

1. Otwórz **pasek menu -> Personalizacja -> Zarządzaj nasłuchiwaczami**.
2. Kliknij **Dodaj nasłuchiwacz**.
3. Kliknij zdarzenie na liście **Dostępne nasłuchiwacze**. Pasek wyszukiwania pozwala znaleźć nasłuchiwacze według nazwy i opisu.
   - **Opis nasłuchiwacza** wyjaśnia jego działanie i informuje, jakie zmienne udostępnia.
   - **Kopiuj zmienne do schowka** kopiuje nazwy jego zmiennych.
   - **Otwórz opis w osobnym oknie** otwiera opis w osobnym oknie.
4. Kliknij **Gotowe** albo kliknij dwukrotnie nasłuchiwacz. Otworzy się edytor skryptów akcji.
5. Dodaj akcje, które mają zostać uruchomione, i kliknij **Gotowe**. Zobacz [Skrypty akcji](/action-scripts#making-an-action-script).
6. Kliknij **Gotowe** w oknie **Zarządzaj nasłuchiwaczami**, aby zapisać zmiany. Nasłuchiwacz zacznie działać od razu.

Kliknięcie **Anuluj** odrzuci wszystkie zmiany wprowadzone w oknie **Zarządzaj nasłuchiwaczami** po wyświetleniu pytania o potwierdzenie.

# Zarządzanie nasłuchiwaczami

<img width="800" alt="Okno Zarządzaj nasłuchiwaczami z pięcioma nasłuchiwaczami; jeden jest zaznaczony, a po prawej stronie widać jego skrypt akcji" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_manage.png?raw=true">

- Kliknij nasłuchiwacz, aby po prawej stronie zobaczyć jego typ i skrypt akcji.
- **Edytuj akcje** lub kliknięcie nasłuchiwacza prawym przyciskiem myszy otwiera jego skrypt akcji.
- Kliknij dwukrotnie nazwę nasłuchiwacza, aby ją zmienić, na przykład na `Klawisz pomocy`. Naciśnij `Enter`, aby zapisać nazwę, lub `Esc`, aby anulować. Jeśli nazwa będzie pusta, ponownie zostanie wyświetlony typ nasłuchiwacza.
- **Usuń nasłuchiwacz** usuwa zaznaczony nasłuchiwacz.
- **Eksportuj dla AI** kopiuje zaznaczony nasłuchiwacz lub wszystkie nasłuchiwacze do [czatu AI](/export-for-ai), uwzględniając niezapisane zmiany.

Nasłuchiwacze są zapisywane w pliku `config/fancymenu/listener_instances.txt` (zobacz [Lokalizacje przechowywania danych](/data-storage-locations)). Każdy [profil](/profiles) ma własne nasłuchiwacze.

# Zmienne nasłuchiwaczy

Zmienne nasłuchiwacza zaczynają się od `$$` i działają w całym przypisanym do niego skrypcie: we wszystkich wartościach akcji i warunkach [instrukcji IF](/action-scripts#if-else-if-and-else). Wielkość liter ma znaczenie. Poniżej przy każdym nasłuchiwaczu wymieniono jego zmienne; znajdziesz je również w opisie nasłuchiwacza w oknie wyboru.

<img width="800" alt="Okno wyboru nasłuchiwacza z zaznaczonym zdarzeniem Po zdobyciu osiągnięcia i opisem zawierającym listę jego zmiennych" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/listeners_choose.png?raw=true">

Na przykład poniższy nasłuchiwacz otwiera ekran pomocy po naciśnięciu klawisza `H`:

1. Dodaj nasłuchiwacz **Po naciśnięciu klawisza**.
2. W jego skrypcie użyj opcji **Dodaj instrukcję IF** z warunkiem [**Czy tekst**](/conditions#is-text). Ustaw **Tryb porównywania** na **Równa się**, **Tekst** na `$$key_name`, a **Porównaj z tekstem** na `H`.
3. Wewnątrz instrukcji IF dodaj akcję [**Otwórz ekran lub niestandardowe GUI**](/action-scripts#open-screen-or-custom-gui) i wybierz swój ekran pomocy.

Więcej informacji o zmiennych nasłuchiwaczy:

- Zmienne nasłuchiwaczy zawsze są tekstem. Jeśli nasłuchiwacz nie może uzyskać danej wartości, zmienna otrzymuje wartość zastępczą, na przykład `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` lub pustą wartość.
- Zmienne nasłuchiwaczy są wypełniane przed [symbolami zastępczymi](/placeholders), dlatego działają również wewnątrz symboli zastępczych.
- Zmienne nasłuchiwaczy istnieją tylko podczas wykonywania ich skryptu. Aby zachować wartość, zapisz ją w jednej ze swoich [zmiennych](/variables) za pomocą akcji [**Ustaw wartość zmiennej (zmienna FM)**](/action-scripts#set-variable-value-fm-variable).
- Własne zmienne utworzone w **pasek menu -> Personalizacja -> Zarządzaj zmiennymi** również działają w skryptach nasłuchiwaczy. Odwołuj się do nich, używając `$$` i ich nazwy, na przykład `$$coins`. Jeśli zmienna użytkownika ma taką samą nazwę jak zmienna nasłuchiwacza, `$$name` oznacza zmienną nasłuchiwacza. Zmienne użytkownika o dłuższych nazwach, takie jak `key_name_log`, nadal działają.
- Tekst pochodzący z czatu, serwerów, plików i od innych graczy może zawierać dowolną treść. Nigdy nie wstawiaj go bezpośrednio do poleceń, ścieżek plików ani linków.

# Warto wiedzieć

- Niektóre nasłuchiwacze wymagają FancyMenu na serwerze. Zostały tak oznaczone poniżej. W trybie jednoosobowym zawsze działają.
- Niektóre nasłuchiwacze uruchamiają się bardzo często, na przykład **Po poruszeniu myszą na ekranie**, **Po przewinięciu elementu**, **Po zmianie pozycji** i **Po odtworzeniu dźwięku w świecie**. Ich skrypty powinny być krótkie. Nie używaj w nich powolnych akcji, takich jak [**Przeładuj FancyMenu**](/action-scripts#reload-fancymenu).
- Aby zastąpić ekran za pomocą nasłuchiwacza **Po otwarciu ekranu**, najpierw sprawdź `$$screen_identifier` instrukcją IF. W przeciwnym razie zostanie zastąpiony każdy ekran, również ten, który otwierasz.

# Wszystkie nasłuchiwacze

Lista wszystkich nasłuchiwaczy FancyMenu, uporządkowana według rodzaju zdarzenia.

## Klawiatura i mysz

Aby sprawdzić, który klawisz został użyty, odwołaj się do `$$key_name`. Numery kodów klawiszy różnią się w zależności od wersji Minecrafta.

### Po naciśnięciu klawisza

**Identyfikator:** `keyboard_key_pressed`

Uruchamia się po naciśnięciu klawisza, zarówno w menu, jak i podczas gry. Jeśli klawisz jest przytrzymywany, nasłuchiwacz uruchamia się wielokrotnie.

- `$$key_name`: nazwa klawisza, na przykład `H` lub `Left Shift`
- `$$key_keycode`: numer kodu klawisza
- `$$key_scancode`: kod skanowania klawisza
- `$$key_modifiers`: liczba odpowiadająca klawiszom modyfikującym wciśniętym w tym samym czasie, na przykład `Shift` i `Ctrl`

### Po zwolnieniu klawisza

**Identyfikator:** `keyboard_key_released`

Uruchamia się po zwolnieniu klawisza, zarówno w menu, jak i podczas gry.

Udostępnia te same zmienne co **Po naciśnięciu klawisza**: `$$key_name`, `$$key_keycode`, `$$key_scancode` i `$$key_modifiers`.

### Po wpisaniu znaku na ekranie

**Identyfikator:** `keyboard_char_typed`

Uruchamia się dla każdego znaku wpisanego przy otwartym ekranie.

- `$$char`: wpisany znak

### Po poruszeniu myszą na ekranie

**Identyfikator:** `mouse_moved`

Uruchamia się za każdym razem, gdy mysz porusza się przy otwartym ekranie.

- `$$mouse_pos_x`, `$$mouse_pos_y`: pozycja myszy w pikselach GUI
- `$$mouse_move_delta_x`, `$$mouse_move_delta_y`: odległość, o jaką przesunęła się mysz od poprzedniego wywołania

### Po kliknięciu przycisku myszy

**Identyfikator:** `mouse_button_clicked`

Uruchamia się raz po naciśnięciu przycisku myszy, zarówno w menu, jak i podczas gry.

- `$$button`: `left`, `right` lub `middle`. Dla pozostałych przycisków podawany jest ich numer.
- `$$mouse_pos_x`, `$$mouse_pos_y`: pozycja myszy w pikselach GUI

### Po zwolnieniu przycisku myszy

**Identyfikator:** `mouse_button_released`

Uruchamia się raz po zwolnieniu przycisku myszy, zarówno w menu, jak i podczas gry.

Udostępnia te same zmienne co **Po kliknięciu przycisku myszy**: `$$button`, `$$mouse_pos_x` i `$$mouse_pos_y`.

### Po przewinięciu myszą na ekranie

**Identyfikator:** `mouse_scrolled`

Uruchamia się po obróceniu kółka myszy przy otwartym ekranie.

- `$$scroll_delta_y`: wartość przewinięcia kółka. Jest większa od `0` przy przewijaniu w górę i mniejsza od `0` przy przewijaniu w dół.

## Ekrany i elementy

### Po otwarciu ekranu

**Identyfikator:** `screen_open`

Uruchamia się zaraz po otwarciu ekranu. Akcja [**Otwórz ekran lub niestandardowe GUI**](/action-scripts#open-screen-or-custom-gui) w skrypcie może zastąpić go innym ekranem.

- `$$screen_identifier`: [identyfikator](/screen-identifiers) ekranu

### Po zamknięciu ekranu

**Identyfikator:** `screen_close`

Uruchamia się zaraz po zamknięciu ekranu.

- `$$screen_identifier`: [identyfikator](/screen-identifiers) zamkniętego ekranu

### Po kliknięciu tekstu Markdown

**Identyfikator:** `text_clicked`

Uruchamia się, gdy ktoś kliknie [zdarzenie kliknięcia](/text-formatting#click-and-hover-events) w tekście, na przykład `[Przeczytaj zasady](click:open_rules)`.

- `$$text_event_id`: identyfikator zdarzenia, na przykład `open_rules`

### Po najechaniu na tekst Markdown

**Identyfikator:** `text_hovered`

Uruchamia się, gdy mysz najedzie na [zdarzenie najechania](/text-formatting#click-and-hover-events) w tekście, na przykład `[Co to jest?](hover:show_hint)`.

- `$$text_event_id`: identyfikator zdarzenia, na przykład `show_hint`

### Po przewinięciu elementu

**Identyfikator:** `scroll_area_scrolled`

Uruchamia się za każdym razem, gdy przesuwa się zawartość [obszaru przewijania](/scrollable-areas) lub [elementu tekstowego](/text-in-menus). Podczas płynnego przewijania uruchamia się co klatkę. Nie działa w edytorze układu.

- `$$element_identifier`: [identyfikator](/element-identifiers) elementu
- `$$scroll_x`: odległość przewinięcia zawartości w poziomie, w pikselach
- `$$scroll_y`: odległość przewinięcia zawartości w dół, w pikselach
- `$$scroll_percent`: odległość przewinięcia zawartości w głównym kierunku elementu, od `0` (początek) do `100` (koniec)

### Po przewinięciu elementu do początku

**Identyfikator:** `scroll_area_reached_start`

Uruchamia się, gdy zawartość obszaru przewijania lub elementu tekstowego zostanie przewinięta z powrotem do początku.

Udostępnia te same zmienne co **Po przewinięciu elementu**: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` i `$$scroll_percent`.

### Po przewinięciu elementu do końca

**Identyfikator:** `scroll_area_reached_end`

Uruchamia się, gdy zawartość obszaru przewijania lub elementu tekstowego zostanie przewinięta do końca, na przykład po przeczytaniu wszystkich zasad.

Udostępnia te same zmienne co **Po przewinięciu elementu**: `$$element_identifier`, `$$scroll_x`, `$$scroll_y` i `$$scroll_percent`.

### Po rozpoczęciu odtwarzania animowanej tekstury

**Identyfikator:** `animated_texture_started_playing`

Uruchamia się, gdy zaczyna być odtwarzana [animowana tekstura](/animations) (GIF, APNG lub FMA), a także za każdym razem, gdy rozpoczyna się jej kolejna pętla.

- `$$texture_source`: źródło tekstury: ścieżka pliku, link internetowy lub lokalizacja zasobu
- `$$texture_source_type`: `LOCAL`, `WEB` lub `RESOURCE_LOCATION`
- `$$texture_will_restart`: `true`, jeśli po zakończeniu tej rundy odtwarzanie rozpocznie się od nowa; w przeciwnym razie `false`

### Po zakończeniu odtwarzania animowanej tekstury

**Identyfikator:** `animated_texture_finished_playing`

Uruchamia się po zakończeniu rundy animowanej tekstury. W przypadku zapętlenia dzieje się to tuż przed rozpoczęciem kolejnej rundy.

Udostępnia te same zmienne co **Po rozpoczęciu odtwarzania animowanej tekstury**: `$$texture_source`, `$$texture_source_type` i `$$texture_will_restart`.

### Po zmianie stanu odtwarzania wideo

**Identyfikator:** `video_playback_status_changed`

Uruchamia się, gdy element [wideo](/video) lub tło menu rozpoczyna odtwarzanie, zostaje wstrzymane, zatrzymane lub dobiega końca.

- `$$video_source`: źródło wideo: ścieżka pliku, link internetowy lub lokalizacja zasobu
- `$$video_source_type`: `LOCAL`, `WEB` lub `RESOURCE_LOCATION`
- `$$is_looping`: `true`, jeśli wideo jest zapętlone; w przeciwnym razie `false`
- `$$new_status`:
  - `PLAYING`: odtwarzanie wideo rozpoczęło się lub zostało wznowione
  - `PAUSED`: odtwarzanie wideo zostało wstrzymane
  - `STOPPED`: odtwarzanie wideo zostało zatrzymane
  - `FINISHED`: wideo dobiegło końca. W przypadku zapętlonych filmów ten stan występuje również tuż przed rozpoczęciem kolejnej pętli.

## Zmienne, pliki i dane

### Po aktualizacji zmiennej [zmienna FM]

**Identyfikator:** `fm_variable_updated`

Uruchamia się za każdym razem, gdy zostanie ustawiona [zmienna](/variables).

- `$$var_name`: nazwa zmiennej
- `$$old_value`: jej poprzednia wartość
- `$$new_value`: jej nowa wartość

W przypadku zmiennych listowych obie wartości zawierają całą listę w postaci tablicy JSON, na przykład `["Diamonds","Emeralds"]`.

### Po rozpoczęciu pobierania pliku przez akcję

**Identyfikator:** `file_download_started_via_action`

Uruchamia się po rozpoczęciu pobierania przez akcję [**Pobierz plik do katalogu gry**](/action-scripts#download-file-to-game-directory), gdy tylko znana jest nazwa pliku. Plik pojawi się pod wskazaną ścieżką dopiero po zakończeniu pobierania. Aby sprawdzić, kiedy będzie gotowy, użyj nasłuchiwacza **Po pobraniu pliku przez akcję**.

- `$$download_url`: link do pliku
- `$$target_file_path`: miejsce, w którym plik zostanie zapisany

### Po pobraniu pliku przez akcję

**Identyfikator:** `file_downloaded_via_action`

Uruchamia się po zakończeniu lub niepowodzeniu pobierania przez akcję [**Pobierz plik do katalogu gry**](/action-scripts#download-file-to-game-directory).

- `$$download_url`: link do pliku
- `$$target_file_path`: miejsce, w którym plik został zapisany. Jeśli pobieranie się nie powiedzie, ścieżka może wskazywać tylko folder.
- `$$download_succeeded`: `true` lub `false`

### Po wybraniu pliku

**Identyfikator:** `file_selected_via_action`

Uruchamia się po zakończeniu akcji [**Wybierz plik z systemu**](/action-scripts#select-file-from-system): po skopiowaniu pliku, anulowaniu okna wyboru pliku lub wystąpieniu błędu.

- `$$selected_file_path`: pełna ścieżka wybranego pliku. Pusta, jeśli anulowano wybór pliku.
- `$$target_file_path`: miejsce, do którego plik został skopiowany w folderze gry
- `$$selection_succeeded`: `true`, jeśli plik został skopiowany
- `$$selection_cancelled`: `true`, jeśli zamknięto okno wyboru bez wybierania pliku
- `$$failure_reason`: opis błędu. Pusta, jeśli nic się nie stało.

### Po rozpakowaniu pliku ZIP przez akcję

**Identyfikator:** `zip_extracted_via_action`

Uruchamia się po zakończeniu akcji [**Wypakuj plik ZIP w katalogu gry**](/action-scripts#extract-zip-file-in-game-directory).

- `$$source_zip_path`: plik ZIP
- `$$target_folder_path`: folder, do którego go wypakowano
- `$$extract_succeeded`: `true` lub `false`
- `$$failure_reason`: opis błędu. Pusta, jeśli nic się nie stało.

Ścieżki w folderze gry zaczynają się od `/`, na przykład `/config/fancymenu/assets/pack.zip`. Ścieżki w folderze `.minecraft` zaczynają się od `.minecraft/`.

### Po otrzymaniu danych FM

**Identyfikator:** `fm_data_received`

Uruchamia się, gdy serwer wysyła dane do tego gracza za pomocą polecenia `/fmdata send`. Zobacz [Dane FM](/fm-data).

- `$$data_identifier`: identyfikator, z którym wysłano dane
- `$$data`: dane
- `$$sent_by`: adres IP serwera lub `integrated_server` w trybie jednoosobowym

### Po połączeniu ze zdalnym serwerem

**Identyfikator:** `remote_server_connected`

Uruchamia się po nawiązaniu [połączenia ze zdalnym serwerem](/remote-server-communication).

- `$$request_id`: identyfikator żądania połączenia
- `$$remote_server_url`: link do zdalnego serwera

### Po otrzymaniu danych ze zdalnego serwera

**Identyfikator:** `remote_server_data_received`

Uruchamia się za każdym razem, gdy połączony zdalny serwer wysyła tekst.

- `$$request_id`: identyfikator żądania połączenia
- `$$remote_server_url`: link do zdalnego serwera
- `$$data`: wysłany tekst

### Po zamknięciu połączenia ze zdalnym serwerem

**Identyfikator:** `remote_server_connection_closed`

Uruchamia się po zamknięciu połączenia ze zdalnym serwerem.

- `$$request_id`: identyfikator żądania połączenia
- `$$remote_server_url`: link do zdalnego serwera
- `$$intentionally_closed`: `true`, jeśli połączenie zamknięto akcją [**Zamknij połączenie ze zdalnym serwerem**](/action-scripts#close-remote-server-connection)
- `$$crashed`: `true`, jeśli połączenie uległo awarii
- `$$unknown_close_reason`: `true`, jeśli połączenie zostało zamknięte z nieznanego powodu

## Gra, światy i serwery

### Przy zamykaniu Minecrafta

**Identyfikator:** `quit_minecraft`

Uruchamia się raz, gdy gra zaczyna się zamykać.

- `$$timestamp_millis`: czas wyrażony w milisekundach od 1970 roku
- `$$timestamp_iso`: czas w formacie tekstowym ISO-8601, na przykład `2026-11-24T18:30:00.123Z`

### Po wykonaniu zrzutu ekranu

**Identyfikator:** `screenshot_taken`

Uruchamia się po wykonaniu i zapisaniu zrzutu ekranu, na przykład za pomocą klawisza przypisanego do tej funkcji.

- `$$screenshot_path`: ścieżka zrzutu ekranu w folderze gry, na przykład `/screenshots/2026-10-29_14.30.00.png`

### Po wejściu do świata jednoosobowego

**Identyfikator:** `world_entered`

Uruchamia się po wczytaniu świata jednoosobowego, gdy można już się poruszać.

- `$$world_name`: nazwa świata
- `$$world_save_path`: pełna ścieżka folderu z zapisem świata
- `$$world_difficulty`: poziom trudności świata
- `$$world_cheats_allowed`: `true`, jeśli kody są włączone
- `$$world_icon_path`: pełna ścieżka ikony świata
- `$$world_is_first_join`: `true` podczas pierwszej wizyty po utworzeniu świata

### Po opuszczeniu świata jednoosobowego

**Identyfikator:** `world_left`

Uruchamia się po zamknięciu i zapisaniu świata jednoosobowego.

Udostępnia te same zmienne co **Po wejściu do świata jednoosobowego**, z wyjątkiem `$$world_is_first_join`: `$$world_name`, `$$world_save_path`, `$$world_difficulty`, `$$world_cheats_allowed` i `$$world_icon_path`.

### Po rozpoczęciu łączenia z serwerem

**Identyfikator:** `start_joining_server`

Uruchamia się, gdy gra rozpoczyna łączenie z serwerem lub Realmem, jeszcze przed dołączeniem. Uruchamia się również w przypadku niepowodzenia lub anulowania połączenia, dzięki czemu można zapamiętać serwer, na przykład na potrzeby przycisku ponownego połączenia na ekranie rozłączenia.

- `$$server_ip`: adres IP serwera

### Po dołączeniu do serwera

**Identyfikator:** `server_joined`

Uruchamia się po dołączeniu do serwera wieloosobowego.

- `$$server_ip`: adres IP serwera

### Po opuszczeniu serwera

**Identyfikator:** `server_left`

Uruchamia się po opuszczeniu serwera wieloosobowego.

- `$$server_ip`: adres IP serwera

### Po dołączeniu innego gracza do świata/serwera

**Identyfikator:** `other_player_joined_world`

Uruchamia się, gdy inny gracz dołączy do twojego świata lub serwera.

- `$$player_name`: nazwa gracza
- `$$player_uuid`: UUID gracza

### Po opuszczeniu świata/serwera przez innego gracza

**Identyfikator:** `other_player_left_world`

Uruchamia się, gdy inny gracz opuści twój świat lub serwer.

- `$$player_name`: nazwa gracza
- `$$player_uuid`: UUID gracza

### Po śmierci innego gracza

**Identyfikator:** `other_player_died`

Uruchamia się, gdy inny gracz w twoim świecie umrze.

- `$$player_name`: nazwa gracza
- `$$player_uuid`: UUID gracza
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: miejsce śmierci gracza

## Czat

### Po otrzymaniu wiadomości na czacie

**Identyfikator:** `chat_message_received`

Uruchamia się, gdy na czacie pojawi się wiadomość od gracza.

- `$$chat_message_string`: wiadomość w postaci zwykłego tekstu
- `$$chat_message_component`: wiadomość jako komponent tekstowy JSON
- `$$sender_uuid`: UUID nadawcy lub `ERROR`, jeśli nie jest znany
- `$$sender_name`: nazwa nadawcy lub `ERROR`, jeśli nie jest znana

### Po wysłaniu wiadomości na czacie

**Identyfikator:** `chat_message_sent`

Uruchamia się po wysłaniu wiadomości na czacie. Polecenia się nie liczą.

- `$$chat_message_string`: wiadomość w postaci zwykłego tekstu
- `$$chat_message_component`: wiadomość jako komponent tekstowy JSON

### Po otrzymaniu wiadomości systemowej na czacie

**Identyfikator:** `system_message_received_in_chat`

Uruchamia się, gdy na czacie pojawi się wiadomość, która nie pochodzi od gracza, na przykład wynik polecenia.

- `$$system_message_string`: wiadomość w postaci zwykłego tekstu
- `$$system_message_component`: wiadomość jako komponent tekstowy JSON

## Gracz

### Po śmierci

**Identyfikator:** `player_death`

Uruchamia się zaraz po otwarciu ekranu śmierci.

- `$$days_survived`: liczba dni w grze od ostatniej śmierci, zaokrąglona w dół
- `$$death_reason_string`: komunikat o śmierci w postaci zwykłego tekstu
- `$$death_reason_component`: komunikat o śmierci jako komponent tekstowy JSON
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: miejsce twojej śmierci

### Po otrzymaniu obrażeń

**Identyfikator:** `damage_taken`

Uruchamia się raz za każdym razem, gdy otrzymasz cios.

- `$$damage_amount`: ilość utraconego zdrowia
- `$$damage_type`: rodzaj obrażeń, na przykład `minecraft:fall`
- `$$is_fatal_damage`: `true`, jeśli cios cię zabił
- `$$damage_source`: typ istoty, która zadała obrażenia, na przykład `minecraft:zombie`, lub `NONE`

### Po uzyskaniu efektu

**Identyfikator:** `effect_gained`

Uruchamia się raz po uzyskaniu efektu statusu.

- `$$effect_key`: efekt, na przykład `minecraft:speed`
- `$$effect_type`: `positive`, `negative` lub `neutral`
- `$$effect_duration`: czas trwania w tickach (20 ticków to 1 sekunda)

### Po utracie efektu

**Identyfikator:** `effect_lost`

Uruchamia się raz po zakończeniu efektu statusu.

- `$$effect_key`: efekt, na przykład `minecraft:speed`
- `$$effect_type`: `positive`, `negative` lub `neutral`

### Po zmianie doświadczenia

**Identyfikator:** `experience_changed`

Uruchamia się za każdym razem, gdy liczba punktów doświadczenia wzrośnie lub spadnie.

- `$$new_experience_amount`: aktualna łączna liczba punktów doświadczenia
- `$$old_experience_amount`: poprzednia łączna liczba punktów doświadczenia
- `$$is_level_up`: `true`, jeśli zdobyto nowy poziom

### Po zdobyciu osiągnięcia

**Identyfikator:** `achievement_unlocked`

Uruchamia się raz po zdobyciu osiągnięcia (postępu). Osiągnięcia zdobyte wcześniej, na przykład podczas dołączania do świata, się nie liczą.

- `$$achievement_key`: osiągnięcie, na przykład `minecraft:story/mine_diamond`
- `$$achievement_label`: tytuł osiągnięcia w języku gry
- `$$achievement_description`: opis osiągnięcia w języku gry
- `$$achievement_icon_item_key`: przedmiot użyty jako ikona osiągnięcia, na przykład `minecraft:diamond`
- `$$achievement_type`: `advancement`, `goal` lub `challenge`

### Po skoku

**Identyfikator:** `jump`

Uruchamia się za każdym razem, gdy skaczesz. Nie udostępnia żadnych zmiennych.

### Po rozpoczęciu sprintu

**Identyfikator:** `started_running`

Uruchamia się raz po rozpoczęciu sprintu. Nie udostępnia żadnych zmiennych.

### Po zakończeniu sprintu

**Identyfikator:** `stopped_running`

Uruchamia się raz po zakończeniu sprintu. Nie udostępnia żadnych zmiennych.

### Po zmianie pozycji

**Identyfikator:** `position_changed`

Uruchamia się za każdym razem, gdy przejdziesz do innego bloku.

- `$$old_pos_x`, `$$old_pos_y`, `$$old_pos_z`: poprzednia pozycja bloku
- `$$new_pos_x`, `$$new_pos_y`, `$$new_pos_z`: nowa pozycja bloku

### Po rozpoczęciu płonięcia

**Identyfikator:** `started_burning`

Uruchamia się raz po rozpoczęciu płonięcia. Nie udostępnia żadnych zmiennych.

### Po zakończeniu płonięcia

**Identyfikator:** `stopped_burning`

Uruchamia się raz po zakończeniu płonięcia. Nie udostępnia żadnych zmiennych.

### Po rozpoczęciu tonięcia

**Identyfikator:** `started_drowning`

Uruchamia się raz po rozpoczęciu otrzymywania obrażeń od tonięcia. Nie udostępnia żadnych zmiennych.

### Po rozpoczęciu zamarzania

**Identyfikator:** `started_freezing`

Uruchamia się raz po rozpoczęciu zamarzania, na przykład w sypkim śniegu.

- `$$freezing_intensity`: stopień zamarznięcia od `0.0` (brak) do `1.0` (całkowite zamarznięcie)

### Po zakończeniu zamarzania

**Identyfikator:** `stopped_freezing`

Uruchamia się raz po zakończeniu zamarzania. Nie udostępnia żadnych zmiennych.

### Po całkowitym zamarznięciu

**Identyfikator:** `fully_frozen`

Uruchamia się raz po całkowitym zamarznięciu. Nie udostępnia żadnych zmiennych.

### Po rozpoczęciu pływania

**Identyfikator:** `start_swimming`

Uruchamia się raz po rozpoczęciu pływania.

- `$$fluid_type`: płyn, na przykład `minecraft:water`

### Po zakończeniu pływania

**Identyfikator:** `stop_swimming`

Uruchamia się raz po zakończeniu pływania.

- `$$fluid_type`: płyn, na przykład `minecraft:water`

### Po rozpoczęciu kontaktu z płynem

**Identyfikator:** `start_touching_fluid`

Uruchamia się raz po rozpoczęciu kontaktu z płynem, na przykład wodą lub lawą.

- `$$fluid_type`: płyn, na przykład `minecraft:lava`

### Po zakończeniu kontaktu z płynem

**Identyfikator:** `stop_touching_fluid`

Uruchamia się raz po zakończeniu kontaktu z płynem.

- `$$fluid_type`: płyn, na przykład `minecraft:lava`

## Przedmioty

### Po podniesieniu przedmiotu

**Identyfikator:** `item_picked_up`

Uruchamia się raz po podniesieniu przedmiotu.

- `$$item_key`: przedmiot, na przykład `minecraft:diamond`

### Po upuszczeniu przedmiotu

**Identyfikator:** `item_dropped`

Uruchamia się raz po upuszczeniu przedmiotu z ekwipunku.

- `$$item_key`: przedmiot, na przykład `minecraft:diamond`

### Po skonsumowaniu przedmiotu

**Identyfikator:** `item_consumed`

Uruchamia się raz po zjedzeniu lub wypiciu przedmiotu.

- `$$item_key`: przedmiot, na przykład `minecraft:golden_apple`

### Po użyciu przedmiotu

**Identyfikator:** `item_used`

Uruchamia się raz po użyciu przedmiotu.

- `$$item_key`: przedmiot, na przykład `minecraft:flint_and_steel`
- `$$used_on_type`: cel użycia: `block`, `entity`, `self` lub `none`
- `$$used_on_entity_key`: typ istoty, na której użyto przedmiotu. Puste, jeśli nie dotyczy.
- `$$used_on_block_key`: blok, na którym użyto przedmiotu. Puste, jeśli nie dotyczy.
- `$$target_pos_x`, `$$target_pos_y`, `$$target_pos_z`: pozycja, na której użyto przedmiotu, lub `-1`

### Po zniszczeniu przedmiotu

**Identyfikator:** `item_broke`

Uruchamia się raz po zniszczeniu przedmiotu znajdującego się w ekwipunku.

- `$$item_key`: przedmiot, na przykład `minecraft:iron_pickaxe`
- `$$item_type`: `tool`, `armor` lub `other`

### Po najechaniu na przedmiot w ekwipunku

**Identyfikator:** `item_hovered_in_inventory`

Uruchamia się raz po najechaniu myszą na przedmiot w dowolnym ekwipunku, na przykład własnym lub w skrzyni.

- `$$item_key`: przedmiot, na przykład `minecraft:diamond_sword`
- `$$item_display_name_string`: nazwa przedmiotu w postaci zwykłego tekstu
- `$$item_display_name_json`: nazwa przedmiotu jako komponent tekstowy JSON

## Bloki

### Po rozpoczęciu patrzenia na blok

**Identyfikator:** `start_looking_at_block`

Uruchamia się raz, gdy celownik zaczyna wskazywać blok oddalony o maksymalnie 20 bloków.

- `$$block_key`: blok, na przykład `minecraft:oak_log`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: pozycja bloku
- `$$distance_to_player`: odległość od twoich oczu do miejsca wskazywanego przez celownik

### Po zaprzestaniu patrzenia na blok

**Identyfikator:** `stop_looking_at_block`

Uruchamia się raz, gdy celownik przestaje wskazywać blok.

Udostępnia te same zmienne co **Po rozpoczęciu patrzenia na blok**, dotyczące poprzednio obserwowanego bloku: `$$block_key`, `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z` i `$$distance_to_player`.

### Po zniszczeniu bloku

**Identyfikator:** `block_broke`

Uruchamia się raz po zniszczeniu bloku.

- `$$block_key`: blok, na przykład `minecraft:stone`
- `$$broke_with_item_key`: przedmiot trzymany w ręce, na przykład `minecraft:iron_pickaxe`, lub `EMPTY`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: pozycja bloku

### Po postawieniu bloku

**Identyfikator:** `block_placed`

Uruchamia się raz po postawieniu bloku.

- `$$block_key`: blok, na przykład `minecraft:torch`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: pozycja bloku

### Po użyciu bloku

**Identyfikator:** `interacted_with_block`

Uruchamia się raz po użyciu bloku, na przykład po otwarciu skrzyni lub naciśnięciu przycisku.

- `$$block_key`: blok, na przykład `minecraft:chest`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: pozycja bloku

### Po wejściu na blok

**Identyfikator:** `stepping_on_block`

Uruchamia się raz po wejściu na blok.

- `$$block_key`: blok, na przykład `minecraft:grass_block`
- `$$block_pos_x`, `$$block_pos_y`, `$$block_pos_z`: pozycja bloku

## Istoty

### Po rozpoczęciu patrzenia na istotę

**Identyfikator:** `start_looking_at_entity`

Uruchamia się raz, gdy celownik zaczyna wskazywać istotę oddaloną o maksymalnie 20 bloków.

- `$$entity_key`: typ istoty, na przykład `minecraft:villager`
- `$$distance_to_player`: odległość od twoich oczu do miejsca wskazywanego przez celownik
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: pozycja istoty
- `$$entity_uuid`: UUID istoty

### Po zaprzestaniu patrzenia na istotę

**Identyfikator:** `stop_looking_at_entity`

Uruchamia się raz, gdy celownik przestaje wskazywać istotę.

Udostępnia te same zmienne co **Po rozpoczęciu patrzenia na istotę**, dotyczące poprzednio obserwowanej istoty: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` i `$$entity_uuid`.

### Po pojawieniu się istoty w polu widzenia

**Identyfikator:** `entity_starts_being_in_sight`

Uruchamia się raz, gdy istota pojawi się na twoim ekranie, w odległości do 200 bloków.

- `$$entity_key`: typ istoty, na przykład `minecraft:creeper`
- `$$distance_to_player`: odległość od twoich oczu do istoty
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: pozycja istoty
- `$$entity_uuid`: UUID istoty

### Po zniknięciu istoty z pola widzenia

**Identyfikator:** `entity_stops_being_in_sight`

Uruchamia się raz, gdy widoczna istota znika z ekranu lub oddala się na więcej niż 200 bloków.

Udostępnia te same zmienne co **Po pojawieniu się istoty w polu widzenia**: `$$entity_key`, `$$distance_to_player`, `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z` i `$$entity_uuid`.

### Po użyciu istoty

**Identyfikator:** `entity_interacted`

Uruchamia się raz po użyciu istoty, na przykład podczas handlu z osadnikiem.

- `$$entity_key`: typ istoty, na przykład `minecraft:villager`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: pozycja istoty
- `$$entity_uuid`: UUID istoty

### Po dosiadaniu istoty

**Identyfikator:** `entity_mounted`

Uruchamia się raz po rozpoczęciu jazdy na istocie, na przykład koniu lub łodzi.

- `$$entity_key`: typ istoty, na przykład `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: pozycja istoty
- `$$entity_uuid`: UUID istoty

### Po zejściu z istoty

**Identyfikator:** `entity_unmounted`

Uruchamia się raz po zejściu z istoty.

- `$$entity_key`: typ istoty, na przykład `minecraft:horse`
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: pozycja istoty
- `$$entity_uuid`: UUID istoty

### Po pojawieniu się istoty

**Identyfikator:** `entity_spawned`

Wymaga FancyMenu na serwerze. Uruchamia się, gdy istota pojawi się w dowolnym miejscu świata, nawet daleko lub w innym wymiarze.

- `$$entity_key`: typ istoty, na przykład `minecraft:zombie`
- `$$distance_to_player`: odległość od ciebie lub `-1` w innym wymiarze
- `$$entity_pos_x`, `$$entity_pos_y`, `$$entity_pos_z`: miejsce pojawienia się istoty
- `$$entity_uuid`: UUID istoty
- `$$dimension_key`: wymiar, na przykład `minecraft:overworld`
- `$$is_same_dimension_as_player`: `true`, jeśli istota pojawiła się w twoim wymiarze

### Po śmierci istoty

**Identyfikator:** `entity_died`

Wymaga FancyMenu na serwerze. Uruchamia się, gdy istota umrze w dowolnym miejscu świata, nawet daleko lub w innym wymiarze.

- `$$entity_key`: typ istoty, na przykład `minecraft:ender_dragon`
- `$$distance_to_player`: odległość od ciebie lub `-1` w innym wymiarze
- `$$death_pos_x`, `$$death_pos_y`, `$$death_pos_z`: miejsce śmierci istoty
- `$$entity_uuid`: UUID istoty
- `$$dimension_key`: wymiar, na przykład `minecraft:the_end`
- `$$damage_type`: rodzaj obrażeń, które ją zabiły, na przykład `minecraft:player_attack`
- `$$is_same_dimension_as_player`: `true`, jeśli istota zginęła w twoim wymiarze
- `$$entity_killed_by_name`: nazwa zabójcy lub `NONE`
- `$$entity_killed_by_key`: typ zabójcy, na przykład `minecraft:player`, lub `NONE`
- `$$entity_killed_by_uuid`: UUID zabójcy lub `NONE`

## Świat i miejsca

### Po wejściu do biomu

**Identyfikator:** `enter_biome`

Uruchamia się raz po wejściu do innego biomu.

- `$$biome_key`: biom, na przykład `minecraft:cherry_grove`

### Po opuszczeniu biomu

**Identyfikator:** `leave_biome`

Uruchamia się raz po opuszczeniu biomu.

- `$$biome_key`: opuszczony biom, na przykład `minecraft:cherry_grove`

### Po wejściu do struktury

**Identyfikator:** `enter_structure`

Wymaga FancyMenu na serwerze. Uruchamia się raz po wejściu na obszar struktury. Obszar jest wyznaczany w przybliżeniu, więc nasłuchiwacz może uruchomić się także w pobliżu struktury lub nad nią, na przykład nad znajdującą się pod tobą kopalnią. Aby wykrywać tylko wejście do środka, użyj nasłuchiwacza **Po wejściu do struktury (wysoka precyzja)**.

- `$$structure_key`: struktura, na przykład `minecraft:village_plains`

### Po opuszczeniu struktury

**Identyfikator:** `leave_structure`

Wymaga FancyMenu na serwerze. Uruchamia się raz po opuszczeniu obszaru struktury. Obszar jest wyznaczany w przybliżeniu, tak jak w przypadku **Po wejściu do struktury**.

- `$$structure_key`: opuszczona struktura

### Po wejściu do struktury (wysoka precyzja)

**Identyfikator:** `enter_structure_high_precision`

Wymaga FancyMenu na serwerze. Uruchamia się raz po wejściu do wnętrza struktury.

- `$$structure_key`: struktura, na przykład `minecraft:stronghold`

### Po opuszczeniu struktury (wysoka precyzja)

**Identyfikator:** `leave_structure_high_precision`

Wymaga FancyMenu na serwerze. Uruchamia się raz po całkowitym opuszczeniu struktury.

- `$$structure_key`: opuszczona struktura

### Po wejściu do wymiaru

**Identyfikator:** `enter_dimension`

Uruchamia się raz po wejściu do innego wymiaru.

- `$$dimension_key`: wymiar, na przykład `minecraft:the_nether`

### Po zmianie pogody

**Identyfikator:** `weather_changed`

Uruchamia się raz po zmianie pogody. Uruchamia się również wtedy, gdy zmienia się pogoda w miejscu, w którym jesteś: podczas deszczu liczy się także wejście na pustynię, do zaśnieżonego biomu lub do budynku.

- `$$weather_type`: `clear`, `rain` lub `thunder`
- `$$weather_can_snow`: `true`, jeśli w miejscu, w którym jesteś, mógłby padać śnieg
- `$$weather_can_rain`: `true`, jeśli w miejscu, w którym jesteś, mógłby padać deszcz

### Po rozpoczęciu najazdu

**Identyfikator:** `raid_started`

Wymaga FancyMenu na serwerze. Uruchamia się, gdy najazd rozpoczyna się w obszarze, w którym jesteś, i pojawia się pasek najazdu. Nie udostępnia żadnych zmiennych.

Wejście na obszar trwającego już najazdu się nie liczy. W takim przypadku użyj nasłuchiwacza **Po wejściu na obszar aktywnego najazdu**.

### Po wejściu na obszar aktywnego najazdu

**Identyfikator:** `enter_active_raid_area`

Wymaga FancyMenu na serwerze. Uruchamia się po wejściu na obszar trwającego już najazdu, gdy pojawia się pasek najazdu. Nie udostępnia żadnych zmiennych.

### Po opuszczeniu obszaru aktywnego najazdu

**Identyfikator:** `leave_active_raid_area`

Wymaga FancyMenu na serwerze. Uruchamia się po opuszczeniu obszaru najazdu, gdy znika pasek najazdu. Liczy się również śmierć lub zmiana wymiaru na tym obszarze, ale nie koniec najazdu. Nie udostępnia żadnych zmiennych.

### Po zakończeniu najazdu

**Identyfikator:** `raid_finished`

Wymaga FancyMenu na serwerze. Uruchamia się, gdy najazd kończy się w obszarze, w którym jesteś.

- `$$raid_result`: `victory` lub `defeat`

## Dźwięk i muzyka

### Po rozpoczęciu utworu muzycznego

**Identyfikator:** `music_track_started`

Uruchamia się raz po rozpoczęciu odtwarzania utworu muzycznego.

- `$$track_resource_location`: plik dźwiękowy utworu
- `$$track_display_name`: nazwa utworu lub `UNKNOWN`
- `$$track_artist`: wykonawca utworu lub `UNKNOWN`
- `$$track_duration_ms`: długość utworu w milisekundach lub `0`, jeśli nie jest znana

### Po zatrzymaniu utworu muzycznego

**Identyfikator:** `music_track_stopped`

Uruchamia się raz po zatrzymaniu utworu muzycznego, gdy się skończy lub zostanie zastąpiony innym.

Udostępnia te same zmienne co **Po rozpoczęciu utworu muzycznego**: `$$track_resource_location`, `$$track_display_name`, `$$track_artist` i `$$track_duration_ms`.

### Po odtworzeniu dźwięku w świecie

**Identyfikator:** `world_sound_triggered`

Uruchamia się za każdym razem, gdy w świecie, w pobliżu ciebie, zaczyna być odtwarzany dźwięk, na przykład dźwięk drzwi lub creepera.

- `$$sound_resource_location`: plik dźwiękowy
- `$$sound_display_name`: napisy dźwiękowe lub `UNKNOWN`
- `$$sound_origin_pos_x`, `$$sound_origin_pos_y`, `$$sound_origin_pos_z`: miejsce, z którego dochodzi dźwięk
- `$$sound_origin_distance_to_player`: odległość od źródła dźwięku
- `$$sound_origin_direction_from_player`: kierunek źródła dźwięku w stopniach (od 0 do 360) względem kierunku, w którym patrzysz
