---
title: Panoramas
description: >-
  Crea tus propios fondos panorámicos giratorios a partir de seis imágenes, como
  el de la pantalla de título de Minecraft.
sourceBlobSha: e1f9ab155301f1b88df58dd8414eeee5714cfba6
---

# Panoramas

Un panorama es un fondo que gira lentamente a tu alrededor, como el de la pantalla de título de Minecraft. Está formado por seis imágenes que crean un cubo alrededor del espectador.

Puedes mostrar tus propios panoramas como [fondo del menú](/menu-backgrounds) de una interfaz, o en lugar del panorama de Minecraft en todos los menús.

<img width="800" alt="La pantalla de título frente a un panorama que gira lentamente de una cabaña de madera en un claro del bosque al atardecer, con un jardín, un cobertizo para leña y un gallinero" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_title.gif?raw=true">

> [!TIP]
> Puedes usar gratis el panorama de esta página para hacer pruebas y en tus propios modpacks: [forest_homestead.zip](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/forest_homestead.zip) (4 MB). Descomprímelo en `config/fancymenu/panoramas/` y vuelve a cargar FancyMenu.

# Crear un panorama

1. Abre la carpeta `panoramas` dentro de `config/fancymenu/`, en el directorio del juego. **Barra de menú -> Herramientas -> Abrir directorio de FancyMenu** abre `config/fancymenu/`.
2. Crea una carpeta para el panorama, por ejemplo `forest_homestead`. El nombre no importa.
3. Añade un archivo `properties.txt` y una carpeta llamada `panorama` con las [seis imágenes](#las-seis-imágenes). También puedes añadir un archivo `overlay.png`, aunque es opcional.
4. Vuelve a cargar FancyMenu con **Barra de menú -> Personalización -> Volver a cargar FancyMenu** o con `Ctrl + Alt + R` (`Cmd + Alt + R` en macOS), o reinicia el juego.

```text
config/fancymenu/panoramas/
└── forest_homestead/
    ├── properties.txt
    ├── overlay.png
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

# Las seis imágenes

Cada imagen es una cara del cubo:

<img width="796" alt="Las seis imágenes del panorama forest_homestead dispuestas como un cubo desplegado: la imagen superior encima de la frontal, las imágenes izquierda, frontal, derecha y trasera en una fila, y la imagen inferior debajo de la frontal" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_cube.png?raw=true">

| Imagen | Cara |
|---|---|
| `panorama_0.png` | Frontal |
| `panorama_1.png` | Derecha |
| `panorama_2.png` | Trasera |
| `panorama_3.png` | Izquierda |
| `panorama_4.png` | Superior |
| `panorama_5.png` | Inferior |

- Las cuatro caras laterales te rodean en este orden: el borde derecho de cada imagen continúa en el borde izquierdo de la siguiente, y el borde derecho de `panorama_3.png` se une al borde izquierdo de `panorama_0.png`.
- El borde inferior de la imagen superior toca el borde superior de la imagen frontal. El borde superior de la imagen inferior toca el borde inferior de la imagen frontal.
- Las seis imágenes deben ser archivos PNG del mismo tamaño. Hazlas cuadradas, por ejemplo, de 1024 × 1024.
- FancyMenu no suaviza las imágenes, así que el pixel art se mantiene nítido.

Este es el mismo diseño que usa Minecraft para su propio panorama, así que también funcionan los panoramas creados para Minecraft.

# properties.txt

```text
type = panorama

panorama-meta {
  name = forest_homestead
  speed = 2.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Ajuste | Función |
|---|---|
| `name` | Nombre que usarás para elegir el panorama. Cada panorama debe tener un nombre distinto. |
| `speed` | Velocidad de giro. Con `1.0` da una vuelta completa en unos 4 minutos; `2.0` gira el doble de rápido. Con `0` permanece inmóvil. Los valores superiores a `10.0` no aumentan la velocidad. |
| `fov` | Cuánto panorama cabe en la pantalla, en grados de arriba abajo. Los valores más pequeños acercan la imagen. |
| `angle` | Cuánto apunta hacia abajo, en grados. Con `0` mira directamente al horizonte; los valores negativos apuntan hacia arriba. |
| `start_rotation` | Punto desde el que empieza a girar, en grados, de `0` a `360`. Con `0`, la imagen frontal queda en el centro al empezar. |

Solo es obligatorio indicar `name`. Los ajustes que omitas usarán los valores `speed = 1.0`, `fov = 85.0`, `angle = 25.0` y `start_rotation = 0`. Mantén las líneas `type = panorama` y `panorama-meta {` tal como están, escribe un ajuste por línea y usa un punto para los decimales, por ejemplo, `1.5`.

# Superposición

Si colocas un archivo `overlay.png` junto a `properties.txt`, se dibujará sobre el panorama y se estirará para cubrir toda la pantalla. No gira con el panorama, así que está pensado para elementos como un viñeteado, un marco o un tinte de color. Las partes transparentes dejan ver el panorama.

# Usar un panorama

## Como fondo del menú

<img width="800" alt="Abrir Fondos del menú, Panorama cúbico en el editor de interfaces, activar Mostrar fondo y elegir forest_homestead en Elegir panorama; después, el panorama gira detrás de los botones de la pantalla de título" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/panoramas_background.gif?raw=true">

1. En el [editor de interfaces](/layout-editor), haz clic derecho en el fondo y abre **Fondos del menú -> Panorama cúbico**.
2. Haz clic en **Mostrar fondo** para activarlo.
3. Haz clic en **Nombre del panorama**, elige tu panorama y haz clic en **Listo**. La vista previa de la derecha muestra cómo gira.

**Borrar panorama** lo quita. Para combinarlo con otros fondos, consulta [Fondos del menú](/menu-backgrounds).

## En todos los menús

**Barra de menú -> Personalización -> Personalizaciones globales -> Panorama de fondo de menú personalizado -> Elegir panorama** muestra tu panorama en lugar del de Minecraft, tanto en la pantalla de título como en todos los menús antes de entrar en un mundo. Consulta [Personalizaciones globales](/global-customizations#menu-backgrounds).

## Precarga

Un panorama grande puede tardar un momento en aparecer la primera vez. Para cargarlo mientras se inicia el juego, añádelo con **Añadir panorama cúbico** en **Barra de menú -> Personalización -> Precargar recursos**. Consulta [Precargar recursos](/preload-layouts#pre-loading-slideshows--panoramas).

# Información útil

- Los panoramas giran hacia la derecha: la imagen frontal se desplaza hacia la izquierda y aparece la imagen derecha.
- Todos los menús que muestran el mismo panorama comparten su rotación, por lo que sigue girando sin interrupciones al cambiar de uno a otro. Se pausa mientras no se muestra en ningún menú.
- Al volver a cargar FancyMenu, todos los panoramas empiezan de nuevo en su valor `start_rotation`.
- Los panoramas pertenecen al [perfil](/profiles) cargado.
- Si un panorama no aparece en **Elegir panorama**, es que no se ha cargado. El registro del juego, `logs/latest.log`, indica el motivo, como la falta de `name` o de alguna imagen.
- Un tablero de ajedrez morado y negro significa que aún no se ha elegido ningún panorama, que sus seis imágenes no tienen el mismo tamaño o que la interfaz usa un nombre de panorama que ya no existe.
- Si dos panoramas tienen el mismo valor `name`, solo aparecerá uno.
