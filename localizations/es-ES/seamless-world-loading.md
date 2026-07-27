---
title: Carga fluida del mundo
description: Usa una vista reciente del mundo como el siguiente fondo de carga.
---

# Carga fluida del mundo

La Carga fluida del mundo usa una vista reciente de un mundo o servidor como fondo de la siguiente pantalla de carga.

Actívala desde [**Personalización -> Personalizaciones globales**](./global-customizations) -> **Carga fluida del mundo**.

# Cómo funciona

- FancyMenu captura periódicamente el fotograma actual mientras estás en un mundo o servidor supervisado.
- La última captura se guarda cuando sales.
- Cada mundo y servidor tiene su propio nombre de archivo PNG con hash.
- FancyMenu precarga hasta cinco capturas recientes de mundos y cinco capturas recientes de servidores.
- No se muestra nada para un destino hasta que se haya guardado su primera captura.

Las capturas se almacenan en:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Las capturas pueden contener cualquier cosa visible en el mundo en el momento en que se hicieron. Desactivar la Carga fluida del mundo detiene la captura y su uso, pero no elimina los archivos PNG existentes. Elimina las capturas que no quieras del directorio mientras el juego esté cerrado.
