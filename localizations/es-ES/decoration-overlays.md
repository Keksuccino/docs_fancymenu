---
title: Superposiciones de decoración
description: >-
  Añade superposiciones visuales a pantalla completa a los menús en el editor de
  diseño de FancyMenu.
---

# Superposiciones de decoración

Las superposiciones de decoración son efectos a pantalla completa que se renderizan delante de los elementos del menú.

Son útiles cuando quieres añadir ambiente o movimiento a un menú sin tener que crear esos efectos manualmente.

Ejemplos comunes:

- Añade **Snowfall** para un menú de invierno con acumulación de nieve.
- Añade **Rainfall** para un aspecto de tormenta con charcos y gotas.
- Añade **Fireflies** para un menú tranquilo con estilo nocturno.
- Añade **String Lights** para temas festivos o decorativos del menú.
- Añade **Leaves**, **Fireworks** o **Confetti** para menús de temporada o de eventos.
- Añade la superposición **Browser** para mostrar una capa de página web o vídeo a pantalla completa.

# Dónde encontrarlo

Abre un diseño en el editor de diseño y luego haz clic derecho en el fondo del editor y abre **Decoration Overlays**.

# Inicio rápido

1. Abre un diseño en el editor de diseño.
2. Haz clic derecho en el fondo (zona vacía).
3. Abre **Decoration Overlays**.
4. Selecciona un tipo de superposición.
5. Pon **Show Overlay** en **Enabled**.
6. Configura los ajustes de la superposición.
7. Guarda el diseño y prueba la pantalla.

# Cómo funcionan los tipos de superposición

Cada tipo de superposición tiene su propio submenú y su propio interruptor **Show Overlay**.

- Puedes activar solo los tipos que quieras.
- Puedes combinar varios tipos activados en un mismo diseño.
- Los ajustes son específicos de cada tipo de superposición (por ejemplo, color, intensidad, velocidad, densidad, escala o comportamiento especial).

> [!INFO]
> Es posible apilar varias instancias del mismo tipo de superposición utilizando varios diseños con el mismo tipo activado.

# Tipos de superposición

- **Snowfall**: caída de nieve con acumulación opcional sobre superficies y botones.
- **Rainfall**: lluvia con charcos, gotas y destellos opcionales de truenos.
- **Fireflies**: grupos de luciérnagas en movimiento con cantidad de grupos, densidad, tamaño y color configurables.
- **String Lights**: combinaciones de guirnaldas configurables, colores de las luces, comportamiento de viento/parpadeo y modo de color festivo.
- **Leaves**: hojas que caen con colores, viento, velocidad, escala y densidad configurables.
- **Fireworks**: fuegos artificiales frecuentes con cantidad, tamaño de explosión y escala configurables.
- **Confetti**: lluvia de confeti con modo opcional de confeti al hacer clic con el ratón.
- **Browser**: superposición de navegador a pantalla completa con URL y ajustes multimedia.
- **GLSL Shader**: superposición de shader personalizado a pantalla completa (para efectos visuales animados o estáticos basados en shaders).

# Superposición de navegador: interactiva o pasiva

La superposición Browser se puede configurar como un navegador interactivo o como una capa visual pasiva.

- Los ajustes **Process Mouse/Keyboard** controlan si el propio navegador procesa la entrada.
- Los ajustes **Consume Mouse/Keyboard** controlan si la entrada queda bloqueada para el menú que está detrás.

Ejemplos prácticos de configuración:

- Navegador interactivo en primer plano: activa tanto **Process** como **Consume**.
- Capa visual solo de navegador: desactiva **Process** y desactiva **Consume**.

> [!IMPORTANT]
> La superposición de decoración Browser requiere el mod **MCEF**.
