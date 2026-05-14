---
title: Comandos
description: Los comandos de FancyMenu y cómo usarlos.
---

# Comandos

FancyMenu agrega algunos comandos al juego que pueden ser muy útiles cuando los combinas con otros mods como FTB Quests.

> ¡FancyMenu necesita estar en el **SERVIDOR** (y en el cliente) para usar comandos en Multijugador!
{.is-warning}

## /openguiscreen

El comando `/openguiscreen` te permite abrir una GUI (vanilla/mod y GUIs personalizadas).
Incluso puede abrir GUIs de forma remota para otros jugadores cuando FancyMenu está instalado tanto en el servidor como en los clientes.

Para una descripción más detallada de este comando, revisa la página [Abrir GUIs por comando](/opengui-command).

Este comando no funcionará con todas las pantallas, especialmente con pantallas de mods. Si el comando falla al abrir una pantalla, mostrará un error. No hay mucho que puedas hacer en ese caso, porque probablemente sea una pantalla demasiado compleja para que FancyMenu la abra automáticamente.

Tampoco agregaré compatibilidad manualmente para pantallas de mods, porque agregar compatibilidad para todos los mods que existen me llevaría muchísimo tiempo, lo siento.

**Uso:** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

El comando `/closeguiscreen` te permite cerrar la GUI actual.

¿Eh? ¿Dices que esto no sirve para nada?
Bueno sí, pero en realidad no.

Este comando es útil cuando usas mods que activan comandos en acciones específicas.
Así que sí, este comando es completamente inútil si lo usas sin otros mods, ¡pero puede ser muy útil si tienes instalados los mods correctos!

**Uso:** `/closeguiscreen <target_player>`

## /fmvariable

El comando `/fmvariable` te permite establecer y obtener variables de FancyMenu.

Para ejecutar este comando como otro jugador en servidores, puedes usar el comando de Vanilla `/execute as`.
Así que, digamos que quieres ejecutar el comando `/fmvariable` como el jugador `ExamplePlayer`. En ese caso escribirías:
`/execute as ExamplePlayer run fmvariable...`.

**Uso:** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### Obtener
Para **obtener el valor de una variable**, usa el subcomando `get` así:
`/fmvariable get some_variable`

Luego el valor de esta variable se mostrará en el chat.

### Establecer
Para **establecer una variable**, usa el subcomando `set` así:
`/fmvariable set some_variable new_value true`

El último argumento aquí sirve para indicar si quieres recibir comentarios en el chat, es decir, si quieres que este comando muestre mensajes en tu chat.
