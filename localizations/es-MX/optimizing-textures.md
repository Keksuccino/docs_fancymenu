---
title: Optimización de texturas
description: Cómo optimizar texturas para FancyMenu.
---

# Optimización de texturas para FancyMenu

FancyMenu usa las texturas que proporcionas tal cual, lo que significa que **no** comprime, reduce ni aumenta el tamaño de tus archivos de imagen. Para asegurarte de que tus menús se vean nítidos y funcionen bien, es importante optimizar tus texturas cuando las uses en tu interfaz.

# Consejos clave para optimizar texturas

Los siguientes consejos son los pasos básicos más importantes que debes tener en cuenta al trabajar con texturas en FancyMenu.

## 1. Usa la resolución correcta
- **Evita imágenes de baja resolución**: Si una imagen es demasiado pequeña y se estira para ajustarse a un área más grande, puede verse borrosa.
- **Evita excederte con la alta resolución**: Las texturas muy grandes que se muestran en un tamaño pequeño también pueden verse distorsionadas o "raras" y pueden desperdiciar rendimiento.

> [!NOTE]
> 📌 **Consejo:** Usa texturas con la resolución que tendrán, o muy cerca de ella, en el menú.

## 2. Conserva la relación de aspecto
- Mantén siempre la relación de aspecto de la imagen al escalarla.
- Estirar una imagen de forma desproporcionada puede generar artefactos visuales y una mala apariencia.

> [!NOTE]
> 📌 **Consejo:** Puedes hacer clic derecho en los elementos de imagen y seleccionar **Restaurar relación de aspecto** para redimensionarlos a su relación de aspecto correcta. Luego, cuando los vuelvas a redimensionar manualmente, mantén presionada **SHIFT** mientras redimensionas para que el cambio respete la relación de aspecto del elemento.

## 3. Considera el Nine-Slicing y el Tiling
- Para elementos de interfaz escalables (como paneles o botones), usa las funciones de FancyMenu de [Nine-Slicing y Tiling](/nine-slicing-and-tiling).
- Esto garantiza que los bordes de las texturas se mantengan nítidos al redimensionarlas.
