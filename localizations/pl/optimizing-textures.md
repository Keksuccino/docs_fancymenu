---
title: Optymalizacja Tekstur
description: Jak optymalizować tekstury dla FancyMenu.
---

# Optymalizacja tekstur dla FancyMenu

FancyMenu używa dostarczonych przez Ciebie tekstur w takiej postaci, w jakiej są, co oznacza, że **nie** kompresuje, nie zmniejsza ani nie powiększa plików graficznych. Aby mieć pewność, że Twoje menu będą wyglądać ostro i działać wydajnie, ważne jest optymalizowanie tekstur podczas korzystania z nich w interfejsie.

# Najważniejsze wskazówki dotyczące optymalizacji tekstur

Poniższe wskazówki to najważniejsze podstawowe kroki, o których warto pamiętać podczas pracy z teksturami w FancyMenu.

## 1. Używaj odpowiedniej rozdzielczości
- **Unikaj obrazów w niskiej rozdzielczości**: Jeśli obraz jest zbyt mały i zostanie rozciągnięty do większego obszaru, może wyglądać na rozmyty.
- **Unikaj przesady z wysoką rozdzielczością**: Bardzo duże tekstury wyświetlane w małym rozmiarze mogą również wyglądać na zniekształcone lub „dziwne” i mogą niepotrzebnie obciążać wydajność.

> 📌 **Wskazówka:** Używaj tekstur w rozdzielczości zbliżonej do tej, w jakiej będą wyświetlane w menu.
{.is-info}

## 2. Zachowaj proporcje obrazu
- Podczas skalowania zawsze zachowuj proporcje obrazu.
- Nierównomierne rozciąganie obrazu może prowadzić do artefaktów wizualnych i słabego wyglądu.

> 📌 **Wskazówka:** Możesz kliknąć prawym przyciskiem myszy elementy obrazu i wybrać **Przywróć proporcje obrazu**, aby dopasować ich rozmiar do właściwych proporcji, a następnie podczas dalszej ręcznej zmiany rozmiaru przytrzymaj **SHIFT**, aby skalowanie respektowało proporcje elementu.
{.is-info}

## 3. Rozważ Nine-Slicing i kafelkowanie
- W przypadku skalowalnych elementów interfejsu (takich jak panele lub przyciski) używaj funkcji FancyMenu [Nine-Slicing & Tiling](/nine-slicing-and-tiling).
- Dzięki temu krawędzie tekstur pozostaną ostre po zmianie rozmiaru.
