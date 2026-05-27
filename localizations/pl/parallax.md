---
title: Efekt paralaksy
description: Jak zastosować efekt paralaksy do tła menu i elementów.
---
# Czym jest efekt paralaksy?

Efekt paralaksy to fajny trik wizualny, który sprawia, że tła i elementy menu wydają się mieć głębię. Gdy poruszasz kursorem myszy, elementy z włączoną paralaksą lekko się przesuwają, tworząc iluzję przestrzeni 3D w Twoim dwuwymiarowym menu. 

Można to porównać do jazdy samochodem — rzeczy znajdujące się bliżej Ciebie (na przykład znaki drogowe) wydają się poruszać szybciej niż te odległe (na przykład góry). W FancyMenu ta sama zasada tworzy bardziej dynamiczne i interaktywne doświadczenie.

# Gdzie można używać paralaksy w FancyMenu?

W FancyMenu efekt paralaksy możesz wykorzystać w dwóch głównych miejscach:

1. **Tła menu**: spraw, aby całe tło menu lekko poruszało się wraz z kursorem myszy
2. **Elementy**: spraw, aby pojedyncze elementy (takie jak obrazy, przyciski lub tekst) poruszały się niezależnie

# Jak używać paralaksy dla tła menu

Dodanie efektu paralaksy do tła menu jest bardzo proste:

1. Otwórz edytor menu, naciskając **CTRL+ALT+C**, aby wyświetlić pasek menu, a następnie przejdź do **Dostosowywanie**
2. Utwórz nowy układ lub edytuj istniejący
3. Kliknij **Układ → Właściwości** 
4. Otwórz **Tła menu**
5. Wybierz **Obraz** jako typ tła
6. Skonfiguruj tło obrazu:
   - Wybierz obraz (lokalny lub z internetu)
   - Włącz **Efekt paralaksy**, klikając przełącznik
   - Ustaw **Intensywność efektu paralaksy X** oraz **Intensywność efektu paralaksy Y** (w zakresie od 0.0 do 1.0)
   - Opcjonalnie włącz **Odwróć ruch paralaksy**, aby zmienić kierunek

> **Wskazówka**: Im wyższa wartość intensywności, tym bardziej będzie poruszać się tło. FancyMenu 3.9.0 pozwala ustawić osobno intensywność X i Y, dzięki czemu możesz wzmocnić ruch poziomy bardziej niż pionowy lub odwrotnie.
{.is-info}

# Jak używać paralaksy dla pojedynczych elementów

Możesz również dodać paralaksę do pojedynczych elementów, aby tworzyć warstwowe efekty:

1. Zaznacz dowolny element w edytorze, klikając go
2. Kliknij element prawym przyciskiem myszy, aby otworzyć menu kontekstowe
3. Przewiń w dół i znajdź **Efekt paralaksy: Włączony/Wyłączony**
4. Ustaw go na **Włączony**
5. Dostosuj wartości **Intensywność paralaksy X** i **Intensywność paralaksy Y** (w zakresie od 0.0 do 1.0)
6. Opcjonalnie włącz **Odwróć paralaksę**, aby zmienić kierunek ruchu

# Wskazówki dotyczące tworzenia świetnych efektów paralaksy

## Układaj elementy warstwowo

Twórz głębię, używając różnych wartości intensywności paralaksy dla różnych elementów. Możesz dostosować X i Y osobno:

- **Tło**: niższa intensywność (0.1-0.3)
- **Elementy środkowej warstwy**: średnia intensywność (0.3-0.6)
- **Elementy na pierwszym planie**: wyższa intensywność (0.6-0.9)

Dzięki temu uzyskasz przekonujący efekt 3D podczas poruszania myszą!

## Łącz zwykłą i odwróconą paralaksę

Spróbuj ustawić niektóre elementy na **Odwróć ruch paralaksy: Włączony**, a inne na **Wyłączony**. Sprawi to, że elementy będą poruszać się w przeciwnych kierunkach, wzmacniając efekt głębi.

## Nie przesadzaj

Zbyt duży ruch może rozpraszać. Używaj efektu paralaksy oszczędnie, zwłaszcza przy wysokich wartościach intensywności.

# Rozwiązywanie problemów

## Paralaksa nie działa?

1. Upewnij się, że efekt paralaksy jest włączony
2. Sprawdź, czy intensywność paralaksy nie jest ustawiona na 0
4. Upewnij się, że opcja "Slide Wide Images From Left To Right" jest wyłączona (ta opcja koliduje z paralaksą)

## Ruch paralaksy jest zbyt szybki/wolny?

Dostosuj wartości **Intensywność paralaksy X/Y**:
- Niższe wartości (bliżej 0) = wolniejszy, bardziej subtelny ruch
- Wyższe wartości (bliżej 1) = szybszy, bardziej wyrazisty ruch

## Paralaksa wydaje się mało płynna albo opóźniona?

To ograniczenie efektu paralaksy, ponieważ Minecraft używa współrzędnych całkowitych (pełnych liczb), więc możliwe, że efekt może sprawiać wrażenie, jakby elementy trochę "skakały", ale nie powinno to być zbyt zauważalne, jeśli używasz „normalnych” wartości intensywności paralaksy, a nie bardzo małych lub bardzo dużych.
