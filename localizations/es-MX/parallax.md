---
title: Efecto Parallax
description: >-
  Haz que los fondos y los elementos se muevan un poco con el mouse para darle
  profundidad a tus menús.
sourceBlobSha: f8481cfcc8d4f90bf2f261d436188763c8f23cba
---

# Efecto Parallax

El efecto Parallax mueve un poco el fondo de un menú o un elemento cuando mueves el mouse. Haz que las capas lejanas se muevan menos y las cercanas más para darle profundidad a tu menú.

<img width="640" alt="Una pantalla de título con un paisaje al atardecer en cuatro capas: mientras el mouse se mueve, el árbol del primer plano es el que más se mueve; las colinas, menos; y las montañas y el cielo, apenas un poco" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_scene.gif?raw=true">

Funciona con [elementos](/elements) y con los [fondos de menú](/menu-backgrounds) de tipo **Image** y **Video**.

# Elementos

<img width="640" alt="En una pantalla de título con los botones en una columna a la izquierda, seleccionar los cinco botones en el editor de diseño con un clic y Ctrl + clic, establecer Efecto Parallax en Activado e Intensidad de Parallax (X) en 1.0 para todos, y después guardar y cerrar el editor. En la pantalla de título, los botones se mueven un poco cuando el mouse va de izquierda a derecha, mientras que el logo y el paisaje no se mueven" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_element_settings.gif?raw=true">

1. Haz clic derecho en el elemento dentro del editor de diseño y desplázate hacia abajo hasta **Efecto Parallax**.
2. Haz clic en **Efecto Parallax** para cambiarlo a **Activado**.
3. Haz clic en **Intensidad de Parallax (X)** y **Intensidad de Parallax (Y)** para definir cuánto se mueve.
4. Guarda el diseño y cierra el editor. Los elementos solo se mueven fuera del editor.

Para aplicar el efecto a varios elementos a la vez, primero [selecciónalos](/layout-editor#selecting) (`Ctrl` + clic agrega un elemento a la selección) y luego haz clic derecho en uno de ellos.

| Ajuste | Qué hace |
|---|---|
| **Efecto Parallax** | Activa el efecto. |
| **Intensidad de Parallax (X)** | Cuánto se mueve el elemento de izquierda a derecha, de `0.0` (nada) a `1.0`. Los elementos nuevos tienen `0.5`. |
| **Intensidad de Parallax (Y)** | Lo mismo, pero hacia arriba y abajo. |
| **Invertir movimiento Parallax** | Mueve el elemento en la misma dirección que el mouse. Si no lo activas, se mueve en la dirección opuesta. |

Con un valor de `1.0`, cuando el mouse está en el borde de la pantalla, un elemento se mueve hasta un 5 % del ancho de la pantalla hacia los lados y un 5 % de su altura hacia arriba o abajo. En el centro de la pantalla, los elementos permanecen donde los colocaste.

- Los elementos [anclados](/positioning-elements) a otro elemento que tiene el efecto se mueven junto con él, y su propio efecto se suma al de ese elemento.
- **Mantener en pantalla** no mantiene en pantalla los elementos que tienen el efecto, así que pueden rebasar los bordes.
- Los elementos estirados no se mueven en la dirección en la que están estirados.
- Los [botones y controles deslizantes de Vanilla](/vanilla-elements) solo se mueven después de que tú los hayas movido. Si el punto de anclaje es **Vanilla (Original)**, permanecen donde los coloca el juego.
- Los botones siguen siendo interactivos donde se muestran.
- Las [áreas desplazables](/scrollable-areas), los elementos que contienen y los elementos Tooltip no tienen efecto Parallax.

# Fondos de menú

<img width="800" alt="El menú del editor de diseño que aparece al hacer clic derecho, con Fondos de menú e Image abiertos, muestra Efecto Parallax, Establecer intensidad de efecto Parallax (X), Establecer intensidad de efecto Parallax (Y) e Invertir movimiento Parallax" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_background_settings.png?raw=true">

1. Haz clic derecho en el fondo del editor y abre **Fondos de menú -> Image** (o **Video**).
2. Haz clic en **Efecto Parallax** para cambiarlo a **Activado**.
3. Define **Establecer intensidad de efecto Parallax (X)** y **Establecer intensidad de efecto Parallax (Y)**.

Los fondos reaccionan con mucha más intensidad que los elementos. El fondo aumenta de tamaño según su intensidad para que nunca se vean sus bordes: con `1.0`, mide el doble que la pantalla y se mueve hasta la mitad del ancho de la pantalla hacia los lados. Mantén los valores bajos: los fondos nuevos tienen `0.02`, y los valores entre `0.01` y `0.1` suelen funcionar bien.

- **Invertir movimiento Parallax** mueve el fondo en la misma dirección que el mouse.
- **Deslizar imágenes anchas de izquierda a derecha** y **Efecto Parallax** no pueden estar activados al mismo tiempo.
- **Repetir textura** y **Conservar proporción del fondo** funcionan junto con este efecto.
- Los fondos también se mueven en el editor de diseño.

# Crear una escena con profundidad

La escena de la parte superior de esta página tiene un cielo y tres capas en la pantalla de título:

1. Dibuja la escena en capas, de la más lejana a la más cercana, como el cielo, las montañas, las colinas y el primer plano. Todas las capas, excepto el cielo, deben ser imágenes PNG con partes transparentes.
2. Establece el cielo como fondo de menú **Image** y activa su efecto Parallax.
3. Agrega las demás capas como [elementos Image](/elements#image), de la más lejana a la más cercana, para que la más cercana quede encima.
4. Haz que las capas sean un poco más grandes que la pantalla para que sus bordes nunca se vean cuando se muevan. Una capa con intensidad `1.0` necesita un 5 % adicional del ancho de la pantalla a la izquierda y a la derecha, y un 5 % adicional de la altura arriba y abajo. Desactiva **Mantener en pantalla** para poder colocarlas más allá de los bordes.
5. Activa el efecto Parallax de cada capa: usa intensidades bajas para las capas lejanas y altas para las cercanas.
6. Haz clic derecho en el fondo del editor y establece **Elementos personalizados detrás de Vanilla** en **Activado**, para que las capas queden detrás de los botones y el logo.

Estas son las intensidades de la escena:

| Capa | Intensidad (X) | Intensidad (Y) |
|---|---|---|
| Cielo (fondo de menú) | `0.02` | `0.01` |
| Montañas | `0.35` | `0.2` |
| Colinas | `0.6` | `0.3` |
| Primer plano | `1.0` | `0.5` |

> [!TIP]
> Procura que la intensidad Y sea aproximadamente la mitad de la intensidad X. Así, el suelo del paisaje no rebotará tanto hacia arriba y abajo.

# Información útil

- Todo se mueve en píxeles enteros de la interfaz gráfica, así que las intensidades bajas producen movimientos en pasos pequeños.
- Los ajustes de intensidad aceptan [marcadores de posición](/placeholders): señala uno y haz clic en **Establecer como texto sin formato** en el menú pequeño que aparece a su lado. Con una [variable](/variables), puedes permitir que los jugadores reduzcan el efecto desde tu propio menú de ajustes.
