---
title: Elementos
description: Todo lo que necesitas saber sobre los tipos de elementos de FancyMenu.
---
# Elementos

Los elementos son los componentes básicos de tus diseños personalizados en FancyMenu. Puedes agregarlos a cualquier diseño para mostrar información, añadir interactividad o crear efectos visuales sorprendentes.

# Agregar elementos a un diseño

Puedes agregar un elemento nuevo a tu diseño desde el **Editor de diseños**.

1.  Haz **clic derecho** en el fondo del editor para abrir el menú contextual.
2.  Coloca el cursor sobre **Elemento nuevo**.
3.  Aparecerá una lista con todos los tipos de elementos disponibles. Haz clic en el que quieras agregar.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Una vez agregado un elemento, puedes moverlo, cambiar su tamaño y personalizarlo al hacer **clic derecho** sobre él para abrir su menú contextual específico. Para obtener más información sobre cómo organizar los elementos, consulta [Posicionar elementos](./positioning-elements) e [Identificadores de elementos](./element-identifiers).

# Elementos en detalle

En esta sección se enumeran los elementos integrados de FancyMenu. Usa [Capas y grupos](./layers-and-groups) para organizar su orden de renderizado.

## Botón
Un botón en el que se puede hacer clic y que puede realizar una amplia variedad de acciones. Es uno de los elementos más potentes y versátiles para crear menús interactivos.

*   **Casos de uso:**
    *   Crear un botón de "Unirse a Discord" o "Visitar sitio web".
    *   Agregar un botón de unión rápida para un servidor específico.
    *   Crear una navegación personalizada entre distintos menús.
    *   Crear botones que activen o desactiven otros diseños.
*   **Características principales:**
    *   **Acciones:** Puede ejecutar una secuencia de [acciones](./action-scripts), como abrir una URL, unirse a un servidor, enviar un comando de chat, imitar la función de otro botón o controlar variables.
    *   **Apariencia personalizada:** Texturas totalmente personalizables para los estados normal, al pasar el cursor e inactivo. Admite fondos transparentes, escalado de nueve segmentos, colores de etiqueta personalizados, colores de etiqueta al pasar el cursor, escala de etiqueta, opciones para activar o desactivar la sombra de la etiqueta y texturas de iconos de botón.
    *   **Sonidos:** Sonidos personalizados al hacer clic, al pasar el cursor y al retirar el cursor.
    *   **Modo de plantilla:** Puede aplicar su apariencia y propiedades a otros botones vanilla o de mods en el menú. Consulta [Plantillas de botones y controles deslizantes](./button-slider-templates).
    *   **Clics automatizados en widgets vanilla o de mods:** Los widgets vanilla y de mods existentes tienen una propiedad de **Clics automatizados** que puede invocar su comportamiento de clic original una cantidad determinada de veces cuando se carga la pantalla. Consulta [Elementos vanilla](./vanilla-elements#automated-clicks) para obtener más información.

## Control deslizante
Un control deslizante que los usuarios pueden arrastrar para seleccionar un valor de una lista o un rango. Puede ejecutar acciones cada vez que cambia su valor.

*   **Casos de uso:**
    *   Crear un control de volumen personalizado.
    *   Un control deslizante para cambiar entre distintos temas o imágenes de fondo (mediante el tipo "Lista").
    *   Ajustar una opción específica de Minecraft, como el brillo o la distancia de renderizado.
*   **Características principales:**
    *   **Tipos:** Puede ser una `Lista de valores` (por ejemplo, "Fácil", "Normal", "Difícil"), un `Rango de enteros` (por ejemplo, 1-100) o un `Rango decimal` (por ejemplo, 0.0-1.0).
    *   **Acciones dinámicas:** Ejecuta acciones cuando cambia su valor. El valor actual se puede usar con [Variables](./variables).
    *   **Personalización:** La etiqueta del control deslizante puede mostrar dinámicamente su valor actual. Las texturas del control y del fondo son totalmente personalizables, incluidos los fondos transparentes, las opciones de color y escala de la etiqueta, las opciones para activar o desactivar la sombra del texto y los sonidos personalizados al hacer clic o retirar el cursor.

## Casilla
Una casilla estándar que se puede activar o desactivar. Puede ejecutar acciones cuando cambia de estado.

*   **Casos de uso:**
    *   Una casilla de "Acepto las reglas".
    *   Una opción para activar o desactivar una función específica en tu menú personalizado.
    *   Activar o desactivar un diseño o una variable.
*   **Características principales:**
    *   **Acciones al cambiar de estado:** Ejecuta [scripts de acciones](./action-scripts) cuando cambia de estado. El estado actual (`true` o `false`) está disponible para sus acciones.
    *   **Modo de variable:** Se puede vincular directamente a una variable de FancyMenu, de modo que el estado de la casilla se lea de esa variable y se escriba en ella.
    *   **Estado persistente:** Cuando el modo de variable está desactivado, la casilla guarda automáticamente su estado mediante el identificador del elemento y lo restaura después de reiniciar el juego. Estos estados se guardan en `<game-directory>/checkbox_states.json`. En el modo de variable, la variable de FancyMenu vinculada es la fuente del estado de la casilla.
    *   **Apariencia personalizada:** Admite texturas personalizadas para el fondo (en los estados normal, al pasar el cursor e inactivo) y para la marca de verificación.

## Campo de entrada de texto
Un campo donde los usuarios pueden escribir texto. Su contenido se puede vincular a una variable de FancyMenu, lo que permite capturar y usar la entrada del usuario.

*   **Casos de uso:**
    *   Un campo de entrada de "IP del servidor" que funcione con un botón de "Unirse al servidor".
    *   Un campo para introducir el nombre de un jugador y mostrar una vista previa de una skin personalizada.
    *   Crear una interfaz básica similar a un inicio de sesión.
*   **Características principales:**
    *   **Vinculación de variables:** Guarda el texto introducido en una [variable](./variables) especificada.
    *   **Validación de entrada:** Se puede configurar para aceptar únicamente tipos de caracteres específicos, como números, URL o texto simple.
    *   **Longitud máxima:** Puedes establecer un límite máximo de caracteres para la entrada.
    *   **Apariencia y sonidos:** Admite color de fondo personalizado, colores y redondeado del borde, color del texto, texto de sugerencia/placeholder, color de la sugerencia, sonidos al pasar y retirar el cursor y sonidos al hacer clic.

## Información emergente
Un cuadro de texto que puede aparecer en una posición fija o seguir el cursor del mouse. Su visibilidad normalmente se controla mediante [Requisitos de carga](./conditions).

*   **Casos de uso:**
    *   Mostrar información detallada cuando el usuario pasa el cursor sobre un botón o una imagen.
    *   Crear sugerencias de ayuda contextuales que aparezcan bajo ciertas condiciones.
    *   Mostrar información dinámica (como el estado del servidor) junto al cursor.
*   **Características principales:**
    *   **Seguimiento del mouse:** Se puede configurar para seguir el puntero del mouse.
    *   **Compatibilidad con Markdown:** El contenido admite todo el formato de Markdown.
    *   **Fondo personalizado:** El fondo puede ser de un color sólido o una textura personalizada con escalado de nueve segmentos para lograr una apariencia totalmente temática.

## Objeto
Muestra un solo objeto de Minecraft, ya sea vanilla o de un mod.

*   **Casos de uso:**
    *   Usar objetos como iconos para botones o selecciones de menú.
    *   Crear una interfaz gráfica de tienda o de selección de kits.
    *   Mostrar el objeto que sostiene un jugador o su armadura.
*   **Características principales:**
    *   **Datos personalizados:** Admite nombre personalizado, descripción, cantidad, brillo de encantamiento y datos NBT. Consulta el [Placeholder de datos NBT](./nbt-data-placeholder).
    *   **Mostrar información emergente:** Se puede configurar para mostrar la información emergente estándar del objeto al pasar el cursor sobre él.

## Modelo JSON de bloque/objeto
Renderiza un modelo JSON de bloque u objeto a partir de los recursos de Minecraft o de fuentes externas.

*   **Casos de uso:**
    *   Mostrar un modelo 3D de un paquete de recursos en un menú.
    *   Mostrar vistas previas de objetos o bloques con texturas personalizadas.
    *   Crear elementos decorativos de interfaz basados en modelos.
*   **Características principales:**
    *   **Origen del modelo:** Puede cargar JSON de modelos desde los recursos de Minecraft o desde fuentes externas.
    *   **Sobrescrituras de textura:** Admite la configuración de una textura personalizada.
    *   **Controles de renderizado:** Desplazamiento, escala y rotación del modelo en tres ejes, renderizado translúcido y transformación del modelo para la interfaz gráfica.
    *   **Iluminación:** Dos luces configurables con controles independientes de tono y rotación.

## Imagen
Muestra una imagen estática desde un archivo local, una URL web o una ubicación de recursos de Minecraft.

*   **Casos de uso:**
    *   Agregar el logotipo de un servidor o la marca de un modpack.
    *   Crear bordes decorativos o marcos de interfaz.
    *   Usar imágenes como parte de un diseño de interfaz más complejo.
*   **Características principales:**
    *   **Escalado de nueve segmentos:** Escala bordes o paneles sin distorsionar sus esquinas. Consulta [Escalado de nueve segmentos y mosaicos](./nine-slicing-and-tiling).
    *   **Repetición de textura:** La imagen se puede repetir en mosaico para llenar el área del elemento.
    *   **Tintado:** Puedes aplicar un tinte de color a la imagen.
    *   **Esquinas redondeadas:** Las imágenes sin escalado de nueve segmentos y sin repetición pueden tener esquinas redondeadas.
    *   **Efecto de paralaje:** Se mueve con el mouse para crear profundidad visual. Consulta [Efecto de paralaje](./parallax).

## Texto
Un elemento muy versátil para mostrar texto. Se puede usar desde etiquetas de una sola línea hasta documentos de varias páginas con desplazamiento.

*   **Casos de uso:**
    *   Mostrar reglas del servidor, notas de actualización o mensajes de bienvenida.
    *   Crear paneles de información dinámica mediante [placeholders](./placeholders), por ejemplo `¡Bienvenido, {"placeholder":"playername"}!`.
    *   Agregar etiquetas y descripciones a tu interfaz.
*   **Características principales:**
    *   **Fuentes del contenido:** El texto se puede introducir directamente, cargar desde un archivo local u obtener desde una URL web.
    *   **Compatibilidad con Markdown:** Admite encabezados, listas, bloques de código, tablas y otros formatos de Markdown. Consulta [Formato de texto](./text-formatting).
    *   **Desplazamiento:** Se vuelve desplazable automáticamente si el contenido es más grande que el área del elemento. Las barras de desplazamiento se pueden personalizar o desactivar.
    *   **Estilo:** Control total sobre el color, la escala, la alineación y la sombra del texto, así como el espaciado entre líneas.

## Video
Reproduce un archivo de video. Es perfecto para introducciones cinematográficas o fondos decorativos en bucle.

> [!WARNING]
> El elemento Video nativo requiere **Watermedia V3** y **Watermedia Binaries V3**. El elemento antiguo **Video [Rinku]** está obsoleto.

*   **Casos de uso:**
    *   Un tráiler animado de un modpack o servidor.
    *   Un video ambiental en bucle para darle vida a tu menú.
    *   Un video tutorial dentro del juego.
*   **Características principales:**
    *   **Fuentes:** Admite archivos de video locales y URL web. Consulta [Videos](./video).
    *   **Control de reproducción:** Se puede configurar para repetirse automáticamente. Su volumen, canal de sonido y comportamiento para conservar la relación de aspecto son ajustables.
    *   **Control interactivo:** La reproducción, el tiempo de búsqueda y el volumen del video se pueden controlar mediante acciones de botones.

## Shader GLSL
Renderiza un shader GLSL personalizado dentro de un elemento.

*   **Casos de uso:**
    *   Paneles con shaders animados.
    *   Efectos visuales procedurales.
    *   Efectos de menú al estilo Shadertoy recortados al rectángulo de un elemento.
*   **Características principales:**
    *   **Ejecución del shader:** Admite shaders de una sola pasada y multipasada.
    *   **Compatibilidad con Shadertoy:** Puede usar shaders estilo Shadertoy con `mainImage`.
    *   **Uniformes:** Expone uniformes de FancyMenu y de entrada. Consulta la [API de shaders GLSL](./glsl-shader-api).

## Presentación de diapositivas
Muestra una secuencia de imágenes. Sus imágenes y el archivo de configuración `properties.txt` se encuentran en el subdirectorio propio de la presentación, dentro de `<game-directory>/config/fancymenu/slideshows/`.

*   **Casos de uso:**
    *   Una galería rotativa de capturas de pantalla del juego.
    *   Mostrar las características principales de un modpack.
    *   Un fondo dinámico que cambie entre distintas escenas.
*   **Características principales:**
    *   Carga [presentaciones de diapositivas](./slideshows) preconfiguradas.
    *   Se puede configurar para mantener la relación de aspecto de las imágenes.

## Forma rectangular
Un rectángulo sencillo de color sólido.

*   **Casos de uso:**
    *   Crear un fondo semitransparente detrás del texto para mejorar la legibilidad.
    *   Diseñar paneles y separadores de interfaz sencillos.
    *   Usarlo como marcador de posición de color durante el diseño del diseño.
*   **Características principales:**
    *   Admite colores HEX RGBA, esquinas redondeadas y desenfoque opcional, lo que permite usar la forma como un panel sencillo, un tinte o un fondo desenfocado.

## Forma circular
Una forma sencilla de círculo/elipse de color sólido.

*   **Casos de uso:**
    *   Crear acentos circulares, indicadores o áreas suaves de interfaz.
    *   Crear decoraciones temáticas para la interfaz sin usar un archivo de textura.
*   **Características principales:**
    *   Admite color, desenfoque y un valor configurable de redondez/exponente.

## Texto de inicio
Una recreación del icónico texto amarillo y rebotante de Minecraft que aparece en la pantalla de título.

*   **Casos de uso:**
    *   Reemplazar el texto de inicio vanilla con tus propios mensajes personalizados.
    *   Agregar un mensaje animado y llamativo a cualquier menú.
*   **Características principales:**
    *   **Fuentes del contenido:** Puede usar los textos de inicio vanilla predeterminados, una lista de textos personalizados introducidos directamente o texto de un archivo local.
    *   **Personalización:** Puedes activar o desactivar el efecto de rebote y personalizar el color, la escala, la rotación y la sombra del texto.

## Entidad del jugador
Renderiza el modelo de un jugador en el menú.

*   **Casos de uso:**
    *   Mostrar el personaje del jugador actual en el menú principal.
    *   Crear una pantalla de selección de equipo o de vista previa de clase.
    *   Una sección de "perfil" que muestre la skin y el nombre del jugador.
*   **Características principales:**
    *   **Apariencia dinámica:** Puede copiar la skin, la capa y el nombre del jugador actual. Consulta [Cabezas de jugador](./player-heads).
    *   **Poses personalizadas:** Ofrece un control detallado sobre la rotación de la cabeza, el cuerpo, los brazos y las piernas. La cabeza y el cuerpo también se pueden configurar para seguir el cursor del mouse.
    *   **Atributos:** Se puede configurar como bebé, agachado o con un modelo delgado.

## Navegador
Un elemento que renderiza una página web en vivo dentro del juego.

Este elemento requiere que el mod **[Rinku](https://modrinth.com/mod/rinku)** esté instalado y funcionando.

Puedes descargar Rinku desde las páginas oficiales del proyecto en [CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku) y [Modrinth](https://modrinth.com/mod/rinku).

*   **Casos de uso:**
    *   Mostrar el Dynmap en vivo de un servidor.
    *   Insertar un reproductor de videos de YouTube.
    *   Mostrar una wiki o página de documentación directamente dentro del juego.
*   **Características principales:**
    *   **Interactividad:** Se puede hacer totalmente interactivo, lo que permite a los usuarios hacer clic en enlaces, desplazarse y escribir.
    *   **Control multimedia:** Ofrece opciones para silenciar contenido multimedia, repetir videos y ocultar los controles de video de la página cargada.

### Cargar archivos HTML locales
El elemento Navegador puede cargar documentos HTML locales desde `<game-directory>/config/fancymenu/assets/`.

Para cargar un archivo HTML local, comienza tu URL con `file:///`, seguido de la RUTA CORTA del archivo; por ejemplo, `/config/fancymenu/assets/cool_changelog.html`, de modo que quede así: `file:///config/fancymenu/assets/cool_changelog.html`.

En **Linux**, usa el [placeholder de **Ruta absoluta de archivo/carpeta**](./placeholders#absolute-filefolder-path-absolute_path) en lugar de escribir directamente una ruta absoluta específica de la instancia: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

La ruta corta de Linux debe comenzar con `/`, como se muestra en el ejemplo.

## Animador de elementos
Una herramienta potente para crear animaciones complejas basadas en fotogramas clave. Puede animar la posición, el tamaño y el punto de anclaje de uno o varios elementos.

*   **Casos de uso:**
    *   Hacer que los elementos entren o salgan de la pantalla deslizándose.
    *   Cambiar el tamaño de paneles o notificaciones.
    *   Animar desplazamientos de posición y transiciones de anclaje.
*   **Características principales:**
    *   **Editor de fotogramas clave:** Un editor específico para agregar, editar y ordenar fotogramas clave en una línea de tiempo.
    *   **Varios objetivos:** Un solo animador puede controlar varios elementos "objetivo" al mismo tiempo.
    *   **Control:** Las animaciones se pueden configurar para repetirse. También puedes elegir animar únicamente la posición o el tamaño.
    *   **Desplazamientos de tiempo:** Los elementos objetivo pueden usar desplazamientos de tiempo de inicio individuales o aleatorios.
    *   Consulta [Animador de elementos](./element-animator) para obtener información sobre la configuración y la edición de fotogramas clave.

## Temporizador
Un elemento invisible que ejecuta una lista de acciones a intervalos regulares (en cada "tick").

> [!NOTE]
> Para automatizaciones en segundo plano, considera usar [Programadores](./schedulers). Los programadores son globales y pueden ejecutarse independientemente de una pantalla específica.

*   **Casos de uso:**
    *   Comprobar periódicamente si un servidor está en línea y actualizar un elemento de texto.
    *   Crear un temporizador de cuenta regresiva que actualice una etiqueta de texto.
    *   Ejecutar repetidamente un script para crear comportamientos personalizados.
*   **Características principales:**
    *   **Control del tiempo:** Puedes establecer el retraso entre ticks en milisegundos.
    *   **Modos de tick:** Se puede configurar para ejecutarse continuamente, solo una vez por sesión de juego o una vez cada vez que se carga el menú.
    *   **Asíncrono:** Puede ejecutar sus [acciones](./action-scripts) por separado, aunque algunas acciones no pueden ejecutarse mientras esta opción está activada.

## Audio
Un elemento invisible que reproduce archivos de audio. Puede administrar una lista de reproducción y ofrece varios controles de reproducción.

*   **Casos de uso:**
    *   Agregar música de fondo personalizada a un menú.
    *   Crear un reproductor de música con botones para controlar la reproducción (pista siguiente/anterior, volumen).
    *   Reproducir paisajes sonoros ambientales.
*   **Características principales:**
    *   **Lista de reproducción:** Puede administrar varias pistas de audio.
    *   **Modos de reproducción:** Puede reproducir las pistas en orden o de forma aleatoria (con compatibilidad para ponderar las pistas y hacer que algunas aparezcan con más frecuencia que otras).
    *   **Control:** Admite repetición, ajuste de volumen y selección del canal de sonido. Consulta [Música de fondo del menú](./background-music).

## Controlador de música
Un elemento invisible que se usa para controlar la reproducción de música predeterminada de Minecraft dentro de un menú específico.

*   **Casos de uso:**
    *   Desactivar la música predeterminada del menú en una pantalla donde quieras reproducir tu propia música personalizada mediante un elemento [**Audio**](#audio).
    *   Evitar que la música del mundo siga reproduciéndose cuando se abre un menú dentro del juego.
*   **Características principales:**
    *   Interruptores independientes para controlar la "Música del menú" y la "Música del mundo" vanilla.

## Barra de progreso
Una barra personalizable que representa visualmente un valor numérico.

*   **Casos de uso:**
    *   Una barra de carga que siga el progreso de carga del mundo mediante `{"placeholder":"world_load_progress"}`.
    *   Barras visuales de salud, hambre o experiencia para una interfaz dentro del juego.
    *   Un indicador de volumen controlado por un elemento [**Control deslizante**](#slider).
*   **Características principales:**
    *   **Valor dinámico:** El valor de progreso (0-100 o 0.0-1.0) se establece mediante un campo de texto compatible con [placeholders](./placeholders).
    *   **Apariencia:** La dirección de la barra (arriba, abajo, izquierda, derecha), los colores, las texturas y el escalado de nueve segmentos para las texturas de la barra y del fondo son totalmente personalizables.
    *   **Animación:** Incluye una animación de llenado suave para que los cambios de progreso se vean menos bruscos.
    *   **Anclaje de elementos basado en el progreso:** Cuando otro elemento usa la barra de progreso como su anclaje de **Elemento**, activa **Usar el progreso para el anclaje del elemento** para mover ese anclaje al borde actual del área rellenada. De esta forma, los elementos anclados se desplazan con el progreso de la barra en lugar de permanecer unidos a sus límites estáticos.

## Arrastrador
Un elemento invisible que el usuario puede seleccionar y arrastrar para moverlo. Se pueden anclar otros elementos a él para crear widgets móviles.

*   **Casos de uso:**
    *   Crear un reloj o panel de información arrastrable.
    *   Permitir que los usuarios personalicen la posición de los elementos de la interfaz según sus preferencias.
*   **Características principales:**
    *   **Persistencia opcional:** Activa **Guardar desplazamiento al arrastrar** para conservar la posición que el usuario establezca al arrastrar entre aperturas de pantalla y reinicios del juego. Desactívala para restablecer el desplazamiento.
    *   **Punto de anclaje:** Funciona como un anclaje móvil para otros elementos, una parte clave de [Posicionar elementos](./positioning-elements).

## Cursor
Un elemento invisible que reemplaza el cursor predeterminado del sistema por una imagen personalizada cuando hay un diseño activo.

*   **Casos de uso:**
    *   Crear una interfaz totalmente temática que coincida con la estética de tu modpack.
*   **Características principales:**
    *   **Textura personalizada:** Usa cualquier imagen para tu cursor.
    *   **Punto activo:** Establece el píxel exacto de la imagen que se usará como punto de clic. Consulta [Cursor personalizado](./custom-cursor).
