---
title: Abrir interfaces gráficas con un comando
description: Cómo abrir interfaces gráficas vanilla y personalizadas con un comando.
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# Abrir interfaces gráficas con un comando

El comando `/openguiscreen` abre interfaces gráficas vanilla, de mods y [personalizadas](/custom-guis). Puede abrirlas para otros jugadores si FancyMenu está instalado en el servidor y en sus clientes.

Para abrir una interfaz gráfica, usa `/openguiscreen <screen_identifier> [<target_players>]`.

Sustituye `<screen_identifier>` por el identificador exacto, respetando mayúsculas y minúsculas, de la interfaz gráfica personalizada o de la pantalla vanilla o de un mod.

Para encontrar un identificador, abre la pantalla correspondiente y activa la superposición de depuración con **CTRL + ALT + D**. Selecciona el identificador de la primera línea para copiarlo. Consulta [Identificadores de pantalla](/screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omite `[<target_players>]` para abrir la interfaz gráfica para ti, o usa el nombre de un jugador o un selector como `@a` para abrirla para uno o varios jugadores. Indicar el argumento de destino requiere el nivel de permiso 2 (Game Master / nivel OP 2), incluso si te nombra a ti, y todos los jugadores de destino deben tener FancyMenu instalado en su cliente.

No todas las pantallas de los mods se pueden crear directamente. FancyMenu muestra un error cuando la pantalla de destino no es compatible. En un diseño local, usa [**Imitar botón vanilla/de mod**](/action-scripts#mimic-vanillamod-button) en el widget que normalmente la abre.

# Cerrar interfaces gráficas con un comando

En el poco habitual caso de que lo necesites, `/closeguiscreen [<target_players>]` cierra la pantalla actual. Si omites el destino, te afecta a ti; indicar el argumento de destino requiere el nivel de permiso 2.
