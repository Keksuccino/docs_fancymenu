---
title: Modpacks
description: Cómo incluir diseños en un modpack.
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# FancyMenu en modpacks

Incluir tu configuración de FancyMenu en un modpack es muy fácil y solo requiere unos sencillos pasos.

> [!CAUTION]
> Las configuraciones de FancyMenu pueden ejecutar acciones. Impórtalas únicamente de fuentes de confianza.

> [!WARNING]
> Esta página es **ÚNICAMENTE** para configuraciones de FancyMenu creadas completamente en **FancyMenu v3 o superior**. Si utilizas una configuración antigua (creada en la v2 y convertida a la v3), algunos pasos podrían ser diferentes.

# Introducir tu configuración en el modpack

La forma más sencilla de trasladar tu configuración desde la instancia en la que la diseñaste a la instancia de tu modpack es mediante un [perfil](./profiles):

1. En la instancia que contiene tu configuración, abre **barra de menú -> Personalización -> Perfiles**, selecciona tu configuración y [expórtala](./profiles#exporting) como archivo `.fmp`.
2. En la instancia de tu modpack, abre la ventana de Perfiles e [importa](./profiles#importing) el archivo `.fmp`, por ejemplo, arrastrándolo a la ventana.
3. Selecciona el perfil importado y haz clic en **Cargar perfil**.

La configuración de FancyMenu que tenía la instancia del modpack no se pierde. Permanece disponible como su propio perfil, así que siempre puedes volver a ella.

# Incluir la configuración en tu modpack

El perfil cargado es el contenido de `<game-directory>/config/fancymenu/`, por lo que se incluirá en la carpeta `config` de tu modpack, al igual que las configuraciones de otros mods.

El resto de perfiles de la instancia se almacenan en `<game-directory>/config/fancymenu/profiles/`. Elimina los perfiles que no deban recibir los jugadores antes de exportar tu modpack o excluye la carpeta `profiles` de la exportación del modpack.

> [!CAUTION]
> Ten en cuenta que las configuraciones antiguas creadas en FancyMenu v2 (incluso si se convirtieron a la v3) permitían almacenar recursos de los diseños fuera de la carpeta `<game-directory>/config/fancymenu/assets/` de FancyMenu. Los perfiles solo contienen la carpeta de configuración de FancyMenu, por lo que, en ese caso, también tendrás que asegurarte de incluir todos tus recursos en el modpack.

## Cómo encontrar la carpeta de la instancia

La carpeta de la instancia es la carpeta principal de tu ordenador donde se almacenan todos los archivos de una configuración específica de Minecraft. Los lanzadores como CurseForge y Modrinth las denominan «instancias» o «perfiles» (no deben confundirse con los perfiles de FancyMenu).

### Si utilizas la aplicación de CurseForge

1. Abre CurseForge.
2. Busca tu perfil o instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Selecciona «Abrir carpeta». Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Captura_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si utilizas la aplicación de Modrinth

1. Abre la aplicación de Modrinth.
2. Busca tu perfil o instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Selecciona «Abrir carpeta». Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Captura_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para otros lanzadores

Busca una opción similar a «Abrir carpeta», «Abrir carpeta de la instancia» o «Ver archivos» para tu configuración específica de Minecraft.

# Desactivar la barra de menú y las teclas de acceso rápido

Seguramente no querrás mantener visible la barra de menú de FancyMenu en tu modpack, así que deberías desactivarla. Sin embargo, como los usuarios aún podrían pulsar la tecla de acceso rápido para volver a mostrarla, hagamos algo un poco más *contundente*.

Ve a `<game-directory>/config/fancymenu/options.txt` y abre el archivo con un editor de texto.

Ahora establece `modpack_mode` en `true` y guarda el archivo.
Esto desactivará por completo todas las superposiciones y teclas de acceso rápido.

Para poder volver a editar tus diseños, cambia de nuevo la opción de configuración a `false`.

# Desactivar la pantalla de bienvenida

En la mayoría de los casos no debería ser necesario, pero si todavía no has cerrado la pantalla de bienvenida (la pantalla que te indica que leas la documentación), asegúrate de establecer `show_welcome_screen` en `false` en `<game-directory>/config/fancymenu/options.txt`.

La pantalla solo se muestra una vez y se desactiva al hacer clic en el botón **Abrir documentación**, por lo que, de nuevo, normalmente no debería ser necesario hacerlo manualmente.

<br>
<img width="630" alt="Captura_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
