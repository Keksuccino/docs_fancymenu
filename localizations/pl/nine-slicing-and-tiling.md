---
title: Nine-Slicing i kafelkowanie
description: Jak używać nine-slicing i kafelkowania w FancyMenu.
---

# Nine-Slicing i kafelkowanie

Podczas projektowania fajnych menu w Minecraftcie za pomocą FancyMenu możesz chcieć używać obrazów, które trzeba poprawnie skalować albo powtarzać w wzory. Ten poradnik wyjaśnia, jak korzystać z **Nine-Slicing** i **kafelkowania** (zwanego też powtarzaniem tekstur), aby Twoje menu wyglądało świetnie!

# Czym jest Nine-Slicing?

Nine-slicing to technika, która pozwala rozciągnąć obraz do dowolnego rozmiaru bez sprawiania, że wygląda dziwnie. Działa to poprzez podzielenie obrazu na dziewięć części (jak plansza do kółko i krzyżyk). Narożniki zachowują ten sam rozmiar, krawędzie rozciągają się w jednym kierunku, a środek rozciąga się w obu kierunkach.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Przykład Nine-Slice" style="max-width: 500px; height: auto;" />

## Gdzie mogę używać Nine-Slicing?

W FancyMenu Nine-Slicing jest dostępne dla:
- **Elementów przycisków** (zarówno własnych przycisków, jak i podczas edycji przycisków Vanilla)
- **Tekstur paska postępu** (tekstury paska i tła)

## Jak używać Nine-Slicing z przyciskami

1. **Utwórz lub wybierz element przycisku** w edytorze układu.
2. Kliknij przycisk prawym przyciskiem myszy i znajdź opcję „Button Textures”.
3. Ustaw tekstury tła przycisku (stany normalny, po najechaniu, nieaktywny).
4. Włącz opcję „Nine-Slice Custom Background”.
5. Ustaw **Nine-Slice Background X-Borders** (rozmiar lewego i prawego brzegu).
6. Ustaw **Nine-Slice Background Y-Borders** (rozmiar górnego i dolnego brzegu).

### Wskazówki dotyczące Nine-Slicing dla przycisków

- Użyj obrazu z wyraźnymi krawędziami i narożnikami.
- Wartości brzegów (X i Y) mówią FancyMenu, ile pikseli od każdej krawędzi ma być traktowane jako brzeg.
- Typowa wartość to na przykład 5 pikseli zarówno dla brzegów X, jak i Y.
- Narożniki zawsze zachowają swój rozmiar, a środkowe części będą się rozciągać, aby wypełnić przycisk.

# Czym jest kafelkowanie?

Kafelkowanie (zwana też powtarzaniem tekstur) pozwala wypełnić duży obszar małym obrazem, powtarzając go jak płytki na podłodze. To idealne rozwiązanie dla teł lub dużych obrazów, gdy chcesz, aby wzór się powtarzał.

## Gdzie mogę używać kafelkowania?

W FancyMenu kafelkowanie jest dostępne dla:
- **Elementów obrazów**
- **Tł wy menu obrazowych**

## Jak używać kafelkowania z elementami obrazu

1. **Utwórz lub wybierz element obrazu** w edytorze układu.
2. Kliknij obraz prawym przyciskiem myszy i znajdź „Image Source”, aby ustawić teksturę.
3. Znajdź i włącz opcję **„Repeat Texture”**.
4. Zmień rozmiar elementu obrazu, aby zobaczyć, jak tekstura powtarza się i wypełnia przestrzeń.

## Jak używać kafelkowania z tłami menu

1. Otwórz **Menu Backgrounds** z menu kontekstowego tła w edytorze układu.
2. Wybierz typ tła **Image**.
3. Wybierz obraz tła.
4. Włącz opcję **„Repeat Texture”**.
5. Tło będzie teraz powtarzać teksturę, aby wypełnić cały ekran.

# Tworzenie dobrych tekstur do Nine-Slicing i kafelkowania

## Dla Nine-Slicing:
- Twórz tekstury z wyraźnymi krawędziami i narożnikami.
- Upewnij się, że brzegi są czytelne i mają stałą szerokość.
- Testuj różne rozmiary brzegów, aby znaleźć najlepsze rozwiązanie.
- Przyciski zwykle dobrze działają z brzegami o szerokości 3–5 pikseli.

## Dla kafelkowania:
- Twórz bezszwowe tekstury, które mogą łączyć się same ze sobą ze wszystkich stron.
- Utrzymuj proste wzory, aby uniknąć wizualnego chaosu.
- Przetestuj teksturę, najpierw powtarzając ją na małym obszarze.

# Przykłady

## Przykład przycisku z Nine-Slicing
Prosty przycisk może zaczynać jako obraz 30x30 z 5-pikselowymi brzegami ze wszystkich stron. Gdy zwiększysz rozmiar przycisku, narożniki pozostaną 5x5 pikseli, a krawędzie i środek rozciągną się tak, aby dopasować się do rozmiaru przycisku.

## Przykład kafelkowanego tła
Mały kafelek 64x64 z subtelnym wzorem może być powtarzany, aby wypełnić całe tło menu, niezależnie od rozmiaru ekranu.

# Częste problemy i rozwiązania

## Mój przycisk z nine-slicing wygląda na rozciągnięty lub zniekształcony:
- Wartości brzegów mogą być za małe albo za duże
- Spróbuj zmienić wartości brzegów tak, aby pasowały do Twojej tekstury

## Moje kafelkowane tło ma widoczne łączenia:
- Twoja tekstura nie jest bezszwowa
- Spróbuj edytować obraz tak, aby krawędzie idealnie do siebie pasowały

## Moje tekstury wyglądają na rozmyte po skalowaniu:
- Użyj tekstur o wyższej rozdzielczości
- Utrzymuj projekty proste i z wyraźnymi liniami

# Pamiętaj

- **Nine-Slicing** jest idealne dla elementów UI, które muszą zmieniać rozmiar, ale zachować swój wygląd (takich jak przyciski).
- **Kafelkowanie** świetnie sprawdza się do wypełniania dużych obszarów wzorem (takich jak tła).
- Obie funkcje pomagają sprawić, że interfejs wygląda dobrze w każdej rozdzielczości i na każdym rozmiarze ekranu!

Teraz stwórz niesamowite menu Minecrafta z idealnie rozciągniętymi przyciskami i pięknymi kafelkowanymi tłami!
