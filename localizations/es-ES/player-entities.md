---
title: Entidades de jugador
description: >-
  Muestra jugadores en tus menús con el elemento Entidad de jugador, con su
  aspecto, nombre, pose, armadura y mucho más.
sourceBlobSha: b8f8d4340ca3a87e1c55c86f95f36786ab840644
---

# Entidades de jugador

El elemento Entidad de jugador muestra a un jugador en 3D, como el personaje del propio jugador junto a los botones de la pantalla de título. Puede copiar a la persona que juega, mostrar a cualquier otro jugador o ser un personaje propio con su aspecto, capa y nombre.

<img width="800" alt="Cinco entidades de jugador: un jugador real con aspecto y capa, uno con armadura de diamante encantada y espada y escudo, uno agachado, uno saludando y un bebé" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> En Minecraft 1.20.1 y versiones posteriores, las entidades de jugador necesitan el mod Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Sin él, se muestra un recuadro rojo. Si aún no hay una versión compatible con la tuya de Minecraft, no se podrán mostrar entidades de jugador.

# Añadir una entidad de jugador

Haz clic derecho en el fondo del editor y selecciona **Nuevo elemento -> Entidad de jugador**. Arrastra los controles para cambiar su tamaño. El tamaño del jugador depende de la altura del elemento.

Todos los ajustes siguientes están en el menú que aparece al hacer clic derecho en el elemento.

# A quién muestra

- **Copiar jugador del cliente** muestra a la persona que juega, con su nombre, aspecto y capa. Mientras esta opción esté activada, los ajustes de nombre, aspecto y capa estarán bloqueados.
- **Nombre del jugador** puede ser cualquier nombre; no tiene por qué pertenecer a un jugador real. Admite [marcadores de posición](/placeholders).
- **Mostrar nombre del jugador** muestra la etiqueta con el nombre sobre la cabeza. Si **Rotación de la etiqueta** está desactivado, la etiqueta no gira con el jugador.

## Aspecto y capa

- **Aspecto automático** y **Capa automática** cargan el aspecto y la capa del jugador indicado en **Nombre del jugador**. Para ello se necesita conexión a Internet.
- **Textura del aspecto** y **Textura de la capa** usan tus propios archivos de aspecto y capa, como un aspecto de tus [recursos](/resources). Los aspectos son los archivos de aspecto habituales de Minecraft.
- **Aspecto fino** sirve para los aspectos con brazos delgados, como el de Alex. **Aspecto automático** y **Copiar jugador del cliente** lo detectan automáticamente.

# Pose y movimiento

<img width="800" alt="Dos entidades de jugador siguen con la mirada el puntero del ratón mientras se mueve: la de la izquierda solo gira la cabeza y la de la derecha gira la cabeza y el cuerpo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **La cabeza sigue al ratón** y **El cuerpo sigue al ratón** hacen que el jugador mire al puntero. Ambas opciones están activadas de forma predeterminada en las entidades de jugador nuevas.
- **Pose** permite elegir una pose corporal: **De pie**, **Agachado**, **Durmiendo**, **Nadando**, **Muriendo** o **Ataque giratorio**.
- **Movimiento del cuerpo** anima la pose.

## Pose de la entidad

**Pose de la entidad** abre una ventana con la rotación en los ejes X, Y y Z de la **Cabeza**, el **Cuerpo**, el **Brazo izquierdo**, el **Brazo derecho**, la **Pierna izquierda** y la **Pierna derecha**, entre `-180` y `180`.

<img width="800" alt="La ventana Pose de la entidad, con controles deslizantes de rotación para la cabeza y el cuerpo del jugador" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

**Modo avanzado**, junto a un control deslizante, lo convierte en un campo de texto compatible con [marcadores de posición](/placeholders). Si contiene una [variable](/variables), como `$$arm_angle`, un [programador](/schedulers) puede animar al jugador cambiando el valor de la variable.

# Armadura, objetos y más

- **Armadura y herramientas** equipa objetos al jugador: **Armadura para la cabeza**, **Armadura para el torso**, **Armadura para las piernas**, **Armadura para los pies**, **Herramienta de la mano izquierda** y **Herramienta de la mano derecha**. Indica el ID de un objeto, como `minecraft:diamond_sword`. Los ID de objetos admiten marcadores de posición. **Encantar armadura para la cabeza** y las demás opciones de encantamiento añaden el brillo de encantamiento.
- **Es un bebé** hace que el jugador sea pequeño, como un bebé.
- **Loro** coloca un loro en el hombro derecho o, si activas **Loro en el hombro izquierdo**, en el izquierdo.

# Información útil

- Las entidades de jugador no se pueden girar, inclinar, atenuar ni hacer transparentes.
- Para mostrar solo la cabeza de un jugador, consulta [Cabezas de jugador](/player-heads).
- En Minecraft 1.19.2, las entidades de jugador no necesitan Fancy Entity Renderer, pero tienen menos ajustes: **Agachado** en lugar de **Pose**, y no incluyen **Rotación de la etiqueta**, **Movimiento del cuerpo** ni **Armadura y herramientas**. Su tamaño depende de **Escala de la entidad** (30 de forma predeterminada; `60` es el doble de grande), en lugar del tamaño del elemento.
