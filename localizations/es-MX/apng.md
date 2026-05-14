---
title: APNG
description: Cómo crear imágenes APNG compatibles con FancyMenu.
---

# Imágenes PNG animadas

> Para animaciones nuevas grandes o complejas, prefiere [archivos AFMA/FMA](/fma). FancyMenu 3.9.0 puede usar Watermedia V3 + Watermedia Binaries V3 para un decodificado de APNG/GIF más rápido cuando estén disponibles, pero AFMA sigue siendo el formato de animación preferido de FancyMenu.
{.is-info}


Los APNG son una versión animada de las imágenes PNG, lo que hace posible tener las mismas funciones que un GIF, ¡pero con la calidad PNG completa y sin pérdida!

FancyMenu tiene compatibilidad integrada con APNG, pero es un poco exigente con los APNG que admite.
Necesita APNGs **sin compresión** que **no** estén entrelazados.

# Crear animaciones APNG

Te sorprendería lo difícil que es encontrar un buen editor de APNG, especialmente con opciones para desactivar la compresión y el entrelazado.

Una excelente opción de editor es [ScreenToGif](https://www.screentogif.com/), que en realidad es una herramienta para grabar GIFs y APNGs de tu pantalla, ¡pero también es genial para crear APNGs normales omitiendo la parte de grabación y cargando directamente en el editor!

## Abrir el editor

Lo primero que ves después de abrir [ScreenToGif](https://www.screentogif.com/) es esta pantalla. Haz clic en **Editor** aquí.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Cargar los fotogramas

Ahora necesitas tus fotogramas PNG. Arrástralos y suéltalos en el editor.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Retardo de fotogramas

Para configurar el retraso entre fotogramas, selecciona el/los fotograma(s) que quieras editar, cambia a la pestaña **Edit** y, en la sección **Delay (Duration)**, haz clic en **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Repetición

El comportamiento de repetición se puede configurar en el menú **Save As**. Consulta el siguiente paso para ver cómo abrir este menú.

## Exportar el APNG

Ahora estás listo para volver a la pestaña **File** y hacer clic en **Save As**.

En el menú de guardado, asegúrate de:
- Establecer el tipo de archivo en **APNG** (primera opción; quizá tengas que desplazarte hasta la parte superior del menú primero)
- Desactivar **Detect Unchanged Pixels**

> ¡También puedes configurar el **comportamiento de repetición** en ese menú! Desactivar **Looped Apng** hará que el APNG no se repita en absoluto, y al activarlo puedes elegir entre un número específico de repeticiones o repetición infinita.
{.is-info}

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Usar el APNG en FancyMenu

Ahora puedes copiar tu archivo APNG a `/config/fancymenu/assets/`. Después podrás usarlo para casi todo lo que acepte imágenes.

> Es **realmente importante** que el nombre del archivo APNG termine en `.apng`.
> FancyMenu no podrá identificar la imagen como APNG si no termina en `.apng`.
{.is-warning}

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
