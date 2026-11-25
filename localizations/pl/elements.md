---
title: Elementy
description: >-
  Wszystkie typy elementów FancyMenu, ich przeznaczenie i sposób dodawania ich
  do układu.
sourceBlobSha: 0e457baa99cbf7103634385145b27f07c22e6e51
---

# Elementy

Elementy to części układu: przyciski, teksty, obrazy, suwaki, muzyka i nie tylko. Na tej stronie znajdziesz wszystkie typy elementów oraz ich najważniejsze ustawienia.

> [!TIP]
> Przyciski i inne elementy, które są domyślnie dostępne na ekranie, to [elementy Vanilla](/vanilla-elements). Możesz je również przenosić, zmieniać i ukrywać.

# Dodawanie elementów

1. W edytorze układu kliknij prawym przyciskiem myszy wolne miejsce, a następnie kliknij **Nowy element**. Ta sama lista znajduje się na pasku menu w **Element -> Nowy**.
2. Kliknij typ elementu. Najedź kursorem na typ, aby zobaczyć, do czego służy.

Element pojawi się w miejscu kliknięcia. Przeciągnij go, aby go przenieść, przeciągnij jego krawędzie, aby zmienić rozmiar, a następnie kliknij go prawym przyciskiem myszy, aby otworzyć jego ustawienia.

<img width="800" alt="Kliknięcie prawym przyciskiem myszy w edytorze układu, dodanie przycisku przez opcję Nowy element, przeniesienie go i poszerzenie oraz ustawienie etykiety Dołącz do serwera" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_add_element.gif?raw=true">

Więcej informacji o zaznaczaniu, przenoszeniu, kopiowaniu i usuwaniu elementów oraz wszystkie skróty klawiszowe edytora znajdziesz na stronie [Edytor układu](/layout-editor). Aby elementy zachowywały swoje położenie przy każdym rozmiarze okna, przeczytaj [Pozycjonowanie elementów](/positioning-elements). Informacje o wyświetlaniu elementów przed innymi lub za nimi znajdziesz na stronie [Warstwy i grupy](/layout-editor#layers-and-groups).

# Ustawienia wspólne dla wszystkich elementów

Każdy element ma w menu dostępnym po kliknięciu prawym przyciskiem myszy poniższe ustawienia, obok ustawień właściwych dla jego typu:

| Ustawienie | Działanie |
|---|---|
| **Punkt zakotwiczenia** | Określa, do czego przytwierdzony jest element, na przykład do rogu ekranu lub innego elementu. Zobacz [Pozycjonowanie elementów](/positioning-elements). |
| **Zaawansowane pozycjonowanie** i **Zaawansowane określanie rozmiaru** | Obliczają położenie i rozmiar, na przykład przy użyciu [symboli zastępczych](/placeholders). Zobacz [Zaawansowane pozycjonowanie i określanie rozmiaru](/advanced-positioning-sizing). |
| **Wymagania dotyczące wyświetlania** i **Wczytaj tylko raz na sesję** | Wyświetlają element tylko po spełnieniu [wymagań](/conditions) albo tylko raz po uruchomieniu gry. Zobacz [Widoczność elementów](/element-visibility). |
| **Opóźnij pojawienie się** i **Opóźnij zniknięcie** | Odczekują kilka sekund, zanim element się pojawi lub zniknie. Zobacz [Widoczność elementów](/element-visibility#delaying-elements). |
| **Pojawianie się/znikanie przez zanikanie** i **Nieprzezroczystość** | Stopniowo pokazują lub ukrywają element albo sprawiają, że staje się przezroczysty. Zobacz [Widoczność elementów](/element-visibility#fading-in-and-out). |
| **Obrót**, **Pochylenie w pionie** i **Pochylenie w poziomie** | Obracają i pochylają element. Zobacz [Obracanie i pochylanie elementów](/rotating-elements). |
| **Efekt paralaksy** | Lekko przesuwa element wraz z ruchem myszy. Zobacz [Efekt paralaksy](/parallax). |
| **Kopiuj identyfikator elementu** | Kopiuje identyfikator używany przez akcje, symbole zastępcze i inne elementy do odnajdywania tego elementu. Zobacz [Identyfikatory elementów](/element-identifiers). |
| **Nazwa wyświetlana w edytorze** | Nazwa elementu na liście warstw. |
| **Eksportuj dla AI** | Zamienia element na tekst dla [asystentów AI](/export-for-ai). |

# Wszystkie elementy

Wszystkie elementy dostępne w FancyMenu, uporządkowane według przeznaczenia.

## Przyciski i pola wprowadzania danych

### Przycisk

Przycisk, który po kliknięciu uruchamia [skrypt akcji](/action-scripts), na przykład dołączający do serwera, otwierający stronę internetową lub inne menu.

<img width="396" alt="Dwa przyciski z etykietami Dołącz do serwera i Otwórz wiki" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_button.png?raw=true">

- **Edytuj skrypt akcji**: określa działanie przycisku po kliknięciu.
- **Etykieta** i **Etykieta po najechaniu**: tekst przycisku oraz tekst wyświetlany po najechaniu na niego kursorem. Oba pola obsługują [symbole zastępcze](/placeholders) i [formatowanie tekstu](/text-formatting).
- **Wyrównanie etykiety**: umieszcza etykietę po **lewej**, **środku** lub **prawej** stronie przycisku. Etykiety, które są zbyt szerokie, przewijają się w obie strony, niezależnie od wyrównania.
- **Skala etykiety**, **Podstawowy kolor etykiety**, **Kolor etykiety po najechaniu**, **Cień etykiety** i **Podkreśl etykietę po najechaniu**: określają rozmiar, kolory i cień etykiety.
- **Tekstury przycisku** i **Tekstury ikony przycisku**: własne obrazy przycisku i umieszczonej na nim ikony dla przycisków w stanie zwykłym, po najechaniu i nieaktywnych. Informacje o teksturach, które dobrze skalują się w różnych rozmiarach, znajdziesz na stronie [Dzielenie na dziewięć części i kafelkowanie](/nine-slicing-and-tiling).
- **Dźwięk po najechaniu**, **Dźwięk po zdjęciu kursora** i **Dźwięk kliknięcia**: dźwięki odtwarzane przez przycisk.
- **Podpowiedź**: tekst wyświetlany po najechaniu kursorem na przycisk.
- **Steruj stanem aktywności**: [wymagania](/conditions), które trzeba spełnić, aby można było kliknąć przycisk. Gdy nie są spełnione, przycisk jest wyszarzony.
- **Tryb szablonu**: nadaje innym przyciskom i suwakom na ekranie wygląd tego przycisku. Zobacz [Szablony przycisków i suwaków](/button-slider-templates).

### Suwak

Suwak, który gracze przeciągają, aby wybrać wartość. Przy każdej zmianie wartości uruchamia swój skrypt akcji.

<img width="436" alt="Suwak Głośność muzyki ustawiony na 70% oraz suwak Poziom trudności ustawiony na Normalny" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_slider.png?raw=true">

- **Typ suwaka**:
  - **Lista wartości**: przechodzi kolejno przez teksty z pola **Wartości listy**, po jednym w wierszu. Opcja **Wartości z listy zmiennej** pobiera je zamiast tego ze [zmiennej listowej](/variables#text-and-list-variables).
  - **Zakres liczb całkowitych**: liczby całkowite od **Minimalnej wartości zakresu** do **Maksymalnej wartości zakresu**.
  - **Zakres liczb dziesiętnych**: działa tak samo, ale dla liczb dziesiętnych. **Miejsce zaokrąglenia** określa liczbę cyfr po przecinku; `-1` oznacza brak zaokrąglania.
- **Etykieta suwaka**: jej tekst. `$$value` wyświetla bieżącą wartość.
- **Edytuj skrypt akcji**: uruchamia się po zmianie wartości. `$$value` oznacza nową wartość.
- **Wstępnie wybrana wartość**: wartość początkowa suwaka. Ustaw ją na wartość, którą suwak zmienia, aby po otwarciu ekranu wyświetlana była prawidłowa wartość.

Na przykład suwak głośności typu **Zakres liczb całkowitych** od `0` do `100` ma etykietę `Głośność muzyki: $$value%` i akcję [**Ustaw wartość zmiennej (zmienna FM)**](/action-scripts#set-variable-value-fm-variable) z następującą wartością:

```
music_volume:$$value
```

Jego **Wstępnie wybrana wartość** to `$$music_volume`, dzięki czemu suwak zaczyna od ostatniej wartości wybranej przez gracza.

Suwaki mają takie same ustawienia etykiety, tekstury, dźwięku, podpowiedzi i **Steruj stanem aktywności** jak przyciski. Dzięki opcji **Wyrównanie etykiety** ich etykiety również można umieścić po lewej lub prawej stronie.

### Pole wyboru

Pole, które gracze mogą zaznaczyć lub odznaczyć. Po każdej zmianie uruchamia swój skrypt akcji.

<img width="588" alt="Zaznaczone pole wyboru obok tekstu Pokaż wskazówki na ekranie tytułowym" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_checkbox.png?raw=true">

- `$$value` w skrypcie akcji i wymaganiach **Steruj stanem aktywności** przyjmuje wartość `true` lub `false`.
- **Tryb zmiennej** i **Połącz ze zmienną**: pole wyboru wyświetla wartość [zmiennej](/variables) i zapisuje w niej `true` lub `false`. Jeśli jest połączone ze zmienną listową, `true` lub `false` staje się jej jedynym wpisem.
- Bez trybu zmiennej pole wyboru samodzielnie zapamiętuje swój stan, osobno dla każdego [profilu](/profiles).
- **Tekstury**: własne obrazy pola i znacznika wyboru.

Pola wyboru mają takie same ustawienia podpowiedzi, dźwięku i **Możliwość nawigacji** jak przyciski.

### Pole tekstowe

Pole, w którym gracze mogą wpisywać tekst, na przykład adres serwera lub nazwę.

<img width="456" alt="Pole tekstowe z wpisanym play.example.net oraz puste pole z szarą podpowiedzią Twoja nazwa gracza" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_input_field.png?raw=true">

- **Połącz ze zmienną**: wpisany tekst trafia do [zmiennej](/variables), a pole wyświetla jej wartość. Jeśli pole jest połączone ze zmienną listową, wpisany tekst zastępuje całą listę.
- **Typ wprowadzanych danych**: **Tekst**, **Tylko liczby**, **Tylko liczby dziesiętne** lub **URL**. Nie można wpisywać innych znaków.
- **Tekst podpowiedzi** i **Kolor tekstu podpowiedzi**: tekst wyświetlany, gdy pole jest puste.
- **Maksymalna długość tekstu**: określa, ile znaków można wpisać.
- **Kolor tła**, **Kolor obramowania**, **Promień zaokrąglenia obramowania** i **Kolor tekstu**: określają wygląd pola.

Na przykład pole połączone ze zmienną `server_address` oraz przycisk z akcją [**Dołącz do serwera**](/action-scripts#join-server) i wartością `$$server_address` pozwalają graczom dołączyć do dowolnego serwera.

Jeśli nie używasz zmiennej, tekst można odczytać za pomocą symbolu zastępczego [**Wartość pola tekstowego**](/placeholders#text-input-field-value), a zmienić go za pomocą akcji [**Ustaw wartość pola tekstowego**](/action-scripts#set-text-input-field-value).

## Teksty i podpowiedzi

### Tekst

Tekst o dowolnej długości — od krótkiej etykiety po przewijane zasady lub informacje o aktualizacji — obsługujący [Markdown](/text-formatting) i [symbole zastępcze](/placeholders).

<img width="636" alt="Element Tekst z informacjami o aktualizacji: nagłówkiem i listą z jednym pogrubionym fragmentem" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_text.png?raw=true">

- **Tryb źródła**: wpisz tekst lub wczytaj go z pliku albo strony internetowej.
- Możesz wybrać wygląd początkowy i włączyć przewijanie, gdy tekst jest większy niż element.
- **Tło**: ciemny panel za tekstem. Wyłącz go opcją **Pokaż tło** lub użyj własnej tekstury.

Więcej informacji znajdziesz na stronie [Tekst w menu](/text-in-menus).

### Podpowiedź

Pole tekstowe przypominające podpowiedzi w grze, obsługujące [Markdown](/text-formatting) i [symbole zastępcze](/placeholders).

<img width="712" alt="Przycisk Potrzebujesz pomocy? z widoczną obok podpowiedzią" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_tooltip.png?raw=true">

- Jest wyświetlana w ustawionym miejscu albo przy kursorze, jeśli włączysz opcję **Podążaj za kursorem**.
- **Wymagania dotyczące wyświetlania** określają, kiedy się pojawi, na przykład po spełnieniu warunku [**Kursor nad elementem**](/conditions#is-element-hovered) dla przycisku.
- **Tło podpowiedzi**: własna tekstura zamiast ciemnego pola.

Więcej informacji znajdziesz na stronie [Tekst w menu](/text-in-menus).

### Tekst powitalny

Żółty tekst z ekranu tytułowego, który możesz zastąpić własnymi tekstami.

<img width="392" alt="Żółty tekst powitalny o treści Sezon 3 już dostępny!" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_splash_text.png?raw=true">

- **Tryb źródła**: domyślne teksty powitalne, własny tekst lub losowy wiersz z pliku tekstowego.
- **Odbijanie**, **Skala**, **Obrót**, **Kolor tekstu** i **Cień**: określają wygląd.
- **Odśwież przy wczytaniu ekranu**: wybiera nowy tekst powitalny za każdym razem, gdy ekran zostanie otwarty.

Więcej informacji znajdziesz na stronie [Tekst powitalny](/splash-text).

## Obrazy i multimedia

### Obraz

Obraz z plików, strony internetowej lub zasobów gry. Obsługiwane są również obrazy animowane.

<img width="608" alt="Element Obraz wyświetlający logo Minecrafta" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_image.png?raw=true">

- **Źródło obrazu**: obraz. Obsługiwane pliki wymieniono na stronie [Obrazy](/images).
- **Zachowaj proporcje**: zmienia szerokość, aby obraz nie był rozciągnięty.
- **Tekstura z podziałem na dziewięć części** i **Powtarzaj teksturę**: pozwalają skalować ramki bez rozciągania ich krawędzi albo kafelkować obraz. Zobacz [Dzielenie na dziewięć części i kafelkowanie](/nine-slicing-and-tiling).
- **Odcień obrazu [HEX]**: zmienia kolor obrazu.
- **Promień zaokrąglenia narożników**: zaokrągla narożniki.

### Pokaz slajdów

Wyświetla kolejno obrazy z pokazu slajdów. Pokazy slajdów tworzy się w folderze `config/fancymenu/slideshows/`. Zobacz [Pokazy slajdów](/slideshows).

- **Pokaz slajdów**: wybierz pokaz, który ma być wyświetlany.
- **Zachowaj proporcje**: zmienia szerokość, aby obrazy nie były rozciągnięte.

### Wideo

Odtwarza plik wideo, na przykład zwiastun lub animowane tło.

> [!IMPORTANT]
> Wideo wymaga modów Watermedia V3 i Watermedia Binaries V3. Zobacz [Wideo](/video).

- **Źródło wideo**: plik wideo, link internetowy lub zasób gry.
- **Odtwarzaj w pętli**, **Głośność** i **Kanał dźwięku**: określają sposób odtwarzania.
- **Odtwarzaj wideo w edytorze układu**: określa, czy wideo ma być odtwarzane także podczas edycji.
- Akcje takie jak [**Przełącz stan wstrzymania elementu wideo**](/action-scripts#toggle-video-element-paused-state) pozwalają wstrzymać odtwarzanie, przejść do wybranego momentu lub zmienić głośność.

**Wideo [Rinku]** to starszy element wideo, który wymaga moda Rinku. Nadal działa w starych układach, ale nie jest dostępny w menu **Nowy element**.

### Shader GLSL

Uruchamia własny shader GLSL w elemencie, na przykład animowane kolory lub efekty z Shadertoy.

<img width="576" alt="Element Shader GLSL wyświetlający kolorowy gradient" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_glsl_shader.png?raw=true">

- **Źródło shadera**: kod shadera. Shadery Shadertoy zawierające `mainImage` działają bez zmian.
- **Tryb kompilacji**: **Auto**, **Shadertoy** lub **Direct Fragment**.
- **Źródło bufora A** do **Źródła bufora D**: dodatkowe etapy przetwarzania dla shaderów korzystających z buforów.

Informacje o tworzeniu shaderów znajdziesz na stronie [API shaderów GLSL](/glsl-shader-api).

### Przeglądarka

Wyświetla na żywo stronę internetową, na przykład mapę serwera lub stronę wiki.

> [!IMPORTANT]
> Przeglądarka wymaga moda [Rinku](https://modrinth.com/mod/rinku) ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku)).

- **URL**: adres strony internetowej.
- **Interaktywność**: pozwala graczom klikać, przewijać i wpisywać tekst. W edytorze układu przeglądarka nigdy nie jest interaktywna.
- **Wycisz przeglądarkę**, **Głośność audio/wideo**, **Odtwarzaj wideo w pętli** i **Ukryj sterowanie wideo**: ustawienia multimediów na stronie.

Aby wczytać plik HTML z folderu `config/fancymenu/assets/`, rozpocznij adres od `file:///`:

```
file:///config/fancymenu/assets/changelog.html
```

W systemie Linux użyj zamiast tego symbolu zastępczego [**Bezwzględna ścieżka do pliku/folderu**](/placeholders#absolute-filefolder-path):

```
file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/changelog.html"}}
```

Strony internetowe mogą uruchamiać akcje i odczytywać symbole zastępcze: [API JavaScript przeglądarki](/browser-api).

## Kształty, przedmioty i modele

### Prostokąt

Prostokąt w jednym kolorze, na przykład panel za tekstem.

<img width="536" alt="Ciemny, półprzezroczysty panel z zaokrąglonymi rogami i rozmytym tłem, zawierający zasady serwera" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_rectangle_shape.png?raw=true">

- **Kolor**: kolor w formacie HEX. Dwie dodatkowe cyfry określają przezroczystość, na przykład `#101828C8`.
- **Promień zaokrąglenia narożników**: zaokrągla wszystkie narożniki albo każdy z osobna.
- **Rozmycie** i **Intensywność rozmycia**: rozmywają tło za elementem.

### Okrąg

Okrąg lub owal w jednym kolorze, na przykład kontrolka stanu.

<img width="428" alt="Zielona kropka obok tekstu Przetrwanie: online i czerwona kropka obok tekstu Kreatywny: offline" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_circle_shape.png?raw=true">

- **Kolor**, **Rozmycie** i **Intensywność rozmycia**: działają tak samo jak w przypadku prostokąta.
- **Okrągłość**: wartość `2` oznacza okrąg. Większe wartości nadają kształtowi bardziej kwadratowy wygląd, a mniejsze — bardziej spiczasty.

### Przedmiot

Wyświetla przedmiot z Minecrafta lub moda, tak jak w ekwipunku.

<img width="460" alt="Zaklęty diamentowy miecz, 16 jabłek, złote jabłko i totem nieśmiertelności" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_item.png?raw=true">

- **Klucz przedmiotu**: przedmiot, na przykład `minecraft:diamond_sword`.
- **Liczba przedmiotów**, **Nazwa przedmiotu**, **Opis przedmiotu** i **Zaklęty**: działają tak jak w przypadku prawdziwego przedmiotu.
- **Pokaż podpowiedź przedmiotu**: wyświetla podpowiedź przedmiotu po najechaniu na niego kursorem.
- **Niestandardowe dane NBT**: dodatkowe dane przedmiotu, zapisane w formacie takim jak fragment polecenia `/give` umieszczony bezpośrednio po przedmiocie.

### Model bloku/przedmiotu JSON

Wyświetla trójwymiarowy model bloku lub przedmiotu z zasobów gry albo z własnego pliku JSON.

<img width="296" alt="Stół rzemieślniczy w 3D" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_json_model.png?raw=true">

- **Model**: **Źródło modelu**, na przykład `minecraft:models/block/crafting_table.json`.
- **Tekstura**: zastępuje teksturę modelu własną.
- **Transformacja**: skaluje, obraca i przesuwa model.
- **Oświetlenie**: opcja **Odcień światła [HEX]** zmienia kolor oświetlenia modelu.

### Postać gracza

Wyświetla trójwymiarową postać gracza, na przykład postać danego gracza na ekranie tytułowym.

<img width="360" alt="Nowy element Postać gracza z domyślną skórką, zwrócony w prawo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_player_entity.png?raw=true">

> [!IMPORTANT]
> Postacie graczy wymagają moda Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Bez niego zamiast postaci wyświetli się błąd.

- **Kopiuj postać gracza**: wyświetla postać osoby grającej w grę, wraz z jej skórką i nazwą.
- **Nazwa gracza**, **Tekstura skórki** i **Tekstura peleryny**: pozwalają wybrać inną postać lub skórkę.
- **Poza postaci**, **Głowa podąża za kursorem** i **Tułów podąża za kursorem**: określają postawę i kierunek patrzenia postaci.
- **Zbroja i narzędzia**, **Papuga**, **Czy małe** i **Pokaż nazwę gracza**: określają, co postać nosi i co jest wyświetlane.

Więcej informacji znajdziesz na stronie [Postacie graczy](/player-entities). Informacje o wyświetlaniu samej głowy znajdziesz na stronie [Głowy graczy](/player-heads).

### Pasek postępu

Wypełniający się pasek, na przykład pasek wczytywania.

<img width="496" alt="Pasek postępu wypełniony w 65%, pod tekstem Wczytywanie świata... 65%" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_progress_bar.png?raw=true">

- **Źródło wartości postępu**: określa stopień wypełnienia. Możesz użyć tu [symboli zastępczych](/placeholders), na przykład [**Postęp wczytywania świata**](/placeholders#world-loading-progress) na ekranie wczytywania świata.
- **Tryb wartości postępu**: **PROCENTY (0-100)** lub **LICZBA ZMIENNOPRZECINKOWA (0.0-1.0)**.
- **Kierunek**: określa, w którą stronę pasek się wypełnia.
- **Kolor paska** i **Kolor tła** albo **Tekstura paska** i **Tekstura tła**.
- **Płynna animacja wypełniania**: płynnie przechodzi do nowych wartości zamiast przeskakiwać.
- **Użyj postępu jako punktu zakotwiczenia elementu**: elementy zakotwiczone do paska przesuwają się wraz z końcem wypełnionej części.

## Narzędzia układu

### Obszar przewijania

Zawiera inne elementy i umożliwia ich przewijanie, na przykład listę serwerów lub długą stronę z informacjami.

<img width="800" alt="Trzy obszary przewijania układające przyciski i przedmioty w stos, siatkę oraz układ przepływowy" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

- Przeciągnij elementy do obszaru w edytorze układu. Można dodawać tylko elementy niestandardowe, nie elementy Vanilla.
- **Układ**: rozmieść elementy samodzielnie albo pozwól obszarowi ułożyć je w stos, siatkę lub układ przepływowy.
- **Tło**: ciemny panel za obszarem. Wyłącz go opcją **Pokaż tło** lub użyj własnej tekstury.

Wszystkie informacje znajdziesz na stronie [Obszary przewijania](/scrollable-areas).

### Uchwyt

Obszar, który gracze mogą chwycić i przesuwać poza edytorem. Zakotwiczone do niego elementy przesuwają się razem z nim, dzięki czemu można na przykład przenosić cały panel informacyjny. Poza edytorem uchwyt jest niewidoczny.

Opcja **Zapisz przesunięcie użytkownika** zachowuje nowe położenie po zamknięciu ekranu i ponownym uruchomieniu gry. Więcej informacji znajdziesz na stronie [Uchwyt](/dragger).

### Animator elementów

Przesuwa i zmienia rozmiar innych elementów za pomocą klatek kluczowych, na przykład animując wjazd panelu na ekran. Poza edytorem jest niewidoczny.

- **Zarządzaj elementami docelowymi**: wybierz elementy, które mają być animowane.
- **Edytuj klatki kluczowe**: otwiera edytor klatek kluczowych.
- **Zapętl animację**: rozpoczyna animację od nowa po jej zakończeniu.

Wszystkie informacje znajdziesz na stronie [Animator elementów](/element-animator).

## Elementy niewidoczne

Te elementy są widoczne tylko w edytorze układu.

### Licznik

Wielokrotnie uruchamia swój skrypt akcji, gdy ekran jest otwarty.

> [!IMPORTANT]
> Zalecanym sposobem na uruchamianie czegoś cyklicznie lub z opóźnieniem są [harmonogramy](/schedulers). W miarę możliwości używaj ich zamiast liczników. Działają na każdym ekranie, a także wtedy, gdy żaden ekran nie jest otwarty. Można w nich uruchamiać wszystkie akcje, a akcje mogą je uruchamiać i zatrzymywać.

Oto jak zastąpić liczniki harmonogramami:

- Uruchamianie przez cały czas, gdy ekran jest otwarty: użyj harmonogramu z ustawieniem **Opóźnienie tyknięcia (ms)**. Uruchom go akcją [**Uruchom harmonogram**](/action-scripts#start-scheduler) w opcji **Edytuj skrypt akcji „Otwórz ekran”** dla układu, a następnie zatrzymaj akcją [**Zatrzymaj harmonogram**](/action-scripts#stop-scheduler) w opcji **Edytuj skrypt akcji „Zamknij ekran”**. Obie opcje znajdziesz w menu dostępnym po kliknięciu prawym przyciskiem myszy tła edytora.
- Uruchamianie raz na start gry: użyj harmonogramu z włączoną opcją **Uruchom przy starcie** i ustawieniem **Liczba tyknięć** równym `1`.
- Uruchamianie za każdym razem, gdy ekran zostanie otwarty: nie trzeba używać licznika ani harmonogramu. Dodaj akcje do opcji **Edytuj skrypt akcji „Otwórz ekran”**.

Ustawienia licznika:

- **Opóźnienie tyknięcia [ms]**: odstęp między kolejnymi uruchomieniami w milisekundach. Wartość `0` uruchamia go przy każdym tyknięciu, czyli 20 razy na sekundę.
- **Tryb tyknięć**: **Normalny** uruchamia go cały czas. **Sesja** uruchamia go tylko raz, aż do ponownego uruchomienia gry. **Przy wczytaniu ekranu** uruchamia go raz za każdym razem, gdy ekran zostanie otwarty, również po zmianie rozmiaru okna.
- **Asynchronicznie**: uruchamia go w tle. Większość akcji nie może działać w ten sposób i wyświetli błąd.

### Audio

Odtwarza muzykę lub dźwięki, jeden utwór po drugim, gdy ekran jest otwarty.

- **Zarządzaj utworami**: pliki audio, ich kolejność i **Waga utworu** używana przy losowaniu.
- **Tryb odtwarzania**: **Normalny** odtwarza utwory po kolei, a **Losowo** w przypadkowej kolejności.
- **Zapętl utwory**, **Głośność** i **Kanał dźwięku**: określają sposób odtwarzania.

Aby muzyka była odtwarzana również podczas przechodzenia między ekranami, umieść element Audio w [układzie uniwersalnym](/universal-layouts). Więcej informacji znajdziesz na stronie [Muzyka w tle menu](/background-music).

### Kontroler muzyki

Wyłącza muzykę gry na tym ekranie.

- **Odtwarzaj muzykę menu**: muzyka odtwarzana w menu, gdy żaden świat nie jest wczytany, na przykład na ekranie tytułowym.
- **Odtwarzaj muzykę świata**: muzyka świata, która nadal jest odtwarzana w menu, na przykład w ekwipunku.

Działa tylko wtedy, gdy ekran jest otwarty.

### Kursor

Zastępuje kursor myszy własnym obrazem, gdy ekran jest otwarty.

- **Tekstura kursora**: obraz PNG, na przykład o rozmiarze 32×32 pikseli.
- **Współrzędna X punktu aktywnego** i **Współrzędna Y punktu aktywnego**: piksel obrazu, który odpowiada za kliknięcie, na przykład czubek strzałki.
- **Tryb podglądu w edytorze**: wyświetla kursor w edytorze, gdy kursor myszy znajduje się nad elementem.

Więcej informacji znajdziesz na stronie [Niestandardowy kursor](/custom-cursor).
