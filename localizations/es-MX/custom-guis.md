---
title: GUIs personalizadas
description: Cómo agregar una nueva pantalla de GUI al juego.
---

# GUIs personalizadas

FancyMenu te permite personalizar las pantallas de GUI existentes, pero también te permite agregar pantallas completamente nuevas y llenarlas con elementos.

# Agregar una nueva pantalla

Para agregar una nueva pantalla, ve a **Personalización -> GUIs personalizadas -> Administrar GUIs personalizadas**.

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

En el siguiente menú, haz clic en **Nueva GUI**.

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

Aquí necesitas darle a tu nueva GUI un identificador único y puedes personalizar otras partes del comportamiento básico de la pantalla.
Cuando termines, presiona **Listo**.

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

Ahora tienes una nueva GUI vacía. Para abrirla, selecciona la GUI en el menú **Administrar GUIs personalizadas** y haz clic en **Abrir GUI**.

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

Esto abrirá la pantalla de GUI todavía bastante vacía. Para hacerla menos vacía, solo crea un nuevo diseño para ella como lo harías con cualquier otra pantalla.

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# Abrir la GUI mediante una acción

La última parte es darle a los usuarios normales acceso a tu GUI. La forma más sencilla de hacerlo es usar la acción **Abrir pantalla o GUI personalizada** con un botón, control deslizante o ticker.

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# Abrir la GUI mediante un comando

También puedes abrir tu GUI personalizada mediante un [comando dentro del juego](./commands#openguiscreen).
¡Esto incluso te permite abrir la GUI de forma remota para otros usuarios!

# Modo emergente

A partir de FancyMenu v3.8.0, las GUIs personalizadas son compatibles con un "Modo emergente" que hace que se vean como una ventana emergente que se abre encima de otra pantalla (la pantalla anterior desde la que se abrió la GUI personalizada). Esta opción se puede activar o desactivar de forma individual para cada GUI personalizada en su configuración.

FancyMenu 3.9.0 también agrega una opción para activar o desactivar la superposición de fondo de la pantalla para las GUIs personalizadas mientras estás en un mundo. Úsala cuando quieras deshabilitar o conservar el desenfoque/la tintura oscura detrás de una GUI personalizada abierta sobre el juego.
