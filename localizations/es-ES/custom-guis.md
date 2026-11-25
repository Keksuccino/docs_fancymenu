---
title: GUI personalizadas
description: >-
  Crea tus propios menús desde cero, ábrelos con botones, teclas o comandos,
  muéstralos como ventanas emergentes y sustituye otros menús por ellos.
sourceBlobSha: 0b336708473ae2964b3d9e777498c6cd40eaffc6
---

# GUI personalizadas

Las GUI personalizadas son menús que creas tú mismo, como una pantalla de información del modpack, un centro del servidor o una página de normas. Empiezan vacías y las completas con un [diseño](/layout-editor), como cualquier otro menú. Después, puedes abrirlas con botones, teclas y comandos.

<img width="800" alt="Al hacer clic en un botón de información del modpack en la pantalla de título, se abre una GUI personalizada como ventana emergente sobre la pantalla de título desenfocada; el botón Atrás la cierra" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_popup.gif?raw=true">

# Crear una GUI personalizada

<img width="800" alt="Abrir Gestionar GUI personalizadas, hacer clic en Nueva GUI, escribir el identificador modpack_info, activar el modo de ventana emergente y abrir la nueva GUI personalizada" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_new.gif?raw=true">

1. Abre **barra de menús -> Personalización -> GUI personalizadas -> Gestionar GUI personalizadas**.
2. Haz clic en **Nueva GUI**.
3. Escribe un **identificador de GUI personalizada**, como `modpack_info`, configura los [ajustes](#settings) y haz clic en **Listo**.
4. Haz clic en la nueva GUI personalizada de la lista y, a continuación, en **Abrir GUI**.
5. Haz clic en **Listo** para cerrar **Gestionar GUI personalizadas**.

**Gestionar GUI personalizadas** solo guarda los cambios cuando haces clic en **Listo** o en **Abrir GUI**. Si haces clic en **Cancelar**, se descartan.

## El identificador

Los botones, comandos y diseños buscan una GUI personalizada por su identificador.

- Solo puede contener letras minúsculas, números, `.`, `_` y `-`. Cada GUI personalizada debe tener un identificador propio.
- No uses el [identificador de otra pantalla](/screen-identifiers), como `title_screen`. La GUI personalizada compartiría sus diseños con esa pantalla.
- Si cambias el identificador más adelante, los diseños, botones y comandos que tengan el identificador antiguo dejarán de encontrarla. Si lo vuelves a cambiar al anterior, volverán a funcionar.

## Crear su diseño

1. Abre la GUI personalizada.
2. Haz clic en **barra de menús -> Personalización -> Diseños -> Nuevo -> Para la pantalla actual**. La personalización siempre está activada para las GUI personalizadas.
3. Añade elementos y guarda el diseño. Consulta [Editor de diseños](/layout-editor).

Una GUI personalizada no incluye nada, ni siquiera un botón Atrás. Añádele un [Botón](/elements#button) con la acción [**Volver a la última pantalla**](/action-scripts#back-to-last-screen) o deja activada la opción **Permitir cerrar la GUI con ESC** para que los jugadores puedan salir de ella.

# Ajustes

La opción **Editar GUI** de **Gestionar GUI personalizadas** permite cambiar los ajustes de la GUI personalizada seleccionada.

| Ajuste | Función |
|---|---|
| **Identificador de GUI personalizada** | El nombre de la GUI personalizada. Consulta [El identificador](#the-identifier). |
| **Título de pantalla (opcional)** | Un título blanco en la parte superior de la GUI. Déjalo vacío si no quieres mostrar ninguno. Se admiten [marcadores de posición](/placeholders), y las claves de localización del juego, los mods y los paquetes de recursos se muestran en el idioma del jugador. |
| **Permitir cerrar la GUI con ESC** | `Esc` cierra la GUI. Activado de forma predeterminada. |
| **Pausar el juego/mundo** | Pausa los mundos de un jugador mientras la GUI está abierta. Activado de forma predeterminada. |
| **Renderizar el fondo del mundo** | Muestra el mundo detrás de la GUI mientras juegas. Fuera de los mundos, o si esta opción está desactivada, se muestra el panorama de Minecraft. Activado de forma predeterminada. |
| **Renderizar la superposición del fondo del mundo** | Desenfoca y oscurece el mundo o el panorama que hay detrás de la GUI, como hace el menú de pausa. Solo funciona con **Renderizar el fondo del mundo**: sin esta opción, el panorama siempre aparece desenfocado y más oscuro. Activado de forma predeterminada. |
| **Modo de ventana emergente** | Muestra la GUI encima del menú desde el que se abrió. Consulta [Modo de ventana emergente](#popup-mode). |
| **Superposición del fondo del modo de ventana emergente** | Desenfoca el menú que hay detrás de la ventana emergente. Solo funciona con **Modo de ventana emergente**. Activado de forma predeterminada. |

- El desenfoque tiene la misma intensidad que la opción de Minecraft **Desenfoque del fondo del menú**.
- Un [fondo de menú](/menu-backgrounds) en el diseño cubre todo esto: el mundo, el panorama y el menú que hay detrás de una ventana emergente.
- El editor de diseños no puede cambiar el título (**Título de pantalla personalizado**) de las GUI personalizadas. En su lugar, cambia **Título de pantalla (opcional)**. Si quieres un título con su propia fuente, color o posición, deja esa opción vacía y añade un [elemento de texto](/elements#text).

## Modo de ventana emergente

Con **Modo de ventana emergente**, el menú desde el que se abrió la GUI personalizada permanece visible detrás de ella, junto con su diseño. No se puede hacer clic en él mientras la ventana emergente esté abierta.

- Las ventanas emergentes funcionan mejor para elementos pequeños, como un cuadro de información, una confirmación o un panel de ajustes. Deja algo de espacio libre para que se vea el menú de detrás.
- No añadas un fondo de menú al diseño de una ventana emergente; de lo contrario, el menú de detrás desaparecerá.
- Si la GUI personalizada se abre cuando no hay ningún menú abierto, por ejemplo, al pulsar una tecla mientras juegas, no habrá ningún menú detrás. En ese caso, se mostrará su fondo normal.

# Abrir una GUI personalizada

Cualquier elemento que abra pantallas puede abrir GUI personalizadas mediante su identificador:

- **Botones:** la acción [**Abrir pantalla o GUI personalizada**](/action-scripts#open-screen-or-custom-gui) con el valor `modpack_info`.
- **Teclas:** un [escuchador **Al pulsar una tecla del teclado**](/listeners#listener-variables) con la misma acción. Abre la GUI personalizada tanto en los menús como mientras juegas.
- **Comandos:** `/openguiscreen modpack_info`, también desde servidores, bloques de comandos y recompensas de misiones. Consulta [Comandos](/commands#openguiscreen).
- **Al salir de un mundo:** la acción [**Salir del mundo o servidor**](/action-scripts#leave-world-or-server) abre la GUI personalizada al salir, si se especifica su identificador.

Las GUI personalizadas forman parte de la configuración de FancyMenu de cada jugador. Un servidor solo puede abrir las GUI personalizadas que tengan sus jugadores, como las incluidas en el modpack.

Para salir de una GUI personalizada:

- `Esc` (si está activada la opción **Permitir cerrar la GUI con ESC**) y la acción **Volver a la última pantalla** vuelven al menú desde el que se abrió. Si no había ningún menú abierto, `Esc` vuelve al juego.
- La acción [**Cerrar pantalla**](/action-scripts#close-screen) la cierra. Fuera de los mundos, se abre la pantalla de título.

# Sustituir una pantalla existente

Una GUI personalizada puede sustituir un menú del juego o de un mod. Cada vez que se fuera a abrir ese menú, se abrirá la GUI personalizada en su lugar.

> [!WARNING]
> El menú sustituido no se abre nunca, así que no se ejecuta nada de lo que hace y pueden dejar de funcionar otros mods que lo necesiten. Siempre que puedas, cambia los menús con un diseño normal. Sustituye un menú solo cuando un diseño no pueda hacer lo que necesitas.

1. Activa **barra de menús -> Personalización -> Ajustes -> Modo de personalización avanzado**.
2. Abre el menú que quieras sustituir.
3. Haz clic en **barra de menús -> Personalización -> GUI personalizadas -> Sustituir la pantalla actual por una GUI personalizada**.
4. Confirma el aviso y elige la GUI personalizada en **Elegir GUI personalizada**.

La GUI personalizada se abre inmediatamente. `Esc` y **Volver a la última pantalla** vuelven al menú que estaba abierto antes del menú sustituido.

Para deshacerlo, abre **barra de menús -> Personalización -> GUI personalizadas -> Gestionar pantallas sustituidas**, haz clic en **Eliminar regla de sustitución** debajo de la pantalla y, a continuación, en **Listo**.

> [!TIP]
> Para sustituir un menú solo en algunos casos, por ejemplo, cuando una [variable](/variables) tiene un valor determinado, usa un [escuchador **Al abrirse una pantalla**](/listeners#on-screen-opened) con una instrucción IF.

# Gestionar GUI personalizadas

- **Nueva GUI**, **Editar GUI** y **Abrir GUI** en **Gestionar GUI personalizadas** permiten añadir, cambiar y abrir GUI personalizadas.
- **Eliminar GUI** elimina la GUI personalizada seleccionada tras pedirte confirmación. Sus diseños se conservan y volverán a mostrarse en una nueva GUI personalizada con el mismo identificador.
- La barra de búsqueda encuentra GUI personalizadas por su identificador.
- **barra de menús -> Ayuda -> Exportar para IA -> GUI personalizadas** exporta todas las GUI personalizadas y las reglas de sustitución para un [chat de IA](/export-for-ai).

Las GUI personalizadas y las reglas de sustitución se guardan en `config/fancymenu/custom_gui_screens.txt`; sus diseños se guardan en `config/fancymenu/customization/`, como todos los demás (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations)). Cada [perfil](/profiles) tiene sus propias GUI personalizadas.
