---
title: Perfiles
description: >-
  Guarda, cambia y comparte configuraciones completas de FancyMenu con perfiles,
  e instala plantillas de diseño de la comunidad.
sourceBlobSha: 52348efde29798073477e572b59a7630f96013ad
---

# Perfiles

Un perfil es una configuración completa de FancyMenu: diseños, recursos, variables, ajustes y todo lo demás que hay en `config/fancymenu/` (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#your-setup)). Con los perfiles, puedes tener varias configuraciones en una misma instancia de Minecraft, cambiar entre ellas en segundos y compartirlas como un solo archivo.

<img width="800" alt="Creación del perfil My Menu Pack, importación del perfil Wind Chimes al arrastrar su archivo .fmp a la ventana Perfiles, eliminación de My Menu Pack y carga de Wind Chimes, que cambia la pantalla de título" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# La ventana Perfiles

Ábrela desde **barra de menú -> Personalización -> Perfiles**.

- La lista de la izquierda muestra todos los perfiles. El que está cargado aparece primero y tiene la marca **Activo**. Cada cambio que hagas en FancyMenu se guarda directamente en ese perfil.
- El lado derecho muestra el perfil seleccionado: su ícono, título, versión, autores, cantidad de diseños, tamaño, enlaces y descripción.
- Los botones debajo de la lista y de los detalles muestran su nombre al pasar el cursor sobre ellos. También puedes hacer clic derecho en un perfil para ver sus acciones.

Tu configuración se convierte automáticamente en tu primer perfil, llamado **My Profile**.

# Cargar un perfil

Selecciona un perfil y haz clic en **Cargar perfil**, haz doble clic en él o presiona `Enter`.

FancyMenu se vuelve a cargar con el perfil, como cuando inicias el juego. Se cierran todas las demás ventanas de FancyMenu y, si no estás dentro de un mundo, se abre la pantalla de título.

> [!NOTE]
> Cargar un perfil nunca elimina nada. Primero se guarda tu configuración actual como otro perfil, así que siempre puedes volver a ella.

# Crear perfiles

- **Nuevo perfil** (el botón `+` debajo de la lista) crea un perfil vacío y abre sus detalles de inmediato para que puedas ponerle un nombre. Conserva tus preferencias de FancyMenu, como la escala de la interfaz y el tema, pero no tiene diseños ni otras personalizaciones. No se carga automáticamente.
- **Duplicar** copia el perfil seleccionado, lo que resulta útil para probar algo sin modificar el original.

# Editar los detalles de un perfil

Selecciona un perfil y haz clic en **Editar** para cambiar sus detalles:

- **Título**, lo único que necesita un perfil.
- **Versión** y **Autores**. Separa varios autores con comas.
- **Descripción**, con [Markdown](/text-formatting#markdown), como texto en negritas, encabezados y listas.
- **Seguimiento de problemas**, un sitio web donde la gente puede reportar problemas con el perfil. Se muestra como **Reportar un problema**.
- **Enlaces** a tu servidor de Discord, canal de YouTube, sitio web y más. Haz clic en **Agregar enlace** y pega el enlace: FancyMenu detecta la plataforma automáticamente.
- Un ícono: **Elegir ícono** acepta una imagen PNG y **Quitar ícono** la elimina. Las imágenes que no sean cuadradas se recortan desde el centro.

Los cambios no se guardan hasta que hagas clic en **Listo**.

# Compartir perfiles

> [!CAUTION]
> Los perfiles pueden ejecutar acciones, como abrir enlaces o ejecutar comandos. Impórtalos solo de fuentes en las que confíes.

## Exportar

Selecciona un perfil, haz clic en **Exportar** y elige dónde guardarlo. Se crea un archivo `.fmp` con el perfil completo, listo para compartir.

## Importar

Haz clic en **Importar**, debajo de la lista, y selecciona un archivo `.fmp`, o arrastra el archivo a la ventana Perfiles.

- Los perfiles importados no se cargan automáticamente. Cárgalos como cualquier otro perfil.
- Si ya tienes el perfil, por ejemplo, una versión anterior, elige **Reemplazar** o **Conservar ambos**. Si reemplazas el perfil cargado, se carga el perfil importado de inmediato y se pierden los cambios que hayas hecho en el anterior.
- Los perfiles creados con una versión más reciente de FancyMenu muestran una advertencia primero, porque es posible que algunas partes no funcionen.
- Solo funcionan los archivos `.fmp` exportados por FancyMenu. Si tienes una carpeta normal, consulta la siguiente sección.

## Agregar carpetas de configuraciones

Algunas configuraciones vienen como una carpeta `fancymenu` normal (una copia del `config/fancymenu/` de alguien) en lugar de un archivo `.fmp`. Para agregarla como perfil:

1. Descomprímela si viene como archivo `.zip`.
2. Mueve la carpeta a `<game-directory>/config/fancymenu/profiles/`. Crea la carpeta `profiles` si aún no existe.
3. Abre la ventana Perfiles o ciérrala y vuelve a abrirla. FancyMenu agregará la carpeta a tus perfiles.

La carpeta debe contener directamente los archivos, como `customization/` y `options.txt`, y no otra carpeta `fancymenu`. El perfil toma como título el nombre de la carpeta, a menos que esta incluya sus propios detalles. Puedes cambiarlo con **Editar**.

## Plantillas de diseño

El canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) del [servidor de Discord Kekscord](https://discord.gg/rhayah27GC) (el servidor oficial de Discord de Keksuccino para recibir ayuda sobre mods) tiene configuraciones completas creadas por la comunidad para FancyMenu y sus complementos, como SpiffyHUD y Drippy Loading Screen. Cada publicación incluye un enlace de descarga, ya sea a un archivo `.fmp` o a una carpeta `fancymenu`.

Las plantillas son complejas, así que no intentes combinarlas con tu propia configuración. Agrégalas como perfiles independientes:

1. [Importa](#importing) el archivo `.fmp` o [agrega la carpeta](#adding-setup-folders).
2. Selecciona la plantilla en la ventana Perfiles y haz clic en **Cargar perfil**.

Tu propia configuración seguirá disponible como un perfil independiente, así que siempre puedes volver a ella.

La mayoría de las plantillas permiten editarlas y usarlas en tus propios proyectos, como modpacks, pero no todas. Revisa siempre la publicación de la plantilla para saber qué puedes hacer con ella.

# Eliminar perfiles

Selecciona un perfil y haz clic en **Eliminar**, o presiona `Delete` (`Fn + Delete` en macOS). No se puede deshacer la eliminación, así que exporta el perfil primero si quieres tener una copia de seguridad.

No se puede eliminar el perfil cargado. Primero carga otro perfil.

# Dónde se guardan los perfiles

- El perfil cargado es el contenido de `<game-directory>/config/fancymenu/`.
- Todos los demás perfiles están en `<game-directory>/config/fancymenu/profiles/`, cada uno en su propia carpeta. **Abrir carpeta** abre la carpeta del perfil seleccionado.

`<game-directory>` es la carpeta de tu instancia, que puede ser distinta de `.minecraft`. Los datos de `<game-directory>/fancymenu_data/` no forman parte de los perfiles; consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#instance-data).

# Si algo sale mal

- **Algunos de sus archivos todavía están en uso:** a menudo, el juego sigue cargando algo, como el audio. Espera unos segundos e inténtalo de nuevo. Si sigue pasando, cierra los programas que podrían estar usando los archivos, como el antivirus, la sincronización en la nube o una ventana del explorador de archivos.
- **El último cambio de perfil aún no termina:** no se perdió nada. Vuelve a cargar un perfil o reinicia el juego para completar el cambio.
- **No hay suficiente espacio libre en el disco:** el mensaje indica cuánto espacio necesita el perfil. Libera espacio e inténtalo de nuevo.
- Las acciones de perfil se ejecutan de una en una. Exportar, importar y duplicar perfiles grandes puede tardar un poco, así que durante el proceso aparece el botón **Cancelar**.
