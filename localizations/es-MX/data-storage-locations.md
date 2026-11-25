---
title: Ubicaciones de almacenamiento de datos
description: >-
  Dónde guarda FancyMenu los diseños, recursos, ajustes y todo lo demás, y qué
  archivos pertenecen a los perfiles.
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# Ubicaciones de almacenamiento de datos

FancyMenu guarda todo en dos carpetas del directorio de tu juego. Este es el directorio de la instancia de tu launcher, que puede ser distinto de `.minecraft`.

- `config/fancymenu/` contiene tu configuración: diseños, recursos, variables, ajustes y más. Es el [perfil](/profiles) cargado, por eso los modpacks incluyen esta carpeta.
- `fancymenu_data/` contiene datos de esta instancia del juego, como las posiciones de Dragger y las descargas. No cambia entre perfiles.

**Barra de menú -> Herramientas -> Abrir directorio de FancyMenu** abre `config/fancymenu/`.

La mayoría de los archivos y carpetas aparecen solo cuando usas la función correspondiente. Cierra el juego antes de modificar o eliminar archivos.

> [!TIP]
> Para compartir estas carpetas entre instancias, puedes moverlas a otro lugar y dejar un enlace simbólico (una unión en Windows) en su ubicación original.

# Tu configuración

Todo lo que está en `<game-directory>/config/fancymenu/` pertenece al [perfil](/profiles) cargado.

| Qué | Ubicación |
| --- | --- |
| Diseños, en archivos `.txt`, también en subcarpetas | `customization/` |
| [Recursos locales](/resources#local-resources), como imágenes y sonidos | `assets/` |
| Ajustes de FancyMenu | `options.txt` |
| Pantallas con **Personalización de la pantalla actual** activada | `customizablemenus.txt` |
| [GUI personalizadas](/custom-guis) y las pantallas que reemplazan | `custom_gui_screens.txt` |
| [Variables](/variables) | `user_variables.db` |
| [Listeners](/listeners) | `listener_instances.txt` |
| [Programadores](/schedulers) | `scheduler_instances.txt` |
| [Panoramas](/panoramas) | `panoramas/` |
| [Presentaciones](/slideshows) | `slideshows/` |
| [Localizaciones personalizadas](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Temas de la interfaz de FancyMenu (**Barra de menú -> Personalización -> Ajustes -> Interfaz de FancyMenu -> Tema de la interfaz**) | `ui_themes/` |
| Estados de los [elementos de casilla](/elements#checkbox) que no usan una variable | `checkbox_states.json` |
| Estado del volumen y de la pausa que las acciones asignaron a los [elementos de video](/video) | `video_element_controller_metas.json` |
| Volumen que las acciones asignaron a los [elementos de audio](/elements#audio) | `audio_element_controller_metas.json` |
| Estado de activación que las acciones asignaron a los [animadores de elementos](/element-animator) | `animation_controller_states.json` |
| Pantallas con **Exponer el contenido del área desplazable de la pantalla actual** activado (consulta [Personalizar pantallas desplazables](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| Listeners del servidor de [FM Data](/fm-data) | `fmdata_server_listeners.json` |
| Datos de bienvenida de [FM Data](/fm-data) | `fmdata_welcome_data.json` |
| Posición, tamaño y visibilidad de los widgets del editor de diseños | `layout_editor/widgets/` |
| Nombre, ícono y detalles del perfil cargado | `profile.json` y `profile_icon.png` |
| Todos los demás [perfiles](/profiles#where-profiles-are-stored) | `profiles/` |
| Qué actualizaciones de archivos antiguos ya realizó FancyMenu | `legacy_checklist.txt` |

`customizablemenus.txt` enumera las pantallas por el nombre de su clase de Java. En este archivo se omiten los [identificadores de pantalla](/screen-identifiers) cortos, como `title_screen`.

En un servidor dedicado, FancyMenu solo usa los dos archivos de [FM Data](/fm-data), dentro de la carpeta `config/fancymenu/` del servidor.

# Datos de la instancia

Todo lo que está en `<game-directory>/fancymenu_data/`. No forma parte de los perfiles, así que se conserva al cambiar de uno a otro.

| Qué | Ubicación |
| --- | --- |
| Posiciones de los [elementos Dragger](/dragger) | `dragger_metas.json` |
| El último mundo o servidor, para la acción **Entrar/Unirse al último mundo/servidor** y el marcador de posición **Último mundo o servidor** | `last_world.fmdata` |
| Capturas de pantalla de [Carga fluida de mundos](/seamless-world-loading) | `seamless_world_loading/` |
| Guardados de [Buddy](/decoration-overlays#buddy), dos archivos por cada superposición de Buddy | `buddy/` |
| Archivos de [Exportar para IA](/export-for-ai) | `ai_exports/` |
| Tus acciones favoritas en el selector de acciones | `action_favorites.json` |
| El volumen de las vistas previas de audio y video en los selectores de archivos | `browser_audio_settings.json` y `browser_video_settings.json` |
| El fotograma que muestra un [fondo de video](/video) mientras está en pausa | `video_thumbnails/` |
| FFmpeg, que FancyMenu descarga para el [creador de AFMA](/animations#fma-and-afma) | `ffmpeg_cache/` |
| Una nota que indica que FancyMenu ya configuró la [**Escala predeterminada de la interfaz**](/global-customizations) | `default_scale_set.fm` |
| Archivos temporales, que se eliminan al iniciar el juego | `fancymenu_temp/` |

- FancyMenu configura la **Escala predeterminada de la interfaz** una sola vez. Elimina `default_scale_set.fm` para que vuelva a configurar la escala en el siguiente inicio.
- Las capturas de pantalla de Carga fluida de mundos muestran todo lo que había en pantalla dentro del mundo. Elimínalas con el juego cerrado si no quieres conservarlas.

# Archivos de versiones anteriores

Las versiones anteriores de FancyMenu guardaban algunos archivos en otros lugares. FancyMenu los traslada a su nueva ubicación la próxima vez que inicias el juego:

- `checkbox_states.json` y `normalized_scroll_screens.json`, desde el directorio del juego a `config/fancymenu/`.
- `dragger_metas.json`, desde `config/fancymenu/` a `fancymenu_data/`.
