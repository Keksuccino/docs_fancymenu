---
title: Diseños universales
description: Aplica un diseño a varias pantallas compatibles.
sourceBlobSha: 2179fed92c6598b6e5c3ecfea354a4c853bc394b
---

# Diseños universales

Un diseño universal se considera para todas las pantallas compatibles que tengan habilitada la personalización de pantalla. No se aplica a las pantallas [bloqueadas](/incompatibility-list#screens-where-customization-is-intentionally-disabled) ni a las que se hayan excluido de alguna otra forma.

Usa los diseños universales para elementos compartidos, como logotipos, navegación, superposiciones o [elementos de audio](/elements#audio), que deban aparecer en varias pantallas.

# Crear un diseño universal

1. Abre una pantalla compatible y muestra la barra de menú de FancyMenu.
2. Selecciona **Diseños -> Nuevo -> Para todas las pantallas [Universal]**.
3. Agrega y configura los elementos.
4. Guarda el diseño.

Las pantallas normales aún requieren que esté habilitada la **Personalización de la pantalla actual**. No hay una opción global para habilitar la personalización en todas las pantallas, ya que personalizar pantallas de mods no compatibles puede causar problemas.

# Limitar las pantallas

Abre la configuración del diseño universal desde el menú contextual del fondo del editor.

- **Lista de permitidos:** el diseño se aplica solo a los identificadores de pantalla incluidos en la lista.
- **Lista de bloqueados:** el diseño se aplica a todas las pantallas aptas, excepto a los identificadores incluidos en la lista.

Usa **Personalización -> Copiar identificador de la pantalla actual** para copiar un [identificador de pantalla](/screen-identifiers).

También puedes agregar [requisitos para todo el diseño](/conditions#layout-wide-requirements) para controlar cuándo se aplica.

# Orden de los diseños

Los diseños universales aptos y los diseños específicos de cada pantalla se combinan y se apilan según el **Índice del diseño**. Los índices más bajos se aplican primero; los ajustes apilables posteriores pueden sobrescribir los anteriores. Si tienen el mismo índice, los diseños universales se recopilan antes que los específicos de cada pantalla.
