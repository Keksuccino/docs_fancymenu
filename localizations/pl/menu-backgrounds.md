---
title: Tła menu
description: 'Jak ustawić własne tła menu (obrazy, animacje) dla ekranów.'
---

# Tła menu

FancyMenu umożliwia ustawianie własnych teł dla menu. Możesz używać obrazów, animowanych tekstur, pokazów slajdów, panoram sześciennych, kolorów, przeglądarek, filmów, shaderów GLSL i nie tylko.

# Ustawianie tła

W FancyMenu 3.9.0+ dostosowywanie tła menu odbywa się bezpośrednio z menu kontekstowego edytora układu:

1. Otwórz edytor układu.
2. Kliknij prawym przyciskiem myszy tło edytora.
3. Otwórz **Tła menu**.
4. Włącz i skonfiguruj wybrane typy tła.

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
- i więcej..

Stary typ tła **Wideo [MCEF]** jest w FancyMenu 3.9.0 przestarzały. Do nowych układów używaj nowego natywnego tła **Wideo** opartego na Watermedia V3.

# Usuwanie własnego tła

Ponownie otwórz **Tła menu** i wyłącz/usuń typ własnego tła, którego już nie chcesz. Jeśli żaden własny typ tła nie jest aktywny, ekran wróci do swojego zwykłego, waniliowego zachowania tła.

# Stacking teł

FancyMenu 3.9.0 pozwala włączać wiele typów tła menu w tym samym układzie. Aktywne tła są renderowane jako stos, więc możesz połączyć bazowy obraz lub panoramę z półprzezroczystymi nakładkami, warstwami przeglądarki, warstwami shaderów, warstwami paralaksy i innymi efektami.

Jeśli masz również aktywnych kilka układów, ich stosy tła też mogą się łączyć. Aby sortować układy i ustawić ich wyświetlanie w określonej kolejności, kliknij prawym przyciskiem myszy tło edytora i wybierz **Indeks układu**.

# Przezroczyste tła

Ponieważ za tłami nic nie ma, nie da się ustawić przezroczystości tła znajdującego się na samym dole, ponieważ prowadziłoby to do graficznych błędów. Możliwe jest jednak używanie przezroczystości w konfiguracjach z wieloma warstwami tła, o ile dolna warstwa pozostaje całkowicie nieprzezroczysta. W ten sposób możesz mieć półprzezroczyste warstwy tła nad warstwą dolną.

Aby nadać obrazowi tła półprzezroczystość, użyj dowolnego edytora graficznego.

# Tła przeglądarki

Typ tła **Przeglądarka** działa podobnie jak element Browser, ale wypełnia cały ekran i jest automatycznie fokusowany. Jest to przydatne do pełnoekranowych treści internetowych, lokalnych stron HTML lub warstw wideo internetowego.

# Tła shaderów GLSL

Typ tła **Shader GLSL** renderuje własne shadery GLSL i obsługuje tworzenie shaderów w stylu Shadertoy. Zobacz stronę [API shaderów GLSL](/glsl-shader-api), aby poznać obsługiwane uniformy i strukturę shaderów.
