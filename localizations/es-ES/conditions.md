---
title: Condiciones (Requisitos)
description: Cómo usar los requisitos de carga.
---

# Requisitos

Los requisitos (llamados **Requisitos de carga** en algunos menús) muestran u ocultan contenido en función de condiciones como el estado de hover, el tamaño de la ventana o si se ha cargado un mundo.

Puedes usarlos en [elementos](./elements), diseños completos y [scripts de acciones](./action-scripts).

# Añadir requisitos a elementos

Para añadir requisitos a un elemento, haz clic derecho sobre él y selecciona **Requisitos de carga**.

Los requisitos se comprueban mientras el menú está abierto, así que los elementos se actualizan cuando cambia una condición.

# Requisitos para todo el diseño

También puedes cambiar la visibilidad de diseños completos haciendo clic derecho en el **fondo del editor** y luego en **Requisitos de carga [Todo el diseño]**.

Cuando cambia el resultado de un requisito a nivel de diseño, FancyMenu reconstruye la pantalla actual y aplica los diseños cuyos requisitos ahora se cumplen.

# Scripts de acciones

Los requisitos también se pueden usar en scripts de acciones.
Puedes añadirlos en la pantalla del editor de scripts de acciones y usarlos para ejecutar acciones específicas solo si se cumple la condición del requisito.

# Combinar requisitos

- Los requisitos fuera de grupos usan **AND**, así que todos deben cumplirse.
- Dentro de un grupo, elige **AND** u **OR**.
- Usa **IF NOT** para invertir un requisito.

Estas reglas son las mismas para elementos, diseños y scripts de acciones.

# Valores de los requisitos

Para los requisitos que necesitan un valor, usa **Editar valor del requisito** y sigue la descripción que se muestra en el editor. Algunos campos admiten autocompletado con **TAB**.

Si un requisito importado deja de funcionar después de cambiar FancyMenu o los complementos, edítalo en la pantalla de requisitos y revisa `logs/latest.log` en busca de errores.

El editor de requisitos admite un menú contextual con clic derecho, navegación con teclado, búsqueda, deshacer/rehacer (`Ctrl/Command + Z` / `Ctrl/Command + Y`) y `Ctrl/Command + S` para guardar.

# Requisitos en detalle

Esta sección enumera los requisitos integrados de FancyMenu.

## El elemento está en hover (`fancymenu_visibility_requirement_is_element_hovered`)

**Propósito:** Comprueba si el puntero del ratón está sobre un elemento concreto.

**Valor:** Obligatorio — [Identificador del elemento](./element-identifiers) del elemento de destino (por ejemplo, `some_element_ID`).

## El elemento está enfocado (`is_element_focused`)

**Propósito:** Comprueba si un elemento concreto tiene actualmente el foco del teclado (por ejemplo, un campo de texto o un botón enfocado).

**Valor:** Obligatorio — ID del elemento de destino (el mismo ID que se muestra en el editor)

> [!NOTE]
> El foco y el hover son estados diferentes. Un elemento puede conservar su apariencia de enfocado después de que el puntero se aleje; al hacer clic o usar la navegación con teclado puede recibir el foco.

## Cualquier elemento está en hover (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Propósito:** Comprueba elementos visibles/renderizables en la capa de personalización activa actual, incluidos los elementos aportados por diseños apilados.

**Valor:** No obligatorio

## Cualquier botón está en hover (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Propósito:** Comprueba si cualquier botón vanilla o personalizado visible/renderizable en la capa de personalización activa actual está en hover, incluidos los botones aportados por diseños apilados.

**Valor:** No obligatorio

## El diseño está habilitado (`fancymenu_visibility_requirement_is_layout_enabled`)

**Propósito:** Comprueba si un diseño concreto está habilitado actualmente.

**Valor:** Obligatorio — El nombre del diseño (por ejemplo, `my_cool_main_menu_layout`)

## El programador está en ejecución (`fancymenu_visibility_requirement_is_scheduler_running`)

**Propósito:** Comprueba si un [programador](./schedulers) está en ejecución actualmente.

**Valor:** Obligatorio — ID del programador (por ejemplo, `my_scheduler`)

## La escala de la GUI es (`fancymenu_loading_requirement_is_gui_scale`)

**Propósito:** Comprueba si la escala actual de la GUI coincide con ciertas condiciones.

**Valor:** Obligatorio — Usa un número para igualdad, `>` para mayor que o `<` para menor que.

Varias condiciones separadas por comas se combinan con AND. Por ejemplo, `>1,<4` solo se cumple cuando la escala de la GUI es mayor que `1` y menor que `4`.

## El botón está activo (`fancymenu_visibility_requirement_is_button_active`)

**Propósito:** Comprueba si un botón concreto está activo (se puede hacer clic).

**Valor:** Obligatorio — ID del elemento del botón de destino (por ejemplo, "some_element_ID")

## El título de la pantalla es (`is_menu_title`)

**Propósito:** Comprueba si el título mostrado en pantalla coincide con un texto concreto o una clave de localización. Esto solo comprobará el nombre visible/título de la pantalla, como "Options" o "Pause". ¡NO comprobará el identificador del menú/pantalla (como `title_screen`)!

**Valor:** Obligatorio — El texto exacto del título o la clave de localización de la pantalla

## Se ha pulsado una tecla (`is_key_pressed`)

**Propósito:** Comprueba si una tecla concreta del teclado se está pulsando actualmente.

**Valor:** Obligatorio — El código de tecla de la tecla de destino. Se selecciona mediante una interfaz al editar el valor del requisito.

## Hay alguna pantalla abierta (`is_any_screen_open`)

**Propósito:** Comprueba si alguna pantalla/menú está abierta actualmente (devuelve false si no se muestra ninguna pantalla).

**Valor:** No obligatorio

## El overlay de depuración de MC está activado (`is_debug_overlay_enabled`)

**Propósito:** Comprueba si el overlay de depuración de F3 está visible actualmente.

**Valor:** No obligatorio

## Tipo de cursor activo (`is_active_cursor_type`)

**Propósito:** Comprueba si el tipo de cursor activo actualmente en FancyMenu coincide con un tipo de cursor estándar concreto.

**Valor:** Obligatorio — Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` o `not_allowed`

## La barra del menú de personalización está visible (`is_customization_menu_bar_visible`)

**Propósito:** Comprueba si la barra del menú de personalización de FancyMenu está visible actualmente.

**Valor:** No obligatorio

## El modo Pack de mods está activado (`is_modpack_mode_enabled`)

**Propósito:** Comprueba si el modo Pack de mods de FancyMenu está activado.

**Valor:** No obligatorio

## Se mantiene pulsado el botón del ratón (`mouse_click`)

**Propósito:** Devuelve true mientras se mantenga pulsado un botón específico del ratón. No es un evento de clic único; usa el [**listener On Mouse Button Clicked**](./listeners#on-mouse-button-clicked-mouse_button_clicked) cuando una acción deba ejecutarse una vez por clic.

**Valor:** Obligatorio — `left` o `right` para indicar qué botón del ratón comprobar

## Pantalla completa (`fancymenu_loading_requirement_is_fullscreen`)

**Propósito:** Comprueba si el juego está actualmente en modo pantalla completa.

**Valor:** No obligatorio

## El ancho de la ventana es (`fancymenu_loading_requirement_is_window_width`)

**Propósito:** Comprueba si el ancho de la ventana del juego coincide con valores concretos.

**Valor:** Obligatorio — Ancho de la ventana en píxeles (por ejemplo, "1920"). Se pueden proporcionar varios valores separándolos con comas.

## La altura de la ventana es (`fancymenu_loading_requirement_is_window_height`)

**Propósito:** Comprueba si la altura de la ventana del juego coincide con valores concretos.

**Valor:** Obligatorio — Altura de la ventana en píxeles (por ejemplo, "1080"). Se pueden proporcionar varios valores separándolos con comas.

## El ancho de la ventana es mayor que (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Propósito:** Comprueba si el ancho de la ventana del juego es mayor que un valor concreto.

**Valor:** Obligatorio — Ancho de la ventana en píxeles (por ejemplo, "1920")

## La altura de la ventana es mayor que (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Propósito:** Comprueba si la altura de la ventana del juego es mayor que un valor concreto.

**Valor:** Obligatorio — Altura de la ventana en píxeles (por ejemplo, "1080")

## Multijugador (`fancymenu_loading_requirement_is_multiplayer`)

**Propósito:** Comprueba si el jugador está actualmente en un mundo multijugador.

**Valor:** No obligatorio

## Un jugador (`fancymenu_loading_requirement_is_singpleplayer`)

**Propósito:** Comprueba si el jugador está actualmente en un mundo de un solo jugador.

**Valor:** No obligatorio

## Hay un mundo cargado (`fancymenu_loading_requirement_is_world_loaded`)

**Propósito:** Comprueba si hay algún mundo cargado actualmente.

**Valor:** No obligatorio

## Aventura (`fancymenu_visibility_requirement_is_adventure`)

**Propósito:** Comprueba si el jugador está actualmente en modo de juego aventura.

**Valor:** No obligatorio

## Creativo (`fancymenu_visibility_requirement_is_creative`)

**Propósito:** Comprueba si el jugador está actualmente en modo de juego creativo.

**Valor:** No obligatorio

## Espectador (`fancymenu_visibility_requirement_is_spectator`)

**Propósito:** Comprueba si el jugador está actualmente en modo de juego espectador.

**Valor:** No obligatorio

## Supervivencia (`fancymenu_visibility_requirement_is_survival`)

**Propósito:** Comprueba si el jugador está actualmente en modo de juego supervivencia.

**Valor:** No obligatorio

## El modo de juego es (`is_gamemode`)

**Propósito:** Comprueba si el jugador está en un modo de juego concreto.

**Valor:** Obligatorio — Nombre del modo de juego (por ejemplo, "creative", "survival", "adventure", "spectator")

## La dificultad es (`is_difficulty`)

**Propósito:** Comprueba si la dificultad actual del juego coincide con un valor concreto.

**Valor:** Obligatorio — Nombre de la dificultad (por ejemplo, "peaceful", "easy", "normal", "hard")

## Hardcore (`is_hardcore`)

**Propósito:** Comprueba si el mundo cargado actualmente está en modo hardcore.

**Valor:** No obligatorio

## La perspectiva de la cámara es (`is_camera_perspective`)

**Propósito:** Comprueba si la perspectiva actual de la cámara coincide con una perspectiva concreta.

**Valor:** Obligatorio — `first_person`, `third_person_back` o `third_person_front`

## Está lloviendo (`is_raining`)

**Propósito:** Comprueba si actualmente está lloviendo en la ubicación del jugador.

**Valor:** No obligatorio

## Está tronando (`is_thundering`)

**Propósito:** Comprueba si actualmente hay una tormenta en el mundo del jugador.

**Valor:** No obligatorio

## El tiempo está despejado (`is_clear_weather`)

**Propósito:** Comprueba si el tiempo está despejado actualmente (no está lloviendo ni tronando).

**Valor:** No obligatorio

## Está nevando (`is_snowing`)

**Propósito:** Comprueba si actualmente está nevando en la ubicación del jugador.

**Valor:** No obligatorio

## El jugador está corriendo (`is_player_running`)

**Propósito:** Comprueba si el jugador está esprintando actualmente.

**Valor:** No obligatorio

## El jugador está agachado (`is_player_sneaking`)

**Propósito:** Comprueba si el jugador está agachado/en cuclillas actualmente.

**Valor:** No obligatorio

## El jugador está usando un objeto (`is_player_using_item`)

**Propósito:** Comprueba si el jugador está usando actualmente un objeto.

**Valor:** No obligatorio

## El jugador está nadando (`is_player_swimming`)

**Propósito:** Comprueba si el jugador está nadando actualmente.

**Valor:** No obligatorio

## El jugador está saltando o cayendo (`is_player_jumping`)

**Propósito:** Devuelve true mientras el jugador está en el aire en un estado normal de salto o caída. Se excluyen la natación, los fluidos, el vuelo con elytra, dormir, la natación visual y el avance agachado.

**Valor:** No obligatorio

## El jugador está bajo el agua (`is_player_under_water`)

**Propósito:** Comprueba si el jugador está completamente bajo el agua.

**Valor:** No obligatorio

## El jugador está en el agua (`is_player_in_water`)

**Propósito:** Comprueba si el jugador está en el agua (puede estar parcialmente sumergido).

**Valor:** No obligatorio

## El jugador está en lava (`is_player_in_lava`)

**Propósito:** Comprueba si el jugador está en lava.

**Valor:** No obligatorio

## El jugador está en un fluido (`is_player_in_fluid`)

**Propósito:** Comprueba si el jugador está en cualquier fluido (agua, lava, etc.).

**Valor:** No obligatorio

## El jugador monta una entidad/vehículo (`is_player_riding_entity`)

**Propósito:** Comprueba si el jugador está montando cualquier entidad.

**Valor:** No obligatorio

## El jugador monta una entidad que puede saltar (`is_player_riding_jumpable_entity`)

**Propósito:** Comprueba si el jugador está montando una entidad que puede saltar (como un caballo).

**Valor:** No obligatorio

## El jugador monta una entidad con salud (`is_player_riding_entity_with_health`)

**Propósito:** Comprueba si el jugador está montando una entidad viva con salud (como animales, no barcas).

**Valor:** No obligatorio

## El jugador está en nieve polvo (`is_player_in_powder_snow`)

**Propósito:** Comprueba si el jugador está actualmente en nieve polvo.

**Valor:** No obligatorio

## El jugador estuvo en nieve polvo (`was_player_in_powder_snow`)

**Propósito:** Comprueba si el jugador estuvo en nieve polvo (se usa para efectos que persisten tras salir).

**Valor:** No obligatorio

## El jugador lleva una calabaza (`is_player_wearing_pumpkin`)

**Propósito:** Comprueba si el jugador lleva una calabaza tallada en la cabeza.

**Valor:** No obligatorio

## El jugador vuela con elytra (`is_player_flying_with_elytra`)

**Propósito:** Comprueba si el jugador está volando actualmente con una elytra.

**Valor:** No obligatorio

## El jugador vuela en creativo (`is_player_creative_flying`)

**Propósito:** Comprueba si el jugador está volando en modo creativo.

**Valor:** No obligatorio

## El jugador tiene corazones de absorción (`has_player_absorption_hearts`)

**Propósito:** Comprueba si el jugador tiene algún corazón de absorción (corazones dorados).

**Valor:** No obligatorio

## El jugador está afectado por wither (`is_player_withered`)

**Propósito:** Comprueba si el jugador está afectado por el efecto wither.

**Valor:** No obligatorio

## El jugador está completamente congelado (`is_player_fully_frozen`)

**Propósito:** Comprueba si el jugador está completamente congelado (normalmente por nieve polvo).

**Valor:** No obligatorio

## El jugador está envenenado (`is_player_poisoned`)

**Propósito:** Comprueba si el jugador está afectado por el efecto veneno.

**Valor:** No obligatorio

## El jugador está en un bioma (`is_player_in_biome`)

**Propósito:** Comprueba si el jugador está en un bioma concreto.

**Valor:** Obligatorio — Identificador del bioma (por ejemplo, `minecraft:birch_forest`)

## El jugador está en una dimensión (`is_player_in_dimension`)

**Propósito:** Comprueba si el jugador está en una dimensión concreta.

**Valor:** Obligatorio — Identificador de la dimensión (por ejemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## El jugador está en una estructura (`is_player_in_structure`)

**Propósito:** Comprueba si el jugador está actualmente dentro de una estructura concreta. Requiere FancyMenu en el servidor para mundos de servidor.

**Valor:** Obligatorio — Identificador de la estructura (por ejemplo, `minecraft:village`)

## Hay una entidad cerca (`is_entity_nearby`)

**Propósito:** Comprueba si un tipo de entidad concreto está dentro de un cierto radio del jugador.

**Valor:** Obligatorio — Formato: "radius:entity_id" (por ejemplo, `10:minecraft:pig` - comprueba si hay cerdos dentro de 10 bloques)

## El efecto está activo (`is_effect_active`)

**Propósito:** Comprueba si un efecto de poción concreto está activo en el jugador.

**Valor:** Obligatorio — Identificador del efecto (por ejemplo, `minecraft:speed`, `minecraft:strength`)

## Cualquier efecto está activo (`is_any_effect_active`)

**Propósito:** Comprueba si el jugador tiene activo algún efecto de poción.

**Valor:** No obligatorio

## El jugador es zurdo (`is_left_handed`)

**Propósito:** Comprueba si el jugador tiene activado el modo zurdo en las opciones del juego.

**Valor:** No obligatorio

## La ranura del inventario está llena (`is_inventory_slot_filled`)

**Propósito:** Comprueba si una ranura concreta del inventario contiene un objeto.

**Valor:** Obligatorio — Número de ranura (0-35 para el inventario principal, las ranuras 0-8 son la barra rápida)

## El objeto en el inventario está en hover (`is_item_hovered_in_inventory`)

**Propósito:** Comprueba si el cursor está sobre cualquier objeto en una pantalla de inventario.

**Valor:** No obligatorio

## El cursor está sosteniendo un objeto del inventario (`is_cursor_holding_inventory_item`)

**Propósito:** Comprueba si el cursor está sosteniendo actualmente una pila de objetos del inventario.

**Valor:** No obligatorio

## La ranura seleccionada de la barra rápida (`is_hotbar_slot_active`)

**Propósito:** Comprueba si una ranura concreta de la barra rápida está seleccionada actualmente.

**Valor:** Obligatorio — Número de ranura de la barra rápida (0-8)

## El jugador tiene nivel de permiso (`fancymenu_loading_requirement_has_player_permission_level`)

**Propósito:** Comprueba si el jugador tiene al menos el nivel de permiso/OP especificado en el mundo o servidor actual.

**Valor:** Obligatorio — Número de nivel de permiso (0-4, donde 4 es operador del servidor)

## La fuerza de ataque está debilitada (`is_attack_strength_weakened`)

**Propósito:** Comprueba si la fuerza de ataque del jugador está actualmente debilitada (no completamente cargada).

**Valor:** No obligatorio

## La hora real es de día (`fancymenu_visibility_requirement_is_realtime_day`)

**Propósito:** Comprueba si el día actual del mes en tiempo real coincide con un valor concreto.

**Valor:** Obligatorio — Número del día (1-31). Se pueden proporcionar varios valores separándolos con comas.

## La hora real es (`fancymenu_visibility_requirement_is_realtime_hour`)

**Propósito:** Comprueba si la hora actual en tiempo real coincide con un valor concreto.

**Valor:** Obligatorio — Hora en formato de 24 horas (0-23). Se pueden proporcionar varios valores separándolos con comas.

## El minuto real es (`fancymenu_visibility_requirement_is_realtime_minute`)

**Propósito:** Comprueba si el minuto actual en tiempo real coincide con un valor concreto.

**Valor:** Obligatorio — Minuto (0-59). Se pueden proporcionar varios valores separándolos con comas.

## El mes real es (`fancymenu_visibility_requirement_is_realtime_month`)

**Propósito:** Comprueba si el mes actual en tiempo real coincide con un valor concreto.

**Valor:** Obligatorio — Número del mes (1-12, donde 1 es enero). Se pueden proporcionar varios valores separándolos con comas.

## El segundo real es (`fancymenu_visibility_requirement_is_realtime_second`)

**Propósito:** Comprueba si el segundo actual en tiempo real coincide con un valor concreto.

**Valor:** Obligatorio — Segundo (0-59). Se pueden proporcionar varios valores separándolos con comas.

## El día real de la semana es (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Propósito:** Comprueba si el día actual de la semana en tiempo real coincide con un valor concreto.

**Valor:** Obligatorio — Día de la semana como número (1-7, donde 1 es domingo). Se pueden proporcionar varios valores separándolos con comas.

## El año real es (`fancymenu_visibility_requirement_is_realtime_year`)

**Propósito:** Comprueba si el año actual en tiempo real coincide con un valor concreto.

**Valor:** Obligatorio — Año completo (por ejemplo, "2023"). Se pueden proporcionar varios valores separándolos con comas.

## Existe archivo/carpeta (`fancymenu_loading_requirement_file_exists`)

**Propósito:** Comprueba si existe un archivo o directorio.

**Valor:** Obligatorio — Una ruta relativa al directorio de juego activo, o una ruta que empiece por `.minecraft/` para el directorio de Minecraft habitual. Tanto los archivos como los directorios cuentan como existentes.

## El SO es Linux (`fancymenu_loading_requirement_is_os_linux`)

**Propósito:** Comprueba si la plataforma actual no es ni Windows ni macOS. Normalmente corresponde a entornos Linux.

**Valor:** No obligatorio

## El SO es macOS (`fancymenu_loading_requirement_is_os_macos`)

**Propósito:** Comprueba si el sistema operativo es macOS.

**Valor:** No obligatorio

## El SO es Windows (`fancymenu_loading_requirement_is_os_windows`)

**Propósito:** Comprueba si el sistema operativo es Windows.

**Valor:** No obligatorio

## Hay conexión a Internet (`is_internet_connection_available`)

**Propósito:** Comprueba si hay una conexión a Internet activa disponible.

**Valor:** No obligatorio

## El idioma del juego es (`fancymenu_loading_requirement_is_language`)

**Propósito:** Comprueba si el idioma actual del juego coincide con un valor concreto.

**Valor:** Obligatorio — Código de idioma (por ejemplo, `en_us` para inglés)

## El mod está cargado (`fancymenu_loading_requirement_is_mod_loaded`)

**Propósito:** Comprueba si un mod concreto está cargado.

**Valor:** Obligatorio — ID del mod (por ejemplo, `fancymenu`, `jei`). También puedes comprobar OptiFine con `optifine`. Se admiten varios IDs de mod separados por comas; todos los mods listados deben estar cargados.

## MCEF está cargado (`is_mcef_loaded`)

**Propósito:** Comprueba si MCEF (Minecraft Chromium Embedded Framework) está instalado e inicializado. MCEF es necesario para el [elemento Browser](./elements#browser) y los [tipos de vídeo basados en MCEF obsoletos](./video#requirements); las [funciones nativas de vídeo](./video) usan Watermedia.

**Valor:** No obligatorio

## Es un número (`fancymenu_visibility_requirement_is_number`)

**Propósito:** Proporciona una comparación numérica avanzada con distintos modos de comparación.

**Valor:** Obligatorio — Formato complejo: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` donde `comparison_mode` puede ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` o `smaller-than-or-equals`

## Es texto (`fancymenu_visibility_requirement_is_text`)

**Propósito:** Proporciona una comparación de texto avanzada con distintos modos de comparación.

**Valor:** Obligatorio — Formato complejo: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` donde `comparison_mode` puede ser `equals`, `contains`, `starts-with` o `ends-with`

## La IP del servidor es (`fancymenu_visibility_requirement_is_server_ip`)

**Propósito:** Comprueba si la IP del servidor actual coincide con un valor concreto.

**Valor:** Obligatorio — Dirección IP del servidor (con o sin puerto)

## El servidor está en línea (`fancymenu_loading_requirement_is_server_online`)

**Propósito:** Comprueba si un servidor concreto está en línea y es accesible.

**Valor:** Obligatorio — Dirección IP del servidor (con o sin puerto)

## El paquete de recursos está activado (`is_resource_pack_enabled`)

**Propósito:** Comprueba si un paquete de recursos concreto está seleccionado/activo actualmente.

**Valor:** Obligatorio — Título del paquete de recursos o ID del paquete (por ejemplo, `Programmer Art` o el ID del paquete)

## El valor de la variable (variable de FM) (`fancymenu_visibility_requirement_is_variable_value`)

**Propósito:** Comprueba si una variable de FancyMenu tiene un valor concreto.

**Valor:** Obligatorio — Formato: "variable_name:expected_value"

## Solo una vez por sesión (`once_per_session`)

**Propósito:** Cada instancia configurada devuelve true una vez por sesión de juego. Las distintas instancias se registran de forma independiente.

**Valor:** No obligatorio
