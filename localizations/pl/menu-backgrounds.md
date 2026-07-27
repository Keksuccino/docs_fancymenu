---
title: Tła menu
description: 'Jak ustawić niestandardowe tła menu (obrazy, animacje) dla ekranów.'
---

# Tła menu

FancyMenu pozwala ustawić niestandardowe tła dla menu. Możesz używać obrazów, animowanych tekstur, pokazów slajdów, panoram sześciennych, kolorów, przeglądarek, filmów, shaderów GLSL i nie tylko.

# Ustawianie tła

Dostosowywanie tła menu jest dostępne z menu kontekstowego edytora układu:

1. Otwórz edytor układu.
2. Kliknij prawym przyciskiem myszy tło edytora.
3. Otwórz **Tła menu**.
4. Włącz i skonfiguruj typy tła, których chcesz używać.

Do najczęściej używanych typów tła należą:

- Vanilla
- Obraz
- Pokaz slajdów
- Panorama sześcienna
- Kolor (HEX)
- Przeglądarka
- Wideo
- Shader GLSL
- Wideo [MCEF] (przestarzałe)
- Dodatkowe typy tła z dodatków

Stary typ tła **Wideo [MCEF]** jest przestarzały. Do nowych układów używaj [natywnego tła **Wideo**](./video) opartego na Watermedia V3.

# Usuwanie niestandardowego tła

Otwórz ponownie **Tła menu** i wyłącz lub usuń typ niestandardowego tła, którego już nie chcesz używać. Jeśli żaden typ niestandardowego tła nie jest aktywny, ekran powróci do swojego zwykłego, domyślnego zachowania tła.

# Nakładanie teł

W jednym układzie można włączyć kilka typów tła menu. Aktywne tła są renderowane jako stos, więc bazowy obraz lub panorama może być połączona z przezroczystą przeglądarką, shaderem, paralaksą lub innymi warstwami.

Jeśli masz również aktywnych kilka układów, ich stosy teł mogą się także łączyć. Aby posortować układy i wyświetlać je w określonej kolejności, kliknij prawym przyciskiem myszy tło edytora i wybierz **Indeks układu**.

# Przezroczyste tła

FancyMenu renderuje czarną warstwę pod aktywnymi niestandardowymi tłami. Przezroczyste piksele w najniższym tle ujawnią więc czerń. Użyj nieprzezroczystego tła bazowego, a następnie dodawaj na nim przezroczyste warstwy.

Aby uczynić obraz tła półprzezroczystym, użyj dowolnego edytora grafiki.

# Tła przeglądarki

Typ tła **Przeglądarka** działa podobnie jak [element Przeglądarka](./elements#browser), ale wypełnia cały ekran i automatycznie zostaje ustawiony jako aktywny. Jest to przydatne do pełnoekranowej treści internetowej, lokalnych stron HTML lub warstw wideo z internetu.

# Tła shaderów GLSL

Typ tła **Shader GLSL** renderuje niestandardowe shadery GLSL i obsługuje tworzenie shaderów w stylu Shadertoy. Zobacz stronę [API shaderów GLSL](/glsl-shader-api), aby poznać obsługiwane zmienne uniform i strukturę shaderów.
