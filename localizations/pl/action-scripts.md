---
title: Skrypty akcji
description: 'Jak używać skryptów akcji z przyciskami, suwakami, tickerami i nie tylko.'
---

# Skrypty akcji

FancyMenu pozwala dodawać interaktywność do menu poprzez przypisywanie do elementów **akcji**. Akcje uruchamiają się, gdy klikniesz przycisk, ticker jest odświeżany, użyjesz suwaka albo gdy ekran się otwiera lub zamyka. Możesz też budować zaawansowane skrypty akcji, używając prostych instrukcji sterujących, takich jak **if**, **else-if**, **else** i **while**, aby kontrolować, które akcje są uruchamiane i kiedy.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Edytor skryptów akcji" style="max-width:800px;width:100%;height:auto;">

# Czym są akcje?

**Akcja** to zadanie lub czynność, którą FancyMenu wykonuje po wyzwoleniu. Na przykład akcja może otworzyć nowy ekran, wysłać wiadomość na czacie albo zmienić głośność elementu audio. W edytorze FancyMenu akcje są konfigurowane za pomocą wartości (jeśli jest potrzebna), która podaje dodatkowe szczegóły — na przykład adres URL lub adres serwera.

# Czym są instrukcje?

Aby tworzyć bardziej złożone zachowania, FancyMenu obsługuje podstawowe instrukcje sterujące w skryptach akcji. Należą do nich:

- **Instrukcja If:** Uruchamia blok akcji tylko wtedy, gdy spełniony jest określony [warunek](/en/conditions).
- **Instrukcja Else-If:** Sprawdza inny [warunek](/en/conditions), jeśli poprzedni *if* (lub wcześniejszy *else-if*) nie został spełniony.
- **Instrukcja Else:** Uruchamia się, jeśli żaden z poprzednich [warunków](/en/conditions) nie został spełniony.
- **Instrukcja While:** Powtarza blok akcji bez przerwy tak długo, jak [warunek](/en/conditions) pozostaje prawdziwy (z wbudowanym limitem czasu, aby zapobiec nieskończonym pętlom).
- **Blok opóźnienia:** Czeka przez określony czas, zanim uruchomi zawarte w nim akcje. Reszta skryptu nadal działa, podczas gdy odliczanie opóźnienia trwa.
- **Blok wykonania później:** Dodaje zawarte akcje do kolejki, aby zostały uruchomione na głównym wątku po opóźnieniu wyrażonym w milisekundach.
- **Komentarz:** Dodaje notatkę wewnątrz skryptu dla lepszej organizacji. Komentarze nie uruchamiają żadnych akcji.

Łącząc te instrukcje z akcjami, możesz tworzyć dynamiczne i warunkowe zachowania, na przykład sprawdzać, czy zdrowie gracza jest niskie, zanim wyślesz ostrzeżenie, albo powtarzać aktualizację, dopóki warunek się nie zmieni.

# Gdzie można używać skryptów akcji?

Skrypty akcji są bardzo uniwersalne i można ich używać w całym układzie. Możesz przypisać je na przykład do:

- **Przycisków:** Wykonują akcję po kliknięciu.
- **Tickerów:** Nieustannie uruchamiają skrypt akcji, aby aktualizować informacje wyświetlane na ekranie w układzie.
- **Suwaków:** Uruchamiają skrypt akcji za każdym razem, gdy zmienia się wartość suwaka.
- **Zdarzeń ekranu:** Uruchamiają skrypty, gdy ekran się otwiera lub zamyka (na przykład odtwarzając dźwięk, gdy pojawia się menu).
- **Słuchaczy:** Gdy słuchacz, który nasłuchuje określonego zdarzenia, zostanie wyzwolony, wykona swój skrypt akcji.
- **Harmonogramów:** Wykonują akcje według ustalonego czasu, nawet gdy żaden ekran nie jest otwarty.

# Używanie placeholderów w akcjach

Wartości akcji obsługują dynamiczną zawartość dzięki **placeholderom**. Najczęściej te placeholdery używają składni podobnej do JSON i są zastępowane aktualnymi danymi w momencie uruchomienia akcji.

## Placeholdery podobne do JSON

To są zwykłe [placeholdere](/en/placeholders), których można używać w wielu miejscach w układach.

Mają następującą składnię:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Mogą pobierać dane z gry, takie jak nazwa gracza, wymiary ekranu lub obliczone wartości z użyciem placeholdera **Calculator**. Możesz też zagnieżdżać placeholdery, aby korzystać z nich w bardziej zaawansowany sposób.

## Placeholdery `$$` (zmienne)

Placeholdery `$$` są specjalne. Niektóre funkcje FancyMenu udostępniają te specjalne placeholdery dla swoich zagnieżdżonych akcji, wymagań i zwykłych placeholderów, dzięki czemu można ich używać wewnątrz, aby uzyskać więcej informacji o środowisku (elemencie, słuchaczu itp.), w którym się znajdują.

Na przykład, jeśli akcje są używane wewnątrz suwaka, użycie `$$value` w akcji zostanie zastąpione bieżącą wartością suwaka.

Podczas używania akcji w słuchaczach każdy słuchacz udostępnia własny unikalny zestaw zmiennych/placeholderów do pobierania większej ilości informacji o słuchaczu, takich jak wciśnięty przycisk myszy, wpisana struktura itp.

# Jak skonfigurować i edytować akcje

Aby dodać, edytować lub usunąć akcje (oraz bloki instrukcji) dla elementu, po prostu **kliknij element prawym przyciskiem myszy** (czy to przycisk, suwak, ticker czy inny interaktywny element), a następnie wybierz **Zarządzaj skryptem akcji**. Otworzy to ekran Zarządzanie akcjami, gdzie możesz:

- **Dodawać nowe akcje lub instrukcje:** Wstawiać nowe wpisy akcji lub instrukcje sterujące (if, else-if, else, while), aby budować swój skrypt.
- **Edytować istniejące akcje lub instrukcje:** Modyfikować wartość akcji lub zmieniać logikę sterującą.
- **Usuwać akcje lub instrukcje:** Kasować niepotrzebne akcje ze skryptu.

Dla [słuchaczy](/listeners) istnieje specjalne menu do zarządzania i tworzenia słuchaczy, w tym dostępu do ich skryptów akcji, aby zapewnić takie samo doświadczenie jak np. podczas edycji skryptu akcji przycisku lub suwaka.

> W ekranie Edytora skryptów akcji po prostu kliknij prawym przyciskiem myszy duży ciemnoszary obszar, aby otworzyć menu kontekstowe do dodawania akcji, instrukcji i nie tylko.
{.is-info}


# Skróty i inne funkcje edytora skryptów akcji

Edytor skryptów akcji ma kilka świetnych funkcji poprawiających wygodę, które sprawiają, że edycja skryptów jest bardzo prosta.

## Skróty

- `DEL` : Szybko usuwa zaznaczony wpis
- `ENTER` : Uruchamia edycję w linii zaznaczonego wpisu (lub otwiera ekran edycji, jeśli dla zaznaczonego wpisu nie ma edycji w linii)
- `CTRL + C` : Kopiuje zaznaczoną akcję (na razie działa tylko z akcjami)
- `CTRL + V` : Wkleja wcześniej skopiowaną akcję
- `CTRL + Z` : Cofnij o jeden krok
- `CTRL + Y` : Ponów o jeden krok
- `ARROW UP` : Przechodzi o jeden wpis wyżej od aktualnie zaznaczonego
- `ARROW DOWN` : Przechodzi o jeden wpis niżej od aktualnie zaznaczonego
- `SHIFT + ARROW UP` : Przesuwa zaznaczony wpis o jeden w górę
- `SHIFT + ARROW DOWN` : Przesuwa zaznaczony wpis o jeden w dół
- `A` : Szybko otwiera ekran Wybór akcji, aby dodać nową akcję
- `CTRL + S` : Zakończenie/zapis z okna edytora

## Więcej funkcji poprawiających wygodę

- Dwukrotne kliknięcie wartości akcji pozwala edytować ją bez przechodzenia do pełnego ekranu edycji wartości.
- Łańcuchy instrukcji IF (z dołączonymi instrukcjami ELSE/ELSE-IF), pętle WHILE i foldery można zwijać (tylko wizualnie, nie wpływa to na logikę skryptu).
- Edytor zawsze dodaje nowe akcje poniżej zaznaczonego wpisu (lub zagnieżdżone w zaznaczonym łańcuchu/pętli/folderze).
- Kliknięcie prawym przyciskiem myszy na ciemnoszare tło obszaru skryptu otwiera menu kontekstowe z opcjami dodawania akcji, instrukcji i wszystkiego innego, co ważne.

# Akcje szczegółowo

Ta lista zawiera większość, jeśli nie wszystkie, akcji dostępnych w FancyMenu. Możliwe, że lista bywa czasem nieco nieaktualna ze względu na aktualizacje moda.

## Następny utwór (`audio_next_track`)
- **Opis:** Przechodzi do następnego utworu w elemencie audio
- **Wymagana wartość:** Tak - `audio_element_identifier` (ID elementu audio do sterowania)

## Poprzedni utwór (`audio_previous_track`)
- **Opis:** Przechodzi do poprzedniego utworu w elemencie audio
- **Wymagana wartość:** Tak - `audio_element_identifier` (ID elementu audio do sterowania)

## Ustaw głośność utworu (`set_audio_element_volume`)
- **Opis:** Ustawia głośność elementu audio (0.0 do 1.0)
- **Wymagana wartość:** Tak - `element_identifier:volume`

## Przełącz odtwarzanie/pauzę utworu (`audio_toggle_play`)
- **Opis:** Przełącza stan odtwarzania/pauzy bieżącego utworu w elemencie audio
- **Wymagana wartość:** Tak - `audio_element_identifier`

## Odtwórz audio (`play_audio`)
- **Opis:** Odtwarza zasób audio jeden raz. Akcja śledzi rozpoczęte audio, aby można je było później zatrzymać przez `stop_all_action_audios`.
- **Wymagana wartość:** Tak - konfiguracja JSON z `audioSource`, `soundChannel` i `baseVolume`
- **Przykładowa wartość:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

## Zatrzymaj wszystkie audio akcji (`stop_all_action_audios`)
- **Opis:** Zatrzymuje wszystkie ścieżki audio uruchomione przez akcję **Odtwórz audio**. Nie zatrzymuje to elementów Audio, dźwięków otwierania/zamykania menu, dźwięków przycisków ani innych systemów audio.
- **Wymagana wartość:** Nie

## Ustaw głośność elementu wideo (`set_video_element_volume`)
- **Opis:** Ustawia głośność elementu wideo (0.0 do 1.0)
- **Wymagana wartość:** Tak - `video_element_identifier:volume`

## Ustaw czas odtwarzania elementu wideo (`set_video_element_play_time`)
- **Opis:** Przewija element wideo do znacznika czasu w milisekundach
- **Wymagana wartość:** Tak - `video_element_identifier:timestamp_ms`

## Przełącz stan pauzy elementu wideo (`toggle_video_element_pause_state`)
- **Opis:** Przełącza stan pauzy elementu wideo
- **Wymagana wartość:** Tak - `video_element_identifier`

## Ustaw głośność tła wideo (`set_video_menu_background_volume`)
- **Opis:** Ustawia głośność tła wideo menu (0.0 do 1.0)
- **Wymagana wartość:** Tak - `background_identifier:volume`

> Aby uzyskać identyfikator tła, kliknij prawym przyciskiem myszy tło edytora i wybierz „Copy Background Identifier”.
{.is-info}

## Ustaw czas odtwarzania tła wideo (`set_video_menu_background_play_time`)
- **Opis:** Przewija tło wideo menu do znacznika czasu w milisekundach
- **Wymagana wartość:** Tak - `background_identifier:timestamp_ms`

> Aby uzyskać identyfikator tła, kliknij prawym przyciskiem myszy tło edytora i wybierz „Copy Background Identifier”.
{.is-info}

## Przełącz stan pauzy tła wideo (`toggle_video_menu_background_pause_state`)
- **Opis:** Przełącza stan pauzy tła wideo menu
- **Wymagana wartość:** Tak - `background_identifier`

> Aby uzyskać identyfikator tła, kliknij prawym przyciskiem myszy tło edytora i wybierz „Copy Background Identifier”.
{.is-info}

## Przełącz układ (`toggle_layout`)
- **Opis:** Przełącza układ (włącz/wyłącz) według jego nazwy
- **Wymagana wartość:** Tak - `layout_name`

## Włącz układ (`enable_layout`)
- **Opis:** Włącza układ według jego nazwy
- **Wymagana wartość:** Tak - `layout_name`

## Wyłącz układ (`disable_layout`)
- **Opis:** Wyłącza układ według jego nazwy
- **Wymagana wartość:** Tak - `layout_name`

## Otwórz ekran lub niestandardowe GUI (`opengui`)
- **Opis:** Otwiera ekran według jego identyfikatora (vanilla, mod lub niestandardowe GUI)
- **Wymagana wartość:** Tak - `screen_identifier`

> Ta akcja **nie zadziała dla każdego ekranu**, zwłaszcza ekranów z modów. Jeśli akcja nie zdoła otworzyć ekranu, wyświetli błąd. Niewiele da się wtedy zrobić, ponieważ prawdopodobnie jest to ekran zbyt złożony, by FancyMenu mógł otworzyć go automatycznie.
> 
> Obsługa ekranów z modów nie będzie już również dodawana ręcznie po stronie FancyMenu, ponieważ dodanie kompatybilności dla wszystkich modów zajęłoby wieki, przepraszamy. W większości przypadków nie zaleca się też kontaktowania z twórcą innego moda, ponieważ jeśli FancyMenu nie może otworzyć ekranu, nie ma łatwego sposobu na dodanie dla niego wsparcia. Zalecanym obejściem jest spróbowanie akcji **„Mimic Vanilla/Mod Button”**, aby zasymulować przycisk otwierający konkretny ekran. Jeśli nie ma przycisku, to niestety nic nie da się zrobić.
{.is-info}

## Zamknij ekran (`closegui`)
- **Opis:** Zamyka aktywny ekran
- **Wymagana wartość:** Nie

## Odśwież ekran (`update_screen`)
- **Opis:** Ponownie inicjalizuje bieżący ekran
- **Wymagana wartość:** Nie

## Wróć do ostatniego ekranu (`back_to_last_screen`)
- **Opis:** Wraca do poprzedniego ekranu (tego sprzed bieżącego)
- **Wymagana wartość:** Nie

## Dołącz do serwera (`joinserver`)
- **Opis:** Łączy gracza z serwerem Minecraft
- **Wymagana wartość:** Tak - `server_ip:port`

## Wejdź do świata (`loadworld`)
- **Opis:** Wchodzi do świata Minecraft
- **Wymagana wartość:** Tak - `world_folder_name`

## Wejdź/Dołącz do ostatniego świata/serwera (`join_last_world`)
- **Opis:** Wchodzi/dołącza do ostatniego świata lub serwera, na którym był gracz
- **Wymagana wartość:** Nie

## Opuść świat lub serwer (`disconnect_server_or_world`)
- **Opis:** Opuszcza świat lub serwer i otwiera określony ekran
- **Wymagana wartość:** Tak - `screen_identifier`

## Zamknij Minecraft (`quitgame`)
- **Opis:** Całkowicie zamyka Minecrafta
- **Wymagana wartość:** Nie

## Wyślij wiadomość/komendę na czacie (`sendmessage`)
- **Opis:** Wysyła wiadomość na czacie lub wykonuje komendę czatu
- **Wymagana wartość:** Tak - `message_text` lub `/command_text`

## Wykonaj komendę jako zintegrowany serwer (`execute_command_as_integrated_server`)
- **Opis:** Wymusza wykonanie komendy w trybie jednoosobowym jako zintegrowany serwer, ignorując uprawnienia i ustawienie cheatów.
- **Wymagana wartość:** Tak - tekst komendy, na przykład `/give @p minecraft:diamond 1`

> Ta akcja działa tylko w trybie jednoosobowym, gdy świat nie jest udostępniony w LAN. Celowo nic nie robi na serwerach wieloosobowych.
{.is-warning}

## Wklej na czat (`paste_to_chat`)
- **Opis:** Wkleja tekst do pola wprowadzania czatu (dopisz lub zastąp)
- **Wymagana wartość:** Tak - `true:Text` lub `false:Text`

## Wyświetl na czacie [po stronie klienta] (`display_in_chat_client_side`)
- **Opis:** Wyświetla tekst bezpośrednio w lokalnym czacie (bez serwera)
- **Wymagana wartość:** Tak - `text_or_json`

## Wyślij dane FM do serwera (`send_fm_data_to_server`)
- **Opis:** Wysyła niestandardowe dane tekstowe do bieżącego serwera FancyMenu przez kanał pakietów FM Data.
- **Wymagana wartość:** Tak - `data_identifier||data`

## Połącz z zdalnym serwerem (`connect_to_remote_server`)
- **Opis:** Otwiera lub ponownie wykorzystuje połączenie WebSocket zainicjowane przez klienta z zewnętrznym serwerem zdalnym.
- **Wymagana wartość:** Tak - adres URL zdalnego serwera, na przykład `wss://example.com/ws`

## Wyślij dane do zdalnego serwera (`send_data_to_remote_server`)
- **Opis:** Otwiera lub ponownie wykorzystuje połączenie zdalnego serwera i wysyła do niego dane tekstowe.
- **Wymagana wartość:** Tak - `remote_server_url||data`

## Zamknij połączenie ze zdalnym serwerem (`close_remote_server_connection`)
- **Opis:** Zamknij określone połączenie ze zdalnym serwerem według identyfikatora żądania.
- **Wymagana wartość:** Tak - Request ID, zwykle z zmiennej słuchacza Remote Server, takiej jak `$$request_id`

## Zamknij wszystkie połączenia ze zdalnymi serwerami (`close_all_remote_server_connections`)
- **Opis:** Zamyka wszystkie aktywne połączenia ze zdalnymi serwerami otwarte przez FancyMenu.
- **Wymagana wartość:** Nie

## Otwórz URL w przeglądarce (`openlink`)
- **Opis:** Otwiera link w domyślnej przeglądarce
- **Wymagana wartość:** Tak - `https://example.com`

## Skopiuj tekst do schowka (`copytoclipboard`)
- **Opis:** Kopiuje tekst do schowka
- **Wymagana wartość:** Tak - `text_to_copy`

## Zapisz do logu gry (`print_to_log`)
- **Opis:** Zapisuje linię do logu gry
- **Wymagana wartość:** Tak - `text_to_log`

## Ustaw wartość zmiennej (zmienna FM) (`set_variable`)
- **Opis:** Zapisuje treść tekstową w zmiennej FancyMenu
- **Wymagana wartość:** Tak - `variable_name:variable_value`

## Wyczyść wszystkie zmienne (zmienna FM) (`clear_variables`)
- **Opis:** Czyści WSZYSTKIE zapisane zmienne FancyMenu
- **Wymagana wartość:** Nie

## Wyślij żądanie HTTP (`send_http_request`)
- **Opis:** Wysyła żądanie HTTP; może zapisać odpowiedź w zmiennej
- **Wymagana wartość:** Tak - konfiguracja żądania HTTP

> Ta akcja pozwala wysyłać dane do REST API, webhooków lub dowolnego punktu końcowego HTTP.
> Obsługuje różne metody uwierzytelniania, niestandardowe nagłówki i różne typy żądań.
> 
> Ta akcja pozwala też zapisać odpowiedź żądania w zmiennej FancyMenu do późniejszego użycia!
{.is-info}

## Zarządzaj pakietem zasobów (`manage_resource_pack`)
- **Opis:** Włącza/wyłącza/przełącza pakiet zasobów według nazwy wyświetlanej (opcjonalne przeładowanie)
- **Wymagana wartość:** Tak - `pack_name|||MODE|||reload_bool`

## Przeładuj pakiety zasobów (`reload_resource_packs`)
- **Opis:** Przeładowuje pakiety zasobów (5 s cooldownu)
- **Wymagana wartość:** Nie

## Przeładuj FancyMenu (`reloadmenu`)
- **Opis:** Przeładowuje FancyMenu, w tym panoramy, pokazy slajdów i wszystkie zasoby (duże obciążenie)
- **Wymagana wartość:** Nie

> Ta akcja ma **duży wpływ na wydajność** i może powodować lagi, jeśli jest używana w tickerach. Nie zaleca się używania tej akcji w niczym innym niż przycisk.
{.is-warning}

## Przełącz animator elementu (`toggle_element_animator`)
- **Opis:** Przełącza stan odtwarzania animatora elementu
- **Wymagana wartość:** Tak - `animator_identifier`

## Włącz animator elementu (`enable_element_animator`)
- **Opis:** Włącza animator elementu
- **Wymagana wartość:** Tak - `animator_identifier`

## Wyłącz animator elementu (`disable_element_animator`)
- **Opis:** Wyłącza animator elementu
- **Wymagana wartość:** Tak - `animator_identifier`

## Zresetuj animator elementu (`reset_element_animator`)
- **Opis:** Resetuje oś czasu / stan animatora elementu
- **Wymagana wartość:** Tak - `animator_identifier`

## Zasymuluj przycisk Vanilla/Mod (`mimicbutton`)
- **Opis:** Naśladuje kliknięcie przycisku vanilla lub z moda
- **Wymagana wartość:** Tak - `screen_identifier:widget_locator`

## Zasymuluj skrót klawiszowy (`mimic_keybind`)
- **Opis:** Uruchamia skrót klawiszowy Minecrafta (opcjonalne przytrzymanie)
- **Wymagana wartość:** Tak - `keybind_id|||keep_pressed_bool|||duration_ms`

## Ustaw wartość pola tekstowego (`set_text_input_field_value`)
- **Opis:** Ustawia wartość niestandardowego lub vanilla pola wejściowego według identyfikatora elementu.
- **Wymagana wartość:** Tak - `element_identifier|||new_value|||force_set_when_inactive`

## Utwórz plik w katalogu gry (`create_file_in_game_dir`)
- **Opis:** Tworzy pusty plik w katalogu gry (root instancji). Obsługuje prefiks `.minecraft/` do wskazania domyślnego katalogu profilu launchera (może różnić się od bieżącego katalogu instancji).
- **Wymagana wartość:** Tak - `file_path`

## Usuń plik/folder w katalogu gry (`delete_file_in_game_dir`)
- **Opis:** Usuwa plik lub folder w katalogu gry (root instancji). Obsługuje prefiks `.minecraft/`, aby wskazać domyślny profil launchera (może różnić się od uruchomionej instancji). Dodaj `*`, aby usunąć **wszystkie pliki bezpośrednio wewnątrz** folderu (ignoruje podkatalogi; pozostawia folder).
- **Wymagana wartość:** Tak - `target_path`

## Skopiuj plik/folder w katalogu gry (`copy_file_in_game_dir`)
- **Opis:** Kopiuje w obrębie katalogu gry (root instancji); prefiks `.minecraft/` wskazuje domyślny profil launchera (nie zawsze bieżącą instancję). Dodaj `*` do ścieżki **źródłowej**, aby skopiować każdy plik znajdujący się bezpośrednio w tym folderze (ignoruje podkatalogi); cel musi być katalogiem i nie może używać `*`.
- **Wymagana wartość:** Tak - `source||destination`

## Przenieś plik/folder w katalogu gry (`move_file_in_game_dir`)
- **Opis:** Przenosi w obrębie katalogu gry (root instancji); prefiks `.minecraft/` wskazuje domyślny profil launchera (może różnić się od bieżącej instancji). Dodaj `*` do ścieżki **źródłowej**, aby przenieść każdy plik znajdujący się bezpośrednio w tym folderze (ignoruje podkatalogi); cel musi być katalogiem i nie może używać `*`.
- **Wymagana wartość:** Tak - `source||destination`

## Zmień nazwę pliku/folderu w katalogu gry (`rename_file_in_game_dir`)
- **Opis:** Zmienia nazwę pliku lub folderu wewnątrz katalogu gry (root instancji); prefiks `.minecraft/` wskazuje domyślny profil launchera (może różnić się od bieżącej instancji). Zachowuje zawartość, zmienia się tylko nazwa.
- **Wymagana wartość:** Tak - `path||new_name`

## Pobierz plik do katalogu gry (`download_file_to_game_dir`)
- **Opis:** Pobiera plik asynchronicznie do katalogu gry (root instancji); prefiks `.minecraft/` wskazuje domyślny profil launchera (niekoniecznie bieżącą instancję). Podaj **folder docelowy**; nazwa pliku jest automatycznie wyprowadzana z nagłówków/URL.
- **Wymagana wartość:** Tak - `url||target_folder`

## Rozpakuj plik ZIP w katalogu gry (`extract_zip_file_in_game_dir`)
- **Opis:** Rozpakowuje plik ZIP do folderu docelowego w katalogu gry lub domyślnym katalogu `.minecraft`. Po zakończeniu wyzwala słuchacz **On ZIP Extracted via Action**.
- **Wymagana wartość:** Tak - `source_zip_path||target_folder_path`

## Otwórz plik/folder w katalogu gry (`open_file_folder_in_game_dir`)
- **Opis:** Otwiera plik lub folder przy użyciu domyślnej aplikacji systemu operacyjnego. Ze względów bezpieczeństwa cel musi znajdować się w katalogu gry lub w domyślnym katalogu `.minecraft`.
- **Wymagana wartość:** Tak - `target_path`

## Zapisz do pliku w katalogu gry (`write_file_in_game_dir`)
- **Opis:** Zapisuje lub dopisuje tekst wewnątrz katalogu gry (root instancji); prefiks `.minecraft/` wskazuje domyślny profil launchera (może różnić się od tej instancji). Tworzy plik, jeśli nie istnieje. Obsługuje `\n` w wartości, aby wstawiać łamanie linii; tryb dopisywania kontroluje końcowa wartość logiczna.
- **Wymagana wartość:** Tak - `path|||content|||append_bool`

## Wybierz plik z systemu (`select_file_to_game_dir`)
- **Opis:** Otwiera natywny selektor plików (dowolna lokalizacja) i kopiuje wybrany plik do katalogu gry (root instancji) lub do domyślnego `.minecraft/`, jeśli użyto prefiksu (ten domyślny katalog może różnić się od tej instancji). Obsługuje filtry rozszerzeń, niestandardową etykietę filtra i opcjonalne przełączanie nadpisywania.
- **Wymagana wartość:** Tak - konfiguracja wyboru

## Pokaż toast (`show_toast`)
- **Opis:** Wyświetla konfigurowalne powiadomienie toast
- **Wymagana wartość:** Tak - konfiguracja toastu

## Uruchom harmonogram (`start_scheduler`)
- **Opis:** Uruchamia harmonogram według jego ID.
- **Wymagana wartość:** Tak - `scheduler_id`

## Zatrzymaj harmonogram (`stop_scheduler`)
- **Opis:** Zatrzymuje harmonogram według jego ID.
- **Wymagana wartość:** Tak - `scheduler_id`

## Ustaw opcję Minecrafta (`edit_minecraft_option`)
- **Opis:** Edytuje opcję konfiguracji Minecrafta
- **Wymagana wartość:** Tak - `option_name:set_to_value`
