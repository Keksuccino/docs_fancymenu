---
title: Placeholder danych NBT
description: 'Odczyt danych NBT encji, bloków i pamięci.'
---

# Placeholdy danych NBT

FancyMenu udostępnia dwa placeholdery NBT:

| Placeholder | Działa po stronie | Dostępne dane |
|---|---|---|
| `nbt_data_get` | Klient | Encje i byty blokowe widoczne po stronie klienta |
| `nbt_data_get_server` | Serwer | Cele zgodne z vanilla `/data get`; wymaga FancyMenu na serwerze |

# Placeholder po stronie klienta

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Wartości

| Wartość | Wymagane | Opis |
|---|---|---|
| `source_type` | Tak | `entity` lub `block` |
| `entity_selector` | Dla encji | Selektor po stronie klienta, UUID lub dokładna nazwa encji |
| `block_pos` | Dla bloków | Trzy bezwzględne współrzędne całkowite, np. `100 64 -200` |
| `nbt_path` | Tak | Ścieżka NBT, np. `Health`, `Pos[0]` lub `Inventory[0].id` |
| `scale` | Nie | Mnoży numeryczne wyniki `value`; domyślnie `1.0` |
| `return_type` | Nie | `value`, `string`, `snbt` lub `json`; domyślnie `value` |

Pozycje bloków po stronie klienta nie obsługują współrzędnych `~` ani `^`.

## Selektory encji po stronie klienta

| Selektor | Początkowe cele | Domyślna kolejność |
|---|---|---|
| `@s` | Lokalny gracz | Sama encja |
| `@p` | Gracze | Najbliższy |
| `@a` | Gracze | Kolejność iteracji klienta |
| `@r` | Gracze | Losowo |
| `@e` | Wszystkie encje widoczne po stronie klienta | Kolejność iteracji klienta |

`@e` nie wybiera najbliższej encji, chyba że dodasz `sort=nearest`. Obsługiwane są również bezpośrednie wyszukiwanie po UUID i dokładnej nazwie encji.

Obsługiwane opcje selektora:

| Opcja | Opis |
|---|---|
| `type` | ID encji; dodaj prefiks `!`, aby wykluczyć |
| `name` | Dokładna nazwa wyświetlana; dodaj prefiks `!`, aby wykluczyć |
| `tag` | Tag encji; dodaj prefiks `!`, aby wykluczyć |
| `limit` | Dodatni limit wyników |
| `sort` | `nearest`, `furthest`, `random` lub `arbitrary` |
| `distance` | Zakres odległości vanilla, np. `..10` lub `5..20` |
| `x`, `y`, `z` | Punkt początkowy wyszukiwania; przyjmuje wartości bezwzględne i przesunięcia `~` |
| `dx`, `dy`, `dz` | Rozmiar obszaru wyszukiwania od punktu początkowego |

Lokalne współrzędne `^` i inne standardowe opcje selektora vanilla nie są obsługiwane przez placeholder po stronie klienta.

Przykład:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## Typy zwracane

| Typ | Wynik |
|---|---|
| `value` | Znaczniki numeryczne są formatowane liczbowo i uwzględniają `scale`; znaczniki tekstowe zwracają swój tekst; pozostałe znaczniki zwracają tekst w stylu SNBT |
| `string` | Zwraca wartość tekstową znacznika albo pusty ciąg, gdy znacznik nie ma wartości tekstowej |
| `snbt` | Zwraca reprezentację SNBT znacznika |
| `json` | Tylko dla znaczników złożonych: zwraca serializowany komponent tekstowy Minecrafta zawierający ładnie sformatowany wynik NBT |

Tryb `json` po stronie klienta nie jest bezpośrednią konwersją NBT do JSON.

## Przykłady

Głód gracza:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

ID pierwszego przedmiotu w hotbarze:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

Liczba przedmiotów w bycie blokowym:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# Placeholder po stronie serwera

`nbt_data_get_server` działa zgodnie z zachowaniem serwerowego `/data get` i obsługuje:

- Pełne selektory encji po stronie serwera.
- Cele bloków z współrzędnymi bezwzględnymi, względnymi (`~`) lub lokalnymi (`^`).
- Pamięć komend przez `source_type:"storage"`.

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

Placeholder zwraca pustą wartość, dopóki nie nadejdzie odpowiedź z serwera. Odpowiedzi są na krótko buforowane, aby uniknąć nadmiernej liczby zapytań.

# Znajdowanie ścieżek NBT

Użyj odpowiedniej komendy bez ścieżki NBT, aby sprawdzić dostępne dane:

```text
/data get entity @s
/data get block 100 64 -200
```

Wyniki po stronie klienta są ograniczone do danych zsynchronizowanych z klientem. Nieprawidłowe cele lub ścieżki zwracają pusty ciąg i zapisują szczegóły do `logs/latest.log`.
