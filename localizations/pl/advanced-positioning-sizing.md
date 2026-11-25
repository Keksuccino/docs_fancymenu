---
title: Zaawansowane pozycjonowanie i rozmiar
description: Jak korzystać z zaawansowanego pozycjonowania i zmiany rozmiaru elementów.
sourceBlobSha: 205b887e844f770856bfd4836ea791e0acdca4b8
---
# Zaawansowane pozycjonowanie i rozmiar

Zaawansowane pozycjonowanie i zmiana rozmiaru zapewniają bezpośrednią kontrolę nad współrzędnymi i wymiarami elementów.

> [!WARNING]
> Aby dostosować układ do skali GUI, najpierw wypróbuj **Automatyczne skalowanie** całego układu. Kliknij prawym przyciskiem myszy tło edytora, wymuś skalę GUI, a następnie włącz **Automatyczne skalowanie** w tym samym menu.


# Włączanie trybu zaawansowanego pozycjonowania/zmiany rozmiaru

Aby włączyć zaawansowane pozycjonowanie lub zmianę rozmiaru elementu, kliknij go **prawym przyciskiem myszy** i wybierz **Zaawansowane pozycjonowanie** lub **Zaawansowana zmiana rozmiaru**.
Element automatycznie przełączy się w tryb zaawansowany po ustawieniu zaawansowanej wartości pozycji lub rozmiaru.

Aby **wyłączyć** ten tryb i wrócić do zwykłego pozycjonowania/zmiany rozmiaru, **wyczyść wszystkie wartości pozycjonowania/zmiany rozmiaru**.

> [!WARNING]
> Gdy element działa w trybie zaawansowanego pozycjonowania/zmiany rozmiaru, zmiana jego rozmiaru i/lub położenia może być wyłączona lub ograniczona.

# Obliczanie pozycji/rozmiarów

Zaawansowane wartości pozycji i rozmiaru obsługują [zmienne zastępcze](/placeholders).

Dzięki temu możesz łączyć zmienną zastępczą [**Kalkulator**](/placeholders#calculator) ze zmiennymi GUI, takimi jak [**Szerokość ekranu**](/placeholders#screen-width), [**Skala GUI**](/placeholders#gui-scale) i [**Szerokość elementu**](/placeholders#element-width).

> [!NOTE]
> Zmienne zastępcze możesz dodawać, klikając przycisk **Zmienne zastępcze** w prawym górnym rogu edytora tekstu. Jeśli nie widzisz tego przycisku, edytowana treść **nie obsługuje** zmiennych zastępczych.

Aby coś obliczyć za pomocą [zmiennej zastępczej **Kalkulator**](/placeholders#calculator), zastąp przykładowe wyrażenie własnym. Zagnieżdżone zmienne zastępcze mogą dostarczać wymiary ekranu lub elementu.

Ten przykład zwraca wartość `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

W przypadku obliczeń pozycji i rozmiaru w pełnych pikselach pozostaw wartość `decimal` ustawioną na `false`.

Poniższy kalkulator korzysta ze zmiennej zastępczej [**Szerokość ekranu**](/placeholders#screen-width) i dzieli ją przez `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Zaawansowane pozycjonowanie** ignoruje punkt zakotwiczenia elementu i używa lewego górnego rogu ekranu (`X0 Y0`) jako początku układu współrzędnych. Opcja **Pozostaw na ekranie** nadal obowiązuje.
