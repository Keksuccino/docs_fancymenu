---
title: GUIs personalizadas
description: Crea y configura nuevas pantallas de interfaz gráfica.
---

# GUIs personalizadas

Las GUIs personalizadas son nuevas pantallas que puedes rellenar con [elementos](./elements) de FancyMenu.

> [!CAUTION]
> Las GUIs personalizadas pueden ejecutar acciones. Impórtalas solo desde fuentes en las que confíes.

# Crear una GUI personalizada

1. Abre **Personalización -> GUIs personalizadas -> Gestionar GUIs personalizadas**.
2. Selecciona **Nueva GUI**.
3. Introduce un identificador y configura los ajustes de la pantalla.
4. Selecciona **Hecho** y, después, abre la nueva GUI desde el gestor.
5. Crea y edita su diseño como cualquier otra pantalla.

Los identificadores pueden usar letras minúsculas, dígitos, `.`, `_` y `-`. No pueden contener espacios y deben ser únicos. No se pueden guardar identificadores vacíos, no válidos o duplicados.

Las GUIs personalizadas siempre tienen la personalización de pantalla activada; su interruptor de personalización no se puede desactivar.

# Ajustes de la pantalla

| Ajuste | Comportamiento |
|---|---|
| Permitir ESC | Permite que Escape cierre la GUI y vuelva a su pantalla principal |
| Pausar juego/mundo | Pausa el modo de un jugador mientras la GUI está abierta |
| Mostrar fondo del mundo | Muestra el mundo cargado detrás de la GUI |
| Superposición del fondo del mundo | Añade la superposición estándar de desenfoque/oscurecimiento sobre el mundo |
| Modo emergente | Mantiene visible la pantalla principal detrás de la GUI personalizada |
| Superposición del fondo emergente | Añade desenfoque/tonalidad sobre la pantalla principal en el modo emergente |

El modo emergente no fusiona las dos pantallas. La GUI personalizada sigue siendo la pantalla activa mientras su pantalla principal se renderiza detrás. Al cerrar la GUI personalizada, se vuelve a esa pantalla principal cuando existe.

# Abrir una GUI personalizada

Usa el identificador exacto de la GUI personalizada con cualquiera de estas opciones:

- La [**acción Abrir pantalla o GUI personalizada**](./action-scripts#open-screen-or-custom-gui-opengui).
- El [comando `/openguiscreen`](./commands#openguiscreen).

# Sobrescribir una pantalla existente

Una GUI personalizada puede reemplazar una pantalla de Vanilla o de un mod cada vez que esa pantalla se abra.

1. Crea la GUI personalizada de reemplazo.
2. Abre la pantalla que quieres reemplazar.
3. Activa **Personalización -> Ajustes -> Modo de personalización avanzada**.
4. Selecciona **Personalización -> GUIs personalizadas -> Sustituir la pantalla actual con una GUI personalizada**.
5. Elige la GUI personalizada de reemplazo.

Gestiona las sustituciones guardadas en **Personalización -> GUIs personalizadas -> Gestionar pantallas sustituidas**.

Una sustitución omite la pantalla original, así que prueba su navegación y cualquier función que dependa del comportamiento de la pantalla original.
