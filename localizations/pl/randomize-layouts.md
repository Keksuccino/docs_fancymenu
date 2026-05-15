---
title: Losowanie układów
description: Jak losować całe układy lub ich części.
---

# Losowanie

FancyMenu ma wiele funkcji, które pomagają losować układy lub ich części.

Może to być przydatne na przykład wtedy, gdy chcesz, aby użytkownicy widzieli za każdym razem inne tła ekranu po otwarciu ekranu albo losowe wskazówki na ekranie ładowania.

# Losowanie układów

FancyMenu ma funkcję, która pozwala utworzyć grupę układów, a system automatycznie wybierze z niej losowy układ. Dzięki temu możesz za każdym razem wyświetlać zupełnie inny, losowy wygląd menu, gdy użytkownik uruchamia grę lub otwiera ekran, ale można to też wykorzystać do zmiany tylko części ekranu, na przykład tła.

## Tryb losowy

Aby losować układy, musisz włączyć **Tryb losowy** dla każdego układu, który ma być możliwym wyborem w losowaniu. Aby to zrobić, **kliknij prawym przyciskiem myszy** na **tło edytora** i znajdź opcję **Tryb losowy**.

<br>

<img width="351" alt="Zrzut ekranu_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/ef0f22d5-2f48-47cd-b526-d12415d8e099">

## Identyfikator grupy losowej

Po włączeniu trybu losowego musisz ustawić **Identyfikator grupy losowej**.
Ta liczba musi być **taka sama** dla każdego układu, który ma należeć do **tej samej grupy**.

<br>

<img width="301" alt="Zrzut ekranu_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/dde0c94e-9729-4251-9aca-32a55c3dfd02">

<br>

<img width="377" alt="Zrzut ekranu_8" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/25e7777c-0503-4e54-b866-e85647241eee">

## Zachowanie losowania

Jeśli chcesz, aby system wybierał losowy układ z grupy **tylko raz na sesję gry**, włącz opcję **Losuj tylko za pierwszym razem**. Spowoduje to wybranie układu przy pierwszym otwarciu ekranu, a następnie system będzie zawsze używać układu wybranego za pierwszym razem. Jeśli ta opcja jest wyłączona, losowy układ będzie wybierany za każdym razem, gdy ekran zostanie otwarty.

<br>

<img width="305" alt="Zrzut ekranu_9" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/355e49eb-73b0-4646-aeb2-c6f113f6ce3b">

# Przykładowy scenariusz 1: Tło

Załóżmy, że chcesz losować tło ekranu tytułowego.

Aby to zrobić, musisz utworzyć **jeden układ na każde tło** i _**TYLKO**_ zmieniać tło w tych układach oraz włączyć tryb losowy z poprawnym identyfikatorem grupy losowej.

W tym przykładzie używamy identyfikatora grupy losowej **10**. Ten identyfikator musi zostać ustawiony dla każdego układu w tej losowej grupie układów.

Najprostszym sposobem jest przygotowanie układu z poprawnym identyfikatorem grupy losowej, a następnie użycie opcji **Zapisz jako**. Zmieniaj tło za każdym razem, gdy zapisujesz układ pod nową nazwą, a otrzymasz zestaw układów z różnymi tłami, z których jeden będzie wybierany za każdym razem, gdy otwierasz ekran, albo raz na sesję gry.

# Przykładowy scenariusz 2: Element

Innym częstym przypadkiem użycia jest losowanie elementu tekstowego lub graficznego.

Tak samo jak w przypadku tła, utwórz jeden układ dla każdej wersji elementu, który ma być losowo wybierany. Dodaj do układów tylko ten element i nic więcej. Nie dostosowuj niczego i nie dodawaj innych elementów.

Następnie po prostu zapisz wszystkie układy z tym samym identyfikatorem grupy losowej, a jeden układ z grupy zostanie wybrany, gdy otworzysz ekran lub uruchomisz grę.
