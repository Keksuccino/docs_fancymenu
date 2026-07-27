---
title: Polecenia
description: Polecenia FancyMenu i sposób ich użycia.
---

# Polecenia

FancyMenu dodaje do gry kilka poleceń, które mogą być bardzo przydatne, zwłaszcza w połączeniu z innymi modami, takimi jak FTB Quests.

> [!WARNING]
> FancyMenu musi być obecne na **SERWERZE** (oraz po stronie klienta), aby używać poleceń w trybie wieloosobowym!

## Gracze docelowi i uprawnienia

Argument gracza docelowego w poleceniach `/openguiscreen`, `/closeguiscreen` i `/fmlayout` jest opcjonalny. Gdy gracz go pominie, polecenie dotyczy jego samego. Jeśli podany zostanie cel, można używać zwykłych nazw graczy oraz selektorów, takich jak `@a`.

- Podanie argumentu celu w `/openguiscreen` lub `/closeguiscreen` wymaga **poziomu uprawnień 2** (Game Master / OP poziom 2), nawet jeśli wskazuje źródło polecenia.
- Podanie argumentu celu w `/fmlayout` wymaga **poziomu uprawnień 3** (Administrator / OP poziom 3), nawet jeśli wskazuje źródło polecenia.
- Każde polecenie podrzędne `/fmdata` wymaga **poziomu uprawnień 2** (Game Master / OP poziom 2).

W przypadku trzech poleceń z opcjonalnym celem pominięcie celu działa tylko wtedy, gdy źródłem polecenia jest gracz. Konsola serwera musi podać cel i spełniać wymagania uprawnień dla argumentu celu.

## /openguiscreen

Polecenie `/openguiscreen` otwiera Vanilla, moda lub [Custom GUI](./custom-guis). Może być używane wobec innych graczy, gdy FancyMenu jest zainstalowane na serwerze i na ich klientach.

Zobacz [Otwieranie GUI za pomocą polecenia](./opengui-command) oraz [Identyfikatory ekranów](./screen-identifiers).

Nie każdy ekran moda można utworzyć bezpośrednio. FancyMenu wyświetla błąd, gdy docelowy ekran nie jest obsługiwany. W lokalnym layoucie użyj [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) na widżecie, który normalnie go otwiera.

**Użycie:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

Polecenie `/closeguiscreen` zamyka bieżący ekran dla źródła polecenia lub wybranych graczy. Jest przydatne w modach z zadaniami, wydarzeniami lub automatyzacją, które mogą uruchamiać polecenia.

**Użycie:** `/closeguiscreen [<target_players>]`

## /fmlayout

Polecenie `/fmlayout` ustawia, czy układ jest włączony na jednym lub kilku klientach. Użyj dokładnie takiej nazwy układu, jaka jest wyświetlana w FancyMenu, a nazwy zawierające spacje umieść w cudzysłowie.

**Użycie:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Przykłady:

- `/fmlayout quest_complete true` włącza `quest_complete` dla gracza, który uruchomił polecenie.
- `/fmlayout quest_complete false @a` wyłącza je dla każdego gracza online. Podanie argumentu celu wymaga poziomu uprawnień 3.

## /fmvariable

Polecenie `/fmvariable` ustawia i odczytuje [zmienne FancyMenu](./variables).

Aby wykonać to polecenie jako inny gracz, użyj wbudowanego w Vanilla polecenia `/execute as`:
`/execute as ExamplePlayer run fmvariable ...`

**Użycie:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Pobieranie

Aby **odczytać wartość zmiennej**, użyj podpolecenia `get` w ten sposób:
`/fmvariable get some_variable`

Następnie wartość tej zmiennej zostanie wypisana na czacie.

### Ustawianie

Aby **ustawić zmienną**, podaj wartość logiczną odpowiadającą za informację zwrotną na czacie przed nową wartością:
`/fmvariable set some_variable true new_value`

Argument `send_chat_feedback` kontroluje, czy FancyMenu potwierdzi zmianę na czacie. Argument `set_to_value` pochłania resztę polecenia, więc wartość może zawierać spacje. Na przykład `/fmvariable set greeting false Hello from FancyMenu` zapisuje `Hello from FancyMenu` bez wysyłania komunikatu o powodzeniu.

## /fmdata

Polecenie `/fmdata` wysyła niestandardowe dane między serwerem a klientami FancyMenu, zarządza nasłuchiwaczami po stronie serwera i konfiguruje dane wysyłane podczas dołączania graczy. Każde podpolecenie `/fmdata` wymaga poziomu uprawnień 2.

Zobacz [FM Data](./fm-data), aby poznać wszystkie podpolecenia, składnię i przykłady.
