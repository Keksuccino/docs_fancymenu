---
title: Elementos
description: >-
  Todos los tipos de elementos de FancyMenu, para qué sirven y cómo añadirlos a
  un diseño.
sourceBlobSha: 0e457baa99cbf7103634385145b27f07c22e6e51
---

# Elementos

Los elementos son las partes de un diseño: botones, textos, imágenes, controles deslizantes, música y mucho más. En esta página se enumeran todos los tipos de elementos y sus ajustes más importantes.

> [!TIP]
> Los botones y otros elementos que una pantalla incluye de forma predeterminada son [Elementos vanilla](/vanilla-elements). También puedes moverlos, modificarlos y ocultarlos.

# Añadir elementos

1. En el editor de diseños, haz clic con el botón derecho en un espacio libre y selecciona **Nuevo elemento**. La barra de menús ofrece la misma lista en **Elemento -> Nuevo**.
2. Haz clic en un tipo de elemento. Pasa el cursor sobre un tipo para ver para qué sirve.

El elemento aparecerá donde hayas hecho clic con el botón derecho. Arrástralo para moverlo, arrastra sus bordes para cambiar su tamaño y haz clic derecho sobre él para abrir sus ajustes.

<img width="800" alt="Haz clic con el botón derecho en el editor de diseños, añade un botón mediante Nuevo elemento, muévelo y ensánchalo, y ponle la etiqueta Unirse al servidor" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_add_element.gif?raw=true">

Consulta [Editor de diseños](/layout-editor) para aprender a seleccionar, mover, copiar y eliminar elementos, y ver todos los atajos del editor. Para mantener los elementos en su sitio en ventanas de cualquier tamaño, lee [Posicionar elementos](/positioning-elements). Para colocar elementos delante o detrás de otros, consulta [Capas y grupos](/layout-editor#layers-and-groups).

# Ajustes comunes a todos los elementos

Todos los elementos tienen estos ajustes en su menú contextual, además de los ajustes específicos de su tipo:

| Ajuste | Para qué sirve |
|---|---|
| **Punto de anclaje** | A qué está unido el elemento, como una esquina de la pantalla u otro elemento. Consulta [Posicionar elementos](/positioning-elements). |
| **Posicionamiento avanzado** y **Tamaño avanzado** | Calculan la posición y el tamaño, por ejemplo mediante [marcadores de posición](/placeholders). Consulta [Posicionamiento y tamaño avanzados](/advanced-positioning-sizing). |
| **Requisitos de carga** y **Cargar una vez por sesión** | Muestran el elemento solo cuando se cumplen los [requisitos](/conditions), o una sola vez por inicio del juego. Consulta [Visibilidad de los elementos](/element-visibility). |
| **Retrasar aparición** y **Retrasar desaparición** | Esperan unos segundos antes de mostrar o quitar el elemento. Consulta [Visibilidad de los elementos](/element-visibility#delaying-elements). |
| **Aparición/desaparición gradual** y **Opacidad** | Hacen que el elemento aparezca o desaparezca gradualmente, o permiten volverlo transparente. Consulta [Visibilidad de los elementos](/element-visibility#fading-in-and-out). |
| **Rotación**, **Inclinación vertical** e **Inclinación horizontal** | Giran e inclinan el elemento. Consulta [Girar e inclinar elementos](/rotating-elements). |
| **Efecto parallax** | Mueve ligeramente el elemento con el ratón. Consulta [Efecto parallax](/parallax). |
| **Copiar ID del elemento** | Copia el identificador que utilizan las acciones, los marcadores de posición y otros elementos para encontrarlo. Consulta [Identificadores de elementos](/element-identifiers). |
| **Nombre para mostrar en el editor** | El nombre del elemento en la lista de capas. |
| **Exportar para IA** | Convierte el elemento en texto para [asistentes de IA](/export-for-ai). |

# Todos los elementos

Aquí se muestran todos los elementos de FancyMenu, clasificados según su función.

## Botones y entradas

### Botón

Un botón que ejecuta un [script de acciones](/action-scripts) al hacer clic, por ejemplo, para unirse a un servidor, abrir una página web u otro menú.

<img width="396" alt="Dos botones con las etiquetas Unirse al servidor y Abrir la wiki" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_button.png?raw=true">

- **Editar script de acciones**: lo que hace el botón al hacer clic.
- **Etiqueta** y **Etiqueta al pasar el cursor**: el texto del botón y el que aparece mientras el cursor está encima. Ambos admiten [marcadores de posición](/placeholders) y [formato de texto](/text-formatting).
- **Alineación de la etiqueta**: coloca la etiqueta a la **izquierda**, **centrada** o a la **derecha** del botón. Las etiquetas demasiado anchas para el botón se desplazan de un lado a otro, independientemente de su alineación.
- **Escala de la etiqueta**, **Color base de la etiqueta**, **Color de la etiqueta al pasar el cursor**, **Sombra de la etiqueta** y **Subrayar etiqueta al pasar el cursor**: ajustan el tamaño, los colores y la sombra de la etiqueta.
- **Texturas del botón** y **Texturas del icono del botón**: imágenes propias para el botón y para un icono sobre él, en los estados normal, al pasar el cursor e inactivo. Consulta [División en nueve partes y mosaico](/nine-slicing-and-tiling) para aprender a crear texturas que se escalen correctamente.
- **Sonido al pasar el cursor**, **Sonido al retirar el cursor** y **Sonido al hacer clic**: los sonidos que reproduce el botón.
- **Información emergente**: texto que aparece mientras el cursor está sobre el botón.
- **Controlar estado activo**: [requisitos](/conditions) para que se pueda hacer clic en el botón. Si no se cumplen, el botón aparece atenuado.
- **Modo de plantilla**: aplica el aspecto de este botón a otros botones y controles deslizantes de la pantalla. Consulta [Plantillas de botones y controles deslizantes](/button-slider-templates).

### Control deslizante

Un control que los jugadores arrastran para elegir un valor. Ejecuta su script de acciones cada vez que cambia el valor.

<img width="436" alt="Un control deslizante de volumen de música al 70 % y otro de dificultad ajustado en Normal" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_slider.png?raw=true">

- **Tipo de control deslizante**:
  - **Lista de valores**: recorre los textos de **Valores de la lista**, uno por línea. **Valores de una variable de lista** los obtiene de una [variable de lista](/variables#text-and-list-variables).
  - **Rango de enteros**: números enteros desde **Valor mínimo del rango** hasta **Valor máximo del rango**.
  - **Rango de decimales**: lo mismo, pero con decimales. **Posición decimal de redondeo** establece cuántas cifras van después de la coma; `-1` no redondea.
- **Etiqueta del control deslizante**: su texto. `$$value` muestra el valor actual.
- **Editar script de acciones**: se ejecuta cuando cambia el valor. `$$value` es el nuevo valor.
- **Valor preseleccionado**: el valor inicial del control deslizante. Indica el valor que modifica el control para que muestre el valor correcto al abrir la pantalla.

Por ejemplo, un control deslizante de volumen del tipo **Rango de enteros**, de `0` a `100`, puede tener la etiqueta `Volumen de música: $$value%` y una acción [**Establecer valor de variable (variable de FM)**](/action-scripts#set-variable-value-fm-variable) con este valor:

```
music_volume:$$value
```

Su **Valor preseleccionado** es `$$music_volume`, así que empieza con el último valor que haya elegido el jugador.

Los controles deslizantes tienen los mismos ajustes de etiqueta, textura, sonido, información emergente y **Controlar estado activo** que los botones. Por tanto, también puedes situar su etiqueta a la izquierda o a la derecha con **Alineación de la etiqueta**.

### Casilla

Una casilla que los jugadores pueden marcar y desmarcar. Ejecuta su script de acciones cada vez que cambia.

<img width="588" alt="Una casilla marcada junto al texto Mostrar consejos en la pantalla del título" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_checkbox.png?raw=true">

- En el script de acciones y en los requisitos de **Controlar estado activo**, `$$value` es `true` o `false`.
- **Modo de variable** y **Vincular a variable**: la casilla muestra el valor de una [variable](/variables) y escribe `true` o `false` en ella. Si se vincula a una variable de lista, `true` o `false` se convierte en su único elemento.
- Sin el modo de variable, la casilla recuerda su estado por sí sola, por separado para cada [perfil](/profiles).
- **Texturas**: imágenes propias para la casilla y la marca.

Las casillas tienen los mismos ajustes de información emergente, sonido y **Navegable** que los botones.

### Campo de texto

Un campo en el que los jugadores pueden escribir, como una dirección de servidor o un nombre.

<img width="456" alt="Un campo de texto con play.example.net y otro vacío con el texto de ayuda gris Tu nombre de jugador" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_input_field.png?raw=true">

- **Vincular a variable**: el texto que escriban los jugadores se guarda en la [variable](/variables), cuyo valor también se muestra en el campo. Si se vincula a una variable de lista, el texto escrito sustituye la lista entera.
- **Tipo de entrada**: **Texto**, **Solo números**, **Solo números decimales** o **URL**. No se pueden escribir otros caracteres.
- **Texto de ayuda** y **Color del texto de ayuda**: texto que aparece mientras el campo está vacío.
- **Longitud máxima del texto**: número de caracteres que caben.
- **Color de fondo**, **Color del borde**, **Radio de redondeo del borde** y **Color del texto**: ajustan su aspecto.

Por ejemplo, un campo vinculado a `server_address` y un botón con la acción [**Unirse al servidor**](/action-scripts#join-server) y el valor `$$server_address` permiten que los jugadores se unan a cualquier servidor.

Sin una variable, el marcador de posición [**Valor del campo de texto**](/placeholders#text-input-field-value) lee el texto, y la acción [**Establecer valor del campo de texto**](/action-scripts#set-text-input-field-value) lo cambia.

## Textos e información emergente

### Texto

Texto de cualquier longitud, desde una etiqueta breve hasta normas o notas de actualización con desplazamiento, con [Markdown](/text-formatting) y [marcadores de posición](/placeholders).

<img width="636" alt="Un elemento de texto con notas de actualización: un encabezado y una lista con una parte en negrita" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_text.png?raw=true">

- **Modo de origen**: escribe el texto o cárgalo desde un archivo o una página web.
- Un aspecto inicial y la opción de desplazarse cuando el texto sea más grande que el elemento.
- **Fondo**: un panel oscuro detrás del texto. Desactívalo con **Mostrar fondo** o usa una textura propia.

Consulta [Texto en los menús](/text-in-menus) para obtener más información.

### Información emergente

Un cuadro de texto como los que aparecen en las ayudas emergentes del juego, con [Markdown](/text-formatting) y [marcadores de posición](/placeholders).

<img width="712" alt="Un botón ¿Necesitas ayuda? con una información emergente al lado" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_tooltip.png?raw=true">

- Aparece donde lo coloques o junto al cursor con **Seguir al ratón**.
- Sus **Requisitos de carga** determinan cuándo aparece; por ejemplo, puedes usar [**El elemento está bajo el cursor**](/conditions#is-element-hovered) para un botón.
- **Fondo de la información emergente**: usa una textura propia en lugar del cuadro oscuro.

Encontrarás más información en [Texto en los menús](/text-in-menus).

### Texto emergente

El texto amarillo de la pantalla del título, con textos propios.

<img width="392" alt="Un texto emergente amarillo que dice ¡Ya está disponible la temporada 3!" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_splash_text.png?raw=true">

- **Modo de origen**: los textos emergentes vanilla, un texto propio o una línea aleatoria de un archivo de texto.
- **Rebote**, **Escala**, **Rotación**, **Color del texto** y **Sombra**: ajustan su aspecto.
- **Actualizar al cargar la pantalla**: elige un texto emergente nuevo cada vez que se abre la pantalla.

Encontrarás más información en [Texto emergente](/splash-text).

## Imágenes y contenido multimedia

### Imagen

Una imagen de tus archivos, de una página web o de los recursos del juego. También reproduce imágenes animadas.

<img width="608" alt="Un elemento de imagen que muestra el logotipo de Minecraft" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_image.png?raw=true">

- **Origen de la imagen**: la imagen. Los archivos compatibles se enumeran en [Imágenes](/images).
- **Restaurar relación de aspecto**: cambia la anchura para que la imagen no se deforme.
- **Textura dividida en nueve partes** y **Repetir textura**: escalan los marcos sin estirar sus bordes o repiten la imagen en mosaico. Consulta [División en nueve partes y mosaico](/nine-slicing-and-tiling).
- **Tinte de imagen [HEX]**: colorea la imagen.
- **Radio de redondeo de esquinas**: redondea sus esquinas.

### Presentación de diapositivas

Muestra, una tras otra, las imágenes de una presentación. Puedes crear presentaciones en `config/fancymenu/slideshows/`; consulta [Presentaciones de diapositivas](/slideshows).

- **Presentación de diapositivas**: la presentación que se mostrará.
- **Restaurar relación de aspecto**: cambia la anchura para que las imágenes no se deformen.

### Vídeo

Reproduce un archivo de vídeo, como un tráiler o un fondo animado.

> [!IMPORTANT]
> Los vídeos necesitan los mods Watermedia V3 y Watermedia Binaries V3. Consulta [Vídeos](/video).

- **Origen del vídeo**: un archivo de vídeo, un enlace web o un recurso del juego.
- **Repetir vídeo**, **Volumen** y **Canal de sonido**: ajustan su reproducción.
- **Reproducir vídeo en el editor de diseños**: indica si también se reproduce mientras editas.
- Acciones como [**Alternar estado de pausa del elemento de vídeo**](/action-scripts#toggle-video-element-paused-state) permiten pausarlo, saltar a un momento concreto o cambiar el volumen.

**Vídeo [Rinku]** es un elemento de vídeo antiguo que necesita el mod Rinku. Sigue funcionando en diseños antiguos, pero no aparece en **Nuevo elemento**.

### Sombreador GLSL

Ejecuta un sombreador GLSL propio dentro del elemento, por ejemplo, para mostrar colores animados o efectos de Shadertoy.

<img width="576" alt="Un elemento de sombreador GLSL que muestra un degradado de colores" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_glsl_shader.png?raw=true">

- **Origen del sombreador**: el código del sombreador. Los sombreadores de Shadertoy con `mainImage` funcionan tal cual.
- **Modo de compilación**: **Automático**, **Shadertoy** o **Fragmento directo**.
- **Origen del búfer A** a **Origen del búfer D**: pasadas adicionales para sombreadores con búferes.

Consulta [API de sombreadores GLSL](/glsl-shader-api) para aprender a crearlos.

### Navegador

Muestra una página web en directo, como un mapa del servidor o una página wiki.

> [!IMPORTANT]
> El navegador necesita el mod [Rinku](https://modrinth.com/mod/rinku) ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku)).

- **URL**: la página web.
- **Interactivo**: permite hacer clic, desplazarse y escribir. En el editor de diseños nunca es interactivo.
- **Silenciar navegador**, **Volumen de audio/vídeo**, **Repetir vídeos** y **Ocultar controles de vídeo**: ajustan el contenido multimedia de la página.

Para cargar un archivo HTML desde `config/fancymenu/assets/`, empieza la URL por `file:///`:

```
file:///config/fancymenu/assets/changelog.html
```

En Linux, utiliza en su lugar el marcador de posición [**Ruta absoluta de archivo/carpeta**](/placeholders#absolute-filefolder-path):

```
file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/changelog.html"}}
```

Las páginas web pueden ejecutar acciones y leer marcadores de posición: [API de JavaScript del navegador](/browser-api).

## Formas, objetos y modelos

### Forma rectangular

Un rectángulo de un solo color, como un panel detrás del texto.

<img width="536" alt="Un panel oscuro semitransparente con esquinas redondeadas y desenfoque, con las normas del servidor encima" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_rectangle_shape.png?raw=true">

- **Color**: un color HEX. Con dos dígitos más se vuelve semitransparente, como `#101828C8`.
- **Radio de redondeo de esquinas**: redondea todas las esquinas o cada una por separado.
- **Desenfoque** e **Intensidad del desenfoque**: desenfocan lo que hay detrás.

### Forma circular

Un círculo o una elipse de un solo color, como una luz de estado.

<img width="428" alt="Un punto verde junto a Supervivencia: conectado y un punto rojo junto a Creativo: desconectado" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_circle_shape.png?raw=true">

- **Color**, **Desenfoque** e **Intensidad del desenfoque**: funcionan igual que en la forma rectangular.
- **Redondez**: `2` es un círculo. Los valores mayores hacen que la forma sea más cuadrada y los menores, más puntiaguda.

### Objeto

Muestra un objeto de Minecraft o de un mod, como en el inventario.

<img width="460" alt="Una espada de diamante encantada, 16 manzanas, una manzana dorada y un tótem de la inmortalidad" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_item.png?raw=true">

- **Clave del objeto**: el objeto, por ejemplo, `minecraft:diamond_sword`.
- **Cantidad del objeto**, **Nombre del objeto**, **Descripción del objeto** y **Encantado**: igual que en un objeto real.
- **Mostrar información emergente del objeto**: muestra la información emergente del objeto cuando el cursor está encima.
- **Datos NBT personalizados**: más datos del objeto, escritos como la parte de un comando `/give` que va justo después del objeto.

### Modelo JSON de bloque/objeto

Muestra en 3D un modelo de bloque u objeto, ya sea de los recursos del juego o de un archivo JSON propio.

<img width="296" alt="Una mesa de trabajo en 3D" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_json_model.png?raw=true">

- **Modelo**: el **Origen del modelo**, por ejemplo, `minecraft:models/block/crafting_table.json`.
- **Textura**: sustituye la textura del modelo por una propia.
- **Transformación**: escala, gira y mueve el modelo.
- **Iluminación**: **Tono de la luz [HEX]** colorea la luz del modelo.

### Entidad de jugador

Muestra un jugador en 3D, como el personaje del propio jugador en la pantalla del título.

<img width="360" alt="Una entidad de jugador nueva con la skin predeterminada, mirando hacia la derecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_player_entity.png?raw=true">

> [!IMPORTANT]
> Las entidades de jugador necesitan el mod Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Sin él, muestran un error en lugar del jugador.

- **Copiar jugador del cliente**: muestra al jugador que está jugando, con su skin y su nombre.
- **Nombre del jugador**, **Textura de la skin** y **Textura de la capa**: permiten mostrar otro jugador o skin.
- **Pose de la entidad**, **La cabeza sigue al ratón** y **El cuerpo sigue al ratón**: determinan cómo se coloca y hacia dónde mira.
- **Armadura y herramientas**, **Loro**, **Es una cría** y **Mostrar nombre del jugador**: determinan qué lleva puesto y qué muestra.

Encontrarás más información en [Entidades de jugador](/player-entities). Si solo quieres mostrar una cabeza, consulta [Cabezas de jugador](/player-heads).

### Barra de progreso

Una barra que se va llenando, como una barra de carga.

<img width="496" alt="Una barra de progreso al 65 % bajo el texto Cargando mundo... 65 %" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/elements_progress_bar.png?raw=true">

- **Origen del valor de progreso**: indica cuánto se ha llenado. Usa aquí [marcadores de posición](/placeholders), como [**Progreso de carga del mundo**](/placeholders#world-loading-progress) en una pantalla de carga del mundo.
- **Modo del valor de progreso**: **PORCENTAJE (0-100)** o **PUNTO FLOTANTE (0.0-1.0)**.
- **Dirección**: el lado hacia el que se llena.
- **Color de la barra** y **Color de fondo**, o **Textura de la barra** y **Textura de fondo**.
- **Animación de llenado suave**: se desplaza hasta los nuevos valores en lugar de dar un salto.
- **Usar el progreso como anclaje del elemento**: los elementos anclados a la barra se desplazan junto al extremo de la parte llena.

## Ayudantes de diseño

### Área desplazable

Contiene otros elementos y permite desplazarse por ellos, como en una lista de servidores o una página de información extensa.

<img width="800" alt="Tres áreas desplazables que organizan botones y objetos como una pila, una cuadrícula y un flujo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

- Suelta elementos dentro del área en el editor de diseños. Solo se pueden incluir elementos personalizados, no elementos vanilla.
- **Disposición**: coloca los elementos manualmente o deja que el área los organice en una pila, cuadrícula o flujo.
- **Fondo**: un panel oscuro detrás del área. Desactívalo con **Mostrar fondo** o usa una textura propia.

Consulta [Áreas desplazables](/scrollable-areas) para obtener más información.

### Arrastrador

Un área que los jugadores pueden agarrar y mover fuera del editor. Los elementos anclados a ella se desplazan junto con ella, como en un panel de información móvil. Es invisible fuera del editor.

**Guardar desplazamiento de arrastre del usuario** conserva la nueva posición al cerrar la pantalla y reiniciar el juego. Encontrarás más información en [Arrastrador](/dragger).

### Animador de elementos

Mueve y cambia el tamaño de otros elementos mediante fotogramas clave, por ejemplo, para hacer que un panel entre deslizándose en la pantalla. Es invisible fuera del editor.

- **Gestionar elementos de destino**: los elementos que anima.
- **Editar fotogramas clave**: abre el editor de fotogramas clave.
- **Repetir animación**: la vuelve a iniciar al terminar.

Consulta [Animador de elementos](/element-animator) para obtener más información.

## Elementos invisibles

Estos elementos solo aparecen en el editor de diseños.

### Temporizador

Ejecuta su script de acciones una y otra vez mientras la pantalla está abierta.

> [!IMPORTANT]
> Se recomienda usar [Programadores](/schedulers) para todo lo que se repita o se ejecute más adelante. Siempre que sea posible, úsalos en lugar de los temporizadores. Funcionan en cualquier pantalla e incluso sin ninguna pantalla abierta; todas las acciones funcionan en ellos, y las acciones permiten iniciarlos y detenerlos.

Estas son algunas tareas que pueden hacer los temporizadores y cómo realizarlas con programadores:

- Ejecutar acciones continuamente mientras una pantalla está abierta: usa un programador con **Retardo entre ticks (ms)**. Inícialo con [**Iniciar programador**](/action-scripts#start-scheduler) en **Editar script de acciones «Abrir pantalla»** del diseño y detenlo con [**Detener programador**](/action-scripts#stop-scheduler) en **Editar script de acciones «Cerrar pantalla»**. Ambas opciones están en el menú contextual del fondo del editor.
- Ejecutar acciones una vez por inicio del juego: usa un programador con **Iniciar al abrir** y **Ticks que ejecutar** con el valor `1`.
- Ejecutar acciones una vez cada vez que se abre una pantalla: no hace falta ningún temporizador ni programador. Añade las acciones a **Editar script de acciones «Abrir pantalla»**.

Ajustes del temporizador:

- **Retardo entre ticks [ms]**: el tiempo, en milisegundos, entre dos ejecuciones. `0` lo ejecuta en cada tick, 20 veces por segundo.
- **Modo de tick**: **Normal** lo ejecuta continuamente. **Sesión** lo ejecuta una sola vez hasta que se reinicie el juego. **Al cargar la pantalla** lo ejecuta una vez cada vez que se abre la pantalla, también cuando se cambia el tamaño de la ventana.
- **Asíncrono**: lo ejecuta en segundo plano. La mayoría de las acciones no pueden ejecutarse así y mostrarán un error.

### Audio

Reproduce música o sonidos mientras la pantalla está abierta, con una pista detrás de otra.

- **Gestionar pistas**: los archivos de audio, su orden y su **Peso de pista** al reproducirlas aleatoriamente.
- **Modo de reproducción**: **Normal** las reproduce en orden; **Aleatorio**, en orden aleatorio.
- **Repetir pistas**, **Volumen** y **Canal de sonido**: ajustan la reproducción.

Para que la música siga sonando al cambiar de pantalla, coloca el elemento de audio en un [Diseño universal](/universal-layouts). Encontrarás más información en [Música de fondo de los menús](/background-music).

### Controlador de música

Desactiva la música propia del juego en esta pantalla.

- **Reproducir música de menú**: la música de los menús cuando no hay ningún mundo cargado, como en la pantalla del título.
- **Reproducir música del mundo**: la música del mundo que sigue sonando en los menús, como el inventario.

Solo funciona mientras una pantalla está abierta.

### Cursor

Sustituye el cursor del ratón por una imagen propia mientras la pantalla está abierta.

- **Textura del cursor**: una imagen PNG, por ejemplo, de 32 × 32 píxeles.
- **Coordenada X del punto activo** y **Coordenada Y del punto activo**: el píxel de la imagen que hace clic, como la punta de una flecha.
- **Modo de vista previa en el editor**: muestra el cursor en el editor cuando el ratón está sobre el elemento.

Encontrarás más información en [Cursor personalizado](/custom-cursor).
