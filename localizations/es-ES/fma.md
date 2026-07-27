---
title: Animaciones (FMA/AFMA)
description: Cómo crear y usar archivos de animación de FancyMenu.
---

# Animaciones

Los archivos AFMA y FMA son formatos de textura animada creados para FancyMenu.

# Archivos AFMA

**AFMA** (Advanced FancyMenu Animation) es el sucesor de los archivos FMA clásicos.

AFMA utiliza un formato que no es ZIP, con archivos más pequeños, menor uso de memoria y mejor rendimiento que el FMA clásico.

Para texturas animadas grandes o complejas, usa **AFMA** en lugar del FMA clásico.

Crea archivos AFMA con el creador integrado:

1. Abre la barra de menús de FancyMenu.
2. Ve a **Tools -> AFMA Creator**.
3. Importa/convierte tus fotogramas con el creador.

> [!IMPORTANT]
> Los archivos AFMA no se pueden empaquetar manualmente. Usa **Tools -> AFMA Creator**.

Los archivos FMA clásicos siguen siendo compatibles, así que los diseños existentes no necesitan convertirse de inmediato.

# Archivos FMA clásicos

## Crear un FMA

Un archivo FMA clásico es un archivo ZIP con la extensión `.fma`.

### Extensiones de archivo

Activa las extensiones de archivo en tu gestor de archivos antes de crear o cambiar el nombre de los archivos de abajo.

En Windows, abre el Explorador de archivos y activa **View -> File name extensions**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Preparación

Crea una carpeta llamada `fancymenu_animation` para el contenido del archivo.

Crea dentro un directorio obligatorio `frames` y un directorio opcional `intro_frames`.

En la misma carpeta, crea `metadata.json`. Asegúrate de que su extensión sea `.json` y no `.txt`.

La carpeta debe contener ahora `frames/`, `intro_frames/` y `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### El JSON de metadatos

Abre `metadata.json` en un editor de texto y usa esta plantilla:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

Edita los valores según sea necesario.

#### `loop_count`

Controla cuántas veces se reproduce la animación. Usa `0` para que se repita indefinidamente. Un valor positivo la reproduce ese número de veces y luego mantiene el último fotograma.

#### `frame_time`

Define durante cuánto tiempo permanece visible cada fotograma normal, en milisegundos.

#### `frame_time_intro`

Define el tiempo de fotograma para los fotogramas opcionales de **intro**.

#### `custom_frame_times`

Sobrescribe opcionalmente la duración de fotogramas normales individuales. Este ejemplo mantiene visibles los fotogramas `0` y `1` durante `5000` milisegundos, mientras que los demás fotogramas usan `frame_time`:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Los índices de fotograma empiezan en cero: el primer fotograma es `0`, el segundo es `1`, y así sucesivamente.

Añade una coma después de cada entrada de tiempo personalizado salvo en la última.

#### `custom_frame_times_intro`

Usa el mismo formato que `custom_frame_times`, pero se aplica a los fotogramas opcionales de intro.

Guarda `metadata.json`.

### Los fotogramas

> [!CAUTION]
> Mantén las animaciones FMA clásicas en 200 fotogramas o menos y a 1080p como máximo. Usa [Video](./video) para contenido largo o con una alta tasa de fotogramas.

Coloca los fotogramas normales en `frames/`. Deben ser archivos PNG con nombres secuenciales desde `0.png`, como `0.png`, `1.png` y `2.png`. No se admiten otros formatos ni nombres.

Para extraer fotogramas de un vídeo, consulta [Extracción de fotogramas con FFmpeg](./ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### La intro

Coloca los fotogramas opcionales de intro en `intro_frames/`. Siguen las mismas reglas de nomenclatura PNG que los fotogramas normales, se reproducen una vez antes de la secuencia normal y no se repiten.

### Empaquetar el archivo FMA

Crea un ZIP que contenga el contenido de la carpeta. `metadata.json`, `frames/` y el directorio opcional `intro_frames/` deben estar en la raíz del ZIP, no dentro de otro directorio.

En Windows, selecciona el contenido de `fancymenu_animation`, haz clic derecho sobre la selección y elige **Send to -> Compressed (zipped) folder**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Localiza el archivo ZIP resultante.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

El contenido de su raíz debería verse así:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Cambia el nombre del archivo a `fancymenu_animation.fma`, reemplazando la extensión `.zip`. El nombre base se puede cambiar, pero la extensión `.fma` es obligatoria.

El archivo renombrado ya está listo para usarse como archivo FMA.

# Usar archivos AFMA y FMA en FancyMenu

> [!IMPORTANT]
> Los archivos AFMA/FMA son texturas animadas, así que añádelos mediante entradas de [**Image**](./elements#image). Casi todo lo que acepta imágenes también acepta archivos AFMA y FMA.

Usa archivos AFMA/FMA en cualquier lugar que acepte una imagen, incluidos [Image elements](./elements#image) y [Image menu backgrounds](./menu-backgrounds).

Guarda el archivo AFMA/FMA en `<game-directory>/config/fancymenu/assets/` para que aparezca en el selector de recursos locales de FancyMenu.
