---
title: Superposiciones de decoración
description: >-
  Agrega superposiciones visuales a pantalla completa a los menús en el editor
  de diseños de FancyMenu.
---
# Superposiciones de decoración

Las Superposiciones de decoración son efectos a pantalla completa que se renderizan por delante de los elementos de tu menú.

Son útiles cuando quieres agregar ambiente o movimiento a un menú sin construir esos efectos manualmente.

# Dónde encontrarlo

Abre un diseño en el editor de diseños, luego haz clic derecho en el fondo del editor y abre **Superposiciones de decoración**.

# Inicio rápido

1. Abre un diseño en el editor de diseños.
2. Haz clic derecho en el fondo (área vacía).
3. Abre **Superposiciones de decoración**.
4. Selecciona un tipo de superposición.
5. Configura **Mostrar superposición** en **Habilitado**.
6. Ajusta la configuración de la superposición.
7. Guarda el diseño y prueba la pantalla.

# Cómo funcionan los tipos de superposición

Cada tipo de superposición tiene su propio submenú y su propio interruptor **Mostrar superposición**.

- Puedes habilitar solo los tipos que quieras.
- Puedes combinar varios tipos habilitados en un solo diseño.
- La configuración es por tipo de superposición (por ejemplo: color, intensidad, velocidad, densidad, escala, comportamiento especial).

> [!INFO]
> Es posible apilar varias instancias del mismo tipo de superposición usando varios diseños con ese mismo tipo habilitado.

# Tipos de superposición

- **Nieve**: nieve con acumulación opcional sobre superficies/botones.
- **Lluvia**: lluvia con charcos, goteras y destellos de trueno opcionales.
- **Luciérnagas**: grupos de luciérnagas en movimiento con cantidad de grupos, densidad, tamaño y color configurables.
- **Luces de cadena**: combinaciones de cadenas configurables, colores de luces, comportamiento de viento/parpadeo y modo de color festivo.
- **Hojas**: hojas que caen con colores, viento, velocidad, escala y densidad configurables.
- **Fuegos artificiales**: fuegos artificiales frecuentes con cantidad, tamaño de explosión y escala configurables.
- **Confeti**: lluvia de confeti con modo opcional de confeti al hacer clic con el mouse.
- **Buddy**: una mascota virtual interactiva con hambre, felicidad, energía, diversión, actividades, niveles, logros y estado persistente.
- **Navegador**: superposición de navegador a pantalla completa con configuración de URL y medios.
- **Shader GLSL**: superposición personalizada de shader a pantalla completa (para efectos visuales animados o estáticos basados en shaders).

# Mascota virtual Buddy

La superposición **Buddy** es una mascota virtual al estilo Tamagotchi, no solo un personaje visual. Camina a lo largo de la parte inferior de la pantalla, muestra globos de pensamiento para sus necesidades, reacciona a la interacción y conserva su estado entre sesiones de juego.

## Necesidades y controles

Buddy rastrea cuatro valores de `0` a `100`:

- **Hambre** disminuye con el tiempo y se restaura con comida.
- **Felicidad** disminuye con el tiempo y aumenta mediante cuidados, incluyendo caricias y juego.
- **Energía** disminuye mientras está despierto y durante las actividades, y luego se regenera mientras duerme.
- **Diversión** disminuye con el tiempo y aumenta mientras juega.

Usa estos controles del mouse y la pantalla de estado para cuidarlo:

- **Haz clic izquierdo en Buddy** para acariciarlo. Hacer clic izquierdo mientras duerme lo despierta y aplica una pequeña penalización a la felicidad.
- **Haz clic derecho en Buddy** para abrir su pantalla de estado. La pestaña de Estadísticas muestra las cuatro necesidades, nivel y XP; la pestaña de Logros muestra el progreso de los logros.
- Selecciona **Alimentar** en la pantalla de estado, luego arrastra la comida hacia Buddy. La comida restaura hambre y felicidad.
- Selecciona **Jugar** en la pantalla de estado, luego arrastra y suelta la pelota. La pelota usa el movimiento del mouse para calcular la velocidad del lanzamiento, y Buddy puede perseguirla, atraparla, sostenerla y jugar con ella.
- Selecciona **Dormir** cuando el botón esté disponible para restaurar energía. Buddy también se duerme automáticamente cuando su energía baja de forma crítica.
- Buddy ocasionalmente deja popó. **Haz clic izquierdo en la popó** para limpiarla. Dejar al menos tres popós en pantalla reduce continuamente la felicidad hasta que queden menos de tres; la cantidad máxima de popós es configurable.

## XP, niveles y logros

Cuidar a Buddy, limpiar popó, mantener buenas necesidades y completar otros hitos otorga XP. Buddy comienza en nivel 1 y puede llegar hasta el nivel 30. Los niveles más altos reducen gradualmente la disminución de hambre, felicidad y energía (hasta 50% en el nivel 30) y mejoran varios efectos de cuidado y XP.

Los logros rastrean hitos de interacción, estadísticas, nivel, sesión y especiales. Abre la pantalla de estado con clic derecho para revisar ambos sistemas de progreso.

## Muerte y restablecimiento del guardado

**Buddy Can Die** está habilitado de forma predeterminada. Si hambre o felicidad permanecen continuamente en `0` durante **10 horas reales**, Buddy muere y es reemplazado por una lápida. Elevar la necesidad en cero antes de que expire el temporizador restablece el temporizador de esa necesidad; deshabilitar **Buddy Can Die** borra ambos temporizadores.

Para empezar de nuevo después de su muerte, haz clic izquierdo en la lápida. También puedes usar **Restablecer guardado de Buddy** en la configuración de la superposición de Buddy en cualquier momento. Restablecer elimina tanto el guardado del estado de la mascota como el guardado separado de niveles/logros para esa instancia de la superposición.

> [!WARNING]
> Restablecer un guardado de Buddy elimina permanentemente sus necesidades, nivel, XP, logros, contadores de actividad y estado de popó guardado.

## Persistencia y personalización

El estado de Buddy se guarda automáticamente aproximadamente cada dos minutos y cuando se cierra su pantalla. El estado de la mascota y el estado de niveles usan archivos JSON separados para cada instancia de superposición dentro de `<game-directory>/fancymenu_data/buddy/`. Consulta [Ubicaciones de almacenamiento de datos](./data-storage-locations) para ver la referencia completa de la ruta de FancyMenu.

La configuración de la superposición también te permite reemplazar el atlas de sprites de Buddy, los elementos de interacción, los íconos de necesidades, las texturas de la pantalla de estado y la lápida. La configuración avanzada de estadísticas controla la disminución, los costos y ganancias de actividades, la efectividad del cuidado, la cantidad máxima de popós y si la muerte está habilitada.

# Superposición de navegador: interactiva vs pasiva

La superposición de Navegador puede configurarse como un navegador interactivo o como una capa visual pasiva.

- La configuración **Procesar mouse/teclado** controla si el navegador maneja la entrada por sí mismo.
- La configuración **Consumir mouse/teclado** controla si la entrada se bloquea para el menú que está detrás.

Ejemplos prácticos de configuración:

- Navegador interactivo al frente: habilita tanto **Procesar** como **Consumir**.
- Capa de navegador solo visual: deshabilita **Procesar** y deshabilita **Consumir**.

> [!IMPORTANT]
> La superposición de decoración del Navegador requiere el mod **MCEF**.
