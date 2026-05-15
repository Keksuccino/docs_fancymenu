---
title: Recursos
description: >-
  Cómo funcionan los recursos en FancyMenu. Cubre ubicaciones de recursos,
  recursos locales y recursos web.
---

# Recursos

El sistema de recursos de FancyMenu te permite usar recursos del propio cargador de recursos de Minecraft (**Paquetes de recursos**), recursos **locales** (archivos del sistema del cliente) y recursos de la **web** (archivos almacenados en línea).

Casi todas las entradas de recursos, ya sean imágenes, audio, video o texto, se configuran mediante el selector de recursos de FancyMenu. Hay algunas excepciones, como cuando se establece una ruta de origen para un placeholder o una acción, pero en la mayoría de los casos los recursos se configuran con la misma interfaz del selector de recursos.

Cuando configuras una entrada de recurso mediante la interfaz del selector de recursos, básicamente eliges una llamada "fuente de recurso" (así les llama FancyMenu), que puede ser una ruta, un enlace o una ubicación de recurso, dependiendo del tipo de fuente.

FancyMenu 3.9.0 agrega un explorador de recursos de Minecraft al selector de recursos. Esto te permite explorar los recursos cargados mediante paquetes de recursos como si fueran un directorio, en lugar de escribir manualmente cada ubicación de recurso.

# Recursos de Minecraft (Paquetes de recursos)

Minecraft usa las llamadas "ubicaciones de recursos" para "apuntar" a un recurso.

Las ubicaciones de recursos escritas como texto constan de dos partes, separadas por dos puntos (`:`).
La primera parte es el **espacio de nombres** y la segunda parte es el resto de la **ruta al recurso**, incluido el nombre del recurso con la extensión del archivo.

El **espacio de nombres** de una ubicación de recurso siempre es solo el **directorio/carpeta de nivel superior** de la ruta completa al recurso.

Así que digamos que cargas un paquete de recursos con un recurso llamado `image.png` que está almacenado en `/assets/custom_resources/images/image.png`.
En este caso, el **espacio de nombres** de la ubicación del recurso sería `custom_resources`, porque `/assets/` es solo la ubicación desde donde Minecraft carga todos sus recursos, así que `custom_resources` es el **directorio de nivel superior** del recurso.
Esto significa que `images/image.png` es el **resto de la ruta** al recurso.

Por lo tanto, la ubicación de recurso correcta para el recurso `image.png` sería:
`custom_resources:images/image.png`

> **Dato curioso**: Como Minecraft tiene la mayoría de sus recursos almacenados en `/assets/minecraft/`, el **espacio de nombres** de la mayoría de los recursos de Minecraft es `minecraft`.
{.is-info}

# Recursos locales

La forma más sencilla de cargar recursos es simplemente usar archivos locales almacenados en el cliente (y, en la mayoría de los casos, incluidos con los modpacks).

FancyMenu solo permite cargar recursos locales almacenados en `/config/fancymenu/assets/`, así que asegúrate de guardar ahí todos tus recursos.

Esto también hace que sea muy fácil [incluir recursos locales con tus modpacks](./modpacks), ya que la mayoría de los sistemas de modpacks (CurseForge, Modrinth, etc.) admiten por defecto incluir carpetas de configuración de mods.

# Recursos web

Cuando necesitas cambiar recursos dinámicamente sin tener que actualizar tu modpack, los recursos **web** son la mejor opción.

Un recurso web es básicamente solo la **URL** de un archivo almacenado en un servidor, así que por ejemplo `https://example-domain.net/image.png`.

Asegúrate de usar siempre **URLs DIRECTAS**, es decir, URLs que terminen con el **nombre de archivo y la extensión** del recurso, tal como en el ejemplo anterior.
Usar URLs no directas afecta el rendimiento y es más probable que falle.

# Placeholders en fuentes de recursos

Es posible usar los placeholders de FancyMenu en las fuentes de recursos, como la ruta a una fuente local, la URL de una fuente web o la ubicación del recurso de Minecraft.

Esto permite actualizar fuentes dinámicamente, como cambiar la fuente de imagen del fondo de un menú al establecer una variable de FancyMenu, para mostrar un fondo diferente según el valor de la variable.

Puedes editar manualmente la fuente haciendo clic en el botón **Abrir en el editor** a la derecha del campo de entrada de la fuente del recurso.

> Ten en cuenta que esto solo aplica a las entradas de recursos que usan la interfaz normal del selector de recursos. Es posible que *algunas* entradas de recursos que no usan el selector **NO** admitan placeholders o no se actualicen dinámicamente cuando cambie el placeholder.
{.is-warning}
