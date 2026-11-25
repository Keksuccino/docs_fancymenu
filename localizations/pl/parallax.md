---
title: Efekt paralaksy
description: >-
  Spraw, by tła i elementy poruszały się lekko za kursorem myszy, nadając menu
  głębi.
sourceBlobSha: f8481cfcc8d4f90bf2f261d436188763c8f23cba
---

# Efekt paralaksy

Efekt paralaksy sprawia, że tło menu lub element lekko się porusza, gdy poruszasz myszą. Ustaw mniejszy ruch dla odległych warstw, a większy dla tych bliższych, aby nadać menu głębi.

<img width="640" alt="Ekran tytułowy z krajobrazem o zmierzchu, podzielonym na cztery warstwy: gdy poruszasz myszą, drzewo na pierwszym planie porusza się najmocniej, wzgórza słabiej, a góry i niebo tylko lekko" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_scene.gif?raw=true">

Efekt działa na [elementach](/elements) oraz na [tłach menu](/menu-backgrounds) typu **Obraz** i **Wideo**.

# Elementy

<img width="640" alt="Ekran tytułowy z przyciskami ułożonymi w kolumnie po lewej stronie. Zaznaczanie pięciu przycisków w edytorze układu kliknięciem i Ctrl + kliknięciem, ustawianie dla wszystkich opcji Efekt paralaksy na Włączony i Intensywności paralaksy (X) na 1.0, a następnie zapisywanie i zamykanie edytora. Na ekranie tytułowym przyciski lekko poruszają się, gdy mysz przesuwa się w lewo i w prawo, natomiast logo i krajobraz pozostają nieruchome" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_element_settings.gif?raw=true">

1. Kliknij element prawym przyciskiem myszy w edytorze układu i przewiń w dół do opcji **Efekt paralaksy**.
2. Kliknij **Efekt paralaksy**, aby ustawić **Włączony**.
3. Kliknij **Intensywność paralaksy (X)** i **Intensywność paralaksy (Y)**, aby ustawić zakres ruchu.
4. Zapisz układ i zamknij edytor. Elementy poruszają się tylko poza edytorem.

Aby jednocześnie zastosować efekt do kilku elementów, najpierw je [zaznacz](/layout-editor#selecting) (`Ctrl` + kliknięcie dodaje element do zaznaczenia), a następnie kliknij jeden z nich prawym przyciskiem myszy.

| Ustawienie | Działanie |
|---|---|
| **Efekt paralaksy** | Włącza efekt. |
| **Intensywność paralaksy (X)** | Określa, jak daleko element porusza się w lewo i w prawo — od `0.0` (brak ruchu) do `1.0`. Nowe elementy mają wartość `0.5`. |
| **Intensywność paralaksy (Y)** | Określa to samo dla ruchu w górę i w dół. |
| **Odwróć kierunek ruchu paralaksy** | Element porusza się w tym samym kierunku co mysz. Gdy ta opcja jest wyłączona, porusza się w przeciwnym kierunku. |

Przy wartości `1.0`, gdy mysz znajduje się przy krawędzi ekranu, element porusza się na boki o maksymalnie 5% szerokości ekranu oraz w górę lub w dół o maksymalnie 5% jego wysokości. Na środku ekranu elementy pozostają w miejscu, w którym je umieszczono.

- Elementy [zakotwiczone](/positioning-elements) do elementu z włączonym efektem poruszają się razem z nim, a ich własny efekt dodatkowo zwiększa ruch.
- Opcja **Pozostaw na ekranie** nie utrzymuje elementów z włączonym efektem na ekranie, więc mogą przesuwać się poza jego krawędzie.
- Rozciągnięte elementy nie poruszają się w kierunku, w którym są rozciągnięte.
- [Przyciski i suwaki z gry](/vanilla-elements) poruszają się dopiero po ich przesunięciu. W przypadku punktu zakotwiczenia **Gra (oryginał)** pozostają tam, gdzie umieszcza je gra.
- Przyciski można klikać w miejscu, w którym są widoczne.
- Efekt paralaksy nie działa na [obszarach przewijania](/scrollable-areas), znajdujących się w nich elementach ani na elementach podpowiedzi.

# Tła menu

<img width="800" alt="Menu kontekstowe edytora układu z rozwiniętymi opcjami Tła menu i Obraz. Widoczne są pozycje Efekt paralaksy, Ustaw intensywność efektu paralaksy (X), Ustaw intensywność efektu paralaksy (Y) i Odwróć kierunek ruchu paralaksy" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_background_settings.png?raw=true">

1. Kliknij tło edytora prawym przyciskiem myszy i otwórz **Tła menu -> Obraz** (lub **Wideo**).
2. Kliknij **Efekt paralaksy**, aby ustawić **Włączony**.
3. Ustaw **Ustaw intensywność efektu paralaksy (X)** i **Ustaw intensywność efektu paralaksy (Y)**.

Tła reagują znacznie silniej niż elementy. Tło powiększa się w zależności od intensywności, dzięki czemu jego krawędzie nigdy nie są widoczne: przy wartości `1.0` ma dwukrotnie większy rozmiar niż ekran i przesuwa się na boki o maksymalnie połowę szerokości ekranu. Ustawiaj niskie wartości: nowe tła mają wartość `0.02`, a zakres od `0.01` do `0.1` sprawdza się dobrze.

- **Odwróć kierunek ruchu paralaksy** sprawia, że tło porusza się w tym samym kierunku co mysz.
- Opcje **Przesuwaj szerokie obrazy od lewej do prawej** i **Efekt paralaksy** nie mogą być włączone jednocześnie.
- Opcje **Powtarzaj teksturę** i **Zachowaj proporcje tła** działają razem z tym efektem.
- Tła poruszają się również w edytorze układu.

# Tworzenie sceny z głębią

Scena widoczna u góry tej strony składa się z nieba i trzech warstw na ekranie tytułowym:

1. Narysuj scenę na osobnych warstwach, od najdalszej do najbliższej, na przykład niebo, góry, wzgórza i pierwszy plan. Wszystkie warstwy poza niebem powinny być obrazami PNG z przezroczystymi fragmentami.
2. Ustaw niebo jako tło menu typu **Obraz** i włącz dla niego efekt paralaksy.
3. Dodaj każdą pozostałą warstwę jako [element obrazu](/elements#image), zaczynając od najdalszej, tak aby najbliższa znalazła się na wierzchu.
4. Nieco powiększ warstwy względem ekranu, aby ich krawędzie nie były widoczne podczas ruchu. Warstwa z wartością `1.0` wymaga dodatkowych 5% szerokości ekranu po lewej i prawej stronie oraz 5% wysokości ekranu u góry i na dole. Wyłącz opcję **Pozostaw na ekranie**, aby umieścić warstwy poza krawędziami ekranu.
5. Włącz efekt paralaksy dla każdej warstwy: ustaw niską intensywność dla odległych warstw, a wysoką dla bliższych.
6. Kliknij tło edytora prawym przyciskiem myszy i ustaw opcję **Niestandardowe elementy za elementami gry** na **Włączony**, aby warstwy pozostały za przyciskami i logo.

Oto wartości intensywności dla tej sceny:

| Warstwa | Intensywność (X) | Intensywność (Y) |
|---|---|---|
| Niebo (tło menu) | `0.02` | `0.01` |
| Góry | `0.35` | `0.2` |
| Wzgórza | `0.6` | `0.3` |
| Pierwszy plan | `1.0` | `0.5` |

> [!TIP]
> Ustaw intensywność Y na około połowę wartości X. Dzięki temu podłoże krajobrazu nie będzie tak mocno podskakiwać.

# Warto wiedzieć

- Wszystko porusza się skokowo, o całe piksele interfejsu, więc przy niskiej intensywności ruch odbywa się małymi krokami.
- Ustawienia intensywności obsługują [placeholdery](/placeholders): wskaż jeden z nich i kliknij **Ustaw jako zwykły tekst** w małym menu obok. Dzięki [zmiennej](/variables) możesz pozwolić graczom zmniejszać intensywność efektu we własnym menu ustawień.
