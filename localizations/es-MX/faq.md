---
title: Preguntas frecuentes
description: Preguntas frecuentes.
sourceBlobSha: 4ae872e8e4a54fc6a89de7c87c8a137a89292455
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debería proporcionar?

Para recibir la mejor ayuda, proporciona todo el contexto posible:
1.  **Una descripción clara del problema:** ¿Qué esperabas que pasara y qué pasó en realidad?
2.  **Tu archivo `latest.log`:** Lo encontrarás en `<game-directory>/logs/latest.log`. **No envíes un registro de errores** a menos que te lo pidan específicamente; `latest.log` suele contener el contexto necesario. Al compartirlo, usa un sitio como https://gist.github.com.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Las capturas de pantalla o los videos** del problema también pueden ser de mucha ayuda.

> [!TIP]
> ¿Le pedirás ayuda a Alice o a otra IA? Adjunta una [Exportación para IA](/export-for-ai) de lo que no funciona. Así la IA podrá ver exactamente cómo está configurado y ya tendrá las versiones de Minecraft, del cargador de mods y de FancyMenu.

### ¿Cómo cambio el orden de las capas de los elementos (para poner algo delante o detrás de otra cosa)?

- **Tus propios elementos:** arrastra sus capas en el widget Capas del editor de diseños o haz clic derecho en un elemento y selecciona **Subir una capa** o **Bajar una capa**. Consulta [Capas y grupos](/layout-editor#layers-and-groups).
- **Tus elementos y los elementos vanilla:** el orden de los elementos vanilla no se puede cambiar. Para poner todos tus elementos detrás de ellos —por ejemplo, una imagen de fondo detrás de los botones predeterminados—, haz clic derecho en el fondo del editor y establece **Elementos personalizados detrás de los de vanilla** en **Activado**.

### ¿Puedo excluir ciertos botones de una plantilla de botones universal?

**No. Si un botón de la plantilla tiene texturas personalizadas, esas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón realice una acción al hacer clic en él?

Usa un [**Script de acciones**](/action-scripts).
1.  Haz clic derecho en el botón desde el editor.
2.  Selecciona **Editar script de acciones**.
3. Haz clic en **Agregar acción** y elige una, como [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui), [**Unirse a un servidor**](/action-scripts#join-server) o [**Establecer valor de variable**](/action-scripts#set-variable-value-fm-variable).

### ¿Puedo crear desde cero una pantalla de menú completamente nueva?

Sí, con una [GUI personalizada](/custom-guis):

1. Abre **barra de menú -> Personalización -> GUIs personalizadas -> Administrar GUIs personalizadas** y haz clic en **Nueva GUI**.
2. Asígnale un identificador, como `modpack_info`, y haz clic en **Listo**.
3. Ábrela con **Abrir GUI** y crea un diseño para ella, como lo harías con cualquier otro menú.
4. Ábrela desde un botón mediante la acción [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui) y su identificador.

### El juego tarda mucho en cargar después de activar la precarga.

Es normal. Precargar recursos grandes, como animaciones de alta resolución o sonidos, durante el inicio hará que el juego tarde más en cargar.

### ¡Mi animación usa mucha RAM o hace que el juego se trabe!

Los fotogramas grandes y las velocidades de fotogramas altas consumen memoria y afectan el rendimiento. Procura que los fotogramas tengan un tamaño parecido al que se mostrarán en pantalla y usa menos fotogramas por segundo. Consulta [Animaciones](/animations#performance). Para clips largos con sonido, usa un [video](/video).

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que causa problemas con muchos mods, incluido FancyMenu. Se recomienda ampliamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](/optifine-alternatives).

### El juego se cierra inesperadamente. ¿Cómo puedo averiguar si se trata de un conflicto entre mods?

La mejor forma de comprobar si hay un conflicto entre mods es **ejecutar el juego solo con FancyMenu y sus dependencias** (Konkrete, Melody). Si el problema deja de ocurrir, vuelve a agregar los demás mods en grupos pequeños hasta que vuelva a pasar y así podrás identificar cuál causa el conflicto.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods agregan widgets de formas que FancyMenu no puede detectar ni personalizar. Consulta [Elementos de vanilla y de mods](/vanilla-elements) y, para las pantallas basadas en listas, [Personalizar pantallas con desplazamiento](/customizing-scrollable-screens). Si el widget sigue sin aparecer, el mod que lo agrega debe exponerlo como un widget de pantalla compatible.

### ¿Puedo usar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se guardan en el cliente del jugador; un servidor no puede aplicarlos a un cliente que no esté configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor si necesitas [comandos de servidor](/commands), [datos de FM](/fm-data), [acceso del lado del servidor a NBT](/nbt-data-placeholder#server-side-placeholder), reglas de juego, estructuras o detectores de eventos del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa que incluye muchas funciones nuevas, una arquitectura más estable y un mejor rendimiento. V2 está obsoleto, ya no tiene soporte y carece de muchas funciones, como los marcadores de posición avanzados y los scripts. Se recomienda ampliamente usar v3 en una versión moderna de Minecraft (1.18.2 o posterior). Los diseños de v2 se pueden convertir automáticamente a v3 al cargarlos, pero quizá sea necesario corregir algunas cosas manualmente.

### ¿Dónde puedo encontrar diseños y plantillas ya hechos?

La comunidad de FancyMenu comparte configuraciones completas en el canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del servidor oficial de Discord («Kekscord»). Instálalas como perfiles independientes; consulta [Plantillas de diseño](/profiles#layout-templates).

### ¿Cómo puedo hacer que la entidad del jugador se muestre detrás de otros elementos?

Por lo general, no puedes forzar que un [elemento de entidad del jugador](/elements#player-entity) quede detrás de los elementos 2D normales mediante el [widget Capas](/layout-editor#layers-and-groups). Su renderizador puede ignorar el orden habitual de las capas de la interfaz. Diseña el diseño teniendo en cuenta esta limitación o usa una imagen pre-renderizada cuando necesites un orden estricto de las capas.

### ¡A mi entidad del jugador le aparece una sola pierna! ¿Qué pasó?

Es un error visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos del jugador. Revisa los ajustes de Pose de la entidad del jugador para ver si las piernas se rotaron o movieron por accidente.

### ¿Cómo puedo agregar una pausa entre las acciones de un script?

Haz clic derecho en el área del script del editor de scripts de acciones, selecciona **Agregar bloque EXECUTE LATER** y coloca dentro las acciones que deban esperar. Estas se ejecutan una vez transcurrido el tiempo indicado en milisegundos, mientras que el resto del script continúa de inmediato. Consulta [Ejecutar más tarde](/action-scripts#execute-later).

Para acciones que deban repetirse, usa [programadores](/schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización de las pantallas de Create está desactivada intencionalmente. Consulta [Pantallas cuya personalización está desactivada intencionalmente](/incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Qué resolución se recomienda para las imágenes de fondo y las texturas de botones?

Fondos: Una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se adaptará bien a la mayoría de los usuarios.
Botones: La mayoría de los botones vanilla miden aproximadamente entre 150 y 200 píxeles de ancho y 20 píxeles de alto. Usar un tamaño similar para las texturas personalizadas es una buena práctica para mantener la coherencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego, como una misión?
FancyMenu incluye muchos [detectores de eventos del juego](/listeners), pero no hay un detector genérico que funcione con todos los sistemas de misiones de terceros. Si el mod de misiones permite recompensas con comandos, usa una para ejecutar [`/openguiscreen`](/commands#openguiscreen), [`/fmvariable`](/commands#fmvariable) u otro [comando de FancyMenu](/commands) adecuado.

### ¿Cómo desactivo un botón o hago que aparezca «atenuado»?

Puedes controlar el estado activo de un botón con [requisitos](/conditions).
Haz clic derecho en el botón desde el editor y selecciona **Controlar estado activo**.
Agrega un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Es un número**](/conditions#is-number) para comprobar si 0 es igual a 1.
El botón usará entonces su textura de «Fondo inactivo» y no se podrá hacer clic en él.

### ¿Cómo puedo quitar el encabezado y el pie de página (las barras con textura de tierra) de las pantallas con desplazamiento?

En el editor de diseños, abre **Propiedades del diseño -> Personalización de encabezado y pie de página**. Establece las texturas como transparentes. Es posible que esta opción no esté disponible en algunas pantallas modificadas.

### No puedo crear un diseño «para la pantalla actual». El botón aparece en gris.

Primero activa las personalizaciones para esa pantalla: haz clic en **barra de menú -> Personalización -> Personalización de la pantalla actual** para que aparezca **Activado**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. Aparece vacía.

Puede que hayas creado un [diseño universal](/universal-layouts) en vez de uno **para la pantalla actual**.

También podría ser una [pantalla con desplazamiento](/customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

Otra posibilidad es que se trate de una pantalla de un mod que agrega elementos de una forma distinta a la de vanilla, por lo que FancyMenu no puede personalizarlos.

### Aparecen unos cuadros grises extraños en mi elemento de texto.

Son las barras de desplazamiento del [elemento de texto](/elements#text). Aparecen cuando el texto no cabe en el elemento, para que los jugadores puedan desplazarse por él.

- Agranda el elemento o acorta el texto para que desaparezcan.
- Haz clic derecho en el elemento y abre **Barras de desplazamiento**. **Mostrar** permite elegir cuándo aparecen: **Siempre**, **Solo al desplazarse** o **Nunca**. Si seleccionas **Nunca**, la rueda del mouse seguirá desplazando el texto.
- En el mismo menú, **Estilo del control de desplazamiento**, **Texturas del control de desplazamiento** y **Color del control de desplazamiento [HEX]** permiten cambiar su apariencia.

Consulta [Texto en los menús](/text-in-menus#scroll-bars) para ver todos los ajustes de las barras de desplazamiento.

### ¿Cómo puedo mostrar en mis menús las notas de la última actualización de Minecraft?

Hay un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte las notas de las actualizaciones de Minecraft a Markdown compatible con FancyMenu, ¡para que puedas mostrar las notas más recientes de MC en tus menús! Se actualiza a diario para obtener las nuevas notas.

Para mostrarlas en un [elemento de texto](/elements#text), establece **Modo de origen** en **Recurso** y el origen del recurso en **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más fácil de estirar cualquier elemento hasta que ocupe toda la pantalla?

La mayoría de los elementos tienen una opción en su menú contextual (al hacer clic derecho) para estirarlos horizontal y verticalmente. Al activarla, el elemento se estirará para ocupar todo el ancho o alto de la pantalla, o ambos. Puedes activar o desactivar el estiramiento horizontal y vertical por separado.

### No puedo hacer clic en los botones ni interactuar con los deslizadores que están detrás o delante de un elemento de texto.

Esto ocurre porque los elementos de texto son interactivos de forma predeterminada (para poder agarrar el control de desplazamiento o hacer clic en los hipervínculos de Markdown), por lo que consumen los clics del mouse y los eventos de desplazamiento. Lo ideal es no colocar botones detrás ni delante de elementos de texto. Si no hay otra opción, puedes hacer que el elemento de texto deje de ser interactivo: **haz clic derecho en él** y establece **Interactivo** en **Desactivado**. Ten en cuenta que esto hará que el texto sea estático y no interactivo, por lo que ya no podrás desplazarte por él ni hacer clic en sus hipervínculos.

### ¿Cómo evito que los botones y los deslizadores se seleccionen o reciban el enfoque al navegar por las pantallas con las teclas de flecha y Tab?

Para que los botones y deslizadores no se puedan recorrer con el teclado, **haz clic derecho en ellos** y establece **Navegable** en **Desactivado**. Aún se podrá hacer clic en el botón o el deslizador, pero ya no podrás enfocarlo con las teclas de flecha o Tab.

Esto también es útil si quieres agregar botones o deslizadores a la pantalla de chat, ya que podrás seguir usando la flecha hacia arriba para recorrer los mensajes anteriores sin seleccionar por accidente los botones o deslizadores de la pantalla.

### A uno de los menús contextuales de FancyMenu le falta una opción que debería aparecer.

Los menús contextuales de FancyMenu (los que se abren al hacer clic derecho en algún lugar o al interactuar con las barras de menú) tienen **desplazamiento**. Esto significa que puedes usar la rueda del mouse mientras el cursor está sobre el menú para desplazarte hacia arriba o abajo y ver más opciones que antes no estaban visibles.

### No puedo personalizar la pantalla de título; al salir del editor, vuelve a aparecer la original.

Otro mod está reemplazando la pantalla `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en sus ajustes. Si no tiene esa opción, FancyMenu no puede aplicar el diseño a la pantalla de reemplazo.

### Cuando intento personalizar la pantalla del inventario, no puedo personalizar el contenedor del inventario.

Es normal. FancyMenu no permite editar el contenedor en sí de ningún tipo de pantalla de inventario (inventario del jugador, cofre, mesa de trabajo, etc.), porque agregar compatibilidad con esa función sería muy difícil.

Aun así, puedes agregar elementos nuevos a esas pantallas; simplemente no puedes editar los contenedores.

Por cierto, SpiffyHUD tampoco te servirá en este caso, porque permite editar la interfaz del juego (por ejemplo, la barra rápida de objetos), pero no las pantallas (como las del inventario).
