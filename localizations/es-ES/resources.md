---
title: Recursos
description: >-
  Cómo funcionan los recursos en FancyMenu. Cubre ubicaciones de recursos,
  recursos locales y recursos web.
---

# Recursos

Los campos de recursos pueden cargar contenido desde:

- **Minecraft:** una ubicación de recurso proporcionada por Minecraft o por un paquete de recursos.
- **Local:** un archivo en la instancia de juego activa.
- **Web:** una URL directa de un archivo.

La mayoría de los campos de imagen, audio, vídeo y texto usan el mismo selector de recursos. El selector incluye un navegador para contenido de Minecraft y de paquetes de recursos.

# Recursos de Minecraft (Paquetes de recursos)

Las ubicaciones de recurso usan `namespace:path`. El namespace es el directorio inmediatamente inferior a `assets`, y la ruta es todo lo que cuelga por debajo de ese namespace.

Por ejemplo, considera una imagen de un paquete de recursos almacenada en `/assets/custom_resources/images/image.png`.
Su ubicación de recurso es `custom_resources:images/image.png`.

> [!NOTE]
> Los recursos integrados de Minecraft normalmente usan el namespace `minecraft`.

# Recursos locales

Guarda los recursos locales en `<game-directory>/config/fancymenu/assets/`. `<game-directory>` es la carpeta de la instancia activa, que puede ser distinta de `.minecraft`.

Los campos de recurso pueden mostrar la misma ruta como `/config/fancymenu/assets/example.png`. En esos campos, la `/` inicial sigue significando `<game-directory>`; no es una ruta raíz del sistema de archivos.

Estos archivos se pueden [incluir con un modpack](./modpacks) a través de su carpeta de configuración.

Para ver un mapa completo de las rutas de diseño, recursos, configuración y estado generado de FancyMenu, consulta [Ubicaciones de almacenamiento de datos](./data-storage-locations).

# Recursos web

Usa una URL directa al archivo, por ejemplo `https://example-domain.net/image.png`. Las páginas y los enlaces con redirecciones son más lentos y tienen más probabilidades de fallar que las URL directas que terminan en el nombre y la extensión del recurso.

# Marcadores de posición en las fuentes de recursos

Los campos de recursos con selector pueden usar [marcadores de posición](./placeholders) en rutas locales, URL y ubicaciones de recurso de Minecraft. Selecciona **Abrir en el editor** junto al campo de origen para editarlo directamente.

> [!WARNING]
> Las entradas de recursos que no usan el selector normal pueden no admitir marcadores de posición ni actualizaciones en vivo de la fuente.
