---
title: Zaawansowane pozycjonowanie i skalowanie
description: Jak używać zaawansowanego pozycjonowania i skalowania elementów.
---
# Zaawansowane pozycjonowanie i skalowanie

Zaawansowane pozycjonowanie/skalowanie pozwala Ci mieć **pełną kontrolę nad pozycją i rozmiarem Twoich elementów**. Jest to bardzo potężne, ale też **znacznie bardziej czasochłonne** niż korzystanie z automatycznego skalowania i pozycjonowania FancyMenu.

> Jeśli chcesz tylko, aby elementy lepiej skalowały się wraz z **skalą GUI** Minecrafta, zaleca się zamiast tego użycie automatycznego skalowania na poziomie układu, które można włączyć, najpierw wymuszając skalę GUI w menu otwieranym po kliknięciu prawym przyciskiem myszy tła edytora, a następnie włączając **Auto-Scaling** w tym samym menu.
{.is-warning}


# Włączanie trybu zaawansowanego pozycjonowania/skalowania

Aby **włączyć** zaawansowane pozycjonowanie/skalowanie dla elementu, **kliknij go prawym przyciskiem myszy** i wybierz **Advanced Positioning** lub **Advanced Sizing**.
Element automatycznie przełączy się w tryb zaawansowany, gdy ustawisz zaawansowaną wartość pozycji lub rozmiaru.

Aby to **wyłączyć** i wrócić do normalnego pozycjonowania/skalowania, **wyczyść wszystkie wartości pozycjonowania/skalowania**.

> Gdy element znajduje się w trybie Advanced Sizing/Positioning, zmiana rozmiaru i/lub przesuwanie elementu może być wyłączone lub ograniczone.
{.is-warning}

# Obliczanie pozycji/rozmiarów

Powodem, dla którego zaawansowane pozycjonowanie/skalowanie jest tak potężne, jest to, że możesz używać **placeholderów** w wartościach pozycji/rozmiaru.

Dzięki temu możesz używać placeholdera **Calculator** (znajdującego się w kategorii placeholderów **Advanced**) w połączeniu z placeholderami z kategorii **GUI**, takimi jak **Screen Width**, **GUI Scale**, **Element Width** i inne.

> Możesz dodawać placeholdery, klikając przycisk **Placeholders** w prawym górnym rogu edytora tekstu. Jeśli nie widzisz tego przycisku, edytowana treść **nie obsługuje** placeholderów.
{.is-info}

Aby coś obliczyć za pomocą placeholdera **Calculator**, zamień przykładowe wyrażenie na własne. Możesz używać zagnieżdżonych placeholderów w wyrażeniu, więc możesz tam korzystać m.in. z rozmiaru ekranu, rozmiaru elementu itd.

Na przykład ten placeholder po prostu obliczy `1 + 1` i później wyświetli się jako `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Zmienna `decimal` jest ustawiona na `false`, co jest ważne w przypadku większości obliczeń pozycji/rozmiarów, więc podczas pracy z zaawansowanym pozycjonowaniem/skalowaniem ustawiaj ją zawsze na `false`.

Poniższy kalkulator używa placeholdera **Screen Width** i dzieli go przez `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> Gdy **Advanced Positioning** jest włączone, **punkt zakotwiczenia** oraz wszelkie inne funkcje elementu związane z pozycją będą **ignorowane**. Advanced Positioning zawsze używa lewego górnego rogu (X0 Y0) jako punktu początkowego, tak jak robi to domyślna logika GUI Minecrafta. Jedynym ustawieniem, które Advanced Positioning uwzględnia, jest **Stay on Screen**.
