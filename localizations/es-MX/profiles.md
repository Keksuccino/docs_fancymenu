---
title: Perfiles
description: >-
  Cómo guardar, cambiar y compartir configuraciones completas de FancyMenu
  mediante perfiles.
sourceBlobSha: d0a07901ee271d802c7bc07ea6d787575f48d51c
---
# Perfiles

Un perfil es una configuración completa de FancyMenu: todos los diseños, recursos, variables y ajustes de FancyMenu de una instancia. Los perfiles te permiten mantener varias configuraciones en una misma instancia de Minecraft, cambiar entre ellas en cuestión de segundos y compartirlas con otras personas como un solo archivo.

<img width="800" alt="perfiles" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Abrir la ventana de Perfiles

Abre la ventana de Perfiles mediante **barra de menú -> Personalización -> Perfiles**.

La lista de la izquierda muestra todos tus perfiles y el lado derecho muestra los detalles del perfil seleccionado. El perfil cargado está marcado como **Activo**. Todos los cambios que hagas en FancyMenu se guardan directamente en el perfil cargado.

Tu configuración existente se convierte automáticamente en tu primer perfil, llamado **Mi perfil**.

> [!TIP]
> Haz clic derecho en un perfil de la lista para ver todas las acciones disponibles para él.

# Cambiar de perfil

Selecciona un perfil y haz clic en **Cargar perfil**, o haz doble clic en él. FancyMenu se vuelve a cargar con la configuración seleccionada.

> [!NOTE]
> Cambiar de perfil nunca elimina nada. Tu configuración actual se guarda como un perfil independiente antes de cargar la otra, así que siempre puedes volver a cambiar a ella.

# Crear perfiles

- **Nuevo perfil** (el botón **+** debajo de la lista) crea un perfil vacío y abre su editor. Los perfiles vacíos conservan tus preferencias personales de FancyMenu, como la escala de la interfaz y el tema.
- **Duplicar** crea una copia del perfil seleccionado, lo cual resulta útil para probar algo sin modificar el original.

# Editar perfiles

Haz clic en **Editar** para cambiar el título, la versión, los autores, la descripción, el ícono, el rastreador de problemas y los enlaces de un perfil. La descripción admite Markdown y el ícono puede ser cualquier imagen PNG.

No se guarda nada hasta que hagas clic en **Listo**.

# Compartir perfiles

> [!CAUTION]
> Los perfiles pueden ejecutar acciones. Impórtalos únicamente de fuentes en las que confíes.

## Exportar

Selecciona un perfil, haz clic en **Exportar** y elige dónde guardarlo. Esto crea un archivo `.fmp` que contiene el perfil completo.

## Importar

Haz clic en **Importar** debajo de la lista y selecciona un archivo `.fmp`, o simplemente arrastra y suelta el archivo en la ventana de Perfiles.

- Los perfiles importados no se cargan automáticamente. Cárgalos como cualquier otro perfil.
- Si ya tienes el mismo perfil (por ejemplo, una versión anterior), puedes elegir **Reemplazarlo** o **Conservar ambos**. Si reemplazas el perfil cargado, la versión importada se carga de inmediato.
- Los perfiles creados con una versión más reciente de FancyMenu muestran una advertencia, ya que algunas partes podrían no funcionar.

## Agregar carpetas de configuraciones

Algunas configuraciones vienen como una carpeta `fancymenu` normal en lugar de un archivo `.fmp`. Para agregar una carpeta de este tipo como perfil, cámbiale el nombre por el nombre de perfil que quieras, muévela a `<game-directory>/config/fancymenu/profiles/` (crea la carpeta `profiles` si aún no existe) y abre la ventana de Perfiles. FancyMenu la agregará automáticamente a tus perfiles.

# Eliminar perfiles

Selecciona un perfil y haz clic en **Eliminar**. La eliminación no se puede deshacer, así que exporta el perfil primero si quieres conservar una copia de seguridad.

No se puede eliminar el perfil cargado. Carga otro perfil primero.

# Dónde se almacenan los perfiles

- El perfil cargado es el contenido de `<game-directory>/config/fancymenu/`, como cualquier configuración de FancyMenu.
- Todos los demás perfiles se almacenan en `<game-directory>/config/fancymenu/profiles/`. Haz clic en **Abrir carpeta** para abrir la carpeta de un perfil.

`<game-directory>` es la carpeta de la instancia activa, que puede ser distinta de `.minecraft`. El estado de ejecución que FancyMenu conserva fuera de `config/fancymenu/` no forma parte de los perfiles. Consulta [Ubicaciones de almacenamiento de datos](./data-storage-locations#persistent-runtime-state).
