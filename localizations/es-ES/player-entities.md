---
title: Entidades de jugador
description: >-
  Cómo funciona el elemento "Entidad de jugador" de FancyMenu y cómo usarlo
  correctamente.
---

# Entidades de jugador

FancyMenu te permite añadir entidades de jugador a las pantallas, para que puedas mostrar al jugador cliente u otros jugadores, incluidas entidades personalizadas que no representan a ningún jugador real, con una skin personalizada, nombre, capa, etc.

# Jugador del cliente

Para mostrar un "espejo" del jugador cliente, solo tienes que hacer clic derecho en el elemento Entidad de jugador y activar **Copiar jugador cliente**. Esto copiará la skin, la capa y el nombre del jugador cliente.

# Otros jugadores

Si quieres mostrar a otro jugador existente, solo tienes que hacer clic derecho en el elemento y establecer **Nombre del jugador** con el nombre de un jugador existente. Esto mostrará automáticamente la skin, la capa y el nombre de ese jugador existente, siempre que no tengas una skin o capa personalizada configurada y **Copiar jugador cliente** esté **desactivado**.

# Entidades de jugador personalizadas

Si no quieres mostrar a un jugador real y en su lugar quieres personalizar por completo la skin, la capa y el nombre de la entidad, puedes hacer clic derecho en el elemento. Hay opciones para establecer una skin y una capa personalizadas. Si hay una skin y una capa personalizadas activas, también puedes establecer cualquier nombre de jugador que quieras sin que copie la skin del nombre del jugador si el jugador existe.

# Pose de la entidad

El elemento Entidad de jugador tiene compatibilidad completa para personalizar su pose; en otras palabras, puedes mover libremente todos sus miembros, partes del cuerpo, etc.

Para hacerlo, haz clic derecho en el elemento y pulsa en **Pose del jugador**. Esto abrirá una pantalla con deslizadores para configurar la rotación X/Y/Z de todas las partes del cuerpo.

Los ajustes de pose del jugador tienen un modo normal en el que puedes personalizar las rotaciones con deslizadores, y también hay un modo avanzado que permite introducir texto para todas las rotaciones con compatibilidad total con marcadores de posición, lo que incluso hace posible animar la entidad con un elemento Ticker que establezca variables de rotación.

# Cambiar el tamaño de la entidad

En Minecraft 1.21.1+, puedes usar simplemente los controladores normales de cambio de tamaño del elemento para escalar la entidad.

En versiones anteriores (1.21.0 y anteriores), los elementos Entidad de jugador no admiten el cambio de tamaño directo mediante los controladores de redimensionado. En su lugar, debes hacer clic derecho en el elemento y pulsar en **Escala**. Esto te permite establecer una escala para el elemento. El valor predeterminado debería ser `30`, así que ponerlo en `60`, por ejemplo, hace que el jugador sea el doble de grande de lo normal; ponerlo en `15` lo muestra a la mitad de tamaño, y así sucesivamente.

# Dependencia: Fancy Entity Renderer (FER)

Para Minecraft 1.21.1+ se necesita un mod adicional para que los elementos Entidad de jugador funcionen. El mod se llama "Fancy Entity Renderer" y está disponible en CurseForge y Modrinth.

Si todavía no hay una compilación disponible para la versión de Minecraft que estás usando, lo más probable es que se publique más adelante.

Ten en cuenta que FER no está desarrollado por Keksuccino, así que no tiene control sobre cuándo se publican las compilaciones.
