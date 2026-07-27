---
title: Posicionamiento y Tamaño Avanzados
description: Cómo usar el Posicionamiento y Tamaño Avanzados de los elementos.
---
# Posicionamiento y Tamaño Avanzados

El posicionamiento y tamaño avanzados te da control directo sobre las coordenadas y dimensiones de los elementos.

> [!WARNING]
> Para la adaptación al tamaño de la GUI, primero prueba **Autoescalado** a nivel de todo el diseño. Haz clic derecho en el fondo del editor, fuerza un tamaño de GUI y luego habilita **Autoescalado** en el mismo menú.


# Activar o desactivar el modo de Posicionamiento/Tamaño Avanzados

Para habilitar el posicionamiento o tamaño avanzados en un elemento, **haz clic derecho** sobre él y selecciona **Posicionamiento Avanzado** o **Tamaño Avanzado**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor de posición o tamaño avanzado.

Para **deshabilitarlo** y volver al posicionamiento/tamaño normal, **borra todos los valores de posicionamiento/tamaño**.

> [!WARNING]
> Mientras un elemento está en modo de Tamaño/Posicionamiento Avanzado, es posible que cambiar su tamaño o moverlo esté deshabilitado o restringido.

# Calcular posiciones/tamaños

Los valores avanzados de posición y tamaño admiten [placeholders](./placeholders).

Esto te permite combinar el placeholder de [**Calculadora**](./placeholders#calculator-calc) con placeholders de la GUI, como [**Ancho de Pantalla**](./placeholders#screen-width-guiwidth), [**Escala de GUI**](./placeholders#gui-scale-guiscale) y [**Ancho del Elemento**](./placeholders#element-width-elementwidth).

> [!NOTE]
> Puedes agregar placeholders haciendo clic en el botón **Placeholders** en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** placeholders.

Para calcular algo con el [**placeholder de Calculadora**](./placeholders#calculator-calc), reemplaza la expresión de ejemplo con la tuya. Los placeholders anidados pueden proporcionar las dimensiones de la pantalla o del elemento.

Este ejemplo devuelve `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Mantén `decimal` en `false` para cálculos de posición y tamaño en píxeles enteros.

La siguiente calculadora usa el [**placeholder de Ancho de Pantalla**](./placeholders#screen-width-guiwidth) y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Posicionamiento Avanzado** ignora el ancla del elemento y usa la esquina superior izquierda de la pantalla (`X0 Y0`) como origen. **Mantener en Pantalla** sigue aplicando.
