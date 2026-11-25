---
title: Tekst w menu
description: >-
  Jak wyświetlać tekst w menu za pomocą elementów Tekst i Podpowiedź oraz jak go
  stylizować i przewijać.
sourceBlobSha: 557734a5ca4e53d75045d7086642e9c561805b29
---
# Tekst w menu

FancyMenu ma dwa elementy służące do wyświetlania tekstu:

- **Tekst** wyświetla tekst bezpośrednio w menu — od pojedynczego wiersza po długie, przewijane strony, takie jak dzienniki zmian, regulaminy czy aktualności.
- **Podpowiedź** wyświetla pole tekstowe w określonym miejscu lub obok kursora, na przykład po najechaniu kursorem na przycisk.

Oba elementy obsługują [Markdown](/text-formatting) i [zmienne zastępcze](/placeholders), a także korzystają z tych samych ustawień wyglądu i stylu.

<img width="800" alt="Edytowanie elementu Tekst" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/text_editor_showcase.gif?raw=true">

> [!TIP]
> Ta strona opisuje elementy i ich ustawienia. Informacje o wszystkim, co można umieścić w tekście, na przykład nagłówkach, listach, linkach i kolorach, znajdziesz na stronie [Formatowanie tekstu](/text-formatting).

# Dodawanie tekstu

1. Otwórz układ w edytorze układów.
2. Kliknij prawym przyciskiem myszy tło edytora i wybierz **Nowy element -> Tekst**.
3. Kliknij prawym przyciskiem myszy nowy element i wybierz **Zawartość tekstu**.
4. Wpisz tekst i kliknij **Gotowe**.

# Zawartość tekstu

## Tryb źródła

Kliknij element prawym przyciskiem myszy i ustaw **Tryb źródła**:

- **Bezpośredni**: wpisujesz tekst samodzielnie w edytorze tekstu.
- **Zasób**: tekst pochodzi z pliku tekstowego. Kliknij **Źródło tekstu**, aby wybrać plik lokalny z folderu `<game-directory>/config/fancymenu/assets/`, adres URL lub plik z paczki zasobów. Zobacz [Zasoby](/resources).

Źródła internetowe świetnie sprawdzają się w przypadku takich treści jak dzienniki zmian czy aktualności, które mają być zawsze aktualne bez konieczności aktualizowania paczki modów.

FancyMenu zapamiętuje tekst z plików i źródeł internetowych do zamknięcia gry. Aby wczytać go ponownie, przeładuj FancyMenu, wybierając **pasek menu -> Dostosowywanie -> Przeładuj FancyMenu**.

## Tekst dynamiczny

Tekst może wyświetlać na bieżąco aktualizowane wartości za pomocą [zmiennych zastępczych](/placeholders), na przykład `Witaj, {"placeholder":"playername"}!`. Może też wyświetlać wartości [zmiennych](/variables). Tekst aktualizuje się automatycznie po zmianie tych wartości.

## Edytor tekstu

Kliknięcie **Zawartość tekstu** otwiera edytor tekstu. Kliknij **Zmienne zastępcze** w jego prawym górnym rogu, aby przeglądać dostępne zmienne i dodawać je do tekstu.

### Skróty formatowania

Edytor tekstu elementów Tekst i Podpowiedź udostępnia skróty do najczęściej używanych opcji formatowania. W systemie macOS używaj klawisza `Cmd` zamiast `Ctrl`.

| Skrót | Działanie |
|---|---|
| `Ctrl + B` | Pogrubienie |
| `Ctrl + I` | Kursywa |
| `Ctrl + U` | Podkreślenie |
| `Ctrl + L` | Wyrównanie do lewej |
| `Ctrl + E` | Wyrównanie do środka |
| `Ctrl + R` | Wyrównanie do prawej |

- Najpierw zaznacz tekst, który chcesz sformatować. Naciśnij ten sam skrót ponownie, aby usunąć formatowanie.
- Jeśli nic nie jest zaznaczone, skrót dodaje znaki formatowania i umieszcza między nimi kursor, dzięki czemu możesz od razu pisać dalej.
- Skróty wyrównania działają na zaznaczonych wierszach lub wierszu, w którym znajduje się kursor. Użycie `Ctrl + E` lub `Ctrl + R` w wierszach już wyrównanych w ten sposób ponownie wyrównuje je do lewej.
- Kliknij edytor prawym przyciskiem myszy i otwórz menu **Formatowanie**, aby zobaczyć wszystkie te opcje.

### Inne skróty

Ten sam edytor tekstu otwiera się w przypadku większości tekstów w FancyMenu, takich jak wartości akcji i wiele ustawień elementów. Te skróty działają w każdym z nich. W systemie macOS używaj klawisza `Cmd` zamiast `Ctrl`.

| Skrót | Działanie |
|---|---|
| `Ctrl + C` | Kopiowanie zaznaczonego tekstu |
| `Ctrl + X` | Wycinanie zaznaczonego tekstu |
| `Ctrl + V` | Wklejanie |
| `Ctrl + A` | Zaznaczanie całego tekstu |
| `Ctrl + Z` | Cofanie |
| `Ctrl + Y` | Ponawianie |
| `Ctrl + D` | Powielanie wiersza, w którym znajduje się kursor |
| `Alt + Strzałka w górę` / `Alt + Strzałka w dół` | Przenoszenie wiersza, w którym znajduje się kursor, w górę lub w dół |
| `Shift + klawisze strzałek` | Zaznaczanie tekstu |
| `Ctrl + Home` / `Ctrl + End` | Przejście na początek lub koniec tekstu |
| `Ctrl + G` | Przejście do wiersza: wpisz jego numer i naciśnij `Enter` |
| `Ctrl + S` | To samo co **Gotowe** |

Skróty edytora układów znajdziesz na stronie [Edytor układów](/layout-editor#shortcuts).

# Wygląd i style

Kliknij element prawym przyciskiem myszy i otwórz menu **Markdown**, aby zmienić wygląd tekstu.

## Wyglądy

**Wygląd** ustawia wszystkie opcje stylu tekstu jednocześnie:

- **Pikselowy**: grafika pikselowa zaprojektowana z myślą o czcionce Minecrafta, w ciepłych kolorach, ze złotymi detalami i odręcznie rysowanymi oznaczeniami.
- **Klasyczny**: klasyczny wygląd FancyMenu — biały tekst, szare pola i szare linie.
- **Neutralny**: prosty wygląd w kolorach bieżącego motywu interfejsu FancyMenu. Kolory są zapisywane razem z elementem, więc nie zmienią się po późniejszej zmianie motywu.

<img width="800" alt="Trzy wyglądy Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_looks.png?raw=true">

Nowe elementy domyślnie korzystają z wyglądu Pikselowego. Elementy ze starszych układów zachowują używany wcześniej wygląd Klasyczny.

> [!NOTE]
> Wybór wyglądu zastępuje wprowadzone przez Ciebie zmiany stylu. Zmieniłeś zdanie? Cofnij tę zmianę za pomocą `Ctrl + Z`.

## Opcje stylu

Po wybraniu wyglądu możesz nadal dostosować każdy jego element. Menu **Markdown** zawiera opcje dla **Tekstu**, **Nagłówków**, **List**, **Linków**, **Kodu**, **Cytatów**, **Wyróżnień**, **Tabel**, **Obrazów** i **Separatorów**. Najedź kursorem na opcję, aby zobaczyć jej działanie.

W sekcji **Markdown -> Tekst** znajdziesz podstawowe ustawienia, takie jak kolor i cień tekstu, odstępy między wierszami oraz odstęp między tekstem a krawędziami elementu.

## Wyłączanie Markdown

Jeśli nie potrzebujesz Markdown, wyłącz opcję **Markdown -> Parser Markdown**. Tekst będzie wtedy wyświetlany dokładnie tak, jak został wpisany. Przy bardzo długich tekstach może to również nieco przyspieszyć działanie.

## Inne ustawienia tekstu

Kliknij element prawym przyciskiem myszy, aby znaleźć również te opcje:

- **Skala tekstu** powiększa lub pomniejsza tekst.
- **Tryb wielkości liter** wyświetla tekst w zwykłej postaci, wyłącznie wielkimi lub wyłącznie małymi literami.
- **Automatyczne zawijanie wierszy** zawija wiersze, które są zbyt długie dla elementu. Gdy ta opcja jest wyłączona, długie wiersze nie są zawijane.
- **Usuń znaczniki nowego wiersza HTML** usuwa znaczniki nowego wiersza HTML (`<br>`) z tekstu. Przydaje się to w przypadku tekstów pochodzących ze stron internetowych.

# Tło

Elementy Tekst mogą wyświetlać panel za tekstem. Otwórz menu **Tło** w menu kontekstowym elementu:

- **Pokaż tło** włącza lub wyłącza panel. W nowych elementach Tekst ta opcja jest włączona.
- Domyślnie używany jest wbudowany ciemny panel. Możesz zamiast niego użyć własnej tekstury, korzystając z [dzielenia na dziewięć części](/nine-slicing-and-tiling) i kafelkowania, aby zachować kształt jego krawędzi.
- **Margines wewnętrzny** określa, jak daleko tło sięga poza tekst.
- **Tło pod paskami przewijania** pozwala tłu zakrywać również paski przewijania. Gdy ta opcja jest wyłączona, paski znajdują się tuż obok tła.

Podpowiedzi mają osobne menu **Tło**, w którym można ustawić teksturę i jej podział na dziewięć części.

# Przewijanie

Element Tekst przewija się, gdy jego treść się w nim nie mieści. Do przewijania używaj kółka myszy. Przytrzymaj `Shift`, aby przewijać w poziomie.

Opcja **Kierunek przewijania** określa, czy tekst przewija się **Pionowo**, **Poziomo** czy w **Obie strony**. W kierunkach, w których przewijanie jest wyłączone, niemieszcząca się treść zostaje obcięta.

## Ustawienia przewijania

Otwórz menu **Przewijanie** w menu kontekstowym elementu:

| Ustawienie | Działanie |
|---|---|
| **Pozwól graczom przewijać** | Określa, czy gracze mogą samodzielnie przewijać tekst. Gdy ta opcja jest wyłączona, tekst przewija się tylko automatycznie lub za pomocą akcji. |
| **Szybkość przewijania** | Określa, jak daleko tekst przewija się po jednym obrocie kółka myszy. |
| **Płynne przewijanie** | Sprawia, że tekst przesuwa się płynnie zamiast przeskakiwać. |
| **Przewijanie przeciąganiem** | Pozwala graczom chwycić tekst myszą i przeciągać go, tak jak na ekranie dotykowym. |
| **Przewijanie klawiaturą** | Gdy kursor znajduje się nad tekstem, klawisze `Page Up` i `Page Down` przewijają o stronę, a `Home` i `End` przenoszą odpowiednio na początek i koniec. |
| **Przyciąganie** | Określa miejsce, w którym tekst się zatrzymuje: w dowolnym miejscu (**Wyłączone**), z całym wierszem u góry (**Do wierszy**), z nagłówkiem u góry (**Do nagłówków**) lub z przeskokiem o całą stronę (**Do stron**). |
| **Pozycja początkowa** | Określa, czy tekst zaczyna się od **Początku**, czy od **Końca**. Koniec przydaje się w przypadku dzienników, w których najnowsze wpisy znajdują się na dole. |
| **Resetuj po otwarciu ekranu** | Za każdym razem, gdy ekran zostanie otwarty, tekst wraca na początek. Gdy ta opcja jest wyłączona, tekst zapamiętuje pozycję przewinięcia do zamknięcia gry. |

## Automatyczne przewijanie

Otwórz menu **Automatyczne przewijanie**, aby tekst przewijał się powoli samoczynnie — jak napisy końcowe lub pasek wiadomości:

- **Przewijaj automatycznie** włącza tę funkcję.
- **Szybkość [piksele na sekundę]** określa szybkość przewijania.
- **Zacznij od początku po dotarciu do końca** ponownie rozpoczyna przewijanie od góry po osiągnięciu końca.
- **Wstrzymaj po najechaniu kursorem** zatrzymuje przewijanie, gdy kursor znajduje się nad tekstem, aby gracze mogli spokojnie czytać.

## Paski przewijania

Otwórz menu **Paski przewijania**, aby zmienić ich ustawienia:

- **Pokaż** określa, kiedy paski są widoczne: **Zawsze**, tylko **Podczas przewijania** lub **Nigdy**. Przy opcji **Nigdy** nadal można przewijać tekst kółkiem myszy.
- **Grubość** określa grubość pasków.
- **Pionowy pasek po lewej** i **Poziomy pasek u góry** przenoszą paski na przeciwną stronę.
- **Styl uchwytów pasków przewijania** wybiera wygląd uchwytów: **Pasek motywu** (w kolorach motywu interfejsu FancyMenu) lub **Pikselowy uchwyt** (grafika pikselowa, która świetnie pasuje do wyglądu Pikselowego).
- **Tekstury uchwytów pasków przewijania** i **Kolor uchwytów pasków przewijania [HEX]** pozwalają zastąpić uchwyty własnymi teksturami lub kolorami.
- **Tła pasków przewijania** dodają tekstury za uchwytami, wzdłuż ich toru ruchu.

## Przewijanie za pomocą akcji

Możesz również sterować przewijaniem i sprawdzać jego stan w innych częściach FancyMenu:

- Akcja **Przewiń element** [akcja](/action-scripts) przewija element Tekst do początku, końca, określonej pozycji, numeru wiersza lub pierwszego wiersza zawierającego dany tekst.
- [Zmienne zastępcze](/placeholders) **Pozycja przewijania elementu**, **Procent przewinięcia elementu** i **Rozmiar przewijanej treści elementu** informują, jak daleko przewinięto tekst i jak duża jest jego zawartość.
- [Warunek](/conditions) **Czy element przewinięto do końca** sprawdza, czy tekst przewinięto do końca. Można go użyć na przykład po to, aby przycisk „Akceptuj” włączył się dopiero po przeczytaniu regulaminu.
- [Nasłuchiwacze](/listeners) **Podczas przewijania elementu**, **Po przewinięciu elementu do początku** i **Po przewinięciu elementu do końca** uruchamiają akcje podczas przewijania tekstu.

Każda z tych funkcji wymaga [identyfikatora elementu](/element-identifiers) elementu Tekst.

# Klikanie przez elementy tekstowe

Elementy Tekst reagują na mysz, dzięki czemu działają w nich linki i paski przewijania. Oznacza to również, że przechwytują kliknięcia — przyciski znajdujące się za elementem Tekst lub przed nim mogą ich nie otrzymać.

Jeśli to problem, kliknij element Tekst prawym przyciskiem myszy i wyłącz opcję **Interaktywny**. Tekstu nie będzie wtedy można przewijać ani klikać znajdujących się w nim linków.

# Podpowiedzi

Elementy Podpowiedź działają podobnie jak elementy Tekst, ale nie obsługują przewijania:

- Ich ustawienia tekstu, wyglądu i stylu są takie same jak w przypadku elementów Tekst.
- Opcja **Podążaj za kursorem** sprawia, że podpowiedź porusza się razem z kursorem.
- Użyj [warunków](/conditions), aby określić, kiedy podpowiedź ma się pojawiać. Możesz na przykład użyć warunku [**Czy kursor znajduje się nad elementem**](/conditions#is-element-hovered), aby wyświetlać ją po najechaniu kursorem na przycisk.
