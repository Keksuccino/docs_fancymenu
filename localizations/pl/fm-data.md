---
title: Udostępnianie danych klient < - > serwer
description: >-
  Wysyłaj i odbieraj niestandardowe dane między serwerem a klientem za pomocą
  FancyMenu.
---

# FM Data

System „FM Data” pozwala wysyłać niestandardowe dane tekstowe między serwerem a klientem.

Każda wiadomość FM Data ma:

1. **Identyfikator danych** (jakiego rodzaju jest to wiadomość)
2. **Wartość danych** (rzeczywista treść)

Przykładowy pomysł:

- Identyfikator: `hud.food`
- Dane: `18/20`

# Szybki start

1. Serwer wysyła dane za pomocą `/fmdata send ...`
2. Klient odbiera je za pomocą nasłuchiwacza FancyMenu **On FM Data Received**
3. Klient może też odesłać dane z powrotem akcją **Send FM Data To Server**
4. Serwer może reagować automatycznie za pomocą `/fmdata listener ...`
5. Serwer może automatycznie wysyłać dane przy dołączeniu gracza za pomocą `/fmdata welcome_data ...`

# Serwer -> Klient

Użyj:

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

Przykłady:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "aktualizacja wartości jedzenia" "18 z 20"
```

Uwagi:

- `<target_player>` obsługuje standardowe selektory graczy, takie jak `@a`, `@p`, `@s`
- W przypadku wartości zawierających spacje używaj cudzysłowów

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
- Uruchamianie logiki na podstawie przychodzącego identyfikatora/danych

# Klient -> Serwer

Użyj akcji FancyMenu:

- **Send FM Data To Server**

Akcja ma 2 pola wejściowe:

1. Data Identifier
2. Data

Serwer może następnie przetwarzać przychodzące dane za pomocą `/fmdata listener ...`.

# Nasłuchiwacze serwera

Nasłuchiwacze serwera odbierają dane przychodzące od klientów i mogą uruchamiać jedną lub wiele komend po wyzwoleniu.

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

`matching_type_identifier` i `matching_type_data` mogą mieć wartości:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Zasady dopasowania

- `ignore_case_identifier` i `ignore_case_data` to przełączniki true/false
- `listen_for_identifier` obsługuje wildcard `*` (zawsze pasuje)
- `listen_for_data` obsługuje wildcard `*` (zawsze pasuje)
- `fire_for_player` używa standardowych selektorów graczy (na przykład `@a`, `@p`, `Player761`)

## Komendy po wyzwoleniu

`commands_to_execute_on_fire` to jedno pole tekstowe.

- Rozdziel wiele komend za pomocą `|||`
- Zapisz dosłowny separator jako `\|\|\|`

Możesz tutaj użyć dwóch specjalnych placeholderów, które zostaną zastąpione tuż przed wykonaniem komend:

- `%fm_sender%` -> gracz, który wysłał FM Data
- `%fm_data%` -> wartość danych otrzymana od klienta

Komendy są wykonywane jako komendy serwera.

## Przykładowe komendy

Reagowanie na naciśnięcie przycisku przez dowolnego gracza:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% nacisnął przycisk\"}"
```

Uruchamianie wielu komend, gdy dane zawierają `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Nagroda od %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Dane powitalne

Dane powitalne wysyłają FM Data do pasujących graczy, gdy dołączają.

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
- Dane są wysyłane do pasujących graczy, gdy dołączają
- Wpisy są zapisywane i ładowane automatycznie

## Przykładowe komendy

Wysyłanie danych powitalnych do wszystkich dołączających graczy:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Witamy!"
```

Wysyłanie danych powitalnych tylko do jednego gracza:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Włączono bonusy VIP"
```

# Najlepsze praktyki

1. Używaj czytelnych identyfikatorów, takich jak `hud.food`, `menu.shop.open`, `quest.progress`.
2. Utrzymuj spójny format danych dla każdego identyfikatora.
3. Zacznij prosto: przetestuj z `/fmdata send`, zanim zbudujesz bardziej złożone nasłuchiwacze.
4. Używaj `@a` tylko wtedy, gdy naprawdę chcesz globalnego działania.
5. Używaj `/fmdata listener list` i `/fmdata welcome_data list`, aby utrzymać konfigurację w porządku.
