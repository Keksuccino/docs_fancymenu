---
title: Requisitos
description: >-
  Muestra elementos y diseños, permite hacer clic en botones o ejecutar acciones
  solo cuando se cumple una condición, como la hora, el tamaño de la ventana o
  el valor de una variable.
sourceBlobSha: 8d7cc9e0182f8478f3a7ab86391e90cae12c626b
---

# Requisitos

Los requisitos son condiciones, como «el cursor está sobre este botón», «es diciembre» o «hay un mundo cargado». Úsalos para:

- mostrar un [elemento](/elements) solo en determinadas ocasiones,
- cargar un diseño completo solo en determinadas ocasiones,
- permitir hacer clic en botones, deslizadores y casillas solo en determinadas ocasiones,
- ejecutar partes de un [script de acciones](/action-scripts) solo en determinadas ocasiones.

FancyMenu comprueba los requisitos continuamente mientras hay un menú abierto, por lo que los elementos aparecen, desaparecen o cambian al instante. Este cuadro de información solo aparece cuando el cursor está sobre «Multijugador»:

<img width="800" alt="Al pasar el cursor sobre el botón Multijugador de la pantalla de título, aparece a su lado un cuadro de información con la dirección de un servidor" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_hover.gif?raw=true">

# Dónde encontrarlos

| Dónde | Qué hacen los requisitos |
|---|---|
| Clic derecho en un elemento -> **Requisitos de carga** | El elemento solo se muestra cuando se cumplen. También funciona con [elementos de Vanilla](/vanilla-elements). |
| Clic derecho en el fondo del editor -> **Requisitos de carga [para todo el diseño]** | El diseño completo solo se carga cuando se cumplen. Consulta [Requisitos para todo el diseño](#requisitos-para-todo-el-diseño). |
| Clic derecho en un botón, deslizador o casilla -> **Estado activo del control** | Solo se puede hacer clic en ellos cuando se cumplen. De lo contrario, aparecen en gris. Los botones de Vanilla también tienen esta opción. |
| IF, ELSE-IF y WHILE en los [scripts de acciones](/action-scripts#statements) | Las acciones que contienen solo se ejecutan cuando se cumplen. |

En el editor de diseños, los elementos siempre se muestran para que puedas seguir editándolos. Los requisitos de los elementos funcionan fuera del editor.

> [!TIP]
> [Visibilidad de los elementos](/element-visibility) explica más formas de mostrar y ocultar elementos, como usar retrasos, fundidos y alternarlos con un botón.

# Añadir un requisito

<img width="800" alt="Copiar el ID del botón Multijugador y, en Administrar requisitos, asignar al cuadro de información el requisito El cursor está sobre un elemento con ese ID" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_add.gif?raw=true">

1. Haz clic derecho en el elemento y selecciona **Requisitos de carga**. Se abrirá **Administrar requisitos**.
2. Haz clic derecho en la lista vacía y selecciona **Añadir requisito**, o pulsa `A`.
3. Haz clic en una categoría de **Requisitos disponibles** o empieza a escribir para buscar por nombre y descripción. **Descripción del requisito** explica el requisito seleccionado.
4. Haz clic en **Siguiente paso** para establecer su valor. Los requisitos que no necesitan un valor muestran **Listo**. También puedes hacer doble clic en un requisito para hacer lo mismo.
5. Introduce el valor y haz clic en **Listo**. Por ejemplo, **El cursor está sobre un elemento** necesita el ID del elemento. Para obtenerlo, haz clic derecho en un elemento y selecciona **Copiar ID del elemento**.
6. Haz clic en **Listo** en **Administrar requisitos**.

## Modo de requisito

El botón **Modo de requisito** del selector de requisitos permite alternar entre:

- **Normal**: se cumple cuando la condición es verdadera.
- **Opuesto**: se cumple cuando la condición NO es verdadera. Por ejemplo, **Hay un mundo cargado** en modo Opuesto solo se cumple en los menús principales.

**Administrar requisitos** muestra el modo y el valor de cada requisito.

## Valores

- Los valores admiten [marcadores de posición](/placeholders) y tus [variables](/variables#showing-variables-in-text), como `$$coins`. FancyMenu los sustituye cada vez que comprueba el requisito.
- Muchos campos de valor sugieren opciones mientras escribes, como biomas, ID de mods, idiomas o nombres de tus variables. Haz clic en una sugerencia o pulsa `Tab`.
- Los requisitos con un valor sencillo abren un editor de texto de una línea. El título indica qué debes escribir, por ejemplo, **ID del elemento de destino**.

## Administrar requisitos

Haz clic derecho en la lista, en un requisito o en un grupo de **Administrar requisitos** para acceder a estas opciones:

| Opción | Atajo | Qué hace |
|---|---|---|
| **Añadir requisito** | `A` | Añade un requisito. |
| **Añadir grupo** | `G` | Añade un grupo (consulta más abajo). |
| **Editar requisito** | `Enter` o doble clic | Abre el selector de requisitos con su tipo, modo y valor. |
| **Eliminar requisito** / **Eliminar grupo** | `Delete` | Lo elimina. |
| **Deshacer** / **Rehacer** | `Ctrl + Z` / `Ctrl + Y` | Deshace y rehace los cambios de esta ventana. |
| **Exportar requisitos para IA** | | Exporta todos los requisitos de la ventana para un [chat de IA](/export-for-ai), incluidos los cambios que no hayas guardado. |

`Arriba` y `Abajo` seleccionan el requisito anterior o siguiente. **Listo** (`Ctrl + S`) guarda los cambios; **Cancelar** descarta todos los cambios realizados en la ventana. En macOS, usa `Cmd` en lugar de `Ctrl`.

Si seleccionas varios elementos, **Requisitos de carga** modifica los requisitos de todos ellos. Si tienen requisitos distintos, FancyMenu te lo pregunta primero, ya que se sustituirán todos.

# Combinar requisitos

Deben cumplirse todos los requisitos de **Administrar requisitos**. Para indicar «esto O aquello», usa un grupo.

Un grupo funciona como un único requisito:

- Modo **Y**: deben cumplirse todas las condiciones del grupo. Los grupos nuevos usan este modo.
- Modo **O**: basta con que se cumpla una condición del grupo.

1. Haz clic derecho en la lista y selecciona **Añadir grupo**, o pulsa `G`. El grupo recibe un nombre como `group_1`.
2. Haz clic derecho en el grupo y selecciona **Modo del grupo** para alternar entre **Y** y **O**.
3. Haz clic en **Editar requisitos del grupo** o haz doble clic en el grupo. Se abrirá una ventana similar a **Administrar requisitos**.
4. Añade los requisitos del grupo y haz clic en **Listo**.

Por ejemplo, para mostrar un saludo navideño en diciembre o cuando el jugador haya activado `xmas_lights`, crea un grupo en modo O con **El mes de la hora real es** `12` y **El valor de la variable (variable de FM) es** para la variable `xmas_lights` con el valor `on`.

<img width="800" alt="Añadir un grupo en Administrar requisitos, cambiarlo al modo O y añadirle El mes de la hora real es y El valor de la variable (variable de FM) es" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_group.gif?raw=true">

- Los grupos pueden contener otros grupos para crear condiciones como «(A y B) o (C y D)». El título de la ventana indica dónde estás, por ejemplo, `Editar grupo: group_1 › group_2`.
- **Editar identificador del grupo** cambia el nombre de un grupo. Cada nombre solo se puede usar una vez, también dentro de los grupos.
- Un grupo vacío en modo **O** nunca se cumple.

# Requisitos para todo el diseño

Los requisitos para todo el diseño determinan si se carga un diseño completo. Úsalos para crear una versión nocturna de la pantalla de título, un diseño por idioma o un diseño que solo se muestre en el modo de un jugador.

Haz clic derecho en el fondo del editor y selecciona **Requisitos de carga [para todo el diseño]**. También está en **barra de menú -> Diseño -> Propiedades del diseño**.

- Si el resultado cambia mientras el menú está abierto, FancyMenu vuelve a crear la pantalla con los diseños que se cumplen en ese momento.
- También funcionan con los [diseños universales](/universal-layouts).
- Para activar y desactivar un diseño con un botón, coloca el botón en otro diseño. Consulta [Activar y desactivar diseños](/element-visibility#turning-layouts-on-and-off).

# Información útil

- Los requisitos relativos al mundo y al jugador nunca se cumplen si no hay un mundo cargado, por ejemplo, en los menús principales.
- Los requisitos relativos a elementos, el cursor, los inventarios, el jugador y el mundo no funcionan en un [Ticker](/elements#ticker) si **Asíncrono** está activado. En ese caso, FancyMenu muestra un error con el nombre del requisito.
- Se omiten los requisitos de los complementos que hayas eliminado. Al guardar el diseño en el editor, se eliminan definitivamente.
- **barra de menú -> Personalización -> Ajustes -> Duración de la caché de requisitos [ms]** reutiliza durante unos milisegundos los resultados de los requisitos, lo que acelera los diseños grandes. `0` desactiva esta opción y es el valor predeterminado. La caché puede hacer que los scripts de acciones y los cambios rápidos se comporten de forma inesperada.

# Todos los requisitos

Los requisitos están ordenados igual que en el selector de requisitos: primero por categoría y luego por nombre. Los requisitos sin categoría aparecen al final del selector y aquí, en [Otros](#otros).

## Interfaz gráfica

### El tipo de cursor activo es

**Identificador:** `is_active_cursor_type`

Se cumple cuando el cursor tiene una forma concreta, como **Mano señaladora** sobre un enlace o **Cursor de escritura** sobre un campo de texto.

- Valor: haz clic en **Tipo de cursor** para elegir **Normal**, **Cursor de escritura**, **Mira**, **Mano señaladora**, **Redimensionar horizontalmente**, **Redimensionar verticalmente**, **Redimensionar en diagonal NO-SE**, **Redimensionar en diagonal NE-SO**, **Redimensionar en todas direcciones** o **No permitido**.

### Hay algún botón bajo el cursor

**Identificador:** `fancymenu_visibility_requirement_is_any_button_hovered`

Se cumple cuando el cursor está sobre cualquier botón visible, ya sea de Vanilla o personalizado.

### Hay algún elemento bajo el cursor

**Identificador:** `fancymenu_visibility_requirement_is_any_element_hovered`

Se cumple cuando el cursor está sobre cualquier elemento visible, no solo sobre botones.

### Hay alguna pantalla abierta

**Identificador:** `is_any_screen_open`

Se cumple cuando hay algún menú abierto, como el menú de pausa o el inventario. No se cumple mientras juegas sin un menú abierto.

### El botón está activo

**Identificador:** `fancymenu_visibility_requirement_is_button_active`

Se cumple cuando se puede hacer clic en un botón.

- Valor: el [ID del elemento](/element-identifiers) del botón. Haz clic derecho en él desde el editor y selecciona **Copiar ID del elemento**.

### La barra de menú de personalización está visible

**Identificador:** `is_customization_menu_bar_visible`

Se cumple cuando se muestra la barra de menú de FancyMenu. No se cumple en el modo de modpack ni cuando la barra de menú está desactivada.

### El elemento está seleccionado

**Identificador:** `is_element_focused`

Se cumple cuando un elemento tiene el foco. Los botones y los deslizadores lo reciben al hacer clic en ellos o al seleccionarlos con las teclas de flecha o `Tab`. Seleccionarlo con el teclado no cuenta como pasar el cursor por encima. Por eso, si quieres que funcione para quienes usan el teclado, incluye este requisito y **El cursor está sobre un elemento** en un [grupo O](#combinar-requisitos).

- Valor: el [ID del elemento](/element-identifiers), como `mc_titlescreen_multiplayer_button`.

### El cursor está sobre un elemento

**Identificador:** `fancymenu_visibility_requirement_is_element_hovered`

Se cumple cuando el cursor está sobre un elemento. El elemento debe estar visible.

- Valor: el [ID del elemento](/element-identifiers), como `mc_titlescreen_multiplayer_button` para el botón Multijugador de la pantalla de título. Para obtenerlo, haz clic derecho en un elemento del editor y selecciona **Copiar ID del elemento**.

### El elemento desplazable ha llegado al final

**Identificador:** `is_scroll_area_scrolled_to_end`

Se cumple cuando se ha desplazado hasta el final de un [área desplazable](/scrollable-areas) o de un elemento de texto. Los elementos que no tienen contenido para desplazar se consideran situados al final. Es útil para un botón **Aceptar** que solo funcione cuando el jugador haya leído las normas desplazándose hasta el final.

- Valor: el [ID del elemento](/element-identifiers) del área desplazable o del elemento de texto.

### La escala de la interfaz gráfica es

**Identificador:** `fancymenu_loading_requirement_is_gui_scale`

Se cumple cuando la escala de la interfaz gráfica de Minecraft coincide.

- Valor: un número como `2` para esa escala exacta, `>2` para un valor superior a 2 o `<4` para uno inferior a 4. También se admiten decimales, como `<3.5`.
- Separa las distintas condiciones con comas. Si son números sin operador, debe coincidir uno de ellos, como `2,3`. Deben cumplirse todas las condiciones con `>` y `<`, como `>1,<4`.

### La tecla está pulsada

**Identificador:** `is_key_pressed`

Se cumple mientras se mantiene pulsada una tecla. Para ejecutar acciones una sola vez por pulsación, usa el activador [**Al pulsar una tecla**](/listeners#on-keyboard-key-pressed).

- Valor: haz clic en **Cambiar tecla** dentro de **Selección de tecla** y pulsa la tecla.

### El diseño está activado

**Identificador:** `fancymenu_visibility_requirement_is_layout_enabled`

Se cumple mientras un diseño esté activado.

- Valor: el nombre del diseño, como `winter_title_screen`.

### La superposición de depuración de MC está activada

**Identificador:** `is_debug_overlay_enabled`

Se cumple mientras se muestra la pantalla de depuración de F3. No se cumple cuando se oculta la interfaz con F1.

### El modo de modpack está activado

**Identificador:** `is_modpack_mode_enabled`

Se cumple cuando el modo de modpack de FancyMenu está activado.

### El título de la pantalla es

**Identificador:** `is_menu_title`

Se cumple cuando coincide el título de la pantalla abierta, como «Opciones» o «Menú del juego». Se refiere al título que ven los jugadores, no al [identificador de la pantalla](/screen-identifiers).

- Valor: el texto del título o su clave de traducción, como `options.title`. La ventana de valores muestra ambos para la pantalla que estás editando y sugiere claves de traducción.
- Las claves de traducción funcionan en todos los idiomas. El texto del título debe coincidir exactamente.

## Hora real

Estos requisitos consultan el reloj del ordenador del jugador. Separa los distintos valores con comas: basta con que coincida uno.

### El día de la hora real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_day`

Se cumple en determinados días del mes.

- Valor: de `1` a `31`, como `24,25,26`.

### La hora de la hora real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_hour`

Se cumple durante determinadas horas.

- Valor: de `0` a `23`, como `20,21,22,23` para la tarde-noche.

### El minuto de la hora real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_minute`

Se cumple durante determinados minutos de la hora.

- Valor: de `0` a `59`.

### El mes de la hora real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_month`

Se cumple en determinados meses.

- Valor: de `1` (enero) a `12` (diciembre), como `12` para Navidad.

### El segundo de la hora real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_second`

Se cumple durante determinados segundos del minuto.

- Valor: de `0` a `59`.

### El día de la semana de la hora real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_week_day`

Se cumple en determinados días de la semana.

- Valor: de `1` (domingo) a `7` (sábado), como `1,7` para el fin de semana.

### El año de la hora real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_year`

Se cumple en determinados años.

- Valor: el año completo, como `2027`.

## Sistema

### El archivo o la carpeta existe

**Identificador:** `fancymenu_loading_requirement_file_exists`

Se cumple cuando existe un archivo o una carpeta.

- Valor: una ruta de la carpeta del juego, como `config/mymodpack/welcome_seen.txt`. Las rutas que empiezan por `.minecraft/` apuntan a la carpeta `.minecraft` predeterminada.

### Hay conexión a Internet

**Identificador:** `is_internet_connection_available`

Se cumple cuando el ordenador tiene conexión. FancyMenu lo comprueba de vez en cuando en segundo plano.

### El sistema operativo es Linux

**Identificador:** `fancymenu_loading_requirement_is_os_linux`

Se cumple en Linux. Técnicamente, en cualquier sistema que no sea Windows ni macOS.

### El sistema operativo es macOS

**Identificador:** `fancymenu_loading_requirement_is_os_macos`

Se cumple en macOS.

### El sistema operativo es Windows

**Identificador:** `fancymenu_loading_requirement_is_os_windows`

Se cumple en Windows.

### El planificador está en ejecución

**Identificador:** `fancymenu_visibility_requirement_is_scheduler_running`

Se cumple mientras se ejecuta un [planificador](/schedulers).

- Valor: el identificador del planificador, como `my_scheduler`.

## Ventana

El tamaño de la ventana se mide en píxeles reales de la ventana del juego, no en píxeles de la interfaz. La descripción del requisito muestra el tamaño actual.

### Está en pantalla completa

**Identificador:** `fancymenu_loading_requirement_is_fullscreen`

Se cumple cuando el juego está en pantalla completa.

### La altura de la ventana es

**Identificador:** `fancymenu_loading_requirement_is_window_height`

Se cumple cuando la ventana tiene una altura determinada.

- Valor: la altura, como `1080`. Separa varias alturas con comas: basta con que coincida una.

### La altura de la ventana es superior a

**Identificador:** `fancymenu_loading_requirement_is_window_height_bigger_than`

Se cumple cuando la ventana supera una altura determinada.

- Valor: la altura, como `1080`.

### La anchura de la ventana es

**Identificador:** `fancymenu_loading_requirement_is_window_width`

Se cumple cuando la ventana tiene una anchura determinada.

- Valor: la anchura, como `1920`. Separa varias anchuras con comas: basta con que coincida una.

### La anchura de la ventana es superior a

**Identificador:** `fancymenu_loading_requirement_is_window_width_bigger_than`

Se cumple cuando la ventana supera una anchura determinada.

- Valor: la anchura, como `1920`.

## Mundo

Estos requisitos nunca se cumplen si no hay un mundo cargado. **El jugador está en una estructura** y **Está en la zona activa de una incursión** requieren que FancyMenu esté instalado en el servidor. En un mundo de un jugador, siempre funcionan.

### El jugador tiene corazones de absorción

**Identificador:** `has_player_absorption_hearts`

Se cumple mientras el jugador tenga corazones dorados de absorción.

### El jugador tiene un nivel de permisos

**Identificador:** `fancymenu_loading_requirement_has_player_permission_level`

Se cumple cuando el jugador tiene al menos un nivel determinado de permisos en el mundo o el servidor, por ejemplo, si es operador.

- Valor: de `0` a `4`. El nivel `0` siempre se cumple; el nivel `2` basta para usar comandos como `/gamemode`, y el comando `/op` otorga el nivel `4`.

### Está en el modo Aventura

**Identificador:** `fancymenu_visibility_requirement_is_adventure`

Se cumple cuando el jugador está en el modo Aventura.

### Hay algún efecto activo

**Identificador:** `is_any_effect_active`

Se cumple mientras el jugador tenga algún efecto, como Velocidad o Veneno.

### La fuerza del ataque está reducida

**Identificador:** `is_attack_strength_weakened`

Se cumple cuando el ataque del jugador no está completamente cargado. Es entonces cuando se muestra el indicador de ataque.

### El bloque o el objeto pertenece a una etiqueta

**Identificador:** `is_in_tag`

Se cumple cuando un bloque o un objeto pertenece a una etiqueta, como `minecraft:logs` o `c:tools`. Las etiquetas solo existen mientras hay un mundo cargado.

- Valor: haz clic en **Tipo de etiqueta** para elegir **Bloque** u **Objeto**; después, introduce la **Clave del bloque u objeto** y la **Etiqueta**. Ambos campos sugieren valores. El `#` delante de la etiqueta es opcional.
- La clave funciona muy bien con variables de activadores, como `$$block_key`. Por ejemplo, una condición IF en el script del activador [**Al romper un bloque**](/listeners#on-block-broke) puede mostrar una notificación emergente solo para los troncos.

### La perspectiva de la cámara es

**Identificador:** `is_camera_perspective`

Se cumple cuando la cámara está en una perspectiva determinada (F5).

- Valor: haz clic en el botón para elegir **Primera persona**, **Tercera persona** o **Vista frontal**.

### Hace buen tiempo

**Identificador:** `is_clear_weather`

Se cumple cuando no llueve ni hay tormenta.

### Está en el modo Creativo

**Identificador:** `fancymenu_visibility_requirement_is_creative`

Se cumple cuando el jugador está en el modo Creativo.

### El cursor sostiene un objeto del inventario

**Identificador:** `is_cursor_holding_inventory_item`

Se cumple cuando el cursor lleva un objeto en una pantalla de inventario.

### La dificultad es

**Identificador:** `is_difficulty`

Se cumple cuando el mundo tiene una dificultad determinada.

- Valor: `peaceful`, `easy`, `normal` o `hard`.

### El efecto está activo

**Identificador:** `is_effect_active`

Se cumple mientras el jugador tenga un efecto determinado.

- Valor: la clave del efecto, como `minecraft:speed`. El campo sugiere efectos cuando estás en un mundo.

### Hay una entidad cerca

**Identificador:** `is_entity_nearby`

Se cumple cuando hay cerca del jugador una entidad de un tipo determinado.

- Valor: la **clave de registro de la entidad**, como `minecraft:creeper`, y el **radio de comprobación en bloques**, como `10`. El campo de la clave sugiere entidades cuando estás en un mundo.

### El modo de juego es

**Identificador:** `is_gamemode`

Se cumple cuando el jugador está en un modo de juego determinado.

- Valor: `survival`, `creative`, `adventure` o `spectator`.

### Es un mundo extremo

**Identificador:** `is_hardcore`

Se cumple en los mundos extremos.

### La ranura de la barra rápida seleccionada es

**Identificador:** `is_hotbar_slot_active`

Se cumple cuando está seleccionada una ranura determinada de la barra rápida.

- Valor: de `0` (la ranura de la izquierda) a `8`.

### Está en la zona activa de una incursión

**Identificador:** `is_in_active_raid_area`

Se cumple cuando el jugador está en la zona de una incursión, donde aparece la barra de incursión. Requiere que FancyMenu esté instalado en el servidor.

### La ranura del inventario está ocupada

**Identificador:** `is_inventory_slot_filled`

Se cumple cuando hay un objeto en una ranura del inventario del jugador.

- Valor: el número de la ranura. De `0` a `8` corresponde a la barra rápida; de `9` a `35`, al resto del inventario.

### El cursor está sobre un objeto del inventario

**Identificador:** `is_item_hovered_in_inventory`

Se cumple cuando el cursor está sobre un objeto en una pantalla de inventario, como el inventario del jugador o un cofre.

### Está en el modo multijugador

**Identificador:** `fancymenu_loading_requirement_is_multiplayer`

Se cumple cuando el jugador está en un servidor.

### El jugador vuela en el modo Creativo

**Identificador:** `is_player_creative_flying`

Se cumple cuando el jugador vuela en el modo Creativo.

### El jugador vuela con élitros

**Identificador:** `is_player_flying_with_elytra`

Se cumple cuando el jugador planea con élitros.

### El jugador está completamente congelado

**Identificador:** `is_player_fully_frozen`

Se cumple cuando el jugador está completamente congelado por la nieve en polvo y aparecen corazones congelados en la barra de salud.

### El jugador está en un bioma

**Identificador:** `is_player_in_biome`

Se cumple cuando el jugador está en un bioma determinado.

- Valor: la clave del bioma, como `minecraft:birch_forest`. El campo sugiere biomas cuando estás en un mundo.

### El jugador está en una dimensión

**Identificador:** `is_player_in_dimension`

Se cumple cuando el jugador está en una dimensión determinada.

- Valor: la clave de la dimensión: `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end` o la de una dimensión de un mod. El campo sugiere dimensiones cuando estás en un mundo.

### El jugador está en un fluido

**Identificador:** `is_player_in_fluid`

Se cumple cuando el jugador está en cualquier fluido, como agua o lava.

### El jugador está en lava

**Identificador:** `is_player_in_lava`

Se cumple cuando el jugador está en lava.

### El jugador está en nieve en polvo

**Identificador:** `is_player_in_powder_snow`

Se cumple cuando el jugador está en nieve en polvo.

### El jugador está en una estructura

**Identificador:** `is_player_in_structure`

Se cumple cuando el jugador está dentro de una estructura determinada. Requiere que FancyMenu esté instalado en el servidor.

- Valor: la clave de la estructura, como `minecraft:village_plains`. El campo sugiere estructuras cuando estás en un mundo.

### El jugador está en el agua

**Identificador:** `is_player_in_water`

Se cumple cuando el jugador está en el agua, aunque solo parcialmente.

### El jugador está saltando o cayendo

**Identificador:** `is_player_jumping`

Se cumple cuando el jugador está en el aire. No cuenta si está nadando, dentro de un fluido, volando con élitros, durmiendo o reptando.

### El jugador es zurdo

**Identificador:** `is_left_handed`

Se cumple cuando la opción «Mano principal» de las opciones de personalización de aspectos de Minecraft está configurada como «Izquierda».

### El jugador está envenenado

**Identificador:** `is_player_poisoned`

Se cumple cuando el jugador tiene el efecto Veneno y aparecen corazones envenenados en la barra de salud.

### El jugador monta una entidad con salud

**Identificador:** `is_player_riding_entity_with_health`

Se cumple cuando el jugador monta una entidad viva, como un caballo o un cerdo. No cuenta si monta en una barca o una vagoneta.

### El jugador monta una entidad o un vehículo

**Identificador:** `is_player_riding_entity`

Se cumple cuando el jugador monta cualquier cosa, como un caballo, una barca o una vagoneta.

### El jugador monta una entidad que puede saltar

**Identificador:** `is_player_riding_jumpable_entity`

Se cumple cuando el jugador monta una entidad que puede saltar, como un caballo.

### El jugador corre

**Identificador:** `is_player_running`

Se cumple cuando el jugador esprinta.

### El jugador está agachado

**Identificador:** `is_player_sneaking`

Se cumple cuando el jugador se agacha.

### El jugador está nadando

**Identificador:** `is_player_swimming`

Se cumple cuando el jugador nada.

### El jugador está bajo el agua

**Identificador:** `is_player_under_water`

Se cumple cuando la cabeza del jugador está bajo el agua.

### El jugador está usando un objeto

**Identificador:** `is_player_using_item`

Se cumple cuando el jugador usa un objeto, por ejemplo, al comer, beber una poción o tensar un arco.

### El jugador lleva una calabaza

**Identificador:** `is_player_wearing_pumpkin`

Se cumple cuando el jugador lleva una calabaza tallada en la cabeza.

### El jugador está debilitado

**Identificador:** `is_player_withered`

Se cumple cuando el jugador tiene el efecto Debilidad y aparecen corazones debilitados en la barra de salud.

### Está lloviendo

**Identificador:** `is_raining`

Se cumple cuando llueve donde está el jugador.

### Está en el modo de un jugador

**Identificador:** `fancymenu_loading_requirement_is_singpleplayer`

Se cumple cuando el jugador está en un mundo de un jugador.

### Está nevando

**Identificador:** `is_snowing`

Se cumple cuando nieva donde está el jugador.

### Está en el modo Espectador

**Identificador:** `fancymenu_visibility_requirement_is_spectator`

Se cumple cuando el jugador está en el modo Espectador.

### Está en el modo Supervivencia

**Identificador:** `fancymenu_visibility_requirement_is_survival`

Se cumple cuando el jugador está en el modo Supervivencia.

### Hay una tormenta eléctrica

**Identificador:** `is_thundering`

Se cumple durante una tormenta eléctrica.

### Hay un mundo cargado

**Identificador:** `fancymenu_loading_requirement_is_world_loaded`

Se cumple cuando el jugador está en un mundo, ya sea de un jugador o multijugador.

### El jugador estaba en nieve en polvo

**Identificador:** `was_player_in_powder_snow`

Se cumple cuando el jugador ha estado en nieve en polvo hace un momento.

## Otros

### El idioma del juego es

**Identificador:** `fancymenu_loading_requirement_is_language`

Se cumple cuando Minecraft usa un idioma determinado.

- Valor: el código del idioma, como `en_us` o `de_de`. El campo sugiere todos los idiomas.

### El mod está cargado

**Identificador:** `fancymenu_loading_requirement_is_mod_loaded`

Se cumple cuando hay determinados mods instalados.

- Valor: el ID del mod, como `jei`. El campo sugiere los ID de tus mods. Separa varios ID con comas: todos deben estar instalados. `optifine` comprueba si está instalado OptiFine.

### Es un número

**Identificador:** `fancymenu_visibility_requirement_is_number`

Compara dos números. Introduce marcadores de posición o variables en los campos, como `$$coins`.

- **Modo de comparación**: **Igual a**, **Mayor que**, **Menor que**, **Mayor o igual que** o **Menor o igual que**.
- **Número**: el número que se va a comprobar, como `$$coins`.
- **Comparar con el número**: el número con el que se compara, como `100`.

Se admiten decimales, como `2.5`. Si un campo no contiene un número, el requisito nunca se cumple.

### El paquete de recursos está activado

**Identificador:** `is_resource_pack_enabled`

Se cumple cuando un paquete de recursos está activado.

- Valor: el nombre del paquete tal como aparece en la pantalla Paquetes de recursos, como `Programmer Art`, o su ID. No distingue entre mayúsculas y minúsculas.

### Rinku está cargado

**Identificador:** `is_rinku_loaded`

Se cumple cuando está instalado el mod [Rinku](https://modrinth.com/mod/rinku). Lo necesitan el [elemento Navegador](/elements#browser) y los antiguos [tipos de vídeo basados en Rinku](/video#requirements).

### La IP del servidor es

**Identificador:** `fancymenu_visibility_requirement_is_server_ip`

Se cumple cuando el jugador está en un servidor determinado.

- Valor: la dirección del servidor, como `play.example.net`. Si indicas un puerto, como `play.example.net:25566`, también debe coincidir el puerto.

### El servidor está en línea

**Identificador:** `fancymenu_loading_requirement_is_server_online`

Se cumple cuando un servidor está en línea. FancyMenu le envía pings en segundo plano cada 30 segundos aproximadamente, así que puede tardar un poco después de iniciar el juego.

- Valor: la dirección del servidor, como `play.example.net`.

### Es un texto

**Identificador:** `fancymenu_visibility_requirement_is_text`

Compara dos textos. Introduce marcadores de posición o variables en los campos, como `$$key_name`.

- **Modo de comparación**: **Igual a**, **Contiene**, **Empieza por** o **Termina en**.
- **Texto**: el texto que se va a comprobar.
- **Comparar con el texto**: el texto con el que se compara.

Distingue entre mayúsculas y minúsculas.

### El valor de la variable (variable de FM) es

**Identificador:** `fancymenu_visibility_requirement_is_variable_value`

Se cumple cuando una de tus [variables](/variables) tiene un valor determinado.

- **Nombre de la variable**: el nombre de la variable, sin `$$`. El campo sugiere tus variables.
- **Valor de la variable que se va a comprobar**: el valor, como `on`. Debe coincidir con el valor completo y distingue entre mayúsculas y minúsculas.

Nunca se cumple si la variable no existe. En el caso de una variable de lista, compara la matriz JSON de todas las entradas, como `["apple","banana"]`. Para comprobar una sola entrada, usa **La lista contiene la entrada (variable de FM)**.

### La lista contiene la entrada (variable de FM)

**Identificador:** `list_contains_entry`

Se cumple cuando una [variable de lista](/variables#text-and-list-variables) contiene una entrada determinada.

- **Nombre de la variable de lista**: el nombre de la lista, sin `$$`. El campo sugiere tus variables de lista y te avisa si escribes el nombre de una variable de texto.
- **Entrada que se va a buscar**: la entrada. Debe coincidir con una entrada completa, no solo con una parte.
- **Ignorar mayúsculas y minúsculas**: si está activado, `Apple` también coincide con `apple`.

Nunca se cumple si la lista no existe.

### El botón del ratón está pulsado

**Identificador:** `mouse_click`

Se cumple mientras se mantiene pulsado un botón del ratón. Para ejecutar acciones una sola vez por clic, usa el activador [**Al hacer clic con el ratón**](/listeners#on-mouse-button-clicked).

- Valor: `left` o `right`.

### Solo una vez por sesión

**Identificador:** `once_per_session`

Se cumple la primera vez que se comprueba y no vuelve a cumplirse hasta que se reinicia el juego. Cada copia de este requisito funciona por separado.

Para los elementos que solo deban aparecer una vez por sesión de juego, es más fácil usar la opción **Cargar una vez por sesión** de los elementos, en [Visibilidad de los elementos](/element-visibility#load-once-per-session): los elementos permanecen visibles hasta que se abre una pantalla nueva.
