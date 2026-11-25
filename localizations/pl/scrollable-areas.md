---
title: Obszary przewijania
description: >-
  Jak umieszczać elementy w obszarze przewijania, rozmieszczać je i zmieniać
  sposób przewijania obszaru.
sourceBlobSha: a424c5e8680ece5f25846de0399fc8e78f375e15
---
# Obszary przewijania

**Obszar przewijania** zawiera inne elementy i pozwala graczom przewijać ich zawartość. Świetnie sprawdza się w przypadku długich list przycisków, selektorów światów lub serwerów, prezentacji przedmiotów, paneli z wiadomościami i wszystkiego, co nie mieści się na jednym ekranie.

Cała zawartość obszaru przewija się razem z nim i jest przycinana przy jego krawędziach.

<img width="800" alt="Umieszczanie przycisków w obszarze przewijania i układanie ich jeden pod drugim" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_showcase.gif?raw=true">

> [!NOTE]
> W obszarze można umieszczać tylko elementy dodane do układu. Nie można w nim umieszczać [elementów Vanilla](/vanilla-elements), ponieważ należą one do samego menu.

# Dodawanie obszaru przewijania

1. Otwórz układ w edytorze układów.
2. Kliknij prawym przyciskiem myszy tło edytora i wybierz **Nowy element -> Obszar przewijania**.
3. Przeciągnij elementy do obszaru.

# Umieszczanie elementów w obszarze i wyjmowanie ich

- Przeciągnij element na obszar, aby go w nim umieścić. Obszar podświetli się, gdy zaakceptuje element. Element zostanie umieszczony w obszarze tylko wtedy, gdy choć jego część znajdzie się wewnątrz obszaru.
- Aby przeciągnąć jednocześnie kilka zaznaczonych elementów, przytrzymaj `Ctrl` (`Cmd` w systemie macOS) podczas rozpoczynania przeciągania.
- Gdy przeciągasz element blisko krawędzi obszaru, obszar zaczyna się przewijać, dzięki czemu możesz dotrzeć do każdej jego części. W edytorze możesz też przewijać go kółkiem myszy.
- Aby wyjąć element z obszaru, przeciągnij go poza obszar albo kliknij go prawym przyciskiem myszy i wybierz **Wyjmij z obszaru przewijania**. Element pozostanie w tym samym miejscu na ekranie.
- Obszary można umieszczać także wewnątrz innych obszarów.

## Warstwy

W widżecie [Warstwy](/layout-editor#scrollable-areas) elementy obszaru są wyświetlane pod nim. Przeciągaj tam warstwy, aby umieszczać je w obszarze lub wyjmować z niego, a także zmieniać ich kolejność. Przycisk zwijania warstwy obszaru ukrywa jego elementy na liście.

## Kopiowanie i usuwanie

- Skopiowanie obszaru kopiuje również wszystko, co się w nim znajduje.
- Jeśli usuwany obszar zawiera elementy, pojawi się pytanie, co z nimi zrobić: **Usuń elementy** usuwa je razem z obszarem, a **Zachowaj elementy** pozostawia je w tym samym miejscu na ekranie.

# Rozmieszczanie elementów

Kliknij obszar prawym przyciskiem myszy i otwórz **Rozmieszczanie**. Opcja **Tryb** określa sposób rozmieszczania elementów w obszarze:

- **Kotwice**: Rozmieszczasz elementy samodzielnie, tak jak w pozostałej części układu. Nowe obszary korzystają z tego trybu.
- **Stos**: Elementy układają się jeden za drugim.
- **Siatka**: Elementy układają się w komórkach o jednakowym rozmiarze.
- **Przepływ**: Elementy układają się obok siebie, a po zapełnieniu wiersza rozpoczyna się nowy.

<img width="800" alt="Obszary przewijania w trybach Stos, Siatka i Przepływ" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

## Tryb kotwic

Elementy w obszarze mają własne kotwice, które odnoszą się do zawartości obszaru, a nie do ekranu. Na przykład kotwica **Górny lewy róg** wskazuje górny lewy róg zawartości, a dolne kotwice są przypięte do końca zawartości. Więcej informacji o działaniu kotwic znajdziesz w sekcji [Pozycjonowanie elementów](/positioning-elements).

- Opcje **Rozciągnij w poziomie** i **Rozciągnij w pionie** dopasowują szerokość lub wysokość elementu do rozmiaru zawartości.
- Elementy można kotwiczyć wyłącznie do innych elementów w tym samym obszarze. Gdy przeniesiesz element do obszaru lub poza niego, elementy zakotwiczone po przeciwnych stronach krawędzi obszaru otrzymają kotwicę **Górny lewy róg** i pozostaną w tym samym miejscu.

### Rozmiar zawartości

W trybie Kotwice określasz rozmiar zawartości, a tym samym zakres przewijania obszaru.

Zaznacz obszar i przeciągnij uchwyt na końcu jego zawartości. Aby przeciągać dalej, przeciągnij uchwyt poza krawędź obszaru — obszar będzie się przy tym przewijać.

<img width="698" alt="Uchwyt zawartości zaznaczonego obszaru przewijania" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_content_handle.png?raw=true">

Możesz też kliknąć obszar prawym przyciskiem myszy i otworzyć **Rozmiar zawartości**:

- **Szerokość zawartości** i **Wysokość zawartości** pozwalają określić jej rozmiar liczbowo. Obsługują [zmienne](/placeholders). Jeśli użyjesz zmiennej, nie będzie można przeciągać uchwytu.
- **Dopasuj do zawartości** ustawia koniec zawartości dokładnie w miejscu, w którym kończy się ostatni element. Elementy zakotwiczone na środku lub na końcu zawartości przesuwają się razem z nią, więc nie są uwzględniane.

Zawartość nigdy nie jest mniejsza od obszaru i powiększa się tylko w kierunkach, w których obszar się przewija.

## Stos, Siatka i Przepływ

- Obszar sam rozmieszcza elementy i automatycznie dopasowuje do nich rozmiar zawartości.
- Przeciągnij element, aby zmienić jego kolejność. Linia wskaże jego nowe miejsce.
- Przełączenie z trybu Kotwice na jeden z tych trybów zachowuje kolejność elementów widoczną na ekranie. Po powrocie do trybu Kotwice każdy element pozostaje w swoim dotychczasowym miejscu.
- Elementy ukryte przez [warunki](/conditions) nie pozostawiają pustego miejsca.
- W tych trybach rozciąganie nie działa.
- Te tryby umożliwiają przewijanie tylko w jednym kierunku. Obszar ustawiony na **Oba kierunki** przewija się pionowo.

Otwórz **Rozmieszczanie**, aby dokładniej skonfigurować te tryby:

| Ustawienie | Działanie |
|---|---|
| **Wyrównanie** | Określa położenie elementów w poprzek kierunku, w którym są ułożone: **Początek**, **Środek**, **Koniec** lub **Wypełnij**. Przy opcji **Wypełnij** elementy zajmują całą dostępną szerokość (lub wysokość w obszarach przewijanych poziomo). Tryb Przepływ nie obsługuje opcji **Wypełnij**. |
| **Odstępy** | Odstęp między elementami. |
| **Margines wewnętrzny** | Odstęp między elementami a krawędziami zawartości. |
| **Elementów w wierszu** | Tylko dla trybu Siatka. Określa liczbę elementów w jednym wierszu. |
| **Dopasuj maksymalną liczbę** | Tylko dla trybu Siatka. Umieszcza w wierszu tyle elementów, ile się zmieści, zamiast stosować stałą liczbę. Liczbę tę określa **Minimalny rozmiar komórki**. |

# Przewijanie

Gracze przewijają obszar kółkiem myszy. Przytrzymaj `Shift`, aby przewijać w poziomie.

- **Kierunek przewijania** określa, czy obszar przewija się **Pionowo**, **Poziomo** czy w **Obu kierunkach**. W kierunkach, w których obszar się nie przewija, zawartość ma dokładnie taki sam rozmiar jak obszar.
- Elementy tekstowe w obszarze przewijają się w pierwszej kolejności. Gdy dotrą do końca, zaczyna przewijać się obszar.
- Gdy gracze przechodzą między przyciskami klawiszem `Tab`, obszar przewija się do wybranego przycisku.

Menu **Przewijanie**, **Automatyczne przewijanie** i **Paski przewijania** zawierają te same ustawienia co w przypadku elementów tekstowych. Opis wszystkich opcji znajdziesz w sekcji [Tekst w menu](/text-in-menus#scrolling-settings). Różnice:

- Przy opcji **Przyciąganie** zawartość można przyciągać **Do elementów**, tak aby element zawsze znajdował się na początku obszaru, albo **Do stron**.
- Przy włączonej opcji **Przeciągnij, aby przewinąć** przyciski i pozostałe elementy w obszarze nadal działają.
- Uchwyty przewijania są pikselowymi uchwytami, chyba że ustawisz własne **Tekstury uchwytów przewijania** lub **Kolor uchwytu przewijania [HEX]**.

# Tło

Obszary rysują panel za swoją zawartością. Otwórz **Tło**, aby je zmienić. Działa ono tak samo jak [tło elementów tekstowych](/text-in-menus#background): wyłącz je opcją **Pokaż tło**, użyj własnej tekstury z [dziewięciopodziałem](/nine-slicing-and-tiling) lub kafelkowaniem, a jego zasięg zmień za pomocą opcji **Margines wewnętrzny**.

# Przewijanie za pomocą akcji

Obszarami można też sterować i monitorować je z innych części FancyMenu:

- Akcja [Przewiń element](/action-scripts) przewija obszar do początku, końca, określonej pozycji lub jednego z zawartych w nim elementów.
- [Zmienne](/placeholders) **Pozycja przewijania elementu**, **Procent przewinięcia elementu** i **Rozmiar zawartości przewijanego elementu** informują o stopniu przewinięcia obszaru i rozmiarze jego zawartości.
- [Warunek](/conditions) **Czy element przewinięto do końca** sprawdza, czy obszar został przewinięty do końca.
- [Nasłuchiwacze](/listeners) **Po przewinięciu elementu**, **Po przewinięciu elementu do początku** i **Po przewinięciu elementu do końca** uruchamiają akcje podczas przewijania obszaru.

Wszystkie te funkcje wymagają [identyfikatora elementu](/element-identifiers) obszaru. Na przykład poniższy kod pokazuje, jak daleko przewinięto obszar — od 0 do 100:

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"3f2a9c1e-7b4d-4e8a-9c2f-1d5e6a7b8c9d-1763950000000","axis":"vertical"}}
```

# Warto wiedzieć

- Ukrycie obszaru ukrywa wszystko, co się w nim znajduje, a krycie obszaru dotyczy również jego zawartości.
- Obszarów nie można obracać ani przechylać, a paralaksa nie działa w przypadku obszarów ani umieszczonych w nich elementów.
- Elementy podpowiedzi w obszarze są przycinane przy jego krawędziach, chyba że podążają za kursorem.
