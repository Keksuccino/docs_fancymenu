---
title: Girar e inclinar elementos
description: >-
  Gira e inclina elementos con sus controles en el editor de diseños, con
  valores exactos o marcadores de posición.
sourceBlobSha: e36d9f5b6a1f4253312e5eee56e1facc1551dcd3
---

# Girar e inclinar elementos

La mayoría de los elementos se pueden girar e inclinar. Ambas acciones se realizan alrededor del centro del elemento, que conserva su posición y tamaño.

- **Giro** hace girar el elemento, como las manecillas de un reloj.
- **Inclinación vertical** lo inclina hacia atrás y **Inclinación horizontal** lo ladea. Los elementos inclinados se muestran sin perspectiva, así que solo se hacen más bajos o más angostos. Al aplicar ambas inclinaciones, también quedan sesgados.

<img width="800" alt="Cuatro elementos de texto sobre el fondo de un menú: uno girado 15 grados, otro con una inclinación vertical de 45 grados que lo hace más bajo, otro con una inclinación horizontal de 45 grados que lo hace más angosto y otro con ambas inclinaciones, que queda sesgado. Los recuadros claros detrás muestran dónde estarían sin giro ni inclinación." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_axes.png?raw=true">

# En el editor de diseños

<img width="800" alt="En el editor de diseños, se gira una calcomanía de Season 3 con el control del círculo que la rodea; después, se inclina un panel de Patch Notes con los controles de las líneas a su derecha y debajo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_editor.gif?raw=true">

Selecciona un elemento en el [editor de diseños](/layout-editor) y arrastra sus controles:

- El control del círculo que rodea el elemento lo hace girar.
- El control de la línea a su derecha establece su **Inclinación vertical**; el de la línea de abajo establece su **Inclinación horizontal**. El punto medio de una línea corresponde a ninguna inclinación.

Mientras arrastras:

- Mantén presionada la tecla `Shift` para ajustar el valor en incrementos: 45 grados para el giro y 15 grados para la inclinación.
- Cerca de 0, los controles se ajustan a 0 para que puedas enderezar fácilmente un elemento.
- La parte superior izquierda del elemento muestra su giro e inclinación.

Ten en cuenta lo siguiente:

- El marco de selección permanece recto. Haz clic dentro de él para seleccionar o mover el elemento.
- Los controles solo aparecen cuando hay un elemento seleccionado.
- Los elementos que no tienen un círculo ni líneas no se pueden girar ni inclinar. Consulta [Elementos que no se pueden girar ni inclinar](#elements-without-rotation-or-tilt).
- **barra de menú -> Ventana -> Controles de giro de elementos** y **Controles de inclinación de elementos** ocultan los controles de todos los elementos.

# Valores exactos

Haz clic derecho en el elemento para acceder a estas opciones. Cada una tiene las opciones **Establecer con selector numérico**, **Establecer como texto sin formato** y **Restablecer al valor predeterminado**.

| Opción | Qué hace |
|---|---|
| **Giro** | Los grados que gira en sentido horario, por ejemplo, `90` para un cuarto de vuelta. Los valores negativos lo hacen girar en sentido antihorario. |
| **Inclinación vertical** | Cuánto se inclina hacia atrás, de `-60` a `60` grados. |
| **Inclinación horizontal** | Cuánto se ladea, de `-60` a `60` grados. |

Una sola inclinación se ve igual con un valor positivo o negativo. Si aplicas ambas inclinaciones, sus signos determinan hacia qué lado queda sesgado el elemento.

## Con marcadores de posición

Para girar o inclinar un elemento con una [variable](/variables) u otro [marcador de posición](/placeholders):

1. Haz clic derecho en el elemento y activa **Modo de giro avanzado**, **Modo de inclinación vertical avanzado** o **Modo de inclinación horizontal avanzado**.
2. Haz clic en **Giro**, **Inclinación vertical** o **Inclinación horizontal**; luego, en **Establecer como texto sin formato**, e ingresa el marcador de posición.

Los modos avanzados conservan su propio valor y ocultan el control, así que al arrastrarlo no se reemplazará el marcador de posición. Al desactivar un modo, el elemento recupera su valor anterior.

Un logotipo que gira una vez cada 3.6 segundos, con este valor de **Giro** en **Modo de giro avanzado**. Divide entre un número mayor que `10` para hacerlo más lento:

```
{"placeholder":"calc","values":{"expression":"{"placeholder":"unix_time"} / 10 % 360"}}
```

Una aguja que apunta al valor indicado por la variable `needle_angle`, que se puede establecer con botones o con un [deslizador](/elements#slider):

```
{"placeholder":"getvariable","values":{"name":"needle_angle"}}
```

# Clics y el mouse

<img width="800" alt="El puntero sobre un botón Join Server girado: no ocurre nada en las esquinas que tendría el botón recto y se iluminan los extremos del botón tal como se muestra" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_hover.gif?raw=true">

Los botones, los deslizadores y los enlaces y barras de desplazamiento de los elementos de texto reaccionan al mouse donde se muestran, incluso si están girados o inclinados. Lo mismo ocurre con los requisitos [**El elemento está bajo el puntero**](/conditions#is-element-hovered), [**Cualquier elemento está bajo el puntero**](/conditions#is-any-element-hovered) y [**Cualquier botón está bajo el puntero**](/conditions#is-any-button-hovered).

> [!NOTE]
> Las casillas de verificación, los campos de entrada de texto, los controles de arrastre y los navegadores siguen reaccionando dentro del recuadro que tendrían sin giro ni inclinación. Mantenlos rectos.

# Elementos que no se pueden girar ni inclinar

- Sin giro ni inclinación: [áreas desplazables](/scrollable-areas), [sombreadores GLSL](/elements#glsl-shader), [modelos JSON de bloques y objetos](/elements#blockitem-json-model), [entidades de jugadores](/player-entities) y [elementos vanilla](/vanilla-elements), como los botones de la propia pantalla.
- Con giro, pero sin inclinación: [información sobre herramientas](/elements#tooltip) y [objetos](/elements#item).

Los elementos dentro de un área desplazable se pueden girar e inclinar; lo único que no se puede es el área en sí.

Los elementos de [texto de pantalla de inicio](/splash-text) también tienen su propia opción **Giro** más abajo en su menú al hacer clic derecho, para aplicarles la inclinación característica. Funciona junto con el giro que se explica en esta página.
