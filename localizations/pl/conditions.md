---
title: Warunki (wymagania)
description: Jak używać wymagań ładowania.
---
# Wymagania

Wymagania (w niektórych menu nazywane **wymaganiami ładowania**) pokazują lub ukrywają zawartość na podstawie warunków, takich jak stan wskazania kursorem, rozmiar okna czy informacja, czy świat jest załadowany.

Możesz używać ich na [elementach](./elements), w całych układach oraz w [skryptach akcji](./action-scripts).

# Dodawanie wymagań do elementów

Aby dodać wymagania do elementu, kliknij go prawym przyciskiem myszy i wybierz **Wymagania ładowania**.

Wymagania są sprawdzane, gdy menu jest otwarte, dlatego elementy aktualizują się po zmianie warunku.

# Wymagania dotyczące całego układu

Możesz także zmieniać widoczność całych układów, klikając prawym przyciskiem myszy **tło edytora**, a następnie wybierając **Wymagania ładowania [dla całego układu]**.

Gdy wynik wymagania dotyczącego całego układu się zmieni, FancyMenu przebuduje bieżący ekran i zastosuje układy, których wymagania są teraz spełnione.

# Skrypty akcji

Wymagań można również używać w skryptach akcji.
Możesz dodawać je na ekranie edytora skryptów akcji i używać ich do wykonywania określonych działań tylko wtedy, gdy warunek wymagania jest spełniony.

# Łączenie wymagań

- Wymagania znajdujące się poza grupami używają operatora **AND**, więc wszystkie muszą być spełnione.
- W grupie wybierz **AND** lub **OR**.
- Użyj **IF NOT**, aby odwrócić wynik jednego wymagania.

Te zasady są takie same dla elementów, układów i skryptów akcji.

# Wartości wymagań

W przypadku wymagań wymagających wartości użyj opcji **Edytuj wartość wymagania** i postępuj zgodnie z opisem wyświetlanym w edytorze. Niektóre pola obsługują autouzupełnianie za pomocą klawisza **TAB**.

Jeśli zaimportowane wymaganie przestanie działać po zmianie FancyMenu lub dodatków, edytuj je na ekranie wymagań i sprawdź plik `logs/latest.log` pod kątem błędów.

Edytor wymagań obsługuje menu kontekstowe otwierane prawym przyciskiem myszy, nawigację za pomocą klawiatury, wyszukiwanie, cofanie/ponawianie (`Ctrl/Command + Z` / `Ctrl/Command + Y`) oraz zapis za pomocą `Ctrl/Command + S`.

# Szczegółowa lista wymagań

W tej sekcji wymieniono wbudowane wymagania FancyMenu.

## Czy wskazano element (`fancymenu_visibility_requirement_is_element_hovered`)

**Cel:** Sprawdza, czy kursor myszy wskazuje konkretny element.

**Wartość:** Wymagana — [identyfikator elementu](./element-identifiers) docelowego elementu (np. `some_element_ID`).

## Czy element ma fokus (`is_element_focused`)

**Cel:** Sprawdza, czy konkretny element ma obecnie fokus klawiatury (np. pole tekstowe lub przycisk z fokusem).

**Wartość:** Wymagana — identyfikator docelowego elementu (ten sam identyfikator, który jest wyświetlany w edytorze)

> [!NOTE]
> Fokus i wskazanie kursorem to różne stany. Element może zachować wygląd elementu z fokusem po przesunięciu nad nim kursora; fokus można uzyskać przez kliknięcie lub nawigację klawiaturą.

## Czy wskazano dowolny element (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Cel:** Sprawdza widoczne/renderowalne elementy w bieżącej aktywnej warstwie personalizacji, w tym elementy dodane przez nakładane układy.

**Wartość:** Niewymagana

## Czy wskazano dowolny przycisk (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Cel:** Sprawdza, czy wskazano dowolny widoczny/renderowalny waniliowy lub niestandardowy przycisk w bieżącej aktywnej warstwie personalizacji, w tym przyciski dodane przez nakładane układy.

**Wartość:** Niewymagana

## Czy układ jest włączony (`fancymenu_visibility_requirement_is_layout_enabled`)

**Cel:** Sprawdza, czy konkretny układ jest obecnie włączony.

**Wartość:** Wymagana — nazwa układu (np. `my_cool_main_menu_layout`)

## Czy harmonogram działa (`fancymenu_visibility_requirement_is_scheduler_running`)

**Cel:** Sprawdza, czy [harmonogram](./schedulers) jest obecnie uruchomiony.

**Wartość:** Wymagana — identyfikator harmonogramu (np. `my_scheduler`)

## Czy skala interfejsu jest równa (`fancymenu_loading_requirement_is_gui_scale`)

**Cel:** Sprawdza, czy bieżąca skala interfejsu spełnia określone warunki.

**Wartość:** Wymagana — użyj liczby dla równości, `>` dla wartości większej lub `<` dla wartości mniejszej.

Wiele warunków oddzielonych przecinkami jest łączonych operatorem AND. Na przykład `>1,<4` jest spełnione tylko wtedy, gdy skala interfejsu jest większa niż `1` i mniejsza niż `4`.

## Czy przycisk jest aktywny (`fancymenu_visibility_requirement_is_button_active`)

**Cel:** Sprawdza, czy konkretny przycisk jest aktywny (można go kliknąć).

**Wartość:** Wymagana — identyfikator docelowego przycisku (np. "some_element_ID")

## Czy tytuł ekranu jest zgodny (`is_menu_title`)

**Cel:** Sprawdza, czy tytuł WYŚWIETLANY na ekranie odpowiada określonemu tekstowi lub kluczowi lokalizacji. Sprawdzana jest tylko wyświetlana nazwa/tytuł ekranu, np. „Opcje” lub „Pauza”. NIE jest sprawdzany identyfikator menu/ekranu, taki jak `title_screen`!

**Wartość:** Wymagana — dokładny tekst tytułu lub klucz lokalizacji ekranu

## Czy klawisz jest wciśnięty (`is_key_pressed`)

**Cel:** Sprawdza, czy konkretny klawisz klawiatury jest obecnie wciśnięty.

**Wartość:** Wymagana — kod docelowego klawisza. Wybiera się go w interfejsie podczas edycji wartości wymagania.

## Czy dowolny ekran jest otwarty (`is_any_screen_open`)

**Cel:** Sprawdza, czy dowolny ekran/menu jest obecnie otwarty (zwraca false, jeśli żaden ekran nie jest wyświetlany).

**Wartość:** Niewymagana

## Czy nakładka debugowania MC jest włączona (`is_debug_overlay_enabled`)

**Cel:** Sprawdza, czy nakładka debugowania F3 jest obecnie widoczna.

**Wartość:** Niewymagana

## Czy aktywny jest typ kursora (`is_active_cursor_type`)

**Cel:** Sprawdza, czy aktualnie aktywny typ kursora FancyMenu odpowiada określonemu standardowemu typowi kursora.

**Wartość:** Wymagana — typ kursora: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` lub `not_allowed`

## Czy pasek menu personalizacji jest widoczny (`is_customization_menu_bar_visible`)

**Cel:** Sprawdza, czy pasek menu personalizacji FancyMenu jest obecnie widoczny.

**Wartość:** Niewymagana

## Czy tryb modpacka jest włączony (`is_modpack_mode_enabled`)

**Cel:** Sprawdza, czy tryb modpacka FancyMenu jest włączony.

**Wartość:** Niewymagana

## Czy przycisk myszy jest wciśnięty (`mouse_click`)

**Cel:** Zwraca true, gdy konkretny przycisk myszy jest przytrzymywany. Nie jest to jednorazowe zdarzenie kliknięcia — gdy akcja ma wykonać się raz na kliknięcie, użyj [nasłuchiwacza **Po kliknięciu przycisku myszy**](./listeners#on-mouse-button-clicked-mouse_button_clicked).

**Wartość:** Wymagana — `left` lub `right`, aby określić sprawdzany przycisk myszy

## Czy gra działa w trybie pełnoekranowym (`fancymenu_loading_requirement_is_fullscreen`)

**Cel:** Sprawdza, czy gra jest obecnie uruchomiona w trybie pełnoekranowym.

**Wartość:** Niewymagana

## Czy szerokość okna jest równa (`fancymenu_loading_requirement_is_window_width`)

**Cel:** Sprawdza, czy szerokość okna gry odpowiada określonym wartościom.

**Wartość:** Wymagana — szerokość okna w pikselach (np. „1920”). Można podać wiele wartości, oddzielając je przecinkami.

## Czy wysokość okna jest równa (`fancymenu_loading_requirement_is_window_height`)

**Cel:** Sprawdza, czy wysokość okna gry odpowiada określonym wartościom.

**Wartość:** Wymagana — wysokość okna w pikselach (np. „1080”). Można podać wiele wartości, oddzielając je przecinkami.

## Czy szerokość okna jest większa niż (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Cel:** Sprawdza, czy szerokość okna gry jest większa od określonej wartości.

**Wartość:** Wymagana — szerokość okna w pikselach (np. „1920”)

## Czy wysokość okna jest większa niż (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Cel:** Sprawdza, czy wysokość okna gry jest większa od określonej wartości.

**Wartość:** Wymagana — wysokość okna w pikselach (np. „1080”)

## Czy gra jest wieloosobowa (`fancymenu_loading_requirement_is_multiplayer`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie w świecie wieloosobowym.

**Wartość:** Niewymagana

## Czy gra jest jednoosobowa (`fancymenu_loading_requirement_is_singpleplayer`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie w świecie jednoosobowym.

**Wartość:** Niewymagana

## Czy świat jest załadowany (`fancymenu_loading_requirement_is_world_loaded`)

**Cel:** Sprawdza, czy dowolny świat jest obecnie załadowany.

**Wartość:** Niewymagana

## Czy tryb gry to przygoda (`fancymenu_visibility_requirement_is_adventure`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie w trybie przygody.

**Wartość:** Niewymagana

## Czy tryb gry to kreatywny (`fancymenu_visibility_requirement_is_creative`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie w trybie kreatywnym.

**Wartość:** Niewymagana

## Czy tryb gry to obserwator (`fancymenu_visibility_requirement_is_spectator`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie w trybie obserwatora.

**Wartość:** Niewymagana

## Czy tryb gry to przetrwanie (`fancymenu_visibility_requirement_is_survival`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie w trybie przetrwania.

**Wartość:** Niewymagana

## Czy tryb gry jest zgodny (`is_gamemode`)

**Cel:** Sprawdza, czy gracz znajduje się w określonym trybie gry.

**Wartość:** Wymagana — nazwa trybu gry (np. „creative”, „survival”, „adventure”, „spectator”)

## Czy poziom trudności jest zgodny (`is_difficulty`)

**Cel:** Sprawdza, czy bieżący poziom trudności gry odpowiada określonej wartości.

**Wartość:** Wymagana — nazwa poziomu trudności (np. „peaceful”, „easy”, „normal”, „hard”)

## Czy tryb hardcore jest włączony (`is_hardcore`)

**Cel:** Sprawdza, czy obecnie załadowany świat działa w trybie hardcore.

**Wartość:** Niewymagana

## Czy perspektywa kamery jest zgodna (`is_camera_perspective`)

**Cel:** Sprawdza, czy bieżąca perspektywa kamery odpowiada określonej perspektywie.

**Wartość:** Wymagana — `first_person`, `third_person_back` lub `third_person_front`

## Czy pada deszcz (`is_raining`)

**Cel:** Sprawdza, czy w miejscu, w którym znajduje się gracz, pada obecnie deszcz.

**Wartość:** Niewymagana

## Czy trwa burza (`is_thundering`)

**Cel:** Sprawdza, czy w świecie gracza trwa obecnie burza z piorunami.

**Wartość:** Niewymagana

## Czy pogoda jest bezchmurna (`is_clear_weather`)

**Cel:** Sprawdza, czy pogoda jest obecnie bezchmurna (nie pada deszcz ani nie ma burzy).

**Wartość:** Niewymagana

## Czy pada śnieg (`is_snowing`)

**Cel:** Sprawdza, czy w miejscu, w którym znajduje się gracz, pada obecnie śnieg.

**Wartość:** Niewymagana

## Czy gracz biegnie (`is_player_running`)

**Cel:** Sprawdza, czy gracz obecnie sprintuje.

**Wartość:** Niewymagana

## Czy gracz się skrada (`is_player_sneaking`)

**Cel:** Sprawdza, czy gracz obecnie się skrada/kuca.

**Wartość:** Niewymagana

## Czy gracz używa przedmiotu (`is_player_using_item`)

**Cel:** Sprawdza, czy gracz obecnie używa przedmiotu.

**Wartość:** Niewymagana

## Czy gracz pływa (`is_player_swimming`)

**Cel:** Sprawdza, czy gracz obecnie pływa.

**Wartość:** Niewymagana

## Czy gracz skacze lub spada (`is_player_jumping`)

**Cel:** Zwraca true, gdy gracz znajduje się w powietrzu podczas zwykłego skoku lub spadania. Pływanie, ciecze, lot z elytrą, sen, pływanie wizualne i czołganie są wykluczone.

**Wartość:** Niewymagana

## Czy gracz jest pod wodą (`is_player_under_water`)

**Cel:** Sprawdza, czy gracz znajduje się całkowicie pod wodą.

**Wartość:** Niewymagana

## Czy gracz jest w wodzie (`is_player_in_water`)

**Cel:** Sprawdza, czy gracz znajduje się w wodzie (może być częściowo zanurzony).

**Wartość:** Niewymagana

## Czy gracz jest w lawie (`is_player_in_lava`)

**Cel:** Sprawdza, czy gracz znajduje się w lawie.

**Wartość:** Niewymagana

## Czy gracz jest w cieczy (`is_player_in_fluid`)

**Cel:** Sprawdza, czy gracz znajduje się w dowolnej cieczy (wodzie, lawie itd.).

**Wartość:** Niewymagana

## Czy gracz dosiada istoty/pojazdu (`is_player_riding_entity`)

**Cel:** Sprawdza, czy gracz dosiada dowolnej istoty.

**Wartość:** Niewymagana

## Czy gracz dosiada istoty, która może skakać (`is_player_riding_jumpable_entity`)

**Cel:** Sprawdza, czy gracz dosiada istoty, która może skakać (np. konia).

**Wartość:** Niewymagana

## Czy gracz dosiada istoty posiadającej zdrowie (`is_player_riding_entity_with_health`)

**Cel:** Sprawdza, czy gracz dosiada żywej istoty posiadającej zdrowie (np. zwierzęcia, ale nie łodzi).

**Wartość:** Niewymagana

## Czy gracz znajduje się w sypkim śniegu (`is_player_in_powder_snow`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie w sypkim śniegu.

**Wartość:** Niewymagana

## Czy gracz znajdował się w sypkim śniegu (`was_player_in_powder_snow`)

**Cel:** Sprawdza, czy gracz znajdował się w sypkim śniegu (używane w przypadku efektów utrzymujących się po wyjściu).

**Wartość:** Niewymagana

## Czy gracz nosi dynię (`is_player_wearing_pumpkin`)

**Cel:** Sprawdza, czy gracz ma na głowie wyrzeźbioną dynię.

**Wartość:** Niewymagana

## Czy gracz lata z elytrą (`is_player_flying_with_elytra`)

**Cel:** Sprawdza, czy gracz obecnie lata z elytrą.

**Wartość:** Niewymagana

## Czy gracz lata w trybie kreatywnym (`is_player_creative_flying`)

**Cel:** Sprawdza, czy gracz lata w trybie kreatywnym.

**Wartość:** Niewymagana

## Czy gracz ma serca absorpcji (`has_player_absorption_hearts`)

**Cel:** Sprawdza, czy gracz ma jakiekolwiek serca absorpcji (złote serca).

**Wartość:** Niewymagana

## Czy gracz jest pod wpływem efektu Wither (`is_player_withered`)

**Cel:** Sprawdza, czy na gracza działa efekt Wither.

**Wartość:** Niewymagana

## Czy gracz jest całkowicie zamrożony (`is_player_fully_frozen`)

**Cel:** Sprawdza, czy gracz jest całkowicie zamrożony (zwykle przez sypki śnieg).

**Wartość:** Niewymagana

## Czy gracz jest zatruty (`is_player_poisoned`)

**Cel:** Sprawdza, czy na gracza działa efekt trucizny.

**Wartość:** Niewymagana

## Czy gracz znajduje się w biomie (`is_player_in_biome`)

**Cel:** Sprawdza, czy gracz znajduje się w określonym biomie.

**Wartość:** Wymagana — identyfikator biomu (np. `minecraft:birch_forest`)

## Czy gracz znajduje się w wymiarze (`is_player_in_dimension`)

**Cel:** Sprawdza, czy gracz znajduje się w określonym wymiarze.

**Wartość:** Wymagana — identyfikator wymiaru (np. `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Czy gracz znajduje się w strukturze (`is_player_in_structure`)

**Cel:** Sprawdza, czy gracz znajduje się obecnie wewnątrz określonej struktury. W przypadku światów serwerowych FancyMenu musi być zainstalowane również na serwerze.

**Wartość:** Wymagana — identyfikator struktury (np. `minecraft:village`)

## Czy w pobliżu znajduje się istota (`is_entity_nearby`)

**Cel:** Sprawdza, czy określony typ istoty znajduje się w danym promieniu od gracza.

**Wartość:** Wymagana — format: „promień:identyfikator_istoty” (np. `10:minecraft:pig` — sprawdza, czy w odległości 10 bloków znajdują się świnie)

## Czy efekt jest aktywny (`is_effect_active`)

**Cel:** Sprawdza, czy na graczu działa określony efekt mikstury.

**Wartość:** Wymagana — identyfikator efektu (np. `minecraft:speed`, `minecraft:strength`)

## Czy dowolny efekt jest aktywny (`is_any_effect_active`)

**Cel:** Sprawdza, czy na graczu działa dowolny efekt mikstury.

**Wartość:** Niewymagana

## Czy gracz jest leworęczny (`is_left_handed`)

**Cel:** Sprawdza, czy w opcjach gry ustawiono dla gracza tryb leworęczny.

**Wartość:** Niewymagana

## Czy slot ekwipunku jest zajęty (`is_inventory_slot_filled`)

**Cel:** Sprawdza, czy określony slot ekwipunku zawiera przedmiot.

**Wartość:** Wymagana — numer slotu (0–35 dla głównego ekwipunku; sloty 0–8 to pasek szybkiego dostępu)

## Czy wskazano przedmiot w ekwipunku (`is_item_hovered_in_inventory`)

**Cel:** Sprawdza, czy kursor wskazuje dowolny przedmiot na ekranie ekwipunku.

**Wartość:** Niewymagana

## Czy kursor trzyma przedmiot z ekwipunku (`is_cursor_holding_inventory_item`)

**Cel:** Sprawdza, czy kursor obecnie trzyma stos przedmiotów z ekwipunku.

**Wartość:** Niewymagana

## Czy wybrano slot paska szybkiego dostępu (`is_hotbar_slot_active`)

**Cel:** Sprawdza, czy określony slot paska szybkiego dostępu jest obecnie wybrany.

**Wartość:** Wymagana — numer slotu paska szybkiego dostępu (0–8)

## Czy gracz ma wymagany poziom uprawnień (`fancymenu_loading_requirement_has_player_permission_level`)

**Cel:** Sprawdza, czy gracz ma co najmniej określony poziom uprawnień/OP w bieżącym świecie lub na serwerze.

**Wartość:** Wymagana — numer poziomu uprawnień (0–4, gdzie 4 oznacza operatora serwera)

## Czy siła ataku jest osłabiona (`is_attack_strength_weakened`)

**Cel:** Sprawdza, czy siła ataku gracza jest obecnie osłabiona (atak nie jest w pełni naładowany).

**Wartość:** Niewymagana

## Czy dzień rzeczywisty jest zgodny (`fancymenu_visibility_requirement_is_realtime_day`)

**Cel:** Sprawdza, czy bieżący dzień miesiąca w czasie rzeczywistym odpowiada określonej wartości.

**Wartość:** Wymagana — numer dnia (1–31). Można podać wiele wartości, oddzielając je przecinkami.

## Czy godzina rzeczywista jest zgodna (`fancymenu_visibility_requirement_is_realtime_hour`)

**Cel:** Sprawdza, czy bieżąca godzina w czasie rzeczywistym odpowiada określonej wartości.

**Wartość:** Wymagana — godzina w formacie 24-godzinnym (0–23). Można podać wiele wartości, oddzielając je przecinkami.

## Czy minuta rzeczywista jest zgodna (`fancymenu_visibility_requirement_is_realtime_minute`)

**Cel:** Sprawdza, czy bieżąca minuta w czasie rzeczywistym odpowiada określonej wartości.

**Wartość:** Wymagana — minuta (0–59). Można podać wiele wartości, oddzielając je przecinkami.

## Czy miesiąc rzeczywisty jest zgodny (`fancymenu_visibility_requirement_is_realtime_month`)

**Cel:** Sprawdza, czy bieżący miesiąc w czasie rzeczywistym odpowiada określonej wartości.

**Wartość:** Wymagana — numer miesiąca (1–12, gdzie 1 oznacza styczeń). Można podać wiele wartości, oddzielając je przecinkami.

## Czy sekunda rzeczywista jest zgodna (`fancymenu_visibility_requirement_is_realtime_second`)

**Cel:** Sprawdza, czy bieżąca sekunda w czasie rzeczywistym odpowiada określonej wartości.

**Wartość:** Wymagana — sekunda (0–59). Można podać wiele wartości, oddzielając je przecinkami.

## Czy dzień tygodnia w czasie rzeczywistym jest zgodny (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Cel:** Sprawdza, czy bieżący dzień tygodnia w czasie rzeczywistym odpowiada określonej wartości.

**Wartość:** Wymagana — dzień tygodnia jako liczba (1–7, gdzie 1 oznacza niedzielę). Można podać wiele wartości, oddzielając je przecinkami.

## Czy rok rzeczywisty jest zgodny (`fancymenu_visibility_requirement_is_realtime_year`)

**Cel:** Sprawdza, czy bieżący rok w czasie rzeczywistym odpowiada określonej wartości.

**Wartość:** Wymagana — pełny rok (np. „2023”). Można podać wiele wartości, oddzielając je przecinkami.

## Czy istnieje plik/katalog (`fancymenu_loading_requirement_file_exists`)

**Cel:** Sprawdza, czy istnieje plik lub katalog.

**Wartość:** Wymagana — ścieżka względna względem aktywnego katalogu gry albo ścieżka zaczynająca się od `.minecraft/`, wskazująca standardowy katalog Minecrafta. Zarówno pliki, jak i katalogi są uznawane za istniejące.

## Czy system operacyjny to Linux (`fancymenu_loading_requirement_is_os_linux`)

**Cel:** Sprawdza, czy bieżąca platforma nie jest systemem Windows ani macOS. Zwykle oznacza to środowisko Linux.

**Wartość:** Niewymagana

## Czy system operacyjny to macOS (`fancymenu_loading_requirement_is_os_macos`)

**Cel:** Sprawdza, czy systemem operacyjnym jest macOS.

**Wartość:** Niewymagana

## Czy system operacyjny to Windows (`fancymenu_loading_requirement_is_os_windows`)

**Cel:** Sprawdza, czy systemem operacyjnym jest Windows.

**Wartość:** Niewymagana

## Czy dostępne jest połączenie z internetem (`is_internet_connection_available`)

**Cel:** Sprawdza, czy dostępne jest aktywne połączenie z internetem.

**Wartość:** Niewymagana

## Czy język gry jest zgodny (`fancymenu_loading_requirement_is_language`)

**Cel:** Sprawdza, czy bieżący język gry odpowiada określonej wartości.

**Wartość:** Wymagana — kod języka (np. `en_us` dla języka angielskiego)

## Czy mod jest załadowany (`fancymenu_loading_requirement_is_mod_loaded`)

**Cel:** Sprawdza, czy określony mod jest załadowany.

**Wartość:** Wymagana — identyfikator moda (np. `fancymenu`, `jei`). Możesz także sprawdzić OptiFine za pomocą `optifine`. Obsługiwanych jest wiele identyfikatorów modów oddzielonych przecinkami; wszystkie wymienione mody muszą być załadowane.

## Czy Rinku jest załadowane (`is_rinku_loaded`)

**Cel:** Sprawdza, czy [Rinku](https://modrinth.com/mod/rinku) jest zainstalowane i zainicjalizowane. [Rinku](https://modrinth.com/mod/rinku) jest wymagane przez [element przeglądarki](./elements#browser) i [przestarzałe typy wideo oparte na Rinku](./video#requirements); [natywne funkcje wideo](./video) używają Watermedia.

**Wartość:** Niewymagana

## Czy jest liczbą (`fancymenu_visibility_requirement_is_number`)

**Cel:** Zapewnia zaawansowane porównywanie liczb z użyciem różnych trybów porównania.

**Wartość:** Wymagana — złożony format: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`, gdzie `comparison_mode` może mieć wartość `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` lub `smaller-than-or-equals`

## Czy jest tekstem (`fancymenu_visibility_requirement_is_text`)

**Cel:** Zapewnia zaawansowane porównywanie tekstu z użyciem różnych trybów porównania.

**Wartość:** Wymagana — złożony format: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`, gdzie `comparison_mode` może mieć wartość `equals`, `contains`, `starts-with` lub `ends-with`

## Czy adres IP serwera jest zgodny (`fancymenu_visibility_requirement_is_server_ip`)

**Cel:** Sprawdza, czy adres IP bieżącego serwera odpowiada określonej wartości.

**Wartość:** Wymagana — adres IP serwera (z portem lub bez)

## Czy serwer jest online (`fancymenu_loading_requirement_is_server_online`)

**Cel:** Sprawdza, czy określony serwer jest online i można się z nim połączyć.

**Wartość:** Wymagana — adres IP serwera (z portem lub bez)

## Czy paczka zasobów jest włączona (`is_resource_pack_enabled`)

**Cel:** Sprawdza, czy określona paczka zasobów jest obecnie wybrana/aktywna.

**Wartość:** Wymagana — tytuł paczki zasobów lub jej identyfikator (np. `Programmer Art` albo identyfikator paczki)

## Czy wartość zmiennej jest zgodna (zmienna FM) (`fancymenu_visibility_requirement_is_variable_value`)

**Cel:** Sprawdza, czy zmienna FancyMenu ma określoną wartość.

**Wartość:** Wymagana — format: „nazwa_zmiennej:oczekiwana_wartość”

## Tylko raz na sesję (`once_per_session`)

**Cel:** Każda skonfigurowana instancja zwraca true raz na sesję gry. Różne instancje są śledzone niezależnie.

**Wartość:** Niewymagana
