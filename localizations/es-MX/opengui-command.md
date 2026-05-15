---
title: Abrir GUIs con comando
description: Cómo abrir GUIs Vanilla y personalizadas mediante comando.
---

# Abrir GUIs con comando

FancyMenu incluye un comando que te permite abrir GUIs de Vanilla y personalizadas mediante comando.
Incluso puedes abrir GUIs de forma remota para **otros jugadores** si instalas FancyMenu tanto en el **servidor** como en los **clientes**.

Para abrir una GUI, solo usa el comando `/openguiscreen <screen_identifier> <target_player>`.

Reemplaza `<screen_identifier>` con el identificador real del menú de la GUI que quieres abrir.
Esto puede ser el identificador de tu GUI personalizada (hecha con FancyMenu) o el identificador normal del menú de una GUI de Vanilla/mod.

Para obtener el **identificador del menú de las GUIs de Vanilla/mod**, abre el menú del que quieres conocer el identificador y activa el **overlay de depuración** de FancyMenu desde **Customization -> Debug Overlay**. Luego puedes hacer clic en el identificador que se muestra como primera línea para copiarlo a tu portapapeles.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Deja vacío el argumento `<target_player>` para abrir la GUI en tu cliente o elige a un jugador (o varios jugadores) para abrir la GUI para ellos.
Ten en cuenta que el otro jugador necesita tener FancyMenu instalado en su cliente.

Este comando no funcionará para todas las pantallas, especialmente las de mods. Si el comando falla al abrir una pantalla, mostrará un error. No hay mucho que puedas hacer en ese caso, porque probablemente sea una pantalla demasiado compleja para que FancyMenu la abra automáticamente.

Tampoco agregaré compatibilidad manualmente para pantallas de mods, porque agregar compatibilidad para todos los mods que existen me llevaría muchísimo tiempo, lo siento.

# Cerrar GUIs con comando

En el caso poco común de que lo necesites, también existe el comando `/closeguiscreen <target_player>` que cierra la pantalla actual.
