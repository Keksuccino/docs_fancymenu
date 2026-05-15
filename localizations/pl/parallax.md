---
title: Efekt paralaksy
description: Jak zastosować efekt paralaksy do tła menu i elementów.
---

# Czym jest efekt paralaksy?

Efekt paralaksy to fajny trik wizualny, który sprawia, że tła i elementy menu wydają się mieć głębię. Gdy poruszasz kursorem myszy, elementy z włączoną paralaksą lekko się przesuwają, tworząc iluzję przestrzeni 3D w Twoim menu 2D. 

Pomyśl o tym jak o jeździe samochodem — rzeczy znajdujące się bliżej Ciebie (na przykład znaki drogowe) wydają się poruszać szybciej niż te odległe (na przykład góry). W FancyMenu ta sama idea tworzy bardziej dynamiczne i interaktywne wrażenia.

# Gdzie można używać paralaksy w FancyMenu?

W FancyMenu efekt paralaksy możesz stosować w dwóch głównych miejscach:

1. **Tła menu**: spraw, aby całe tło menu lekko poruszało się wraz z kursorem myszy
2. **Elementy**: spraw, aby pojedyncze elementy (na przykład obrazy, przyciski lub tekst) poruszały się niezależnie

# Jak używać paralaksy w tle menu

Dodanie efektu paralaksy do tła menu jest bardzo proste:

1. Otwórz edytor menu, naciskając **CTRL+ALT+C**, aby wyświetlić pasek menu, a następnie przejdź do **Personalizacja**
2. Utwórz nowy układ lub edytuj istniejący
3. Kliknij **Układ → Właściwości** 
4. Otwórz **Tła menu**
5. Jako typ tła wybierz **Obraz**
6. Skonfiguruj tło obrazowe:
   - Wybierz obraz (lokalny lub z internetu)
   - Włącz **Efekt paralaksy**, klikając przełącznik
   - Ustaw **Intensywność efektu paralaksy X** i **Intensywność efektu paralaksy Y** (między 0.0 a 1.0)
   - Opcjonalnie włącz **Odwróć ruch paralaksy**, aby zmienić kierunek

> **Wskazówka**: Im wyższa wartość intensywności, tym bardziej będzie się poruszać tło. FancyMenu 3.9.0 pozwala ustawiać intensywność X i Y osobno, więc możesz sprawić, że ruch będzie silniejszy poziomo niż pionowo albo odwrotnie.
{.is-info}

# Jak używać paralaksy dla pojedynczych elementów

Możesz też dodać paralaksę do pojedynczych elementów, aby tworzyć warstwowe efekty:

1. Wybierz dowolny element w edytorze, klikając go
2. Kliknij prawym przyciskiem myszy element, aby otworzyć menu kontekstowe
3. Przewiń w dół i znajdź **Efekt paralaksy: Włączony/Wyłączony**
4. Przełącz go na **Włączony**
5. Dostosuj wartości **Intensywność paralaksy X** i **Intensywność paralaksy Y** (między 0.0 a 1.0)
6. Opcjonalnie włącz **Odwróć paralaksę**, aby zmienić kierunek ruchu

# Wskazówki dotyczące tworzenia świetnych efektów paralaksy

## Warstwuj elementy

Twórz wrażenie głębi, używając różnych wartości intensywności paralaksy dla różnych elementów. Możesz dostosowywać X i Y osobno:

- **Tło**: niższa intensywność (0.1-0.3)
- **Elementy środkowej warstwy**: średnia intensywność (0.3-0.6)
- **Elementy pierwszego planu**: wyższa intensywność (0.6-0.9)

To tworzy przekonujący efekt 3D podczas poruszania myszą!

## Łącz zwykłą i odwróconą paralaksę

Spróbuj ustawić niektóre elementy na **Odwróć ruch paralaksy: Włączony**, a inne na **Wyłączony**. Sprawi to, że elementy będą poruszać się w przeciwnych kierunkach, wzmacniając efekt głębi.

## Nie przesadzaj

Zbyt duży ruch może rozpraszać. Używaj efektu paralaksy oszczędnie, zwłaszcza przy wysokich wartościach intensywności.

# Rozwiązywanie problemów

## Paralaksa nie działa?

1. Upewnij się, że efekt paralaksy jest włączony
2. Sprawdź, czy intensywność paralaksy nie jest ustawiona na 0
4. Potwierdź, że opcja „Slide Wide Images From Left To Right” jest wyłączona (ta opcja koliduje z paralaksą)

## Ruch paralaksy jest za szybki/za wolny?

Dostosuj wartości **Intensywność paralaksy X/Y**:
- Niższe wartości (bliżej 0) = wolniejszy, bardziej subtelny ruch
- Wyższe wartości (bliżej 1) = szybszy, bardziej wyrazisty ruch

# Podsumowanie

Efekt paralaksy to świetny sposób, aby menu Minecrafta wydawało się bardziej żywe i interaktywne. Eksperymentuj z różnymi kombinacjami paralaksy tła i elementów, aby tworzyć efektowne, dynamiczne układy reagujące na ruchy myszy!

Pamiętaj, że najlepsze efekty są często subtelne — odrobina ruchu wystarczy, by stworzyć wciągające wrażenie.
