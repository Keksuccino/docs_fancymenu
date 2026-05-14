---
title: Nasłuchiwacze
description: Jak tworzyć i używać nasłuchiwaczy w FancyMenu.
---

# Nasłuchiwacze

Począwszy od FancyMenu v3.8.0, dostępna jest nowa funkcja o nazwie „nasłuchiwacze”.

Nasłuchiwacze wykonują skrypty akcji, gdy wystąpią określone zdarzenia klienta lub rozgrywki.
Mogą one udostępniać zmienne dla akcji, placeholderów i wymagań zagnieżdżonych w nasłuchiwaczu.

W przeciwieństwie do większości rzeczy w FancyMenu, nasłuchiwacze nie są przypisane do ekranu ani nakładki. Działają cały czas w tle, nasłuchując swoich zdarzeń. Gdy tylko nasłuchiwacz zostanie wywołany, wykonuje swój skrypt akcji, nawet jeśli w danym momencie nie jest otwarty żaden ekran.

# Używanie nasłuchiwaczy

Aby utworzyć nowy nasłuchiwacz, który nasłuchuje zdarzenia i wykonuje skrypt akcji, kliknij **menu bar -> Customization -> Manage Listeners**, będąc **NIE** w edytorze układu. Znajdziesz tam prosty w obsłudze interfejs do tworzenia i zarządzania nasłuchiwaczami.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Zarządzanie nasłuchiwaczami" style="max-width:800px;width:100%;height:auto;">

# Zmienne nasłuchiwaczy

Nasłuchiwacze często udostępniają specjalny typ zmiennych dla swoich zagnieżdżonych akcji, wymagań i placeholderów.
Do tych zmiennych można odwoływać się jak do placeholderów (w praktyce są one placeholderami).

Używa się ich po prostu, wpisując ich nazwy z prefiksem `$$` w polach tekstowych, podobnie jak w przypadku zwykłego placeholdera.

Na przykład, jeśli używasz nasłuchiwacza **On Keyboard Key Pressed** i chcesz wypisać nazwę klawisza do logu za pomocą akcji **Print to Log**, możesz użyć czegoś takiego jak `Key pressed! The key is: $$key_name` jako treści wiadomości, którą ma wypisać akcja. Placeholder zmiennej zostanie później zastąpiony rzeczywistą nazwą klawisza.

> Mimo że nazywają się „zmiennymi”, nie mają one żadnego związku ze zwykłym [systemem zmiennych](/variables) FancyMenu. Nie można ich ustawiać, ponieważ są **tylko do odczytu**. Nie można też używać akcji, wymagań ani placeholderów przeznaczonych dla systemu zmiennych FancyMenu z tymi specjalnymi zmiennymi nasłuchiwaczy, więc **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** ani **Set Variable Value [FM Variable]** nie będą działać dla zmiennych nasłuchiwaczy.
{.is-warning}

# Nasłuchiwacze szczegółowo

Ta lista powinna zawierać większość, jeśli nie wszystkie, nasłuchiwacze FancyMenu. Możliwe, że nie zawsze jest ona aktualna z powodu aktualizacji moda.

## On Markdown Text Clicked
- Wyzwalane, gdy kliknięty zostanie tekst Markdown ze zdarzeniem `click:`, na przykład `[Open](click:open_menu)`.
- Zmienne:
  - `$$text_event_id` – ID zdarzenia z linku Markdown

## On Markdown Text Hovered
- Wyzwalane, gdy najedzie się kursorem na tekst Markdown ze zdarzeniem `hover:`, na przykład `[Hint](hover:show_hint)`.
- Zmienne:
  - `$$text_event_id` – ID zdarzenia z linku Markdown

## On ZIP Extracted via Action
- Wyzwalane, gdy zakończy się akcja **Extract ZIP File In Game Directory**.
- Zmienne:
  - `$$source_zip_path` – rozpoznana ścieżka źródłowego pliku ZIP
  - `$$target_folder_path` – rozpoznana ścieżka docelowego rozpakowania
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – tekst błędu, gdy rozpakowanie się nie powiodło

## On Element Spawned
- Wyzwalane, gdy element zostaje utworzony za pomocą akcji lub przepływu tworzenia elementu przez skrypt.
- Zmienne:
  - `$$element_type` – typ utworzonego elementu
  - `$$element_identifier` – identyfikator utworzonego elementu
  - `$$target_screen` – identyfikator ekranu docelowego

## On Animated Texture Started Playing
- Wyzwalane, gdy animowana tekstura zaczyna się odtwarzać.
- Zmienne:
  - `$$texture_source` – źródło tekstury
  - `$$texture_source_type` – typ źródła
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing
- Wyzwalane, gdy animowana tekstura kończy odtwarzanie.
- Zmienne:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed
- Wyzwalane, gdy element wideo lub tło menu wideo zmienia status odtwarzania.
- Zmienne:
  - `$$video_source` – źródło wideo
  - `$$video_source_type` – typ źródła
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` lub `FINISHED`

## On System Message Received in Chat
- Wyzwalane, gdy klient otrzyma wiadomość systemową na czacie, np. odpowiedź na komendę.
- Zmienne:
  - `$$system_message_string` – zwykły tekst wiadomości
  - `$$system_message_component` – komponent JSON

## On FM Data Received
- Wyzwalane, gdy serwer wysyła dane FM do tego klienta przez `/fmdata send`.
- Zmienne:
  - `$$data_identifier` – identyfikator danych jako tekst
  - `$$data` – ładunek danych
  - `$$sent_by` – IP serwera lub `integrated_server`

## On Remote Server Connected
- Wyzwalane, gdy FancyMenu inicjuje połączenie z serwerem zdalnym.
- Zmienne:
  - `$$request_id` – zapisany identyfikator żądania
  - `$$remote_server_url` – adres URL serwera zdalnego

## On Remote Server Data Received
- Wyzwalane, gdy z połączonego serwera zdalnego otrzymane zostaną dane tekstowe.
- Zmienne:
  - `$$request_id` – identyfikator żądania
  - `$$remote_server_url` – adres URL serwera zdalnego
  - `$$data` – otrzymany ładunek

## On Remote Server Connection Closed
- Wyzwalane, gdy połączenie z serwerem zdalnym zostanie zamknięte.
- Zmienne:
  - `$$request_id` – identyfikator żądania
  - `$$remote_server_url` – adres URL serwera zdalnego
  - `$$intentionally_closed` – TRUE, jeśli zamknięto je akcją
  - `$$crashed` – TRUE, jeśli połączenie uległo nieoczekiwanemu awaryjnemu zamknięciu
  - `$$unknown_close_reason` – TRUE, jeśli nie było znanej przyczyny zamknięcia

## On Keyboard Key Pressed
- Wyzwalane za każdym naciśnięciem klawisza (powtarza się przy przytrzymaniu; działa w ekranach i w grze).
- Zmienne:
  - `$$key_name` – nazwa wyświetlana klawisza
  - `$$key_keycode` – kod klawisza GLFW
  - `$$key_scancode` – kod skanowania GLFW
  - `$$key_modifiers` – aktywna maska bitowa modyfikatorów

## On Keyboard Key Released
- Wyzwalane po zwolnieniu klawisza (w ekranach i w grze).
- Zmienne:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- Wyzwalane, gdy wpisywany jest znak przy otwartym ekranie.
- Zmienne:
  - `$$char` – wpisany znak

## On Mouse Moved in Screen
- Wyzwalane za każdym razem, gdy mysz porusza się przy otwartym ekranie.
- Zmienne:
  - `$$mouse_pos_x` – bieżące X
  - `$$mouse_pos_y` – bieżące Y
  - `$$mouse_move_delta_x` – różnica X od ostatniego zdarzenia
  - `$$mouse_move_delta_y` – różnica Y od ostatniego zdarzenia

## On Mouse Button Clicked
- Wyzwalane, gdy wciśnięty zostanie przycisk myszy (w ekranach i w grze).
- Zmienne:
  - `$$button` – lewy/prawy/środkowy
  - `$$mouse_pos_x` – bieżące X
  - `$$mouse_pos_y` – bieżące Y

## On Mouse Button Released
- Wyzwalane, gdy przycisk myszy zostanie zwolniony (w ekranach i w grze).
- Zmienne:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- Wyzwalane, gdy kółko myszy zostanie przewinięte przy otwartym ekranie.
- Zmienne:
  - `$$scroll_delta_y` – pionowa wartość przewinięcia

## On Screen Opened
- Uruchamiane zaraz po tym, jak jakikolwiek ekran stanie się aktywny; można użyć do jego nadpisania.
- Zmienne:
  - `$$screen_identifier` – identyfikator otwartego ekranu

## On Screen Closed
- Uruchamiane natychmiast po zamknięciu ekranu.
- Zmienne:
  - `$$screen_identifier` – identyfikator zamkniętego ekranu

## On Quit Minecraft
- Wyzwalane raz, gdy klient zaczyna się zamykać.
- Zmienne:
  - `$$timestamp_millis` – epoch millis w momencie wyjścia
  - `$$timestamp_iso` – znacznik czasu ISO-8601 momentu wyjścia

## On Death
- Uruchamiane, gdy dla lokalnego gracza otwiera się domyślny ekran śmierci.
- Zmienne:
  - `$$days_survived` – dni od ostatniej śmierci
  - `$$death_reason_string` – przyczyna w zwykłym tekście
  - `$$death_reason_component` – przyczyna jako komponent JSON
  - `$$death_pos_x` – współrzędna X śmierci
  - `$$death_pos_y` – współrzędna Y śmierci
  - `$$death_pos_z` – współrzędna Z śmierci

## On Variable Updated [FM Variable]
- Wyzwalane za każdym razem, gdy zmienna FancyMenu zostanie ustawiona/zaktualizowana.
- Zmienne:
  - `$$var_name` – nazwa zmiennej
  - `$$old_value` – poprzednia wartość
  - `$$new_value` – nowa wartość

## On File Downloaded via Action
- Wyzwalane po zakończeniu akcji „Download File to Game Directory”.
- Zmienne:
  - `$$download_url` – źródło pobierania
  - `$$target_file_path` – zapisana ścieżka pliku
  - `$$download_succeeded` – true/false

## On File Selected
- Wyzwalane po zakończeniu akcji „Select File”.
- Zmienne:
  - `$$selected_file_path` – pełna wybrana ścieżka pliku lub pusta, jeśli anulowano
  - `$$target_file_path` – rozpoznana ścieżka wewnątrz instancji
  - `$$selection_succeeded` – true, jeśli kopiowanie się powiodło
  - `$$selection_cancelled` – true, jeśli okno zostało zamknięte
  - `$$failure_reason` – informacje o błędzie w przypadku niepowodzenia

## On Chat Message Received
- Wyzwalane, gdy zwykła wiadomość czatu gracza pojawi się u klienta.
- Zmienne:
  - `$$chat_message_string` – zwykły tekst linii
  - `$$chat_message_component` – pełny komponent JSON
  - `$$sender_uuid` – UUID nadawcy lub ERROR
  - `$$sender_name` – nazwa nadawcy lub ERROR

## On Chat Message Sent
- Wyzwalane, gdy lokalny gracz wyśle wiadomość na czacie.
- Zmienne:
  - `$$chat_message_string` – zwykły tekst linii
  - `$$chat_message_component` – pełny komponent JSON

## On Effect Gained
- Wyzwalane, gdy gracz otrzyma efekt statusu.
- Zmienne:
  - `$$effect_key` – lokalizacja zasobu efektu
  - `$$effect_type` – pozytywny/negatywny/neutralny
  - `$$effect_duration` – pozostałe ticki

## On Effect Lost
- Wyzwalane, gdy gracz straci efekt statusu.
- Zmienne:
  - `$$effect_key` – wygasły efekt
  - `$$effect_type` – kategoria

## On Experience Changed
- Wyzwalane za każdym razem, gdy zmienia się całkowite XP gracza.
- Zmienne:
  - `$$new_experience_amount` – po zmianie
  - `$$old_experience_amount` – przed zmianą
  - `$$is_level_up` – TRUE, jeśli poziom wzrósł

## On Damage Taken
- Wyzwalane raz na każde trafienie, gdy gracz otrzymuje obrażenia.
- Zmienne:
  - `$$damage_amount` – utracone zdrowie
  - `$$damage_type` – lokalizacja zasobu typu obrażeń
  - `$$is_fatal_damage` – TRUE, jeśli obrażenia są śmiertelne
  - `$$damage_source` – lokalizacja zasobu atakującego lub NONE

## On Started Freezing
- Wyzwalane, gdy gracz zaczyna zamarzać.
- Zmienne:
  - `$$freezing_intensity` – 0.0 brak, 1.0 całkowite zamarznięcie

## On Stopped Freezing
- Wyzwalane, gdy gracz przestaje zamarzać.
- Zmienne:
  - (brak)

## On Fully Frozen
- Wyzwalane raz, gdy gracz zostaje całkowicie zamrożony.
- Zmienne:
  - (brak)

## On Start Looking At Block
- Wyzwalane raz, gdy celownik po raz pierwszy wskazuje blok (maks. odległość 20 bloków).
- Zmienne:
  - `$$block_key` – wskazywany blok
  - `$$block_pos_x` – X bloku
  - `$$block_pos_y` – Y bloku
  - `$$block_pos_z` – Z bloku
  - `$$distance_to_player` – od oczu do punktu trafienia

## On Stop Looking At Block
- Wyzwalane, gdy celownik przestaje wskazywać blok (zgłasza ostatnio wskazywany blok, maks. 20 bloków).
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- Wyzwalane raz, gdy celownik po raz pierwszy wskazuje encję (maks. 20 bloków).
- Zmienne:
  - `$$entity_key` – wskazywany typ encji
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- Wyzwalane, gdy celownik przestaje wskazywać encję (zgłasza ostatnio wskazywaną encję, maks. 20 bloków).
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **Wymaga FancyMenu na serwerze.** Wyzwalane, gdy jakakolwiek encja pojawi się gdziekolwiek w połączonym świecie/na serwerze.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player` – −1, jeśli inny wymiar
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **Wymaga FancyMenu na serwerze.** Wyzwalane, gdy jakakolwiek encja umrze w połączonym świecie/na serwerze.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player` – −1, jeśli inny wymiar
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

## On Entity Starts Being In Sight
- Wyzwalane, gdy encja po raz pierwszy staje się widoczna w odległości do 200 bloków.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- Wyzwalane, gdy wcześniej widoczna encja znika z pola widzenia lub oddala się ponad 200 bloków.
- Zmienne:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- Wyzwalane, gdy gracz skutecznie wejdzie w interakcję z encją.
- Zmienne:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- Wyzwalane, gdy gracz zaczyna jeździć na encji.
- Zmienne:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- Wyzwalane, gdy gracz przestaje jeździć na swojej aktualnej encji.
- Zmienne:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- Wyzwalane, gdy gracz niszczy blok.
- Zmienne:
  - `$$block_key`
  - `$$broke_with_item_key` – użyte narzędzie lub EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- Wyzwalane, gdy gracz stawia blok.
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- Wyzwalane, gdy gracz skutecznie wejdzie w interakcję z blokiem.
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- Wyzwalane, gdy gracz staje na bloku.
- Zmienne:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- Wyzwalane, gdy gracz wchodzi do nowego biomu.
- Zmienne:
  - `$$biome_key` – biom, do którego wszedł

## On Leave Biome
- Wyzwalane, gdy gracz opuszcza aktualny biom.
- Zmienne:
  - `$$biome_key` – biom, który właśnie opuścił

## On Enter Structure
- **Wymaga FancyMenu na serwerze.** Zgrubne wykrywanie obszaru struktury; może zostać wyzwolone w pobliżu/nad/pod strukturą.
- Zmienne:
  - `$$structure_key` – struktura, do której wszedł

## On Leave Structure
- **Wymaga FancyMenu na serwerze.** Zgrubne wykrywanie; może zostać wyzwolone w pobliżu zarysu struktury.
- Zmienne:
  - `$$structure_key` – struktura, którą właśnie opuścił

## On Enter Structure (High Precision)
- **Wymaga FancyMenu na serwerze.** Wyzwalane, gdy gracz wejdzie do brył ograniczających struktury.
- Zmienne:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **Wymaga FancyMenu na serwerze.** Wyzwalane po wyjściu gracza poza bryły ograniczające struktury.
- Zmienne:
  - `$$structure_key`

## On Dimension Entered
- Wyzwalane, gdy gracz wchodzi do nowego wymiaru.
- Zmienne:
  - `$$dimension_key` – wymiar, do którego wszedł

## On Start Swimming
- Wyzwalane, gdy gracz zaczyna pływać.
- Zmienne:
  - `$$fluid_type` – lokalizacja zasobu płynu

## On Stop Swimming
- Wyzwalane, gdy gracz przestaje pływać.
- Zmienne:
  - `$$fluid_type` – płyn, w którym pływanie się zakończyło

## On Start Touching Fluid
- Wyzwalane, gdy gracz zaczyna dotykać płynu.
- Zmienne:
  - `$$fluid_type` – dotykany płyn

## On Stop Touching Fluid
- Wyzwalane, gdy gracz przestaje dotykać płynu.
- Zmienne:
  - `$$fluid_type` – płyn, którego gracz już nie dotyka

## On Music Track Started
- Wyzwalane, gdy zaczyna się nowy utwór muzyczny.
- Zmienne:
  - `$$track_resource_location` – plik audio
  - `$$track_display_name` – czytelna nazwa lub UNKNOWN
  - `$$track_artist` – wykonawca lub UNKNOWN
  - `$$track_duration_ms` – milisekundy (0, jeśli nieznane)

## On Music Track Stopped
- Wyzwalane, gdy bieżący utwór muzyczny kończy się lub zostaje zastąpiony.
- Zmienne:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- Wyzwalane, gdy dźwięk świata o określonej pozycji rozpoczyna się w pobliżu gracza.
- Zmienne:
  - `$$sound_resource_location` – plik dźwiękowy
  - `$$sound_display_name` – nazwa napisu pomocniczego, jeśli dostępna
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – stopnie 0–360 względem kierunku patrzenia

## On Weather Changed
- Wyzwalane, gdy pogoda zmienia się globalnie lub lokalnie (zmiana biomu albo wejście do wnętrza może uruchomić je ponownie).
- Zmienne:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE, jeśli renderowany jest śnieg
  - `$$weather_can_rain` – TRUE, jeśli renderowany jest deszcz

## On Started Burning
- Wyzwalane, gdy gracz zaczyna płonąć.
- Zmienne:
  - (brak)

## On Stopped Burning
- Wyzwalane, gdy gracz przestaje płonąć.
- Zmienne:
  - (brak)

## On Started Drowning
- Wyzwalane, gdy gracz zaczyna otrzymywać obrażenia od utonięcia.
- Zmienne:
  - (brak)

## On Position Changed
- Wyzwalane za każdym razem, gdy zmienia się blokowa pozycja gracza.
- Zmienne:
  - `$$old_pos_x` – poprzedni X bloku
  - `$$old_pos_y` – poprzedni Y bloku
  - `$$old_pos_z` – poprzedni Z bloku
  - `$$new_pos_x` – nowy X bloku
  - `$$new_pos_y` – nowy Y bloku
  - `$$new_pos_z` – nowy Z bloku

## On Started Running
- Wyzwalane, gdy gracz zaczyna sprintować.
- Zmienne:
  - (brak)

## On Stopped Running
- Wyzwalane, gdy gracz przestaje sprintować.
- Zmienne:
  - (brak)

## On Jump
- Wyzwalane za każdym razem, gdy gracz skacze.
- Zmienne:
  - (brak)

## On Server Joined
- Wyzwalane po pomyślnym dołączeniu do serwera wieloosobowego.
- Zmienne:
  - `$$server_ip` – adres dołączonego serwera

## On Server Left
- Wyzwalane po rozłączeniu z serwera wieloosobowego.
- Zmienne:
  - `$$server_ip` – adres opuszczonego serwera

## Singleplayer World Entered
- Wyzwalane po zakończeniu ładowania świata jednoosobowego i przywróceniu kontroli.
- Zmienne:
  - `$$world_name` – nazwa wyświetlana
  - `$$world_save_path` – pełna ścieżka folderu zapisu
  - `$$world_difficulty` – klucz trudności
  - `$$world_cheats_allowed` – TRUE, jeśli kody są włączone
  - `$$world_icon_path` – pełna ścieżka ikony
  - `$$world_is_first_join` – TRUE przy pierwszej wizycie

## Singleplayer World Left
- Wyzwalane po zamknięciu świata jednoosobowego i zakończeniu zapisu.
- Zmienne:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- Wyzwalane, gdy inny gracz dołącza do bieżącego świata/serwera.
- Zmienne:
  - `$$player_name` – nazwa dołączającego gracza
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- Wyzwalane, gdy inny gracz opuszcza bieżący świat/serwer.
- Zmienne:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- Wyzwalane, gdy inny gracz w bieżącym świecie umiera.
- Zmienne:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- Wyzwalane, gdy gracz podnosi encję przedmiotu.
- Zmienne:
  - `$$item_key` – lokalizacja zasobu podniesionego przedmiotu

## On Item Dropped
- Wyzwalane, gdy gracz wyrzuca przedmiot z ekwipunku.
- Zmienne:
  - `$$item_key` – lokalizacja zasobu wyrzuconego przedmiotu

## On Item Consumed
- Wyzwalane, gdy gracz kończy konsumowanie przedmiotu.
- Zmienne:
  - `$$item_key` – skonsumowany przedmiot

## On Item Hovered in Inventory
- Wyzwalane, gdy użytkownik najedzie na przedmiot w dowolnym ekranie ekwipunku.
- Zmienne:
  - `$$item_key` – lokalizacja zasobu wskazanego przedmiotu
  - `$$item_display_name_string` – nazwa przedmiotu w zwykłym tekście
  - `$$item_display_name_json` – nazwa przedmiotu jako komponent JSON

## On Item Used
- Wyzwalane, gdy gracz używa przedmiotu.
- Zmienne:
  - `$$item_key` – użyty przedmiot
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – docelowy typ encji lub puste
  - `$$used_on_block_key` – docelowy blok lub puste
  - `$$target_pos_x` – docelowy X lub -1
  - `$$target_pos_y` – docelowy Y lub -1
  - `$$target_pos_z` – docelowy Z lub -1

## On Item Broke
- Wyzwalane, gdy przedmiot w ekwipunku gracza się psuje.
- Zmienne:
  - `$$item_key` – zepsuty przedmiot
  - `$$item_type` – tool/armor/other
