---
title: APNG
description: Jak tworzyć obrazy APNG zgodne z FancyMenu.
---

# Animowane obrazy PNG

> [!NOTE]
> W przypadku dużych lub złożonych animacji lepiej użyć [plików AFMA](./fma). Watermedia V3 i Watermedia Binaries V3 mogą przyspieszyć dekodowanie APNG/GIF, jeśli są dostępne, ale AFMA pozostaje preferowanym formatem animacji FancyMenu.


APNG to animowana wersja obrazów PNG, dzięki czemu można uzyskać te same możliwości co w GIF-ie, ale w pełnej, bezstratnej jakości PNG!

FancyMenu ma wbudowaną obsługę APNG, ale jest dość wybredny, jeśli chodzi o obsługiwane pliki APNG.
Wymaga APNG **bez kompresji**, które **nie są przeplatane**.

# Tworzenie animacji APNG

Możesz się zdziwić, jak trudno jest znaleźć dobry edytor APNG, zwłaszcza z opcjami wyłączenia kompresji i przeplotu.

Świetnym wyborem edytora jest [ScreenToGif](https://www.screentogif.com/), które jest właściwie narzędziem do nagrywania GIF-ów i APNG z ekranu, ale świetnie nadaje się też do tworzenia zwykłych APNG — wystarczy pominąć nagrywanie i od razu wczytać pliki do edytora!

## Otwórz edytor

Pierwszą rzeczą, którą zobaczysz po otwarciu [ScreenToGif](https://www.screentogif.com/), jest ten ekran. Kliknij tutaj **Editor**.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Wczytaj klatki

Teraz potrzebujesz swoich klatek PNG. Przeciągnij i upuść je do edytora.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Opóźnienie klatki

Aby skonfigurować opóźnienie między klatkami, zaznacz klatkę lub klatki, które chcesz edytować, przejdź do zakładki **Edit** i w sekcji **Delay (Duration)** kliknij **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Zapętlanie

Zachowanie zapętlania można skonfigurować w menu **Save As**. Sprawdź następny krok, aby dowiedzieć się, jak otworzyć to menu.

## Eksportowanie APNG

Teraz możesz wrócić do zakładki **File** i kliknąć **Save As**.

W menu zapisu upewnij się, że:
- Ustawiono typ pliku na **APNG** (pierwsze ustawienie; może być konieczne przewinięcie menu na samą górę)
- Wyłączono **Detect Unchanged Pixels**

> [!NOTE]
> W tym menu możesz też skonfigurować **zachowanie zapętlania**! Wyłączenie **Looped Apng** spowoduje, że APNG w ogóle nie będzie się zapętlać, a po jego włączeniu możesz wybrać określoną liczbę powtórzeń albo nieskończone zapętlanie.

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Używanie APNG w FancyMenu

Skopiuj teraz swój plik APNG do `<game-directory>/config/fancymenu/assets/`. Następnie będzie można go używać prawie wszędzie tam, gdzie akceptowane są obrazy.

> [!WARNING]
> Bardzo ważne jest, aby nazwa pliku APNG kończyła się na `.apng`!
> FancyMenu nie będzie w stanie rozpoznać obrazu jako APNG, jeśli nie kończy się on na `.apng`.

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
