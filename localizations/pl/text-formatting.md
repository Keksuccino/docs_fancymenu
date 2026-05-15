---
title: Formatowanie tekstu
description: Jak formatować tekst za pomocą Markdown i kodów formatowania Minecrafta.
---

# Formatowanie tekstu

FancyMenu ma wiele funkcji, które sprawiają, że treści tekstowe w układach są *ładniejsze*!

Elementy tekstowe mają pełną obsługę **Markdown** z kilkoma fajnymi dodatkami, a większość innych treści tekstowych obsługuje system **formatowania tekstu Minecrafta**, a etykiety przycisków obsługują nawet **komponenty tekstowe Minecrafta**, które pozwalają używać niestandardowych czcionek i nie tylko.

# Markdown

**Elementy tekstowe** FancyMenu mają pełną obsługę Markdown, co oznacza, że możesz formatować tekst, dodając do niego specjalne znaki.

Na przykład, aby pogrubić tekst, dodajesz `**` przed i po pogrubionym fragmencie, więc `**Jakiś pogrubiony tekst, który jest bardzo pogrubiony.**` będzie wyglądać tak:
**Jakiś pogrubiony tekst, który jest bardzo pogrubiony.**

Markdown w FancyMenu ma też kilka specjalnych funkcji, które czynią go jeszcze potężniejszym!

> Markdown **NIE DZIAŁA** dla innych treści tekstowych, takich jak etykiety przycisków. Działa tylko w przypadku **ELEMENTÓW TEKSTOWYCH**. We wszystkich pozostałych przypadkach użyj [kodów formatowania Minecrafta](/text-formatting#minecraft-text-formatting).
{.is-danger}

## Czcionki

Możesz wyświetlić tekst w niestandardowej czcionce wczytanej z paczki zasobów, dodając `%!!<nazwa_czcionki>%` przed tekstem i `%!!%` po nim.

Prawidłową czcionką zawartą w podstawowej grze jest `uniform`, więc aby wyświetlić tekst czcionką `uniform`, zrób tak:
`%!!uniform%to jest niestandardowa czcionka%!!%`

Spowoduje to wyświetlenie `to jest niestandardowa czcionka` czcionką `uniform`.

## Kolor tekstu (HEX)

Wyświetlanie tekstu w określonym kolorze HEX jest możliwe przez dodanie `%<kolor_HEX>%` przed tekstem i `%#%` po nim.

Prawidłowy kolor HEX dla zieleni to `#77fc03`, więc aby wyświetlić tekst w tym kolorze, zrób tak:
`%#77fc03%ten tekst jest zielony!%#%`

Spowoduje to wyświetlenie `ten tekst jest zielony!` w kolorze `#77fc03` (zielonym).

Upewnij się, że kolor HEX zaczyna się od `#`!

FancyMenu 3.9.0 obsługuje również popularne nazwy kolorów w stylu HTML w tym samym kodzie formatowania koloru:

```
%#red%Ten tekst jest czerwony!%#%
```

Obsługiwane nazwy: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` oraz `transparent`.

## Wyrównanie tekstu

Możesz wyrównywać linie tekstu, rozpoczynając linię od odpowiedniego kodu formatowania wyrównania, następnie nie dodając nic więcej, potem wpisując linie tekstu, które chcesz pokazać z tym wyrównaniem, a na końcu ponownie umieszczając kod wyrównania w osobnej linii.

Cała treść tekstowa jest domyślnie **wyrównana do lewej**, więc istnieją tylko kody formatowania dla **wyśrodkowania** i **wyrównania do prawej**.

### Wyśrodkowanie

Aby wyśrodkować linie tekstu, użyj kodu formatowania `^^^`.

Przykład:
```
Ten tekst nie jest wyśrodkowany.

^^^
Ten tekst jest wyśrodkowany.
Ten tekst też jest wyśrodkowany.
^^^

Ten tekst nie jest już wyśrodkowany.
```

### Wyrównanie do prawej

Aby wyświetlić linie tekstu jako wyrównane do prawej, użyj kodu formatowania `|||`.

Przykład:
```
Ten tekst nie jest wyrównany do prawej.

|||
Ten tekst jest wyrównany do prawej.
Ten tekst też jest wyrównany do prawej.
|||

Ten tekst nie jest już wyrównany do prawej.
```

## Nagłówki

Aby wyświetlić **jedną linię tekstu** jako nagłówek (większy i podkreślony), dodaj `# ` (bardzo duży), `## ` (duży) lub `### ` (mały) przed linią tekstu.

Przykład:
`## Duży nagłówek`

## Pogrubienie

Dodaj `**` przed i po tekście, aby był **pogrubiony**.

Przykład:
`**pogrubiona treść tekstowa**`

## Kursywa

Dodaj `_` LUB `*` przed i po tekście, aby był *kursywą*.

Przykład:
`*treść tekstowa kursywą*`

## Przekreślenie

Dodaj `~` przed i po tekście, aby był ~~przekreślony~~.

Przykład:
`~treść tekstowa przekreślona~`

## Hiperłącza

Możesz dodawać hiperłącza do treści tekstowej, które po kliknięciu otwierają stronę internetową.

Tekst, który ma się pojawić jako [hiperłącze](https://google.com), musi być ujęty w `[ ]`, a następnie trzeba dodać właściwy link w `( )`.

Jeśli więc chcesz, aby `przykładowa treść tekstowa` była klikalna i otwierała `https://example-website.net`, zrób tak:
`[przykładowa treść tekstowa](https://example-website.net)`

## Zdarzenia kliknięcia i najechania

FancyMenu 3.9.0 dodaje w Markdown zdarzenia kliknięcia i najechania dla elementów tekstowych i innego tekstu w Markdown.

Zdarzenia kliknięcia używają prefiksu `click:`:

```
[jakiś klikalny tekst](click:unique_text_click_event_id)
```

Zdarzenia najechania używają prefiksu `hover:`:

```
[jakiś tekst z reakcją na najechanie](hover:unique_text_hover_event_id)
```

Użyj nasłuchiwaczy **On Markdown Text Clicked** i **On Markdown Text Hovered**, aby reagować na te zdarzenia. Oba nasłuchiwacze udostępniają identyfikator zdarzenia jako `$$text_event_id`.

## Obrazy

Markdown obsługuje wyświetlanie obrazów w treści tekstowej.

FancyMenu obsługuje zasoby Minecrafta, zasoby lokalne i zasoby internetowe w Markdown.

Aby dodać obraz, rozpocznij linię tekstu od `![](`, następnie podaj [adres URL, lokalizację zasobu lub ścieżkę do zasobu](/resources), a potem dodaj `)`.

Aby więc pokazać zasób internetowy `https://example-website.net/image.png`, zrób tak:
`![](https://example-website.net/image.png)`

Obrazy mogą być też **hiperłączami**, jeśli owiniesz całą linię obrazu w **hiperłącze**, tak:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> Zasoby lokalne muszą znajdować się w `/config/fancymenu/assets/` !
{.is-warning}

## Cytat

Aby sformatować tekst jako cytat, rozpocznij linię tekstu od `> `.
Spowoduje to formatowanie wszystkich kolejnych linii jako cytat aż do napotkania **pustej** linii.

Przykład:
```
To nie będzie wyglądać jak cytat.

> To będzie wyglądać jak cytat.
To też będzie wyglądać jak cytat.

To nie będzie już wyglądać jak cytat.
```

## Listy punktowane

Aby wyświetlić tekst jako listę punktowaną, taką jak:
- Pozycja 1
- Pozycja 2
  - Podpozycja

wystarczy rozpocząć linię od `- `.

Przykład:
```
- Pozycja 1
- Pozycja 2
  - Podpozycja
```

## Linia oddzielająca

Aby dodać do tekstu linię oddzielającą o szerokości całej linii tekstu, po prostu rozpocznij linię od `---` i nie dodawaj nic więcej.

Będzie to wyglądać mniej więcej tak:

---

## Bloki kodu

Bloki kodu mogą pomóc wyświetlić tekst jako `zwykły tekst` bez tego, aby Markdown próbował go formatować, albo po prostu pokazać tekst w stylu przypominającym kod, bez automatycznego zawijania linii tekstu.

Jednolinijkowy blok kodu (między innymi tekstami) zaczyna się i kończy znakiem \` , co w rzeczywistości jest dość trudne do pokazania w tekście Markdown..

Linia tekstu zawierająca jednolinijkowy blok kodu wygląda tak:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Wielolinijkowe bloki kodu obejmują wiele linii w jednym dużym bloku kodu i zaczynają się linią zawierającą tylko \`\`\`, następnie treść tekstową, a potem ponownie \`\`\`:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Zwykły tekst

Kod formatowania zwykłego tekstu ominie wszystkie inne kody formatowania znajdujące się wewnątrz niego.

Działa podobnie do bloków kodu, ale nie formatuje go jak blok kodu. Zamiast tego wyświetla się jak zwykły tekst, ale bez żadnego formatowania.

Aby objąć fragment tekstu w linii kodem formatowania zwykłego tekstu, musisz dodać `;;` przed i po fragmencie, który chcesz pokazać jako zwykły tekst, tak:

```
To jest linia tekstu z ;;**tą częścią**;; wyświetlaną jako niesformatowany tekst z widocznym kodem formatowania ** (pogrubienie) oraz _tą częścią_ jako normalnie sformatowany tekst kursywą.
```

Zwykły tekst działa również jako wielolinijkowy kod otaczający. Aby objąć całe linie, dodaj `;;;` przed i po liniach, które chcesz pokazać jako zwykły tekst, tak:

```
;;;
Ta linia będzie wyświetlana jako **niesformatowana** z widocznymi kodami formatowania ** (pogrubienie).
Ta linia będzie również wyświetlana jako _niesformatowana_ z widocznymi kodami formatowania _ (kursywa).
;;;

Ta linia znów będzie wyglądać **normalnie**, a słowo "normalnie" będzie pogrubione.
```

# Formatowanie tekstu Minecrafta

Sam Minecraft ma całkiem dobry system formatowania, który działa podobnie do Markdown, gdzie dodajesz specjalne znaki do treści tekstu, aby ją sformatować.

Aby dowiedzieć się więcej o systemie formatowania Minecrafta, zajrzyj na [tę stronę wiki Minecrafta](https://minecraft.wiki/w/Formatting_codes).

> Wiki podaje, że prefiks kodu formatowania to `§`, ale w FancyMenu musisz zastąpić go `&`. Wszystko inne pozostaje bez zmian.
{.is-warning}

> **Elementy tekstowe** są bardzo złożone i aby obsługiwać Markdown, kompromisem było **zepsucie natywnych kodów formatowania Minecrafta**, więc te kody nie będą działać dobrze w elementach tekstowych (po kodzie formatowania formatowane jest tylko pierwsze słowo itp.). Zamiast tego w elementach tekstowych używaj kodów formatowania Markdown.
{.is-danger}

# Komponenty tekstowe Minecrafta (surowy system komponentów)

System komponentów tekstowych Minecrafta jest bardzo potężny dla **jednoliniowej** treści tekstowej, takiej jak **etykiety przycisków**.

W Vanilla Minecraft możesz go używać w komendach `/tellraw` i `/title` (i prawdopodobnie w innych miejscach).
Jest to sformatowany tekst zapisany jako JSON, więc możesz dodawać atrybuty formatowania do treści tekstowej.

Aby dowiedzieć się więcej o komponentach tekstowych, zajrzyj na [tę stronę wiki Minecrafta](https://minecraft.wiki/w/Raw_JSON_text_format).
Aby dowiedzieć się więcej o czcionkach w Minecraftcie, zajrzyj na [tę stronę wiki Minecrafta](https://minecraft.wiki/w/Resource_pack#Fonts).

Aby FancyMenu rozpoznało etykietę przycisku jako **komponent tekstowy**, ustaw jako etykietę tylko zapisany tekst komponentu, tak jak tutaj:
`{"text":"Tekst etykiety przycisku","font":"uniform"}`

Powyższy przykład wyświetli etykietę przycisku `Tekst etykiety przycisku` czcionką `uniform`.

> Możesz używać placeholderów FancyMenu w wartości `text` komponentów.
{.is-info}
