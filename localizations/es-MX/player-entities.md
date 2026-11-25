---
title: Entidades de jugador
description: >-
  Muestra jugadores en tus menús con el elemento Entidad de jugador, con su
  skin, nombre, pose, armadura y más.
sourceBlobSha: b8f8d4340ca3a87e1c55c86f95f36786ab840644
---

# Entidades de jugador

El elemento Entidad de jugador muestra a un jugador en 3D, como el personaje del propio jugador junto a los botones de la pantalla de título. Puede copiar a quien está jugando, mostrar a cualquier otro jugador o ser un personaje propio con su propia skin, capa y nombre.

<img width="800" alt="Cinco entidades de jugador: un jugador real con skin y capa, uno con armadura de diamante encantada, espada y escudo, uno agachado, uno saludando y un bebé" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> En Minecraft 1.20.1 y versiones posteriores, las entidades de jugador necesitan el mod Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Sin él, aparecen como un cuadro rojo. Si todavía no hay una versión del mod para tu versión de Minecraft, las entidades de jugador no se podrán mostrar.

# Agregar una entidad de jugador

Haz clic derecho en el fondo del editor y selecciona **Nuevo elemento -> Entidad de jugador**. Arrastra los controles para cambiar su tamaño. El tamaño del jugador depende de la altura del elemento.

Todos los ajustes de abajo están en el menú que aparece al hacer clic derecho en el elemento.

# A quién muestra

- **Copiar jugador del cliente** muestra a quien está jugando, con su nombre, skin y capa. Mientras esta opción esté activada, los ajustes de nombre, skin y capa estarán bloqueados.
- **Nombre del jugador** puede ser cualquier nombre; no tiene que pertenecer a un jugador real. Es compatible con [marcadores de posición](/placeholders).
- **Mostrar nombre del jugador** muestra la etiqueta de nombre sobre la cabeza. Si **Rotación de la etiqueta de nombre** está desactivada, la etiqueta no girará junto con el jugador.

## Skin y capa

- **Skin automática** y **Capa automática** cargan la skin y la capa del jugador con ese **Nombre del jugador**. Para ello se necesita conexión a internet.
- **Textura de skin** y **Textura de capa** usan tus propios archivos de skin y capa, como una skin de tus [recursos](/resources). Las skins son los archivos de skin normales de Minecraft.
- **Skin delgada** sirve para skins con brazos delgados, como Alex. **Skin automática** y **Copiar jugador del cliente** lo detectan automáticamente.

# Pose y movimiento

<img width="800" alt="Dos entidades de jugador miran el puntero del mouse mientras se mueve: la de la izquierda solo gira la cabeza y la de la derecha gira la cabeza y el cuerpo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **La cabeza sigue al mouse** y **El cuerpo sigue al mouse** hacen que el jugador mire hacia el puntero del mouse. Ambas opciones están activadas en las entidades de jugador nuevas.
- **Pose** elige una pose corporal: **De pie**, **Agachado**, **Durmiendo**, **Nadando**, **Muriendo** o **Ataque giratorio**.
- **Movimiento del cuerpo** anima la pose.

## Pose de la entidad

**Pose de la entidad** abre una ventana con la rotación en los ejes X, Y y Z de la **Cabeza**, el **Cuerpo**, el **Brazo izquierdo**, el **Brazo derecho**, la **Pierna izquierda** y la **Pierna derecha**, desde `-180` hasta `180`.

<img width="800" alt="La ventana Pose de la entidad, con controles deslizantes de rotación para la cabeza y el cuerpo del jugador" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

**Modo avanzado**, junto a un control deslizante, lo convierte en un valor de texto compatible con [marcadores de posición](/placeholders). Si usas una [variable](/variables), como `$$arm_angle`, un [planificador](/schedulers) puede animar al jugador al cambiar el valor de la variable.

# Armadura, objetos y más

- **Armadura y herramientas** equipa objetos al jugador: **Armadura de cabeza**, **Armadura de pecho**, **Armadura de piernas**, **Armadura de pies**, **Herramienta de la mano izquierda** y **Herramienta de la mano derecha**. Asígnales un ID de objeto, como `minecraft:diamond_sword`. Los ID de objetos son compatibles con marcadores de posición. **Encantar armadura de cabeza** y las demás opciones de encantamiento agregan el brillo de encantamiento.
- **Es bebé** hace que el jugador sea pequeño, como un bebé.
- **Loro** coloca un loro en el hombro derecho, o en el izquierdo si activas **Loro en el hombro izquierdo**.

# Información útil

- Las entidades de jugador no se pueden rotar, inclinar, desvanecer ni hacer transparentes.
- Para mostrar solo la cabeza de un jugador, consulta [Cabezas de jugador](/player-heads).
- En Minecraft 1.19.2, las entidades de jugador no necesitan Fancy Entity Renderer, pero tienen menos ajustes: **Agachado** en lugar de **Pose**, y no incluyen **Rotación de la etiqueta de nombre**, **Movimiento del cuerpo** ni **Armadura y herramientas**. Su tamaño depende de **Escala de la entidad** (el valor predeterminado es `30`, así que `60` es el doble de grande), no del tamaño del elemento.
