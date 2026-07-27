---
title: Modpacks
description: Cómo incluir diseños en un modpack.
---

# FancyMenu en Modpacks

Incluir tu configuración de FancyMenu en un modpack es muy fácil y solo requiere unos cuantos pasos sencillos.

> [!CAUTION]
> Las configuraciones de FancyMenu pueden ejecutar acciones. Impórtalas solo desde fuentes en las que confíes.

> [!WARNING]
> Esta página es **SOLO** para configuraciones de FancyMenu creadas completamente en **FancyMenu v3+**. Si usas una configuración heredada (hecha en v2 y convertida a v3), algunos pasos podrían ser diferentes.

# Incluir la configuración de FancyMenu en tu modpack

Lo principal que necesitas hacer es copiar una carpeta especial que FancyMenu usa para guardar todos tus diseños.

## Lo que necesitas encontrar

1. **Tu carpeta de "Instancia de Minecraft":** Esta es la carpeta principal en tu computadora donde se guardan todos los archivos de una configuración específica de Minecraft (como aquella en la que diseñaste tus menús). Lanzadores como CurseForge y Modrinth la llaman "instancias" o "perfiles".
2. **La carpeta `config`:** Dentro de la carpeta de tu instancia de Minecraft, normalmente hay una carpeta llamada `config`. Ahí es donde muchos mods guardan su configuración.
3. **La carpeta `fancymenu`:** Dentro de esa carpeta `config`, FancyMenu crea su propia carpeta llamada `fancymenu`. ¡Esa es la carpeta dorada que necesitamos!

## Cómo encontrar la ubicación de guardado de la instancia

### Si usas la app de CurseForge

1. Abre CurseForge.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige "Open Folder". Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si usas la app de Modrinth

1. Abre la app de Modrinth.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige "Open Folder". Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para otros lanzadores

Busca una opción similar como "Open Folder", "Open Instance Folder" o "View Files" para tu configuración específica de Minecraft.

## Copiar la configuración de FancyMenu

1. Ve a la carpeta `config` de tu instancia del MODPACK (la que quieres usar como destino para copiar tu configuración).
2. Si hay una carpeta `fancymenu` dentro, ELIMÍNALA.
3. Abre la carpeta `config` de la instancia FUENTE (la que quieres usar como origen de la configuración).
4. Copia la carpeta `fancymenu` dentro de la carpeta `config` de tu instancia FUENTE a la carpeta `config` de tu instancia del MODPACK.
5. Listo. Eso es todo. Reinicia tu instancia del modpack ahora y deberías ver que la configuración se carga.

> [!CAUTION]
> Ten en cuenta que las configuraciones heredadas antiguas hechas en FancyMenu v2 (incluso si se convirtieron a v3) permitían almacenar recursos de diseño fuera de la carpeta `<game-directory>/config/fancymenu/assets/` de FancyMenu, así que en ese caso debes asegurarte de incluir también todos tus recursos en el modpack.

# Deshabilitar la barra de menú y las teclas rápidas

Seguramente no quieres mantener visible la barra de menú de FancyMenu en tu modpack, así que deberías deshabilitarla. Pero como la gente todavía puede presionar la tecla rápida para volver a hacerla visible, hagamos algo un poco más *agresivo*.

Ve a `<game-directory>/config/fancymenu/options.txt` y abre el archivo en un editor de texto.

Ahora establece `modpack_mode` en `true` y guarda el archivo.
Esto deshabilitará por completo todos los overlays y teclas rápidas.

Para poder editar tus diseños otra vez, vuelve a cambiar la opción de configuración a `false`.

# Deshabilitar la pantalla de bienvenida

Esto no debería ser necesario en la mayoría de los casos, pero si todavía no has cerrado la pantalla de bienvenida (la pantalla que te indica que leas la documentación), asegúrate de establecer `show_welcome_screen` en `false` en `<game-directory>/config/fancymenu/options.txt`.

La pantalla solo aparece una vez y se desactiva sola al hacer clic en el botón **Open Documentation**, así que, de nuevo, hacerlo manualmente no debería ser necesario en la mayoría de los casos.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
