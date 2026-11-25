---
title: Exportar para IA
description: >-
  Convierte partes de tu configuración de FancyMenu en texto para asistentes de
  IA como Alice, para que puedan ayudarte más rápido.
sourceBlobSha: 37ce2fdd6cf8d770ca3f6f31528ac6076fe46922
---
# Exportar para IA

**Exportar para IA** convierte una parte de tu configuración de FancyMenu en texto pensado para asistentes de IA, como Alice, el bot de ayuda del [Discord de FancyMenu](https://discord.gg/rhayah27GC). Pégalo en el chat y la IA verá exactamente cómo está configurado todo, en lugar de tener que adivinar.

<img width="800" alt="Una publicación de ayuda en Discord donde Alice pide una exportación, encuentra el problema y ayuda al jugador a corregir su botón" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/export_for_ai_chat.gif?raw=true">

# Por qué existe

Una captura de pantalla muestra cómo se ve algo, pero no cómo está configurado. Es tardado escribir a mano un script de acciones o un requisito, y muchas veces se pierde en el proceso justo el detalle importante.

Una exportación incluye todo lo que necesita la IA:

- Cada ajuste, acción, requisito y valor de lo que exportes.
- Las versiones de FancyMenu, Minecraft, el cargador de mods, Java y tu sistema.
- Explicaciones breves sobre cómo funciona FancyMenu, para que la IA lo interprete correctamente.

Las exportaciones siempre están en inglés, sin importar el idioma en el que juegues. El nombre de tu cuenta en las rutas de los archivos se reemplaza por `<user>`, así que puedes compartir las exportaciones en chats públicos.

# Cuándo usarlo

- Algo no funciona como debería, por ejemplo, un botón que no hace nada o un elemento que nunca aparece.
- FancyMenu muestra un error o una advertencia.
- Quieres ayuda para crear algo, como un script de acciones, un requisito o un menú completo.
- Quieres saber qué puedes hacer en tu juego. **Todo lo que FancyMenu puede hacer** enumera todos los elementos, fondos, acciones, requisitos, marcadores de posición y escuchas disponibles, incluidos los de los complementos.

Exporta solo lo relacionado con tu pregunta, como el botón que no funciona. Las exportaciones más pequeñas ayudan a que la IA se enfoque. Después, dile qué esperabas que pasara y qué ocurrió en realidad.

# Cómo exportar

Cada opción de la lista abre un menú pequeño:

- **Copiar al portapapeles** copia la exportación para que puedas pegarla en el chat con `Ctrl + V` (`Cmd + V` en macOS).
- **Guardar como archivo** guarda la exportación como archivo Markdown en `<game-directory>/fancymenu_data/ai_exports/` y abre esa carpeta para que puedas arrastrar el archivo al chat. Usa esta opción para las exportaciones grandes que no caben en un mensaje.

Las exportaciones del editor de diseños y de las ventanas de escuchas y programadores incluyen los cambios que aún no hayas guardado.

# Dónde puedes exportar

## Barra de menú

| Qué se exporta | Dónde encontrarlo |
|---|---|
| La pantalla actual, con sus widgets y lo que FancyMenu hace en ella | **barra de menú -> Personalización -> Exportar pantalla actual para IA** |
| Un diseño | **barra de menú -> Personalización -> Diseños**, elige el diseño y luego **Exportar diseño para IA** |
| Tu juego, hardware y mods, además de las funciones que FancyMenu puede usar, como la compatibilidad con video y navegador | **barra de menú -> Ayuda -> Exportar para IA -> Información del sistema** |
| Todos los ajustes de FancyMenu, incluidas las [personalizaciones globales](/global-customizations) | **barra de menú -> Ayuda -> Exportar para IA -> Ajustes de FancyMenu** |
| Todas las [variables](/variables) | **barra de menú -> Ayuda -> Exportar para IA -> Todas las variables** |
| Todas las [escuchas](/listeners) | **barra de menú -> Ayuda -> Exportar para IA -> Todas las escuchas** |
| Todos los [programadores](/schedulers) | **barra de menú -> Ayuda -> Exportar para IA -> Todos los programadores** |
| Todas las [GUI personalizadas](/custom-guis) | **barra de menú -> Ayuda -> Exportar para IA -> GUI personalizadas** |
| Todos los [perfiles](/profiles) | **barra de menú -> Ayuda -> Exportar para IA -> Perfiles** |
| Todos los elementos, fondos, acciones, requisitos, marcadores de posición y escuchas de tu juego | **barra de menú -> Ayuda -> Exportar para IA -> Todo lo que FancyMenu puede hacer** |

## Editor de diseños

| Qué se exporta | Dónde encontrarlo |
|---|---|
| El diseño que estás editando | **Diseño -> Exportar diseño para IA** en la barra de menú del editor |
| Otro diseño de la pantalla | **Diseño -> Abrir** en la barra de menú del editor, elige el diseño y luego **Exportar diseño para IA** |
| Un elemento | Haz clic derecho en el elemento y luego selecciona **Exportar para IA** |
| Todos los elementos seleccionados | **Editar -> Exportar elementos seleccionados para IA** en la barra de menú del editor |
| Un [fondo de menú](/menu-backgrounds) | Haz clic derecho en el fondo del editor, selecciona **Fondos de menú**, elige el fondo y luego **Exportar para IA** |
| Una [superposición decorativa](/decoration-overlays) | Haz clic derecho en el fondo del editor, selecciona **Superposiciones decorativas**, elige la superposición y luego **Exportar para IA** |

## Editores y ventanas

| Qué se exporta | Dónde encontrarlo |
|---|---|
| Un [script de acciones](/action-scripts) | Haz clic derecho en el editor de scripts de acciones y luego selecciona **Exportar script de acciones para IA** |
| [Requisitos](/conditions) | Haz clic derecho en la ventana **Administrar requisitos** y luego selecciona **Exportar requisitos para IA** |
| Un texto, como el contenido de un elemento de texto | Haz clic derecho en el editor de texto y luego selecciona **Exportar texto para IA** |
| Una variable o todas las variables | Abre **barra de menú -> Personalización -> Administrar variables**, haz clic derecho y luego selecciona **Exportar variable para IA** o **Exportar todas las variables para IA** |
| Una escucha o todas las escuchas | Abre **barra de menú -> Personalización -> Administrar escuchas**, haz clic en **Exportar para IA** y luego selecciona **Escucha seleccionada** o **Todas las escuchas** |
| Un programador o todos los programadores | Abre **barra de menú -> Personalización -> Administrar programadores**, haz clic en **Exportar para IA** y luego selecciona **Programador seleccionado** o **Todos los programadores** |

## Errores y advertencias

Cuando FancyMenu muestre un error o una advertencia, haz clic en **Exportar para IA**, junto a **Aceptar**, para exportar el mensaje.

## Servidores

La configuración de [FMData](/fm-data) de un servidor, con sus escuchas del servidor y datos de bienvenida, se puede exportar con un comando. Se necesita el nivel de permiso 2, igual que para todos los comandos `/fmdata`.

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

- `copy` te envía un mensaje en el chat. Haz clic en él para copiar la exportación. En la consola del servidor, se muestra la exportación completa.
- `file` guarda la exportación en el servidor, en `fancymenu_data/ai_exports/`. Úsalo cuando la exportación sea demasiado grande para el chat.
