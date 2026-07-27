---
title: Nueve cortes y mosaico
description: Escala texturas con bordes o repite texturas sin juntas.
---

# Nueve cortes y mosaico

El sistema de nueve cortes conserva las esquinas y los bordes de una textura mientras estira su centro. El mosaico repite una textura en lugar de estirarla.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Nine-slice regions" style="max-width:500px;height:auto;" />

# Compatibilidad con nueve cortes

| Área | Elementos compatibles |
|---|---|
| Widgets | Texturas de [Botón](./elements#button) y [Deslizador](./elements#slider); [estilos globales de botón y deslizador](./global-customizations#button-visuals) |
| Imágenes y paneles | [Elementos de imagen](./elements#image) |
| Barras de progreso | [Texturas de relleno y fondo](./elements#progress-bar) |
| Tooltips | [Texturas de fondo personalizadas](./elements#tooltip) |

# Configurar nueve cortes

1. Establece la textura de destino.
2. Activa la opción **Nine-Slice**.
3. Ajusta los tamaños de borde para que coincidan con el área fija del borde en la textura original.
4. Redimensiona el elemento y ajusta los valores del borde si las esquinas o los bordes se deforman.

Los ajustes de Botón e Imagen usan tamaños de borde X/Y. Las Barras de progreso y los Tooltips exponen valores separados para cada borde cuando es necesario.

# Compatibilidad con mosaico

Las texturas repetidas están disponibles para:

- [Elementos de imagen](./elements#image).
- [Fondos de menú de imagen](./menu-backgrounds).
- [Texturas de cabecera y pie de listas desplazables](./customizing-scrollable-screens).

Activa **Repeat Texture** en un elemento de imagen o en un fondo de imagen. En pantallas desplazables, usa las opciones de repetición en el menú de personalización de la cabecera/pie.

Usa una textura de origen sin juntas; los bordes que no coinciden crean líneas visibles entre los mosaicos.

El sistema de nueve cortes y la repetición son modos distintos. Si se muestran ambas opciones para un destino, elige la que coincida con el comportamiento de escalado previsto.
