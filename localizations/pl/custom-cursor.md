---
title: Niestandardowy kursor
description: 'Jak sprawić, by menu używały niestandardowego kursora myszy.'
---

# Niestandardowy kursor myszy

Dodaj do układu [**element Cursor**](./elements#cursor), aby zastąpić systemowy kursor na tym ekranie:

1. Wybierz **New Element -> Cursor**.
2. Ustaw teksturę PNG z kolorem RGBA.
3. Ustaw **Hotspot X** i **Hotspot Y** na piksel tekstury, w którym mają następować kliknięcia.
4. Włącz podgląd w edytorze, gdy chcesz sprawdzić kursor podczas edycji.
5. Użyj [Universal Layout](./universal-layouts), gdy ten sam kursor ma się pojawiać na wielu obsługiwanych ekranach.

Zalecane są małe tekstury kursora, takie jak `32×32` lub `64×64`. Wygląd i działanie kursora mogą się różnić w zależności od systemu operacyjnego.
