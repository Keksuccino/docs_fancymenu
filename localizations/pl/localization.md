---
title: Lokalizowanie układów
description: Lokalizuj tekst i inne elementy układu.
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# Lokalizowanie układów

Użyj [**symbolu zastępczego Lokalizuj tekst**](/placeholders#localize-text) dla tekstu do przetłumaczenia:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu najpierw sprawdza aktywne dane językowe Minecrafta. Jeśli nie ma tam danego klucza, sprawdza niestandardowe pliki lokalizacyjne FancyMenu. Jeśli klucza nie ma w żadnym z tych źródeł, wyświetlany jest sam klucz.

# Niestandardowe pliki lokalizacyjne FancyMenu

Umieść pliki w katalogu:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Utwórz podkatalog na pliki lokalizacyjne:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Umieść pliki lokalizacyjne w co najmniej jednym podkatalogu `custom_locals`; pliki umieszczone bezpośrednio w katalogu głównym `custom_locals` nie są wczytywane. Możesz używać zagnieżdżonych podkatalogów.

Obsługiwane formaty UTF-8:

| Rozszerzenie | Format |
|---|---|
| `.json` | Obiekt JSON; zagnieżdżone obiekty są zamieniane na klucze rozdzielone kropkami |
| `.lang` | Wiersze w formacie `key=value` |
| `.properties` | Składnia plików właściwości języka Java |

Przykład JSON:

```json
{
  "modpack": {
    "menu": {
      "play": "Graj"
    }
  }
}
```

Definiuje to klucz `modpack.menu.play`.

FancyMenu łączy obsługiwane pliki z tych podkatalogów w jeden niestandardowy słownik lokalizacyjny. Każdego klucza używaj tylko w jednym pliku. Niestandardowe pliki lokalizacyjne nie zmieniają się wraz z wybranym językiem Minecrafta; jeśli potrzebujesz automatycznego przełączania języka, skorzystaj z opisanej poniżej metody z pakietem zasobów.

Po edycji niestandardowych plików lokalizacyjnych uruchom ponownie klienta.

# Tekst zależny od języka

Aby automatycznie przełączać język zgodnie z ustawieniem Minecrafta, dodaj standardowe pliki językowe Minecrafta do [pakietu zasobów](/resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Użyj tych samych kluczy w każdym pliku językowym, włącz pakiet zasobów, a następnie odczytuj tekst za pomocą [**symbolu zastępczego Lokalizuj tekst**](/placeholders#localize-text).

# Lokalizowanie obrazów i elementów

Użyj [warunku **Język gry**](/conditions#is-game-language), aby wyświetlać różne elementy lub układy dla różnych kodów języka, takich jak `en_us` i `de_de`.
