---
title: Texto de bienvenida
description: Cómo crear textos de bienvenida personalizados en FancyMenu.
---

# Elemento de texto de bienvenida personalizado

El elemento de texto de bienvenida de FancyMenu es una versión totalmente personalizable de los títulos rebotantes de Minecraft. Mantiene el rebote clásico, a la vez que te da control sobre qué aparece, cómo se ve y cuándo se actualiza.

> [!WARNING]
> Ten en cuenta que realmente no puedes personalizar el elemento original de texto de bienvenida de Vanilla en la pantalla de título, así que deberías **eliminarlo** y usar en su lugar un elemento de texto de bienvenida personalizado.

## Añadir y seleccionar el elemento
- Abre el editor de diseños y añade el elemento llamado `Splash Text`.
- Haz clic izquierdo una vez para seleccionarlo y mostrar el cuadro delimitador; después, haz clic derecho para abrir su menú contextual. Todas las opciones de configuración están en ese menú.

## Elegir de dónde sale el texto de bienvenida
- `Source Mode: Vanilla` mantiene los textos aleatorios clásicos que incluye Minecraft.
- `Source Mode: Direct Input` te permite introducir tu propio texto mediante `Input Splash Text`. Solo admite una sola línea de texto de bienvenida, pero la línea puede contener marcadores de posición.
- `Source Mode: Text File` toma una línea aleatoria de un archivo `.txt` que eliges con `Set Source Text File`. Cada línea no vacía puede convertirse en el texto activo.
- Cambiar de modo restablece el texto activo, así que puedes experimentar con seguridad. Si el texto parece quedarse fijo, cambia a otro modo o haz clic en `Refresh On Screen Load: Enabled` para forzar un nuevo resultado cada vez que se abra el menú.

## Archivo de texto de ejemplo
Cuando uses el modo de origen "Text File", guarda tu lista de textos como texto sin formato (UTF-8 sin BOM). Cada línea es un posible texto de bienvenida:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Sustituye `your_placeholder_id_here` por el marcador de posición que quieras resolver en tiempo de ejecución. FancyMenu elige una línea aleatoria no vacía cada vez que se actualiza el texto de bienvenida.

## Hacer que se vea como quieras
- Usa `Set Scale` y `Set Rotation` para controlar el tamaño y el ángulo de rotación.
- `Set Text Color` acepta un valor hexadecimal (por ejemplo `#FFFF00`) para adaptarse a tu tema.
- `Shadow: Enabled` añade la sombra proyectada de Minecraft; desactívalo para un texto plano.
- `Bouncing: Enabled` mantiene el movimiento de balanceo característico; desactívalo para una etiqueta estática.
- FancyMenu renderiza el texto de bienvenida como un componente completo de Minecraft, así que los códigos de color y otras decoraciones de texto funcionan como se espera.

## Funciones de texto dinámico
- Los marcadores de posición se resuelven antes de renderizar, así que puedes referenciar nombres de jugador, fechas u otros valores compatibles dentro del texto de bienvenida.
- Como el elemento acepta JSON serializado de componentes de Minecraft, puedes pegar fragmentos avanzados de JSON en Direct Input o en tu archivo de texto. El elemento los deserializa automáticamente y, si algo falla, vuelve al texto literal.

## Solución de problemas
- Un texto vacío en Direct Input muestra `< empty splash element >` mientras lo editas. Escribe cualquier cosa (incluso un espacio) para quitar el aviso.
- Si un archivo de texto no contiene líneas válidas, el elemento muestra `ERROR: SPLASH FILE IS EMPTY`. Añade al menos una línea no vacía y vuelve a abrir la pantalla.
- Los errores de JSON serializado vuelven a texto sin formato. Ateniéndote a la estructura JSON estándar de Mojang o probando los fragmentos con el comando vanilla `/tellraw` antes de pegarlos.
