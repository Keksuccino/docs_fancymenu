---
title: Udostępnianie danych między klientem a serwerem
description: >-
  Wysyłaj i odbieraj niestandardowe dane między serwerem a klientem za pomocą
  FancyMenu.
---

# FM Data

System „FM Data” pozwala wysyłać niestandardowe dane tekstowe między serwerem a klientem.

Każda podkomenda `/fmdata` wymaga **poziomu uprawnień 2** (Game Master / OP poziom 2).

Każda wiadomość FM Data zawiera:

1. **identyfikator danych** (określa, jaki to rodzaj wiadomości)
2. **wartość danych** (rzeczywistą treść)

Przykład:

- Identyfikator: `hud.food`
- Dane: `18/20`

# Szybki start

1. Serwer wysyła dane za pomocą `/fmdata send ...`
2. Klient odbiera je za pomocą nasłuchiwacza FancyMenu **On FM Data Received**
3. Klient może też odesłać dane z powrotem za pomocą akcji **Send FM Data To Server**
4. Serwer może reagować automatycznie za pomocą `/fmdata listener ...`
5. Serwer może automatycznie wysyłać dane przy dołączeniu gracza za pomocą `/fmdata welcome_data ...`

# Serwer -> Klient

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

- `<target_players>` obsługuje nazwy graczy oraz selektory, takie jak `@a`, `@p` i `@s`
- Używaj cudzysłowów dla wartości zawierających spacje

# Klient: odbieranie danych

Użyj nasłuchiwacza FancyMenu:

- **On FM Data Received**

Dostępne zmienne:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` to:

- adres IP serwera w trybie wieloosobowym
- `integrated_server` w trybie jednoosobowym

Typowe zastosowania:

- Aktualizowanie elementów tekstowych
- Wyzwalanie akcji menu
- Uruchamianie logiki na podstawie otrzymanego identyfikatora/danych

# Klient -> Serwer

Użyj akcji FancyMenu:

- **Send FM Data To Server**

Akcja ma 2 pola wejściowe:

1. Data Identifier
2. Data

Serwer może następnie przetwarzać przychodzące dane za pomocą `/fmdata listener ...`.

# Nasłuchiwacze serwera

Nasłuchiwacze serwera nasłuchują przychodzących danych od klientów i mogą uruchamiać jedną lub wiele komend po wyzwoleniu.

Nasłuchiwacze serwera są zapisywane i pozostają aktywne po restarcie.

Zarządzaj nimi za pomocą:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Składnia dodawania / edycji

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

`matching_type_identifier` i `matching_type_data` mogą mieć wartość:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Zasady dopasowania

- `ignore_case_identifier` i `ignore_case_data` to przełączniki true/false
- `listen_for_identifier` obsługuje wieloznacznik `*` (zawsze pasuje)
- `listen_for_data` obsługuje wieloznacznik `*` (zawsze pasuje)
- `fire_for_player` używa standardowych selektorów graczy (na przykład `@a`, `@p`, `Player761`)

## Komendy przy wyzwoleniu

`commands_to_execute_on_fire` to jedno pole tekstowe.

- Oddzielaj wiele komend za pomocą `|||`
- Ucieknij dosłowny separator jako `\|\|\|`

Możesz użyć tutaj dwóch specjalnych placeholderów, które zostaną zastąpione tuż przed wykonaniem komend:

- `%fm_sender%` -> gracz, który wysłał FM Data
- `%fm_data%` -> wartość danych odebrana od klienta

Komendy są wykonywane jako komendy serwera.

## Przykładowe komendy

Reaguj na naciśnięcie przycisku przez dowolnego gracza:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Uruchom wiele komend, gdy dane zawierają `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Dane powitalne

Dane powitalne wysyłają FM Data do pasujących graczy, gdy dołączają do gry.

Zarządzaj wpisami za pomocą:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Składnia dodawania / edycji

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

- `<target_player>` obsługuje standardowe selektory, takie jak `@a`, `@p`, `@s`
- Dane są wysyłane do pasujących graczy po dołączeniu
- Wpisy są automatycznie zapisywane i wczytywane

## Przykładowe komendy

Wyślij dane powitalne do wszystkich dołączających graczy:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Wyślij dane powitalne tylko do jednego gracza:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Najlepsze praktyki

1. Używaj czytelnych identyfikatorów, takich jak `hud.food`, `menu.shop.open`, `quest.progress`.
2. Dla każdego identyfikatora utrzymuj spójny format danych.
3. Zacznij prosto: przetestuj `/fmdata send` przed tworzeniem złożonych nasłuchiwaczy.
4. Używaj `@a` tylko wtedy, gdy naprawdę chcesz globalnego działania.
5. Używaj `/fmdata listener list` i `/fmdata welcome_data list`, aby utrzymywać konfigurację w porządku.
