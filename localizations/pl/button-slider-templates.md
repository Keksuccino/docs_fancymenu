---
title: Szablony przycisków i suwaków
description: >-
  Nadaj wszystkim przyciskom lub suwakom na ekranie tekstury, dźwięki i styl
  etykiet z jednego przycisku-szablonu.
sourceBlobSha: 805a2ae3221a644c78cd5eafebc5579bc8d60815
---

# Szablony przycisków i suwaków

Szablon to [element Przycisk](/elements#button), który przekazuje swój wygląd wszystkim pozostałym przyciskom albo suwakom na ekranie — zarówno domyślnym, jak i własnym. Zmień szablon, a zmienią się wszystkie te elementy.

> [!TIP]
> Jeśli chcesz uzyskać taki sam wygląd we wszystkich menu gry, użyj [globalnych modyfikacji](/global-customizations). Szablony dotyczą jednego ekranu lub wszystkich ekranów wczytywanych przez [uniwersalny układ](/universal-layouts).

# Tworzenie szablonu

1. Dodaj element Przycisk do układu.
2. Kliknij go prawym przyciskiem myszy, otwórz **Ustawienia szablonu** i włącz **Tryb szablonu**.
3. Ustaw **Udostępniaj ustawienia** na **Przyciski** lub **Suwaki**.
4. Nadaj szablonowi wybrane tekstury, dźwięki i ustawienia etykiety, tak jak w przypadku każdego innego przycisku. Po wybraniu **Suwaki** ustawienia tekstur będą dotyczyć suwaków.

Szablon nie jest widoczny poza edytorem, więc umieść go w miejscu, w którym nie będzie przeszkadzał. W edytorze szablon suwaków wygląda jak suwak.

# Ustawienia udostępniane przez szablony

## Zawsze

- Tekstury przycisku (lub suwaka) wraz z ustawieniami [dziewięciopolowego skalowania](/nine-slicing-and-tiling).
- Dźwięki najechania kursorem, opuszczenia elementu i kliknięcia.

Gdy szablon jest aktywny, przyciski używają jego tekstur i dźwięków zamiast własnych. Jeśli szablon nie ma tekstur, przyciski również nie używają własnych tekstur.

## Po włączeniu

Włącz poniższe opcje w **Ustawieniach szablonu**:

| Ustawienie | Co przyciski przejmują z szablonu |
|---|---|
| **Udostępniaj etykietę w trybie szablonu** | Jego **Etykietę** i **Etykietę po najechaniu**, a także cały styl etykiety: **Wyrównanie etykiety**, **Skala etykiety**, **Kolor podstawowy etykiety**, **Kolor etykiety po najechaniu**, **Cień etykiety** i **Podkreślaj etykietę po najechaniu**. |
| **Udostępniaj pozycję X w trybie szablonu** i **Udostępniaj pozycję Y w trybie szablonu** | Jego pozycję. Domyślne przyciski przesuwają się dopiero po zmianie ustawienia **Punkt zakotwiczenia** z **Domyślny (oryginalny)**. |
| **Udostępniaj przezroczystość w trybie szablonu** | Jego przezroczystość. |

## Wyrównywanie etykiet we wszystkich przyciskach

Po włączeniu opcji **Udostępniaj etykietę w trybie szablonu** wszystkie przyciski przejmują również tekst szablonu, więc ta opcja jest przeznaczona dla ekranów, na których wszystkie przyciski mają mieć tę samą etykietę.

Aby wyrównać same etykiety, zachowując ich tekst:

- Na jednym ekranie zaznacz przyciski, klikając je z wciśniętym klawiszem `Ctrl` (zobacz [Zaznaczanie](/layout-editor#selecting)), kliknij jeden z nich prawym przyciskiem myszy i ustaw **Wyrównanie etykiety** dla wszystkich naraz.
- We wszystkich menu użyj opcji **Wyrównanie etykiety** w sekcji [Globalne modyfikacje](/global-customizations#labels).

# Warto wiedzieć

- Szablonem może być tylko element Przycisk, ale działa on z domyślnymi i własnymi przyciskami oraz suwakami.
- Na ekranie może jednocześnie działać jeden szablon przycisków i jeden szablon suwaków. Jeśli istnieje więcej niż jeden szablon tego samego rodzaju, działa tylko jeden z nich.
- Szablon działa tylko wtedy, gdy jest widoczny. Możesz go włączać i wyłączać za pomocą [warunków widoczności](/element-visibility).
