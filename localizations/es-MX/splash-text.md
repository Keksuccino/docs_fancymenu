---
title: Texto de Pantalla de Inicio
description: Cómo crear textos de pantalla de inicio personalizados en FancyMenu.
---

# Elemento de Texto de Pantalla de Inicio Personalizado

El elemento de Texto de Pantalla de Inicio en FancyMenu es una versión totalmente personalizable de los textos flotantes rebotantes de Minecraft. Conserva el rebote característico mientras te da control sobre qué aparece, cómo se ve y cuándo se actualiza.

> [!WARNING]
> Ten en cuenta que realmente no puedes personalizar el elemento original de Texto de Pantalla de Inicio de Vanilla en la pantalla de título, así que debes **eliminarlo** y usar en su lugar un elemento de Texto de Pantalla de Inicio personalizado.

## Agregar y Seleccionar el Elemento
- Abre el editor de diseño y agrega el elemento llamado `Splash Text`.
- Haz clic izquierdo una vez para seleccionarlo y mostrar el cuadro delimitador, luego haz clic derecho para abrir su menú contextual. Todas las opciones de configuración están en ese menú.

## Elegir de Dónde Proviene el Texto
- `Source Mode: Vanilla` mantiene los textos aleatorios clásicos que incluye Minecraft.
- `Source Mode: Direct Input` te permite escribir tu propio texto mediante `Input Splash Text`. Esto solo admite una sola línea de texto de inicio, pero la línea puede contener marcadores de posición.
- `Source Mode: Text File` toma una línea aleatoria de un archivo `.txt` que elijas con `Set Source Text File`. Cada línea que no esté vacía puede convertirse en el texto activo.
- Cambiar de modo reinicia el texto activo, así que puedes experimentar con seguridad. Si el texto parece quedarse atascado, alterna a otro modo o haz clic en `Refresh On Screen Load: Enabled` para forzar un nuevo sorteo cada vez que se abre el menú.

## Ejemplo de Archivo de Texto
Cuando uses el modo de origen "Text File", guarda tu lista de textos como texto plano (UTF-8 sin BOM). Cada línea es un posible texto:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Reemplaza `your_placeholder_id_here` con el marcador de posición que quieres resolver en tiempo de ejecución. FancyMenu elige una línea aleatoria que no esté vacía cada vez que el texto de inicio se actualiza.

## Hacer que Se Vea Como Quieres
- Usa `Set Scale` y `Set Rotation` para controlar el tamaño y el ángulo de rotación.
- `Set Text Color` acepta un valor hexadecimal (por ejemplo `#FFFF00`) para combinar con tu tema.
- `Shadow: Enabled` agrega la sombra proyectada de Minecraft; desactívala para texto plano.
- `Bouncing: Enabled` mantiene el movimiento de rebote característico; desactívalo para una etiqueta estática.
- FancyMenu renderiza el texto de inicio como un componente completo de Minecraft, así que los códigos de color y otras decoraciones de texto funcionan como se espera.

## Funciones de Texto Dinámico
- Los marcadores de posición se resuelven antes de renderizar, así que puedes hacer referencia a nombres de jugadores, fechas u otros valores compatibles dentro del texto de inicio.
- Como el elemento acepta el JSON serializado de componentes de Minecraft, puedes pegar fragmentos JSON avanzados en Direct Input o en tu archivo de texto. El elemento los deserializa automáticamente y vuelve a texto literal si algo sale mal.

## Solución de Problemas
- El texto vacío en Direct Input muestra `< empty splash element >` mientras editas. Escribe cualquier cosa (incluso un espacio) para quitar la advertencia.
- Si un archivo de texto no contiene líneas válidas, el elemento muestra `ERROR: SPLASH FILE IS EMPTY`. Agrega al menos una línea que no esté vacía y vuelve a abrir la pantalla.
- Los errores del JSON serializado vuelven a texto plano. Usa la estructura JSON estándar de Mojang o prueba los fragmentos con el comando vanilla `/tellraw` antes de pegarlos.
