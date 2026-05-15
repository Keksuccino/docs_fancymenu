---
title: Marcador de posición de datos NBT
description: Cómo usar el marcador de posición de datos NBT.
---


# Obtener datos NBT

Estos marcadores de posición están disponibles en FancyMenu v3.8.0+.

Los marcadores de posición **Client NBT Data Get** y **Server NBT Data Get** te permiten recuperar datos NBT (Named Binary Tag) de entidades y bloques en Minecraft, de forma similar al comando `/data get`. Esto es extremadamente útil para crear diseños dinámicos que respondan al estado del juego, a las estadísticas del jugador o a las condiciones del mundo.

> Este marcador de posición es especialmente potente en partidas con mods, ya que puede acceder a datos NBT personalizados que los mods añaden a entidades y jugadores. Tanto si juegas con mods de magia que añaden sistemas de maná, mods de rol con estadísticas personalizadas o mods de tecnología con valores de energía, puedes mostrar esos valores modificados en tus interfaces.
{.is-info}

## Vista general

Estos marcadores de posición extraen valores concretos de estructuras de datos NBT mediante rutas NBT. Puedes recuperar la salud del jugador, el hambre, los objetos del inventario, los estados de bloque, atributos modificados como maná o energía, y mucho más.

La versión del marcador de posición del lado del cliente tiene la gran ventaja de que funciona completamente en el cliente, así que no necesitas FancyMenu en el servidor, pero también es mucho más limitada, porque no todo lo relacionado con los datos NBT está visible para todos los clientes todo el tiempo.

La versión del lado del servidor requiere que FancyMenu esté instalado en el servidor, pero esto le da **compatibilidad total** con prácticamente **todo** lo que se almacena como NBT.

Esta página se centrará en la versión del lado del cliente (`nbt_data_get`), pero todo funciona de forma muy similar también para la versión del lado del servidor (`nbt_data_get_server`).

## Sintaxis del marcador de posición

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Valores obligatorios

| Valor | Descripción | Opciones |
|-------|-------------|---------|
| `source_type` | El tipo de fuente de datos | `entity` o `block` |
| `nbt_path` | La ruta NBT que consultar | p. ej. `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## Valores condicionales

Según tu `source_type`, necesitarás uno de estos:

| Valor | Obligatorio cuando | Descripción | Formato |
|-------|--------------------|-------------|---------|
| `entity_selector` | `source_type` es `entity` | Selecciona qué entidad consultar | `@s` (uno mismo), `@p` (jugador más cercano), `@e` (entidad más cercana), UUID o nombre de entidad |
| `block_pos` | `source_type` es `block` | Las coordenadas del bloque | `x y z` (por ejemplo, `100 64 -200`) |

## Valores opcionales

| Valor | Descripción | Predeterminado | Opciones |
|-------|-------------|---------------|---------|
| `scale` | Factor de escala para valores numéricos | `1.0` | Cualquier número decimal |
| `return_type` | Cómo formatear los datos devueltos | `value` | `value` (numérico/tamaño), `string` (texto), `snbt` (NBT formateado), `json` (formato JSON) |

## Explicación de los tipos de retorno

- **`value`** - Devuelve valores numéricos o tamaños (predeterminado)
  - Para números: devuelve el número (opcionalmente escalado)
  - Para cadenas: devuelve la longitud de la cadena
  - Para listas/arrays: devuelve el número de elementos
  - Para compounds: devuelve el número de etiquetas

- **`string`** - Devuelve el valor de texto real de los datos NBT

- **`snbt`** - Devuelve los datos en formato SNBT (Stringified NBT)

- **`json`** - Devuelve los datos en formato JSON (solo para etiquetas compound)

## Ejemplos

### Obtener la salud del jugador
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### Obtener el nivel de hambre del jugador
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### Obtener la coordenada X del jugador
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### Obtener el objeto de la primera ranura de la barra rápida
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### Obtener datos de un bloque en una posición concreta
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### Obtener el porcentaje de salud escalado (Health * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## Cómo encontrar rutas NBT disponibles

### Método 1: Usar el comando `/data get` (recomendado)

La forma más sencilla de descubrir rutas NBT disponibles es usar el comando `/data get` en el juego sin especificar una ruta:

1. **Para entidades:** `/data get entity @p`
2. **Para bloques:** `/data get block <x> <y> <z>`

Esto mostrará todos los datos NBT disponibles para ese objetivo, enseñándote las rutas exactas que puedes usar.

#### Entender la salida

Cuando ejecutes `/data get entity @p`, verás una salida similar a esta:

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

Para extraer una ruta válida de esta salida:

1. **Valores simples** - Usa directamente el nombre de la clave:
   - `Health: 20.0f` → Ruta: `Health`
   - Ejemplo: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **Valores anidados** - Usa la notación con puntos para acceder a datos anidados:
   - `abilities: {walkSpeed: 0.1f}` → Ruta: `abilities.walkSpeed`
   - Ejemplo: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **Valores de array** - Usa corchetes con números de índice:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Ruta para el movimiento Y: `Motion[1]`
   - Ejemplo: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### Método 2: Mod NBT Autocomplete

Para facilitar el descubrimiento de rutas NBT, considera instalar el mod **NBT Autocomplete**:
- Disponible para Fabric y Forge (Minecraft 1.21.x)
- Ofrece sugerencias de autocompletado en el juego mientras escribes comandos
- Muestra los nombres y tipos de etiquetas disponibles
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## Rutas NBT comunes

### Entidad jugador
- `Health` - Salud actual (float)
- `foodLevel` - Nivel de hambre (int, 0-20)
- `foodSaturationLevel` - Nivel de saturación (float)
- `XpLevel` - Nivel de experiencia (int)
- `XpP` - Progreso de experiencia (float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - Coordenadas X, Y, Z
- `Inventory` - Array del inventario del jugador
- `SelectedItemSlot` - Ranura de la barra rápida seleccionada actualmente (int, 0-8)

### NBT común de bloques
- `Items` - Contenido del contenedor (cofres, hornos, etc.)
- `CustomName` - Nombre personalizado del bloque
- `Lock` - Cadena de bloqueo para contenedores

### Ejemplos comunes de NBT modificado
- **Mods de magia**: a menudo guardan el maná como `playerMana`, `mana.current` o algo similar
- **Mods de tecnología**: valores de energía como `energy`, `forgeEnergy` o `energyStorage.energy`
- **Mods de rol**: estadísticas personalizadas como `customStats.strength`, `rpgAttributes.level`

Para encontrar rutas NBT modificadas, usa `/data get entity @p` mientras el mod esté activo y busca las etiquetas personalizadas añadidas por el mod.

## Limitaciones

- **Sin acceso a storage en el cliente** - La fuente de datos storage no está compatible en el lado del cliente (solo lado del servidor)
- **Rendimiento** - Consultar datos NBT con frecuencia puede afectar al rendimiento
- Devuelve una cadena vacía si la ruta no es válida o si no se puede acceder a los datos

## Consejos

1. Prueba siempre primero tus rutas NBT en el juego usando `/data get`
2. Usa el parámetro `scale` para convertir valores a porcentajes u otros formatos útiles
3. Recuerda que algunos datos NBT pueden no estar sincronizados con el cliente
4. Los selectores de entidad están limitados a entidades dentro de la distancia de renderizado
5. Para contenido modificado, consulta la documentación del mod o usa `/data get` para descubrir rutas NBT personalizadas
