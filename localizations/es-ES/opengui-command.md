---
title: Abrir GUIs por comando
description: Cómo abrir GUIs Vanilla y personalizadas mediante comando.
---

# Abrir GUIs por comando

El comando `/openguiscreen` abre GUIs de Vanilla, de mods y [GUIs personalizadas](./custom-guis). Puede dirigirse a otros jugadores cuando FancyMenu está instalado en el servidor y en sus clientes.

Para abrir una GUI, usa `/openguiscreen <screen_identifier> [<target_players>]`.

Sustituye `<screen_identifier>` por el identificador exacto, sensible a mayúsculas y minúsculas, de la GUI personalizada o de la pantalla de Vanilla/mod.

Para encontrar un identificador, abre la pantalla objetivo y activa la superposición de depuración con **CTRL + ALT + D**. Selecciona el identificador en su primera línea para copiarlo. Consulta [Identificadores de pantalla](./screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omite `[<target_players>]` para abrir la GUI para ti, o usa el nombre de un jugador o un selector como `@a` para abrirla para uno o varios jugadores. Proporcionar el argumento de destino requiere un nivel de permisos 2 (Game Master / OP nivel 2), incluso si te señala a ti mismo, y cada jugador objetivo necesita tener FancyMenu instalado en su cliente.

No todas las pantallas de mods pueden crearse directamente. FancyMenu muestra un error cuando la pantalla de destino no es compatible. En una disposición local, usa [**Botón imitar Vanilla/Mod**](./action-scripts#mimic-vanillamod-button-mimicbutton) en el widget que normalmente la abre.

# Cerrar GUIs por comando

En el raro caso de que lo necesites, `/closeguiscreen [<target_players>]` cierra la pantalla actual. Te afecta a ti cuando se omite el destino; proporcionar el argumento de destino requiere un nivel de permisos 2.
