---
title: Niestandardowy kursor
description: Jak ustawić niestandardowy kursor myszy w menu.
sourceBlobSha: 6ccd4932bed99ab10c094adffd503bd0a44d9edd
---

# Niestandardowy kursor myszy

Dodaj do układu [element **Kursor**](/elements#cursor), aby zastąpić kursor systemowy na danym ekranie:

1. Wybierz **Nowy element -> Kursor**.
2. Ustaw teksturę PNG z kanałem alfa RGBA.
3. Ustaw wartości **Punkt aktywny X** i **Punkt aktywny Y** na piksel tekstury, w którym mają być rejestrowane kliknięcia.
4. Włącz podgląd w edytorze, jeśli chcesz sprawdzić wygląd kursora podczas edycji.
5. Użyj [układu uniwersalnego](/universal-layouts), jeśli ten sam kursor ma być widoczny na wielu obsługiwanych ekranach.

Zalecamy małe tekstury kursora, takie jak `32×32` lub `64×64`. Wygląd i działanie kursora mogą się różnić w zależności od systemu operacyjnego.
