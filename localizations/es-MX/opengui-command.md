---
title: Abrir interfaces gráficas con comandos
description: >-
  Cómo abrir interfaces gráficas de Minecraft vanilla y personalizadas mediante
  comandos.
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# Abrir interfaces gráficas con comandos

El comando `/openguiscreen` abre interfaces gráficas de Minecraft vanilla, de mods y [personalizadas](/custom-guis). Si FancyMenu está instalado en el servidor y en los clientes de los jugadores, también puede abrirlas para otros jugadores.

Para abrir una interfaz gráfica, usa `/openguiscreen <screen_identifier> [<target_players>]`.

Reemplaza `<screen_identifier>` por el identificador exacto, respetando mayúsculas y minúsculas, de la interfaz gráfica personalizada o de Minecraft vanilla/de un mod.

Para encontrar un identificador, abre la interfaz gráfica deseada y activa la superposición de depuración con **CTRL + ALT + D**. Selecciona el identificador de la primera línea para copiarlo. Consulta [Identificadores de pantalla](/screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omite `[<target_players>]` para abrir la interfaz gráfica para ti. También puedes usar el nombre de un jugador o un selector, como `@a`, para abrirla para uno o varios jugadores. Indicar un objetivo requiere el nivel de permiso 2 (Game Master / nivel OP 2), aunque seas tú mismo el objetivo. Además, cada jugador objetivo debe tener FancyMenu instalado en su cliente.

No todas las pantallas de los mods se pueden crear directamente. FancyMenu muestra un error cuando la pantalla no es compatible. En un diseño local, usa [**Imitar botón de Minecraft vanilla/de un mod**](/action-scripts#mimic-vanillamod-button) en el widget que normalmente la abre.

# Cerrar interfaces gráficas con comandos

En el caso poco común de que lo necesites, `/closeguiscreen [<target_players>]` cierra la pantalla actual. Si omites el objetivo, el comando te afecta a ti; indicar un objetivo requiere el nivel de permiso 2.
