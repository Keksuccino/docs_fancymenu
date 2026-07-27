---
title: Globalne dostosowania
description: 'Zastosuj globalne zmiany FancyMenu, które wpływają na wszystkie ekrany.'
---

# Globalne dostosowania

Globalne dostosowania stosują wspólne ustawienia interfejsu i uruchamiania bez konieczności edycji każdego układu osobno. Działają nawet wtedy, gdy zwykłe dostosowywanie ekranów jest wyłączone.

Typowe przykłady:

- Użyj jednego wspólnego stylu przycisków i suwaków dla wszystkich ekranów.
- Globalnie podmień tło menu, panoramę i muzykę menu.
- Zastosuj globalne zachowanie przy uruchamianiu/okna (skala GUI, pełny ekran, tytuł/ikona okna).
- Globalnie podmień tekstury przycisków vanilla bez paczki zasobów.
- Globalnie podmień muzykę menu vanilla bez paczki zasobów.

# Gdzie je znaleźć

Otwórz **pasek menu** FancyMenu, gdy **nie** jesteś w edytorze układu, a następnie wybierz **Dostosowywanie -> Globalne dostosowania**.

# Co możesz dostosować

## Globalne zachowanie i uruchamianie

- [**Intro gry**](./game-intro) (wideo lub animacja intro odtwarzana przed ekranem tytułowym)
- **Ikony świata na ekranie gry jednoosobowej**
- **Ikony serwerów na ekranie gry wieloosobowej**
- [**Płynne wczytywanie świata**](./seamless-world-loading) (używa niedawnego zrzutu ekranu świata jako tła ekranu ładowania)
- [**Niestandardowa ikona okna**](./window-customization#custom-icon)
- [**Niestandardowy tytuł okna**](./window-customization#custom-title)
- **Domyślna skala GUI**
- **Wymuś pełny ekran przy uruchomieniu**

## Wygląd przycisków

- **Niestandardowe tekstury przycisków** (stany Normalny/Najechany/Nieaktywny, tryb przezroczysty, [nine-slice](./nine-slicing-and-tiling) + rozmiary obramowania)
- **Etykiety przycisków** (podkreślenie po najechaniu, kolor bazowy/po najechaniu, skala, cień)

## Wygląd suwaków

- **Niestandardowe tekstury suwaków**
- **Tekstura tła suwaka** (tekstura, tryb przezroczysty, [nine-slice](./nine-slicing-and-tiling) + rozmiary obramowania)
- **Tekstury uchwytu suwaka** (stany Normalny/Najechany/Nieaktywny, [nine-slice](./nine-slicing-and-tiling) + rozmiary obramowania)
- **Etykiety suwaków** (podkreślenie po najechaniu, kolor bazowy/po najechaniu, skala, cień)

## Wygląd menu i dźwięk

- [**Niestandardowa tekstura tła menu**](./menu-backgrounds)
- [**Niestandardowa panorama tła menu**](./panoramas)
- **Odtwarzaj muzykę menu Vanilla** (włączanie/wyłączanie odtwarzania muzyki menu Vanilla)
- [**Niestandardowe utwory muzyczne menu**](./background-music)
- **Niestandardowy dźwięk kliknięcia przycisku/suwaka**

# Niestandardowe utwory muzyczne menu

Użyj **Niestandardowych utworów muzycznych menu**, aby zbudować losową listę utworów dla menu.

> [!IMPORTANT]
> Globalne niestandardowe utwory menu odtwarzają się tylko wtedy, gdy nie jest załadowany żaden świat, na przykład na ekranie tytułowym. Użyj elementu [**Audio**](./elements#audio) dla dźwięku menu wewnątrz świata.

Skonfigurowane utwory używają kanału dźwiękowego Music i zastępują muzykę menu Vanilla w obsługiwanych menu spoza świata.

- Pierwszy utwór zaczyna się po około pięciu sekundach.
- Kolejne utwory zaczynają się po losowym opóźnieniu od około jednej do trzydziestu sekund.
- Utwory są wybierane losowo.
- Przy wielu utworach poprzedni utwór nie jest wybierany dwa razy z rzędu.

Zarządzaj listą utworów z poziomu **Niestandardowe utwory muzyczne menu**:

- Otwórz **Niestandardowe utwory muzyczne menu**, aby otworzyć **Zarządzaj utworami muzyki menu**.
- Użyj **Dodaj utwór**, aby dodać źródła audio.
- Użyj **Usuń utwór**, aby usunąć jeden wpis.
- Użyj **Wyczyść utwory**, aby usunąć wszystkie wpisy.
