---
title: Preguntas frecuentes
description: Preguntas frecuentes.
sourceBlobSha: 405be9869106a7871195d6e03828f428cc20b4a1
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para recibir la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que sucediera y qué ocurrió realmente?
2.  **Tu archivo `latest.log`:** Puedes encontrarlo en `<game-directory>/logs/latest.log`. **No envíes un registro de error** a menos que se te solicite específicamente; `latest.log` normalmente contiene el contexto necesario. Usa un sitio como https://gist.github.com para publicarlo.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Las capturas de pantalla o videos** del problema también pueden ser muy útiles.

### ¿Cómo cambio el orden de las capas de los elementos (mover algo delante o detrás de otra cosa)?

*   **Personalizado vs. personalizado:** Abre **Ventana -> Editor de widgets -> Capas** y arrastra los elementos dentro de la jerarquía. También puedes hacer clic derecho en un elemento y usar **Mover una capa arriba/abajo**. Consulta [Capas y grupos](./layers-and-groups).
*   **Personalizado vs. vanilla:** Para renderizar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, para colocar una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Renderizar elementos personalizados detrás de los elementos vanilla"**.

### ¿Puedo excluir ciertos botones de una plantilla universal de botones?

**No. Si un botón de plantilla tiene texturas personalizadas configuradas, esas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic en él?

Usa un [**Script de acciones**](./action-scripts).
1.  Haz clic derecho en el botón dentro del editor.
2.  Selecciona **Editar script de acciones**.
3. Haz clic en **Agregar acción** y elige una acción, como [**Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui), [**Unirse a un servidor**](./action-scripts#join-server-joinserver) o [**Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Usa una [**GUI personalizada**](./custom-guis).
1.  En la barra de menú, ve a **Personalización -> GUIs personalizadas -> Administrar GUIs personalizadas**.
2.  Haz clic en **"Nueva GUI"** y asígnale un identificador único.
3.  Después puedes abrir esta nueva pantalla vacía y crear un diseño para ella, agregando los elementos que quieras.
4. Abre la GUI personalizada con la acción [**Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mi juego tarda mucho en cargar después de activar la precarga.

Este comportamiento es esperado. Precargar recursos grandes, como animaciones o sonidos de alta resolución, durante el inicio aumentará naturalmente el tiempo de carga del juego.

### ¡Mi animación FMA usa demasiada RAM!

Las [animaciones FMA](./fma) clásicas pueden consumir mucha memoria cuando contienen muchos fotogramas de alta resolución. AFMA es más adecuada para texturas animadas grandes o complejas. Mantén cortas las animaciones FMA clásicas; usa [Video](./video) para reproducir videos completos.

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda ampliamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](./optifine-alternatives).

### Mi juego se cierra inesperadamente. ¿Cómo puedo saber si se trata de un conflicto entre mods?

La mejor forma de comprobar si existe un conflicto entre mods es **ejecutar el juego únicamente con FancyMenu y sus dependencias** (Konkrete, Melody). Si el error ya no ocurre, vuelve a agregar tus otros mods en grupos pequeños hasta que el error aparezca de nuevo, para identificar el mod en conflicto.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods agregan widgets de formas que FancyMenu no puede detectar ni personalizar. Consulta [Elementos vanilla/de mods](./vanilla-elements) y, para las pantallas basadas en listas, [Personalizar pantallas desplazables](./customizing-scrollable-screens). Si el widget aún no aparece, el mod que lo agrega debe exponerlo como un widget de pantalla compatible.

### ¿Puedo usar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se almacenan en el cliente del jugador; un servidor no puede imponerlos a un cliente que no esté configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor cuando necesites [comandos del servidor](./commands), [datos de FM](./fm-data), [acceso a NBT del lado del servidor](./nbt-data-placeholder#server-side-placeholder), reglas del juego, estructuras o listeners del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y un mejor rendimiento. La v2 está obsoleta, ya no recibe soporte y carece de muchas funciones, como los placeholders avanzados y los scripts. Se recomienda ampliamente usar la v3 en una versión moderna de Minecraft (1.18.2 o superior). Los diseños de la v2 pueden convertirse automáticamente a la v3 cuando los cargues, aunque podría ser necesario corregir algunos detalles manualmente.

### ¿Dónde puedo encontrar diseños y plantillas prediseñados?

La comunidad de FancyMenu comparte diseños en el canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del servidor oficial de Discord de Keksuccino's Mods ("Kekscord").

### ¿Cómo puedo hacer que la entidad del jugador se renderice detrás de otros elementos?

Por lo general, no puedes forzar que un [elemento Entidad del jugador](./elements#player-entity) aparezca detrás de los elementos 2D normales mediante el [widget Capas](./layers-and-groups). Su renderizador puede ignorar el orden normal de las capas de la GUI. Diseña el diseño teniendo en cuenta esta limitación o usa una imagen prerenderizada cuando sea necesario respetar estrictamente el orden de las capas.

### ¡Mi entidad del jugador solo tiene una pierna! ¿Qué ocurrió?

Es un error visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos del jugador. Revisa la configuración de Pose de la entidad del jugador para comprobar si las piernas se rotaron o movieron accidentalmente.

### ¿Cómo creo un retraso entre acciones en un script?

Usa los [bloques **Retrasar** o **Ejecutar después**](./action-scripts#what-are-statements) para la lógica de acciones retrasadas. Para la lógica repetitiva en segundo plano, usa los [planificadores](./schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización está desactivada intencionalmente para las pantallas de Create. Consulta [Pantallas donde la personalización está desactivada intencionalmente](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Cuál es la resolución recomendada para las imágenes de fondo y las texturas de los botones?

Fondos: Una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se escalará bien para la mayoría de los usuarios.
Botones: La mayoría de los botones vanilla miden aproximadamente entre 150 y 200 píxeles de ancho y 20 píxeles de alto. Igualar este tamaño para las texturas personalizadas es una buena práctica para mantener la consistencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?
FancyMenu tiene muchos [listeners de eventos del juego integrados](./listeners), pero no existe un listener genérico para todos los sistemas de misiones de terceros. Si el mod de misiones admite recompensas mediante comandos, usa una para ejecutar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) u otro [comando de FancyMenu](./commands) adecuado.

### ¿Cómo hago que un botón esté inactivo o "atenuado"?

Puedes controlar el estado activo de un botón mediante los [Requisitos de carga](./conditions).
Haz clic derecho en el botón dentro del editor y selecciona **Controlar estado activo**.
Agrega un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Es número**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para comprobar si 0 es igual a 1.
El botón usará ahora su textura de "Fondo inactivo" y no se podrá seleccionar.

### ¿Cómo puedo quitar el encabezado y el pie de página (las barras con textura de tierra) de las pantallas desplazables?

En el editor de diseños, abre **Propiedades del diseño -> Personalizaciones del encabezado/pie de página**. Establece las texturas como transparentes. Es posible que esta opción no esté disponible en algunas pantallas modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón aparece atenuado.

Primero debes activar las personalizaciones para esa pantalla mediante **barra de menú -> Personalización -> Personalizaciones de la pantalla actual -> Activado**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. La pantalla aparece vacía.

Esto podría significar que creaste un [Diseño universal](./universal-layouts) en lugar de uno **para la pantalla actual**.

También podría tratarse de una [pantalla desplazable](./customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que agrega elementos de una forma no vanilla, lo que impide que FancyMenu pueda personalizarlos.

### Hay unos cuadros grises extraños en mi elemento de texto.

Estos cuadros translúcidos son los controles de desplazamiento del [elemento de texto](./elements#text), no un error de renderizado.

Si no quieres que estos cuadros sean visibles, puedes hacer clic derecho en el elemento y desactivar completamente el desplazamiento O establecer las texturas de los controles como completamente transparentes desde el mismo menú del clic derecho, si quieres que el elemento siga permitiendo desplazamiento.

### ¿Cómo puedo mostrar el registro de cambios más reciente de Minecraft en mis menús?

Existe un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte los registros de cambios de Minecraft a Markdown compatible con FancyMenu, ¡para que puedas mostrar el registro de cambios más reciente de MC en tus menús! Se actualiza diariamente para obtener los nuevos registros de cambios.

Para mostrarlo en un [elemento de texto](./elements#text), establece el **Modo de fuente** como **Recurso** y la fuente del recurso como **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más sencilla de ajustar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales del clic derecho para ajustarlos horizontal y verticalmente. Al activarla, el elemento ocupará siempre todo el ancho o alto de la pantalla. El ajuste horizontal y vertical se puede activar de forma independiente.

### No puedo hacer clic en los botones ni interactuar con los controles deslizantes cuando están detrás o delante de un elemento de texto.

Esto ocurre porque los elementos de texto son interactivos de forma predeterminada (para poder tomar el control de desplazamiento o hacer clic en los hipervínculos de Markdown), lo que significa que consumen los clics del mouse y los eventos de desplazamiento. Lo mejor sería no colocar botones detrás o delante de los elementos de texto, pero si no hay otra opción, puedes hacer que el elemento de texto deje de ser interactivo **haciendo clic derecho en él** y estableciendo **Interactivo** como **Desactivado**. Ten en cuenta que esto convierte el elemento de texto en un texto estático no interactivo, por lo que ya no podrás desplazarlo ni hacer clic en los hipervínculos.

### ¿Cómo puedo evitar que los botones y controles deslizantes se seleccionen o reciban el enfoque al navegar por las pantallas con las teclas de flecha y Tab?

Para que los botones y controles deslizantes no sean navegables, debes **hacer clic derecho** en ellos y establecer **Navegable** como **Desactivado**. El botón o control deslizante seguirá siendo seleccionable con el mouse, pero ya no podrás enfocarlo mediante la navegación con las teclas de flecha o Tab.

Esto también es útil si quieres agregar botones o controles deslizantes a la pantalla de chat, para que puedas seguir usando la tecla Flecha arriba para desplazarte por los mensajes anteriores sin seleccionar accidentalmente los botones o controles deslizantes de la pantalla.

### Falta una opción que debería estar en uno de los menús contextuales de FancyMenu.

Los menús contextuales de FancyMenu (los menús que se abren al hacer clic derecho en algún lugar o al interactuar con las barras de menú) **se pueden desplazar**. Esto significa que puedes usar la rueda del mouse mientras el cursor está sobre el menú para desplazarte hacia arriba o abajo y ver más opciones que antes no estaban visibles.

### No puedo personalizar la pantalla de título; cuando salgo del editor, sigue apareciendo la original.

Otro mod está reemplazando la `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en su configuración. Si no tiene esa opción, FancyMenu no puede aplicar el diseño a la pantalla reemplazada.

### Cuando intento personalizar la pantalla del inventario, no puedo personalizar el contenedor del inventario.

Es lo esperado. FancyMenu no admite editar el contenedor real de ningún tipo de pantalla de inventario (inventario del jugador, cofre, mesa de trabajo, etc.), ya que agregar compatibilidad con estos contenedores sería muy difícil.

Aun así, es posible agregar nuevos elementos a estas pantallas; simplemente no puedes editar los contenedores.

Por cierto, SpiffyHUD tampoco ayudará en este caso, ya que sirve para editar la HUD (por ejemplo, la barra rápida de objetos), pero no puede editar pantallas (como las pantallas de inventario).
