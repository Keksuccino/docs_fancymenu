---
title: Superposiciones decorativas
description: >-
  Agrega superposiciones visuales de pantalla completa a los menús en el editor
  de diseños de FancyMenu.
---
# Superposiciones decorativas

Las superposiciones decorativas son efectos de pantalla completa que se muestran delante de los elementos de tu menú.

Son útiles cuando quieres agregar ambiente o movimiento a un menú sin tener que crear esos efectos manualmente.

# Dónde encontrarlo

Abre un diseño en el editor de diseños, haz clic derecho en el fondo del editor y abre **Superposiciones decorativas**.

# Inicio rápido

1. Abre un diseño en el editor de diseños.
2. Haz clic derecho en el fondo (área vacía).
3. Abre **Superposiciones decorativas**.
4. Selecciona un tipo de superposición.
5. Establece **Mostrar superposición** en **Activado**.
6. Configura los ajustes de la superposición.
7. Guarda el diseño y prueba la pantalla.

# Cómo funcionan los tipos de superposición

Cada tipo de superposición tiene su propio submenú y su propio interruptor **Mostrar superposición**.

- Puedes activar únicamente los tipos que quieras.
- Puedes combinar varios tipos activados en un mismo diseño.
- Los ajustes son independientes para cada tipo de superposición (por ejemplo, color, intensidad, velocidad, densidad, escala y comportamiento especial).

> [!INFO]
> Es posible apilar varias instancias del mismo tipo de superposición usando varios diseños con el mismo tipo activado.

# Tipos de superposición

- **Nevada**: nevada con acumulación opcional de nieve en superficies y botones.
- **Lluvia**: lluvia con charcos y goteos opcionales, además de destellos de trueno opcionales.
- **Luciérnagas**: grupos de luciérnagas en movimiento con cantidad de grupos, densidad, tamaño y color configurables.
- **Luces en serie**: combinaciones de series, colores de las luces, comportamiento del viento y parpadeo, y modo de colores festivos configurables.
- **Hojas**: hojas que caen con colores, viento, velocidad, escala y densidad configurables.
- **Fuegos artificiales**: fuegos artificiales frecuentes con cantidad, tamaño de explosión y escala configurables.
- **Confeti**: lluvia de confeti con un modo opcional de confeti al hacer clic con el mouse.
- **Buddy**: una mascota virtual interactiva con hambre, felicidad, energía, diversión, actividades, niveles, logros y estado persistente.
- **Navegador**: superposición de navegador de pantalla completa con ajustes de URL y multimedia.
- **Sombreado GLSL**: superposición de sombreado personalizado de pantalla completa (para efectos visuales animados o estáticos basados en sombreadores).

# Mascota virtual Buddy

La superposición **Buddy** es una mascota virtual al estilo Tamagotchi, no solo un personaje visual. Camina por la parte inferior de la pantalla, muestra burbujas de pensamiento relacionadas con sus necesidades, reacciona a las interacciones y conserva su estado entre sesiones de juego.

## Necesidades y controles

Buddy registra cuatro valores del `0` al `100`:

- **Hambre** disminuye con el tiempo y se recupera al darle comida.
- **Felicidad** disminuye con el tiempo y aumenta con los cuidados, incluyendo acariciarlo y jugar.
- **Energía** disminuye mientras está despierto y durante las actividades, y se regenera mientras duerme.
- **Diversión** disminuye con el tiempo y aumenta al jugar.

Usa estos controles del mouse y la pantalla de estado para cuidarlo:

- **Haz clic izquierdo en Buddy** para acariciarlo. Si haces clic izquierdo mientras duerme, se despertará y sufrirá una pequeña penalización de felicidad.
- **Haz clic derecho en Buddy** para abrir su pantalla de estado. La pestaña Estadísticas muestra sus cuatro necesidades, nivel y XP; la pestaña Logros muestra el progreso de los logros.
- Selecciona **Alimentar** en la pantalla de estado y luego arrastra la comida hasta Buddy. La comida recupera hambre y felicidad.
- Selecciona **Jugar** en la pantalla de estado y luego arrastra y suelta la pelota. La pelota usa el movimiento del mouse para calcular la velocidad del lanzamiento, y Buddy puede perseguirla, atraparla, sostenerla y jugar con ella.
- Selecciona **Dormir** cuando el botón esté disponible para recuperar energía. Buddy también se queda dormido automáticamente cuando su energía es críticamente baja.
- Buddy deja popó ocasionalmente. **Haz clic izquierdo en la popó** para limpiarla. Dejar al menos tres popós en pantalla reduce continuamente la felicidad hasta que queden menos de tres; la cantidad máxima de popós se puede configurar.

## XP, niveles y logros

Cuidar a Buddy, limpiar la popó, mantener buenas necesidades y completar otros hitos otorga XP. Buddy comienza en el nivel 1 y puede llegar al nivel 30. Los niveles más altos reducen gradualmente el deterioro del hambre, la felicidad y la energía (hasta un 50% en el nivel 30) y mejoran varios efectos de cuidado y XP.

Los logros registran hitos de interacción, estadísticas, nivel, sesión y categorías especiales. Abre la pantalla de estado con un clic derecho para revisar ambos sistemas de progreso.

## Muerte y reinicio de la partida guardada

**Buddy puede morir** está activado de forma predeterminada. Si el hambre o la felicidad permanecen continuamente en `0` durante **10 horas reales**, Buddy muere y es reemplazado por una lápida. Aumentar la necesidad que está en cero antes de que expire el temporizador reinicia el temporizador de esa necesidad; desactivar **Buddy puede morir** borra ambos temporizadores.

Para comenzar de nuevo después de una muerte, haz clic izquierdo en la lápida. También puedes usar **Reiniciar partida guardada de Buddy** en los ajustes de la superposición de Buddy en cualquier momento. Al reiniciar, se eliminan tanto la partida guardada del estado de la mascota como la partida guardada independiente de niveles y logros de esa instancia de superposición.

> [!WARNING]
> Reiniciar una partida guardada de Buddy elimina permanentemente sus necesidades, nivel, XP, logros, contadores de actividad y estado guardado de la popó.

## Persistencia y personalización

El estado de Buddy se guarda automáticamente aproximadamente cada dos minutos y cuando se cierra su pantalla. El estado de la mascota y el estado de niveles usan archivos JSON independientes para cada instancia de superposición dentro de `<game-directory>/fancymenu_data/buddy/`. Consulta [Ubicaciones de almacenamiento de datos](./data-storage-locations) para ver la referencia completa de las rutas de FancyMenu.

Los ajustes de la superposición también te permiten reemplazar el atlas de sprites de Buddy, los objetos de interacción, los íconos de necesidades, las texturas de la pantalla de estado y la lápida. Los ajustes avanzados de estadísticas controlan el deterioro, los costos y las ganancias de las actividades, la eficacia de los cuidados, la cantidad máxima de popós y si la muerte está activada.

# Superposición de navegador: interactiva o pasiva

La superposición de navegador se puede configurar como un navegador interactivo o como una capa visual pasiva.

- Los ajustes **Procesar mouse/teclado** controlan si el navegador procesa las entradas.
- Los ajustes **Consumir mouse/teclado** controlan si las entradas se bloquean para el menú que está detrás.

Ejemplos prácticos de configuración:

- Navegador interactivo al frente: activa **Procesar** y **Consumir**.
- Capa de navegador únicamente visual: desactiva **Procesar** y **Consumir**.

> [!IMPORTANT]
> La superposición decorativa Navegador requiere el mod **[Rinku](https://modrinth.com/mod/rinku)**.
