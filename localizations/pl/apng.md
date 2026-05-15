---
title: APNG
description: Jak tworzyć obrazy APNG zgodne z FancyMenu.
---

# Animowane obrazy PNG

> W przypadku nowych, dużych lub złożonych animacji lepiej używać plików [AFMA/FMA](/fma). FancyMenu 3.9.0 może korzystać z Watermedia V3 + Watermedia Binaries V3, aby szybciej dekodować APNG/GIF, gdy są dostępne, ale AFMA nadal pozostaje preferowanym formatem animacji w FancyMenu.
{.is-info}


APNG to animowana wersja obrazów PNG, dzięki czemu można uzyskać te same możliwości co w GIF-ie, ale w pełnej, bezstratnej jakości PNG!

FancyMenu ma wbudowaną obsługę APNG, ale jest dość wybredne co do tego, które APNG są obsługiwane.
Wymaga **nieskompresowanych** APNG, które **nie są przeplatane**.

# Tworzenie animacji APNG

Możesz się zdziwić, jak trudno znaleźć dobry edytor APNG, zwłaszcza z opcjami wyłączenia kompresji i przeplatania.

Świetnym wyborem jest [ScreenToGif](https://www.screentogif.com/), które jest właściwie narzędziem do nagrywania GIF-ów i APNG z ekranu, ale doskonale nadaje się też do tworzenia zwykłych APNG — wystarczy pominąć część nagrywania i od razu wczytać pliki do edytora!

## Otwórz edytor

Pierwszą rzeczą, którą zobaczysz po otwarciu [ScreenToGif](https://www.screentogif.com/), jest ten ekran. Kliknij tutaj **Editor**.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Wczytaj klatki

Teraz potrzebujesz swoich klatek PNG. Przeciągnij je i upuść do edytora.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Opóźnienie klatek

Aby skonfigurować opóźnienie między klatkami, zaznacz klatkę/klatki, które chcesz edytować, przejdź do zakładki **Edit**, a w sekcji **Delay (Duration)** kliknij **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Zapętlanie

Zachowanie zapętlania można skonfigurować w menu **Save As**. Sprawdź następny krok, aby dowiedzieć się, jak otworzyć to menu.

## Eksportowanie APNG

Teraz możesz wrócić do zakładki **File** i kliknąć **Save As**.

W menu zapisu upewnij się, że:
- Ustawisz typ pliku na **APNG** (pierwsze ustawienie; być może trzeba najpierw przewinąć menu do góry)
- Wyłączysz **Detect Unchanged Pixels**

> Możesz też skonfigurować w tym menu **zachowanie zapętlania**! Wyłączenie **Looped Apng** sprawi, że APNG w ogóle nie będzie się zapętlać, a po włączeniu tej opcji możesz wybrać określoną liczbę powtórzeń albo nieskończone zapętlanie.
{.is-info}

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Używanie APNG w FancyMenu

Teraz możesz skopiować plik APNG do `/config/fancymenu/assets/`. Następnie będzie można używać go w prawie wszystkich miejscach, które akceptują obrazy.

> To jest **naprawdę ważne**, aby nazwa pliku APNG kończyła się na `.apng`!
> FancyMenu nie będzie w stanie rozpoznać obrazu jako APNG, jeśli nie będzie on kończył się na `.apng`.
{.is-warning}

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
