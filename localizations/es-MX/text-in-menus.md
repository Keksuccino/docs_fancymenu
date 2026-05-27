---
title: Texto en Menús
description: Cómo agregar contenido de texto a los menús.
---
# Texto en Menús

FancyMenu te permite agregar contenido de texto a menús/pantallas mediante el elemento **Text**.

Este elemento se puede desplazar, tiene compatibilidad total con Markdown y ajuste de línea, lo que lo hace muy potente para mostrar incluso contenido de texto complejo, pero también es ideal para líneas simples de una sola frase.

# Contenido de Texto

El elemento Text puede obtener su contenido de muchas maneras. Te permite definir una fuente para su contenido de texto, que puede ser una entrada de texto sin formato directa, un archivo de texto local en la carpeta `assets` de FancyMenu (`/config/fancymenu/assets/`), un archivo de texto web (mediante URL) o un archivo de texto local cargado a través de un paquete de recursos.

Usar el tipo de fuente web como fuente de texto es especialmente útil si quieres crear algo como un registro de cambios que siempre esté actualizado, un ticker de noticias o cosas similares, sin necesidad de lanzar una actualización de tu modpack.

Ten en cuenta que FancyMenu almacena en caché el contenido de las fuentes de texto, para no tener que obtenerlo constantemente de nuevo (lo cual sería muy malo para el rendimiento). El contenido solo se guarda en caché durante la sesión activa, así que reiniciar el juego limpiará la caché. También puedes limpiar la caché recargando FancyMenu mediante **barra de menú -> Personalización -> Recargar FancyMenu**.

# Marcadores de posición

El elemento Text también es compatible con el sistema de marcadores de posición de FancyMenu, lo que permite que el contenido de texto sea dinámico y reaccione a diversos cambios en menús, mundos, jugadores, etc.

# Personalizar o Desactivar Markdown

Si quieres personalizar los colores de los encabezados u otros elementos relacionados con Markdown, solo haz **clic derecho** sobre el elemento Text y después en **Markdown**. En el submenú de contexto que se abre, verás muchas opciones para personalizar la apariencia y el comportamiento del analizador de Markdown.

Si no quieres que se analice Markdown en absoluto, lo cual puede mejorar el rendimiento para contenido de texto largo, puedes desactivar Markdown por completo en el menú **Markdown** al hacer **clic derecho** sobre el elemento Text.

# Desactivar el Ajuste de Línea

Si no quieres ajuste de línea, puedes desactivarlo haciendo **clic derecho** sobre el elemento Text.

# Desactivar el Desplazamiento y Ocultar los Agarradores de Desplazamiento

Los elementos de texto se pueden desplazar de forma predeterminada y, si el elemento considera que el usuario necesita desplazarse para ver todo su contenido, mostrará sus barras/agarradores de desplazamiento, que son barras pequeñas, grises y translúcidas (con bordes redondeados) en los lados derecho e inferior del elemento Text (barras de desplazamiento vertical y horizontal). A veces también se confunden con sombras.

Puedes desactivar estos agarradores desactivando **Scrolling** en el menú que aparece al hacer **clic derecho** sobre el elemento. Esto desactivará el desplazamiento en general, no solo los agarradores. Si solo quieres que los agarradores sean invisibles, pero seguir pudiendo desplazarte, puedes definir texturas personalizadas para los agarradores de desplazamiento haciendo **clic derecho** sobre el elemento. Solo configura ahí una textura completamente transparente.

# Formato de Texto de Componentes en Bruto de Minecraft (Componentes JSON Serializados)

El elemento Text NO es compatible con el formato de componentes en bruto de Minecraft. Este formato solo es compatible con las etiquetas de botones y deslizadores.
