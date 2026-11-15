---
title: Modpacks
description: Cómo incluir diseños en un modpack.
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# FancyMenu en modpacks

Incluir tu configuración de FancyMenu en un modpack es muy fácil y solo requiere unos cuantos pasos.

> [!CAUTION]
> Las configuraciones de FancyMenu pueden ejecutar acciones. Impórtalas únicamente de fuentes confiables.

> [!WARNING]
> Esta página es **ÚNICAMENTE** para configuraciones de FancyMenu creadas completamente en **FancyMenu v3 o posterior**. Si usas una configuración antigua (creada en la v2 y convertida a la v3), algunos pasos podrían ser diferentes.

# Llevar tu configuración al modpack

La forma más fácil de mover tu configuración desde la instancia en la que la diseñaste a la instancia de tu modpack es mediante un [perfil](./profiles):

1. En la instancia que contiene tu configuración, abre **barra de menú -> Personalización -> Perfiles**, selecciona tu configuración y [expórtala](./profiles#exporting) como un archivo `.fmp`.
2. En la instancia de tu modpack, abre la ventana de Perfiles y [importa](./profiles#importing) el archivo `.fmp`, por ejemplo, arrastrándolo a la ventana.
3. Selecciona el perfil importado y haz clic en **Cargar perfil**.

La configuración de FancyMenu que tenía la instancia del modpack no se pierde. Permanece disponible como un perfil independiente, así que siempre puedes volver a ella.

# Incluir la configuración en tu modpack

El perfil cargado es el contenido de `<game-directory>/config/fancymenu/`, por lo que se incluye en la carpeta `config` de tu modpack, igual que las configuraciones de otros mods.

Todos los demás perfiles de la instancia se almacenan en `<game-directory>/config/fancymenu/profiles/`. Elimina los perfiles que los jugadores no deban recibir antes de exportar tu modpack o excluye la carpeta `profiles` de la exportación del modpack.

> [!CAUTION]
> Ten en cuenta que las configuraciones antiguas creadas en FancyMenu v2 (incluso si se convirtieron a la v3) permitían almacenar recursos de diseños fuera de la carpeta `<game-directory>/config/fancymenu/assets/` de FancyMenu. Los perfiles solo contienen la carpeta de configuración de FancyMenu, así que, en ese caso, debes asegurarte de incluir también todos tus recursos en el modpack.

## Cómo encontrar la carpeta de la instancia

La carpeta de la instancia es la carpeta principal de tu computadora donde se almacenan todos los archivos de una configuración específica de Minecraft. Los launchers como CurseForge y Modrinth las llaman "instancias" o "perfiles" (no deben confundirse con los perfiles de FancyMenu).

### Si usas la aplicación de CurseForge

1. Abre CurseForge.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Selecciona "Abrir carpeta". Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si usas la aplicación de Modrinth

1. Abre la aplicación de Modrinth.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Selecciona "Abrir carpeta". Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para otros launchers

Busca una opción similar a "Abrir carpeta", "Abrir carpeta de la instancia" o "Ver archivos" para tu configuración específica de Minecraft.

# Desactivar la barra de menú y las teclas de acceso rápido

Seguramente no querrás que la barra de menú de FancyMenu permanezca visible en tu modpack, así que deberías desactivarla. Sin embargo, como los usuarios todavía pueden presionar la tecla de acceso rápido para volver a mostrarla, hagamos algo un poco más *agresivo*.

Ve a `<game-directory>/config/fancymenu/options.txt` y abre el archivo en un editor de texto.

Ahora establece `modpack_mode` en `true` y guarda el archivo.
Esto desactivará por completo todas las superposiciones y teclas de acceso rápido.

Para poder editar tus diseños nuevamente, vuelve a establecer esta opción de configuración en `false`.

# Desactivar la pantalla de bienvenida

En la mayoría de los casos esto no será necesario, pero si todavía no has cerrado la pantalla de bienvenida (la pantalla que te indica que leas la documentación), asegúrate de establecer `show_welcome_screen` en `false` en `<game-directory>/config/fancymenu/options.txt`.

La pantalla solo aparece una vez y se desactiva al hacer clic en el botón **Abrir documentación**, así que, nuevamente, en la mayoría de los casos no debería ser necesario hacerlo manualmente.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
