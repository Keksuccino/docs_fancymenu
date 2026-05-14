---
title: Krycie elementu
description: Jak kontrolować przezroczystość elementów.
---

# Krycie elementu

Większość elementów w FancyMenu (z kilkoma wyjątkami) obsługuje ustawianie krycia za pomocą menu dostępnego po kliknięciu prawym przyciskiem myszy.

Wartość krycia elementów obsługuje placeholdery, co umożliwia dynamiczną aktualizację ich przezroczystości na podstawie placeholdera.

Dzięki temu można tworzyć własną logikę zanikania, gdy użyje się tego w połączeniu z elementami Ticker do aktualizowania wartości zmiennych, a następnie zastosowania ich jako krycia za pomocą placeholderów.

Aby ustawić krycie elementów, **kliknij element prawym przyciskiem myszy -> Krycie -> Ustaw**.

# Zanikanie elementów

Jeśli chcesz po prostu sprawić, by elementy pojawiały się lub znikały z efektem zanikania, prawdopodobnie łatwiej będzie skorzystać z wbudowanej funkcji zanikania elementów. Możesz ją włączyć w menu dostępnym po kliknięciu elementu prawym przyciskiem myszy.

Ta funkcja sprawia, że elementy płynnie pojawiają się za każdym razem, gdy się ładują — zarówno przy początkowym wczytaniu po otwarciu menu, jak i wtedy, gdy wymagania ładowania elementu powodują jego wczytanie. Będą one płynnie znikać zawsze, gdy ich wymagania ładowania spowodują, że przestaną się ładować / staną się niewidoczne.

Funkcja zanikania obsługuje ustawienie szybkości zanikania, aby kontrolować, jak szybko element powinien pojawiać się lub znikać.
