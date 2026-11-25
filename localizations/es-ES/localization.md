---
title: Localizar diseños
description: Localiza texto y otros contenidos de los diseños.
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# Localizar diseños

Usa el [marcador de posición **Localizar texto**](/placeholders#localize-text) para el texto traducible:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu primero comprueba los datos de idioma activos de Minecraft. Si la clave no está ahí, comprueba los archivos de localización personalizados de FancyMenu. Si la clave no está en ninguna de las dos fuentes, se muestra la propia clave.

# Archivos de localización personalizados de FancyMenu

Coloca los archivos en:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Crea un subdirectorio para tus archivos de localización:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Coloca los archivos de localización en al menos un subdirectorio de `custom_locals`; los archivos que se coloquen directamente en la raíz de `custom_locals` no se cargarán. Se admiten subdirectorios anidados.

Formatos UTF-8 admitidos:

| Extensión | Formato |
|---|---|
| `.json` | Objeto JSON; los objetos anidados se convierten en claves separadas por puntos |
| `.lang` | Líneas con el formato `clave=valor` |
| `.properties` | Sintaxis de propiedades de Java |

Ejemplo de JSON:

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

Esto define `modpack.menu.play`.

FancyMenu combina los archivos admitidos de estos subdirectorios en un único diccionario de localización personalizado. Usa cada clave en un solo archivo. Los archivos de localización personalizados no cambian al seleccionar otro idioma en Minecraft; si necesitas que el cambio de idioma sea automático, usa el método de paquete de recursos que se indica más abajo.

Reinicia el cliente después de editar los archivos de localización personalizados.

# Texto específico de cada idioma

Para que el idioma cambie automáticamente según el idioma seleccionado en Minecraft, proporciona archivos de idioma estándar de Minecraft mediante un [paquete de recursos](/resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Usa las mismas claves en cada archivo de idioma, activa el paquete de recursos y, después, consúltalas con el [marcador de posición **Localizar texto**](/placeholders#localize-text).

# Localizar imágenes y elementos

Usa el [requisito **El idioma del juego es**](/conditions#is-game-language) para mostrar distintos elementos o diseños según el código de idioma, como `en_us` y `de_de`.
