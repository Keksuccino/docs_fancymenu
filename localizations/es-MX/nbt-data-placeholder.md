---
title: Marcador de posición de datos NBT
description: 'Lee datos NBT de entidades, bloques y almacenamiento.'
---

# Marcadores de posición de datos NBT

FancyMenu proporciona dos marcadores de posición NBT:

| Marcador de posición | Se ejecuta en | Datos disponibles |
|---|---|---|
| `nbt_data_get` | Cliente | Entidades y entidades de bloque visibles para el cliente |
| `nbt_data_get_server` | Servidor | Objetivos de `/data get` de Vanilla; requiere FancyMenu en el servidor |

# Marcador de posición del lado del cliente

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Valores

| Valor | Requerido | Descripción |
|---|---|---|
| `source_type` | Sí | `entity` o `block` |
| `entity_selector` | Para entidades | Selector del lado del cliente, UUID o nombre exacto de la entidad |
| `block_pos` | Para bloques | Tres coordenadas enteras absolutas, como `100 64 -200` |
| `nbt_path` | Sí | Ruta NBT, como `Health`, `Pos[0]` o `Inventory[0].id` |
| `scale` | No | Multiplica los resultados numéricos de `value`; por defecto `1.0` |
| `return_type` | No | `value`, `string`, `snbt` o `json`; por defecto `value` |

Las posiciones de bloques del lado del cliente no admiten coordenadas `~` ni `^`.

## Selectores de entidades del cliente

| Selector | Objetivos iniciales | Orden predeterminado |
|---|---|---|
| `@s` | Jugador local | Uno mismo |
| `@p` | Jugadores | Más cercano |
| `@a` | Jugadores | Orden de iteración del cliente |
| `@r` | Jugadores | Aleatorio |
| `@e` | Todas las entidades visibles para el cliente | Orden de iteración del cliente |

`@e` no selecciona la entidad más cercana a menos que agregues `sort=nearest`. También se admite la búsqueda directa por UUID y por nombre exacto de la entidad.

Opciones de selector compatibles:

| Opción | Descripción |
|---|---|
| `type` | ID de entidad; usa `!` como prefijo para excluir |
| `name` | Nombre visible exacto; usa `!` como prefijo para excluir |
| `tag` | Etiqueta de la entidad; usa `!` como prefijo para excluir |
| `limit` | Límite positivo de resultados |
| `sort` | `nearest`, `furthest`, `random` o `arbitrary` |
| `distance` | Rango de distancia de Vanilla, como `..10` o `5..20` |
| `x`, `y`, `z` | Origen de búsqueda; acepta valores absolutos y desplazamientos `~` |
| `dx`, `dy`, `dz` | Tamaño de la caja de búsqueda desde el origen |

Las coordenadas locales `^` y otras opciones de selector de Vanilla no son compatibles con el marcador de posición del cliente.

Ejemplo:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## Tipos de retorno

| Tipo | Resultado |
|---|---|
| `value` | Las etiquetas numéricas se formatean numéricamente y aplican `scale`; las etiquetas de texto regresan su texto; otras etiquetas regresan texto tipo SNBT |
| `string` | Regresa el valor de cadena de la etiqueta, o una cadena vacía cuando la etiqueta no tiene un valor de cadena |
| `snbt` | Regresa la representación SNBT de la etiqueta |
| `json` | Solo para etiquetas compuestas: regresa un componente de texto serializado de Minecraft que contiene salida NBT legible |

El modo `json` del lado del cliente no es una conversión directa de NBT a JSON.

## Ejemplos

Hambre del jugador:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

ID del primer objeto de la barra rápida:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

Cantidad de un objeto de entidad de bloque:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# Marcador de posición del lado del servidor

`nbt_data_get_server` sigue el comportamiento de `/data get` del servidor y admite:

- Selectores completos de entidades del lado del servidor.
- Objetivos de bloque con coordenadas absolutas, relativas (`~`) o locales (`^`).
- Almacenamiento de comandos mediante `source_type:"storage"`.

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

El marcador de posición devuelve un valor vacío hasta que llega la respuesta del servidor. Las respuestas se almacenan en caché por un momento para evitar solicitudes excesivas.

# Cómo encontrar rutas NBT

Usa el comando correspondiente sin una ruta NBT para inspeccionar los datos disponibles:

```text
/data get entity @s
/data get block 100 64 -200
```

Los resultados del lado del cliente se limitan a los datos sincronizados con el cliente. Los objetivos o rutas no válidos devuelven una cadena vacía y escriben los detalles en `logs/latest.log`.
