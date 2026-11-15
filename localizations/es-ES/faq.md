---
title: Preguntas frecuentes
description: Preguntas frecuentes.
sourceBlobSha: 405be9869106a7871195d6e03828f428cc20b4a1
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para obtener la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que ocurriera y qué ocurrió realmente?
2.  **Tu archivo `latest.log`:** Lo encontrarás en `<game-directory>/logs/latest.log`. **No envíes un registro de error** a menos que se te solicite específicamente; `latest.log` normalmente contiene el contexto necesario. Usa un sitio como https://gist.github.com para publicarlo.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Las capturas de pantalla o vídeos** del problema también pueden resultar muy útiles.

### ¿Cómo cambio el orden de las capas de los elementos (mover algo delante o detrás de otra cosa)?

*   **Personalizado frente a personalizado:** Abre **Ventana -> Widgets del editor -> Capas** y arrastra los elementos dentro de la jerarquía. También puedes hacer clic derecho en un elemento y usar **Mover una capa arriba/abajo**. Consulta [Capas y grupos](./layers-and-groups).
*   **Personalizado frente a vanilla:** Para mostrar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, para colocar una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **«Mostrar elementos personalizados detrás de los elementos vanilla»**.

### ¿Puedo excluir ciertos botones de una plantilla de botones universal?

**No. Si un botón de plantilla tiene texturas personalizadas configuradas, estas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic en él?

Usa un [**script de acción**](./action-scripts).
1.  Haz clic derecho en el botón dentro del editor.
2.  Selecciona **Editar script de acción**.
3.  Haz clic en **Añadir acción** y elige una acción, como [**Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui), [**Unirse a un servidor**](./action-scripts#join-server-joinserver) o [**Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Usa una [**GUI personalizada**](./custom-guis).
1.  En la barra de menús, ve a **Personalización -> GUIs personalizadas -> Gestionar GUIs personalizadas**.
2.  Haz clic en **«Nueva GUI»** y asígnale un identificador único.
3.  Después podrás abrir esta nueva pantalla vacía y crear un diseño para ella, añadiendo los elementos que quieras.
4. Abre la GUI personalizada con la [acción **Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mi juego tarda mucho en cargar después de activar la precarga.

Este comportamiento es normal. Precargar recursos grandes, como animaciones o sonidos de alta resolución, durante el inicio inicial aumentará de forma natural el tiempo de carga del juego.

### ¡Mi animación FMA usa demasiada RAM!

Las [animaciones FMA](./fma) clásicas pueden consumir mucha memoria cuando contienen muchos fotogramas de alta resolución. AFMA es más adecuada para texturas animadas grandes o complejas. Mantén cortas las animaciones FMA clásicas y usa [Vídeo](./video) para reproducir vídeos completos.

### ¿Funciona FancyMenu con OptiFine?

No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda encarecidamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](./optifine-alternatives).

### Mi juego se bloquea. ¿Cómo puedo averiguar si se trata de un conflicto entre mods?

La mejor forma de comprobar si existe un conflicto entre mods es **ejecutar el juego únicamente con FancyMenu y sus dependencias** (Konkrete, Melody). Si el error deja de producirse, vuelve a añadir el resto de tus mods en grupos pequeños hasta que el error vuelva a aparecer, para identificar el mod conflictivo.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods añaden widgets de formas que FancyMenu no puede detectar ni personalizar. Consulta [Elementos vanilla/de mods](./vanilla-elements) y, para las pantallas basadas en listas, [Personalizar pantallas desplazables](./customizing-scrollable-screens). Si el widget sigue sin aparecer, el mod que lo añade debe exponerlo como un widget de pantalla compatible.

### ¿Puedo usar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se almacenan en el cliente del jugador; un servidor no puede imponerlos a un cliente que no esté configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor cuando necesites [comandos del servidor](./commands), [datos de FM](./fm-data), [acceso a NBT del lado del servidor](./nbt-data-placeholder#server-side-placeholder), reglas del juego, estructuras o listeners del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y un mejor rendimiento. V2 está obsoleta, ya no recibe soporte y carece de muchas funciones, como los placeholders avanzados y los scripts. Se recomienda encarecidamente usar v3 en una versión moderna de Minecraft (1.18.2 o posterior). Los diseños de V2 se pueden convertir automáticamente a v3 al cargarlos, aunque puede ser necesario corregir algunos aspectos manualmente.

### ¿Dónde puedo encontrar diseños y plantillas ya preparados?

La comunidad de FancyMenu comparte diseños en el canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del servidor oficial de Discord de Keksuccino's Mods («Kekscord»).

### ¿Cómo puedo hacer que la entidad del jugador se renderice detrás de otros elementos?

Por lo general, no puedes forzar que un [elemento Entidad del jugador](./elements#player-entity) aparezca detrás de elementos 2D normales mediante el [widget Capas](./layers-and-groups). Su renderizador puede ignorar el orden normal de las capas de la GUI. Diseña el diseño teniendo en cuenta esta limitación o usa una imagen prerenderizada cuando sea necesario respetar estrictamente el orden de las capas.

### ¡A mi entidad del jugador solo le aparece una pierna! ¿Qué ha ocurrido?

Se trata de un fallo visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos del jugador. Comprueba la configuración de Pose de la entidad del jugador para ver si las piernas se han girado o movido accidentalmente.

### ¿Cómo creo un retraso entre acciones de un script?

Usa los [bloques **Retraso** o **Ejecutar más tarde**](./action-scripts#what-are-statements) para la lógica de acciones retrasadas. Para la lógica de fondo que se repite, usa los [planificadores](./schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización está desactivada intencionadamente para las pantallas de Create. Consulta [Pantallas en las que la personalización está desactivada intencionadamente](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Cuál es la resolución recomendada para las imágenes de fondo y las texturas de los botones?

Fondos: Una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se adaptará bien a la mayoría de los usuarios.
Botones: La mayoría de los botones vanilla miden aproximadamente entre 150 y 200 píxeles de ancho y 20 píxeles de alto. Igualar este tamaño en las texturas personalizadas es una buena práctica para mantener la coherencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?
FancyMenu tiene muchos [listeners de eventos del juego integrados](./listeners), pero no existe un listener genérico para todos los sistemas de misiones de terceros. Si el mod de misiones admite recompensas mediante comandos, usa una para ejecutar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) u otro [comando de FancyMenu](./commands) adecuado.

### ¿Cómo hago que un botón esté inactivo o «atenuado»?

Puedes controlar el estado activo de un botón mediante los [requisitos de carga](./conditions).
Haz clic derecho en el botón dentro del editor y selecciona **Controlar estado activo**.
Añade un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Es número**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para comprobar si 0 es igual a 1.
El botón usará ahora su textura de «Fondo inactivo» y no se podrá hacer clic en él.

### ¿Cómo puedo eliminar el encabezado y el pie de página (las barras con textura de tierra) de las pantallas desplazables?

En el editor de diseños, abre **Propiedades del diseño -> Personalización del encabezado/pie de página**. Establece las texturas como transparentes. Es posible que esta opción no esté disponible en algunas pantallas modificadas.

### No puedo crear un diseño «para la pantalla actual». El botón aparece desactivado.

Primero debes activar las personalizaciones para esa pantalla mediante **barra de menús -> Personalización -> Personalizaciones de la pantalla actual -> Activado**.

### No puedo personalizar ningún elemento de una pantalla al abrirla en el editor. Es una pantalla vacía.

Podría significar que has creado un [diseño universal](./universal-layouts) en lugar de uno **para la pantalla actual**.

También podría tratarse de una [pantalla desplazable](./customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que añade elementos de una forma no vanilla, lo que impide que FancyMenu pueda personalizar esos elementos.

### Hay unos cuadros grises extraños en mi elemento de texto.

Estos cuadros translúcidos son los controles de desplazamiento del [elemento de texto](./elements#text), no un error de renderizado.

Si no quieres que estos cuadros sean visibles, puedes hacer clic derecho en el elemento y desactivar por completo el desplazamiento. También puedes establecer las texturas de los controles en unas completamente transparentes desde el mismo menú contextual, si quieres que el elemento siga pudiéndose desplazar.

### ¿Cómo puedo mostrar en mis menús las últimas notas de cambios de Minecraft?

Existe un magnífico [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte las notas de cambios de Minecraft a Markdown compatible con FancyMenu, ¡para que puedas mostrar las últimas notas de cambios de MC en tus menús! Se actualiza a diario para obtener las nuevas notas de cambios.

Para mostrarlo en un [elemento de texto](./elements#text), establece **Modo de origen** en **Recurso** y el origen del recurso en **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más sencilla de ajustar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales, que se abren al hacer clic derecho, para estirarlos horizontal y verticalmente. Al activarla, se estirarán siempre hasta ocupar todo el ancho o el alto de la pantalla. El estiramiento horizontal y el vertical se pueden activar de forma independiente.

### No puedo hacer clic en los botones ni interactuar con los deslizadores cuando están detrás o delante de un elemento de texto.

Esto ocurre porque los elementos de texto son interactivos de forma predeterminada (para poder agarrar el control de desplazamiento o hacer clic en los hipervínculos Markdown), lo que significa que consumen los clics del ratón y los eventos de desplazamiento. Lo mejor sería no mover los botones detrás o delante de los elementos de texto, pero si no hay otra opción, puedes hacer que el elemento de texto deje de ser interactivo **haciendo clic derecho en él** y estableciendo **Interactivo** en **Desactivado**. Ten en cuenta que esto convierte el elemento de texto en un texto estático no interactivo, por lo que ya no podrás desplazarte por él ni hacer clic en los hipervínculos.

### ¿Cómo puedo hacer que los botones y deslizadores dejen de seleccionarse o recibir el foco al navegar por las pantallas con las teclas de flecha y Tab?

Para que los botones y deslizadores no se puedan recorrer mediante la navegación, debes **hacer clic derecho** en ellos y establecer **Navegable** en **Desactivado**. El botón o deslizador seguirá siendo interactivo mediante clic, pero ya no podrás enfocarlo con la navegación mediante las teclas de flecha o Tab.

Esto también resulta útil si quieres añadir botones o deslizadores a la pantalla de chat, ya que podrás seguir usando la tecla de flecha arriba para desplazarte por los mensajes antiguos sin seleccionar accidentalmente botones o deslizadores de la pantalla.

### A uno de los menús contextuales de FancyMenu le falta una opción que debería estar ahí.

Los menús contextuales de FancyMenu (los menús que se abren al hacer clic derecho en algún sitio o al interactuar con las barras de menús) son DESPLAZABLES. Esto significa que puedes usar la rueda del ratón mientras el cursor se encuentra sobre el menú para desplazarte hacia arriba o hacia abajo y ver más opciones que antes no estaban visibles.

### No puedo personalizar la pantalla de título; sigue mostrando la original cuando salgo del editor.

Otro mod está reemplazando la `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en sus ajustes. Si no tiene una opción de ese tipo, FancyMenu no puede aplicar el diseño a la pantalla reemplazada.

### Cuando intento personalizar la pantalla del inventario, no puedo personalizar el contenedor del inventario.

Es lo esperado. FancyMenu no admite editar el contenedor real de ningún tipo de pantalla de inventario (inventario del jugador, cofre, mesa de trabajo, etc.), porque añadir compatibilidad para ello sería muy difícil.

Aun así, puedes añadir elementos nuevos a estas pantallas; simplemente no puedes editar sus contenedores.

Por cierto, SpiffyHUD tampoco te ayudará en este caso, ya que sirve para editar el HUD (por ejemplo, la barra rápida de objetos), pero no puede editar pantallas (como las pantallas de inventario).
