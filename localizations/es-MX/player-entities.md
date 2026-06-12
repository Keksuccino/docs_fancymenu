---
title: Entidades de jugador
description: >-
  Cómo funciona el elemento "Player Entity" de FancyMenu y cómo usarlo
  correctamente.
---
# Entidades de jugador

FancyMenu te permite agregar entidades de jugador a las pantallas, para que puedas mostrar al jugador del cliente u otros jugadores, incluyendo entidades personalizadas que en realidad no representan a un jugador real, con una skin, nombre, capa, etc. personalizados.

# Jugador del cliente

Para mostrar un "espejo" del jugador del cliente, solo haz clic derecho en el elemento Player Entity y activa **Copy Client Player**. Esto copiará la skin, la capa y el nombre del jugador del cliente.

# Otros jugadores

Si quieres mostrar a otro jugador existente, solo haz clic derecho en el elemento y establece **Player Name** en el nombre de un jugador existente. Esto mostrará automáticamente la skin, la capa y el nombre de ese jugador, siempre que no tengas una skin o capa personalizada configurada y **Copy Client Player** esté **desactivado**.

# Entidades de jugador personalizadas

Si no quieres mostrar a un jugador real y, en su lugar, quieres personalizar por completo la skin, la capa y el nombre de la entidad, puedes hacer clic derecho en el elemento. Hay opciones para configurar una textura de skin y capa personalizadas. Si una skin y capa personalizadas están activas, también puedes establecer cualquier nombre de jugador que quieras sin que copie la skin del nombre del jugador si el jugador existe.

# Pose de la entidad

El elemento Player Entity tiene soporte completo para personalizar su pose; en otras palabras, puedes mover libremente todas sus extremidades, partes del cuerpo, etc.

Para hacerlo, haz clic derecho en el elemento y luego en **Player Pose**. Esto abrirá una pantalla con controles deslizantes para configurar la rotación X/Y/Z de todas las partes del cuerpo.

La configuración de pose del jugador tiene un modo normal en el que puedes personalizar las rotaciones con controles deslizantes, y también hay un modo avanzado que permite ingresar texto para todas las rotaciones con soporte completo para placeholders, lo que incluso hace posible animar la entidad con un elemento Ticker que establezca variables de rotación.

# Cambiar el tamaño de la entidad

En Minecraft 1.20.1+ puedes simplemente usar los agarradores normales de redimensionamiento del elemento para escalar la entidad.

En versiones anteriores (1.19.2 y anteriores), los elementos Player Entity no admiten el cambio de tamaño directo mediante los agarradores de redimensionamiento. En su lugar, necesitas hacer clic derecho en el elemento y luego en **Scale**. Esto te permite establecer una escala para el elemento. La predeterminada debería ser `30`, así que establecerla en `60`, por ejemplo, hace que el jugador sea el doble de grande de lo normal, establecerla en `15` lo muestra a la mitad de su tamaño y así sucesivamente.

# Dependencia: Fancy Entity Renderer (FER)

Para **Minecraft 1.20.1+**, se necesita un **mod adicional** para que los elementos Player Entity funcionen. El mod se llama **Fancy Entity Renderer** y está disponible en [CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer) y [Modrinth](https://modrinth.com/mod/fancy-entity-renderer).

Si todavía no hay una versión disponible para la versión de Minecraft que estás usando, lo más probable es que se publique más adelante.

Ten en cuenta que FER no es desarrollado por Keksuccino, así que él no tiene control sobre cuándo se publican las versiones.
