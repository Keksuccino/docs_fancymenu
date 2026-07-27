---
title: Efekt paralaksy
description: Przesuwaj tła i elementy za pomocą kursora myszy.
---

# Efekt paralaksy

Paralaksa przesuwa tło lub element na podstawie ruchu myszy, aby stworzyć wizualną głębię.

# Tło menu z obrazem

1. Kliknij prawym przyciskiem myszy tło edytora układu.
2. Otwórz [**Tła menu**](./menu-backgrounds) -> **Obraz**.
3. Ustaw źródło obrazu.
4. Włącz **Efekt paralaksy**.
5. Ustaw wartości intensywności X i Y.
6. Opcjonalnie włącz **Odwróć ruch paralaksy**.

Wartości X i Y kontrolują niezależnie ruch poziomy i pionowy. Używaj wartości od `0.0` (brak) do `1.0` (maksimum).

# Elementy

1. Kliknij prawym przyciskiem myszy [element](./elements).
2. Włącz **Efekt paralaksy**.
3. Ustaw **Intensywność paralaksy X** i **Intensywność paralaksy Y**.
4. Opcjonalnie odwróć ruch.

Używaj niższej intensywności dla dalszych warstw i wyższej dla warstw na pierwszym planie. Duże różnice lub odwrócone warstwy tworzą silniejszy efekt głębi.

# Rozwiązywanie problemów

- Intensywność `0` nie powoduje ruchu na tej osi.
- **Przesuwanie szerokich obrazów od lewej do prawej** koliduje z paralaksą tła i musi być wyłączone.
- Bardzo mały ruch może wyglądać na schodkowy, ponieważ pozycje interfejsu GUI używają całych pikseli.
