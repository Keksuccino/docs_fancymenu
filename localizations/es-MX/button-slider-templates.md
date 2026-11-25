---
title: Plantillas de botones y controles deslizantes
description: >-
  Aplica a todos los botones o controles deslizantes de una pantalla las
  texturas, los sonidos y el estilo de etiqueta de un botón de plantilla.
sourceBlobSha: 805a2ae3221a644c78cd5eafebc5579bc8d60815
---

# Plantillas de botones y controles deslizantes

Una plantilla es un [elemento Botón](/elements#button) que transmite su apariencia a todos los demás botones o controles deslizantes de la pantalla, tanto los predeterminados como los personalizados. Cambia la plantilla y todos cambiarán con ella.

> [!TIP]
> Para que todos los menús del juego tengan la misma apariencia, usa [Personalizaciones globales](/global-customizations). Las plantillas son para una sola pantalla o para todas las pantallas que cargue una [distribución universal](/universal-layouts).

# Crear una plantilla

1. Agrega un elemento Botón a la distribución.
2. Haz clic derecho en él, abre **Configuración de plantilla** y activa **Modo de plantilla**.
3. En **Compartir configuración con**, selecciona **Botones** o **Controles deslizantes**.
4. Asigna a la plantilla las texturas, los sonidos y la configuración de etiqueta que quieras, como harías con cualquier otro botón. Si seleccionas **Controles deslizantes**, la configuración de textura será la de los controles deslizantes.

La plantilla no aparece fuera del editor, así que puedes colocarla donde no estorbe. En el editor, una plantilla para controles deslizantes tiene la apariencia de uno de ellos.

# Qué comparten las plantillas

## Siempre

- Sus texturas de botón (o de control deslizante), con la configuración de [división en nueve partes](/nine-slicing-and-tiling).
- Sus sonidos de colocar el cursor encima, quitarlo y hacer clic.

Mientras una plantilla esté activa, los botones usarán sus texturas y sonidos en lugar de los propios. Si la plantilla no tiene texturas, los botones tampoco usarán las suyas.

## Al activar estas opciones

Activa estas opciones en **Configuración de plantilla** de la plantilla:

| Opción | Qué toman los botones de la plantilla |
|---|---|
| **Compartir etiqueta en modo de plantilla** | Su **Etiqueta** y **Etiqueta al pasar el cursor**, además de todo el estilo de etiqueta: **Alineación de etiqueta**, **Escala de etiqueta**, **Color base de etiqueta**, **Color de etiqueta al pasar el cursor**, **Sombra de etiqueta** y **Subrayar etiqueta al pasar el cursor**. |
| **Compartir posición X en modo de plantilla** y **Compartir posición Y en modo de plantilla** | Su posición. Los botones predeterminados solo se mueven cuando su **Punto de anclaje** es distinto de **Predeterminado (original)**. |
| **Compartir opacidad en modo de plantilla** | Su opacidad. |

## Alineación de etiquetas para todos los botones

Al activar **Compartir etiqueta en modo de plantilla**, todos los botones también reciben el texto de la plantilla. Por eso, esta opción está pensada para pantallas en las que todos los botones deben tener el mismo texto.

Para alinear solo las etiquetas y conservar sus textos:

- En una pantalla, selecciona los botones con `Ctrl` + clic (consulta [Seleccionar](/layout-editor#selecting)), haz clic derecho en uno de ellos y configura **Alineación de etiqueta** una sola vez para todos.
- Para todos los menús, usa **Alineación de etiqueta** en [Personalizaciones globales](/global-customizations#labels).

# Información útil

- Solo los elementos Botón pueden ser plantillas, pero funcionan con botones y controles deslizantes predeterminados y personalizados.
- Una pantalla puede tener una plantilla para botones y otra para controles deslizantes al mismo tiempo. Si hay más de una plantilla del mismo tipo, solo una funcionará.
- Una plantilla solo funciona mientras está visible. Puedes usar [requisitos](/element-visibility) en la plantilla para activarla y desactivarla.
