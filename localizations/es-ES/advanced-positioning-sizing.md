---
title: Posicionamiento y tamaño avanzados
description: Cómo usar el posicionamiento y el tamaño avanzados de los elementos.
sourceBlobSha: 205b887e844f770856bfd4836ea791e0acdca4b8
---
# Posicionamiento y tamaño avanzados

El posicionamiento y el tamaño avanzados te permiten controlar directamente las coordenadas y dimensiones de los elementos.

> [!WARNING]
> Para adaptar el diseño a la escala de la interfaz, prueba primero el **Autoescalado** de todo el diseño. Haz clic derecho en el fondo del editor, fuerza una escala de interfaz y, a continuación, activa el **Autoescalado** en el mismo menú.


# Activar y desactivar el modo de posicionamiento y tamaño avanzados

Para activar el posicionamiento o el tamaño avanzados de un elemento, haz **clic derecho** en él y selecciona **Posicionamiento avanzado** o **Tamaño avanzado**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor avanzado de posición o tamaño.

Para **desactivarlo** y volver al posicionamiento o tamaño normal, **borra todos los valores de posicionamiento o tamaño**.

> [!WARNING]
> Cuando un elemento está en el modo de tamaño o posicionamiento avanzados, es posible que no puedas cambiar su tamaño o moverlo, o que estas acciones estén limitadas.

# Calcular posiciones y tamaños

Los valores avanzados de posición y tamaño admiten [marcadores de posición](/placeholders).

Esto te permite combinar el marcador de posición [**Calculadora**](/placeholders#calculator) con marcadores de posición de la interfaz, como [**Ancho de la pantalla**](/placeholders#screen-width), [**Escala de la interfaz**](/placeholders#gui-scale) y [**Ancho del elemento**](/placeholders#element-width).

> [!NOTE]
> Puedes añadir marcadores de posición haciendo clic en el botón **Marcadores de posición**, situado en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** marcadores de posición.

Para calcular un valor con el [marcador de posición **Calculadora**](/placeholders#calculator), sustituye la expresión de ejemplo por la tuya. Los marcadores de posición anidados pueden proporcionar las dimensiones de la pantalla o del elemento.

Este ejemplo devuelve `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Mantén `decimal` en `false` para calcular posiciones y tamaños en píxeles enteros.

La siguiente calculadora usa el marcador de posición [**Ancho de la pantalla**](/placeholders#screen-width) y lo divide por `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> El **Posicionamiento avanzado** ignora el anclaje del elemento y usa la esquina superior izquierda de la pantalla (`X0 Y0`) como origen. La opción **Mantener en pantalla** sigue aplicándose.
