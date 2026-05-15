---
title: Formato de texto
description: Cómo dar formato al texto con Markdown y los códigos de formato de Minecraft.
---

# Formato de texto

¡FancyMenu tiene un montón de funciones para hacer que el contenido de texto en los diseños sea *más elegante*!

Los elementos de texto tienen compatibilidad total con **Markdown**, además de algunos extras muy interesantes, y la mayor parte del resto del contenido de texto también admite el sistema de **formato de texto de Minecraft**; incluso las etiquetas de los botones admiten **componentes de texto de Minecraft**, lo que te permite usar fuentes personalizadas y mucho más.

# Markdown

Los **elementos de texto** de FancyMenu tienen compatibilidad total con Markdown, lo que significa que puedes dar formato al contenido de texto añadiendo caracteres especiales.

Por ejemplo, para poner texto en negrita, añade `**` antes y después del texto en negrita, así `**Este es un texto en negrita muy marcado.**` se verá así:
**Este es un texto en negrita muy marcado.**

¡El Markdown de FancyMenu incluso tiene algunas funciones especiales que lo hacen todavía más potente!

> Markdown **NO FUNCIONA** para otros elementos basados en texto, como las etiquetas de los botones. Solo funciona en los **ELEMENTOS DE TEXTO**. Para todo lo demás, utiliza [los códigos de formato de Minecraft](/text-formatting#minecraft-text-formatting).
{.is-danger}

## Fuentes

Puedes mostrar texto con una fuente personalizada cargada mediante un paquete de recursos añadiendo `%!!<font_name>%` antes del texto y `%!!%` después.

Una fuente válida incluida en el juego base es `uniform`, así que para mostrar texto con la fuente `uniform`, haz esto:
`%!!uniform%este es un tipo de letra personalizado%!!%`

Esto mostrará `este es un tipo de letra personalizado` con la fuente `uniform`.

## Color del texto (HEX)

Es posible mostrar texto en un color HEX concreto añadiendo `%<HEX_color>%` antes del texto y `%#%` después.

Un color HEX válido para el verde es `#77fc03`, así que para mostrar texto de este color, haz esto:
`%#77fc03%¡este texto es verde!%#%`

Esto mostrará `¡este texto es verde!` en `#77fc03` (verde).

¡Asegúrate de que el color HEX empieza por `#`!

FancyMenu 3.9.0 también admite nombres de color comunes similares a HTML en este mismo código de formato de color:

```
%#red%¡Este texto es rojo!%#%
```

Nombres compatibles: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` y `transparent`.

## Alineación del texto

Puedes alinear líneas de texto comenzando una línea con el código de formato de alineación correspondiente, sin nada más, y luego las líneas de texto que quieras mostrar con esa alineación específica, terminando con el código de alineación de nuevo en una línea adicional.

Todo el contenido de texto está **alineado a la izquierda por defecto**, así que solo hay códigos de formato para **centrado** y **alineación a la derecha**.

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

Para mostrar **una línea de texto** como título (más grande y subrayada), añade `# ` (muy grande), `## ` (grande) o `### ` (pequeño) antes de la línea de texto.

Ejemplo:
`## Título grande`

## Negrita

Añade `**` antes y después del texto para que se vea **en negrita**.

Ejemplo:
`**contenido de texto en negrita**`

## Cursiva

Añade `_` O `*` antes y después del texto para que se vea en *cursiva*.

Ejemplo:
`*contenido de texto en cursiva*`

## Tachado

Añade `~` antes y después del texto para que se vea ~~tachado~~.

Ejemplo:
`~contenido de texto tachado~`

## Hipervínculos

Puedes añadir hipervínculos al contenido de texto para que abran una página web al hacer clic.

El texto que debe aparecer como [hipervínculo](https://google.com) tiene que ir entre `[ ]`, seguido del enlace real entre `( )`.

Así que, si quieres que `texto de ejemplo` sea clicable y abra `https://example-website.net`, haz esto:
`[texto de ejemplo](https://example-website.net)`

## Eventos de clic y de pasar el cursor

FancyMenu 3.9.0 añade eventos de clic y de pasar el cursor en Markdown para los elementos de texto y para otros textos con Markdown.

Los eventos de clic usan el prefijo `click:`:

```
[un texto clicable](click:unique_text_click_event_id)
```

Los eventos al pasar el cursor usan el prefijo `hover:`:

```
[un texto interactivo al pasar el cursor](hover:unique_text_hover_event_id)
```

Usa los listeners **On Markdown Text Clicked** y **On Markdown Text Hovered** para reaccionar a estos eventos. Ambos listeners exponen el ID del evento como `$$text_event_id`.

## Imágenes

Markdown admite mostrar imágenes en el contenido de texto.

FancyMenu admite recursos de Minecraft, recursos locales y recursos web en Markdown.

Para añadir una imagen, empieza una línea de texto con `![](`, luego la [URL, ubicación del recurso o ruta al recurso](/resources) y después `)`.

Así que, para mostrar el recurso web `https://example-website.net/image.png`, haz esto:
`![](https://example-website.net/image.png)`

Las imágenes también pueden ser **hipervínculos** envolviendo toda la línea de texto de la imagen en un **hipervínculo**, así:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> ¡Los recursos locales deben estar en `/config/fancymenu/assets/`!
{.is-warning}

## Cita

Para dar formato al texto como una cita, empieza una línea de texto con `> `.
Esto formateará todas las líneas siguientes como cita hasta que encuentre una línea **vacía**.

Ejemplo:
```
Esto no tendrá aspecto de cita.

> Esto tendrá aspecto de cita.
Esto también tendrá aspecto de cita.

Esto ya no tendrá aspecto de cita.
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

Para añadir una línea de separación a tu texto con el ancho de una línea completa, simplemente empieza una línea con `---` y no añadas nada más.

Entonces se verá algo así:

---

## Bloques de código

Los bloques de código pueden ayudarte a mostrar texto como `texto plano` sin que Markdown intente formatearlo, o simplemente a mostrar texto con estilo de código sin ajuste automático de línea.

Un bloque de código de una sola línea (entre otro texto) empieza y termina con \` , lo cual en realidad es bastante difícil de mostrar en un texto Markdown..

Una línea de texto que contiene un bloque de código de una sola línea se ve así:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Los bloques de código multilínea agrupan varias líneas en un bloque de código grande y empiezan con una línea que contiene solo \`\`\` , luego el contenido del texto y después \`\`\` de nuevo:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texto plano

El código de formato de texto plano anulará todos los demás códigos de formato que haya dentro.

Funciona de forma parecida a los bloques de código, pero no lo formatea como un bloque de código. En su lugar, se mostrará como texto normal, pero sin ningún formato.

Para envolver una parte de texto dentro de una línea en un código de formato de texto plano, debes añadir `;;` antes y después de la parte del texto que quieras mostrar como texto plano, así:

```
Esta es una línea de texto con ;;**esta parte**;; mostrándose como texto sin formato con el código de formato ** (negrita) visible y _esta parte_ como texto normal en cursiva con formato.
```

El texto plano también funciona como código envolvente de varias líneas. Para envolver líneas completas, añade `;;;` antes y después de la(s) línea(s) que quieras mostrar como texto plano, así:

```
;;;
Esta línea se mostrará **sin formato** con los códigos de formato ** (negrita) visibles.
Esta línea también se mostrará _sin formato_ con los códigos de formato _ (cursiva) visibles.
;;;

Esta línea volverá a verse **normal** con "normal" formateado como texto en negrita.
```

# Formato de texto de Minecraft

Minecraft tiene por sí mismo un sistema de formato bastante bueno que funciona de forma similar a Markdown, donde añades caracteres especiales a tu contenido de texto para darle formato.

Para leer más sobre el sistema de formato de Minecraft, consulta [esta página de la wiki de Minecraft](https://minecraft.wiki/w/Formatting_codes).

> La wiki dirá que el prefijo del código de formato es `§`, pero en FancyMenu debes sustituirlo por `&`. Todo lo demás se mantiene igual.
{.is-warning}

> Los **elementos de texto** son muy complejos y, para dar soporte a Markdown, el compromiso fue **romper los códigos de formato Vanilla de Minecraft**, así que estos códigos no funcionarán bien en los elementos de texto (solo se formatea la primera palabra después del código de formato, etc.). En su lugar, deberías usar códigos de formato de Markdown en los elementos de texto.
{.is-danger}

# Componentes de texto de Minecraft (sistema de componentes en bruto)

El sistema de componentes de texto de Minecraft es bastante potente para contenido de texto de **una sola línea**, como las **etiquetas de los botones**.

En Minecraft Vanilla puedes usarlo en los comandos `/tellraw` y `/title` (y probablemente en otros lugares).
Se trata de texto con formato serializado en JSON, así que puedes añadir atributos de formato al contenido de texto.

Para aprender más sobre los componentes de texto en detalle, consulta [esta página de la wiki de Minecraft](https://minecraft.wiki/w/Raw_JSON_text_format).
Para aprender más sobre las fuentes en Minecraft, consulta [esta página de la wiki de Minecraft](https://minecraft.wiki/w/Resource_pack#Fonts).

Para que FancyMenu detecte la etiqueta de un botón como **componente de texto**, no pongas nada más que el texto del componente serializado como etiqueta, así:
`{"text":"Texto de la etiqueta del botón","font":"uniform"}`

El ejemplo anterior mostrará la etiqueta del botón `Texto de la etiqueta del botón` con la fuente `uniform`.

> Puedes usar los marcadores de posición de FancyMenu en el valor `text` de los componentes.
{.is-info}
