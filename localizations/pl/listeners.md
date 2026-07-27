---
title: Nasłuchiwacze
description: Jak tworzyć i używać nasłuchiwaczy w FancyMenu.
---

# Nasłuchiwacze

Nasłuchiwacze uruchamiają [skrypty akcji](./action-scripts) w określonych momentach, gdy wystąpią konkretne zdarzenia. Nie są powiązane z otwartym ekranem, więc mogą działać także podczas gry lub ładowania.

Nasłuchiwacze mogą przekazywać do swoich akcji i wymagań wartości `$$`, takie jak wciśnięty klawisz lub kliknięty przycisk myszy.

> [!CAUTION]
> Nasłuchiwacz może uruchamiać akcje związane z plikami, siecią, komendami, schowkiem, paczką zasobów lub linkami bez otwartego ekranu. Importuj nasłuchiwacze tylko z zaufanych źródeł.

# Używanie nasłuchiwaczy

Poza Edytorem Układu otwórz **menu bar -> Customization -> Manage Listeners**, aby utworzyć lub edytować nasłuchiwacze.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Zarządzanie nasłuchiwaczami" style="max-width:800px;width:100%;height:auto;">

# Zmienne nasłuchiwaczy

Nasłuchiwacze mogą przekazywać do swoich akcji i wymagań wartości tylko do odczytu. Używaj ich nazw `$$` w obsługiwanych polach tekstowych.

Na przykład użyj [**On Keyboard Key Pressed**](#on-keyboard-key-pressed-keyboard_key_pressed) wraz z akcją [**Print to Game Log**](./action-scripts#print-to-game-log-print_to_log). Wartość `Key pressed! The key is: $$key_name` wstawia nazwę wciśniętego klawisza.

> [!WARNING]
> Zmienne nasłuchiwaczy są oddzielone od [zapisanych zmiennych](./variables) FancyMenu. Akcje, wymagania i placeholdery dotyczące zapisanych zmiennych nie działają z wartościami `$$`.

Nazwy zmiennych nasłuchiwaczy rozróżniają wielkość liter i działają tylko wewnątrz skryptu danego nasłuchiwacza.

Traktuj wartości pochodzące z czatu, zdalnych serwerów, plików i danych wprowadzonych przez użytkownika jako niezaufane. Nie wstawiaj ich bezpośrednio do ścieżek, adresów URL ani poleceń.

Zmienne nasłuchiwaczy są ciągami tekstowymi. Gdy informacja jest niedostępna, nasłuchiwacz może zwrócić udokumentowaną wartość zastępczą, taką jak `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` lub pusty ciąg. Testuj te wartości przed wstawieniem danych z nasłuchiwacza do ścieżek, poleceń lub adresów URL.

# Nasłuchiwacze szczegółowo

Ta sekcja zawiera wbudowane nasłuchiwacze FancyMenu.

## Po kliknięciu tekstu Markdown (`text_clicked`)
- Uruchamia się, gdy kliknięty zostanie [tekst Markdown z wydarzeniem `click:`](./text-formatting#click-and-hover-events), na przykład `[Otwórz](click:open_menu)`.
- Zmienne:
  - `$$text_event_id` – identyfikator wydarzenia z linku Markdown

## Po najechaniu na tekst Markdown (`text_hovered`)
- Uruchamia się, gdy kursor znajdzie się nad [tekstem Markdown z wydarzeniem `hover:`](./text-formatting#click-and-hover-events), na przykład `[Wskazówka](hover:show_hint)`.
- Zmienne:
  - `$$text_event_id` – identyfikator wydarzenia z linku Markdown

## Po rozpakowaniu ZIP przez akcję (`zip_extracted_via_action`)
- Uruchamia się po zakończeniu akcji [**Extract ZIP File In Game Directory**](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir).
- Zmienne:
  - `$$source_zip_path` – znormalizowana ścieżka źródłowa widoczna dla użytkownika; ścieżki katalogu gry mogą być zwracane jako `/...`, a standardowe ścieżki katalogu Minecrafta mogą używać `.minecraft/...`
  - `$$target_folder_path` – znormalizowana ścieżka docelowa widoczna dla użytkownika, używająca tych samych form ścieżek
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – tekst błędu, gdy rozpakowywanie się nie powiodło

## Po utworzeniu elementu (`element_spawned_via_action`)
- Uruchamia się, gdy obsługiwana funkcja FancyMenu lub dodatek dynamicznie tworzy instancję elementu.
- Zmienne:
  - `$$element_type` – typ utworzonego elementu
  - `$$element_identifier` – identyfikator utworzonego elementu
  - `$$target_screen` – identyfikator docelowego ekranu

## Po rozpoczęciu odtwarzania animowanej tekstury (`animated_texture_started_playing`)
- Uruchamia się, gdy [animowana tekstura](./fma) zaczyna się odtwarzać.
- Zmienne:
  - `$$texture_source` – źródło tekstury
  - `$$texture_source_type` – typ źródła
  - `$$texture_will_restart` – true/false

## Po zakończeniu odtwarzania animowanej tekstury (`animated_texture_finished_playing`)
- Uruchamia się, gdy animowana tekstura kończy odtwarzanie.
- Zmienne:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## Po zmianie statusu odtwarzania wideo (`video_playback_status_changed`)
- Uruchamia się, gdy [element wideo lub tło menu](./video) zmienia status odtwarzania.
- Zmienne:
  - `$$video_source` – źródło wideo
  - `$$video_source_type` – typ źródła
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` lub `FINISHED`

## Po otrzymaniu komunikatu systemowego na czacie (`system_message_received_in_chat`)
- Uruchamia się, gdy klient otrzyma systemową wiadomość czatu, na przykład odpowiedź na komendę.
- Zmienne:
  - `$$system_message_string` – wiadomość jako zwykły tekst
  - `$$system_message_component` – komponent JSON

## Po odebraniu FM Data (`fm_data_received`)
- Uruchamia się, gdy serwer wyśle do tego klienta [FM Data](./fm-data) przez `/fmdata send`.
- Zmienne:
  - `$$data_identifier` – ciąg identyfikujący dane
  - `$$data` – ładunek danych
  - `$$sent_by` – adres IP serwera lub `integrated_server`

## Po połączeniu ze zdalnym serwerem (`remote_server_connected`)
- Uruchamia się po pomyślnym nawiązaniu [połączenia ze zdalnym serwerem](./remote-server-communication).
- Zmienne:
  - `$$request_id` – zapisany identyfikator żądania
  - `$$remote_server_url` – adres URL zdalnego serwera

## Po odebraniu danych ze zdalnego serwera (`remote_server_data_received`)
- Uruchamia się, gdy tekstowe dane zostaną odebrane z podłączonego zdalnego serwera.
- Zmienne:
  - `$$request_id` – identyfikator żądania
  - `$$remote_server_url` – adres URL zdalnego serwera
  - `$$data` – odebrany ładunek

## Po zamknięciu połączenia ze zdalnym serwerem (`remote_server_connection_closed`)
- Uruchamia się, gdy połączenie ze zdalnym serwerem zostanie zamknięte.
- Zmienne:
  - `$$request_id` – identyfikator żądania
  - `$$remote_server_url` – adres URL zdalnego serwera
  - `$$intentionally_closed` – TRUE, jeśli zamknięto przez akcję
  - `$$crashed` – TRUE, jeśli połączenie niespodziewanie uległo awarii
  - `$$unknown_close_reason` – TRUE, jeśli nie było znanego powodu zamknięcia

## Po wciśnięciu klawisza (`keyboard_key_pressed`)
- Uruchamia się za każdym razem, gdy klawisz zostanie wciśnięty (powtarza się przy przytrzymaniu; działa w ekranach i w grze).
- Zmienne:
  - `$$key_name` – wyświetlana nazwa klawisza
  - `$$key_keycode` – kod klawisza GLFW
  - `$$key_scancode` – kod skanowania GLFW
  - `$$key_modifiers` – aktywna maska bitowa modyfikatorów

## Po zwolnieniu klawisza (`keyboard_key_released`)
- Uruchamia się, gdy klawisz zostanie zwolniony (ekrany i gra).
- Zmienne:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## Po wpisaniu znaku klawiaturą na ekranie (`keyboard_char_typed`)
- Uruchamia się, gdy wpisany zostanie znak, a ekran jest otwarty.
- Zmienne:
  - `$$char` – wpisany znak

## Po ruchu myszy na ekranie (`mouse_moved`)
- Uruchamia się za każdym razem, gdy mysz porusza się, gdy ekran jest otwarty.
- Zmienne:
  - `$$mouse_pos_x` – bieżące X
  - `$$mouse_pos_y` – bieżące Y
  - `$$mouse_move_delta_x` – przesunięcie X od ostatniego zdarzenia
  - `$$mouse_move_delta_y` – przesunięcie Y od ostatniego zdarzenia

## Po kliknięciu przycisku myszy (`mouse_button_clicked`)
- Uruchamia się, gdy przycisk myszy zostanie wciśnięty (ekrany i gra).
- Zmienne:
  - `$$button` – lewy/prawy/środkowy
  - `$$mouse_pos_x` – bieżące X
  - `$$mouse_pos_y` – bieżące Y

## Po zwolnieniu przycisku myszy (`mouse_button_released`)
- Uruchamia się, gdy przycisk myszy zostanie zwolniony (ekrany i gra).
- Zmienne:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## Po przewinięciu myszy na ekranie (`mouse_scrolled`)
- Uruchamia się, gdy kółko myszy zostanie przewinięte, gdy ekran jest otwarty.
- Zmienne:
  - `$$scroll_delta_y` – pionowa wartość przewinięcia

## Po otwarciu ekranu (`screen_open`)
- Uruchamia się zaraz po aktywacji dowolnego ekranu; może służyć do jego nadpisania.
- Zmienne:
  - `$$screen_identifier` – identyfikator otwartego ekranu

## Po zamknięciu ekranu (`screen_close`)
- Uruchamia się natychmiast po zamknięciu ekranu.
- Zmienne:
  - `$$screen_identifier` – identyfikator zamkniętego ekranu

## Po wyjściu z Minecrafta (`quit_minecraft`)
- Uruchamia się raz, gdy klient zaczyna się zamykać.
- Zmienne:
  - `$$timestamp_millis` – czas epoki w milisekundach w momencie wyjścia
  - `$$timestamp_iso` – znacznik czasu ISO-8601 momentu wyjścia

## Po śmierci (`player_death`)
- Uruchamia się, gdy dla lokalnego gracza otwiera się standardowy ekran śmierci.
- Zmienne:
  - `$$days_survived` – liczba dni od ostatniej śmierci
  - `$$death_reason_string` – przyczyna jako zwykły tekst
  - `$$death_reason_component` – przyczyna jako komponent JSON
  - `$$death_pos_x` – współrzędna X śmierci
  - `$$death_pos_y` – współrzędna Y śmierci
  - `$$death_pos_z` – współrzędna Z śmierci

## Po aktualizacji zmiennej [FM Variable] (`fm_variable_updated`)
- Uruchamia się za każdym razem, gdy [zmienna FancyMenu](./variables) zostanie ustawiona lub zaktualizowana.
- Zmienne:
  - `$$var_name` – nazwa zmiennej
  - `$$old_value` – poprzednia wartość
  - `$$new_value` – nowa wartość

## Po pobraniu pliku przez akcję (`file_downloaded_via_action`)
- Uruchamia się po zakończeniu akcji [**Download File to Game Directory**](./action-scripts#download-file-to-game-directory-download_file_to_game_dir).
- Zmienne:
  - `$$download_url` – źródło pobierania
  - `$$target_file_path` – zapisana ścieżka pliku po powodzeniu; w przypadku niepowodzenia może zawierać tylko katalog docelowy, ponieważ nie udało się ustalić końcowej nazwy pliku
  - `$$download_succeeded` – true/false

## Po wybraniu pliku (`file_selected_via_action`)
- Uruchamia się po zakończeniu akcji [**Select File from System**](./action-scripts#select-file-from-system-select_file_to_game_dir).
- Zmienne:
  - `$$selected_file_path` – pełna ścieżka wybranego pliku lub pusta, jeśli anulowano
  - `$$target_file_path` – rozwiązana ścieżka wewnątrz instancji
  - `$$selection_succeeded` – true, jeśli kopiowanie się powiodło
  - `$$selection_cancelled` – true, jeśli okno zostało zamknięte
  - `$$failure_reason` – informacje o błędzie w przypadku niepowodzenia

## Po odebraniu wiadomości czatu (`chat_message_received`)
- Uruchamia się, gdy na kliencie pojawi się zwykła linia czatu gracza.
- Zmienne:
  - `$$chat_message_string` – linia jako zwykły tekst
  - `$$chat_message_component` – pełny komponent JSON
  - `$$sender_uuid` – UUID nadawcy lub ERROR
  - `$$sender_name` – nazwa nadawcy lub ERROR

## Po wysłaniu wiadomości czatu (`chat_message_sent`)
- Uruchamia się, gdy lokalny gracz wyśle wiadomość na czacie.
- Zmienne:
  - `$$chat_message_string` – linia jako zwykły tekst
  - `$$chat_message_component` – pełny komponent JSON

## Po zdobyciu efektu (`effect_gained`)
- Uruchamia się, gdy gracz zyska efekt statusu.
- Zmienne:
  - `$$effect_key` – lokalizacja zasobu efektu
  - `$$effect_type` – pozytywny/negatywny/neutralny
  - `$$effect_duration` – pozostałe ticki

## Po utracie efektu (`effect_lost`)
- Uruchamia się, gdy gracz straci efekt statusu.
- Zmienne:
  - `$$effect_key` – wygasły efekt
  - `$$effect_type` – kategoria

## Po zmianie doświadczenia (`experience_changed`)
- Uruchamia się za każdym razem, gdy zmienia się łączna liczba punktów XP gracza.
- Zmienne:
  - `$$new_experience_amount` – po zmianie
  - `$$old_experience_amount` – przed zmianą
  - `$$is_level_up` – TRUE, jeśli poziom wzrósł

## Po otrzymaniu obrażeń (`damage_taken`)
- Uruchamia się raz na trafienie, gdy gracz otrzymuje obrażenia.
- Zmienne:
  - `$$damage_amount` – utracone zdrowie
  - `$$damage_type` – lokalizacja zasobu typu obrażeń
  - `$$is_fatal_damage` – TRUE, jeśli śmiertelne
  - `$$damage_source` – lokalizacja zasobu atakującego lub NONE

## Po rozpoczęciu zamarzania (`started_freezing`)
- Uruchamia się, gdy gracz zaczyna zamarzać.
- Zmienne:
  - `$$freezing_intensity` – 0.0 brak, 1.0 całkowicie zamarznięty

## Po zakończeniu zamarzania (`stopped_freezing`)
- Uruchamia się, gdy gracz przestaje zamarzać.
- Zmienne:
  - (brak)

## Po całkowitym zamarznięciu (`fully_frozen`)
- Uruchamia się raz, gdy gracz stanie się całkowicie zamarznięty.
- Zmienne:
  - (brak)

## Po rozpoczęciu patrzenia na blok (`start_looking_at_block`)
- Uruchamia się raz, gdy celownik po raz pierwszy wskazuje blok (maksymalnie 20 bloków odległości).
- Zmienne:
  - `$$block_key` – celowany blok
  - `$$block_pos_x` – X bloku
  - `$$block_pos_y` – Y bloku
  - `$$block_pos_z` – Z bloku
  - `$$distance_to_player` – od oczu do punktu trafienia

## Po zakończeniu patrzenia na blok (`stop_looking_at_block`)
- Uruchamia się, gdy celownik przestaje wskazywać blok (raportuje ostatni celowany blok, maksymalnie 20 bloków).
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## Po rozpoczęciu patrzenia na encję (`start_looking_at_entity`)
- Uruchamia się raz, gdy celownik po raz pierwszy wskazuje encję (maksymalnie 20 bloków).
- Zmienne:
  - `$$entity_key` – typ celowanej encji
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Po zakończeniu patrzenia na encję (`stop_looking_at_entity`)
- Uruchamia się, gdy celownik przestaje wskazywać encję (raportuje ostatnią celowaną encję, maksymalnie 20 bloków).
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Po pojawieniu się encji (`entity_spawned`)
- **Wymaga FancyMenu na serwerze.** Uruchamia się, gdy jakakolwiek encja pojawi się gdziekolwiek w połączonym świecie/na serwerze.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player` – −1, jeśli w inym wymiarze
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## Po śmierci encji (`entity_died`)
- **Wymaga FancyMenu na serwerze.** Uruchamia się, gdy jakakolwiek encja umrze w połączonym świecie/na serwerze.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player` – −1, jeśli w inym wymiarze
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## Po rozpoczęciu widoczności encji (`entity_starts_being_in_sight`)
- Uruchamia się, gdy encja po raz pierwszy staje się widoczna w promieniu 200 bloków.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Po zakończeniu widoczności encji (`entity_stops_being_in_sight`)
- Uruchamia się, gdy wcześniej widoczna encja znika z pola widzenia lub oddala się poza 200 bloków.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Po interakcji z encją (`entity_interacted`)
- Uruchamia się, gdy gracz pomyślnie wejdzie w interakcję z encją.
- Zmienne:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Po wejściu na encję (`entity_mounted`)
- Uruchamia się, gdy gracz zaczyna jechać na encji.
- Zmienne:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Po zejściu z encji (`entity_unmounted`)
- Uruchamia się, gdy gracz przestaje jechać na aktualnej encji.
- Zmienne:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Po zniszczeniu bloku (`block_broke`)
- Uruchamia się, gdy gracz zniszczy blok.
- Zmienne:
  - `$$block_key`
  - `$$broke_with_item_key` – użyte narzędzie lub EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Po postawieniu bloku (`block_placed`)
- Uruchamia się, gdy gracz postawi blok.
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Po interakcji z blokiem (`interacted_with_block`)
- Uruchamia się, gdy gracz pomyślnie wejdzie w interakcję z blokiem.
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Po wejściu na blok (`stepping_on_block`)
- Uruchamia się, gdy gracz stanie na bloku.
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Po wejściu do biomu (`enter_biome`)
- Uruchamia się, gdy gracz wchodzi do nowego biomu.
- Zmienne:
  - `$$biome_key` – biom, do którego weszto

## Po opuszczeniu biomu (`leave_biome`)
- Uruchamia się, gdy gracz opuszcza obecny biom.
- Zmienne:
  - `$$biome_key` – biom, który właśnie opuściono

## Po wejściu do struktury (`enter_structure`)
- **Wymaga FancyMenu na serwerze.** Grube wykrywanie obszaru struktury; może uruchamiać się w pobliżu, nad lub pod strukturą.
- Zmienne:
  - `$$structure_key` – struktura, do której weszto

## Po opuszczeniu struktury (`leave_structure`)
- **Wymaga FancyMenu na serwerze.** Grube wykrywanie; może uruchamiać się w pobliżu zasięgu struktury.
- Zmienne:
  - `$$structure_key` – struktura, którą właśnie opuszczono

## Po wejściu do struktury (wysoka precyzja) (`enter_structure_high_precision`)
- **Wymaga FancyMenu na serwerze.** Uruchamia się, gdy gracz wejdzie do brył ograniczających struktury.
- Zmienne:
  - `$$structure_key`

## Po opuszczeniu struktury (wysoka precyzja) (`leave_structure_high_precision`)
- **Wymaga FancyMenu na serwerze.** Uruchamia się po wyjściu gracza z brył ograniczających struktury.
- Zmienne:
  - `$$structure_key`

## Po wejściu do wymiaru (`enter_dimension`)
- Uruchamia się, gdy gracz wchodzi do nowego wymiaru.
- Zmienne:
  - `$$dimension_key` – wymiar, do którego weszto

## Po rozpoczęciu pływania (`start_swimming`)
- Uruchamia się, gdy gracz zaczyna pływać.
- Zmienne:
  - `$$fluid_type` – lokalizacja zasobu płynu

## Po zatrzymaniu pływania (`stop_swimming`)
- Uruchamia się, gdy gracz przestaje pływać.
- Zmienne:
  - `$$fluid_type` – płyn, w którym pływanie się zatrzymało

## Po rozpoczęciu dotykania płynu (`start_touching_fluid`)
- Uruchamia się, gdy gracz zaczyna dotykać płynu.
- Zmienne:
  - `$$fluid_type` – dotykany płyn

## Po zakończeniu dotykania płynu (`stop_touching_fluid`)
- Uruchamia się, gdy gracz przestaje dotykać płynu.
- Zmienne:
  - `$$fluid_type` – płyn, którego gracz już nie dotyka

## Po rozpoczęciu utworu muzycznego (`music_track_started`)
- Uruchamia się, gdy zaczyna się nowy utwór muzyczny.
- Zmienne:
  - `$$track_resource_location` – plik audio
  - `$$track_display_name` – czytelna nazwa lub UNKNOWN
  - `$$track_artist` – wykonawca lub UNKNOWN
  - `$$track_duration_ms` – milisekundy (0, jeśli nieznane)

## Po zatrzymaniu utworu muzycznego (`music_track_stopped`)
- Uruchamia się, gdy bieżący utwór muzyczny kończy się lub zostaje zastąpiony.
- Zmienne:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## Po wyzwoleniu dźwięku świata (`world_sound_triggered`)
- Uruchamia się, gdy dźwięk świata o określonej pozycji zaczyna się w pobliżu gracza.
- Zmienne:
  - `$$sound_resource_location` – plik dźwiękowy
  - `$$sound_display_name` – nazwa napisu, jeśli dostępna
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – stopnie 0–360 względem kierunku patrzenia

## Po zmianie pogody (`weather_changed`)
- Uruchamia się, gdy pogoda zmienia się globalnie lub lokalnie (zmiana biomu albo wejście do pomieszczenia może ponownie ją wywołać).
- Zmienne:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE, jeśli renderuje się śnieg
  - `$$weather_can_rain` – TRUE, jeśli renderuje się deszcz

## Po rozpoczęciu palenia (`started_burning`)
- Uruchamia się, gdy gracz zaczyna się palić.
- Zmienne:
  - (brak)

## Po zatrzymaniu palenia (`stopped_burning`)
- Uruchamia się, gdy gracz przestaje się palić.
- Zmienne:
  - (brak)

## Po rozpoczęciu topienia się (`started_drowning`)
- Uruchamia się, gdy gracz zaczyna otrzymywać obrażenia od utonięcia.
- Zmienne:
  - (brak)

## Po zmianie pozycji (`position_changed`)
- Uruchamia się za każdym razem, gdy zmienia się blokowa pozycja gracza.
- Zmienne:
  - `$$old_pos_x` – poprzedni X bloku
  - `$$old_pos_y` – poprzedni Y bloku
  - `$$old_pos_z` – poprzedni Z bloku
  - `$$new_pos_x` – nowy X bloku
  - `$$new_pos_y` – nowy Y bloku
  - `$$new_pos_z` – nowy Z bloku

## Po rozpoczęciu biegu (`started_running`)
- Uruchamia się, gdy gracz zaczyna sprintować.
- Zmienne:
  - (brak)

## Po zatrzymaniu biegu (`stopped_running`)
- Uruchamia się, gdy gracz przestaje sprintować.
- Zmienne:
  - (brak)

## Po skoku (`jump`)
- Uruchamia się za każdym razem, gdy gracz skacze.
- Zmienne:
  - (brak)

## Po dołączeniu do serwera (`server_joined`)
- Uruchamia się po pomyślnym dołączeniu do serwera wieloosobowego.
- Zmienne:
  - `$$server_ip` – adres dołączonego serwera

## Po opuszczeniu serwera (`server_left`)
- Uruchamia się po rozłączeniu z serwerem wieloosobowym.
- Zmienne:
  - `$$server_ip` – adres opuszczonego serwera

## Po wejściu do świata singleplayer (`world_entered`)
- Uruchamia się po zakończeniu ładowania świata singleplayer i przywróceniu kontroli.
- Zmienne:
  - `$$world_name` – nazwa wyświetlana
  - `$$world_save_path` – pełna ścieżka folderu zapisu
  - `$$world_difficulty` – klucz trudności
  - `$$world_cheats_allowed` – TRUE, jeśli kody są włączone
  - `$$world_icon_path` – pełna ścieżka ikony
  - `$$world_is_first_join` – TRUE przy pierwszym wejściu

## Po wyjściu ze świata singleplayer (`world_left`)
- Uruchamia się po zamknięciu świata singleplayer i zakończeniu zapisu.
- Zmienne:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## Po dołączeniu innego gracza do świata/serwera (`other_player_joined_world`)
- Uruchamia się, gdy inny gracz dołącza do bieżącego świata/serwera.
- Zmienne:
  - `$$player_name` – nazwa dołączającego gracza
  - `$$player_uuid` – UUID

## Po opuszczeniu świata/serwera przez innego gracza (`other_player_left_world`)
- Uruchamia się, gdy inny gracz opuszcza bieżący świat/serwer.
- Zmienne:
  - `$$player_name`
  - `$$player_uuid`

## Po śmierci innego gracza (`other_player_died`)
- Uruchamia się, gdy inny gracz w bieżącym świecie umiera.
- Zmienne:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## Po podniesieniu przedmiotu (`item_picked_up`)
- Uruchamia się, gdy gracz podnosi encję przedmiotu.
- Zmienne:
  - `$$item_key` – lokalizacja zasobu podniesionego przedmiotu

## Po wyrzuceniu przedmiotu (`item_dropped`)
- Uruchamia się, gdy gracz wyrzuca przedmiot z ekwipunku.
- Zmienne:
  - `$$item_key` – lokalizacja zasobu wyrzuconego przedmiotu

## Po zużyciu przedmiotu (`item_consumed`)
- Uruchamia się, gdy gracz kończy konsumowanie przedmiotu.
- Zmienne:
  - `$$item_key` – zużyty przedmiot

## Po najechaniu na przedmiot w ekwipunku (`item_hovered_in_inventory`)
- Uruchamia się, gdy użytkownik najeżdża na przedmiot w dowolnym ekranie ekwipunku.
- Zmienne:
  - `$$item_key` – lokalizacja zasobu najechanego przedmiotu
  - `$$item_display_name_string` – nazwa przedmiotu jako zwykły tekst
  - `$$item_display_name_json` – nazwa przedmiotu jako komponent JSON

## Po użyciu przedmiotu (`item_used`)
- Uruchamia się, gdy gracz używa przedmiotu.
- Zmienne:
  - `$$item_key` – użyty przedmiot
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – typ docelowej encji lub puste
  - `$$used_on_block_key` – docelowy blok lub puste
  - `$$target_pos_x` – docelowy X lub -1
  - `$$target_pos_y` – docelowy Y lub -1
  - `$$target_pos_z` – docelowy Z lub -1

## Po zepsuciu przedmiotu (`item_broke`)
- Uruchamia się, gdy przedmiot w ekwipunku gracza ulega zniszczeniu.
- Zmienne:
  - `$$item_key` – zepsuty przedmiot
  - `$$item_type` – tool/armor/other
