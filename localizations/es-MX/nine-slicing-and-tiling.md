---
title: Nine-Slicing y Tiling
description: Escala texturas con borde o repite texturas sin costuras.
---

# Nine-Slicing y Tiling

Nine-slicing conserva las esquinas y los bordes de una textura mientras estira su centro. Tiling repite una textura en lugar de estirarla.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Regiones de nine-slice" style="max-width:500px;height:auto;" />

# Compatibilidad con Nine-Slicing

| Área | Destinos compatibles |
|---|---|
| Widgets | Texturas de [Botón](./elements#button) y [Deslizador](./elements#slider); [estilos globales de botón y deslizador](./global-customizations#button-visuals) |
| Imágenes y paneles | [Elementos de imagen](./elements#image) |
| Barras de progreso | [Texturas de relleno y fondo](./elements#progress-bar) |
| Tooltips | [Texturas personalizadas de fondo](./elements#tooltip) |

# Configuración de Nine-Slicing

1. Configura la textura de destino.
2. Activa la opción **Nine-Slice**.
3. Ajusta los tamaños de borde para que coincidan con el área fija del borde en la textura de origen.
4. Redimensiona el elemento y ajusta los valores del borde si las esquinas o los bordes se distorsionan.

Los ajustes de Botón e Imagen usan tamaños de borde X/Y. Las Barras de progreso y los Tooltips exponen valores de borde separados cuando es necesario.

# Compatibilidad con Tiling

Las texturas repetidas están disponibles para:

- [Elementos de imagen](./elements#image).
- [Fondos de imagen del menú](./menu-backgrounds).
- [Texturas del encabezado y pie de la lista desplazable](./customizing-scrollable-screens).

Activa **Repetir textura** en un elemento de imagen o en un fondo de imagen. Para pantallas desplazables, usa las opciones de repetición en el menú de personalización del encabezado/pie.

Usa una textura de origen sin costuras; los bordes que no coincidan crearán líneas visibles entre los mosaicos.

Nine-slicing y repetición son modos separados. Si ambos se muestran para un destino, elige el que coincida con el comportamiento de escalado deseado.
