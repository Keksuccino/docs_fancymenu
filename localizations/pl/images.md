---
title: Obrazy
description: 'Wszystko, co ważne na temat zasobów obrazów w FancyMenu.'
---
# Obrazy

FancyMenu obsługuje zasoby obrazów w wielu miejscach, takich jak tła menu, tekstury przycisków i wiele innych.

W FancyMenu możesz używać plików obrazów PNG, JPEG, GIF i APNG, ale w przypadku obrazów statycznych zaleca się używanie PNG, gdy tylko jest to możliwe. Zamiast używać GIF-ów i APNG do animacji, lepiej skorzystać z [pliku AFMA](/fma), czyli własnego formatu animowanych obrazów FancyMenu, ponieważ pliki AFMA są znacznie lepiej zoptymalizowane niż GIF/APNG, zużywają mniej pamięci RAM i mają mniejszy wpływ na wydajność.

# Konwertowanie obrazów do obsługiwanych formatów

Jeśli potrzebujesz przekonwertować obrazy do jednego z formatów obsługiwanych przez FancyMenu albo chcesz z różnych powodów przekonwertować jeden obsługiwany format na inny, zapoznaj się z poniższą listą stron internetowych, które dobrze sprawdzają się do konwersji obrazów online, bez konieczności pobierania jakiegokolwiek oprogramowania.

## GIF do APNG
Aby przekonwertować obraz GIF do APNG, skorzystaj z tej strony: https://ezgif.com/gif-to-apng.

## APNG do GIF
Aby przekonwertować APNG do GIF, skorzystaj z tej strony: https://ezgif.com/apng-to-gif.

## MP4 do APNG
Jeśli potrzebujesz przekonwertować krótką sekwencję wideo do APNG, wypróbuj tę stronę: https://ezgif.com/video-to-apng

## PNG do JPEG
Czasami użycie JPEG może zmniejszyć rozmiar zasobów, więc w takich przypadkach warto użyć JPEG zamiast PNG: https://www.freeconvert.com/png-to-jpeg. Pamiętaj, że pliki JPEG nie obsługują przezroczystości.

## JPEG do PNG
W typowym przypadku konwersji JPEG do PNG wypróbuj tę stronę: https://jpg2png.com/

## WebP do PNG
Pliki WebP nie są obsługiwane przez FancyMenu, dlatego musisz przekonwertować je do PNG: https://convertio.co/webp-png/

# Ograniczenia animowanych tekstur

FancyMenu używa własnego formatu [AFMA](/fma) do zoptymalizowanych animacji, dzięki czemu [pliki AFMA](/fma) mogą zawierać wiele klatek w wysokiej rozdzielczości. W przypadku starszych animowanych typów plików, takich jak GIF i APNG, należy jednak przestrzegać poniższych zalecanych limitów, aby nie zapełnić nadmiernie pamięci RAM ani zbytnio nie pogorszyć wydajności gry:

- Używaj maksymalnie **200 klatek** na animację.
- Używaj maksymalnej rozdzielczości **1080p** dla swoich klatek.
- Łączna liczba **1000 klatek dla WSZYSTKICH animacji** nie powinna zostać przekroczona, ponieważ nawet jeśli używasz tylko 200 klatek na animację, wszystkie zostaną załadowane do pamięci. Używanie zbyt wielu animacji jednocześnie nadal może więc zapełnić pamięć RAM.

> [!IMPORTANT]
> Te limity NIE dotyczą [plików AFMA](/fma), ponieważ pliki AFMA nie ładują wszystkich klatek do pamięci i są znacznie lepiej zoptymalizowane, dzięki czemu nie wpływają na wydajność tak mocno jak starsze typy animacji.
