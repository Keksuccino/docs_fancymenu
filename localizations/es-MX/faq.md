---
title: Preguntas frecuentes
description: Preguntas frecuentes.
---
# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?

Para recibir la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que pasara y qué pasó en realidad?
2.  **Tu archivo `latest.log`:** Encuéntralo en `<game-directory>/logs/latest.log`. **No envíes un crash log** a menos que te lo soliciten específicamente; `latest.log` normalmente contiene el contexto necesario. Usa un sitio como https://gist.github.com para compartirlo.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y su versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Capturas de pantalla o videos** del problema también pueden ser muy útiles.

### ¿Cómo cambio la superposición de elementos (poner algo delante o detrás de otro)?

*   **Personalizado vs. Personalizado:** Abre **Window -> Editor Widgets -> Layers** y arrastra los elementos en la jerarquía. También puedes hacer clic derecho en un elemento y usar **Move One Layer Up/Down**. Consulta [Capas y grupos](./layers-and-groups).
*   **Personalizado vs. Vanilla:** Para renderizar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, para poner una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Render Custom Elements Behind Vanilla"**.

### ¿Puedo excluir ciertos botones de una plantilla universal de botones?

**No. Si un botón de plantilla tiene texturas personalizadas configuradas, estas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic?

Usa un [**Script de acciones**](./action-scripts).
1.  Haz clic derecho en el botón dentro del editor.
2.  Selecciona **Edit Action Script**.
3. Haz clic en **Add Action** y elige una acción, como [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) o [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?

Usa una [**GUI personalizada**](./custom-guis).
1.  En la barra de menú, ve a **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Haz clic en **"New GUI"** y asígnale un identificador único.
3.  Después puedes abrir esta nueva pantalla vacía y crear un diseño para ella, agregando todos los elementos que quieras.
4. Abre la GUI personalizada con la [**acción Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mi juego tarda mucho en cargar después de habilitar la precarga.

Esto es un comportamiento esperado. Precargar recursos grandes como animaciones o sonidos de alta resolución durante el inicio naturalmente aumentará el tiempo de carga del juego.

### ¡Mi animación FMA está usando demasiada RAM!

Las [animaciones FMA](./fma) clásicas pueden consumir mucha memoria cuando contienen muchos cuadros de alta resolución. AFMA es más adecuada para texturas animadas grandes o complejas. Mantén las animaciones FMA clásicas cortas; usa [Video](./video) para reproducción de video completa.

### ¿FancyMenu funciona con OptiFine?

No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda ampliamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Consulta [Alternativas a OptiFine](./optifine-alternatives).

### Mi juego se está cerrando. ¿Cómo puedo saber si es un conflicto entre mods?

La mejor forma de comprobar si hay un conflicto entre mods es **ejecutar el juego solo con FancyMenu y sus dependencias** (Konkrete, Melody). Si el cierre inesperado ya no ocurre, puedes volver a agregar tus otros mods en grupos pequeños hasta que vuelva a ocurrir el error para identificar el mod conflictivo.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.

Algunos mods agregan widgets de formas que FancyMenu no puede detectar ni personalizar. Revisa [Elementos Vanilla/Mod](./vanilla-elements) y, para pantallas basadas en listas, [Personalización de pantallas desplazables](./customizing-scrollable-screens). Si el widget aún no aparece, el mod que lo agrega debe exponerlo como un widget de pantalla compatible.

### ¿Puedo usar los diseños de FancyMenu en un servidor?

Los diseños y las personalizaciones visuales se almacenan en el cliente del jugador; un servidor no puede forzarlos en un cliente que no esté configurado. Distribúyelos como parte de un modpack. Instala FancyMenu en el servidor cuando necesites [comandos del servidor](./commands), [FM Data](./fm-data), [acceso NBT del lado del servidor](./nbt-data-placeholder#server-side-placeholder), gamerules, estructuras o listeners del servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?

FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y mejor rendimiento. V2 está desactualizado, ya no tiene soporte y le faltan muchas funciones como placeholders avanzados y scripting. Se recomienda encarecidamente usar v3 en una versión moderna de Minecraft (1.18.2+). Los diseños de V2 se pueden convertir automáticamente a v3 cuando los cargas, aunque puede ser necesario hacer algunos ajustes manuales.

### ¿Dónde puedo encontrar diseños y plantillas ya hechas?

La comunidad de FancyMenu comparte diseños en el canal `#layout-templates` del servidor oficial de Discord de Keksuccino's Mods ("Kekscord").

### ¿Cómo puedo hacer que la Entidad del jugador se renderice detrás de otros elementos?

Por lo general no puedes forzar que un [elemento Player Entity](./elements#player-entity) quede detrás de los elementos 2D normales mediante el [widget Layers](./layers-and-groups). Su renderizador puede ignorar el orden normal de capas de la interfaz. Diseña el layout considerando esa limitación o usa una imagen pre-renderizada cuando necesites un orden de capas estricto.

### ¡Mi Player Entity solo tiene una pierna! ¿Qué pasó?

Es un error visual, probablemente causado por un conflicto con otro mod que altera las animaciones o modelos del jugador. Revisa la configuración de Pose del Player Entity para ver si las piernas se movieron o rotaron por accidente.

### ¿Cómo creo un retraso entre acciones en un script?

Usa bloques [**Delay** o **Execute Later**](./action-scripts#what-are-statements) para lógica de acciones con retraso. Para lógica de fondo repetitiva, usa [Schedulers](./schedulers).

### ¿Puedo personalizar los menús del mod Create?

No. La personalización está deshabilitada intencionalmente para las pantallas de Create. Consulta [Pantallas donde la personalización está deshabilitada intencionalmente](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### ¿Cuál es la resolución recomendada para imágenes de fondo y texturas de botones?

Fondos: una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se adaptará bien para la mayoría de los usuarios.
Botones: la mayoría de los botones vanilla miden alrededor de 150-200 píxeles de ancho y 20 píxeles de alto. Igualar este tamaño en las texturas personalizadas es una buena práctica para mantener la consistencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo dentro del juego (como una misión)?
FancyMenu tiene muchos [listeners de eventos del juego](./listeners) integrados, pero no existe un listener genérico para cada sistema de misiones de terceros. Si el mod de misiones admite recompensas por comandos, usa una para ejecutar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) u otro [comando de FancyMenu](./commands) adecuado.

### ¿Cómo hago que un botón quede inactivo o "gris"?

Puedes controlar el estado activo de un botón usando [Loading Requirements](./conditions).
Haz clic derecho en el botón dentro del editor y selecciona **Control Active State**.
Agrega un requisito que deba cumplirse para que el botón esté activo. Para desactivarlo permanentemente, usa [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para comprobar si 0 es igual a 1.
Ahora el botón usará su textura de "Inactive Background" y no se podrá hacer clic en él.

### ¿Cómo puedo quitar el encabezado y el pie de página (las barras con textura de tierra) en pantallas desplazables?

En el editor de diseños, abre **Layout Properties -> Header/Footer Customizations**. Configura las texturas como transparentes. Esta opción puede no estar disponible en algunas pantallas modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón está desactivado.

Primero debes habilitar las personalizaciones para esa pantalla en **menu bar -> Customization -> Current Screen Customizations -> Enabled**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. Entonces solo aparece una pantalla vacía.

Esto podría significar que creaste un [Diseño universal](./universal-layouts) en lugar de uno **para la pantalla actual**.

También podría tratarse de una [pantalla desplazable](./customizing-scrollable-screens), que FancyMenu no puede personalizar de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que agrega elementos de una manera no vanilla, lo que impide que FancyMenu pueda personalizar esos elementos.

### Hay cuadros grises extraños en mi elemento Text.

Esos cuadros translúcidos son los agarradores de desplazamiento del [elemento Text](./elements#text), no un error de renderizado.

Si no quieres que esos cuadros sean visibles, puedes hacer clic derecho en el elemento y desactivar por completo el desplazamiento, o también puedes configurar las texturas de los agarradores como completamente transparentes en el mismo menú de clic derecho, si quieres que el elemento siga siendo desplazable.

### ¿Cómo puedo mostrar el changelog más reciente de Minecraft en mis menús?

Hay un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte los changelogs de Minecraft a Markdown compatible con FancyMenu, ¡así puedes mostrar el changelog más reciente de MC en tus menús! Se actualiza diariamente para obtener los nuevos changelogs.

Para mostrarlo en un [elemento Text](./elements#text), configura **Source Mode** en **Resource** y su fuente de recurso en **Web**. Usa `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### ¿Cuál es la forma más fácil de estirar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales de clic derecho para estirarlos horizontal y verticalmente. Activar esto hará que siempre ocupen todo el ancho y/o alto de la pantalla. El estiramiento horizontal y vertical pueden activarse de forma independiente.

### No puedo hacer clic en botones ni interactuar con sliders cuando están detrás o delante de un elemento Text.

Esto ocurre porque los elementos Text son interactivos por defecto (para poder tomar el agarrador de desplazamiento o hacer clic en hipervínculos Markdown), lo que significa que consumen los clics del mouse y los eventos de desplazamiento. Lo mejor sería simplemente no mover botones detrás o delante de los elementos Text, pero si no hay otra opción, puedes hacer que el elemento Text no sea interactivo haciendo **clic derecho** sobre él y configurando **Interactable** en **Disabled**. Ten en cuenta que esto convierte el elemento Text en texto estático y no interactivo, así que ya no podrás desplazarlo ni hacer clic en hipervínculos.

### ¿Cómo puedo hacer que los botones y sliders ya no se seleccionen o enfoquen al navegar en pantallas con las teclas de flecha y Tab?

Para que los botones y sliders no sean navegables, debes **hacer clic derecho** sobre ellos y configurar **Navigable** en **Disabled**. El botón o slider seguirá siendo clicable, pero ya no podrás enfocarlo con la navegación de flechas/Tab.

Esto también es útil si quieres agregar botones o sliders a la pantalla de chat, para que aún puedas usar la tecla Flecha Arriba para recorrer mensajes anteriores sin seleccionar accidentalmente botones o sliders en la pantalla.

### A uno de los menús contextuales de FancyMenu le falta una opción que debería estar ahí.

Los menús contextuales de FancyMenu (los menús que se abren cuando haces clic derecho en algún lugar o cuando interactúas con las barras de menú) son DESPLAZABLES. Esto significa que puedes usar la rueda del mouse mientras el cursor está sobre el menú para desplazarte hacia arriba o abajo, lo que te permite ver más opciones que antes no eran visibles.

### No puedo personalizar la pantalla de título; sigue mostrando la original cuando salgo del editor.

Otro mod está reemplazando la `title_screen` original. Desactiva la pantalla de título personalizada de ese mod en su configuración. Si no tiene esa opción, FancyMenu no puede aplicar el diseño a la pantalla reemplazada.
