---
title: APNG
description: Cómo crear imágenes APNG compatibles con FancyMenu.
---
# Imágenes PNG animadas

> [!NOTE]
> Para animaciones grandes o complejas, es preferible usar [archivos AFMA](./fma). Watermedia V3 y Watermedia Binaries V3 pueden acelerar la decodificación de APNG/GIF cuando están disponibles, pero AFMA sigue siendo el formato de animación preferido de FancyMenu.


Los APNG son una versión animada de las imágenes PNG, lo que permite tener las mismas características que un GIF, ¡pero con calidad PNG completa y sin pérdidas!

FancyMenu tiene compatibilidad integrada con APNG, pero es un poco exigente con qué APNG se admiten.
Necesita APNG **sin comprimir** y **sin entrelazado**.

# Crear animaciones APNG

Te sorprendería lo difícil que es encontrar un buen editor de APNG, especialmente con opciones para desactivar la compresión y el entrelazado.

Una muy buena opción como editor es [ScreenToGif](https://www.screentogif.com/), que en realidad es una herramienta para grabar GIF y APNG de la pantalla, ¡pero también es genial para crear APNG normales saltándote la parte de la grabación y cargándolos directamente en el editor!

## Abrir el editor

Lo primero que verás al abrir [ScreenToGif](https://www.screentogif.com/) es esta pantalla. Haz clic aquí en **Editor**.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Cargar los fotogramas

Ahora necesitas tus fotogramas PNG. Arrástralos y suéltalos en el editor.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Retardo entre fotogramas

Para configurar el retardo entre fotogramas, selecciona el/los fotograma(s) que quieras editar, cambia a la pestaña **Edit** y, en la sección **Delay (Duration)**, haz clic en **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Repetición

El comportamiento de repetición se puede configurar en el menú **Save As**. Consulta el siguiente paso para ver cómo abrir este menú.

## Exportar el APNG

Ahora ya puedes volver a la pestaña **File** y hacer clic en **Save As**.

En el menú de guardado, asegúrate de:
- Establecer el tipo de archivo como **APNG** (primer ajuste; quizá primero tengas que desplazarte hasta la parte superior del menú)
- Desactivar **Detect Unchanged Pixels**

> [!NOTE]
> ¡También puedes configurar el **comportamiento de repetición** en ese menú! Si desactivas **Looped Apng**, el APNG no se repetirá en absoluto, y al activarlo podrás elegir entre un número concreto de repeticiones o repetición infinita.

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Usar el APNG en FancyMenu

Ahora copia tu archivo APNG a `<game-directory>/config/fancymenu/assets/`. Después podrás usarlo para casi todo lo que acepte imágenes.

> [!WARNING]
> ¡Es **realmente importante** que el nombre del archivo APNG termine en `.apng`!
> FancyMenu no podrá identificar la imagen como APNG si no termina en `.apng`.

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
