---
title: Paquetes de mods
description: Cómo incluir diseños en un paquete de mods.
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# FancyMenu en paquetes de mods

Incluir tu configuración de FancyMenu en un paquete de mods es muy fácil y solo requiere unos sencillos pasos.

> [!CAUTION]
> Las configuraciones de FancyMenu pueden ejecutar acciones. Impórtalas solo de fuentes de confianza.

> [!WARNING]
> Esta página es **SOLO** para configuraciones de FancyMenu creadas íntegramente con **FancyMenu v3 o posterior**. Si usas una configuración heredada (creada en la v2 y convertida a la v3), algunos pasos pueden ser diferentes.

# Añadir tu configuración al paquete de mods

La forma más fácil de trasladar tu configuración desde la instancia en la que la diseñaste hasta la instancia de tu paquete de mods es mediante un [perfil](/profiles):

1. En la instancia que contiene tu configuración, abre **barra de menú -> Personalización -> Perfiles**, selecciona tu configuración y [expórtala](/profiles#exporting) como archivo `.fmp`.
2. En la instancia de tu paquete de mods, abre la ventana Perfiles e [importa](/profiles#importing) el archivo `.fmp`, por ejemplo, arrastrándolo a la ventana.
3. Selecciona el perfil importado y haz clic en **Cargar perfil**.

La configuración de FancyMenu que tenía la instancia del paquete de mods antes de esto no se pierde. Sigue disponible como perfil independiente, así que siempre puedes volver a ella.

# Incluir la configuración en tu paquete de mods

El perfil cargado constituye el contenido de `<game-directory>/config/fancymenu/`, así que se incluirá en la carpeta `config` de tu paquete de mods, igual que las configuraciones de los demás mods.

Todos los demás perfiles de la instancia se guardan en `<game-directory>/config/fancymenu/profiles/`. Elimina los perfiles que no quieras incluir para los jugadores antes de exportar el paquete de mods, o excluye la carpeta `profiles` de la exportación.

> [!CAUTION]
> Ten en cuenta que las antiguas configuraciones heredadas creadas en FancyMenu v2 (incluso si se convirtieron a la v3) permitían guardar recursos de diseño fuera de la carpeta `<game-directory>/config/fancymenu/assets/` de FancyMenu. Los perfiles solo contienen la carpeta de configuración de FancyMenu, así que, en ese caso, también tendrás que asegurarte de incluir todos tus recursos en el paquete de mods.

## Restablecer las casillas antes de exportar

Los [elementos de casilla](/elements#checkbox) recuerdan si están marcados en `config/fancymenu/checkbox_states.json`. Por tanto, las casillas que marques durante las pruebas también aparecerán marcadas para tus jugadores.

Para que los jugadores empiecen desde cero, cierra el juego y elimina `checkbox_states.json` antes de exportar el paquete de mods o el perfil. Si no existe el archivo, todas las casillas aparecerán desmarcadas. Las casillas que usan una [variable](/variables) guardan su estado en la propia variable.

Lo mismo se aplica a los cambios realizados mediante acciones durante las pruebas, como el volumen de los [elementos de vídeo](/video): consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#your-setup) para encontrar esos archivos.

## Cómo encontrar la carpeta de la instancia

La carpeta de la instancia es la carpeta principal de tu ordenador donde se guardan todos los archivos de una configuración concreta de Minecraft. Lanzadores como CurseForge y Modrinth las llaman «instancias» o «perfiles» (no los confundas con los perfiles de FancyMenu).

### Si usas la aplicación de CurseForge

1. Abre CurseForge.
2. Busca tu perfil o instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige «Abrir carpeta». Se abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si usas la aplicación de Modrinth

1. Abre la aplicación de Modrinth.
2. Busca tu perfil o instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige «Abrir carpeta». Se abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Si usas otros lanzadores

Busca una opción similar a «Abrir carpeta», «Abrir carpeta de la instancia» o «Ver archivos» para tu configuración concreta de Minecraft.

# Desactivar la barra de menú y las teclas de acceso rápido

Seguramente no quieras que la barra de menú de FancyMenu siga visible en tu paquete de mods, así que deberías desactivarla. Sin embargo, como los usuarios todavía podrían pulsar la tecla de acceso rápido para volver a mostrarla, vamos a aplicar una medida un poco más *contundente*.

Ve a `<game-directory>/config/fancymenu/options.txt` y abre el archivo con un editor de texto.

Ahora cambia `modpack_mode` a `true` y guarda el archivo.
Esto desactivará por completo todas las superposiciones y teclas de acceso rápido.

Para poder volver a editar tus diseños, cambia de nuevo la opción de configuración a `false`.

# Desactivar la pantalla de bienvenida

En la mayoría de los casos no hará falta, pero, si todavía no has cerrado la pantalla de bienvenida (la que te indica que leas la documentación), asegúrate de establecer `show_welcome_screen` en `false` en `<game-directory>/config/fancymenu/options.txt`.

La pantalla solo aparece una vez y se desactiva al hacer clic en el botón **Abrir documentación**, así que, por lo general, no tendrás que hacerlo manualmente.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
