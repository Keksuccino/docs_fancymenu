---
title: Presentaciones
description: Crea y usa presentaciones de imágenes.
---

# Presentaciones

Cada presentación tiene su propio directorio en:

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` es la instancia activa del launcher, que puede diferir del directorio `.minecraft` convencional.

# Estructura de directorios

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

Cuando `randomize = false`, las imágenes se reproducen en orden alfabético sin distinguir mayúsculas de minúsculas según el nombre del archivo. Usa nombres con ceros a la izquierda, como `image_01.png`, `image_02.png` y `image_10.png`.

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
| `width`, `height` | Tamaño base en píxeles escalados por la GUI y la relación de aspecto de la fuente |
| `x`, `y` | Posición base de la esquina superior izquierda; los elementos normales y los fondos usan su propia posición, así que déjalos en `0` |
| `duration` | Número mínimo de segundos entre el inicio de transiciones; incluye el tiempo de fundido y debe ser mayor que `0` |
| `fadespeed` | Multiplicador de velocidad del fundido; `1.0` es el valor predeterminado, valores más altos funden más rápido y el valor debe ser mayor que `0` |
| `randomize` | `true` para selección aleatoria o `false` para el orden por nombre de archivo |

Solo `name` es obligatorio. Los valores predeterminados son `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0` y `randomize = false`. Mantén `type = slideshow` y `slideshow-meta` sin cambios; escribe un `key = value` por línea y usa un punto para los decimales.

Los diseños seleccionan el valor de `name`, no el nombre del directorio. Los nombres duplicados no se rechazan, y el orden del escaneo de directorios decide qué presentación permanece disponible. Mantén los nombres únicos dentro del directorio de presentaciones.

El modo aleatorio elige de forma independiente en cada transición y evita repetir inmediatamente cuando hay varias imágenes disponibles. El temporizador usa tiempo real; un fundido que tarda más que `duration` retrasa la siguiente transición, y volver a una presentación después de ocultarla puede avanzar a la siguiente inmediatamente.

# Usar una presentación

Recarga FancyMenu a través de **Personalización -> Recargar FancyMenu**, o reinicia el cliente. Usa el [elemento **Presentación**](./elements#slideshow), o haz clic derecho en el fondo del editor de diseños y selecciona [**Fondos del menú**](./menu-backgrounds) -> **Presentación**.
