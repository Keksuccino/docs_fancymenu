---
title: Nakładki dekoracyjne
description: Dodawaj pełnoekranowe nakładki wizualne do menu w edytorze układów FancyMenu.
---
# Nakładki dekoracyjne

Nakładki dekoracyjne to pełnoekranowe efekty renderowane przed elementami menu.

Są przydatne, gdy chcesz dodać do menu atmosferę lub ruch, bez ręcznego tworzenia tych efektów.

# Gdzie to znaleźć

Otwórz układ w edytorze układów, a następnie kliknij prawym przyciskiem myszy tło edytora i otwórz **Nakładki dekoracyjne**.

# Szybki start

1. Otwórz układ w edytorze układów.
2. Kliknij prawym przyciskiem myszy tło (pusty obszar).
3. Otwórz **Nakładki dekoracyjne**.
4. Wybierz typ nakładki.
5. Ustaw **Pokaż nakładkę** na **Włączone**.
6. Skonfiguruj ustawienia nakładki.
7. Zapisz układ i przetestuj ekran.

# Jak działają typy nakładek

Każdy typ nakładki ma własne podmenu i własny przełącznik **Pokaż nakładkę**.

- Możesz włączyć tylko te typy, których chcesz używać.
- Możesz łączyć kilka włączonych typów w jednym układzie.
- Ustawienia są przypisane do danego typu nakładki (na przykład kolor, intensywność, prędkość, gęstość, skala, specjalne zachowanie).

> [!INFO]
> Możliwe jest nakładanie wielu instancji tego samego typu nakładki, używając kilku układów z włączonym tym samym typem.

# Typy nakładek

- **Opad śniegu**: opad śniegu z opcjonalnym gromadzeniem się śniegu na powierzchniach/przyciskach.
- **Opad deszczu**: deszcz z opcjonalnymi kałużami, skapującą wodą i opcjonalnymi błyskami grzmotu.
- **Świetliki**: poruszające się grupy świetlików z konfigurowalną liczbą grup, gęstością, rozmiarem i kolorem.
- **Lampki sznurkowe**: konfigurowalne kombinacje sznurów, kolory świateł, zachowanie na wietrze/migotanie i tryb kolorów świątecznych.
- **Liście**: spadające liście z konfigurowalnymi kolorami, wiatrem, prędkością, skalą i gęstością.
- **Fajerwerki**: częste fajerwerki z konfigurowalną liczbą, rozmiarem eksplozji i skalą.
- **Konfetti**: opad konfetti z opcjonalnym trybem konfetti po kliknięciu myszą.
- **Buddy**: interaktywny wirtualny zwierzak z głodem, szczęściem, energią, zabawą, aktywnościami, poziomami, osiągnięciami i trwałym stanem.
- **Przeglądarka**: pełnoekranowa nakładka przeglądarki z ustawieniami URL i multimediów.
- **Shader GLSL**: pełnoekranowa niestandardowa nakładka shaderowa (do animowanych lub statycznych efektów wizualnych opartych na shaderach).

# Wirtualny zwierzak Buddy

Nakładka **Buddy** to wirtualny zwierzak w stylu Tamagotchi, a nie tylko wizualna postać. Chodzi po dolnej części ekranu, wyświetla dymki myśli dotyczące swoich potrzeb, reaguje na interakcje i zachowuje swój stan między sesjami gry.

## Potrzeby i sterowanie

Buddy śledzi cztery wartości od `0` do `100`:

- **Głód** spada z czasem i jest odnawiany przez jedzenie.
- **Szczęście** spada z czasem i rośnie dzięki opiece, w tym głaskaniu i zabawie.
- **Energia** spada, gdy Buddy nie śpi i podczas aktywności, a następnie regeneruje się podczas snu.
- **Zabawa** spada z czasem i rośnie podczas zabawy.

Użyj tych sterowań myszą oraz ekranu statusu, aby się nim opiekować:

- **Lewy klik na Buddy** go głaszcze. Lewy klik podczas snu budzi go i nakłada niewielką karę do szczęścia.
- **Prawy klik na Buddy** otwiera ekran statusu. Karta Statystyki pokazuje wszystkie cztery potrzeby, poziom i XP; karta Osiągnięcia pokazuje postęp osiągnięć.
- Wybierz **Nakarm** na ekranie statusu, a następnie przeciągnij jedzenie do Buddy. Jedzenie odnawia głód i szczęście.
- Wybierz **Zagraj** na ekranie statusu, a następnie przeciągnij i puść piłkę. Piłka używa ruchu myszy do obliczania prędkości rzutu, a Buddy może ją gonić, łapać, trzymać i bawić się nią.
- Wybierz **Śpij**, gdy przycisk jest dostępny, aby odzyskać energię. Buddy zasypia też automatycznie, gdy jego energia spadnie do krytycznie niskiego poziomu.
- Buddy czasami zostawia po sobie kupę. **Lewy klik na kupę** ją czyści. Pozostawienie na ekranie co najmniej trzech kup jednocześnie stale obniża szczęście, dopóki liczba ta nie spadnie poniżej trzech; maksymalna liczba kup jest konfigurowalna.

## XP, poziomy i osiągnięcia

Opieka nad Buddy, sprzątanie kup, utrzymywanie dobrych wartości potrzeb i osiąganie innych kamieni milowych przyznaje XP. Buddy zaczyna na poziomie 1 i może osiągnąć poziom 30. Wyższe poziomy stopniowo zmniejszają spadek głodu, szczęścia i energii (do 50% na poziomie 30) oraz poprawiają kilka efektów związanych z opieką i XP.

Osiągnięcia śledzą interakcje, statystyki, poziom, sesję oraz specjalne kamienie milowe. Otwórz ekran statusu prawym kliknięciem, aby sprawdzić oba systemy postępu.

## Śmierć i resetowanie zapisu

Opcja **Buddy może umrzeć** jest domyślnie włączona. Jeśli głód lub szczęście pozostają nieprzerwanie na `0` przez **10 rzeczywistych godzin**, Buddy umiera i zostaje zastąpiony nagrobkiem. Podniesienie wartości zerowej potrzeby przed upływem tego czasu resetuje licznik tej potrzeby; wyłączenie opcji **Buddy może umrzeć** czyści oba liczniki.

Aby zacząć od nowa po śmierci, kliknij lewym przyciskiem myszy nagrobek. Możesz też w dowolnym momencie użyć opcji **Resetuj zapis Buddy** w ustawieniach nakładki Buddy. Resetowanie usuwa zarówno zapis stanu zwierzaka, jak i osobny zapis poziomowania/osiągnięć dla tej instancji nakładki.

> [!WARNING]
> Resetowanie zapisu Buddy trwale usuwa jego potrzeby, poziom, XP, osiągnięcia, liczniki aktywności i zapisany stan kupy.

## Trwałość i dostosowanie

Stan Buddy jest zapisywany automatycznie mniej więcej co dwie minuty oraz po zamknięciu jego ekranu. Stan zwierzaka i stan poziomowania są przechowywane w osobnych plikach JSON dla każdej instancji nakładki w `<game-directory>/fancymenu_data/buddy/`. Zobacz [Lokalizacje przechowywania danych](./data-storage-locations), aby uzyskać pełną listę ścieżek FancyMenu.

Ustawienia nakładki pozwalają też zastąpić atlas sprite'ów Buddy, elementy interakcji, ikony potrzeb, tekstury ekranu statusu oraz nagrobek. Zaawansowane ustawienia statystyk kontrolują spadek wartości, koszty i zyski aktywności, skuteczność opieki, maksymalną liczbę kup oraz to, czy śmierć jest włączona.

# Nakładka przeglądarki: interaktywna a pasywna

Nakładkę przeglądarki można skonfigurować zarówno jako interaktywną przeglądarkę, jak i jako pasywną warstwę wizualną.

- Ustawienia **Przetwarzaj mysz/klawiaturę** określają, czy sama przeglądarka obsługuje dane wejściowe.
- Ustawienia **Przejmij mysz/klawiaturę** określają, czy dane wejściowe są blokowane przed menu znajdującym się pod spodem.

Praktyczne przykłady konfiguracji:

- Interaktywna przeglądarka na wierzchu: włącz zarówno **Przetwarzaj**, jak i **Przejmij**.
- Przeglądarka wyłącznie jako warstwa wizualna: wyłącz **Przetwarzaj** i wyłącz **Przejmij**.

> [!IMPORTANT]
> Nakładka dekoracyjna Przeglądarka wymaga moda **MCEF**.
