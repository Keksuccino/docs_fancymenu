---
title: Preguntas frecuentes
description: Preguntas frecuentes.
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para recibir la mejor ayuda, proporciona todo el contexto posible:
1.  **Una descripción clara del problema:** ¿Qué esperabas que sucediera y qué ocurrió realmente?
2.  **Tu archivo `latest.log`:** Encuéntralo en `<game-directory>/logs/latest.log`. **No envíes un registro de crash** a menos que se solicite específicamente; `latest.log` normalmente contiene el contexto necesario. Usa un sitio como https://gist.github.com para publicarlo.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  Las **capturas de pantalla o videos** del problema también pueden ser muy útiles.

### ¿Cómo cambio el orden de las capas de los elementos (mover algo delante o detrás de otra cosa)?

*   **Personalizado vs. personalizado:** Abre **Window -> Editor Widgets -> Layers** y arrastra los elementos dentro de la jerarquía. También puedes hacer clic derecho en un elemento y usar **Move One Layer Up/Down**. Consulta [Capas y grupos](./layers-and-groups).
*   **Personalizado vs. vanilla:** Para mostrar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, para colocar una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Render Custom Elements Behind Vanilla"**.

### ¿Puedo excluir ciertos botones de una plantilla de botones universal?

**No. Si un botón de plantilla tiene texturas personalizadas configuradas, estas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic en él?

Usa un [**script de acción**](./action-scripts).
1.  Haz clic derecho en el botón dentro del editor.
2.  Selecciona **Edit Action Script**.
3. Haz clic en **Add Action** y elige una acción, como [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) o [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Usa una [**GUI personalizada**](./custom-guis).
1.  En la barra de menú, ve a **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Haz clic en **"New GUI"** y asígnale un identificador único.
3.  Después puedes abrir esta nueva pantalla vacía y crear un diseño para ella, agregando los elementos que quieras.
4. Abre la GUI personalizada con la acción [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mi juego tarda mucho en cargar después de activar la precarga.

Este comportamiento es esperado. Precargar recursos grandes, como animaciones o sonidos de alta resolución, durante el inicio aumentará naturalmente el tiempo de carga del juego.

### ¡Mi animación FMA está usando demasiada RAM!

Las [animaciones FMA](./fma) clásicas pueden consumir mucha memoria cuando contienen muchos fotogramas de alta resolución. AFMA es más adecuado para texturas animadas grandes o complejas. Mantén cortas las animaciones FMA clásicas; usa [Video](./video) para reproducir videos completos.

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda ampliamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](./optifine-alternatives).

### Mi juego se cierra inesperadamente. ¿Cómo sé si se trata de un conflicto entre mods?

La mejor forma de comprobar si existe un conflicto entre mods es **ejecutar el juego únicamente con FancyMenu y sus dependencias** (Konkrete, Melody). Si el crash ya no ocurre, vuelve a agregar los demás mods en grupos pequeños hasta que el crash vuelva a ocurrir, para identificar el mod en conflicto.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods agregan widgets de formas que FancyMenu no puede detectar ni personalizar. Consulta [Elementos vanilla/de mods](./vanilla-elements) y, para las pantallas basadas en listas, [Personalización de pantallas desplazables](./customizing-scrollable-screens). Si el widget sigue sin aparecer, el mod que lo agrega debe exponerlo como un widget de pantalla compatible.

### ¿Puedo usar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se almacenan en el cliente del jugador; un servidor no puede imponerlos a un cliente que no esté configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor cuando necesites [comandos del servidor](./commands), [datos de FM](./fm-data), [acceso del servidor a NBT](./nbt-data-placeholder#server-side-placeholder), gamerules, estructuras o listeners del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de Minecraft) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y un mejor rendimiento. La v2 está obsoleta, ya no recibe soporte y carece de muchas funciones, como los placeholders avanzados y los scripts. Se recomienda ampliamente usar la v3 en una versión moderna de Minecraft (1.18.2+). Los diseños de la v2 se pueden convertir automáticamente a la v3 al cargarlos, aunque puede ser necesario corregir algunos detalles manualmente.

### ¿Dónde puedo encontrar diseños y plantillas prediseñados?

La comunidad de FancyMenu comparte diseños en el canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del servidor oficial de Discord de Keksuccino's Mods ("Kekscord").

### ¿Cómo puedo hacer que la entidad del jugador se renderice detrás de otros elementos?

Por lo general, no puedes forzar que un [elemento Entidad del jugador](./elements#player-entity) aparezca detrás de los elementos 2D normales mediante el [widget Capas](./layers-and-groups). Su renderizador puede ignorar el orden normal de las capas de la GUI. Diseña el layout teniendo en cuenta esta limitación o usa una imagen prerenderizada cuando necesites un orden estricto de las capas.

### ¡Mi entidad del jugador solo tiene una pierna! ¿Qué pasó?

Se trata de un error visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos del jugador. Revisa la configuración de Pose de la entidad del jugador para comprobar si las piernas se rotaron o movieron accidentalmente.

### ¿Cómo creo un retraso entre acciones en un script?

Usa los [bloques **Delay** o **Execute Later**](./action-scripts#what-are-statements) para ejecutar acciones con retraso. Para lógica en segundo plano que se repite, usa [Schedulers](./schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización está desactivada intencionalmente para las pantallas de Create. Consulta [Pantallas en las que la personalización está desactivada intencionalmente](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Cuál es la resolución recomendada para las imágenes de fondo y las texturas de los botones?

Fondos: Una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se ajustará bien para la mayoría de los usuarios.
Botones: La mayoría de los botones vanilla tienen aproximadamente 150-200 píxeles de ancho y 20 píxeles de alto. Usar este tamaño para las texturas personalizadas es una buena práctica para mantener la consistencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?
FancyMenu tiene muchos [listeners de eventos del juego integrados](./listeners), pero no existe un listener genérico para todos los sistemas de misiones de terceros. Si el mod de misiones admite recompensas mediante comandos, usa una para ejecutar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) u otro [comando de FancyMenu](./commands) adecuado.

### ¿Cómo hago que un botón esté inactivo o "atenuado"?

Puedes controlar el estado activo de un botón mediante los [requisitos de carga](./conditions).
Haz clic derecho en el botón dentro del editor y selecciona **Control Active State**.
Agrega un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para comprobar si 0 es igual a 1.
El botón usará entonces su textura de "Inactive Background" y no se podrá hacer clic en él.

### ¿Cómo quito el encabezado y el pie de página (las barras de textura de tierra) de las pantallas desplazables?

En el editor de diseños, abre **Layout Properties -> Header/Footer Customizations**. Establece las texturas como transparentes. Es posible que esta opción no esté disponible en algunas pantallas modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón aparece en gris.

Primero debes activar las personalizaciones para esa pantalla mediante **menu bar -> Customization -> Current Screen Customizations -> Enabled**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. Solo aparece una pantalla vacía.

Esto podría significar que creaste un [diseño universal](./universal-layouts) en lugar de uno **para la pantalla actual**.

También podría tratarse de una [pantalla desplazable](./customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que agrega elementos de una forma que no es vanilla, lo que impide que FancyMenu pueda personalizarlos.

### Hay cuadros grises extraños en mi elemento de texto.

Estos cuadros translúcidos son los controles de desplazamiento del [elemento de texto](./elements#text), no un error de renderizado.

Si no quieres que estos cuadros sean visibles, puedes hacer clic derecho en el elemento y desactivar completamente el desplazamiento O establecer las texturas de los controles como completamente transparentes en el mismo menú del clic derecho, si quieres que el elemento siga siendo desplazable.

### ¿Cómo puedo mostrar el registro de cambios más reciente de Minecraft en mis menús?

Existe un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte los registros de cambios de Minecraft a Markdown compatible con FancyMenu, ¡para que puedas mostrar el registro de cambios más reciente de MC en tus menús! Se actualiza diariamente para obtener los nuevos registros de cambios.

Para mostrarlo en un [elemento de texto](./elements#text), establece **Source Mode** en **Resource** y el origen del recurso en **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más sencilla de estirar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales del clic derecho para estirarlos horizontal y verticalmente. Al activarla, se estirarán siempre hasta ocupar todo el ancho o alto de la pantalla. El estiramiento horizontal y vertical se puede activar de forma independiente.

### No puedo hacer clic en los botones ni interactuar con los controles deslizantes cuando están detrás o delante de un elemento de texto.

Esto ocurre porque los elementos de texto son interactivos de forma predeterminada (para poder tomar el control de desplazamiento o hacer clic en los hipervínculos de Markdown), lo que significa que consumen los clics del mouse y los eventos de desplazamiento. Lo mejor sería no colocar botones detrás o delante de los elementos de texto, pero si no hay otra opción, puedes hacer que el elemento de texto no sea interactivo **haciendo clic derecho en él** y estableciendo **Interactable** en **Disabled**. Ten en cuenta que esto convierte el elemento de texto en un texto estático y no interactivo, por lo que ya no podrás desplazarlo ni hacer clic en los hipervínculos.

### ¿Cómo hago para que los botones y controles deslizantes ya no se seleccionen ni reciban el foco al navegar por las pantallas con las teclas de flecha y Tab?

Para que los botones y controles deslizantes no se puedan navegar, debes **hacer clic derecho** en ellos y establecer **Navigable** en **Disabled**. El botón o control deslizante seguirá siendo seleccionable con el mouse, pero ya no podrás enfocarlo mediante la navegación con las teclas de flecha o Tab.

Esto también es útil si quieres agregar botones o controles deslizantes a la pantalla de chat, ya que podrás seguir usando la tecla Flecha arriba para desplazarte por los mensajes anteriores sin seleccionar accidentalmente botones o controles deslizantes de la pantalla.

### A uno de los menús contextuales de FancyMenu le falta una opción que debería estar ahí.

Los menús contextuales de FancyMenu (los menús que se abren al hacer clic derecho en algún lugar o al interactuar con las barras de menú) son DESPLAZABLES. Esto significa que puedes usar la rueda del mouse mientras el cursor está sobre el menú para desplazarte hacia arriba o abajo y ver más opciones que antes no estaban visibles.

### No puedo personalizar la pantalla de título; cuando salgo del editor, sigue apareciendo la original.

Otro mod está reemplazando la `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en su configuración. Si no tiene esa opción, FancyMenu no puede aplicar el diseño a la pantalla reemplazada.
