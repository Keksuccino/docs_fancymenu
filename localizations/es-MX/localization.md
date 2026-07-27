---
title: Localización de diseños
description: Localiza texto y otro contenido del diseño.
---

# Localización de diseños

Usa el [**marcador de posición Localize Text**](./placeholders#localize-text-local) para texto traducible:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu primero revisa los datos de idioma activos de Minecraft. Si la clave no está presente ahí, revisa los archivos de localización personalizados de FancyMenu. Si ninguna de las dos fuentes contiene la clave, se muestra la propia clave.

# Archivos de localización personalizados de FancyMenu

Coloca los archivos aquí:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Crea un subdirectorio para tus archivos de localización:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Pon los archivos de localización dentro de al menos un subdirectorio de `custom_locals`; los archivos colocados directamente en la raíz de `custom_locals` no se cargan. Se admiten subdirectorios anidados.

Formatos UTF-8 compatibles:

| Extensión | Formato |
|---|---|
| `.json` | Objeto JSON; los objetos anidados se convierten en claves separadas por puntos |
| `.lang` | Líneas `key=value` |
| `.properties` | Sintaxis de propiedades de Java |

Ejemplo JSON:

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

FancyMenu combina los archivos compatibles de estos subdirectorios en un solo diccionario de localización personalizado. Usa cada clave solo en un archivo. Los archivos de localización personalizados no cambian con el idioma seleccionado en Minecraft; usa el método de paquete de recursos de abajo cuando necesites cambio automático de idioma.

Reinicia el cliente después de editar los archivos de localización personalizados.

# Texto específico del idioma

Para el cambio automático según el idioma seleccionado en Minecraft, proporciona archivos de idioma normales de Minecraft mediante un [paquete de recursos](./resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Usa las mismas claves en cada archivo de idioma, habilita el paquete de recursos y luego léelos con el [**marcador de posición Localize Text**](./placeholders#localize-text-local).

# Localización de imágenes y elementos

Usa el [**requisito Is Game Language**](./conditions#is-game-language-fancymenu_loading_requirement_is_language) para mostrar diferentes elementos o diseños para distintos códigos de idioma, como `en_us` y `de_de`.
