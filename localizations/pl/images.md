---
title: Obrazy
description: Jakie pliki graficzne obsługuje FancyMenu i jak konwertować inne formaty.
sourceBlobSha: 382f9ed2d99b0df29018dc4abf0b9b842ff01dec
---
# Obrazy

FancyMenu wyświetla obrazy w wielu miejscach, na przykład jako elementy graficzne, tła menu i tekstury przycisków. Obsługuje następujące pliki:

- PNG (`.png`): najlepszy wybór w przypadku nieruchomych obrazów z przezroczystością.
- JPEG (`.jpg` lub `.jpeg`): mniejsze pliki ze zdjęciami, ale bez przezroczystości.
- APNG (`.apng`) i GIF (`.gif`): animowane obrazy. Zobacz [Animacje](/animations).

FancyMenu rozpoznaje typy obrazów na podstawie rozszerzenia pliku, dlatego nazwa pliku musi kończyć się właściwym rozszerzeniem.

> [!TIP]
> FancyMenu używa obrazów dokładnie w takiej postaci, w jakiej je zapisano. Aby były wyraźne i wczytywały się szybko, zobacz [Optymalizacja tekstur](/optimizing-textures).

# Konwertowanie obrazów

Inne formaty, takie jak WebP, nie działają w FancyMenu. Najpierw przekonwertuj je, na przykład online:

- [WebP na PNG](https://convertio.co/webp-png/)
- [JPEG na PNG](https://jpg2png.com/)
- [PNG na JPEG](https://www.freeconvert.com/png-to-jpeg): zmniejsza rozmiar dużych obrazów, ale usuwa przezroczystość.

Aby tworzyć lub konwertować animacje, zobacz [Tworzenie animacji](/animations#making-animations).
