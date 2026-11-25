---
title: Udostępnianie danych klient–serwer
description: >-
  Wysyłaj i odbieraj niestandardowe dane między serwerem a klientem za pomocą
  FancyMenu.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# Dane FM

System „Dane FM” umożliwia wysyłanie niestandardowych danych tekstowych między serwerem a klientem.

Każde podpolecenie `/fmdata` wymaga **poziomu uprawnień 2** (Game Master / OP poziom 2).

Każda wiadomość FM Data zawiera:

1. **Identyfikator danych** (rodzaj wiadomości)
2. **Wartość danych** (właściwa treść)

Przykład:

- Identyfikator: `hud.food`
- Dane: `18/20`

# Szybki start

1. Serwer wysyła dane za pomocą `/fmdata send ...`
2. Klient odbiera je za pomocą nasłuchiwacza FancyMenu **Po odebraniu danych FM**
3. Klient może również odesłać dane za pomocą akcji **Wyślij dane FM do serwera**
4. Serwer może automatycznie reagować za pomocą `/fmdata listener ...`
5. Serwer może automatycznie wysyłać dane przy dołączaniu gracza za pomocą `/fmdata welcome_data ...`

# Serwer -> klient

Użyj:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Przykłady:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Uwagi:

- `<target_players>` obsługuje nazwy graczy i selektory, takie jak `@a`, `@p` i `@s`
- Używaj cudzysłowów, jeśli wartości zawierają spacje

# Klient: odbieranie danych

Użyj nasłuchiwacza FancyMenu:

- **Po odebraniu danych FM**

Dostępne zmienne:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

Zmienna `$$sent_by` zawiera:

- Adres IP serwera w trybie wieloosobowym
- `integrated_server` w trybie jednoosobowym

Typowe zastosowania:

- Aktualizowanie elementów tekstowych
- Wywoływanie akcji menu
- Uruchamianie logiki na podstawie otrzymanego identyfikatora lub danych

# Klient -> serwer

Użyj akcji FancyMenu:

- **Wyślij dane FM do serwera**

Akcja ma 2 pola:

1. Identyfikator danych
2. Dane

Serwer może następnie przetworzyć otrzymane dane za pomocą `/fmdata listener ...`.

# Nasłuchiwacze serwera

Nasłuchiwacze serwera oczekują na dane od klientów i po ich otrzymaniu mogą uruchomić jedno lub kilka poleceń.

Nasłuchiwacze są zapisywane i pozostają aktywne po ponownym uruchomieniu.

Zarządzaj nimi za pomocą poleceń:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Składnia dodawania i edycji

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Składnia usuwania

```mcfunction
/fmdata listener remove <listener_name>
```

## Typy dopasowania

`matching_type_identifier` i `matching_type_data` mogą przyjmować wartości:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Zasady dopasowania

- `ignore_case_identifier` i `ignore_case_data` to przełączniki true/false
- `listen_for_identifier` obsługuje symbol wieloznaczny `*` (zawsze pasuje)
- `listen_for_data` obsługuje symbol wieloznaczny `*` (zawsze pasuje)
- `fire_for_player` korzysta ze standardowych selektorów graczy (na przykład `@a`, `@p`, `Player761`)

## Polecenia uruchamiane po wywołaniu

`commands_to_execute_on_fire` to jedno pole tekstowe.

- Oddzielaj wiele poleceń za pomocą `|||`
- Zapisz dosłowny separator jako `\|\|\|`

Możesz użyć dwóch specjalnych symboli zastępczych, które zostaną podmienione tuż przed uruchomieniem poleceń:

- `%fm_sender%` -> gracz, który wysłał dane FM
- `%fm_data%` -> wartość danych otrzymana od klienta

Polecenia są uruchamiane jako polecenia serwera.

## Przykładowe polecenia

Reagowanie na naciśnięcie przycisku przez dowolnego gracza:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Uruchamianie kilku poleceń, gdy dane zawierają `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Dane powitalne

Dane powitalne wysyłają dane FM pasującym graczom, gdy dołączają do gry.

Zarządzaj wpisami za pomocą poleceń:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Składnia dodawania i edycji

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Składnia usuwania

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Uwagi:

- `<target_player>` obsługuje standardowe selektory, takie jak `@a`, `@p` i `@s`
- Dane są wysyłane pasującym graczom, gdy dołączają do gry
- Wpisy są automatycznie zapisywane i wczytywane

## Przykładowe polecenia

Wysyłanie danych powitalnych wszystkim dołączającym graczom:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Wysyłanie danych powitalnych tylko jednemu graczowi:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Eksport dla AI

Aby uzyskać pomoc od Alice lub innej AI, wyeksportuj nasłuchiwacze serwera i dane powitalne za pomocą opcji [Eksport dla AI](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` wysyła wiadomość na czacie, której kliknięcie kopiuje eksport. `file` zapisuje go na serwerze w folderze `fancymenu_data/ai_exports/`.

# Dobre praktyki

1. Używaj czytelnych identyfikatorów, takich jak `hud.food`, `menu.shop.open`, `quest.progress`.
2. Zachowuj spójny format danych dla każdego identyfikatora.
3. Zacznij od prostych rozwiązań: przetestuj `/fmdata send`, zanim utworzysz złożone nasłuchiwacze.
4. Używaj `@a` tylko wtedy, gdy naprawdę chcesz, aby działanie obejmowało wszystkich graczy.
5. Korzystaj z `/fmdata listener list` i `/fmdata welcome_data list`, aby utrzymywać porządek w konfiguracji.
