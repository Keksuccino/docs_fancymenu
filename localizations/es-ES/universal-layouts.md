---
title: Diseños universales
description: Aplica un mismo diseño a varias pantallas compatibles.
---
# Diseños universales

Un Diseño universal se tiene en cuenta para todas las pantallas compatibles que tengan habilitada la personalización de pantalla. No se aplica a pantallas [bloqueadas](./incompatibility-list#screens-where-customization-is-intentionally-disabled) ni a otras pantallas excluidas.

Usa los Diseños universales para elementos compartidos, como logotipos, navegación, superposiciones o [elementos de audio](./elements#audio), que deban mantenerse a través de varias pantallas.

# Crear uno

1. Abre una pantalla compatible y muestra la barra de menús de FancyMenu.
2. Selecciona **Diseños -> Nuevo -> Para todas las pantallas [Universal]**.
3. Añade y configura elementos.
4. Guarda el diseño.

Las pantallas normales siguen requiriendo que esté habilitada **Personalización de la pantalla actual**. No existe un interruptor global para habilitarlo todo, porque las pantallas de mods no compatibles pueden fallar al personalizarlas.

# Limitar pantallas

Abre la configuración del Diseño universal desde el menú contextual del fondo del editor.

- **Lista blanca:** el diseño se aplica solo a los identificadores de pantalla incluidos en la lista.
- **Lista negra:** el diseño se aplica a todas las pantallas aptas excepto a los identificadores incluidos en la lista.

Usa **Personalización -> Copiar identificador de la pantalla actual** para copiar un [identificador de pantalla](./screen-identifiers).

También puedes añadir [requisitos a nivel de diseño](./conditions#layout-wide-requirements) para controlar cuándo se aplica el diseño.

# Orden de los diseños

Los Diseños universales aptos y los diseños específicos de pantalla se combinan y se apilan según el **Índice del diseño**. Los índices más bajos se aplican primero; las configuraciones apilables posteriores pueden sobrescribir las anteriores. En el mismo índice, los Diseños universales se recopilan antes que los diseños específicos de pantalla.
