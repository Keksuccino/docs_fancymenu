---
title: Płynne wczytywanie świata
description: Użyj widoku świata jako tła kolejnego ekranu wczytywania.
sourceBlobSha: 2b8e960b11ea70fca33b317a7c14815ce5844e13
---

# Płynne wczytywanie świata

Funkcja płynnego wczytywania świata używa ostatniego widoku świata lub serwera jako tła kolejnego ekranu wczytywania.

Włącz ją w sekcji [**Dostosowywanie -> Globalne dostosowania**](/global-customizations) -> **Płynne wczytywanie świata**.

# Jak to działa

- FancyMenu okresowo zapisuje bieżący kadr, gdy przebywasz w śledzonym świecie lub na śledzonym serwerze.
- Po wyjściu zapisywany jest najnowszy zrzut.
- Każdy świat i serwer ma własny plik PNG o nazwie będącej skrótem.
- FancyMenu wczytuje wstępnie do pięciu najnowszych zrzutów ze światów i pięciu najnowszych zrzutów z serwerów.
- Dla danego celu nic nie jest wyświetlane, dopóki nie zostanie zapisany pierwszy zrzut.

Zrzuty są przechowywane w:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Zrzuty ekranu mogą zawierać wszystko, co było widoczne w świecie w chwili ich wykonania. Wyłączenie płynnego wczytywania świata zatrzymuje wykonywanie zrzutów i korzystanie z nich, ale nie usuwa istniejących plików PNG. Niechciane zrzuty usuń z tego katalogu, gdy gra jest zamknięta.
