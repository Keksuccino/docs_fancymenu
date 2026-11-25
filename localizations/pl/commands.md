---
title: Polecenia
description: Polecenia FancyMenu i sposób ich używania.
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# Polecenia

FancyMenu dodaje do gry kilka poleceń, które mogą być bardzo przydatne w połączeniu z innymi modami, takimi jak FTB Quests.

> [!WARNING]
> Aby używać poleceń w trybie wieloosobowym, FancyMenu musi być zainstalowane na **SERWERZE** (i u klienta)!

## Gracze docelowi i uprawnienia

Argument gracza docelowego w poleceniach `/openguiscreen`, `/closeguiscreen` i `/fmlayout` jest opcjonalny. Jeśli gracz go pominie, polecenie zadziała na niego. Jeśli wskażesz cel, możesz użyć zwykłych nazw graczy i selektorów, takich jak `@a`.

- Podanie argumentu celu w poleceniu `/openguiscreen` lub `/closeguiscreen` wymaga **poziomu uprawnień 2** (Mistrz Gry / poziom OP 2), nawet jeśli wskazuje ono osobę wykonującą polecenie.
- Podanie argumentu celu w poleceniu `/fmlayout` wymaga **poziomu uprawnień 3** (Administrator / poziom OP 3), nawet jeśli wskazuje ono osobę wykonującą polecenie.
- Każde podpolecenie `/fmdata` wymaga **poziomu uprawnień 2** (Mistrz Gry / poziom OP 2).

W przypadku trzech poleceń z opcjonalnym celem pominięcie celu działa tylko wtedy, gdy polecenie wykonuje gracz. Konsola serwera musi podać cel i spełniać wymagania dotyczące uprawnień dla argumentu celu.

## /openguiscreen

Polecenie `/openguiscreen` otwiera ekran Vanilla, moda lub [własne GUI](/custom-guis). Może wskazywać innych graczy, jeśli FancyMenu jest zainstalowane na serwerze i u tych graczy.

Zobacz [Otwieranie GUI za pomocą polecenia](/opengui-command) i [Identyfikatory ekranów](/screen-identifiers).

Nie każdy ekran moda można utworzyć bezpośrednio. FancyMenu wyświetli błąd, jeśli wskazany ekran nie jest obsługiwany. W lokalnym układzie użyj opcji [**Naśladuj przycisk Vanilla/moda**](/action-scripts#mimic-vanillamod-button) w widżecie, który normalnie otwiera ten ekran.

**Użycie:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

Polecenie `/closeguiscreen` zamyka bieżący ekran osoby wykonującej polecenie lub wybranych graczy. Przydaje się w połączeniu z modami do zadań, wydarzeń lub automatyzacji, które mogą uruchamiać polecenia.

**Użycie:** `/closeguiscreen [<target_players>]`

## /fmlayout

Polecenie `/fmlayout` włącza lub wyłącza układ u jednego albo kilku klientów. Użyj nazwy układu dokładnie tak, jak wyświetla się w FancyMenu, a nazwy zawierające spacje ujmij w cudzysłów.

**Użycie:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Przykłady:

- `/fmlayout quest_complete true` włącza układ `quest_complete` u gracza wykonującego polecenie.
- `/fmlayout quest_complete false @a` wyłącza go u wszystkich graczy online. Podanie argumentu celu wymaga poziomu uprawnień 3.

## /fmvariable

Polecenie `/fmvariable` ustawia i odczytuje [zmienne FancyMenu](/variables).

Aby wykonać to polecenie jako inny gracz, użyj waniliowego polecenia `/execute as`:
`/execute as ExamplePlayer run fmvariable ...`

**Użycie:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Odczyt

Aby **odczytać wartość zmiennej**, użyj podpolecenia `get` w następujący sposób:
`/fmvariable get some_variable`

Wartość zmiennej zostanie wyświetlona na czacie.

### Ustawianie

Aby **ustawić zmienną**, podaj wartość logiczną określającą informację zwrotną na czacie przed nową wartością:
`/fmvariable set some_variable true new_value`

Argument `send_chat_feedback` określa, czy FancyMenu potwierdzi zmianę na czacie. Argument `set_to_value` obejmuje resztę polecenia, więc wartość może zawierać spacje. Na przykład `/fmvariable set greeting false Hello from FancyMenu` zapisuje `Hello from FancyMenu` bez wyświetlania informacji o pomyślnym wykonaniu.

## /fmdata

Polecenie `/fmdata` przesyła własne dane między serwerem a klientami FancyMenu, zarządza nasłuchiwaczami po stronie serwera, konfiguruje dane wysyłane przy dołączaniu graczy i eksportuje tę konfigurację do [czatów AI](/export-for-ai#servers). Każde podpolecenie `/fmdata` wymaga poziomu uprawnień 2.

Zobacz [FM Data](/fm-data), aby poznać wszystkie podpolecenia, składnię i przykłady.
