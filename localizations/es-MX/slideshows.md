---
title: Presentaciones de diapositivas
description: Crea y usa presentaciones de imágenes.
---

# Presentaciones de diapositivas

Cada presentación de diapositivas tiene su propio directorio debajo de:

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` es la instancia activa del launcher, que puede ser diferente del directorio convencional `.minecraft`.

# Estructura del directorio

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # opcional
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

Las imágenes deben usar `.png` o `.jpg`; las demás extensiones, incluida `.jpeg`, se ignoran.

Cuando `randomize = false`, las imágenes se reproducen en orden alfabético sin distinción entre mayúsculas y minúsculas según el nombre del archivo. Usa nombres con ceros a la izquierda, como `image_01.png`, `image_02.png` y `image_10.png`.

# `properties.txt`

```text
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

| Propiedad | Significado |
|---|---|
| `name` | Obligatorio, identificador en tiempo de ejecución sensible a mayúsculas y minúsculas; mantenlo único |
| `width`, `height` | Tamaño base en píxeles escalados por la interfaz y la relación de aspecto de origen |
| `x`, `y` | Posición base de la esquina superior izquierda; los elementos normales y los fondos usan su propia posición, así que déjalos en `0` |
| `duration` | Segundos mínimos entre inicios de transición; incluye el tiempo de desvanecimiento y debe ser mayor que `0` |
| `fadespeed` | Multiplicador de velocidad de desvanecimiento; `1.0` es el valor predeterminado, los valores más altos desvanecen más rápido y el valor debe ser mayor que `0` |
| `randomize` | `true` para selección aleatoria o `false` para el orden por nombre de archivo |

Solo `name` es obligatorio. Los valores predeterminados son `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0` y `randomize = false`. Mantén sin cambios `type = slideshow` y `slideshow-meta`; escribe una línea por cada `key = value` y usa punto para los decimales.

Los diseños seleccionan el valor de `name`, no el nombre del directorio. Los nombres duplicados no se rechazan, y el orden de escaneo de directorios decide qué presentación de diapositivas permanece disponible. Mantén los nombres únicos dentro del directorio de presentaciones de diapositivas.

El modo aleatorio elige de forma independiente en cada transición y evita repetir la misma imagen de inmediato cuando hay varias disponibles. El tiempo usa tiempo real; un desvanecimiento que tarda más que `duration` retrasa la siguiente transición, y volver a una presentación de diapositivas después de ocultarla puede avanzar inmediatamente.

# Usar una presentación de diapositivas

Recarga FancyMenu mediante **Personalización -> Recargar FancyMenu**, o reinicia el cliente. Usa el [elemento de **Presentación de diapositivas**](./elements#slideshow), o haz clic derecho en el fondo del editor de diseños y selecciona [**Fondos de menú**](./menu-backgrounds) -> **Presentación de diapositivas**.
