---
title: Condiciones (Requisitos)
description: Cómo usar los requisitos de carga.
---

# Requisitos

Los requisitos (llamados **Requisitos de carga** en algunos menús) muestran u ocultan contenido según condiciones como el estado de hover, el tamaño de la ventana o si un mundo está cargado.

Puedes usarlos en [elementos](./elements), en diseños completos y en [scripts de acción](./action-scripts).

# Agregar requisitos a elementos

Para agregar requisitos a un elemento, haz clic derecho sobre él y selecciona **Requisitos de carga**.

Los requisitos se revisan mientras el menú está abierto, así que los elementos se actualizan cuando cambia una condición.

# Requisitos para todo el diseño

También puedes cambiar la visibilidad de diseños completos haciendo clic derecho en el **fondo del editor** y luego en **Requisitos de carga [Todo el diseño]**.

Cuando cambia el resultado a nivel de diseño, FancyMenu reconstruye la pantalla actual y aplica los diseños cuyos requisitos ahora se cumplen.

# Scripts de acción

Los requisitos también se pueden usar en scripts de acción.
Puedes agregarlos en la pantalla del editor de scripts de acción y usarlos para ejecutar acciones específicas solo si se cumple la condición del requisito.

# Combinar requisitos

- Los requisitos fuera de grupos usan **AND**, así que todos deben cumplirse.
- Dentro de un grupo, elige **AND** u **OR**.
- Usa **IF NOT** para invertir un requisito.

Estas reglas son las mismas para elementos, diseños y scripts de acción.

# Valores de los requisitos

Para los requisitos que necesitan un valor, usa **Editar valor del requisito** y sigue la descripción que aparece en el editor. Algunos campos admiten autocompletado con **TAB**.

Si un requisito importado deja de funcionar después de cambiar FancyMenu o los complementos, edítalo en la pantalla de requisitos y revisa `logs/latest.log` para ver errores.

El editor de requisitos admite un menú contextual con clic derecho, navegación con teclado, búsqueda, deshacer/rehacer (`Ctrl/Command + Z` / `Ctrl/Command + Y`) y `Ctrl/Command + S` para guardar.

# Requisitos en detalle

Esta sección enumera los requisitos integrados de FancyMenu.

## ¿El elemento está en hover? (`fancymenu_visibility_requirement_is_element_hovered`)

**Propósito:** Verifica si el cursor del mouse está sobre un elemento específico.

**Valor:** Obligatorio — [Identificador del elemento](./element-identifiers) de destino (por ejemplo, `some_element_ID`).

## ¿El elemento tiene foco? (`is_element_focused`)

**Propósito:** Verifica si un elemento específico tiene el foco del teclado actualmente (por ejemplo, un campo de texto o un botón enfocado).

**Valor:** Obligatorio — ID del elemento de destino (el mismo ID que se muestra en el editor)

> [!NOTE]
> El foco y el hover son estados diferentes. Un elemento puede conservar su apariencia de enfocado después de que el puntero se aleje; al hacer clic o usar la navegación con teclado puede recibir el foco.

## ¿Algún elemento está en hover? (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Propósito:** Verifica elementos visibles/renderizables en la capa de personalización activa actual, incluidos los elementos aportados por diseños apilados.

**Valor:** No requerido

## ¿Algún botón está en hover? (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Propósito:** Verifica si cualquier botón vanilla o personalizado visible/renderizable en la capa de personalización activa actual está en hover, incluidos los botones aportados por diseños apilados.

**Valor:** No requerido

## ¿El diseño está habilitado? (`fancymenu_visibility_requirement_is_layout_enabled`)

**Propósito:** Verifica si un diseño específico está habilitado actualmente.

**Valor:** Obligatorio — Nombre del diseño (por ejemplo, `my_cool_main_menu_layout`)

## ¿El programador está ejecutándose? (`fancymenu_visibility_requirement_is_scheduler_running`)

**Propósito:** Verifica si un [programador](./schedulers) está ejecutándose actualmente.

**Valor:** Obligatorio — ID del programador (por ejemplo, `my_scheduler`)

## ¿El escalado de GUI coincide? (`fancymenu_loading_requirement_is_gui_scale`)

**Propósito:** Verifica si el escalado actual de la GUI cumple ciertas condiciones.

**Valor:** Obligatorio — Usa un número para igualdad, `>` para mayor que, o `<` para menor que.

Varias condiciones separadas por comas se combinan con AND. Por ejemplo, `>1,<4` solo pasa cuando el escalado de la GUI es mayor que `1` y menor que `4`.

## ¿El botón está activo? (`fancymenu_visibility_requirement_is_button_active`)

**Propósito:** Verifica si un botón específico está activo (se puede hacer clic).

**Valor:** Obligatorio — ID del elemento del botón de destino (por ejemplo, "some_element_ID")

## ¿El título de la pantalla coincide? (`is_menu_title`)

**Propósito:** Verifica si el título MOSTRADO de la pantalla coincide con un texto específico o una clave de localización. Esto solo comprobará el nombre/título visible de la pantalla, como "Options" o "Pause". ¡NO comprobará el identificador del menú/pantalla (como `title_screen`)! 

**Valor:** Obligatorio — El texto exacto del título o la clave de localización de la pantalla

## ¿Hay una tecla presionada? (`is_key_pressed`)

**Propósito:** Verifica si una tecla específica del teclado se está presionando actualmente.

**Valor:** Obligatorio — El código de tecla del botón objetivo. Se selecciona mediante una interfaz al editar el valor del requisito.

## ¿Hay alguna pantalla abierta? (`is_any_screen_open`)

**Propósito:** Verifica si alguna pantalla/menú está abierta actualmente (devuelve false si no se está mostrando ninguna pantalla).

**Valor:** No requerido

## ¿La superposición de depuración de MC está activada? (`is_debug_overlay_enabled`)

**Propósito:** Verifica si la superposición de depuración de F3 está visible actualmente.

**Valor:** No requerido

## ¿El tipo de cursor activo coincide? (`is_active_cursor_type`)

**Propósito:** Verifica si el tipo de cursor activo de FancyMenu coincide con un tipo de cursor estándar específico.

**Valor:** Obligatorio — Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` o `not_allowed`

## ¿La barra del menú de personalización está visible? (`is_customization_menu_bar_visible`)

**Propósito:** Verifica si la barra del menú de personalización de FancyMenu está visible actualmente.

**Valor:** No requerido

## ¿Está activado el Modo paquete mod? (`is_modpack_mode_enabled`)

**Propósito:** Verifica si el Modo paquete mod de FancyMenu está activado.

**Valor:** No requerido

## Botón del mouse presionado (`mouse_click`)

**Propósito:** Devuelve true mientras se mantenga presionado un botón específico del mouse. Esto no es un evento de clic único; usa el [**escuchador On Mouse Button Clicked**](./listeners#on-mouse-button-clicked-mouse_button_clicked) cuando una acción deba ejecutarse una vez por clic.

**Valor:** Obligatorio — `left` o `right` para indicar qué botón del mouse comprobar

## ¿Está en pantalla completa? (`fancymenu_loading_requirement_is_fullscreen`)

**Propósito:** Verifica si el juego está actualmente en modo de pantalla completa.

**Valor:** No requerido

## ¿El ancho de la ventana coincide? (`fancymenu_loading_requirement_is_window_width`)

**Propósito:** Verifica si el ancho de la ventana del juego coincide con valores específicos.

**Valor:** Obligatorio — Ancho de la ventana en píxeles (por ejemplo, "1920"). Se pueden proporcionar varios valores separándolos con comas.

## ¿La altura de la ventana coincide? (`fancymenu_loading_requirement_is_window_height`)

**Propósito:** Verifica si la altura de la ventana del juego coincide con valores específicos.

**Valor:** Obligatorio — Altura de la ventana en píxeles (por ejemplo, "1080"). Se pueden proporcionar varios valores separándolos con comas.

## ¿El ancho de la ventana es mayor que? (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Propósito:** Verifica si el ancho de la ventana del juego es mayor que un valor específico.

**Valor:** Obligatorio — Ancho de la ventana en píxeles (por ejemplo, "1920")

## ¿La altura de la ventana es mayor que? (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Propósito:** Verifica si la altura de la ventana del juego es mayor que un valor específico.

**Valor:** Obligatorio — Altura de la ventana en píxeles (por ejemplo, "1080")

## ¿Es multijugador? (`fancymenu_loading_requirement_is_multiplayer`)

**Propósito:** Verifica si el jugador está actualmente en un mundo multijugador.

**Valor:** No requerido

## ¿Es un jugador? (`fancymenu_loading_requirement_is_singpleplayer`)

**Propósito:** Verifica si el jugador está actualmente en un mundo de un solo jugador.

**Valor:** No requerido

## ¿El mundo está cargado? (`fancymenu_loading_requirement_is_world_loaded`)

**Propósito:** Verifica si actualmente hay algún mundo cargado.

**Valor:** No requerido

## ¿Está en aventura? (`fancymenu_visibility_requirement_is_adventure`)

**Propósito:** Verifica si el jugador está actualmente en modo aventura.

**Valor:** No requerido

## ¿Está en creativo? (`fancymenu_visibility_requirement_is_creative`)

**Propósito:** Verifica si el jugador está actualmente en modo creativo.

**Valor:** No requerido

## ¿Está en espectador? (`fancymenu_visibility_requirement_is_spectator`)

**Propósito:** Verifica si el jugador está actualmente en modo espectador.

**Valor:** No requerido

## ¿Está en supervivencia? (`fancymenu_visibility_requirement_is_survival`)

**Propósito:** Verifica si el jugador está actualmente en modo supervivencia.

**Valor:** No requerido

## ¿El modo de juego coincide? (`is_gamemode`)

**Propósito:** Verifica si el jugador está en un modo de juego específico.

**Valor:** Obligatorio — Nombre del modo de juego (por ejemplo, "creative", "survival", "adventure", "spectator")

## ¿La dificultad coincide? (`is_difficulty`)

**Propósito:** Verifica si la dificultad actual del juego coincide con un valor específico.

**Valor:** Obligatorio — Nombre de la dificultad (por ejemplo, "peaceful", "easy", "normal", "hard")

## ¿Es hardcore? (`is_hardcore`)

**Propósito:** Verifica si el mundo cargado actualmente está en modo hardcore.

**Valor:** No requerido

## ¿La perspectiva de la cámara coincide? (`is_camera_perspective`)

**Propósito:** Verifica si la perspectiva actual de la cámara coincide con una perspectiva específica.

**Valor:** Obligatorio — `first_person`, `third_person_back` o `third_person_front`

## ¿Está lloviendo? (`is_raining`)

**Propósito:** Verifica si actualmente está lloviendo en la ubicación del jugador.

**Valor:** No requerido

## ¿Está tronando? (`is_thundering`)

**Propósito:** Verifica si actualmente hay una tormenta eléctrica en el mundo del jugador.

**Valor:** No requerido

## ¿El clima está despejado? (`is_clear_weather`)

**Propósito:** Verifica si el clima está despejado actualmente (no está lloviendo ni tronando).

**Valor:** No requerido

## ¿Está nevando? (`is_snowing`)

**Propósito:** Verifica si actualmente está nevando en la ubicación del jugador.

**Valor:** No requerido

## ¿El jugador está corriendo? (`is_player_running`)

**Propósito:** Verifica si el jugador está esprintando actualmente.

**Valor:** No requerido

## ¿El jugador está agachado? (`is_player_sneaking`)

**Propósito:** Verifica si el jugador está actualmente agachado/en cuclillas.

**Valor:** No requerido

## ¿El jugador está usando un objeto? (`is_player_using_item`)

**Propósito:** Verifica si el jugador está usando actualmente un objeto.

**Valor:** No requerido

## ¿El jugador está nadando? (`is_player_swimming`)

**Propósito:** Verifica si el jugador está nadando actualmente.

**Valor:** No requerido

## ¿El jugador está saltando o cayendo? (`is_player_jumping`)

**Propósito:** Devuelve true mientras el jugador está en el aire en un estado normal de salto o caída. Se excluyen la natación, los fluidos, el vuelo con alas de elytra, dormir, la natación visual y arrastrarse.

**Valor:** No requerido

## ¿El jugador está bajo el agua? (`is_player_under_water`)

**Propósito:** Verifica si el jugador está completamente bajo el agua.

**Valor:** No requerido

## ¿El jugador está en el agua? (`is_player_in_water`)

**Propósito:** Verifica si el jugador está en el agua (puede estar parcialmente sumergido).

**Valor:** No requerido

## ¿El jugador está en lava? (`is_player_in_lava`)

**Propósito:** Verifica si el jugador está en lava.

**Valor:** No requerido

## ¿El jugador está en un fluido? (`is_player_in_fluid`)

**Propósito:** Verifica si el jugador está en cualquier fluido (agua, lava, etc.).

**Valor:** No requerido

## ¿El jugador está montando una entidad/vehículo? (`is_player_riding_entity`)

**Propósito:** Verifica si el jugador está montando cualquier entidad.

**Valor:** No requerido

## ¿El jugador está montando una entidad que puede saltar? (`is_player_riding_jumpable_entity`)

**Propósito:** Verifica si el jugador está montando una entidad que puede saltar (como un caballo).

**Valor:** No requerido

## ¿El jugador está montando una entidad con salud? (`is_player_riding_entity_with_health`)

**Propósito:** Verifica si el jugador está montando una entidad viva con salud (como animales, no botes).

**Valor:** No requerido

## ¿El jugador está en nieve polvo? (`is_player_in_powder_snow`)

**Propósito:** Verifica si el jugador está actualmente en nieve polvo.

**Valor:** No requerido

## ¿El jugador estuvo en nieve polvo? (`was_player_in_powder_snow`)

**Propósito:** Verifica si el jugador estuvo en nieve polvo (se usa para efectos que persisten después de salir).

**Valor:** No requerido

## ¿El jugador lleva una calabaza? (`is_player_wearing_pumpkin`)

**Propósito:** Verifica si el jugador lleva una calabaza tallada en la cabeza.

**Valor:** No requerido

## ¿El jugador vuela con elytra? (`is_player_flying_with_elytra`)

**Propósito:** Verifica si el jugador está volando actualmente con un elytra.

**Valor:** No requerido

## ¿El jugador vuela en creativo? (`is_player_creative_flying`)

**Propósito:** Verifica si el jugador está volando en modo creativo.

**Valor:** No requerido

## ¿El jugador tiene corazones de absorción? (`has_player_absorption_hearts`)

**Propósito:** Verifica si el jugador tiene corazones de absorción (corazones dorados).

**Valor:** No requerido

## ¿El jugador tiene el efecto Wither? (`is_player_withered`)

**Propósito:** Verifica si el jugador está afectado por el efecto wither.

**Valor:** No requerido

## ¿El jugador está completamente congelado? (`is_player_fully_frozen`)

**Propósito:** Verifica si el jugador está completamente congelado (normalmente por nieve polvo).

**Valor:** No requerido

## ¿El jugador está envenenado? (`is_player_poisoned`)

**Propósito:** Verifica si el jugador está afectado por el efecto veneno.

**Valor:** No requerido

## ¿El jugador está en un bioma? (`is_player_in_biome`)

**Propósito:** Verifica si el jugador está en un bioma específico.

**Valor:** Obligatorio — Identificador del bioma (por ejemplo, `minecraft:birch_forest`)

## ¿El jugador está en una dimensión? (`is_player_in_dimension`)

**Propósito:** Verifica si el jugador está en una dimensión específica.

**Valor:** Obligatorio — Identificador de la dimensión (por ejemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## ¿El jugador está en una estructura? (`is_player_in_structure`)

**Propósito:** Verifica si el jugador está actualmente dentro de una estructura específica. Requiere FancyMenu en el servidor para mundos de servidor.

**Valor:** Obligatorio — Identificador de la estructura (por ejemplo, `minecraft:village`)

## ¿Hay una entidad cerca? (`is_entity_nearby`)

**Propósito:** Verifica si un tipo de entidad específico está dentro de cierto radio del jugador.

**Valor:** Obligatorio — Formato: "radio:id_de_entidad" (por ejemplo, `10:minecraft:pig` - verifica si hay cerdos dentro de 10 bloques)

## ¿Un efecto está activo? (`is_effect_active`)

**Propósito:** Verifica si un efecto de poción específico está activo en el jugador.

**Valor:** Obligatorio — Identificador del efecto (por ejemplo, `minecraft:speed`, `minecraft:strength`)

## ¿Algún efecto está activo? (`is_any_effect_active`)

**Propósito:** Verifica si el jugador tiene algún efecto de poción activo.

**Valor:** No requerido

## ¿El jugador es zurdo? (`is_left_handed`)

**Propósito:** Verifica si el jugador tiene activado el modo zurdo en las opciones del juego.

**Valor:** No requerido

## ¿La ranura del inventario está llena? (`is_inventory_slot_filled`)

**Propósito:** Verifica si una ranura específica del inventario contiene un objeto.

**Valor:** Obligatorio — Número de ranura (0-35 para el inventario principal, las ranuras 0-8 son la barra rápida)

## ¿Hay un objeto en hover en el inventario? (`is_item_hovered_in_inventory`)

**Propósito:** Verifica si el cursor está pasando sobre cualquier objeto en una pantalla de inventario.

**Valor:** No requerido

## ¿El cursor sostiene un objeto del inventario? (`is_cursor_holding_inventory_item`)

**Propósito:** Verifica si el cursor está sosteniendo actualmente una pila de objetos del inventario.

**Valor:** No requerido

## ¿La ranura de la barra rápida está seleccionada? (`is_hotbar_slot_active`)

**Propósito:** Verifica si una ranura específica de la barra rápida está seleccionada actualmente.

**Valor:** Obligatorio — Número de ranura de la barra rápida (0-8)

## ¿Tiene el jugador nivel de permisos? (`fancymenu_loading_requirement_has_player_permission_level`)

**Propósito:** Verifica si el jugador tiene al menos el nivel especificado de permiso/OP en el mundo o servidor actual.

**Valor:** Obligatorio — Número de nivel de permiso (0-4, donde 4 es operador del servidor)

## ¿La fuerza de ataque está debilitada? (`is_attack_strength_weakened`)

**Propósito:** Verifica si la fuerza de ataque del jugador está debilitada actualmente (no totalmente cargada).

**Valor:** No requerido

## ¿Es día en tiempo real? (`fancymenu_visibility_requirement_is_realtime_day`)

**Propósito:** Verifica si el día actual del mes en tiempo real coincide con un valor específico.

**Valor:** Obligatorio — Número del día (1-31). Se pueden proporcionar varios valores separándolos con comas.

## ¿Es hora en tiempo real? (`fancymenu_visibility_requirement_is_realtime_hour`)

**Propósito:** Verifica si la hora actual en tiempo real coincide con un valor específico.

**Valor:** Obligatorio — Hora en formato de 24 horas (0-23). Se pueden proporcionar varios valores separándolos con comas.

## ¿Es minuto en tiempo real? (`fancymenu_visibility_requirement_is_realtime_minute`)

**Propósito:** Verifica si el minuto actual en tiempo real coincide con un valor específico.

**Valor:** Obligatorio — Minuto (0-59). Se pueden proporcionar varios valores separándolos con comas.

## ¿Es mes en tiempo real? (`fancymenu_visibility_requirement_is_realtime_month`)

**Propósito:** Verifica si el mes actual en tiempo real coincide con un valor específico.

**Valor:** Obligatorio — Número del mes (1-12, donde 1 es enero). Se pueden proporcionar varios valores separándolos con comas.

## ¿Es segundo en tiempo real? (`fancymenu_visibility_requirement_is_realtime_second`)

**Propósito:** Verifica si el segundo actual en tiempo real coincide con un valor específico.

**Valor:** Obligatorio — Segundo (0-59). Se pueden proporcionar varios valores separándolos con comas.

## ¿Es día de la semana en tiempo real? (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Propósito:** Verifica si el día actual de la semana en tiempo real coincide con un valor específico.

**Valor:** Obligatorio — Día de la semana como número (1-7, donde 1 es domingo). Se pueden proporcionar varios valores separándolos con comas.

## ¿Es año en tiempo real? (`fancymenu_visibility_requirement_is_realtime_year`)

**Propósito:** Verifica si el año actual en tiempo real coincide con un valor específico.

**Valor:** Obligatorio — Año completo (por ejemplo, "2023"). Se pueden proporcionar varios valores separándolos con comas.

## ¿Existe archivo/carpeta? (`fancymenu_loading_requirement_file_exists`)

**Propósito:** Verifica si existe un archivo o directorio.

**Valor:** Obligatorio — Una ruta relativa al directorio activo del juego, o una ruta que empiece con `.minecraft/` para el directorio convencional de Minecraft. Tanto archivos como directorios cuentan como existentes.

## ¿El SO es Linux? (`fancymenu_loading_requirement_is_os_linux`)

**Propósito:** Verifica si la plataforma actual no es Windows ni macOS. Normalmente esto corresponde a entornos Linux.

**Valor:** No requerido

## ¿El SO es macOS? (`fancymenu_loading_requirement_is_os_macos`)

**Propósito:** Verifica si el sistema operativo es macOS.

**Valor:** No requerido

## ¿El SO es Windows? (`fancymenu_loading_requirement_is_os_windows`)

**Propósito:** Verifica si el sistema operativo es Windows.

**Valor:** No requerido

## ¿Hay conexión a internet disponible? (`is_internet_connection_available`)

**Propósito:** Verifica si hay una conexión activa a internet disponible.

**Valor:** No requerido

## ¿El idioma del juego coincide? (`fancymenu_loading_requirement_is_language`)

**Propósito:** Verifica si el idioma actual del juego coincide con un valor específico.

**Valor:** Obligatorio — Código de idioma (por ejemplo, `en_us` para inglés)

## ¿Mod cargado? (`fancymenu_loading_requirement_is_mod_loaded`)

**Propósito:** Verifica si un mod específico está cargado.

**Valor:** Obligatorio — ID del mod (por ejemplo, `fancymenu`, `jei`). También puedes comprobar OptiFine con `optifine`. Se admiten varios IDs de mod separados por comas; todos los mods listados deben estar cargados.

## ¿MCEF está cargado? (`is_mcef_loaded`)

**Propósito:** Verifica si MCEF (Minecraft Chromium Embedded Framework) está instalado e inicializado. MCEF es necesario para el [elemento Browser](./elements#browser) y para [tipos de video basados en MCEF obsoletos](./video#requirements); las [funciones nativas de Video](./video) usan Watermedia.

**Valor:** No requerido

## ¿Es número? (`fancymenu_visibility_requirement_is_number`)

**Propósito:** Proporciona comparación avanzada de números con distintos modos de comparación.

**Valor:** Obligatorio — Formato complejo: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` donde `comparison_mode` puede ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` o `smaller-than-or-equals`

## ¿Es texto? (`fancymenu_visibility_requirement_is_text`)

**Propósito:** Proporciona comparación avanzada de texto con distintos modos de comparación.

**Valor:** Obligatorio — Formato complejo: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` donde `comparison_mode` puede ser `equals`, `contains`, `starts-with` o `ends-with`

## ¿La IP del servidor coincide? (`fancymenu_visibility_requirement_is_server_ip`)

**Propósito:** Verifica si la IP del servidor actual coincide con un valor específico.

**Valor:** Obligatorio — Dirección IP del servidor (con o sin puerto)

## ¿El servidor está en línea? (`fancymenu_loading_requirement_is_server_online`)

**Propósito:** Verifica si un servidor específico está en línea y responde.

**Valor:** Obligatorio — Dirección IP del servidor (con o sin puerto)

## ¿El paquete de recursos está activado? (`is_resource_pack_enabled`)

**Propósito:** Verifica si un paquete de recursos específico está actualmente seleccionado/activo.

**Valor:** Obligatorio — Título del paquete de recursos o ID del paquete (por ejemplo, `Programmer Art` o el ID del paquete)

## ¿El valor de la variable (variable de FM) coincide? (`fancymenu_visibility_requirement_is_variable_value`)

**Propósito:** Verifica si una variable de FancyMenu tiene un valor específico.

**Valor:** Obligatorio — Formato: "nombre_de_variable:valor_esperado"

## Solo una vez por sesión (`once_per_session`)

**Propósito:** Cada instancia configurada devuelve true una vez por sesión de juego. Las distintas instancias se rastrean de forma independiente.

**Valor:** No requerido
