---
title: Carga fluida de mundos
description: Usa una vista reciente de un mundo como el siguiente fondo de carga.
sourceBlobSha: 2b8e960b11ea70fca33b317a7c14815ce5844e13
---

# Carga fluida de mundos

La carga fluida de mundos usa una vista reciente de un mundo o servidor como fondo de la siguiente pantalla de carga.

Actívala en [**Personalización -> Personalizaciones globales**](/global-customizations) -> **Carga fluida de mundos**.

# Cómo funciona

- FancyMenu captura periódicamente el fotograma actual mientras estás en un mundo o servidor que se esté monitoreando.
- Al salir, se guarda la captura más reciente.
- Cada mundo y servidor tiene su propio archivo PNG con un nombre cifrado.
- FancyMenu precarga hasta cinco capturas recientes de mundos y cinco de servidores.
- No se muestra nada para un destino hasta que se guarde su primera captura.

Las capturas se guardan en:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Las capturas de pantalla pueden incluir cualquier cosa visible en el mundo al momento de capturarlas. Si desactivas la carga fluida de mundos, se detendrá la captura y el uso de imágenes, pero no se eliminarán los archivos PNG existentes. Cierra el juego y elimina del directorio las capturas que no quieras conservar.
