---
title: Superposiciones de decoración
description: >-
  Agrega superposiciones visuales a pantalla completa a los menús en el editor
  de diseño de FancyMenu.
---

# Superposiciones de decoración

Las superposiciones de decoración son efectos a pantalla completa que se renderizan frente a los elementos de tu menú.

Son útiles cuando quieres agregar ambiente o movimiento a un menú sin construir esos efectos manualmente.

Ejemplos comunes:

- Agrega **Caída de nieve** para un menú de invierno con acumulación de nieve.
- Agrega **Lluvia** para un aspecto de tormenta con charcos y gotas.
- Agrega **Luciérnagas** para un menú tranquilo de estilo nocturno.
- Agrega **Luces de cadena** para temas festivos o decorativos de menú.
- Agrega **Hojas**, **Fuegos artificiales** o **Confeti** para menús de temporada o eventos.
- Agrega la superposición de **Navegador** para mostrar una capa a pantalla completa de una página web o video.

# Dónde encontrarlo

Abre un diseño en el editor de diseño, luego haz clic derecho en el fondo del editor y abre **Superposiciones de decoración**.

# Inicio rápido

1. Abre un diseño en el editor de diseño.
2. Haz clic derecho en el fondo (área vacía).
3. Abre **Superposiciones de decoración**.
4. Selecciona un tipo de superposición.
5. Configura **Mostrar superposición** en **Habilitado**.
6. Configura los ajustes de la superposición.
7. Guarda el diseño y prueba la pantalla.

# Cómo funcionan los tipos de superposición

Cada tipo de superposición tiene su propio submenú y su propio interruptor de **Mostrar superposición**.

- Puedes habilitar solo los tipos que quieras.
- Puedes combinar varios tipos habilitados en un solo diseño.
- Los ajustes son por tipo de superposición (por ejemplo, color, intensidad, velocidad, densidad, escala y comportamiento especial).

> [!INFO]
> Es posible apilar varias instancias del mismo tipo de superposición usando varios diseños con el mismo tipo habilitado.

# Tipos de superposición

- **Caída de nieve**: nieve con acumulación opcional sobre superficies/botones.
- **Lluvia**: lluvia con charcos, gotas y destellos de trueno opcionales.
- **Luciérnagas**: grupos de luciérnagas en movimiento con cantidad de grupos, densidad, tamaño y color configurables.
- **Luces de cadena**: combinaciones de cadenas configurables, colores de luz, comportamiento de viento/parpadeo y modo de color festivo.
- **Hojas**: hojas que caen con colores, viento, velocidad, escala y densidad configurables.
- **Fuegos artificiales**: fuegos artificiales frecuentes con cantidad, tamaño de explosión y escala configurables.
- **Confeti**: lluvia de confeti con modo opcional de confeti al hacer clic con el mouse.
- **Navegador**: superposición de navegador a pantalla completa con URL y ajustes de medios.
- **Shader GLSL**: superposición personalizada de shader a pantalla completa (para efectos visuales animados o estáticos basados en shaders).

# Superposición de navegador: interactiva vs pasiva

La superposición de Navegador se puede configurar como un navegador interactivo o como una capa visual pasiva.

- Los ajustes de **Procesar mouse/teclado** controlan si el navegador maneja la entrada por sí mismo.
- Los ajustes de **Consumir mouse/teclado** controlan si la entrada se bloquea para que no llegue al menú que está detrás.

Ejemplos prácticos de configuración:

- Navegador interactivo al frente: habilita **Procesar** y **Consumir**.
- Capa visual בלבד del navegador: deshabilita **Procesar** y deshabilita **Consumir**.

> [!IMPORTANT]
> La superposición de decoración de Navegador requiere el mod **MCEF**.
