---
title: Ubicaciones de almacenamiento de datos
description: >-
  Dónde FancyMenu almacena los diseños, recursos, configuración y el estado
  persistente en tiempo de ejecución.
---

# Ubicaciones de almacenamiento de datos

`<game-directory>` significa la carpeta activa de la instancia de Minecraft, que puede ser distinta de `.minecraft`.

Los directorios y archivos normalmente solo se crean después de que la función relacionada se inicializa o se usa. Cierra Minecraft antes de editar manualmente los archivos de estado generados y conserva una copia de seguridad al migrar o restablecer datos.

# Diseños, recursos y configuración

Algunas entradas son configuración o recursos creados por el autor; otras son estado que FancyMenu actualiza en tiempo de ejecución.

| Sistema / Función | Archivo o directorio |
| --- | --- |
| Pantallas personalizables | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [GUIs personalizadas](./custom-guis) y reglas de sobrescritura de pantallas | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| Diseños | `<game-directory>/config/fancymenu/customization/` |
| [Recursos locales](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [Archivos de localización personalizados](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [Panoramas](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [Presentaciones de diapositivas](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [Variables de FancyMenu](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| Metadatos del controlador del elemento [Video](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| Metadatos del controlador del elemento [Audio](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| Detectores del servidor de [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| Datos de bienvenida de [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| Instancias de [Listeners](./listeners) y scripts de acción | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Programadores](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` es administrado por el interruptor **Personalización de pantalla actual** y almacena identificadores concretos de clases de pantalla. No agregues identificadores de [Universal Layout](./universal-layouts); FancyMenu los ignora al cargar el archivo.

En un servidor dedicado, los dos archivos de FM Data están relativos a la raíz del juego de ese servidor. Los demás recursos y configuraciones pertenecientes al cliente viven en la instancia de cada jugador.

# Estado persistente en tiempo de ejecución

FancyMenu guarda estado adicional generado por instancia fuera de `config/fancymenu/`. Incluye estas rutas en una copia de seguridad solo cuando quieras conservar el estado de usuario o de ejecución relacionado; no son definiciones de diseño ni recursos de origen.

| Sistema / Función | Archivo o directorio |
| --- | --- |
| Estados de [Checkbox](./elements#checkbox) que no son de variables | `<game-directory>/checkbox_states.json` |
| Posiciones y metadatos del elemento [Dragger](./dragger) | `<game-directory>/fancymenu_data/dragger_metas.json` |
| Estado del último mundo | `<game-directory>/fancymenu_data/last_world.fmdata` |
| Estado de [Seamless World Loading](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Guardados de la mascota Buddy y de nivelación | `<game-directory>/fancymenu_data/buddy/` |
| Posiciones y visibilidad de los widgets del editor de diseño | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| Marcador de inicialización del tamaño de GUI predeterminado | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy guarda el estado de la mascota y el estado de nivelación/logros en archivos JSON separados dentro de su directorio. Cada instancia de superposición de Buddy usa su propio par de archivos.

Los archivos de los widgets del editor de diseño almacenan la posición, tamaño, visibilidad, estado expandido y el lado de ajuste de cada widget. Eliminar `default_scale_set.fm` hace que FancyMenu trate la escala predeterminada de GUI configurada como si aún no se hubiera aplicado en el siguiente inicio.
