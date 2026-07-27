---
title: Superposiciones decorativas
description: >-
  Añade superposiciones visuales a pantalla completa a los menús en el editor de
  diseños de FancyMenu.
---
# Superposiciones decorativas

Las superposiciones decorativas son efectos a pantalla completa que se renderizan delante de los elementos del menú.

Son útiles cuando quieres añadir atmósfera o movimiento a un menú sin tener que crear esos efectos manualmente.

# Dónde encontrarlo

Abre un diseño en el editor de diseños y luego haz clic derecho sobre el fondo del editor y abre **Superposiciones decorativas**.

# Inicio rápido

1. Abre un diseño en el editor de diseños.
2. Haz clic derecho en el fondo (zona vacía).
3. Abre **Superposiciones decorativas**.
4. Selecciona un tipo de superposición.
5. Establece **Mostrar superposición** en **Habilitado**.
6. Configura los ajustes de la superposición.
7. Guarda el diseño y prueba la pantalla.

# Cómo funcionan los tipos de superposición

Cada tipo de superposición tiene su propio submenú y su propio interruptor **Mostrar superposición**.

- Puedes habilitar solo los tipos que quieras.
- Puedes combinar varios tipos habilitados en un mismo diseño.
- Los ajustes son específicos de cada tipo de superposición (por ejemplo, color, intensidad, velocidad, densidad, escala, comportamiento especial).

> [!INFO]
> Es posible apilar varias instancias del mismo tipo de superposición usando varios diseños con ese mismo tipo habilitado.

# Tipos de superposición

- **Nieve**: nieve con acumulación opcional sobre superficies/botones.
- **Lluvia**: lluvia con charcos, gotas y destellos de trueno opcionales.
- **Luciérnagas**: grupos de luciérnagas en movimiento con cantidad de grupos, densidad, tamaño y color configurables.
- **Luces de cadena**: combinaciones de guirnaldas configurables, colores de luz, comportamiento del viento/parpadeo y modo de color festivo.
- **Hojas**: hojas cayendo con colores, viento, velocidad, escala y densidad configurables.
- **Fuegos artificiales**: fuegos artificiales frecuentes con cantidad, tamaño de la explosión y escala configurables.
- **Confeti**: lluvia de confeti con modo opcional de confeti al hacer clic con el ratón.
- **Buddy**: una mascota virtual interactiva con hambre, felicidad, energía, diversión, actividades, niveles, logros y estado persistente.
- **Navegador**: superposición de navegador a pantalla completa con ajustes de URL y medios.
- **Shader GLSL**: superposición personalizada de shader a pantalla completa (para efectos visuales animados o estáticos basados en shaders).

# Mascota virtual Buddy

La superposición **Buddy** es una mascota virtual estilo Tamagotchi, no solo un personaje visual. Camina por la parte inferior de la pantalla, muestra globos de pensamiento para sus necesidades, reacciona a la interacción y conserva su estado entre sesiones de juego.

## Necesidades y controles

Buddy registra cuatro valores de `0` a `100`:

- **Hambre**: disminuye con el tiempo y se recupera con comida.
- **Felicidad**: disminuye con el tiempo y aumenta con los cuidados, incluyendo las caricias y el juego.
- **Energía**: disminuye mientras está despierto y durante las actividades, y luego se regenera mientras duerme.
- **Diversión**: disminuye con el tiempo y aumenta mientras juega.

Usa estos controles con el ratón y la pantalla de estado para cuidarlo:

- **Haz clic izquierdo sobre Buddy** para acariciarlo. Hacer clic izquierdo mientras duerme lo despierta y aplica una pequeña penalización de felicidad.
- **Haz clic derecho sobre Buddy** para abrir su pantalla de estado. La pestaña Stats muestra las cuatro necesidades, el nivel y la XP; la pestaña Achievements muestra el progreso de los logros.
- Selecciona **Feed** en la pantalla de estado y luego arrastra la comida hasta Buddy. La comida restaura el hambre y la felicidad.
- Selecciona **Play** en la pantalla de estado y luego arrastra y suelta la pelota. La pelota usa el movimiento del ratón para calcular la velocidad del lanzamiento, y Buddy puede perseguirla, atraparla, sostenerla y jugar con ella.
- Selecciona **Sleep** cuando el botón esté disponible para recuperar energía. Buddy también se duerme automáticamente cuando su energía se vuelve críticamente baja.
- Buddy a veces deja excrementos. **Haz clic izquierdo sobre el excremento** para limpiarlo. Si dejas al menos tres excrementos en pantalla, la felicidad disminuye continuamente hasta que queden menos de tres; el número máximo de excrementos es configurable.

## XP, niveles y logros

Cuidar de Buddy, limpiar excrementos, mantener buenas necesidades y completar otros hitos otorga XP. Buddy empieza en el nivel 1 y puede llegar al nivel 30. Los niveles más altos reducen gradualmente el consumo de hambre, felicidad y energía (hasta un 50 % en el nivel 30) y mejoran varios efectos de cuidado y de XP.

Los logros registran hitos de interacción, estadísticas, nivel, sesión y especiales. Abre la pantalla de estado con clic derecho para consultar ambos sistemas de progreso.

## Muerte y reinicio de la partida guardada

**Buddy Can Die** está habilitado por defecto. Si el hambre o la felicidad permanecen continuamente en `0` durante **10 horas reales**, Buddy muere y es sustituido por una lápida. Volver a subir la necesidad que está a cero antes de que expire el temporizador reinicia el temporizador de esa necesidad; desactivar **Buddy Can Die** borra ambos temporizadores.

Para empezar de nuevo después de la muerte, haz clic izquierdo sobre la lápida. También puedes usar **Reset Buddy Save** en cualquier momento en los ajustes de la superposición Buddy. Al reiniciar se eliminan tanto la partida guardada del estado de la mascota como la partida guardada separada de niveles/logros para esa instancia de la superposición.

> [!WARNING]
> Reiniciar una partida guardada de Buddy elimina de forma permanente sus necesidades, nivel, XP, logros, contadores de actividad y el estado guardado de excrementos.

## Persistencia y personalización

El estado de Buddy se guarda automáticamente aproximadamente cada dos minutos y cuando se cierra su pantalla. El estado de la mascota y el estado de niveles usan archivos JSON separados para cada instancia de la superposición dentro de `<game-directory>/fancymenu_data/buddy/`. Consulta [Ubicaciones de almacenamiento de datos](./data-storage-locations) para ver la referencia completa de rutas de FancyMenu.

Los ajustes de la superposición también te permiten reemplazar el atlas de sprites de Buddy, los objetos de interacción, los iconos de necesidades, las texturas de la pantalla de estado y la lápida. Los ajustes avanzados de estadísticas controlan el desgaste, los costes y ganancias de las actividades, la eficacia de los cuidados, el número máximo de excrementos y si la muerte está habilitada.

# Superposición del navegador: interactiva vs pasiva

La superposición del navegador se puede configurar como un navegador interactivo o como una capa visual pasiva.

- Los ajustes **Process Mouse/Keyboard** controlan si el propio navegador procesa la entrada.
- Los ajustes **Consume Mouse/Keyboard** controlan si la entrada queda bloqueada para el menú que hay detrás.

Ejemplos prácticos de configuración:

- Navegador interactivo en primer plano: habilita tanto **Process** como **Consume**.
- Capa de navegador solo visual: deshabilita **Process** y deshabilita **Consume**.

> [!IMPORTANT]
> La superposición decorativa del navegador requiere el mod **MCEF**.
