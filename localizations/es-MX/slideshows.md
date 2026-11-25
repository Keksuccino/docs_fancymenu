---
title: Presentaciones de diapositivas
description: >-
  Muestra tus imágenes una tras otra, con una transición suave, como fondo del
  menú o en una parte de la pantalla.
sourceBlobSha: 24ba0cbe9184108453b9829b8e6cd48d49a48b12
---

# Presentaciones de diapositivas

Una presentación de diapositivas muestra imágenes una tras otra y hace una transición suave entre ellas, como capturas del mundo de tu modpack.

Puedes mostrarla como [fondo del menú](/menu-backgrounds) de un diseño o en una parte de la pantalla con un [elemento de presentación de diapositivas](/elements#slideshow).

<img width="800" alt="La pantalla de título con una presentación de diapositivas como fondo que pasa de un valle con río a un bosque de cerezos y una costa, con capturas de un mundo de Minecraft" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_title.gif?raw=true">

# Crear una presentación de diapositivas

1. Abre la carpeta `slideshows` en `config/fancymenu/` dentro del directorio de tu juego. **Barra de menú -> Herramientas -> Abrir directorio de FancyMenu** abre `config/fancymenu/`.
2. Crea ahí una carpeta para tu presentación de diapositivas, por ejemplo, `world_tour`. El nombre no importa.
3. Coloca dentro un archivo [`properties.txt`](#propertiestxt) y una carpeta llamada `images` con [tus imágenes](#las-imágenes). El archivo [`overlay.png`](#superposición) es opcional.
4. Recarga FancyMenu desde **Barra de menú -> Personalización -> Recargar FancyMenu**, con `Ctrl + Alt + R` (`Cmd + Alt + R` en macOS) o reinicia el juego.

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

- Solo cuentan los archivos PNG y JPG, con nombres que terminen en `.png` o `.jpg`. Cambia la extensión de los archivos `.jpeg` a `.jpg`.
- Se muestran en orden alfabético según el nombre del archivo. Los números cuentan como letras, así que `10.png` aparece antes que `2.png`. Usa ceros al inicio, como `01`, `02`… `10`.
- Usa el mismo tamaño para todas las imágenes. La primera determina las proporciones de la presentación de diapositivas y las demás se estiran para ajustarse.
- No cuentan los archivos que estén dentro de carpetas en `images`.

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
| `name` | El nombre que usarás para elegir la presentación de diapositivas. Dale un nombre distinto a cada una. |
| `duration` | Segundos entre el cambio de una imagen y el siguiente, incluida la transición. Si la transición tarda más, el siguiente cambio esperará a que termine. |
| `fadespeed` | Qué tan rápido se desvanece una imagen para mostrar la siguiente. Con `1.0`, la transición tarda unos 6 segundos; con `3.0`, unos 2. Debe ser mayor que `0`. |
| `randomize` | `true` muestra las imágenes en orden aleatorio, sin repetir la misma dos veces seguidas. `false` las muestra en el orden de sus nombres de archivo. |

Solo `name` es obligatorio. Los ajustes que omitas usarán `duration = 10.0`, `fadespeed = 1.0` y `randomize = false`. Deja las líneas `type = slideshow` y `slideshow-meta {` tal como están, escribe un ajuste por línea y usa un punto para los decimales, como en `2.5`.

Las presentaciones de diapositivas creadas para versiones anteriores pueden tener las líneas `width`, `height`, `x` y `y`. No hacen nada: el fondo o el elemento determina dónde se muestra la presentación y qué tamaño tiene.

# Superposición

Si colocas un archivo `overlay.png` junto a `properties.txt`, se dibujará sobre cada imagen, estirado para ajustarse al tamaño de la presentación de diapositivas. No se desvanece junto con las imágenes, así que es ideal para marcos, viñetas o un logotipo en una esquina. Las partes transparentes dejan ver las imágenes.

La superposición forma parte de la presentación de diapositivas, así que aparecerá en todos los lugares donde se muestre esta. Si quieres usar las mismas imágenes con y sin marco, crea dos presentaciones de diapositivas.

# Usar una presentación de diapositivas

## Como fondo del menú

<img width="800" alt="Al abrir Fondos del menú, la opción Presentación de diapositivas en el editor de diseños, activar Mostrar fondo y elegir world_tour en Elegir presentación de diapositivas; la vista previa pasa a la siguiente imagen y luego la presentación aparece detrás de los botones de la pantalla de título" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_background.gif?raw=true">

1. En el [editor de diseños](/layout-editor), haz clic derecho en el fondo y abre **Fondos del menú -> Presentación de diapositivas**.
2. Haz clic en **Mostrar fondo** para activarlo.
3. Haz clic en **Nombre de la presentación de diapositivas**, elige una y haz clic en **Listo**. La vista previa de la derecha muestra la presentación en funcionamiento.

**Quitar presentación de diapositivas** la elimina. Para combinarla con otros fondos, consulta [Fondos del menú](/menu-backgrounds).

La presentación de diapositivas se estira para cubrir toda la pantalla. Para conservar las proporciones de las imágenes, activa **Conservar proporción del fondo** en **Fondos del menú**. Así llenará la pantalla, pero se recortarán los lados o la parte superior e inferior.

## Como elemento

<img width="800" alt="La pantalla de título con sus botones a la izquierda y un elemento de presentación de diapositivas a la derecha que muestra capturas de un mundo de Minecraft con transiciones" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/slideshows_element.gif?raw=true">

1. En el editor de diseños, haz clic derecho en un espacio vacío y agrega una presentación de diapositivas con **Nuevo elemento**.
2. Haz clic derecho en el elemento, selecciona **Presentación de diapositivas** y elige una. El elemento adoptará las proporciones de sus imágenes.
3. Muévelo y cambia su tamaño como cualquier otro elemento. **Restaurar proporción** ajusta de nuevo su ancho según su altura para que las imágenes no se estiren.

## Precarga

Cada imagen se carga la primera vez que se muestra, así que las imágenes grandes pueden tardar un momento en aparecer la primera vez. Para cargar todas las imágenes y la superposición mientras inicia el juego, agrega la presentación de diapositivas con **Agregar presentación de diapositivas** en **Barra de menú -> Personalización -> Precargar recursos**. Consulta [Precargar recursos](/preload-layouts#pre-loading-slideshows--panoramas).

# Información útil

- Todo lo que muestre la misma presentación de diapositivas mostrará la misma imagen al mismo tiempo, incluso en distintos menús.
- Una presentación de diapositivas solo se reproduce mientras algo la muestra. Si vuelve a aparecer después de una pausa más larga que su `duration`, pasará de inmediato a la siguiente imagen con una transición.
- Al recargar FancyMenu, todas las presentaciones de diapositivas vuelven a empezar. La primera imagen después del inicio solo dura la mitad que las demás.
- Las presentaciones de diapositivas pertenecen al [perfil](/profiles) cargado.
- Si una presentación no aparece en **Elegir presentación de diapositivas**, no se cargó. El registro del juego, `logs/latest.log`, indica el motivo, como la falta de `name`, `properties.txt` o la carpeta `images`.
- En Windows, activa la visualización de las extensiones de nombre de archivo en el Explorador de archivos para evitar que `properties.txt` termine por accidente como `properties.txt.txt`.
- Un tablero de cuadros morados y negros significa que no se eligió ninguna presentación de diapositivas o que el diseño usa un nombre que ya no existe.
- Si dos presentaciones de diapositivas tienen el mismo `name`, solo aparecerá una.
- La **Superposición de depuración** (`Ctrl + Alt + D`) muestra cuántas presentaciones de diapositivas e imágenes cargó FancyMenu.
