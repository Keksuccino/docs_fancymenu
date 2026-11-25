---
title: Fondos del menú
description: >-
  Dale a un menú su propio fondo, como una imagen, una panorámica, un vídeo, un
  color o un shader, y combina varios.
sourceBlobSha: 934e0cbcce41f049826fcd7b96715e3cb0e27214
---

# Fondos del menú

Un diseño puede darle a su pantalla un fondo propio: una imagen, una animación, una panorámica, una presentación de diapositivas, un vídeo, un color, un sitio web o un shader. Este sustituye al fondo normal de la pantalla, como la panorámica de la pantalla del título, el desenfoque de otros menús o el mundo que hay detrás del menú de pausa.

<img width="800" alt="La pantalla del título con un fondo de pixel art de un valle nevado de noche, con una aurora, luna llena y una cabaña con las ventanas iluminadas" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_hero.png?raw=true">

> [!TIP]
> Para dar el mismo fondo a todos los menús sin crear diseños, usa las [Personalizaciones globales](/global-customizations#menu-backgrounds).

# Configurar un fondo

<img width="800" alt="Al hacer clic derecho en el fondo del editor de la pantalla del título, se abre Fondos del menú y luego Imagen, se activa Mostrar fondo y se elige una imagen con Elegir imagen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_image.gif?raw=true">

1. Abre un diseño de la pantalla en el [editor de diseños](/layout-editor).
2. Haz clic derecho en el fondo del editor y abre **Fondos del menú**. También está en **barra de menús -> Diseño -> Propiedades del diseño**.
3. Abre un tipo de fondo, como **Imagen**.
4. Haz clic en **Mostrar fondo** para cambiarlo a **Activado**.
5. Configura el fondo; por ejemplo, pulsa **Elegir imagen** para un fondo de imagen.

<img width="800" alt="El menú Fondos del menú, con una marca delante de Imagen y una cruz delante de los demás tipos, y debajo los ajustes de todos los fondos" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_menu.png?raw=true">

En **Fondos del menú**, cada tipo activado tiene un ✔ delante, y cada tipo desactivado, un ✖. Pasa el cursor por encima de un tipo para ver qué hace.

Para recuperar el fondo normal de la pantalla, vuelve a cambiar **Mostrar fondo** del tipo a **Desactivado**. Los ajustes se conservan, así que puedes volver a activarlo más adelante.

# Tipos de fondo

## Imagen

Una imagen de tus archivos, de un sitio web o de los recursos del juego, extendida por toda la pantalla. También se reproducen las imágenes animadas. En [Imágenes](/images) se enumeran los archivos compatibles.

- **Elegir imagen**: la imagen. Consulta de dónde puede proceder en [Recursos](/resources).
- **Elegir imagen alternativa**: se muestra mientras no se pueda cargar la imagen, como ocurre con una imagen web cuando no tienes conexión.
- **Reiniciar texturas animadas al abrir la pantalla**: vuelve a iniciar una [imagen animada](/animations) cada vez que se abre la pantalla. Si no, continúa desde donde se quedó.
- **Repetir textura**: repite la imagen por toda la pantalla en lugar de estirarla. Consulta [División en nueve partes y repetición](/nine-slicing-and-tiling).
- **Deslizar imágenes anchas de izquierda a derecha**: una imagen ancha, como una foto de un paisaje entero, ocupa toda la altura de la pantalla y se desliza lentamente de un lado a otro, haciendo una breve pausa en cada extremo.
- **Efecto de paralaje** y sus ajustes: la imagen se mueve ligeramente con el ratón. Consulta [Efecto de paralaje](/parallax#menu-backgrounds).

**Deslizar imágenes anchas de izquierda a derecha** no se puede activar a la vez que **Repetir textura** o **Efecto de paralaje**.

## Color

Un solo color en toda la pantalla.

- **Color [HEX]**: el color, como `#1B2440`. Si añades dos dígitos más, será semitransparente, como `#1B2440C8`. También puede ser un [marcador de posición](/placeholders).

El color queda debajo de los demás fondos del diseño, así que rellena sus partes transparentes. Consulta [Combinar fondos](#stacking-backgrounds).

## Panorámica cúbica

Una panorámica que gira lentamente, como la de la pantalla del título. Puedes crear panorámicas en `config/fancymenu/panoramas/`; consulta [Panorámicas](/panoramas).

- **Nombre de la panorámica**: abre **Elegir panorámica**, donde puedes seleccionar una de tus panorámicas y ver una vista previa.
- **Borrar panorámica**: elimina la panorámica.

Si no hay ninguna panorámica, el fondo muestra la textura morada y negra de Minecraft para las texturas que faltan.

## Presentación de diapositivas

Muestra, una tras otra, las imágenes de una presentación de diapositivas. Puedes crear presentaciones en `config/fancymenu/slideshows/`; consulta [Presentaciones de diapositivas](/slideshows).

- **Nombre de la presentación**: abre **Elegir presentación**, donde puedes seleccionar una de tus presentaciones.
- **Borrar presentación**: elimina la presentación.

Si no hay ninguna presentación, el fondo también muestra la textura que falta de Minecraft.

## Vídeo

Reproduce un vídeo de tus archivos, de un sitio web o de los recursos del juego. Necesita Watermedia; consulta [Vídeos](/video#requirements). Si no está instalado, el fondo muestra un aviso con enlaces de descarga.

- **Fuente del vídeo**: el vídeo.
- **Repetir vídeo**, **Volumen** y **Canal de sonido**: cómo se reproduce.
- **Efecto de paralaje** y sus ajustes: como en los fondos de imagen.
- **Reproducir vídeo en el editor de diseños**: si está desactivado, el vídeo permanece en pausa en el editor de diseños.

Las [acciones](/video) pueden pausar el vídeo y cambiar su volumen y su posición de reproducción. Necesitan el ID del fondo: haz clic en **Copiar identificador del fondo** en sus ajustes.

## Navegador

Un sitio web que ocupa toda la pantalla, como el [elemento Navegador](/elements#browser).

> [!IMPORTANT]
> El navegador necesita el mod [Rinku](https://modrinth.com/mod/rinku). Si no está instalado, el fondo es rojo e indica que falta Rinku.

- **URL**: el sitio web. Puede contener [marcadores de posición](/placeholders).
- **Procesar clics del ratón**, **Procesar desplazamientos del ratón** y **Procesar pulsaciones del teclado**: permiten a los jugadores hacer clic, desplazarse y escribir en el sitio web. El sitio web recibe el teclado en cuanto se abre la pantalla.
- **Consumir clics del ratón**, **Consumir desplazamientos del ratón** y **Consumir pulsaciones del teclado**: impiden que los clics, el desplazamiento y las teclas lleguen al sitio web, para que la propia pantalla tampoco reaccione a ellos.
- **Silenciar navegador**, **Volumen de audio/vídeo**, **Repetir vídeos** y **Ocultar controles de vídeo**: opciones para los archivos multimedia del sitio web.

Los botones y elementos que estén delante del fondo siempre reciben los clics primero. En el editor de diseños, el fondo muestra franjas en lugar del sitio web.

## Shader GLSL

Dibuja un shader, un pequeño programa para la tarjeta gráfica, como ondas animadas, estrellas o patrones. También funcionan los shaders de Shadertoy.

- **Código fuente del shader**: el código del shader.
- **Mostrar errores de compilación**: muestra en pantalla los errores del código. Desactívalo cuando el diseño esté terminado.

El resto de los ajustes, como las pasadas adicionales, las texturas y el tiempo, se explican en la [API de shaders GLSL](/glsl-shader-api).

## Vídeo [Rinku]

Un fondo de vídeo antiguo que necesita Rinku. Solo aparece en la lista mientras está activado, por ejemplo, en diseños de versiones anteriores. Usa **Vídeo** en su lugar.

# Ajustes para todos los fondos

Debajo de los tipos, **Fondos del menú** incluye ajustes que se aplican a todos los fondos del diseño:

- **Conservar la relación de aspecto del fondo**: mantiene las proporciones de los fondos de imagen, presentación de diapositivas y vídeo. Siguen ocupando toda la pantalla, pero se recortan las partes que no caben. Si está desactivado, se estiran para ajustarse a la pantalla.
- **Mostrar capa oscura sobre el fondo personalizado**: coloca sobre los fondos la capa oscura y transparente de los menús de Minecraft, para que los botones y el texto destaquen más.
- **Aplicar el desenfoque del fondo de Minecraft**: desenfoca los fondos igual que Minecraft desenfoca el mundo que hay detrás de los menús. La intensidad depende del ajuste **Desenfoque del fondo del menú** del jugador, en **Ajustes de accesibilidad** de Minecraft. En `0`, no hay desenfoque.

<img width="800" alt="El mismo fondo tres veces, una al lado de otra: tal cual, más oscuro con Mostrar capa oscura sobre el fondo personalizado y desenfocado con Aplicar el desenfoque del fondo de Minecraft" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_effects.png?raw=true">

De izquierda a derecha: sin ajustes, **Mostrar capa oscura sobre el fondo personalizado** y **Aplicar el desenfoque del fondo de Minecraft**.

# Combinar fondos

Puedes activar varios tipos en un mismo diseño. Se dibujan unos sobre otros en este orden, de abajo arriba:

1. Color
2. Panorámica cúbica
3. Imagen
4. Presentación de diapositivas
5. Vídeo
6. Vídeo [Rinku]
7. Navegador
8. Shader GLSL

Los tipos añadidos por otros mods se dibujan al final, por encima de los demás.

FancyMenu dibuja un fondo negro detrás de los fondos, así que las partes transparentes de una imagen se ven negras. Si colocas debajo un fondo de color, esas partes se rellenan con ese color:

<img width="800" alt="Un paisaje de pixel art con el cielo transparente. En la mitad izquierda, el cielo es negro. En la mitad derecha, un fondo de color azul lo rellena" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_stacking.png?raw=true">

A la izquierda, solo está activada la imagen. A la derecha, un fondo de color rellena el cielo.

- Una imagen, presentación de diapositivas o shader transparente sobre una panorámica cúbica funciona igual, como un marco alrededor de una panorámica giratoria.
- Un fondo de vídeo nunca es transparente. Cubre todo lo que haya debajo, incluso las zonas que el vídeo no ocupa.

## Varios diseños

Cuando hay varios diseños activos en una pantalla, como un [diseño universal](/universal-layouts) y un diseño de la propia pantalla, también se combinan sus fondos:

- El diseño con el valor más alto de **Índice del diseño [Orden de varios diseños]** queda por encima. Puedes cambiarlo en el menú que aparece al hacer clic derecho en el fondo del editor.
- Si uno de los diseños activa un [ajuste para todos los fondos](#settings-for-all-backgrounds), se aplica a los fondos de todos ellos.
- El editor de diseños solo muestra los fondos del diseño que estás editando.

# Información útil

- Los elementos del diseño siempre aparecen delante de sus fondos.
- **Copiar identificador del fondo**, en los ajustes de cada tipo, copia el ID del fondo para usarlo en acciones y marcadores de posición que lo controlen, como los de los [fondos de vídeo](/video).
- **Exportar para IA**, en los ajustes de cada tipo, copia el fondo para un [chat de IA](/export-for-ai).
- El encabezado y el pie de página de las pantallas con listas, como la lista de mundos, tienen sus propias texturas: haz clic derecho en el fondo del editor y abre **Personalizaciones del encabezado/pie de página**.
