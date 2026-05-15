---
title: Entidades de jugador
description: >-
  Cómo funciona el elemento "Entidad de jugador" de FancyMenu y cómo usarlo
  correctamente.
---

# Entidades de jugador

FancyMenu te permite agregar entidades de jugador a las pantallas, para que puedas mostrar al jugador cliente u otros jugadores, incluyendo entidades personalizadas que no representan a un jugador real en absoluto, con skin, nombre, capa, etc. personalizados.

# Jugador cliente

Para mostrar un "espejo" del jugador cliente, solo haz clic derecho en el elemento Entidad de jugador y activa **Copiar jugador cliente**. Esto copiará la skin, la capa y el nombre del jugador cliente.

# Otros jugadores

Si quieres mostrar a otro jugador existente, solo haz clic derecho en el elemento y establece **Nombre del jugador** en el nombre de un jugador existente. Esto mostrará automáticamente la skin, la capa y el nombre de ese jugador, siempre y cuando no tengas una skin o capa personalizada configurada y **Copiar jugador cliente** esté **desactivado**.

# Entidades de jugador personalizadas

Si no quieres mostrar a un jugador real y prefieres personalizar por completo la skin, la capa y el nombre de la entidad, puedes hacer clic derecho en el elemento. Hay opciones para establecer una skin y una textura de capa personalizadas. Si una skin y una capa personalizadas están activas, también puedes establecer cualquier nombre de jugador que quieras sin que copie la skin del nombre del jugador si el jugador existe.

# Pose de la entidad

El elemento Entidad de jugador tiene compatibilidad total para personalizar su pose, así que, en otras palabras, puedes mover libremente todos sus brazos, piernas, cuerpo, etc.

Para hacerlo, haz clic derecho en el elemento y luego en **Pose del jugador**. Esto abrirá una pantalla con deslizadores para configurar la rotación X/Y/Z de todas las partes del cuerpo.

La configuración de la pose del jugador tiene un modo normal en el que puedes personalizar las rotaciones con deslizadores, y también hay un modo avanzado que permite una entrada de texto para todas las rotaciones con compatibilidad completa con marcadores de posición, lo que incluso hace posible animar la entidad con un elemento Ticker que establezca variables de rotación.

# Cambiar el tamaño de la entidad

En Minecraft 1.21.1+ puedes usar simplemente los controladores normales de cambio de tamaño del elemento para escalar la entidad.

Para versiones anteriores (1.21.0 y anteriores), los elementos Entidad de jugador no admiten el cambio de tamaño directo mediante los controladores de cambio de tamaño. En su lugar, necesitas hacer clic derecho en el elemento y luego en **Escala**. Esto te permite establecer una escala para el elemento. La predeterminada debería ser `30`, así que configurarla en `60`, por ejemplo, hace que el jugador sea el doble de grande de lo normal; configurarla en `15` lo muestra a la mitad de tamaño y así sucesivamente.

# Dependencia: Fancy Entity Renderer (FER)

Para Minecraft 1.21.1+, se necesita un mod adicional para que funcionen los elementos Entidad de jugador. El mod se llama "Fancy Entity Renderer" y está disponible en CurseForge y Modrinth.

Si todavía no hay una compilación disponible para la versión de Minecraft que estás usando, lo más probable es que se publique más adelante.

Ten en cuenta que FER no es desarrollado por Keksuccino, así que él no tiene control sobre cuándo se publican las compilaciones.
