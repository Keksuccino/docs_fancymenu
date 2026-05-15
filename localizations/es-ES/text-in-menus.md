---
title: Texto en menús
description: Cómo añadir contenido de texto a los menús.
---

# Texto en menús

FancyMenu te permite añadir contenido de texto a menús/pantallas mediante el elemento **Texto**.

Este elemento es desplazable, tiene compatibilidad completa con Markdown y ajuste de línea, lo que lo hace muy potente para mostrar incluso contenido de texto complejo, pero también es ideal para simples frases de una sola línea.

## Contenido de texto

El elemento Texto puede obtener su contenido de muchas formas. Te permite definir una fuente para su contenido, que puede ser una entrada de texto plano directa, un archivo de texto local en la carpeta `assets` de FancyMenu (`/config/fancymenu/assets/`), un archivo de texto web (mediante URL) o un archivo de texto local cargado a través de un paquete de recursos.

Usar el tipo de origen web como fuente de texto es especialmente útil si quieres crear algo como un registro de cambios siempre actualizado o un ticker de noticias y cosas similares, sin necesidad de publicar una actualización de tu modpack.

Ten en cuenta que FancyMenu almacena en caché el contenido de las fuentes de texto, para no tener que recuperarlo constantemente (lo que sería muy malo para el rendimiento). El contenido solo se almacena en caché durante la sesión activa, así que reiniciar el juego borrará la caché. También puedes borrar la caché recargando FancyMenu mediante **barra de menú -> Personalización -> Recargar FancyMenu**.

## Marcadores de posición

El elemento Texto también admite el sistema de marcadores de posición de FancyMenu, lo que permite que el contenido de texto sea dinámico y reaccione a distintos cambios en menús, mundos, jugadores, etc.

## Personalizar o desactivar Markdown

Si quieres personalizar los colores de los encabezados u otros aspectos relacionados con Markdown, simplemente haz **clic derecho** en el elemento Texto y selecciona **Markdown**. En el submenú contextual que se abre, verás muchas opciones para personalizar la apariencia y el comportamiento del analizador de Markdown.

Si no quieres que se analice Markdown en absoluto, lo que puede mejorar el rendimiento con contenido de texto largo, puedes desactivar Markdown por completo en el menú **Markdown** al hacer **clic derecho** en el elemento Texto.

## Desactivar el ajuste de línea

Si no quieres ajuste de línea, puedes desactivarlo haciendo **clic derecho** en el elemento Texto.

## Desactivar el desplazamiento

Los elementos de texto son desplazables de forma predeterminada y, si el elemento cree que el usuario necesita desplazarse para ver todo su contenido, mostrará sus barras de desplazamiento, que son unas barras pequeñas y grises en los lados derecho e inferior del elemento Texto (barras de desplazamiento vertical y horizontal).

Puedes desactivar estas barras desactivando **Desplazamiento** en el menú que se abre al hacer **clic derecho** en el elemento. Esto desactivará el desplazamiento en general, no solo las barras. Si prefieres que las barras sean invisibles, puedes establecer texturas personalizadas para las barras de desplazamiento haciendo clic derecho en el elemento. Solo tienes que asignar allí una textura completamente transparente.

## Formato de texto de componente sin procesar de Minecraft (componentes JSON serializados)

El elemento Texto NO es compatible con el formato de componentes sin procesar de Minecraft. Este formato solo es compatible con las etiquetas de los botones y los deslizadores.
