---
title: Condiciones (requisitos)
description: Cómo usar los requisitos de carga.
---
# Requisitos

Los requisitos (llamados **Requisitos de carga** en algunos menús) muestran u ocultan contenido según condiciones como el estado de desplazamiento del cursor, el tamaño de la ventana o si hay un mundo cargado.

Puedes usarlos en [elementos](./elements), diseños completos y [scripts de acciones](./action-scripts).

# Agregar requisitos a elementos

Para agregar requisitos a un elemento, haz clic derecho en él y selecciona **Requisitos de carga**.

Los requisitos se comprueban mientras el menú está abierto, por lo que los elementos se actualizan cuando cambia una condición.

# Requisitos para todo el diseño

También puedes cambiar la visibilidad de diseños completos haciendo clic derecho en el **fondo del editor** y seleccionando **Requisitos de carga [para todo el diseño]**.

Cuando cambia el resultado de un requisito para todo el diseño, FancyMenu reconstruye la pantalla actual y aplica los diseños cuyos requisitos ahora se cumplen.

# Scripts de acciones

Los requisitos también se pueden usar en scripts de acciones.
Puedes agregarlos en la pantalla del editor de scripts de acciones y usarlos para ejecutar acciones específicas solo si se cumple la condición del requisito.

# Combinar requisitos

- Los requisitos fuera de los grupos usan **AND**, por lo que todos deben cumplirse.
- Dentro de un grupo, elige **AND** u **OR**.
- Usa **IF NOT** para invertir un requisito.

Estas reglas son las mismas para elementos, diseños y scripts de acciones.

# Valores de los requisitos

Para los requisitos que necesitan un valor, usa **Editar valor del requisito** y sigue la descripción que se muestra en el editor. Algunos campos admiten autocompletado con **TAB**.

Si un requisito importado deja de funcionar después de cambiar FancyMenu o algún complemento, edítalo en la pantalla de requisitos y revisa `logs/latest.log` en busca de errores.

El editor de requisitos admite un menú contextual con clic derecho, navegación mediante el teclado, búsqueda, deshacer/rehacer (`Ctrl/Command + Z` / `Ctrl/Command + Y`) y `Ctrl/Command + S` para guardar.

# Requisitos en detalle

Esta sección enumera los requisitos integrados de FancyMenu.

## El cursor está sobre el elemento (`fancymenu_visibility_requirement_is_element_hovered`)

**Propósito:** Comprueba si el cursor del mouse está sobre un elemento específico.

**Valor:** Obligatorio — [Identificador del elemento](./element-identifiers) del elemento objetivo (por ejemplo, `some_element_ID`).

## El elemento tiene el foco (`is_element_focused`)

**Propósito:** Comprueba si un elemento específico tiene actualmente el foco del teclado (por ejemplo, un campo de texto o un botón enfocado).

**Valor:** Obligatorio — ID del elemento objetivo (el mismo ID que se muestra en el editor).

> [!NOTE]
> El foco y el estado de desplazamiento del cursor son diferentes. Un elemento puede conservar su apariencia de enfocado después de que el cursor se aleje; hacer clic o navegar con el teclado puede darle el foco.

## El cursor está sobre cualquier elemento (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Propósito:** Comprueba los elementos visibles/renderizables de la capa de personalización activa actual, incluidos los elementos aportados por diseños apilados.

**Valor:** No requerido

## El cursor está sobre cualquier botón (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Propósito:** Comprueba si el cursor está sobre cualquier botón visible/renderizable de Minecraft o personalizado en la capa de personalización activa actual, incluidos los botones aportados por diseños apilados.

**Valor:** No requerido

## El diseño está habilitado (`fancymenu_visibility_requirement_is_layout_enabled`)

**Propósito:** Comprueba si un diseño específico está habilitado actualmente.

**Valor:** Obligatorio — Nombre del diseño (por ejemplo, `my_cool_main_menu_layout`).

## El programador está ejecutándose (`fancymenu_visibility_requirement_is_scheduler_running`)

**Propósito:** Comprueba si un [programador](./schedulers) está ejecutándose actualmente.

**Valor:** Obligatorio — ID del programador (por ejemplo, `my_scheduler`).

## La escala de la interfaz es (`fancymenu_loading_requirement_is_gui_scale`)

**Propósito:** Comprueba si la escala actual de la interfaz coincide con ciertas condiciones.

**Valor:** Obligatorio — Usa un número para igualdad, `>` para mayor que o `<` para menor que.

Varias condiciones separadas por comas se combinan con AND. Por ejemplo, `>1,<4` solo se cumple cuando la escala de la interfaz es mayor que `1` y menor que `4`.

## El botón está activo (`fancymenu_visibility_requirement_is_button_active`)

**Propósito:** Comprueba si un botón específico está activo (se puede hacer clic en él).

**Valor:** Obligatorio — ID del elemento del botón objetivo (por ejemplo, "some_element_ID").

## El título de la pantalla es (`is_menu_title`)

**Propósito:** Comprueba si el título visible de la pantalla coincide con un texto específico o una clave de localización. Solo comprobará el nombre/título visible de la pantalla, como "Opciones" o "Pausa". ¡NO comprobará el identificador del menú o la pantalla (como `title_screen`)!

**Valor:** Obligatorio — Texto exacto del título o clave de localización de la pantalla.

## La tecla está presionada (`is_key_pressed`)

**Propósito:** Comprueba si se está presionando actualmente una tecla específica del teclado.

**Valor:** Obligatorio — Código de la tecla objetivo. Se selecciona mediante una interfaz al editar el valor del requisito.

## Hay alguna pantalla abierta (`is_any_screen_open`)

**Propósito:** Comprueba si hay alguna pantalla/menú abierto actualmente (devuelve false si no se muestra ninguna pantalla).

**Valor:** No requerido

## La superposición de depuración de Minecraft está habilitada (`is_debug_overlay_enabled`)

**Propósito:** Comprueba si la superposición de depuración de F3 está visible actualmente.

**Valor:** No requerido

## El tipo de cursor activo es (`is_active_cursor_type`)

**Propósito:** Comprueba si el tipo de cursor activo de FancyMenu coincide con un tipo de cursor estándar específico.

**Valor:** Obligatorio — Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` o `not_allowed`.

## La barra del menú de personalización está visible (`is_customization_menu_bar_visible`)

**Propósito:** Comprueba si la barra del menú de personalización de FancyMenu está visible actualmente.

**Valor:** No requerido

## El modo de modpack está habilitado (`is_modpack_mode_enabled`)

**Propósito:** Comprueba si el modo de modpack de FancyMenu está habilitado.

**Valor:** No requerido

## El botón del mouse está presionado (`mouse_click`)

**Propósito:** Devuelve true mientras se mantenga presionado un botón específico del mouse. No es un evento de clic de una sola ejecución; usa el [listener **Al hacer clic en un botón del mouse**](./listeners#on-mouse-button-clicked-mouse_button_clicked) cuando una acción deba ejecutarse una vez por clic.

**Valor:** Obligatorio — `left` o `right` para indicar qué botón del mouse se debe comprobar.

## Está en pantalla completa (`fancymenu_loading_requirement_is_fullscreen`)

**Propósito:** Comprueba si el juego está actualmente en modo de pantalla completa.

**Valor:** No requerido

## El ancho de la ventana es (`fancymenu_loading_requirement_is_window_width`)

**Propósito:** Comprueba si el ancho de la ventana del juego coincide con valores específicos.

**Valor:** Obligatorio — Ancho de la ventana en píxeles (por ejemplo, "1920"). Puedes proporcionar varios valores separándolos con comas.

## El alto de la ventana es (`fancymenu_loading_requirement_is_window_height`)

**Propósito:** Comprueba si el alto de la ventana del juego coincide con valores específicos.

**Valor:** Obligatorio — Alto de la ventana en píxeles (por ejemplo, "1080"). Puedes proporcionar varios valores separándolos con comas.

## El ancho de la ventana es mayor que (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Propósito:** Comprueba si el ancho de la ventana del juego es mayor que un valor específico.

**Valor:** Obligatorio — Ancho de la ventana en píxeles (por ejemplo, "1920").

## El alto de la ventana es mayor que (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Propósito:** Comprueba si el alto de la ventana del juego es mayor que un valor específico.

**Valor:** Obligatorio — Alto de la ventana en píxeles (por ejemplo, "1080").

## Es multijugador (`fancymenu_loading_requirement_is_multiplayer`)

**Propósito:** Comprueba si el jugador está actualmente en un mundo multijugador.

**Valor:** No requerido

## Es de un jugador (`fancymenu_loading_requirement_is_singpleplayer`)

**Propósito:** Comprueba si el jugador está actualmente en un mundo de un solo jugador.

**Valor:** No requerido

## Hay un mundo cargado (`fancymenu_loading_requirement_is_world_loaded`)

**Propósito:** Comprueba si hay algún mundo cargado actualmente.

**Valor:** No requerido

## Está en modo aventura (`fancymenu_visibility_requirement_is_adventure`)

**Propósito:** Comprueba si el jugador está actualmente en el modo de juego Aventura.

**Valor:** No requerido

## Está en modo creativo (`fancymenu_visibility_requirement_is_creative`)

**Propósito:** Comprueba si el jugador está actualmente en el modo de juego Creativo.

**Valor:** No requerido

## Está en modo espectador (`fancymenu_visibility_requirement_is_spectator`)

**Propósito:** Comprueba si el jugador está actualmente en el modo de juego Espectador.

**Valor:** No requerido

## Está en modo supervivencia (`fancymenu_visibility_requirement_is_survival`)

**Propósito:** Comprueba si el jugador está actualmente en el modo de juego Supervivencia.

**Valor:** No requerido

## El modo de juego es (`is_gamemode`)

**Propósito:** Comprueba si el jugador está en un modo de juego específico.

**Valor:** Obligatorio — Nombre del modo de juego (por ejemplo, "creative", "survival", "adventure", "spectator").

## La dificultad es (`is_difficulty`)

**Propósito:** Comprueba si la dificultad actual del juego coincide con un valor específico.

**Valor:** Obligatorio — Nombre de la dificultad (por ejemplo, "peaceful", "easy", "normal", "hard").

## Es hardcore (`is_hardcore`)

**Propósito:** Comprueba si el mundo cargado actualmente está en modo extremo.

**Valor:** No requerido

## La perspectiva de la cámara es (`is_camera_perspective`)

**Propósito:** Comprueba si la perspectiva actual de la cámara coincide con una perspectiva específica.

**Valor:** Obligatorio — `first_person`, `third_person_back` o `third_person_front`.

## Está lloviendo (`is_raining`)

**Propósito:** Comprueba si está lloviendo actualmente en la ubicación del jugador.

**Valor:** No requerido

## Hay tormenta eléctrica (`is_thundering`)

**Propósito:** Comprueba si hay actualmente una tormenta eléctrica en el mundo del jugador.

**Valor:** No requerido

## El clima está despejado (`is_clear_weather`)

**Propósito:** Comprueba si el clima está despejado actualmente (no está lloviendo ni hay tormenta eléctrica).

**Valor:** No requerido

## Está nevando (`is_snowing`)

**Propósito:** Comprueba si está nevando actualmente en la ubicación del jugador.

**Valor:** No requerido

## El jugador está corriendo (`is_player_running`)

**Propósito:** Comprueba si el jugador está corriendo actualmente.

**Valor:** No requerido

## El jugador está agachado (`is_player_sneaking`)

**Propósito:** Comprueba si el jugador está agachado actualmente.

**Valor:** No requerido

## El jugador está usando un objeto (`is_player_using_item`)

**Propósito:** Comprueba si el jugador está usando un objeto actualmente.

**Valor:** No requerido

## El jugador está nadando (`is_player_swimming`)

**Propósito:** Comprueba si el jugador está nadando actualmente.

**Valor:** No requerido

## El jugador está saltando o cayendo (`is_player_jumping`)

**Propósito:** Devuelve true mientras el jugador está en el aire en un estado normal de salto o caída. Se excluyen nadar, los fluidos, volar con élitros, dormir, nadar visualmente y gatear.

**Valor:** No requerido

## El jugador está bajo el agua (`is_player_under_water`)

**Propósito:** Comprueba si el jugador está completamente bajo el agua.

**Valor:** No requerido

## El jugador está en el agua (`is_player_in_water`)

**Propósito:** Comprueba si el jugador está en el agua (puede estar parcialmente sumergido).

**Valor:** No requerido

## El jugador está en lava (`is_player_in_lava`)

**Propósito:** Comprueba si el jugador está en lava.

**Valor:** No requerido

## El jugador está en un fluido (`is_player_in_fluid`)

**Propósito:** Comprueba si el jugador está en cualquier fluido (agua, lava, etc.).

**Valor:** No requerido

## El jugador monta una entidad/vehículo (`is_player_riding_entity`)

**Propósito:** Comprueba si el jugador está montando cualquier entidad.

**Valor:** No requerido

## El jugador monta una entidad que puede saltar (`is_player_riding_jumpable_entity`)

**Propósito:** Comprueba si el jugador está montando una entidad que puede saltar (como un caballo).

**Valor:** No requerido

## El jugador monta una entidad con vida (`is_player_riding_entity_with_health`)

**Propósito:** Comprueba si el jugador está montando una entidad viva con salud (como un animal, pero no una lancha).

**Valor:** No requerido

## El jugador está en nieve polvo (`is_player_in_powder_snow`)

**Propósito:** Comprueba si el jugador está actualmente en nieve polvo.

**Valor:** No requerido

## El jugador estuvo en nieve polvo (`was_player_in_powder_snow`)

**Propósito:** Comprueba si el jugador estuvo en nieve polvo (se usa para efectos que persisten después de salir).

**Valor:** No requerido

## El jugador lleva una calabaza (`is_player_wearing_pumpkin`)

**Propósito:** Comprueba si el jugador lleva una calabaza tallada en la cabeza.

**Valor:** No requerido

## El jugador vuela con élitros (`is_player_flying_with_elytra`)

**Propósito:** Comprueba si el jugador está volando actualmente con élitros.

**Valor:** No requerido

## El jugador vuela en creativo (`is_player_creative_flying`)

**Propósito:** Comprueba si el jugador está volando en modo creativo.

**Valor:** No requerido

## El jugador tiene corazones de absorción (`has_player_absorption_hearts`)

**Propósito:** Comprueba si el jugador tiene corazones de absorción (corazones dorados).

**Valor:** No requerido

## El jugador tiene el efecto de marchitez (`is_player_withered`)

**Propósito:** Comprueba si el jugador está afectado por el efecto de marchitez.

**Valor:** No requerido

## El jugador está completamente congelado (`is_player_fully_frozen`)

**Propósito:** Comprueba si el jugador está completamente congelado (normalmente por la nieve polvo).

**Valor:** No requerido

## El jugador está envenenado (`is_player_poisoned`)

**Propósito:** Comprueba si el jugador está afectado por el efecto de veneno.

**Valor:** No requerido

## El jugador está en un bioma (`is_player_in_biome`)

**Propósito:** Comprueba si el jugador está en un bioma específico.

**Valor:** Obligatorio — Identificador del bioma (por ejemplo, `minecraft:birch_forest`).

## El jugador está en una dimensión (`is_player_in_dimension`)

**Propósito:** Comprueba si el jugador está en una dimensión específica.

**Valor:** Obligatorio — Identificador de la dimensión (por ejemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`).

## El jugador está en una estructura (`is_player_in_structure`)

**Propósito:** Comprueba si el jugador está dentro de una estructura específica. Para mundos de servidor, FancyMenu debe estar instalado en el servidor.

**Valor:** Obligatorio — Identificador de la estructura (por ejemplo, `minecraft:village`).

## Hay una entidad cerca (`is_entity_nearby`)

**Propósito:** Comprueba si un tipo de entidad específico se encuentra dentro de cierto radio del jugador.

**Valor:** Obligatorio — Formato: "radio:identificador_de_entidad" (por ejemplo, `10:minecraft:pig`; comprueba si hay cerdos a menos de 10 bloques).

## Hay un efecto activo (`is_effect_active`)

**Propósito:** Comprueba si un efecto de poción específico está activo en el jugador.

**Valor:** Obligatorio — Identificador del efecto (por ejemplo, `minecraft:speed`, `minecraft:strength`).

## Hay algún efecto activo (`is_any_effect_active`)

**Propósito:** Comprueba si el jugador tiene algún efecto de poción activo.

**Valor:** No requerido

## El jugador es zurdo (`is_left_handed`)

**Propósito:** Comprueba si el jugador está configurado en modo zurdo en las opciones del juego.

**Valor:** No requerido

## El espacio del inventario está ocupado (`is_inventory_slot_filled`)

**Propósito:** Comprueba si un espacio específico del inventario contiene un objeto.

**Valor:** Obligatorio — Número del espacio (0-35 para el inventario principal; los espacios 0-8 son la barra rápida).

## Hay un objeto bajo el cursor en el inventario (`is_item_hovered_in_inventory`)

**Propósito:** Comprueba si el cursor está sobre cualquier objeto en una pantalla de inventario.

**Valor:** No requerido

## El cursor sostiene un objeto del inventario (`is_cursor_holding_inventory_item`)

**Propósito:** Comprueba si el cursor está sosteniendo actualmente una pila de objetos del inventario.

**Valor:** No requerido

## El espacio de la barra rápida está seleccionado (`is_hotbar_slot_active`)

**Propósito:** Comprueba si un espacio específico de la barra rápida está seleccionado actualmente.

**Valor:** Obligatorio — Número del espacio de la barra rápida (0-8).

## El jugador tiene un nivel de permisos (`fancymenu_loading_requirement_has_player_permission_level`)

**Propósito:** Comprueba si el jugador tiene al menos el nivel de permisos/operador especificado en el mundo o servidor actual.

**Valor:** Obligatorio — Número del nivel de permisos (0-4, donde 4 corresponde a un operador del servidor).

## La fuerza de ataque está debilitada (`is_attack_strength_weakened`)

**Propósito:** Comprueba si la fuerza de ataque del jugador está debilitada actualmente (no está completamente cargada).

**Valor:** No requerido

## Es el día de la fecha real (`fancymenu_visibility_requirement_is_realtime_day`)

**Propósito:** Comprueba si el día actual del mes en el mundo real coincide con un valor específico.

**Valor:** Obligatorio — Número del día (1-31). Puedes proporcionar varios valores separándolos con comas.

## Es la hora real (`fancymenu_visibility_requirement_is_realtime_hour`)

**Propósito:** Comprueba si la hora actual en el mundo real coincide con un valor específico.

**Valor:** Obligatorio — Hora en formato de 24 horas (0-23). Puedes proporcionar varios valores separándolos con comas.

## Es el minuto real (`fancymenu_visibility_requirement_is_realtime_minute`)

**Propósito:** Comprueba si el minuto actual en el mundo real coincide con un valor específico.

**Valor:** Obligatorio — Minuto (0-59). Puedes proporcionar varios valores separándolos con comas.

## Es el mes real (`fancymenu_visibility_requirement_is_realtime_month`)

**Propósito:** Comprueba si el mes actual en el mundo real coincide con un valor específico.

**Valor:** Obligatorio — Número del mes (1-12, donde 1 es enero). Puedes proporcionar varios valores separándolos con comas.

## Es el segundo real (`fancymenu_visibility_requirement_is_realtime_second`)

**Propósito:** Comprueba si el segundo actual en el mundo real coincide con un valor específico.

**Valor:** Obligatorio — Segundo (0-59). Puedes proporcionar varios valores separándolos con comas.

## Es el día de la semana real (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Propósito:** Comprueba si el día actual de la semana en el mundo real coincide con un valor específico.

**Valor:** Obligatorio — Día de la semana como número (1-7, donde 1 es domingo). Puedes proporcionar varios valores separándolos con comas.

## Es el año real (`fancymenu_visibility_requirement_is_realtime_year`)

**Propósito:** Comprueba si el año actual en el mundo real coincide con un valor específico.

**Valor:** Obligatorio — Año completo (por ejemplo, "2023"). Puedes proporcionar varios valores separándolos con comas.

## Existe el archivo o la carpeta (`fancymenu_loading_requirement_file_exists`)

**Propósito:** Comprueba si existe un archivo o directorio.

**Valor:** Obligatorio — Una ruta relativa al directorio activo del juego o una ruta que comience con `.minecraft/` para el directorio convencional de Minecraft. Tanto los archivos como los directorios cuentan como existentes.

## El sistema operativo es Linux (`fancymenu_loading_requirement_is_os_linux`)

**Propósito:** Comprueba si la plataforma actual no es Windows ni macOS. Normalmente corresponde a entornos Linux.

**Valor:** No requerido

## El sistema operativo es macOS (`fancymenu_loading_requirement_is_os_macos`)

**Propósito:** Comprueba si el sistema operativo es macOS.

**Valor:** No requerido

## El sistema operativo es Windows (`fancymenu_loading_requirement_is_os_windows`)

**Propósito:** Comprueba si el sistema operativo es Windows.

**Valor:** No requerido

## Hay conexión a Internet (`is_internet_connection_available`)

**Propósito:** Comprueba si hay una conexión activa a Internet disponible.

**Valor:** No requerido

## El idioma del juego es (`fancymenu_loading_requirement_is_language`)

**Propósito:** Comprueba si el idioma actual del juego coincide con un valor específico.

**Valor:** Obligatorio — Código del idioma (por ejemplo, `en_us` para inglés).

## El mod está cargado (`fancymenu_loading_requirement_is_mod_loaded`)

**Propósito:** Comprueba si hay un mod específico cargado.

**Valor:** Obligatorio — ID del mod (por ejemplo, `fancymenu`, `jei`). También puedes comprobar si OptiFine está cargado con `optifine`. Se admiten varios ID de mods separados por comas; todos los mods indicados deben estar cargados.

## Rinku está cargado (`is_rinku_loaded`)

**Propósito:** Comprueba si [Rinku](https://modrinth.com/mod/rinku) está instalado e inicializado. [Rinku](https://modrinth.com/mod/rinku) es necesario para el [elemento de navegador](./elements#browser) y los [tipos de video obsoletos basados en Rinku](./video#requirements); las [funciones de video nativas](./video) usan Watermedia.

**Valor:** No requerido

## Es un número (`fancymenu_visibility_requirement_is_number`)

**Propósito:** Proporciona una comparación numérica avanzada con diferentes modos de comparación.

**Valor:** Obligatorio — Formato complejo: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`, donde `comparison_mode` puede ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` o `smaller-than-or-equals`.

## Es texto (`fancymenu_visibility_requirement_is_text`)

**Propósito:** Proporciona una comparación de texto avanzada con diferentes modos de comparación.

**Valor:** Obligatorio — Formato complejo: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`, donde `comparison_mode` puede ser `equals`, `contains`, `starts-with` o `ends-with`.

## La IP del servidor es (`fancymenu_visibility_requirement_is_server_ip`)

**Propósito:** Comprueba si la IP del servidor actual coincide con un valor específico.

**Valor:** Obligatorio — Dirección IP del servidor (con o sin puerto).

## El servidor está en línea (`fancymenu_loading_requirement_is_server_online`)

**Propósito:** Comprueba si un servidor específico está en línea y es accesible.

**Valor:** Obligatorio — Dirección IP del servidor (con o sin puerto).

## El paquete de recursos está habilitado (`is_resource_pack_enabled`)

**Propósito:** Comprueba si un paquete de recursos específico está seleccionado/activo actualmente.

**Valor:** Obligatorio — Título del paquete de recursos o ID del paquete (por ejemplo, `Programmer Art` o el ID del paquete).

## El valor de la variable es (variable de FM) (`fancymenu_visibility_requirement_is_variable_value`)

**Propósito:** Comprueba si una variable de FancyMenu tiene un valor específico.

**Valor:** Obligatorio — Formato: "nombre_de_variable:valor_esperado".

## Solo una vez por sesión (`once_per_session`)

**Propósito:** Cada instancia configurada devuelve true una vez por sesión de juego. Las distintas instancias se rastrean de forma independiente.

**Valor:** No requerido
