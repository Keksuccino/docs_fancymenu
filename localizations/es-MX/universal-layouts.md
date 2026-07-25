---
title: Diseños universales
description: Aplica un solo diseño a varias pantallas compatibles.
---
# Diseños universales

Un Diseño universal se toma en cuenta para cada pantalla compatible que tenga habilitada la personalización de pantalla. No se aplica a pantallas [bloqueadas](./incompatibility-list#screens-where-customization-is-intentionally-disabled) ni a otras pantallas excluidas.

Usa Diseños universales para elementos compartidos como logotipos, navegación, superposiciones o [elementos de audio](./elements#audio) que deban mantenerse en varias pantallas.

# Cómo crear uno

1. Abre una pantalla compatible y muestra la barra de menú de FancyMenu.
2. Selecciona **Layouts -> New -> For All Screens [Universal]**.
3. Agrega y configura elementos.
4. Guarda el diseño.

Las pantallas normales todavía requieren que **Current Screen Customization** esté habilitado. No existe un interruptor global para habilitar todo porque las pantallas no compatibles de los mods pueden fallar cuando se personalizan.

# Limitar pantallas

Abre la configuración del Diseño universal desde el menú contextual del fondo del editor.

- **Whitelist:** el diseño se aplica solo a los identificadores de pantalla listados.
- **Blacklist:** el diseño se aplica a todas las pantallas elegibles excepto a los identificadores listados.

Usa **Customization -> Copy Identifier of Current Screen** para copiar el [identificador de pantalla](./screen-identifiers).

También puedes agregar [requisitos a nivel de diseño](./conditions#layout-wide-requirements) para controlar cuándo se aplica el diseño.

# Orden de los diseños

Los Diseños universales elegibles y los diseños específicos de pantalla se combinan y apilan según el **Layout Index**. Los índices más bajos se aplican primero; después, las opciones apilables posteriores pueden sobrescribir las anteriores. En el mismo índice, los Diseños universales se recopilan antes que los diseños específicos de pantalla.
