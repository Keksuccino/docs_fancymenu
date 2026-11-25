---
title: Recursos
description: >-
  Cómo funcionan los recursos en FancyMenu. Incluye las ubicaciones de recursos,
  los recursos locales y los recursos web.
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# Recursos

Los campos de recursos pueden cargar contenido desde:

- **Minecraft:** una ubicación de recurso proporcionada por Minecraft o por un paquete de recursos.
- **Local:** un archivo de la instancia activa del juego.
- **Web:** una URL directa al archivo.

La mayoría de los campos de imagen, audio, vídeo y texto usan el mismo selector de recursos. El selector incluye un explorador para el contenido de Minecraft y de los paquetes de recursos.

# Recursos de Minecraft (paquetes de recursos)

Las ubicaciones de recursos usan el formato `namespace:path`. El espacio de nombres es el directorio situado justo debajo de `assets`, y la ruta incluye todo lo que hay debajo de ese espacio de nombres.

Por ejemplo, imagina una imagen de un paquete de recursos almacenada en `/assets/custom_resources/images/image.png`.
Su ubicación de recurso es `custom_resources:images/image.png`.

> [!NOTE]
> Los recursos integrados de Minecraft suelen usar el espacio de nombres `minecraft`.

# Recursos locales

Guarda los recursos locales en `<game-directory>/config/fancymenu/assets/`. `<game-directory>` es la carpeta de la instancia activa, que puede ser distinta de `.minecraft`.

Los campos de recursos pueden mostrar la misma ruta como `/config/fancymenu/assets/example.png`. En esos campos, la `/` inicial sigue indicando `<game-directory>`; no es una ruta desde la raíz del sistema de archivos.

Estos archivos se pueden [incluir en un modpack](/modpacks) mediante su carpeta de configuración.

Para consultar un mapa completo de las rutas de diseño, recursos, configuración y estado generado de FancyMenu, visita [Ubicaciones de almacenamiento de datos](/data-storage-locations).

# Recursos web

Usa una URL directa al archivo, por ejemplo, `https://example-domain.net/image.png`. Las páginas y los enlaces de redirección son más lentos y tienen más probabilidades de fallar que las URL directas que terminan con el nombre y la extensión del recurso.

# Marcadores de posición en las fuentes de recursos

Los campos de recursos que usan un selector pueden incluir [marcadores de posición](/placeholders) en rutas locales, URL y ubicaciones de recursos de Minecraft. Selecciona **Abrir en el editor**, junto al campo de origen, para editarlo directamente.

> [!WARNING]
> Es posible que las entradas de recursos que no usan el selector habitual no admitan marcadores de posición ni actualizaciones de origen en tiempo real.
