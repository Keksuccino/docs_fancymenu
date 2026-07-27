---
title: GUIs personalizadas
description: Crea y configura nuevas pantallas de GUI.
---

# GUIs personalizadas

Las GUIs personalizadas son nuevas pantallas que puedes llenar con [elementos](./elements) de FancyMenu.

> [!CAUTION]
> Las GUIs personalizadas pueden ejecutar acciones. Impórtalas solo de fuentes en las que confíes.

# Crear una GUI personalizada

1. Abre **Personalización -> GUIs personalizadas -> Administrar GUIs personalizadas**.
2. Selecciona **Nueva GUI**.
3. Ingresa un identificador y configura los ajustes de la pantalla.
4. Selecciona **Hecho** y luego abre la nueva GUI desde el administrador.
5. Crea y edita su diseño como cualquier otra pantalla.

Los identificadores pueden usar letras minúsculas, dígitos, `.`, `_` y `-`. No pueden contener espacios y deben ser únicos. Los identificadores vacíos, inválidos o duplicados no se pueden guardar.

Las GUIs personalizadas siempre tienen habilitada la personalización de pantalla; su interruptor de personalización no se puede desactivar.

# Ajustes de pantalla

| Ajuste | Comportamiento |
|---|---|
| Permitir ESC | Permite que Escape cierre la GUI y regrese a su pantalla principal |
| Pausar juego/mundo | Pausa el modo individual mientras la GUI está abierta |
| Renderizar fondo del mundo | Muestra el mundo cargado detrás de la GUI |
| Superposición del fondo del mundo | Agrega el desenfoque/oscurecimiento estándar sobre el mundo |
| Modo emergente | Mantiene visible la pantalla principal detrás de la GUI personalizada |
| Superposición del fondo emergente | Agrega desenfoque/tono sobre la pantalla principal en el Modo emergente |

El Modo emergente no combina ambas pantallas. La GUI personalizada sigue siendo la pantalla activa mientras su pantalla principal se renderiza detrás. Al cerrar la GUI personalizada, regresarás a esa pantalla principal cuando exista una.

# Abrir una GUI personalizada

Usa el identificador exacto de la GUI personalizada con cualquiera de estas opciones:

- La [**acción Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui).
- El comando [`/openguiscreen`](./commands#openguiscreen).

# Reemplazar una pantalla existente

Una GUI personalizada puede reemplazar una pantalla de Vanilla o de un mod cada vez que esa pantalla se abra.

1. Crea la GUI personalizada de reemplazo.
2. Abre la pantalla que quieres reemplazar.
3. Activa **Personalización -> Ajustes -> Modo de personalización avanzada**.
4. Selecciona **Personalización -> GUIs personalizadas -> Reemplazar pantalla actual con GUI personalizada**.
5. Elige la GUI personalizada de reemplazo.

Administra los reemplazos guardados en **Personalización -> GUIs personalizadas -> Administrar pantallas reemplazadas**.

Un reemplazo omite la pantalla original, así que prueba su navegación y cualquier función que dependa del comportamiento de la pantalla original.
