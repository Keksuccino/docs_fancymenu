---
title: Preguntas frecuentes
description: Preguntas frecuentes.
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para obtener la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que ocurriera y qué ocurrió realmente?
2.  **Tu archivo `latest.log`:** Lo encontrarás en `<directorio-del-juego>/logs/latest.log`. **No envíes un registro de fallos** salvo que te lo pidan específicamente; `latest.log` suele contener el contexto necesario. Usa un sitio como https://gist.github.com cuando lo compartas.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Capturas de pantalla o vídeos** del problema también pueden ser muy útiles.

### ¿Cómo cambio la superposición de los elementos (poner algo delante de otro elemento o detrás)?

*   **Personalizado vs. personalizado:** Abre **Ventana -> Widgets del editor -> Capas** y arrastra los elementos en la jerarquía. También puedes hacer clic derecho en un elemento y usar **Mover una capa arriba/abajo**. Consulta [Capas y grupos](./layers-and-groups).
*   **Personalizado vs. Vanilla:** Para renderizar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, para poner una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Renderizar elementos personalizados detrás de Vanilla"**.

### ¿Puedo excluir ciertos botones de una plantilla universal de botón?

**No. Si un botón de plantilla tiene texturas personalizadas configuradas, estas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic?

Usa un [**Script de acciones**](./action-scripts).
1.  Haz clic derecho en el botón en el editor.
2.  Selecciona **Editar script de acciones**.
3. Haz clic en **Añadir acción** y elige una acción, como [**Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui), [**Unirse a un servidor**](./action-scripts#join-server-joinserver) o [**Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Usa una [**GUI personalizada**](./custom-guis).
1.  En la barra de menús, ve a **Personalización -> GUIs personalizadas -> Gestionar GUIs personalizadas**.
2.  Haz clic en **"Nueva GUI"** y asígnale un identificador único.
3.  Después puedes abrir esta nueva pantalla vacía y crear un diseño para ella, añadiendo todos los elementos que quieras.
4. Abre la GUI personalizada con la [**acción Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mi juego tarda mucho en cargar después de activar la precarga.

Este comportamiento es normal. Precargar recursos grandes, como animaciones o sonidos de alta resolución, durante el inicio aumentará de forma natural el tiempo de carga del juego.

### ¡Mi animación FMA usa demasiada RAM!

Las animaciones clásicas [FMA](./fma) pueden consumir mucha memoria cuando contienen muchos fotogramas de alta resolución. AFMA es más adecuada para texturas animadas grandes o complejas. Mantén las animaciones FMA clásicas cortas; usa [Vídeo](./video) para la reproducción de vídeo completa.

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda encarecidamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](./optifine-alternatives).

### Mi juego se cierra. ¿Cómo averiguo si es un conflicto entre mods?

La mejor forma de comprobar si hay un conflicto entre mods es **ejecutar el juego solo con FancyMenu y sus dependencias** (Konkrete, Melody). Si el fallo deja de ocurrir, puedes volver a añadir tus otros mods en grupos pequeños hasta que vuelva a producirse el cierre para identificar el mod conflictivo.

### Desaparece un botón de otro mod o no funciona cuando intento editarlo.

Normalmente esto significa que el otro mod añade sus botones de una forma no estándar con la que FancyMenu no puede interactuar. Es un problema que el desarrollador del otro mod tendría que corregir por su parte. FancyMenu no puede personalizar elementos que no puede "ver".

### ¿Puedo usar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se guardan en el cliente del jugador; un servidor no puede forzarlos en un cliente no configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor cuando necesites [comandos del servidor](./commands), [datos de FM](./fm-data), [acceso a NBT del lado del servidor](./nbt-data-placeholder#server-side-placeholder), gamerules, estructuras o listeners del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y mejor rendimiento. V2 está obsoleto, ya no recibe soporte y le faltan muchas funciones, como marcadores de posición avanzados y scripting. Se recomienda encarecidamente usar v3 en una versión moderna de Minecraft (1.18.2+). Los diseños de V2 pueden convertirse automáticamente a v3 al cargarlos, aunque puede ser necesario realizar algunos ajustes manuales.

### ¿Dónde puedo encontrar diseños y plantillas ya hechas?

La comunidad de FancyMenu comparte diseños en el canal `#layout-templates` del servidor oficial de Discord de Keksuccino's Mods ("Kekscord").

### ¿Cómo puedo hacer que la entidad del jugador se renderice detrás de otros elementos?

El [elemento Entidad del jugador](./elements#player-entity) normalmente se renderiza delante de los elementos 2D, independientemente del orden de capas.

### ¡Mi entidad del jugador solo tiene una pierna! ¿Qué ha pasado?

Es un fallo visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos de los jugadores. Revisa la configuración de Pose de la Entidad del jugador para comprobar si las piernas se han girado o movido por accidente.

### ¿Cómo creo un retraso entre acciones en un script?

Usa bloques de [**Retraso** o **Ejecutar más tarde**](./action-scripts#what-are-statements) para la lógica de acciones retardadas. Para lógica en segundo plano repetitiva, usa [Programadores](./schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización está desactivada intencionadamente para las pantallas de Create. Consulta [Pantallas en las que la personalización está desactivada intencionadamente](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Por qué desaparecen en el editor los botones del mod X?

Esto significa que el mod añade sus botones de una forma personalizada, no vanilla. FancyMenu no puede "ver" ni interactuar con estos elementos, así que no puede personalizarlos. El desarrollador del otro mod tendría que cambiar la forma en que añade sus botones para que sean compatibles.

### ¿Cuál es la resolución recomendada para las imágenes de fondo y las texturas de los botones?

Fondos: una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se adaptará bien a la mayoría de los usuarios.
Botones: la mayoría de los botones vanilla tienen un ancho de entre 150 y 200 píxeles y una altura de 20 píxeles. Igualar este tamaño para las texturas personalizadas es una buena práctica para mantener la coherencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?
FancyMenu tiene muchos [listeners de eventos del juego integrados](./listeners), pero no existe un listener genérico para todos los sistemas de misiones de terceros. Si el mod de misiones admite recompensas mediante comandos, usa una para ejecutar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) u otro [comando de FancyMenu](./commands) adecuado.

### ¿Cómo hago que un botón esté inactivo o "atenuado"?

Puedes controlar el estado activo de un botón usando [Requisitos de carga](./conditions).
Haz clic derecho en el botón en el editor y selecciona "Estado activo".
Añade un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Es número**](./conditions#is-number) para comprobar si 0 es igual a 1.
El botón usará ahora su textura de "Fondo inactivo" y no se podrá hacer clic en él.

### ¿Cómo puedo quitar el encabezado y el pie de página (las barras con textura de tierra) en pantallas desplazables?

En el editor de diseños, haz clic derecho en el fondo del editor y abre **Personalizar encabezado/pie de página**. Configura las texturas como transparentes. Esta opción puede no estar disponible en algunas pantallas modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón está en gris.

Primero debes activar las personalizaciones para esa pantalla en **barra de menús -> Personalización -> Personalizaciones de la pantalla actual -> activarlo en Habilitado**.

### No puedo personalizar ningún elemento de una pantalla al abrirla en el editor. Entonces solo aparece una pantalla vacía.

Esto puede significar que has creado un [Diseño universal](./universal-layouts) en lugar de uno **para la pantalla actual**.

También podría ser una [pantalla desplazable](./customizing-scrollable-screens), que FancyMenu no puede personalizar por defecto.

La tercera posibilidad es que sea una pantalla de un mod que añade elementos de una forma no vanilla, lo que impide que FancyMenu pueda personalizar esos elementos.

### Hay cajas grises extrañas en mi elemento de texto.

Estas cajas translúcidas son los controles de desplazamiento del [elemento de texto](./elements#text), no un error de renderizado.

Si no quieres que estas cajas sean visibles, puedes hacer clic derecho en el elemento y desactivar completamente el desplazamiento O también puedes configurar las texturas de los controles como totalmente transparentes en el mismo menú contextual, si quieres que el elemento siga siendo desplazable.

### ¿Cómo puedo mostrar el último changelog de Minecraft en mis menús?

Hay un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte los changelogs de Minecraft a Markdown compatible con FancyMenu, ¡así puedes mostrar el último changelog de MC en tus menús! Se actualiza diariamente para obtener los nuevos changelogs.

Para mostrarlo en un [elemento de texto](./elements#text), configura **Modo de origen** como **Recurso** y su origen de recurso como **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más sencilla de estirar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales de clic derecho para estirarlos horizontal y verticalmente. Al activarla, el elemento se estirará siempre hasta ocupar todo el ancho y/o la altura de la pantalla. El estiramiento horizontal y vertical se pueden activar de forma independiente.

### No puedo hacer clic en botones ni interactuar con deslizadores cuando están detrás o delante de un elemento de texto.

Esto ocurre porque los elementos de texto son interactivos por defecto (para poder arrastrar el control de desplazamiento o hacer clic en enlaces Markdown), lo que significa que consumen los clics del ratón y los eventos de desplazamiento. Lo mejor sería simplemente no mover botones detrás/delante de elementos de texto, pero si no hay otra opción, puedes hacer que el elemento de texto no sea interactivo haciendo **clic derecho** sobre él y configurando **Interactuable** en **Desactivado**. Ten en cuenta que esto convierte el elemento de texto en texto estático, no interactivo, por lo que ya no podrás desplazarte por él ni hacer clic en enlaces.

### ¿Cómo puedo hacer para que los botones y deslizadores dejen de seleccionarse/enfocarse al navegar en pantallas con las teclas de flecha y Tabulador?

Para que los botones y deslizadores no sean navegables, debes hacer **clic derecho** sobre ellos y configurar **Navegable** en **Desactivado**. El botón/deslizador seguirá siendo clicable, pero ya no podrás enfocarlo con la navegación mediante flechas/Tab.

Esto también es útil si quieres añadir botones/deslizadores a la pantalla del chat, de modo que puedas seguir usando la tecla Flecha arriba para desplazarte por mensajes anteriores sin seleccionar accidentalmente botones/deslizadores en la pantalla.

### Falta una opción en uno de los menús contextuales de FancyMenu que debería estar ahí.

Los menús contextuales de FancyMenu (los menús que se abren al hacer clic derecho en algún lugar o al interactuar con las barras de menús) son DESPLAZABLES. Esto significa que puedes usar la rueda del ratón mientras el cursor está sobre el menú para desplazarte hacia arriba o hacia abajo, lo que te permite ver más opciones que antes no eran visibles.

### No puedo personalizar la pantalla de título; sigue mostrando la original cuando salgo del editor.

Otro mod está reemplazando la `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en su configuración. Si no tiene esa opción, FancyMenu no puede aplicar el diseño a la pantalla sustituida.
