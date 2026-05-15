---
title: Texto de Splash
description: Cómo crear textos de splash personalizados en FancyMenu.
---

# Elemento de Texto de Splash Personalizado

El elemento de Texto de Splash en FancyMenu es una versión totalmente personalizable de los títulos de splash rebotantes de Minecraft. Conserva el rebote clásico mientras te da control sobre qué aparece, cómo se ve y cuándo se actualiza.

> Ten en cuenta que realmente no puedes personalizar el elemento original de Texto de Splash de Vanilla en la pantalla de título, así que deberías **eliminarlo** y usar en su lugar un elemento de Texto de Splash personalizado.
{.is-warning}

## Agregar y Seleccionar el Elemento
- Abre el editor de diseño y agrega el elemento llamado `Splash Text`.
- Haz clic izquierdo una vez para seleccionarlo y mostrar el cuadro delimitador; luego haz clic derecho para abrir su menú contextual. Todas las opciones de configuración están en ese menú.

## Elegir de Dónde Viene el Texto de Splash
- `Source Mode: Vanilla` conserva los splashes aleatorios clásicos con los que viene Minecraft.
- `Source Mode: Direct Input` te permite escribir tu propio texto mediante `Input Splash Text`. Solo admite una sola línea de texto de splash, pero la línea puede contener marcadores de posición.
- `Source Mode: Text File` toma una línea aleatoria de un archivo `.txt` que elijas con `Set Source Text File`. Cada línea no vacía puede convertirse en el splash activo.
- Cambiar de modo reinicia el texto activo, así que puedes experimentar con seguridad. Si el texto parece quedarse atorado, cambia a otro modo o haz clic en `Refresh On Screen Load: Enabled` para forzar una nueva selección cada vez que se abra el menú.

## Archivo de Texto de Ejemplo
Al usar el modo de origen "Text File", guarda tu lista de splashes como texto plano (UTF-8 sin BOM). Cada línea es un posible splash:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Reemplaza `your_placeholder_id_here` con el marcador de posición que quieras resolver en tiempo de ejecución. FancyMenu elige una línea aleatoria no vacía cada vez que se actualiza el splash.

## Cómo Hacer que se Vea Como Quieres
- Usa `Set Scale` y `Set Rotation` para controlar el tamaño y el ángulo de rotación.
- `Set Text Color` acepta un valor hexadecimal (por ejemplo `#FFFF00`) para que combine con tu tema.
- `Shadow: Enabled` agrega la sombra de texto de Minecraft; desactívala para texto plano.
- `Bouncing: Enabled` mantiene el movimiento de rebote familiar; desactívalo para una etiqueta estática.
- FancyMenu renderiza el splash como un componente completo de Minecraft, así que los códigos de color y otras decoraciones de texto funcionan como se espera.

## Funciones de Texto Dinámico
- Los marcadores de posición se resuelven antes de renderizarse, así que puedes referenciar nombres de jugadores, fechas u otros valores compatibles dentro del texto de splash.
- Como el elemento acepta el JSON serializado de componentes de Minecraft, puedes pegar fragmentos avanzados de JSON en Direct Input o en tu archivo de texto. El elemento los deserializa automáticamente y, si algo falla, regresa al texto literal.

## Solución de Problemas
- El texto vacío en Direct Input muestra `< empty splash element >` mientras editas. Escribe cualquier cosa (incluso un espacio) para quitar la advertencia.
- Si un archivo de texto no contiene líneas válidas, el elemento muestra `ERROR: SPLASH FILE IS EMPTY`. Agrega al menos una línea no vacía y vuelve a abrir la pantalla.
- Los errores de JSON serializado regresan a texto plano. Quédate con la estructura JSON estándar de Mojang o prueba los fragmentos con el comando vanilla `/tellraw` antes de pegarlos.
