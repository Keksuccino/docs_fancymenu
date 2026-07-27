---
title: Tekst powitalny
description: Jak tworzyć własne teksty powitalne w FancyMenu.
---

# Własny element tekstu powitalnego

Element Splash Text w FancyMenu to w pełni konfigurowalna, ulepszona wersja odbijającego się tytułu z Minecrafta. Zachowuje znane, sprężyste animacje, a jednocześnie daje Ci kontrolę nad tym, co się wyświetla, jak wygląda i kiedy się odświeża.

> [!WARNING]
> Pamiętaj, że oryginalnego, domyślnego elementu Splash Text na ekranie tytułowym nie da się tak naprawdę dostosować, więc powinieneś go **usunąć** i zamiast niego użyć własnego elementu Splash Text.

## Dodawanie i wybieranie elementu
- Otwórz edytor układu i dodaj element o nazwie `Splash Text`.
- Kliknij go lewym przyciskiem myszy, aby go zaznaczyć i wyświetlić ramkę obwiedni, a następnie kliknij prawym przyciskiem, aby otworzyć menu kontekstowe. Wszystkie opcje konfiguracji znajdują się właśnie w tym menu.

## Wybór źródła tekstu powitalnego
- `Source Mode: Vanilla` zachowuje klasyczne, losowe teksty powitalne dołączone do Minecrafta.
- `Source Mode: Direct Input` pozwala wpisać własny tekst w polu `Input Splash Text`. Obsługuje tylko jedną linię tekstu powitalnego, ale linia może zawierać placeholdery.
- `Source Mode: Text File` pobiera losową linię z pliku `.txt` wybranego przez `Set Source Text File`. Każda niepusta linia może stać się aktywnym tekstem powitalnym.
- Przełączanie trybów resetuje aktywny tekst, więc możesz bezpiecznie eksperymentować. Jeśli tekst wydaje się zablokowany, przełącz inny tryb albo kliknij `Refresh On Screen Load: Enabled`, aby wymusić losowanie za każdym razem, gdy menu się otwiera.

## Przykładowy plik tekstowy
Podczas korzystania z trybu źródła „Text File” zapisz listę tekstów powitalnych jako zwykły plik tekstowy (UTF-8 bez BOM). Każda linia może być potencjalnym tekstem powitalnym:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Zastąp `your_placeholder_id_here` placeholderem, który ma zostać rozwiązany w czasie działania. FancyMenu wybiera losową, niepustą linię za każdym razem, gdy tekst powitalny się odświeża.

## Nadawanie wyglądu według własnych upodobań
- Użyj `Set Scale` i `Set Rotation`, aby kontrolować rozmiar oraz kąt obrotu.
- `Set Text Color` akceptuje wartość hex (na przykład `#FFFF00`), aby dopasować kolor do motywu.
- `Shadow: Enabled` dodaje cień rzucany przez Minecrafta; wyłącz tę opcję, aby uzyskać płaski tekst.
- `Bouncing: Enabled` zachowuje znane kołysanie; wyłącz, jeśli chcesz statyczną etykietę.
- FancyMenu renderuje tekst powitalny jako pełny komponent Minecrafta, więc kody kolorów i inne dekoracje tekstu działają dokładnie tak, jak powinny.

## Dynamiczne funkcje tekstu
- Placeholdery są rozwiązywane przed renderowaniem, więc możesz odwoływać się w tekście powitalnym do nazw graczy, dat lub innych obsługiwanych wartości.
- Ponieważ element obsługuje serializowany JSON komponentów Minecrafta, możesz wklejać zaawansowane fragmenty JSON do trybu Direct Input lub do pliku tekstowego. Element automatycznie je deserializuje i w razie problemu wraca do tekstu dosłownego.

## Rozwiązywanie problemów
- Pusty tekst w trybie Direct Input wyświetla podczas edycji `< empty splash element >`. Wpisz cokolwiek (nawet spację), aby usunąć ostrzeżenie.
- Jeśli plik tekstowy nie zawiera żadnych poprawnych linii, element wyświetli `ERROR: SPLASH FILE IS EMPTY`. Dodaj przynajmniej jedną niepustą linię i otwórz ekran ponownie.
- Błędy serializowanego JSON-a powodują powrót do zwykłego tekstu. Trzymaj się standardowej struktury JSON Mojanga albo przetestuj fragmenty komendą `/tellraw` w vanilla przed wklejeniem.
