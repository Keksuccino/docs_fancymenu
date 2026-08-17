---
title: Tła menu
description: 'Jak ustawiać niestandardowe tła menu (obrazy, animacje) dla ekranów.'
---
# Tła menu

FancyMenu umożliwia ustawianie niestandardowych teł menu. Możesz używać obrazów, animowanych tekstur, pokazów slajdów, panoram sześciennych, kolorów, przeglądarek, filmów, shaderów GLSL i nie tylko.

# Ustawianie tła

Dostosowywanie tła menu jest dostępne w menu kontekstowym edytora układu:

1. Otwórz edytor układu.
2. Kliknij prawym przyciskiem myszy tło edytora.
3. Otwórz **Tła menu**.
4. Włącz i skonfiguruj wybrany typ tła lub typy teł.

Najczęściej używane typy teł to:

- Waniliowe
- Obraz
- Pokaz slajdów
- Panorama sześcienna
- Kolor (HEX)
- Przeglądarka
- Film
- Shader GLSL
- Film [Rinku] (przestarzały)
- Dodatkowe typy teł z dodatków

Stary typ tła **Film [Rinku]** jest przestarzały. W nowych układach używaj [natywnego tła **Film**](./video), obsługiwanego przez Watermedia V3.

# Usuwanie niestandardowego tła

Ponownie otwórz **Tła menu** i wyłącz lub usuń niepotrzebny już niestandardowy typ tła. Jeśli żaden niestandardowy typ tła nie jest aktywny, ekran powróci do standardowego działania tła waniliowego.

# Nakładanie teł

W jednym układzie można włączyć wiele typów teł menu. Aktywne tła są renderowane jako stos, dzięki czemu bazowy obraz lub panorama mogą być łączone z półprzezroczystą przeglądarką, shaderem, warstwą paralaksy lub innymi warstwami.

Jeśli aktywnych jest również wiele układów, ich stosy teł także mogą się łączyć. Aby uporządkować układy i wyświetlać je w określonej kolejności, kliknij prawym przyciskiem myszy tło edytora, a następnie kliknij **Indeks układu**.

# Przezroczyste tła

FancyMenu renderuje czarną warstwę podkładową za aktywnymi niestandardowymi tłami. Przezroczyste piksele w tle znajdującym się na samym spodzie stosu ujawnią więc czarny kolor. Użyj nieprzezroczystego tła bazowego, a następnie umieść nad nim półprzezroczyste tła.

Aby ustawić przezroczystość obrazu tła, użyj wybranego edytora obrazów.

# Tła przeglądarki

Typ tła **Przeglądarka** działa podobnie jak [element Przeglądarka](./elements#browser), ale wypełnia cały ekran i automatycznie otrzymuje fokus. Jest to przydatne w przypadku pełnoekranowych treści internetowych, lokalnych stron HTML lub warstw z filmami internetowymi.

# Tła shaderów GLSL

Typ tła **Shader GLSL** renderuje niestandardowe shadery GLSL i obsługuje tworzenie shaderów w stylu Shadertoy. Więcej informacji o obsługiwanych uniformach i strukturze shaderów znajdziesz na stronie [API shaderów GLSL](/glsl-shader-api).
