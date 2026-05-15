---
title: Abrir GUIs mediante comando
description: Cómo abrir GUIs de Vanilla y personalizadas mediante comando.
---

# Abrir GUIs mediante comando

FancyMenu incluye un comando que te permite abrir GUIs de Vanilla y personalizadas mediante comando.
Incluso puedes abrir GUIs de forma remota para **otros jugadores** si instalas FancyMenu tanto en el **servidor** como en los **clientes**.

Para abrir una GUI, solo tienes que usar el comando `/openguiscreen <screen_identifier> <target_player>`.

Sustituye `<screen_identifier>` por el identificador real del menú de la GUI que quieras abrir.
Puede ser el identificador de tu GUI personalizada (hecha con FancyMenu) o el identificador normal de una GUI de Vanilla/mod.

Para obtener el **identificador de menú de las GUIs de Vanilla/mod**, abre el menú del que quieras conocer el identificador y activa la **superposición de depuración** de FancyMenu mediante **Personalización -> Superposición de depuración**. Después, puedes hacer clic en el identificador que aparece como primera línea para copiarlo al portapapeles.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Deja el argumento `<target_player>` vacío para abrir la GUI en tu cliente, o elige un jugador (o varios jugadores) para abrir la GUI para ellos.
Ten en cuenta que el otro jugador necesita tener FancyMenu instalado en su cliente.

Este comando no funcionará con todas las pantallas, especialmente con las pantallas de mods. Si el comando falla al abrir una pantalla, mostrará un error. En ese caso no hay mucho que puedas hacer, porque probablemente se trate de una pantalla demasiado compleja para que FancyMenu pueda abrirla automáticamente.

Tampoco añadiré compatibilidad manualmente para pantallas de mods, porque añadir compatibilidad para todos los mods que existen me llevaría una eternidad, lo siento.

# Cerrar GUIs mediante comando

En el raro caso de que lo necesites, también existe el comando `/closeguiscreen <target_player>` que cierra la pantalla actual.
