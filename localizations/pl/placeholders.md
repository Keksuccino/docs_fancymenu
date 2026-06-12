---
title: Placeholders
description: Jak używać placeholderów.
---
# Placeholders

Placeholdy to dynamiczne wartości, które są zastępowane rzeczywistą treścią w momencie użycia. W FancyMenu placeholdy pozwalają wstawiać dynamiczne treści do różnych elementów, takich jak tekst, przyciski i wymagania ładowania. Można je traktować jak zmienne, które są obliczane i zastępowane swoimi rzeczywistymi wartościami, gdy układy są wyświetlane.

# Informacje ogólne

## Podstawowa składnia
Placeholdy w FancyMenu używają składni podobnej do JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Na przykład, aby wyświetlić nazwę gracza:
```
{"placeholder":"playername"}
```

## Zagnieżdżanie placeholderów
Jedną z najpotężniejszych funkcji systemu placeholderów w FancyMenu jest możliwość zagnieżdżania placeholderów wewnątrz innych placeholderów. Oznacza to, że możesz użyć wyniku jednego placeholdera jako wejścia dla innego.

Przykład zagnieżdżonych placeholderów:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Ten przykład pobiera maksymalną wartość RAM i dzieli ją przez 1024, aby przeliczyć ją z MB na GB.

> [!IMPORTANT]
> W przeciwieństwie do prawdziwego JSON-a, zagnieżdżone placeholdery **nie** są **escape’owane** za pomocą `\`. To bardzo ważne, ponieważ placeholdery przestaną działać po escape’owaniu (oczywiście). Placeholdery używają tylko składni podobnej do JSON-a. Nie są prawdziwym JSON-em.

# Używanie placeholderów

Większość elementów, które mają pola tekstowe, obsługuje placeholdery. Podczas edycji możesz sprawdzić, czy dane pole tekstowe obsługuje placeholdery. Jeśli podczas edycji tekstu otwiera się pełnoekranowy **edytor tekstu**, oznacza to, że placeholdery są obsługiwane.

Aby znaleźć **listę wszystkich placeholderów**, kliknij przycisk **Placeholders** w **prawym górnym rogu** **edytora tekstu**.

Na górze listy placeholderów znajduje się **pasek wyszukiwania**, który pozwala wyszukiwać placeholdery.

Kliknięcie placeholdera na liście spowoduje wklejenie go do treści tekstu.

# Placeholdy szczegółowo

Ta lista zawiera większość, jeśli nie wszystkie, placeholdery dostępne w FancyMenu. Lista może czasem być nieco nieaktualna z powodu aktualizacji moda.

## Nazwa gracza (playername)
Zwraca nazwę użytkownika aktualnego gracza.
```
{"placeholder":"playername"}
```
Przykładowy wynik: `Steve`

## UUID gracza (playeruuid)
Zwraca unikalny identyfikator gracza.
```
{"placeholder":"playeruuid"}
```
Przykładowy wynik: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Wersja Minecrafta (mcversion)
Zwraca aktualną wersję Minecrafta.
```
{"placeholder":"mcversion"}
```
Przykładowy wynik: `1.19.2`

## Wersja mod loadera (loaderver)
Zwraca wersję mod loadera (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Przykładowy wynik: `43.2.0`

## Nazwa mod loadera (loadername)
Zwraca nazwę mod loadera.
```
{"placeholder":"loadername"}
```
Przykładowy wynik: `Forge`

## Wersja moda (modversion)
Zwraca wersję określonego moda.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Przykładowy wynik: `2.14.9`

## Łączna liczba modów (totalmods)
Zwraca łączną liczbę zainstalowanych modów.
```
{"placeholder":"totalmods"}
```
Przykładowy wynik: `45`

## Liczba aktywnych modów (loadedmods)
Zwraca liczbę aktualnie załadowanych modów.
```
{"placeholder":"loadedmods"}
```
Przykładowy wynik: `43`

## Postęp ładowania świata (world_load_progress)
Zwraca aktualny postęp ładowania świata w procentach.
```
{"placeholder":"world_load_progress"}
```
Przykładowy wynik: `75`

## Wartość opcji Minecrafta (minecraft_option_value)
Zwraca wartość opcji Minecrafta.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Przykładowy wynik: `70`

## Ostatni świat lub serwer (last_world_server)
Zwraca informacje o ostatnio otwartym świecie lub serwerze.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parametry:
- `type`: Określa, jaki rodzaj informacji ma zostać zwrócony
  - `"both"`: Zwraca ostatnio otwarty świat lub serwer (domyślnie)
  - `"server"`: Zwraca tylko wtedy, gdy ostatnio otwarty był serwer
  - `"world"`: Zwraca tylko wtedy, gdy ostatnio otwarty był świat
- `full_world_path`: Kontroluje sposób wyświetlania ścieżek światów
  - `"true"`: Zwraca pełną ścieżkę świata (domyślnie)
  - `"false"`: Zwraca tylko nazwę świata bez ścieżki (nie wpływa na serwery)

Przykłady:
- Serwer: `mc.hypixel.net`
- Świat z pełną ścieżką: `saves/New World`
- Świat bez pełnej ścieżki: `New World`

## Szerokość ekranu (guiwidth)
Zwraca aktualną szerokość ekranu.
```
{"placeholder":"guiwidth"}
```
Przykładowy wynik: `1920`

## Wysokość ekranu (guiheight)
Zwraca aktualną wysokość ekranu.
```
{"placeholder":"guiheight"}
```
Przykładowy wynik: `1080`

## Identyfikator aktualnego ekranu (screenid)
Zwraca identyfikator aktualnego ekranu.
```
{"placeholder":"screenid"}
```
Przykładowy wynik: `title_screen`

## Szerokość elementu (elementwidth)
Zwraca szerokość określonego elementu.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Przykładowy wynik: `200`

## Wysokość elementu (elementheight)
Zwraca wysokość określonego elementu.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Przykładowy wynik: `20`

## Pozycja X elementu (elementposx)
Zwraca pozycję X określonego elementu.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Przykładowy wynik: `150`

## Pozycja Y elementu (elementposy)
Zwraca pozycję Y określonego elementu.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Przykładowy wynik: `100`

## Pozycja X myszy (mouseposx)
Zwraca aktualną pozycję X myszy.
```
{"placeholder":"mouseposx"}
```
Przykładowy wynik: `960`

## Pozycja Y myszy (mouseposy)
Zwraca aktualną pozycję Y myszy.
```
{"placeholder":"mouseposy"}
```
Przykładowy wynik: `540`

## Kliknięcia na sekundę (clicks_per_second)
Zwraca aktualną liczbę kliknięć na sekundę dla przycisku myszy.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parametry:
- `mouse_button`: `left` lub `right`

Przykładowy wynik: `8`

## Skala GUI (guiscale)
Zwraca aktualną skalę GUI.
```
{"placeholder":"guiscale"}
```
Przykładowy wynik: `2`

## Etykieta/tekst przycisku Vanilla (vanillabuttonlabel)
Zwraca etykietę/tekst zwykłego widgetu/przycisku.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Przykładowy wynik: `Options...`

## Wartość pola tekstowego (text_input_field_value)
Zwraca aktualną wartość niestandardowego lub vanilla pola tekstowego na podstawie identyfikatora elementu.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Przykładowy wynik: `Hello World`

## Aktualne zdrowie gracza (current_player_health)
Zwraca aktualną liczbę punktów zdrowia gracza.
```
{"placeholder":"current_player_health"}
```
Przykładowy wynik: `20.0`

## Maksymalne zdrowie gracza (max_player_health)
Zwraca maksymalną liczbę punktów zdrowia gracza.
```
{"placeholder":"max_player_health"}
```
Przykładowy wynik: `20.0`

## Aktualne zdrowie gracza (procent) (current_player_health_percent)
Zwraca zdrowie gracza w procentach.
```
{"placeholder":"current_player_health_percent"}
```
Przykładowy wynik: `100`

## Aktualne zdrowie absorpcji gracza (current_player_absorption_health)
Zwraca punkty zdrowia absorpcji gracza (złote serca).
```
{"placeholder":"current_player_absorption_health"}
```
Przykładowy wynik: `4.0`

## Maksymalne zdrowie absorpcji gracza (max_player_absorption_health)
Zwraca maksymalne zdrowie absorpcji.
```
{"placeholder":"max_player_absorption_health"}
```
Przykładowy wynik: `4.0`

## Aktualne zdrowie absorpcji gracza (procent) (current_player_absorption_health_percent)
Zwraca zdrowie absorpcji gracza w procentach.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Przykładowy wynik: `100`

## Aktualny poziom głodu gracza (current_player_hunger)
Zwraca aktualny poziom głodu gracza.
```
{"placeholder":"current_player_hunger"}
```
Przykładowy wynik: `20`

## Maksymalny poziom głodu gracza (max_player_hunger)
Zwraca maksymalny poziom głodu.
```
{"placeholder":"max_player_hunger"}
```
Przykładowy wynik: `20`

## Aktualny poziom głodu gracza (procent) (current_player_hunger_percent)
Zwraca poziom głodu gracza w procentach.
```
{"placeholder":"current_player_hunger_percent"}
```
Przykładowy wynik: `100`

## Aktualne nasycenie głodu gracza (current_player_hunger_saturation)
Zwraca aktualną wartość nasycenia głodu gracza.
```
{"placeholder":"current_player_hunger_saturation"}
```
Przykładowy wynik: `5.0`

## Aktualny pancerz gracza (current_player_armor)
Zwraca aktualną wartość pancerza gracza.
```
{"placeholder":"current_player_armor"}
```
Przykładowy wynik: `20`

## Wytrzymałość pancerza gracza (player_armor_toughness)
Zwraca łączną wartość wytrzymałości pancerza gracza.
```
{"placeholder":"player_armor_toughness"}
```
Przykładowy wynik: `8.0`

## Maksymalny pancerz gracza (max_player_armor)
Zwraca maksymalną wartość pancerza.
```
{"placeholder":"max_player_armor"}
```
Przykładowy wynik: `20`

## Aktualny pancerz gracza (procent) (current_player_armor_percent)
Zwraca pancerz gracza w procentach.
```
{"placeholder":"current_player_armor_percent"}
```
Przykładowy wynik: `100`

## Aktualny poziom tlenu gracza (current_player_oxygen)
Zwraca aktualny poziom tlenu gracza (bąbelki powietrza).
```
{"placeholder":"current_player_oxygen"}
```
Przykładowy wynik: `300`

## Maksymalny poziom tlenu gracza (max_player_oxygen)
Zwraca maksymalny poziom tlenu.
```
{"placeholder":"max_player_oxygen"}
```
Przykładowy wynik: `300`

## Aktualny poziom tlenu gracza (procent) (current_player_oxygen_percent)
Zwraca poziom tlenu gracza w procentach.
```
{"placeholder":"current_player_oxygen_percent"}
```
Przykładowy wynik: `100`

## Aktualny poziom doświadczenia gracza (current_player_level)
Zwraca aktualny poziom doświadczenia gracza.
```
{"placeholder":"current_player_level"}
```
Przykładowy wynik: `30`

## Aktualne doświadczenie gracza (current_player_exp)
Zwraca łączną liczbę punktów doświadczenia gracza.
```
{"placeholder":"current_player_exp"}
```
Przykładowy wynik: `1250`

## Postęp doświadczenia gracza (procent) (current_player_exp_progress)
Zwraca postęp doświadczenia gracza do następnego poziomu w procentach.
```
{"placeholder":"current_player_exp_progress"}
```
Przykładowy wynik: `75`

## Siła ataku gracza (procent) (player_attack_strength)
Zwraca czas odnowienia ataku gracza w procentach.
```
{"placeholder":"player_attack_strength"}
```
Przykładowy wynik: `100`

## Tryb gry gracza (player_gamemode)
Zwraca aktualny tryb gry gracza.
```
{"placeholder":"player_gamemode"}
```
Przykładowy wynik: `survival`

## Kierunek patrzenia gracza (player_view_direction)
Zwraca kierunek, w którym patrzy gracz.
```
{"placeholder":"player_view_direction"}
```
Przykładowy wynik: `north`

## Współrzędna X gracza (player_x_coordinate)
Zwraca pozycję X gracza w świecie.
```
{"placeholder":"player_x_coordinate"}
```
Przykładowy wynik: `125`

## Współrzędna Y gracza (player_y_coordinate)
Zwraca pozycję Y gracza w świecie.
```
{"placeholder":"player_y_coordinate"}
```
Przykładowy wynik: `64`

## Współrzędna Z gracza (player_z_coordinate)
Zwraca pozycję Z gracza w świecie.
```
{"placeholder":"player_z_coordinate"}
```
Przykładowy wynik: `-250`

## Aktualne zdrowie wierzchowca (current_mount_health)
Zwraca aktualne zdrowie encji, na której jedzie gracz.
```
{"placeholder":"current_mount_health"}
```
Przykładowy wynik: `30.0`

## Maksymalne zdrowie wierzchowca (max_mount_health)
Zwraca maksymalne zdrowie encji, na której jedzie gracz.
```
{"placeholder":"max_mount_health"}
```
Przykładowy wynik: `30.0`

## Aktualne zdrowie wierzchowca (procent) (current_mount_health_percent)
Zwraca zdrowie wierzchowca w procentach.
```
{"placeholder":"current_mount_health_percent"}
```
Przykładowy wynik: `100`

## Aktualny wskaźnik skoku wierzchowca (procent) (current_mount_jump_meter)
Zwraca wartość wskaźnika mocy skoku wierzchowca.
```
{"placeholder":"current_mount_jump_meter"}
```
Przykładowy wynik: `75`

## Aktualne zdrowie bossa (procent) (current_boss_health)
Zwraca zdrowie aktywnego bossa.
```
{"placeholder":"current_boss_health"}
```
Przykładowy wynik: `150.0`

## Nazwa bossa (boss_name)
Zwraca nazwę aktywnego bossa.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Przykładowy wynik: `Ender Dragon`

## Liczba bossów (boss_count)
Zwraca liczbę aktywnych bossów.
```
{"placeholder":"boss_count"}
```
Przykładowy wynik: `1`

## Liczba aktywnych efektów (effects_count)
Zwraca liczbę aktywnych efektów mikstur.
```
{"placeholder":"effects_count"}
```
Przykładowy wynik: `3`

## Aktywny efekt (active_effect)
Zwraca informacje o określonym aktywnym efekcie.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Przykładowy wynik: `minecraft:speed`

## Wybrany slot paska szybkiego dostępu (active_hotbar_slot)
Zwraca aktualnie wybrany slot hotbara (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Przykładowy wynik: `4`

## Przedmiot w slocie (slot_item)
Zwraca informacje o przedmiocie w określonym slocie ekwipunku.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Przykładowy wynik: `minecraft:diamond_sword`

## Liczba przedmiotów w slocie (slot_item_count)
Zwraca liczebność stosu przedmiotu w określonym slocie ekwipunku gracza.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Przykładowy wynik: `64`

## Trwałość przedmiotu w slocie (slot_item_durability)
Zwraca informacje o trwałości przedmiotu w określonym slocie ekwipunku gracza.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parametry:
- `slot`: Numer slota ekwipunku gracza.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` lub `percent`.

Przykładowy wynik: `87`

## Nazwa wyświetlana przedmiotu w slocie (slot_item_display_name_fm)
Zwraca nazwę wyświetlaną przedmiotu w określonym slocie jako komponent tekstowy JSON. W trybie obserwatora sloty hotbara mogą zwracać nazwy przedmiotów z menu obserwatora, chyba że `ignore_spectator` ma wartość `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Przykładowy wynik: `{"text":"Diamond Sword","color":"aqua"}`

## Liczba przedmiotów w ekwipunku (inventory_item_count)
Zwraca łączną liczbę przedmiotów danego typu w ekwipunku gracza. Jeśli `item` jest puste, zlicza wszystkie stosy przedmiotów w ekwipunku.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Przykładowy wynik: `12`

## Ilość głodu przywracana przez przedmiot w slocie ekwipunku (inventory_slot_food_point_restore_amount)
Zwraca liczbę punktów głodu przywracanych przez jedzenie znajdujące się w danym slocie ekwipunku gracza.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Przykładowy wynik: `4.0`

## Przedmiot nad którym znajduje się kursor w ekwipunku (hovered_inventory_item)
Zwraca klucz przedmiotu aktualnie wskazywanego w ekranie ekwipunku.
```
{"placeholder":"hovered_inventory_item"}
```
Przykładowy wynik: `minecraft:apple`

## Czas gry świata (game_time)
Zwraca aktualny licznik ticków czasu w grze.
```
{"placeholder":"game_time"}
```
Przykładowy wynik: `18000`

## Czas dobowy świata (world_daytime)
Zwraca aktualny czas dnia w świecie.
```
{"placeholder":"world_daytime"}
```
Przykładowy wynik: `13000`

## Godzina czasu świata (world_daytime_hour)
Zwraca godzinę czasu świata. Domyślnie używany jest format 24-godzinny; ustaw `twelve_hour_format` na `"true"`, aby użyć formatu 12-godzinnego.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Przykładowy wynik: `12`

## Minuta czasu świata (world_daytime_minute)
Zwraca minutę czasu świata (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Przykładowy wynik: `30`

## Poziom trudności świata (world_difficulty)
Zwraca aktualny poziom trudności świata.
```
{"placeholder":"world_difficulty"}
```
Przykładowy wynik: `normal`

## Aktualny seed świata (current_world_seed)
Zwraca seed aktualnego świata jednoosobowego. Gdy seed nie jest dostępny, zwraca pustą wartość.
```
{"placeholder":"current_world_seed"}
```
Przykładowy wynik: `123456789`

## Aktualny biom (current_biome)
Zwraca biom, w którym aktualnie znajduje się gracz. Ustaw `as_key` na `"false"`, aby zwrócić przetłumaczoną/nazwaną pozycję, jeśli jest dostępna.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Przykładowy wynik: `minecraft:plains`

## Aktualny wymiar (current_dimension)
Zwraca wymiar, w którym aktualnie znajduje się gracz. Ustaw `as_key` na `"false"`, aby zwrócić przetłumaczoną/nazwaną pozycję, jeśli jest dostępna.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Przykładowy wynik: `minecraft:overworld`

## Wartość gamerule (gamerule_value)
Zwraca aktualną wartość gamerule’a w załadowanym świecie/serwerze. Światy serwerowe wymagają FancyMenu po stronie serwera.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Przykładowy wynik: `true`

## Kategoria przedmiotu (item_category)
Zwraca kategorię zakładki kreatywnej dla przedmiotu. Ustaw `as_key` na `"true"`, aby zwrócić klucz kategorii zamiast nazwy wyświetlanej.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Przykładowy wynik: `Combat`

## Aktualny tytuł/podtytuł HUD (current_title)
Zwraca aktualnie wyświetlany tekst tytułu.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Przykładowy wynik: `Game Over!`

## Wiadomość paska akcji (action_bar_message_fm)
Zwraca aktualną wiadomość vanilla action bar nad hotbarem.
```
{"placeholder":"action_bar_message_fm"}
```
Przykładowy wynik: `You may not rest now`

## Czas wyświetlania wiadomości paska akcji (action_bar_message_time_fm)
Zwraca, przez ile ticków aktualna wiadomość vanilla action bar będzie jeszcze wyświetlana.
```
{"placeholder":"action_bar_message_time_fm"}
```
Przykładowy wynik: `42`

## Obrót kamery X (camera_rotation_x_fm)
Zwraca aktualny pitch kamery w stopniach.
```
{"placeholder":"camera_rotation_x_fm"}
```
Przykładowy wynik: `12.5`

## Obrót kamery Y (camera_rotation_y_fm)
Zwraca aktualny yaw kamery w stopniach.
```
{"placeholder":"camera_rotation_y_fm"}
```
Przykładowy wynik: `-90.0`

## Zmiana obrotu kamery X (camera_rotation_delta_x_fm)
Zwraca zmianę pitch kamery na tick.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Przykładowy wynik: `0.4`

## Zmiana obrotu kamery Y (camera_rotation_delta_y_fm)
Zwraca zmianę yaw kamery na tick.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Przykładowy wynik: `-1.2`

## Czas podświetlenia przedmiotu (highlighted_item_time_fm)
Zwraca, przez ile ticków nazwa podświetlonego przedmiotu będzie jeszcze wyświetlana nad hotbarem.
```
{"placeholder":"highlighted_item_time_fm"}
```
Przykładowy wynik: `30`

## Postęp używania przedmiotu przez gracza (player_item_use_progress_fm)
Zwraca aktualny postęp używania przedmiotu od `0.0` do `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Przykładowy wynik: `0.65`

## Zmiana pozycji gracza X (player_position_delta_x_fm)
Zwraca zmianę pozycji gracza na osi X na tick.
```
{"placeholder":"player_position_delta_x_fm"}
```
Przykładowy wynik: `0.0`

## Zmiana pozycji gracza Y (player_position_delta_y_fm)
Zwraca zmianę pozycji gracza na osi Y na tick.
```
{"placeholder":"player_position_delta_y_fm"}
```
Przykładowy wynik: `-0.08`

## Zmiana pozycji gracza Z (player_position_delta_z_fm)
Zwraca zmianę pozycji gracza na osi Z na tick.
```
{"placeholder":"player_position_delta_z_fm"}
```
Przykładowy wynik: `0.12`

## Aktualne IP serwera (current_server_ip)
Zwraca IP połączonego serwera.
```
{"placeholder":"current_server_ip"}
```
Przykładowy wynik: `mc.hypixel.net`

## Lista graczy w świecie (world_players_list)
Zwraca listę wszystkich graczy aktualnie znajdujących się w świecie.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Przykładowy wynik: `Steve, Alex, Notch`

## MOTD serwera (servermotd)
Zwraca wiadomość dnia serwera.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Przykładowy wynik: `Welcome to Hypixel!`

## Ping serwera (serverping)
Zwraca ping do serwera w milisekundach.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Przykładowy wynik: `54`

## Liczba graczy na serwerze (serverplayercount)
Zwraca liczbę graczy na serwerze.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Przykładowy wynik: `25000/30000`

## Status serwera (serverstatus)
Zwraca status online/offline serwera.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Przykładowy wynik: `§aOnline` lub `§cOffline`

## Wersja serwera (serverversion)
Zwraca wersję Minecrafta serwera.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Przykładowy wynik: `1.19.2`

## Rok (realtimeyear)
Zwraca aktualny rok.
```
{"placeholder":"realtimeyear"}
```
Przykładowy wynik: `2024`

## Miesiąc (realtimemonth)
Zwraca aktualny miesiąc (01-12).
```
{"placeholder":"realtimemonth"}
```
Przykładowy wynik: `01`

## Dzień (realtimeday)
Zwraca aktualny dzień miesiąca (01-31).
```
{"placeholder":"realtimeday"}
```
Przykładowy wynik: `27`

## Godzina (realtimehour)
Zwraca aktualną godzinę. Domyślnie używany jest format 24-godzinny; ustaw `twelve_hour_format` na `"true"`, aby użyć formatu 12-godzinnego.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Przykładowy wynik: `14`

## Minuta (realtimeminute)
Zwraca aktualną minutę (00-59).
```
{"placeholder":"realtimeminute"}
```
Przykładowy wynik: `30`

## Sekunda (realtimesecond)
Zwraca aktualną sekundę (00-59).
```
{"placeholder":"realtimesecond"}
```
Przykładowy wynik: `45`

## Aktualny czas w milisekundach (Unix Timestamp) (unix_time)
Zwraca aktualny znacznik czasu Unix w milisekundach.
```
{"placeholder":"unix_time"}
```
Przykładowy wynik: `1716552478123`

> Placeholdy czasu rzeczywistego (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` i `unix_time`) obsługują wartość `timezone`. Używaj standardowych identyfikatorów stref czasowych Java, takich jak `UTC`, `Europe/Berlin` lub `America/New_York`; pomiń ją albo użyj `system`, aby skorzystać ze strefy systemowej.
{.is-info}

## Informacje o CPU (cpuinfo)
Zwraca informacje o procesorze.
```
{"placeholder":"cpuinfo"}
```
Przykładowy wynik: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Użycie CPU (JVM) (jvmcpu)
Zwraca użycie CPU przez JVM w procentach.
```
{"placeholder":"jvmcpu"}
```
Przykładowy wynik: `25.5`

## Użycie CPU (system) (oscpu)
Zwraca użycie CPU przez system operacyjny w procentach.
```
{"placeholder":"oscpu"}
```
Przykładowy wynik: `42.8`

## Informacje o GPU (gpuinfo)
Zwraca informacje o karcie graficznej.
```
{"placeholder":"gpuinfo"}
```
Przykładowy wynik: `NVIDIA GeForce RTX 3080`

## Wersja Java (javaver)
Zwraca wersję Java.
```
{"placeholder":"javaver"}
```
Przykładowy wynik: `17.0.2`

## Wirtualna maszyna Java (jvmname)
Zwraca nazwę maszyny wirtualnej Java.
```
{"placeholder":"jvmname"}
```
Przykładowy wynik: `OpenJDK 64-Bit Server VM`

## Wersja OpenGL (glver)
Zwraca wersję OpenGL.
```
{"placeholder":"glver"}
```
Przykładowy wynik: `4.6.0 NVIDIA 516.94`

## Nazwa systemu operacyjnego (osname)
Zwraca nazwę systemu operacyjnego.
```
{"placeholder":"osname"}
```
Przykładowy wynik: `Windows 10`

## FPS (klatki na sekundę) (fps)
Zwraca aktualną liczbę klatek na sekundę.
```
{"placeholder":"fps"}
```
Przykładowy wynik: `120`

## Używana pamięć RAM w MB (usedram)
Zwraca ilość aktualnie używanej pamięci RAM (MB).
```
{"placeholder":"usedram"}
```
Przykładowy wynik: `4096`

## Maksymalna pamięć RAM w MB (maxram)
Zwraca maksymalnie przydzieloną pamięć RAM (MB).
```
{"placeholder":"maxram"}
```
Przykładowy wynik: `8192`

## Używana pamięć RAM w %% (percentram)
Zwraca procent aktualnie używanej pamięci RAM.
```
{"placeholder":"percentram"}
```
Przykładowy wynik: `50`

## Głośność elementu audio (audio_element_vol)
Zwraca głośność elementu audio.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Przykładowy wynik: `0.5`

## Aktualny utwór audio (audio_element_current_track)
Zwraca nazwę utworu elementu audio.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Przykładowy wynik: `Cool Track Name`

## Czas trwania audio (audio_duration)
Zwraca całkowity czas trwania utworu audio w formacie MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Przykładowy wynik: `03:45`

## Czas odtwarzania audio (audio_playtime)
Zwraca aktualny czas odtwarzania utworu audio. Ustaw `show_percentage` na `"true"`, aby otrzymać wartość postępu 0-100 zamiast formatu `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Przykładowy wynik: `01:30` (lub `45`, gdy `show_percentage` ma wartość `"true"`)

## Stan odtwarzania audio (audio_playing_state)
Zwraca informację, czy element audio jest odtwarzany (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Przykładowy wynik: `true`

## Głośność elementu wideo (video_element_vol)
Zwraca poziom głośności elementu wideo (0.0 do 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Przykładowy wynik: `0.5`

## Czas trwania elementu wideo (video_element_duration)
Zwraca całkowity czas trwania elementu wideo w formacie `MM:SS`. Ustaw `output_as_timestamp` na `"true"`, aby zwrócić znacznik czasu w milisekundach.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Przykładowy wynik: `02:00` (lub `120000`, gdy `output_as_timestamp` ma wartość `"true"`)

## Czas odtwarzania elementu wideo (video_element_playtime)
Zwraca aktualny czas odtwarzania (postęp) elementu wideo w formacie `MM:SS`. Ustaw `show_percentage` na `"true"` dla wartości postępu 0-100 albo `output_as_timestamp` na `"true"` dla milisekund.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Przykładowy wynik: `00:45` (lub `38` jako procent, albo `45200` jako znacznik czasu)

## Stan pauzy elementu wideo (video_element_paused_state)
Zwraca informację, czy element wideo jest wstrzymany (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Przykładowy wynik: `false`

## Głośność tła wideo (video_background_vol)
Zwraca poziom głośności tła wideo menu (0.0 do 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Przykładowy wynik: `0.7`

## Czas trwania tła wideo (video_background_duration)
Zwraca całkowity czas trwania tła wideo menu w formacie `MM:SS`. Ustaw `output_as_timestamp` na `"true"`, aby zwrócić znacznik czasu w milisekundach.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Przykładowy wynik: `03:00` (lub `180000`, gdy `output_as_timestamp` ma wartość `"true"`)

## Czas odtwarzania tła wideo (video_background_playtime)
Zwraca aktualny czas odtwarzania (postęp) tła wideo menu w formacie `MM:SS`. Ustaw `show_percentage` na `"true"` dla wartości postępu 0-100 albo `output_as_timestamp` na `"true"` dla milisekund.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Przykładowy wynik: `01:00` (lub `33` jako procent, albo `60500` jako znacznik czasu)

## Stan pauzy tła wideo (video_background_paused_state)
Zwraca informację, czy tło wideo menu jest wstrzymane (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Przykładowy wynik: `true`

## Kalkulator (calc)
Placeholder kalkulatora to potężne narzędzie, które pozwala wykonywać obliczenia matematyczne w układach. Obsługuje szeroki zakres operacji matematycznych i może działać zarówno na liczbach dziesiętnych, jak i całkowitych.

### Podstawowa składnia
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

Kalkulator ma dwa główne parametry:
- `decimal`: Określa, czy wynik ma zawierać miejsca po przecinku (`true`), czy zostać zaokrąglony do liczb całkowitych (`false`)
- `expression`: Wyrażenie matematyczne do obliczenia

### Obsługiwane operacje
Kalkulator obsługuje następujące operacje matematyczne:
- Podstawowe działania: `+` (dodawanie), `-` (odejmowanie), `*` (mnożenie), `/` (dzielenie)
- Nawiasy: `( )` do grupowania operacji
- Potęgowanie: `^`
- Pierwiastek kwadratowy: `sqrt()`
- Funkcje trygonometryczne: `sin()`, `cos()`, `tan()`
- Stałe matematyczne: `pi`, `e`
- Wartość bezwzględna: `abs()`
- Logarytmy: `log()`, `ln()`

## Losowa liczba (random_number)
Generuje losową liczbę w określonym zakresie.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Przykładowy wynik: `42`

## Maksymalna liczba (maxnum)
Zwraca większą z dwóch liczb.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Przykładowy wynik: `20`

## Minimalna liczba (minnum)
Zwraca mniejszą z dwóch liczb.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Przykładowy wynik: `10`

## Wartość bezwzględna liczby (absnum)
Zwraca wartość bezwzględną liczby.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Przykładowy wynik: `10.5`

## Negacja liczby (negnum)
Zwraca wartość liczby ze zmianą znaku.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Przykładowy wynik: `-10.5`

## *pi* (Matematyka) (math_pi)
Zwraca wartość π.
```
{"placeholder":"math_pi"}
```
Przykładowy wynik: `3.141592653589793`

## Sinus trygonometryczny (Matematyka) (math_sin)
Zwraca sinus kąta.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Przykładowy wynik: `0.7071067811865476`

## Cosinus trygonometryczny (Matematyka) (math_cos)
Zwraca cosinus kąta.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Przykładowy wynik: `0.7071067811865476`

## Tangens trygonometryczny (Matematyka) (math_tan)
Zwraca tangens kąta.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Przykładowy wynik: `1.0`

## Podłoga (Matematyka) (math_floor)
Zaokrągla liczbę w dół do najbliższej liczby całkowitej.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Przykładowy wynik: `3`

## Sufit (Matematyka) (math_ceil)
Zaokrągla liczbę w górę do najbliższej liczby całkowitej.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Przykładowy wynik: `4`

## Zaokrąglanie (Matematyka) (math_round)
Zaokrągla liczbę. Domyślnie do najbliższej liczby całkowitej; ustaw `decimals` na nieujemną liczbę, aby zaokrąglić do określonej liczby miejsc po przecinku.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Przykładowy wynik: `3.14` (z `decimals:-1` lub bez parametru → `3`)

## Znak (Matematyka) (math_sign)
Zwraca znak liczby (1 dla dodatniej, -1 dla ujemnej, 0 dla zera).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Przykładowy wynik: `-1`

## Sinus hiperboliczny (Matematyka) (math_sinh)
Zwraca sinus hiperboliczny kąta.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Przykładowy wynik: `1.1752011936438014`

## Cosinus hiperboliczny (Matematyka) (math_cosh)
Zwraca cosinus hiperboliczny kąta.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Przykładowy wynik: `1.5430806348152437`

## Tangens hiperboliczny (Matematyka) (math_tanh)
Zwraca tangens hiperboliczny kąta.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Przykładowy wynik: `0.7615941559557649`

## Podziel tekst (split_text)
Dzieli tekst przy użyciu określonego separatora.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Przykładowy wynik: `world`

## Przytnij tekst (trim_text)
Usuwa białe znaki z początku i końca tekstu.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Przykładowy wynik: `hello world`

## Przytnij tekst z końców (crop_text)
Usuwa znaki z początku i końca tekstu.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Przykładowy wynik: `ello worl`

## Stringify (stringify)
Konwertuje tekst do postaci ciągu, escape’ując wszystkie znaki składni.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Przykładowy wynik: `text with \{special\} \"characters\"`

## Lokalizuj tekst (local)
Pobiera przetłumaczony tekst dla określonego klucza.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Przykładowy wynik: `Singleplayer`

## Tekst z sieci (webtext)
Pobiera treść tekstową z adresu URL.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Przykładowy wynik: treść tekstowa z adresu URL

## Losowy tekst (randomtext)
Zwraca losową linię z pliku tekstowego, adresu URL lub bezpośrednio podanego zwykłego tekstu. Tekst zmienia się w określonych odstępach.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parametry:
- `source`: Źródło linii tekstu (zastępuje stary parametr `path`)
  - Ścieżka pliku: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Zwykły tekst: `Line 1\nLine 2\nLine 3`
- `interval`: Czas w sekundach między zmianami tekstu

Placeholder obsługuje teraz trzy typy źródeł:
1. **Pliki lokalne**: Pliki tekstowe z katalogu gry
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL-e**: Zdalne pliki tekstowe z internetu
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Zwykły tekst**: Bezpośrednio wpisany tekst z liniami oddzielonymi przez `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Uwaga: Starsze placeholdery używające `path` zamiast `source` nadal będą działać.

## Parser JSON (json)
Parsuje dane JSON z pliku, URL-a lub bezpośrednio podanej treści JSON i wyciąga wartości przy użyciu wyrażeń JSON Path.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parametry:
- `source`: Źródło danych JSON
  - Ścieżka pliku: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Bezpośredni JSON: `{"name":"Steve","level":42}`
- `json_path`: Wyrażenie JSON Path do wyciągania danych

Placeholder obsługuje teraz trzy typy źródeł:
1. **Pliki lokalne**: Pliki JSON z katalogu gry
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL-e**: Zdalne dane JSON z API lub usług webowych
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Bezpośredni JSON**: Osadzona treść JSON
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Przykładowe ścieżki JSON:
- `$.name` - Pobiera pole "name" z głównego obiektu
- `$.player.level` - Pobiera zagnieżdżone pole "level" wewnątrz "player"
- `$.items[0].id` - Pobiera "id" pierwszego elementu tablicy
- `$.scores.*` - Pobiera wszystkie wartości z obiektu "scores"

## Absolutna ścieżka pliku/folderu (absolute_path)
Zwraca pełną ścieżkę pliku.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Przykładowy wynik: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Liczba znaków tekstu (text_character_count)
Zwraca liczbę znaków w podanym tekście.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Przykładowy wynik: `12`

## Szerokość tekstu (text_width)
Zwraca szerokość podanego tekstu w pikselach po wyrenderowaniu.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Przykładowy wynik: `66`

## Tekst wielkimi literami (uppercase_text)
Konwertuje tekst wejściowy na same wielkie litery.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Przykładowy wynik: `HELLO WORLD`

## Tekst małymi literami (lowercase_text)
Konwertuje tekst wejściowy na same małe litery.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Przykładowy wynik: `hello world`

## Tekst w kapitalikach tytułowych (title_case_text)
Konwertuje tekst wejściowy do kapitalików tytułowych.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Przykładowy wynik: `Hello World`

## Zdaniowy zapis tekstu (sentence_case_text)
Konwertuje tekst wejściowy do zapisu zdaniowego.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Przykładowy wynik: `Hello world. This is fancymenu!`

## Tekst w snake_case (snake_case_text)
Konwertuje tekst wejściowy do formatu `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Przykładowy wynik: `hello_world`

## Tekst w kebab-case (kebab_case_text)
Konwertuje tekst wejściowy do formatu `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Przykładowy wynik: `hello-world`

## Tekst z naprzemienną wielkością liter (alternating_case_text)
Konwertuje tekst wejściowy do zapisu naprzemiennego.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Przykładowy wynik: `aLtErNaTiNg CaSe`

## Przełącz wielkość liter tekstu (toggle_case_text)
Przełącza wielkość liter każdej litery w tekście wejściowym.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Przykładowy wynik: `tOGGLE cASE`

## Kodowanie do Base64 (base64_encode)
Koduje podany tekst jako Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Przykładowy wynik: `SGVsbG8gV29ybGQ=`

## Dekodowanie z Base64 (base64_decode)
Dekoduje ciąg Base64 z powrotem do zwykłego tekstu.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Przykładowy wynik: `Hello World`

## Tekst z pliku (file_text)
Zwraca linie tekstu z pliku lub URL-a. Może zwrócić wszystkie linie albo tylko ostatnie X linii.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parametry:
- `path_or_url`: Ścieżka pliku lub URL do odczytu
- `mode`: `"all"` (zwraca wszystkie linie) lub `"last"` (zwraca tylko ostatnie X linii)
- `separator`: Tekst używany do łączenia linii (domyślnie: `"\n"`)
- `last_lines`: Liczba linii do zwrócenia, gdy `mode` ma wartość `"last"` (domyślnie: `"1"`)

Przykładowy wynik: Zależy od zawartości pliku

## Zawartość schowka (clipboard_content)
Zwraca aktualną zawartość tekstową przechowywaną w systemowym schowku.
```
{"placeholder":"clipboard_content"}
```
Przykładowy wynik: Dowolny tekst aktualnie znajdujący się w schowku

## Zamień tekst (replace_text)
Zamienia tekst w ciągu przy użyciu zwykłego tekstu lub wyrażeń regularnych.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parametry:
- `text`: Tekst wejściowy do przetworzenia
- `search`: Tekst lub wzorzec regex do wyszukania
- `replacement`: Tekst zastępczy
- `use_regex`: Czy używać wyrażeń regularnych (`"true"`), czy dopasowania literalnego (`"false"`)
- `replace_all`: Zastąp wszystkie wystąpienia (`"true"`) lub tylko pierwsze (`"false"`)

Przykładowy wynik: `Hello FancyMenu! This is a test.`

## Switch Case (switch_case)
Wykonuje operację switch-case na podstawie wartości.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Przykładowy wynik: `first case` (jeśli wartość wynosi 1)

## Pobierz wartość zmiennej (FM Variable) (getvariable)
Pobiera wartość wcześniej zapisanej zmiennej.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Przykładowy wynik: Zależy od zapisanej wartości

## Pobierz dane NBT (nbt_data_get)
Pobiera dane NBT po stronie klienta (podobnie do komendy `/data get`). Użyj wariantu serwerowego `nbt_data_get_server`, gdy jesteś połączony z serwerem i potrzebujesz autorytatywnych wartości po stronie serwera.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parametry:
- `source_type`: `"entity"` lub `"block"`
- `entity_selector`: Selektor encji, np. `@s`, `@p`, `@e` albo UUID/nazwa (dla encji)
- `block_pos`: Pozycja bloku w formacie `"x y z"` (dla bloków)
- `nbt_path`: Ścieżka NBT do pobrania
- `scale`: Opcjonalny współczynnik skalowania dla wartości numerycznych (domyślnie: `"1.0"`)
- `return_type`: Sposób zwrócenia danych:
  - `"value"`: Domyślnie, zwraca wartość (z opcjonalnym skalowaniem dla liczb)
  - `"string"`: Zwraca rzeczywiste dane NBT jako tekst
  - `"snbt"`: Zwraca jako SNBT (sformatowane NBT)
  - `"json"`: Zwraca jako komponent w formacie JSON (dla tagów złożonych)

Przykładowy wynik: `20` (dla poziomu głodu)

## Pobierz dane NBT (po stronie serwera) (nbt_data_get_server)
Zapyta o dane NBT po stronie serwera (używając pakietu) i tymczasowo buforuje wyniki. Wartości odpowiadają placeholderowi po stronie klienta.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Przykładowy wynik: `minecraft:diamond_sword`

## Ostatnia wiadomość śmierci (lastdeathmessage)
Zwraca ostatnio zarejestrowaną wiadomość śmierci gracza klienta. Ustaw `as_json_component` na `"true"`, aby otrzymać surowy komponent tekstowy JSON.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Przykładowy wynik: `Steve was slain by Zombie`

## Czas działania (uptime_duration)
Zwraca, jak długo FancyMenu jest załadowane. Domyślnie wartość podawana jest w sekundach; ustaw `output_as_millis` na `"true"`, aby otrzymać milisekundy.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Przykładowy wynik: `742` (sekundy od załadowania)

## Nazwy zapisów światów (level_save_names)
Wyświetla nazwy wszystkich lokalnych zapisów światów połączone wybranym separatorem. Działa na wątku klienta.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Przykładowy wynik: `Creative Test, Survival World, Hardcore`

## Dane zapisu świata (level_save_data)
Zwraca serializowane dane poziomu dla podanej nazwy świata (musi odpowiadać nazwie wyświetlanej na liście zapisów).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Przykładowy wynik: `{"name":"Survival World","gameMode":"survival",...}`

## Konwerter podstawy liczby (number_base_convert)
Konwertuje liczbę (całkowitą lub ułamkową) z jednej podstawy na inną (2–36). Domyślnie używa systemu dziesiętnego, jeśli podstawy nie zostaną podane.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Przykładowy wynik: `43.8`

## Rozmiar pliku (file_size)
Zwraca rozmiar lokalnego pliku w bajtach. Dozwolone są tylko lokalne ścieżki.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Przykładowy wynik: `1284`

## MD5 pliku (file_md5)
Zwraca hash MD5 lokalnego pliku jako mały ciąg szesnastkowy.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Przykładowy wynik: `d41d8cd98f00b204e9800998ecf8427e`

# Praktyczne przykłady

## Tworzenie dynamicznego wyświetlania pamięci
```
Używana RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Tworzenie zegara czasu rzeczywistego
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Tworzenie wyświetlania informacji o systemie
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD stanu gracza
```
Zdrowie: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Pancerz: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Poziom XP: {"placeholder":"current_player_level"}
```

## Złożone obliczenie z zagnieżdżonymi placeholderami
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Wyświetlanie współrzędnych z zaokrąglaniem
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Najlepsze praktyki

1. **Buforuj kosztowne operacje**: Niektóre placeholdery (np. pobierające informacje systemowe) mogą obciążać zasoby. Jeśli musisz używać ich wielokrotnie, rozważ przechowywanie ich wartości w zmiennych.

2. **Używaj odpowiednich ustawień dziesiętnych**: Podczas pracy z obliczeniami używaj parametru `decimal` właściwie. Ustaw go na `false`, gdy potrzebujesz liczb całkowitych, oraz na `true`, gdy potrzebujesz precyzyjnych wartości dziesiętnych.

3. **Obsługuj brakujące wartości**: Zawsze rozważ, co ma się stać, jeśli placeholder nie zwróci wartości. W takich przypadkach warto ustawić wartości domyślne.

4. **Testuj wydajność**: Przy używaniu wielu placeholderów lub złożonych struktur zagnieżdżonych przetestuj wpływ na wydajność, zwłaszcza na słabszych komputerach.

5. **Używaj zaawansowanego skalowania/pozycjonowania**: Dla dynamicznych elementów UI łącz placeholdery z zaawansowanym skalowaniem i pozycjonowaniem, aby tworzyć responsywne układy.

6. **Łącz z zmiennymi**: Używaj placeholderów razem ze zmiennymi, aby uzyskać jeszcze bardziej dynamiczną treść, którą można aktualizować za pomocą akcji.

# Częste problemy i rozwiązania

## Placeholder się nie aktualizuje
Jeśli wartość placeholdera nie aktualizuje się zgodnie z oczekiwaniami, sprawdź:
- Czy placeholder ma prawidłowy format
- Czy używasz właściwej wielkości liter w identyfikatorze placeholdera
- Czy placeholder wymaga spełnienia określonych warunków, aby się zaktualizować

## Zagnieżdżone placeholdery nie działają
Podczas zagnieżdżania placeholderów:
- Upewnij się, że cudzysłowy są poprawnie escape’owane
- Sprawdź, czy każdy zagnieżdżony placeholder jest sam w sobie prawidłowy

## Problemy z wydajnością
Jeśli zauważysz problemy z wydajnością:
- Ogranicz liczbę używanych placeholderów
- Unikaj niepotrzebnego zagnieżdżania
- Rozważ używanie zmiennych dla często używanych wartości
- Używaj odpowiedniego placeholdera do danego zadania (np. nie używaj placeholderów czasu rzeczywistego, jeśli wystarczą wartości statyczne)
