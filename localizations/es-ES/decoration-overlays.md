---
title: Superposiciones decorativas
description: >-
  Añade superposiciones visuales a pantalla completa a los menús en el editor de
  diseños de FancyMenu.
---
# Superposiciones decorativas

Las superposiciones decorativas son efectos a pantalla completa que se renderizan delante de los elementos del menú.

Son útiles cuando quieres añadir ambiente o movimiento a un menú sin tener que crear esos efectos manualmente.

# Dónde encontrarlo

Abre un diseño en el editor de diseños, haz clic derecho en el fondo del editor y abre **Superposiciones decorativas**.

# Inicio rápido

1. Abre un diseño en el editor de diseños.
2. Haz clic derecho en el fondo (zona vacía).
3. Abre **Superposiciones decorativas**.
4. Selecciona un tipo de superposición.
5. Establece **Mostrar superposición** en **Activado**.
6. Configura los ajustes de la superposición.
7. Guarda el diseño y prueba la pantalla.

# Cómo funcionan los tipos de superposición

Cada tipo de superposición tiene su propio submenú y su propio interruptor **Mostrar superposición**.

- Puedes activar solo los tipos que quieras.
- Puedes combinar varios tipos activados en un mismo diseño.
- Los ajustes son específicos de cada tipo de superposición (por ejemplo, color, intensidad, velocidad, densidad, escala y comportamiento especial).

> [!INFO]
> Es posible apilar varias instancias del mismo tipo de superposición usando varios diseños con el mismo tipo activado.

# Tipos de superposición

- **Nieve**: nevada con acumulación opcional de nieve en superficies y botones.
- **Lluvia**: lluvia con charcos, goteos y destellos de truenos opcionales.
- **Luciernagas**: grupos de luciérnagas en movimiento con cantidad, densidad, tamaño y color configurables.
- **Guirnaldas de luces**: combinaciones de guirnaldas, colores de las luces, comportamiento del viento y del parpadeo, y modo de colores festivos configurables.
- **Hojas**: hojas que caen con colores, viento, velocidad, escala y densidad configurables.
- **Fuegos artificiales**: fuegos artificiales frecuentes con cantidad, tamaño de explosión y escala configurables.
- **Confeti**: lluvia de confeti con un modo opcional de confeti al hacer clic con el ratón.
- **Buddy**: mascota virtual interactiva con hambre, felicidad, energía, diversión, actividades, niveles, logros y estado persistente.
- **Navegador**: superposición de navegador a pantalla completa con ajustes de URL y contenido multimedia.
- **Sombreado GLSL**: superposición de sombreado personalizado a pantalla completa (para efectos visuales animados o estáticos basados en sombreadores).

# Mascota virtual Buddy

La superposición **Buddy** es una mascota virtual al estilo de un Tamagotchi, no solo un personaje visual. Camina por la parte inferior de la pantalla, muestra bocadillos de pensamiento para indicar sus necesidades, reacciona a las interacciones y conserva su estado entre sesiones de juego.

## Necesidades y controles

Buddy controla cuatro valores de `0` a `100`:

- **Hambre** disminuye con el tiempo y se recupera con comida.
- **Felicidad** disminuye con el tiempo y aumenta al cuidarlo, lo que incluye acariciarlo y jugar.
- **Energía** disminuye mientras está despierto y durante las actividades, y se regenera mientras duerme.
- **Diversión** disminuye con el tiempo y aumenta mientras juega.

Usa estos controles del ratón y la pantalla de estado para cuidarlo:

- **Haz clic izquierdo en Buddy** para acariciarlo. Si haces clic izquierdo mientras duerme, se despertará y sufrirá una pequeña penalización de felicidad.
- **Haz clic derecho en Buddy** para abrir su pantalla de estado. La pestaña Estadísticas muestra las cuatro necesidades, el nivel y la experiencia; la pestaña Logros muestra el progreso de los logros.
- Selecciona **Dar de comer** en la pantalla de estado y arrastra la comida hasta Buddy. La comida restaura el hambre y la felicidad.
- Selecciona **Jugar** en la pantalla de estado y arrastra y suelta la pelota. La pelota usa el movimiento del ratón para calcular la velocidad del lanzamiento, y Buddy puede perseguirla, atraparla, sostenerla y jugar con ella.
- Selecciona **Dormir** cuando el botón esté disponible para restaurar la energía. Buddy también se duerme automáticamente cuando su energía es demasiado baja.
- Buddy deja excrementos ocasionalmente. **Haz clic izquierdo en el excremento** para limpiarlo. Si quedan al menos tres excrementos en pantalla, la felicidad disminuye continuamente hasta que queden menos de tres; la cantidad máxima de excrementos se puede configurar.

## Experiencia, niveles y logros

Cuidar de Buddy, limpiar excrementos, mantener sus necesidades en buen estado y completar otros hitos otorga experiencia. Buddy comienza en el nivel 1 y puede alcanzar el nivel 30. Los niveles superiores reducen gradualmente el deterioro del hambre, la felicidad y la energía (hasta un 50 % en el nivel 30), y mejoran varios efectos relacionados con los cuidados y la experiencia.

Los logros registran hitos de interacción, estadísticas, nivel, sesiones y otros hitos especiales. Abre la pantalla de estado con un clic derecho para consultar ambos sistemas de progreso.

## Muerte y reinicio de la partida guardada

**Buddy puede morir** está activado de forma predeterminada. Si el hambre o la felicidad permanecen continuamente en `0` durante **10 horas reales**, Buddy muere y es reemplazado por una lápida. Aumentar la necesidad cuyo valor sea cero antes de que expire el temporizador reinicia el temporizador de esa necesidad; desactivar **Buddy puede morir** borra ambos temporizadores.

Para empezar de nuevo tras la muerte, haz clic izquierdo en la lápida. También puedes usar **Reiniciar partida guardada de Buddy** en los ajustes de la superposición de Buddy en cualquier momento. Al reiniciar, se eliminan tanto la partida guardada del estado de la mascota como la partida guardada independiente de niveles y logros de esa instancia de superposición.

> [!WARNING]
> Reiniciar una partida guardada de Buddy elimina permanentemente sus necesidades, nivel, experiencia, logros, contadores de actividad y estado guardado de los excrementos.

## Persistencia y personalización

El estado de Buddy se guarda automáticamente aproximadamente cada dos minutos y cuando se cierra su pantalla. El estado de la mascota y el estado de los niveles usan archivos JSON independientes para cada instancia de superposición dentro de `<game-directory>/fancymenu_data/buddy/`. Consulta [Ubicaciones de almacenamiento de datos](./data-storage-locations) para ver la referencia completa de rutas de FancyMenu.

Los ajustes de la superposición también permiten sustituir el atlas de sprites de Buddy, los objetos de interacción, los iconos de necesidades, las texturas de la pantalla de estado y la lápida. Los ajustes avanzados de estadísticas controlan el deterioro, los costes y las ganancias de las actividades, la eficacia de los cuidados, la cantidad máxima de excrementos y si la muerte está activada.

# Superposición de navegador: interactiva frente a pasiva

La superposición de navegador se puede configurar como un navegador interactivo o como una capa visual pasiva.

- Los ajustes **Procesar ratón/teclado** controlan si el propio navegador gestiona la entrada.
- Los ajustes **Consumir ratón/teclado** controlan si la entrada se bloquea para el menú que queda detrás.

Ejemplos de configuración:

- Navegador interactivo en primer plano: activa **Procesar** y **Consumir**.
- Capa de navegador solo visual: desactiva **Procesar** y **Consumir**.

> [!IMPORTANT]
> La superposición decorativa de navegador requiere el mod **[Rinku](https://modrinth.com/mod/rinku)**.
