---
title: Elementos
description: Todo lo que necesitas saber sobre los tipos de elementos de FancyMenu.
---

# Elementos

Los elementos son los bloques de construcción de tus diseños personalizados en FancyMenu. Puedes agregarlos a cualquier diseño para mostrar información, añadir interactividad o crear efectos visuales impresionantes.

# Agregar elementos a un diseño

Puedes agregar un elemento nuevo a tu diseño desde el **Editor de diseño**.

1.  Haz **clic derecho** en el fondo del editor para abrir el menú contextual.
2.  Pasa el cursor sobre **Nuevo elemento**.
3.  Aparecerá una lista con todos los tipos de elementos disponibles. Haz clic en el que quieras agregar.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Una vez que se agrega un elemento, puedes moverlo, cambiar su tamaño y personalizarlo haciendo **clic derecho** sobre él para abrir su menú contextual específico. Para aprender más sobre cómo acomodar elementos, consulta [Posicionar elementos](./positioning-elements) e [Identificadores de elementos](./element-identifiers).

# Elementos en detalle

Esta sección enumera los elementos integrados de FancyMenu. Usa [Capas y grupos](./layers-and-groups) para organizar su orden de renderizado.

## Botón
Un botón clicable que puede realizar una gran variedad de acciones. Es uno de los elementos más poderosos y versátiles para crear menús interactivos.

*   **Casos de uso:**
    *   Crear un botón de "Unirse a Discord" o "Visitar sitio web".
    *   Agregar un botón de acceso rápido para un servidor específico.
    *   Construir navegación personalizada entre distintos menús.
    *   Crear botones que activen o desactiven otros diseños.
*   **Funciones clave:**
    *   **Acciones:** Puede ejecutar una secuencia de [acciones](./action-scripts), como abrir una URL, unirse a un servidor, enviar un comando de chat, imitar la función de otro botón o controlar variables.
    *   **Apariencia personalizada:** Texturas totalmente personalizables para los estados normal, resaltado e inactivo. Compatible con fondos transparentes, nine-slicing, colores personalizados de etiqueta, colores de etiqueta al pasar el cursor, escala de la etiqueta, activación/desactivación de sombra de la etiqueta y texturas del icono del botón.
    *   **Sonidos:** Sonidos personalizados de clic, pasar el cursor y dejar de pasar el cursor.
    *   **Modo de plantilla:** Puede aplicar su apariencia y propiedades a otros botones de Vanilla o modificados en el menú. Consulta [Plantillas de botones y deslizadores](./button-slider-templates).
    *   **Clics automatizados de widgets Vanilla/mod:** Los widgets existentes de Vanilla y de mods tienen una propiedad de **Clics automatizados** que puede invocar su comportamiento original de clic un número elegido de veces cuando se carga la pantalla. Consulta [Elementos de Vanilla](./vanilla-elements#automated-clicks) para más detalles.

## Deslizador
Un deslizador que los usuarios pueden arrastrar para seleccionar un valor de una lista o un rango. Puede ejecutar acciones cada vez que cambia su valor.

*   **Casos de uso:**
    *   Crear un control de volumen personalizado.
    *   Un deslizador para cambiar entre distintos temas o imágenes de fondo (usando el tipo "Lista").
    *   Ajustar una opción específica de Minecraft, como brillo o distancia de renderizado.
*   **Funciones clave:**
    *   **Tipos:** Puede ser una `Lista de valores` (por ejemplo, "Fácil", "Normal", "Difícil"), un `Rango entero` (por ejemplo, 1-100) o un `Rango decimal` (por ejemplo, 0.0-1.0).
    *   **Acciones dinámicas:** Ejecuta acciones cuando cambia su valor. El valor actual puede usarse con [Variables](./variables).
    *   **Personalización:** La etiqueta del deslizador puede mostrar dinámicamente su valor actual. Las texturas del control y del fondo son totalmente personalizables, incluyendo fondos transparentes, opciones de color/escala de la etiqueta, activación/desactivación de sombra del texto y sonidos personalizados de clic/soltar al pasar el cursor.

## Casilla de verificación
Una casilla de verificación estándar que puede activarse o desactivarse. Puede ejecutar acciones al cambiar de estado.

*   **Casos de uso:**
    *   Una casilla de "Acepto las reglas".
    *   Una opción para habilitar o deshabilitar una función específica en tu menú personalizado.
    *   Activar o desactivar un diseño o variable.
*   **Funciones clave:**
    *   **Acciones al cambiar:** Ejecuta [scripts de acción](./action-scripts) cuando cambia su estado. El estado actual (`true` o `false`) está disponible para sus acciones.
    *   **Modo de variable:** Puede vincularse directamente a una variable de FancyMenu, haciendo que el estado de la casilla lea y escriba en esa variable.
    *   **Estado persistente:** Cuando el Modo de variable está desactivado, la casilla guarda automáticamente su estado por identificador de elemento y lo restaura después de reiniciar el juego. Estos estados se almacenan en `<game-directory>/checkbox_states.json`. En el Modo de variable, la variable de FancyMenu vinculada es la fuente del estado de la casilla.
    *   **Apariencia personalizada:** Compatible con texturas personalizadas para el fondo (en estados normal, resaltado e inactivo) y para la marca de verificación.

## Campo de texto
Un campo donde los usuarios pueden escribir texto. Su contenido puede vincularse a una variable de FancyMenu, lo que te permite capturar y usar la entrada del usuario.

*   **Casos de uso:**
    *   Un campo para "IP del servidor" que funcione con un botón de "Unirse al servidor".
    *   Un campo para ingresar el nombre de un jugador para una vista previa de skin personalizada.
    *   Crear una interfaz básica tipo inicio de sesión.
*   **Funciones clave:**
    *   **Vinculación con variables:** Guarda el texto ingresado en una [variable](./variables) específica.
    *   **Validación de entrada:** Puede configurarse para aceptar solo tipos específicos de caracteres, como números, URLs o texto plano.
    *   **Longitud máxima:** Puedes establecer un límite máximo de caracteres para la entrada.
    *   **Apariencia y sonidos:** Compatible con color de fondo personalizado, colores de borde, redondeo del borde, color del texto, texto de pista/placeholder, color de la pista, sonidos al pasar el cursor, al dejar de pasar el cursor y al hacer clic.

## Tooltip
Un cuadro de texto que puede aparecer en una posición fija o seguir el cursor del mouse. Su visibilidad normalmente se controla con [Requisitos de carga](./conditions).

*   **Casos de uso:**
    *   Mostrar información detallada cuando el usuario pasa el cursor sobre un botón o una imagen.
    *   Crear consejos de ayuda contextual que aparezcan bajo ciertas condiciones.
    *   Mostrar información dinámica (como el estado del servidor) junto al cursor.
*   **Funciones clave:**
    *   **Sigue al mouse:** Puede configurarse para seguir el puntero del mouse.
    *   **Compatibilidad con Markdown:** El contenido del tooltip admite formato completo de Markdown.
    *   **Fondo personalizado:** El fondo puede ser de color sólido o una textura personalizada con nine-slicing para una apariencia totalmente temática.

## Ítem
Muestra un solo ítem de Minecraft, ya sea de vanilla o de un mod.

*   **Casos de uso:**
    *   Usar ítems como iconos para botones o selecciones de menú.
    *   Crear una interfaz de tienda o selección de kits.
    *   Mostrar el ítem que el jugador tiene en la mano o su armadura.
*   **Funciones clave:**
    *   **Datos personalizados:** Compatible con nombre personalizado, lore, cantidad, brillo de encantamiento y datos NBT. Consulta el [Marcador de posición de datos NBT](./nbt-data-placeholder).
    *   **Mostrar tooltip:** Puede configurarse para mostrar el tooltip estándar del ítem al pasar el cursor.

## Modelo JSON de bloque/ítem
Renderiza un modelo JSON de bloque o ítem desde recursos de Minecraft o fuentes externas.

*   **Casos de uso:**
    *   Mostrar un modelo 3D de un paquete de recursos en un menú.
    *   Mostrar vistas previas de ítems/bloques con texturas personalizadas.
    *   Crear elementos decorativos de UI basados en modelos.
*   **Funciones clave:**
    *   **Fuente del modelo:** Puede cargar JSON del modelo desde recursos de Minecraft o fuentes externas.
    *   **Sobrescritura de texturas:** Permite establecer una textura personalizada.
    *   **Controles de renderizado:** Desplazamiento del modelo, escala, rotación en tres ejes, renderizado translúcido y la transformación GUI del modelo.
    *   **Iluminación:** Dos luces configurables con controles independientes de tono y rotación.

## Imagen
Muestra una imagen estática desde un archivo local, una URL web o una ubicación de recurso de Minecraft.

*   **Casos de uso:**
    *   Agregar el logo de un servidor o la marca de un modpack.
    *   Crear bordes decorativos o marcos de UI.
    *   Usar imágenes como parte de un diseño de interfaz más complejo.
*   **Funciones clave:**
    *   **Nine-slicing:** Escala bordes o paneles sin distorsionar sus esquinas. Consulta [Nine-slicing y mosaico](./nine-slicing-and-tiling).
    *   **Repetición de textura:** La imagen puede repetirse en mosaico para llenar el área del elemento.
    *   **Tinte:** Puedes aplicar un tinte de color a la imagen.
    *   **Esquinas redondeadas:** Las imágenes que no usan nine-slicing ni repetición pueden tener esquinas redondeadas.
    *   **Efecto parallax:** Se mueve con el mouse para crear profundidad visual. Consulta [Efecto parallax](./parallax).

## Texto
Un elemento muy versátil para mostrar texto. Puede usarse para todo, desde etiquetas de una sola línea hasta documentos con varias páginas y desplazamiento.

*   **Casos de uso:**
    *   Mostrar reglas del servidor, notas de parche o mensajes de bienvenida.
    *   Crear paneles de información dinámicos usando [marcadores de posición](./placeholders), por ejemplo `Welcome, {"placeholder":"playername"}!`.
    *   Agregar etiquetas y descripciones a tu interfaz.
*   **Funciones clave:**
    *   **Fuentes de contenido:** El texto puede escribirse directamente, cargarse desde un archivo local o descargarse desde una URL web.
    *   **Compatibilidad con Markdown:** Admite encabezados, listas, bloques de código, tablas y otro formato de Markdown. Consulta [Formato de texto](./text-formatting).
    *   **Desplazamiento:** Se vuelve desplazable automáticamente si el contenido es más grande que el área del elemento. Las barras de desplazamiento pueden personalizarse o desactivarse.
    *   **Estilo:** Control total sobre el color del texto, escala, alineación, sombra y espaciado entre líneas.

## Video
Reproduce un archivo de video. Es perfecto para intros cinematográficas o fondos decorativos en bucle.

> [!WARNING]
> El elemento nativo de Video requiere **Watermedia V3** y **Watermedia Binaries V3**. El antiguo elemento **Video [MCEF]** está obsoleto.

*   **Casos de uso:**
    *   Un tráiler animado del modpack o del servidor.
    *   Un video ambiental en bucle para dar vida a tu menú.
    *   Un video tutorial dentro del juego.
*   **Funciones clave:**
    *   **Fuentes:** Compatible con archivos de video locales y URLs web. Consulta [Videos](./video).
    *   **Control de reproducción:** Puede configurarse para repetirse automáticamente. Su volumen, canal de sonido y comportamiento de conservación de proporción son ajustables.
    *   **Control interactivo:** La reproducción, el tiempo de avance y el volumen del video pueden controlarse mediante acciones de botón.

## Shader GLSL
Renderiza un shader GLSL personalizado dentro de un elemento.

*   **Casos de uso:**
    *   Paneles de shader animados.
    *   Efectos visuales procedurales.
    *   Efectos de menú al estilo Shadertoy recortados a un rectángulo del elemento.
*   **Funciones clave:**
    *   **Entorno de ejecución del shader:** Compatible con shaders de una sola pasada y de múltiples pasadas.
    *   **Compatibilidad con Shadertoy:** Puede usar shaders `mainImage` al estilo Shadertoy.
    *   **Uniformes:** Expone uniformes de FancyMenu y de entrada. Consulta la [API de shader GLSL](./glsl-shader-api).

## Presentación
Muestra una secuencia de imágenes. Sus imágenes y el archivo de configuración `properties.txt` viven en el subdirectorio propio de la presentación dentro de `<game-directory>/config/fancymenu/slideshows/`.

*   **Casos de uso:**
    *   Una galería rotativa de capturas dentro del juego.
    *   Mostrar las características clave de un modpack.
    *   Un fondo dinámico que alterna entre distintas escenas.
*   **Funciones clave:**
    *   Carga [presentaciones](./slideshows) preconfiguradas.
    *   Puede configurarse para conservar la proporción de las imágenes.

## Forma de rectángulo
Un rectángulo simple de color sólido.

*   **Casos de uso:**
    *   Crear un fondo semitransparente detrás del texto para mejorar la legibilidad.
    *   Diseñar paneles y divisores simples de UI.
    *   Como marcador de posición de color durante el diseño del layout.
*   **Funciones clave:**
    *   Compatible con colores HEX RGBA, esquinas redondeadas y desenfoque opcional, lo que permite que la forma funcione como un panel simple, tinte o fondo borroso.

## Forma de círculo
Una forma simple de círculo/elipse de color sólido.

*   **Casos de uso:**
    *   Crear acentos circulares, indicadores o áreas suaves de la UI.
    *   Construir decoraciones temáticas de UI sin un archivo de textura.
*   **Funciones clave:**
    *   Compatible con color, desenfoque y un valor configurable de redondez/exponente.

## Texto llamativo
Una recreación del icónico texto llamativo amarillo y rebotante de la pantalla de título de Minecraft.

*   **Casos de uso:**
    *   Reemplazar el texto llamativo vanilla con tus propios mensajes personalizados.
    *   Agregar un mensaje animado que llame la atención en cualquier menú.
*   **Funciones clave:**
    *   **Fuentes de contenido:** Puede usar los textos llamativos vanilla predeterminados, una lista de texto personalizado escrito directamente o texto de un archivo local.
    *   **Personalización:** Puedes activar o desactivar el efecto de rebote y personalizar el color, la escala, la rotación y la sombra del texto.

## Entidad del jugador
Renderiza un modelo de jugador en el menú.

*   **Casos de uso:**
    *   Mostrar el personaje del jugador actual en el menú principal.
    *   Crear una pantalla de selección de equipo o vista previa de clase.
    *   Una sección de "perfil" que muestre la skin y el nombre del jugador.
*   **Funciones clave:**
    *   **Apariencia dinámica:** Puede copiar la skin, la capa y el nombre del jugador actual. Consulta [Cabezas de jugador](./player-heads).
    *   **Poses personalizadas:** Ofrece control detallado sobre la rotación de la cabeza, el cuerpo, los brazos y las piernas. La cabeza y el cuerpo también pueden configurarse para seguir el cursor del mouse.
    *   **Atributos:** Puede configurarse como bebé, agachado o con un modelo delgado.

## Navegador
Un elemento que renderiza una página web en vivo dentro del juego.

¡Este elemento requiere que el mod **MCEF (Minecraft Chromium Embedded Framework)** esté instalado y funcionando!

Puedes descargar MCEF desde las páginas oficiales del proyecto en [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) y [Modrinth](https://modrinth.com/mod/mcef).

Para versiones más nuevas de Minecraft (1.21.5+), los proyectos oficiales de MCEF no proporcionan compilaciones, pero existe un fork con compilaciones para las versiones más recientes de Minecraft, que se puede encontrar [aquí](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) y [aquí](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Este fork lo mantiene Keksuccino para ofrecer compilaciones para las versiones más recientes de Minecraft lo más rápido posible.

*   **Casos de uso:**
    *   Mostrar el Dynmap en vivo de un servidor.
    *   Incrustar un reproductor de video de YouTube.
    *   Mostrar una wiki o página de documentación directamente dentro del juego.
*   **Funciones clave:**
    *   **Interactividad:** Puede hacerse totalmente interactivo, permitiendo a los usuarios hacer clic en enlaces, desplazarse y escribir.
    *   **Control de medios:** Ofrece opciones para silenciar medios, repetir videos y ocultar los controles de video en la página cargada.

### Cargar archivos HTML locales
El elemento Navegador puede cargar documentos HTML locales desde `<game-directory>/config/fancymenu/assets/`.

Para cargar un archivo HTML local, comienza tu URL con `file:///`, seguido de la ruta COMPLETA del archivo, por ejemplo `/config/fancymenu/assets/cool_changelog.html`, lo que lo deja así: `file:///config/fancymenu/assets/cool_changelog.html`.

En **Linux**, usa el marcador de posición [**Ruta absoluta de archivo/carpeta**](./placeholders#absolute-filefolder-path-absolute_path) en lugar de poner una ruta absoluta específica de la instancia: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

La ruta corta en Linux debe comenzar con `/`, como se muestra en el ejemplo.

## Animador de elementos
Una herramienta poderosa para crear animaciones complejas basadas en fotogramas clave. Puede animar la posición, el tamaño y el punto de anclaje de uno o varios elementos.

*   **Casos de uso:**
    *   Deslizar elementos dentro o fuera de la vista.
    *   Cambiar el tamaño de paneles o notificaciones.
    *   Animar desplazamientos de posición y transiciones de anclaje.
*   **Funciones clave:**
    *   **Editor de fotogramas clave:** Un editor dedicado para agregar, editar y secuenciar fotogramas clave en una línea de tiempo.
    *   **Multidestino:** Un solo Animador puede controlar varios elementos "objetivo" al mismo tiempo.
    *   **Control:** Las animaciones pueden configurarse para repetirse. También puedes elegir animar solo la posición o el tamaño.
    *   **Desplazamientos de tiempo:** Los elementos objetivo pueden usar desplazamientos de inicio individuales o aleatorios.
    *   Consulta [Animador de elementos](./element-animator) para la configuración y edición de fotogramas clave.

## Ticker
Un elemento invisible que ejecuta una lista de acciones a intervalos regulares (cada "tick").

> [!NOTE]
> Para automatización en segundo plano, considera usar [Programadores](./schedulers). Los programadores son globales y pueden ejecutarse independientemente de una pantalla específica.

*   **Casos de uso:**
    *   Revisar periódicamente si un servidor está en línea y actualizar un elemento de texto.
    *   Crear un temporizador regresivo que actualice una etiqueta de texto.
    *   Ejecutar un script repetidamente para crear comportamientos personalizados.
*   **Funciones clave:**
    *   **Control de tiempo:** Puedes configurar el retraso entre ticks en milisegundos.
    *   **Modos de tick:** Puede configurarse para hacer tick continuamente, solo una vez por sesión de juego o una vez cada vez que se carga el menú.
    *   **Asíncrono:** Puede ejecutar sus [acciones](./action-scripts) por separado, aunque algunas acciones no pueden ejecutarse mientras esta opción está habilitada.

## Audio
Un elemento invisible que reproduce archivos de audio. Puede administrar una lista de reproducción de pistas y ofrece varios controles de reproducción.

*   **Casos de uso:**
    *   Agregar música de fondo personalizada a un menú.
    *   Crear un reproductor de música con botones para controlar la reproducción (siguiente/anterior pista, volumen).
    *   Reproducir paisajes sonoros ambientales.
*   **Funciones clave:**
    *   **Lista de reproducción:** Puede administrar varias pistas de audio.
    *   **Modos de reproducción:** Puede reproducir pistas en orden o aleatoriamente (con compatibilidad con ponderación de pistas para hacer que algunas sean más comunes que otras).
    *   **Control:** Compatible con repetición, ajuste de volumen y selección de canal de sonido. Consulta [Música de fondo del menú](./background-music).

## Controlador de música
Un elemento invisible usado para controlar la reproducción de música predeterminada de Minecraft dentro de un menú específico.

*   **Casos de uso:**
    *   Desactivar la música predeterminada del menú en una pantalla donde quieras reproducir tu propia música personalizada mediante un [elemento **Audio**](#audio).
    *   Evitar que la música del mundo siga reproduciéndose cuando se abre un menú dentro del juego.
*   **Funciones clave:**
    *   Interruptores separados para controlar la "Música del menú" y la "Música del mundo" de vanilla.

## Barra de progreso
Una barra personalizable que representa visualmente un valor numérico.

*   **Casos de uso:**
    *   Una barra de carga que sigue el progreso de carga del mundo usando `{"placeholder":"world_load_progress"}`.
    *   Barras visuales de salud, hambre o experiencia para un HUD dentro del juego.
    *   Un indicador de volumen controlado por un [elemento **Deslizador**](#slider).
*   **Funciones clave:**
    *   **Valor dinámico:** El valor de progreso (0-100 o 0.0-1.0) se establece mediante un campo de texto que admite [marcadores de posición](./placeholders).
    *   **Apariencia:** La dirección de la barra (arriba, abajo, izquierda, derecha), los colores, las texturas y el nine-slicing para las texturas de la barra/fondo son totalmente personalizables.
    *   **Animación:** Incluye una animación de llenado suave para que los cambios de progreso se vean menos bruscos.
    *   **Ancla de elemento basada en progreso:** Cuando otro elemento usa la barra de progreso como su ancla de **Elemento**, habilita **Usar progreso para ancla de elemento** para mover ese ancla al borde actual del área llenada. Los elementos anclados entonces se desplazan con el progreso de la barra en lugar de permanecer pegados a los límites estáticos de la barra de progreso.

## Arrastrador
Un elemento invisible que el usuario puede hacer clic y arrastrar para moverlo. Otros elementos pueden anclarse a él para crear widgets movibles.

*   **Casos de uso:**
    *   Crear un reloj o panel de información arrastrable.
    *   Permitir que los usuarios personalicen la posición de los elementos de la UI según sus preferencias.
*   **Funciones clave:**
    *   **Persistencia opcional:** Activa **Guardar desplazamiento de arrastre del usuario** para conservar la posición arrastrada por el usuario entre aperturas de pantalla y reinicios del juego. Desactívalo para restablecer el desplazamiento.
    *   **Punto de anclaje:** Actúa como un ancla movible para otros elementos, lo cual es una parte clave de [Posicionar elementos](./positioning-elements).

## Cursor
Un elemento invisible que reemplaza el cursor del sistema por una imagen personalizada cuando un diseño está activo.

*   **Casos de uso:**
    *   Crear una interfaz totalmente temática que combine con la estética de tu modpack.
*   **Funciones clave:**
    *   **Textura personalizada:** Usa cualquier imagen para tu cursor.
    *   **Punto activo:** Establece el píxel exacto de la imagen que se usa como punto de clic. Consulta [Cursor personalizado](./custom-cursor).
