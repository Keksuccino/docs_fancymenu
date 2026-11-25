---
title: Compartir datos entre cliente y servidor
description: >-
  Envía y recibe datos personalizados entre el servidor y el cliente con
  FancyMenu.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# Datos de FM

El sistema «Datos de FM» permite enviar datos de texto personalizados entre el servidor y el cliente.

Todos los subcomandos de `/fmdata` requieren **nivel de permiso 2** (Maestro de juego / nivel 2 de OP).

Cada mensaje de Datos de FM incluye:

1. Un **identificador de datos** (el tipo de mensaje)
2. Un **valor de datos** (el contenido propiamente dicho)

Ejemplo:

- Identificador: `hud.food`
- Datos: `18/20`

# Inicio rápido

1. El servidor envía datos con `/fmdata send ...`
2. El cliente los recibe mediante el listener de FancyMenu **Al recibir datos de FM**
3. El cliente también puede enviar datos de vuelta con la acción **Enviar datos de FM al servidor**
4. El servidor puede reaccionar automáticamente con `/fmdata listener ...`
5. El servidor puede enviar datos automáticamente cuando un jugador se conecta con `/fmdata welcome_data ...`

# Del servidor al cliente

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

- **Al recibir datos de FM**

Variables disponibles:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` contiene:

- La IP del servidor en multijugador
- `integrated_server` en un mundo de un jugador

Usos habituales:

- Actualizar elementos de texto
- Activar acciones de menú
- Ejecutar lógica en función del identificador o los datos recibidos

# Del cliente al servidor

Usa la acción de FancyMenu:

- **Enviar datos de FM al servidor**

La acción tiene 2 campos:

1. Identificador de datos
2. Datos

A continuación, el servidor puede procesar los datos recibidos con `/fmdata listener ...`.

# Listeners del servidor

Los listeners del servidor esperan datos entrantes de los clientes y pueden ejecutar uno o varios comandos cuando se activan.

Los listeners del servidor se guardan y siguen activos después de reiniciar el servidor.

Adminístralos con:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Sintaxis para añadir o editar

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

- `ignore_case_identifier` y `ignore_case_data` son opciones de tipo verdadero/falso
- `listen_for_identifier` admite el comodín `*` (siempre coincide)
- `listen_for_data` admite el comodín `*` (siempre coincide)
- `fire_for_player` usa los selectores habituales de jugadores (por ejemplo, `@a`, `@p`, `Player761`)

## Comandos al activarse

`commands_to_execute_on_fire` es un único campo de texto.

- Separa los comandos con `|||` si quieres ejecutar varios
- Escapa un separador literal como `\|\|\|`

Puedes usar dos marcadores especiales que se sustituirán justo antes de ejecutar los comandos:

- `%fm_sender%` -> jugador que envió los Datos de FM
- `%fm_data%` -> valor de los datos recibidos del cliente

Los comandos se ejecutan como comandos del servidor.

## Ejemplos de comandos

Reaccionar a la pulsación de un botón de cualquier jugador:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Ejecutar varios comandos cuando los datos contengan `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Datos de bienvenida

Los datos de bienvenida envían Datos de FM a los jugadores que coincidan cuando se conectan.

Administra las entradas con:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Sintaxis para añadir o editar

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

- `<target_player>` admite selectores habituales como `@a`, `@p` y `@s`
- Los datos se envían a los jugadores que coincidan cuando se conectan
- Las entradas se guardan y cargan automáticamente

## Ejemplos de comandos

Enviar datos de bienvenida a todos los jugadores que se conecten:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Enviar datos de bienvenida solo a un jugador:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Exportar para IA

Para pedir ayuda a Alice o a otra IA, exporta los listeners y los datos de bienvenida del servidor con [Exportar para IA](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` envía un mensaje al chat que copia la exportación al hacer clic. `file` la guarda en el servidor, en `fancymenu_data/ai_exports/`.

# Buenas prácticas

1. Usa identificadores claros, como `hud.food`, `menu.shop.open` o `quest.progress`.
2. Mantén un formato de datos coherente para cada identificador.
3. Empieza con algo sencillo: prueba con `/fmdata send` antes de crear listeners complejos.
4. Usa `@a` solo si de verdad quieres que la acción afecte a todos los jugadores.
5. Usa `/fmdata listener list` y `/fmdata welcome_data list` para mantener ordenada la configuración.
