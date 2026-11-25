---
title: Pases de diapositivas
description: >-
  Muestra tus propias imágenes una tras otra, con una transición suave entre
  ellas, como fondo del menú o en una parte de la pantalla.
sourceBlobSha: 24ba0cbe9184108453b9829b8e6cd48d49a48b12
---

# Pases de diapositivas

Un pase de diapositivas muestra imágenes una tras otra y pasa suavemente de una a la siguiente, como si fueran capturas del mundo de tu modpack.

Puedes mostrarlo como [fondo del menú](/menu-backgrounds) de un diseño o en una parte de la pantalla con un [elemento Pase de diapositivas](/elements#slideshow).

<img width="800" alt="La pantalla de título con un pase de diapositivas como fondo que pasa de un valle con río a un bosque de cerezos y una costa; son capturas de un mundo de Minecraft" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_title.gif?raw=true">

# Crear un pase de diapositivas

1. Abre la carpeta `slideshows` de `config/fancymenu/` en el directorio del juego. **Barra de menú -> Herramientas -> Abrir directorio de FancyMenu** abre `config/fancymenu/`.
2. Crea una carpeta para el pase de diapositivas, por ejemplo, `world_tour`. El nombre da igual.
3. Añade un archivo [`properties.txt`](#propertiestxt) y una carpeta llamada `images` con [tus imágenes](#the-images). El archivo [`overlay.png`](#overlay) es opcional.
4. Recarga FancyMenu con **Barra de menú -> Personalización -> Recargar FancyMenu**, con `Ctrl + Alt + R` (`Cmd + Alt + R` en macOS) o reinicia el juego.

```text
config/fancymenu/slideshows/
└── world_tour/
    ├── properties.txt
    ├── overlay.png
    └── images/
        ├── 01_river_valley.png
        ├── 02_cherry_grove.png
        └── 03_coast.png
```

# Las imágenes

- Solo se tienen en cuenta los archivos PNG y JPG, cuyos nombres terminen en `.png` o `.jpg`. Cambia la extensión de los archivos `.jpeg` a `.jpg`.
- Se muestran en el orden alfabético de sus nombres de archivo. Los números cuentan como letras, así que `10.png` aparece antes que `2.png`. Añade ceros al principio, como `01`, `02`… `10`.
- Todas las imágenes deben tener el mismo tamaño. La primera determina la forma del pase de diapositivas y las demás se estiran para adaptarse.
- No se tienen en cuenta los archivos que estén en subcarpetas de `images`.

# properties.txt

```text
type = slideshow

slideshow-meta {
  name = world_tour
  duration = 5.0
  fadespeed = 5.0
  randomize = false
}
```

| Ajuste | Qué hace |
|---|---|
| `name` | El nombre con el que seleccionarás el pase de diapositivas. Asigna un nombre distinto a cada uno. |
| `duration` | Segundos entre un cambio de imagen y el siguiente, incluida la transición. Si la transición dura más, el siguiente cambio esperará a que termine. |
| `fadespeed` | La velocidad a la que una imagen se funde con la siguiente. Con `1.0`, la transición dura unos 6 segundos; con `3.0`, unos 2. Debe ser superior a `0`. |
| `randomize` | `true` muestra las imágenes en orden aleatorio, sin repetir la misma dos veces seguidas. `false` las muestra en el orden de sus nombres de archivo. |

Solo es obligatorio indicar `name`. Los ajustes que omitas usarán `duration = 10.0`, `fadespeed = 1.0` y `randomize = false`. Deja las líneas `type = slideshow` y `slideshow-meta {` tal como están, escribe un ajuste por línea y usa un punto para los decimales, como en `2.5`.

Los pases de diapositivas creados para versiones anteriores pueden incluir las líneas `width`, `height`, `x` e `y`. No hacen nada: el fondo o el elemento determina dónde se muestra el pase de diapositivas y qué tamaño tiene.

# Superposición

Si colocas un archivo `overlay.png` junto a `properties.txt`, se dibujará sobre cada imagen y se estirará para ajustarse al tamaño del pase de diapositivas. No se desvanece con las imágenes, por lo que sirve para añadir marcos, viñetas o un logotipo en una esquina. Las partes transparentes dejan ver las imágenes.

La superposición pertenece al pase de diapositivas, así que aparece en todos los lugares donde se muestre. Si quieres usar las mismas imágenes con y sin marco, crea dos pases de diapositivas.

# Usar un pase de diapositivas

## Como fondo del menú

<img width="800" alt="Se abre Fondos del menú; se selecciona Pase de diapositivas en el editor de diseños, se activa Mostrar fondo y se elige world_tour en Elegir pase de diapositivas. La vista previa pasa a la siguiente imagen y, después, el pase aparece detrás de los botones de la pantalla de título" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_background.gif?raw=true">

1. En el [editor de diseños](/layout-editor), haz clic con el botón derecho en el fondo y abre **Fondos del menú -> Pase de diapositivas**.
2. Haz clic en **Mostrar fondo** para activarlo.
3. Haz clic en **Nombre del pase de diapositivas**, selecciona el que quieras y pulsa **Listo**. La vista previa de la derecha muestra el pase en funcionamiento.

**Quitar pase de diapositivas** lo elimina. Para combinarlo con otros fondos, consulta [Fondos del menú](/menu-backgrounds).

El pase de diapositivas se estira para cubrir toda la pantalla. Para conservar la proporción de sus imágenes, activa **Conservar relación de aspecto del fondo** en **Fondos del menú**. Así cubrirá la pantalla y se recortará por los lados o por arriba y abajo.

## Como elemento

<img width="800" alt="La pantalla de título, con los botones a la izquierda y un elemento Pase de diapositivas a la derecha que muestra capturas de un mundo de Minecraft mediante transiciones" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_element.gif?raw=true">

1. En el editor de diseños, haz clic con el botón derecho en un espacio libre y añade un pase de diapositivas con **Nuevo elemento**.
2. Haz clic con el botón derecho en el elemento, selecciona **Pase de diapositivas** y elige el que quieras. El elemento adopta la forma de sus imágenes.
3. Muévelo y cambia su tamaño como cualquier otro elemento. **Restaurar relación de aspecto** ajusta de nuevo su anchura para que se adapte a su altura y las imágenes no se estiren.

## Precarga

El pase de diapositivas carga cada imagen la primera vez que la muestra, así que las imágenes grandes pueden tardar un momento en aparecer la primera vez. Para cargar todas las imágenes y la superposición al iniciar el juego, añade el pase con **Añadir pase de diapositivas** en **Barra de menú -> Personalización -> Precargar recursos**. Consulta [Precargar recursos](/preload-layouts#pre-loading-slideshows--panoramas).

# Información útil

- Todo lo que muestre el mismo pase de diapositivas mostrará la misma imagen al mismo tiempo, incluso en menús distintos.
- Un pase de diapositivas solo funciona mientras haya algo que lo muestre. Si vuelve a aparecer después de una pausa superior a su `duration`, pasará inmediatamente a la siguiente imagen.
- Al recargar FancyMenu, todos los pases de diapositivas vuelven a empezar. La primera imagen solo se muestra durante la mitad de tiempo que las demás.
- Los pases de diapositivas pertenecen al [perfil](/profiles) cargado.
- Si un pase no aparece en **Elegir pase de diapositivas**, es que no se ha cargado. El registro del juego, `logs/latest.log`, indica el motivo; por ejemplo, que falte `name`, `properties.txt` o la carpeta `images`.
- En Windows, activa la visualización de las extensiones de archivo en el Explorador de archivos para evitar que `properties.txt` acabe llamándose `properties.txt.txt` por accidente.
- Un patrón de cuadros morados y negros indica que no se ha seleccionado ningún pase de diapositivas o que el diseño utiliza un nombre de pase que ya no existe.
- Si dos pases de diapositivas tienen el mismo `name`, solo aparecerá uno.
- La **Superposición de depuración** (`Ctrl + Alt + D`) muestra cuántos pases de diapositivas e imágenes ha cargado FancyMenu.
