---
title: Dzielenie na dziewięć części i kafelkowanie
description: Skaluj tekstury z obramowaniem lub powtarzaj bezszwowe tekstury.
---

# Dzielenie na dziewięć części i kafelkowanie

Dzielenie na dziewięć części zachowuje rogi i krawędzie tekstury, jednocześnie rozciągając jej środek. Kafelkowanie powtarza teksturę zamiast ją rozciągać.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Obszary podziału na dziewięć części" style="max-width:500px;height:auto;" />

# Obsługa podziału na dziewięć części

| Obszar | Obsługiwane elementy docelowe |
|---|---|
| Widżety | Tekstury [przycisku](./elements#button) i [suwaka](./elements#slider); [globalne style przycisków i suwaków](./global-customizations#button-visuals) |
| Obrazy i panele | [Elementy obrazu](./elements#image) |
| Paski postępu | [Tekstury wypełnienia i tła](./elements#progress-bar) |
| Podpowiedzi | [Niestandardowe tekstury tła](./elements#tooltip) |

# Konfigurowanie podziału na dziewięć części

1. Ustaw teksturę docelową.
2. Włącz opcję **Nine-Slice**.
3. Ustaw rozmiary obramowania tak, aby odpowiadały stałemu obszarowi krawędzi w źródłowej teksturze.
4. Zmień rozmiar elementu i dostosuj wartości obramowania, jeśli rogi lub krawędzie ulegają zniekształceniu.

Ustawienia przycisku i obrazu używają rozmiarów obramowania X/Y. Paski postępu i podpowiedzi udostępniają oddzielne wartości krawędzi, tam gdzie jest to potrzebne.

# Obsługa kafelkowania

Powtarzane tekstury są dostępne dla:

- [Elementów obrazu](./elements#image).
- [Tła menu obrazu](./menu-backgrounds).
- [Tekstur nagłówka i stopki list przewijanych](./customizing-scrollable-screens).

Włącz **Repeat Texture** na elemencie obrazu lub tle obrazu. W przypadku ekranów przewijanych użyj opcji powtarzania w menu konfiguracji nagłówka/stopki.

Użyj bezszwowej tekstury źródłowej; niedopasowane krawędzie tworzą widoczne linie między kafelkami.

Dzielenie na dziewięć części i powtarzanie to odrębne tryby. Jeśli dla danego elementu docelowego widoczne są obie opcje, wybierz tę, która odpowiada zamierzonemu sposobowi skalowania.
