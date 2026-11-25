---
title: Efecto de paralaje
description: >-
  Haz que los fondos y los elementos se muevan un poco con el ratón para dar
  profundidad a tus menús.
sourceBlobSha: f8481cfcc8d4f90bf2f261d436188763c8f23cba
---

# Efecto de paralaje

El efecto de paralaje mueve un poco el fondo de un menú o uno de sus elementos cuando se mueve el ratón. Haz que las capas lejanas se muevan menos y las cercanas, más, y tu menú ganará profundidad.

<img width="640" alt="Una pantalla de título con un paisaje al atardecer en cuatro capas: al mover el ratón, el árbol del primer plano es el que más se mueve, las colinas se mueven menos y las montañas y el cielo apenas se mueven" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_scene.gif?raw=true">

Funciona con [elementos](/elements) y con los [fondos de menú](/menu-backgrounds) de tipo **Imagen** y **Vídeo**.

# Elementos

<img width="640" alt="En una pantalla de título con los botones en una columna a la izquierda, selecciona los cinco botones en el editor de diseños con un clic y Ctrl + clic, establece Efecto de paralaje en Activado e Intensidad del paralaje (X) en 1.0 para todos ellos y, a continuación, guarda y cierra el editor. En la pantalla de título, los botones se mueven un poco al desplazar el ratón de izquierda a derecha, mientras que el logotipo y el paisaje permanecen quietos" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_element_settings.gif?raw=true">

1. Haz clic derecho en el elemento del editor de diseños y desplázate hacia abajo hasta **Efecto de paralaje**.
2. Haz clic en **Efecto de paralaje** para establecerlo en **Activado**.
3. Haz clic en **Intensidad del paralaje (X)** e **Intensidad del paralaje (Y)** para establecer cuánto se mueve.
4. Guarda el diseño y cierra el editor. Los elementos solo se mueven fuera del editor.

Para aplicar el efecto a varios elementos a la vez, [selecciónalos](/layout-editor#selecting) primero (con `Ctrl` + clic añades un elemento a la selección) y, después, haz clic derecho en uno de ellos.

| Ajuste | Función |
|---|---|
| **Efecto de paralaje** | Activa el efecto. |
| **Intensidad del paralaje (X)** | Cuánto se mueve el elemento hacia la izquierda y la derecha, desde `0.0` (nada) hasta `1.0`. Los elementos nuevos tienen un valor de `0.5`. |
| **Intensidad del paralaje (Y)** | Lo mismo, pero hacia arriba y abajo. |
| **Invertir movimiento de paralaje** | Mueve el elemento en la misma dirección que el ratón. Si no activas esta opción, se mueve en la dirección opuesta. |

Con un valor de `1.0`, el elemento se mueve hasta un 5 % del ancho de la pantalla hacia los lados y un 5 % de su alto hacia arriba o abajo cuando el ratón está en el borde de la pantalla. En el centro de la pantalla, los elementos permanecen donde los has colocado.

- Los elementos [anclados](/positioning-elements) a otro elemento con el efecto se mueven con él, y su propio efecto se suma al del elemento al que están anclados.
- **Mantener en pantalla** no mantiene en pantalla los elementos con el efecto, por lo que pueden sobrepasar sus bordes.
- Los elementos estirados no se mueven en la dirección en la que están estirados.
- Los [botones y controles deslizantes de Vanilla](/vanilla-elements) solo se mueven después de que los hayas movido. Con el punto de anclaje **Vanilla (Original)**, permanecen donde los coloca el juego.
- Los botones siguen siendo interactivos donde aparecen.
- Las [áreas desplazables](/scrollable-areas), los elementos que contienen y los elementos de información emergente no tienen efecto de paralaje.

# Fondos de menú

<img width="800" alt="El menú contextual del editor de diseños, con Fondos de menú e Imagen abiertos, muestra Efecto de paralaje, Establecer intensidad del efecto de paralaje (X), Establecer intensidad del efecto de paralaje (Y) e Invertir movimiento de paralaje" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_background_settings.png?raw=true">

1. Haz clic derecho en el fondo del editor y abre **Fondos de menú -> Imagen** (o **Vídeo**).
2. Haz clic en **Efecto de paralaje** para establecerlo en **Activado**.
3. Establece **Establecer intensidad del efecto de paralaje (X)** y **Establecer intensidad del efecto de paralaje (Y)**.

Los fondos reaccionan con mucha más intensidad que los elementos. El fondo aumenta de tamaño según su intensidad, por lo que sus bordes nunca quedan a la vista: con un valor de `1.0`, ocupa el doble que la pantalla y se mueve hasta media pantalla hacia los lados. Mantén los valores bajos: los fondos nuevos tienen un valor de `0.02`, y suele funcionar bien usar valores entre `0.01` y `0.1`.

- **Invertir movimiento de paralaje** mueve el fondo en la misma dirección que el ratón.
- **Deslizar imágenes panorámicas de izquierda a derecha** y **Efecto de paralaje** no pueden estar activados a la vez.
- **Repetir textura** y **Mantener la relación de aspecto del fondo** funcionan junto con este efecto.
- Los fondos también se mueven en el editor de diseños.

# Crear una escena con profundidad

La escena de la parte superior de esta página consta de un cielo y tres capas en la pantalla de título:

1. Dibuja la escena en capas, desde el fondo hacia el primer plano: por ejemplo, el cielo, las montañas, las colinas y el primer plano. Todas las capas, excepto el cielo, deben ser imágenes PNG con partes transparentes.
2. Establece el cielo como fondo de menú de tipo **Imagen** y activa su efecto de paralaje.
3. Añade cada una de las otras capas como un [elemento de imagen](/elements#image), desde el fondo hacia el primer plano, de modo que la más cercana quede encima.
4. Haz que las capas sean un poco más grandes que la pantalla para que sus bordes nunca queden a la vista cuando se muevan. Una capa con un valor de `1.0` necesita un 5 % más del ancho de la pantalla a izquierda y derecha, y un 5 % más de su alto arriba y abajo. Desactiva **Mantener en pantalla** para colocarlas más allá de los bordes de la pantalla.
5. Activa el efecto de paralaje de cada capa: usa intensidades bajas para las capas lejanas y altas para las cercanas.
6. Haz clic derecho en el fondo del editor y establece **Elementos personalizados detrás de los elementos de Vanilla** en **Activado** para que las capas queden detrás de los botones y el logotipo.

Estas son las intensidades de la escena:

| Capa | Intensidad (X) | Intensidad (Y) |
|---|---|---|
| Cielo (fondo de menú) | `0.02` | `0.01` |
| Montañas | `0.35` | `0.2` |
| Colinas | `0.6` | `0.3` |
| Primer plano | `1.0` | `0.5` |

> [!TIP]
> Usa para la intensidad Y aproximadamente la mitad del valor de la intensidad X. Así, el suelo del paisaje no subirá y bajará tanto.

# Información útil

- Todo se mueve en píxeles enteros de la interfaz, por lo que las intensidades bajas producen movimientos en pequeños saltos.
- Los ajustes de intensidad aceptan [marcadores de posición](/placeholders): señala uno y haz clic en **Establecer como texto sin formato** en el pequeño menú que aparece a su lado. Con una [variable](/variables), puedes permitir que los jugadores reduzcan la intensidad del efecto desde tu propio menú de ajustes.
