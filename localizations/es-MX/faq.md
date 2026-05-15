---
title: Preguntas frecuentes
description: Preguntas frecuentes.
---

# Preguntas frecuentes

### Necesito ayuda con un problema. ¿Qué información debo proporcionar?
Para recibir la mejor ayuda posible, proporciona todo el contexto que puedas:
1.  **Una descripción clara del problema:** ¿Qué esperabas que sucediera y qué pasó realmente?
2.  **Tu archivo `latest.log`:** Este es el archivo más importante para diagnosticar problemas. Encuéntralo en la carpeta `/logs/` de tu instancia. **No envíes un crash log** a menos que te lo pidan específicamente; `latest.log` es mucho más útil. Usa un sitio como https://gist.github.com para compartirlo.
3.  **Tu versión de Minecraft:** (por ejemplo, 1.20.1)
4.  **Tu cargador de mods y versión:** (por ejemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Tu versión de FancyMenu:** (por ejemplo, 3.5.2)
6.  **Capturas de pantalla o videos** del problema también pueden ser de mucha ayuda.

### ¿Cómo cambio la jerarquía de los elementos (poner algo delante o detrás de otro)?
*   **Personalizado vs. personalizado:** Para cambiar el orden de renderizado de tus propios elementos personalizados, usa el **widget Layers**. Puedes abrirlo desde la barra de menú: **Window -> Widgets -> Layers**. Desde ahí, puedes arrastrar elementos hacia arriba o hacia abajo en la jerarquía. También puedes hacer clic derecho en un elemento y usar "Move One Layer Up/Down".
*   **Personalizado vs. vanilla:** Para renderizar todos tus elementos personalizados detrás de todos los elementos vanilla (por ejemplo, poner una imagen de fondo detrás de los botones predeterminados), **haz clic derecho en el fondo del editor** y activa la opción **"Render Custom Elements Behind Vanilla"**.

### ¿Puedo excluir ciertos botones de una plantilla universal de botones?
**No. Si un botón de plantilla tiene texturas personalizadas configuradas, esas texturas siempre se comparten con todos los elementos afectados. No puedes excluir botones individuales.**

### ¿Cómo hago que un botón haga algo al hacer clic?
Usa un **script de acciones**.
1.  Haz clic derecho en el botón en el editor.
2.  Selecciona **Edit Action Script**.
3.  Haz clic en **Add Action** y elige de la lista (por ejemplo, `Open Screen or Custom GUI`, `Join Server`, `Set Variable Value`).
*   Más información: [Action Scripts](https://docs.fancymenu.net/en/action-scripts)

### ¿Puedo crear una pantalla de menú completamente nueva desde cero?
Sí, esto se hace usando **Custom GUIs**.
1.  En la barra de menú, ve a **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Haz clic en **"New GUI"** y dale un identificador único.
3.  Después podrás abrir esta nueva pantalla vacía y crear un diseño para ella, agregando los elementos que quieras.
4.  Luego esta Custom GUI se puede abrir mediante una acción de botón.
*   Más información: [Custom GUIs](https://docs.fancymenu.net/en/custom-guis)

### Mi juego tarda mucho en cargar después de habilitar la precarga.
Esto es un comportamiento esperado. Precargar recursos grandes, como animaciones o sonidos de alta resolución, durante el arranque inicial aumentará naturalmente el tiempo de carga del juego.

### ¡Mi animación FMA está usando demasiada RAM!
Los archivos FMA clásicos pueden consumir mucha memoria cuando contienen muchos cuadros de alta resolución. FancyMenu 3.9.0 agrega AFMA, que es mucho mejor para texturas animadas grandes o complejas. Para archivos FMA clásicos, mantén las animaciones cortas y evita contar con demasiados cuadros o resoluciones muy altas. Las animaciones están pensadas para bucles cortos y decorativos, no para reproducir videos completos.

### ¿FancyMenu funciona con OptiFine?
No. OptiFine **no es compatible** y se sabe que rompe muchos mods, incluido FancyMenu. Se recomienda encarecidamente usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
*   Más información: [Alternativas a OptiFine](https://docs.fancymenu.net/en/optifine-alternatives)

### Mi juego se cierra inesperadamente. ¿Cómo puedo saber si es un conflicto de mods?
La mejor forma de revisar si hay un conflicto de mods es **ejecutar el juego solo con FancyMenu y sus dependencias** (Konkrete, Melody). Si el cierre inesperado ya no ocurre, puedes volver a agregar tus otros mods en grupos pequeños hasta que el problema reaparezca, para identificar el mod conflictivo.

### Un botón de otro mod desaparece o no funciona cuando intento editarlo.
Esto normalmente significa que el otro mod agrega sus botones de una forma no estándar con la que FancyMenu no puede interactuar. Este es un problema que el desarrollador del otro mod tendría que corregir de su lado. FancyMenu no puede personalizar elementos que no puede "ver".

### ¿Puedo usar los diseños de FancyMenu en un servidor?
FancyMenu es un mod del lado del cliente. Todos los diseños y personalizaciones están en el cliente del jugador. No puedes poner diseños en un servidor para obligar a los jugadores a verlos. Sin embargo, puedes distribuir tu carpeta `config/fancymenu` como parte de un modpack. Si quieres usar comandos como `/fmvariable` o `/openguiscreen` desde el servidor, entonces FancyMenu (o su plugin de Spigot) debe estar instalado en el servidor.

### ¿Cuál es la diferencia entre FancyMenu v2 (para versiones antiguas de MC) y v3?
FancyMenu v3 es una reescritura completa con muchas funciones nuevas, una arquitectura más estable y mejor rendimiento. V2 está desactualizado, ya no tiene soporte y le faltan muchas funciones como placeholders avanzados y scripting. Se recomienda encarecidamente usar v3 en una versión moderna de Minecraft (1.18.2+). Los diseños de V2 se pueden convertir automáticamente a v3 al cargarlos, pero quizá sea necesario hacer algunos ajustes manuales.

### ¿Dónde puedo encontrar diseños y plantillas ya hechas?
La comunidad de FancyMenu comparte diseños en el canal `#layout-templates` del servidor oficial de Discord de Keksuccino's Mods.

### ¿Cómo puedo hacer que la entidad del jugador se renderice detrás de otros elementos?
No se puede. Debido a la forma en que Minecraft renderiza las entidades, el elemento Player Entity casi siempre se renderizará delante de otros elementos 2D, sin importar la configuración de capas.

### ¡Mi entidad del jugador solo tiene una pierna! ¿Qué pasó?
Es un fallo visual, probablemente causado por un conflicto de mods con otro mod que modifica las animaciones o modelos del jugador. Revisa la configuración de Pose de Player Entity para ver si las piernas se rotaron o movieron por accidente.

### ¿Cómo creo un retraso entre acciones en un script?
FancyMenu 3.9.0 agrega bloques **Delay** y **Execute Later** a los scripts de acciones. Úsalos para la mayoría de la lógica de acciones con retraso. Para lógica en segundo plano que se repite, usa [Schedulers](https://docs.fancymenu.net/en/schedulers).

### ¿Puedo personalizar menús del mod Create?
No. FancyMenu tiene incompatibilidades conocidas con las GUIs complejas de Create. La personalización de las pantallas de Create se deshabilitó intencionalmente para evitar cierres inesperados.

### ¿Por qué desaparecen los botones del mod X en el editor?
Esto significa que el mod agrega sus botones de una forma personalizada, no vanilla. FancyMenu no puede "ver" ni interactuar con esos elementos, así que no puede personalizarlos. El desarrollador del otro mod tendría que cambiar cómo agrega sus botones para que sean compatibles.

### ¿Cuál es la resolución recomendada para imágenes de fondo y texturas de botones?
Fondos: una imagen estándar de 1920x1080 (1080p) es un excelente punto de partida y se adaptará bien para la mayoría de los usuarios.
Botones: la mayoría de los botones vanilla tienen un ancho de alrededor de 150 a 200 píxeles y una altura de 20 píxeles. Igualar este tamaño para texturas personalizadas es una buena práctica para mantener la consistencia.

### ¿Hay alguna forma de abrir automáticamente un menú o ejecutar un comando cuando un jugador completa un objetivo del juego (como una misión)?
FancyMenu por sí solo no puede detectar eventos del juego como este. Sin embargo, puedes integrarlo con un mod de misiones como FTB Quests. La mayoría de los mods de misiones permiten ejecutar un comando como recompensa de una misión. Configurarías la recompensa para ejecutar el comando `/openguiscreen` o `/fmvariable` e interactuar con tus menús.

### ¿Cómo hago que un botón esté inactivo o "gris"?
Puedes controlar el estado activo de un botón usando Loading Requirements.
Haz clic derecho en el botón en el editor y selecciona "Active State".
Agrega un requisito que deba cumplirse para que el botón esté activo. Por ejemplo, para deshabilitar permanentemente un botón, podrías agregar un requisito Is Number que verifique si 0 es igual a 1 (lo cual siempre es falso).
Ahora el botón usará su textura de "Inactive Background" y no se podrá hacer clic en él.

### ¿Cómo puedo quitar el encabezado y el pie de página (las barras con textura de tierra) en pantallas desplazables?
En FancyMenu v3, puedes personalizarlos. En el editor de diseño, haz clic derecho en el fondo del editor y busca opciones como "Customize Header/Footer". Puedes configurar sus texturas para que sean completamente transparentes y así eliminarlos visualmente. Ten en cuenta que esto puede no funcionar en todas las pantallas, especialmente en las más antiguas o muy modificadas.

### No puedo crear un diseño "para la pantalla actual". El botón está deshabilitado.
Primero debes habilitar las personalizaciones para esa pantalla mediante **menu bar -> Customization -> Current Screen Customizations -> toggle it to Enabled**.

### No puedo personalizar ningún elemento de una pantalla cuando la abro en el editor. Entonces solo aparece una pantalla vacía.

Esto podría significar que por accidente creaste un diseño universal en lugar de uno **para la pantalla actual**.

También podría significar que la pantalla que estás personalizando es una pantalla desplazable, y FancyMenu no puede personalizar esas pantallas de forma predeterminada.

La tercera posibilidad es que sea una pantalla de un mod que agrega elementos de una forma no vanilla, lo que hace que FancyMenu no pueda personalizar esos elementos.

### Hay cajas grises extrañas en mi elemento de texto.

Estas cajas o rectángulos translúcidos (de baja opacidad) pueden estar en el borde derecho o inferior de tu elemento de texto y no son un error. Son los controladores de desplazamiento del elemento de texto, ya que el elemento es desplazable.

Si no quieres que estas cajas sean visibles, puedes hacer clic derecho en el elemento y desactivar completamente el desplazamiento, o también puedes configurar las texturas de los controladores para que sean completamente transparentes en el mismo menú de clic derecho, si quieres que el elemento siga siendo desplazable.

### ¿Cómo puedo mostrar el changelog más reciente de Minecraft en mis menús?

Hay un excelente [proyecto de GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que convierte los changelogs de Minecraft a Markdown compatible con FancyMenu, ¡así puedes mostrar el changelog más reciente de MC en tus menús! Se actualiza todos los días para obtener los nuevos changelogs.

Por ejemplo, para mostrar el changelog más reciente de Minecraft en un elemento de texto, configura su **Source Mode** como **Resource** y define su fuente de recursos como **Web**. Luego usa esta URL como fuente: `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`

### ¿Cuál es la forma más fácil de estirar cualquier elemento al tamaño de la pantalla?

La mayoría de los elementos tienen una opción en sus menús contextuales de clic derecho para estirarlos horizontal y verticalmente. Al habilitarla, siempre se estirarán al ancho y/o alto completo de la pantalla. El estiramiento horizontal y vertical se pueden activar de manera independiente.

### No puedo hacer clic en botones ni interactuar con deslizadores cuando están detrás o delante de un elemento de texto.

Esto sucede porque los elementos de texto son interactuables por defecto (para poder arrastrar el controlador de desplazamiento o hacer clic en hipervínculos Markdown), lo que significa que consumen clics del mouse y eventos de desplazamiento. La mejor solución sería simplemente no mover botones detrás o delante de elementos de texto, pero si no hay otra opción, puedes hacer que el elemento de texto no sea interactuable **haciendo clic derecho en él** y luego configurando **Interactable** en **Disabled**. Ten en cuenta que esto convierte el elemento de texto en un texto estático, no interactuable, así que ya no podrás desplazarte por él ni hacer clic en hipervínculos.

### ¿Cómo hago para que los botones y deslizadores ya no se seleccionen o enfoquen al navegar en pantallas con las teclas de flecha y Tab?

Para que los botones y deslizadores no sean navegables, necesitas **hacer clic derecho** y configurar **Navigable** en **Disabled**. El botón o deslizador seguirá siendo clicable, pero ya no podrás enfocarlo con la navegación de Arrow/Tab.

Esto también es útil si quieres agregar botones o deslizadores a la pantalla del chat, para que aún puedas usar la tecla de flecha arriba para desplazarte por mensajes anteriores sin seleccionar accidentalmente botones o deslizadores en la pantalla.

### A uno de los menús contextuales de FancyMenu le falta una opción que debería estar ahí.

Los menús contextuales de FancyMenu (los menús que se abren cuando haces clic derecho en algún lugar o interactúas con las barras de menú) son DESPLAZABLES. Esto significa que puedes usar la rueda del mouse mientras el cursor está sobre el menú para desplazarte hacia arriba o hacia abajo, lo que te permite ver más opciones que antes no eran visibles.
