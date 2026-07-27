---
title: Optymalizacja tekstur
description: Jak optymalizować tekstury dla FancyMenu.
---

# Optymalizacja tekstur dla FancyMenu

FancyMenu używa dostarczonych przez Ciebie tekstur bez zmian, co oznacza, że **nie** kompresuje, nie zmniejsza ani nie powiększa plików graficznych. Aby Twoje menu wyglądały wyraźnie i działały wydajnie, ważne jest optymalizowanie tekstur podczas używania ich w interfejsie użytkownika.

# Najważniejsze wskazówki dotyczące optymalizacji tekstur

Poniższe wskazówki to najważniejsze podstawowe kroki, o których warto pamiętać podczas pracy z teksturami w FancyMenu.

## 1. Używaj odpowiedniej rozdzielczości
- **Unikaj obrazów o zbyt niskiej rozdzielczości**: Jeśli obraz jest zbyt mały i zostanie rozciągnięty do większego obszaru, może wyglądać na rozmazany.
- **Unikaj przesady z wysoką rozdzielczością**: Bardzo duże tekstury wyświetlane w małym rozmiarze mogą również wyglądać na zniekształcone lub „dziwne” i mogą niepotrzebnie obciążać wydajność.

> [!NOTE]
> 📌 **Wskazówka:** Używaj tekstur w rozdzielczości odpowiadającej lub zbliżonej do tej, w jakiej będą wyświetlane w menu.

## 2. Zachowuj proporcje obrazu
- Podczas skalowania zawsze zachowuj proporcje obrazu.
- Nierównomierne rozciąganie obrazu może prowadzić do artefaktów wizualnych i słabego wyglądu.

> [!NOTE]
> 📌 **Wskazówka:** Możesz kliknąć prawym przyciskiem myszy elementy obrazu i wybrać **Przywróć proporcje obrazu**, aby ustawić ich właściwe proporcje, a następnie podczas dalszego ręcznego skalowania przytrzymaj **SHIFT**, aby skalowanie respektowało proporcje elementu.

## 3. Weź pod uwagę nine-slicing i kafelkowanie
- W przypadku skalowalnych elementów UI (takich jak panele lub przyciski) korzystaj z funkcji FancyMenu [Nine-Slicing & Tiling](/nine-slicing-and-tiling).
- Dzięki temu krawędzie tekstur pozostaną ostre po zmianie rozmiaru.
