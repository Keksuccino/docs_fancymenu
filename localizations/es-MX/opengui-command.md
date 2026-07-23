---
title: Abrir GUIs por comando
description: Cómo abrir GUIs Vanilla y personalizadas mediante comando.
---
# Abrir GUIs por comando

El comando `/openguiscreen` abre GUIs de Vanilla, mods y [GUIs personalizadas](./custom-guis). Puede dirigirse a otros jugadores cuando FancyMenu está instalado en el servidor y en sus clientes.

Para abrir una GUI, usa `/openguiscreen <screen_identifier> [<target_players>]`.

Reemplaza `<screen_identifier>` con el identificador exacto, sensible a mayúsculas y minúsculas, de la GUI personalizada o de la pantalla de Vanilla/mod.

Para encontrar un identificador, abre la pantalla objetivo y activa la superposición de depuración con **CTRL + ALT + D**. Selecciona el identificador en su primera línea para copiarlo. Consulta [Identificadores de pantalla](./screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omite `[<target_players>]` para abrir la GUI para ti, o usa el nombre de un jugador o un selector como `@a` para abrirla para uno o más jugadores. Proporcionar el argumento de destino requiere nivel de permiso 2 (Game Master / nivel OP 2), incluso si te incluye a ti mismo, y cada jugador objetivo necesita tener FancyMenu instalado en su cliente.

No todas las pantallas de mods se pueden crear directamente. FancyMenu muestra un error cuando la pantalla objetivo no es compatible. En un diseño local, usa [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) en el widget que normalmente la abriría.

# Cerrar GUIs por comando

En el raro caso de que lo necesites, `/closeguiscreen [<target_players>]` cierra la pantalla actual. Te afecta a ti cuando se omite el destino; proporcionar el argumento de destino requiere nivel de permiso 2.
