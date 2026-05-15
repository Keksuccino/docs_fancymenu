---
title: Modpacks
description: Cómo incluir diseños en un modpack.
---

# FancyMenu en Modpacks

Incluir tu configuración de FancyMenu en un modpack es muy fácil y solo toma unos pasos sencillos.

> Esta página es **SOLO** para configuraciones de FancyMenu hechas por completo en **FancyMenu v3+**, así que si usas una configuración antigua (hecha en v2 y convertida a v3), algunos pasos podrían ser diferentes.
{.is-warning}

# Incluir la Configuración de FancyMenu en Tu Modpack

Lo principal que necesitas hacer es copiar una carpeta especial que FancyMenu usa para guardar todos tus diseños.

## Lo que necesitarás encontrar

1. **Tu carpeta de "instancia de Minecraft":** Esta es la carpeta principal en tu computadora donde se almacenan todos los archivos de una configuración específica de Minecraft (como aquella en la que diseñaste tus menús). Launchers como CurseForge y Modrinth llaman a esto "instancias" o "perfiles".
2. **La carpeta `config`:** Dentro de la carpeta de tu instancia de Minecraft, normalmente hay una carpeta llamada `config`. Aquí es donde muchos mods guardan sus ajustes.
3. **La carpeta `fancymenu`:** Dentro de esa carpeta `config`, FancyMenu crea su propia carpeta llamada `fancymenu`. ¡Esa es la carpeta de oro que necesitamos!

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

### Para otros launchers

Busca una opción similar como "Open Folder", "Open Instance Folder" o "View Files" para tu configuración específica de Minecraft.

## Copiar la Configuración de FancyMenu

1. Ve a la carpeta `config` de tu instancia del MODPACK (la que quieres que reciba tu configuración).
2. Si ya existe una carpeta `fancymenu` dentro, ELÍMINAla.
3. Abre la carpeta `config` de la instancia ORIGEN (la que tiene la configuración que quieres usar).
4. Copia la carpeta `fancymenu` dentro de la carpeta `config` de tu instancia ORIGEN a la carpeta `config` de tu instancia del MODPACK.
5. Listo. Eso es todo. Reinicia tu instancia del modpack y deberías ver que la configuración se carga.

> Ten en cuenta que las configuraciones antiguas hechas en FancyMenu v2 (incluso si se convirtieron a v3) permitían guardar recursos de los diseños fuera de la carpeta `/config/fancymenu/assets/` de FancyMenu, así que en ese caso debes asegurarte de incluir también todos tus recursos en el modpack.
{.is-danger}

# Desactivar la Barra de Menú y las Teclas Rápidas

Seguramente no quieres mantener visible la barra de menú de FancyMenu en tu modpack, así que deberías desactivarla. Pero como la gente todavía puede presionar la tecla rápida para volver a mostrarla, hagamos algo un poco más *agresivo*.

Ve a `/config/fancymenu/options.txt` y abre el archivo en un editor de texto.

Ahora configura `modpack_mode` en `true` y guarda el archivo.
Esto desactivará por completo todos los overlays y teclas rápidas.

Para poder editar tus diseños otra vez, vuelve a configurar la opción de la configuración en `false`.

# Desactivar la Pantalla de Bienvenida

Esto no debería ser necesario en la mayoría de los casos, pero si todavía no cerraste la pantalla de bienvenida (la pantalla que te indica que leas la documentación), asegúrate de poner `show_welcome_screen` en `false` en `/config/fancymenu/options.txt`.

La pantalla solo se muestra una vez y se desactiva sola al hacer clic en el botón **Open Documentation**, así que de nuevo, hacerlo manualmente no debería ser necesario en la mayoría de los casos.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
