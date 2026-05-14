---
title: Posicionamiento y dimensionamiento avanzados
description: Cómo usar el posicionamiento y dimensionamiento avanzados de los elementos.
---

# Posicionamiento y dimensionamiento avanzados

El posicionamiento y dimensionamiento avanzados te permiten tener **control total sobre la posición y el tamaño de tus elementos**. Esto es muy potente, pero también **bastante más lento y laborioso** que usar el dimensionamiento y posicionamiento automáticos de FancyMenu.

> Si solo quieres que los elementos se adapten mejor a la **escala de la interfaz** de Minecraft, se recomienda usar en su lugar el **autoescalado** a nivel de diseño, que puede habilitarse primero forzando una escala de interfaz en el menú que se abre al hacer clic derecho sobre el fondo del editor y luego activando **Auto-Scaling** en ese mismo menú.
{.is-warning}


# Activar o desactivar el modo de posicionamiento/dimensionamiento avanzados

Para **activar** el posicionamiento/dimensionamiento avanzados en un elemento, haz **clic derecho** sobre él y selecciona **Advanced Positioning** o **Advanced Sizing**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor avanzado de posición o tamaño.

Para **desactivarlo** y volver al posicionamiento/dimensionamiento normal, **borra todos los valores de posicionamiento/dimensionamiento**.

> Mientras un elemento está en modo de dimensionamiento/posicionamiento avanzado, cambiar su tamaño o moverlo puede estar deshabilitado o restringido.
{.is-warning}

# Calcular posiciones y tamaños

La razón por la que el posicionamiento/dimensionamiento avanzados es tan potente es que puedes usar **placeholders** en los valores de posición/tamaño.

Esto te permite usar el placeholder **Calculator** (ubicado en la categoría de placeholders **Advanced**) junto con placeholders de la categoría **GUI**, como **Screen Width**, **GUI Scale**, **Element Width** y más.

> Puedes añadir placeholders haciendo clic en el botón **Placeholders** situado en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** placeholders.
{.is-info}

Para calcular algo con el placeholder **Calculator**, sustituye la expresión de ejemplo por la tuya. Puedes usar placeholders anidados en la expresión, así que puedes aprovechar ahí los placeholders de tamaño de pantalla, tamaño del elemento, etc.

Por ejemplo, este placeholder simplemente resolverá `1 + 1` y más tarde se mostrará como `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

La variable `decimal` está configurada en `false`, lo cual es importante para la mayoría de los cálculos de tamaño/posicionamiento, así que configúrala siempre como `false` cuando trabajes con posicionamiento/dimensionamiento avanzados.

El siguiente calculador usa el placeholder **Screen Width** y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`
