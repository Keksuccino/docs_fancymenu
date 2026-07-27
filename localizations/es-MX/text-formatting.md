---
title: Formato de texto
description: Cómo dar formato al texto con Markdown y los códigos de formato de Minecraft.
---

# Formato de texto

[Los elementos de texto](./elements#text) admiten Markdown. Otros campos de texto usan el formato de Minecraft, y las etiquetas de botones pueden usar componentes de texto de Minecraft.

# Markdown

Los **elementos de texto** de FancyMenu tienen compatibilidad completa con Markdown, lo que significa que puedes dar formato al contenido del texto agregándole caracteres especiales.

Por ejemplo, para que el texto se vea en negritas, agrega `**` antes y después del texto en negritas, así `**Algo de texto en negritas que se ve muy en negritas.**` se verá así:
**Algo de texto en negritas que se ve muy en negritas.**

FancyMenu también admite las extensiones documentadas abajo.

> [!CAUTION]
> Markdown solo funciona en **elementos de texto**. Para etiquetas de botones y otros campos de texto, usa [los códigos de formato de Minecraft](#minecraft-text-formatting).

## Fuentes

Puedes mostrar texto con una fuente personalizada cargada mediante un paquete de recursos agregando `%!!<font_name>%` antes del texto y `%!!%` después.

Una fuente válida incluida en el juego base es `uniform`, así que para mostrar texto con la fuente `uniform`, haz esto:
`%!!uniform%este es un tipo de letra personalizado%!!%`

Esto mostrará `este es un tipo de letra personalizado` con la fuente `uniform`.

## Color del texto (HEX)

Es posible mostrar texto en un color HEX específico agregando `%<HEX_color>%` antes del texto y `%#%` después.

Un color HEX válido para verde es `#77fc03`, así que para mostrar texto con este color, haz esto:
`%#77fc03%¡este texto es verde!%#%`

Esto mostrará `¡este texto es verde!` como `#77fc03` (verde).

¡Asegúrate de que el color HEX empiece con `#`!

Los nombres de color comunes tipo HTML son compatibles con el mismo código de formato de color:

```
%#red%¡Este texto es rojo!%#%
```

Nombres compatibles: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` y `transparent`.

## Alineación del texto

Puedes alinear líneas de texto empezando una línea con el código de formato de alineación específico, sin nada más, luego las líneas de texto que quieras mostrar con esa alineación y después el código de alineación otra vez en una línea adicional.

Todo el contenido de texto está **alineado a la izquierda por defecto**, así que solo existen códigos de formato para **centrado** y **alineación a la derecha**.

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

## Encabezados

Para mostrar **una línea de texto** como encabezado (más grande y subrayado), agrega `# ` (muy grande), `## ` (grande) o `### ` (pequeño) antes de la línea de texto.

Ejemplo:
`## Encabezado grande`

## Negritas

Agrega `**` antes y después del texto para que se vea en **negritas**.

Ejemplo:
`**contenido de texto en negritas**`

## Cursiva

Agrega `_` O `*` antes y después del texto para que se vea en *cursiva*.

Ejemplo:
`*contenido de texto en cursiva*`

## Tachado

Agrega `~` antes y después del texto para que se vea ~~tachado~~.

Ejemplo:
`~contenido de texto tachado~`

## Hipervínculos

Puedes agregar hipervínculos al contenido de texto para que abran un sitio web al hacer clic.

El texto que debe aparecer como [hipervínculo](https://google.com) necesita ir entre `[ ]`, seguido del enlace real entre `( )`.

Así que, si quieres que `texto de ejemplo` sea clickable y abra `https://example-website.net`, haz esto:
`[texto de ejemplo](https://example-website.net)`

## Eventos de clic y de hover

Los eventos de clic y hover de Markdown están disponibles para [elementos de texto](./elements#text) y otro texto Markdown. Usa [**Al hacer clic en texto Markdown**](./listeners#on-markdown-text-clicked-text_clicked) y [**Al pasar el cursor sobre texto Markdown**](./listeners#on-markdown-text-hovered-text_hovered) para reaccionar a ellos.

Los eventos de clic usan el prefijo `click:`:

```
[algún texto clickable](click:unique_text_click_event_id)
```

Los eventos de hover usan el prefijo `hover:`:

```
[algún texto con hover](hover:unique_text_hover_event_id)
```

Ambos listeners exponen el ID del evento como `$$text_event_id`.

## Imágenes

Markdown admite mostrar imágenes en el contenido de texto.

FancyMenu admite recursos de Minecraft, recursos locales y recursos web en Markdown.

Para agregar una imagen, empieza una línea de texto con `![](`, luego la [URL, ubicación del recurso o ruta al recurso](./resources) y después `)`.

Así que, para mostrar el recurso web `https://example-website.net/image.png`, haz esto:
`![](https://example-website.net/image.png)`

Las imágenes también pueden ser **hipervínculos** envolviendo toda la línea de texto de la imagen en un **hipervínculo** así:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> ¡Los recursos locales deben estar en `<game-directory>/config/fancymenu/assets/`!

## Cita

Para dar formato al texto como una cita, empieza una línea de texto con `> `.
Esto formateará todas las líneas siguientes como cita hasta que encuentre una línea **vacía**.

Ejemplo:
```
Esto no se verá como una cita.

> Esto se verá como una cita.
Este también se verá como una cita.

Esto ya no se verá como una cita.
```

## Listas con viñetas

Para mostrar texto como una lista con viñetas como esta:
- Entrada 1
- Entrada 2
  - Subentrada

Solo necesitas empezar una línea con `- `.

Ejemplo:
```
- Entrada 1
- Entrada 2
  - Subentrada
```

## Línea de separación

Para agregar una línea de separación a tu texto que tenga el ancho de toda una línea de texto, simplemente empieza una línea con `---` y no agregues nada más.

Entonces se verá algo así:

---

## Bloques de código

Los bloques de código pueden ayudarte a mostrar texto como `texto plano` sin que Markdown intente darle formato, o simplemente para mostrar texto con un estilo tipo código sin ajuste automático de las líneas de texto.

Un bloque de código de una sola línea (entre otro texto) empieza y termina con \` , lo cual en realidad es bastante difícil de mostrar en texto Markdown..

Una línea de texto que contiene un bloque de código de una sola línea se ve así:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Los bloques de código de varias líneas abarcan múltiples líneas en un solo bloque de código grande y empiezan con una línea que solo contiene \`\`\` y luego el contenido del texto y después \`\`\` otra vez:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texto sin formato

El código de formato de texto sin formato omitirá todos los demás códigos de formato dentro de él.

Funciona de manera similar a los bloques de código, pero no lo formateará como un bloque de código. En su lugar, se mostrará como texto normal, pero sin ningún formato.

Para envolver una parte del texto dentro de una línea en un código de formato de texto sin formato, necesitas agregar `;;` antes y después de la parte del texto que quieres mostrar como texto sin formato, así:

```
Esta es una línea de texto con ;;**esta parte**;; mostrándose como texto sin formato con el código visible de formato ** (negritas) y _esta parte_ como texto cursiva con formato normal.
```

El texto sin formato también funciona como un código envolvente de varias líneas. Para envolver líneas completas, agrega `;;;` antes y después de la(s) línea(s) que quieras mostrar como texto sin formato, así:

```
;;;
Esta línea se mostrará **sin formato** con los códigos visibles de formato ** (negritas).
Esta línea también se mostrará _sin formato_ con los códigos visibles de formato _ (cursiva).
;;;

Esta línea volverá a verse **normal** con "normal" formateado como texto en negritas.
```

# Formato de texto de Minecraft

Los códigos de formato de Minecraft funcionan en los campos de texto con formato compatibles en FancyMenu. Usa `&` en lugar del prefijo `§` de Minecraft; por ejemplo, `&cWarning` muestra texto rojo.

Consulta la [referencia de códigos de formato de Minecraft en el Wiki de Minecraft](https://minecraft.wiki/w/Formatting_codes) para ver los colores y estilos disponibles.

> [!CAUTION]
> Los códigos de formato de Minecraft no son confiables en los **elementos de texto** porque esos elementos analizan Markdown. En su lugar, usa el formato Markdown descrito arriba.

# Componentes de texto de Minecraft (Sistema de componentes sin procesar)

El sistema de componentes de texto de Minecraft es bastante potente para contenido de texto de **una sola línea** como las **etiquetas de botones**.

En Minecraft Vanilla puedes usarlo en los comandos `/tellraw` y `/title` (y probablemente en otros lugares).
Es texto con formato serializado a JSON, así que puedes agregar atributos de formato al contenido del texto.

Para aprender más sobre los componentes de texto en detalle, por favor revisa [esta página del wiki de Minecraft](https://minecraft.wiki/w/Raw_JSON_text_format).
Para aprender más sobre las fuentes en Minecraft, revisa [esta página del wiki de Minecraft](https://minecraft.wiki/w/Resource_pack#Fonts).

Para hacer que FancyMenu detecte una etiqueta de botón como **componente de texto**, no pongas nada más que el texto serializado del componente como etiqueta, así:
`{"text":"Texto de la etiqueta del botón","font":"uniform"}`

El ejemplo anterior mostrará la etiqueta del botón `Texto de la etiqueta del botón` con la fuente `uniform`.

> [!NOTE]
> Puedes usar los placeholders de FancyMenu en el valor `text` de los componentes.
