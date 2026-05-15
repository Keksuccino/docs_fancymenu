---
title: Comandos
description: Los comandos de FancyMenu y cómo usarlos.
---

# Comandos

FancyMenu añade algunos comandos al juego que pueden ser muy útiles al combinarlos con otros mods, como FTB Quests.

> FancyMenu debe estar en el **SERVIDOR** (y en el cliente) para usar comandos en multijugador.
{.is-warning}

## /openguiscreen

El comando `/openguiscreen` te permite abrir una GUI (vanilla/de mods y GUIs personalizadas).
Incluso puede abrir GUIs de forma remota para otros jugadores cuando FancyMenu está instalado tanto en el servidor como en los clientes.

Para una descripción más detallada de este comando, consulta la página [Abrir GUIs por comando](/opengui-command).

Este comando no funcionará con todas las pantallas, especialmente con las pantallas de mods. Si el comando no consigue abrir una pantalla, mostrará un error. No hay mucho que puedas hacer en ese caso, porque probablemente sea una pantalla demasiado compleja como para que FancyMenu la abra automáticamente.

Tampoco añadiré compatibilidad manualmente para las pantallas de mods a partir de ahora, porque añadir compatibilidad para todos los mods que existen me llevaría una eternidad, lo siento.

**Uso:** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

El comando `/closeguiscreen` te permite cerrar la GUI actual.

¿Eh? ¿Dices que esto no sirve para nada?
Bueno, sí, pero en realidad no.

Este comando es útil cuando se usan mods que activan comandos en acciones concretas.
Así que sí, este comando es absolutamente inútil si lo usas sin otros mods, ¡pero puede ser realmente útil si tienes instalados los mods adecuados!

**Uso:** `/closeguiscreen <target_player>`

## /fmvariable

El comando `/fmvariable` te permite establecer y obtener variables de FancyMenu.

Para ejecutar este comando como otro jugador en servidores, puedes usar el comando de vanilla `/execute as`.
Así que, por ejemplo, si quieres ejecutar el comando `/fmvariable` como el jugador `ExamplePlayer`, escribirías:
`/execute as ExamplePlayer run fmvariable...`.

**Uso:** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### Obtener
Para **obtener el valor de una variable**, usa el subcomando `get` de esta forma:
`/fmvariable get some_variable`

Entonces el valor de esta variable se mostrará en tu chat.

### Establecer
Para **establecer una variable**, usa el subcomando `set` de esta forma:
`/fmvariable set some_variable new_value true`

El último argumento sirve para indicar si quieres recibir mensajes en el chat, es decir, si quieres que este comando imprima mensajes en tu chat.
