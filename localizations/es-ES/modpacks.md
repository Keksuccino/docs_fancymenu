---
title: Modpacks
description: Cómo incluir diseños en un modpack.
---

# FancyMenu en Modpacks

Incluir tu configuración de FancyMenu en un modpack es muy fácil y solo requiere unos pocos pasos sencillos.

> Esta página es **SOLO** para configuraciones de FancyMenu creadas completamente en **FancyMenu v3+**, así que si usas una configuración heredada (creada en v2 y convertida a v3), algunos pasos podrían ser diferentes.
{.is-warning}

# Incluir la configuración de FancyMenu en tu modpack

Lo principal que necesitas hacer es copiar una carpeta especial que FancyMenu usa para guardar todos tus diseños.

## Lo que tendrás que encontrar

1. **Tu carpeta de "instancia de Minecraft":** es la carpeta principal de tu ordenador donde se guardan todos los archivos de una configuración concreta de Minecraft (como la que usaste para diseñar tus menús). Lanzadores como CurseForge y Modrinth las llaman "instancias" o "perfiles".
2. **La carpeta `config`:** dentro de la carpeta de tu instancia de Minecraft, suele haber una carpeta llamada `config`. Aquí es donde muchos mods guardan sus ajustes.
3. **La carpeta `fancymenu`:** dentro de esa carpeta `config`, FancyMenu crea su propia carpeta llamada `fancymenu`. ¡Esa es la carpeta de oro que necesitamos!

## Cómo encontrar la ubicación de guardado de la instancia

### Si usas la aplicación CurseForge

1. Abre CurseForge.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige "Open Folder". Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Si usas la aplicación Modrinth

1. Abre la aplicación Modrinth.
2. Busca tu perfil/instancia de Minecraft en la lista y ábrelo.
3. Haz clic en los tres puntos.
4. Elige "Open Folder". Esto abrirá la carpeta principal de esa instancia de Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para otros lanzadores

Busca una opción similar a "Open Folder", "Open Instance Folder" o "View Files" para tu configuración concreta de Minecraft.

## Copiar la configuración de FancyMenu

1. Ve a la carpeta `config` de tu instancia del MODPACK (la que quieres usar para copiar tu configuración).
2. Si hay una carpeta `fancymenu` dentro, ELIMÍNALA.
3. Abre la carpeta `config` de la instancia de ORIGEN (la que quieres usar como base de la configuración).
4. Copia la carpeta `fancymenu` de la carpeta `config` de tu instancia de ORIGEN a la carpeta `config` de tu instancia del MODPACK.
5. Hecho. Eso es todo. Reinicia ahora la instancia de tu modpack y deberías ver cómo se carga la configuración.

> Ten en cuenta que las configuraciones heredadas antiguas creadas en FancyMenu v2 (incluso si se convirtieron a v3) permitían almacenar los recursos de los diseños fuera de la carpeta `/config/fancymenu/assets/` de FancyMenu, así que en ese caso debes asegurarte de incluir también todos tus recursos en el modpack.
{.is-danger}

# Desactivar la barra de menú y las teclas de acceso rápido

Seguramente no querrás mantener visible la barra de menú de FancyMenu en tu modpack, así que deberías desactivarla. Pero como la gente aún puede pulsar la tecla de acceso rápido para volver a hacerla visible, vamos a hacer algo un poco más *agresivo*.

Ve a `/config/fancymenu/options.txt` y abre el archivo en un editor de texto.

Ahora establece `modpack_mode` en `true` y guarda el archivo.
Esto desactivará por completo todas las superposiciones y teclas de acceso rápido.

Para poder editar tus diseños de nuevo, vuelve a cambiar la opción de configuración a `false`.

# Desactivar la pantalla de bienvenida

En la mayoría de los casos no debería hacer falta, pero si todavía no has cerrado la pantalla de bienvenida (la pantalla que te indica que leas la documentación), asegúrate de poner `show_welcome_screen` en `false` en `/config/fancymenu/options.txt`.

La pantalla solo se muestra una vez y se desactiva al hacer clic en el botón **Open Documentation**, así que, de nuevo, normalmente no debería ser necesario hacerlo manualmente.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
