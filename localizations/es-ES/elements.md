---
title: Elementos
description: Todo lo que necesitas saber sobre los tipos de elementos de FancyMenu.
---
# Elementos

Los elementos son los bloques de construcción de tus diseños personalizados en FancyMenu. Puedes añadirlos a cualquier diseño para mostrar información, añadir interactividad o crear efectos visuales espectaculares.

# Añadir elementos a un diseño

Puedes añadir un nuevo elemento a tu diseño desde el **Editor de diseño**.

1.  **Haz clic derecho** sobre el fondo del editor para abrir el menú contextual.
2.  Pasa el cursor sobre **Nuevo elemento**.
3.  Aparecerá una lista con todos los tipos de elementos disponibles. Haz clic en el que quieras añadir.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Una vez añadido un elemento, puedes moverlo, redimensionarlo y personalizarlo haciendo **clic derecho** sobre él para abrir su menú contextual específico. Para saber más sobre cómo organizar los elementos, consulta [Posicionar elementos](./positioning-elements) e [Identificadores de elementos](./element-identifiers).

# Elementos en detalle

Esta sección enumera los elementos integrados de FancyMenu. Usa [Capas y grupos](./layers-and-groups) para organizar su orden de renderizado.

## Button
Un botón pulsable que puede realizar una amplia variedad de acciones. Este es uno de los elementos más potentes y versátiles para crear menús interactivos.

*   **Casos de uso:**
    *   Crear un botón de "Unirse a Discord" o "Visitar sitio web".
    *   Añadir un botón de acceso rápido a un servidor específico.
    *   Construir navegación personalizada entre distintos menús.
    *   Crear botones que activen o desactiven otros diseños.
*   **Características principales:**
    *   **Acciones:** Puede ejecutar una secuencia de [acciones](./action-scripts), como abrir una URL, unirse a un servidor, enviar un comando de chat, imitar la función de otro botón o controlar variables.
    *   **Apariencia personalizada:** Texturas totalmente personalizables para los estados normal, resaltado e inactivo. Admite fondos transparentes, nine-slicing, colores de etiqueta personalizados, colores de etiqueta al pasar el cursor, escala de la etiqueta, activación/desactivación de sombra en la etiqueta y texturas de icono del botón.
    *   **Sonidos:** Sonidos personalizados de clic, pasar el cursor y dejar de pasar el cursor.
    *   **Modo plantilla:** Puede aplicar su apariencia y propiedades a otros botones vainilla o modificados en el menú. Consulta [Plantillas de botón y deslizador](./button-slider-templates).
    *   **Clics automatizados de widgets vainilla/mod:** Los widgets vainilla y modificados existentes tienen una propiedad **Clics automatizados** que puede invocar su comportamiento original de clic un número elegido de veces cuando se carga la pantalla. Consulta [Elementos de vainilla](./vanilla-elements#automated-clicks) para más detalles.

## Slider
Un deslizador que los usuarios pueden arrastrar para seleccionar un valor de una lista o un rango. Puede ejecutar acciones cada vez que cambia su valor.

*   **Casos de uso:**
    *   Crear un control de volumen personalizado.
    *   Un deslizador para cambiar entre distintos temas o imágenes de fondo (usando el tipo "Lista").
    *   Ajustar una opción específica de Minecraft, como el brillo o la distancia de renderizado.
*   **Características principales:**
    *   **Tipos:** Puede ser una `Lista de valores` (por ejemplo, "Fácil", "Normal", "Difícil"), un `Rango entero` (por ejemplo, 1-100) o un `Rango decimal` (por ejemplo, 0,0-1,0).
    *   **Acciones dinámicas:** Ejecuta acciones cuando cambia su valor. El valor actual se puede usar con [Variables](./variables).
    *   **Personalización:** La etiqueta del deslizador puede mostrar dinámicamente su valor actual. Las texturas del tirador y del fondo son totalmente personalizables, incluyendo fondos transparentes, opciones de color/escala de la etiqueta, activación/desactivación de sombra del texto y sonidos personalizados de clic/no pasar el cursor.

## Checkbox
Una casilla de verificación estándar que se puede activar o desactivar. Puede ejecutar acciones al cambiar su estado.

*   **Casos de uso:**
    *   Una casilla de "Acepto las normas".
    *   Un ajuste para activar o desactivar una función específica en tu menú personalizado.
    *   Activar o desactivar un diseño o una variable.
*   **Características principales:**
    *   **Acciones al cambiar:** Ejecuta [scripts de acciones](./action-scripts) cuando cambia su estado. El estado actual (`true` o `false`) está disponible para sus acciones.
    *   **Modo variable:** Puede vincularse directamente a una variable de FancyMenu, haciendo que el estado de la casilla se lea y escriba en esa variable.
    *   **Estado persistente:** Cuando el Modo variable está desactivado, la casilla guarda automáticamente su estado por identificador de elemento y lo restaura tras reiniciar el juego. Estos estados se almacenan en `<game-directory>/checkbox_states.json`. En Modo variable, la variable de FancyMenu vinculada es la fuente del estado de la casilla.
    *   **Apariencia personalizada:** Admite texturas personalizadas para el fondo (en estados normal, resaltado e inactivo) y para la propia marca de verificación.

## Text Input Field
Un campo donde los usuarios pueden escribir texto. Su contenido puede vincularse a una variable de FancyMenu, lo que te permite capturar y usar la entrada del usuario.

*   **Casos de uso:**
    *   Un campo de entrada de "IP del servidor" que funcione con un botón de "Unirse al servidor".
    *   Un campo para introducir el nombre de un jugador para una vista previa de skin personalizada.
    *   Crear una interfaz básica tipo inicio de sesión.
*   **Características principales:**
    *   **Vinculación con variables:** Guarda el texto introducido en una [variable](./variables) específica.
    *   **Validación de entrada:** Se puede configurar para aceptar solo tipos concretos de caracteres, como números, URLs o texto sin formato.
    *   **Longitud máxima:** Puedes establecer un límite máximo de caracteres para la entrada.
    *   **Apariencia y sonidos:** Admite color de fondo personalizado, colores del borde, redondeo del borde, color del texto, texto de pista/marcador, color de la pista, sonidos al pasar el cursor, al dejar de pasar el cursor y al hacer clic.

## Tooltip
Un cuadro de texto que puede aparecer en una posición fija o seguir el cursor del ratón. Su visibilidad normalmente se controla con [Requisitos de carga](./conditions).

*   **Casos de uso:**
    *   Mostrar información detallada cuando el usuario pasa el cursor sobre un botón o una imagen.
    *   Crear ayudas contextuales que aparecen bajo ciertas condiciones.
    *   Mostrar información dinámica (como el estado del servidor) junto al cursor.
*   **Características principales:**
    *   **Seguimiento del ratón:** Se puede configurar para seguir el puntero del ratón.
    *   **Compatibilidad con Markdown:** El contenido del tooltip admite formato Markdown completo.
    *   **Fondo personalizado:** El fondo puede ser de color sólido o una textura personalizada con nine-slicing para un aspecto totalmente temático.

## Item
Muestra un único objeto de Minecraft, ya sea de vainilla o de un mod.

*   **Casos de uso:**
    *   Usar objetos como iconos para botones o selecciones de menú.
    *   Crear una interfaz de tienda o selección de kits.
    *   Mostrar el objeto o la armadura que lleva equipado un jugador.
*   **Características principales:**
    *   **Datos personalizados:** Admite nombre personalizado, lore, cantidad, brillo de encantamiento y datos NBT. Consulta el [Marcador de posición de datos NBT](./nbt-data-placeholder).
    *   **Mostrar tooltip:** Se puede configurar para mostrar el tooltip estándar del objeto al pasar el cursor.

## Block/Item JSON Model
Renderiza un modelo JSON de bloque u objeto a partir de recursos de Minecraft o de fuentes externas.

*   **Casos de uso:**
    *   Mostrar un modelo 3D de un paquete de recursos en un menú.
    *   Enseñar vistas previas de objetos/bloques con texturas personalizadas.
    *   Crear elementos decorativos de interfaz basados en modelos.
*   **Características principales:**
    *   **Origen del modelo:** Puede cargar el JSON del modelo desde recursos de Minecraft o fuentes externas.
    *   **Sustitución de texturas:** Admite establecer una textura personalizada.
    *   **Controles de renderizado:** Desplazamiento del modelo, escala, rotación en tres ejes, renderizado translúcido y la transformación GUI del modelo.
    *   **Iluminación:** Dos luces configurables con controles independientes de tono y rotación.

## Image
Muestra una imagen estática desde un archivo local, una URL web o una ubicación de recurso de Minecraft.

*   **Casos de uso:**
    *   Añadir el logo de un servidor o la marca de un modpack.
    *   Crear bordes decorativos o marcos de interfaz.
    *   Usar imágenes como parte de un diseño de interfaz más complejo.
*   **Características principales:**
    *   **Nine-slicing:** Escala bordes o paneles sin deformar las esquinas. Consulta [Nine-Slicing y mosaico](./nine-slicing-and-tiling).
    *   **Repetición de textura:** La imagen puede repetirse en mosaico para rellenar el área del elemento.
    *   **Tintado:** Puedes aplicar un tinte de color a la imagen.
    *   **Esquinas redondeadas:** Las imágenes que no usan nine-slicing ni repetición pueden tener esquinas redondeadas.
    *   **Efecto parallax:** Se mueve con el ratón para crear profundidad visual. Consulta [Efecto parallax](./parallax).

## Text
Un elemento muy versátil para mostrar texto. Puede usarse para cualquier cosa, desde etiquetas de una sola línea hasta documentos multipágina con desplazamiento.

*   **Casos de uso:**
    *   Mostrar normas del servidor, notas de parche o mensajes de bienvenida.
    *   Crear paneles de información dinámicos usando [marcadores de posición](./placeholders), por ejemplo `Welcome, {"placeholder":"playername"}!`.
    *   Añadir etiquetas y descripciones a tu interfaz.
*   **Características principales:**
    *   **Fuentes de contenido:** El texto puede introducirse directamente, cargarse desde un archivo local o obtenerse desde una URL web.
    *   **Compatibilidad con Markdown:** Admite encabezados, listas, bloques de código, tablas y otros formatos Markdown. Consulta [Formato de texto](./text-formatting).
    *   **Desplazamiento:** Pasa automáticamente a ser desplazable si el contenido es mayor que el área del elemento. Las barras de desplazamiento se pueden personalizar o desactivar.
    *   **Estilo:** Control total sobre el color del texto, la escala, la alineación, la sombra y el espaciado entre líneas.

## Video
Reproduce un archivo de vídeo. Es perfecto para introducciones cinemáticas o fondos decorativos en bucle.

> [!WARNING]
> El elemento nativo de vídeo requiere **Watermedia V3** y **Watermedia Binaries V3**. El antiguo elemento **Video [Rinku]** está obsoleto.

*   **Casos de uso:**
    *   Un tráiler animado del modpack o del servidor.
    *   Un vídeo ambiental en bucle para dar vida a tu menú.
    *   Un vídeo tutorial dentro del juego.
*   **Características principales:**
    *   **Fuentes:** Admite archivos de vídeo locales y URLs web. Consulta [Vídeos](./video).
    *   **Control de reproducción:** Se puede configurar para que se repita automáticamente. Su volumen, canal de sonido y comportamiento de conservación de la relación de aspecto son ajustables.
    *   **Control interactivo:** La reproducción, el tiempo de avance y el volumen del vídeo se pueden controlar mediante acciones de botones.

## GLSL Shader
Renderiza un shader GLSL personalizado dentro de un elemento.

*   **Casos de uso:**
    *   Paneles animados con shaders.
    *   Efectos visuales procedurales.
    *   Efectos de menú al estilo Shadertoy recortados a un rectángulo de elemento.
*   **Características principales:**
    *   **Entorno de ejecución del shader:** Admite shaders de un solo pase y de varios pases.
    *   **Compatibilidad con Shadertoy:** Puede usar shaders `mainImage` al estilo Shadertoy.
    *   **Uniforms:** Expone uniforms de FancyMenu y de entrada. Consulta la [API de shaders GLSL](./glsl-shader-api).

## Slideshow
Muestra una secuencia de imágenes. Sus imágenes y el archivo de configuración `properties.txt` están en el propio subdirectorio de la presentación bajo `<game-directory>/config/fancymenu/slideshows/`.

*   **Casos de uso:**
    *   Una galería rotatoria de capturas de pantalla del juego.
    *   Mostrar las características clave de un modpack.
    *   Un fondo dinámico que alterna entre distintas escenas.
*   **Características principales:**
    *   Carga [presentaciones](./slideshows) preconfiguradas.
    *   Se puede configurar para mantener la relación de aspecto de las imágenes.

## Rectangle Shape
Un rectángulo simple de color sólido.

*   **Casos de uso:**
    *   Crear un fondo semitransparente detrás del texto para mejorar la legibilidad.
    *   Diseñar paneles e विभisores sencillos de interfaz.
    *   Como marcador de posición coloreado durante el diseño del layout.
*   **Características principales:**
    *   Admite colores HEX RGBA, esquinas redondeadas y desenfoque opcional, lo que permite que la forma funcione como un panel simple, un tinte o un fondo desenfocado.

## Circle Shape
Un círculo/elipse simple de color sólido.

*   **Casos de uso:**
    *   Crear adornos circulares, indicadores o zonas suaves de interfaz.
    *   Construir decoraciones temáticas de interfaz sin un archivo de textura.
*   **Características principales:**
    *   Admite color, desenfoque y un valor configurable de redondez/exponente.

## Splash Text
Una recreación del icónico texto amarillo rebotante de la pantalla principal de Minecraft.

*   **Casos de uso:**
    *   Sustituir el texto splash de vainilla por tus propios mensajes personalizados.
    *   Añadir un mensaje llamativo y animado a cualquier menú.
*   **Características principales:**
    *   **Fuentes de contenido:** Puede usar los splashes vainilla predeterminados, una lista de texto personalizado introducido directamente o texto desde un archivo local.
    *   **Personalización:** Puedes activar o desactivar el efecto de rebote y personalizar el color, la escala, la rotación y la sombra del texto.

## Player Entity
Renderiza un modelo de jugador en el menú.

*   **Casos de uso:**
    *   Mostrar el personaje del jugador actual en el menú principal.
    *   Crear una pantalla de selección de equipo o vista previa de clase.
    *   Una sección de "perfil" que muestre la skin y el nombre del jugador.
*   **Características principales:**
    *   **Apariencia dinámica:** Puede copiar la skin, la capa y el nombre del jugador actual. Consulta [Cabezales de jugador](./player-heads).
    *   **Posturas personalizadas:** Ofrece control detallado sobre la rotación de la cabeza, el cuerpo, los brazos y las piernas. La cabeza y el cuerpo también pueden configurarse para seguir el cursor del ratón.
    *   **Atributos:** Se puede configurar como bebé, agachado o con modelo estrecho.

## Browser
Un elemento que renderiza una página web en vivo dentro del juego.

Este elemento requiere que el mod **[Rinku](https://modrinth.com/mod/rinku)** esté instalado y funcionando.

Puedes descargar Rinku desde las páginas oficiales del proyecto en [CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku) y [Modrinth](https://modrinth.com/mod/rinku).

*   **Casos de uso:**
    *   Mostrar un Dynmap en vivo de un servidor.
    *   Incrustar un reproductor de vídeo de YouTube.
    *   Mostrar una wiki o una página de documentación directamente dentro del juego.
*   **Características principales:**
    *   **Interactividad:** Puede hacerse totalmente interactivo, permitiendo a los usuarios hacer clic en enlaces, desplazarse y escribir.
    *   **Control de medios:** Ofrece opciones para silenciar los medios, repetir vídeos y ocultar los controles de vídeo en la página cargada.

### Cargar archivos HTML locales
El elemento Browser puede cargar documentos HTML locales desde `<game-directory>/config/fancymenu/assets/`.

Para cargar un archivo HTML local, empieza tu URL con `file:///`, seguido de la ruta de archivo SHORT, por ejemplo `/config/fancymenu/assets/cool_changelog.html`, lo que quedaría así: `file:///config/fancymenu/assets/cool_changelog.html`.

En **Linux**, usa el marcador de posición de [**Ruta absoluta de archivo/carpeta**](./placeholders#absolute-filefolder-path-absolute_path) en lugar de codificar una ruta absoluta específica de la instancia: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

La ruta corta de Linux debe empezar por `/`, como se muestra en el ejemplo.

## Element Animator
Una poderosa herramienta para crear animaciones complejas basadas en fotogramas clave. Puede animar la posición, el tamaño y el punto de anclaje de uno o varios elementos.

*   **Casos de uso:**
    *   Desplazar elementos hacia dentro o fuera de la vista.
    *   Redimensionar paneles o notificaciones.
    *   Animar desplazamientos de posición y transiciones de anclaje.
*   **Características principales:**
    *   **Editor de fotogramas clave:** Un editor dedicado para añadir, editar y secuenciar fotogramas clave en una línea de tiempo.
    *   **Multidestino:** Un único Animator puede controlar varios elementos "destino" a la vez.
    *   **Control:** Las animaciones se pueden configurar en bucle. También puedes elegir animar solo la posición o el tamaño.
    *   **Desplazamientos de tiempo:** Los elementos destino pueden usar desplazamientos de tiempo de inicio individuales o aleatorios.
    *   Consulta [Element Animator](./element-animator) para la configuración y edición de fotogramas clave.

## Ticker
Un elemento invisible que ejecuta una lista de acciones a intervalos regulares (cada "tick").

> [!NOTE]
> Para la automatización en segundo plano, considera usar [Programadores](./schedulers). Los programadores son globales y pueden ejecutarse de forma independiente de una pantalla concreta.

*   **Casos de uso:**
    *   Comprobar periódicamente el estado en línea de un servidor y actualizar un elemento de texto.
    *   Crear un temporizador de cuenta atrás que actualice una etiqueta de texto.
    *   Ejecutar un script repetidamente para crear comportamientos personalizados.
*   **Características principales:**
    *   **Control de tiempo:** Puedes establecer el retraso entre ticks en milisegundos.
    *   **Modos de tick:** Se puede configurar para hacer tick continuamente, solo una vez por sesión de juego o una vez cada vez que se carga el menú.
    *   **Asíncrono:** Puede ejecutar sus [acciones](./action-scripts) por separado, aunque algunas acciones no pueden ejecutarse mientras esta opción está activada.

## Audio
Un elemento invisible que reproduce archivos de audio. Puede gestionar una lista de reproducción de pistas y ofrece varios controles de reproducción.

*   **Casos de uso:**
    *   Añadir música de fondo personalizada a un menú.
    *   Crear un reproductor de música con botones para controlar la reproducción (pista siguiente/anterior, volumen).
    *   Reproducir paisajes sonoros ambientales.
*   **Características principales:**
    *   **Lista de reproducción:** Puede gestionar varias pistas de audio.
    *   **Modos de reproducción:** Puede reproducir pistas en orden o en orden aleatorio (con compatibilidad con ponderación de pistas para que algunas sean más frecuentes que otras).
    *   **Control:** Admite repetición, ajuste de volumen y selección de canal de sonido. Consulta [Música de fondo del menú](./background-music).

## Music Controller
Un elemento invisible utilizado para controlar la reproducción de música predeterminada de Minecraft dentro de un menú específico.

*   **Casos de uso:**
    *   Desactivar la música predeterminada del menú en una pantalla en la que quieras reproducir tu propia música personalizada mediante un [elemento **Audio**](#audio).
    *   Evitar que la música del mundo siga sonando cuando se abre un menú dentro del juego.
*   **Características principales:**
    *   Interruptores separados para controlar la "Música del menú" y la "Música del mundo" de vainilla.

## Progress Bar
Una barra personalizable que representa visualmente un valor numérico.

*   **Casos de uso:**
    *   Una barra de carga que sigue el progreso de carga del mundo usando `{"placeholder":"world_load_progress"}`.
    *   Barras visuales de salud, hambre o experiencia para un HUD dentro del juego.
    *   Un indicador de volumen controlado por un [elemento **Slider**](#slider).
*   **Características principales:**
    *   **Valor dinámico:** El valor de progreso (0-100 o 0,0-1,0) se establece mediante un campo de texto que admite [marcadores de posición](./placeholders).
    *   **Apariencia:** La dirección de la barra (arriba, abajo, izquierda, derecha), los colores, las texturas y el nine-slicing para las texturas de barra/fondo son totalmente personalizables.
    *   **Animación:** Incluye una animación de relleno suave para que los cambios de progreso resulten menos bruscos.
    *   **Anclaje de elemento basado en el progreso:** Cuando otro elemento usa la barra de progreso como anclaje de **Elemento**, activa **Usar progreso para el anclaje del elemento** para mover ese anclaje hasta el borde actual del área rellena. Los elementos anclados entonces se desplazan con el progreso de la barra en lugar de permanecer unidos a los límites estáticos de la barra de progreso.

## Dragger
Un elemento invisible sobre el que el usuario puede hacer clic y arrastrar para moverlo. Otros elementos pueden anclarse a él para crear widgets móviles.

*   **Casos de uso:**
    *   Crear un reloj o panel de información arrastrable.
    *   Permitir que los usuarios personalicen la posición de los elementos de la interfaz según sus preferencias.
*   **Características principales:**
    *   **Persistencia opcional:** Activa **Guardar desplazamiento de arrastre del usuario** para conservar la posición arrastrada por el usuario al abrir pantallas y al reiniciar el juego. Desactívalo para restablecer el desplazamiento.
    *   **Punto de anclaje:** Actúa como un anclaje móvil para otros elementos, lo cual es una parte clave de [Posicionar elementos](./positioning-elements).

## Cursor
Un elemento invisible que sustituye el cursor del sistema predeterminado por una imagen personalizada cuando un diseño está activo.

*   **Casos de uso:**
    *   Crear una interfaz totalmente tematizada que encaje con la estética de tu modpack.
*   **Características principales:**
    *   **Textura personalizada:** Usa cualquier imagen para tu cursor.
    *   **Hotspot:** Define el píxel exacto de la imagen que se usará como punto de clic. Consulta [Cursor personalizado](./custom-cursor).
