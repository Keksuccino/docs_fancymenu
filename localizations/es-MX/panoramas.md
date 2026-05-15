---
title: Panoramas
description: Cómo crear y usar panoramas personalizados de fondo.
---

# Panoramas cúbicos

FancyMenu permite cargar panoramas cúbicos personalizados de 6 imágenes como fondo para los menús.

Estos panoramas son un formato especial de panorama cúbico que Minecraft usa como fondo en la pantalla de título y se construyen a partir de 6 imágenes (caras) que se renderizan como un cubo (o skybox, para ser más precisos).

> **IMPORTANTE**: Si usas Windows, no olvides activar las [extensiones de archivo](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png), porque de lo contrario más adelante no podrás ver partes importantes de los nombres de archivo.
{.is-warning}

# Crear un panorama

Si no sabes cómo maneja Minecraft sus panoramas de fondo y cómo crearlos, te recomendamos ver [este video](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t).
¡Te dará una muy buena comprensión de cómo funcionan los panoramas en Minecraft y cómo hacer uno!

Después de ver el video, notarás que crear estos panoramas puede tomar algo de tiempo.
Para ahorrarte tiempo, quizá te convenga usar un mod que los cree por ti.
Puedes encontrar algunos buscando `minecraft panorama mod`, pero uno de ellos es [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica) (hecho por mí).

# Preparar el panorama

Después de obtener tus 6 imágenes del panorama, ¡necesitarás moverlas al lugar correcto!

El directorio de panoramas de FancyMenu se encuentra en `.minecraft/config/fancymenu/panoramas`.
Este es el directorio para todos los panoramas que quieras usar en el mod.

## La carpeta del panorama

Cada panorama tiene su propia carpeta.
Necesitarás crear una nueva carpeta en `.minecraft/config/fancymenu/panoramas` si quieres agregar un panorama nuevo.
En mi ejemplo, llamaré a la carpeta `mypanorama`.

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## Contenido de la carpeta

Después de crear la carpeta, necesitarás llenarla.

### Archivo de propiedades
Cada panorama necesita un archivo de propiedades para funcionar.
Este archivo siempre debe llamarse `properties.txt` y necesita que se escriban algunas cosas importantes.

El contenido de un archivo de propiedades de panorama siempre debería verse así:
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
¡Solo se pueden cambiar las variables dentro de la sección `panorama-meta`!

#### name
Este tiene que ser el nombre **único** de tu panorama.
¡No es posible cargar dos panoramas con el mismo nombre!
Usarás este nombre más adelante para identificar tu panorama.

#### speed
La velocidad a la que rota tu panorama.
Este valor es un multiplicador de velocidad. Por ejemplo, `1.0` es la velocidad predeterminada, `2.0` duplica la velocidad y `0.5` la reduce a la mitad.
No se admiten valores negativos; usa valores decimales para disminuir la velocidad.

#### fov
El campo de visión.
El FOV predeterminado es `85.0`.
Usar valores demasiado grandes o pequeños aquí romperá el panorama. Solo prueba distintas opciones para encontrar el FOV que quieras.

#### angle
El ángulo vertical desde el que se ve el panorama.
El ángulo predeterminado es `25.0`.

#### start_rotation
El ángulo de rotación (horizontal) con el que debe iniciar el panorama. Valor entre 0 y 360.

<br>

### Carpeta de imágenes del panorama

La segunda cosa obligatoria que necesita tu carpeta de panorama es la carpeta de imágenes real que contiene las imágenes del panorama.

El nombre de esta carpeta debe ser `panorama`.

Pon todas las imágenes de tu panorama ahí, pero no olvides nombrarlas correctamente como se muestra en el [video](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t) de arriba.

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> ¡Solo se admiten archivos PNG como imágenes del panorama!
{.is-warning}

### Superposición del panorama

El último paso es **opcional** y se puede omitir si no quieres una superposición sobre tu panorama.

Si quieres agregar una viñeta u otros tipos de superposición a tu panorama, puedes añadir una llamada `overlay.png`.
Ten en cuenta que solo se admite PNG para la superposición y que el nombre del archivo siempre debe ser `overlay.png`.

### Revisar todo otra vez

Ahora deberías tener una carpeta ubicada en `.minecraft/config/fancymenu/panoramas`, que contenga un archivo `properties.txt`, otra carpeta llamada `panorama` y quizá una superposición llamada `overlay.png`.

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# Usar el panorama

Después de (re)iniciar el juego o recargar FancyMenu mediante **Customization -> Reload FancyMenu**, ya deberías poder establecer tu panorama como fondo del menú. Para hacerlo, haz clic derecho sobre el fondo del editor de diseño y selecciona **Menu Background**.
