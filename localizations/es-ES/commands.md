---
title: Comandos
description: Los comandos de FancyMenu y cómo usarlos.
---

# Comandos

FancyMenu añade algunos comandos al juego que pueden ser muy útiles al combinarlos con otros mods como FTB Quests.

> [!WARNING]
> ¡FancyMenu debe estar en el **SERVIDOR** (y en el cliente) para usar comandos en Multijugador!

## Jugadores objetivo y permisos

El argumento de jugador objetivo de `/openguiscreen`, `/closeguiscreen` y `/fmlayout` es opcional. Cuando un jugador lo omite, el comando afecta a ese jugador. Cuando se proporciona un objetivo, se pueden usar nombres de jugador normales y selectores como `@a`.

- Proporcionar el argumento de objetivo a `/openguiscreen` o `/closeguiscreen` requiere **nivel de permiso 2** (Game Master / nivel OP 2), incluso si nombra al origen del comando.
- Proporcionar el argumento de objetivo a `/fmlayout` requiere **nivel de permiso 3** (Admin / nivel OP 3), incluso si nombra al origen del comando.
- Cada subcomando de `/fmdata` requiere **nivel de permiso 2** (Game Master / nivel OP 2).

Para los tres comandos con objetivos opcionales, omitir el objetivo solo funciona cuando la fuente del comando es un jugador. La consola del servidor debe proporcionar un objetivo y cumplir el requisito de permiso del argumento objetivo.

## /openguiscreen

El comando `/openguiscreen` abre una GUI de Vanilla, de un mod o una [GUI personalizada](./custom-guis). Puede dirigirse a otros jugadores cuando FancyMenu está instalado en el servidor y en sus clientes.

Consulta [Abrir GUIs mediante comando](./opengui-command) y [Identificadores de pantalla](./screen-identifiers).

No todas las pantallas de mods pueden crearse directamente. FancyMenu muestra un error cuando una pantalla de destino no es compatible. En un diseño local, usa [**Botón imitar Vanilla/Mod**](./action-scripts#mimic-vanillamod-button-mimicbutton) en el widget que normalmente la abre.

**Uso:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

El comando `/closeguiscreen` cierra la pantalla actual para la fuente del comando o para los jugadores seleccionados. Es útil con mods de misiones, eventos o automatización que puedan ejecutar comandos.

**Uso:** `/closeguiscreen [<target_players>]`

## /fmlayout

El comando `/fmlayout` establece si un diseño está activado en uno o más clientes. Usa el nombre del diseño exactamente como aparece en FancyMenu y pon entre comillas los nombres que contengan espacios.

**Uso:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Ejemplos:

- `/fmlayout quest_complete true` activa `quest_complete` para el jugador que ejecuta el comando.
- `/fmlayout quest_complete false @a` lo desactiva para todos los jugadores conectados. Proporcionar el argumento de objetivo requiere nivel de permiso 3.

## /fmvariable

El comando `/fmvariable` establece y lee [variables de FancyMenu](./variables).

Para ejecutar este comando como otro jugador, usa el comando `/execute as` de Vanilla:
`/execute as ExamplePlayer run fmvariable ...`

**Uso:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Obtener

Para **obtener el valor de una variable**, usa el subcomando `get` así:
`/fmvariable get some_variable`

Entonces el valor de esta variable se mostrará en tu chat.

### Establecer

Para **establecer una variable**, coloca el booleano de confirmación en chat antes del nuevo valor:
`/fmvariable set some_variable true new_value`

El argumento `send_chat_feedback` controla si FancyMenu confirma el cambio en el chat. El argumento `set_to_value` consume el resto del comando, por lo que el valor puede contener espacios. Por ejemplo, `/fmvariable set greeting false Hello from FancyMenu` almacena `Hello from FancyMenu` sin mostrar una confirmación de éxito.

## /fmdata

El comando `/fmdata` envía datos personalizados entre el servidor y los clientes de FancyMenu, gestiona escuchadores del lado del servidor y configura los datos que se envían cuando los jugadores se conectan. Cada subcomando de `/fmdata` requiere nivel de permiso 2.

Consulta [FM Data](./fm-data) para ver todos los subcomandos, la sintaxis y los ejemplos.
