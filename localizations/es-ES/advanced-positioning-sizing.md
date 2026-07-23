---
title: Posicionamiento y dimensionado avanzados
description: Cómo usar el posicionamiento y el dimensionado avanzados de los elementos.
---
# Posicionamiento y dimensionado avanzados

El posicionamiento y el dimensionado avanzados te dan control directo sobre las coordenadas y dimensiones de los elementos.

> [!WARNING]
> Para la adaptación al escalado de la interfaz, prueba primero el **Autoescalado** a nivel de diseño. Haz clic derecho en el fondo del editor, fuerza un escalado de GUI y luego activa **Autoescalado** en el mismo menú.


# Activar o desactivar el modo de posicionamiento/dimensionado avanzado

Para habilitar el posicionamiento o dimensionado avanzado de un elemento, haz **clic derecho** sobre él y selecciona **Posicionamiento avanzado** o **Dimensionado avanzado**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor de posición o tamaño avanzado.

Para **desactivarlo** y volver al posicionamiento/dimensionado normal, **borra todos los valores de posicionamiento/dimensionado**.

> [!WARNING]
> Mientras un elemento esté en modo de Dimensionado/Posicionamiento avanzado, el cambio de tamaño y/o el movimiento del elemento podrían estar deshabilitados o restringidos.

# Calcular posiciones/tamaños

Los valores avanzados de posición y tamaño admiten [marcadores de posición](./placeholders).

Esto te permite combinar el marcador de posición [**Calculadora**](./placeholders#calculator-calc) con marcadores de posición de la interfaz como [**Ancho de pantalla**](./placeholders#screen-width-guiwidth), [**Escala de GUI**](./placeholders#gui-scale-guiscale) y [**Ancho del elemento**](./placeholders#element-width-elementwidth).

> [!NOTE]
> Puedes añadir marcadores de posición haciendo clic en el botón **Marcadores de posición** en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** marcadores de posición.

Para calcular algo con el [**marcador de posición Calculadora**](./placeholders#calculator-calc), sustituye la expresión de ejemplo por la tuya propia. Los marcadores de posición anidados pueden proporcionar dimensiones de pantalla o de elementos.

Este ejemplo devuelve `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Mantén `decimal` en `false` para cálculos de posición y tamaño en píxeles enteros.

La siguiente calculadora usa el [**marcador de posición Ancho de pantalla**](./placeholders#screen-width-guiwidth) y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Posicionamiento avanzado** ignora el ancla del elemento y usa la esquina superior izquierda de la pantalla (`X0 Y0`) como origen. **Permanecer en pantalla** sigue aplicándose.
