---
title: Localizar diseños
description: Localiza texto y otros contenidos del diseño.
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# Localizar diseños

Usa el marcador de posición [**Localizar texto**](/placeholders#localize-text) para el texto que quieras traducir:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu primero revisa los datos de idioma activos de Minecraft. Si la clave no está ahí, revisa los archivos de localización personalizados de FancyMenu. Si ninguna de las dos fuentes contiene la clave, se muestra la propia clave.

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

Coloca los archivos de localización dentro de al menos un subdirectorio de `custom_locals`; los archivos que pongas directamente en la carpeta raíz de `custom_locals` no se cargarán. Se admiten subdirectorios anidados.

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
      "play": "Jugar"
    }
  }
}
```

Esto define `modpack.menu.play`.

FancyMenu combina los archivos admitidos de estos subdirectorios en un solo diccionario de localización personalizado. Usa cada clave en un solo archivo. Los archivos de localización personalizados no cambian según el idioma seleccionado en Minecraft; si necesitas que el idioma cambie automáticamente, usa el método del paquete de recursos que se describe abajo.

Reinicia el cliente después de editar los archivos de localización personalizados.

# Texto específico para cada idioma

Para que el idioma cambie automáticamente según el idioma seleccionado en Minecraft, proporciona archivos de idioma normales de Minecraft mediante un [paquete de recursos](/resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Usa las mismas claves en cada archivo de idioma, activa el paquete de recursos y luego léelas con el marcador de posición [**Localizar texto**](/placeholders#localize-text).

# Localizar imágenes y elementos

Usa el requisito [**Es el idioma del juego**](/conditions#is-game-language) para mostrar distintos elementos o diseños según los códigos de idioma, como `en_us` y `de_de`.
