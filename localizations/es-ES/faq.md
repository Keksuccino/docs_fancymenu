---
title: Preguntas frecuentes
description: Preguntas frecuentes.
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para obtener la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que ocurriera y qué ocurrió realmente?
2.  **Tu archivo `latest.log`:** Lo encontrarás en `<game-directory>/logs/latest.log`. **No envíes un registro de crash** salvo que te lo pidan específicamente; `latest.log` normalmente contiene el contexto necesario. Usa un sitio como https://gist.github.com para publicarlo.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Capturas de pantalla o vídeos** del problema también pueden ser muy útiles.

### ¿Cómo cambio la jerarquía de elementos (poner algo delante o detrás de otro)?

*   **Personalizado vs. personalizado:** Abre **Window -> Editor Widgets -> Layers** y arrastra los elementos en la jerarquía. También puedes hacer clic derecho en un elemento y usar **Move One Layer Up/Down**. Consulta [Layers and Groups](./layers-and-groups).
*   **Personalizado vs. vanilla:** Para renderizar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, para poner una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Render Custom Elements Behind Vanilla"**.

### ¿Puedo excluir ciertos botones de una plantilla de botón universal?

**No. Si un botón de plantilla tiene texturas personalizadas configuradas, estas texturas se comparten siempre con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic?

Usa un [**Action Script**](./action-scripts).
1.  Haz clic derecho en el botón en el editor.
2.  Selecciona **Edit Action Script**.
3. Haz clic en **Add Action** y elige una acción, como [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) o [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Usa una [**Custom GUI**](./custom-guis).
1.  En la barra de menú, ve a **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Haz clic en **"New GUI"** y asígnale un identificador único.
3.  Después podrás abrir esta nueva pantalla vacía y crear un diseño para ella, añadiendo cualquier elemento que quieras.
4. Abre la Custom GUI con la [**Open Screen or Custom GUI** action](./action-scripts#open-screen-or-custom-gui-opengui).

### Mi juego tarda mucho en cargar después de activar la precarga.

Este comportamiento es normal. Precargar recursos grandes, como animaciones o sonidos de alta resolución, durante el inicio aumentará de forma natural el tiempo de carga del juego.

### ¡Mi animación FMA consume demasiada RAM!

Las [animaciones FMA](./fma) clásicas pueden consumir mucha memoria cuando contienen muchos fotogramas de alta resolución. AFMA está más pensado para texturas animadas grandes o complejas. Mantén las animaciones FMA clásicas cortas; usa [Video](./video) para la reproducción completa de vídeo.

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda encarecidamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [OptiFine Alternatives](./optifine-alternatives).

### Mi juego se cierra. ¿Cómo averiguo si es un conflicto entre mods?

La mejor forma de comprobar si hay un conflicto entre mods es **ejecutar el juego solo con FancyMenu y sus dependencias** (Konkrete, Melody). Si el cierre ya no ocurre, puedes volver a añadir tus otros mods en pequeños grupos hasta que vuelva a producirse el crash y así identificar el mod conflictivo.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods añaden widgets de formas que FancyMenu no puede detectar ni personalizar. Consulta [Vanilla/Mod Elements](./vanilla-elements) y, para pantallas basadas en listas, [Customizing Scrollable Screens](./customizing-scrollable-screens). Si el widget sigue sin aparecer, el mod que lo añade debe exponerlo como un widget de pantalla compatible.

### ¿Puedo usar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se guardan en el cliente del jugador; un servidor no puede imponerlos a un cliente no configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor cuando necesites [server commands](./commands), [FM Data](./fm-data), [server-side NBT access](./nbt-data-placeholder#server-side-placeholder), gamerules, estructuras o listeners del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y mejor rendimiento. V2 está obsoleto, ya no recibe soporte y carece de muchas funciones, como placeholders avanzados y scripting. Se recomienda encarecidamente usar v3 en una versión moderna de Minecraft (1.18.2+). Los diseños de V2 pueden convertirse automáticamente a v3 al cargarlos, pero puede que sea necesario hacer algunos ajustes manuales.

### ¿Dónde puedo encontrar diseños y plantillas ya hechos?

La comunidad de FancyMenu comparte diseños en el canal `#layout-templates` del servidor oficial de Discord de Keksuccino's Mods ("Kekscord").

### ¿Cómo puedo hacer que la entidad del jugador se renderice detrás de otros elementos?

Por lo general, no puedes forzar que un [Player Entity element](./elements#player-entity) quede detrás de elementos 2D normales mediante el [Layers widget](./layers-and-groups). Su renderizador puede ignorar el orden normal de capas de la interfaz. Diseña el diseño teniendo en cuenta esa limitación o usa una imagen prerenderizada cuando necesites un orden de capas estricto.

### ¡Mi entidad del jugador solo tiene una pierna! ¿Qué ha pasado?

Es un fallo visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos del jugador. Revisa la configuración de Pose de la Player Entity para ver si las piernas se han girado o movido por accidente.

### ¿Cómo creo un retraso entre acciones en un script?

Usa bloques [**Delay** o **Execute Later**](./action-scripts#what-are-statements) para lógica de acciones con retraso. Para lógica repetitiva en segundo plano, usa [Schedulers](./schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización está desactivada intencionadamente para las pantallas de Create. Consulta [Screens where customization is intentionally disabled](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Cuál es la resolución recomendada para imágenes de fondo y texturas de botones?

Fondos: una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se adaptará bien a la mayoría de usuarios.
Botones: la mayoría de los botones vanilla tienen unos 150-200 píxeles de ancho y 20 píxeles de alto. Mantener ese tamaño para las texturas personalizadas es una buena práctica para conservar la coherencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?
FancyMenu tiene muchos [listeners de eventos del juego integrados](./listeners), pero no existe un listener genérico para todos los sistemas de misiones de terceros. Si el mod de misiones admite recompensas por comando, usa una para ejecutar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) u otro [comando de FancyMenu](./commands) adecuado.

### ¿Cómo hago que un botón esté inactivo o "en gris"?

Puedes controlar el estado activo de un botón usando [Loading Requirements](./conditions).
Haz clic derecho en el botón en el editor y selecciona **Control Active State**.
Añade un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para comprobar si 0 es igual a 1.
El botón usará ahora su textura de "Inactive Background" y no se podrá pulsar.

### ¿Cómo puedo quitar la cabecera y el pie de página (las barras con textura de tierra) en las pantallas desplazables?

En el editor de diseños, abre **Layout Properties -> Header/Footer Customizations**. Establece las texturas como transparentes. Esta opción puede no estar disponible en algunas pantallas modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón está en gris.

Primero debes activar las personalizaciones para esa pantalla a través de **menu bar -> Customization -> Current Screen Customizations -> Enabled**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. Entonces solo aparece una pantalla vacía.

Esto puede significar que has creado un [Universal Layout](./universal-layouts) en lugar de uno **para la pantalla actual**.

También podría tratarse de una [pantalla desplazable](./customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que añade elementos de una forma no vanilla, lo que impide que FancyMenu pueda personalizar esos elementos.

### Hay unas extrañas cajas grises en mi elemento de texto.

Esas cajas translúcidas son los tiradores de desplazamiento del [elemento de texto](./elements#text), no un fallo de renderizado.

Si no quieres que esas cajas sean visibles, puedes hacer clic derecho en el elemento y desactivar el desplazamiento por completo, o también puedes establecer las texturas de los tiradores como completamente transparentes en el mismo menú de clic derecho, si quieres que el elemento siga siendo desplazable.

### ¿Cómo puedo mostrar el último changelog de Minecraft en mis menús?

Hay un gran [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte los changelogs de Minecraft a Markdown compatible con FancyMenu, ¡así puedes mostrar el último changelog de MC en tus menús! Se actualiza diariamente para obtener los nuevos changelogs.

Para mostrarlo en un [Text element](./elements#text), establece **Source Mode** en **Resource** y su recurso de origen en **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más fácil de estirar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales de clic derecho para estirarlos horizontal y verticalmente. Al activarla, se estirarán siempre hasta ocupar todo el ancho y/o alto de la pantalla. El estiramiento horizontal y vertical pueden activarse de forma independiente.

### No puedo hacer clic en botones ni interactuar con deslizadores cuando están detrás o delante de un elemento de texto.

Esto ocurre porque los elementos de texto son interactivos por defecto (para poder arrastrar el tirador de desplazamiento o hacer clic en enlaces Markdown), lo que significa que consumen los clics del ratón y los eventos de desplazamiento. Lo mejor sería simplemente no mover botones detrás o delante de elementos de texto, pero si no hay otra opción, puedes hacer que el elemento de texto no sea interactivo **haciendo clic derecho** sobre él y estableciendo **Interactable** en **Disabled**. Ten en cuenta que esto convierte el elemento de texto en texto estático no interactivo, por lo que ya no podrás desplazarte por él ni hacer clic en enlaces.

### ¿Cómo hago para que los botones y deslizadores dejen de seleccionarse o recibir el foco al navegar por pantallas con las teclas de flecha y Tab del teclado?

Para que los botones y deslizadores no sean navegables, debes **hacer clic derecho** sobre ellos y establecer **Navigable** en **Disabled**. El botón o deslizador seguirá siendo clicable, pero ya no podrás enfocarlo mediante la navegación con las teclas de flecha/Tab.

Esto también es útil si quieres añadir botones o deslizadores a la pantalla de chat, para que puedas seguir usando la tecla Flecha arriba para desplazarte por mensajes anteriores sin seleccionar accidentalmente botones o deslizadores en la pantalla.

### Falta una opción en uno de los menús contextuales de FancyMenu que debería estar ahí.

Los menús contextuales de FancyMenu (los menús que se abren cuando haces clic derecho en algún sitio o cuando interactúas con las barras de menú) son DESPLAZABLES. Esto significa que puedes usar la rueda del ratón mientras el cursor está sobre el menú para desplazarte hacia arriba o hacia abajo, lo que te permite ver más opciones que antes no eran visibles.

### No puedo personalizar la pantalla de título; sigue mostrando la original cuando salgo del editor.

Otro mod está sustituyendo la `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en su configuración. Si no tiene esa opción, FancyMenu no puede aplicar el diseño a la pantalla sustituta.
