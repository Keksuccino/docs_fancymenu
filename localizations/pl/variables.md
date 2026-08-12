---
title: Zmienne
description: Jak tworzyć i używać zmienne.
---
# Zmienne w FancyMenu

Zmienne przechowują wartości tekstowe, z których mogą korzystać układy, akcje, placeholdery, wymagania, listenery, harmonogramy i niestandardowe GUI.

## Tworzenie zmiennych

Aby utworzyć zmienną w FancyMenu:

1. Upewnij się, że nie jesteś aktualnie w Edytorze Układu. 
2. Kliknij pasek menu u góry ekranu.
3. Przejdź do **Customization -> Variables -> Manage Variables**.
4. W oknie „Manage Variables”, które się pojawi, kliknij przycisk **Add Variable**.
5. Wpisz nazwę nowej zmiennej i kliknij **OK**.

To wszystko! Twoja zmienna jest gotowa do użycia. Możesz ją zobaczyć na liście w oknie „Manage Variables”.

Okno Manage Variables obsługuje menu kontekstowe po kliknięciu prawym przyciskiem myszy, nawigację klawiaturą, kopiowanie/wklejanie, cofnij/ponów, wyszukiwanie podczas pisania, **Delete** do usuwania oraz **Ctrl/Command + S** do zapisywania.

## Ustawianie wartości zmiennych

Pusta zmienna sama w sobie nie jest zbyt użyteczna. Aby zmienne działały na twoją korzyść, musisz wprowadzić do nich dane. W FancyMenu nazywa się to „ustawianiem wartości zmiennej”. 

Są dwa główne sposoby ustawiania wartości zmiennej:

1. W oknie „Manage Variables” znajdź zmienną na liście, kliknij ją, a następnie kliknij **Set Value**. Wpisz dane, które chcesz przechować.

2. Podczas dostosowywania menu użyj [akcji **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) na elemencie [Button](./elements#button), [Slider](./elements#slider) lub [Ticker](./elements#ticker).

Na przykład utwórz zmienną o nazwie `clicks` i dodaj [akcję **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) do przycisku:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Tak to działa:
1. [Placeholder **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) pobiera aktualną wartość zmiennej `clicks`.
2. [Placeholder **Calculator**](./placeholders#calculator-calc) bierze tę wartość i dodaje do niej 1.
3. Wynik jest zapisywany z powrotem do `clicks` za pomocą [akcji **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

Za każdym razem, gdy przycisk zostanie kliknięty, zmienna `clicks` zwiększy się o 1, skutecznie licząc łączną liczbę kliknięć.

## Używanie zmiennych

Teraz, gdy masz zmienne przechowujące dane, możesz używać tych danych w różnych częściach konfiguracji menu:

* [**Loading Requirements**](./conditions): Sprawdzaj wartość zmiennej, aby kontrolować, kiedy elementy się pojawiają. Na przykład wyświetl element, gdy `clicks` jest większe niż 5, łącząc [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) z [placeholderem **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

* **Placeholders**: Wstaw zmienną do tekstu za pomocą [placeholdera **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable), na przykład `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Zagnieżdżone placeholdery**: Możesz użyć [placeholdera **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) wewnątrz [placeholdera **Calculator**](./placeholders#calculator-calc).

* **Akcje**: Zmienne mogą tworzyć dynamiczne zachowanie:
  - Użyj instrukcji **IF** w [skrypcie akcji](./action-scripts#what-are-statements) z [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) oraz [placeholderem **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Połącz [placeholder **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) z [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Używaj zmiennych w [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), aby wybrać ekran na podstawie zapisanych postępów lub preferencji.

## Przykłady zmiennych

Oto kilka przykładów, które mogą zainspirować cię do własnego użycia zmiennych:

1. **Wynik najwyższy**: Utwórz zmienną `highscore` i przycisk, który ustawia ją na aktualny wynik gracza, jeśli jest wyższy niż istniejąca wartość. Wyświetlaj ją za pomocą [placeholdera **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Selektor trudności**: Utwórz zmienne dla różnych poziomów trudności gry, takich jak `easy`, `medium` i `hard`. Użyj przycisków do ustawiania zmiennej trudności i pokazuj/ukrywaj elementy na podstawie wybranego poziomu.

3. **Postęp samouczka**: Dodaj zmienne do śledzenia postępów gracza w samouczku, na przykład `tutorial_step`. Zwiększaj wartość zmiennej po ukończeniu każdego kroku i używaj wymagań ładowania, aby stopniowo odsłaniać kolejne elementy menu.

## Trwałość, zakres i przechowywanie

Zmienne są współdzielone w ramach bieżącej instancji Minecrafta. Nie są rozdzielone per układ, świat, serwer ani gracz.

Wartości są zapisywane natychmiast w `<game-directory>/config/fancymenu/user_variables.db` i zachowują się po ponownym uruchomieniu.

- **Reset on Launch** czyści tę zmienną przy następnym uruchomieniu gry.
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) usuwa wszystkie zapisane wartości zmiennych.
- Nazwy rozróżniają wielkość liter. Używaj prostych, unikalnych nazw, takich jak `tutorial_step`.

[Placeholder **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) zwraca `0`, gdy nazwana zmienna nie istnieje lub gdy jej zapisana wartość jest pusta. To zachowanie ma znaczenie w porównaniach i wyrażeniach kalkulatora.

[Akcja **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) używa formatu `variable_name:variable_value` i dzieli tekst przy pierwszym dwukropku, więc wartość może zawierać więcej dwukropków.

Nie przechowuj haseł, tokenów ani innych poufnych danych w zmiennych FancyMenu. Są to czytelne dane konfiguracyjne.
