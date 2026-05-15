---
title: Animaciones (FMA/AFMA)
description: Cómo crear y usar archivos de animación de FancyMenu.
---

# Animaciones

Los archivos AFMA/FMA son archivos de textura animada especiales creados para FancyMenu.
Son prácticamente lo mismo que los APNG, pero mucho más optimizados para FancyMenu.

# Archivos AFMA

FancyMenu 3.9.0 añade **AFMA** (Advanced FancyMenu Animation), el sucesor de los archivos FMA clásicos.

Los archivos AFMA ya no son archivos ZIP. Usan el formato de animación más reciente de FancyMenu, con mejores tamaños de archivo, menor uso de memoria y mejor rendimiento.

Para texturas animadas nuevas, grandes o complejas, usa **AFMA** en lugar del FMA clásico.

Para crear un archivo AFMA, haz lo siguiente:

1. Abre la barra de menús de FancyMenu.
2. Ve a **Tools -> AFMA Creator**.
3. Importa/convierte tus fotogramas con el creador.

> [!IMPORTANT]
> Los archivos AFMA no se pueden empaquetar manualmente como los archivos FMA clásicos. Debes usar el **AFMA Creator** para empaquetarlos/crearlos.

Los archivos FMA clásicos siguen siendo compatibles y se optimizaron en FancyMenu 3.9.0, así que los diseños existentes no necesitan convertirse de inmediato.

# Archivos FMA clásicos

## Cómo crear un FMA

¡Crear un archivo FMA es tan fácil como crear un archivo ZIP! Bueno, eso es sobre todo porque, internamente, _sí_ es un ZIP.

### Extensiones de archivo

Necesitas ver las extensiones de archivo para poder seguir esta documentación, así que asegúrate de **HABILITAR LAS EXTENSIONES DE ARCHIVO** antes de empezar.

En Windows, esto se hace abriendo cualquier carpeta y luego haciendo clic en la flecha de la parte superior derecha para desplegar el menú de abajo.

Después, ve a la pestaña **Vista** y activa **Extensiones de nombre de archivo**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Preparación

Empecemos creando una nueva carpeta para el contenido del archivo FMA.
En este ejemplo, llamemos a la carpeta `fancymenu_animation`.

Dentro de esta carpeta, crea otras dos carpetas. La primera **tiene** que llamarse `frames` y la segunda **tiene** que llamarse `intro_frames`.

Ahora, en la misma carpeta, crea un nuevo archivo TXT y renómbralo a `metadata.json`.
Asegúrate de que el archivo no siga siendo un TXT. **Tienes que** cambiar la extensión del archivo a `json`.

Ahora deberías tener una carpeta llamada `fancymenu_animation` y dentro de ella una carpeta llamada `frames`, una carpeta llamada `intro_frames` y un archivo JSON llamado `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### El JSON de metadatos

Este es el archivo que indica a FancyMenu cómo debe gestionar tu textura FMA.
Contiene información como los tiempos de fotograma (cuánto tiempo se muestra un fotograma) y el número de bucles.

Abre el archivo `metadata.json` con un editor de texto.

Copia este texto en el archivo:

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

Esta es la plantilla básica de cómo debe verse el archivo.
Ahora puedes personalizarlo a tu gusto.

#### `loop_count`

Esto sirve para controlar cuántas veces debe repetirse la textura (reiniciar su animación).

Si se establece en `0`, se repetirá indefinidamente. _Nunca_ se detendrá.

Cualquier valor mayor que `0` indica cuántas veces se reproduce la textura. Por ejemplo, establecer el valor en `1` significa que la textura solo se reproducirá una vez y luego se detendrá en el último fotograma; `2` significa que se reproducirá dos veces y luego se detendrá en el último fotograma, _y así sucesivamente_.

#### `frame_time`

Este es el tiempo de fotograma universal en **milisegundos** para los fotogramas de la textura animada.
El tiempo de fotograma indica cuánto tiempo permanece visible un fotograma antes de que la animación pase al siguiente.

#### `frame_time_intro`

Es básicamente lo mismo que `frame_time`, pero para los fotogramas de **introducción** de tu textura animada.
Los fotogramas de introducción son **opcionales** y más adelante aprenderás más sobre ellos.

#### `custom_frame_times`

Esto es **opcional** y se puede usar para sobrescribir el tiempo de fotograma de fotogramas concretos (no de introducción).
Por ejemplo, quieres que todos tus fotogramas se muestren durante `41` milisegundos, así que estableces `frame_time` en `41`, pero quieres que el primer y el segundo fotograma se muestren durante `5000` milisegundos.

En ese caso, harías esto:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    0: 5000,
    1: 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Los fotogramas empiezan en cero, lo que significa que el primer fotograma de la animación es `0`, el segundo es `1` y así sucesivamente.

Debe haber una **coma** al final de cada entrada de tiempo de fotograma personalizado, **excepto** en la última.

#### `custom_frame_times_intro`

Es exactamente lo mismo que `custom_frame_times`, pero en este caso para los fotogramas de **introducción**. Los fotogramas de introducción son **opcionales** y más adelante aprenderás más sobre ellos.

Eso es todo para el archivo `metadata.json`. Guárdalo ahora y cierra el editor de texto.

### Los fotogramas

> Se recomienda usar **como máximo 200 fotogramas** con una **resolución máxima de 1080p** por animación, porque las animaciones consumen mucha memoria y no son vídeos. Están pensadas para usarse en bucles animados cortos, no para reproducir vídeos completos a 24 FPS.
{.is-danger}

Los fotogramas de tu textura animada van en la carpeta `frames`.

¡Los fotogramas deben ser **ARCHIVOS PNG**! ¡**NO HAY COMPATIBILIDAD CON JPEG NI OTROS FORMATOS**!

Cada fotograma **tiene** que llamarse simplemente con el número del fotograma y la extensión del archivo.
El primer fotograma debe llamarse `0.png`, el segundo `1.png`, el tercero `2.png` y así sucesivamente.
¡La textura **NO FUNCIONARÁ** si los fotogramas tienen nombres de archivo incorrectos!

Para **extraer fotogramas de vídeos**, consulta [esta página de documentación](/ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### La introducción

Esta función es **OPCIONAL**.

La función de **introducción** de los archivos FMA es una forma especial de reproducir algunos fotogramas **antes** de que empiecen a reproducirse los fotogramas reales de la carpeta `frames`.

La introducción **nunca** se repetirá en bucle y solo se reproduce la primera vez que se ejecuta la animación, lo que te permite reproducir algo como una animación de fundido de entrada antes de que la animación real empiece a reproducirse en bucle.

Los fotogramas de introducción van en la carpeta `intro_frames` y funcionan igual que los fotogramas normales:

¡Los fotogramas deben ser **ARCHIVOS PNG**! ¡**NO HAY COMPATIBILIDAD CON JPEG NI OTROS FORMATOS**!

Cada fotograma **tiene** que llamarse simplemente con el número del fotograma y la extensión del archivo.
El primer fotograma debe llamarse `0.png`, el segundo `1.png`, el tercero `2.png` y así sucesivamente.
¡La textura **NO FUNCIONARÁ** si los fotogramas tienen nombres de archivo incorrectos!

### Empaquetar el archivo FMA

Ahora todo lo importante está en la carpeta `fancymenu_animation`, así que ya puedes empaquetar tu archivo FMA.

Empaquetar el archivo FMA básicamente significa comprimir el contenido de la carpeta en un archivo ZIP.
El contenido debe estar en la **RAÍZ DEL ZIP**, así que no puede estar dentro de una carpeta adicional en el ZIP.

En Windows, la forma más sencilla de empaquetar el contenido FMA en un archivo ZIP es seleccionar todo en la carpeta `fancymenu_animation` y luego hacer **clic derecho** sobre el archivo `metadata.json`. En el menú contextual que se abre, haz clic en **Send To -> Compressed ZIP Folder**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Ahora debería haber un nuevo archivo ZIP en la carpeta `fancymenu_animation` llamado `metadata.zip`, `frames.zip` o `intro_frames.zip`.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Al abrir este archivo, su contenido debería verse así:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Ahora tienes que renombrar el archivo a `fancymenu_animation.fma`. Asegúrate de **REEMPLAZAR** `.zip` por `.fma`, para que ya no sea un ZIP.

Por supuesto, puedes cambiar la parte `fancymenu_animation` por lo que quieras, pero asegúrate de que siga siendo un archivo `.fma`.

¡Eso es todo! ¡Ya tienes un archivo FMA que, con suerte, funciona!

# Usar archivos AFMA y FMA en FancyMenu

> [!IMPORTANT]
> Los archivos AFMA/FMA se consideran **texturas animadas**, así que se añaden mediante entradas de **Imagen**. Casi todo lo que acepta imágenes (PNG, JPEG, GIF, etc.) también aceptará archivos FMA y AFMA.

Puedes usar archivos AFMA/FMA como cualquier otro formato de textura/imagen animada. FancyMenu lo ve como una imagen normal, así que puedes usarlo en cualquier lugar donde puedas asignar una textura, como **elementos de imagen o fondos de menú de imagen**.

Asegúrate de que el archivo AFMA/FMA esté en la carpeta `/config/fancymenu/assets/`, porque FancyMenu solo puede cargar texturas y otros recursos desde su carpeta `assets`.
