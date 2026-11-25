---
title: Posicionamiento y tamaño avanzados
description: Cómo usar el posicionamiento y el tamaño avanzados de los elementos.
sourceBlobSha: 205b887e844f770856bfd4836ea791e0acdca4b8
---
# Posicionamiento y tamaño avanzados

El posicionamiento y el tamaño avanzados te dan control directo sobre las coordenadas y dimensiones de los elementos.

> [!WARNING]
> Para adaptar la escala de la interfaz, primero prueba el **Autoescalado** en todo el diseño. Haz clic derecho en el fondo del editor, establece una escala de interfaz y luego activa **Autoescalado** en el mismo menú.


# Activar o desactivar el modo de posicionamiento y tamaño avanzados

Para activar el posicionamiento o el tamaño avanzados de un elemento, haz **clic derecho** en él y selecciona **Posicionamiento avanzado** o **Tamaño avanzado**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor avanzado de posición o tamaño.

Para **desactivarlo** y volver al posicionamiento o tamaño normal, **borra todos los valores de posicionamiento o tamaño**.

> [!WARNING]
> Mientras un elemento esté en el modo de tamaño o posicionamiento avanzados, es posible que no puedas cambiar su tamaño ni moverlo, o que estas acciones estén restringidas.

# Calcular posiciones y tamaños

Los valores avanzados de posición y tamaño admiten [marcadores de posición](/placeholders).

Esto te permite combinar el marcador de posición [**Calculadora**](/placeholders#calculator) con marcadores de posición de la interfaz, como [**Ancho de pantalla**](/placeholders#screen-width), [**Escala de la interfaz**](/placeholders#gui-scale) y [**Ancho del elemento**](/placeholders#element-width).

> [!NOTE]
> Puedes agregar marcadores de posición haciendo clic en el botón **Marcadores de posición**, en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** marcadores de posición.

Para hacer un cálculo con el [marcador de posición **Calculadora**](/placeholders#calculator), reemplaza la expresión de ejemplo por la tuya. Los marcadores de posición anidados pueden proporcionar las dimensiones de la pantalla o del elemento.

Este ejemplo devuelve `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Mantén `decimal` en `false` para calcular posiciones y tamaños en píxeles enteros.

La siguiente calculadora usa el [marcador de posición **Ancho de pantalla**](/placeholders#screen-width) y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> El **Posicionamiento avanzado** ignora el ancla del elemento y usa la esquina superior izquierda de la pantalla (`X0 Y0`) como origen. La opción **Mantener en pantalla** sigue aplicándose.
