---
title: NBT-Daten-Platzhalter
description: 'Liest NBT-Daten von Entitäten, Blöcken und Speicher.'
---

# NBT-Daten-Platzhalter

FancyMenu stellt zwei NBT-Platzhalter bereit:

| Platzhalter | Läuft auf | Verfügbare Daten |
|---|---|---|
| `nbt_data_get` | Client | Vom Client sichtbare Entitäten und Block-Entitäten |
| `nbt_data_get_server` | Server | Vanilla-`/data get`-Ziele; erfordert FancyMenu auf dem Server |

# Client-seitiger Platzhalter

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Werte

| Wert | Erforderlich | Beschreibung |
|---|---|---|
| `source_type` | Ja | `entity` oder `block` |
| `entity_selector` | Für Entitäten | Client-seitiger Selektor, UUID oder exakter Entitätsname |
| `block_pos` | Für Blöcke | Drei absolute Ganzzahl-Koordinaten, z. B. `100 64 -200` |
| `nbt_path` | Ja | NBT-Pfad, z. B. `Health`, `Pos[0]` oder `Inventory[0].id` |
| `scale` | Nein | Multipliziert numerische `value`-Ergebnisse; Standard `1.0` |
| `return_type` | Nein | `value`, `string`, `snbt` oder `json`; Standard `value` |

Client-seitige Blockpositionen unterstützen keine `~`- oder `^`-Koordinaten.

## Client-Entitätsselektoren

| Selektor | Anfangsziele | Standardreihenfolge |
|---|---|---|
| `@s` | Lokaler Spieler | Selbst |
| `@p` | Spieler | Nächster |
| `@a` | Spieler | Client-Iterationsreihenfolge |
| `@r` | Spieler | Zufällig |
| `@e` | Alle client-sichtbaren Entitäten | Client-Iterationsreihenfolge |

`@e` wählt nicht automatisch die nächstgelegene Entität aus, außer du fügst `sort=nearest` hinzu. Direkte UUID- und exakte Entitätsnamen-Suche werden ebenfalls unterstützt.

Unterstützte Selektoroptionen:

| Option | Beschreibung |
|---|---|
| `type` | Entitäts-ID; mit `!` voranstellen, um auszuschließen |
| `name` | Exakter Anzeigename; mit `!` voranstellen, um auszuschließen |
| `tag` | Entitäts-Tag; mit `!` voranstellen, um auszuschließen |
| `limit` | Positive Ergebnisbegrenzung |
| `sort` | `nearest`, `furthest`, `random` oder `arbitrary` |
| `distance` | Vanille-Entfernungsbereich, z. B. `..10` oder `5..20` |
| `x`, `y`, `z` | Suchursprung; akzeptiert absolute Werte und `~`-Offsets |
| `dx`, `dy`, `dz` | Größe der Suchbox vom Ursprung aus |

Lokale `^`-Koordinaten und andere Vanille-Selektoroptionen werden vom Client-Platzhalter nicht unterstützt.

Beispiel:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## Rückgabetypen

| Typ | Ergebnis |
|---|---|
| `value` | Numerische Tags werden numerisch formatiert und `scale` wird angewendet; String-Tags geben ihren Text zurück; andere Tags geben SNBT-ähnlichen Text zurück |
| `string` | Gibt den String-Wert des Tags zurück oder einen leeren String, wenn der Tag keinen String-Wert hat |
| `snbt` | Gibt die SNBT-Darstellung des Tags zurück |
| `json` | Nur für Compound-Tags: gibt eine serialisierte Minecraft-Textkomponente mit formatierter NBT-Ausgabe zurück |

Der client-seitige `json`-Modus ist keine direkte NBT-zu-JSON-Konvertierung.

## Beispiele

Spieler-Hunger:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

Erste Hotbar-Gegenstands-ID:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

Gegenstandsanzahl einer Block-Entität:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# Server-seitiger Platzhalter

`nbt_data_get_server` folgt dem Verhalten von `/data get` auf dem Server und unterstützt:

- Vollständige serverseitige Entitätsselektoren.
- Block-Ziele mit absoluten, relativen (`~`) oder lokalen (`^`) Koordinaten.
- Kommando-Speicher über `source_type:"storage"`.

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

Der Platzhalter gibt einen leeren Wert zurück, bis die Server-Antwort eintrifft. Antworten werden kurzzeitig zwischengespeichert, um übermäßige Anfragen zu vermeiden.

# NBT-Pfade finden

Verwende den passenden Befehl ohne NBT-Pfad, um verfügbare Daten zu prüfen:

```text
/data get entity @s
/data get block 100 64 -200
```

Client-seitige Ergebnisse sind auf Daten beschränkt, die mit dem Client synchronisiert werden. Ungültige Ziele oder Pfade geben einen leeren String zurück und schreiben Details in `logs/latest.log`.
