---
title: Elementos
description: Todo lo que necesitas saber sobre los tipos de elementos de FancyMenu.
---

# Elementos

Los elementos son los bloques de construcción de tus diseños personalizados en FancyMenu. Puedes añadirlos a cualquier diseño para mostrar información, añadir interactividad o crear efectos visuales impresionantes.

# Añadir elementos a un diseño

Puedes añadir un nuevo elemento a tu diseño desde el **Editor de diseños**.

1.  **Haz clic con el botón derecho** sobre el fondo del editor para abrir el menú contextual.
2.  Pasa el cursor sobre **Nuevo elemento**.
3.  Aparecerá una lista con todos los tipos de elemento disponibles. Haz clic en el que quieras añadir.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Una vez añadido un elemento, puedes moverlo, cambiar su tamaño y personalizarlo haciendo **clic con el botón derecho** sobre él para abrir su menú contextual específico. Para saber más sobre cómo organizar los elementos, consulta las páginas [Posicionamiento de elementos](https://docs.fancymenu.net/en/positioning-elements) e [Identificadores de elementos](https://docs.fancymenu.net/en/element-identifiers).

# Elementos en detalle

La siguiente lista contiene la mayoría, si no todos, los elementos disponibles en FancyMenu. La lista a veces puede estar algo desactualizada debido a las actualizaciones de FancyMenu.

## Button
Un botón clicable que puede realizar una gran variedad de acciones. Este es uno de los elementos más potentes y versátiles para crear menús interactivos.

*   **Casos de uso:**
    *   Crear un botón de "Unirse a Discord" o "Visitar sitio web".
    *   Añadir un botón de unión rápida para un servidor concreto.
    *   Crear navegación personalizada entre distintos menús.
    *   Crear botones que activen o desactiven otros diseños.
*   **Características clave:**
    *   **Acciones:** Puede ejecutar una secuencia de acciones, como abrir una URL, unirse a un servidor, enviar un comando de chat, imitar la función de otro botón, controlar variables y mucho más. Más información en la documentación de [Scripts de acciones](https://docs.fancymenu.net/en/action-scripts).
    *   **Apariencia personalizada:** Texturas totalmente personalizables para los estados normal, resaltado e inactivo. Admite fondos transparentes, nine-slicing, colores personalizados de etiqueta, colores de etiqueta al pasar el cursor, escala de etiqueta, activación/desactivación de sombra de etiqueta y texturas personalizadas para el icono del botón.
    *   **Sonidos:** Sonidos personalizados de clic, pasar el cursor y sacar el cursor.
    *   **Modo plantilla:** Puede actuar como plantilla para aplicar su apariencia y propiedades a todos los demás botones de Vanilla o de mods del menú, garantizando un aspecto uniforme. Lee más en la página [Plantillas de botones y deslizadores](https://docs.fancymenu.net/en/button-slider-templates).

## Slider
Un deslizador que los usuarios pueden arrastrar para seleccionar un valor de una lista o de un rango. Puede ejecutar acciones cada vez que cambia su valor.

*   **Casos de uso:**
    *   Crear un control de volumen personalizado.
    *   Un deslizador para cambiar entre distintos temas o imágenes de fondo (usando el tipo "Lista").
    *   Ajustar una opción concreta de Minecraft, como el brillo o la distancia de renderizado.
*   **Características clave:**
    *   **Tipos:** Puede ser una `Lista de valores` (p. ej., "Fácil", "Normal", "Difícil"), un `Rango de enteros` (p. ej., 1-100) o un `Rango decimal` (p. ej., 0,0-1,0).
    *   **Acciones dinámicas:** Ejecuta acciones al cambiar el valor. El valor actual del deslizador se puede usar dentro de sus acciones para realizar tareas dinámicas, y puede combinarse con [Variables](https://docs.fancymenu.net/en/variables).
    *   **Personalización:** La etiqueta del deslizador puede mostrar dinámicamente su valor actual. Las texturas del control y del fondo son totalmente personalizables, incluidas opciones de fondos transparentes, color/escala de etiqueta, activación/desactivación de sombra del texto y sonidos personalizados al hacer clic o al sacar el cursor.

## Checkbox
Una casilla de verificación estándar que puede activarse o desactivarse. Puede ejecutar acciones al cambiar de estado.

*   **Casos de uso:**
    *   Una casilla de "Acepto las normas".
    *   Un ajuste para activar o desactivar una función concreta en tu menú personalizado.
    *   Activar o desactivar un diseño o una variable.
*   **Características clave:**
    *   **Acciones al cambiar:** Ejecuta [Scripts de acciones](https://docs.fancymenu.net/en/action-scripts) cuando cambia su estado. El estado actual (`true` o `false`) se puede consultar dentro de sus acciones.
    *   **Modo variable:** Puede vincularse directamente a una variable de FancyMenu, de modo que el estado de la casilla lea y escriba en esa variable.
    *   **Apariencia personalizada:** Admite texturas personalizadas para el fondo (en estado normal, al pasar el cursor e inactivo) y para la propia marca de verificación.

## Text Input Field
Un campo en el que los usuarios pueden escribir texto. Su contenido puede vincularse a una variable de FancyMenu, lo que te permite capturar y usar la entrada del usuario.

*   **Casos de uso:**
    *   Un campo de entrada para "IP del servidor" que funciona con un botón "Unirse al servidor".
    *   Un campo para introducir el nombre de un jugador para una vista previa de skin personalizada.
    *   Crear una interfaz básica similar a un inicio de sesión.
*   **Características clave:**
    *   **Vinculación a variables:** El texto introducido por el usuario se almacena en una [variable](https://docs.fancymenu.net/en/variables) específica.
    *   **Validación de entrada:** Se puede configurar para aceptar solo tipos concretos de caracteres, como números, URLs o texto plano.
    *   **Longitud máxima:** Puedes establecer un límite máximo de caracteres para la entrada.
    *   **Apariencia y sonidos:** Admite color de fondo personalizado, colores del borde, redondeo del borde, color del texto, texto de sugerencia/placeholder, color de la sugerencia, sonidos al pasar el cursor, al sacar el cursor y al hacer clic.

## Tooltip
Un cuadro de texto que se puede configurar para aparecer en una ubicación concreta o seguir el cursor del ratón. Su visibilidad normalmente se controla mediante [Condiciones (requisitos de carga)](https://docs.fancymenu.net/en/conditions).

*   **Casos de uso:**
    *   Mostrar información detallada cuando el usuario pasa el cursor sobre un botón o una imagen.
    *   Crear ayudas contextuales que aparezcan bajo ciertas condiciones.
    *   Mostrar información dinámica (como el estado de un servidor) junto al cursor.
*   **Características clave:**
    *   **Seguimiento del ratón:** Se puede configurar para seguir el puntero del ratón.
    *   **Compatibilidad con Markdown:** El contenido del tooltip admite formato Markdown completo.
    *   **Fondo personalizado:** El fondo puede ser de un color sólido o una textura personalizada con nine-slicing para un aspecto totalmente tematizado.

## Item
Muestra un único objeto de Minecraft, ya sea de vanilla o de un mod.

*   **Casos de uso:**
    *   Usar objetos como iconos para botones o selecciones de menú.
    *   Crear una interfaz de tienda o de selección de kits.
    *   Mostrar el objeto o la armadura que lleva un jugador.
*   **Características clave:**
    *   **Datos personalizados:** Puedes configurar el nombre del objeto, la descripción, la cantidad, el brillo de encantamiento e incluso datos NBT personalizados. Puedes aprender más sobre el uso de NBT con la documentación de [Marcador de posición de datos NBT](https://docs.fancymenu.net/en/nbt-data-placeholder).
    *   **Mostrar tooltip:** Se puede configurar para mostrar el tooltip estándar del objeto al pasar el cursor.

## Block/Item JSON Model
Renderiza un modelo JSON de bloque u objeto desde recursos de Minecraft o desde fuentes externas.

*   **Casos de uso:**
    *   Mostrar un modelo 3D de un paquete de recursos en un menú.
    *   Enseñar vistas previas de objetos/bloques con texturas personalizadas.
    *   Crear elementos decorativos de interfaz basados en modelos.
*   **Características clave:**
    *   **Fuente del modelo:** Puede cargar el JSON del modelo desde recursos de Minecraft o desde fuentes externas.
    *   **Sustitución de texturas:** Admite establecer una textura personalizada.
    *   **Controles de renderizado:** Incluye controles de rotación e iluminación.

## Image
Muestra una imagen estática desde un archivo local, una URL web o una ubicación de recurso de Minecraft.

*   **Casos de uso:**
    *   Añadir un logotipo de servidor o la marca de un modpack.
    *   Crear bordes decorativos o marcos de interfaz.
    *   Usar imágenes como parte de un diseño de interfaz más complejo.
*   **Características clave:**
    *   **Nine-Slicing:** Permite usar la imagen como un borde o panel escalable sin deformar las esquinas. Más información en la página [Nine-Slicing y tiling](https://docs.fancymenu.net/en/nine-slicing-and-tiling).
    *   **Repetición de textura:** La imagen puede repetirse en mosaico para llenar el área del elemento.
    *   **Tintado:** Puedes aplicar un tinte de color a la imagen.
    *   **Esquinas redondeadas:** Las imágenes que no usan nine-slicing ni repetición pueden tener esquinas redondeadas.
    *   **Efecto parallax:** Se puede configurar para que se mueva ligeramente con el ratón y lograr un efecto 3D. Consulta la página [Efecto parallax](https://docs.fancymenu.net/en/parallax) para más información.

## Text
Un elemento muy versátil para mostrar texto. Se puede usar para todo, desde etiquetas de una sola línea hasta documentos multipágina y desplazables.

*   **Casos de uso:**
    *   Mostrar normas del servidor, notas del parche o mensajes de bienvenida.
    *   Crear paneles de información dinámicos usando [marcadores de posición](https://docs.fancymenu.net/en/placeholders), por ejemplo, "¡Bienvenido, `{"placeholder":"playername"}`!".
    *   Añadir etiquetas y descripciones a tu interfaz.
*   **Características clave:**
    *   **Fuentes de contenido:** El texto se puede introducir directamente, cargar desde un archivo local o obtener desde una URL web.
    *   **Compatibilidad con Markdown:** Admite una amplia gama de Markdown para formato de texto enriquecido, incluidos encabezados, listas, bloques de código y tablas. La apariencia de los elementos Markdown es totalmente personalizable. Consulta la página [Formato de texto](https://docs.fancymenu.net/en/text-formatting) para más información.
    *   **Desplazamiento:** Se vuelve desplazable automáticamente si el contenido es mayor que el área del elemento. Las barras de desplazamiento se pueden personalizar o desactivar.
    *   **Estilo:** Control total sobre el color del texto, la escala, la alineación, la sombra y el espaciado entre líneas.

## Video
Reproduce un archivo de vídeo. Es perfecto para intros cinemáticas o fondos decorativos en bucle.

> El nuevo elemento nativo de vídeo en FancyMenu 3.9.0 requiere **Watermedia V3** y **Watermedia Binaries V3**. El antiguo elemento **Video [MCEF]** está obsoleto.
{.is-warning}

*   **Casos de uso:**
    *   Un tráiler animado del modpack o del servidor.
    *   Un vídeo ambiental en bucle para dar vida al menú.
    *   Un vídeo tutorial dentro del juego.
*   **Características clave:**
    *   **Fuentes:** Admite tanto archivos de vídeo locales como URL web. Consulta la página [Vídeos (MP4)](https://docs.fancymenu.net/en/video) para más detalles.
    *   **Control de reproducción:** Se puede configurar para repetir automáticamente. Su volumen, canal de sonido y comportamiento de conservación de la relación de aspecto son ajustables.
    *   **Control interactivo:** La reproducción, el tiempo de avance y el volumen del vídeo se pueden controlar mediante acciones de botones.

## GLSL Shader
Renderiza un shader GLSL personalizado dentro de un elemento.

*   **Casos de uso:**
    *   Paneles con shaders animados.
    *   Efectos visuales procedurales.
    *   Efectos de menú al estilo Shadertoy recortados al rectángulo de un elemento.
*   **Características clave:**
    *   **Ejecución del shader:** Admite shaders de una sola pasada y de varias pasadas.
    *   **Compatibilidad con Shadertoy:** Puede usar shaders `mainImage` al estilo Shadertoy.
    *   **Uniformes:** Expone uniformes de FancyMenu y de entrada. Consulta la página [API del shader GLSL](https://docs.fancymenu.net/en/glsl-shader-api) para más detalles.

## Slideshow
Muestra una secuencia de imágenes. La configuración del pase de diapositivas (imágenes, tiempos, transiciones) se realiza en un archivo `.properties` independiente situado en el directorio `/config/fancymenu/assets/slideshows/`.

*   **Casos de uso:**
    *   Una galería rotatoria de capturas de pantalla del juego.
    *   Mostrar las características clave de un modpack.
    *   Un fondo dinámico que alterna entre distintas escenas.
*   **Características clave:**
    *   Carga pases de diapositivas preconfigurados. Consulta la documentación de [Pases de diapositivas](https://docs.fancymenu.net/en/slideshows) para ver las instrucciones de configuración.
    *   Se puede configurar para mantener la relación de aspecto de las imágenes.

## Rectangle Shape
Un rectángulo simple de color sólido.

*   **Casos de uso:**
    *   Crear un fondo semitransparente detrás del texto para mejorar la legibilidad.
    *   Diseñar paneles e বিভiders de interfaz sencillos.
    *   Como marcador de posición de color durante el diseño del layout.
*   **Características clave:**
    *   Admite colores HEX RGBA, esquinas redondeadas y desenfoque opcional, lo que permite que la forma funcione como un panel sencillo, un tinte o un fondo desenfocado.

## Circle Shape
Una forma simple de círculo/elipse de color sólido.

*   **Casos de uso:**
    *   Crear acentos circulares, indicadores o zonas suaves de interfaz.
    *   Construir decoraciones de interfaz tematizadas sin un archivo de textura.
*   **Características clave:**
    *   Funciona de forma similar al elemento Rectangle Shape y admite personalización visual de color/estilo desenfoque.

## Splash Text
Una recreación del icónico texto amarillo rebotante de la pantalla de título de Minecraft.

*   **Casos de uso:**
    *   Sustituir el splash text de vanilla por tus propios mensajes personalizados.
    *   Añadir un mensaje animado y llamativo a cualquier menú.
*   **Características clave:**
    *   **Fuentes de contenido:** Puede usar los splashes predeterminados de vanilla, una lista de texto personalizado introducido directamente o texto desde un archivo local.
    *   **Personalización:** Puedes activar o desactivar el efecto de rebote y personalizar el color, la escala, la rotación y la sombra del texto.

## Player Entity
Renderiza un modelo de jugador en el menú.

*   **Casos de uso:**
    *   Mostrar el personaje del jugador actual en el menú principal.
    *   Crear una pantalla de selección de equipo o vista previa de clase.
    *   Una sección de "perfil" que muestre la skin y el nombre del jugador.
*   **Características clave:**
    *   **Apariencia dinámica:** Se puede configurar para copiar automáticamente la skin, la capa y el nombre del jugador actual. Para más información, consulta la guía de [Cabezas de jugador](https://docs.fancymenu.net/en/player-heads).
    *   **Posturas personalizadas:** Ofrece un control preciso sobre la rotación de la cabeza, el cuerpo, los brazos y las piernas. La cabeza y el cuerpo también se pueden configurar para seguir el cursor del ratón.
    *   **Atributos:** Se puede configurar para que sea un bebé, esté agachado o tenga un modelo delgado.

## Browser
Un elemento que renderiza una página web en directo dentro del juego.

Este elemento requiere que el mod **MCEF (Minecraft Chromium Embedded Framework)** esté instalado y funcionando.

Puedes descargar MCEF desde las páginas oficiales del proyecto en [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) y [Modrinth](https://modrinth.com/mod/mcef).

Para versiones más nuevas de Minecraft (1.21.5+), los proyectos oficiales de MCEF no ofrecen compilaciones, pero existe un fork con compilaciones para las últimas versiones de Minecraft, que puedes encontrar [aquí](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) y [aquí](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Este fork está mantenido por Keksuccino, para ofrecer compilaciones para las últimas versiones de Minecraft lo más rápido posible.

*   **Casos de uso:**
    *   Mostrar el Dynmap en directo de un servidor.
    *   Incrustar un reproductor de vídeo de YouTube.
    *   Mostrar una wiki o una página de documentación directamente dentro del juego.
*   **Características clave:**
    *   **Interactividad:** Se puede hacer completamente interactivo, permitiendo a los usuarios hacer clic en enlaces, desplazarse y escribir.
    *   **Control multimedia:** Ofrece opciones para silenciar el contenido, repetir vídeos y ocultar los controles del vídeo en la página cargada.

### Carga de archivos HTML locales
¡El elemento Browser te permite cargar documentos HTML locales en `/config/fancymenu/assets/`! Esto significa que puedes mostrar contenido local renderizado en el navegador para changelogs con un aspecto elegante y mucho más.

Para cargar un archivo HTML local, empieza tu URL con `file:///`, seguido de la ruta del archivo en formato CORTO; por ejemplo `/config/fancymenu/assets/cool_changelog.html`, que quedaría así: `file:///config/fancymenu/assets/cool_changelog.html`.

En **Linux** necesitas proporcionar la ruta absoluta del archivo, pero como escribir una ruta absoluta fija rompería el diseño, debes dejar que un marcador de posición convierta dinámicamente la ruta corta en una absoluta: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Es SUPERIMPORTANTE que en Linux la ruta corta empiece con `/`, como en el ejemplo anterior. Sin esto, no funcionará.

## Element Animator
Una herramienta potente para crear animaciones complejas basadas en fotogramas clave. Puede animar la posición, el tamaño y el punto de anclaje de uno o varios elementos.

*   **Casos de uso:**
    *   Crear una animación de introducción sofisticada en la que los elementos del menú se deslicen o aparezcan mediante fundido.
    *   Hacer que los elementos decorativos palpiten, roten o se muevan a lo largo de una trayectoria.
    *   Animar una notificación para que aparezca y luego desaparezca.
*   **Características clave:**
    *   **Editor de fotogramas clave:** Un editor dedicado para añadir, editar y secuenciar fotogramas clave en una línea de tiempo.
    *   **Multiobjetivo:** Un solo Animator puede controlar varios elementos "objetivo" a la vez.
    *   **Control:** Las animaciones se pueden configurar para repetirse. También puedes elegir animar solo la posición o el tamaño.
    *   **Desplazamientos de tiempo:** Los elementos objetivo pueden usar desplazamientos de inicio individuales o aleatorios.
    *   **[Más información sobre el Element Animator.](https://docs.fancymenu.net/en/element-animator)**

## Ticker
Un elemento invisible que ejecuta una lista de acciones a intervalos regulares (cada "tick").

> Para nuevas automatizaciones en segundo plano en FancyMenu 3.9.0+, considera usar [Programadores](https://docs.fancymenu.net/en/schedulers). Los programadores son globales, más fáciles de organizar y pueden seguir ejecutándose de forma independiente de una pantalla específica.
{.is-info}

*   **Casos de uso:**
    *   Comprobar periódicamente el estado en línea de un servidor y actualizar un elemento de texto.
    *   Crear una cuenta atrás que actualice una etiqueta de texto.
    *   Ejecutar un script repetidamente para crear comportamientos personalizados.
*   **Características clave:**
    *   **Control temporal:** Puedes establecer el retraso entre ticks en milisegundos.
    *   **Modos de tick:** Se puede configurar para que se ejecute continuamente, solo una vez por sesión de juego o una vez cada vez que se cargue el menú.
    *   **Asíncrono:** Puede ejecutar sus [acciones](https://docs.fancymenu.net/en/action-scripts) en un hilo separado para no afectar al rendimiento del juego, aunque algunas acciones no se pueden ejecutar así.

## Audio
Un elemento invisible que reproduce archivos de audio. Puede gestionar una lista de reproducción de pistas y ofrece varios controles de reproducción.

*   **Casos de uso:**
    *   Añadir música de fondo personalizada a un menú.
    *   Crear un reproductor de música con botones para controlar la reproducción (pista siguiente/anterior, volumen).
    *   Reproducir paisajes sonoros ambientales.
*   **Características clave:**
    *   **Lista de reproducción:** Puede gestionar varias pistas de audio.
    *   **Modos de reproducción:** Puede reproducir las pistas en orden o en orden aleatorio (con compatibilidad para ponderar pistas y hacer que algunas aparezcan con más frecuencia que otras).
    *   **Control:** Admite repetición, ajuste de volumen y puede asignarse a un canal de sonido específico (por ejemplo, Master, Music). Para más información, consulta la página [Música de fondo del menú](https://docs.fancymenu.net/en/background-music).

## Music Controller
Un elemento invisible usado para controlar la reproducción de la música predeterminada de Minecraft dentro de un menú concreto.

*   **Casos de uso:**
    *   Desactivar la música predeterminada del menú en una pantalla donde quieras reproducir tu propia música personalizada mediante un elemento **Audio**.
    *   Detener la música del mundo para que no siga sonando cuando se abre un menú dentro del juego.
*   **Características clave:**
    *   Interruptores separados para controlar la "Música del menú" y la "Música del mundo" de vanilla.

## Progress Bar
Una barra personalizable que representa visualmente un valor numérico.

*   **Casos de uso:**
    *   Una barra de carga que sigue el progreso de carga del mundo usando `{"placeholder":"world_load_progress"}`.
    *   Barras visuales de salud, hambre o experiencia para un HUD dentro del juego.
    *   Un indicador de volumen controlado por un elemento **Slider**.
*   **Características clave:**
    *   **Valor dinámico:** El valor de progreso (0-100 o 0,0-1,0) se establece mediante un campo de texto compatible con [marcadores de posición](https://docs.fancymenu.net/en/placeholders).
    *   **Apariencia:** La dirección de la barra (arriba, abajo, izquierda, derecha), los colores, las texturas y el nine-slicing para las texturas de la barra/fondo son totalmente personalizables.
    *   **Animación:** Incluye una animación de relleno suave para que los cambios de progreso se vean menos bruscos.

## Dragger
Un elemento invisible que el usuario puede pulsar y arrastrar para mover. Otros elementos se pueden anclar a él para crear widgets movibles.

*   **Casos de uso:**
    *   Crear un reloj o un panel de información arrastrable.
    *   Permitir a los usuarios personalizar la posición de los elementos de la interfaz según sus preferencias.
*   **Características clave:**
    *   **Posición persistente:** El desplazamiento arrastrado se guarda, de modo que el elemento permanece donde el usuario lo dejó, incluso después de reiniciar el juego.
    *   **Punto de anclaje:** Actúa como un anclaje movible para otros elementos, lo que es una parte clave de [Posicionamiento de elementos](https://docs.fancymenu.net/en/positioning-elements).

## Cursor
Un elemento invisible que reemplaza el cursor predeterminado del sistema por una imagen personalizada cuando un diseño está activo.

*   **Casos de uso:**
    *   Crear una interfaz completamente tematizada que encaje con la estética de tu modpack.
*   **Características clave:**
    *   **Textura personalizada:** Usa cualquier imagen como cursor.
    *   **Punto activo:** Puedes definir el píxel exacto de la imagen que actúa como "punto de clic". Consulta la guía [Cursor personalizado](https://docs.fancymenu.net/en/custom-cursor) para más información.
