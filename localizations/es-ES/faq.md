---
title: Preguntas frecuentes
description: Preguntas frecuentes.
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para obtener la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que ocurriera y qué ocurrió realmente?
2.  **Tu archivo `latest.log`:** Puedes encontrarlo en `<game-directory>/logs/latest.log`. **No envíes un registro de errores** a menos que se te solicite específicamente; `latest.log` normalmente contiene el contexto necesario. Utiliza un sitio como https://gist.github.com para publicarlo.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Las capturas de pantalla o vídeos** del problema también pueden ser muy útiles.

### ¿Cómo cambio el orden de las capas de los elementos (mover algo delante o detrás de otra cosa)?

*   **Personalizado frente a personalizado:** Abre **Ventana -> Widgets del editor -> Capas** y arrastra los elementos dentro de la jerarquía. También puedes hacer clic derecho en un elemento y utilizar **Mover una capa arriba/abajo**. Consulta [Capas y grupos](./layers-and-groups).
*   **Personalizado frente a Vanilla:** Para dibujar todos tus elementos personalizados detrás de todos los elementos de Vanilla (por ejemplo, para colocar una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Dibujar elementos personalizados detrás de Vanilla"**.

### ¿Puedo excluir determinados botones de una plantilla de botones universal?

**No. Si un botón de plantilla tiene texturas personalizadas configuradas, esas texturas se comparten siempre con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón realice una acción al hacer clic en él?

Utiliza un [**script de acciones**](./action-scripts).
1.  Haz clic derecho en el botón dentro del editor.
2.  Selecciona **Editar script de acciones**.
3. Haz clic en **Añadir acción** y elige una acción, como [**Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui), [**Unirse a un servidor**](./action-scripts#join-server-joinserver) o [**Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Utiliza una [**GUI personalizada**](./custom-guis).
1.  En la barra de menús, ve a **Personalización -> GUIs personalizadas -> Gestionar GUIs personalizadas**.
2.  Haz clic en **"Nueva GUI"** y asígnale un identificador único.
3.  A continuación, puedes abrir esta nueva pantalla vacía y crear un diseño para ella, añadiendo los elementos que quieras.
4. Abre la GUI personalizada con la acción [**Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mi juego tarda mucho en cargarse después de activar la precarga.

Este comportamiento es normal. Precargar recursos grandes, como animaciones o sonidos de alta resolución, durante el inicio aumentará de forma natural el tiempo de carga del juego.

### ¡Mi animación FMA utiliza demasiada RAM!

Las [animaciones FMA](./fma) clásicas pueden consumir mucha memoria cuando contienen muchos fotogramas de alta resolución. AFMA es más adecuada para texturas animadas grandes o complejas. Mantén cortas las animaciones FMA clásicas y utiliza [Vídeo](./video) para reproducir vídeos completos.

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda encarecidamente utilizar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](./optifine-alternatives).

### Mi juego se bloquea. ¿Cómo puedo averiguar si se trata de un conflicto entre mods?

La mejor forma de comprobar si existe un conflicto entre mods es **ejecutar el juego únicamente con FancyMenu y sus dependencias** (Konkrete, Melody). Si el error deja de producirse, vuelve a añadir los demás mods en grupos pequeños hasta que el error vuelva a aparecer, para identificar el mod conflictivo.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods añaden widgets de formas que FancyMenu no puede detectar ni personalizar. Consulta [Elementos de Vanilla/mods](./vanilla-elements) y, para las pantallas basadas en listas, [Personalización de pantallas desplazables](./customizing-scrollable-screens). Si el widget sigue sin aparecer, el mod que lo añade debe exponerlo como un widget de pantalla compatible.

### ¿Puedo utilizar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se almacenan en el cliente del jugador; un servidor no puede imponerlos a un cliente que no esté configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor cuando necesites [comandos del servidor](./commands), [datos de FM](./fm-data), [acceso a NBT del lado del servidor](./nbt-data-placeholder#server-side-placeholder), reglas del juego, estructuras o listeners del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y un mejor rendimiento. V2 está obsoleta, ya no recibe soporte y carece de muchas funciones, como los placeholders avanzados y los scripts. Se recomienda encarecidamente utilizar v3 en una versión moderna de Minecraft (1.18.2 o superior). Los diseños de V2 pueden convertirse automáticamente a v3 al cargarlos, aunque puede ser necesario realizar algunas correcciones manuales.

### ¿Dónde puedo encontrar diseños y plantillas ya preparados?

La comunidad de FancyMenu comparte diseños en el canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del servidor oficial de Discord de Keksuccino's Mods ("Kekscord").

### ¿Cómo puedo hacer que la entidad del jugador se dibuje detrás de otros elementos?

Por lo general, no puedes forzar que un [elemento Entidad del jugador](./elements#player-entity) se sitúe detrás de los elementos 2D normales mediante el [widget Capas](./layers-and-groups). Su renderizador puede ignorar el orden normal de las capas de la GUI. Diseña el diseño teniendo en cuenta esta limitación o utiliza una imagen prerenderizada cuando sea necesario respetar estrictamente el orden de las capas.

### ¡Mi entidad del jugador solo tiene una pierna! ¿Qué ha ocurrido?

Se trata de un error visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos del jugador. Comprueba la configuración de Pose de la entidad del jugador para asegurarte de que las piernas no se hayan girado o movido accidentalmente.

### ¿Cómo creo un retraso entre acciones en un script?

Utiliza los bloques [**Retraso** o **Ejecutar más tarde**](./action-scripts#what-are-statements) para crear lógica de acciones retardadas. Para la lógica en segundo plano que se repite, utiliza los [Programadores](./schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización está desactivada intencionadamente para las pantallas de Create. Consulta [Pantallas en las que la personalización está desactivada intencionadamente](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Cuál es la resolución recomendada para las imágenes de fondo y las texturas de los botones?

Fondos: una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se adaptará bien a la mayoría de los usuarios.
Botones: la mayoría de los botones de Vanilla tienen unos 150-200 píxeles de ancho y 20 píxeles de alto. Utilizar este tamaño para las texturas personalizadas es una buena práctica para mantener la coherencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?

FancyMenu tiene muchos [listeners de eventos del juego integrados](./listeners), pero no existe un listener genérico para todos los sistemas de misiones de terceros. Si el mod de misiones admite recompensas mediante comandos, utiliza una para ejecutar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) u otro [comando de FancyMenu](./commands) adecuado.

### ¿Cómo hago que un botón esté inactivo o aparezca "atenuado"?

Puedes controlar el estado activo de un botón mediante los [Requisitos de carga](./conditions).
Haz clic derecho en el botón dentro del editor y selecciona **Controlar estado activo**.
Añade un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, utiliza [**Es número**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para comprobar si 0 es igual a 1.
El botón utilizará entonces su textura de "Fondo inactivo" y no se podrá hacer clic en él.

### ¿Cómo puedo eliminar la cabecera y el pie (las barras de textura de tierra) de las pantallas desplazables?

En el editor de diseños, abre **Propiedades del diseño -> Personalizaciones de cabecera/pie**. Establece las texturas como transparentes. Es posible que esta opción no esté disponible en algunas pantallas modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón aparece en gris.

Primero debes activar las personalizaciones para esa pantalla mediante **barra de menús -> Personalización -> Personalizaciones de la pantalla actual -> Activado**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. Es una pantalla vacía.

Esto podría significar que has creado un [Diseño universal](./universal-layouts) en lugar de uno **para la pantalla actual**.

También podría tratarse de una [pantalla desplazable](./customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que añade elementos de una forma que no es la de Vanilla, lo que impide que FancyMenu pueda personalizarlos.

### Hay unos cuadros grises extraños en mi elemento Texto.

Estos cuadros translúcidos son los controles de desplazamiento del [elemento Texto](./elements#text), no un error de renderizado.

Si no quieres que se vean, puedes hacer clic derecho en el elemento y desactivar completamente el desplazamiento O establecer las texturas de los controles como completamente transparentes en el mismo menú contextual, si quieres que el elemento siga pudiendo desplazarse.

### ¿Cómo puedo mostrar las últimas novedades de Minecraft en mis menús?

Existe un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte las novedades de Minecraft a Markdown compatible con FancyMenu, ¡para que puedas mostrar las últimas novedades de MC en tus menús! Se actualiza diariamente para obtener las novedades nuevas.

Para mostrarlo en un [elemento Texto](./elements#text), establece el **Modo de origen** como **Recurso** y el origen del recurso como **Web**. Utiliza `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más sencilla de ajustar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales, que se abren al hacer clic derecho, para ajustarlos horizontal y verticalmente. Al activarla, el elemento ocupará siempre todo el ancho o alto de la pantalla. El ajuste horizontal y el vertical se pueden activar de forma independiente.

### No puedo hacer clic en los botones ni interactuar con los deslizadores cuando están detrás o delante de un elemento Texto.

Esto ocurre porque los elementos Texto son interactivos de forma predeterminada (para poder utilizar el control de desplazamiento o hacer clic en los hipervínculos Markdown), lo que significa que consumen los clics del ratón y los eventos de desplazamiento. Lo mejor sería no colocar botones detrás o delante de elementos Texto, pero si no hay otra opción, puedes hacer que el elemento Texto deje de ser interactivo **haciendo clic derecho en él** y estableciendo **Interactivo** como **Desactivado**. Ten en cuenta que esto convierte el elemento Texto en un texto estático no interactivo, por lo que ya no podrás desplazarte por él ni hacer clic en los hipervínculos.

### ¿Cómo puedo evitar que los botones y deslizadores se seleccionen o reciban el foco al navegar por las pantallas con las teclas de flecha y Tab?

Para que los botones y deslizadores no se puedan recorrer, debes **hacer clic derecho** en ellos y establecer **Navegable** como **Desactivado**. El botón o deslizador seguirá pudiendo recibir clics, pero ya no podrás enfocarlo mediante la navegación con las teclas de flecha o Tab.

Esto también resulta útil si quieres añadir botones o deslizadores a la pantalla del chat, ya que podrás seguir utilizando la tecla de flecha arriba para desplazarte por los mensajes antiguos sin seleccionar accidentalmente los botones o deslizadores de la pantalla.

### A uno de los menús contextuales de FancyMenu le falta una opción que debería estar disponible.

Los menús contextuales de FancyMenu (los menús que se abren al hacer clic derecho en algún lugar o al interactuar con las barras de menús) SON DESPLAZABLES. Esto significa que puedes utilizar la rueda del ratón mientras el cursor está sobre el menú para desplazarte hacia arriba o hacia abajo y ver más opciones que antes no estaban visibles.

### No puedo personalizar la pantalla de título; cuando salgo del editor sigue apareciendo la original.

Otro mod está reemplazando la `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en sus ajustes. Si no tiene esa opción, FancyMenu no puede aplicar el diseño a la pantalla reemplazada.
