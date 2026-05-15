---
title: Formato de texto
description: Cómo dar formato al texto con Markdown y los códigos de formato de Minecraft.
---

# Formato de texto

¡FancyMenu tiene un montón de funciones para hacer que el contenido de texto en los diseños se vea *más elegante*! 

Los elementos de texto tienen compatibilidad completa con **Markdown** con algunos extras muy interesantes, y la mayoría de los demás contenidos de texto también son compatibles con el sistema de **formato de texto de Minecraft**. Incluso las etiquetas de los botones tienen compatibilidad con **componentes de texto de Minecraft**, lo que te permite usar fuentes personalizadas y más.

# Markdown

Los **elementos de texto** de FancyMenu tienen compatibilidad completa con Markdown, lo que significa que puedes dar formato al contenido del texto agregando caracteres especiales.

Por ejemplo, para poner el texto en negritas, agrega `**` antes y después del texto en negritas; así, `**Algún texto en negritas muy en negritas.**` se verá así:
**Algún texto en negritas muy en negritas.**

¡El Markdown de FancyMenu incluso tiene algunas funciones especiales que lo hacen aún más potente!

> Markdown **NO FUNCIONA** para otros textos como las etiquetas de los botones. Solo funciona en **ELEMENTOS DE TEXTO**. Para todo lo demás, usa [los códigos de formato de Minecraft](/text-formatting#minecraft-text-formatting).
{.is-danger}

## Fuentes

Puedes mostrar texto con una fuente personalizada cargada mediante un paquete de recursos agregando `%!!<nombre_fuente>%` antes del texto y `%!!%` después.

Una fuente válida incluida en el juego base es `uniform`, así que para mostrar texto con la fuente `uniform`, haz esto:
`%!!uniform%este es un texto con fuente personalizada%!!%`

Esto mostrará `este es un texto con fuente personalizada` con la fuente `uniform`.

## Color del texto (HEX)

Es posible mostrar texto con un color HEX específico agregando `%<color_HEX>%` antes del texto y `%#%` después.

Un color HEX válido para verde es `#77fc03`, así que para mostrar texto con este color, haz esto:
`%#77fc03%¡este texto es verde!%#%`

Esto mostrará `¡este texto es verde!` en `#77fc03` (verde).

¡Asegúrate de que el color HEX empiece con `#`!

FancyMenu 3.9.0 también admite nombres de color comunes similares a HTML en este mismo código de formato de color:

```
%#red%¡Este texto es rojo!%#%
```

Nombres compatibles: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` y `transparent`.

## Alineación de texto

Puedes alinear las líneas de texto empezando una línea con el código de formato de alineación específico, sin nada más, y luego las líneas de texto que quieras mostrar con esa alineación; después, vuelve a poner el código de alineación en una línea extra.

Todo el contenido de texto está **alineado a la izquierda** por defecto, así que solo hay códigos de formato para texto **centrado** y **alineado a la derecha**.

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

Agrega `**` antes y después del texto para que se vea **en negritas**.

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

Puedes agregar hipervínculos al contenido de texto para que abran un sitio web cuando se hace clic.

El texto que debe aparecer como [hipervínculo](https://google.com) debe ir entre `[ ]`, seguido del enlace real entre `( )`.

Así que, si quieres que `texto de ejemplo` sea clicable y abra `https://example-website.net`, haz esto:
`[texto de ejemplo](https://example-website.net)`

## Eventos de clic y de pasar el cursor

FancyMenu 3.9.0 agrega eventos de Markdown al hacer clic y al pasar el cursor para los elementos de texto y otros textos en Markdown.

Los eventos de clic usan el prefijo `click:`:

```
[algún texto clicable](click:unique_text_click_event_id)
```

Los eventos de pasar el cursor usan el prefijo `hover:`:

```
[algún texto sobre el que se puede pasar el cursor](hover:unique_text_hover_event_id)
```

Usa los listeners **On Markdown Text Clicked** y **On Markdown Text Hovered** para reaccionar a estos eventos. Ambos listeners exponen el ID del evento como `$$text_event_id`.

## Imágenes

Markdown admite mostrar imágenes en el contenido de texto.

FancyMenu admite recursos de Minecraft, recursos locales y recursos web en Markdown.

Para agregar una imagen, empieza una línea de texto con `![](`, luego la [URL, la ubicación del recurso o la ruta al recurso](/resources) y después `)`.

Así que para mostrar el recurso web `https://example-website.net/image.png`, haz esto:
`![](https://example-website.net/image.png)`

Las imágenes también pueden ser **hipervínculos** envolviendo toda la línea de texto de la imagen en un **hipervínculo**, así:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> ¡Los recursos locales deben estar en `/config/fancymenu/assets/`!
{.is-warning}

## Cita

Para dar formato al texto como una cita, empieza una línea de texto con `> `.
Esto dará formato a todas las líneas siguientes como cita hasta que encuentre una línea **vacía**.

Ejemplo:
```
Esto no se verá como una cita.

> Esto se verá como una cita.
Esto también se verá como una cita.

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

Para agregar una línea de separación a tu texto que tenga el ancho de una línea completa, simplemente empieza una línea con `---` y no agregues nada más.

Entonces se verá algo así:

---

## Bloques de código

Los bloques de código pueden ayudarte a mostrar texto como `texto plano` sin que Markdown intente darle formato, o simplemente para mostrar texto con un estilo tipo código sin ajuste automático de las líneas.

Un bloque de código de una sola línea (entre otro texto) empieza y termina con \` , lo cual en realidad es bastante difícil de mostrar en texto Markdown..

Una línea de texto que contiene un bloque de código de una sola línea se ve así:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Los bloques de código de varias líneas envuelven varias líneas en un bloque de código grande y empiezan con una línea que solo contiene \`\`\` , luego el contenido de texto y después \`\`\` otra vez:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texto plano

El código de formato de texto plano omitirá todos los demás códigos de formato dentro de él.

Funciona de manera similar a los bloques de código, pero no lo formateará como un bloque de código. En su lugar, se mostrará como texto normal, pero sin ningún formato.

Para envolver una parte de texto dentro de una línea con un código de formato de texto plano, necesitas agregar `;;` antes y después de la parte que quieras mostrar como texto plano, así:

```
Esta es una línea de texto con ;;**esta parte**;; mostrándose como texto sin formato con el código de formato ** (negritas) visible y _esta parte_ como texto normal en cursiva.
```

El texto plano también funciona como un código envolvente de varias líneas. Para envolver líneas completas, agrega `;;;` antes y después de la(s) línea(s) que quieras mostrar como texto plano, así:

```
;;;
Esta línea se mostrará **sin formato** con los códigos de formato ** (negritas) visibles.
Esta línea también se mostrará _sin formato_ con los códigos de formato _ (cursiva) visibles.
;;;

Esta línea volverá a verse **normal** con "normal" formateado como texto en negritas.
```

# Formato de texto de Minecraft

Minecraft tiene un sistema de formato bastante bueno que funciona de manera similar a Markdown, donde agregas caracteres especiales al contenido de tu texto para darle formato.

Para leer más sobre el sistema de formato de Minecraft, consulta [esta página de la wiki de Minecraft](https://minecraft.wiki/w/Formatting_codes).

> La wiki dirá que el prefijo del código de formato es `§`, pero en FancyMenu necesitas reemplazarlo por `&`. Todo lo demás permanece igual.
{.is-warning}

> Los **elementos de texto** son muy complejos y, para dar compatibilidad con Markdown, la desventaja fue **romper los códigos de formato Vanilla de Minecraft**, así que estos códigos no funcionarán bien en los elementos de texto (solo la primera palabra se formatea después del código de formato, etc.). En su lugar, debes usar los códigos de formato Markdown en los elementos de texto.
{.is-danger}

# Componentes de texto de Minecraft (sistema de componentes sin procesar)

El sistema de componentes de texto de Minecraft es bastante potente para contenido de texto de **una sola línea**, como las **etiquetas de botones**.

En Vanilla Minecraft puedes usarlo en los comandos `/tellraw` y `/title` (y probablemente en otros lugares).
Es texto con formato serializado en JSON, así que puedes agregar atributos de formato al contenido de texto.

Para aprender más sobre los componentes de texto en detalle, consulta [esta página de la wiki de Minecraft](https://minecraft.wiki/w/Raw_JSON_text_format).
Para aprender más sobre las fuentes en Minecraft, consulta [esta página de la wiki de Minecraft](https://minecraft.wiki/w/Resource_pack#Fonts).

Para hacer que FancyMenu detecte una etiqueta de botón como **componente de texto**, no pongas nada más que el texto serializado del componente como etiqueta, así:
`{"text":"Texto de la etiqueta del botón","font":"uniform"}`

El ejemplo anterior mostrará la etiqueta del botón `Texto de la etiqueta del botón` con la fuente `uniform`.

> Puedes usar los placeholders de FancyMenu en el valor `text` de los componentes.
{.is-info}
