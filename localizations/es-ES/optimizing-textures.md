---
title: Optimización de texturas
description: Cómo optimizar texturas para FancyMenu.
---

# Optimización de texturas para FancyMenu

FancyMenu utiliza las texturas que proporcionas tal cual, lo que significa que **no** comprime, reduce ni amplía tus archivos de imagen. Para asegurarte de que tus menús se vean nítidos y funcionen bien, es importante optimizar tus texturas cuando las uses en tu interfaz.

# Consejos clave para optimizar texturas

Los siguientes consejos son los pasos básicos más importantes que debes tener en cuenta al trabajar con texturas en FancyMenu.

## 1. Usa la resolución adecuada
- **Evita imágenes de baja resolución**: Si una imagen es demasiado pequeña y se estira para encajar en un área más grande, puede verse borrosa.
- **Evita el exceso de alta resolución**: Las texturas muy grandes mostradas a un tamaño pequeño también pueden verse distorsionadas o "raras" y pueden desperdiciar rendimiento.

> 📌 **Consejo:** Usa texturas con la resolución a la que se mostrarán en el menú o muy cercana a ella.
{.is-info}

## 2. Conserva la proporción de aspecto
- Mantén siempre la proporción de aspecto de la imagen al escalarla.
- Estirar una imagen de forma desproporcionada puede provocar artefactos visuales y un aspecto deficiente.

> 📌 **Consejo:** Puedes hacer clic derecho en los elementos de imagen y pulsar en **Restaurar proporción de aspecto** para redimensionarlos a su proporción correcta; después, cuando los redimensiones manualmente, mantén pulsado **SHIFT** mientras redimensionas para que el cambio de tamaño respete la proporción de aspecto del elemento.
{.is-info}

## 3. Ten en cuenta el nueve-slicing y el mosaico
- Para elementos de interfaz escalables (como paneles o botones), usa las funciones de FancyMenu de [Nueve-slicing y mosaico](/nine-slicing-and-tiling).
- Esto garantiza que los bordes de las texturas se mantengan nítidos al cambiarles el tamaño.
