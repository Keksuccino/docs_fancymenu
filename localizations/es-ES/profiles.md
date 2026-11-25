---
title: Perfiles
description: >-
  Guarda, cambia y comparte configuraciones completas de FancyMenu con perfiles,
  e instala plantillas de diseño de la comunidad.
sourceBlobSha: 52348efde29798073477e572b59a7630f96013ad
---

# Perfiles

Un perfil es una configuración completa de FancyMenu: diseños, recursos, variables, ajustes y todo lo demás que hay en `config/fancymenu/` (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#your-setup)). Con los perfiles, puedes tener varias configuraciones en una misma instancia de Minecraft, cambiar entre ellas en segundos y compartirlas en un único archivo.

<img width="800" alt="Creación del perfil My Menu Pack, importación del perfil Wind Chimes al soltar su archivo .fmp en la ventana Perfiles, eliminación de My Menu Pack y carga de Wind Chimes, que cambia la pantalla del título" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# La ventana Perfiles

Ábrela desde **barra de menús -> Personalización -> Perfiles**.

- La lista de la izquierda muestra todos los perfiles. El que está cargado aparece el primero y tiene la marca **Activo**. Todos los cambios que hagas en FancyMenu se guardan directamente en él.
- La parte derecha muestra el perfil seleccionado: su icono, título, versión, autores, número de diseños, tamaño, enlaces y descripción.
- Los botones que hay debajo de la lista y de los detalles muestran su nombre al pasar el cursor por encima. Al hacer clic derecho en un perfil también aparecen sus acciones.

Tu configuración se convierte automáticamente en tu primer perfil, llamado **Mi perfil**.

# Cargar un perfil

Selecciona un perfil y haz clic en **Cargar perfil**, haz doble clic en él o pulsa `Enter`.

FancyMenu se vuelve a cargar con el perfil, como cuando se inicia el juego. Se cierran todas las demás ventanas de FancyMenu y, si no estás en un mundo, se abre la pantalla del título.

> [!NOTE]
> Cargar un perfil nunca elimina nada. Primero se guarda tu configuración actual como un perfil independiente, así que siempre puedes volver a ella.

# Crear perfiles

- **Nuevo perfil** (el botón `+` debajo de la lista) crea un perfil vacío y abre sus detalles para que puedas ponerle nombre. Conserva tus preferencias de FancyMenu, como la escala de la interfaz y el tema, pero no incluye diseños ni otras personalizaciones. No se carga automáticamente.
- **Duplicar** copia el perfil seleccionado. Es una opción práctica para probar algo sin modificar el original.

# Editar los detalles de un perfil

Selecciona un perfil y haz clic en **Editar** para cambiar sus detalles:

- **Título**, lo único que necesita un perfil.
- **Versión** y **Autores**. Separa los nombres de varios autores con comas.
- **Descripción**, con [Markdown](/text-formatting#markdown), como texto en negrita, encabezados y listas.
- **Seguimiento de problemas**, un sitio web donde la gente puede informar de problemas con el perfil. Aparece como **Informar de un problema**.
- **Enlaces** a tu servidor de Discord, canal de YouTube, sitio web y otros. Haz clic en **Añadir enlace** y pega el enlace: FancyMenu detecta automáticamente la plataforma.
- Un icono: **Elegir icono** acepta una imagen PNG y **Eliminar icono** la quita. Las imágenes que no sean cuadradas se recortan por el centro.

No se guarda nada hasta que hagas clic en **Listo**.

# Compartir perfiles

> [!CAUTION]
> Los perfiles pueden ejecutar acciones, como abrir enlaces o ejecutar comandos. Impórtalos solo de fuentes en las que confíes.

## Exportar

Selecciona un perfil, haz clic en **Exportar** y elige dónde guardarlo. Se creará un archivo `.fmp` con todo el perfil, listo para compartir.

## Importar

Haz clic en **Importar**, debajo de la lista, y elige un archivo `.fmp`, o arrástralo y suéltalo en la ventana Perfiles.

- Los perfiles importados no se cargan automáticamente. Cárgalos como cualquier otro perfil.
- Si ya tienes el perfil, por ejemplo una versión anterior, elige **Reemplazar** o **Conservar ambos**. Si reemplazas el perfil cargado, el perfil importado se carga inmediatamente y se pierden los cambios que hayas hecho en el anterior.
- Los perfiles creados con una versión más reciente de FancyMenu muestran primero una advertencia, ya que algunas partes podrían no funcionar.
- Solo funcionan los archivos `.fmp` exportados por FancyMenu. Si tienes una carpeta normal, consulta la siguiente sección.

## Añadir carpetas de configuración

Algunas configuraciones vienen en una carpeta `fancymenu` normal (una copia de `config/fancymenu/` de otra persona) en lugar de en un archivo `.fmp`. Para añadirla como perfil:

1. Descomprímela si viene en un archivo `.zip`.
2. Mueve la carpeta a `<game-directory>/config/fancymenu/profiles/`. Crea la carpeta `profiles` si todavía no existe.
3. Abre la ventana Perfiles, o ciérrala y vuelve a abrirla. FancyMenu añadirá la carpeta a tus perfiles.

La carpeta debe contener directamente los archivos, como `customization/` y `options.txt`, no otra carpeta `fancymenu`. El perfil usará como título el nombre de la carpeta, a menos que esta incluya sus propios detalles de perfil. Puedes cambiarlo con **Editar**.

## Plantillas de diseño

El canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del [servidor de Discord Kekscord](https://discord.gg/rhayah27GC) (el servidor oficial de Discord de Keksuccino para obtener ayuda sobre los mods) contiene configuraciones completas creadas por la comunidad para FancyMenu y sus complementos, como SpiffyHUD y Drippy Loading Screen. Cada publicación incluye un enlace de descarga, ya sea a un archivo `.fmp` o a una carpeta `fancymenu`.

Las plantillas son complejas, así que no intentes combinarlas con tu propia configuración. Añádelas como perfiles independientes:

1. [Importa](#importing) el archivo `.fmp` o [añade la carpeta](#adding-setup-folders).
2. Selecciona la plantilla en la ventana Perfiles y haz clic en **Cargar perfil**.

Tu propia configuración seguirá disponible como perfil independiente, así que siempre podrás volver a ella.

La mayoría de las plantillas permiten editarlas y usarlas en tus propios proyectos, como modpacks, pero no todas. Consulta siempre la publicación de la plantilla para saber qué puedes hacer con ella.

# Eliminar perfiles

Selecciona un perfil y haz clic en **Eliminar**, o pulsa `Delete` (`Fn + Delete` en macOS). No se puede deshacer la eliminación, así que exporta el perfil antes si quieres tener una copia de seguridad.

No se puede eliminar el perfil cargado. Carga primero otro perfil.

# Dónde se guardan los perfiles

- El perfil cargado es el contenido de `<game-directory>/config/fancymenu/`.
- Los demás perfiles están en `<game-directory>/config/fancymenu/profiles/`, cada uno en su propia carpeta. **Abrir carpeta** abre la carpeta del perfil seleccionado.

`<game-directory>` es la carpeta de tu instancia, que puede ser distinta de `.minecraft`. Los datos de `<game-directory>/fancymenu_data/` no forman parte de los perfiles; consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#instance-data).

# Si algo sale mal

- **Algunos de sus archivos siguen en uso:** a menudo el propio juego sigue cargando algo, como el audio. Espera unos segundos e inténtalo de nuevo. Si sigue ocurriendo, cierra los programas que puedan estar usando los archivos, como el antivirus, un servicio de sincronización en la nube o una ventana del explorador de archivos.
- **El último cambio de perfil aún no ha terminado:** no se ha perdido nada. Vuelve a cargar un perfil o reinicia el juego para completar el cambio.
- **No hay suficiente espacio libre en el disco:** el mensaje indica cuánto espacio necesita el perfil. Libera espacio e inténtalo de nuevo.
- Las acciones de los perfiles se ejecutan de una en una. Exportar, importar y duplicar perfiles grandes puede tardar un poco, por lo que mientras se ejecutan aparece un botón **Cancelar**.
