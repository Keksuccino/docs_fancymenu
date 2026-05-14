---
title: Głowy graczy
description: Jak wyświetlić głowę gracza jako obraz 2D lub 3D w menu.
---

# Głowy graczy w menu

Aby wyświetlić głowę gracza jako obraz 2D lub 3D za pomocą elementu Image, możesz skorzystać z zewnętrznego internetowego API o nazwie „Minotar”.

## Obraz 2D

### 1. Dodaj element Image

W edytorze FancyMenu kliknij prawym przyciskiem myszy tło, wybierz „New Element”, a następnie „Image” (lub „Picture”).

### 2. Ustaw źródło internetowe

Kliknij prawym przyciskiem myszy element Image, aby otworzyć jego właściwości. W polu typu źródła wybierz „Web”.

### 3. Zbuduj adres URL z prawidłowym placeholderem

W polu „Source” wpisz następujący adres URL:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

FancyMenu użyje `{"placeholder":"playername"}` do dynamicznego wstawienia nazwy użytkownika aktualnego gracza do adresu URL, dzięki czemu element Image pobierze i wyświetli jego głowę z Minotar.

## Obraz 3D

To działa bardzo podobnie jak wersja 2D, ale tutaj musimy użyć innego adresu URL:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

`200` oznacza tutaj rozmiar w pikselach, więc jeśli chcesz mniejszą wersję, zastąp go na przykład `100`, a jeśli większą, użyj `300` i tak dalej.
