---
title: Texto emergente
description: Cómo crear textos emergentes personalizados en FancyMenu.
---

# Elemento de texto emergente personalizado

El elemento de texto emergente de FancyMenu es una versión totalmente personalizable de los títulos emergentes rebotantes de Minecraft. Conserva el rebote clásico, pero te da control sobre qué aparece, cómo se ve y cuándo se actualiza.

> Ten en cuenta que realmente no puedes personalizar el elemento original de texto emergente de Vanilla en la pantalla de título, así que deberías **eliminarlo** y usar en su lugar un elemento de texto emergente personalizado.
{.is-warning}

## Añadir y seleccionar el elemento
- Abre el editor de diseño y añade el elemento llamado `Splash Text`.
- Haz clic izquierdo una vez para seleccionarlo y mostrar el cuadro delimitador; después haz clic derecho para abrir su menú contextual. Todas las opciones de configuración están en ese menú.

## Elegir de dónde sale el texto emergente
- `Source Mode: Vanilla` conserva los textos emergentes aleatorios clásicos que incluye Minecraft.
- `Source Mode: Direct Input` te permite introducir tu propio texto mediante `Input Splash Text`. Solo admite una sola línea de texto emergente, pero esa línea puede contener marcadores de posición.
- `Source Mode: Text File` toma una línea aleatoria de un archivo `.txt` que elijas con `Set Source Text File`. Cada línea no vacía puede convertirse en el texto emergente activo.
- Cambiar de modo restablece el texto activo, así que puedes experimentar con seguridad. Si el texto parece quedarse atascado, cambia a otro modo o haz clic en `Refresh On Screen Load: Enabled` para forzar un nuevo sorteo cada vez que se abra el menú.

## Ejemplo de archivo de texto
Al usar el modo de origen "Text File", guarda tu lista de textos emergentes como texto sin formato (UTF-8 sin BOM). Cada línea es un posible texto emergente:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Sustituye `your_placeholder_id_here` por el marcador de posición que quieras resolver en tiempo de ejecución. FancyMenu elige una línea aleatoria no vacía cada vez que se actualiza el texto emergente.

## Hacer que se vea como tú quieres
- Usa `Set Scale` y `Set Rotation` para controlar el tamaño y el ángulo de rotación.
- `Set Text Color` acepta un valor hexadecimal (por ejemplo `#FFFF00`) para que coincida con tu tema.
- `Shadow: Enabled` añade la sombra de texto de Minecraft; desactívala para un texto plano.
- `Bouncing: Enabled` mantiene el conocido movimiento de rebote; desactívalo para una etiqueta estática.
- FancyMenu renderiza el texto emergente como un componente completo de Minecraft, así que los códigos de color y otras decoraciones de texto funcionan como se espera.

## Funciones de texto dinámico
- Los marcadores de posición se resuelven antes de renderizar, así que puedes hacer referencia a nombres de jugadores, fechas u otros valores compatibles dentro del texto emergente.
- Como el elemento acepta JSON serializado de componentes de Minecraft, puedes pegar fragmentos JSON avanzados en Direct Input o en tu archivo de texto. El elemento los deserializa automáticamente y, si algo falla, recurre al texto literal.

## Solución de problemas
- Si dejas vacío el texto en Direct Input, al editar se mostrará `< empty splash element >`. Escribe cualquier cosa (incluso un espacio) para quitar el aviso.
- Si un archivo de texto no contiene líneas válidas, el elemento mostrará `ERROR: SPLASH FILE IS EMPTY`. Añade al menos una línea no vacía y vuelve a abrir la pantalla.
- Los errores de JSON serializado se sustituyen por texto sin formato. Mantente fiel a la estructura JSON estándar de Mojang o prueba los fragmentos con el comando vanilla `/tellraw` antes de pegarlos.
