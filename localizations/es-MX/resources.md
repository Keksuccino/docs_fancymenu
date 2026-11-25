---
title: Recursos
description: >-
  Cómo funcionan los recursos en FancyMenu. Incluye las ubicaciones de recursos,
  los recursos locales y los recursos web.
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# Recursos

Los campos de recursos pueden cargar contenido desde:

- **Minecraft:** una ubicación de recurso proporcionada por Minecraft o un paquete de recursos.
- **Local:** un archivo en la instancia activa del juego.
- **Web:** la URL directa de un archivo.

La mayoría de los campos de imagen, audio, video y texto usan el mismo selector de recursos. El selector incluye un explorador para el contenido de Minecraft y de los paquetes de recursos.

# Recursos de Minecraft (paquetes de recursos)

Las ubicaciones de recursos usan el formato `namespace:path`. El espacio de nombres es el directorio que está inmediatamente debajo de `assets`, y la ruta es todo lo que está debajo de ese espacio de nombres.

Por ejemplo, considera una imagen de un paquete de recursos guardada en `/assets/custom_resources/images/image.png`.
Su ubicación de recurso es `custom_resources:images/image.png`.

> [!NOTE]
> Normalmente, los recursos integrados de Minecraft usan el espacio de nombres `minecraft`.

# Recursos locales

Guarda los recursos locales en `<game-directory>/config/fancymenu/assets/`. `<game-directory>` es la carpeta de la instancia activa, que puede ser distinta de `.minecraft`.

Los campos de recursos pueden mostrar la misma ruta como `/config/fancymenu/assets/example.png`. En esos campos, la `/` inicial sigue representando `<game-directory>`; no es una ruta desde la raíz del sistema de archivos.

Estos archivos se pueden [incluir con un modpack](/modpacks) a través de su carpeta de configuración.

Para ver un mapa completo de las rutas de FancyMenu relacionadas con la estructura, los recursos, la configuración y los datos de estado generados, consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations).

# Recursos web

Usa la URL directa del archivo, por ejemplo, `https://example-domain.net/image.png`. Las páginas y los enlaces que redirigen son más lentos y tienen más probabilidades de fallar que las URL directas que terminan con el nombre y la extensión del recurso.

# Marcadores de posición en las fuentes de recursos

Los campos de recursos que usan el selector pueden incluir [marcadores de posición](/placeholders) en rutas locales, URL y ubicaciones de recursos de Minecraft. Selecciona **Abrir en el editor**, junto al campo de fuente, para editarlo directamente.

> [!WARNING]
> Es posible que las entradas de recursos que no usan el selector habitual no admitan marcadores de posición ni actualizaciones de la fuente en tiempo real.
