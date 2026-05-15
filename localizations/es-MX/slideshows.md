---
title: Presentaciones
description: Cómo crear y usar presentaciones.
---

# Presentaciones

FancyMenu te permite agregar presentaciones y mostrarlas en menús y como fondos de menú.

> **IMPORTANTE**: Si usas Windows, no olvides activar las [extensiones de archivo](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10), porque de lo contrario más adelante no podrás ver partes importantes de los nombres de archivo.
{.is-warning}

# Crear una presentación

Cada presentación debe estar en su propia carpeta **dentro** del directorio de presentaciones ubicado en `/config/fancymenu/slideshows/`.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

Para que el sistema reconozca una presentación como tal, necesita tener un archivo de propiedades ubicado en la carpeta de la presentación; así que, si has nombrado la carpeta de tu presentación `myslideshow`, el archivo de propiedades debe estar en `/config/fancymenu/slideshows/myslideshow/properties.txt`.

**¡Este archivo siempre debe llamarse `properties.txt`!**
Por ahora, solo crea el archivo de propiedades **vacío** y pasa al siguiente paso.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## Agregar imágenes

Una presentación necesita imágenes (obvio), ¡así que vamos a agregar algunas!

> ¡Las imágenes de tu presentación deben ser archivos **PNG**! ¡Nada de JPEG, GIF, APNG o FMA!
{.is-danger}

Todas las imágenes de tu presentación van en una carpeta extra **dentro** de la carpeta de tu presentación (`myslideshow` en el ejemplo anterior).
El nombre de esta carpeta debe ser `images`.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Ahora coloca todas las imágenes de tu presentación en la carpeta `images`.
Se ordenan alfabéticamente (respetando los números), así que nómbralas algo como `image_1.png`, `image_2.png` y así sucesivamente.
En mi ejemplo, `image_1.png` se mostraría primero y `image_2.png` después.

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## Agregar contenido al archivo de propiedades

Al principio creaste un archivo vacío `properties.txt` en la carpeta de tu presentación.
Ahora hay que llenarlo con información importante.

Cada archivo de propiedades de una presentación debería verse así:

```
type = slideshow

slideshow-meta {
   name = cool_slideshow
   width = 1920
   height = 1080
   x = 0
   y = 0
   duration = 5.0
   fadespeed = 12.0
   randomize = false
}
```
¡Solo se pueden cambiar las variables dentro de la sección `slideshow-meta`!

### name

Este es el nombre, o mejor dicho el identificador, de tu presentación.
Los nombres de las presentaciones deben ser **únicos**, así que no es posible tener dos presentaciones con el mismo nombre.

### width | height

El `width` (ancho) y `height` (alto) base de tu presentación.
FancyMenu los usa para calcular la relación de aspecto.

### x | y

La posición `x` e `y` de tu presentación.
Más que nada para depuración, así que simplemente configura ambos en `0`.

### duration

La duración en **segundos** durante la cual se muestra cada imagen antes de pasar a la siguiente.
¡Admite valores decimales!

### fadespeed

La velocidad de la animación de desvanecimiento al cambiar a la siguiente imagen.
Este valor es un multiplicador de velocidad. Por ejemplo, `1.0` es la velocidad predeterminada, `2.0` duplica la velocidad y `0.5` la hará la mitad de rápida que la predeterminada.
No se admiten valores negativos.

### randomize

Si las imágenes de la presentación deben reproducirse en orden aleatorio (`true`) o no (`false`).

# Usar la presentación

Ya terminaste todos los pasos importantes y tu presentación debería estar lista, ¡así que probémosla!

Para cargar tu presentación nueva (o editada) en FancyMenu, recarga el mod mediante **Personalización -> Recargar FancyMenu**.

Ahora puedes usar tu presentación en el elemento **Slideshow** o como fondo de menú (clic derecho en el fondo del editor de diseño -> **Menu Background**).
