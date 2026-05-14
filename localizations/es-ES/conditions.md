---
title: Condiciones (Requisitos)
description: Cómo usar los requisitos de carga.
---

# Requisitos
Los requisitos (también llamados "requisitos de carga") te permiten hacer que partes de tus diseños sean visibles o invisibles en función de distintas condiciones, como si un elemento está en estado de hover, si la ventana tiene un tamaño específico o si te encuentras actualmente en un mundo.

También se pueden usar en los scripts de acción de botones, deslizadores, selectores y cualquier otra cosa que tenga una entrada de script de acción.

# Añadir requisitos a los elementos
Para añadir uno o varios requisitos a elementos, solo tienes que hacer clic derecho sobre el elemento y hacer clic en **Requisitos de carga**.

# Requisitos para todo el diseño
También puedes cambiar la visibilidad de diseños completos haciendo clic derecho en el **fondo del editor** y luego haciendo clic en **Requisitos de carga [para todo el diseño]**.

# Scripts de acción
Los requisitos también se pueden usar en scripts de acción.
Puedes añadirlos en la pantalla del editor de scripts de acción y utilizarlos para ejecutar acciones específicas solo si se cumple la condición del requisito.

# Valores del requisito
Algunos requisitos necesitan que definas ciertos valores para funcionar correctamente. Si ese es el caso, la pantalla del requisito debería indicarte que primero establezcas todos los valores, pero si no, comprueba si el botón **Editar valor del requisito** se puede pulsar al añadir el requisito.
Consulta siempre la descripción del requisito si no estás seguro de qué poner como valor.
Algunas entradas de valor incluso admiten **autocompletado con TAB**.

FancyMenu 3.9.0 rediseña la ventana de Gestionar requisitos para usar un menú contextual al hacer clic derecho, navegación con teclado, búsqueda, deshacer/rehacer (`CTRL + Z` / `CTRL + Y`) y `CTRL + S` como atajo de **Hecho**.

# Requisitos en detalle
La siguiente lista contiene la mayoría, si no todos, los requisitos disponibles en FancyMenu. Es posible que la lista a veces esté algo desactualizada debido a actualizaciones del mod.

## El elemento está bajo el cursor
Comprueba si un elemento específico está bajo el cursor del ratón.  
**Valor requerido**: Sí - ID del elemento de destino (por ejemplo, `some_element_ID`). Puedes obtener el ID haciendo clic derecho sobre un elemento en el editor.

## El elemento tiene el foco
Comprueba si un elemento específico tiene actualmente el foco del teclado (por ejemplo, un campo de texto o un botón enfocado).
**Valor requerido**: Sí - ID del elemento de destino (el mismo ID que se muestra en el editor)

> Esto no es lo mismo que cuando un elemento simplemente está bajo el cursor, aunque lo parezca. Los elementos con foco siguen pareciendo "bajo el cursor" incluso cuando ya no lo están. Los elementos reciben el foco al hacer clic en ellos o al usar el teclado para navegar por los menús.
{.is-info}

## Hay algún elemento bajo el cursor
Comprueba si cualquier elemento del diseño está actualmente bajo el cursor del ratón.  
**Valor requerido**: No

## Hay algún botón bajo el cursor
Comprueba si cualquier botón (vanilla o personalizado) está actualmente bajo el cursor del ratón.  
**Valor requerido**: No

## El diseño está habilitado
Comprueba si un diseño específico está actualmente habilitado.  
**Valor requerido**: Sí - El nombre del diseño (por ejemplo, `my_cool_main_menu_layout`)

## El programador está en ejecución
Comprueba si un programador está actualmente en ejecución.
**Valor requerido**: Sí - ID del programador (por ejemplo, `my_scheduler`)

## La escala de la interfaz es
Comprueba si la escala actual de la interfaz coincide con ciertas condiciones.  
**Valor requerido**: Sí - Puede aceptar valores numéricos como `1`, `2`, etc.

## El botón está activo
Comprueba si un botón específico está activo (se puede pulsar).  
**Valor requerido**: Sí - ID del elemento del botón de destino (por ejemplo, "some_element_ID")

## El título de la pantalla es
Comprueba si el título MOSTRADO de la pantalla coincide con un texto específico o una clave de localización. Esto solo comprobará el nombre visible/título de la pantalla, como "Opciones" o "Pausa". ¡NO comprobará el identificador del menú/pantalla (como `title_screen`)!

**Valor requerido**: Sí - El texto exacto del título o la clave de localización de la pantalla

## Se ha pulsado una tecla
Comprueba si se está pulsando actualmente una tecla específica del teclado.  
**Valor requerido**: Sí - El código de la tecla objetivo. Se selecciona mediante una interfaz al editar el valor del requisito.

## Hay alguna pantalla abierta
Comprueba si cualquier pantalla/menú está abierto actualmente (devuelve false si no se muestra ninguna pantalla).  
**Valor requerido**: No

## La superposición de depuración de MC está activada
Comprueba si la superposición de depuración de F3 está visible actualmente.
**Valor requerido**: No

## Tipo de cursor activo
Comprueba si el tipo de cursor activo de FancyMenu coincide con un tipo de cursor estándar específico.
**Valor requerido**: Sí - Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` o `not_allowed`

## La barra del menú de personalización está visible
Comprueba si la barra del menú de personalización de FancyMenu está visible actualmente.
**Valor requerido**: No

## El modo paquete de mods está activado
Comprueba si el Modo paquete de mods de FancyMenu está activado.
**Valor requerido**: No

## Se ha hecho clic con el ratón
Comprueba si se está pulsando un botón específico del ratón.  
**Valor requerido**: Sí - `left` o `right` para indicar qué botón del ratón comprobar

## Pantalla completa
Comprueba si el juego está actualmente en modo de pantalla completa.  
**Valor requerido**: No

## El ancho de la ventana es
Comprueba si el ancho de la ventana del juego coincide con valores específicos.  
**Valor requerido**: Sí - Ancho de la ventana en píxeles (por ejemplo, "1920"). Se pueden proporcionar varios valores separándolos con comas.

## La altura de la ventana es
Comprueba si la altura de la ventana del juego coincide con valores específicos.  
**Valor requerido**: Sí - Altura de la ventana en píxeles (por ejemplo, "1080"). Se pueden proporcionar varios valores separándolos con comas.

## El ancho de la ventana es mayor que
Comprueba si el ancho de la ventana del juego es mayor que un valor específico.  
**Valor requerido**: Sí - Ancho de la ventana en píxeles (por ejemplo, "1920")

## La altura de la ventana es mayor que
Comprueba si la altura de la ventana del juego es mayor que un valor específico.  
**Valor requerido**: Sí - Altura de la ventana en píxeles (por ejemplo, "1080")

## Multijugador
Comprueba si el jugador está actualmente en un mundo multijugador.  
**Valor requerido**: No

## Un jugador
Comprueba si el jugador está actualmente en un mundo de un solo jugador.  
**Valor requerido**: No

## Hay un mundo cargado
Comprueba si hay algún mundo cargado actualmente.  
**Valor requerido**: No

## Aventura
Comprueba si el jugador está actualmente en modo de juego Aventura.  
**Valor requerido**: No

## Creativo
Comprueba si el jugador está actualmente en modo de juego Creativo.  
**Valor requerido**: No

## Espectador
Comprueba si el jugador está actualmente en modo de juego Espectador.  
**Valor requerido**: No

## Supervivencia
Comprueba si el jugador está actualmente en modo de juego Supervivencia.  
**Valor requerido**: No

## Es modo de juego
Comprueba si el jugador está en un modo de juego específico.  
**Valor requerido**: Sí - Nombre del modo de juego (por ejemplo, "creative", "survival", "adventure", "spectator")

## Es dificultad
Comprueba si la dificultad actual del juego coincide con un valor específico.  
**Valor requerido**: Sí - Nombre de la dificultad (por ejemplo, "peaceful", "easy", "normal", "hard")

## Es Hardcore
Comprueba si el mundo cargado actualmente está en modo Hardcore.
**Valor requerido**: No

## Es perspectiva de la cámara
Comprueba si la perspectiva actual de la cámara coincide con una perspectiva específica.
**Valor requerido**: Sí - `first_person`, `third_person_back` o `third_person_front`

## Está lloviendo
Comprueba si actualmente está lloviendo en la ubicación del jugador.  
**Valor requerido**: No

## Está tronando
Comprueba si actualmente hay una tormenta eléctrica en el mundo del jugador.  
**Valor requerido**: No

## El tiempo está despejado
Comprueba si el tiempo está actualmente despejado (ni llueve ni truena).  
**Valor requerido**: No

## Está nevando
Comprueba si actualmente está nevando en la ubicación del jugador.  
**Valor requerido**: No

## El jugador está corriendo
Comprueba si el jugador está esprintando actualmente.  
**Valor requerido**: No

## El jugador está agachado
Comprueba si el jugador está agachado/en cuclillas actualmente.  
**Valor requerido**: No

## El jugador está usando un objeto
Comprueba si el jugador está usando actualmente un objeto.
**Valor requerido**: No

## El jugador está nadando
Comprueba si el jugador está nadando actualmente.  
**Valor requerido**: No

## El jugador está saltando o cayendo
Comprueba si el jugador está saltando actualmente.  
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

## El jugador monta una entidad/vehículo
Comprueba si el jugador está montando cualquier entidad.  
**Valor requerido**: No

## El jugador monta una entidad que puede saltar
Comprueba si el jugador está montando una entidad que puede saltar (como un caballo).  
**Valor requerido**: No

## El jugador monta una entidad con salud
Comprueba si el jugador está montando una entidad viva con salud (como animales, no barcos).  
**Valor requerido**: No

## El jugador está en nieve polvo
Comprueba si el jugador está actualmente en nieve polvo.  
**Valor requerido**: No

## El jugador estuvo en nieve polvo
Comprueba si el jugador estuvo en nieve polvo (se usa para efectos que persisten después de salir).  
**Valor requerido**: No

## El jugador lleva una calabaza
Comprueba si el jugador lleva una calabaza tallada en la cabeza.  
**Valor requerido**: No

## El jugador está volando con un elytra
Comprueba si el jugador está volando actualmente con un elytra.  
**Valor requerido**: No

## El jugador vuela en creativo
Comprueba si el jugador está volando en modo creativo.  
**Valor requerido**: No

## El jugador tiene corazones de absorción
Comprueba si el jugador tiene corazones de absorción (corazones dorados).  
**Valor requerido**: No

## El jugador está marchitado
Comprueba si el jugador está afectado por el efecto wither.  
**Valor requerido**: No

## El jugador está completamente congelado
Comprueba si el jugador está completamente congelado (normalmente por nieve polvo).  
**Valor requerido**: No

## El jugador está envenenado
Comprueba si el jugador está afectado por el efecto veneno.  
**Valor requerido**: No

## El jugador está en un bioma
Comprueba si el jugador está en un bioma específico.  
**Valor requerido**: Sí - Identificador del bioma (por ejemplo, `minecraft:birch_forest`)

## El jugador está en una dimensión
Comprueba si el jugador está en una dimensión específica.  
**Valor requerido**: Sí - Identificador de la dimensión (por ejemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## El jugador está en una estructura
Comprueba si el jugador está actualmente dentro de una estructura específica. Requiere FancyMenu en el servidor para mundos de servidor.
**Valor requerido**: Sí - Identificador de la estructura (por ejemplo, `minecraft:village`)

## Hay una entidad cerca
Comprueba si un tipo de entidad específico está dentro de un determinado radio del jugador.  
**Valor requerido**: Sí - Formato: "radio:id_de_entidad" (por ejemplo, `10:minecraft:pig` - comprueba si hay cerdos dentro de 10 bloques)

## Efecto activo
Comprueba si el jugador tiene activo un efecto de poción específico.  
**Valor requerido**: Sí - Identificador del efecto (por ejemplo, `minecraft:speed`, `minecraft:strength`)

## Hay algún efecto activo
Comprueba si el jugador tiene activo algún efecto de poción.  
**Valor requerido**: No

## El jugador es zurdo
Comprueba si el jugador está configurado en modo zurdo en las opciones del juego.  
**Valor requerido**: No

## La ranura del inventario está llena
Comprueba si una ranura específica del inventario contiene un objeto.  
**Valor requerido**: Sí - Número de ranura (0-35 para el inventario principal, las ranuras 0-8 son la barra rápida)

## Hay un objeto bajo el cursor en el inventario
Comprueba si el cursor está pasando por encima de algún objeto en una pantalla de inventario.
**Valor requerido**: No

## El cursor está sosteniendo un objeto del inventario
Comprueba si el cursor está sosteniendo actualmente una pila de objetos del inventario.
**Valor requerido**: No

## La ranura de la barra rápida está seleccionada
Comprueba si una ranura específica de la barra rápida está seleccionada actualmente.  
**Valor requerido**: Sí - Número de ranura de la barra rápida (0-8)

## El jugador tiene nivel de permiso
Comprueba si el jugador tiene al menos el nivel de permiso/OP especificado en el mundo o servidor actual.  
**Valor requerido**: Sí - Número de nivel de permiso (0-4, donde 4 es operador del servidor)

## El poder de ataque está debilitado
Comprueba si el poder de ataque del jugador está actualmente debilitado (no completamente cargado).  
**Valor requerido**: No

## Es día de la hora real
Comprueba si el día del mes del mundo real actual coincide con un valor específico.  
**Valor requerido**: Sí - Número de día (1-31). Se pueden proporcionar varios valores separándolos con comas.

## Es hora de la hora real
Comprueba si la hora actual del mundo real coincide con un valor específico.  
**Valor requerido**: Sí - Hora en formato de 24 horas (0-23). Se pueden proporcionar varios valores separándolos con comas.

## Es minuto de la hora real
Comprueba si el minuto actual del mundo real coincide con un valor específico.  
**Valor requerido**: Sí - Minuto (0-59). Se pueden proporcionar varios valores separándolos con comas.

## Es mes de la hora real
Comprueba si el mes actual del mundo real coincide con un valor específico.  
**Valor requerido**: Sí - Número de mes (1-12, donde 1 es enero). Se pueden proporcionar varios valores separándolos con comas.

## Es segundo de la hora real
Comprueba si el segundo actual del mundo real coincide con un valor específico.  
**Valor requerido**: Sí - Segundo (0-59). Se pueden proporcionar varios valores separándolos con comas.

## Es día de la semana de la hora real
Comprueba si el día actual de la semana del mundo real coincide con un valor específico.  
**Valor requerido**: Sí - Día de la semana como número (1-7, donde 1 es domingo). Se pueden proporcionar varios valores separándolos con comas.

## Es año de la hora real
Comprueba si el año actual del mundo real coincide con un valor específico.  
**Valor requerido**: Sí - Año completo (por ejemplo, "2023"). Se pueden proporcionar varios valores separándolos con comas.

## Existe archivo/carpeta
Comprueba si existe en el sistema un archivo o carpeta específica.  
**Valor requerido**: Sí - Ruta al archivo o carpeta (absoluta o relativa al directorio del juego)

## El sistema operativo es Linux
Comprueba si el sistema operativo es Linux.  
**Valor requerido**: No

## El sistema operativo es macOS
Comprueba si el sistema operativo es macOS.  
**Valor requerido**: No

## El sistema operativo es Windows
Comprueba si el sistema operativo es Windows.  
**Valor requerido**: No

## Hay conexión a Internet disponible
Comprueba si hay disponible una conexión activa a Internet.  
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
Proporciona una comparación avanzada de números con distintos modos de comparación.  
**Valor requerido**: Sí - Formato complejo: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` donde `comparison_mode` puede ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` o `smaller-than-or-equals`

## Es texto
Proporciona una comparación avanzada de texto con distintos modos de comparación.  
**Valor requerido**: Sí - Formato complejo: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` donde `comparison_mode` puede ser `equals`, `contains`, `starts-with` o `ends-with`

## Es la IP del servidor
Comprueba si la IP del servidor actual coincide con un valor específico.  
**Valor requerido**: Sí - Dirección IP del servidor (con o sin puerto)

## El servidor está en línea
Comprueba si un servidor específico está en línea y accesible.  
**Valor requerido**: Sí - Dirección IP del servidor (con o sin puerto)

## El paquete de recursos está activado
Comprueba si un paquete de recursos específico está actualmente seleccionado/activo.  
**Valor requerido**: Sí - Título del paquete de recursos o ID del paquete (por ejemplo, `Programmer Art` o el ID del paquete)

## Es valor de variable (variable de FM)
Comprueba si una variable de FancyMenu tiene un valor específico.  
**Valor requerido**: Sí - Formato: "nombre_de_variable:valor_esperado"

## Solo una vez por sesión
Devuelve true solo una vez por sesión de juego. Útil para anuncios o acciones que solo deben ejecutarse una vez.  
**Valor requerido**: No
