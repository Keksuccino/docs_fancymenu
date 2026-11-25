---
title: Ubicaciones de almacenamiento de datos
description: >-
  Dónde guarda FancyMenu los diseños, recursos, ajustes y todo lo demás, y qué
  archivos pertenecen a los perfiles.
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# Ubicaciones de almacenamiento de datos

FancyMenu guarda todo en dos carpetas del directorio del juego. Se trata de la carpeta de la instancia de tu launcher, que puede ser distinta de `.minecraft`.

- `config/fancymenu/` contiene tu configuración: diseños, recursos, variables, ajustes y mucho más. Es el [perfil](/profiles) cargado, por lo que los modpacks incluyen esta carpeta.
- `fancymenu_data/` contiene datos de esta instancia del juego, como las posiciones de Dragger y las descargas. Es la misma para todos los perfiles.

**barra de menú -> Herramientas -> Abrir directorio de FancyMenu** abre `config/fancymenu/`.

La mayoría de los archivos y carpetas solo aparecen cuando utilizas la función correspondiente. Cierra el juego antes de modificar o eliminar archivos de estas carpetas.

> [!TIP]
> Para compartir estas carpetas entre instancias, puedes moverlas a otro sitio y dejar en su lugar un enlace simbólico (una unión en Windows).

# Tu configuración

Todo lo que hay en `<game-directory>/config/fancymenu/`. Todo pertenece al [perfil](/profiles) cargado.

| Qué | Ubicación |
| --- | --- |
| Diseños, en archivos `.txt`, también en subcarpetas | `customization/` |
| [Recursos locales](/resources#local-resources), como imágenes y sonidos | `assets/` |
| Ajustes de FancyMenu | `options.txt` |
| Pantallas con **Personalización de la pantalla actual** activada | `customizablemenus.txt` |
| [Interfaces personalizadas](/custom-guis) y las pantallas que sustituyen | `custom_gui_screens.txt` |
| [Variables](/variables) | `user_variables.db` |
| [Listeners](/listeners) | `listener_instances.txt` |
| [Programadores](/schedulers) | `scheduler_instances.txt` |
| [Panoramas](/panoramas) | `panoramas/` |
| [Presentaciones](/slideshows) | `slideshows/` |
| [Localizaciones personalizadas](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Temas de la propia interfaz de FancyMenu (**barra de menú -> Personalización -> Ajustes -> Interfaz de FancyMenu -> Tema de la interfaz**) | `ui_themes/` |
| Estados de los [elementos de casilla](/elements#checkbox) que no utilizan una variable | `checkbox_states.json` |
| Volumen y estado de pausa que las acciones asignaron a los [elementos de vídeo](/video) | `video_element_controller_metas.json` |
| Volumen que las acciones asignaron a los [elementos de audio](/elements#audio) | `audio_element_controller_metas.json` |
| Estado de activación y desactivación que las acciones asignaron a los [animadores de elementos](/element-animator) | `animation_controller_states.json` |
| Pantallas con **Mostrar el contenido del área desplazable de la pantalla actual** activado (consulta [Personalizar pantallas desplazables](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| Listeners del servidor de [FM Data](/fm-data) | `fmdata_server_listeners.json` |
| Datos de bienvenida de [FM Data](/fm-data) | `fmdata_welcome_data.json` |
| Posición, tamaño y visibilidad de los widgets del editor de diseños | `layout_editor/widgets/` |
| Nombre, icono y detalles del perfil cargado | `profile.json` y `profile_icon.png` |
| Todos los demás [perfiles](/profiles#where-profiles-are-stored) | `profiles/` |
| Actualizaciones de archivos antiguos que FancyMenu ya ha aplicado | `legacy_checklist.txt` |

`customizablemenus.txt` enumera las pantallas por el nombre de su clase Java. En este archivo se omiten los [identificadores de pantalla](/screen-identifiers) cortos, como `title_screen`.

En un servidor dedicado, FancyMenu solo utiliza los dos archivos de [FM Data](/fm-data), en la carpeta `config/fancymenu/` del servidor.

# Datos de la instancia

Todo lo que hay en `<game-directory>/fancymenu_data/`. No forma parte de los perfiles, así que se conserva al cambiar de uno a otro.

| Qué | Ubicación |
| --- | --- |
| Posiciones de los [elementos Dragger](/dragger) | `dragger_metas.json` |
| El último mundo o servidor, para la acción **Entrar/Unirse al último mundo/servidor** y el marcador de posición **Último mundo o servidor** | `last_world.fmdata` |
| Capturas de pantalla de [Carga continua del mundo](/seamless-world-loading) | `seamless_world_loading/` |
| Guardados de [Buddy](/decoration-overlays#buddy), dos archivos por cada superposición de Buddy | `buddy/` |
| Archivos de [Exportar para IA](/export-for-ai) | `ai_exports/` |
| Tus acciones favoritas en el selector de acciones | `action_favorites.json` |
| El volumen de las vistas previas de audio y vídeo en los selectores de archivos | `browser_audio_settings.json` y `browser_video_settings.json` |
| El fotograma que muestra un [fondo de vídeo](/video) cuando está en pausa | `video_thumbnails/` |
| FFmpeg, que FancyMenu descarga para el [creador de AFMA](/animations#fma-and-afma) | `ffmpeg_cache/` |
| Una nota que indica que FancyMenu ya ha establecido la [**Escala de interfaz predeterminada**](/global-customizations) | `default_scale_set.fm` |
| Archivos temporales, que se eliminan cada vez que se inicia el juego | `fancymenu_temp/` |

- FancyMenu establece la **Escala de interfaz predeterminada** una sola vez. Elimina `default_scale_set.fm` para que vuelva a establecerla en el siguiente inicio.
- Las capturas de Carga continua del mundo muestran todo lo que había en pantalla dentro del mundo. Elimínalas con el juego cerrado si no quieres conservarlas.

# Archivos de versiones anteriores

Las versiones anteriores de FancyMenu guardaban algunos archivos en otras ubicaciones. FancyMenu los traslada al iniciar el juego la próxima vez:

- `checkbox_states.json` y `normalized_scroll_screens.json`, desde el propio directorio del juego a `config/fancymenu/`.
- `dragger_metas.json`, desde `config/fancymenu/` a `fancymenu_data/`.
