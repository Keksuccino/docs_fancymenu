---
title: Comandos
description: Los comandos de FancyMenu y cómo usarlos.
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# Comandos

FancyMenu añade algunos comandos al juego que pueden resultar muy útiles al combinarlos con otros mods, como FTB Quests.

> [!WARNING]
> ¡FancyMenu debe estar instalado en el **SERVIDOR** (y en el cliente) para usar comandos en multijugador!

## Jugadores objetivo y permisos

El argumento del jugador objetivo de `/openguiscreen`, `/closeguiscreen` y `/fmlayout` es opcional. Si se omite, el comando afecta al jugador que lo ejecuta. Si se indica un objetivo, se pueden usar nombres de jugadores y selectores como `@a`.

- Indicar el argumento de objetivo en `/openguiscreen` o `/closeguiscreen` requiere el **nivel de permiso 2** (Game Master / nivel OP 2), aunque se indique como objetivo al jugador que ejecuta el comando.
- Indicar el argumento de objetivo en `/fmlayout` requiere el **nivel de permiso 3** (Admin / nivel OP 3), aunque se indique como objetivo al jugador que ejecuta el comando.
- Todos los subcomandos de `/fmdata` requieren el **nivel de permiso 2** (Game Master / nivel OP 2).

En los tres comandos que admiten un objetivo opcional, omitirlo solo funciona si quien ejecuta el comando es un jugador. La consola del servidor debe indicar un objetivo y cumplir el requisito de permisos del argumento de objetivo.

## /openguiscreen

El comando `/openguiscreen` abre una pantalla de Vanilla, de un mod o una [GUI personalizada](/custom-guis). Puede dirigirse a otros jugadores si FancyMenu está instalado en el servidor y en sus clientes.

Consulta [Abrir GUI mediante comandos](/opengui-command) e [Identificadores de pantalla](/screen-identifiers).

No todas las pantallas de los mods se pueden crear directamente. FancyMenu muestra un error si la pantalla de destino no es compatible. En un diseño local, usa [**Imitar botón de Vanilla/mod**](/action-scripts#mimic-vanillamod-button) en el widget que normalmente la abre.

**Uso:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

El comando `/closeguiscreen` cierra la pantalla actual de quien ejecuta el comando o de los jugadores seleccionados. Es útil con mods de misiones, eventos o automatización que puedan ejecutar comandos.

**Uso:** `/closeguiscreen [<target_players>]`

## /fmlayout

El comando `/fmlayout` activa o desactiva un diseño en uno o varios clientes. Usa el nombre del diseño exactamente como aparece en FancyMenu y escribe entre comillas los nombres que contengan espacios.

**Uso:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Ejemplos:

- `/fmlayout quest_complete true` activa `quest_complete` para el jugador que ejecuta el comando.
- `/fmlayout quest_complete false @a` lo desactiva para todos los jugadores conectados. Indicar el argumento de objetivo requiere el nivel de permiso 3.

## /fmvariable

El comando `/fmvariable` permite establecer y consultar [variables de FancyMenu](/variables).

Para ejecutar este comando como otro jugador, usa el comando Vanilla `/execute as`:
`/execute as ExamplePlayer run fmvariable ...`

**Uso:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Consultar

Para **consultar el valor de una variable**, usa el subcomando `get` así:
`/fmvariable get some_variable`

A continuación, el valor de esta variable aparecerá en el chat.

### Establecer

Para **establecer una variable**, escribe el valor booleano de confirmación en el chat antes del nuevo valor:
`/fmvariable set some_variable true new_value`

El argumento `send_chat_feedback` determina si FancyMenu confirma el cambio en el chat. El argumento `set_to_value` consume el resto del comando, así que el valor puede contener espacios. Por ejemplo, `/fmvariable set greeting false Hola desde FancyMenu` guarda `Hola desde FancyMenu` sin mostrar un mensaje de confirmación.

## /fmdata

El comando `/fmdata` envía datos personalizados entre el servidor y los clientes de FancyMenu, gestiona los listeners del servidor, configura los datos que se envían cuando se conectan jugadores y exporta esta configuración para [chats de IA](/export-for-ai#servers). Todos los subcomandos de `/fmdata` requieren el nivel de permiso 2.

Consulta [Datos FM](/fm-data) para ver todos los subcomandos, la sintaxis y algunos ejemplos.
