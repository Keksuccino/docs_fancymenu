---
title: Szablony przycisków i suwaków
description: >-
  Jak używać szablonów przycisków/suwaków, aby zastosować określony wygląd
  przycisków/suwaków do WSZYSTKICH przycisków naraz.
---

# Używanie elementów przycisku jako szablonów dla przycisków i suwaków

Można użyć elementu przycisku jako szablonu dla innych przycisków, a nawet suwaków. Dzięki temu możesz zastosować określony wygląd przycisku/suwaka do WSZYSTKICH przycisków/suwaków w menu, a nawet do wszystkich menu naraz, gdy używasz układu uniwersalnego.

> [!IMPORTANT]
> W przypadku szerokiego stylizowania standardowych przycisków i suwaków Vanilla preferuj [Global Customizations](./global-customizations). Szablonów przycisków/suwaków używaj wtedy, gdy zachowanie musi być zależne od układu.

# Ważne przed rozpoczęciem

Dla jednego przycisku lub suwaka **kliknij go prawym przyciskiem myszy** w edytorze i edytuj bezpośrednio jego **Background Textures** lub tekstury uchwytu suwaka.

# Czym jest przycisk-szablon?

Przycisk-szablon to specjalny rodzaj niestandardowego przycisku w FancyMenu, który pozwala kontrolować wygląd i zachowanie innych przycisków oraz suwaków. To jak stworzenie wzorcowego projektu, według którego będą działać liczne inne elementy.

Gdy tworzysz przycisk-szablon, możesz sprawić, że wiele przycisków lub suwaków będzie współdzielić te same:
- Rozmiar (szerokość i wysokość)
- Położenie
- Widoczność
- Przezroczystość (jak bardzo są prześwitujące)
- Etykiety tekstowe
- **Tekstury przycisku** (automatycznie współdzielone, gdy ustawione są własne tekstury)

To bardzo przydatne, gdy chcesz zachować spójny wygląd menu albo gdy musisz zaktualizować wiele przycisków naraz!

# Kto może używać szablonów?

Tylko **niestandardowe przyciski** mogą działać jako szablony. Jednak takie szablony można stosować do:
- Przyciski Vanilla (domyślne przyciski Minecrafta)
- Niestandardowe przyciski (przyciski tworzone w FancyMenu)
- Suwaki Vanilla (np. sterowanie głośnością)
- Niestandardowe suwaki (suwaki tworzone w FancyMenu)

# Jak utworzyć przycisk-szablon

1. Otwórz edytor FancyMenu dla ekranu, który chcesz dostosować
2. Dodaj nowy niestandardowy element przycisku do swojego układu
3. Kliknij prawym przyciskiem myszy nowy przycisk
4. Z menu wybierz "Template Settings"
5. Kliknij "Is Template: ON", aby włączyć tryb szablonu

Twój przycisk będzie teraz gotowy do działania jako szablon dla innych przycisków i suwaków!

# Opcje współdzielenia szablonu

Możesz wybrać, na jakie typy elementów będzie oddziaływać twój szablon:
- **Buttons** - Twój szablon będzie wpływał tylko na przyciski (zarówno Vanilla, jak i niestandardowe)
- **Sliders** - Twój szablon będzie wpływał tylko na suwaki (zarówno Vanilla, jak i niestandardowe)

Aby ustawić tę opcję:
1. Kliknij prawym przyciskiem myszy swój przycisk-szablon
2. Przejdź do "Template Settings"
3. Klikaj "Share With: [Current Option]", aby przełączać się między opcjami

> [!WARNING]
> **Ważne**: Możesz mieć jednocześnie aktywne dwa szablony — jeden dla przycisków ORAZ jeden dla suwaków. Oznacza to, że możesz tworzyć osobne projekty szablonów dla różnych typów elementów na tym samym ekranie!


# Co można szablonować

Możesz dokładnie kontrolować, które właściwości twój szablon będzie współdzielić z innymi elementami:

## Właściwości, które można włączać i wyłączać:

1. Kliknij prawym przyciskiem myszy swój przycisk-szablon
2. Przejdź do "Template Settings" 
3. Przełącz dowolne z tych opcji:
   - **Width** - Ustawia wszystkim objętym elementom taką samą szerokość jak twój szablon
   - **Height** - Ustawia wszystkim objętym elementom taką samą wysokość jak twój szablon
   - **X Position** - Ustawia wszystkim objętym elementom tę samą współrzędną X co twój szablon
   - **Y Position** - Ustawia wszystkim objętym elementom tę samą współrzędną Y co twój szablon
   - **Opacity** - Nadaje wszystkim objętym elementom taką samą przezroczystość jak twój szablon
   - **Visibility** - Kontroluje, czy objęte elementy są pokazywane, czy ukrywane
   - **Label** - Sprawia, że wszystkie objęte elementy używają tego samego tekstu co twój szablon

## Właściwości, które są zawsze współdzielone:

- **Tekstury przycisku** - Gdy ustawisz własne tekstury na szablonie, zostaną one automatycznie zastosowane do wszystkich objętych elementów
  - W przeciwieństwie do innych właściwości, współdzielenia tekstur nie można wyłączyć
  - Tekstury są stosowane tylko wtedy, gdy na szablonie faktycznie ustawiono własne tekstury
  - Jeśli nie ustawiono własnych tekstur, użyte zostaną oryginalne tekstury elementu

# Dostosowywanie wyglądu szablonu

Twój przycisk-szablon można dostosować tak samo jak każdy inny przycisk:

1. Kliknij prawym przyciskiem myszy swój przycisk-szablon
2. Możesz ustawić:
   - Tekstury przycisku (stany normalny, po najechaniu i nieaktywny)
   - Etykiety (normalną i po najechaniu)
   - Dźwięki (po najechaniu i kliknięciu)
   - Podpowiedzi

Dla przycisków możesz ustawić własne tekstury dla różnych stanów:
- Tło normalne (gdy nie ma interakcji)
- Tło po najechaniu (gdy kursor myszy znajduje się nad nim)
- Tło nieaktywne (gdy przycisk jest wyłączony)

Dla suwaków możesz także ustawić:
- Tekstury uchwytu suwaka
- Tekstury tła suwaka

# Ważne wskazówki

1. **Przyciski-szablony nie będą widoczne w grze** - są widoczne tylko w edytorze, więc umieść je tam, gdzie jest to wygodne.

2. **Możesz mieć aktywne dwa szablony jednocześnie** - jeden szablon dla przycisków i jeden dla suwaków mogą być aktywne w tym samym czasie.

3. **Aktywny jest tylko jeden szablon danego typu** - jeśli masz wiele szablonów przycisków, tylko ten najwyżej na liście elementów będzie używany dla przycisków. To samo dotyczy szablonów suwaków.

4. **Zmiany w szablonie są aktualizowane natychmiast** - gdy edytujesz szablon, wszystkie objęte przyciski i suwaki od razu się zaktualizują.

5. **Używaj właściwego trybu współdzielenia** - pamiętaj, że tryb "Buttons" nie wpływa na suwaki, a tryb "Sliders" nie wpływa na przyciski.

6. **Stosuj właściwości wybiórczo** - nie musisz stosować wszystkich właściwości. Na przykład możesz chcieć szablonować tylko tekstury i rozmiar, ale pozostawić elementom ich oryginalne pozycje.

7. **Tekstury są zawsze współdzielone, gdy są ustawione** - w przeciwieństwie do innych właściwości, wszelkie własne tekstury zastosowane do szablonu będą automatycznie współdzielone z pasującymi elementami. Nie musisz włączać ani wyłączać tej funkcji.

# Przykładowe zastosowania

- Stworzenie spójnego stylu dla wszystkich przycisków na ekranie
- Dopasowanie wszystkich suwaków do własnego motywu za pomocą osobnego szablonu
- Utworzenie trybu "ukrycia", w którym można pokazać lub ukryć wiele przycisków naraz
- Zmiana rozmiaru wielu przycisków za pomocą jednej edycji
- Nadanie wszystkim przyciskom w menu tych samych własnych tekstur i dźwięków
