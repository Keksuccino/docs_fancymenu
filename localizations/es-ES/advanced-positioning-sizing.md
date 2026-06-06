---
title: Posicionamiento y dimensionado avanzados
description: Cómo usar el posicionamiento y el dimensionado avanzados de los elementos.
---
# Posicionamiento y dimensionado avanzados

El posicionamiento/dimensionado avanzado te permite tener **control total sobre la posición y el tamaño de tus elementos**. Esto es muy potente, pero también **mucho más lento** que usar el dimensionado y posicionamiento automáticos de FancyMenu.

> Si solo quieres que los elementos se adapten mejor al **escalado de la interfaz (GUI)** de Minecraft, se recomienda usar en su lugar el **autoescalado** de todo el diseño, que puede activarse primero forzando una escala de GUI en el menú que se abre al hacer clic derecho en el fondo del editor y luego habilitando **Auto-Scaling** en ese mismo menú.
{.is-warning}

# Activar o desactivar el modo de posicionamiento/dimensionado avanzado

Para **activar** el posicionamiento/dimensionado avanzado de un elemento, haz **clic derecho** sobre él y pulsa **Advanced Positioning** o **Advanced Sizing**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor avanzado de posición o tamaño.

Para **desactivarlo** y volver al posicionamiento/dimensionado normal, **borra todos los valores de posicionamiento/dimensionado**.

> Mientras un elemento esté en modo de Posicionamiento/Dimensionado avanzado, puede que cambiar su tamaño y/o moverlo esté deshabilitado o limitado.
{.is-warning}

# Calcular posiciones/tamaños

La razón por la que el posicionamiento/dimensionado avanzado es tan potente es que puedes usar **marcadores de posición** en los valores de posición/tamaño.

Esto te permite usar el marcador de posición **Calculator** (ubicado en la categoría de marcadores de posición **Advanced**) en combinación con marcadores de posición de la categoría **GUI**, como **Screen Width**, **GUI Scale**, **Element Width** y más.

> Puedes añadir marcadores de posición haciendo clic en el botón **Placeholders** en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** marcadores de posición.
{.is-info}

Para calcular algo con el marcador de posición **Calculator**, sustituye la expresión de ejemplo por la tuya. Puedes usar marcadores de posición anidados en la expresión, así que puedes aprovechar ahí el tamaño de la pantalla, el tamaño del elemento, etc.

Por ejemplo, este marcador de posición simplemente resolverá `1 + 1` y más adelante mostrará `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

La variable `decimal` está establecida en `false`, lo cual es importante para la mayoría de los cálculos de dimensionado/posicionamiento, así que déjala siempre en `false` cuando trabajes con posicionamiento/dimensionado avanzado.

El siguiente calculador usa el marcador de posición **Screen Width** y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> Mientras **Advanced Positioning** esté activado, el **anchor** y cualquier otro tipo de función relacionada con la posición del elemento serán **ignorados**. Advanced Positioning siempre usará la esquina superior izquierda (X0 Y0) como origen, igual que lo hace la lógica de la GUI predeterminada de Minecraft. La única configuración que respeta Advanced Positioning es **Stay on Screen**.
