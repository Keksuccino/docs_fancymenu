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

- mostrar un [elemento](/elements) solo en ciertos momentos,
- cargar un diseño completo solo en ciertos momentos,
- permitir hacer clic en botones, controles deslizantes y casillas solo en ciertos momentos,
- ejecutar partes de un [script de acciones](/action-scripts) solo en ciertos momentos.

FancyMenu comprueba los requisitos constantemente mientras hay un menú abierto, así que los elementos aparecen, se ocultan o cambian de inmediato. Este cuadro de información solo aparece cuando el cursor está sobre «Multijugador»:

<img width="800" alt="Al pasar el cursor sobre el botón Multijugador de la pantalla de título, aparece un cuadro de información con la dirección de un servidor a un lado" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_hover.gif?raw=true">

# Dónde encontrarlos

| Dónde | Qué hacen los requisitos |
|---|---|
| Haz clic derecho en un elemento -> **Requisitos de carga** | El elemento solo aparece mientras se cumplan. También funciona con los [elementos de Vanilla](/vanilla-elements). |
| Haz clic derecho en el fondo del editor -> **Requisitos de carga [para todo el diseño]** | El diseño completo solo se carga mientras se cumplan. Consulta [Requisitos para todo el diseño](#requisitos-para-todo-el-diseño). |
| Haz clic derecho en un botón, control deslizante o casilla -> **Estado activo del control** | Solo se puede hacer clic mientras se cumplan. De lo contrario, aparece en gris. Los botones de Vanilla también tienen esta opción. |
| IF, ELSE-IF y WHILE en los [scripts de acciones](/action-scripts#statements) | Las acciones que contienen solo se ejecutan mientras se cumplan. |

En el editor de diseños, los elementos siempre aparecen para que puedas editarlos. Los requisitos de los elementos funcionan fuera del editor.

> [!TIP]
> [Visibilidad de los elementos](/element-visibility) muestra otras formas de mostrar y ocultar elementos, como usar retrasos, hacerlos aparecer gradualmente y alternar su visibilidad con un botón.

# Agregar un requisito

<img width="800" alt="Se copia el ID del botón Multijugador y luego se agrega al cuadro de información el requisito El elemento está bajo el cursor con ese ID, en Administrar requisitos" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_add.gif?raw=true">

1. Haz clic derecho en el elemento y selecciona **Requisitos de carga**. Se abrirá **Administrar requisitos**.
2. Haz clic derecho en la lista vacía y selecciona **Agregar requisito**, o presiona `A`.
3. Haz clic en una categoría de **Requisitos disponibles** o empieza a escribir para buscar por nombre y descripción. **Descripción del requisito** explica el requisito seleccionado.
4. Haz clic en **Siguiente paso** para establecer su valor. Los requisitos que no necesitan un valor muestran **Listo** en su lugar. También puedes hacer doble clic en un requisito para hacer lo mismo.
5. Ingresa el valor y haz clic en **Listo**. Por ejemplo, **El elemento está bajo el cursor** necesita el ID del elemento. Haz clic derecho en un elemento y selecciona **Copiar ID del elemento** para obtenerlo.
6. Haz clic en **Listo** en **Administrar requisitos**.

## Modo del requisito

El botón **Modo del requisito** del selector de requisitos permite alternar entre:

- **Normal**: se cumple cuando la condición es verdadera.
- **Opuesto**: se cumple cuando la condición NO es verdadera. Por ejemplo, **Hay un mundo cargado** en modo Opuesto solo se cumple en los menús principales.

**Administrar requisitos** muestra el modo y el valor de cada requisito.

## Valores

- Los valores admiten [marcadores de posición](/placeholders) y tus [variables](/variables#showing-variables-in-text), como `$$coins`. FancyMenu los reemplaza cada vez que comprueba el requisito.
- Muchos campos de valor sugieren opciones mientras escribes, como biomas, IDs de mods, idiomas o los nombres de tus variables. Haz clic en una sugerencia o presiona `Tab`.
- Los requisitos con un valor sencillo abren un editor de texto de una línea. El título indica qué debes escribir, como **ID del elemento objetivo**.

## Administrar requisitos

Haz clic derecho en la lista, en un requisito o en un grupo de **Administrar requisitos** para ver estas opciones:

| Opción | Atajo | Qué hace |
|---|---|---|
| **Agregar requisito** | `A` | Agrega un requisito. |
| **Agregar grupo** | `G` | Agrega un grupo (consulta la sección siguiente). |
| **Editar requisito** | `Enter` o doble clic | Abre el selector de requisitos con el tipo, el modo y el valor del requisito. |
| **Eliminar requisito** / **Eliminar grupo** | `Delete` | Lo elimina. |
| **Deshacer** / **Rehacer** | `Ctrl + Z` / `Ctrl + Y` | Deshace y rehace los cambios de esta ventana. |
| **Exportar requisitos para IA** | | Exporta todos los requisitos de la ventana para un [chat con IA](/export-for-ai), incluidos los cambios sin guardar. |

`Up` y `Down` seleccionan el requisito anterior o siguiente. **Listo** (`Ctrl + S`) guarda los cambios; **Cancelar** descarta todo lo que hayas cambiado en la ventana. En macOS, usa `Cmd` en lugar de `Ctrl`.

Si seleccionas varios elementos, **Requisitos de carga** cambia los requisitos de todos. Si tienen requisitos distintos, FancyMenu te pregunta antes, porque se reemplazarán todos.

# Combinar requisitos

Se deben cumplir todos los requisitos de **Administrar requisitos**. Para indicar «esto O aquello», usa un grupo.

Un grupo funciona como un solo requisito:

- Modo **Y**: se deben cumplir todos los requisitos del grupo. Los grupos nuevos comienzan en este modo.
- Modo **O**: basta con que se cumpla uno de los requisitos del grupo.

1. Haz clic derecho en la lista y selecciona **Agregar grupo**, o presiona `G`. El grupo recibe un nombre como `group_1`.
2. Haz clic derecho en el grupo y selecciona **Modo del grupo** para alternar entre **Y** y **O**.
3. Selecciona **Editar requisitos del grupo** o haz doble clic en el grupo. Se abrirá una ventana similar a **Administrar requisitos**.
4. Agrega los requisitos del grupo y haz clic en **Listo**.

Por ejemplo, para mostrar un saludo navideño en diciembre o cuando el jugador active `xmas_lights`, crea un grupo O con **El mes en tiempo real es** `12` y **El valor de la variable es (variable de FM)** para la variable `xmas_lights` con el valor `on`.

<img width="800" alt="Se agrega un grupo en Administrar requisitos, se cambia a O y se añaden los requisitos El mes en tiempo real es y El valor de la variable es (variable de FM)" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_group.gif?raw=true">

- Los grupos pueden contener otros grupos para crear condiciones como «(A y B) o (C y D)». El título de la ventana indica dónde estás, por ejemplo, `Editar grupo: group_1 › group_2`.
- **Editar identificador del grupo** cambia el nombre de un grupo. Cada nombre solo se puede usar una vez, incluso dentro de los grupos.
- Un grupo vacío en modo **O** nunca se cumple.

# Requisitos para todo el diseño

Los requisitos para todo el diseño determinan si se carga un diseño completo. Úsalos para crear una versión nocturna de la pantalla de título, un diseño para cada idioma o un diseño que solo aparezca en el modo de un jugador.

Haz clic derecho en el fondo del editor y selecciona **Requisitos de carga [para todo el diseño]**. También está en **barra de menú -> Diseño -> Propiedades del diseño**.

- Si el resultado cambia mientras el menú está abierto, FancyMenu vuelve a generar la pantalla con los diseños que se cumplan en ese momento.
- También funcionan con los [diseños universales](/universal-layouts).
- Para activar y desactivar un diseño con un botón, coloca el botón en otro diseño. Consulta [Activar y desactivar diseños](/element-visibility#turning-layouts-on-and-off).

# Información útil

- Los requisitos de mundo y jugador nunca se cumplen si no hay un mundo cargado, como sucede en los menús principales.
- Los requisitos relacionados con elementos, el cursor, los inventarios, el jugador y el mundo no funcionan en un [Ticker](/elements#ticker) si **Asíncrono** está activado. En ese caso, FancyMenu muestra un error con el nombre del requisito.
- Se omiten los requisitos de los complementos que hayas eliminado. Al guardar el diseño en el editor, se eliminan definitivamente.
- **barra de menú -> Personalización -> Ajustes -> Duración del almacenamiento en caché de requisitos [ms]** reutiliza los resultados de los requisitos durante cierta cantidad de milisegundos, lo que agiliza los diseños grandes. El valor predeterminado es `0`, que desactiva esta opción. El almacenamiento en caché puede hacer que los scripts de acciones y los cambios rápidos tengan resultados inesperados.

# Todos los requisitos

Los requisitos están ordenados igual que en el selector: primero por categoría y luego por nombre. Los requisitos sin categoría aparecen al final del selector y en la sección [Otros](#otros) de esta página.

## Interfaz

### El tipo de cursor activo es

**Identificador:** `is_active_cursor_type`

Se cumple cuando el cursor tiene una forma determinada, como **Mano señalando** sobre un enlace o **Cursor de escritura** sobre un campo de texto.

- Valor: haz clic en **Tipo de cursor** para elegir **Normal**, **Cursor de escritura**, **Mira**, **Mano señalando**, **Cambiar tamaño horizontal**, **Cambiar tamaño vertical**, **Cambiar tamaño diagonal NO-SE**, **Cambiar tamaño diagonal NE-SO**, **Cambiar tamaño en todas direcciones** o **No permitido**.

### Hay algún botón bajo el cursor

**Identificador:** `fancymenu_visibility_requirement_is_any_button_hovered`

Se cumple cuando el cursor está sobre cualquier botón visible, ya sea de Vanilla o personalizado.

### Hay algún elemento bajo el cursor

**Identificador:** `fancymenu_visibility_requirement_is_any_element_hovered`

Se cumple cuando el cursor está sobre cualquier elemento visible, no solo botones.

### Hay alguna pantalla abierta

**Identificador:** `is_any_screen_open`

Se cumple cuando hay un menú abierto, como el menú de pausa o el inventario. No se cumple mientras juegas sin un menú abierto.

### El botón está activo

**Identificador:** `fancymenu_visibility_requirement_is_button_active`

Se cumple cuando se puede hacer clic en un botón.

- Valor: el [ID del elemento](/element-identifiers) del botón. Haz clic derecho en él en el editor y selecciona **Copiar ID del elemento**.

### La barra de menú de personalización está visible

**Identificador:** `is_customization_menu_bar_visible`

Se cumple cuando aparece la barra de menú de FancyMenu. No se cumple en el modo de modpack ni cuando la barra de menú está desactivada.

### El elemento tiene el foco

**Identificador:** `is_element_focused`

Se cumple cuando un elemento tiene el foco. Los botones y controles deslizantes obtienen el foco al hacer clic en ellos o al seleccionarlos con las flechas o `Tab`. Seleccionarlos con el teclado no cuenta como tener el cursor encima, así que agrega este requisito y **El elemento está bajo el cursor** a un [grupo O](#combinar-requisitos) para quienes usan el teclado.

- Valor: el [ID del elemento](/element-identifiers), como `mc_titlescreen_multiplayer_button`.

### El elemento está bajo el cursor

**Identificador:** `fancymenu_visibility_requirement_is_element_hovered`

Se cumple cuando el cursor está sobre un elemento. El elemento debe estar visible.

- Valor: el [ID del elemento](/element-identifiers), como `mc_titlescreen_multiplayer_button` para el botón Multijugador de la pantalla de título. Haz clic derecho en un elemento del editor y selecciona **Copiar ID del elemento** para obtenerlo.

### El elemento se desplazó hasta el final

**Identificador:** `is_scroll_area_scrolled_to_end`

Se cumple cuando un [área desplazable](/scrollable-areas) o un elemento de texto se desplaza hasta abajo. Si un elemento no tiene contenido para desplazar, se considera que ya llegó al final. Es útil para un botón **Aceptar** que solo funciona después de que el jugador haya leído las reglas.

- Valor: el [ID del elemento](/element-identifiers) del área desplazable o del elemento de texto.

### La escala de la interfaz es

**Identificador:** `fancymenu_loading_requirement_is_gui_scale`

Se cumple cuando la escala de la interfaz de Minecraft coincide con el valor indicado.

- Valor: un número como `2` para esa escala exacta, `>2` para una escala mayor que 2 o `<4` para una menor que 4. También se permiten decimales, como `<3.5`.
- Separa varias condiciones con comas. Si son números simples, debe coincidir uno de ellos, como `2,3`. Si son condiciones con `>` o `<`, deben cumplirse todas, como `>1,<4`.

### La tecla está presionada

**Identificador:** `is_key_pressed`

Se cumple mientras se mantenga presionada una tecla. Para ejecutar acciones una sola vez por cada pulsación, usa el listener [**Al presionar una tecla**](/listeners#on-keyboard-key-pressed).

- Valor: haz clic en **Cambiar tecla** dentro de **Selección de teclas** y presiona la tecla.

### El diseño está activado

**Identificador:** `fancymenu_visibility_requirement_is_layout_enabled`

Se cumple cuando un diseño está activado.

- Valor: el nombre del diseño, como `winter_title_screen`.

### La superposición de depuración de Minecraft está activada

**Identificador:** `is_debug_overlay_enabled`

Se cumple cuando aparece la pantalla de depuración de F3. No se cumple cuando la interfaz está oculta con F1.

### El modo de modpack está activado

**Identificador:** `is_modpack_mode_enabled`

Se cumple cuando el modo de modpack de FancyMenu está activado.

### El título de la pantalla es

**Identificador:** `is_menu_title`

Se cumple cuando el título de la pantalla abierta coincide, como «Opciones» o «Menú del juego». Se refiere al título que ven los jugadores, no al [identificador de la pantalla](/screen-identifiers).

- Valor: el texto del título o su clave de traducción, como `options.title`. La ventana de valores muestra ambos para la pantalla que estás editando y sugiere claves de traducción.
- Las claves de traducción funcionan en todos los idiomas. El texto del título debe coincidir exactamente.

## Tiempo real

Estos requisitos consultan el reloj de la computadora del jugador. Separa varios valores con comas: basta con que coincida uno.

### El día en tiempo real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_day`

Se cumple en ciertos días del mes.

- Valor: de `1` a `31`, como `24,25,26`.

### La hora en tiempo real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_hour`

Se cumple durante ciertas horas.

- Valor: de `0` a `23`, como `20,21,22,23` para la noche.

### El minuto en tiempo real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_minute`

Se cumple durante ciertos minutos de la hora.

- Valor: de `0` a `59`.

### El mes en tiempo real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_month`

Se cumple en ciertos meses.

- Valor: `1` (enero) a `12` (diciembre), como `12` para Navidad.

### El segundo en tiempo real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_second`

Se cumple durante ciertos segundos del minuto.

- Valor: de `0` a `59`.

### El día de la semana en tiempo real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_week_day`

Se cumple en ciertos días de la semana.

- Valor: `1` (domingo) a `7` (sábado), como `1,7` para los fines de semana.

### El año en tiempo real es

**Identificador:** `fancymenu_visibility_requirement_is_realtime_year`

Se cumple en ciertos años.

- Valor: el año completo, como `2027`.

## Sistema

### El archivo o la carpeta existe

**Identificador:** `fancymenu_loading_requirement_file_exists`

Se cumple cuando existe un archivo o una carpeta.

- Valor: una ruta dentro de la carpeta del juego, como `config/mymodpack/welcome_seen.txt`. Las rutas que empiezan con `.minecraft/` apuntan a la carpeta `.minecraft` predeterminada.

### Hay conexión a Internet

**Identificador:** `is_internet_connection_available`

Se cumple cuando la computadora está conectada a Internet. FancyMenu comprueba la conexión en segundo plano de vez en cuando.

### El sistema operativo es Linux

**Identificador:** `fancymenu_loading_requirement_is_os_linux`

Se cumple en Linux. Técnicamente, se cumple en cualquier sistema que no sea Windows ni macOS.

### El sistema operativo es macOS

**Identificador:** `fancymenu_loading_requirement_is_os_macos`

Se cumple en macOS.

### El sistema operativo es Windows

**Identificador:** `fancymenu_loading_requirement_is_os_windows`

Se cumple en Windows.

### El programador está en ejecución

**Identificador:** `fancymenu_visibility_requirement_is_scheduler_running`

Se cumple mientras se ejecuta un [programador](/schedulers).

- Valor: el identificador del programador, como `my_scheduler`.

## Ventana

Los tamaños de ventana se indican en píxeles reales de la ventana del juego, no en píxeles de la interfaz. La descripción del requisito muestra el tamaño actual.

### Está en pantalla completa

**Identificador:** `fancymenu_loading_requirement_is_fullscreen`

Se cumple cuando el juego está en pantalla completa.

### La altura de la ventana es

**Identificador:** `fancymenu_loading_requirement_is_window_height`

Se cumple cuando la ventana tiene una altura determinada.

- Valor: la altura, como `1080`. Separa varias alturas con comas: basta con que coincida una.

### La altura de la ventana es mayor que

**Identificador:** `fancymenu_loading_requirement_is_window_height_bigger_than`

Se cumple cuando la ventana tiene una altura mayor que la indicada.

- Valor: la altura, como `1080`.

### El ancho de la ventana es

**Identificador:** `fancymenu_loading_requirement_is_window_width`

Se cumple cuando la ventana tiene un ancho determinado.

- Valor: el ancho, como `1920`. Separa varios anchos con comas: basta con que coincida uno.

### El ancho de la ventana es mayor que

**Identificador:** `fancymenu_loading_requirement_is_window_width_bigger_than`

Se cumple cuando la ventana tiene un ancho mayor que el indicado.

- Valor: el ancho, como `1920`.

## Mundo

Estos requisitos nunca se cumplen si no hay un mundo cargado. **El jugador está en una estructura** y **Está en una zona de asalto activa** requieren que FancyMenu esté instalado en el servidor. En un mundo de un jugador, siempre funcionan.

### El jugador tiene corazones de absorción

**Identificador:** `has_player_absorption_hearts`

Se cumple cuando el jugador tiene corazones dorados de absorción.

### El jugador tiene el nivel de permisos

**Identificador:** `fancymenu_loading_requirement_has_player_permission_level`

Se cumple cuando el jugador tiene al menos cierto nivel de permisos en el mundo o en el servidor, como el de operador.

- Valor: de `0` a `4`. El nivel `0` siempre se cumple; el nivel `2` basta para usar comandos como `/gamemode`; el comando `/op` otorga el nivel `4`.

### Está en modo Aventura

**Identificador:** `fancymenu_visibility_requirement_is_adventure`

Se cumple cuando el jugador está en modo Aventura.

### Tiene algún efecto activo

**Identificador:** `is_any_effect_active`

Se cumple cuando el jugador tiene algún efecto, como Velocidad o Veneno.

### La fuerza del ataque está reducida

**Identificador:** `is_attack_strength_weakened`

Se cumple cuando el ataque del jugador no está completamente cargado. Esto ocurre cuando aparece el indicador de ataque.

### El bloque o el objeto pertenece a una etiqueta

**Identificador:** `is_in_tag`

Se cumple cuando un bloque o un objeto pertenece a una etiqueta, como `minecraft:logs` o `c:tools`. Las etiquetas solo existen mientras hay un mundo cargado.

- Valor: haz clic en **Tipo de etiqueta** para elegir **Bloque** u **Objeto**; luego escribe la **Clave del bloque o del objeto** y la **Etiqueta**. Ambos campos sugieren valores. El símbolo `#` antes de la etiqueta es opcional.
- La clave funciona muy bien con variables de listener, como `$$block_key`. Por ejemplo, una instrucción IF en el script del listener [**Al romper un bloque**](/listeners#on-block-broke) puede mostrar una notificación emergente solo para los troncos.

### La perspectiva de la cámara es

**Identificador:** `is_camera_perspective`

Se cumple cuando la cámara está en cierta perspectiva (F5).

- Valor: haz clic en el botón para elegir **Primera persona**, **Tercera persona** o **Vista frontal**.

### El clima está despejado

**Identificador:** `is_clear_weather`

Se cumple cuando no llueve ni hay tormenta eléctrica.

### Está en modo Creativo

**Identificador:** `fancymenu_visibility_requirement_is_creative`

Se cumple cuando el jugador está en modo Creativo.

### El cursor sostiene un objeto del inventario

**Identificador:** `is_cursor_holding_inventory_item`

Se cumple cuando el cursor lleva un objeto en una pantalla de inventario.

### La dificultad es

**Identificador:** `is_difficulty`

Se cumple cuando el mundo tiene una dificultad determinada.

- Valor: `peaceful`, `easy`, `normal` o `hard`.

### El efecto está activo

**Identificador:** `is_effect_active`

Se cumple cuando el jugador tiene un efecto determinado.

- Valor: la clave del efecto, como `minecraft:speed`. El campo sugiere efectos mientras estás en un mundo.

### Hay una entidad cerca

**Identificador:** `is_entity_nearby`

Se cumple cuando hay una entidad de cierto tipo cerca del jugador.

- Valor: la **Clave de registro de la entidad**, como `minecraft:creeper`, y el **Radio de comprobación en bloques**, como `10`. El campo de la clave sugiere entidades mientras estás en un mundo.

### El modo de juego es

**Identificador:** `is_gamemode`

Se cumple cuando el jugador está en cierto modo de juego.

- Valor: `survival`, `creative`, `adventure` o `spectator`.

### Es un mundo Hardcore

**Identificador:** `is_hardcore`

Se cumple en mundos Hardcore.

### La ranura de la barra rápida está seleccionada

**Identificador:** `is_hotbar_slot_active`

Se cumple cuando está seleccionada cierta ranura de la barra rápida.

- Valor: de `0` (la ranura de la izquierda) a `8`.

### Está en una zona de asalto activa

**Identificador:** `is_in_active_raid_area`

Se cumple cuando el jugador está en la zona de un asalto y aparece la barra del asalto. Requiere que FancyMenu esté instalado en el servidor.

### La ranura del inventario tiene un objeto

**Identificador:** `is_inventory_slot_filled`

Se cumple cuando hay un objeto en una ranura del inventario del jugador.

- Valor: el número de la ranura. De `0` a `8` corresponde a la barra rápida; de `9` a `35`, al resto del inventario.

### Hay un objeto del inventario bajo el cursor

**Identificador:** `is_item_hovered_in_inventory`

Se cumple cuando el cursor está sobre un objeto en una pantalla de inventario, como el inventario del jugador o un cofre.

### Está en multijugador

**Identificador:** `fancymenu_loading_requirement_is_multiplayer`

Se cumple cuando el jugador está en un servidor.

### El jugador vuela en modo Creativo

**Identificador:** `is_player_creative_flying`

Se cumple cuando el jugador vuela en modo Creativo.

### El jugador vuela con élitros

**Identificador:** `is_player_flying_with_elytra`

Se cumple cuando el jugador planea con élitros.

### El jugador está completamente congelado

**Identificador:** `is_player_fully_frozen`

Se cumple cuando el jugador está completamente congelado por la nieve en polvo y aparecen corazones congelados en la barra de salud.

### El jugador está en un bioma

**Identificador:** `is_player_in_biome`

Se cumple cuando el jugador está en un bioma determinado.

- Valor: la clave del bioma, como `minecraft:birch_forest`. El campo sugiere biomas mientras estás en un mundo.

### El jugador está en una dimensión

**Identificador:** `is_player_in_dimension`

Se cumple cuando el jugador está en una dimensión determinada.

- Valor: la clave de la dimensión: `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end` o la de un mod. El campo sugiere dimensiones mientras estás en un mundo.

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

- Valor: la clave de la estructura, como `minecraft:village_plains`. El campo sugiere estructuras mientras estás en un mundo.

### El jugador está en el agua

**Identificador:** `is_player_in_water`

Se cumple cuando el jugador está en el agua, aunque solo sea parcialmente.

### El jugador está saltando o cayendo

**Identificador:** `is_player_jumping`

Se cumple cuando el jugador está en el aire. Nadar, estar en fluidos, volar con élitros, dormir y gatear no cuentan.

### El jugador es zurdo

**Identificador:** `is_left_handed`

Se cumple cuando «Mano principal» está configurada como «Izquierda» en las opciones de personalización de apariencia de Minecraft.

### El jugador está envenenado

**Identificador:** `is_player_poisoned`

Se cumple cuando el jugador tiene el efecto de Veneno y aparecen corazones envenenados en la barra de salud.

### El jugador monta una entidad con salud

**Identificador:** `is_player_riding_entity_with_health`

Se cumple cuando el jugador monta una entidad viva, como un caballo o un cerdo. No cuentan los botes ni las vagonetas.

### El jugador monta una entidad o un vehículo

**Identificador:** `is_player_riding_entity`

Se cumple cuando el jugador monta cualquier cosa, como un caballo, un bote o una vagoneta.

### El jugador monta una entidad que puede saltar

**Identificador:** `is_player_riding_jumpable_entity`

Se cumple cuando el jugador monta una entidad que puede saltar, como un caballo.

### El jugador está corriendo

**Identificador:** `is_player_running`

Se cumple cuando el jugador corre a toda velocidad.

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

Se cumple cuando el jugador usa un objeto, como al comer, beber una poción o tensar un arco.

### El jugador lleva una calabaza

**Identificador:** `is_player_wearing_pumpkin`

Se cumple cuando el jugador lleva una calabaza tallada en la cabeza.

### El jugador está bajo el efecto de Wither

**Identificador:** `is_player_withered`

Se cumple cuando el jugador tiene el efecto de Wither y aparecen corazones marchitos en la barra de salud.

### Está lloviendo

**Identificador:** `is_raining`

Se cumple cuando llueve donde está el jugador.

### Está en un mundo de un jugador

**Identificador:** `fancymenu_loading_requirement_is_singpleplayer`

Se cumple cuando el jugador está en un mundo de un jugador.

### Está nevando

**Identificador:** `is_snowing`

Se cumple cuando nieva donde está el jugador.

### Está en modo Espectador

**Identificador:** `fancymenu_visibility_requirement_is_spectator`

Se cumple cuando el jugador está en modo Espectador.

### Está en modo Supervivencia

**Identificador:** `fancymenu_visibility_requirement_is_survival`

Se cumple cuando el jugador está en modo Supervivencia.

### Hay una tormenta eléctrica

**Identificador:** `is_thundering`

Se cumple durante una tormenta eléctrica.

### Hay un mundo cargado

**Identificador:** `fancymenu_loading_requirement_is_world_loaded`

Se cumple cuando el jugador está en un mundo, ya sea de un jugador o multijugador.

### El jugador estuvo en nieve en polvo

**Identificador:** `was_player_in_powder_snow`

Se cumple cuando el jugador estuvo en nieve en polvo hace un momento.

## Otros

### El idioma del juego es

**Identificador:** `fancymenu_loading_requirement_is_language`

Se cumple cuando Minecraft usa un idioma determinado.

- Valor: el código del idioma, como `en_us` o `de_de`. El campo sugiere todos los idiomas.

### El mod está cargado

**Identificador:** `fancymenu_loading_requirement_is_mod_loaded`

Se cumple cuando hay ciertos mods instalados.

- Valor: el ID del mod, como `jei`. El campo sugiere los IDs de tus mods. Separa varios IDs con comas: todos deben estar instalados. `optifine` comprueba si está instalado OptiFine.

### El número es

**Identificador:** `fancymenu_visibility_requirement_is_number`

Compara dos números. Escribe marcadores de posición o variables en los campos, como `$$coins`.

- **Modo de comparación**: **Es igual a**, **Es mayor que**, **Es menor que**, **Es mayor o igual que** o **Es menor o igual que**.
- **Número**: el número que quieres comprobar, como `$$coins`.
- **Comparar con el número**: el número con el que se comparará, como `100`.

Se permiten decimales, como `2.5`. Si un campo no contiene un número, el requisito nunca se cumple.

### El paquete de recursos está activado

**Identificador:** `is_resource_pack_enabled`

Se cumple cuando un paquete de recursos está activado.

- Valor: el nombre del paquete tal como aparece en la pantalla de Paquetes de recursos, como `Programmer Art`, o su ID. No se distingue entre mayúsculas y minúsculas.

### Rinku está cargado

**Identificador:** `is_rinku_loaded`

Se cumple cuando está instalado el mod [Rinku](https://modrinth.com/mod/rinku). El [elemento de navegador](/elements#browser) y los antiguos [tipos de video basados en Rinku](/video#requirements) lo necesitan.

### La IP del servidor es

**Identificador:** `fancymenu_visibility_requirement_is_server_ip`

Se cumple cuando el jugador está en un servidor determinado.

- Valor: la dirección del servidor, como `play.example.net`. Si incluye un puerto, como `play.example.net:25566`, el puerto también debe coincidir.

### El servidor está en línea

**Identificador:** `fancymenu_loading_requirement_is_server_online`

Se cumple cuando un servidor está en línea. FancyMenu le envía una señal en segundo plano cada 30 segundos aproximadamente, así que puede tardar un poco en comprobarlo después de iniciar el juego.

- Valor: la dirección del servidor, como `play.example.net`.

### El texto es

**Identificador:** `fancymenu_visibility_requirement_is_text`

Compara dos textos. Escribe marcadores de posición o variables en los campos, como `$$key_name`.

- **Modo de comparación**: **Es igual a**, **Contiene**, **Empieza con** o **Termina con**.
- **Texto**: el texto que quieres comprobar.
- **Comparar con el texto**: el texto con el que se comparará.

Se distingue entre mayúsculas y minúsculas.

### El valor de la variable es (variable de FM)

**Identificador:** `fancymenu_visibility_requirement_is_variable_value`

Se cumple cuando una de tus [variables](/variables) tiene un valor determinado.

- **Nombre de la variable**: el nombre de la variable, sin `$$`. El campo sugiere tus variables.
- **Valor de la variable que se debe comprobar**: el valor, como `on`. Debe coincidir con el valor completo y distinguir entre mayúsculas y minúsculas.

Nunca se cumple si la variable no existe. En una variable de lista, compara el arreglo JSON de todas las entradas, como `["apple","banana"]`. Para comprobar una sola entrada, usa **La lista contiene una entrada (variable de FM)**.

### La lista contiene una entrada (variable de FM)

**Identificador:** `list_contains_entry`

Se cumple cuando una [variable de lista](/variables#text-and-list-variables) contiene una entrada determinada.

- **Nombre de la variable de lista**: el nombre de la lista, sin `$$`. El campo sugiere tus variables de lista y te avisa si escribes el nombre de una variable de texto.
- **Entrada que se debe buscar**: la entrada. Debe coincidir con una entrada completa, no solo con una parte.
- **Ignorar mayúsculas y minúsculas**: si está activado, `Apple` también coincide con `apple`.

Nunca se cumple si la lista no existe.

### El botón del mouse está presionado

**Identificador:** `mouse_click`

Se cumple mientras se mantenga presionado un botón del mouse. Para ejecutar acciones una sola vez por cada clic, usa el listener [**Al hacer clic en un botón del mouse**](/listeners#on-mouse-button-clicked).

- Valor: `left` (izquierdo) o `right` (derecho).

### Solo una vez por sesión

**Identificador:** `once_per_session`

Se cumple la primera vez que se comprueba y no vuelve a cumplirse hasta que se reinicie el juego. Cada copia de este requisito funciona por separado.

Para elementos que deben aparecer solo una vez por sesión de juego, es más sencillo usar la opción [**Cargar una vez por sesión**](/element-visibility#load-once-per-session) de los elementos: estos permanecen hasta que se abre una pantalla nueva.
