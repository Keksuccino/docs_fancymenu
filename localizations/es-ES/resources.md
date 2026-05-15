---
title: Recursos
description: >-
  Cómo funcionan los recursos en FancyMenu. Cubre ubicaciones de recursos,
  recursos locales y recursos web.
---

# Recursos

El sistema de recursos de FancyMenu te permite usar recursos del propio cargador de recursos de Minecraft (**paquetes de recursos**), recursos **locales** (archivos del sistema del cliente) y fuentes de la **web** (archivos almacenados en línea).

Casi todas las entradas de recursos, ya sean imágenes, audio, vídeo o texto, se establecen mediante el selector de recursos de FancyMenu. Hay algunas excepciones, como cuando se define una ruta de origen para un marcador de posición o una acción, pero en la mayoría de los casos los recursos se establecen a través de la misma interfaz del selector de recursos.

Cuando defines una entrada de recurso mediante la interfaz del selector de recursos, básicamente eliges una llamada "fuente de recurso" (así es como las llama FancyMenu), que puede ser una ruta, un enlace o una ubicación de recurso, según el tipo de fuente.

FancyMenu 3.9.0 añade un explorador de recursos de Minecraft al selector de recursos. Esto te permite navegar por los recursos cargados mediante paquetes de recursos como si fueran un directorio, en lugar de escribir manualmente cada ubicación de recurso.

# Recursos de Minecraft (paquetes de recursos)

Minecraft utiliza las llamadas "ubicaciones de recurso" para "apuntar" a un recurso.

Las ubicaciones de recurso escritas como texto constan de dos partes, separadas por dos puntos (`:`).
La primera parte es el **espacio de nombres** y la segunda ruta es el resto de la **ruta hasta el recurso**, incluido el nombre del recurso con la extensión del archivo.

El **espacio de nombres** de una ubicación de recurso es siempre solo el **directorio/carpeta de nivel superior** de la ruta completa al recurso.

Supongamos que cargas un paquete de recursos con un recurso llamado `image.png` que está almacenado en `/assets/custom_resources/images/image.png`.
En este caso, el **espacio de nombres** de la ubicación de recurso sería `custom_resources`, porque `/assets/` es simplemente desde donde Minecraft carga todos sus recursos, así que `custom_resources` es el **directorio de nivel superior** del recurso.
Esto significa que `images/image.png` es el **resto de la ruta** hasta el recurso.

Por tanto, la ubicación de recurso correcta para el recurso `image.png` sería:
`custom_resources:images/image.png`

> **Dato curioso**: Como Minecraft almacena la mayoría de sus recursos en `/assets/minecraft/`, el **espacio de nombres** de la mayoría de los recursos de Minecraft es `minecraft`.
{.is-info}

# Recursos locales

La forma más sencilla de cargar recursos es simplemente usar archivos locales almacenados en el cliente (y, en la mayoría de los casos, incluidos con los modpacks).

FancyMenu solo permite cargar recursos locales almacenados en `/config/fancymenu/assets/`, así que asegúrate de guardar allí todos tus recursos.

Esto también hace que sea muy fácil [incluir recursos locales con tus modpacks](./modpacks), ya que la mayoría de los sistemas de modpacks (CurseForge, Modrinth, etc.) admiten incluir carpetas de configuración del mod por defecto.

# Recursos web

Cuando necesitas cambiar recursos de forma dinámica sin tener que actualizar tu modpack, los recursos **web** son la mejor opción.

Un recurso web básicamente es solo la **URL** de un archivo almacenado en un servidor, por ejemplo `https://example-domain.net/image.png`.

Asegúrate de usar siempre **URL DIRECTAS**, es decir, URL que terminan con el **nombre de archivo y la extensión** del recurso, igual que en el ejemplo anterior.
Usar URL no directas perjudica el rendimiento y es más probable que falle.

# Marcadores de posición en fuentes de recursos

Es posible usar los marcadores de posición de FancyMenu en las fuentes de recursos, como la ruta de una fuente local, la URL de una fuente web o la ubicación de recurso de un recurso de Minecraft.

Esto hace posible actualizar las fuentes dinámicamente, por ejemplo cambiando la fuente de imagen del fondo de un menú al establecer una variable de FancyMenu, para mostrar un fondo diferente según el valor de la variable.

Puedes editar manualmente la fuente haciendo clic en el botón **Abrir en el editor** a la derecha del campo de entrada de la fuente de recurso.

> Ten en cuenta que esto solo se aplica a las entradas de recursos que usan la interfaz normal del selector de recursos. Es posible que *algunas* entradas de recursos que no usan el selector **NO** admitan marcadores de posición o no se actualicen de forma dinámica cuando cambie el marcador de posición.
{.is-warning}
