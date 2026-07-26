---
title: Identificadores de pantalla
description: >-
  Acerca de los identificadores de pantalla y cómo encontrar el identificador de
  una pantalla.
---
# Identificadores de pantalla

FancyMenu usa identificadores de pantalla para los diseños, los widgets de Vanilla, las [acciones de pantalla](./action-scripts#open-screen-or-custom-gui-opengui) y las [sobrescrituras de GUI personalizadas](./custom-guis#overriding-an-existing-screen). Los identificadores distinguen entre mayúsculas y minúsculas, así que cópialos exactamente desde la superposición de depuración.

Las pantallas integradas normalmente usan un identificador universal corto como `title_screen`. Otras pantallas de mods pueden usar el nombre de su clase Java. Las GUI personalizadas usan el identificador que se ingresa en su administrador. Estos son identificadores de pantalla de FancyMenu, no ubicaciones de recursos de Minecraft.

# Cómo encontrar el identificador de una pantalla

Puedes ver el identificador del menú actualmente activo usando la **superposición de depuración**.
Contiene el identificador de la pantalla actual y te permite copiarlo al portapapeles con un clic izquierdo.

>[!TIP]
>Puedes habilitar la **superposición de depuración** presionando **CTRL + ALT + D** mientras **no** estés en el editor de diseños.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Abrir pantallas

La [acción **Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui) solo puede abrir las pantallas que FancyMenu puede construir en el estado actual del juego. Algunas pantallas requieren un mundo cargado, conexión, jugador o la pantalla original principal.

Si FancyMenu no puede construir el identificador, mostrará un error. Usa [**Imitar botón de Vanilla/Mod**](./action-scripts#mimic-vanillamod-button-mimicbutton) en el widget que normalmente abre la pantalla.
