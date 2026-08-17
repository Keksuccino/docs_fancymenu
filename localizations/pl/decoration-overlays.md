---
title: Nakładki dekoracyjne
description: Dodawaj pełnoekranowe nakładki wizualne do menu w edytorze układu FancyMenu.
---
# Nakładki dekoracyjne

Nakładki dekoracyjne to pełnoekranowe efekty renderowane przed elementami menu.

Są przydatne, gdy chcesz dodać menu atmosferę lub ruch bez konieczności tworzenia tych efektów ręcznie.

# Gdzie to znaleźć

Otwórz układ w edytorze układu, następnie kliknij prawym przyciskiem myszy tło edytora i otwórz **Nakładki dekoracyjne**.

# Szybki start

1. Otwórz układ w edytorze układu.
2. Kliknij prawym przyciskiem myszy tło (pusty obszar).
3. Otwórz **Nakładki dekoracyjne**.
4. Wybierz typ nakładki.
5. Ustaw **Pokaż nakładkę** na **Włączone**.
6. Skonfiguruj ustawienia nakładki.
7. Zapisz układ i przetestuj ekran.

# Jak działają typy nakładek

Każdy typ nakładki ma własne podmenu i własny przełącznik **Pokaż nakładkę**.

- Możesz włączyć tylko wybrane typy.
- W jednym układzie możesz łączyć wiele włączonych typów.
- Ustawienia są przypisane do poszczególnych typów nakładek (np. kolor, intensywność, szybkość, gęstość, skala oraz specjalne zachowanie).

> [!INFO]
> Możliwe jest nałożenie na siebie wielu instancji tego samego typu nakładki poprzez użycie wielu układów z włączonym tym samym typem.

# Typy nakładek

- **Opady śniegu**: opady śniegu z opcjonalnym gromadzeniem się śniegu na powierzchniach i przyciskach.
- **Deszcz**: deszcz z opcjonalnymi kałużami, kroplami oraz opcjonalnymi błyskami piorunów.
- **Świetliki**: poruszające się grupy świetlików z możliwością konfiguracji liczby grup, gęstości, rozmiaru i koloru.
- **Lampki na sznurze**: konfigurowalne kombinacje sznurów, kolory świateł, zachowanie związane z wiatrem i migotaniem oraz tryb kolorów świątecznych.
- **Liście**: spadające liście z możliwością konfiguracji kolorów, wiatru, szybkości, skali i gęstości.
- **Fajerwerki**: częste fajerwerki z możliwością konfiguracji liczby, rozmiaru eksplozji i skali.
- **Konfetti**: deszcz konfetti z opcjonalnym trybem konfetti wywoływanego kliknięciem myszy.
- **Buddy**: interaktywny wirtualny zwierzak z głodem, szczęściem, energią, zabawą, aktywnościami, awansowaniem na kolejne poziomy, osiągnięciami i zapisywanym stanem.
- **Przeglądarka**: pełnoekranowa nakładka przeglądarki z ustawieniami adresu URL i multimediów.
- **Shader GLSL**: pełnoekranowa nakładka z niestandardowym shaderem (do tworzenia animowanych lub statycznych efektów opartych na shaderach).

# Wirtualny zwierzak Buddy

Nakładka **Buddy** to wirtualny zwierzak w stylu Tamagotchi, a nie tylko postać wyświetlana na ekranie. Spaceruje wzdłuż dolnej krawędzi ekranu, wyświetla dymki z informacjami o swoich potrzebach, reaguje na interakcje i zachowuje swój stan między sesjami gry.

## Potrzeby i sterowanie

Buddy śledzi cztery wartości z zakresu od `0` do `100`:

- **Głód** zmniejsza się z czasem i jest uzupełniany przez jedzenie.
- **Szczęście** zmniejsza się z czasem i rośnie dzięki opiece, w tym głaskaniu i zabawie.
- **Energia** zmniejsza się podczas czuwania i aktywności, a następnie regeneruje się podczas snu.
- **Zabawa** zmniejsza się z czasem i rośnie podczas zabawy.

Korzystaj z poniższych elementów sterowania myszą oraz ekranu stanu, aby się nim opiekować:

- **Kliknij Buddy lewym przyciskiem myszy**, aby go pogłaskać. Kliknięcie lewym przyciskiem myszy, gdy śpi, budzi go i powoduje niewielki spadek szczęścia.
- **Kliknij Buddy prawym przyciskiem myszy**, aby otworzyć ekran stanu. Karta Statystyki pokazuje wszystkie cztery potrzeby, poziom i PD; karta Osiągnięcia pokazuje postęp osiągnięć.
- Wybierz **Nakarm** na ekranie stanu, a następnie przeciągnij jedzenie do Buddy. Jedzenie uzupełnia głód i szczęście.
- Wybierz **Baw się** na ekranie stanu, a następnie przeciągnij i upuść piłkę. Prędkość rzutu jest obliczana na podstawie ruchu myszy, a Buddy może gonić piłkę, łapać ją, trzymać i bawić się nią.
- Wybierz **Śpij**, gdy przycisk jest dostępny, aby uzupełnić energię. Buddy zasypia również automatycznie, gdy jego poziom energii stanie się krytycznie niski.
- Buddy od czasu do czasu zostawia odchody. **Kliknij odchody lewym przyciskiem myszy**, aby je posprzątać. Pozostawienie na ekranie co najmniej trzech odchodów powoduje ciągły spadek szczęścia, dopóki ich liczba nie spadnie poniżej trzech; maksymalną liczbę odchodów można skonfigurować.

## PD, poziomy i osiągnięcia

Opieka nad Buddym, sprzątanie odchodów, utrzymywanie dobrego poziomu potrzeb oraz realizowanie innych celów zapewniają PD. Buddy zaczyna na poziomie 1 i może osiągnąć poziom 30. Wyższe poziomy stopniowo zmniejszają tempo spadku głodu, szczęścia i energii (maksymalnie o 50% na poziomie 30), a także poprawiają efekty kilku czynności opiekuńczych i zdobywania PD.

Osiągnięcia śledzą interakcje, statystyki, poziom, sesje oraz specjalne cele. Kliknij prawym przyciskiem myszy, aby otworzyć ekran stanu i sprawdzić oba systemy postępów.

## Śmierć i resetowanie zapisu

Opcja **Buddy może umrzeć** jest domyślnie włączona. Jeśli głód lub szczęście pozostaje nieprzerwanie na poziomie `0` przez **10 godzin rzeczywistych**, Buddy umiera i zostaje zastąpiony nagrobkiem. Podniesienie wartości potrzeby z poziomu zero przed upływem tego czasu resetuje licznik tej potrzeby; wyłączenie opcji **Buddy może umrzeć** resetuje oba liczniki.

Aby rozpocząć od nowa po śmierci, kliknij nagrobek lewym przyciskiem myszy. Możesz także w dowolnym momencie użyć opcji **Resetuj zapis Buddy** w ustawieniach nakładki Buddy. Resetowanie usuwa zarówno zapis stanu zwierzaka, jak i osobny zapis poziomów oraz osiągnięć dla tej instancji nakładki.

> [!WARNING]
> Zresetowanie zapisu Buddy trwale usuwa jego potrzeby, poziom, PD, osiągnięcia, liczniki aktywności i zapisany stan odchodów.

## Zapisywanie stanu i dostosowywanie

Stan Buddy jest automatycznie zapisywany mniej więcej co dwie minuty oraz przy zamykaniu jego ekranu. Stan zwierzaka i stan poziomów są przechowywane w osobnych plikach JSON dla każdej instancji nakładki w katalogu `<game-directory>/fancymenu_data/buddy/`. Zobacz [Lokalizacje przechowywania danych](./data-storage-locations), aby zapoznać się z pełną listą ścieżek FancyMenu.

Ustawienia nakładki pozwalają także zastąpić atlas sprite'ów Buddy'ego, przedmioty interakcji, ikony potrzeb, tekstury ekranu stanu oraz nagrobek. Zaawansowane ustawienia statystyk kontrolują tempo spadku wartości, koszty i zyski aktywności, skuteczność opieki, maksymalną liczbę odchodów oraz to, czy śmierć jest włączona.

# Nakładka przeglądarki: interaktywna czy pasywna

Nakładkę przeglądarki można skonfigurować jako przeglądarkę interaktywną albo pasywną warstwę wizualną.

- Ustawienia **Przetwarzaj mysz/klawiaturę** określają, czy sama przeglądarka obsługuje dane wejściowe.
- Ustawienia **Przechwytuj mysz/klawiaturę** określają, czy dane wejściowe są blokowane dla menu znajdującego się za nakładką.

Przykłady praktycznej konfiguracji:

- Interaktywna przeglądarka na pierwszym planie: włącz zarówno **Przetwarzaj**, jak i **Przechwytuj**.
- Warstwa przeglądarki wyłącznie do celów wizualnych: wyłącz **Przetwarzaj** i **Przechwytuj**.

> [!IMPORTANT]
> Nakładka dekoracyjna przeglądarki wymaga moda **[Rinku](https://modrinth.com/mod/rinku)**.
