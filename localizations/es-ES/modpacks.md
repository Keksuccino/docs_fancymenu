---
title: Modpacks
description: Cómo incluir diseños en un modpack.
---

# FancyMenu en modpacks

Incluir tu configuración de FancyMenu en un modpack es muy fácil y solo requiere unos pocos pasos sencillos.

> [!CAUTION]
> Las configuraciones de FancyMenu pueden ejecutar acciones. Importa solo aquellas que provengan de fuentes de confianza.

> [!WARNING]
> Esta página es **SOLO** para configuraciones de FancyMenu creadas completamente en **FancyMenu v3+**; así que, si usas una configuración heredada (creada en v2 y convertida a v3), algunos pasos podrían ser diferentes.

# Incluir la configuración de FancyMenu en tu modpack

Lo principal que necesitas hacer es copiar una carpeta especial que FancyMenu utiliza para guardar todos tus diseños.

## Lo que tendrás que localizar

1. **Tu carpeta de "instancia de Minecraft":** Es la carpeta principal de tu ordenador donde se almacenan todos los archivos de una configuración concreta de Minecraft (como aquella en la que diseñaste tus menús). Launchers como CurseForge y Modrinth la llaman "instancia" o "perfil".
2. **La carpeta `config`:** Dentro de la carpeta de tu instancia de Minecraft, normalmente hay una carpeta llamada `config`. Aquí es donde muchos mods guardan su configuración.
3. **La carpeta `fancymenu`:** Dentro de esa carpeta `config`, FancyMenu crea su propia carpeta llamada `fancymenu`. ¡Esta es la carpeta importante que necesitamos!

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

### Para otros launchers

Busca una opción similar como "Open Folder", "Open Instance Folder" o "View Files" para tu configuración concreta de Minecraft.

## Copiar la configuración de FancyMenu

1. Ve a la carpeta `config` de tu instancia del MODPACK (la que quieres usar como destino para copiar tu configuración).
2. Si hay una carpeta `fancymenu` dentro, ELIMÍNALA.
3. Abre la carpeta `config` de la instancia ORIGEN (la que quieres usar como fuente de la configuración).
4. Copia la carpeta `fancymenu` dentro de la carpeta `config` de tu instancia ORIGEN a la carpeta `config` de tu instancia del MODPACK.
5. Listo. Eso es todo. Reinicia ahora la instancia de tu modpack y deberías ver cómo se carga la configuración.

> [!CAUTION]
> Ten en cuenta que las configuraciones heredadas antiguas creadas en FancyMenu v2 (incluso aunque se hayan convertido a v3) permitían guardar recursos del diseño fuera de la carpeta `<game-directory>/config/fancymenu/assets/` de FancyMenu, así que, en ese caso, debes asegurarte de incluir también todos tus recursos en el modpack.

# Desactivar la barra de menú y las teclas rápidas

Seguro que no quieres mantener visible la barra de menú de FancyMenu en tu modpack, así que deberías desactivarla. Pero como la gente aún puede pulsar la tecla rápida para volver a mostrarla, hagamos algo un poco más *agresivo*.

Ve a `<game-directory>/config/fancymenu/options.txt` y abre el archivo en un editor de texto.

Ahora establece `modpack_mode` en `true` y guarda el archivo.
Esto desactivará por completo todas las superposiciones y las teclas rápidas.

Para poder editar tus diseños de nuevo, vuelve a establecer la opción de configuración en `false`.

# Desactivar la pantalla de bienvenida

Esto no debería ser necesario en la mayoría de los casos, pero si todavía no has cerrado la pantalla de bienvenida (la pantalla que te indica que leas la documentación), asegúrate de establecer `show_welcome_screen` en `false` en `<game-directory>/config/fancymenu/options.txt`.

La pantalla solo se muestra una vez y se desactiva al hacer clic en el botón **Open Documentation**, así que, de nuevo, no debería ser necesario hacerlo manualmente en la mayoría de los casos.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
