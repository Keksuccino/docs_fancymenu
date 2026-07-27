---
title: Panoramy
description: Twórz i używaj sześcioobrazowych panoram sześciennych.
---

# Panoramy sześcienne

Każda panorama ma swój własny katalog poniżej:

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` to aktywna instancja launchera, która może różnić się od standardowego katalogu `.minecraft`.

# Struktura katalogów

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # opcjonalne
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

Sześć obrazów ścian musi być plikami PNG o dokładnie takich nazwach jak pokazano powyżej, a wszystkie sześć musi mieć identyczne wymiary. Wielkość liter w nazwach plików może mieć znaczenie w niektórych systemach operacyjnych.

Dodaj opcjonalny plik `overlay.png` obok `properties.txt`, aby uzyskać winietę lub inną nakładkę obejmującą całą panoramę.

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Właściwość | Znaczenie |
|---|---|
| `name` | Wymagany, rozróżniany wielkością liter identyfikator używany w czasie działania; zachowaj go jako unikalny |
| `speed` | Mnożnik prędkości obrotu; `1.0` jest wartością domyślną |
| `fov` | Pole widzenia w stopniach |
| `angle` | Pionowy kąt widzenia w stopniach |
| `start_rotation` | Początkowy poziomy obrót w stopniach |

Wymagane jest tylko `name`. Brakujące wartości opcjonalne użyją domyślnych ustawień pokazanych w przykładzie. Pozostaw `type = panorama` i `panorama-meta` bez zmian; wpisuj jedną parę `key = value` w każdej linii i używaj kropki jako separatora dziesiętnego.

Duplikaty nazw nie są odrzucane, a kolejność skanowania katalogów decyduje o tym, która panorama pozostanie dostępna. Zachowuj unikalne nazwy w obrębie katalogu panoram. Nazwy panoram i pokazów slajdów używają oddzielnych list.

# Używanie panoramy

Przeładuj FancyMenu przez **Dostosowanie -> Przeładuj FancyMenu** albo uruchom klienta ponownie. Następnie kliknij prawym przyciskiem myszy tło edytora układu i wybierz [**Tła menu**](./menu-backgrounds) -> **Panorama sześcienna**.
