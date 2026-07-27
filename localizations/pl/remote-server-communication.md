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
FancyMenu używa tego ID do śledzenia połączenia i udostępniania go w zmiennych nasłuchiwaczy.

# Szybki start

1. Dodaj [**Połącz z zdalnym serwerem**](#connect-to-remote-server), gdy połączenie ma zostać otwarte wcześniej.
2. Dodaj [**Wyślij dane do zdalnego serwera**](#send-data-to-remote-server) z tym samym adresem URL.
3. Dodaj [**Po odebraniu danych z zdalnego serwera**](#on-remote-server-data-received), aby reagować na odpowiedzi.
4. Użyj [**Po połączeniu z zdalnym serwerem**](#on-remote-server-connected) oraz [**Po zamknięciu połączenia z zdalnym serwerem**](#on-remote-server-connection-closed) do logiki stanu połączenia.
5. Zamykaj połączenia za pomocą [**Zamknij połączenie z zdalnym serwerem**](#close-remote-server-connection) lub [**Zamknij wszystkie połączenia z zdalnym serwerem**](#close-all-remote-server-connections).

# Akcje

## Połącz z zdalnym serwerem

Otwiera lub ponownie wykorzystuje połączenie z zdalnym serwerem bez wysyłania danych ładunku.

Wejście:

- URL zdalnego serwera

## Wyślij dane do zdalnego serwera

Łączy się (lub ponownie wykorzystuje istniejące połączenie) i wysyła dane tekstowe.

Wejścia:

1. URL zdalnego serwera
2. Dane

## Zamknij połączenie z zdalnym serwerem

Zamyka jedno połączenie na podstawie ID żądania.

Wejście:

- ID żądania połączenia

## Zamknij wszystkie połączenia z zdalnym serwerem

Zamyka wszystkie aktualnie aktywne połączenia z zdalnym serwerem.

# Nasłuchiwacze

## Po połączeniu z zdalnym serwerem

Wywoływane po pomyślnym otwarciu połączenia z zdalnym serwerem.

Zmienne:

- `$$request_id`
- `$$remote_server_url`

## Po odebraniu danych z zdalnego serwera

Wywoływane, gdy dane zostaną odebrane od podłączonego zdalnego serwera.

Zmienne:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Po zamknięciu połączenia z zdalnym serwerem

Wywoływane, gdy połączenie z zdalnym serwerem zostanie zamknięte.

Zmienne:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Zachowanie połączenia

- Połączenia są **inicjowane przez klienta**
- FancyMenu utrzymuje połączenia aktywne w tle
- Jeśli połączenie się zawiesi lub przekroczy limit czasu, FancyMenu ponawia próbę co 10 sekund
- Gdy zawieszone połączenie zostanie przywrócone, FancyMenu rejestruje komunikat o przywróceniu
- Niewysłane wiadomości wychodzące są kolejkowane z **maksymalnym wiekiem 30 sekund**
- Wiadomości w kolejce starsze niż 30 sekund są odrzucane

# Tryby URL

- `wss://` jest używany tak, jak zapisano, i jest zalecany.
- `ws://` jest używany tak, jak zapisano, i jest nieszyfrowany.
- `https://` jest konwertowany na `wss://`.
- `http://` jest konwertowany na `ws://`.
- Sam host jest poprzedzany `wss://`.
- Inne jawnie określone schematy URL są odrzucane.

Preferuj jawne adresy URL `wss://`. Przykładowy lokalny adres URL:

- `ws://127.0.0.1:8765`

Używaj jednego stabilnego adresu URL na usługę, obsługuj stany nasłuchiwaczy zamknięcia/zawieszenia i zamykaj połączenia, gdy nie są już potrzebne.
