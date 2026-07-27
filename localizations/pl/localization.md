---
title: Lokalizowanie układów
description: Lokalizuj tekst i inne elementy układu.
---

# Lokalizowanie układów

Użyj [**placeholdera Localize Text**](./placeholders#localize-text-local) dla tekstu, który ma być tłumaczony:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu najpierw sprawdza aktywne dane językowe Minecrafta. Jeśli klucz nie jest tam obecny, sprawdza niestandardowe pliki lokalizacji FancyMenu. Jeśli żadne z tych źródeł nie zawiera klucza, wyświetlany jest sam klucz.

# Niestandardowe pliki lokalizacji FancyMenu

Umieść pliki poniżej:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Utwórz podkatalog dla swoich plików lokalizacyjnych:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Umieszczaj pliki lokalizacji w co najmniej jednym podkatalogu `custom_locals`; pliki znajdujące się bezpośrednio w katalogu głównym `custom_locals` nie są wczytywane. Zagnieżdżone podkatalogi są obsługiwane.

Obsługiwane formaty UTF-8:

| Rozszerzenie | Format |
|---|---|
| `.json` | Obiekt JSON; zagnieżdżone obiekty stają się kluczami rozdzielanymi kropkami |
| `.lang` | Linie `key=value` |
| `.properties` | Składnia plików właściwości Java |

Przykład JSON:

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

Definiuje to `modpack.menu.play`.

FancyMenu łączy obsługiwane pliki z tych podkatalogów w jeden niestandardowy słownik lokalizacji. Używaj każdego klucza tylko w jednym pliku. Niestandardowe pliki lokalizacji nie zmieniają się wraz z językiem wybranym w Minecraftcie; gdy potrzebujesz automatycznego przełączania języka, użyj opisanej poniżej metody z paczką zasobów.

Po edycji niestandardowych plików lokalizacji uruchom ponownie klienta.

# Tekst zależny od języka

Aby automatycznie przełączać język zgodnie z językiem wybranym w Minecraftcie, udostępnij zwykłe pliki językowe Minecrafta za pomocą [pakietu zasobów](./resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Użyj tych samych kluczy w każdym pliku językowym, włącz pakiet zasobów, a następnie odczytaj je za pomocą [**placeholdera Localize Text**](./placeholders#localize-text-local).

# Lokalizowanie obrazów i elementów

Użyj [**wymagania Is Game Language**](./conditions#is-game-language-fancymenu_loading_requirement_is_language), aby pokazywać różne elementy lub układy dla różnych kodów językowych, takich jak `en_us` i `de_de`.
