---
title: Comandos
description: Los comandos de FancyMenu y cómo usarlos.
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# Comandos

FancyMenu agrega algunos comandos al juego que pueden ser muy útiles al combinarlos con otros mods, como FTB Quests.

> [!WARNING]
> ¡FancyMenu debe estar instalado en el **SERVIDOR** (y en el cliente) para usar comandos en multijugador!

## Jugadores objetivo y permisos

El argumento de jugador objetivo de `/openguiscreen`, `/closeguiscreen` y `/fmlayout` es opcional. Si un jugador lo omite, el comando afecta a ese jugador. Si se especifica un objetivo, se pueden usar nombres de jugadores normales y selectores como `@a`.

- Especificar el argumento de objetivo en `/openguiscreen` o `/closeguiscreen` requiere el **nivel de permiso 2** (Game Master / OP nivel 2), incluso si indica a quien ejecuta el comando.
- Especificar el argumento de objetivo en `/fmlayout` requiere el **nivel de permiso 3** (administrador / OP nivel 3), incluso si indica a quien ejecuta el comando.
- Todos los subcomandos de `/fmdata` requieren el **nivel de permiso 2** (Game Master / OP nivel 2).

En los tres comandos con objetivos opcionales, omitir el objetivo solo funciona si quien ejecuta el comando es un jugador. La consola del servidor debe especificar un objetivo y cumplir con el requisito de permisos de ese argumento.

## /openguiscreen

El comando `/openguiscreen` abre una interfaz de Vanilla, de un mod o una [interfaz gráfica personalizada](/custom-guis). Puede dirigirse a otros jugadores si FancyMenu está instalado en el servidor y en sus clientes.

Consulta [Abrir interfaces gráficas mediante comandos](/opengui-command) e [Identificadores de pantalla](/screen-identifiers).

No todas las pantallas de los mods se pueden crear directamente. FancyMenu muestra un error cuando la pantalla objetivo no es compatible. En un diseño local, usa [**Imitar botón de Vanilla/mod**](/action-scripts#mimic-vanillamod-button) en el widget que normalmente la abre.

**Uso:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

El comando `/closeguiscreen` cierra la pantalla actual de quien ejecuta el comando o de los jugadores seleccionados. Es útil con mods de misiones, eventos o automatización que pueden ejecutar comandos.

**Uso:** `/closeguiscreen [<target_players>]`

## /fmlayout

El comando `/fmlayout` establece si un diseño está habilitado en uno o más clientes. Usa el nombre del diseño exactamente como aparece en FancyMenu y pon entre comillas los nombres que contengan espacios.

**Uso:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Ejemplos:

- `/fmlayout quest_complete true` habilita `quest_complete` para el jugador que ejecuta el comando.
- `/fmlayout quest_complete false @a` lo deshabilita para todos los jugadores en línea. Especificar el argumento de objetivo requiere el nivel de permiso 3.

## /fmvariable

El comando `/fmvariable` establece y consulta [variables de FancyMenu](/variables).

Para ejecutar este comando como otro jugador, usa el comando de Vanilla `/execute as`:
`/execute as ExamplePlayer run fmvariable ...`

**Uso:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Consultar

Para **consultar el valor de una variable**, usa el subcomando `get` así:
`/fmvariable get some_variable`

Después, el valor de esta variable aparecerá en el chat.

### Establecer

Para **establecer una variable**, pon el valor booleano de la respuesta en el chat antes del valor nuevo:
`/fmvariable set some_variable true new_value`

El argumento `send_chat_feedback` determina si FancyMenu confirma el cambio en el chat. El argumento `set_to_value` consume el resto del comando, así que el valor puede contener espacios. Por ejemplo, `/fmvariable set greeting false Hola desde FancyMenu` guarda `Hola desde FancyMenu` sin enviar un mensaje de confirmación.

## /fmdata

El comando `/fmdata` envía datos personalizados entre el servidor y los clientes de FancyMenu, administra los escuchas del lado del servidor, configura los datos que se envían cuando los jugadores se conectan y exporta esta configuración para [chats de IA](/export-for-ai#servers). Todos los subcomandos de `/fmdata` requieren el nivel de permiso 2.

Consulta [Datos de FM](/fm-data) para ver todos los subcomandos, la sintaxis y los ejemplos.
