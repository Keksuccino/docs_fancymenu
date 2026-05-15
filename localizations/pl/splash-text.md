---
title: Tekst powitalny
description: Jak tworzyć własne teksty powitalne w FancyMenu.
---

# Niestandardowy element tekstu powitalnego

Element tekstu powitalnego w FancyMenu to w pełni konfigurowalne ulepszenie odbijających się tytułów z Minecrafta. Zachowuje znajome odbijanie, jednocześnie dając Ci kontrolę nad tym, co się wyświetla, jak wygląda i kiedy się aktualizuje.

> Pamiętaj, że nie da się tak naprawdę dostosować oryginalnego elementu Vanilla Splash Text na ekranie tytułowym, więc powinieneś go **usunąć** i zamiast niego użyć niestandardowego elementu Splash Text.
{.is-warning}

## Dodawanie i wybieranie elementu
- Otwórz edytor układu i dodaj element o nazwie `Splash Text`.
- Kliknij go lewym przyciskiem myszy raz, aby go zaznaczyć i wyświetlić ramkę ograniczającą, a następnie kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe. Wszystkie opcje konfiguracji znajdują się właśnie w tym menu.

## Wybór źródła tekstu powitalnego
- `Source Mode: Vanilla` zachowuje klasyczne losowe teksty powitalne dołączone do Minecrafta.
- `Source Mode: Direct Input` pozwala wpisać własny tekst w polu `Input Splash Text`. Obsługuje tylko jedną linię tekstu powitalnego, ale ta linia może zawierać placeholdery.
- `Source Mode: Text File` pobiera losową linię z pliku `.txt`, który wybierzesz przez `Set Source Text File`. Każda niepusta linia może stać się aktywnym tekstem powitalnym.
- Zmiana trybu resetuje aktywny tekst, więc możesz bezpiecznie eksperymentować. Jeśli tekst wydaje się zablokowany, przełącz na inny tryb albo kliknij `Refresh On Screen Load: Enabled`, aby wymusić ponowne losowanie za każdym razem, gdy menu się otworzy.

## Przykładowy plik tekstowy
Gdy używasz trybu źródła „Text File”, zapisz listę tekstów powitalnych jako zwykły plik tekstowy (UTF-8 bez BOM). Każda linia to potencjalny tekst powitalny:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Zastąp `your_placeholder_id_here` placeholderem, który ma zostać rozwiązany w czasie działania. FancyMenu wybiera losową niepustą linię za każdym razem, gdy tekst powitalny się odświeża.

## Nadawanie wyglądu według własnego uznania
- Użyj `Set Scale` i `Set Rotation`, aby kontrolować rozmiar oraz kąt obrotu.
- `Set Text Color` przyjmuje wartość szesnastkową (na przykład `#FFFF00`), aby dopasować tekst do motywu.
- `Shadow: Enabled` dodaje cień Minecrafta; wyłącz to, jeśli chcesz płaski tekst.
- `Bouncing: Enabled` zachowuje znajomy efekt podskakiwania; wyłącz go, aby uzyskać statyczną etykietę.
- FancyMenu renderuje tekst powitalny jako pełny komponent Minecrafta, więc kody kolorów i inne dekoracje tekstu działają zgodnie z oczekiwaniami.

## Funkcje dynamicznego tekstu
- Placeholdery są rozwiązywane przed renderowaniem, więc możesz odwoływać się w tekście powitalnym do nazw graczy, dat lub innych obsługiwanych wartości.
- Ponieważ element akceptuje serializowany JSON komponentu Minecrafta, możesz wklejać zaawansowane fragmenty JSON do Direct Input lub do pliku tekstowego. Element automatycznie je deserializuje i w razie problemu wraca do dosłownego tekstu.

## Rozwiązywanie problemów
- Pusty tekst w Direct Input pokazuje podczas edycji `< empty splash element >`. Wpisz cokolwiek (nawet spację), aby usunąć ostrzeżenie.
- Jeśli plik tekstowy nie zawiera żadnych poprawnych linii, element wyświetla `ERROR: SPLASH FILE IS EMPTY`. Dodaj co najmniej jedną niepustą linię i ponownie otwórz ekran.
- Błędy w serializowanym JSON-ie powodują powrót do zwykłego tekstu. Trzymaj się standardowej struktury JSON Mojanga albo przetestuj fragmenty za pomocą vanilla komendy `/tellraw` przed wklejeniem.
