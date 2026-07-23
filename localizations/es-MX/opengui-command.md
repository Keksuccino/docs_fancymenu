---
title: Abrir GUI con comando
description: Cómo abrir GUI Vanilla y personalizadas mediante comandos.
---
# Abrir GUI con comando

FancyMenu incluye un comando que te permite abrir GUI Vanilla y personalizadas mediante comando.
Incluso puedes abrir GUI de forma remota para **otros jugadores** al instalar FancyMenu tanto en el **servidor** como en los **clientes**.

Para abrir una GUI, usa `/openguiscreen <screen_identifier> [<target_players>]`.

Reemplaza `<screen_identifier>` con el identificador real del menú de la GUI que quieres abrir.
Este puede ser el identificador de tu GUI personalizada (hecha con FancyMenu) o el identificador normal de menú de una GUI Vanilla/de mod.

Para obtener el **identificador de menú de las GUI Vanilla/de mod**, abre el menú del que quieres conocer el identificador y activa la **superposición de depuración** de FancyMenu mediante **Personalización -> Superposición de depuración**. Luego puedes hacer clic en el identificador mostrado como primera línea para copiarlo al portapapeles.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omitir `[<target_players>]` abrirá la GUI para ti, o puedes usar un nombre de jugador o un selector como `@a` para abrirla para uno o más jugadores. Proporcionar el argumento de destino requiere nivel de permiso 2 (Game Master / nivel OP 2), incluso si te incluye a ti, y cada jugador objetivo necesita tener FancyMenu instalado en su cliente.

Este comando no funcionará con todas las pantallas, especialmente con pantallas de mods. Si el comando falla al abrir una pantalla, mostrará un error. No hay mucho que puedas hacer en ese caso, porque probablemente se trate de una pantalla demasiado compleja para que FancyMenu la abra automáticamente.

Tampoco agregaré compatibilidad manualmente para pantallas de mods, porque añadir compatibilidad para todos los mods existentes me tomaría muchísimo tiempo, lo siento.

# Cerrar GUI con comando

En el caso poco común de que lo necesites, `/closeguiscreen [<target_players>]` cierra la pantalla actual. Te afecta a ti cuando se omite el destino; proporcionar el argumento de destino requiere nivel de permiso 2.
