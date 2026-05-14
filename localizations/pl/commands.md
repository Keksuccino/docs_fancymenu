---
title: Polecenia
description: Polecenia FancyMenu i sposób ich używania.
---

# Polecenia

FancyMenu dodaje do gry kilka poleceń, które mogą być bardzo przydatne w połączeniu z innymi modami, takimi jak FTB Quests.

> FancyMenu musi być zainstalowany na **SERWERZE** (i u klienta), aby używać poleceń w trybie wieloosobowym!
{.is-warning}

## /openguiscreen

Polecenie `/openguiscreen` pozwala otworzyć GUI (vanilla/modowe oraz niestandardowe GUI).
Może nawet zdalnie otwierać GUI dla innych graczy, gdy FancyMenu jest zainstalowany zarówno na serwerze, jak i na klientach.

Bardziej szczegółowy opis tego polecenia znajdziesz na stronie [Otwieranie GUI za pomocą polecenia](/opengui-command).

To polecenie nie zadziała dla każdego ekranu, zwłaszcza ekranów z modów. Jeśli polecenie nie zdoła otworzyć ekranu, wyświetli błąd. Niewiele da się wtedy zrobić, ponieważ najprawdopodobniej jest to ekran zbyt złożony, aby FancyMenu mógł otworzyć go automatycznie.

Nie będę też już ręcznie dodawać kompatybilności dla ekranów z modów, ponieważ dodanie obsługi wszystkich modów zajęłoby mi wieki, przepraszam.

**Użycie:** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

Polecenie `/closeguiscreen` pozwala zamknąć aktualne GUI.

Hę? Mówisz, że to całkiem bezużyteczne?
Cóż, tak, ale jednak nie.

To polecenie jest przydatne, gdy używasz modów, które uruchamiają polecenia po określonych akcjach.
Tak więc, owszem, to polecenie jest absolutnie bezużyteczne bez innych modów, ale może być naprawdę pomocne, jeśli masz zainstalowane odpowiednie mody!

**Użycie:** `/closeguiscreen <target_player>`

## /fmvariable

Polecenie `/fmvariable` מאפשרa ustawianie i pobieranie zmiennych FancyMenu.

Aby wykonać to polecenie jako inny gracz na serwerach, możesz użyć vanilla polecenia `/execute as`.
Załóżmy więc, że chcesz wykonać polecenie `/fmvariable` jako gracz `ExamplePlayer`. W takim przypadku wpiszesz:
`/execute as ExamplePlayer run fmvariable...`.

**Użycie:** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### Pobieranie
Aby **pobrać wartość zmiennej**, użyj podpolecenia `get` w ten sposób:
`/fmvariable get some_variable`

Następnie wartość tej zmiennej zostanie wyświetlona na czacie.

### Ustawianie
Aby **ustawić zmienną**, użyj podpolecenia `set` w ten sposób:
`/fmvariable set some_variable new_value true`

Ostatni argument służy do określenia, czy chcesz otrzymywać informacje zwrotne na czacie, czyli czy to polecenie ma wyświetlać wiadomości na twoim czacie.
