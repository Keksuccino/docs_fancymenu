---
title: Preguntas frecuentes
description: Preguntas frecuentes.
---

# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?
Para recibir la mejor ayuda posible, proporciona tanto contexto como sea posible:
1.  **Una descripción clara del problema:** ¿Qué esperabas que ocurriera y qué ha ocurrido realmente?
2.  **Tu archivo `latest.log`:** Es el archivo más importante para diagnosticar problemas. Encuéntralo en la carpeta `/logs/` de tu instancia. **No envíes un registro de crash** salvo que te lo pidan específicamente; `latest.log` es mucho más útil. Usa un sitio como https://gist.github.com para compartirlo.
3.  **Tu versión de Minecraft:** (p. ej., 1.20.1)
4.  **Tu cargador de mods y su versión:** (p. ej., Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (p. ej., 3.5.2)
6.  **Capturas de pantalla o vídeos** del problema también pueden ser muy útiles.

### ¿Cómo cambio la superposición de los elementos (poner algo delante o detrás de otro)?
*   **Personalizado vs. personalizado:** Para cambiar el orden de renderizado de tus propios elementos personalizados, usa el **widget Layers**. Puedes abrirlo desde la barra de menú: **Window -> Widgets -> Layers**. Desde ahí, puedes arrastrar elementos hacia arriba o hacia abajo en la jerarquía. También puedes hacer clic derecho en un elemento y usar "Move One Layer Up/Down".
*   **Personalizado vs. Vanilla:** Para renderizar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, para poner una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Render Custom Elements Behind Vanilla"**.

### ¿Puedo excluir ciertos botones de una plantilla universal de botones?
**No. Si un botón de plantilla tiene texturas personalizadas configuradas, estas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic?
Usa un **Action Script**.
1.  Haz clic derecho en el botón en el editor.
2.  Selecciona **Edit Action Script**.
3.  Haz clic en **Add Action** y elige de la lista (por ejemplo, `Open Screen or Custom GUI`, `Join Server`, `Set Variable Value`).
*   Más información: [Action Scripts](https://docs.fancymenu.net/en/action-scripts)

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?
Sí, esto se hace usando **Custom GUIs**.
1.  En la barra de menú, ve a **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Haz clic en **"New GUI"** y asígnale un identificador único.
3.  Después puedes abrir esta nueva pantalla vacía y crear un diseño para ella, añadiendo cualquier elemento que quieras.
4.  Esta Custom GUI se puede abrir después mediante la acción de un botón.
*   Más información: [Custom GUIs](https://docs.fancymenu.net/en/custom-guis)

### Mi juego tarda mucho en cargar después de activar la precarga.
Esto es el comportamiento esperado. Pre-cargar recursos grandes, como animaciones o sonidos de alta resolución, durante el arranque inicial aumentará de forma natural el tiempo de carga del juego.

### ¡Mi animación FMA consume demasiada RAM!
Los archivos FMA clásicos pueden consumir mucha memoria cuando contienen muchos fotogramas de alta resolución. FancyMenu 3.9.0 añade AFMA, que es mucho mejor para texturas animadas grandes o complejas. En los archivos FMA clásicos, mantén las animaciones cortas y evita cantidades de fotogramas/resoluciones muy grandes. Las animaciones están pensadas para bucles cortos y decorativos, no para reproducir vídeos completos.

### ¿FancyMenu funciona con OptiFine?
No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda encarecidamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
*   Más información: [OptiFine Alternatives](https://docs.fancymenu.net/en/optifine-alternatives)

### Mi juego se cierra. ¿Cómo averiguo si es un conflicto entre mods?
La mejor manera de comprobar si hay un conflicto entre mods es **ejecutar el juego solo con FancyMenu y sus dependencias** (Konkrete, Melody). Si el cierre ya no ocurre, puedes volver a añadir el resto de mods en pequeños grupos hasta que vuelva a fallar para identificar el mod conflictivo.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.
Normalmente esto significa que el otro mod añade sus botones de una forma no estándar con la que FancyMenu no puede interactuar. Es un problema que el desarrollador de ese otro mod tendría que corregir por su parte. FancyMenu no puede personalizar elementos que no puede "ver".

### ¿Puedo usar diseños de FancyMenu en un servidor?
FancyMenu es un mod del lado del cliente. Todos los diseños y personalizaciones están en el cliente del jugador. No puedes poner diseños en un servidor para obligar a los jugadores a verlos. Sin embargo, puedes distribuir tu carpeta `config/fancymenu` como parte de un modpack. Si quieres usar comandos como `/fmvariable` o `/openguiscreen` desde el servidor, entonces FancyMenu (o su plugin de Spigot) debe estar instalado en el servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?
FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y mejor rendimiento. La v2 está obsoleta, ya no recibe soporte y le faltan muchas funciones como los marcadores de posición avanzados y los scripts. Se recomienda encarecidamente usar v3 en una versión moderna de Minecraft (1.18.2+). Los diseños de v2 pueden convertirse automáticamente a v3 al cargarlos, pero puede ser necesario hacer algunos ajustes manuales.

### ¿Dónde puedo encontrar diseños y plantillas ya hechos?
La comunidad de FancyMenu comparte diseños en el canal `#layout-templates` del servidor oficial de Discord de Keksuccino's Mods.

### ¿Cómo puedo hacer que la entidad del jugador se renderice detrás de otros elementos?
No puedes. Debido a cómo Minecraft renderiza las entidades, el elemento Player Entity casi siempre se renderizará delante de otros elementos 2D, independientemente de los ajustes de capa.

### ¡Mi Player Entity solo tiene una pierna! ¿Qué ha pasado?
Es un fallo visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos del jugador. Revisa los ajustes de Pose de la Player Entity para ver si las piernas se han rotado o movido por accidente.

### ¿Cómo creo un retraso entre acciones en un script?
FancyMenu 3.9.0 añade bloques **Delay** y **Execute Later** a los action scripts. Úsalos para la mayoría de la lógica de acciones retrasadas. Para lógica de fondo repetitiva, usa [Schedulers](https://docs.fancymenu.net/en/schedulers).

### ¿Puedo personalizar menús del mod Create?
No. FancyMenu tiene incompatibilidades conocidas con las GUIs complejas de Create. La personalización de las pantallas de Create se ha deshabilitado intencionadamente para evitar cierres.

### ¿Por qué desaparecen los botones del mod X en el editor?
Esto significa que el mod añade sus botones de una forma personalizada, no vanilla. FancyMenu no puede "ver" ni interactuar con estos elementos, así que no puede personalizarlos. El desarrollador del otro mod tendría que cambiar cómo añade sus botones para que fueran compatibles.

### ¿Cuál es la resolución recomendada para imágenes de fondo y texturas de botones?
Fondos: Una imagen estándar de 1920x1080 (1080p) es un muy buen punto de partida y se adaptará bien a la mayoría de los usuarios.
Botones: La mayoría de los botones vanilla tienen una anchura de unos 150-200 píxeles y una altura de 20 píxeles. Ajustar las texturas personalizadas a este tamaño es una buena práctica para mantener la coherencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?
FancyMenu por sí mismo no puede detectar eventos del juego como este. Sin embargo, puedes integrarlo con un mod de misiones como FTB Quests. La mayoría de los mods de misiones permiten ejecutar un comando como recompensa de una misión. Tendrías que configurar la recompensa para ejecutar el comando `/openguiscreen` o `/fmvariable` e interactuar así con tus menús.

### ¿Cómo hago que un botón esté inactivo o "apagado"?
Puedes controlar el estado activo de un botón usando Loading Requirements.
Haz clic derecho en el botón en el editor y selecciona "Active State".
Añade un requisito que deba cumplirse para que el botón esté activo. Por ejemplo, para desactivar permanentemente un botón, podrías añadir un requisito Is Number que compruebe si 0 es igual a 1 (lo que siempre es falso).
Ahora el botón usará su textura de "Inactive Background" y no se podrá pulsar.

### ¿Cómo puedo quitar el encabezado y el pie de página (las barras de textura de tierra) de las pantallas desplazables?
En FancyMenu v3 puedes personalizarlos. En el editor de diseño, haz clic derecho en el fondo del editor y busca opciones como "Customize Header/Footer". Puedes configurar sus texturas para que sean completamente transparentes y así eliminarlos visualmente. Ten en cuenta que esto puede no funcionar en todas las pantallas, especialmente en las más antiguas o muy modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón está desactivado.
Primero debes habilitar las personalizaciones para esa pantalla mediante **menu bar -> Customization -> Current Screen Customizations -> toggle it to Enabled**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. Entonces solo aparece una pantalla vacía.

Esto podría significar que has creado por accidente un diseño universal en lugar de uno **para la pantalla actual**.

También podría significar que la pantalla que estás personalizando es una pantalla desplazable, es decir, una pantalla que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que añade elementos de una forma no vanilla, lo que hace que FancyMenu no pueda personalizar esos elementos.

### Hay cajas grises extrañas en mi elemento Text.

Estas cajas o rectángulos translúcidos (de baja opacidad) pueden aparecer en el borde derecho o inferior de tu elemento Text y no son un error. Son los controles de arrastre de desplazamiento del elemento Text, ya que el elemento es desplazable.

Si no quieres que estas cajas sean visibles, puedes hacer clic derecho en el elemento y desactivar por completo el desplazamiento, o también puedes configurar las texturas de los controles de arrastre como completamente transparentes en ese mismo menú de clic derecho si quieres que el elemento siga siendo desplazable.

### ¿Cómo puedo mostrar el último changelog de Minecraft en mis menús?

Hay un gran [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte los changelogs de Minecraft a Markdown compatible con FancyMenu, ¡así puedes mostrar el último changelog de MC en tus menús! Se actualiza a diario para obtener los nuevos changelogs.

Por ejemplo, para mostrar el último changelog de Minecraft en un elemento Text, configura su **Source Mode** como **Resource** y define su origen de recurso como **Web**. Después usa esta URL como origen: `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`

### ¿Cuál es la forma más fácil de estirar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales de clic derecho para estirarlos horizontal y verticalmente. Al activarla, siempre se estirarán hasta ocupar todo el ancho y/o alto de la pantalla. El estiramiento horizontal y vertical se puede activar de forma independiente.

### No puedo hacer clic en botones ni interactuar con deslizadores cuando están detrás o delante de un elemento Text.

Esto ocurre porque los elementos Text son interactivos por defecto (para poder arrastrar el control de desplazamiento o hacer clic en los enlaces Markdown), lo que significa que consumen los clics del ratón y los eventos de desplazamiento. La mejor solución sería simplemente no mover botones detrás/delante de elementos Text, pero si no hay más remedio, puedes hacer que el elemento Text no sea interactivo **haciendo clic derecho sobre él** y estableciendo **Interactable** en **Disabled**. Ten en cuenta que esto convierte el elemento Text en texto estático no interactivo, por lo que ya no podrás desplazarte ni hacer clic en hipervínculos.

### ¿Cómo puedo hacer que los botones y deslizadores no se seleccionen ni reciban el foco al navegar en pantallas con las teclas de flecha y Tab?

Para que los botones y deslizadores no sean navegables, tienes que **hacer clic derecho** sobre ellos y establecer **Navigable** en **Disabled**. El botón o deslizador seguirá siendo pulsable, pero ya no podrás enfocarlo mediante la navegación con las teclas de flecha/Tab.

Esto también es útil si quieres añadir botones o deslizadores a la pantalla de chat, ya que así puedes seguir usando la tecla Flecha arriba para desplazarte por mensajes antiguos sin seleccionar accidentalmente botones o deslizadores en la pantalla.

### A uno de los menús contextuales de FancyMenu le falta una opción que debería estar ahí.

Los menús contextuales de FancyMenu (los menús que se abren al hacer clic derecho en algún sitio o al interactuar con las barras de menú) son DESPLAZABLES. Esto significa que puedes usar la rueda del ratón mientras el cursor esté sobre el menú para desplazarte hacia arriba o hacia abajo, lo que te permite ver más opciones que antes no eran visibles.
