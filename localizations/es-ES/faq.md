---
title: Preguntas frecuentes
description: Preguntas frecuentes.
sourceBlobSha: 4ae872e8e4a54fc6a89de7c87c8a137a89292455
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para recibir la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que ocurriera y qué ha ocurrido en realidad?
2.  **Tu archivo `latest.log`:** Lo encontrarás en `<game-directory>/logs/latest.log`. **No envíes un registro de error** salvo que te lo pidan expresamente; `latest.log` suele contener el contexto necesario. Para compartirlo, usa un sitio como https://gist.github.com.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **También pueden ser de gran ayuda las capturas de pantalla o los vídeos** del problema.

> [!TIP]
> ¿Vas a pedir ayuda a Alice o a otra IA? Añade una [exportación para IA](/export-for-ai) de lo que no funciona. Así, la IA verá exactamente cómo está configurado y, además, ya incluirá tus versiones de Minecraft, del cargador de mods y de FancyMenu.

### ¿Cómo cambio el orden de los elementos (para poner algo delante o detrás de otra cosa)?

- **Tus propios elementos:** arrastra sus capas en el widget Capas del editor de diseños o haz clic derecho en un elemento y selecciona **Subir una capa** o **Bajar una capa**. Consulta [Capas y grupos](/layout-editor#layers-and-groups).
- **Tus elementos y los elementos vanilla:** no se puede cambiar el orden de los elementos vanilla. Para colocar todos tus elementos detrás de ellos —por ejemplo, para poner una imagen de fondo detrás de los botones predeterminados—, haz clic derecho en el fondo del editor y establece **Elementos personalizados detrás de los vanilla** en **Activado**.

### ¿Puedo excluir algunos botones de una plantilla de botones universal?

**No. Si un botón de la plantilla tiene texturas personalizadas, estas se compartirán siempre con todos los elementos afectados. No puedes excluir botones concretos.**

### ¿Cómo hago que un botón realice una acción al hacer clic en él?

Usa un [**script de acciones**](/action-scripts).
1.  Haz clic derecho en el botón del editor.
2.  Selecciona **Editar script de acciones**.
3.  Haz clic en **Añadir acción** y elige una, como [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui), [**Unirse a un servidor**](/action-scripts#join-server) o [**Establecer valor de variable**](/action-scripts#set-variable-value-fm-variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Sí, con una [GUI personalizada](/custom-guis):

1. Abre **barra de menús -> Personalización -> GUIs personalizadas -> Gestionar GUIs personalizadas** y haz clic en **Nueva GUI**.
2. Asígnale un identificador, como `modpack_info`, y haz clic en **Listo**.
3. Ábrela con **Abrir GUI** y crea un diseño para ella, igual que para cualquier otro menú.
4. Ábrela desde un botón con la acción [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui) y su identificador.

### El juego tarda mucho en cargarse después de activar la precarga.

Es el comportamiento esperado. Precargar recursos grandes, como animaciones de alta resolución o sonidos, durante el inicio del juego aumentará de forma natural el tiempo de carga.

### ¡Mi animación usa mucha RAM o hace que el juego vaya a tirones!

Los fotogramas grandes y una frecuencia de fotogramas elevada consumen memoria y rendimiento. Procura que los fotogramas tengan aproximadamente el tamaño con el que aparecerán en pantalla y usa menos fotogramas por segundo. Consulta [Animaciones](/animations#performance). Para clips largos con sonido, usa un [vídeo](/video).

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que da problemas con muchos mods, incluido FancyMenu. Se recomienda encarecidamente usar alternativas modernas, como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](/optifine-alternatives).

### El juego se bloquea. ¿Cómo puedo averiguar si se trata de un conflicto entre mods?

La mejor forma de comprobar si hay un conflicto entre mods es **ejecutar el juego solo con FancyMenu y sus dependencias** (Konkrete, Melody). Si el bloqueo deja de producirse, vuelve a añadir los demás mods en grupos pequeños hasta que vuelva a ocurrir para identificar el mod conflictivo.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods añaden widgets de formas que FancyMenu no puede detectar ni personalizar. Consulta [Elementos vanilla/de mods](/vanilla-elements) y, para las pantallas con listas, [Personalizar pantallas desplazables](/customizing-scrollable-screens). Si el widget sigue sin aparecer, el mod que lo añade debe exponerlo como un widget de pantalla compatible.

### ¿Puedo usar diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se guardan en el cliente del jugador; un servidor no puede aplicarlos a un cliente que no esté configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor si necesitas [comandos de servidor](/commands), [datos de FM](/fm-data), [acceso a NBT desde el servidor](/nbt-data-placeholder#server-side-placeholder), reglas de juego, estructuras o escuchas de eventos del servidor.

### ¿Qué diferencias hay entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y un mejor rendimiento. V2 está obsoleto, ya no tiene soporte y carece de muchas funciones, como los marcadores de posición avanzados y los scripts. Se recomienda encarecidamente usar v3 con una versión moderna de Minecraft (1.18.2 o posterior). Los diseños de V2 se pueden convertir automáticamente a v3 al cargarlos, aunque quizá haya que corregir algunas cosas manualmente.

### ¿Dónde puedo encontrar diseños y plantillas ya preparados?

La comunidad de FancyMenu comparte configuraciones completas en el canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del servidor oficial de Discord («Kekscord»). Instálalas como un perfil independiente; consulta [Plantillas de diseños](/profiles#layout-templates).

### ¿Cómo puedo hacer que la entidad del jugador aparezca detrás de otros elementos?

Por lo general, no puedes obligar a un [elemento de entidad del jugador](/elements#player-entity) a aparecer detrás de los elementos 2D normales mediante el [widget Capas](/layout-editor#layers-and-groups). Su renderizador puede ignorar el orden normal de las capas de la GUI. Diseña el diseño teniendo en cuenta esta limitación o usa una imagen prerenderizada si necesitas controlar estrictamente el orden de las capas.

### ¡A mi entidad del jugador le falta una pierna! ¿Qué ha pasado?

Es un fallo visual, probablemente causado por un conflicto con otro mod que modifica las animaciones o los modelos de los jugadores. Comprueba los ajustes de Pose de la entidad del jugador para ver si las piernas se han girado o movido por accidente.

### ¿Cómo puedo añadir una pausa entre acciones de un script?

Haz clic derecho en el área del script del editor de scripts de acciones, haz clic en **Añadir bloque EXECUTE LATER** y coloca dentro las acciones que deban esperar. Se ejecutarán una vez transcurrido el tiempo especificado en milisegundos, y el resto del script continuará inmediatamente. Consulta [Execute Later](/action-scripts#execute-later).

Para acciones que deban repetirse, usa los [programadores](/schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización de las pantallas de Create está desactivada intencionadamente. Consulta [Pantallas cuya personalización está desactivada intencionadamente](/incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Qué resolución se recomienda para las imágenes de fondo y las texturas de los botones?

Fondos: una imagen estándar de 1920 × 1080 (1080p) es un buen punto de partida y se adaptará bien a la mayoría de usuarios.
Botones: la mayoría de los botones vanilla miden unos 150-200 píxeles de ancho y 20 píxeles de alto. Usar ese tamaño para las texturas personalizadas es una buena práctica para mantener la coherencia.

### ¿Hay alguna forma de abrir un menú automáticamente o ejecutar un comando cuando un jugador completa un objetivo del juego, como una misión?
FancyMenu cuenta con muchos [escuchas de eventos del juego integrados](/listeners), pero no existe un escucha genérico para todos los sistemas de misiones de terceros. Si el mod de misiones permite recompensas mediante comandos, usa una para ejecutar [`/openguiscreen`](/commands#openguiscreen), [`/fmvariable`](/commands#fmvariable) u otro [comando de FancyMenu](/commands) adecuado.

### ¿Cómo puedo desactivar un botón o hacer que aparezca atenuado?

Puedes controlar si un botón está activo mediante [requisitos](/conditions).
Haz clic derecho en el botón del editor y selecciona **Controlar estado activo**.
Añade un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Es número**](/conditions#is-number) para comprobar si 0 es igual a 1.
El botón usará entonces su textura «Fondo inactivo» y no se podrá hacer clic en él.

### ¿Cómo puedo quitar el encabezado y el pie (las barras con textura de tierra) de las pantallas desplazables?

En el editor de diseños, abre **Propiedades del diseño -> Personalización del encabezado/pie**. Establece las texturas como transparentes. Es posible que esta opción no esté disponible en algunas pantallas de mods.

### No puedo crear un diseño «para la pantalla actual». El botón aparece atenuado.

Activa primero las personalizaciones para esa pantalla: haz clic en **barra de menús -> Personalización -> Personalización de la pantalla actual** y comprueba que aparezca **Activado**.

### No puedo personalizar ningún elemento de una pantalla al abrirla en el editor. Aparece vacía.

Puede que hayas creado un [diseño universal](/universal-layouts) en vez de uno **para la pantalla actual**.

También podría tratarse de una [pantalla desplazable](/customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que añade elementos de una forma distinta a la de Vanilla, por lo que FancyMenu no puede personalizarlos.

### Aparecen unos cuadros grises extraños en mi elemento de texto.

Son las barras de desplazamiento del [elemento de texto](/elements#text). Aparecen cuando el texto no cabe en el elemento, para que los jugadores puedan desplazarse por él.

- Haz el elemento más grande o acorta el texto para que desaparezcan.
- Haz clic derecho en el elemento y abre **Barras de desplazamiento**. La opción **Mostrar** permite elegir cuándo aparecen: **Siempre**, solo **Al desplazarse** o **Nunca**. Aunque selecciones **Nunca**, la rueda del ratón seguirá desplazando el texto.
- En el mismo menú, las opciones **Estilo del control de desplazamiento**, **Texturas del control de desplazamiento** y **Color del control de desplazamiento [HEX]** permiten cambiar su aspecto.

Consulta [Texto en los menús](/text-in-menus#scroll-bars) para ver todas las opciones de las barras de desplazamiento.

### ¿Cómo puedo mostrar en mis menús las últimas notas de cambios de Minecraft?

Hay un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte las notas de cambios de Minecraft a Markdown compatible con FancyMenu, ¡para que puedas mostrar las últimas notas de cambios de MC en tus menús! Se actualiza a diario para obtener las nuevas notas de cambios.

Para mostrarlo en un [elemento de texto](/elements#text), establece **Modo de origen** en **Recurso** y el origen del recurso en **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más sencilla de ajustar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en su menú contextual (clic derecho) para estirarlos horizontal o verticalmente. Al activarla, se estirarán siempre hasta ocupar todo el ancho o el alto de la pantalla. El estiramiento horizontal y el vertical se pueden activar por separado.

### No puedo hacer clic en los botones ni interactuar con los controles deslizantes que están detrás o delante de un elemento de texto.

Esto ocurre porque los elementos de texto son interactivos de forma predeterminada (para poder agarrar el control de desplazamiento o hacer clic en los enlaces Markdown), por lo que capturan los clics y los eventos de desplazamiento del ratón. Lo más sencillo es no colocar botones detrás ni delante de elementos de texto. Pero, si no hay otra opción, puedes hacer que el elemento de texto deje de ser interactivo: **haz clic derecho en él** y establece **Interactivo** en **Desactivado**. Ten en cuenta que, así, el texto será estático y no interactivo, por lo que ya no podrás desplazarte por él ni hacer clic en los enlaces.

### ¿Cómo puedo evitar que se seleccionen o enfoquen los botones y los controles deslizantes al navegar por las pantallas con las teclas de flecha y Tabulador?

Para que no se pueda navegar hasta los botones y los controles deslizantes, **haz clic derecho** en el elemento y establece **Navegable** en **Desactivado**. Seguirá siendo posible hacer clic en él, pero ya no podrás enfocarlo con las teclas de flecha o el tabulador.

También es útil si quieres añadir botones o controles deslizantes a la pantalla del chat, porque podrás seguir usando la tecla de flecha arriba para recorrer los mensajes anteriores sin seleccionar accidentalmente los botones o los controles deslizantes de la pantalla.

### Falta una opción que debería aparecer en uno de los menús contextuales de FancyMenu.

Los menús contextuales de FancyMenu (los que se abren al hacer clic derecho en algún sitio o al interactuar con las barras de menús) son DESPLAZABLES. Puedes usar la rueda del ratón mientras el cursor esté sobre el menú para desplazarte hacia arriba o hacia abajo y ver más opciones que antes no estaban visibles.

### No puedo personalizar la pantalla del título; al salir del editor, sigue apareciendo la original.

Otro mod está sustituyendo la pantalla original `title_screen`. Desactiva la pantalla del título personalizada de ese mod en sus ajustes. Si no existe esa opción, FancyMenu no podrá aplicar el diseño a la pantalla que la sustituye.

### Al intentar personalizar la pantalla del inventario, no puedo personalizar el contenedor del inventario.

Es lo esperado. FancyMenu no permite editar el contenedor propiamente dicho de ningún tipo de pantalla de inventario (inventario del jugador, cofre, mesa de trabajo, etc.), ya que sería muy difícil añadir compatibilidad con ello.

Aun así, puedes añadir elementos nuevos a estas pantallas; lo que no puedes hacer es editar sus contenedores.

Por cierto, SpiffyHUD tampoco sirve para esto, porque permite editar el HUD (por ejemplo, la barra de acceso rápido de objetos), pero no las pantallas, como las del inventario.
