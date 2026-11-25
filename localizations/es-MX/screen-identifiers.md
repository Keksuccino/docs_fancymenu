---
title: Identificadores de pantalla
description: >-
  Información sobre los identificadores de pantalla y cómo encontrar el
  identificador de una pantalla.
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# Identificadores de pantalla

FancyMenu usa identificadores de pantalla para los diseños, los widgets de Minecraft vanilla, las [acciones de pantalla](/action-scripts#open-screen-or-custom-gui) y las [sobrescrituras de GUI personalizada](/custom-guis#overriding-an-existing-screen). Los identificadores distinguen entre mayúsculas y minúsculas, así que cópialos exactamente desde la superposición de depuración.

Las pantallas integradas suelen usar un identificador universal corto, como `title_screen`. Otras pantallas de mods pueden usar el nombre de su clase Java. Las GUI personalizadas usan el identificador que ingresaste en su administrador. Estos son identificadores de pantalla de FancyMenu, no ubicaciones de recursos de Minecraft.

# Cómo encontrar el identificador de una pantalla

Puedes ver el identificador del menú activo en ese momento mediante la **superposición de depuración**.
Esta muestra el identificador de la pantalla actual y te permite copiarlo al portapapeles con un clic izquierdo.

>[!TIP]
>Puedes activar la **superposición de depuración** presionando **CTRL + ALT + D** cuando **no** estés en el editor de diseños.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Abrir pantallas

La acción [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui) solo puede abrir las pantallas que FancyMenu puede crear en el estado actual del juego. Algunas pantallas requieren que haya un mundo cargado, una conexión, un jugador o una pantalla de origen.

Si FancyMenu no puede crear la pantalla a partir del identificador, mostrará un error. Usa [**Imitar botón de Vanilla/mod**](/action-scripts#mimic-vanillamod-button) en el widget que normalmente abre la pantalla.
