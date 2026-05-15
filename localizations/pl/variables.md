---
title: Zmienne
description: Jak tworzyć i używać zmiennych.
---

# Zmienne w FancyMenu

Zmienne to potężna funkcja w FancyMenu, która pozwala przechowywać i ponownie wykorzystywać informacje w całych konfiguracjach menu. Działają jak pojemniki, do których możesz wkładać różne typy danych, nadać każdemu pojemnikowi nazwę, a potem odwoływać się do tych danych później za pomocą nazwy zmiennej. Zmienne otwierają mnóstwo możliwości tworzenia dynamicznych menu, które zmieniają się w zależności od zdefiniowanych przez Ciebie warunków.

## Tworzenie zmiennych

Aby utworzyć zmienną w FancyMenu:

1. Upewnij się, że nie jesteś aktualnie w Edytorze Układu.
2. Kliknij pasek menu u góry ekranu.
3. Przejdź do **Customization -> Variables -> Manage Variables**.
4. W oknie „Manage Variables”, które się pojawi, kliknij przycisk **Add Variable**.
5. Wpisz nazwę nowej zmiennej i kliknij **OK**.

To wszystko! Twoja zmienna jest gotowa do użycia. Zobaczysz ją na liście w oknie „Manage Variables”.

FancyMenu 3.9.0 przebudowuje okno Manage Variables. Najważniejsze akcje są dostępne przez menu kontekstowe po kliknięciu prawym przyciskiem myszy, lista obsługuje nawigację klawiaturą, zmienne można kopiować/wklejać, zmiany można cofać/ponawiać, wpisywanie rozpoczyna wyszukiwanie, **DEL** usuwa zaznaczoną zmienną, a **CTRL + S** zatwierdza okno.

## Ustawianie wartości zmiennych

Pusta zmienna sama w sobie nie jest zbyt użyteczna. Aby zmienne działały na Twoją korzyść, musisz wpisywać do nich dane. W FancyMenu nazywa się to „ustawianiem wartości zmiennej”.

Są dwa główne sposoby ustawiania wartości zmiennej:

1. W oknie „Manage Variables” znajdź zmienną na liście, kliknij ją, a następnie kliknij **Set Value**. Wpisz dane, które chcesz przechować.

2. Podczas dostosowywania menu użyj akcji **Set Variable** na elemencie Button, Slider lub Ticker. W tej akcji podajesz nazwę zmiennej i wartość, która ma zostać w niej zapisana. Gdy ktoś na przykład kliknie przycisk z tą akcją, zmienna zostanie zaktualizowana do nowej wartości.

Na przykład załóżmy, że tworzysz zmienną o nazwie `clicks`, aby zliczać, ile razy przycisk został naciśnięty. Dodasz akcję **Set Variable** do przycisku i użyjesz placeholdera w wartości akcji, aby zwiększać liczbę kliknięć za każdym razem, na przykład tak:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Tak to działa:
1. Placeholder **Get Stored Variable** pobiera bieżącą wartość zmiennej `clicks`.
2. Placeholder **Calculator** dodaje do tej wartości 1.
3. Następnie wynik jest zapisywany z powrotem do zmiennej `clicks` za pomocą akcji **Set Variable**.

Za każdym razem, gdy przycisk zostanie kliknięty, zmienna `clicks` zwiększy się o 1, skutecznie zliczając łączną liczbę kliknięć.

## Używanie zmiennych

Teraz, gdy Twoje zmienne przechowują dane, możesz używać tych danych w różnych częściach konfiguracji menu:

* **Wymagania ładowania**: Możesz sprawdzać wartość zmiennej w wymaganiu ładowania, aby kontrolować, kiedy mają się pojawiać określone elementy menu. Na przykład możesz sprawić, by element pojawiał się tylko wtedy, gdy zmienna `clicks` jest większa niż 5, używając kombinacji wymagania **Is Number** i placeholdera **Get Stored Variable**.

* **Placeholders**: Zmienne można wstawiać do tekstu za pomocą placeholdera **Get Stored Variable**. Jeśli masz element tekstowy, możesz użyć `{"placeholder":"getvariable","values":{"name":"clicks"}}`, aby wyświetlić bieżącą wartość zmiennej „clicks”.

* **Zagnieżdżone placeholdery**: Możesz nawet używać zmiennych wewnątrz innych placeholderów! Powyższy przykład z liczeniem kliknięć pokazał to, używając placeholdera **Get Stored Variable** wewnątrz placeholdera **Calculator**.

* **Akcje**: Zmienne można wykorzystywać w akcjach, aby tworzyć dynamiczne zachowanie w zależności od wartości zmiennych. Oto kilka przykładów:
    - Użyj instrukcji **IF** w skrypcie akcji, aby sprawdzić wartość zmiennej za pomocą kombinacji wymagania ładowania **Is Number** i akcji **Get Stored Variable**, a następnie wykonaj różne działania w zależności od wyniku. Na przykład możesz mieć przycisk z tekstem „Kliknąłeś mnie X razy!” i użyć bloku IF, aby pokazać specjalny komunikat, jeśli liczba kliknięć przekroczy 10.
    - Połącz placeholder **Get Stored Variable** z akcją **Copy to Clipboard**, aby pozwolić użytkownikom skopiować wartość zmiennej do schowka.
    - Używaj zmiennych w akcji **Open GUI**, aby wczytywać różne ekrany na podstawie postępów lub preferencji użytkownika, które śledzisz za pomocą zmiennych.

## Przykłady zmiennych

Oto kilka przykładów, które mogą zainspirować Cię do własnego użycia zmiennych:

1. **Wysoki wynik**: Utwórz zmienną `highscore` i przycisk, który ustawia ją na aktualny wynik gracza, jeśli jest on wyższy od istniejącej wartości. Wyświetl wysoki wynik w menu za pomocą placeholdera **Get Stored Variable**.

2. **Wybór poziomu trudności**: Utwórz zmienne dla różnych poziomów trudności gry, takich jak `easy`, `medium` i `hard`. Użyj przycisków, aby ustawiać zmienną trudności, oraz pokazuj lub ukrywaj elementy zależnie od wybranego poziomu.

3. **Postęp samouczka**: Dodaj zmienne do śledzenia postępów gracza w samouczku, na przykład `tutorial_step`. Zwiększaj wartość zmiennej po ukończeniu każdego kroku i używaj wymagań ładowania, aby stopniowo odsłaniać kolejne elementy menu.

Zmienne w połączeniu z innymi funkcjami FancyMenu dają Ci niesamowitą elastyczność w tworzeniu menu dopasowanych do działań i preferencji każdego gracza. Eksperymentuj z różnymi konfiguracjami zmiennych, aby w pełni wykorzystać potencjał personalizacji menu!
