---
title: Edytor układu
description: >-
  Jak otworzyć edytor układu, wybierać, przesuwać i zmieniać rozmiar elementów,
  porządkować je za pomocą warstw i grup, zapisywać układ oraz korzystać ze
  wszystkich skrótów edytora.
sourceBlobSha: c247d44a67ac209f2a0b638cb4748b408c7e7b13
---

# Edytor układu

Edytor układu służy do tworzenia [układów](/home#your-first-layout): dodajesz w nim elementy, przesuwasz je, zmieniasz ich rozmiar i modyfikujesz otaczające je menu. Wyświetla menu tak, jak widzą je gracze, więc od razu widzisz, jak ono wygląda.

<img width="800" alt="Przesuwanie, poszerzanie i delikatne przesuwanie tytułu, a następnie zaznaczanie dwóch przycisków, kopiowanie ich i wklejanie, przeciąganie kopii w dół i cofanie tej czynności" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_basics.gif?raw=true">

# Otwieranie edytora

1. Otwórz menu, które chcesz zmienić, na przykład ekran tytułowy.
2. Kliknij **pasek menu -> Dostosowywanie -> Dostosowywanie bieżącego ekranu**, aby wyświetlił się stan **Włączone**.
3. Kliknij **pasek menu -> Dostosowywanie -> Układy -> Nowy -> Dla bieżącego ekranu**.

- Opcja **Dla wszystkich ekranów [uniwersalny]** tworzy [układ uniwersalny](/universal-layouts), który wyświetla się w każdym menu.
- Istniejące układy również są wymienione w sekcji **Układy**. Najedź kursorem na wybrany układ i kliknij **Edytuj układ**.
- W dowolnym menu skrót `Ctrl + Alt + L` otwiera ostatnio edytowany układ. Zobacz [skróty paska menu](/home#menu-bar-shortcuts).

# Przegląd edytora

<img width="800" alt="Edytor układu z zaznaczonym przyciskiem Dołącz do serwera, paskiem menu u góry i widżetem Warstwy po prawej stronie" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Kliknij prawym przyciskiem myszy tło, aby otworzyć ustawienia całego układu i dodać elementy za pomocą opcji **Nowy element**.
- Kliknij element prawym przyciskiem myszy, aby otworzyć jego ustawienia. Zobacz [Elementy](/elements#settings-of-all-elements).
- Sekcja **Warstwy** po prawej stronie zawiera listę wszystkich elementów układu. Zobacz [Warstwy i grupy](#layers-and-groups).
- Pasek menu u góry:

| Menu | Zawartość |
|---|---|
| **Układ** | **Nowy**, **Otwórz**, **Zapisz**, **Zapisz jako**, **Eksportuj układ dla AI**, **Właściwości układu** (to samo co menu kontekstowe tła), **Ustawienia** i **Zamknij edytor** |
| **Edycja** | **Cofnij**, **Ponów**, **Kopiuj**, **Wklej** i **Zaznacz wszystko** |
| **Element** | **Nowy** — dodaje elementy, a **Usunięte elementy waniliowe** przywraca [usunięte elementy waniliowe](/deleted-vanilla-elements) |
| **Okno** | **Widżety edytora**, [siatka](#grid-and-anchor-overlay), [nakładka punktów zakotwiczenia](#grid-and-anchor-overlay), **Elementy sterujące obrotem elementu** i **Elementy sterujące pochyleniem elementu** |

## Ustawienia układu

Menu kontekstowe tła zawiera wszystkie ustawienia samego układu, na przykład:

- [**Tła menu**](/menu-backgrounds) i [**Nakładki dekoracyjne**](/decoration-overlays)
- **Niestandardowy tytuł ekranu** — tekst u góry niektórych menu, na przykład „Opcje”. Można w nim używać [symboli zastępczych](/placeholders).
- **Dostosowywanie nagłówka/stopki** dla [przewijanych ekranów](/customizing-scrollable-screens)
- **Indeks układu [kolejność wielu układów]** i **Tryb losowy** dla [kilku układów w jednym menu](/randomize-layouts)
- **Wymagania ładowania [dla całego układu]** — zobacz [Wymagania](/conditions#layout-wide-requirements)
- **Edytuj skrypt akcji „Otwórz ekran”** i **Edytuj skrypt akcji „Zamknij ekran”** — zobacz [Skrypty akcji](/action-scripts)
- **Opcje układu uniwersalnego**, dostępne tylko w [układach uniwersalnych](/universal-layouts)

# Praca z elementami

## Zaznaczanie

- Kliknij element, aby go zaznaczyć. Kliknij tło, aby odznaczyć wszystko.
- Przeciągnij kursor po tle, aby zaznaczyć wszystkie elementy znajdujące się w prostokącie.
- Kliknięcie z wciśniętym `Ctrl` dodaje element do zaznaczenia lub usuwa z niego już zaznaczony element.
- `Ctrl + A` zaznacza wszystkie elementy.

Kliknięcia, zaznaczanie prostokątem i skrót `Ctrl + A` pomijają elementy [ukryte w sekcji Warstwy](#hiding-and-renaming).

## Przesuwanie

- Przeciągnij element, aby go przesunąć. Aby przesunąć kilka zaznaczonych elementów, przytrzymaj `Ctrl` podczas rozpoczynania przeciągania. Bez `Ctrl` kliknięcie zaznacza tylko kliknięty element.
- Klawisze strzałek przesuwają zaznaczone elementy o jeden piksel.
- Podczas przeciągania wyświetlają się punkty zakotwiczenia. Przytrzymaj element nad innym punktem zakotwiczenia lub elementem, aby go tam zakotwiczyć. Zobacz [Pozycjonowanie elementów](/positioning-elements).
- Upuść element na [obszarze przewijanym](/scrollable-areas), aby umieścić go w środku.

## Zmiana rozmiaru

Przeciągnij krawędź lub róg zaznaczonego elementu. Przytrzymaj `Shift`, aby zachować proporcje.

Zmiana rozmiaru działa tylko wtedy, gdy zaznaczony jest jeden element.

## Obracanie i pochylanie

Zaznaczone elementy obsługujące tę funkcję wyświetlają elementy sterujące do [obracania i pochylania](/rotating-elements). Przytrzymaj `Shift` podczas przeciągania, aby przyciągać do skoków: 45° przy obracaniu i 15° przy pochylaniu.

Opcje **Okno -> Elementy sterujące obrotem elementu** i **Elementy sterujące pochyleniem elementu** ukrywają te elementy sterujące.

## Kopiowanie, wklejanie i usuwanie

- `Ctrl + C` kopiuje zaznaczone elementy, a `Ctrl + V` je wkleja. Kopie pojawiają się na oryginałach i zostają zaznaczone, więc możesz od razu przeciągnąć je w inne miejsce.
- Możesz też wkleić elementy do innego układu, dopóki gra nie zostanie zamknięta.
- `Delete` usuwa zaznaczone elementy. Elementy waniliowe są tylko ukrywane — możesz je przywrócić za pomocą opcji **Element -> Usunięte elementy waniliowe**.
- Podczas usuwania obszaru przewijanego pojawi się pytanie, czy jego zawartość również usunąć, czy pozostawić w układzie.

## Cofanie i ponawianie

`Ctrl + Z` cofa ostatnią zmianę, a `Ctrl + Y` ponawia ją. Obie opcje są również dostępne w menu **Edycja**.

## Niewidoczne elementy

Gracze nie widzą elementów [Audio](/elements#audio), [Przesuwacz](/dragger), [Animator elementów](/element-animator), [Kontroler muzyki](/elements#music-controller) ani [Przewijacz](/elements#ticker). W edytorze są one widoczne jako kolorowe pola z nazwami, dzięki czemu można je znaleźć, przesuwać i zmieniać ich rozmiar.

- Opcja **Kolor w edytorze** w menu kontekstowym elementu zmienia kolor pola, na przykład pomaga odróżnić od siebie kilka Przewijaczy. Kolory zapisuje się jako `#RRGGBB` albo `#RRGGBBAA` z przezroczystością. Półprzezroczysty kolor, taki jak `#E30E2366`, pozwala zobaczyć, co znajduje się za polem.
- Nazwa wyświetlana w polu to nazwa warstwy elementu — zobacz [Ukrywanie i zmiana nazw](#hiding-and-renaming).

Gracze nigdy nie widzą pola, jego koloru ani nazwy.

# Warstwy i grupy

Sekcja **Warstwy** zawiera listę wszystkich elementów układu, zaczynając od elementu na samej górze. Element jest wyświetlany przed wszystkimi elementami znajdującymi się niżej na liście. Opcja **Okno -> Widżety edytora -> Warstwy** pokazuje lub ukrywa tę sekcję.

<img width="800" alt="Przeciąganie warstwy Tło aktualności poniżej warstwy Tekst aktualności, aby po odznaczeniu wyświetliły się informacje o aktualizacji, a następnie dodawanie grupy, umieszczanie w niej obu warstw, ukrywanie i pokazywanie grupy za pomocą ikony oka oraz zwijanie jej" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_layers.gif?raw=true">

## Zmiana kolejności

- Kliknij warstwę, aby zaznaczyć jej element, a następnie przeciągnij ją w górę lub w dół. Linia wskazuje miejsce, w którym warstwa zostanie umieszczona. Wszystkie zaznaczone warstwy przesuwają się razem.
- Możesz też kliknąć element lub jego warstwę prawym przyciskiem myszy, a następnie wybrać **Przesuń o jedną warstwę w górę** albo **Przesuń o jedną warstwę w dół**.

W edytorze zaznaczone elementy są zawsze wyświetlane przed pozostałymi. Odznacz je, aby zobaczyć rzeczywistą kolejność.

W niektórych wersjach Minecrafta elementy [Encja gracza](/elements#player-entity) i [Przedmiot](/elements#item) są wyświetlane przed wszystkim innym, niezależnie od położenia na warstwie. Zobacz [Znane problemy](/known-issues#1-player-entity--item-elements-are-always-in-front-of-everything).

## Elementy waniliowe

Wiersz **Elementy waniliowe** reprezentuje wszystkie elementy samego menu, na przykład jego przyciski. Nie można zmienić ich kolejności, ale przycisk po prawej stronie wiersza pozwala umieścić wszystkie własne elementy za nimi lub przed nimi. Działa tak samo jak opcja **Własne elementy za elementami waniliowymi** w menu kontekstowym tła.

## Ukrywanie i zmiana nazw

- Ikona oka przy warstwie ukrywa jej element w edytorze, dzięki czemu nie przeszkadza podczas pracy nad pozostałymi elementami. Kliknij ją ponownie, aby pokazać element.
- Ukrytych elementów nie można klikać, przesuwać, kopiować ani usuwać. Gracze nadal je widzą — są ukryte tylko w edytorze. Układ zapamiętuje, które elementy zostały ukryte.
- Kliknij warstwę prawym przyciskiem myszy i wybierz **Zmień nazwę warstwy**, aby nadać jej łatwiejszą do rozpoznania nazwę, na przykład `Panel aktualności`. To samo ustawienie co **Nazwa wyświetlana w edytorze** elementu. Gracze jej nie widzą.

## Grupy

Grupy pozwalają zebrać powiązane warstwy pod jedną nazwą, na przykład wszystkie elementy panelu aktualności. Służą tylko do uporządkowania listy — elementy wyświetlają się i działają tak jak wcześniej.

- Kliknij prawym przyciskiem myszy wewnątrz sekcji Warstwy i wybierz **Dodaj grupę**. Grupa pojawi się pod warstwami.
- Przeciągnij warstwy na grupę, aby do niej dołączyć. Przeciągnij je poza grupę, aby je z niej usunąć.
- Kliknij grupę, aby zaznaczyć wszystkie jej elementy. Przeciągnij ją, aby jednocześnie przesunąć wszystkie te elementy w górę lub w dół.
- Strzałka przy grupie zwija lub rozwija jej warstwy, a ikona oka ukrywa lub pokazuje wszystkie elementy grupy.
- Kliknij grupę prawym przyciskiem myszy, aby zmienić jej nazwę, przesunąć ją o jedną warstwę w górę lub w dół albo ją usunąć. Opcja **Usuń grupę** pozostawia jej elementy.

Opcje **Przesuń o jedną warstwę w górę** i **Przesuń o jedną warstwę w dół** nie wyprowadzają elementu z grupy. Aby go z niej usunąć, przeciągnij jego warstwę poza grupę.

Układ zapamiętuje grupy i ich stan zwinięcia.

## Obszary przewijane

Elementy w [obszarze przewijanym](/scrollable-areas) są wyświetlane pod warstwą tego obszaru i są wcięte.

- Przeciągnij warstwę na dolną połowę warstwy obszaru, aby umieścić w nim element. Przeciągnij ją poza obszar, między inne warstwy, aby go z niego usunąć. Element pozostanie w tym samym miejscu na ekranie.
- Strzałka przy warstwie obszaru zwija lub rozwija jego elementy.
- Elementy w obszarze nie należą do żadnej grupy. Przesuwają się razem z obszarem.

# Siatka i nakładka punktów zakotwiczenia

Menu **Okno** zawiera ustawienia narzędzi pomocniczych edytora:

- **Siatka** wyświetla linie siatki; skrót `Ctrl + G` włącza je i wyłącza. **Rozmiar siatki** ustawia odstęp między liniami.
- **Przyciąganie do siatki** powoduje, że przeciągany element przyciąga się do linii siatki, gdy siatka jest widoczna. **Siła przyciągania do siatki** określa, jak mocno element jest przyciągany.
- **Widoczność nakładki punktów zakotwiczenia** określa, kiedy są wyświetlane punkty zakotwiczenia:
  - **Pokaż podczas przeciągania elementu**: podczas przeciągania elementów.
  - **Zawsze widoczne**: przez cały czas.
  - **Pokaż po naciśnięciu klawisza (klawisz „O”)**: gdy przytrzymujesz `O`.
  - **Wyłączone**: nigdy.
- **Wykrywanie najechania na obszar zakotwiczenia** określa, czy przytrzymanie elementu nad punktem zakotwiczenia zmienia jego punkt zakotwiczenia. Opcja **Wykrywanie najechania na element zakotwiczenia** dodaje inne elementy do punktów zakotwiczenia. Działa tylko wtedy, gdy włączona jest również opcja **Wykrywanie najechania na obszar zakotwiczenia**.

# Zapisywanie i zamykanie

- `Ctrl + S` lub **Układ -> Zapisz** zapisuje układ. Przy pierwszym zapisie FancyMenu poprosi o nazwę pliku.
- **Układ -> Zapisz jako** zapisuje układ w nowym pliku.
- Gdy istnieją niezapisane zmiany, na pasku menu wyświetla się komunikat **\* Niezapisane zmiany! \***.
- Kliknięcie ikony X po prawej stronie paska menu lub wybranie **Układ -> Zamknij edytor** zamyka edytor. Jeśli istnieją niezapisane zmiany, pojawi się prośba o potwierdzenie.

# Skróty

W systemie macOS używaj `Cmd` zamiast `Ctrl`.

| Skrót | Działanie |
|---|---|
| `Ctrl + S` | Zapisz |
| `Ctrl + Z` | Cofnij |
| `Ctrl + Y` | Ponów |
| `Ctrl + C` | Kopiuj zaznaczone elementy |
| `Ctrl + V` | Wklej |
| `Ctrl + A` | Zaznacz wszystkie elementy |
| `Delete` | Usuń zaznaczone elementy |
| Klawisze strzałek | Przesuń zaznaczone elementy o jeden piksel |
| Kliknięcie z wciśniętym `Ctrl` | Dodaj element do zaznaczenia lub usuń go z zaznaczenia |
| Przeciąganie z wciśniętym `Ctrl` | Przesuń kilka zaznaczonych elementów |
| Zmiana rozmiaru z wciśniętym `Shift` | Zachowaj proporcje |
| Obracanie lub pochylanie z wciśniętym `Shift` | Przyciągaj do skoków |
| `Ctrl + G` | Włącz lub wyłącz siatkę |
| Przytrzymaj `O` | Pokaż punkty zakotwiczenia przy ustawieniu **Pokaż po naciśnięciu klawisza (klawisz „O”)** |

> [!TIP]
> Edytor tekstu ma własne skróty — zobacz [Tekst w menu](/text-in-menus#the-text-editor). Skróty dostępne w oknach takich jak [Skrypty akcji](/action-scripts#shortcuts) znajdziesz na stronach poświęconych tym funkcjom.
