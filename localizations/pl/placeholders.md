---
title: Placeholders
description: Jak używać placeholderów.
---

# Placeholders

Placeholders to dynamiczne wartości, które są zastępowane rzeczywistą treścią w momencie użycia. W FancyMenu placeholdery pozwalają wstawiać dynamiczną zawartość do różnych elementów, takich jak tekst, przyciski i wymagania ładowania. Traktuj je jak zmienne, które są obliczane i zastępowane swoimi rzeczywistymi wartościami, gdy wyświetlane są Twoje układy.

# Informacje ogólne

## Podstawowa składnia
Placeholders w FancyMenu używają składni podobnej do JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Na przykład, aby wyświetlić nazwę gracza:
```
{"placeholder":"playername"}
```

## Zagnieżdżanie placeholderów
Jedną z najpotężniejszych funkcji systemu placeholderów FancyMenu jest możliwość zagnieżdżania placeholderów wewnątrz innych placeholderów. Oznacza to, że możesz użyć wyniku jednego placeholdera jako wejścia dla innego.

Przykład zagnieżdżonych placeholderów:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Ten przykład pobiera maksymalną wartość RAM i dzieli ją przez 1024, aby przeliczyć ją z MB na GB.

# Używanie placeholderów

Większość elementów, które mają pola tekstowe, obsługuje placeholdery. Podczas edycji możesz sprawdzić, czy dane pole tekstowe obsługuje placeholdery. Jeśli podczas edycji tekstu otwiera się pełnoekranowy **edytor tekstu**, oznacza to, że obsługuje on placeholdery. 

Aby znaleźć **listę wszystkich placeholderów**, kliknij przycisk **Placeholders** w **prawym górnym rogu** **edytora tekstu**.

Na górze listy placeholderów znajduje się **pasek wyszukiwania**, który pozwala wyszukiwać placeholdery.

Kliknięcie placeholdera na liście spowoduje wklejenie go do treści tekstu.

# Placeholders szczegółowo

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
Zwraca bieżącą wersję Minecrafta.
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

## Całkowita liczba modów (totalmods)
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
Zwraca bieżący postęp ładowania świata w procentach.
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
Zwraca informacje o ostatnio użytym świecie lub serwerze.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parametry:
- `type`: Określa, jaki typ informacji ma zostać zwrócony
  - `"both"`: Zwraca ostatnio użyty świat lub serwer (domyślnie)
  - `"server"`: Zwraca tylko wtedy, gdy ostatnio użyty był serwer
  - `"world"`: Zwraca tylko wtedy, gdy ostatnio użyty był świat
- `full_world_path`: Określa sposób wyświetlania ścieżek świata
  - `"true"`: Zwraca pełną ścieżkę świata (domyślnie)
  - `"false"`: Zwraca tylko nazwę świata bez ścieżki (nie dotyczy serwerów)

Przykłady:
- Serwer: `mc.hypixel.net`
- Świat z pełną ścieżką: `saves/New World`
- Świat bez pełnej ścieżki: `New World`

## Szerokość ekranu (guiwidth)
Zwraca bieżącą szerokość ekranu.
```
{"placeholder":"guiwidth"}
```
Przykładowy wynik: `1920`

## Wysokość ekranu (guiheight)
Zwraca bieżącą wysokość ekranu.
```
{"placeholder":"guiheight"}
```
Przykładowy wynik: `1080`

## Identyfikator bieżącego ekranu (screenid)
Zwraca identyfikator bieżącego ekranu.
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
Zwraca bieżącą pozycję X myszy.
```
{"placeholder":"mouseposx"}
```
Przykładowy wynik: `960`

## Pozycja Y myszy (mouseposy)
Zwraca bieżącą pozycję Y myszy.
```
{"placeholder":"mouseposy"}
```
Przykładowy wynik: `540`

## Kliknięcia na sekundę (clicks_per_second)
Zwraca bieżącą liczbę kliknięć na sekundę dla przycisku myszy.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parametry:
- `mouse_button`: `left` lub `right`

Przykładowy wynik: `8`

## Skala GUI (guiscale)
Zwraca bieżącą skalę GUI.
```
{"placeholder":"guiscale"}
```
Przykładowy wynik: `2`

## Etykieta/tekst vanillowego widgetu/przycisku (vanillabuttonlabel)
Zwraca etykietę/tekst vanillowego widgetu lub przycisku.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Przykładowy wynik: `Options...`

## Wartość pola tekstowego (text_input_field_value)
Zwraca bieżącą wartość niestandardowego lub vanillowego pola tekstowego na podstawie identyfikatora elementu.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Przykładowy wynik: `Hello World`

## Bieżące zdrowie gracza (current_player_health)
Zwraca bieżącą liczbę punktów zdrowia gracza.
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

## Bieżące zdrowie gracza (procent) (current_player_health_percent)
Zwraca zdrowie gracza w procentach.
```
{"placeholder":"current_player_health_percent"}
```
Przykładowy wynik: `100`

## Bieżące zdrowie absorpcji gracza (current_player_absorption_health)
Zwraca bieżące punkty zdrowia absorpcji gracza (złote serca).
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

## Bieżące zdrowie absorpcji gracza (procent) (current_player_absorption_health_percent)
Zwraca zdrowie absorpcji gracza w procentach.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Przykładowy wynik: `100`

## Bieżący poziom głodu gracza (current_player_hunger)
Zwraca bieżący poziom głodu gracza.
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

## Bieżący poziom głodu gracza (procent) (current_player_hunger_percent)
Zwraca głód gracza w procentach.
```
{"placeholder":"current_player_hunger_percent"}
```
Przykładowy wynik: `100`

## Bieżące nasycenie głodu gracza (current_player_hunger_saturation)
Zwraca bieżącą wartość nasycenia głodu gracza.
```
{"placeholder":"current_player_hunger_saturation"}
```
Przykładowy wynik: `5.0`

## Bieżąca zbroja gracza (current_player_armor)
Zwraca bieżącą wartość zbroi gracza.
```
{"placeholder":"current_player_armor"}
```
Przykładowy wynik: `20`

## Wytrzymałość zbroi gracza (player_armor_toughness)
Zwraca łączną wartość wytrzymałości zbroi gracza.
```
{"placeholder":"player_armor_toughness"}
```
Przykładowy wynik: `8.0`

## Maksymalna zbroja gracza (max_player_armor)
Zwraca maksymalną wartość zbroi.
```
{"placeholder":"max_player_armor"}
```
Przykładowy wynik: `20`

## Bieżąca zbroja gracza (procent) (current_player_armor_percent)
Zwraca zbroję gracza w procentach.
```
{"placeholder":"current_player_armor_percent"}
```
Przykładowy wynik: `100`

## Bieżący poziom tlenu gracza (current_player_oxygen)
Zwraca bieżący poziom tlenu gracza (bąbelki powietrza).
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

## Bieżący poziom tlenu gracza (procent) (current_player_oxygen_percent)
Zwraca poziom tlenu gracza w procentach.
```
{"placeholder":"current_player_oxygen_percent"}
```
Przykładowy wynik: `100`

## Bieżący poziom gracza (current_player_level)
Zwraca bieżący poziom doświadczenia gracza.
```
{"placeholder":"current_player_level"}
```
Przykładowy wynik: `30`

## Bieżące doświadczenie gracza (current_player_exp)
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

## Bieżące zdrowie wierzchowca (current_mount_health)
Zwraca bieżące zdrowie encji, na której jedzie gracz.
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

## Bieżące zdrowie wierzchowca (procent) (current_mount_health_percent)
Zwraca zdrowie wierzchowca w procentach.
```
{"placeholder":"current_mount_health_percent"}
```
Przykładowy wynik: `100`

## Bieżący wskaźnik skoku wierzchowca (procent) (current_mount_jump_meter)
Zwraca wartość wskaźnika siły skoku wierzchowca.
```
{"placeholder":"current_mount_jump_meter"}
```
Przykładowy wynik: `75`

## Bieżące zdrowie bossa (procent) (current_boss_health)
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

## Wybrany slot hotbara (active_hotbar_slot)
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
Zwraca liczbę sztuk przedmiotu w określonym slocie ekwipunku gracza.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Przykładowy wynik: `64`

## Wytrzymałość przedmiotu w slocie (slot_item_durability)
Zwraca informacje o wytrzymałości przedmiotu w określonym slocie ekwipunku gracza.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parametry:
- `slot`: Numer slota w ekwipunku gracza.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` lub `percent`.

Przykładowy wynik: `87`

## Nazwa wyświetlana przedmiotu w slocie (slot_item_display_name_fm)
Zwraca nazwę wyświetlaną przedmiotu w określonym slocie jako komponent tekstowy JSON. W trybie obserwatora sloty hotbara mogą zwracać nazwy pozycji menu obserwatora, chyba że `ignore_spectator` ma wartość `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Przykładowy wynik: `{"text":"Diamond Sword","color":"aqua"}`

## Liczba przedmiotów w ekwipunku (inventory_item_count)
Zwraca łączną liczbę przedmiotów danego typu w ekwipunku gracza. Jeśli `item` jest puste, liczy wszystkie stosy przedmiotów w ekwipunku.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Przykładowy wynik: `12`

## Ilość punktów głodu przywracanych przez przedmiot w slocie ekwipunku (inventory_slot_food_point_restore_amount)
Zwraca liczbę punktów głodu przywracanych przez przedmiot spożywczy w danym slocie ekwipunku gracza.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Przykładowy wynik: `4.0`

## Przedmiot w podświetlonym slocie ekwipunku (hovered_inventory_item)
Zwraca klucz przedmiotu aktualnie wskazywanego w ekranie ekwipunku.
```
{"placeholder":"hovered_inventory_item"}
```
Przykładowy wynik: `minecraft:apple`

## Czas gry świata (game_time)
Zwraca bieżący licznik ticków czasu gry.
```
{"placeholder":"game_time"}
```
Przykładowy wynik: `18000`

## Czas dnia świata (world_daytime)
Zwraca bieżący czas dnia w świecie.
```
{"placeholder":"world_daytime"}
```
Przykładowy wynik: `13000`

## Godzina czasu dnia świata (world_daytime_hour)
Zwraca godzinę z czasu świata. Domyślnie używa formatu 24-godzinnego; ustaw `twelve_hour_format` na `"true"`, aby użyć formatu 12-godzinnego.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Przykładowy wynik: `12`

## Minuta czasu dnia świata (world_daytime_minute)
Zwraca minutę z czasu świata (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Przykładowy wynik: `30`

## Trudność świata (world_difficulty)
Zwraca bieżącą trudność świata.
```
{"placeholder":"world_difficulty"}
```
Przykładowy wynik: `normal`

## Bieżące ziarno świata (current_world_seed)
Zwraca ziarno aktualnego świata jednoosobowego. Zwraca pustą wartość, gdy ziarno nie jest dostępne.
```
{"placeholder":"current_world_seed"}
```
Przykładowy wynik: `123456789`

## Bieżący biom (current_biome)
Zwraca biom, w którym aktualnie znajduje się gracz. Ustaw `as_key` na `"false"`, aby zwrócić tłumaczoną/wyświetlaną nazwę, jeśli jest dostępna.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Przykładowy wynik: `minecraft:plains`

## Bieżący wymiar (current_dimension)
Zwraca wymiar, w którym aktualnie znajduje się gracz. Ustaw `as_key` na `"false"`, aby zwrócić tłumaczoną/wyświetlaną nazwę, jeśli jest dostępna.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Przykładowy wynik: `minecraft:overworld`

## Wartość gamerule (gamerule_value)
Zwraca bieżącą wartość gamerule w załadowanym świecie/serwerze. Światy serwerowe wymagają FancyMenu na serwerze.
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

## Bieżący tytuł/podtytuł HUD (current_title)
Zwraca aktualnie wyświetlany tekst tytułu.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Przykładowy wynik: `Game Over!`

## Wiadomość paska akcji (action_bar_message_fm)
Zwraca bieżącą vanillową wiadomość paska akcji nad hotbarem.
```
{"placeholder":"action_bar_message_fm"}
```
Przykładowy wynik: `You may not rest now`

## Czas wiadomości paska akcji (action_bar_message_time_fm)
Zwraca, przez ile ticków bieżąca vanillowa wiadomość paska akcji będzie jeszcze wyświetlana.
```
{"placeholder":"action_bar_message_time_fm"}
```
Przykładowy wynik: `42`

## Obrót kamery X (camera_rotation_x_fm)
Zwraca bieżące pochylenie kamery w stopniach.
```
{"placeholder":"camera_rotation_x_fm"}
```
Przykładowy wynik: `12.5`

## Obrót kamery Y (camera_rotation_y_fm)
Zwraca bieżący obrót kamery w poziomie w stopniach.
```
{"placeholder":"camera_rotation_y_fm"}
```
Przykładowy wynik: `-90.0`

## Zmiana obrotu kamery X (camera_rotation_delta_x_fm)
Zwraca zmianę pochylenia kamery na tick.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Przykładowy wynik: `0.4`

## Zmiana obrotu kamery Y (camera_rotation_delta_y_fm)
Zwraca zmianę obrotu kamery w poziomie na tick.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Przykładowy wynik: `-1.2`

## Czas podświetlonego przedmiotu (highlighted_item_time_fm)
Zwraca, przez ile ticków nazwa podświetlonego przedmiotu będzie jeszcze wyświetlana nad hotbarem.
```
{"placeholder":"highlighted_item_time_fm"}
```
Przykładowy wynik: `30`

## Postęp używania przedmiotu przez gracza (player_item_use_progress_fm)
Zwraca bieżący postęp używania przedmiotu od `0.0` do `1.0`.
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

## Bieżące IP serwera (current_server_ip)
Zwraca adres IP połączonego serwera.
```
{"placeholder":"current_server_ip"}
```
Przykładowy wynik: `mc.hypixel.net`

## Lista graczy w świecie (world_players_list)
Zwraca listę wszystkich graczy aktualnie obecnych w świecie.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Przykładowy wynik: `Steve, Alex, Notch`

## MOTD serwera (servermotd)
Zwraca Message of the Day serwera.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Przykładowy wynik: `Welcome to Hypixel!`

## PING serwera (serverping)
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
Zwraca bieżący rok.
```
{"placeholder":"realtimeyear"}
```
Przykładowy wynik: `2024`

## Miesiąc (realtimemonth)
Zwraca bieżący miesiąc (01-12).
```
{"placeholder":"realtimemonth"}
```
Przykładowy wynik: `01`

## Dzień (realtimeday)
Zwraca bieżący dzień miesiąca (01-31).
```
{"placeholder":"realtimeday"}
```
Przykładowy wynik: `27`

## Godzina (realtimehour)
Zwraca bieżącą godzinę. Domyślnie używa formatu 24-godzinnego; ustaw `twelve_hour_format` na `"true"`, aby użyć formatu 12-godzinnego.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Przykładowy wynik: `14`

## Minuta (realtimeminute)
Zwraca bieżącą minutę (00-59).
```
{"placeholder":"realtimeminute"}
```
Przykładowy wynik: `30`

## Sekunda (realtimesecond)
Zwraca bieżącą sekundę (00-59).
```
{"placeholder":"realtimesecond"}
```
Przykładowy wynik: `45`

## Bieżący czas w milisekundach (znacznik czasu Unix) (unix_time)
Zwraca bieżący znacznik czasu Unix w milisekundach.
```
{"placeholder":"unix_time"}
```
Przykładowy wynik: `1716552478123`

> Placeholders czasu rzeczywistego (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` i `unix_time`) obsługują wartość `timezone`. Używaj standardowych identyfikatorów stref czasowych Java, takich jak `UTC`, `Europe/Berlin` lub `America/New_York`; pomiń ją lub użyj `system`, aby skorzystać ze strefy czasowej systemu.
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

## Użycie CPU (system operacyjny) (oscpu)
Zwraca użycie CPU przez system operacyjny w procentach.
```
{"placeholder":"oscpu"}
```
Przykładowy wynik: `42.8`

## Informacje o GPU (gpuinfo)
Zwraca informacje o GPU.
```
{"placeholder":"gpuinfo"}
```
Przykładowy wynik: `NVIDIA GeForce RTX 3080`

## Wersja Javy (javaver)
Zwraca wersję Javy.
```
{"placeholder":"javaver"}
```
Przykładowy wynik: `17.0.2`

## Maszyna wirtualna Javy (jvmname)
Zwraca nazwę Java Virtual Machine.
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
Zwraca bieżącą liczbę klatek na sekundę.
```
{"placeholder":"fps"}
```
Przykładowy wynik: `120`

## Używany RAM w MB (usedram)
Zwraca ilość aktualnie używanej pamięci RAM (MB).
```
{"placeholder":"usedram"}
```
Przykładowy wynik: `4096`

## Maksymalny RAM w MB (maxram)
Zwraca maksymalnie przydzieloną pamięć RAM (MB).
```
{"placeholder":"maxram"}
```
Przykładowy wynik: `8192`

## Używany RAM w %% (percentram)
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
Zwraca bieżący czas odtwarzania utworu audio. Ustaw `show_percentage` na `"true"`, aby otrzymać wartość postępu 0-100 zamiast formatu MM:SS.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Przykładowy wynik: `01:30` (lub `45`, gdy `show_percentage` ma wartość `"true"`)

## Stan odtwarzania audio (audio_playing_state)
Zwraca, czy element audio jest odtwarzany (true/false).
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
Zwraca bieżący czas odtwarzania (postęp) elementu wideo w formacie `MM:SS`. Ustaw `show_percentage` na `"true"`, aby otrzymać wartość postępu 0-100, lub `output_as_timestamp` na `"true"`, aby otrzymać milisekundy.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Przykładowy wynik: `00:45` (lub `38` jako procent, albo `45200` jako znacznik czasu)

## Stan pauzy elementu wideo (video_element_paused_state)
Zwraca, czy element wideo jest wstrzymany (true/false).
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
Zwraca bieżący czas odtwarzania (postęp) tła wideo menu w formacie `MM:SS`. Ustaw `show_percentage` na `"true"`, aby otrzymać wartość postępu 0-100, lub `output_as_timestamp` na `"true"`, aby otrzymać milisekundy.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Przykładowy wynik: `01:00` (lub `33` jako procent, albo `60500` jako znacznik czasu)

## Stan pauzy tła wideo (video_background_paused_state)
Zwraca, czy tło wideo menu jest wstrzymane (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Przykładowy wynik: `true`

## Kalkulator (calc)
Placeholder kalkulatora to potężne narzędzie, które pozwala wykonywać obliczenia matematyczne w obrębie Twoich układów. Obsługuje szeroki zakres działań matematycznych i może pracować zarówno z liczbami dziesiętnymi, jak i całkowitymi.

### Podstawowa składnia
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

Kalkulator ma dwa główne parametry:
- `decimal`: Określa, czy wynik ma zawierać miejsca po przecinku (`true`), czy być zaokrąglony do liczb całkowitych (`false`)
- `expression`: Wyrażenie matematyczne do obliczenia

### Obsługiwane operacje
Kalkulator obsługuje następujące działania matematyczne:
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
Zwraca wartość przeciwną liczby.
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

## Funkcja sinus (Matematyka) (math_sin)
Zwraca sinus kąta.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Przykładowy wynik: `0.7071067811865476`

## Funkcja cosinus (Matematyka) (math_cos)
Zwraca cosinus kąta.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Przykładowy wynik: `0.7071067811865476`

## Funkcja tangens (Matematyka) (math_tan)
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
Zaokrągla liczbę. Domyślnie do najbliższej liczby całkowitej; ustaw `decimals` na nieujemną liczbę, aby zaokrąglić do tylu miejsc po przecinku.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Przykładowy wynik: `3.14` (przy `decimals:-1` lub bez wartości → `3`)

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

## Przytnij tekst na krawędziach (crop_text)
Usuwa znaki z początku i końca tekstu.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Przykładowy wynik: `ello worl`

## Stringify (stringify)
Konwertuje tekst, escape’ując wszystkie znaki składni.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Przykładowy wynik: `text with \{special\} \"characters\"`

## Lokalizuj tekst (local)
Pobiera zlokalizowany tekst dla podanego klucza.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Przykładowy wynik: `Singleplayer`

## Tekst z sieci (webtext)
Pobiera treść tekstu z adresu URL.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Przykładowy wynik: Treść tekstu z adresu URL

## Losowy tekst (randomtext)
Zwraca losową linię z pliku tekstowego, adresu URL lub bezpośrednio podanego zwykłego tekstu. Tekst zmienia się w określonych odstępach czasu.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parametry:
- `source`: Źródło linii tekstu (zastępuje stary parametr `path`)
  - Ścieżka do pliku: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Zwykły tekst: `Linia 1\nLinia 2\nLinia 3`
- `interval`: Czas w sekundach między zmianami tekstu

Ten placeholder obsługuje teraz trzy typy źródeł:
1. **Pliki lokalne**: Pliki tekstowe z katalogu gry
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URL-e**: Zdalne pliki tekstowe z internetu
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Zwykły tekst**: Bezpośrednio wpisany tekst z liniami rozdzielonymi `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Uwaga: stare placeholdery używające `path` zamiast `source` nadal będą działać.

## Parser JSON (json)
Parsuje dane JSON z pliku, URL-a lub bezpośrednio podanej zawartości JSON i wyodrębnia wartości przy użyciu wyrażeń JSON path.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parametry:
- `source`: Źródło danych JSON
  - Ścieżka do pliku: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Bezpośredni JSON: `{"name":"Steve","level":42}`
- `json_path`: Wyrażenie JSON path do wyodrębnienia danych

Ten placeholder obsługuje teraz trzy typy źródeł:
1. **Pliki lokalne**: Pliki JSON z katalogu gry
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL-e**: Zdalne dane JSON z API lub usług webowych
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Bezpośredni JSON**: Wstawiona bezpośrednio zawartość JSON
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Przykładowe ścieżki JSON:
- `$.name` - Pobiera pole "name" z poziomu głównego
- `$.player.level` - Pobiera zagnieżdżone pole "level" wewnątrz "player"
- `$.items[0].id` - Pobiera "id" pierwszego elementu w tablicy
- `$.scores.*` - Pobiera wszystkie wartości z obiektu "scores"

## Absolutna ścieżka pliku/folderu (absolute_path)
Zwraca absolutną ścieżkę pliku.
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
Zwraca szerokość w pikselach podanego tekstu po wyrenderowaniu.
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

## Tekst w tytule (title_case_text)
Konwertuje tekst wejściowy do formatu Title Case.
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
Konwertuje tekst wejściowy do `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Przykładowy wynik: `hello_world`

## Tekst w kebab-case (kebab_case_text)
Konwertuje tekst wejściowy do `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Przykładowy wynik: `hello-world`

## Naprzemienna wielkość liter (alternating_case_text)
Konwertuje tekst wejściowy do naprzemiennej wielkości liter.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Przykładowy wynik: `aLtErNaTiNg CaSe`

## Przełącz wielkość liter (toggle_case_text)
Przełącza wielkość każdej litery w tekście wejściowym.
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
- `path_or_url`: Ścieżka do pliku lub URL, z którego należy odczytać dane
- `mode`: `"all"` (zwraca wszystkie linie) albo `"last"` (zwraca tylko ostatnie X linii)
- `separator`: Tekst używany do łączenia linii (domyślnie: `"\n"`)
- `last_lines`: Liczba linii do zwrócenia, gdy `mode` ma wartość `"last"` (domyślnie: `"1"`)

Przykładowy wynik: Zależy od zawartości pliku

## Zawartość schowka (clipboard_content)
Zwraca bieżącą treść tekstową przechowywaną w schowku systemowym.
```
{"placeholder":"clipboard_content"}
```
Przykładowy wynik: Dowolny tekst aktualnie znajdujący się w schowku

## Zastąp tekst (replace_text)
Zastępuje tekst w ciągu przy użyciu tekstu dosłownego lub wyrażeń regularnych.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parametry:
- `text`: Tekst wejściowy do przetworzenia
- `search`: Tekst lub wzorzec regex do wyszukania
- `replacement`: Tekst zastępujący
- `use_regex`: Czy używać regex (`"true"`), czy dopasowania dosłownego (`"false"`)
- `replace_all`: Zastąp wszystkie wystąpienia (`"true"`) czy tylko pierwsze (`"false"`)

Przykładowy wynik: `Hello FancyMenu! This is a test.`

## Instrukcja switch-case (switch_case)
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
Pobiera dane NBT po stronie klienta (podobnie jak komenda `/data get`). Użyj wariantu serwerowego `nbt_data_get_server`, gdy jesteś połączony z serwerem i potrzebujesz autorytatywnych wartości po stronie serwera.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parametry:
- `source_type`: `"entity"` lub `"block"`
- `entity_selector`: selektor encji, np. `@s`, `@p`, `@e` albo UUID/nazwa (dla encji)
- `block_pos`: pozycja bloku w formacie `"x y z"` (dla bloków)
- `nbt_path`: ścieżka NBT do pobrania
- `scale`: opcjonalny współczynnik skalowania dla wartości liczbowych (domyślnie: `"1.0"`)
- `return_type`: sposób zwracania danych:
  - `"value"`: domyślnie, zwraca wartość (z opcjonalnym skalowaniem dla liczb)
  - `"string"`: zwraca rzeczywiste dane NBT jako ciąg
  - `"snbt"`: zwraca jako SNBT (formatowany NBT)
  - `"json"`: zwraca jako komponent sformatowany JSON (dla tagów compound)

Przykładowy wynik: `20` (dla poziomu głodu)

## Pobierz dane NBT (po stronie serwera) (nbt_data_get_server)
Pyta o dane NBT po stronie serwera (używając pakietu) i krótko buforuje wyniki. Wartości odpowiadają placeholderowi po stronie klienta.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Przykładowy wynik: `minecraft:diamond_sword`

## Ostatnia wiadomość śmierci (lastdeathmessage)
Zwraca ostatnio zapisaną wiadomość śmierci klienta-gracza. Ustaw `as_json_component` na `"true"`, aby uzyskać surowy komponent tekstowy JSON.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Przykładowy wynik: `Steve was slain by Zombie`

## Czas działania (uptime_duration)
Zwraca czas, od jakiego załadowane jest FancyMenu. Domyślnie wartość podawana jest w sekundach; ustaw `output_as_millis` na `"true"`, aby otrzymać milisekundy.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Przykładowy wynik: `742` (sekundy od załadowania)

## Nazwy zapisów świata (level_save_names)
Wyświetla wszystkie lokalne nazwy zapisów świata połączone wybranym separatorem. Działa w wątku klienta.
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
Konwertuje liczbę (całkowitą lub ułamkową) z jednej podstawy do innej (2–36). Domyślnie używa systemu dziesiętnego, jeśli podstawy nie zostaną podane.
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
Zwraca hash MD5 lokalnego pliku jako mały łańcuch szesnastkowy.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Przykładowy wynik: `d41d8cd98f00b204e9800998ecf8427e`

# Praktyczne przykłady

## Tworzenie dynamicznego wyświetlacza pamięci
```
Używany RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Tworzenie zegara czasu rzeczywistego
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Tworzenie wyświetlacza informacji o systemie
```
OS: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD stanu gracza
```
Zdrowie: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Zbroja: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Poziom XP: {"placeholder":"current_player_level"}
```

## Złożone obliczenie z zagnieżdżonymi placeholderami
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Wyświetlanie współrzędnych z zaokrągleniem
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Najlepsze praktyki

1. **Buforuj kosztowne operacje**: Niektóre placeholdery (np. te odczytujące informacje o systemie) mogą być zasobożerne. Rozważ użycie zmiennych do przechowywania ich wartości, jeśli potrzebujesz używać ich wielokrotnie.

2. **Używaj odpowiednich ustawień dziesiętnych**: Podczas wykonywania obliczeń używaj parametru `decimal` odpowiednio. Ustaw go na `false`, gdy potrzebujesz liczb całkowitych, i na `true`, gdy potrzebujesz dokładnych wartości dziesiętnych.

3. **Obsługuj brakujące wartości**: Zawsze zastanów się, co ma się stać, jeśli placeholder nie zwróci żadnej wartości. W takich przypadkach możesz chcieć podać wartości domyślne.

4. **Testuj wydajność**: Podczas używania wielu placeholderów lub złożonych struktur zagnieżdżonych testuj wpływ na wydajność, zwłaszcza na słabszych systemach.

5. **Korzystaj z zaawansowanego skalowania/pozycjonowania**: W przypadku dynamicznych elementów UI łącz placeholdery z zaawansowanym skalowaniem i pozycjonowaniem, aby tworzyć responsywne układy.

6. **Łącz z zmiennymi**: Używaj placeholderów razem ze zmiennymi, aby uzyskać jeszcze bardziej dynamiczną treść, którą można aktualizować za pomocą akcji.

# Typowe problemy i rozwiązania

## Placeholder się nie aktualizuje
Jeśli wartość placeholdera nie aktualizuje się zgodnie z oczekiwaniami, sprawdź:
- czy placeholder jest poprawnie sformatowany
- czy używasz właściwej wielkości liter w identyfikatorach placeholderów
- czy placeholder wymaga spełnienia określonych warunków, aby się zaktualizować

## Zagnieżdżone placeholdery nie działają
Podczas zagnieżdżania placeholderów:
- upewnij się, że cudzysłowy są poprawnie escapowane
- sprawdź, czy każdy zagnieżdżony placeholder działa poprawnie samodzielnie

## Problemy z wydajnością
Jeśli zauważysz problemy z wydajnością:
- zmniejsz liczbę używanych placeholderów
- unikaj niepotrzebnego zagnieżdżania
- rozważ użycie zmiennych dla często używanych wartości
- używaj odpowiedniego placeholdera do swoich potrzeb (np. nie używaj placeholderów czasu rzeczywistego, gdy wystarczą wartości statyczne)
