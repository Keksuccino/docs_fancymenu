---
title: Dziewięciopodział i kafelkowanie
description: >-
  Dopasuj tekstury z ramkami do dowolnego rozmiaru bez ich zniekształcania albo
  powtarzaj wzór zamiast go rozciągać.
sourceBlobSha: 0dca8e7070606cdafccd9edc23a77535048d4ba3
---

# Dziewięciopodział i kafelkowanie

Własne tekstury są rozciągane do rozmiaru elementu. W przypadku zdjęć to nie problem, ale ramki, panele i przyciski z obramowaniem wyglądają na zniekształcone, gdy stają się szersze lub wyższe. Rozwiązaniem są dwa ustawienia:

- Dziewięciopodział zachowuje kształt narożników i krawędzi tekstury, a wypełnia tylko środek.
- Kafelkowanie powtarza teksturę zamiast ją rozciągać, dzięki czemu wzór zachowuje swój rozmiar.

<img width="800" alt="Kwadratowa tekstura panelu podzielona czterema liniami na dziewięć części oraz ta sama tekstura jako szeroki panel, którego narożniki i krawędzie zachowują swój kształt" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png">

# Jak działa dziewięciopodział

Cztery linie dzielą teksturę na dziewięć części. Cztery narożniki zawsze zachowują ten sam rozmiar, krawędzie tylko się wydłużają, a środek wypełnia pozostałą przestrzeń.

1. Ustaw teksturę.
2. Włącz dla niej ustawienie dziewięciopodziału. Jego nazwa znajduje się w sekcji [Gdzie to działa](#where-it-works).
3. Ustaw rozmiary obramowania tak, aby odpowiadały grubości ramki tekstury, wyrażonej w pikselach tekstury. Jeśli ramka ma 4 piksele grubości, wpisz `4`.

Warto wiedzieć:

- Obramowania są wyświetlane na ekranie w takim samym rozmiarze, jak w teksturze. Dlatego tekstura z obramowaniem o szerokości 40 pikseli będzie wyglądać masywnie na małym przycisku. Rozmiar tekstury powinien być zbliżony do rozmiaru elementu.
- Większość tekstur ma jeden rozmiar dla lewego i prawego obramowania (obramowania X) oraz jeden dla górnego i dolnego (obramowania Y). Paski postępu, podpowiedzi i ustawienia globalne pozwalają określić rozmiar każdej krawędzi osobno.
- Zbyt duże obramowania są automatycznie zmniejszane, aby zmieściły się w teksturze.

# Gdzie to działa

| Tekstura | Dziewięciopodział | Kafelkowanie |
|---|---|---|
| Tekstury [przycisków](/elements#button), w sekcji **Tekstury przycisków** | **Niestandardowe tło — dziewięciopodział** | - |
| Tekstury [suwaków](/elements#slider), w sekcji **Tekstury suwaków** | **Niestandardowe tło — dziewięciopodział** i **Niestandardowy uchwyt — dziewięciopodział** | - |
| Elementy [obrazów](/elements#image) | **Tekstura — dziewięciopodział** | **Powtarzaj teksturę** |
| **Tło** elementów [tekstu](/text-in-menus#background) i [obszarów przewijania](/scrollable-areas#background) | **Niestandardowe tło — dziewięciopodział** | **Kafelkuj teksturę** |
| **Tła pasków przewijania** elementów tekstowych i obszarów przewijania | zawsze włączony | - |
| **Tło** elementów [podpowiedzi](/elements#tooltip) | zawsze włączony; rozmiary w sekcji **Ustawienia dziewięciopodziału** | - |
| Tekstury [pasków postępu](/elements#progress-bar) | **Tekstura paska — dziewięciopodział** i **Tekstura tła — dziewięciopodział** | - |
| [Globalne tekstury przycisków i suwaków](/global-customizations#buttons-and-sliders) | **Tła przycisków — dziewięciopodział**, **Tło suwaka — dziewięciopodział** i **Uchwyt suwaka — dziewięciopodział** | - |
| [Tła menu z obrazem](/menu-backgrounds#image) | - | **Powtarzaj teksturę** |
| Nagłówek i stopka [przewijanych ekranów](/customizing-scrollable-screens) | - | **Powtarzaj teksturę nagłówka** i **Powtarzaj teksturę stopki** |

## Tła elementów tekstowych i obszarów przewijania

Otwórz pozycję **Tło** w menu dostępnym po kliknięciu prawym przyciskiem myszy elementu tekstowego lub obszaru przewijania:

- **Niestandardowa tekstura tła** zastępuje wbudowany ciemny panel własną teksturą. Zresetuj ją, aby przywrócić panel.
- **Niestandardowe tło — dziewięciopodział** jest domyślnie włączone. Ustaw obramowania za pomocą opcji **Obramowania X tła — dziewięciopodział (lewe i prawe)** oraz **Obramowania Y tła — dziewięciopodział (górne i dolne)**.
- **Kafelkuj teksturę** powtarza teksturę zamiast ją rozciągać. W połączeniu z dziewięciopodziałem powtarzane są krawędzie i środek, a narożniki pozostają bez zmian.
- **Pokaż tło** wyłącza całe tło.

## Tła pasków przewijania

Otwórz sekcję **Paski przewijania -> Tła pasków przewijania** elementu tekstowego lub obszaru przewijania. Opcje **Tekstura pionowego paska** i **Tekstura poziomego paska** wyświetlają teksturę wzdłuż toru, po którym porusza się uchwyt przewijania. Tekstury są zawsze dzielone na dziewięć części, dzięki czemu ich końce zachowują kształt niezależnie od długości paska. Ustaw obramowania za pomocą dwóch znajdujących się poniżej opcji.

# Jak działa kafelkowanie

Kafelkowanie umieszcza obok siebie tyle kopii tekstury o jej oryginalnym rozmiarze, ile się zmieści. Używaj tekstury bez widocznych łączeń, w której lewa krawędź pasuje do prawej, a górna do dolnej. W przeciwnym razie między kafelkami będą widoczne linie.

W elementach obrazów opcje **Powtarzaj teksturę** i **Tekstura — dziewięciopodział** nie działają jednocześnie. Jeśli obie są włączone, obraz będzie powtarzany.
