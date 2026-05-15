---
title: Optimización de texturas
description: Cómo optimizar texturas para FancyMenu.
---

# Optimización de texturas para FancyMenu

FancyMenu usa las texturas que proporcionas tal cual, lo que significa que **no** comprime, reduce ni amplía tus archivos de imagen. Para asegurarte de que tus menús se vean nítidos y funcionen bien, es importante optimizar tus texturas cuando las uses en tu interfaz.

# Consejos clave para optimizar texturas

Los siguientes consejos son los pasos básicos más importantes que debes tener en cuenta cuando trabajes con texturas en FancyMenu.

## 1. Usa la resolución correcta
- **Evita imágenes de baja resolución**: Si una imagen es demasiado pequeña y se estira para ocupar un área más grande, puede verse borrosa.
- **Evita exagerar con alta resolución**: Las texturas muy grandes mostradas en un tamaño pequeño también pueden verse distorsionadas o "extrañas" y podrían desperdiciar rendimiento.

> 📌 **Consejo:** Usa texturas a la resolución en la que se mostrarán en el menú, o lo más cercano posible.
{.is-info}

## 2. Conserva la relación de aspecto
- Mantén siempre la relación de aspecto de la imagen cuando la escales.
- Estirar una imagen de forma desproporcionada puede provocar artefactos visuales y un mal aspecto.

> 📌 **Consejo:** Puedes hacer clic derecho en los elementos de imagen y seleccionar **Restaurar relación de aspecto** para redimensionarlos a su proporción correcta; luego, cuando los vuelvas a redimensionar manualmente, mantén presionada **SHIFT** mientras los ajustas para que el cambio de tamaño respete la relación de aspecto del elemento.
{.is-info}

## 3. Considera el nine-slicing y el tiling
- Para elementos de interfaz escalables (como paneles o botones), usa las funciones de FancyMenu de [Nine-Slicing y Tiling](/nine-slicing-and-tiling).
- Esto asegura que los bordes de las texturas se mantengan nítidos al redimensionarlas.
