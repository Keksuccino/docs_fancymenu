---
title: Plantillas de botones y controles deslizantes
description: >-
  Aplica a todos los botones o controles deslizantes de una pantalla las
  texturas, los sonidos y el estilo de etiqueta de un botón de plantilla.
sourceBlobSha: 805a2ae3221a644c78cd5eafebc5579bc8d60815
---

# Plantillas de botones y controles deslizantes

Una plantilla es un [elemento de botón](/elements#button) que transmite su aspecto a todos los demás botones o controles deslizantes de la pantalla, tanto los originales del juego como los que hayas creado. Cambia la plantilla y todos ellos cambiarán con ella.

> [!TIP]
> Para que todos los menús del juego tengan el mismo aspecto, usa las [personalizaciones globales](/global-customizations). Las plantillas son para una sola pantalla o para todas las pantallas que cargue una [disposición universal](/universal-layouts).

# Crear una plantilla

1. Añade un elemento de botón a la disposición.
2. Haz clic derecho en él, abre **Ajustes de plantilla** y activa **Modo de plantilla**.
3. En **Compartir ajustes con**, selecciona **Botones** o **Controles deslizantes**.
4. Dale a la plantilla las texturas, los sonidos y los ajustes de etiqueta que quieras, como harías con cualquier otro botón. Si seleccionas **Controles deslizantes**, los ajustes de textura serán los de los controles deslizantes.

La plantilla no aparece fuera del editor, así que colócala donde no estorbe. En el editor, una plantilla para controles deslizantes tiene el aspecto de un control deslizante.

# Qué comparten las plantillas

## Siempre

- Sus texturas de botón (o de control deslizante), con sus ajustes de [división en nueve partes](/nine-slicing-and-tiling).
- Sus sonidos al pasar el cursor, al quitarlo y al hacer clic.

Mientras una plantilla esté activa, los botones usarán sus texturas y sonidos en lugar de los propios. Si la plantilla no tiene texturas, los botones tampoco usarán las suyas.

## Al activarlo

Activa estos ajustes en **Ajustes de plantilla** de la plantilla:

| Ajuste | Qué reciben los botones de la plantilla |
|---|---|
| **Compartir etiqueta en modo de plantilla** | Su **Etiqueta** y **Etiqueta al pasar el cursor**, así como todo su estilo de etiqueta: **Alineación de la etiqueta**, **Escala de la etiqueta**, **Color base de la etiqueta**, **Color de la etiqueta al pasar el cursor**, **Sombra de la etiqueta** y **Subrayar la etiqueta al pasar el cursor**. |
| **Compartir posición X en modo de plantilla** y **Compartir posición Y en modo de plantilla** | Su posición. Los botones originales del juego solo se moverán si su **Punto de anclaje** es distinto de **Original (predeterminado)**. |
| **Compartir opacidad en modo de plantilla** | Su opacidad. |

## Alineación de etiquetas para todos los botones

Al activar **Compartir etiqueta en modo de plantilla**, todos los botones también reciben el texto de la plantilla, así que esta opción está pensada para pantallas en las que todos los botones deban mostrar lo mismo.

Para alinear únicamente las etiquetas y conservar sus textos:

- En una pantalla, selecciona los botones con `Ctrl` + clic (consulta [Selección](/layout-editor#selecting)), haz clic derecho en uno de ellos y establece **Alineación de la etiqueta** una sola vez para todos.
- Para todos los menús, usa **Alineación de la etiqueta** en las [personalizaciones globales](/global-customizations#labels).

# Información útil

- Solo los elementos de botón pueden ser plantillas, pero funcionan con botones y controles deslizantes, tanto originales como personalizados.
- Una pantalla puede tener una plantilla para botones y otra para controles deslizantes al mismo tiempo. Si hay más de una plantilla del mismo tipo, solo funcionará una.
- Una plantilla solo funciona mientras esté visible. Puedes activarla y desactivarla mediante [requisitos](/element-visibility) en la plantilla.
