---
title: Entidades del jugador
description: >-
  Cómo funciona el elemento «Entidad del jugador» de FancyMenu y cómo usarlo
  correctamente.
---
# Entidades del jugador

FancyMenu te permite añadir entidades de jugador a las pantallas, para que puedas mostrar al jugador del cliente u otros jugadores, incluidas entidades personalizadas que no representan a un jugador real en absoluto, con una skin, nombre, capa, etc. personalizados.

# Jugador del cliente

Para mostrar un «espejo» del jugador del cliente, haz clic derecho sobre el elemento Entidad del jugador y activa **Copiar jugador del cliente**. Esto copiará la skin, la capa y el nombre del jugador del cliente.

# Otros jugadores

Si quieres mostrar a otro jugador existente, simplemente haz clic derecho en el elemento y establece **Nombre del jugador** como el nombre de un jugador existente. Esto mostrará automáticamente la skin, la capa y el nombre de ese jugador, siempre que no tengas una skin o capa personalizada configurada y **Copiar jugador del cliente** esté **desactivado**.

# Entidades de jugador personalizadas

Si no quieres mostrar a un jugador real y, en su lugar, quieres personalizar completamente la skin, la capa y el nombre de la entidad, puedes hacer clic derecho en el elemento. Hay opciones para establecer una skin y una capa personalizadas. Si hay una skin y una capa personalizadas activas, también puedes establecer cualquier nombre de jugador que quieras sin que copie la skin del nombre del jugador si el jugador existe.

# Pose de la entidad

El elemento Entidad del jugador ofrece compatibilidad completa para personalizar su pose; en otras palabras, puedes mover libremente todas sus extremidades, partes del cuerpo, etc.

Para ello, haz clic derecho sobre el elemento y haz clic en **Pose del jugador**. Esto abrirá una pantalla con deslizadores para configurar la rotación X/Y/Z de todas las partes del cuerpo.

La configuración de la pose del jugador tiene un modo normal en el que puedes personalizar las rotaciones con deslizadores, y también hay un modo avanzado que permite introducir texto para todas las rotaciones con compatibilidad total con marcadores de posición, ¡lo que incluso hace posible animar la entidad con un elemento Ticker que establezca variables de rotación!

# Cambiar el tamaño de la entidad

En Minecraft 1.20.1+ puedes usar simplemente los tiradores normales de cambio de tamaño del elemento para escalar la entidad.

En versiones anteriores (1.19.2 y anteriores), los elementos Entidad del jugador no admiten el cambio de tamaño directo mediante los tiradores de redimensionado. En su lugar, debes hacer clic derecho sobre el elemento y hacer clic en **Escala**. Esto te permite establecer una escala para el elemento. La predeterminada debería ser `30`, así que ponerla en `60`, por ejemplo, hace que el jugador sea el doble de grande de lo normal; ponerla en `15` lo muestra a la mitad de tamaño, y así sucesivamente.

# Dependencia: Fancy Entity Renderer (FER)

Para **Minecraft 1.20.1+**, se necesita **un mod adicional** para que los elementos Entidad del jugador funcionen. El mod se llama **Fancy Entity Renderer** y está disponible en [CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer) y [Modrinth](https://modrinth.com/mod/fancy-entity-renderer).

Si aún no hay una versión disponible para la versión de Minecraft que estás usando, lo más probable es que se publique más adelante.

Ten en cuenta que FER no está desarrollado por Keksuccino, así que él no tiene control sobre cuándo se publican las versiones.
