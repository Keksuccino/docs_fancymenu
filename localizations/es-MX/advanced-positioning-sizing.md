---
title: Posicionamiento y Tamaño Avanzados
description: Cómo usar el Posicionamiento y Tamaño Avanzados de los elementos.
---

# Posicionamiento y Tamaño Avanzados

El posicionamiento/tamaño avanzado te permite tener **control total sobre la posición y el tamaño de tus elementos**. Esto es muy poderoso, pero también **consume mucho más tiempo** que usar el tamaño y posicionamiento automáticos de FancyMenu.

> Si solo quieres que los elementos se escalen mejor con la **escala de la GUI** de Minecraft, se recomienda usar en su lugar el **autoescalado** de todo el diseño, que puede activarse primero forzando una escala de GUI en el menú que se abre al hacer clic derecho sobre el fondo del editor y luego habilitando **Auto-Scaling** en el mismo menú.
{.is-warning}


# Activar o desactivar el modo de Posicionamiento/Tamaño Avanzados

Para **activar** el posicionamiento/tamaño avanzado de un elemento, haz **clic derecho** sobre él y luego haz clic en **Advanced Positioning** o **Advanced Sizing**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor de posición o tamaño avanzado.

Para **desactivarlo** y volver al posicionamiento/tamaño normal, **borra todos los valores de posicionamiento/tamaño**.

> Mientras un elemento está en modo de Tamaño/Posicionamiento Avanzado, cambiar su tamaño y/o moverlo podría estar deshabilitado o restringido.
{.is-warning}

# Cálculo de Posiciones/Tamaños

La razón por la que el posicionamiento/tamaño avanzado es tan poderoso es que puedes usar **placeholders** en los valores de posición/tamaño.

Esto te permite usar el placeholder **Calculator** (ubicado en la categoría de placeholders **Advanced**) en combinación con placeholders de la categoría **GUI**, como **Screen Width**, **GUI Scale**, **Element Width** y más.

> Puedes agregar placeholders haciendo clic en el botón **Placeholders** en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** placeholders.
{.is-info}

Para calcular algo con el placeholder **Calculator**, reemplaza la expresión de ejemplo con la tuya. Puedes usar placeholders anidados en la expresión, así que ahí puedes aprovechar los placeholders de tamaño de pantalla, tamaño del elemento, etc.

Por ejemplo, este placeholder simplemente resolverá `1 + 1` y después se mostrará como `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

La variable `decimal` está configurada en `false`, lo cual es importante para la mayoría de los cálculos de tamaño/posicionamiento, así que configúrala siempre en `false` cuando trabajes con posicionamiento/tamaño avanzado.

El siguiente cálculo usa el placeholder **Screen Width** y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`
