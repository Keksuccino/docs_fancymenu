---
title: Globalne dostosowania
description: 'Zastosuj globalne poprawki FancyMenu, które wpływają na wszystkie ekrany.'
---

# Globalne dostosowania

Globalne dostosowania to poprawki FancyMenu, które działają w całym interfejsie gry.
Używaj ich, gdy chcesz uzyskać spójny styl lub zachowanie wszędzie, zamiast edytować osobno każdy układ ekranu.

> [!INFO]
> W przeciwieństwie do większości funkcji dostosowywania FancyMenu, globalne dostosowania działają nawet wtedy, gdy zwykłe dostosowania ekranów są wyłączone.
> **Nie** wymagają włączania dostosowań osobno dla każdego ekranu, co oznacza, że jedna zmiana może od razu objąć wszystkie ekrany.

Typowe przykłady:

- Użyj jednego wspólnego stylu przycisków i suwaków dla wszystkich ekranów.
- Globalnie podmień tło menu, panoramę i muzykę menu.
- Zastosuj globalne zachowanie uruchamiania/okna (skala GUI, pełny ekran, tytuł/ikona okna).
- Globalnie podmień tekstury przycisków vanilla bez paczki zasobów.
- Globalnie podmień muzykę menu vanilla bez paczki zasobów.

# Gdzie je znaleźć

Otwórz **pasek menu** FancyMenu, gdy **nie** jesteś w edytorze układu, a następnie wybierz **Dostosowanie -> Globalne dostosowania**.

# Szybki start

1. Otwórz **Dostosowanie -> Globalne dostosowania**.
2. Wybierz jedną kategorię na początek (na przykład **Niestandardowe tekstury przycisków**).
3. Skonfiguruj opcje w tej kategorii (selektory zasobów, przełączniki lub pola liczbowe).
4. Przetestuj efekt na kilku ekranach.
5. Dopracuj powiązane ustawienia (na przykład przezroczystość, style etykiet, obramowania nine-slice).

# Co możesz dostosować

## Globalne zachowanie i uruchamianie

- **Intro gry** (film lub animacja intro odtwarzana przed pojawieniem się ekranu tytułowego)
- **Ikony świata na ekranie singleplayer**
- **Ikony serwerów na ekranie multiplayer**
- **Płynne ładowanie świata** (używa zrzutu ekranu świata jako tła ekranu ładowania świata)
- **Niestandardowa ikona okna**
- **Niestandardowy tytuł okna**
- **Domyślna skala GUI**
- **Wymuś pełny ekran przy uruchomieniu**

## Wygląd przycisków

- **Niestandardowe tekstury przycisków** (stany Normalny/Najechany/Nieaktywny, tryb przezroczysty, nine-slice + rozmiary obramowania)
- **Etykiety przycisków** (podkreślenie po najechaniu, kolor bazowy/kolor po najechaniu, skala, cień)

## Wygląd suwaków

- **Niestandardowe tekstury suwaków**
- **Tekstura tła suwaka** (tekstura, tryb przezroczysty, nine-slice + rozmiary obramowania)
- **Tekstury uchwytu suwaka** (stany Normalny/Najechany/Nieaktywny, nine-slice + rozmiary obramowania)
- **Etykiety suwaków** (podkreślenie po najechaniu, kolor bazowy/kolor po najechaniu, skala, cień)

## Wygląd i dźwięki menu

- **Niestandardowa tekstura tła menu**
- **Niestandardowa panorama tła menu**
- **Odtwarzaj muzykę menu vanilla** (włącza/wyłącza odtwarzanie muzyki menu vanilla)
- **Niestandardowe utwory muzyczne menu**
- **Niestandardowy dźwięk kliknięcia przycisku/suwaka**

# Niestandardowe utwory muzyczne menu

Użyj **Niestandardowych utworów muzycznych menu**, aby zbudować losowaną listę utworów dla menu.

Skonfigurowane niestandardowe utwory zastępują muzykę menu vanilla w menu.

- Otwórz **Niestandardowe utwory muzyczne menu**, aby otworzyć **Zarządzaj utworami muzycznymi menu**.
- Użyj **Dodaj utwór**, aby dodać źródła audio.
- Użyj **Usuń utwór**, aby usunąć jeden wpis.
- Użyj **Wyczyść utwory**, aby usunąć wszystkie wpisy.
