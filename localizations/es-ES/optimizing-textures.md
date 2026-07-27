---
title: Optimización de texturas
description: Cómo optimizar texturas para FancyMenu.
---

# Optimización de texturas para FancyMenu

FancyMenu usa las texturas que proporcionas tal cual, lo que significa que **no** comprime, reescala ni amplía tus archivos de imagen. Para asegurarte de que tus menús se vean nítidos y funcionen bien, es importante optimizar tus texturas cuando las uses en tu interfaz.

# Consejos clave para optimizar texturas

Los siguientes consejos son los pasos básicos más importantes que debes tener en cuenta al trabajar con texturas en FancyMenu.

## 1. Usa la resolución adecuada
- **Evita imágenes de baja resolución**: si una imagen es demasiado pequeña y se estira para encajar en un área mayor, puede verse borrosa.
- **Evita un exceso de alta resolución**: las texturas muy grandes mostradas a un tamaño pequeño también pueden verse deformadas o "raras" y pueden desperdiciar rendimiento.

> [!NOTE]
> 📌 **Consejo:** usa texturas con la resolución a la que se vayan a mostrar en el menú, o muy cerca de ella.

## 2. Conserva la relación de aspecto
- Mantén siempre la relación de aspecto de la imagen al escalarla.
- Estirar una imagen de forma desproporcionada puede provocar artefactos visuales y un aspecto deficiente.

> [!NOTE]
> 📌 **Consejo:** puedes hacer clic derecho en los elementos de imagen y pulsar **Restaurar relación de aspecto** para redimensionarlos a su proporción correcta; después, cuando los redimensiones manualmente, mantén pulsado **MAYÚS** mientras cambias el tamaño para que el redimensionado respete la relación de aspecto del elemento.

## 3. Ten en cuenta el nueve-partido y el mosaico
- Para elementos de interfaz escalables (como paneles o botones), usa las funciones de FancyMenu de [Nueve-partido y mosaico](/nine-slicing-and-tiling).
- Esto garantiza que los bordes de las texturas se mantengan nítidos al redimensionarlas.
