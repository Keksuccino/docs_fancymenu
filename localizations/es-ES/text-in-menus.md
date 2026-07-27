---
title: Texto en los menús
description: Cómo añadir contenido de texto a los menús.
---
# Texto en los menús

FancyMenu te permite añadir contenido de texto a menús/pantallas mediante el elemento **Texto**.

Este elemento es desplazable, tiene compatibilidad total con Markdown y ajuste de línea, lo que lo hace muy potente para mostrar incluso contenido de texto complejo, aunque también es ideal para frases simples de una sola línea.

# Contenido del texto

El elemento Texto puede obtener su contenido de muchas formas. Te permite establecer una fuente para su contenido de texto, que puede ser una entrada de texto plano directa, un archivo de texto local en el directorio de recursos de FancyMenu (`<game-directory>/config/fancymenu/assets/`), un archivo de texto web (mediante URL) o un archivo de texto local cargado a través de un paquete de recursos.

Usar el tipo de fuente web como fuente de texto es especialmente útil si quieres crear algo como un registro de cambios que esté siempre actualizado o un teletipo de noticias y cosas parecidas, sin necesidad de publicar una actualización de tu modpack.

Ten en cuenta que FancyMenu almacena en caché el contenido de las fuentes de texto, para no tener que obtenerlo constantemente de nuevo (lo cual sería muy malo para el rendimiento). El contenido solo se almacena en caché durante la sesión activa, así que reiniciar el juego borrará la caché. También puedes borrar la caché recargando FancyMenu mediante **barra de menú -> Personalización -> Recargar FancyMenu**.

# Marcadores de posición

El elemento Texto también admite el sistema de marcadores de posición de FancyMenu, lo que permite hacer que el contenido de texto sea dinámico y reaccione a distintos cambios en menús, mundos, jugadores, etc.

# Personalizar o desactivar Markdown

Si quieres personalizar los colores de los encabezados u otros elementos relacionados con Markdown, simplemente **haz clic con el botón derecho** en el elemento Texto y pulsa en **Markdown**. En el submenú contextual que se abre, verás muchas opciones para personalizar el aspecto y el comportamiento del analizador de Markdown.

Si no quieres que se analice Markdown en absoluto, lo que puede mejorar el rendimiento en contenidos de texto largos, puedes desactivar Markdown por completo en el menú **Markdown** al **hacer clic con el botón derecho** en el elemento Texto.

# Desactivar el ajuste de línea

Si no quieres el ajuste de línea, puedes desactivarlo **haciendo clic con el botón derecho** en el elemento Texto.

# Desactivar el desplazamiento y ocultar las barras de desplazamiento

Los elementos de texto son desplazables por defecto y, si el elemento cree que el usuario necesita desplazarse para ver todo su contenido, mostrará sus barras/deslizadores de desplazamiento, que son pequeñas barras grises translúcidas (con bordes redondeados) en los lados derecho e inferior del elemento Texto (barras de desplazamiento vertical y horizontal). A veces también se confunden los deslizadores de desplazamiento con sombras.

Puedes desactivar estos deslizadores desactivando **Desplazamiento** en el menú que se abre al **hacer clic con el botón derecho** en el elemento. Esto desactivará el desplazamiento en general, no solo los deslizadores. Si solo quieres que los deslizadores sean invisibles, pero seguir pudiendo desplazarte, puedes establecer texturas personalizadas para los deslizadores de desplazamiento haciendo clic con el botón derecho en el elemento. Solo tienes que poner allí una textura totalmente transparente.

# Formato de texto de componentes sin procesar de Minecraft (componentes JSON serializados)

El elemento Texto NO es compatible con el formato de componentes sin procesar de Minecraft. Este formato solo es compatible con las etiquetas de los botones y los deslizadores.
