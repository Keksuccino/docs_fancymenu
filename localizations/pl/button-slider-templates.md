---
title: Szablony przycisków i suwaków
description: >-
  Jak używać szablonów przycisków/suwaków, aby zastosować określony wygląd
  przycisków/suwaków do WSZYSTKICH przycisków naraz.
---

# Używanie elementów przycisku jako szablonów dla przycisków i suwaków

Można użyć elementu przycisku jako szablonu dla innych przycisków, a nawet suwaków. Dzięki temu możesz zastosować określony wygląd przycisku/suwaka do WSZYSTKICH przycisków/suwaków w menu, a nawet do wszystkich menu naraz, gdy używasz układu uniwersalnego.

> [!IMPORTANT]
> Od FancyMenu 3.9.0 zaleca się używanie [Global Customizations](/global-customizations) zamiast Szablonów przycisków/suwaków, gdy tylko jest to możliwe. Mogą one globalnie zastępować domyślne tekstury przycisków i suwaków bez użycia paczki zasobów. Używaj globalnych dostosowań do szerokiego stylizowania interfejsu vanilla, a szablonów tylko wtedy, gdy potrzebujesz zachowania zależnego od układu.

# Ważne przed rozpoczęciem

Jeśli chcesz tylko zmienić teksturę pojedynczego przycisku lub suwaka, najprościej i zalecane jest po prostu **kliknąć prawym przyciskiem myszy** przycisk lub suwak (vanilla i własny) w edytorze. Dostępna jest opcja ustawienia **tekstur tła** (oraz tekstur uchwytu suwaka) dla przycisków i suwaków.

# Czym jest przycisk szablonu?

Przycisk szablonu to specjalny rodzaj własnego przycisku w FancyMenu, który pozwala kontrolować wygląd i zachowanie innych przycisków oraz suwaków. To jak stworzenie głównego projektu, którego będą przestrzegać wiele innych elementów.

Gdy tworzysz przycisk szablonu, możesz sprawić, że wiele przycisków lub suwaków będzie współdzielić te same:
- Rozmiar (szerokość i wysokość)
- Pozycję
- Widoczność
- Nieprzezroczystość (jak bardzo są przezroczyste)
- Etykiety tekstowe
- **Tekstury przycisków** (automatycznie współdzielone, gdy ustawione są własne tekstury)

To bardzo przydatne, gdy chcesz, aby Twoje menu wyglądało spójnie albo gdy musisz zaktualizować wiele przycisków naraz!

# Kto może używać szablonów?

Tylko **własne przyciski** mogą działać jako szablony. Jednak takie szablony można zastosować do:
- Przycisków vanilla (domyślnych przycisków Minecrafta)
- Własnych przycisków (przycisków tworzonych w FancyMenu)
- Suwaków vanilla (np. kontroli głośności)
- Własnych suwaków (suwaków tworzonych w FancyMenu)

# Jak utworzyć przycisk szablonu

1. Otwórz edytor FancyMenu dla ekranu, który chcesz dostosować
2. Dodaj nowy własny element przycisku do swojego układu
3. Kliknij prawym przyciskiem myszy swój nowy przycisk
4. Wybierz "Template Settings" z menu
5. Kliknij "Is Template: ON", aby włączyć tryb szablonu

Twój przycisk będzie teraz gotowy do działania jako szablon dla innych przycisków i suwaków!

# Opcje współdzielenia szablonu

Możesz wybrać, na które typy elementów szablon będzie wpływał:
- **Buttons** - Twój szablon będzie wpływał tylko na przyciski (zarówno vanilla, jak i własne)
- **Sliders** - Twój szablon będzie wpływał tylko na suwaki (zarówno vanilla, jak i własne)

Aby ustawić tę opcję:
1. Kliknij prawym przyciskiem myszy swój przycisk szablonu
2. Przejdź do "Template Settings"
3. Klikaj "Share With: [Current Option]", aby przełączać między opcjami

> **Ważne**: Możesz mieć dwa aktywne szablony jednocześnie - jeden dla przycisków ORAZ jeden dla suwaków. Oznacza to, że możesz tworzyć oddzielne projekty szablonów dla różnych typów elementów na tym samym ekranie!
{.is-warning}


# Co można szablonować

Możesz dokładnie kontrolować, które właściwości twój szablon będzie współdzielić z innymi elementami:

## Właściwości, które można włączać i wyłączać:

1. Kliknij prawym przyciskiem myszy swój przycisk szablonu
2. Przejdź do "Template Settings" 
3. Przełącz dowolne z tych opcji:
   - **Width** - Sprawia, że wszystkie objęte elementy mają taką samą szerokość jak twój szablon
   - **Height** - Sprawia, że wszystkie objęte elementy mają taką samą wysokość jak twój szablon
   - **X Position** - Ustawia wszystkie objęte elementy na tej samej współrzędnej X co twój szablon
   - **Y Position** - Ustawia wszystkie objęte elementy na tej samej współrzędnej Y co twój szablon
   - **Opacity** - Nadaje wszystkim objętym elementom taką samą przezroczystość jak twój szablon
   - **Visibility** - Kontroluje, czy objęte elementy są pokazywane, czy ukrywane
   - **Label** - Sprawia, że wszystkie objęte elementy używają tego samego tekstu co twój szablon

## Właściwości, które są zawsze współdzielone:

- **Tekstury przycisków** - Gdy ustawisz własne tekstury na swoim szablonie, zostaną one automatycznie zastosowane do wszystkich objętych elementów
  - W przeciwieństwie do innych właściwości, współdzielenia tekstur nie można wyłączyć
  - Tekstury są stosowane tylko wtedy, gdy na szablonie rzeczywiście ustawiono własne tekstury
  - Jeśli nie ustawiono własnych tekstur, zostaną użyte oryginalne tekstury elementu

# Dostosowywanie wyglądu szablonu

Twój przycisk szablonu można dostosować tak samo jak każdy inny przycisk:

1. Kliknij prawym przyciskiem myszy swój przycisk szablonu
2. Możesz ustawić:
   - Tekstury przycisku (stany normalny, po najechaniu i nieaktywny)
   - Etykiety (normalna i po najechaniu)
   - Dźwięki (po najechaniu i kliknięciu)
   - Podpowiedzi

Dla przycisków możesz ustawić własne tekstury dla różnych stanów:
- Tło normalne (gdy nie ma interakcji)
- Tło po najechaniu (gdy kursor znajduje się nad nim)
- Tło nieaktywne (gdy przycisk jest wyłączony)

Dla suwaków możesz także ustawić:
- Tekstury uchwytu suwaka
- Tekstury tła suwaka

# Ważne wskazówki

1. **Przyciski szablonów nie będą widoczne w grze** - są widoczne tylko w edytorze, więc umieść je tam, gdzie jest to wygodne.

2. **Możesz mieć dwa aktywne szablony jednocześnie** - jeden szablon dla przycisków i jeden dla suwaków mogą być aktywne w tym samym czasie.

3. **Aktywny jest tylko jeden szablon danego typu** - jeśli masz kilka szablonów przycisków, użyty dla przycisków będzie tylko ten najwyżej na liście elementów. To samo dotyczy szablonów suwaków.

4. **Zmiany w szablonie są aktualizowane natychmiast** - gdy edytujesz swój szablon, wszystkie objęte przyciski i suwaki zaktualizują się od razu.

5. **Używaj właściwego trybu współdzielenia** - pamiętaj, że tryb "Buttons" nie wpływa na suwaki, a tryb "Sliders" nie wpływa na przyciski.

6. **Stosuj właściwości selektywnie** - nie musisz stosować wszystkich właściwości. Na przykład możesz chcieć szablonować tylko tekstury i rozmiar, ale pozwolić elementom zachować ich oryginalne pozycje.

7. **Tekstury są zawsze współdzielone po ustawieniu** - w przeciwieństwie do innych właściwości, wszystkie własne tekstury zastosowane do szablonu będą automatycznie współdzielone z pasującymi elementami. Nie trzeba włączać ani wyłączać tej funkcji.

# Przykłady zastosowania

- Stwórz spójny styl dla wszystkich przycisków na ekranie
- Dopasuj wszystkie suwaki do własnego motywu za pomocą osobnego szablonu
- Stwórz "tryb ukryty", w którym możesz pokazywać/ukrywać wiele przycisków naraz
- Zmień rozmiar wielu przycisków jednym edytowaniem
- Nadaj wszystkim przyciskom w menu te same własne tekstury i dźwięki
