---
title: Skrypty akcji
description: >-
  Jak używać skryptów akcji z przyciskami, suwakami, tickerami i innymi
  elementami.
---
# Skrypty akcji

Skrypty akcji uruchamiają skonfigurowane zadania, gdy zostanie kliknięty [Button](./elements#button), zaktualizuje się [Ticker](./elements#ticker), zmieni się [Slider](./elements#slider), otworzy się lub zamknie ekran albo wystąpi inne obsługiwane zdarzenie. Instrukcje takie jak **if**, **else-if**, **else** i **while** dodają warunkowe sterowanie.

> [!CAUTION]
> Zaimportowane skrypty akcji mogą modyfikować pliki, kontaktować się z serwerami, otwierać linki lub uruchamiać polecenia. Używaj tylko źródeł, którym ufasz.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Edytor skryptów akcji" style="max-width:800px;width:100%;height:auto;">

# Czym są akcje?

**Akcja** to zadanie lub operacja, którą FancyMenu uruchamia po wyzwoleniu. Na przykład akcja może otworzyć nowy ekran, wysłać wiadomość na czacie albo zmienić głośność [Audio element](./elements#audio). W edytorze FancyMenu akcje są konfigurowane z wartością (jeśli jest potrzebna), która dostarcza dodatkowych informacji — takich jak URL lub adres serwera.

# Instrukcje

Aby tworzyć bardziej złożone zachowania, FancyMenu obsługuje instrukcje sterujące w skryptach akcji:

| Instrukcja | Zachowanie |
|---|---|
| **If** | Uruchamia swoje akcje tylko wtedy, gdy spełnione są jego [wymagania](./conditions). |
| **Else-If** | Sprawdza kolejny zestaw [wymagań](./conditions), gdy poprzedni **If** lub **Else-If** nie został uruchomiony. |
| **Else** | Uruchamia się, gdy żadne z poprzednich wymagań **If** lub **Else-If** nie są spełnione. |
| **While** | Powtarza swoje akcje, dopóki jego [wymagania](./conditions) pozostają spełnione. Zatrzymuje się po trzech sekundach, aby zapobiec nieskończonym pętlom; nie używaj go jako timera. |

# Bloki

Do skryptów można dodawać bloki, które zapewniają przydatne funkcje pozwalające lepiej kontrolować przepływ/czas wykonywania skryptu oraz oferują kilka przydatnych usprawnień:

| Blok | Zachowanie |
|---|---|
| **Delay** | Rozpoczyna odliczanie bez zatrzymywania reszty skryptu. Zagnieżdżone akcje stają się dostępne po upływie opóźnienia; ponowna inicjalizacja ekranu resetuje odliczanie. |
| **Execute Later** | Zaplanowuje ponowne uruchomienie zagnieżdżonych akcji po opóźnieniu za każdym razem, gdy blok zostanie osiągnięty. |
| **Comment** | Dodaje notatkę wewnątrz skryptu dla lepszej organizacji i nie uruchamia żadnej akcji. |

# Wykonywanie skryptu

Akcje wykonywane są od góry do dołu. Nieudana akcja jest zapisywana w logu, a następnie skrypt jest kontynuowany.

Pobieranie, rozpakowywanie ZIP-ów i żądania HTTP kończą się później; następna akcja nie czeka. Użyj [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) albo zmiennej odpowiedzi HTTP, gdy dalsze działania zależą od wyniku.

# Gdzie można używać skryptów akcji?

Skrypty akcji są wszechstronne i można ich używać w całym układzie. Możesz przypisać je na przykład do:

- [**Buttons**](./elements#button): Wykonuje akcję po kliknięciu przycisku.
- [**Tickers**](./elements#ticker): Ciągle uruchamia skrypt akcji, aby aktualizować informacje wyświetlane na ekranie w układzie.
- [**Sliders**](./elements#slider): Uruchamia skrypt akcji za każdym razem, gdy zmienia się wartość suwaka.
- **Screen Events:** Uruchamia skrypty, gdy ekran się otwiera lub zamyka (na przykład odtwarzanie dźwięku, gdy pojawia się menu).
- [**Listeners**](./listeners): Gdy listener otrzyma skonfigurowane zdarzenie, uruchamia swój skrypt akcji.
- [**Schedulers**](./schedulers): Wykonuje akcje według harmonogramu, nawet gdy żaden ekran nie jest otwarty.

# Używanie placeholderów w akcjach

Wartości akcji obsługują dynamiczną zawartość za pomocą **placeholderów**. Najczęściej placeholdery te używają składni podobnej do JSON i są zastępowane danymi na żywo podczas uruchamiania akcji.

## Placeholdery w stylu JSON

Są to standardowe [placeholdere](./placeholders), których można używać w wielu miejscach w układach.

Korzystają z następującej składni:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Mogą pobierać dane gry, takie jak nazwa gracza, wymiary ekranu lub obliczone wartości za pomocą [**Calculator** placeholder](./placeholders#calculator-calc). Można też zagnieżdżać placeholdery, aby uzyskać bardziej zaawansowane zastosowania.

## Placeholdery `$$` (zmienne)

Wartości `$$` to tylko do odczytu, przekazywane do konkretnego skryptu akcji przez funkcję, która go uruchamia.

Na przykład [Slider](./elements#slider) przekazuje swoją bieżącą wartość jako `$$value`.

Każdy [listener](./listeners) dokumentuje wartości `$$`, które przekazuje, takie jak wciśnięty przycisk myszy lub wprowadzona struktura.

Nazwy `$$` rozróżniają wielkość liter i działają tylko w skrypcie, który je udostępnia. Zobacz [Listeners](./listeners#listener-variables).

## Separatory wartości akcji

Użyj dokładnie takiego separatora, jaki pokazano dla danej akcji: `:`, `||` lub `|||`. Nie istnieje składnia ucieczki dla separatorów wewnątrz pola.

Placeholdere są zastępowane przed podziałem wartości. W przypadku `set_variable` tylko pierwszy dwukropek oddziela nazwę od wartości, więc kolejne dwukropki pozostają częścią wartości.

## Wartości tekstowe

[Kody formatowania FancyMenu](./text-formatting#minecraft-text-formatting) używają `&` zamiast znaku `§` z Minecrafta wszędzie tam, gdzie akcja przyjmuje sformatowany tekst.

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) i [**Paste to Chat**](#paste-to-chat-paste_to_chat) obsługują te kody formatowania.
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) przyjmuje zwykły tekst lub serializowany JSON komponentu tekstowego Minecrafta.
- [**Open URL in Browser**](#open-url-in-browser-openlink) stosuje tę samą konwersję kodów formatowania przed przekazaniem URL do systemu operacyjnego.

# Jak skonfigurować i edytować akcje

Aby edytować akcje elementu i bloki instrukcji, **kliknij element prawym przyciskiem myszy** i wybierz **Manage Action Script**. W edytorze możesz:

- **Dodawać nowe akcje lub instrukcje:** Wstawiaj nowe wpisy akcji lub instrukcje sterujące (if, else-if, else, while), aby budować swój skrypt.
- **Edytować istniejące akcje lub instrukcje:** Modyfikuj wartość akcji lub zmieniaj logikę sterującą.
- **Usuwać akcje lub instrukcje:** Kasuj niepotrzebne akcje ze skryptu.

Twórz i edytuj skrypty listenerów przez [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Skróty edytora skryptów akcji

## Skróty

- `DEL` : Szybko usuwa zaznaczony wpis
- `ENTER` : Rozpoczyna edycję inline zaznaczonego wpisu (lub otwiera ekran edycji, jeśli dla zaznaczonego wpisu nie ma edycji inline)
- `Ctrl/Command + C` : Kopiuje zaznaczoną akcję (na razie działa tylko z akcjami)
- `Ctrl/Command + V` : Wkleja wcześniej skopiowaną akcję
- `Ctrl/Command + Z` : Cofnij o jeden krok
- `Ctrl/Command + Y` : Ponów o jeden krok
- `ARROW UP` : Przechodzi o jeden wpis w górę od aktualnie zaznaczonego
- `ARROW DOWN` : Przechodzi o jeden wpis w dół od aktualnie zaznaczonego
- `SHIFT + ARROW UP` : Przenosi zaznaczony wpis o jeden poziom w górę
- `SHIFT + ARROW DOWN` : Przenosi zaznaczony wpis o jeden poziom w dół
- `A` : Szybko otwiera ekran Action Chooser, aby dodać nową akcję
- `Ctrl/Command + S` : Zakończ/zapisz z okna edytora

## Edycja

- Dwukrotne kliknięcie wartości akcji pozwala edytować ją bez przechodzenia do pełnego ekranu edycji wartości.
- Łańcuchy instrukcji IF (z dołączonymi instrukcjami ELSE/ELSE-IF), pętle WHILE i Foldery można zwijać (tylko wizualnie, nie wpływa to na logikę skryptu).
- Edytor zawsze dodaje nowe akcje poniżej zaznaczonego wpisu (lub wewnątrz zaznaczonego łańcucha/pętli/folderu).
- Kliknięcie prawym przyciskiem myszy na ciemnoszarym tle obszaru skryptu otwiera menu kontekstowe z opcjami dodawania akcji, instrukcji i wszystkich innych ważnych elementów.

# Szczegóły akcji

Ta sekcja zawiera listę wbudowanych akcji FancyMenu.

## Następny utwór (`audio_next_track`)

**Cel:** Przechodzi do następnego utworu w [Audio element](./elements#audio)

**Wartość:** Wymagana — `audio_element_identifier` (identyfikator elementu audio, którym chcesz sterować)

## Poprzedni utwór (`audio_previous_track`)

**Cel:** Przechodzi do poprzedniego utworu w [Audio element](./elements#audio)

**Wartość:** Wymagana — `audio_element_identifier` (identyfikator elementu audio, którym chcesz sterować)

## Ustaw głośność utworu (`set_audio_element_volume`)

**Cel:** Ustawia głośność [Audio element](./elements#audio) (`0.0` do `1.0`)

**Wartość:** Wymagana — `element_identifier:volume`

## Przełącz odtwarzanie/pauzę utworu (`audio_toggle_play`)

**Cel:** Przełącza bieżący utwór w [Audio element](./elements#audio) między odtwarzaniem a pauzą

**Wartość:** Wymagana — `audio_element_identifier`

## Odtwórz audio (`play_audio`)

**Cel:** Odtwarza zasób audio jednorazowo. Audio uruchomione przez tę akcję można później zatrzymać za pomocą [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

**Wartość:** Wymagana — konfiguracja JSON z `audioSource`, `soundChannel` i `baseVolume`

**Przykład:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Zachowanie:**

- `baseVolume` jest ograniczane do zakresu `0.0`–`1.0`.
- Nieznany kanał dźwięku używa kanału Master.
- Akcja nie może zostać uruchomiona z asynchronicznego [Ticker](./elements#ticker); FancyMenu pokaże zamiast tego błąd.
- FancyMenu czeka do dziesięciu sekund, aż zasób audio będzie gotowy.
- Pomyślnie rozpoczęte utwory można zatrzymać za pomocą [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

## Zatrzymaj wszystkie audio akcji (`stop_all_action_audios`)

**Cel:** Zatrzymuje wszystkie ścieżki audio uruchomione przez akcję [**Play Audio**](#play-audio-play_audio). Nie zatrzymuje to [Audio elements](./elements#audio), dźwięków otwierania/zamykania menu, dźwięków przycisków ani innych systemów audio.

**Wartość:** Nie jest wymagana

## Ustaw głośność elementu wideo (`set_video_element_volume`)

**Cel:** Ustawia głośność [Video element](./video) (`0.0` do `1.0`)

**Wartość:** Wymagana — `video_element_identifier:volume`

## Ustaw czas odtwarzania elementu wideo (`set_video_element_play_time`)

**Cel:** Przewija [Video element](./video) do znacznika czasu w milisekundach

**Wartość:** Wymagana — `video_element_identifier:timestamp_ms`

## Przełącz stan pauzy elementu wideo (`toggle_video_element_pause_state`)

**Cel:** Przełącza stan pauzy [Video element](./video)

**Wartość:** Wymagana — `video_element_identifier`

## Ustaw głośność tła wideo (`set_video_menu_background_volume`)

**Cel:** Ustawia głośność [Video menu background](./video) (`0.0` do `1.0`)

**Wartość:** Wymagana — `background_identifier:volume`

> [!NOTE]
> Aby uzyskać identyfikator tła, kliknij prawym przyciskiem myszy tło edytora i wybierz „Copy Background Identifier”.

## Ustaw czas odtwarzania tła wideo (`set_video_menu_background_play_time`)

**Cel:** Przewija [Video menu background](./video) do znacznika czasu w milisekundach

**Wartość:** Wymagana — `background_identifier:timestamp_ms`

> [!NOTE]
> Aby uzyskać identyfikator tła, kliknij prawym przyciskiem myszy tło edytora i wybierz „Copy Background Identifier”.

## Przełącz stan pauzy tła wideo (`toggle_video_menu_background_pause_state`)

**Cel:** Przełącza stan pauzy [Video menu background](./video)

**Wartość:** Wymagana — `background_identifier`

> [!NOTE]
> Aby uzyskać identyfikator tła, kliknij prawym przyciskiem myszy tło edytora i wybierz „Copy Background Identifier”.

## Przełącz układ (`toggle_layout`)

**Cel:** Przełącza układ (włącz/wyłącz) według nazwy pliku bez `.txt`

**Wartość:** Wymagana — `layout_name`

## Włącz układ (`enable_layout`)

**Cel:** Włącza i zapisuje układ według nazwy pliku bez `.txt`

**Wartość:** Wymagana — `layout_name`

## Wyłącz układ (`disable_layout`)

**Cel:** Wyłącza i zapisuje układ według nazwy pliku bez `.txt`

**Wartość:** Wymagana — `layout_name`

Wszystkie trzy akcje układu zapisują stan w pliku układu i natychmiast aktualizują bieżący ekran. Używaj nazwy pliku z uwzględnieniem wielkości liter, bez `.txt`.

## Otwórz ekran lub niestandardowe GUI (`opengui`)

**Cel:** Otwiera ekran według jego identyfikatora (vanilla, mod lub własne GUI)

**Wartość:** Wymagana — `screen_identifier`

Skopiuj dokładny identyfikator z uwzględnieniem wielkości liter z nakładki debugowania [Screen Identifiers](./screen-identifiers).

Niektórych ekranów modów nie można utworzyć bezpośrednio. Jeśli otwieranie się nie powiedzie, użyj [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) na widżecie, który normalnie otwiera ten ekran.

## Zamknij ekran (`closegui`)

**Cel:** Zamknij aktywny ekran

**Wartość:** Nie jest wymagana

## Zaktualizuj ekran (`update_screen`)

**Cel:** Ponownie inicjalizuje bieżący ekran

**Wartość:** Nie jest wymagana

## Powrót do poprzedniego ekranu (`back_to_last_screen`)

**Cel:** Wraca do rodzica [Custom GUI](./custom-guis) albo do ostatnio zamkniętej instancji ekranu

**Wartość:** Nie jest wymagana

## Dołącz do serwera (`joinserver`)

**Cel:** Łączy gracza z serwerem Minecraft

**Wartość:** Wymagana — `server_ip` lub `server_ip:port`

Ta akcja nie może być uruchomiona, gdy świat lub serwer jest już załadowany. Gdy port nie zostanie podany, używany jest `25565`. Jeśli adres nie znajduje się na liście zapisanych serwerów Minecrafta, FancyMenu doda go i zapisze.

## Wejdź do świata (`loadworld`)

**Cel:** Wchodzi do świata Minecraft

**Wartość:** Wymagana — `world_folder_name`

Wartość to nazwa folderu zapisu. Akcja nie robi nic, jeśli taki zapis nie istnieje albo inny świat/serwer jest już załadowany.

## Wejdź/dołącz do ostatniego świata/serwera (`join_last_world`)

**Cel:** Wchodzi/dołącza do ostatniego świata lub serwera, na którym był gracz

**Wartość:** Nie jest wymagana

Ta akcja nie może zostać uruchomiona, gdy inny świat/serwer jest już załadowany. Zapamiętany serwer, którego nie ma na liście zapisanych serwerów Minecrafta, zostaje dodany i zapisany przed połączeniem.

## Opuść świat lub serwer (`disconnect_server_or_world`)

**Cel:** Opuszcza świat lub serwer i otwiera wskazany ekran

**Wartość:** Wymagana — `screen_identifier`

Ta akcja działa tylko wtedy, gdy załadowany jest świat i gracz. Cel może być identyfikatorem [Custom GUI](./custom-guis) lub [identyfikatorem ekranu](./screen-identifiers), który FancyMenu potrafi utworzyć. Jeśli nie uda się otworzyć celu, FancyMenu wraca do ekranu tytułowego.

## Wyjdź z Minecrafta (`quitgame`)

**Cel:** Całkowicie zamyka Minecrafta

**Wartość:** Nie jest wymagana

## Wyślij wiadomość na czacie/polecenie (`sendmessage`)

**Cel:** Wysyła wiadomość na czat lub wykonuje polecenie czatu. Tekst wiadomości obsługuje [kody formatowania FancyMenu](./text-formatting#minecraft-text-formatting).

**Wartość:** Wymagana — `message_text` lub `/command_text`

## Wykonaj polecenie jako zintegrowany serwer (`execute_command_as_integrated_server`)

**Cel:** Wymusza wykonanie polecenia w singleplayerze jako zintegrowany serwer, ignorując uprawnienia i ustawienie cheatów.

**Wartość:** Wymagana — tekst polecenia, na przykład `/give @p minecraft:diamond 1`

> [!WARNING]
> Ta akcja działa tylko w trybie singleplayer, gdy świat **nie jest otwarty do LAN**. Celowo nic nie robi, gdy nie istnieje zintegrowany serwer lub gdy zintegrowany serwer jest udostępniony do LAN.

## Wklej do czatu (`paste_to_chat`)

**Cel:** Wkleja sformatowany tekst do pola wprowadzania czatu, gdy załadowany jest gracz/świat

**Wartość:** Wymagana — `true:Text` lub `false:Text`

Gdy czat nie jest jeszcze otwarty, FancyMenu otwiera go i ustawia tekst wprowadzania. Gdy czat jest już otwarty, `true` dopisuje do istniejącego tekstu, a `false` go zastępuje.

## Wyświetl na czacie [po stronie klienta] (`display_in_chat_client_side`)

**Cel:** Wyświetla wiadomość na czacie po stronie klienta, gdy załadowany jest świat lub serwer. Nic nie jest wysyłane do serwera.

**Wartość:** Wymagana — `text_or_json`

Wartość może być zwykłym tekstem lub serializowanym komponentem tekstowym Minecrafta. Akcja nie robi nic, gdy nie jest załadowany żaden świat.

## Wyślij dane FM do serwera (`send_fm_data_to_server`)

**Cel:** Wysyła [FM Data](./fm-data) do bieżącego serwera FancyMenu.

**Wartość:** Wymagana — `data_identifier||data`

## Połącz z zdalnym serwerem (`connect_to_remote_server`)

**Cel:** Otwiera lub ponownie wykorzystuje połączenie WebSocket zainicjowane przez klienta z zewnętrznym zdalnym serwerem.

**Wartość:** Wymagana — adres URL zdalnego serwera, na przykład `wss://example.com/ws`

Zobacz [Remote Server Communication](./remote-server-communication#url-modes), aby poznać akceptowane formy URL.

## Wyślij dane do zdalnego serwera (`send_data_to_remote_server`)

**Cel:** Otwiera lub ponownie wykorzystuje połączenie ze zdalnym serwerem i wysyła do niego dane tekstowe.

**Wartość:** Wymagana — `remote_server_url||data`

## Zamknij połączenie ze zdalnym serwerem (`close_remote_server_connection`)

**Cel:** Zamyka określone połączenie ze zdalnym serwerem na podstawie ID żądania.

**Wartość:** Wymagana — ID żądania, zwykle `$$request_id` z [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected)

## Zamknij wszystkie połączenia ze zdalnymi serwerami (`close_all_remote_server_connections`)

**Cel:** Zamyka wszystkie aktywne połączenia ze zdalnymi serwerami otwarte przez FancyMenu.

**Wartość:** Nie jest wymagana

## Otwórz URL w przeglądarce (`openlink`)

**Cel:** Przekazuje URL do domyślnej obsługi systemu operacyjnego bez monitu potwierdzającego FancyMenu

**Wartość:** Wymagana — `https://example.com`

Używaj zaufanych linków `https://`. FancyMenu nie wyświetla monitu o potwierdzenie przed przekazaniem URL do systemu operacyjnego.

## Kopiuj tekst do schowka (`copytoclipboard`)

**Cel:** Kopiuje tekst do schowka

**Wartość:** Wymagana — `text_to_copy`

## Wypisz do logu gry (`print_to_log`)

**Cel:** Zapisuje linię do logu gry

**Wartość:** Wymagana — `text_to_log`

## Ustaw wartość zmiennej (zmienna FM) (`set_variable`)

**Cel:** Przechowuje tekst w [FancyMenu variable](./variables)

**Wartość:** Wymagana — `variable_name:variable_value`

Pierwszy dwukropek oddziela nazwę od wartości. Kolejne dwukropki pozostają częścią wartości. Zmiany są zapisywane natychmiast.

## Wyczyść wszystkie zmienne (zmienna FM) (`clear_variables`)

**Cel:** Czyści wszystkie zapisane wartości [FancyMenu variable](./variables)

**Wartość:** Nie jest wymagana

## Wyślij żądanie HTTP (`send_http_request`)

**Cel:** Uruchamia w tle żądanie HTTP/HTTPS; może zapisać i/lub przechować odpowiedź w zmiennej

**Wartość:** Wymagana — konfiguracja żądania HTTP

| Ustawienie | Zachowanie |
|---|---|
| URL | Punkt końcowy HTTP lub HTTPS |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` lub `OPTIONS` |
| Body | Wysyłane dla metod innych niż `GET` i `HEAD` |
| Content type | Wartość `Content-Type` żądania |
| Timeout | Liczba sekund używana zarówno dla połączenia, jak i odczytu odpowiedzi |
| Log response | Odczytuje odpowiedź i zapisuje ją do logu |
| Response variable | Odczytuje odpowiedź i zapisuje ją po zakończeniu żądania |
| Single-line response | Usuwa podziały linii odpowiedzi przed zapisaniem |
| Authentication | Brak, Basic, Bearer lub klucz API |
| Headers | Opcjonalne własne nagłówki żądania |

Żądania działają asynchronicznie, więc następna akcja nie czeka. Treść odpowiedzi jest odczytywana tylko wtedy, gdy włączone jest logowanie lub skonfigurowano zmienną odpowiedzi; treści nieudanych odpowiedzi są odczytywane z odpowiedzi błędu. Nie zapisuj haseł ani tokenów dostępu w konfiguracji akcji.

## Zarządzaj pakietem zasobów (`manage_resource_pack`)

**Cel:** Włącza, wyłącza lub przełącza pakiet zasobów, z opcjonalnym przeładowaniem

**Wartość:** Wymagana — `pack_name_or_id|||MODE|||reload_bool`

Nazwy wyświetlane i wewnętrzne ID pakietów są dopasowywane bez rozróżniania wielkości liter. Pakiety oznaczone jako wymagane nie mogą zostać wyłączone.

## Przeładuj pakiety zasobów (`reload_resource_packs`)

**Cel:** Przeładowuje pakiety zasobów Minecrafta. Wbudowany pięciosekundowy cooldown ignoruje powtarzające się wyzwolenia w tym czasie, aby zapobiec spamowaniu przeładowania.

**Wartość:** Nie jest wymagana

## Przeładuj FancyMenu (`reloadmenu`)

**Cel:** Przeładowuje układy, [Custom GUIs](./custom-guis), [panoramy](./panoramas), [pokazy slajdów](./slideshows), ustawienia oraz zasoby zarządzane przez FancyMenu

**Wartość:** Nie jest wymagana

Nie przeładowuje to pakietów zasobów Minecrafta. Do tego użyj [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs).

> [!WARNING]
> Przeładowywanie jest kosztowne. Wyzwalaj je świadomie z przycisku, a nie z [Ticker](./elements#ticker) ani często uruchamianego [listener](./listeners).

## Przełącz animator elementu (`toggle_element_animator`)

**Cel:** Przełącza zapisany stan odtwarzania i resetuje odpowiadającą aktywną oś czasu Animatora

**Wartość:** Wymagana — `animator_identifier`

Zobacz [Element Animator](./element-animator), aby poznać konfigurację i szczegóły identyfikatora.

## Włącz animator elementu (`enable_element_animator`)

**Cel:** Włącza odtwarzanie; aktywna oś czasu Animatora resetuje się tylko wtedy, gdy stan zmienia się z wyłączonego na włączony

**Wartość:** Wymagana — `animator_identifier`

## Wyłącz animator elementu (`disable_element_animator`)

**Cel:** Wyłącza odtwarzanie i resetuje odpowiadającą aktywną oś czasu Animatora

**Wartość:** Wymagana — `animator_identifier`

## Zresetuj animator elementu (`reset_element_animator`)

**Cel:** Resetuje odpowiadającą aktywną oś czasu Animatora bez zmiany tego, czy odtwarzanie jest włączone

**Wartość:** Wymagana — `animator_identifier`

## Naśladuj przycisk Vanilla/Mod (`mimicbutton`)

**Cel:** Naśladuje akcję kliknięcia przycisku vanilla lub moda

**Wartość:** Wymagana — pełny [widget locator](./widget-locators), na przykład `example.menu.identifier:505280`

## Naśladuj keybind (`mimic_keybind`)

**Cel:** Uruchamia klawisz lub przycisk myszy Minecrafta, opcjonalnie przytrzymując go

**Wartość:** Wymagana — `keybind_id|||keep_pressed_bool|||duration_ms`

| Pole | Znaczenie |
|---|---|
| `keybind_id` | Identyfikator skrótu klawiszowego Minecrafta, taki jak `key.jump` |
| `keep_pressed_bool` | `true`, aby przytrzymać klawisz; `false` dla normalnego naciśnięcia |
| `duration_ms` | Czas przytrzymania, gdy `keep_pressed_bool` ma wartość `true`; domyślnie `1000` |

## Ustaw wartość pola tekstowego (`set_text_input_field_value`)

**Cel:** Ustawia wartość niestandardowego lub vanilla [Text Input Field](./elements#text-input-field) według identyfikatora elementu.

**Wartość:** Wymagana — `element_identifier|||new_value|||force_set_when_inactive`

Te trzy pola muszą być oddzielone separatorem potrójnego pionowego kreskowania `|||`. Ustaw `force_set_when_inactive` na `true`, aby zaktualizować także wyłączone pole wprowadzania; gdy ma wartość `false`, nieaktywne pola pozostają bez zmian.

## Utwórz plik w katalogu gry (`create_file_in_game_dir`)

**Cel:** Tworzy pusty plik względnie do aktywnego katalogu gry. Akceptuje prefiks `.minecraft/`, aby wskazać standardowy katalog Minecrafta (który może różnić się od bieżącej instancji).

**Wartość:** Wymagana — `file_path`

Przykład: `config/some_mod_folder/new_file.txt`. Brakujące katalogi nadrzędne są tworzone; istniejący plik pozostaje bez zmian.

## Usuń plik/folder w katalogu gry (`delete_file_in_game_dir`)

**Cel:** Usuwa plik lub rekurencyjnie usuwa folder względnie do aktywnego katalogu gry. Akceptuje `.minecraft/`, aby wskazać standardowy katalog Minecrafta. Dodaj `*`, aby usunąć **wszystkie pliki bezpośrednio wewnątrz** folderu (ignoruje podkatalogi i pozostawia folder).

**Wartość:** Wymagana — `target_path`

Na przykład `config/downloads/*` usuwa pliki znajdujące się bezpośrednio w `config/downloads/`, ale nie przechodzi do podkatalogów ani ich nie usuwa.

## Skopiuj plik/folder w katalogu gry (`copy_file_in_game_dir`)

**Cel:** Kopiuje w obrębie aktywnego katalogu gry; `.minecraft/` wskazuje standardowy katalog Minecrafta. Nazwany katalog jest kopiowany rekurencyjnie. Dodaj `*` do ścieżki **źródłowej**, aby skopiować tylko każdy bezpośredni plik podrzędny; celem musi być katalog i nie może używać `*`.

**Wartość:** Wymagana — `source||destination`

Na przykład `config/source/*||config/destination/` kopiuje tylko pliki znajdujące się bezpośrednio w `config/source/`. Przy źródle z wildcardem FancyMenu w razie potrzeby tworzy katalog docelowy, ale nie kopiuje żadnych podkatalogów źródłowych. Kopiowanie odmawia użycia istniejącego celu/kolidującego pliku zamiast go nadpisywać.

## Przenieś plik/folder w katalogu gry (`move_file_in_game_dir`)

**Cel:** Przenosi w obrębie aktywnego katalogu gry; `.minecraft/` wskazuje standardowy katalog Minecrafta. Dodaj `*` do ścieżki **źródłowej**, aby przenieść tylko każdy bezpośredni plik podrzędny; celem musi być katalog i nie może używać `*`.

**Wartość:** Wymagana — `source||destination`

Na przykład `config/source/*||config/destination/` przenosi tylko pliki znajdujące się bezpośrednio w `config/source/`. Przy źródle z wildcardem FancyMenu w razie potrzeby tworzy katalog docelowy, ale pozostawia podkatalogi źródłowe na miejscu. Przenoszenie odmawia użycia istniejącego celu/kolidującego pliku zamiast go nadpisywać.

## Zmień nazwę pliku/folderu w katalogu gry (`rename_file_in_game_dir`)

**Cel:** Zmienia nazwę pliku lub folderu w jego bieżącym katalogu nadrzędnym; `.minecraft/` wskazuje standardowy katalog Minecrafta. Zachowuje zawartość i odmawia użycia istniejącej nazwy docelowej.

**Wartość:** Wymagana — `path||new_name`

## Pobierz plik do katalogu gry (`download_file_to_game_dir`)

**Cel:** Pobiera w tle plik do katalogu względnego wobec aktywnego katalogu gry; `.minecraft/` wskazuje standardowy katalog Minecrafta.

**Wartość:** Wymagana — `url||target_folder`

Drugie pole to **katalog docelowy**, a nie pełna ścieżka pliku docelowego. FancyMenu tworzy katalog w razie potrzeby i określa nazwę pliku na podstawie nagłówka `Content-Disposition` odpowiedzi, a następnie przechodzi do ścieżki URL. Rozwiązana nazwa jest dekodowana z URL i oczyszczana przed użyciem; jeśli żadne źródło nie dostarczy użytecznej nazwy, FancyMenu generuje ją. Istniejący plik o tej samej nazwie zostaje nadpisany.

[**On File Downloaded via Action** listener](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) uruchamia się po udanych i nieudanych próbach pobierania i udostępnia URL, rozwiązaną ścieżkę docelową oraz stan powodzenia.

Po sukcesie `$$target_file_path` jest zapiszaną ścieżką pliku. W przypadku niepowodzenia może zawierać tylko katalog docelowy, ponieważ nie udało się ustalić końcowej nazwy pliku.

## Wyodrębnij plik ZIP w katalogu gry (`extract_zip_file_in_game_dir`)

**Cel:** Rozpakowuje ZIP do folderu docelowego w aktywnym katalogu gry lub standardowym katalogu `.minecraft`. Po zakończeniu uruchamia [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action).

**Wartość:** Wymagana — `source_zip_path||target_folder_path`

Istniejące pliki o pasujących nazwach są zastępowane. Rozpakowuj tylko zaufane pliki ZIP.

## Otwórz plik/folder w katalogu gry (`open_file_folder_in_game_dir`)

**Cel:** Otwiera plik lub folder za pomocą domyślnej aplikacji systemu operacyjnego. Ze względów bezpieczeństwa cel musi pozostać wewnątrz katalogu gry lub domyślnego katalogu `.minecraft`.

**Wartość:** Wymagana — `target_path`

## Zapisz do pliku w katalogu gry (`write_file_in_game_dir`)

**Cel:** Zapisuje lub dopisuje tekst względnie do aktywnego katalogu gry; `.minecraft/` wskazuje standardowy katalog Minecrafta. Tworzy plik i katalogi nadrzędne, jeśli ich brakuje. `\n` wstawia podziały linii; `append_bool=false` zastępuje istniejący plik.

**Wartość:** Wymagana — `path|||content|||append_bool`

## Wybierz plik z systemu (`select_file_to_game_dir`)

**Cel:** Otwiera natywny selektor plików i kopiuje wybrany plik do aktywnego katalogu gry lub do standardowego `.minecraft/`, gdy użyto prefiksu. Obsługuje filtry rozszerzeń, własną etykietę filtra oraz przełącznik nadpisywania.

**Wartość:** Wymagana — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` to pełna docelowa ścieżka pliku. Kilka rozszerzeń oddziel `;` lub `,`, na przykład `png;jpg`; pusta lista rozszerzeń pozwala na wszystkie pliki. Jeśli `overwrite_bool` ma wartość `false`, akcja kończy się niepowodzeniem zamiast zastąpić istniejący plik docelowy.

[**On File Selected** listener](./listeners#on-file-selected-file_selected_via_action) uruchamia się, gdy plik zostanie skopiowany, wybór zostanie anulowany albo wybór się nie powiedzie. Udostępnia wybraną ścieżkę, rozwiązaną ścieżkę docelową, stany powodzenia/anulowania oraz powód niepowodzenia.

## Pokaż toast (`show_toast`)

**Cel:** Wyświetla konfigurowalne powiadomienie toast

**Wartość:** Wymagana — konfiguracja JSON toast

Edytor zapisuje tę akcję jako JSON. Zalecane jest korzystanie z okna konfiguracji zamiast ręcznej edycji wartości.

| Pole | Znaczenie |
|---|---|
| `width` | Ograniczane do `120`–`320` pikseli |
| `durationMs` | Ograniczane do `1000`–`600000` milisekund |
| `title` | Zwykły tekst, serializowany komponent tekstowy Minecrafta albo puste |
| `message` | Zwykły tekst, serializowany komponent tekstowy albo puste |
| `iconSource` | Opcjonalne [image source](./resources) |
| `backgroundSource` | Opcjonalne [image source](./resources) |

## Uruchom scheduler (`start_scheduler`)

**Cel:** Uruchamia scheduler według jego ID.

**Wartość:** Wymagana — `scheduler_id`

Zobacz [Schedulers](./schedulers), aby dowiedzieć się, jak tworzyć i zarządzać ID schedulerów.

## Zatrzymaj scheduler (`stop_scheduler`)

**Cel:** Zatrzymuje scheduler według jego ID.

**Wartość:** Wymagana — `scheduler_id`

## Ustaw opcję Minecrafta (`edit_minecraft_option`)

**Cel:** Edytuje opcję konfiguracji Minecrafta

**Wartość:** Wymagana — `option_name:set_to_value`
