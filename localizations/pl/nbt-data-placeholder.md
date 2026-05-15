---
title: Plik zastępczy danych NBT
description: Jak używać pliku zastępczego danych NBT.
---


# Pobieranie danych NBT

Te placeholdery są dostępne w FancyMenu v3.8.0+.

Placeholders **Client NBT Data Get** i **Server NBT Data Get** pozwalają pobierać dane NBT (Named Binary Tag) z encji i bloków w Minecraft, podobnie jak polecenie `/data get`. Jest to niezwykle przydatne do tworzenia dynamicznych układów reagujących na stan gry, statystyki gracza lub warunki świata.

> Ten placeholder jest szczególnie potężny w modowanej rozgrywce, ponieważ może odczytywać niestandardowe dane NBT dodawane przez mody do encji i graczy. Niezależnie od tego, czy grasz z modami magicznymi dodającymi systemy many, modami RPG z własnymi statystykami, czy modami technicznymi z wartościami energii, możesz wyświetlać te zmodyfikowane wartości w swoich interfejsach.
{.is-info}

## Przegląd

Te placeholdery wyodrębniają konkretne wartości ze структур danych NBT za pomocą ścieżek NBT. Możesz pobierać zdrowie gracza, poziom głodu, przedmioty w ekwipunku, stany bloków, zmodyfikowane atrybuty takie jak mana czy energia i wiele więcej.

Wersja po stronie klienta ma dużą zaletę, że działa wyłącznie po stronie klienta, więc nie potrzebujesz FancyMenu na serwerze, ale jest przez to znacznie bardziej ograniczona, ponieważ nie wszystko związane z danymi NBT jest zawsze widoczne dla wszystkich klientów.

Wersja po stronie serwera wymaga zainstalowania FancyMenu na serwerze, ale zapewnia **pełną obsługę** praktycznie **wszystkiego**, co jest przechowywane jako NBT.

Ta strona skupia się na wersji po stronie klienta (`nbt_data_get`), ale wszystko działa bardzo podobnie także dla wersji po stronie serwera (`nbt_data_get_server`).

## Składnia placeholdera

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Wymagane wartości

| Wartość | Opis | Opcje |
|-------|-------------|---------|
| `source_type` | Typ źródła danych | `entity` lub `block` |
| `nbt_path` | Ścieżka NBT do odczytu | np. `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## Wartości warunkowe

W zależności od `source_type`, potrzebujesz jednej z poniższych opcji:

| Wartość | Wymagana, gdy | Opis | Format |
|-------|--------------|-------------|--------|
| `entity_selector` | source_type to `entity` | Wybiera encję do odczytu | `@s` (ja), `@p` (najbliższy gracz), `@e` (najbliższa encja), UUID lub nazwa encji |
| `block_pos` | source_type to `block` | Współrzędne bloku | `x y z` (np. `100 64 -200`) |

## Wartości opcjonalne

| Wartość | Opis | Domyślna | Opcje |
|-------|-------------|---------|---------|
| `scale` | Współczynnik skalowania dla wartości liczbowych | `1.0` | Dowolna liczba dziesiętna |
| `return_type` | Jak sformatować zwrócone dane | `value` | `value` (liczba/rozmiar), `string` (tekst), `snbt` (sformatowane NBT), `json` (format JSON) |

## Wyjaśnienie typów zwracanych danych

- **`value`** - Zwraca wartości liczbowe lub rozmiary (domyślnie)
  - Dla liczb: zwraca liczbę (opcjonalnie przeskalowaną)
  - Dla ciągów tekstowych: zwraca długość tekstu
  - Dla list/tablic: zwraca liczbę elementów
  - Dla compoundów: zwraca liczbę tagów

- **`string`** - Zwraca rzeczywistą wartość tekstową danych NBT

- **`snbt`** - Zwraca dane w formacie SNBT (Stringified NBT)

- **`json`** - Zwraca dane w formacie JSON (tylko dla tagów compound)

## Przykłady

### Pobranie zdrowia gracza
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### Pobranie poziomu głodu gracza
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### Pobranie współrzędnej X gracza
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### Pobranie przedmiotu z pierwszego slotu hotbara
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### Pobranie danych bloku na określonej pozycji
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### Pobranie przeskalowanego procentu zdrowia (Health * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## Znajdowanie dostępnych ścieżek NBT

### Metoda 1: Użycie polecenia `/data get` (zalecane)

Najłatwiejszym sposobem odkrywania dostępnych ścieżek NBT jest użycie w grze polecenia `/data get` bez podawania ścieżki:

1. **Dla encji:** `/data get entity @p`
2. **Dla bloków:** `/data get block <x> <y> <z>`

Wyświetli to wszystkie dostępne dane NBT dla danego celu, pokazując dokładne ścieżki, z których możesz skorzystać.

#### Zrozumienie wyniku

Gdy uruchomisz `/data get entity @p`, zobaczysz wynik podobny do tego:

```
Player616 has the following entity data: {Brain: {memories: {}}, 
HurtByTimestamp: 0, SleepTimer: 0s, Invulnerable: 0b, FallFlying: 
0b, PortalCooldown: 0, AbsorptionAmount: 0.0f, abilities: 
{invulnerable: 1b, mayfly: 1b, instabuild: 1b, walkSpeed: 0.1f, 
mayBuild: 1b, flying: 1b, flySpeed: 0.05f}, FallDistance: 0.0f, 
recipeBook: {recipes: ["minecraft:crafting_table"]}, 
DeathTime: 0s, XpSeed: -380875747, XpTotal: 0, UUID: [I; 1379890089, -1732753738, 
-2135065633, -718799804], playerGameType: 1, seenCredits: 
0b, Motion: [0.0d, 0.0d, 0.0d], Health: 20.0f, foodSaturationLevel: 
5.0f, ...}
```

Aby wyodrębnić poprawną ścieżkę z tego wyniku:

1. **Proste wartości** - Użyj bezpośrednio nazwy klucza:
   - `Health: 20.0f` → Ścieżka: `Health`
   - Przykład: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **Zagnieżdżone wartości** - Użyj zapisu z kropkami, aby uzyskać dostęp do zagnieżdżonych danych:
   - `abilities: {walkSpeed: 0.1f}` → Ścieżka: `abilities.walkSpeed`
   - Przykład: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **Wartości tablicowe** - Użyj nawiasów kwadratowych z numerami indeksów:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Ścieżka dla ruchu w osi Y: `Motion[1]`
   - Przykład: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### Metoda 2: Mod NBT Autocomplete

Aby łatwiej odkrywać ścieżki NBT, rozważ zainstalowanie moda **NBT Autocomplete**:
- Dostępny dla Fabric i Forge (Minecraft 1.21.x)
- Zapewnia podpowiedzi autouzupełniania w grze podczas wpisywania poleceń
- Pokazuje dostępne nazwy tagów i typy
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## Popularne ścieżki NBT

### Encja gracza
- `Health` - Aktualne zdrowie (float)
- `foodLevel` - Poziom głodu (int, 0-20)
- `foodSaturationLevel` - Poziom nasycenia (float)
- `XpLevel` - Poziom doświadczenia (int)
- `XpP` - Postęp doświadczenia (float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - Współrzędne X, Y, Z
- `Inventory` - Tablica ekwipunku gracza
- `SelectedItemSlot` - Aktualnie wybrany slot hotbara (int, 0-8)

### Popularne NBT bloków
- `Items` - Zawartość kontenera (skrzynie, piece itd.)
- `CustomName` - Niestandardowa nazwa bloku
- `Lock` - Ciąg blokady dla kontenerów

### Przykłady popularnych NBT z modów
- **Mody magiczne**: Często przechowują manę jako `playerMana`, `mana.current` lub podobnie
- **Mody techniczne**: Wartości energii, takie jak `energy`, `forgeEnergy` lub `energyStorage.energy`
- **Mody RPG**: Niestandardowe statystyki, takie jak `customStats.strength`, `rpgAttributes.level`

Aby znaleźć ścieżki NBT dodane przez mody, użyj `/data get entity @p`, gdy mod jest aktywny, i poszukaj niestandardowych tagów dodanych przez mod.

## Ograniczenia

- **Brak dostępu do storage po stronie klienta** - Źródło danych storage nie jest obsługiwane po stronie klienta (tylko po stronie serwera)
- **Wydajność** - Częste odczytywanie danych NBT może wpływać na wydajność
- Zwraca pusty ciąg, jeśli ścieżka jest nieprawidłowa lub nie można uzyskać dostępu do danych

## Wskazówki

1. Zawsze najpierw testuj ścieżki NBT w grze za pomocą `/data get`
2. Użyj parametru `scale`, aby przekształcać wartości na procenty lub inne przydatne formaty
3. Pamiętaj, że niektóre dane NBT mogą nie być synchronizowane do klienta
4. Selektory encji są ograniczone do encji znajdujących się w zasięgu renderowania
5. W przypadku zawartości z modów sprawdź dokumentację moda lub użyj `/data get`, aby odkryć niestandardowe ścieżki NBT
