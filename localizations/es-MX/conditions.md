---
title: Condiciones (Requisitos)
description: Cómo usar requisitos de carga.
---

# Requisitos
Los requisitos (también conocidos como "requisitos de carga") te permiten hacer que partes de tus diseños sean visibles o invisibles según distintas condiciones, como si un elemento está en hover, si la ventana tiene un tamaño específico o si actualmente estás en un mundo.

También se pueden usar en scripts de acción de botones, deslizadores, marcadores y todo lo demás que tenga una entrada de script de acción.

# Agregar requisitos a elementos
Para agregar uno o más requisitos a elementos, solo haz clic derecho sobre el elemento y luego en **Requisitos de carga**.

# Requisitos para todo el diseño
También puedes cambiar la visibilidad de diseños completos haciendo clic derecho en el **fondo del editor** y después en **Requisitos de carga [Todo el diseño]**.

# Scripts de acción
Los requisitos también se pueden usar en scripts de acción.
Puedes agregarlos en la pantalla del editor de scripts de acción y usarlos para ejecutar acciones específicas solo si se cumple la condición del requisito.

# Valores del requisito
Algunos requisitos necesitan que configures ciertos valores para funcionar correctamente. Si ese es el caso, la pantalla del requisito debería indicarte que primero configures todos los valores, pero si no, solo revisa si el botón **Editar valor del requisito** se puede hacer clic cuando agregues el requisito.
Siempre revisa la descripción del requisito si no estás seguro de qué poner como valor.
Algunas entradas de valor incluso admiten **autocompletado con TAB**.

FancyMenu 3.9.0 rediseña la ventana de Administrar requisitos para usar un menú contextual con clic derecho, navegación con teclado, búsqueda, deshacer/rehacer (`CTRL + Z` / `CTRL + Y`) y `CTRL + S` como atajo de **Listo**.

# Requisitos en detalle
La siguiente lista contiene la mayoría, si no es que todos, los requisitos disponibles en FancyMenu. Es posible que la lista a veces quede un poco desactualizada debido a actualizaciones del mod.

## El elemento está en hover
Comprueba si un elemento específico está en hover por el cursor del mouse.  
**Valor requerido**: Sí - ID del elemento objetivo (por ejemplo, `some_element_ID`). Puedes obtener el ID haciendo clic derecho en un elemento en el editor.

## El elemento tiene foco
Comprueba si un elemento específico actualmente tiene el foco del teclado (por ejemplo, un campo de texto o un botón con foco).
**Valor requerido**: Sí - ID del elemento objetivo (el mismo ID que se muestra en el editor)

> Esto no es lo mismo que cuando un elemento solo está en hover, aunque se vea similar. Los elementos con foco siguen pareciendo "en hover" incluso cuando ya no lo están. Los elementos reciben foco al hacer clic en ellos o al usar el teclado para navegar en menús.
{.is-info}

## Cualquier elemento está en hover
Comprueba si cualquier elemento del diseño está actualmente en hover por el cursor del mouse.  
**Valor requerido**: No

## Cualquier botón está en hover
Comprueba si cualquier botón (vanilla o personalizado) está actualmente en hover por el cursor del mouse.  
**Valor requerido**: No

## El diseño está habilitado
Comprueba si un diseño específico está actualmente habilitado.  
**Valor requerido**: Sí - El nombre del diseño (por ejemplo, `my_cool_main_menu_layout`)

## El programador está en ejecución
Comprueba si un programador está actualmente en ejecución.
**Valor requerido**: Sí - ID del programador (por ejemplo, `my_scheduler`)

## Escala de GUI
Comprueba si la escala actual de la GUI coincide con ciertas condiciones.  
**Valor requerido**: Sí - Puede aceptar valores numéricos como `1`, `2`, etc.

## El botón está activo
Comprueba si un botón específico está activo (se puede hacer clic).  
**Valor requerido**: Sí - ID del elemento del botón objetivo (por ejemplo, "some_element_ID")

## El título de la pantalla coincide
Comprueba si el título EN PANTALLA de la pantalla coincide con un texto específico o una clave de localización. Esto solo revisará el nombre visible/título de la pantalla, como "Opciones" o "Pausa". ¡NO revisará el identificador del menú/pantalla (como `title_screen`)!

**Valor requerido**: Sí - El texto exacto del título o la clave de localización de la pantalla

## Se presiona una tecla
Comprueba si una tecla específica del teclado se está presionando actualmente.  
**Valor requerido**: Sí - El código de la tecla objetivo. Se selecciona mediante una interfaz al editar el valor del requisito.

## Cualquier pantalla está abierta
Comprueba si cualquier pantalla/menú está abierta actualmente (devuelve false si no se muestra ninguna pantalla).  
**Valor requerido**: No

## El overlay de depuración de MC está habilitado
Comprueba si el overlay de depuración F3 está visible actualmente.
**Valor requerido**: No

## Tipo de cursor activo
Comprueba si el tipo de cursor actualmente activo de FancyMenu coincide con un tipo estándar específico.
**Valor requerido**: Sí - Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` o `not_allowed`

## La barra del menú de personalización está visible
Comprueba si la barra del menú de personalización de FancyMenu está visible actualmente.
**Valor requerido**: No

## El modo de modpack está habilitado
Comprueba si el Modo Modpack de FancyMenu está habilitado.
**Valor requerido**: No

## Se hizo clic con el mouse
Comprueba si se está presionando un botón específico del mouse.  
**Valor requerido**: Sí - `left` o `right` para indicar qué botón del mouse revisar

## Está en pantalla completa
Comprueba si el juego está actualmente en modo de pantalla completa.  
**Valor requerido**: No

## Ancho de la ventana
Comprueba si el ancho de la ventana del juego coincide con valores específicos.  
**Valor requerido**: Sí - Ancho de la ventana en píxeles (por ejemplo, "1920"). Se pueden proporcionar varios valores separándolos con comas.

## Alto de la ventana
Comprueba si la altura de la ventana del juego coincide con valores específicos.  
**Valor requerido**: Sí - Altura de la ventana en píxeles (por ejemplo, "1080"). Se pueden proporcionar varios valores separándolos con comas.

## El ancho de la ventana es mayor que
Comprueba si el ancho de la ventana del juego es mayor que un valor específico.  
**Valor requerido**: Sí - Ancho de la ventana en píxeles (por ejemplo, "1920")

## El alto de la ventana es mayor que
Comprueba si la altura de la ventana del juego es mayor que un valor específico.  
**Valor requerido**: Sí - Altura de la ventana en píxeles (por ejemplo, "1080")

## Está en multijugador
Comprueba si el jugador está actualmente en un mundo multijugador.  
**Valor requerido**: No

## Está en un jugador
Comprueba si el jugador está actualmente en un mundo de un solo jugador.  
**Valor requerido**: No

## El mundo está cargado
Comprueba si actualmente hay algún mundo cargado.  
**Valor requerido**: No

## Es aventura
Comprueba si el jugador está actualmente en modo de juego aventura.  
**Valor requerido**: No

## Es creativo
Comprueba si el jugador está actualmente en modo de juego creativo.  
**Valor requerido**: No

## Es espectador
Comprueba si el jugador está actualmente en modo de juego espectador.  
**Valor requerido**: No

## Es supervivencia
Comprueba si el jugador está actualmente en modo de juego supervivencia.  
**Valor requerido**: No

## Es modo de juego
Comprueba si el jugador está en un modo de juego específico.  
**Valor requerido**: Sí - Nombre del modo de juego (por ejemplo, "creative", "survival", "adventure", "spectator")

## Es dificultad
Comprueba si la dificultad actual del juego coincide con un valor específico.  
**Valor requerido**: Sí - Nombre de la dificultad (por ejemplo, "peaceful", "easy", "normal", "hard")

## Es hardcore
Comprueba si el mundo cargado actualmente está en modo hardcore.
**Valor requerido**: No

## Es perspectiva de cámara
Comprueba si la perspectiva actual de la cámara coincide con una perspectiva específica.
**Valor requerido**: Sí - `first_person`, `third_person_back` o `third_person_front`

## Está lloviendo
Comprueba si actualmente está lloviendo en la ubicación del jugador.  
**Valor requerido**: No

## Está tronando
Comprueba si actualmente hay una tormenta eléctrica en el mundo del jugador.  
**Valor requerido**: No

## El clima está despejado
Comprueba si el clima actualmente está despejado (sin lluvia ni tormenta eléctrica).  
**Valor requerido**: No

## Está nevando
Comprueba si actualmente está nevando en la ubicación del jugador.  
**Valor requerido**: No

## El jugador está corriendo
Comprueba si el jugador actualmente está esprintando.  
**Valor requerido**: No

## El jugador está agachado
Comprueba si el jugador actualmente está agachado/en cuclillas.  
**Valor requerido**: No

## El jugador está usando un objeto
Comprueba si el jugador actualmente está usando un objeto.
**Valor requerido**: No

## El jugador está nadando
Comprueba si el jugador actualmente está nadando.  
**Valor requerido**: No

## El jugador está saltando o cayendo
Comprueba si el jugador actualmente está saltando.  
**Valor requerido**: No

## El jugador está bajo el agua
Comprueba si el jugador está completamente bajo el agua.  
**Valor requerido**: No

## El jugador está en el agua
Comprueba si el jugador está en el agua (puede estar parcialmente sumergido).  
**Valor requerido**: No

## El jugador está en lava
Comprueba si el jugador está en lava.  
**Valor requerido**: No

## El jugador está en un fluido
Comprueba si el jugador está en cualquier fluido (agua, lava, etc.).  
**Valor requerido**: No

## El jugador está montado en una entidad/vehículo
Comprueba si el jugador está montado en alguna entidad.  
**Valor requerido**: No

## El jugador está montado en una entidad que puede saltar
Comprueba si el jugador está montado en una entidad que puede saltar (como un caballo).  
**Valor requerido**: No

## El jugador está montado en una entidad con vida
Comprueba si el jugador está montado en una entidad viviente con vida (como animales, no botes).  
**Valor requerido**: No

## El jugador está en nieve en polvo
Comprueba si el jugador actualmente está en nieve en polvo.  
**Valor requerido**: No

## El jugador estuvo en nieve en polvo
Comprueba si el jugador estuvo en nieve en polvo (se usa para efectos que persisten después de salir).  
**Valor requerido**: No

## El jugador lleva una calabaza
Comprueba si el jugador lleva una calabaza tallada en la cabeza.  
**Valor requerido**: No

## El jugador está volando con alas de elytra
Comprueba si el jugador actualmente está volando con una elytra.  
**Valor requerido**: No

## El jugador vuela en creativo
Comprueba si el jugador está volando en modo creativo.  
**Valor requerido**: No

## El jugador tiene corazones de absorción
Comprueba si el jugador tiene algún corazón de absorción (corazones dorados).  
**Valor requerido**: No

## El jugador está con wither
Comprueba si el jugador está afectado por el efecto wither.  
**Valor requerido**: No

## El jugador está completamente congelado
Comprueba si el jugador está completamente congelado (normalmente por nieve en polvo).  
**Valor requerido**: No

## El jugador está envenenado
Comprueba si el jugador está afectado por el efecto de veneno.  
**Valor requerido**: No

## El jugador está en un bioma
Comprueba si el jugador está en un bioma específico.  
**Valor requerido**: Sí - Identificador del bioma (por ejemplo, `minecraft:birch_forest`)

## El jugador está en una dimensión
Comprueba si el jugador está en una dimensión específica.  
**Valor requerido**: Sí - Identificador de la dimensión (por ejemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## El jugador está en una estructura
Comprueba si el jugador se encuentra actualmente dentro de una estructura específica. Requiere FancyMenu en el servidor para mundos de servidor.
**Valor requerido**: Sí - Identificador de la estructura (por ejemplo, `minecraft:village`)

## Hay una entidad cerca
Comprueba si un tipo específico de entidad está dentro de cierto radio del jugador.  
**Valor requerido**: Sí - Formato: "radio:entity_id" (por ejemplo, `10:minecraft:pig` - revisa si hay cerdos dentro de 10 bloques)

## El efecto está activo
Comprueba si el jugador tiene activo un efecto de poción específico.  
**Valor requerido**: Sí - Identificador del efecto (por ejemplo, `minecraft:speed`, `minecraft:strength`)

## Cualquier efecto está activo
Comprueba si el jugador tiene activo algún efecto de poción.  
**Valor requerido**: No

## El jugador es zurdo
Comprueba si el jugador tiene activado el modo zurdo en las opciones del juego.  
**Valor requerido**: No

## La ranura del inventario está llena
Comprueba si una ranura específica del inventario contiene un objeto.  
**Valor requerido**: Sí - Número de ranura (0-35 para el inventario principal, las ranuras 0-8 son la barra rápida)

## El objeto está en hover en el inventario
Comprueba si el cursor está en hover sobre cualquier objeto en una pantalla de inventario.
**Valor requerido**: No

## El cursor tiene un objeto del inventario
Comprueba si el cursor actualmente está sosteniendo una pila de objetos del inventario.
**Valor requerido**: No

## La ranura de la barra rápida está seleccionada
Comprueba si una ranura específica de la barra rápida está seleccionada actualmente.  
**Valor requerido**: Sí - Número de ranura de la barra rápida (0-8)

## El jugador tiene nivel de permisos
Comprueba si el jugador tiene al menos el nivel de permisos/OP especificado en el mundo o servidor actual.  
**Valor requerido**: Sí - Número de nivel de permisos (0-4, donde 4 es operador del servidor)

## La fuerza de ataque está debilitada
Comprueba si la fuerza de ataque del jugador está actualmente debilitada (no completamente cargada).  
**Valor requerido**: No

## Es día en tiempo real
Comprueba si el día actual del mes en tiempo real coincide con un valor específico.  
**Valor requerido**: Sí - Número del día (1-31). Se pueden proporcionar varios valores separándolos con comas.

## Es hora en tiempo real
Comprueba si la hora actual en tiempo real coincide con un valor específico.  
**Valor requerido**: Sí - Hora en formato de 24 horas (0-23). Se pueden proporcionar varios valores separándolos con comas.

## Es minuto en tiempo real
Comprueba si el minuto actual en tiempo real coincide con un valor específico.  
**Valor requerido**: Sí - Minuto (0-59). Se pueden proporcionar varios valores separándolos con comas.

## Es mes en tiempo real
Comprueba si el mes actual en tiempo real coincide con un valor específico.  
**Valor requerido**: Sí - Número de mes (1-12, donde 1 es enero). Se pueden proporcionar varios valores separándolos con comas.

## Es segundo en tiempo real
Comprueba si el segundo actual en tiempo real coincide con un valor específico.  
**Valor requerido**: Sí - Segundo (0-59). Se pueden proporcionar varios valores separándolos con comas.

## Es día de la semana en tiempo real
Comprueba si el día actual de la semana en tiempo real coincide con un valor específico.  
**Valor requerido**: Sí - Día de la semana como número (1-7, donde 1 es domingo). Se pueden proporcionar varios valores separándolos con comas.

## Es año en tiempo real
Comprueba si el año actual en tiempo real coincide con un valor específico.  
**Valor requerido**: Sí - Año completo (por ejemplo, "2023"). Se pueden proporcionar varios valores separándolos con comas.

## Existe archivo/carpeta
Comprueba si un archivo o carpeta específica existe en el sistema.  
**Valor requerido**: Sí - Ruta del archivo o carpeta (absoluta o relativa al directorio del juego)

## El sistema operativo es Linux
Comprueba si el sistema operativo es Linux.  
**Valor requerido**: No

## El sistema operativo es macOS
Comprueba si el sistema operativo es macOS.  
**Valor requerido**: No

## El sistema operativo es Windows
Comprueba si el sistema operativo es Windows.  
**Valor requerido**: No

## Hay conexión a internet disponible
Comprueba si hay una conexión activa a internet disponible.  
**Valor requerido**: No

## Es el idioma del juego
Comprueba si el idioma actual del juego coincide con un valor específico.  
**Valor requerido**: Sí - Código de idioma (por ejemplo, `en_us` para inglés)

## El mod está cargado
Comprueba si un mod específico está cargado.  
**Valor requerido**: Sí - ID del mod (por ejemplo, `fancymenu`, `jei`). También puedes comprobar Optifine con `optifine`. Se pueden proporcionar varios IDs de mod separándolos con comas.

## MCEF está cargado
Comprueba si MCEF (Minecraft Chromium Embedded Framework) está instalado e inicializado.  
**Valor requerido**: No

## Es número
Proporciona una comparación avanzada de números con diferentes modos de comparación.  
**Valor requerido**: Sí - Formato complejo: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` donde `comparison_mode` puede ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` o `smaller-than-or-equals`

## Es texto
Proporciona una comparación avanzada de texto con diferentes modos de comparación.  
**Valor requerido**: Sí - Formato complejo: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` donde `comparison_mode` puede ser `equals`, `contains`, `starts-with` o `ends-with`

## Es IP del servidor
Comprueba si la IP del servidor actual coincide con un valor específico.  
**Valor requerido**: Sí - Dirección IP del servidor (con o sin puerto)

## El servidor está en línea
Comprueba si un servidor específico está en línea y responde.  
**Valor requerido**: Sí - Dirección IP del servidor (con o sin puerto)

## El paquete de recursos está habilitado
Comprueba si un paquete de recursos específico está actualmente seleccionado/activo.  
**Valor requerido**: Sí - Título del paquete de recursos o ID del paquete (por ejemplo, `Programmer Art` o el ID del paquete)

## Es valor de variable (variable de FM)
Comprueba si una variable de FancyMenu tiene un valor específico.  
**Valor requerido**: Sí - Formato: "nombre_de_variable:valor_esperado"

## Solo una vez por sesión
Devuelve true solo una vez por sesión de juego. Útil para anuncios o acciones de una sola vez.  
**Valor requerido**: No
