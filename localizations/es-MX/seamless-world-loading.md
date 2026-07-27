---
title: Carga fluida del mundo
description: Usa una vista reciente del mundo como el siguiente fondo de carga.
---

# Carga fluida del mundo

La Carga fluida del mundo usa una vista reciente de un mundo o servidor como el fondo de la siguiente pantalla de carga.

Actívalo desde [**Personalización -> Personalizaciones globales**](./global-customizations) -> **Carga fluida del mundo**.

# Cómo funciona

- FancyMenu captura periódicamente el cuadro actual mientras estás en un mundo o servidor rastreado.
- La captura más reciente se guarda cuando sales.
- Cada mundo y servidor tiene su propio nombre de archivo PNG con hash.
- FancyMenu precarga hasta cinco capturas recientes de mundos y cinco capturas recientes de servidores.
- No se muestra nada para un destino hasta que se haya guardado su primera captura.

Las capturas se almacenan en:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

Las capturas de pantalla pueden contener cualquier cosa visible en el mundo al momento de capturarse. Desactivar la Carga fluida del mundo detiene la captura y su uso, pero no elimina los archivos PNG existentes. Elimina las capturas no deseadas del directorio mientras el juego esté cerrado.
