---
title: Texto en menús
description: Cómo agregar contenido de texto a los menús.
---

# Texto en menús

FancyMenu te permite agregar contenido de texto a menús/pantallas mediante el elemento **Texto**.

Este elemento es desplazable, tiene soporte completo de Markdown y ajuste de línea, lo que lo hace muy potente para mostrar incluso contenido de texto complejo, pero también es ideal para textos sencillos de una sola línea.

## Contenido de texto

El elemento de Texto puede obtener su contenido de muchas formas. Te permite definir una fuente para su contenido de texto, que puede ser una entrada de texto plano directa, un archivo de texto local en la carpeta `assets` de FancyMenu (`/config/fancymenu/assets/`), un archivo de texto en la web (mediante URL) o un archivo de texto local cargado a través de un resource pack.

Usar el tipo de fuente web como fuente de texto es especialmente útil si quieres hacer algo como un registro de cambios que siempre esté actualizado, un ticker de noticias o cosas similares, sin necesidad de publicar una actualización de tu modpack.

Ten en cuenta que FancyMenu almacena en caché el contenido de las fuentes de texto, para que no tenga que obtenerlo constantemente de nuevo (lo cual sería muy malo para el rendimiento). El contenido solo se almacena en caché durante la sesión activa, así que reiniciar el juego limpiará la caché. También puedes limpiar la caché recargando FancyMenu mediante **barra de menú -> Personalización -> Recargar FancyMenu**.

## Marcadores de posición

El elemento de Texto también es compatible con el sistema de marcadores de posición de FancyMenu, lo que permite hacer que el contenido del texto sea dinámico y responda a varios cambios en menús, mundos, jugadores, etc.

## Personalizar o desactivar Markdown

Si quieres personalizar los colores de los encabezados u otros elementos relacionados con Markdown, solo **haz clic derecho** en el elemento de Texto y luego en **Markdown**. En el submenú contextual que se abre, verás muchas opciones para personalizar la apariencia y el comportamiento del analizador de Markdown.

Si no quieres que Markdown se procese en absoluto, lo cual puede mejorar el rendimiento en contenido de texto largo, puedes desactivar Markdown por completo en el menú **Markdown** al **hacer clic derecho** en el elemento de Texto.

## Desactivar el ajuste de línea

Si no quieres que el texto se ajuste automáticamente a nuevas líneas, puedes desactivarlo **haciendo clic derecho** en el elemento de Texto.

## Desactivar el desplazamiento

Los elementos de Texto son desplazables de forma predeterminada y, si el elemento considera que el usuario necesita desplazarse para ver todo su contenido, mostrará sus barras de desplazamiento, que son barras pequeñas y grises en los lados derecho e inferior del elemento de Texto (barras de desplazamiento vertical y horizontal).

Puedes desactivar estas barras quitando **Desplazamiento** en el menú que se abre al **hacer clic derecho** en el elemento. Esto desactivará el desplazamiento en general, no solo las barras. Si en cambio quieres que las barras sean invisibles, puedes establecer texturas personalizadas para las barras de desplazamiento al hacer clic derecho en el elemento. Solo configura ahí una textura completamente transparente.

## Formato de texto de componentes sin procesar de Minecraft (componentes JSON serializados)

El elemento de Texto NO es compatible con el formato de componentes sin procesar de Minecraft. Este formato solo es compatible con las etiquetas de botones y deslizadores.
