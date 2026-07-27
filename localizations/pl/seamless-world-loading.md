---
title: Płynne ładowanie świata
description: Użyj ostatniego widoku świata jako kolejnego tła ładowania.
---

# Płynne ładowanie świata

Płynne ładowanie świata używa ostatniego widoku świata lub serwera jako kolejnego tła ekranu ładowania.

Włącz tę funkcję w [**Dostosowywanie -> Globalne dostosowania**](./global-customizations) -> **Płynne ładowanie świata**.

# Jak to działa

- FancyMenu okresowo przechwytuje bieżącą klatkę, gdy znajdujesz się w śledzonym świecie lub na serwerze.
- Najnowszy zrzut jest zapisywany po wyjściu.
- Każdy świat i każdy serwer ma własną haszowaną nazwę pliku PNG.
- FancyMenu wstępnie ładuje do pięciu najnowszych zrzutów świata i pięciu najnowszych zrzutów serwera.
- Dla danego celu nic nie jest wyświetlane, dopóki nie zostanie zapisany jego pierwszy zrzut.

Zrzuty są przechowywane w:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Zrzuty ekranu mogą zawierać wszystko, co było widoczne w świecie w momencie wykonania. Wyłączenie funkcji Płynne ładowanie świata zatrzymuje przechwytywanie i używanie zrzutów, ale nie usuwa istniejących plików PNG. Niechciane zrzuty usuń z tego katalogu, gdy gra jest zamknięta.
