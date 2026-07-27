---
title: Texto en los menús
description: Cómo agregar contenido de texto a los menús.
---
# Texto en los menús

FancyMenu te permite agregar contenido de texto a menús/pantallas mediante el elemento **Texto**.

Este elemento es desplazable, tiene compatibilidad completa con Markdown y ajuste de línea, lo que lo hace muy poderoso para mostrar incluso contenido de texto complejo, pero también es excelente para líneas simples.

# Contenido de texto

El elemento Texto puede obtener su contenido de muchas maneras. Te permite definir una fuente para su contenido de texto, que puede ser una entrada de texto plano directa, un archivo de texto local en el directorio de assets de FancyMenu (`<game-directory>/config/fancymenu/assets/`), un archivo de texto en la web (mediante URL) o un archivo de texto local cargado a través de un paquete de recursos.

Usar el tipo de fuente web como fuente de texto es especialmente útil si quieres crear algo como un registro de cambios que siempre esté actualizado o un ticker de noticias y cosas similares, sin necesidad de publicar una actualización para tu modpack.

Ten en cuenta que FancyMenu almacena en caché el contenido de las fuentes de texto, así que no tiene que obtenerlo constantemente de nuevo (lo cual sería muy malo para el rendimiento). El contenido solo se guarda en caché durante la sesión activa, así que reiniciar el juego limpiará la caché. También puedes borrar la caché recargando FancyMenu mediante **barra de menú -> Personalización -> Recargar FancyMenu**.

# Marcadores de posición

El elemento Texto también es compatible con el sistema de marcadores de posición de FancyMenu, lo que hace posible que el contenido de texto sea dinámico y reaccione a diversos cambios en menús, mundos, jugadores, etc.

# Personalizar o desactivar Markdown

Si quieres personalizar los colores de los encabezados u otras cosas relacionadas con Markdown, solo haz **clic derecho** en el elemento Texto y luego en **Markdown**. En el submenú contextual que se abre, verás muchas opciones para personalizar la apariencia y el comportamiento del analizador de Markdown.

Si no quieres el análisis de Markdown en absoluto, lo cual puede mejorar el rendimiento para contenido de texto largo, puedes desactivar Markdown por completo en el menú **Markdown** al **hacer clic derecho** en el elemento Texto.

# Desactivar el ajuste de línea

Si no quieres el ajuste de línea, puedes desactivarlo haciendo **clic derecho** en el elemento Texto.

# Desactivar el desplazamiento y ocultar los controles de desplazamiento

Los elementos de texto se pueden desplazar de forma predeterminada y, si el elemento considera que el usuario necesita desplazarse para ver todo su contenido, mostrará sus barras/controles de desplazamiento, que son pequeñas barras grises semitransparentes (con bordes redondeados) en los lados derecho e inferior del elemento Texto (barras de desplazamiento vertical y horizontal). A veces también se confunden los controles de desplazamiento con sombras.

Puedes desactivar estos controles desmarcando **Desplazamiento** en el menú que se abre al **hacer clic derecho** en el elemento. Esto desactivará el desplazamiento en general, no solo los controles. Si solo quieres que los controles sean invisibles, pero seguir pudiendo desplazarte, puedes establecer texturas personalizadas para los controles de desplazamiento haciendo clic derecho en el elemento. Solo asigna ahí una textura completamente transparente.

# Formato de texto de componentes sin formato de Minecraft (componentes JSON serializados)

El elemento Texto NO es compatible con el formato de componentes sin formato de Minecraft. Este formato solo es compatible con las etiquetas de botones y deslizadores.
