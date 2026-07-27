---
title: Miejsca zastępcze
description: Jak używać miejsc zastępczych.
---
# Miejsca zastępcze

Miejsca zastępcze wstawiają na żywo wartości do tekstu, przycisków, wymagań i innych obsługiwanych pól.

# Informacje ogólne

## Podstawowa składnia
Miejsca zastępcze w FancyMenu używają składni podobnej do JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Na przykład, aby wyświetlić nazwę gracza:
```
{"placeholder":"playername"}
```

## Zagnieżdżanie miejsc zastępczych
Możesz użyć jednego miejsca zastępczego wewnątrz wartości innego.

Przykład zagnieżdżonych miejsc zastępczych:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Ten przykład pobiera wartość maksymalnej pamięci RAM i dzieli ją przez 1024, aby przeliczyć ją z MB na GB.

> [!IMPORTANT]
> To jest składnia FancyMenu, a nie JSON. Zagnieżdżone miejsca zastępcze używają dokładnie takiej formy jak pokazano powyżej, bez ucieczki znaków, więc formatery JSON odrzucą je lub przepiszą. Nazwy miejsc zastępczych są rozróżniane wielkością liter; nieprawidłowe lub nieznane miejsca zastępcze pozostają widoczne jako tekst i są logowane.

# Korzystanie z miejsc zastępczych

Większość elementów z polami tekstowymi obsługuje miejsca zastępcze. Podczas edycji możesz sprawdzić, czy dane pole tekstowe je obsługuje. Jeśli przy edycji tekstu otwiera się pełnoekranowy **edytor tekstu**, oznacza to, że obsługuje on miejsca zastępcze.

Aby znaleźć **listę wszystkich miejsc zastępczych**, kliknij przycisk **Miejsca zastępcze** w **prawym górnym rogu** **edytora tekstu**.

Na górze listy miejsc zastępczych znajduje się **pasek wyszukiwania**, który pozwala przeszukiwać listę.

Kliknięcie miejsca zastępczego na liście wstawi je do treści tekstu.

# Miejsca zastępcze — szczegóły

Ta sekcja zawiera wbudowane miejsca zastępcze FancyMenu.

## Niedostępne wyniki

Wynik miejsca zastępczego jest zawsze tekstem. Gdy dane są niedostępne, wynik zależy od miejsca zastępczego: typowe wartości awaryjne to pusty ciąg, `0`, `0.0`, `00:00`, `false`, `UNKNOWN` lub `ERROR`. Pozycje z określoną wartością awaryjną podają ją bezpośrednio; przetestuj wartość awaryjną, zanim użyjesz zależnego od środowiska wyniku w [wymaganiu](./conditions), ścieżce, komendzie lub adresie URL.

## Nazwa gracza (`playername`)

**Cel:** Zwraca nazwę użytkownika aktualnego gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"playername"}
```

**Wynik:** `Steve`

## UUID gracza (`playeruuid`)

**Cel:** Zwraca unikalny identyfikator gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"playeruuid"}
```

**Wynik:** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Wersja Minecrafta (`mcversion`)

**Cel:** Zwraca bieżącą wersję Minecrafta.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"mcversion"}
```

**Wynik:** `1.21.1`

## Wersja modułu ładującego (`loaderver`)

**Cel:** Zwraca wersję loadera modów (Fabric/NeoForge).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"loaderver"}
```

**Wynik:** `0.16.14`

## Nazwa loadera modów (`loadername`)

**Cel:** Zwraca nazwę loadera modów.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"loadername"}
```

**Wynik:** `Fabric`

## Wersja moda (`modversion`)

**Cel:** Zwraca wersję określonego moda.

**Wartości:** `modid`

**Przykład:**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**Wynik:** `1.2.3`

## Łączna liczba modów (`totalmods`)

**Cel:** Zwraca przybliżoną liczbę plików modów na podstawie katalogu `mods` i liczby załadowanych modów. Nie zlicza wiarygodnie każdego wyłączonego moda.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"totalmods"}
```

**Wynik:** `45`

## Liczba aktywnych modów (`loadedmods`)

**Cel:** Zwraca liczbę aktualnie załadowanych modów.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"loadedmods"}
```

**Wynik:** `43`

## Postęp ładowania świata (`world_load_progress`)

**Cel:** Zwraca bieżący postęp ładowania świata w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"world_load_progress"}
```

**Wynik:** `75`

## Wartość opcji Minecrafta (`minecraft_option_value`)

**Cel:** Zwraca wartość opcji Minecrafta.

**Wartości:** `name`

**Przykład:**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**Wynik:** `70`

## Ostatni świat lub serwer (`last_world_server`)

**Cel:** Zwraca informacje o ostatnio używanym świecie lub serwerze.

**Wartości:** `type`, `full_world_path`

**Przykład:**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parametry:
- `type`: Określa, jaki typ informacji ma zostać zwrócony
  - `"both"`: Zwraca ostatnio używany świat lub serwer (domyślnie)
  - `"server"`: Zwraca tylko wtedy, gdy ostatnio używany był serwer
  - `"world"`: Zwraca tylko wtedy, gdy ostatnio używany był świat
- `full_world_path`: Kontroluje sposób wyświetlania ścieżek świata
  - `"true"`: Zwraca pełną ścieżkę świata (domyślnie)
  - `"false"`: Zwraca tylko nazwę świata bez ścieżki (nie dotyczy serwerów)

Przykłady:
- Serwer: `mc.hypixel.net`
- Świat z pełną ścieżką: `saves/New World`
- Świat bez pełnej ścieżki: `New World`

## Szerokość ekranu (`guiwidth`)

**Cel:** Zwraca bieżącą szerokość ekranu w pikselach przeskalowanych przez GUI, a nie fizycznych pikselach monitora.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"guiwidth"}
```

**Wynik:** `960`

## Wysokość ekranu (`guiheight`)

**Cel:** Zwraca bieżącą wysokość ekranu w pikselach przeskalowanych przez GUI, a nie fizycznych pikselach monitora.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"guiheight"}
```

**Wynik:** `540`

## Identyfikator bieżącego ekranu (`screenid`)

**Cel:** Zwraca identyfikator bieżącego ekranu.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"screenid"}
```

**Wynik:** `title_screen`

## Szerokość elementu (`elementwidth`)

**Cel:** Zwraca szerokość określonego elementu.

**Wartości:** `id`

**Przykład:**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**Wynik:** `200`

## Wysokość elementu (`elementheight`)

**Cel:** Zwraca wysokość określonego elementu.

**Wartości:** `id`

**Przykład:**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**Wynik:** `20`

## Pozycja X elementu (`elementposx`)

**Cel:** Zwraca pozycję X określonego elementu.

**Wartości:** `id`

**Przykład:**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**Wynik:** `150`

## Pozycja Y elementu (`elementposy`)

**Cel:** Zwraca pozycję Y określonego elementu.

**Wartości:** `id`

**Przykład:**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**Wynik:** `100`

## Pozycja X myszy (`mouseposx`)

**Cel:** Zwraca bieżącą pozycję X myszy.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"mouseposx"}
```

**Wynik:** `960`

## Pozycja Y myszy (`mouseposy`)

**Cel:** Zwraca bieżącą pozycję Y myszy.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"mouseposy"}
```

**Wynik:** `540`

## Kliknięcia na sekundę (`clicks_per_second`)

**Cel:** Zwraca bieżącą liczbę kliknięć na sekundę dla przycisku myszy.

**Wartości:** `mouse_button`

**Przykład:**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parametry:
- `mouse_button`: `left` lub `right`

**Wynik:** `8`

## Skala GUI (`guiscale`)

**Cel:** Zwraca bieżącą skalę GUI.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"guiscale"}
```

**Wynik:** `2`

## Etykieta/tekst widżetu waniliowego (`vanillabuttonlabel`)

**Cel:** Zwraca etykietę/tekst waniliowego widżetu/przycisku.

**Wartości:** `locator`

**Przykład:**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**Wynik:** `Options...`

## Wartość pola tekstowego (`text_input_field_value`)

**Cel:** Zwraca bieżącą wartość niestandardowego lub waniliowego pola tekstowego na podstawie identyfikatora elementu.

**Wartości:** `element_identifier`

**Przykład:**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**Wynik:** `Hello World`

## Bieżące zdrowie gracza (`current_player_health`)

**Cel:** Zwraca bieżące punkty zdrowia gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_health"}
```

**Wynik:** `20.0`

## Maksymalne zdrowie gracza (`max_player_health`)

**Cel:** Zwraca maksymalną liczbę punktów zdrowia gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"max_player_health"}
```

**Wynik:** `20.0`

## Bieżące zdrowie gracza (procent) (`current_player_health_percent`)

**Cel:** Zwraca zdrowie gracza w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_health_percent"}
```

**Wynik:** `100`

## Bieżące zdrowie absorpcji gracza (`current_player_absorption_health`)

**Cel:** Zwraca punkty zdrowia absorpcji gracza (złote serca).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_absorption_health"}
```

**Wynik:** `4.0`

## Maksymalne zdrowie absorpcji gracza (`max_player_absorption_health`)

**Cel:** Zwraca maksymalne zdrowie absorpcji.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"max_player_absorption_health"}
```

**Wynik:** `4.0`

## Bieżące zdrowie absorpcji gracza (procent) (`current_player_absorption_health_percent`)

**Cel:** Zwraca zdrowie absorpcji gracza w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**Wynik:** `100`

## Bieżący poziom głodu gracza (`current_player_hunger`)

**Cel:** Zwraca bieżący poziom głodu gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_hunger"}
```

**Wynik:** `20`

## Maksymalny poziom głodu gracza (`max_player_hunger`)

**Cel:** Zwraca maksymalny poziom głodu.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"max_player_hunger"}
```

**Wynik:** `20`

## Bieżący poziom głodu gracza (procent) (`current_player_hunger_percent`)

**Cel:** Zwraca głód gracza w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_hunger_percent"}
```

**Wynik:** `100`

## Bieżąca saturacja głodu gracza (`current_player_hunger_saturation`)

**Cel:** Zwraca bieżącą wartość saturacji głodu gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_hunger_saturation"}
```

**Wynik:** `5.0`

## Bieżąca zbroja gracza (`current_player_armor`)

**Cel:** Zwraca bieżącą wartość zbroi gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_armor"}
```

**Wynik:** `20`

## Wytrzymałość zbroi gracza (`player_armor_toughness`)

**Cel:** Zwraca łączną wartość wytrzymałości zbroi gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_armor_toughness"}
```

**Wynik:** `8.0`

## Maksymalna zbroja gracza (`max_player_armor`)

**Cel:** Zwraca maksymalną wartość zbroi.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"max_player_armor"}
```

**Wynik:** `20`

## Bieżąca zbroja gracza (procent) (`current_player_armor_percent`)

**Cel:** Zwraca zbroję gracza w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_armor_percent"}
```

**Wynik:** `100`

## Bieżący poziom tlenu gracza (`current_player_oxygen`)

**Cel:** Zwraca bieżący poziom tlenu gracza (bąbelki powietrza).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_oxygen"}
```

**Wynik:** `300`

## Maksymalny poziom tlenu gracza (`max_player_oxygen`)

**Cel:** Zwraca maksymalny poziom tlenu.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"max_player_oxygen"}
```

**Wynik:** `300`

## Bieżący poziom tlenu gracza (procent) (`current_player_oxygen_percent`)

**Cel:** Zwraca poziom tlenu gracza w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_oxygen_percent"}
```

**Wynik:** `100`

## Bieżący poziom doświadczenia gracza (`current_player_level`)

**Cel:** Zwraca bieżący poziom doświadczenia gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_level"}
```

**Wynik:** `30`

## Bieżące doświadczenie gracza (`current_player_exp`)

**Cel:** Zwraca całkowitą liczbę punktów doświadczenia gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_exp"}
```

**Wynik:** `1250`

## Postęp doświadczenia gracza (procent) (`current_player_exp_progress`)

**Cel:** Zwraca postęp doświadczenia gracza do następnego poziomu w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_player_exp_progress"}
```

**Wynik:** `75`

## Siła ataku gracza (procent) (`player_attack_strength`)

**Cel:** Zwraca odnowienie ataku gracza w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_attack_strength"}
```

**Wynik:** `100`

## Tryb gry gracza (`player_gamemode`)

**Cel:** Zwraca bieżący tryb gry gracza.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_gamemode"}
```

**Wynik:** `survival`

## Kierunek patrzenia gracza (`player_view_direction`)

**Cel:** Zwraca kierunek, w którym patrzy gracz.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_view_direction"}
```

**Wynik:** `north`

## Współrzędna X gracza (`player_x_coordinate`)

**Cel:** Zwraca pozycję X gracza w świecie.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_x_coordinate"}
```

**Wynik:** `125`

## Współrzędna Y gracza (`player_y_coordinate`)

**Cel:** Zwraca pozycję Y gracza w świecie.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_y_coordinate"}
```

**Wynik:** `64`

## Współrzędna Z gracza (`player_z_coordinate`)

**Cel:** Zwraca pozycję Z gracza w świecie.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_z_coordinate"}
```

**Wynik:** `-250`

## Bieżące zdrowie wierzchowca (`current_mount_health`)

**Cel:** Zwraca bieżące zdrowie jednostki, na której jedzie gracz.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_mount_health"}
```

**Wynik:** `30.0`

## Maksymalne zdrowie wierzchowca (`max_mount_health`)

**Cel:** Zwraca maksymalne zdrowie jednostki, na której jedzie gracz.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"max_mount_health"}
```

**Wynik:** `30.0`

## Bieżące zdrowie wierzchowca (procent) (`current_mount_health_percent`)

**Cel:** Zwraca zdrowie wierzchowca w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_mount_health_percent"}
```

**Wynik:** `100`

## Bieżący wskaźnik skoku wierzchowca (procent) (`current_mount_jump_meter`)

**Cel:** Zwraca wartość wskaźnika mocy skoku wierzchowca.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_mount_jump_meter"}
```

**Wynik:** `75`

## Bieżące zdrowie bossa (procent) (`current_boss_health`)

**Cel:** Zwraca zdrowie wybranego aktywnego bossa jako liczbę całkowitą od `0` do `100`. `boss_index` jest indeksowany od zera; `0` wybiera pierwszy pasek bossa.

**Wartości:** `boss_index`

**Przykład:**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**Wynik:** `75`

## Nazwa bossa (`boss_name`)

**Cel:** Zwraca nazwę aktywnego bossa.

**Wartości:** `boss_index`, `as_json`

**Przykład:**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**Wynik:** `Ender Dragon`

## Liczba bossów (`boss_count`)

**Cel:** Zwraca liczbę aktywnych bossów.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"boss_count"}
```

**Wynik:** `1`

## Liczba aktywnych efektów (`effects_count`)

**Cel:** Zwraca liczbę aktywnych efektów mikstur.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"effects_count"}
```

**Wynik:** `3`

## Aktywny efekt (`active_effect`)

**Cel:** Zwraca informacje o określonym aktywnym efekcie.

**Wartości:** `effect_index`

**Przykład:**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**Wynik:** `minecraft:speed`

## Wybrany slot paska szybkiego dostępu (`active_hotbar_slot`)

**Cel:** Zwraca aktualnie wybrany slot paska szybkiego dostępu (0-8).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"active_hotbar_slot"}
```

**Wynik:** `4`

## Przedmiot w slocie (`slot_item`)

**Cel:** Zwraca informacje o przedmiocie w określonym slocie ekwipunku.

**Wartości:** `slot`

**Przykład:**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**Wynik:** `minecraft:diamond_sword`

## Liczba przedmiotów w slocie (`slot_item_count`)

**Cel:** Zwraca liczbę sztuk przedmiotu w określonym slocie ekwipunku gracza.

**Wartości:** `slot`

**Przykład:**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**Wynik:** `64`

## Trwałość przedmiotu w slocie (`slot_item_durability`)

**Cel:** Zwraca informacje o trwałości przedmiotu w określonym slocie ekwipunku gracza.

**Wartości:** `slot`, `format`

**Przykład:**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parametry:
- `slot`: Numer slota w ekwipunku gracza.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` lub `percent`.

**Wynik:** `87`

## Nazwa wyświetlana przedmiotu w slocie (`slot_item_display_name_fm`)

**Cel:** Zwraca nazwę wyświetlaną przedmiotu w określonym slocie jako komponent tekstowy JSON. W trybie widza sloty paska szybkiego dostępu mogą zwracać nazwy przedmiotów menu widza, chyba że `ignore_spectator` ma wartość `true`.

**Wartości:** `slot`, `ignore_spectator`

**Przykład:**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**Wynik:** `{"text":"Diamond Sword","color":"aqua"}`

## Liczba przedmiotów w ekwipunku (`inventory_item_count`)

**Cel:** Zwraca łączną liczbę pasujących przedmiotów w ekwipunku gracza. Gdy `item` jest puste, sumuje liczbę sztuk we wszystkich zajętych slotach ekwipunku.

**Wartości:** `item`

**Przykład:**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**Wynik:** `12`

## Ilość punktów głodu przywracanych przez żywność w slocie ekwipunku (`inventory_slot_food_point_restore_amount`)

**Cel:** Zwraca liczbę punktów głodu przywracanych przez jedzenie znajdujące się w danym slocie ekwipunku gracza.

**Wartości:** `slot`

**Przykład:**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**Wynik:** `4.0`

## Przedmiot pod kursorem w ekwipunku (`hovered_inventory_item`)

**Cel:** Zwraca klucz przedmiotu, na który aktualnie wskazuje kursor w ekranie ekwipunku.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"hovered_inventory_item"}
```

**Wynik:** `minecraft:apple`

## Czas gry świata (`game_time`)

**Cel:** Zwraca bieżący licznik ticków czasu w grze.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"game_time"}
```

**Wynik:** `18000`

## Dzienne światowe czasu (`world_daytime`)

**Cel:** Zwraca bieżący dzienny czas świata.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"world_daytime"}
```

**Wynik:** `13000`

## Godzina dziennego czasu świata (`world_daytime_hour`)

**Cel:** Zwraca komponent godziny czasu świata. Domyślnie używa formatu 24-godzinnego; ustaw `twelve_hour_format` na `"true"`, aby użyć formatu 12-godzinnego.

**Wartości:** `twelve_hour_format`

**Przykład:**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**Wynik:** `12`

## Minuta dziennego czasu świata (`world_daytime_minute`)

**Cel:** Zwraca komponent minut czasu świata (00-59).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"world_daytime_minute"}
```

**Wynik:** `30`

## Trudność świata (`world_difficulty`)

**Cel:** Zwraca bieżącą trudność świata.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"world_difficulty"}
```

**Wynik:** `normal`

## Bieżący seed świata (`current_world_seed`)

**Cel:** Zwraca seed bieżącego świata jednoosobowego. Zwraca pustą wartość, gdy seed nie jest dostępny.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_world_seed"}
```

**Wynik:** `123456789`

## Bieżący biom (`current_biome`)

**Cel:** Zwraca biom, w którym aktualnie znajduje się gracz. Ustaw `as_key` na `"false"`, aby zwrócić przetłumaczoną/wyświetlaną nazwę, jeśli jest dostępna.

**Wartości:** `as_key`

**Przykład:**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**Wynik:** `minecraft:plains`

## Bieżący wymiar (`current_dimension`)

**Cel:** Zwraca wymiar, w którym aktualnie znajduje się gracz. Ustaw `as_key` na `"false"`, aby zwrócić przetłumaczoną/wyświetlaną nazwę, jeśli jest dostępna.

**Wartości:** `as_key`

**Przykład:**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**Wynik:** `minecraft:overworld`

## Wartość gamerule (`gamerule_value`)

**Cel:** Zwraca bieżącą wartość reguły gry w załadowanym świecie/serwerze. Światy serwerowe wymagają FancyMenu na serwerze.

**Wartości:** `name`

**Przykład:**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**Wynik:** `true`

## Kategoria przedmiotu (`item_category`)

**Cel:** Zwraca kategorię zakładki kreatywnej dla przedmiotu. Ustaw `as_key` na `"true"`, aby zwrócić klucz kategorii zamiast nazwy wyświetlanej.

**Wartości:** `item`, `as_key`

**Przykład:**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**Wynik:** `Combat`

## Aktualny tytuł/podtytuł HUD (`current_title`)

**Cel:** Zwraca aktualnie wyświetlany tekst tytułu.

**Wartości:** `is_subtitle`, `as_json`

**Przykład:**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**Wynik:** `Game Over!`

## Wiadomość paska akcji (`action_bar_message_fm`)

**Cel:** Zwraca aktualną waniliową wiadomość paska akcji jako serializowany komponent tekstowy Minecrafta.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"action_bar_message_fm"}
```

**Wynik:** `{"text":"You may not rest now","color":"red"}`

## Czas wiadomości paska akcji (`action_bar_message_time_fm`)

**Cel:** Zwraca, przez ile ticków bieżąca waniliowa wiadomość paska akcji będzie jeszcze wyświetlana.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"action_bar_message_time_fm"}
```

**Wynik:** `42`

## Obrót kamery X (`camera_rotation_x_fm`)

**Cel:** Zwraca bieżący pitch kamery w stopniach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"camera_rotation_x_fm"}
```

**Wynik:** `12.5`

## Obrót kamery Y (`camera_rotation_y_fm`)

**Cel:** Zwraca bieżący yaw kamery w stopniach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"camera_rotation_y_fm"}
```

**Wynik:** `-90.0`

## Zmiana obrotu kamery X (`camera_rotation_delta_x_fm`)

**Cel:** Zwraca zmianę pitch kamery na tick.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**Wynik:** `0.4`

## Zmiana obrotu kamery Y (`camera_rotation_delta_y_fm`)

**Cel:** Zwraca zmianę yaw kamery na tick.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**Wynik:** `-1.2`

## Czas podświetlonego przedmiotu (`highlighted_item_time_fm`)

**Cel:** Zwraca, przez ile ticków nazwa podświetlonego przedmiotu będzie jeszcze wyświetlana nad paskiem szybkiego dostępu.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"highlighted_item_time_fm"}
```

**Wynik:** `30`

## Postęp używania przedmiotu przez gracza (`player_item_use_progress_fm`)

**Cel:** Zwraca bieżący postęp używania przedmiotu od `0.0` do `1.0`.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_item_use_progress_fm"}
```

**Wynik:** `0.65`

## Zmiana pozycji gracza X (`player_position_delta_x_fm`)

**Cel:** Zwraca zmianę pozycji gracza na osi X na tick.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_position_delta_x_fm"}
```

**Wynik:** `0.0`

## Zmiana pozycji gracza Y (`player_position_delta_y_fm`)

**Cel:** Zwraca zmianę pozycji gracza na osi Y na tick.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_position_delta_y_fm"}
```

**Wynik:** `-0.08`

## Zmiana pozycji gracza Z (`player_position_delta_z_fm`)

**Cel:** Zwraca zmianę pozycji gracza na osi Z na tick.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"player_position_delta_z_fm"}
```

**Wynik:** `0.12`

## Bieżący adres IP serwera (`current_server_ip`)

**Cel:** Zwraca adres IP połączonego serwera.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"current_server_ip"}
```

**Wynik:** `mc.hypixel.net`

## Lista graczy w świecie (`world_players_list`)

**Cel:** Zwraca listę wszystkich graczy aktualnie znajdujących się w świecie.

**Wartości:** `separator`

**Przykład:**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**Wynik:** `Steve, Alex, Notch`

## MOTD serwera (`servermotd`)

**Cel:** Zwraca wiadomość dnia serwera.

**Wartości:** `ip`, `line`

**Przykład:**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**Wynik:** `Welcome to Hypixel!`

## Ping serwera (`serverping`)

**Cel:** Zwraca ping do serwera w milisekundach.

**Wartości:** `ip`

**Przykład:**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**Wynik:** `54`

## Liczba graczy na serwerze (`serverplayercount`)

**Cel:** Zwraca liczbę graczy na serwerze.

**Wartości:** `ip`

**Przykład:**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**Wynik:** `25000/30000`

## Status serwera (`serverstatus`)

**Cel:** Zwraca status online/offline serwera.

**Wartości:** `ip`

**Przykład:**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**Wynik:** `§aOnline` lub `§cOffline`

## Wersja serwera (`serverversion`)

**Cel:** Zwraca wersję Minecrafta serwera.

**Wartości:** `ip`

**Przykład:**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**Wynik:** `1.21.1`

> [!NOTE]
> Poniższe miejsca zastępcze czasu rzeczywistego akceptują wartość `timezone`. Użyj identyfikatora strefy czasowej Java, takiego jak `UTC`, `Europe/Berlin` lub `America/New_York`; pomiń ją albo użyj `system`, aby zastosować strefę systemową. `unix_time` zawsze zwraca znacznik czasu Unix i nie ma wartości `timezone`.

## Rok (`realtimeyear`)

**Cel:** Zwraca bieżący rok.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"realtimeyear"}
```

**Wynik:** `2024`

## Miesiąc (`realtimemonth`)

**Cel:** Zwraca bieżący miesiąc (01-12).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"realtimemonth"}
```

**Wynik:** `01`

## Dzień (`realtimeday`)

**Cel:** Zwraca bieżący dzień miesiąca (01-31).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"realtimeday"}
```

**Wynik:** `27`

## Godzina (`realtimehour`)

**Cel:** Zwraca bieżącą godzinę. Domyślnie używany jest format 24-godzinny; ustaw `twelve_hour_format` na `"true"`, aby użyć formatu 12-godzinnego.

**Wartości:** `twelve_hour_format`, `timezone`

**Przykład:**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**Wynik:** `14`

## Minuta (`realtimeminute`)

**Cel:** Zwraca bieżącą minutę (00-59).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"realtimeminute"}
```

**Wynik:** `30`

## Sekunda (`realtimesecond`)

**Cel:** Zwraca bieżącą sekundę (00-59).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"realtimesecond"}
```

**Wynik:** `45`

## Bieżący czas w milisekundach (znacznik czasu Unix) (`unix_time`)

**Cel:** Zwraca bieżący znacznik czasu Unix w milisekundach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"unix_time"}
```

**Wynik:** `1716552478123`

## Informacje o CPU (`cpuinfo`)

**Cel:** Zwraca informacje o procesorze.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"cpuinfo"}
```

**Wynik:** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Użycie CPU (JVM) (`jvmcpu`)

**Cel:** Zwraca użycie CPU przez JVM w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"jvmcpu"}
```

**Wynik:** `25.5`

## Użycie CPU (system) (`oscpu`)

**Cel:** Zwraca użycie CPU przez system operacyjny w procentach.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"oscpu"}
```

**Wynik:** `42.8`

## Informacje o GPU (`gpuinfo`)

**Cel:** Zwraca nazwę raportowaną dla aktywnego urządzenia renderującego Minecrafta. Nie gwarantuje to identyfikacji konkretnej fizycznej karty GPU.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"gpuinfo"}
```

**Wynik:** `NVIDIA GeForce RTX 3080`

## Wersja Java (`javaver`)

**Cel:** Zwraca wersję Javy.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"javaver"}
```

**Wynik:** `17.0.2`

## Wirtualna maszyna Javy (`jvmname`)

**Cel:** Zwraca nazwę Java Virtual Machine.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"jvmname"}
```

**Wynik:** `OpenJDK 64-Bit Server VM`

## Wersja OpenGL (`glver`)

**Cel:** Zwraca informacje o sterowniku dla aktywnego urządzenia renderującego Minecrafta. Mimo historycznej nazwy `glver`, wartość nie musi być wyłącznie ciągiem wersji OpenGL.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"glver"}
```

**Wynik:** `4.6.0 NVIDIA 516.94`

## Nazwa systemu operacyjnego (`osname`)

**Cel:** Zwraca nazwę systemu operacyjnego.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"osname"}
```

**Wynik:** `Windows 10`

## FPS (klatki na sekundę) (`fps`)

**Cel:** Zwraca bieżącą liczbę klatek na sekundę.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"fps"}
```

**Wynik:** `120`

## Używana pamięć RAM w MB (`usedram`)

**Cel:** Zwraca ilość aktualnie używanej pamięci RAM (MB).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"usedram"}
```

**Wynik:** `4096`

## Maksymalna pamięć RAM w MB (`maxram`)

**Cel:** Zwraca maksymalnie przydzieloną pamięć RAM (MB).

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"maxram"}
```

**Wynik:** `8192`

## Używana pamięć RAM w %% (`percentram`)

**Cel:** Zwraca procent pamięci RAM aktualnie używanej.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"percentram"}
```

**Wynik:** `50`

## Głośność elementu audio (`audio_element_vol`)

**Cel:** Zwraca głośność elementu audio.

**Wartości:** `element_identifier`

**Przykład:**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**Wynik:** `0.5`

## Bieżący utwór audio (`audio_element_current_track`)

**Cel:** Zwraca nazwę utworu elementu audio.

**Wartości:** `element_identifier`, `display_name_mappings`

**Przykład:**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

W `display_name_mappings`, `=>` oddziela nazwę pliku od jego nazwy wyświetlanej, a `%:%` oddziela kolejne mapowania.

**Wynik:** `Menu Theme`

## Czas trwania audio (`audio_duration`)

**Cel:** Zwraca czas trwania aktualnie wczytanego utworu [elementu audio](./elements#audio) w formacie `MM:SS`. Utwór może być odtwarzany, wstrzymany lub zatrzymany.

**Wartości:** `element_identifier`

**Przykład:**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**Wynik:** `03:45`

## Czas odtwarzania audio (`audio_playtime`)

**Cel:** Zwraca bieżący czas odtwarzania utworu audio. Ustaw `show_percentage` na `"true"`, aby uzyskać wartość postępu 0-100 zamiast `MM:SS`.

**Wartości:** `element_identifier`, `show_percentage`

**Przykład:**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**Wynik:** `01:30` (lub `45`, gdy `show_percentage` ma wartość `"true"`)

**Wynik niedostępny:** `00:00`, lub `0` w trybie procentowym. Bieżąca wartość jest dostępna, gdy utwór jest odtwarzany lub wstrzymany; utwory zatrzymane, brakujące i niegotowe używają wyniku niedostępnego.

## Stan odtwarzania audio (`audio_playing_state`)

**Cel:** Zwraca, czy element audio jest odtwarzany (true/false).

**Wartości:** `element_identifier`

**Przykład:**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**Wynik:** `true`

## Głośność elementu wideo (`video_element_vol`)

**Cel:** Zwraca poziom głośności elementu wideo (0.0 do 1.0).

**Wartości:** `element_identifier`

**Przykład:**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**Wynik:** `0.5`

## Czas trwania elementu wideo (`video_element_duration`)

**Cel:** Zwraca całkowity czas trwania elementu wideo w formacie `MM:SS`. Ustaw `output_as_timestamp` na `"true"`, aby zwrócić znacznik czasu w milisekundach.

**Wartości:** `element_identifier`, `output_as_timestamp`

**Przykład:**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**Wynik:** `02:00` (lub `120000`, gdy `output_as_timestamp` ma wartość `"true"`)

## Czas odtwarzania elementu wideo (`video_element_playtime`)

**Cel:** Zwraca bieżący czas odtwarzania (postęp) elementu wideo w formacie `MM:SS`. Ustaw `show_percentage` na `"true"`, aby uzyskać wartość postępu 0-100, lub `output_as_timestamp` na `"true"`, aby zwrócić milisekundy.

**Wartości:** `element_identifier`, `show_percentage`, `output_as_timestamp`

**Przykład:**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**Wynik:** `00:45` (lub `38` jako procent, albo `45200` jako znacznik czasu)

## Stan pauzy elementu wideo (`video_element_paused_state`)

**Cel:** Zwraca, czy element wideo jest wstrzymany (true/false).

**Wartości:** `element_identifier`

**Przykład:**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**Wynik:** `false`

## Głośność tła wideo (`video_background_vol`)

**Cel:** Zwraca poziom głośności wideo tła menu (0.0 do 1.0).

**Wartości:** `background_identifier`

**Przykład:**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**Wynik:** `0.7`

## Czas trwania tła wideo (`video_background_duration`)

**Cel:** Zwraca całkowity czas trwania tła wideo menu w formacie `MM:SS`. Ustaw `output_as_timestamp` na `"true"`, aby zwrócić znacznik czasu w milisekundach.

**Wartości:** `background_identifier`, `output_as_timestamp`

**Przykład:**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**Wynik:** `03:00` (lub `180000`, gdy `output_as_timestamp` ma wartość `"true"`)

## Czas odtwarzania tła wideo (`video_background_playtime`)

**Cel:** Zwraca bieżący czas odtwarzania (postęp) tła wideo menu w formacie `MM:SS`. Ustaw `show_percentage` na `"true"`, aby uzyskać wartość postępu 0-100, lub `output_as_timestamp` na `"true"`, aby zwrócić milisekundy.

**Wartości:** `background_identifier`, `show_percentage`, `output_as_timestamp`

**Przykład:**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**Wynik:** `01:00` (lub `33` jako procent, albo `60500` jako znacznik czasu)

## Stan pauzy tła wideo (`video_background_paused_state`)

**Cel:** Zwraca, czy tło wideo menu jest wstrzymane (true/false).

**Wartości:** `background_identifier`

**Przykład:**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**Wynik:** `true`

## Kalkulator (`calc`)

**Cel:** Miejsce zastępcze kalkulatora to potężne narzędzie, które pozwala wykonywać obliczenia matematyczne w układach. Obsługuje szeroki zakres działań matematycznych i może pracować zarówno na liczbach dziesiętnych, jak i całkowitych.

**Wartości:** `decimal`, `expression`

### Podstawowa składnia

**Przykład:**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"twoje_wyrażenie"}}
```

Kalkulator ma dwa główne parametry:
- `decimal`: Określa, czy wynik ma zawierać część dziesiętną (`true`), czy zostać zaokrąglony do liczb całkowitych (`false`)
- `expression`: Wyrażenie matematyczne do obliczenia

### Obsługiwane działania
Kalkulator obsługuje następujące działania matematyczne:
- Podstawowe działania: `+` (dodawanie), `-` (odejmowanie), `*` (mnożenie), `/` (dzielenie)
- Nawiasy: `( )` do grupowania działań
- Potęgowanie: `^`
- Pierwiastek kwadratowy: `sqrt()`
- Funkcje trygonometryczne: `sin()`, `cos()`, `tan()`
- Stałe matematyczne: `pi`, `e`
- Wartość bezwzględna: `abs()`
- Logarytmy: `log()`, `ln()`

## Losowa liczba (`random_number`)

**Cel:** Generuje losową liczbę w określonym zakresie.

**Wartości:** `min`, `max`

**Przykład:**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**Wynik:** `42`

## Maksymalna liczba (`maxnum`)

**Cel:** Zwraca większą z dwóch liczb.

**Wartości:** `first`, `second`

**Przykład:**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**Wynik:** `20`

## Minimalna liczba (`minnum`)

**Cel:** Zwraca mniejszą z dwóch liczb.

**Wartości:** `first`, `second`

**Przykład:**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**Wynik:** `10`

## Wartość bezwzględna liczby (`absnum`)

**Cel:** Zwraca wartość bezwzględną liczby.

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**Wynik:** `10.5`

## Zmień liczbę na ujemną (`negnum`)

**Cel:** Zmienia dodatnią liczbę na ujemną. Zera i wartości już ujemne są zwracane bez zmian.

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**Wynik:** `-10.5`

## *pi* (matematyczna) (`math_pi`)

**Cel:** Zwraca wartość π.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"math_pi"}
```

**Wynik:** `3.141592653589793`

## Sinus trygonometryczny (matematyka) (`math_sin`)

**Cel:** Zwraca sinus kąta w radianach. Najpierw przelicz wartości w stopniach na radiany.

**Wartości:** `angle`

**Przykład:**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**Wynik:** `1.0`

## Cosinus trygonometryczny (matematyka) (`math_cos`)

**Cel:** Zwraca cosinus kąta w radianach. Najpierw przelicz wartości w stopniach na radiany.

**Wartości:** `angle`

**Przykład:**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**Wynik:** `1.0`

## Tangens trygonometryczny (matematyka) (`math_tan`)

**Cel:** Zwraca tangens kąta w radianach. Najpierw przelicz wartości w stopniach na radiany.

**Wartości:** `angle`

**Przykład:**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**Wynik:** `0.0`

## Podłoga (matematyka) (`math_floor`)

**Cel:** Zwraca matematyczną funkcję podłogi dla liczby, sformatowaną z sufiksem dziesiętnym `.0`.

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**Wynik:** `3.0`

## Sufit (matematyka) (`math_ceil`)

**Cel:** Zwraca matematyczną funkcję sufitu dla liczby, sformatowaną z sufiksem dziesiętnym `.0`.

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**Wynik:** `4.0`

Użyj [**Zaokrąglij**](#round-math-math_round) lub [**Kalkulatora**](#kalkulator-calc) z wyłączonym wynikiem dziesiętnym, gdy potrzebujesz tekstu całkowitego bez `.0`.

## Zaokrąglij (matematyka) (`math_round`)

**Cel:** Zaokrągla liczbę. Domyślnie zaokrągla do najbliższej liczby całkowitej; ustaw `decimals` na nieujemną liczbę, aby zaokrąglić do tylu miejsc po przecinku.

**Wartości:** `num`, `decimals`

**Przykład:**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**Wynik:** `3.14` (przy `decimals:-1` lub gdy pominięte → `3`)

## Znak (matematyka) (`math_sign`)

**Cel:** Zwraca znak liczby (1 dla dodatniej, -1 dla ujemnej, 0 dla zera).

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**Wynik:** `-1`

## Sinus hiperboliczny (matematyka) (`math_sinh`)

**Cel:** Zwraca sinus hiperboliczny liczby.

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**Wynik:** `1.1752011936438014`

## Cosinus hiperboliczny (matematyka) (`math_cosh`)

**Cel:** Zwraca cosinus hiperboliczny liczby.

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**Wynik:** `1.5430806348152437`

## Tangens hiperboliczny (matematyka) (`math_tanh`)

**Cel:** Zwraca tangens hiperboliczny liczby.

**Wartości:** `num`

**Przykład:**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**Wynik:** `0.7615941559557649`

## Podziel tekst (`split_text`)

**Cel:** Dzieli tekst przy użyciu określonego separatora.

**Wartości:** `input`, `regex`, `max_parts`, `split_index`

**Przykład:**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**Wynik:** `world`

## Przytnij tekst (`trim_text`)

**Cel:** Usuwa wiodące i końcowe białe znaki.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**Wynik:** `hello world`

## Przytnij tekst z obu stron (`crop_text`)

**Cel:** Usuwa znaki z początku i końca tekstu.

**Wartości:** `text`, `remove_from_start`, `remove_from_end`

**Przykład:**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**Wynik:** `ello worl`

## Stringifikuj (`stringify`)

**Cel:** Zamienia tekst na ciąg, ucieczką wszystkich znaków składni.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**Wynik:** `text with \{special\} \"characters\"`

## Tłumacz tekst (`local`)

**Cel:** Pobiera zlokalizowany tekst dla klucza.

**Wartości:** `key`

**Przykład:**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**Wynik:** `Singleplayer`

## Tekst z sieci (`webtext`)

**Cel:** Pobiera zawartość tekstową z adresu URL.

**Wartości:** `link`

**Przykład:**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**Wynik:** `Welcome to the server!`

## Losowy tekst (`randomtext`)

**Cel:** Zwraca losową linię z pliku tekstowego, adresu URL lub bezpośredniego zwykłego tekstu. Tekst zmienia się w określonych odstępach. Zawartość plików i adresów URL jest odświeżana mniej więcej co 30 sekund; bezpośredni tekst pozostaje w pamięci podręcznej, ponieważ nie wymaga ponownego wczytywania.

**Wartości:** `source`, `interval`

W wartościach miejsc zastępczych `/config/...` oznacza `<game-directory>/config/...`; nie jest to ścieżka z katalogu głównego systemu plików. Zobacz [Zasoby](./resources#local-resources).

**Przykład:**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parametry:
- `source`: Źródło linii tekstu (zastępuje stary parametr `path`)
  - Ścieżka pliku: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Zwykły tekst: `Linia 1\nLinia 2\nLinia 3`
- `interval`: Czas w sekundach między zmianami tekstu

Miejsce zastępcze obsługuje teraz trzy typy źródeł:
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

Uwaga: Stare miejsca zastępcze używające `path` zamiast `source` nadal będą działać.

## Parser JSON (`json`)

**Cel:** Parsuje dane JSON z pliku, adresu URL lub bezpośredniej zawartości JSON i wyodrębnia wartości za pomocą wyrażeń ścieżek JSON.

**Wartości:** `source`, `json_path`

**Przykład:**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parametry:
- `source`: Źródło danych JSON
  - Ścieżka pliku: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - Bezpośredni JSON: `{"name":"Steve","level":42}`
- `json_path`: Wyrażenie ścieżki JSON służące do wyodrębnienia danych

Miejsce zastępcze obsługuje teraz trzy typy źródeł:
1. **Pliki lokalne**: Pliki JSON z katalogu gry
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URL-e**: Zdalne dane JSON z API lub usług WWW
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **Bezpośredni JSON**: Wbudowana zawartość JSON
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Przykładowe ścieżki JSON:
- `$.name` - Pobiera pole "name" z korzenia
- `$.player.level` - Pobiera zagnieżdżone pole "level" wewnątrz "player"
- `$.items[0].id` - Pobiera "id" pierwszego elementu w tablicy
- `$.scores.*` - Pobiera wszystkie wartości z obiektu "scores"

## Absolutna ścieżka pliku/folderu (`absolute_path`)

**Cel:** Zwraca absolutną ścieżkę pliku.

**Wartości:** `short_path`

**Przykład:**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**Wynik:** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## Liczba znaków tekstu (`text_character_count`)

**Cel:** Zwraca liczbę znaków w podanym tekście.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**Wynik:** `12`

## Szerokość tekstu (`text_width`)

**Cel:** Zwraca szerokość podanego tekstu w pikselach podczas renderowania.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**Wynik:** `66`

## Tekst wielkimi literami (`uppercase_text`)

**Cel:** Zamienia tekst wejściowy na wielkie litery.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**Wynik:** `HELLO WORLD`

## Tekst małymi literami (`lowercase_text`)

**Cel:** Zamienia tekst wejściowy na małe litery.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**Wynik:** `hello world`

## Tekst w formacie tytułowym (`title_case_text`)

**Cel:** Zamienia tekst wejściowy na format tytułowy.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**Wynik:** `Hello World`

## Tekst w formacie zdania (`sentence_case_text`)

**Cel:** Zamienia tekst wejściowy na format zdaniowy.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**Wynik:** `Hello world. This is fancymenu!`

## Tekst w snake_case (`snake_case_text`)

**Cel:** Zamienia tekst wejściowy na `snake_case`.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**Wynik:** `hello_world`

## Tekst w kebab-case (`kebab_case_text`)

**Cel:** Zamienia tekst wejściowy na `kebab-case`.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**Wynik:** `hello-world`

## Tekst o naprzemiennych wielkościach liter (`alternating_case_text`)

**Cel:** Zamienia tekst wejściowy na tekst o naprzemiennych wielkościach liter.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**Wynik:** `aLtErNaTiNg CaSe`

## Przełącz wielkość liter tekstu (`toggle_case_text`)

**Cel:** Zmienia wielkość liter każdej litery w tekście wejściowym.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**Wynik:** `tOGGLE cASE`

## Kodowanie do Base64 (`base64_encode`)

**Cel:** Koduje podany tekst jako Base64.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**Wynik:** `SGVsbG8gV29ybGQ=`

## Dekodowanie z Base64 (`base64_decode`)

**Cel:** Dekoduje ciąg Base64 z powrotem do zwykłego tekstu.

**Wartości:** `text`

**Przykład:**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**Wynik:** `Hello World`

## Tekst z pliku (`file_text`)

**Cel:** Zwraca linie tekstu z pliku lub adresu URL. Może zwrócić wszystkie linie albo tylko ostatnie X linii.

**Wartości:** `path_or_url`, `mode`, `separator`, `last_lines`

**Przykład:**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parametry:
- `path_or_url`: Ścieżka pliku lub adres URL do odczytu
- `mode`: `"all"` (zwraca wszystkie linie) lub `"last"` (zwraca tylko ostatnie X linii)
- `separator`: Tekst używany między liniami (domyślnie: `"\n"`)
- `last_lines`: Liczba linii do zwrócenia, gdy `mode` ma wartość `"last"` (domyślnie: `"1"`)

**Wynik:**

```text
First line
Second line
```

## Zawartość schowka (`clipboard_content`)

**Cel:** Zwraca bieżącą zawartość tekstową zapisaną w systemowym schowku.

**Wartości:** Brak

**Przykład:**

```
{"placeholder":"clipboard_content"}
```

**Wynik:** `Hello from the clipboard`

## Zamień tekst (`replace_text`)

**Cel:** Zastępuje tekst w ciągu przy użyciu tekstu dosłownego lub wyrażeń regularnych.

**Wartości:** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**Przykład:**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parametry:
- `text`: Tekst wejściowy do przetworzenia
- `search`: Tekst lub wzorzec regex do wyszukania
- `replacement`: Tekst zastępujący
- `use_regex`: Czy używać regex (`"true"`), czy dopasowania dosłownego (`"false"`)
- `replace_all`: Zastąp wszystkie wystąpienia (`"true"`) czy tylko pierwsze (`"false"`)

**Wynik:** `Hello FancyMenu! This is a test.`

## Przełącznik wielokrotnego wyboru (`switch_case`)

**Cel:** Wykonuje operację switch-case na podstawie wartości.

**Wartości:** `value`, `cases`, `default`

**Przykład:**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**Wynik:** `first case` (jeśli value wynosi 1)

## Pobierz wartość zmiennej (zmienna FM) (`getvariable`)

**Cel:** Pobiera wartość wcześniej zapisanej zmiennej.

**Wartości:** `name`

**Przykład:**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**Wynik:** `42`

## Pobierz dane NBT (`nbt_data_get`)

**Cel:** Pobiera dane NBT po stronie klienta (podobnie do komendy `/data get`). Użyj serwerowej wersji `nbt_data_get_server`, gdy jesteś połączony z serwerem i potrzebujesz autorytatywnych danych po stronie serwera.

**Wartości:** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**Przykład:**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parametry:
- `source_type`: `"entity"` lub `"block"`
- `entity_selector`: Selektor encji, np. `@s`, `@p`, `@e`, albo UUID/nazwa (dla encji)
- `block_pos`: Pozycja bloku w formacie `"x y z"` (dla bloków)
- `nbt_path`: Ścieżka NBT do pobrania
- `scale`: Opcjonalny współczynnik skalowania wartości liczbowych (domyślnie: `"1.0"`)
- `return_type`: Sposób zwracania danych:
  - `"value"`: Domyślnie, zwraca wartość (z opcjonalnym skalowaniem dla liczb)
  - `"string"`: Zwraca rzeczywiste dane NBT jako ciąg
  - `"snbt"`: Zwraca jako SNBT (sformatowany NBT)
  - `"json"`: Zwraca jako komponent sformatowany w JSON (dla tagów compound)

**Wynik:** `20` (dla poziomu głodu)

## Pobierz dane NBT (po stronie serwera) (`nbt_data_get_server`)

**Cel:** Zapyta o dane NBT po stronie serwera (za pomocą pakietu) i przez chwilę przechowuje wyniki w pamięci podręcznej. Wartości odpowiadają wariantowi po stronie klienta.

**Wartości:** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**Przykład:**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**Wynik:** `minecraft:diamond_sword`

## Ostatnia wiadomość śmierci (`lastdeathmessage`)

**Cel:** Zwraca ostatnio zapisaną wiadomość śmierci gracza klienta. Ustaw `as_json_component` na `"true"`, aby otrzymać surowy komponent tekstowy JSON.

**Wartości:** `as_json_component`

**Przykład:**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**Wynik:** `Steve was slain by Zombie`

## Czas działania (`uptime_duration`)

**Cel:** Zwraca, jak długo FancyMenu jest załadowane. Domyślnie wartość podawana jest w sekundach; ustaw `output_as_millis` na `"true"`, aby otrzymać milisekundy.

**Wartości:** `output_as_millis`

**Przykład:**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**Wynik:** `742` (sekundy od załadowania)

## Nazwy zapisów światów (`level_save_names`)

**Cel:** Wyświetla wszystkie lokalne nazwy zapisów światów połączone wybranym separatorem. Działa w wątku klienta.

**Wartości:** `separator`

**Przykład:**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**Wynik:** `Creative Test, Survival World, Hardcore`

## Dane zapisu świata (`level_save_data`)

**Cel:** Zwraca serializowane dane poziomu dla podanej nazwy świata (musi odpowiadać nazwie wyświetlanej na liście zapisów).

**Wartości:** `level_name`

**Przykład:**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**Wynik:** `{"name":"Survival World","gameMode":"survival",...}`

## Konwerter podstawy liczby (`number_base_convert`)

**Cel:** Konwertuje liczbę (całkowitą lub ułamkową) z jednej podstawy do drugiej (2–36). Domyślnie używa dziesiętnej, jeśli podstawy nie są podane.

**Wartości:** `input`, `from_base`, `to_base`

**Przykład:**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**Wynik:** `43.8`

## Rozmiar pliku (`file_size`)

**Cel:** Zwraca rozmiar lokalnego pliku w bajtach. Dozwolone są tylko lokalne ścieżki.

**Wartości:** `path`

**Przykład:**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Wynik:** `1284`

## MD5 pliku (`file_md5`)

**Cel:** Zwraca skrót MD5 lokalnego pliku jako mały ciąg szesnastkowy.

**Wartości:** `path`

**Przykład:**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Wynik:** `d41d8cd98f00b204e9800998ecf8427e`

# Praktyczne przykłady

## Tworzenie dynamicznego wyświetlacza pamięci
```
Używana RAM: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Tworzenie zegara czasu rzeczywistego
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
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

## Złożone obliczenie z zagnieżdżonymi miejscami zastępczymi
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

1. **Buforuj kosztowne operacje**: Niektóre miejsca zastępcze (np. odczytujące informacje systemowe) mogą być zasobożerne. Rozważ użycie zmiennych do przechowywania ich wartości, jeśli musisz używać ich wielokrotnie.

2. **Używaj odpowiednich ustawień dziesiętnych**: Podczas pracy z obliczeniami używaj parametru `decimal` odpowiednio. Ustaw `false`, gdy potrzebujesz liczb całkowitych, a `true`, gdy potrzebujesz precyzyjnych wartości dziesiętnych.

3. **Obsługuj brakujące wartości**: Zawsze rozważ, co powinno się stać, jeśli miejsce zastępcze zwróci brak wartości. W takich przypadkach możesz chcieć podać wartości domyślne.

4. **Testuj wydajność**: Przy używaniu wielu miejsc zastępczych lub złożonych struktur zagnieżdżonych testuj wpływ na wydajność, szczególnie na słabszych systemach.

5. **Korzystaj z zaawansowanego skalowania/pozycjonowania**: Dla dynamicznych elementów interfejsu łącz miejsca zastępcze z zaawansowanym skalowaniem i pozycjonowaniem, aby tworzyć responsywne układy.

6. **Łącz z zmiennymi**: Używaj miejsc zastępczych razem ze zmiennymi, aby uzyskać jeszcze bardziej dynamiczną treść, którą można aktualizować za pomocą akcji.

# Typowe problemy i rozwiązania

## Miejsce zastępcze się nie aktualizuje
Jeśli wartość miejsca zastępczego nie aktualizuje się zgodnie z oczekiwaniami, sprawdź:
- Czy miejsce zastępcze jest poprawnie sformatowane
- Czy używasz właściwej wielkości liter w identyfikatorach miejsc zastępczych
- Czy miejsce zastępcze wymaga określonych warunków do aktualizacji

## Zagnieżdżone miejsca zastępcze nie działają
Podczas zagnieżdżania miejsc zastępczych:
- Upewnij się, że cudzysłowy są poprawnie ucieczkowane
- Sprawdź, czy każde zagnieżdżone miejsce zastępcze jest samo w sobie poprawne

## Problemy z wydajnością
Jeśli zauważysz problemy z wydajnością:
- Ogranicz liczbę używanych miejsc zastępczych
- Unikaj niepotrzebnego zagnieżdżania
- Rozważ użycie zmiennych dla często pobieranych wartości
- Używaj odpowiedniego miejsca zastępczego do swoich potrzeb (np. nie używaj miejsc zastępczych czasu rzeczywistego, gdy wystarczą wartości statyczne)
