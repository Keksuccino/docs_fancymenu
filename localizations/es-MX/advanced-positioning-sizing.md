---
title: Posicionamiento y dimensionamiento avanzados
description: Cómo usar el posicionamiento y dimensionamiento avanzados de elementos.
---
# Posicionamiento y dimensionamiento avanzados

El posicionamiento/dimensionamiento avanzado te permite tener **control total sobre la posición y el tamaño de tus elementos**. Esto es muy poderoso, pero también **consume bastante más tiempo** que usar el dimensionamiento y posicionamiento automáticos de FancyMenu.

> Si solo quieres que los elementos se adapten mejor a la **escala de la interfaz** de Minecraft, se recomienda usar en su lugar el **autoescalado** a nivel de diseño, que se puede habilitar primero forzando una escala de interfaz en el menú que se abre al hacer clic derecho en el fondo del editor y luego activando **Auto-Scaling** en ese mismo menú.
{.is-warning}


# Activar o desactivar el modo de posicionamiento/dimensionamiento avanzado

Para **activar** el posicionamiento/dimensionamiento avanzado de un elemento, **haz clic derecho** sobre él y selecciona **Advanced Positioning** o **Advanced Sizing**.
El elemento cambiará automáticamente al modo avanzado cuando establezcas un valor de posición o tamaño avanzado.

Para **desactivarlo** y volver al posicionamiento/dimensionamiento normal, **borra todos los valores de posicionamiento/dimensionamiento**.

> Mientras un elemento esté en modo de Dimensionamiento/Posicionamiento Avanzado, es posible que cambiar su tamaño y/o moverlo esté deshabilitado o restringido.
{.is-warning}

# Cálculo de posiciones/tamaños

La razón por la que el posicionamiento/dimensionamiento avanzado es tan poderoso es que puedes usar **placeholders** en los valores de posición/tamaño.

Esto te permite usar el placeholder **Calculator** (ubicado en la categoría de placeholders **Advanced**) en combinación con placeholders de la categoría **GUI**, como **Screen Width**, **GUI Scale**, **Element Width** y más.

> Puedes agregar placeholders haciendo clic en el botón **Placeholders** en la parte superior derecha del editor de texto. Si no ves este botón, el contenido que quieres editar **no admite** placeholders.
{.is-info}

Para calcular algo con el placeholder **Calculator**, reemplaza la expresión de ejemplo con la tuya. Puedes usar placeholders anidados en la expresión, así que ahí puedes aprovechar el tamaño de pantalla, el tamaño del elemento, etc.

Por ejemplo, este placeholder simplemente resolverá `1 + 1` y después se mostrará como `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

La variable `decimal` está configurada en `false`, lo cual es importante para la mayoría de los cálculos de tamaño/posicionamiento, así que mantén siempre este valor en `false` cuando trabajes con posicionamiento/dimensionamiento avanzado.

El siguiente calculador usa el placeholder **Screen Width** y lo divide entre `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> Mientras **Advanced Positioning** esté habilitado, el **anchor** y cualquier otro tipo de función relacionada con la posición del elemento serán **ignorados**. Advanced Positioning siempre usará la esquina superior izquierda (X0 Y0) como origen, tal como lo hace la lógica predeterminada de la interfaz de Minecraft. La única configuración que respeta Advanced Positioning es **Stay on Screen**.
