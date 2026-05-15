---
title: Animaciones (FMA/AFMA)
description: Cómo crear y usar archivos de animación de FancyMenu.
---

# Animaciones

Los archivos AFMA/FMA son archivos de textura animada especiales creados para FancyMenu.
Son prácticamente lo mismo que los APNG, pero mucho más optimizados para FancyMenu.

# Archivos AFMA

FancyMenu 3.9.0 agrega **AFMA** (Advanced FancyMenu Animation), el sucesor de los archivos FMA clásicos.

Los archivos AFMA ya no son archivos ZIP. Usan el formato de animación más reciente de FancyMenu, con mejores tamaños de archivo, menor uso de memoria y mejor rendimiento.

Para texturas animadas nuevas, grandes o complejas, usa **AFMA** en lugar del FMA clásico.

Para crear un archivo AFMA, haz esto:

1. Abre la barra de menú de FancyMenu.
2. Ve a **Tools -> AFMA Creator**.
3. Importa/convierte tus cuadros con el creador.

> [!IMPORTANT]
> Los archivos AFMA no se pueden empaquetar manualmente como los archivos FMA clásicos. Necesitas usar el **AFMA Creator** para empaquetarlos/crearlos.

Los archivos FMA clásicos todavía son compatibles y fueron optimizados en FancyMenu 3.9.0, así que los diseños existentes no necesitan convertirse de inmediato.

# Archivos FMA clásicos

## Crear un FMA

¡Crear un archivo FMA es tan fácil como crear un archivo ZIP! Bueno, eso es principalmente porque _sí_ es un archivo ZIP por debajo.

### Extensiones de archivo

Necesitas ver las extensiones de archivo para poder seguir esta documentación, así que asegúrate de **HABILITAR LAS EXTENSIONES DE ARCHIVO** antes de empezar.

En Windows, esto se hace abriendo una carpeta cualquiera y luego haciendo clic en la flecha en la parte superior derecha para desplegar el menú de abajo.

Después ve a la pestaña **Vista** y habilita **Extensiones de nombre de archivo**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Preparación

Empecemos creando una nueva carpeta para el contenido del archivo FMA.
En este ejemplo, llamemos a la carpeta `fancymenu_animation`.

En esta carpeta, crea dos carpetas más. La primera carpeta **debe** llamarse `frames` y la segunda carpeta **debe** llamarse `intro_frames`.

Ahora, en la misma carpeta, crea un archivo TXT nuevo y cámbiale el nombre a `metadata.json`.
Por favor asegúrate de que el archivo ya no siga siendo un TXT. **Tienes que** cambiar la extensión del archivo a `json`.

Ahora deberías tener una carpeta llamada `fancymenu_animation` y dentro de ella una carpeta llamada `frames`, una carpeta llamada `intro_frames` y un archivo JSON llamado `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### El JSON de metadatos

Este es el archivo que le dice a FancyMenu cómo debe manejar tu textura FMA.
Contiene información como el tiempo de cuadro (cuánto tiempo se muestra un cuadro) y el número de repeticiones.

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
Ahora puedes personalizarlo como quieras.

#### `loop_count`

Esto sirve para controlar cuántas veces debe repetirse la textura (reiniciar su animación).

Si lo estableces en `0`, se repetirá indefinidamente. **Nunca se detendrá**.

Cualquier valor mayor que `0` indica cuántas veces se reproduce la textura. Por ejemplo, si estableces el valor en `1`, la textura solo se reproducirá una vez y luego se detendrá en el último cuadro; `2` significa que se reproducirá dos veces y luego se detendrá en el último cuadro, y así sucesivamente.

#### `frame_time`

Este es el tiempo de cuadro universal en **milisegundos** para los cuadros de la textura animada.
El tiempo de cuadro indica cuánto tiempo permanece visible un cuadro antes de que la animación pase al siguiente.

#### `frame_time_intro`

Esto es básicamente lo mismo que `frame_time`, pero para los cuadros de **intro** de tu textura animada.
Los cuadros de intro son **opcionales** y más adelante aprenderás más sobre ellos.

#### `custom_frame_times`

Esto es **opcional** y se puede usar para sobrescribir el tiempo de cuadro de cuadros específicos (que no sean de intro).
Por ejemplo, quieres que todos tus cuadros se muestren durante `41` milisegundos, así que configuras `frame_time` en `41`, pero quieres que el primer y segundo cuadro se muestren durante `5000` milisegundos.

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

Los cuadros se numeran desde cero, lo que significa que el primer cuadro de la animación es `0`, el segundo es `1` y así sucesivamente.

Debe haber una **coma** al final de cada entrada de tiempo personalizado, **excepto** en la última.

#### `custom_frame_times_intro`

Esto es exactamente lo mismo que `custom_frame_times`, pero en este caso para los cuadros de **intro**. Los cuadros de intro son **opcionales** y más adelante aprenderás más sobre ellos.

Eso es todo para el archivo `metadata.json`. Guárdalo ahora y cierra el editor de texto.

### Los cuadros

> Se recomienda usar **como máximo 200 cuadros** con una **resolución máxima de 1080p** por animación, porque las animaciones consumen mucha memoria y no son videos. Están pensadas para usarse en bucles animados cortos, no para reproducir videos completos con 24 FPS.
{.is-danger}

Los cuadros de tu textura animada van dentro de la carpeta `frames`.

¡Los cuadros deben ser **ARCHIVOS PNG**! ¡**NO HAY SOPORTE PARA JPEG NI OTROS FORMATOS**!

Cada cuadro **debe** llamarse únicamente con el número del cuadro y la extensión del archivo.
El primer cuadro debe llamarse `0.png`, el segundo `1.png`, el tercero `2.png` y así sucesivamente.
¡La textura **NO FUNCIONARÁ** si los cuadros tienen nombres de archivo inválidos!

Para **extraer cuadros de videos**, por favor consulta [esta página de documentación](/ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### La intro

Esta función es **OPCIONAL**.

La función de **intro** de los archivos FMA es una forma especial de reproducir algunos cuadros **antes** de que empiecen a reproducirse los cuadros reales de la carpeta `frames`.

La intro **nunca** se repetirá y solo se reproduce la primera vez que la animación se ejecuta, lo que te permite reproducir algo como una animación de desvanecimiento antes de que la animación principal comience a reproducirse en bucle.

Los cuadros de intro van en la carpeta `intro_frames` y funcionan igual que los cuadros normales:

¡Los cuadros deben ser **ARCHIVOS PNG**! ¡**NO HAY SOPORTE PARA JPEG NI OTROS FORMATOS**!

Cada cuadro **debe** llamarse únicamente con el número del cuadro y la extensión del archivo.
El primer cuadro debe llamarse `0.png`, el segundo `1.png`, el tercero `2.png` y así sucesivamente.
¡La textura **NO FUNCIONARÁ** si los cuadros tienen nombres de archivo inválidos!

### Empaquetar el archivo FMA

Ahora todo lo importante está en la carpeta `fancymenu_animation`, ¡así que ya puedes empaquetar tu archivo FMA!

Empaquetar el archivo FMA básicamente solo significa comprimir el contenido de la carpeta en un archivo ZIP.
El contenido necesita estar en la **RAÍZ DEL ZIP**, así que no puede estar dentro de una carpeta extra dentro del ZIP.

En Windows, la forma más fácil de empaquetar tu contenido FMA en un archivo ZIP es seleccionar todo dentro de la carpeta `fancymenu_animation` y luego hacer **clic derecho** en el archivo `metadata.json`. En el menú contextual que se abre, haz clic en **Enviar a -> Carpeta comprimida (zip)**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Ahora debería haber un nuevo archivo ZIP en la carpeta `fancymenu_animation` llamado `metadata.zip`, `frames.zip` o `intro_frames.zip`.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Cuando abras este archivo, su contenido debería verse así:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Ahora necesitas renombrar el archivo a `fancymenu_animation.fma`. Asegúrate de REEMPLAZAR `.zip` con `.fma`, para que ya no sea un ZIP.

Por supuesto, puedes cambiar la parte `fancymenu_animation` por lo que quieras, pero asegúrate de que siga siendo un archivo `.fma`.

¡Eso es todo! ¡Ahora tienes un archivo FMA que (con suerte) funciona!

# Usar archivos AFMA y FMA en FancyMenu

> [!IMPORTANT]
> Los archivos AFMA/FMA se consideran **texturas animadas**, así que se agregan mediante entradas de **Imagen**. Casi todo lo que acepte imágenes (PNG, JPEG, GIF, etc.) también aceptará archivos FMA y AFMA.

Puedes usar archivos AFMA/FMA como cualquier otro formato de textura/imagen animada. FancyMenu lo ve como una imagen normal, así que puedes usarlo en cualquier lugar donde puedas asignar una textura, como **elementos de imagen o fondos de menú de imagen**.

Asegúrate de que el archivo AFMA/FMA esté en la carpeta `/config/fancymenu/assets/`, porque FancyMenu solo puede tomar texturas y otros recursos de su carpeta `assets`.
