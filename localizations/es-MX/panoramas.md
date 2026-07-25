---
title: Panoramas
description: Crea y usa panoramas cúbicos de seis imágenes.
---
# Panoramas cúbicos

Cada panorama tiene su propio directorio debajo de:

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` es la instancia activa del lanzador, que puede ser distinta del directorio convencional `.minecraft`.

# Estructura del directorio

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # opcional
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

Las seis imágenes de las caras deben ser archivos PNG con los nombres exactos que se muestran arriba, y las seis deben tener dimensiones idénticas. La diferencia entre mayúsculas y minúsculas en el nombre del archivo puede importar en algunos sistemas operativos.

Agrega un `overlay.png` opcional junto a `properties.txt` para una viñeta u otra superposición de panorama completo.

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = nombre_de_tu_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Propiedad | Significado |
|---|---|
| `name` | Obligatorio, identificador en tiempo de ejecución sensible a mayúsculas y minúsculas; mantenlo único |
| `speed` | Multiplicador de velocidad de rotación; `1.0` es el valor predeterminado |
| `fov` | Campo de visión en grados |
| `angle` | Ángulo vertical de visión en grados |
| `start_rotation` | Rotación horizontal inicial en grados |

Solo `name` es obligatorio. Los valores opcionales que falten usarán los valores predeterminados mostrados en el ejemplo. Mantén `type = panorama` y `panorama-meta` sin cambios; escribe un `key = value` por línea y usa punto para los decimales.

Los nombres duplicados no se rechazan, y el orden de análisis de directorios decide qué panorama permanece disponible. Mantén los nombres únicos dentro del directorio de panoramas. Los nombres de panoramas y presentaciones usan listas separadas.

# Usar un panorama

Recarga FancyMenu desde **Personalización -> Recargar FancyMenu**, o reinicia el cliente. Luego haz clic derecho en el fondo del editor de diseño y selecciona [**Fondos de menú**](./menu-backgrounds) -> **Panorama cúbico**.
