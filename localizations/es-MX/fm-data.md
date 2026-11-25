---
title: Compartir datos entre cliente y servidor
description: >-
  Envía y recibe datos personalizados entre el servidor y el cliente con
  FancyMenu.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# FM Data

El sistema «FM Data» te permite enviar datos de texto personalizados entre el servidor y el cliente.

Todos los subcomandos de `/fmdata` requieren **nivel de permiso 2** (Game Master / nivel OP 2).

Cada mensaje de FM Data incluye:

1. Un **identificador de datos** (el tipo de mensaje)
2. Un **valor de datos** (el contenido en sí)

Ejemplo:

- Identificador: `hud.food`
- Datos: `18/20`

# Inicio rápido

1. El servidor envía datos con `/fmdata send ...`
2. El cliente los recibe mediante el listener de FancyMenu **Al recibir FM Data**
3. El cliente también puede enviar datos de vuelta con la acción **Enviar FM Data al servidor**
4. El servidor puede reaccionar automáticamente con `/fmdata listener ...`
5. El servidor puede enviar datos automáticamente al entrar con `/fmdata welcome_data ...`

# Servidor -> Cliente

Usa:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Ejemplos:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Notas:

- `<target_players>` admite nombres de jugadores y selectores como `@a`, `@p` y `@s`
- Usa comillas para los valores que contengan espacios

# Cliente: recibir datos

Usa el listener de FancyMenu:

- **Al recibir FM Data**

Variables disponibles:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` corresponde a:

- La IP del servidor en multijugador
- `integrated_server` en un jugador

Usos comunes:

- Actualizar elementos de texto
- Activar acciones de menú
- Ejecutar lógica según el identificador o los datos recibidos

# Cliente -> Servidor

Usa la acción de FancyMenu:

- **Enviar FM Data al servidor**

La acción tiene 2 entradas:

1. Identificador de datos
2. Datos

Después, el servidor puede procesar los datos recibidos con `/fmdata listener ...`.

# Listeners del servidor

Los listeners del servidor esperan datos de los clientes y pueden ejecutar uno o varios comandos cuando se activan.

Los listeners del servidor se guardan y permanecen activos después de reiniciar.

Adminístralos con:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Sintaxis para agregar o editar

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Sintaxis para eliminar

```mcfunction
/fmdata listener remove <listener_name>
```

## Tipos de coincidencia

`matching_type_identifier` y `matching_type_data` pueden ser:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Reglas de coincidencia

- `ignore_case_identifier` y `ignore_case_data` son opciones de verdadero/falso
- `listen_for_identifier` admite el comodín `*` (siempre coincide)
- `listen_for_data` admite el comodín `*` (siempre coincide)
- `fire_for_player` usa los selectores normales de jugadores (por ejemplo, `@a`, `@p`, `Player761`)

## Comandos al activarse

`commands_to_execute_on_fire` es una sola entrada de texto.

- Separa varios comandos con `|||`
- Escapa un separador literal como `\|\|\|`

Puedes usar dos marcadores especiales que se reemplazan justo antes de ejecutar los comandos:

- `%fm_sender%` -> jugador que envió FM Data
- `%fm_data%` -> valor de datos recibido del cliente

Los comandos se ejecutan como comandos del servidor.

## Ejemplos de comandos

Reacciona cuando cualquier jugador presione un botón:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Ejecuta varios comandos cuando los datos contengan `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Datos de bienvenida

Los datos de bienvenida envían FM Data a los jugadores que coincidan cuando entren al servidor.

Administra las entradas con:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Sintaxis para agregar o editar

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Sintaxis para eliminar

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Notas:

- `<target_player>` admite selectores normales como `@a`, `@p` y `@s`
- Los datos se envían a los jugadores que coincidan cuando entren al servidor
- Las entradas se guardan y cargan automáticamente

## Ejemplos de comandos

Envía datos de bienvenida a todos los jugadores que entren:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Envía datos de bienvenida a un solo jugador:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Exportar para IA

Para pedir ayuda a Alice o a otra IA, exporta los listeners y los datos de bienvenida del servidor con [Exportar para IA](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` envía un mensaje al chat que permite copiar la exportación al hacer clic. `file` la guarda en el servidor, en `fancymenu_data/ai_exports/`.

# Buenas prácticas

1. Usa identificadores claros como `hud.food`, `menu.shop.open`, `quest.progress`.
2. Mantén un formato de datos uniforme para cada identificador.
3. Empieza con algo sencillo: prueba con `/fmdata send` antes de crear listeners complejos.
4. Usa `@a` solo cuando realmente quieras que la acción sea global.
5. Usa `/fmdata listener list` y `/fmdata welcome_data list` para mantener la configuración ordenada.
