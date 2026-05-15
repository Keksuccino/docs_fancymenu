---
title: Compartir datos entre cliente y servidor
description: >-
  Envía y recibe datos personalizados entre el servidor y el cliente con
  FancyMenu.
---

# Datos de FM

El sistema de "Datos de FM" te permite enviar datos de texto personalizados entre el servidor y el cliente.

Cada mensaje de Datos de FM tiene:

1. Un **identificador de datos** (qué tipo de mensaje es)
2. Un **valor de datos** (el contenido real)

Ejemplo:

- Identificador: `hud.food`
- Datos: `18/20`

# Inicio rápido

1. El servidor envía datos con `/fmdata send ...`
2. El cliente los recibe con el listener de FancyMenu **On FM Data Received**
3. El cliente también puede enviar datos de vuelta con la acción **Send FM Data To Server**
4. El servidor puede reaccionar automáticamente con `/fmdata listener ...`
5. El servidor puede enviar datos automáticamente al entrar con `/fmdata welcome_data ...`

# Servidor -> Cliente

Usa:

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

Ejemplos:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Notas:

- `<target_player>` admite selectores normales de jugadores como `@a`, `@p`, `@s`
- Usa comillas para valores con espacios

# Cliente: recibir datos

Usa el listener de FancyMenu:

- **On FM Data Received**

Variables disponibles:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` es:

- La IP del servidor en multijugador
- `integrated_server` en un jugador

Casos de uso comunes:

- Actualizar elementos de texto
- Disparar acciones del menú
- Ejecutar lógica según el identificador o los datos recibidos

# Cliente -> Servidor

Usa la acción de FancyMenu:

- **Send FM Data To Server**

La acción tiene 2 entradas:

1. Identificador de datos
2. Datos

Después, el servidor puede procesar los datos entrantes con `/fmdata listener ...`.

# Listeners del servidor

Los listeners del servidor escuchan los datos entrantes de los clientes y pueden ejecutar uno o varios comandos cuando se activan.

Los listeners del servidor se guardan y permanecen activos después de reiniciar.

Adminístralos con:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Sintaxis para agregar / editar

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

- `ignore_case_identifier` y `ignore_case_data` son interruptores true/false
- `listen_for_identifier` admite el comodín `*` (siempre coincide)
- `listen_for_data` admite el comodín `*` (siempre coincide)
- `fire_for_player` usa selectores normales de jugadores (por ejemplo `@a`, `@p`, `Player761`)

## Comandos al activarse

`commands_to_execute_on_fire` es un solo campo de texto.

- Separa varios comandos con `|||`
- Escapa un separador literal como `\|\|\|`

Aquí puedes usar dos marcadores especiales que se reemplazan justo antes de ejecutar los comandos:

- `%fm_sender%` -> jugador que envió los Datos de FM
- `%fm_data%` -> valor de datos recibido del cliente

Los comandos se ejecutan como comandos del servidor.

## Ejemplos de comandos

Responder a la pulsación de un botón de cualquier jugador:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Ejecutar varios comandos cuando los datos contengan `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Datos de bienvenida

Los datos de bienvenida envían Datos de FM a los jugadores que coincidan cuando se unen.

Administra las entradas con:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Sintaxis para agregar / editar

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

- `<target_player>` admite selectores normales como `@a`, `@p`, `@s`
- Los datos se envían a los jugadores coincidentes cuando se unen
- Las entradas se guardan y cargan automáticamente

## Ejemplos de comandos

Enviar datos de bienvenida a todos los jugadores que se unan:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "¡Bienvenido!"
```

Enviar datos de bienvenida solo a un jugador:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Privilegios VIP activados"
```

# Mejores prácticas

1. Usa identificadores claros como `hud.food`, `menu.shop.open`, `quest.progress`.
2. Mantén un formato de datos consistente para cada identificador.
3. Empieza simple: prueba con `/fmdata send` antes de crear listeners complejos.
4. Usa `@a` solo cuando de verdad quieras un comportamiento global.
5. Usa `/fmdata listener list` y `/fmdata welcome_data list` para mantener limpias las configuraciones.
