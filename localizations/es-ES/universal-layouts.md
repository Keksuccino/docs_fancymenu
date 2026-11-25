---
title: Diseños universales
description: Aplica un mismo diseño a varias pantallas compatibles.
sourceBlobSha: 2179fed92c6598b6e5c3ecfea354a4c853bc394b
---

# Diseños universales

Se tiene en cuenta un diseño universal para todas las pantallas compatibles que tengan activada la personalización. No se aplica a las pantallas [bloqueadas](/incompatibility-list#screens-where-customization-is-intentionally-disabled) ni a otras pantallas excluidas.

Utiliza los diseños universales para elementos compartidos, como logotipos, navegación, superposiciones o [elementos de audio](/elements#audio), que deban mantenerse en varias pantallas.

# Cómo crear uno

1. Abre una pantalla compatible y muestra la barra de menús de FancyMenu.
2. Selecciona **Diseños -> Nuevo -> Para todas las pantallas [Universal]**.
3. Añade y configura los elementos.
4. Guarda el diseño.

Para las pantallas normales, también es necesario activar la **Personalización de la pantalla actual**. No hay ningún interruptor global para activarla en todas las pantallas, ya que la personalización puede provocar errores en las pantallas de mods no compatibles.

# Limitar las pantallas

Abre los ajustes del diseño universal desde el menú contextual del fondo del editor.

- **Lista de permitidos:** el diseño solo se aplica a los identificadores de pantalla incluidos en la lista.
- **Lista de bloqueados:** el diseño se aplica a todas las pantallas aptas, excepto a los identificadores incluidos en la lista.

Utiliza **Personalización -> Copiar identificador de la pantalla actual** para copiar un [identificador de pantalla](/screen-identifiers).

También puedes añadir [requisitos para todo el diseño](/conditions#layout-wide-requirements) para controlar cuándo se aplica.

# Orden de los diseños

Los diseños universales aptos y los específicos de cada pantalla se combinan y apilan según el **Índice del diseño**. Los índices más bajos se aplican primero; los ajustes posteriores que permitan el apilamiento pueden sobrescribir los anteriores. Si tienen el mismo índice, los diseños universales se recopilan antes que los específicos de cada pantalla.
