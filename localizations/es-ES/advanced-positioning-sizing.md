---
title: Posicionamiento y dimensionado avanzados
description: Cómo usar el posicionamiento y dimensionado avanzados de los elementos.
---
# Posicionamiento y dimensionado avanzados

El posicionamiento y dimensionado avanzados te ofrecen control directo sobre las coordenadas y dimensiones de los elementos.

> Para adaptar la escala de la interfaz gráfica, prueba primero el **Autoescalado** a nivel de diseño. Haz clic derecho en el fondo del editor, fuerza una escala de GUI y, después, activa **Autoescalado** en ese mismo menú.
{.is-warning}


# Activar o desactivar el modo de posicionamiento/dimensionado avanzado

Para activar el posicionamiento o dimensionado avanzados de un elemento, **haz clic derecho** sobre él y selecciona **Posicionamiento avanzado** o **Dimensionado avanzado**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor avanzado de posición o tamaño.

Para **desactivarlo** y volver al posicionamiento/dimensionado normal, **borra todos los valores de posicionamiento/dimensionado**.

> Mientras un elemento esté en modo de Posicionamiento/Dimensionado avanzado, puede que cambiar su tamaño o moverlo esté deshabilitado o restringido.
{.is-warning}

# Calcular posiciones/tamaños

Los valores avanzados de posición y tamaño admiten [placeholders](./placeholders).

Esto te permite combinar el placeholder [**Calculator**](./placeholders#calculator-calc) con placeholders de la GUI como [**Screen Width**](./placeholders#screen-width-guiwidth), [**GUI Scale**](./placeholders#gui-scale-guiscale) y [**Element Width**](./placeholders#element-width-elementwidth).

> Puedes añadir placeholders haciendo clic en el botón **Placeholders** en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** placeholders.
{.is-info}

Para calcular algo con el [**placeholder Calculator**](./placeholders#calculator-calc), sustituye la expresión de ejemplo por la tuya. Los placeholders anidados pueden proporcionar dimensiones de pantalla o de elemento.

Este ejemplo devuelve `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Mantén `decimal` en `false` para cálculos de posición y tamaño con píxeles enteros.

El siguiente cálculo usa el [**placeholder Screen Width**](./placeholders#screen-width-guiwidth) y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Posicionamiento avanzado** ignora el anclaje del elemento y usa la esquina superior izquierda de la pantalla (`X0 Y0`) como origen. **Permanecer en pantalla** sigue aplicándose.
