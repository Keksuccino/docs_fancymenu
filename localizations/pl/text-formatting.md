---
title: Formatowanie tekstu
description: Jak formatować tekst za pomocą Markdown i kodów formatowania Minecrafta.
---

# Formatowanie tekstu

[Elementy tekstowe](./elements#text) obsługują Markdown. Inne pola tekstowe używają formatowania Minecrafta, a etykiety przycisków mogą korzystać z komponentów tekstu Minecrafta.

# Markdown

**Elementy tekstowe** FancyMenu mają pełną obsługę Markdown, co oznacza, że możesz formatować treść tekstu, dodając do niej specjalne znaki.

Na przykład, aby pogrubić tekst, dodaj `**` przed i po pogrubionym tekście, więc `**Jakiś bardzo pogrubiony tekst.**` będzie wyglądać tak:
**Jakiś bardzo pogrubiony tekst.**

FancyMenu obsługuje również rozszerzenia opisane poniżej.

> [!CAUTION]
> Markdown działa tylko w **elementach tekstowych**. W przypadku etykiet przycisków i innych pól tekstowych używaj [kodów formatowania Minecrafta](#minecraft-text-formatting).

## Czcionki

Możesz wyświetlić tekst w niestandardowej czcionce wczytanej przez paczkę zasobów, dodając `%!!<font_name>%` przed tekstem oraz `%!!%` po nim.

Poprawną czcionką dołączoną do podstawowej wersji gry jest `uniform`, więc aby wyświetlić tekst w czcionce `uniform`, zrób tak:
`%!!uniform%to jest niestandardowa czcionka%!!%`

Spowoduje to wyświetlenie `to jest niestandardowa czcionka` w czcionce `uniform`.

## Kolor tekstu (HEX)

Wyświetlanie tekstu w określonym kolorze HEX jest możliwe przez dodanie `%<HEX_color>%` przed tekstem oraz `%#%` po nim.

Poprawnym kolorem HEX dla zieleni jest `#77fc03`, więc aby wyświetlić tekst w tym kolorze, zrób tak:
`%#77fc03%ten tekst jest zielony!%#%`

Spowoduje to wyświetlenie `ten tekst jest zielony!` jako `#77fc03` (zielony).

Upewnij się, że kolor HEX zaczyna się od `#`!

W tym samym kodzie formatowania koloru obsługiwane są popularne nazwy kolorów podobne do HTML:

```
%#red%Ten tekst jest czerwony!%#%
```

Obsługiwane nazwy: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` i `transparent`.

## Wyrównanie tekstu

Możesz wyrównywać wiersze tekstu, zaczynając linię od odpowiedniego kodu formatowania wyrównania, następnie nic więcej, potem wiersze tekstu, które mają być wyświetlane z takim wyrównaniem, a na końcu ponownie kod wyrównania w osobnej linii.

Cała treść tekstowa jest domyślnie **wyrównana do lewej**, więc istnieją tylko kody formatowania dla tekstu **wyśrodkowanego** i **wyrównanego do prawej**.

### Wyśrodkowane

Aby wyśrodkować wiersze tekstu, użyj kodu formatowania `^^^`.

Przykład:
```
Ten tekst nie jest wyśrodkowany.

^^^
Ten tekst jest wyśrodkowany.
Ten tekst też jest wyśrodkowany.
^^^

Ten tekst nie jest już wyśrodkowany.
```

### Wyrównane do prawej

Aby wyświetlić wiersze tekstu jako wyrównane do prawej, użyj kodu formatowania `|||`.

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

Aby wyświetlić **wiersz tekstu** jako nagłówek (większy i podkreślony), dodaj przed linią tekstu `# ` (bardzo duży), `## ` (duży) lub `### ` (mały).

Przykład:
`## Duży nagłówek`

## Pogrubienie

Dodaj `**` przed i po tekście, aby był **pogrubiony**.

Przykład:
`**pogrubiona treść tekstu**`

## Kursywa

Dodaj `_` LUB `*` przed i po tekście, aby był *kursywą*.

Przykład:
`*treść tekstu kursywą*`

## Przekreślenie

Dodaj `~` przed i po tekście, aby był ~~przekreślony~~.

Przykład:
`~treść tekstu przekreślona~`

## Hiperłącza

Do treści tekstu możesz dodawać hiperłącza, które po kliknięciu otwierają stronę internetową.

Tekst, który ma być widoczny jako [hiperłącze](https://google.com), należy umieścić w `[ ]`, a następnie właściwy link w `( )`.

Jeśli więc chcesz, aby `przykładowa treść tekstu` była klikalna i otwierała `https://example-website.net`, zrób tak:
`[przykładowa treść tekstu](https://example-website.net)`

## Zdarzenia kliknięcia i najechania

Zdarzenia kliknięcia i najechania w Markdown są dostępne dla [elementów tekstowych](./elements#text) i innego tekstu Markdown. Użyj [**On Markdown Text Clicked**](./listeners#on-markdown-text-clicked-text_clicked) oraz [**On Markdown Text Hovered**](./listeners#on-markdown-text-hovered-text_hovered), aby na nie reagować.

Zdarzenia kliknięcia używają prefiksu `click:`:

```
[some clickable text](click:unique_text_click_event_id)
```

Zdarzenia najechania używają prefiksu `hover:`:

```
[some hoverable text](hover:unique_text_hover_event_id)
```

Oba listenery udostępniają identyfikator zdarzenia jako `$$text_event_id`.

## Obrazy

Markdown obsługuje wyświetlanie obrazów w treści tekstu.

FancyMenu obsługuje zasoby Minecrafta, zasoby lokalne oraz zasoby internetowe w Markdown.

Aby dodać obraz, rozpocznij linię tekstu od `![](`, następnie podaj [URL, lokalizację zasobu lub ścieżkę do zasobu](./resources), a potem `)`.

Aby więc wyświetlić zasób internetowy `https://example-website.net/image.png`, zrób tak:
`![](https://example-website.net/image.png)`

Obrazy mogą być także **hiperłączami**, jeśli opakujesz całą linię tekstu obrazu w **hiperłącze**, tak jak tutaj:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> Zasoby lokalne muszą znajdować się w `<game-directory>/config/fancymenu/assets/`!

## Cytat

Aby sformatować tekst jako cytat, rozpocznij linię tekstu od `> `.
Spowoduje to formatowanie wszystkich kolejnych linii jako cytat, dopóki nie napotka **pustej** linii.

Przykład:
```
To nie będzie wyglądać jak cytat.

> To będzie wyglądać jak cytat.
To również będzie wyglądać jak cytat.

To nie będzie już wyglądać jak cytat.
```

## Lista punktowana

Aby wyświetlić tekst jako listę punktowaną, taką jak:
- Wpis 1
- Wpis 2
  - Podwpis

wystarczy rozpocząć linię od `- `.

Przykład:
```
- Wpis 1
- Wpis 2
  - Podwpis
```

## Linia oddzielająca

Aby dodać do tekstu linię oddzielającą o szerokości całego wiersza tekstu, wystarczy rozpocząć linię od `---` i nie dodawać nic więcej.

Będzie wtedy wyglądać mniej więcej tak:

---

## Bloki kodu

Bloki kodu mogą pomóc wyświetlać tekst jako `zwykły tekst` bez próby formatowania przez Markdown, albo po prostu pokazać tekst w stylu przypominającym kod, bez automatycznego zawijania linii.

Jednolinijkowy blok kodu (w środku innego tekstu) zaczyna się i kończy znakiem \` , co w Markdown jest właściwie dość trudne do pokazania..

Linia tekstu zawierająca jednolinijkowy blok kodu wygląda tak:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Wielolinijkowe bloki kodu obejmują wiele linii w jednym dużym bloku kodu i zaczynają się od linii zawierającej tylko \`\`\`, potem treść tekstu i ponownie \`\`\`:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Tekst zwykły

Kod formatowania zwykłego tekstu ominie wszystkie inne kody formatowania znajdujące się wewnątrz niego.

Działa podobnie do bloków kodu, ale nie formatuje tekstu jak blok kodu. Zamiast tego wyświetla go jak zwykły tekst, ale bez żadnego formatowania.

Aby objąć fragment tekstu w jednej linii kodem formatowania zwykłego tekstu, dodaj `;;` przed i po fragmencie tekstu, który ma być pokazany jako zwykły tekst, tak jak tutaj:

```
To jest linia tekstu z ;;**tą częścią**;; wyświetlaną jako sformatowany tekst bez formatowania, z widocznym kodem formatowania ** (pogrubienie) oraz _tą częścią_ jako normalnie sformatowanym tekstem kursywą.
```

Zwykły tekst działa również jako wielolinijkowy kod otaczający. Aby objąć całe linie, dodaj `;;;` przed i po linii (liniach), które chcesz pokazać jako zwykły tekst, tak jak tutaj:

```
;;;
Ta linia będzie wyświetlona **bez formatowania** z widocznymi kodami formatowania ** (pogrubienie).
Ta linia będzie też wyświetlona _bez formatowania_ z widocznymi kodami formatowania _ (kursywa).
;;;

Ta linia znów będzie wyglądać **normalnie**, a słowo "normalnie" będzie pogrubione.
```

# Formatowanie tekstu Minecrafta

Kody formatowania Minecrafta działają w obsługiwanych sformatowanych polach tekstowych w całym FancyMenu. Użyj `&` zamiast prefiksu `§` z Minecrafta; na przykład `&cOstrzeżenie` wyświetla czerwony tekst.

Dostępne kolory i style znajdziesz w [odnośniku do kodów formatowania w Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes).

> [!CAUTION]
> Kody formatowania Minecrafta są zawodliwe w **elementach tekstowych**, ponieważ te elementy analizują Markdown. Zamiast tego używaj formatowania Markdown opisanego powyżej.

# Komponenty tekstu Minecrafta (surowy system komponentów)

System komponentów tekstu Minecrafta jest całkiem potężny w przypadku **jednolinijkowej** treści tekstowej, takiej jak **etykiety przycisków**.

W Vanilla Minecraft możesz go używać w komendach `/tellraw` i `/title` (i prawdopodobnie w innych miejscach).
To sformatowany tekst zapisany w JSON, więc możesz dodawać atrybuty formatowania do treści tekstu.

Aby dowiedzieć się więcej o komponentach tekstu, zajrzyj na [tę stronę Minecraft Wiki](https://minecraft.wiki/w/Raw_JSON_text_format).
Aby dowiedzieć się więcej o czcionkach w Minecraft, zajrzyj na [tę stronę Minecraft Wiki](https://minecraft.wiki/w/Resource_pack#Fonts).

Aby FancyMenu wykrył etykietę przycisku jako **komponent tekstowy**, ustaw jako etykietę wyłącznie serializowany tekst komponentu, tak jak tutaj:
`{"text":"Tekst etykiety przycisku","font":"uniform"}`

Powyższy przykład wyświetli etykietę przycisku `Tekst etykiety przycisku` w czcionce `uniform`.

> [!NOTE]
> Możesz używać placeholderów FancyMenu w wartości `text` komponentów.
