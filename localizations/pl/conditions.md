---
title: Warunki (wymagania)
description: Jak używać wymagań ładowania.
---

# Wymagania

Wymagania (w niektórych menu nazywane **Loading Requirements**) pokazują lub ukrywają zawartość na podstawie warunków, takich jak stan po najechaniu, rozmiar okna lub to, czy świat jest załadowany.

Możesz używać ich na [elementach](./elements), całych układach oraz [skryptach akcji](./action-scripts).

# Dodawanie wymagań do elementów

Aby dodać wymagania do elementu, kliknij go prawym przyciskiem myszy i wybierz **Loading Requirements**.

Wymagania są sprawdzane, gdy menu jest otwarte, więc elementy aktualizują się po zmianie warunku.

# Wymagania dla całego układu

Możesz także zmieniać widoczność całych układów, klikając prawym przyciskiem myszy **tło edytora**, a następnie **Loading Requirements [Layout-Wide]**.

Gdy wynik wymagań dla całego układu się zmieni, FancyMenu przebudowuje aktualny ekran i stosuje układy, których wymagania są teraz spełnione.

# Skrypty akcji

Wymagania mogą być również używane w skryptach akcji.
Możesz dodać je w ekranie edytora skryptu akcji i używać ich do wykonywania określonych akcji tylko wtedy, gdy warunek wymagania jest spełniony.

# Łączenie wymagań

- Wymagania poza grupami używają operatora **AND**, więc wszystkie muszą zostać spełnione.
- Wewnątrz grupy wybierz **AND** albo **OR**.
- Użyj **IF NOT**, aby odwrócić jedno wymaganie.

Te zasady są takie same dla elementów, układów i skryptów akcji.

# Wartości wymagań

W przypadku wymagań, które potrzebują wartości, użyj **Edit Requirement Value** i postępuj zgodnie z opisem pokazanym w edytorze. Niektóre pola obsługują uzupełnianie za pomocą **TAB**.

Jeśli zaimportowane wymaganie przestanie działać po zmianie FancyMenu lub dodatków, edytuj je w ekranie wymagań i sprawdź `logs/latest.log` pod kątem błędów.

Edytor wymagań obsługuje menu kontekstowe pod prawym przyciskiem myszy, nawigację klawiaturą, wyszukiwanie, cofanie/ponawianie (`Ctrl/Command + Z` / `Ctrl/Command + Y`) oraz `Ctrl/Command + S` do zapisu.

# Wymagania — szczegóły

Ta sekcja zawiera wbudowane wymagania FancyMenu.

## Czy element jest pod kursorem (`fancymenu_visibility_requirement_is_element_hovered`)

**Cel:** Sprawdza, czy określony element jest pod kursorem myszy.

**Wartość:** Wymagana — [Identyfikator elementu](./element-identifiers) elementu docelowego (np. `some_element_ID`).

## Czy element ma fokus (`is_element_focused`)

**Cel:** Sprawdza, czy określony element ma obecnie fokus klawiatury (na przykład pole tekstowe lub przycisk z fokusem).

**Wartość:** Wymagana — ID elementu docelowego (to samo ID widoczne w edytorze)

> [!NOTE]
> Fokus i najechanie to różne stany. Element może zachować wygląd fokusu po opuszczeniu go przez wskaźnik; kliknięcie lub nawigacja klawiaturą może nadać mu fokus.

## Czy dowolny element jest pod kursorem (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Cel:** Sprawdza widoczne/renderowalne elementy w bieżącej aktywnej warstwie personalizacji, w tym elementy pochodzące ze stosowanych układów.

**Wartość:** Niewymagana

## Czy dowolny przycisk jest pod kursorem (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Cel:** Sprawdza, czy dowolny widoczny/renderowalny przycisk vanilla lub niestandardowy w bieżącej aktywnej warstwie personalizacji jest pod kursorem, w tym przyciski pochodzące ze stosowanych układów.

**Wartość:** Niewymagana

## Czy układ jest włączony (`fancymenu_visibility_requirement_is_layout_enabled`)

**Cel:** Sprawdza, czy określony układ jest obecnie włączony.

**Wartość:** Wymagana — Nazwa układu (np. `my_cool_main_menu_layout`)

## Czy działa scheduler (`fancymenu_visibility_requirement_is_scheduler_running`)

**Cel:** Sprawdza, czy [scheduler](./schedulers) jest obecnie uruchomiony.

**Wartość:** Wymagana — ID schedulera (np. `my_scheduler`)

## Czy skala GUI (`fancymenu_loading_requirement_is_gui_scale`)

**Cel:** Sprawdza, czy bieżąca skala GUI spełnia określone warunki.

**Wartość:** Wymagana — Użyj liczby dla równości, `>` dla większe niż lub `<` dla mniejsze niż.

Wiele warunków oddzielonych przecinkami jest łączonych operatorem AND. Na przykład `>1,<4` przejdzie tylko wtedy, gdy skala GUI jest większa niż `1` i mniejsza niż `4`.

## Czy przycisk jest aktywny (`fancymenu_visibility_requirement_is_button_active`)

**Cel:** Sprawdza, czy określony przycisk jest aktywny (klikalny).

**Wartość:** Wymagana — ID elementu docelowego przycisku (np. "some_element_ID")

## Czy tytuł ekranu (`is_menu_title`)

**Cel:** Sprawdza, czy WYŚWIETLANY tytuł ekranu pasuje do określonego tekstu lub klucza lokalizacji. Sprawdza wyłącznie nazwę wyświetlaną/tytuł ekranu, np. „Options” lub „Pause”. NIE sprawdza identyfikatora menu/ekranu (takiego jak `title_screen`)!

**Wartość:** Wymagana — Dokładny tekst tytułu lub klucz lokalizacji ekranu

## Czy klawisz jest wciśnięty (`is_key_pressed`)

**Cel:** Sprawdza, czy określony klawisz klawiatury jest obecnie wciśnięty.

**Wartość:** Wymagana — Kod klawisza docelowego. Wybierany przez interfejs użytkownika podczas edycji wartości wymagania.

## Czy otwarty jest jakiś ekran (`is_any_screen_open`)

**Cel:** Sprawdza, czy jakikolwiek ekran/menu jest obecnie otwarty (zwraca false, jeśli żaden ekran nie jest wyświetlany).

**Wartość:** Niewymagana

## Czy włączona jest nakładka debugowania MC (`is_debug_overlay_enabled`)

**Cel:** Sprawdza, czy nakładka debugowania F3 jest obecnie widoczna.

**Wartość:** Niewymagana

## Czy aktywny typ kursora (`is_active_cursor_type`)

**Cel:** Sprawdza, czy obecnie aktywny typ kursora FancyMenu odpowiada określonemu standardowemu typowi kursora.

**Wartość:** Wymagana — Typ kursora: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` lub `not_allowed`

## Czy widoczny jest pasek menu personalizacji (`is_customization_menu_bar_visible`)

**Cel:** Sprawdza, czy pasek menu personalizacji FancyMenu jest obecnie widoczny.

**Wartość:** Niewymagana

## Czy włączony jest tryb modpacka (`is_modpack_mode_enabled`)

**Cel:** Sprawdza, czy tryb Modpack Mode FancyMenu jest włączony.

**Wartość:** Niewymagana

## Czy przycisk myszy jest wciśnięty (`mouse_click`)

**Cel:** Zwraca true, gdy określony przycisk myszy jest przytrzymywany. To nie jest jednorazowe zdarzenie kliknięcia; użyj [**On Mouse Button Clicked** listenera](./listeners#on-mouse-button-clicked-mouse_button_clicked), gdy akcja ma być uruchamiana raz na kliknięcie.

**Wartość:** Wymagana — `left` lub `right`, aby wskazać, który przycisk myszy sprawdzić

## Czy jest pełny ekran (`fancymenu_loading_requirement_is_fullscreen`)

**Cel:** Sprawdza, czy gra jest obecnie w trybie pełnoekranowym.

**Wartość:** Niewymagana

## Czy szerokość okna (`fancymenu_loading_requirement_is_window_width`)

**Cel:** Sprawdza, czy szerokość okna gry odpowiada określonym wartościom.

**Wartość:** Wymagana — Szerokość okna w pikselach (np. "1920"). Można podać wiele wartości, oddzielając je przecinkami.

## Czy wysokość okna (`fancymenu_loading_requirement_is_window_height`)

**Cel:** Sprawdza, czy wysokość okna gry odpowiada określonym wartościom.

**Wartość:** Wymagana — Wysokość okna w pikselach (np. "1080"). Można podać wiele wartości, oddzielając je przecinkami.

## Czy szerokość okna większa niż (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Cel:** Sprawdza, czy szerokość okna gry jest większa niż określona wartość.

**Wartość:** Wymagana — Szerokość okna w pikselach (np. "1920")

## Czy wysokość okna większa niż (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Cel:** Sprawdza, czy wysokość okna gry jest większa niż określona wartość.

**Wartość:** Wymagana — Wysokość okna w pikselach (np. "1080")

## Czy multiplayer (`fancymenu_loading_requirement_is_multiplayer`)

**Cel:** Sprawdza, czy gracz aktualnie znajduje się w świecie wieloosobowym.

**Wartość:** Niewymagana

## Czy singleplayer (`fancymenu_loading_requirement_is_singpleplayer`)

**Cel:** Sprawdza, czy gracz aktualnie znajduje się w świecie jednoosobowym.

**Wartość:** Niewymagana

## Czy świat jest załadowany (`fancymenu_loading_requirement_is_world_loaded`)

**Cel:** Sprawdza, czy jakikolwiek świat jest obecnie załadowany.

**Wartość:** Niewymagana

## Czy tryb przygodowy (`fancymenu_visibility_requirement_is_adventure`)

**Cel:** Sprawdza, czy gracz jest obecnie w trybie gry przygodowym.

**Wartość:** Niewymagana

## Czy tryb kreatywny (`fancymenu_visibility_requirement_is_creative`)

**Cel:** Sprawdza, czy gracz jest obecnie w trybie gry kreatywnym.

**Wartość:** Niewymagana

## Czy tryb widza (`fancymenu_visibility_requirement_is_spectator`)

**Cel:** Sprawdza, czy gracz jest obecnie w trybie gry widza.

**Wartość:** Niewymagana

## Czy tryb przetrwania (`fancymenu_visibility_requirement_is_survival`)

**Cel:** Sprawdza, czy gracz jest obecnie w trybie gry przetrwania.

**Wartość:** Niewymagana

## Czy tryb gry (`is_gamemode`)

**Cel:** Sprawdza, czy gracz jest w określonym trybie gry.

**Wartość:** Wymagana — Nazwa trybu gry (np. "creative", "survival", "adventure", "spectator")

## Czy poziom trudności (`is_difficulty`)

**Cel:** Sprawdza, czy aktualny poziom trudności gry odpowiada określonej wartości.

**Wartość:** Wymagana — Nazwa poziomu trudności (np. "peaceful", "easy", "normal", "hard")

## Czy hardcore (`is_hardcore`)

**Cel:** Sprawdza, czy aktualnie załadowany świat jest w trybie hardcore.

**Wartość:** Niewymagana

## Czy perspektywa kamery (`is_camera_perspective`)

**Cel:** Sprawdza, czy bieżąca perspektywa kamery odpowiada określonej perspektywie.

**Wartość:** Wymagana — `first_person`, `third_person_back` lub `third_person_front`

## Czy pada deszcz (`is_raining`)

**Cel:** Sprawdza, czy aktualnie pada deszcz w lokalizacji gracza.

**Wartość:** Niewymagana

## Czy grzmi (`is_thundering`)

**Cel:** Sprawdza, czy w świecie gracza aktualnie trwa burza z piorunami.

**Wartość:** Niewymagana

## Czy pogoda jest bezchmurna (`is_clear_weather`)

**Cel:** Sprawdza, czy pogoda jest obecnie bezchmurna (nie pada deszcz ani nie grzmi).

**Wartość:** Niewymagana

## Czy pada śnieg (`is_snowing`)

**Cel:** Sprawdza, czy w lokalizacji gracza aktualnie pada śnieg.

**Wartość:** Niewymagana

## Czy gracz biegnie (`is_player_running`)

**Cel:** Sprawdza, czy gracz aktualnie sprintuje.

**Wartość:** Niewymagana

## Czy gracz się skrada (`is_player_sneaking`)

**Cel:** Sprawdza, czy gracz aktualnie skrada się/kuca.

**Wartość:** Niewymagana

## Czy gracz używa przedmiotu (`is_player_using_item`)

**Cel:** Sprawdza, czy gracz aktualnie używa przedmiotu.

**Wartość:** Niewymagana

## Czy gracz pływa (`is_player_swimming`)

**Cel:** Sprawdza, czy gracz aktualnie pływa.

**Wartość:** Niewymagana

## Czy gracz skacze lub spada (`is_player_jumping`)

**Cel:** Zwraca true, gdy gracz jest w powietrzu w normalnym stanie skoku lub spadania. Wyklucza pływanie, płyny, lot na elytrze, spanie, wizualne pływanie i czołganie.

**Wartość:** Niewymagana

## Czy gracz jest pod wodą (`is_player_under_water`)

**Cel:** Sprawdza, czy gracz jest całkowicie pod wodą.

**Wartość:** Niewymagana

## Czy gracz jest w wodzie (`is_player_in_water`)

**Cel:** Sprawdza, czy gracz znajduje się w wodzie (może być częściowo zanurzony).

**Wartość:** Niewymagana

## Czy gracz jest w lawie (`is_player_in_lava`)

**Cel:** Sprawdza, czy gracz znajduje się w lawie.

**Wartość:** Niewymagana

## Czy gracz jest w płynie (`is_player_in_fluid`)

**Cel:** Sprawdza, czy gracz znajduje się w jakimkolwiek płynie (woda, lawa itp.).

**Wartość:** Niewymagana

## Czy gracz dosiada encji/pojazdu (`is_player_riding_entity`)

**Cel:** Sprawdza, czy gracz dosiada dowolnej encji.

**Wartość:** Niewymagana

## Czy gracz dosiada skaczącej encji (`is_player_riding_jumpable_entity`)

**Cel:** Sprawdza, czy gracz dosiada encji, która może skakać (np. konia).

**Wartość:** Niewymagana

## Czy gracz dosiada encji z punktami życia (`is_player_riding_entity_with_health`)

**Cel:** Sprawdza, czy gracz dosiada żywej encji z punktami zdrowia (np. zwierząt, nie łodzi).

**Wartość:** Niewymagana

## Czy gracz jest w śnieżnym pyle (`is_player_in_powder_snow`)

**Cel:** Sprawdza, czy gracz aktualnie znajduje się w śnieżnym pyle.

**Wartość:** Niewymagana

## Czy gracz był w śnieżnym pyle (`was_player_in_powder_snow`)

**Cel:** Sprawdza, czy gracz był w śnieżnym pyle (używane dla efektów utrzymujących się po wyjściu).

**Wartość:** Niewymagana

## Czy gracz nosi dynię (`is_player_wearing_pumpkin`)

**Cel:** Sprawdza, czy gracz ma na głowie wydrążoną dynię.

**Wartość:** Niewymagana

## Czy gracz lata na elytrze (`is_player_flying_with_elytra`)

**Cel:** Sprawdza, czy gracz aktualnie lata na elytrze.

**Wartość:** Niewymagana

## Czy gracz lata w trybie kreatywnym (`is_player_creative_flying`)

**Cel:** Sprawdza, czy gracz lata w trybie kreatywnym.

**Wartość:** Niewymagana

## Czy gracz ma serca absorpcji (`has_player_absorption_hearts`)

**Cel:** Sprawdza, czy gracz ma jakiekolwiek serca absorpcji (złote serca).

**Wartość:** Niewymagana

## Czy gracz jest osłabiony Witherem (`is_player_withered`)

**Cel:** Sprawdza, czy gracz jest pod wpływem efektu Wither.

**Wartość:** Niewymagana

## Czy gracz jest całkowicie zamarznięty (`is_player_fully_frozen`)

**Cel:** Sprawdza, czy gracz jest całkowicie zamarznięty (zwykle od śnieżnego pyłu).

**Wartość:** Niewymagana

## Czy gracz jest zatruty (`is_player_poisoned`)

**Cel:** Sprawdza, czy gracz jest pod wpływem efektu trucizny.

**Wartość:** Niewymagana

## Czy gracz jest w biomie (`is_player_in_biome`)

**Cel:** Sprawdza, czy gracz znajduje się w określonym biomie.

**Wartość:** Wymagana — Identyfikator biomu (np. `minecraft:birch_forest`)

## Czy gracz jest w wymiarze (`is_player_in_dimension`)

**Cel:** Sprawdza, czy gracz znajduje się w określonym wymiarze.

**Wartość:** Wymagana — Identyfikator wymiaru (np. `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Czy gracz jest w strukturze (`is_player_in_structure`)

**Cel:** Sprawdza, czy gracz aktualnie znajduje się wewnątrz określonej struktury. W przypadku światów serwerowych wymagany jest FancyMenu na serwerze.

**Wartość:** Wymagana — Identyfikator struktury (np. `minecraft:village`)

## Czy encja jest w pobliżu (`is_entity_nearby`)

**Cel:** Sprawdza, czy określony typ encji znajduje się w pewnym promieniu od gracza.

**Wartość:** Wymagana — Format: "radius:entity_id" (np. `10:minecraft:pig` - sprawdza świnie w promieniu 10 bloków)

## Czy efekt jest aktywny (`is_effect_active`)

**Cel:** Sprawdza, czy na graczu jest aktywny określony efekt mikstury.

**Wartość:** Wymagana — Identyfikator efektu (np. `minecraft:speed`, `minecraft:strength`)

## Czy aktywny jest dowolny efekt (`is_any_effect_active`)

**Cel:** Sprawdza, czy gracz ma aktywny jakikolwiek efekt mikstury.

**Wartość:** Niewymagana

## Czy gracz jest leworęczny (`is_left_handed`)

**Cel:** Sprawdza, czy gracz ma w opcjach gry ustawiony tryb leworęczny.

**Wartość:** Niewymagana

## Czy slot ekwipunku jest zajęty (`is_inventory_slot_filled`)

**Cel:** Sprawdza, czy określony slot ekwipunku zawiera przedmiot.

**Wartość:** Wymagana — Numer slotu (0-35 dla głównego ekwipunku, sloty 0-8 to pasek szybkiego dostępu)

## Czy przedmiot jest pod kursorem w ekwipunku (`is_item_hovered_in_inventory`)

**Cel:** Sprawdza, czy kursor znajduje się nad jakimkolwiek przedmiotem na ekranie ekwipunku.

**Wartość:** Niewymagana

## Czy kursor trzyma przedmiot z ekwipunku (`is_cursor_holding_inventory_item`)

**Cel:** Sprawdza, czy kursor aktualnie trzyma stos przedmiotów z ekwipunku.

**Wartość:** Niewymagana

## Czy wybrany jest slot paska szybkiego dostępu (`is_hotbar_slot_active`)

**Cel:** Sprawdza, czy określony slot paska szybkiego dostępu jest obecnie wybrany.

**Wartość:** Wymagana — Numer slotu paska szybkiego dostępu (0-8)

## Czy gracz ma poziom uprawnień (`fancymenu_loading_requirement_has_player_permission_level`)

**Cel:** Sprawdza, czy gracz ma co najmniej określony poziom uprawnień/OP w bieżącym świecie lub na serwerze.

**Wartość:** Wymagana — Numer poziomu uprawnień (0-4, gdzie 4 to operator serwera)

## Czy osłabiona jest siła ataku (`is_attack_strength_weakened`)

**Cel:** Sprawdza, czy siła ataku gracza jest obecnie osłabiona (nie jest w pełni naładowana).

**Wartość:** Niewymagana

## Czy czas rzeczywisty: dzień (`fancymenu_visibility_requirement_is_realtime_day`)

**Cel:** Sprawdza, czy bieżący rzeczywisty dzień miesiąca odpowiada określonej wartości.

**Wartość:** Wymagana — Numer dnia (1-31). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: godzina (`fancymenu_visibility_requirement_is_realtime_hour`)

**Cel:** Sprawdza, czy bieżąca rzeczywista godzina odpowiada określonej wartości.

**Wartość:** Wymagana — Godzina w formacie 24-godzinnym (0-23). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: minuta (`fancymenu_visibility_requirement_is_realtime_minute`)

**Cel:** Sprawdza, czy bieżąca rzeczywista minuta odpowiada określonej wartości.

**Wartość:** Wymagana — Minuta (0-59). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: miesiąc (`fancymenu_visibility_requirement_is_realtime_month`)

**Cel:** Sprawdza, czy bieżący rzeczywisty miesiąc odpowiada określonej wartości.

**Wartość:** Wymagana — Numer miesiąca (1-12, gdzie 1 to styczeń). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: sekunda (`fancymenu_visibility_requirement_is_realtime_second`)

**Cel:** Sprawdza, czy bieżąca rzeczywista sekunda odpowiada określonej wartości.

**Wartość:** Wymagana — Sekunda (0-59). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: dzień tygodnia (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Cel:** Sprawdza, czy bieżący rzeczywisty dzień tygodnia odpowiada określonej wartości.

**Wartość:** Wymagana — Dzień tygodnia jako liczba (1-7, gdzie 1 to niedziela). Można podać wiele wartości, oddzielając je przecinkami.

## Czy czas rzeczywisty: rok (`fancymenu_visibility_requirement_is_realtime_year`)

**Cel:** Sprawdza, czy bieżący rzeczywisty rok odpowiada określonej wartości.

**Wartość:** Wymagana — Pełny rok (np. "2023"). Można podać wiele wartości, oddzielając je przecinkami.

## Czy plik/folder istnieje (`fancymenu_loading_requirement_file_exists`)

**Cel:** Sprawdza, czy plik lub katalog istnieje.

**Wartość:** Wymagana — Ścieżka względna względem aktywnego katalogu gry albo ścieżka zaczynająca się od `.minecraft/` dla standardowego katalogu Minecrafta. Za istniejące uznawane są zarówno pliki, jak i katalogi.

## Czy system operacyjny to Linux (`fancymenu_loading_requirement_is_os_linux`)

**Cel:** Sprawdza, czy bieżąca platforma nie jest Windows ani macOS. Zwykle odpowiada to środowiskom Linux.

**Wartość:** Niewymagana

## Czy system operacyjny to macOS (`fancymenu_loading_requirement_is_os_macos`)

**Cel:** Sprawdza, czy system operacyjny to macOS.

**Wartość:** Niewymagana

## Czy system operacyjny to Windows (`fancymenu_loading_requirement_is_os_windows`)

**Cel:** Sprawdza, czy system operacyjny to Windows.

**Wartość:** Niewymagana

## Czy dostępne jest połączenie internetowe (`is_internet_connection_available`)

**Cel:** Sprawdza, czy dostępne jest aktywne połączenie z internetem.

**Wartość:** Niewymagana

## Czy język gry (`fancymenu_loading_requirement_is_language`)

**Cel:** Sprawdza, czy bieżący język gry odpowiada określonej wartości.

**Wartość:** Wymagana — Kod języka (np. `en_us` dla angielskiego)

## Czy mod jest załadowany (`fancymenu_loading_requirement_is_mod_loaded`)

**Cel:** Sprawdza, czy określony mod jest załadowany.

**Wartość:** Wymagana — ID modu (np. `fancymenu`, `jei`). Możesz także sprawdzić OptiFine za pomocą `optifine`. Obsługiwanych jest wiele identyfikatorów modów oddzielonych przecinkami; wszystkie wymienione mody muszą być załadowane.

## Czy MCEF jest załadowany (`is_mcef_loaded`)

**Cel:** Sprawdza, czy MCEF (Minecraft Chromium Embedded Framework) jest zainstalowany i zainicjalizowany. MCEF jest wymagany dla [elementu Browser](./elements#browser) oraz [przestarzałych typów wideo opartych na MCEF](./video#requirements); [natywne funkcje wideo](./video) używają Watermedia.

**Wartość:** Niewymagana

## Czy liczba (`fancymenu_visibility_requirement_is_number`)

**Cel:** Zapewnia zaawansowane porównanie liczb z różnymi trybami porównania.

**Wartość:** Wymagana — Złożony format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`, gdzie `comparison_mode` może być `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` lub `smaller-than-or-equals`

## Czy tekst (`fancymenu_visibility_requirement_is_text`)

**Cel:** Zapewnia zaawansowane porównanie tekstu z różnymi trybami porównania.

**Wartość:** Wymagana — Złożony format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`, gdzie `comparison_mode` może być `equals`, `contains`, `starts-with` lub `ends-with`

## Czy IP serwera (`fancymenu_visibility_requirement_is_server_ip`)

**Cel:** Sprawdza, czy bieżący adres IP serwera odpowiada określonej wartości.

**Wartość:** Wymagana — Adres IP serwera (z portem lub bez)

## Czy serwer jest online (`fancymenu_loading_requirement_is_server_online`)

**Cel:** Sprawdza, czy określony serwer jest online i osiągalny.

**Wartość:** Wymagana — Adres IP serwera (z portem lub bez)

## Czy paczka zasobów jest włączona (`is_resource_pack_enabled`)

**Cel:** Sprawdza, czy określona paczka zasobów jest obecnie wybrana/aktywna.

**Wartość:** Wymagana — Tytuł paczki zasobów lub ID paczki (np. `Programmer Art` albo ID paczki)

## Czy wartość zmiennej (zmienna FM) (`fancymenu_visibility_requirement_is_variable_value`)

**Cel:** Sprawdza, czy zmienna FancyMenu ma określoną wartość.

**Wartość:** Wymagana — Format: "nazwa_zmiennej:oczekiwana_wartość"

## Tylko raz na sesję (`once_per_session`)

**Cel:** Każda skonfigurowana instancja zwraca true raz na sesję gry. Poszczególne instancje są śledzone niezależnie.

**Wartość:** Niewymagana
