---
title: Elementos
description: Todo lo que necesitas saber sobre los tipos de elementos de FancyMenu.
---

# Elementos

Los elementos son los bloques de construcción de tus diseños personalizados en FancyMenu. Puedes agregarlos a cualquier diseño para mostrar información, añadir interactividad o crear efectos visuales impresionantes.

# Agregar elementos a un diseño

Puedes agregar un nuevo elemento a tu diseño desde el **Editor de diseño**.

1.  **Haz clic derecho** sobre el fondo del editor para abrir el menú contextual.
2.  Pasa el cursor sobre **Nuevo elemento**.
3.  Aparecerá una lista con todos los tipos de elementos disponibles. Haz clic en el que quieras agregar.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Una vez agregado un elemento, puedes moverlo, cambiar su tamaño y personalizarlo haciendo **clic derecho** sobre él para abrir su menú contextual específico. Para aprender más sobre cómo acomodar elementos, consulta las páginas [Posicionar elementos](https://docs.fancymenu.net/en/positioning-elements) e [Identificadores de elementos](https://docs.fancymenu.net/en/element-identifiers).

# Elementos en detalle

La siguiente lista contiene la mayoría, si no es que todos, los elementos disponibles en FancyMenu. La lista a veces puede estar un poco desactualizada debido a actualizaciones de FancyMenu.

## Botón
Un botón clicable que puede realizar una gran variedad de acciones. Este es uno de los elementos más poderosos y versátiles para crear menús interactivos.

*   **Casos de uso:**
    *   Crear un botón de "Unirse a Discord" o "Visitar sitio web".
    *   Agregar un botón de ingreso rápido para un servidor específico.
    *   Construir navegación personalizada entre diferentes menús.
    *   Crear botones que activen o desactiven otros diseños.
*   **Características clave:**
    *   **Acciones:** Puede ejecutar una secuencia de acciones, como abrir una URL, unirse a un servidor, enviar un comando de chat, imitar la función de otro botón, controlar variables y mucho más. Aprende más en la documentación de [Scripts de acciones](https://docs.fancymenu.net/en/action-scripts).
    *   **Apariencia personalizada:** Texturas totalmente personalizables para los estados normal, al pasar el cursor e inactivo. Compatible con fondos transparentes, nine-slicing, colores personalizados de etiqueta, colores de etiqueta al pasar el cursor, escala de la etiqueta, activación/desactivación de sombra en la etiqueta y texturas de icono del botón.
    *   **Sonidos:** Sonidos personalizados de clic, al pasar el cursor y al quitar el cursor.
    *   **Modo plantilla:** Puede funcionar como plantilla para aplicar su apariencia y propiedades a todos los demás botones de Vanilla o de mods en el menú, asegurando un aspecto uniforme. Lee más en la página [Plantillas de botón y control deslizante](https://docs.fancymenu.net/en/button-slider-templates).

## Control deslizante
Un control deslizante que los usuarios pueden arrastrar para seleccionar un valor de una lista o un rango. Puede ejecutar acciones cada vez que su valor cambie.

*   **Casos de uso:**
    *   Crear un control de volumen personalizado.
    *   Un control deslizante para cambiar entre diferentes temas o imágenes de fondo (usando el tipo "Lista").
    *   Ajustar una opción específica de Minecraft, como el brillo o la distancia de renderizado.
*   **Características clave:**
    *   **Tipos:** Puede ser una `Lista de valores` (por ejemplo, "Fácil", "Normal", "Difícil"), un `Rango entero` (por ejemplo, 1-100) o un `Rango decimal` (por ejemplo, 0.0-1.0).
    *   **Acciones dinámicas:** Ejecuta acciones al cambiar el valor. El valor actual del control deslizante puede usarse dentro de sus acciones para realizar tareas dinámicas, lo cual puede aprovecharse con [Variables](https://docs.fancymenu.net/en/variables).
    *   **Personalización:** La etiqueta del control deslizante puede mostrar dinámicamente su valor actual. Las texturas del control y del fondo son totalmente personalizables, incluyendo fondos transparentes, opciones de color/escala de la etiqueta, activación/desactivación de sombra del texto y sonidos personalizados de clic y al quitar el cursor.

## Casilla de verificación
Una casilla estándar que se puede activar o desactivar. Puede ejecutar acciones al cambiar de estado.

*   **Casos de uso:**
    *   Una casilla de "Acepto las reglas".
    *   Una opción para activar o desactivar una característica específica en tu menú personalizado.
    *   Activar o desactivar un diseño o variable.
*   **Características clave:**
    *   **Acciones al cambiar:** Ejecuta [Scripts de acciones](https://docs.fancymenu.net/en/action-scripts) cuando cambia su estado. El estado actual (`true` o `false`) puede consultarse dentro de sus acciones.
    *   **Modo variable:** Puede vincularse directamente a una variable de FancyMenu, haciendo que el estado de la casilla lea y escriba en esa variable.
    *   **Apariencia personalizada:** Compatible con texturas personalizadas para el fondo (en estados normal, al pasar el cursor e inactivo) y para la marca de verificación.

## Campo de entrada de texto
Un campo donde los usuarios pueden escribir texto. Su contenido puede vincularse a una variable de FancyMenu, lo que te permite capturar y usar la entrada del usuario.

*   **Casos de uso:**
    *   Un campo de entrada "IP del servidor" que funcione con un botón "Unirse al servidor".
    *   Un campo para escribir el nombre de un jugador para una vista previa de skin personalizada.
    *   Crear una interfaz básica tipo inicio de sesión.
*   **Características clave:**
    *   **Vinculación con variables:** El texto que escribe el usuario se almacena en una [variable](https://docs.fancymenu.net/en/variables) específica.
    *   **Validación de entrada:** Puede configurarse para aceptar solo ciertos tipos de caracteres, como números, URLs o texto plano.
    *   **Longitud máxima:** Puedes establecer un límite máximo de caracteres para la entrada.
    *   **Apariencia y sonidos:** Compatible con color de fondo personalizado, colores del borde, redondeo del borde, color del texto, texto de sugerencia/marcador de posición, color de sugerencia, sonidos al pasar el cursor, al quitar el cursor y al hacer clic.

## Tooltip
Un cuadro de texto que puede configurarse para aparecer en una ubicación específica o seguir el cursor del mouse. Su visibilidad normalmente está controlada por [Condiciones (Requisitos de carga)](https://docs.fancymenu.net/en/conditions).

*   **Casos de uso:**
    *   Mostrar información detallada cuando el usuario pasa el cursor sobre un botón o una imagen.
    *   Crear consejos de ayuda contextuales que aparezcan bajo ciertas condiciones.
    *   Mostrar información dinámica (como el estado del servidor) junto al cursor.
*   **Características clave:**
    *   **Seguimiento del mouse:** Puede configurarse para seguir el puntero del mouse.
    *   **Compatibilidad con Markdown:** El contenido del tooltip admite formato Markdown completo.
    *   **Fondo personalizado:** El fondo puede ser de color sólido o una textura personalizada con nine-slicing para lograr una apariencia totalmente temática.

## Objeto
Muestra un solo objeto de Minecraft, ya sea de Vanilla o de un mod.

*   **Casos de uso:**
    *   Usar objetos como iconos para botones o selecciones de menú.
    *   Crear una interfaz de tienda o selección de kits.
    *   Mostrar el objeto o la armadura que sostiene un jugador.
*   **Características clave:**
    *   **Datos personalizados:** Puedes establecer el nombre del objeto, su lore, cantidad, brillo de encantamiento e incluso datos NBT personalizados. Puedes aprender más sobre usar NBT con la documentación de [Marcador de posición de datos NBT](https://docs.fancymenu.net/en/nbt-data-placeholder).
    *   **Mostrar tooltip:** Puede configurarse para mostrar el tooltip estándar del objeto al pasar el cursor.

## Modelo JSON de bloque/objeto
Renderiza un modelo JSON de bloque u objeto desde recursos de Minecraft o fuentes externas.

*   **Casos de uso:**
    *   Mostrar un modelo 3D de un resource pack en un menú.
    *   Mostrar vistas previas de objetos/bloques con texturas personalizadas.
    *   Crear elementos decorativos de UI basados en modelos.
*   **Características clave:**
    *   **Fuente del modelo:** Puede cargar JSON del modelo desde recursos de Minecraft o fuentes externas.
    *   **Reemplazos de textura:** Permite establecer una textura personalizada.
    *   **Controles de renderizado:** Incluye controles de rotación e iluminación.

## Imagen
Muestra una imagen estática desde un archivo local, una URL web o una ubicación de recurso de Minecraft.

*   **Casos de uso:**
    *   Agregar un logo del servidor o la marca de un modpack.
    *   Crear bordes decorativos o marcos de interfaz.
    *   Usar imágenes como parte de un diseño de UI más complejo.
*   **Características clave:**
    *   **Nine-slicing:** Permite usar la imagen como un borde o panel escalable sin deformar las esquinas. Aprende más en la página [Nine-slicing y mosaico](https://docs.fancymenu.net/en/nine-slicing-and-tiling).
    *   **Repetición de textura:** La imagen puede repetirse en mosaico para llenar el área del elemento.
    *   **Tintado:** Puedes aplicar un tinte de color a la imagen.
    *   **Esquinas redondeadas:** Las imágenes que no usan nine-slicing ni repetición pueden tener esquinas redondeadas.
    *   **Efecto paralaje:** Puede configurarse para moverse ligeramente con el mouse y crear un efecto 3D. Consulta la página [Efecto paralaje](https://docs.fancymenu.net/en/parallax) para más información.

## Texto
Un elemento muy versátil para mostrar texto. Puede usarse para todo, desde etiquetas de una sola línea hasta documentos desplazables de varias páginas.

*   **Casos de uso:**
    *   Mostrar reglas del servidor, notas del parche o mensajes de bienvenida.
    *   Crear paneles de información dinámica usando [marcadores de posición](https://docs.fancymenu.net/en/placeholders), por ejemplo: "¡Bienvenido, `{"placeholder":"playername"}`!".
    *   Agregar etiquetas y descripciones a tu interfaz.
*   **Características clave:**
    *   **Fuentes de contenido:** El texto puede escribirse directamente, cargarse desde un archivo local o recuperarse desde una URL web.
    *   **Compatibilidad con Markdown:** Admite una amplia gama de Markdown para dar formato enriquecido al texto, incluyendo encabezados, listas, bloques de código y tablas. La apariencia de los elementos Markdown es totalmente personalizable. Consulta la página [Formato de texto](https://docs.fancymenu.net/en/text-formatting) para más información.
    *   **Desplazamiento:** Se vuelve desplazable automáticamente si el contenido es más grande que el área del elemento. Las barras de desplazamiento pueden personalizarse o desactivarse.
    *   **Estilo:** Control total sobre el color del texto, escala, alineación, sombra y espaciado entre líneas.

## Video
Reproduce un archivo de video. Es perfecto para intros cinemáticas o fondos decorativos en bucle.

> El nuevo elemento nativo de Video en FancyMenu 3.9.0 requiere **Watermedia V3** y **Watermedia Binaries V3**. El elemento antiguo **Video [MCEF]** está obsoleto.
{.is-warning}

*   **Casos de uso:**
    *   Un tráiler animado del modpack o del servidor.
    *   Un video ambiental en bucle para darle vida a tu menú.
    *   Un video tutorial dentro del juego.
*   **Características clave:**
    *   **Fuentes:** Compatible con archivos de video locales y URLs web. Consulta la página [Videos (MP4)](https://docs.fancymenu.net/en/video) para más detalles.
    *   **Control de reproducción:** Puede configurarse para repetirse automáticamente. Su volumen, canal de sonido y comportamiento para mantener la relación de aspecto son ajustables.
    *   **Control interactivo:** La reproducción, el tiempo de avance y el volumen del video pueden controlarse mediante acciones de botones.

## Shader GLSL
Renderiza un shader GLSL personalizado dentro de un elemento.

*   **Casos de uso:**
    *   Paneles animados con shaders.
    *   Efectos visuales procedurales.
    *   Efectos de menú tipo Shadertoy recortados dentro de un rectángulo de elemento.
*   **Características clave:**
    *   **Runtime del shader:** Compatible con shaders de un solo pase y de varios pases.
    *   **Compatibilidad con Shadertoy:** Puede usar shaders estilo Shadertoy `mainImage`.
    *   **Uniforms:** Expone uniforms de FancyMenu y de entrada. Consulta la página [API del Shader GLSL](https://docs.fancymenu.net/en/glsl-shader-api) para más detalles.

## Presentación
Muestra una secuencia de imágenes. La configuración de la presentación (imágenes, tiempos, transiciones) se hace en un archivo `.properties` separado ubicado en el directorio `/config/fancymenu/assets/slideshows/`.

*   **Casos de uso:**
    *   Una galería rotativa de capturas dentro del juego.
    *   Mostrar las características clave de un modpack.
    *   Un fondo dinámico que va alternando entre distintas escenas.
*   **Características clave:**
    *   Carga presentaciones preconfiguradas. Consulta la documentación de [Presentaciones](https://docs.fancymenu.net/en/slideshows) para ver las instrucciones de configuración.
    *   Puede configurarse para mantener la relación de aspecto de las imágenes.

## Forma de rectángulo
Un rectángulo simple de color sólido.

*   **Casos de uso:**
    *   Crear un fondo semitransparente detrás del texto para mejorar su legibilidad.
    *   Diseñar paneles y divisores sencillos de UI.
    *   Como marcador de posición de color durante el diseño del layout.
*   **Características clave:**
    *   Compatible con colores HEX RGBA, esquinas redondeadas y desenfoque opcional, lo que permite que la forma funcione como un panel simple, tinte o fondo difuminado.

## Forma de círculo
Una forma simple de círculo/elipse de color sólido.

*   **Casos de uso:**
    *   Crear acentos circulares, indicadores o áreas suaves de UI.
    *   Construir decoraciones de UI temáticas sin un archivo de textura.
*   **Características clave:**
    *   Funciona de manera similar al elemento Forma de rectángulo y admite personalización visual de color/estilo de desenfoque.

## Texto emergente
Una recreación del icónico texto emergente amarillo y rebotante de la pantalla de título de Minecraft.

*   **Casos de uso:**
    *   Reemplazar el texto emergente vanilla con tus propios mensajes personalizados.
    *   Agregar un mensaje animado y llamativo a cualquier menú.
*   **Características clave:**
    *   **Fuentes de contenido:** Puede usar los mensajes emergentes vanilla predeterminados, una lista de texto personalizado escrito directamente o texto desde un archivo local.
    *   **Personalización:** Puedes activar o desactivar el efecto de rebote y personalizar el color, la escala, la rotación y la sombra del texto.

## Entidad del jugador
Renderiza un modelo de jugador en el menú.

*   **Casos de uso:**
    *   Mostrar el personaje del jugador actual en el menú principal.
    *   Crear una pantalla de selección de equipo o vista previa de clase.
    *   Una sección de "perfil" que muestre la skin y el nombre del jugador.
*   **Características clave:**
    *   **Apariencia dinámica:** Puede configurarse para copiar automáticamente la skin, capa y nombre del jugador actual. Para más información, consulta la guía de [Cabezas de jugador](https://docs.fancymenu.net/en/player-heads).
    *   **Poses personalizadas:** Ofrece control detallado sobre la rotación de la cabeza, el cuerpo, los brazos y las piernas. La cabeza y el cuerpo también pueden configurarse para seguir el cursor del mouse.
    *   **Atributos:** Puede configurarse como bebé, agachado o con modelo delgado.

## Navegador
Un elemento que renderiza una página web en vivo dentro del juego.

¡Este elemento requiere que el mod **MCEF (Minecraft Chromium Embedded Framework)** esté instalado y funcionando!

Puedes descargar MCEF desde las páginas oficiales del proyecto en [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) y [Modrinth](https://modrinth.com/mod/mcef).

Para versiones más nuevas de Minecraft (1.21.5+), los proyectos oficiales de MCEF no proporcionan compilaciones, pero existe un fork con compilaciones para las versiones más recientes de Minecraft, que puedes encontrar [aquí](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) y [aquí](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Este fork es mantenido por Keksuccino para publicar compilaciones para las versiones más recientes de Minecraft lo más rápido posible.

*   **Casos de uso:**
    *   Mostrar el Dynmap en vivo de un servidor.
    *   Incrustar un reproductor de video de YouTube.
    *   Mostrar una wiki o página de documentación directamente dentro del juego.
*   **Características clave:**
    *   **Interactividad:** Puede hacerse totalmente interactivo, permitiendo que los usuarios hagan clic en enlaces, se desplacen y escriban.
    *   **Control de medios:** Ofrece opciones para silenciar contenido multimedia, repetir videos y ocultar los controles de video en la página cargada.

### Cargar archivos HTML locales
¡El elemento Navegador te permite cargar documentos HTML locales en `/config/fancymenu/assets/`! Esto significa que puedes mostrar contenido local renderizado por el navegador para changelogs elegantes y más.

Para cargar un archivo HTML local, comienza tu URL con `file:///`, seguido de la ruta CORTA del archivo, por ejemplo `/config/fancymenu/assets/cool_changelog.html`, lo que se vería así: `file:///config/fancymenu/assets/cool_changelog.html`.

En **Linux** necesitas proporcionar la ruta absoluta del archivo, pero como codificar una ruta absoluta directamente rompería el diseño, necesitas permitir que un marcador de posición convierta dinámicamente la ruta corta en una absoluta: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Es SUMAMENTE IMPORTANTE que en Linux la ruta corta comience con `/`, como en el ejemplo anterior. Si no, no funcionará.

## Animador de elementos
Una herramienta poderosa para crear animaciones complejas basadas en fotogramas clave. Puede animar la posición, el tamaño y el punto de anclaje de uno o varios otros elementos.

*   **Casos de uso:**
    *   Crear una animación de introducción sofisticada donde los elementos del menú se deslicen o aparezcan con desvanecimiento.
    *   Hacer que elementos decorativos palpiten, roten o se muevan siguiendo una trayectoria.
    *   Animar una notificación para que aparezca y luego desaparezca.
*   **Características clave:**
    *   **Editor de fotogramas clave:** Un editor dedicado para agregar, editar y secuenciar fotogramas clave en una línea de tiempo.
    *   **Multiobjetivo:** Un solo Animador puede controlar varios elementos "objetivo" al mismo tiempo.
    *   **Control:** Las animaciones pueden configurarse para repetirse. También puedes elegir animar solo la posición o el tamaño.
    *   **Desplazamientos de tiempo:** Los elementos objetivo pueden usar desplazamientos de tiempo de inicio individuales o aleatorios.
    *   **[Aprende más sobre el Animador de elementos.](https://docs.fancymenu.net/en/element-animator)**

## Ticker
Un elemento invisible que ejecuta una lista de acciones a un intervalo regular (cada "tick").

> Para automatización de fondo nueva en FancyMenu 3.9.0+, considera usar [Programadores](https://docs.fancymenu.net/en/schedulers). Los programadores son globales, más fáciles de organizar y pueden seguir ejecutándose de forma independiente de una pantalla específica.
{.is-info}

*   **Casos de uso:**
    *   Verificar periódicamente el estado en línea de un servidor y actualizar un elemento de texto.
    *   Crear un temporizador de cuenta regresiva que actualice una etiqueta de texto.
    *   Ejecutar un script repetidamente para crear comportamientos personalizados.
*   **Características clave:**
    *   **Control de tiempo:** Puedes establecer el retraso entre ticks en milisegundos.
    *   **Modos de tick:** Puede configurarse para ejecutarse continuamente, solo una vez por sesión de juego o una vez cada vez que se cargue el menú.
    *   **Asíncrono:** Puede ejecutar sus [acciones](https://docs.fancymenu.net/en/action-scripts) en un hilo separado para evitar afectar el rendimiento del juego, aunque algunas acciones no pueden ejecutarse de esta manera.

## Audio
Un elemento invisible que reproduce archivos de audio. Puede administrar una lista de reproducción de pistas y ofrece varios controles de reproducción.

*   **Casos de uso:**
    *   Agregar música de fondo personalizada a un menú.
    *   Crear un reproductor de música con botones para controlar la reproducción (siguiente/anterior pista, volumen).
    *   Reproducir paisajes sonoros ambientales.
*   **Características clave:**
    *   **Lista de reproducción:** Puede administrar varias pistas de audio.
    *   **Modos de reproducción:** Puede reproducir las pistas en orden o mezclarlas aleatoriamente (con soporte para ponderación de pistas para hacer que algunas aparezcan con más frecuencia que otras).
    *   **Control:** Compatible con repetición, ajuste de volumen y asignación a un canal de sonido específico (por ejemplo, Master, Music). Para más información, consulta la página [Música de fondo del menú](https://docs.fancymenu.net/en/background-music).

## Controlador de música
Un elemento invisible usado para controlar la reproducción de la música predeterminada de Minecraft dentro de un menú específico.

*   **Casos de uso:**
    *   Desactivar la música predeterminada del menú en una pantalla donde quieras reproducir tu propia música personalizada mediante un elemento **Audio**.
    *   Hacer que la música del mundo no siga sonando cuando se abre un menú dentro del juego.
*   **Características clave:**
    *   Interruptores separados para controlar "Música del menú" y "Música del mundo" de Vanilla.

## Barra de progreso
Una barra personalizable que representa visualmente un valor numérico.

*   **Casos de uso:**
    *   Una barra de carga que siga el progreso de carga del mundo usando `{"placeholder":"world_load_progress"}`.
    *   Barras visuales de salud, hambre o experiencia para un HUD dentro del juego.
    *   Un indicador de volumen controlado por un elemento **Control deslizante**.
*   **Características clave:**
    *   **Valor dinámico:** El valor de progreso (0-100 o 0.0-1.0) se establece mediante un campo de texto que admite [marcadores de posición](https://docs.fancymenu.net/en/placeholders).
    *   **Apariencia:** La dirección de la barra (arriba, abajo, izquierda, derecha), los colores, las texturas y el nine-slicing para las texturas de barra/fondo son totalmente personalizables.
    *   **Animación:** Incluye una animación suave de llenado para que los cambios de progreso se vean menos bruscos.

## Arrastrador
Un elemento invisible sobre el que el usuario puede hacer clic y arrastrar para moverlo. Otros elementos pueden anclarse a él para crear widgets móviles.

*   **Casos de uso:**
    *   Crear un reloj o panel de información arrastrable.
    *   Permitir que los usuarios personalicen la posición de los elementos de la interfaz según sus preferencias.
*   **Características clave:**
    *   **Posición persistente:** El desplazamiento arrastrado se guarda, así que el elemento se queda donde el usuario lo dejó, incluso después de reiniciar el juego.
    *   **Punto de anclaje:** Actúa como un ancla móvil para otros elementos, lo cual es una parte clave de [Posicionar elementos](https://docs.fancymenu.net/en/positioning-elements).

## Cursor
Un elemento invisible que reemplaza el cursor del sistema predeterminado con una imagen personalizada cuando un diseño está activo.

*   **Casos de uso:**
    *   Crear una interfaz totalmente temática que combine con la estética de tu modpack.
*   **Características clave:**
    *   **Textura personalizada:** Usa cualquier imagen para tu cursor.
    *   **Hotspot:** Puedes definir el píxel exacto de la imagen que funciona como el "punto de clic". Consulta la guía de [Cursor personalizado](https://docs.fancymenu.net/en/custom-cursor) para más información.
