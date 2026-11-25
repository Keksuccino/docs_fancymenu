---
title: Carga fluida del mundo
description: Usa una vista reciente del mundo como siguiente fondo de carga.
sourceBlobSha: 2b8e960b11ea70fca33b317a7c14815ce5844e13
---

# Carga fluida del mundo

La carga fluida del mundo usa una vista reciente de un mundo o servidor como siguiente fondo de la pantalla de carga.

Actívala en [**Personalización -> Personalizaciones globales**](/global-customizations) -> **Carga fluida del mundo**.

# Cómo funciona

- FancyMenu captura periódicamente el fotograma actual mientras estás en un mundo o servidor seguido.
- Al salir, se guarda la captura más reciente.
- Cada mundo y servidor tiene su propio nombre de archivo PNG cifrado mediante hash.
- FancyMenu precarga hasta cinco capturas recientes de mundos y cinco de servidores.
- No se muestra nada para un destino hasta que se haya guardado su primera captura.

Las capturas se guardan en:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Las capturas de pantalla pueden contener cualquier elemento visible en el mundo en el momento de la captura. Al desactivar la carga fluida del mundo, se detienen las capturas y su uso, pero no se eliminan los archivos PNG existentes. Para eliminar las capturas que no quieras, bórralas del directorio con el juego cerrado.
