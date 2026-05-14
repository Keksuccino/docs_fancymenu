---
title: NBT-Daten-Placeholder
description: Wie man den NBT-Daten-Placeholder verwendet.
---


# NBT-Daten abrufen

Diese Platzhalter sind in FancyMenu v3.8.0+ verfügbar.

Die Platzhalter **Client NBT Data Get** und **Server NBT Data Get** ermöglichen es dir, NBT-Daten (Named Binary Tag) von Entitäten und Blöcken in Minecraft abzurufen, ähnlich dem Befehl `/data get`. Das ist extrem nützlich, um dynamische Layouts zu erstellen, die auf den Spielzustand, Spielerstats oder Weltbedingungen reagieren.

> Dieser Platzhalter ist besonders leistungsstark für modifiziertes Gameplay, da er auf benutzerdefinierte NBT-Daten zugreifen kann, die Mods zu Entitäten und Spielern hinzufügen. Egal, ob du mit Magie-Mods spielst, die Manasysteme hinzufügen, mit RPG-Mods mit benutzerdefinierten Stats oder mit Technologie-Mods mit Energiewerten – du kannst diese modifizierten Werte in deinen UI-Layouts anzeigen.
{.is-info}

## Übersicht

Diese Platzhalter extrahieren spezifische Werte aus NBT-Datenstrukturen mithilfe von NBT-Pfaden. Du kannst Spielerleben, Hunger, Inventargegenstände, Blockzustände, modifizierte Attribute wie Mana oder Energie und vieles mehr abrufen.

Die clientseitige Version des Platzhalters hat den großen Vorteil, dass sie rein clientseitig funktioniert, du FancyMenu also nicht auf dem Server benötigst. Allerdings ist sie dadurch auch deutlich eingeschränkter, da nicht alle NBT-Daten jederzeit für alle Clients sichtbar sind.

Die serverseitige Version erfordert, dass FancyMenu auf dem Server installiert ist, bietet dafür aber **volle Unterstützung** für praktisch **alles**, was als NBT gespeichert ist.

Diese Seite konzentriert sich auf die clientseitige Version (`nbt_data_get`), aber alles funktioniert für die serverseitige Version (`nbt_data_get_server`) sehr ähnlich.

## Platzhalter-Syntax

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Erforderliche Werte

| Wert | Beschreibung | Optionen |
|-------|-------------|---------|
| `source_type` | Der Typ der Datenquelle | `entity` oder `block` |
| `nbt_path` | Der abzufragende NBT-Pfad | z. B. `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## Bedingte Werte

Je nach `source_type` benötigst du einen dieser Werte:

| Wert | Erforderlich wenn | Beschreibung | Format |
|-------|--------------|-------------|--------|
| `entity_selector` | `source_type` ist `entity` | Wählt aus, welche Entität abgefragt werden soll | `@s` (selbst), `@p` (nächster Spieler), `@e` (nächste Entität), UUID oder Entitätsname |
| `block_pos` | `source_type` ist `block` | Die Koordinaten des Blocks | `x y z` (z. B. `100 64 -200`) |

## Optionale Werte

| Wert | Beschreibung | Standard | Optionen |
|-------|-------------|---------|---------|
| `scale` | Skalierungsfaktor für numerische Werte | `1.0` | Beliebige Dezimalzahl |
| `return_type` | Wie die zurückgegebenen Daten formatiert werden | `value` | `value` (numerisch/Größe), `string` (Text), `snbt` (formatiertes NBT), `json` (JSON-Format) |

## Rückgabetypen erklärt

- **`value`** - Gibt numerische Werte oder Größen zurück (Standard)
  - Bei Zahlen: gibt die Zahl zurück (optional skaliert)
  - Bei Strings: gibt die Länge des Strings zurück
  - Bei Listen/Arrays: gibt die Anzahl der Elemente zurück
  - Bei Compounds: gibt die Anzahl der Tags zurück

- **`string`** - Gibt den tatsächlichen String-Wert der NBT-Daten zurück

- **`snbt`** - Gibt die Daten im SNBT-Format (Stringified NBT) zurück

- **`json`** - Gibt die Daten im JSON-Format zurück (nur für Compound-Tags)

## Beispiele

### Spielerleben abrufen
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### Hungerlevel des Spielers abrufen
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### X-Koordinate des Spielers abrufen
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### Gegenstand im ersten Hotbar-Slot abrufen
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### Blockdaten an einer bestimmten Position abrufen
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### Skalierten Gesundheitsprozentsatz abrufen (Gesundheit * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## Verfügbare NBT-Pfade finden

### Methode 1: Den Befehl `/data get` verwenden (empfohlen)

Der einfachste Weg, verfügbare NBT-Pfade zu entdecken, ist, den Befehl `/data get` im Spiel ohne einen Pfad zu verwenden:

1. **Für Entitäten:** `/data get entity @p`
2. **Für Blöcke:** `/data get block <x> <y> <z>`

Dadurch werden alle verfügbaren NBT-Daten für das Ziel angezeigt, sodass du die genauen Pfade siehst, die du verwenden kannst.

#### Die Ausgabe verstehen

Wenn du `/data get entity @p` ausführst, siehst du eine Ausgabe ähnlich dieser:

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

Um einen gültigen Pfad aus dieser Ausgabe zu extrahieren:

1. **Einfache Werte** - Verwende den Schlüsselnamen direkt:
   - `Health: 20.0f` → Pfad: `Health`
   - Beispiel: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **Verschachtelte Werte** - Verwende Punktnotation, um auf verschachtelte Daten zuzugreifen:
   - `abilities: {walkSpeed: 0.1f}` → Pfad: `abilities.walkSpeed`
   - Beispiel: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **Array-Werte** - Verwende eckige Klammern mit Indexzahlen:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Pfad für die Y-Bewegung: `Motion[1]`
   - Beispiel: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### Methode 2: NBT-Autocomplete-Mod

Für eine einfachere Ermittlung von NBT-Pfaden solltest du das **NBT Autocomplete**-Mod installieren:
- Verfügbar für Fabric und Forge (Minecraft 1.21.x)
- Bietet Ingame-Autovervollständigungsvorschläge beim Tippen von Befehlen
- Zeigt verfügbare Tag-Namen und Typen an
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## Häufige NBT-Pfade

### Spieler-Entität
- `Health` - Aktuelle Gesundheit (float)
- `foodLevel` - Hungerlevel (int, 0-20)
- `foodSaturationLevel` - Sättigungslevel (float)
- `XpLevel` - Erfahrungsstufe (int)
- `XpP` - Erfahrungsfortschritt (float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - X-, Y-, Z-Koordinaten
- `Inventory` - Spieler-Inventararray
- `SelectedItemSlot` - Der aktuell ausgewählte Hotbar-Slot (int, 0-8)

### Häufige Block-NBTs
- `Items` - Inhalt von Behältern (Truhen, Öfen usw.)
- `CustomName` - Benutzerdefinierter Name des Blocks
- `Lock` - Sperrstring für Behälter

### Häufige Beispiele für modifizierte NBT-Daten
- **Magie-Mods**: Speichern Mana oft als `playerMana`, `mana.current` oder ähnlich
- **Technik-Mods**: Energiewerte wie `energy`, `forgeEnergy` oder `energyStorage.energy`
- **RPG-Mods**: Benutzerdefinierte Stats wie `customStats.strength`, `rpgAttributes.level`

Um modifizierte NBT-Pfade zu finden, verwende `/data get entity @p`, während der Mod aktiv ist, und achte auf die benutzerdefinierten Tags, die der Mod hinzugefügt hat.

## Einschränkungen

- **Kein Speicherzugriff auf dem Client** - Die Datenquelle „storage“ wird clientseitig nicht unterstützt (nur serverseitig)
- **Leistung** - Häufiger Zugriff auf NBT-Daten kann die Leistung beeinträchtigen
- Gibt einen leeren String zurück, wenn der Pfad ungültig ist oder auf die Daten nicht zugegriffen werden kann

## Tipps

1. Teste deine NBT-Pfade immer zuerst im Spiel mit `/data get`
2. Verwende den Parameter `scale`, um Werte in Prozente oder andere nützliche Formate umzuwandeln
3. Denke daran, dass einige NBT-Daten möglicherweise nicht mit dem Client synchronisiert werden
4. Entitätsselektoren sind auf Entitäten innerhalb der Renderdistanz beschränkt
5. Bei modifizierten Inhalten solltest du die Dokumentation des Mods prüfen oder `/data get` verwenden, um benutzerdefinierte NBT-Pfade zu entdecken
