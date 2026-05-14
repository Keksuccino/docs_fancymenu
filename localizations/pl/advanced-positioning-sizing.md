---
title: Zaawansowane pozycjonowanie i rozmiary
description: Jak używać zaawansowanego pozycjonowania i rozmiarów elementów.
---

# Zaawansowane pozycjonowanie i rozmiary

Zaawansowane pozycjonowanie/ustawianie rozmiaru pozwala Ci mieć **pełną kontrolę nad pozycją i rozmiarem Twoich elementów**. To bardzo potężne rozwiązanie, ale też **znacznie bardziej czasochłonne** niż korzystanie z automatycznego skalowania i pozycjonowania FancyMenu.

> Jeśli chcesz tylko, aby elementy lepiej skalowały się wraz z **skalą GUI** Minecrafta, zaleca się zamiast tego użycie globalnego **automatycznego skalowania** układu. Można je włączyć, najpierw wymuszając skalę GUI w menu, które otwiera się po kliknięciu prawym przyciskiem myszy tła edytora, a następnie włączając **Auto-Scaling** w tym samym menu.
{.is-warning}


# Przełączanie trybu zaawansowanego pozycjonowania/rozmiarów

Aby **włączyć** zaawansowane pozycjonowanie/ustawianie rozmiaru dla elementu, **kliknij go prawym przyciskiem myszy** i wybierz **Advanced Positioning** lub **Advanced Sizing**.
Element automatycznie przełączy się w tryb zaawansowany, gdy ustawisz zaawansowaną wartość pozycji lub rozmiaru.

Aby to **wyłączyć** i wrócić do normalnego pozycjonowania/ustawiania rozmiaru, **wyczyść wszystkie wartości pozycjonowania/rozmiaru**.

> Gdy element znajduje się w trybie Advanced Sizing/Positioning, zmiana rozmiaru i/lub przesuwanie elementu może być wyłączone lub ograniczone.
{.is-warning}

# Obliczanie pozycji/rozmiarów

Powodem, dla którego zaawansowane pozycjonowanie/ustawianie rozmiaru jest tak potężne, jest możliwość używania **placeholderów** w wartościach pozycji/rozmiaru.

Pozwala to na używanie placeholdera **Calculator** (znajdującego się w kategorii placeholderów **Advanced**) w połączeniu z placeholderami z kategorii **GUI**, takimi jak **Screen Width**, **GUI Scale**, **Element Width** i inne.

> Możesz dodawać placeholdery, klikając przycisk **Placeholders** w prawym górnym rogu edytora tekstu. Jeśli nie widzisz tego przycisku, zawartość, którą chcesz edytować, **nie obsługuje** placeholderów.
{.is-info}

Aby coś obliczyć za pomocą placeholdera **Calculator**, zastąp przykładowe wyrażenie własnym. Możesz używać w wyrażeniu zagnieżdżonych placeholderów, więc możesz tam korzystać m.in. z rozmiaru ekranu, rozmiaru elementu itd.

Na przykład ten placeholder po prostu obliczy `1 + 1` i później wyświetli się jako `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Zmienna `decimal` jest ustawiona na `false`, co jest ważne w przypadku większości obliczeń pozycji/rozmiarów, więc podczas pracy z zaawansowanym pozycjonowaniem/rozmiarami ustawiaj ją zawsze na `false`.

Poniższy kalkulator używa placeholdera **Screen Width** i dzieli go przez `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`
