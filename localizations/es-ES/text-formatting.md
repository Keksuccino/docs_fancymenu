---
title: Formato de texto
description: Cómo dar formato al texto con Markdown y los códigos de formato de Minecraft.
---
# Formato de texto

[Los elementos de texto](./elements#text) admiten Markdown. Otros campos de texto usan el formato de Minecraft, y las etiquetas de los botones pueden usar componentes de texto de Minecraft.

# Markdown

Los **elementos de texto** de FancyMenu tienen compatibilidad total con Markdown, lo que significa que puedes dar formato al contenido del texto añadiéndole caracteres especiales.

Por ejemplo, para poner el texto en negrita, añade `**` antes y después del texto en negrita, así `**Algo de texto en negrita muy resaltado.**` se verá así:
**Algo de texto en negrita muy resaltado.**

FancyMenu también admite las extensiones documentadas a continuación.

> [!CAUTION]
> Markdown solo funciona en **elementos de texto**. Para las etiquetas de los botones y otros campos de texto, usa [los códigos de formato de Minecraft](#minecraft-text-formatting).

## Fuentes

Puedes mostrar texto con una fuente personalizada cargada mediante un paquete de recursos añadiendo `%!!<nombre_de_fuente>%` antes del texto y `%!!%` después.

Una fuente válida incluida en el juego base es `uniform`, así que para mostrar texto con la fuente `uniform`, haz esto:
`%!!uniform%este es un tipo de letra personalizado%!!%`

Esto mostrará `este es un tipo de letra personalizado` con la fuente `uniform`.

## Color del texto (HEX)

Es posible mostrar texto en un color HEX específico añadiendo `%<color_HEX>%` antes del texto y `%#%` después.

Un color HEX válido para el verde es `#77fc03`, así que para mostrar texto con este color, haz esto:
`%#77fc03%¡este texto es verde!%#%`

Esto mostrará `¡este texto es verde!` en `#77fc03` (verde).

¡Asegúrate de que el color HEX empiece por `#`!

Los nombres de color comunes similares a HTML se admiten en el mismo código de formato de color:

```
%#red%¡Este texto es rojo!%#%
```

Nombres admitidos: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` y `transparent`.

## Alineación del texto

Puedes alinear las líneas de texto empezando una línea con el código de formato de alineación específico, sin nada más, después las líneas de texto que quieras mostrar con esa alineación y luego el código de alineación otra vez en una línea adicional.

Todo el contenido de texto está **alineado a la izquierda de forma predeterminada**, así que solo hay códigos de formato para **centrado** y **alineación a la derecha**.

### Centrado

Para centrar líneas de texto, usa el código de formato `^^^`.

Ejemplo:
```
Este texto no está centrado.

^^^
Este texto está centrado.
Este texto también está centrado.
^^^

Este texto ya no está centrado.
```

### Alineado a la derecha

Para mostrar líneas de texto alineadas a la derecha, usa el código de formato `|||`.

Ejemplo:
```
Este texto no está alineado a la derecha.

|||
Este texto está alineado a la derecha.
Este texto también está alineado a la derecha.
|||

Este texto ya no está alineado a la derecha.
```

## Títulos

Para mostrar **una línea de texto** como título (más grande y subrayado), añade `# ` (muy grande), `## ` (grande) o `### ` (pequeño) antes de la línea de texto.

Ejemplo:
`## Título grande`

## Negrita

Añade `**` antes y después del texto para que aparezca en **negrita**.

Ejemplo:
`**contenido de texto en negrita**`

## Cursiva

Añade `_` O `*` antes y después del texto para que aparezca en *cursiva*.

Ejemplo:
`*contenido de texto en cursiva*`

## Tachado

Añade `~` antes y después del texto para que aparezca ~~tachado~~.

Ejemplo:
`~contenido de texto tachado~`

## Hipervínculos

Puedes añadir hipervínculos al contenido de texto para que abran un sitio web al hacer clic.

El texto que debe aparecer como [hipervínculo](https://google.com) tiene que ir entre `[ ]`, seguido del enlace real entre `( )`.

Así que si quieres que `example text content` sea clicable y abra `https://example-website.net`, haz esto:
`[example text content](https://example-website.net)`

## Eventos de clic y de pasar el cursor

Los eventos de clic y de pasar el cursor de Markdown están disponibles para [elementos de texto](./elements#text) y otro texto en Markdown. Usa [**On Markdown Text Clicked**](./listeners#on-markdown-text-clicked-text_clicked) y [**On Markdown Text Hovered**](./listeners#on-markdown-text-hovered-text_hovered) para reaccionar ante ellos.

Los eventos de clic usan el prefijo `click:`:

```
[some clickable text](click:unique_text_click_event_id)
```

Los eventos de pasar el cursor usan el prefijo `hover:`:

```
[some hoverable text](hover:unique_text_hover_event_id)
```

Ambos listeners exponen el ID del evento como `$$text_event_id`.

## Imágenes

Markdown admite mostrar imágenes en el contenido de texto.

FancyMenu admite recursos de Minecraft, recursos locales y recursos web en Markdown.

Para añadir una imagen, empieza una línea de texto con `![](`, luego la [URL, ubicación del recurso o ruta al recurso](./resources) y después `)`.

Así que para mostrar el recurso web `https://example-website.net/image.png`, haz esto:
`![](https://example-website.net/image.png)`

Las imágenes también pueden ser **hipervínculos** envolviendo toda la línea de texto de la imagen en un **hipervínculo** como este:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> ¡Los recursos locales deben estar en `<game-directory>/config/fancymenu/assets/`!

## Cita

Para dar formato al texto como una cita, empieza una línea de texto con `> `.
Esto formateará todas las líneas siguientes como cita hasta que encuentre una línea **vacía**.

Ejemplo:
```
Esto no parecerá una cita.

> Esto parecerá una cita.
Esto también parecerá una cita.

Esto ya no parecerá una cita.
```

## Listas con viñetas

Para mostrar texto como una lista con viñetas así:
- Entrada 1
- Entrada 2
  - Subentrada

Solo tienes que empezar una línea con `- `.

Ejemplo:
```
- Entrada 1
- Entrada 2
  - Subentrada
```

## Línea de separación

Para añadir una línea de separación a tu texto que tenga el ancho de una línea completa de texto, simplemente empieza una línea con `---` y no añadas nada más.

Entonces se verá algo así:

---

## Bloques de código

Los bloques de código pueden ayudarte a mostrar texto como `texto sin formato` sin que Markdown intente darle formato, o simplemente a mostrar texto con un estilo similar al de código sin ajuste automático de las líneas de texto.

Un bloque de código de una sola línea (entre otro texto) empieza y termina con \` , lo cual en realidad es bastante difícil de mostrar en un texto Markdown.

Una línea de texto que contiene un bloque de código de una sola línea se ve así:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Los bloques de código de varias líneas agrupan varias líneas en un único bloque grande y empiezan con una línea que solo contiene \`\`\`, luego el contenido del texto y después \`\`\` de nuevo:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texto sin formato

El código de formato de texto sin formato anulará todos los demás códigos de formato que haya dentro de él.

Funciona de manera parecida a los bloques de código, pero no lo formatea como un bloque de código. En su lugar, se mostrará como texto normal, pero sin ningún formato.

Para envolver una parte de texto dentro de una línea en un código de formato de texto sin formato, debes añadir `;;` antes y después de la parte de texto que quieras mostrar como texto sin formato, así:

```
Esta es una línea de texto con ;;**esta parte**;; mostrándose como texto sin formato con el código de formato ** (negrita) visible y _esta parte_ como texto en cursiva con formato normal.
```

El texto sin formato también funciona como un código envolvente de varias líneas. Para envolver líneas completas, añade `;;;` antes y después de la(s) línea(s) que quieras mostrar como texto sin formato, así:

```
;;;
Esta línea se mostrará **sin formato** con los códigos de formato ** (negrita) visibles.
Esta línea también se mostrará _sin formato_ con los códigos de formato _ (cursiva) visibles.
;;;

Esta línea volverá a verse **normal** con "normal" formateado como texto en negrita.
```

# Formato de texto de Minecraft

Los códigos de formato de Minecraft funcionan en los campos de texto con formato compatibles en FancyMenu. Usa `&` en lugar del prefijo `§` de Minecraft; por ejemplo, `&cWarning` muestra texto rojo.

Consulta la [referencia de códigos de formato de Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes) para ver los colores y estilos disponibles.

> [!CAUTION]
> Los códigos de formato de Minecraft no son fiables en los **elementos de texto** porque esos elementos analizan Markdown. Usa en su lugar el formato Markdown descrito arriba.

# Componentes de texto de Minecraft (sistema de componentes en bruto)

El sistema de componentes de texto de Minecraft es bastante potente para contenido de texto de **una sola línea** como las **etiquetas de botones**.

En Minecraft Vanilla puedes usarlo en los comandos `/tellraw` y `/title` (y probablemente en otros sitios).
Se trata de texto con formato serializado a JSON, así que puedes añadir atributos de formato al contenido del texto.

Para aprender más sobre los componentes de texto en detalle, consulta [esta página de Minecraft Wiki](https://minecraft.wiki/w/Raw_JSON_text_format).
Para aprender más sobre las fuentes en Minecraft, consulta [esta página de Minecraft Wiki](https://minecraft.wiki/w/Resource_pack#Fonts).

Para hacer que FancyMenu detecte una etiqueta de botón como **componente de texto**, no pongas nada más que el texto del componente serializado como etiqueta, así:
`{"text":"Texto de la etiqueta del botón","font":"uniform"}`

El ejemplo anterior mostrará la etiqueta del botón `Texto de la etiqueta del botón` con la fuente `uniform`.

> [!NOTE]
> Puedes usar los marcadores de posición de FancyMenu en el valor `text` de los componentes.
