---
title: Compartición de datos Cliente < - > Servidor
description: >-
  Envía y recibe datos personalizados entre el servidor y el cliente con
  FancyMenu.
---

# Datos FM

El sistema "Datos FM" te permite enviar datos de texto personalizados entre el servidor y el cliente.

Cada subcomando de `/fmdata` requiere **nivel de permiso 2** (Game Master / OP nivel 2).

Cada mensaje de Datos FM tiene:

1. Un **identificador de datos** (qué tipo de mensaje es)
2. Un **valor de datos** (el contenido real)

Ejemplo de idea:

- Identificador: `hud.food`
- Datos: `18/20`

# Inicio rápido

1. El servidor envía datos con `/fmdata send ...`
2. El cliente los recibe con el oyente de FancyMenu **On FM Data Received**
3. El cliente también puede enviar datos de vuelta con la acción **Send FM Data To Server**
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
/fmdata send @a "actualización del valor de comida" "18 de 20"
```

Notas:

- `<target_players>` admite nombres de jugadores y selectores como `@a`, `@p` y `@s`
- Usa comillas para valores con espacios

# Cliente: recibir datos

Usa el oyente de FancyMenu:

- **On FM Data Received**

Variables disponibles:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` es:

- La IP del servidor en multijugador
- `integrated_server` en un jugador

Casos de uso habituales:

- Actualizar elementos de texto
- Disparar acciones del menú
- Ejecutar lógica basada en el identificador/datos entrantes

# Cliente -> Servidor

Usa la acción de FancyMenu:

- **Send FM Data To Server**

La acción tiene 2 entradas:

1. Identificador de datos
2. Datos

El servidor puede procesar después los datos entrantes con `/fmdata listener ...`.

# Oyentes del servidor

Los oyentes del servidor escuchan los datos entrantes de los clientes y pueden ejecutar uno o varios comandos cuando se activan.

Los oyentes del servidor se guardan y siguen activos después de reiniciar.

Gestionarlos con:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Sintaxis de añadir / editar

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Sintaxis de eliminación

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

- `ignore_case_identifier` y `ignore_case_data` son conmutadores true/false
- `listen_for_identifier` admite el comodín `*` (coincide siempre)
- `listen_for_data` admite el comodín `*` (coincide siempre)
- `fire_for_player` usa selectores de jugador normales (por ejemplo `@a`, `@p`, `Player761`)

## Comandos al activarse

`commands_to_execute_on_fire` es un único campo de texto.

- Separa varios comandos con `|||`
- Escapa un separador literal como `\|\|\|`

Aquí puedes usar dos marcadores de posición especiales que se sustituyen justo antes de ejecutar los comandos:

- `%fm_sender%` -> jugador que envió los Datos FM
- `%fm_data%` -> valor de datos recibido del cliente

Los comandos se ejecutan como comandos del servidor.

## Comandos de ejemplo

Reaccionar a una pulsación de botón de cualquier jugador:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% ha pulsado el botón\"}"
```

Ejecutar varios comandos cuando los datos contienen `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Recompensa de %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Datos de bienvenida

Los datos de bienvenida envían Datos FM a los jugadores que coincidan cuando entran al servidor.

Gestionar entradas con:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Sintaxis de añadir / editar

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Sintaxis de eliminación

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Notas:

- `<target_player>` admite selectores normales como `@a`, `@p`, `@s`
- Los datos se envían a los jugadores que coincidan cuando entran
- Las entradas se guardan y se cargan automáticamente

## Comandos de ejemplo

Enviar datos de bienvenida a todos los jugadores que entren:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "¡Bienvenido!"
```

Enviar datos de bienvenida solo a un jugador:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Ventajas VIP activadas"
```

# Buenas prácticas

1. Usa identificadores claros como `hud.food`, `menu.shop.open`, `quest.progress`.
2. Mantén un formato de datos coherente para cada identificador.
3. Empieza por algo sencillo: prueba con `/fmdata send` antes de crear oyentes complejos.
4. Usa `@a` solo cuando realmente quieras un comportamiento global.
5. Usa `/fmdata listener list` y `/fmdata welcome_data list` para mantener las configuraciones limpias.
