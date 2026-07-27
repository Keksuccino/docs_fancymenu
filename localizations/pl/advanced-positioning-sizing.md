---
title: Zaawansowane pozycjonowanie i rozmiar
description: Jak korzystać z zaawansowanego pozycjonowania i ustalania rozmiaru elementów.
---
# Zaawansowane pozycjonowanie i rozmiar

Zaawansowane pozycjonowanie i rozmiar daje bezpośrednią kontrolę nad współrzędnymi i wymiarami elementu.

> [!WARNING]
> Aby dopasować do skali GUI, najpierw wypróbuj **Auto-Scaling** dla całego układu. Kliknij prawym przyciskiem myszy tło edytora, wymuś skalę GUI, a następnie włącz **Auto-Scaling** w tym samym menu.


# Włączanie trybu zaawansowanego pozycjonowania/rozmiaru

Aby włączyć zaawansowane pozycjonowanie lub rozmiar dla elementu, **kliknij go prawym przyciskiem myszy** i wybierz **Advanced Positioning** lub **Advanced Sizing**.
Element automatycznie przełączy się w tryb zaawansowany, gdy ustawisz zaawansowaną wartość pozycji lub rozmiaru.

Aby to **wyłączyć** i wrócić do normalnego pozycjonowania/rozmiaru, **wyczyść wszystkie wartości pozycjonowania/rozmiaru**.

> [!WARNING]
> Gdy element znajduje się w trybie Advanced Sizing/Positioning, zmiana rozmiaru i/lub przesuwanie elementu może być wyłączone lub ograniczone.

# Obliczanie pozycji/rozmiarów

Zaawansowane wartości pozycji i rozmiaru obsługują [placeholders](./placeholders).

Dzięki temu możesz łączyć placeholder [**Calculator**](./placeholders#calculator-calc) z placeholderami GUI, takimi jak [**Screen Width**](./placeholders#screen-width-guiwidth), [**GUI Scale**](./placeholders#gui-scale-guiscale) oraz [**Element Width**](./placeholders#element-width-elementwidth).

> [!NOTE]
> Możesz dodać placeholdery, klikając przycisk **Placeholders** w prawym górnym rogu edytora tekstu. Jeśli nie widzisz tego przycisku, treść, którą chcesz edytować, **nie obsługuje** placeholderów.

Aby obliczyć coś za pomocą [placeholdera **Calculator**](./placeholders#calculator-calc), zastąp przykładowe wyrażenie własnym. Zagnieżdżone placeholdery mogą dostarczać wymiary ekranu lub elementu.

Ten przykład zwraca `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Zostaw `decimal` ustawione na `false`, aby wykonywać obliczenia pozycji i rozmiaru w całych pikselach.

Poniższy kalkulator używa [placeholdera **Screen Width**](./placeholders#screen-width-guiwidth) i dzieli go przez `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Advanced Positioning** ignoruje punkt zakotwiczenia elementu i używa lewego górnego rogu ekranu (`X0 Y0`) jako punktu odniesienia. Opcja **Stay on Screen** nadal ma zastosowanie.
