---
title: Komunikacja z zdalnym serwerem
description: >-
  Wysyłaj i odbieraj niestandardowe dane tekstowe między klientami FancyMenu a
  zewnętrznymi serwerami.
---

# Komunikacja z zdalnym serwerem

System „Komunikacja z zdalnym serwerem” pozwala klientom FancyMenu komunikować się z zewnętrznymi serwerami za pomocą połączeń WebSocket.

Wszystkie dane mają postać tekstową:

- Obsługiwany jest zwykły tekst
- Obsługiwany jest JSON (jako zwykły tekst)

Każdy adres URL serwera otrzymuje w czasie działania jedną buforowaną **ID żądania**.
FancyMenu używa tego identyfikatora do śledzenia połączenia i udostępniania go w zmiennych nasłuchiwaczy.

# Szybki start

1. Dodaj akcję **Połącz z zdalnym serwerem** (opcjonalnie, ale przydatne do wcześniejszego otwarcia połączenia)
2. Dodaj akcję **Wyślij dane do zdalnego serwera** z tym samym adresem URL
3. Dodaj nasłuchiwacz **Po odebraniu danych z zdalnego serwera**, aby reagować na odpowiedzi
4. Użyj **Po połączeniu z zdalnym serwerem** / **Po zamknięciu połączenia z zdalnym serwerem** dla logiki stanu połączenia
5. Zamykaaj połączenia w razie potrzeby za pomocą akcji zamykania

# Akcje

## Połącz z zdalnym serwerem

Inicjalizuje połączenie z zdalnym serwerem bez wysyłania danych ładunku.

Wejście:

- URL zdalnego serwera

## Wyślij dane do zdalnego serwera

Łączy się (lub ponownie wykorzystuje istniejące połączenie) i wysyła dane tekstowe.

Wejścia:

1. URL zdalnego serwera
2. Dane

## Zamknij połączenie z zdalnym serwerem

Zamyka jedno połączenie według ID żądania.

Wejście:

- ID żądania połączenia

## Zamknij wszystkie połączenia z zdalnym serwerem

Zamyka wszystkie aktualnie aktywne połączenia z zdalnym serwerem.

# Nasłuchiwacze

## Po połączeniu z zdalnym serwerem

Uruchamia się, gdy połączenie z zdalnym serwerem zostanie zainicjalizowane.

Zmienne:

- `$$request_id`
- `$$remote_server_url`

## Po odebraniu danych z zdalnego serwera

Uruchamia się, gdy dane zostaną odebrane z połączonego zdalnego serwera.

Zmienne:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Po zamknięciu połączenia z zdalnym serwerem

Uruchamia się, gdy połączenie z zdalnym serwerem zostanie zamknięte.

Zmienne:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Zachowanie połączenia

- Połączenia są **inicjowane przez klienta**
- FancyMenu utrzymuje połączenia aktywne w tle
- Jeśli połączenie ulegnie awarii lub przekroczy limit czasu, FancyMenu ponawia próbę co 10 sekund
- Gdy awaryjne połączenie zostanie przywrócone, FancyMenu zapisuje komunikat o przywróceniu
- Niewysłane wiadomości wychodzące są kolejkowane z **maksymalnym wiekiem 30 sekund**
- Wiadomości w kolejce starsze niż 30 sekund są odrzucane

# Tryby adresu URL

- `wss://` = bezpieczny (TLS), zalecany
- `ws://` = nieszyfrowany, przydatny do testów lokalnych

Przykładowy lokalny adres URL:

- `ws://127.0.0.1:8765`

# Najlepsze praktyki

1. Używaj jednego stabilnego adresu URL dla każdej usługi backendowej.
2. Zachowuj spójny format ładunku dla każdego przypadku użycia.
3. Obsługuj zamknięte/uszkodzone połączenia za pomocą logiki awaryjnego interfejsu.
4. Używaj akcji zamykania, gdy przepływ jest zakończony.
5. Do środowiska produkcyjnego używaj `wss://`.
