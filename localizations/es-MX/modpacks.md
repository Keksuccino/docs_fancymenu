---
title: Modpacks
description: Cómo incluir diseños en un modpack.
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# FancyMenu en modpacks

Incluir tu configuración de FancyMenu en un modpack es muy fácil y solo requiere unos cuantos pasos.

> [!CAUTION]
> Las configuraciones de FancyMenu pueden ejecutar acciones. Impórtalas solo desde fuentes confiables.

> [!WARNING]
> Esta página es **SOLO** para configuraciones de FancyMenu creadas completamente en **FancyMenu v3+**. Si usas una configuración antigua (creada en v2 y convertida a v3), algunos pasos podrían ser diferentes.

# Cómo agregar tu configuración al modpack

La forma más sencilla de pasar tu configuración desde la instancia donde la diseñaste a la instancia de tu modpack es mediante un [perfil](/profiles):

1. En la instancia que contiene tu configuración, abre **barra de menú -> Personalización -> Perfiles**, selecciona tu configuración y [expórtala](/profiles#exporting) como archivo `.fmp`.
2. En la instancia de tu modpack, abre la ventana Perfiles e [importa](/profiles#importing) el archivo `.fmp`; por ejemplo, arrastrándolo a la ventana.
3. Selecciona el perfil importado y haz clic en **Cargar perfil**.

La configuración de FancyMenu que tenía la instancia del modpack no se pierde. Sigue disponible en su propio perfil, así que siempre puedes volver a ella.

# Cómo incluir la configuración en tu modpack

El perfil cargado corresponde al contenido de `<game-directory>/config/fancymenu/`, así que se incluye con la carpeta `config` de tu modpack, como las configuraciones de otros mods.

Todos los demás perfiles de la instancia se guardan en `<game-directory>/config/fancymenu/profiles/`. Elimina los perfiles que no quieras incluir para los jugadores antes de exportar tu modpack, o excluye la carpeta `profiles` de la exportación.

> [!CAUTION]
> Ten en cuenta que las configuraciones antiguas creadas en FancyMenu v2 (incluso si se convirtieron a v3) permitían guardar recursos de diseño fuera de la carpeta `<game-directory>/config/fancymenu/assets/` de FancyMenu. Los perfiles solo incluyen la carpeta de configuración de FancyMenu, así que en ese caso debes asegurarte de incluir también todos tus recursos en el modpack.

## Cómo restablecer las casillas antes de exportar

Los [elementos de casilla](/elements#checkbox) recuerdan si están marcados en `config/fancymenu/checkbox_states.json`. Así que las casillas que marcaste durante las pruebas también aparecerían marcadas para tus jugadores.

Para que los jugadores empiecen desde cero, cierra el juego y elimina `checkbox_states.json` antes de exportar tu modpack o perfil. Si no existe el archivo, todas las casillas aparecerán desmarcadas. Las casillas que usan una [variable](/variables) guardan su estado en la variable.

Lo mismo aplica a los cambios hechos por acciones durante las pruebas, como el volumen de los [elementos de video](/video): consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations#your-setup) para ver dónde están esos archivos.

## Cómo encontrar la carpeta de la instancia

La carpeta de la instancia es la carpeta principal de tu computadora donde se almacenan todos los archivos de una configuración específica de Minecraft. Los launchers, como CurseForge y Modrinth, las llaman «instancias» o «perfiles» (no los confundas con los perfiles de FancyMenu).

### Si usas la aplicación de CurseForge

1. Abre CurseForge.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige «Abrir carpeta». Se abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si usas la aplicación de Modrinth

1. Abre la aplicación de Modrinth.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige «Abrir carpeta». Se abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para otros launchers

Busca una opción similar a «Abrir carpeta», «Abrir carpeta de la instancia» o «Ver archivos» para tu configuración de Minecraft.

# Cómo desactivar la barra de menú y las teclas de acceso rápido

Seguro que no quieres que la barra de menú de FancyMenu siga visible en tu modpack, así que deberías desactivarla. Pero, como la gente aún podría presionar la tecla de acceso rápido para volver a mostrarla, hagamos algo un poco más *drástico*.

Ve a `<game-directory>/config/fancymenu/options.txt` y abre el archivo en un editor de texto.

Ahora cambia `modpack_mode` a `true` y guarda el archivo.
Esto desactivará por completo todas las superposiciones y teclas de acceso rápido.

Para volver a editar tus diseños, cambia la opción de configuración a `false`.

# Cómo desactivar la pantalla de bienvenida

En la mayoría de los casos no será necesario, pero si todavía no cerraste la pantalla de bienvenida (la que te indica que leas la documentación), asegúrate de cambiar `show_welcome_screen` a `false` en `<game-directory>/config/fancymenu/options.txt`.

La pantalla solo aparece una vez y se desactiva al hacer clic en el botón **Abrir documentación**, así que, en la mayoría de los casos, no debería ser necesario hacerlo manualmente.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
