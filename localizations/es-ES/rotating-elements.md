---
title: Rotar e inclinar elementos
description: >-
  Rota e inclina elementos con sus controles en el editor de diseños, con
  valores exactos o con marcadores de posición.
sourceBlobSha: e36d9f5b6a1f4253312e5eee56e1facc1551dcd3
---

# Rotar e inclinar elementos

La mayoría de los elementos se pueden rotar e inclinar. Ambos movimientos se realizan alrededor del centro del elemento, que conserva su posición y tamaño.

- **Rotación**: gira el elemento, como las agujas de un reloj.
- **Inclinación vertical**: lo inclina hacia atrás; **Inclinación horizontal**: lo gira hacia un lado. Los elementos inclinados se muestran sin perspectiva, así que solo se hacen más bajos o más estrechos. Al aplicar ambas inclinaciones, también quedan oblicuos.

<img width="800" alt="Cuatro elementos de texto sobre el fondo de un menú: uno rotado 15 grados, otro con una inclinación vertical de 45 grados que lo hace más bajo, otro con una inclinación horizontal de 45 grados que lo hace más estrecho y otro con ambas inclinaciones, que queda oblicuo. Unas cajas claras detrás muestran cómo quedarían sin rotación ni inclinación." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_axes.png?raw=true">

# En el editor de diseños

<img width="800" alt="En el editor de diseños, se rota una pegatina de la temporada 3 con el control del círculo que la rodea. Después, se inclina un panel de notas de la versión con los controles de las líneas situadas a su derecha y debajo." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_editor.gif?raw=true">

Selecciona un elemento en el [editor de diseños](/layout-editor) y arrastra sus controles:

- El control del círculo que rodea el elemento lo rota.
- El control de la línea situada a su derecha ajusta su **Inclinación vertical**; el de la línea situada debajo ajusta su **Inclinación horizontal**. El centro de cada línea corresponde a ninguna inclinación.

Mientras arrastras:

- Mantén pulsada la tecla `Shift` para ajustar el movimiento a intervalos: de 45 grados para la rotación y de 15 grados para la inclinación.
- Cerca de 0, los controles se ajustan a 0 para que puedas volver a enderezar fácilmente el elemento.
- En la esquina superior izquierda del elemento se muestran sus valores de rotación e inclinación.

A tener en cuenta:

- El marco de selección sigue recto. Haz clic dentro de él para seleccionar o mover el elemento.
- Los controles solo se muestran cuando hay un elemento seleccionado.
- Los elementos que no tienen un círculo ni líneas no se pueden rotar ni inclinar. Consulta [Elementos que no se pueden rotar ni inclinar](#elementos-que-no-se-pueden-rotar-ni-inclinar).
- **Barra de menú -> Ventana -> Controles de rotación de elementos** y **Controles de inclinación de elementos** ocultan los controles de todos los elementos.

# Valores exactos

Haz clic con el botón derecho en el elemento para acceder a estos ajustes. Cada uno ofrece las opciones **Establecer mediante selector numérico**, **Establecer como texto sin formato** y **Restablecer al valor predeterminado**.

| Ajuste | Función |
|---|---|
| **Rotación** | Los grados que gira en el sentido de las agujas del reloj; por ejemplo, `90` para un cuarto de vuelta. Los valores negativos lo giran en sentido contrario a las agujas del reloj. |
| **Inclinación vertical** | Cuánto se inclina hacia atrás, entre `-60` y `60` grados. |
| **Inclinación horizontal** | Cuánto se gira hacia un lado, entre `-60` y `60` grados. |

Una sola inclinación tiene el mismo aspecto tanto con un valor positivo como con uno negativo. Si se aplican ambas inclinaciones, sus signos determinan hacia qué lado queda oblicuo el elemento.

## Con marcadores de posición

Para rotar o inclinar un elemento mediante una [variable](/variables) u otro [marcador de posición](/placeholders):

1. Haz clic con el botón derecho en el elemento y activa **Modo de rotación avanzada**, **Modo de inclinación vertical avanzada** o **Modo de inclinación horizontal avanzada**.
2. Haz clic en **Rotación**, **Inclinación vertical** o **Inclinación horizontal** y, después, en **Establecer como texto sin formato**. A continuación, introduce el marcador de posición.

Los modos avanzados conservan su propio valor y ocultan el control, para que al arrastrarlo no se sustituya el marcador de posición. Al desactivar uno de estos modos, el elemento recupera su valor anterior.

Un logotipo que gira una vez cada 3,6 segundos con esta **Rotación** en **Modo de rotación avanzada**. Divídelo entre un número mayor que `10` para que gire más despacio:

```
{"placeholder":"calc","values":{"expression":"{"placeholder":"unix_time"} / 10 % 360"}}
```

Una aguja que apunta en la dirección indicada por la variable `needle_angle`, que pueden establecer los botones o un [control deslizante](/elements#slider):

```
{"placeholder":"getvariable","values":{"name":"needle_angle"}}
```

# Clics y ratón

<img width="800" alt="El puntero sobre un botón de Unirse al servidor rotado: no ocurre nada en las esquinas que tendría el botón recto, pero los extremos del botón se iluminan al pasar el puntero por encima." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_hover.gif?raw=true">

Los botones, los controles deslizantes y los enlaces y barras de desplazamiento de los elementos de texto reaccionan al ratón donde se muestran, incluso si están rotados o inclinados. Lo mismo ocurre con los requisitos [**¿Hay un elemento bajo el cursor?**](/conditions#is-element-hovered), [**¿Hay algún elemento bajo el cursor?**](/conditions#is-any-element-hovered) y [**¿Hay algún botón bajo el cursor?**](/conditions#is-any-button-hovered).

> [!NOTE]
> Las casillas de verificación, los campos de texto, los elementos de arrastre y los navegadores siguen reaccionando dentro del recuadro que ocuparían sin rotación ni inclinación. Mantenlos rectos.

# Elementos que no se pueden rotar ni inclinar

- Sin rotación ni inclinación: [Áreas desplazables](/scrollable-areas), [sombreadores GLSL](/elements#glsl-shader), [modelos JSON de bloques o elementos](/elements#blockitem-json-model), [entidades de jugadores](/player-entities) y [elementos vanilla](/vanilla-elements), como los botones de la propia pantalla.
- Se pueden rotar, pero no inclinar: [Información emergente](/elements#tooltip) y [elementos](/elements#item).

Los elementos de un área desplazable sí se pueden rotar e inclinar; lo que no se puede es rotar ni inclinar el área en sí.

Los elementos de [texto de bienvenida](/splash-text) también tienen su propia opción **Rotación**, más abajo en el menú que aparece al hacer clic con el botón derecho, para aplicarles su inclinación característica. Esta opción funciona junto con la rotación descrita en esta página.
