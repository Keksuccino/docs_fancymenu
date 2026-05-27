---
title: Texto en menús
description: Cómo añadir contenido de texto a los menús.
---
# Texto en menús

FancyMenu te permite añadir contenido de texto a menús/pantallas mediante el elemento **Text**.

Este elemento es desplazable, tiene soporte completo de Markdown y ajuste de línea, lo que lo hace muy potente para mostrar incluso contenido de texto complejo, pero también es ideal para una sola línea sencilla.

# Contenido de texto

El elemento Text puede obtener su contenido de muchas formas. Te permite definir una fuente para su contenido de texto, que puede ser una entrada de texto plano directa, un archivo de texto local en la carpeta `assets` de FancyMenu (`/config/fancymenu/assets/`), un archivo de texto web (mediante URL) o un archivo de texto local cargado a través de un paquete de recursos.

Usar el tipo de fuente web como origen de texto es especialmente útil si quieres crear algo como un registro de cambios que esté siempre actualizado, un ticker de noticias o cosas similares, sin necesidad de publicar una actualización de tu modpack.

Ten en cuenta que FancyMenu almacena en caché el contenido de las fuentes de texto, para no tener que volver a obtenerlo constantemente (lo que sería muy malo para el rendimiento). El contenido solo se guarda en caché durante la sesión activa, así que reiniciar el juego borrará la caché. También puedes borrar la caché recargando FancyMenu mediante **barra de menús -> Personalización -> Recargar FancyMenu**.

# Marcadores de posición

El elemento Text también admite el sistema de marcadores de posición de FancyMenu, lo que permite que el contenido de texto sea dinámico y reaccione a distintos cambios en menús, mundos, jugadores, etc.

# Personalizar o desactivar Markdown

Si quieres personalizar los colores de los títulos u otros elementos relacionados con Markdown, simplemente haz **clic derecho** en el elemento Text y pulsa en **Markdown**. En el submenú contextual que se abre, verás muchas opciones para personalizar la apariencia y el comportamiento del analizador de Markdown.

Si no quieres usar Markdown en absoluto, lo que puede mejorar el rendimiento con contenido de texto largo, puedes desactivarlo por completo en el menú **Markdown** al **hacer clic derecho** sobre el elemento Text.

# Desactivar el ajuste de línea

Si no quieres ajuste de línea, puedes desactivarlo haciendo **clic derecho** sobre el elemento Text.

# Desactivar el desplazamiento y ocultar los controles de desplazamiento

Los elementos de texto son desplazables de forma predeterminada y, si el elemento considera que el usuario necesita desplazarse para ver todo su contenido, mostrará sus barras/controles de desplazamiento, que son pequeñas barras grises translúcidas (con bordes redondeados) en los lados derecho e inferior del elemento Text (barras de desplazamiento vertical y horizontal). A veces, los controles de desplazamiento también se confunden con sombras.

Puedes desactivar estos controles desmarcando **Scrolling** en el menú que se abre al **hacer clic derecho** sobre el elemento. Esto desactivará el desplazamiento en general, no solo los controles. Si solo quieres que los controles sean invisibles, pero seguir pudiendo desplazarte, puedes establecer texturas personalizadas para los controles de desplazamiento haciendo clic derecho sobre el elemento. Solo tienes que definir allí una textura completamente transparente.

# Formato de texto de componentes sin procesar de Minecraft (componentes JSON serializados)

El elemento Text NO es compatible con el formato de componentes sin procesar de Minecraft. Este formato solo es compatible con las etiquetas de botones y deslizadores.
