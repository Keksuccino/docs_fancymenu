---
title: Formato de texto
description: >-
  Cómo dar formato al texto con Markdown, códigos de formato de Minecraft y
  componentes de texto.
sourceBlobSha: c6ddde5939e929b3d4c04541f0b104ee6ee795bc
---
# Formato de texto

FancyMenu te ofrece tres formas de dar formato al texto:

- **Markdown** para [elementos de texto e información sobre herramientas](/text-in-menus): encabezados, listas, colores, imágenes, tablas y más.
- **Códigos de formato de Minecraft**, como `&c`, para aplicar colores rápidamente. Funcionan en casi todos los campos de texto, incluso en el texto Markdown.
- **Componentes de texto de Minecraft** para las etiquetas de botones y controles deslizantes.

> [!TIP]
> Esta página trata sobre *cómo escribir* texto con formato. Para aprender a agregar texto a tus menús, cambiar su apariencia o hacer que se desplace, consulta [Texto en los menús](/text-in-menus).

<img width="800" alt="Markdown en un elemento de texto" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_showcase.png?raw=true">

# Markdown

Markdown da formato al texto con unos cuantos caracteres especiales a su alrededor. Por ejemplo, `**negritas**` se convierte en texto **en negritas**.

Markdown funciona en los [elementos de texto](/elements#text) y los [elementos de información sobre herramientas](/elements#tooltip). Los caracteres que escribes determinan *qué* es algo (un encabezado, una lista o una cita). La [apariencia](/text-in-menus#looks-and-styles) del elemento determina cómo se ve, por ejemplo, sus colores y tamaños.

## Resumen rápido

| Escribes | Obtienes |
|---|---|
| `**negritas**` o `__negritas__` | Texto en negritas |
| `*cursiva*` o `_cursiva_` | Texto en cursiva |
| `++subrayado++` | Texto subrayado |
| `~~tachado~~` | Texto tachado |
| `` `código` `` | Código en línea |
| `[Abrir sitio web](https://example.com)` | Un enlace en el que se puede hacer clic |
| `%#ff5555%texto rojo%#%` | Texto de color |
| `# Encabezado` | Un encabezado |
| `- Elemento` | Una lista con viñetas |
| `1. Elemento` | Una lista numerada |
| `> Texto` | Una cita |
| `> [!TIP]` | Un recuadro informativo |
| `---` | Una línea separadora |

## Estilos de texto

| Estilo | Cómo escribirlo |
|---|---|
| **Negritas** | `**texto**` o `__texto__` |
| **Cursiva** | `*texto*` o `_texto_` |
| **Subrayado** | `++texto++` |
| **Tachado** | `~~texto~~` (también puedes usar un solo `~` a cada lado) |

Puedes combinar estilos, por ejemplo: `***negritas y cursiva***`.

Los guiones bajos individuales dentro de las palabras se mantienen como guiones bajos normales, así que `mi_diseño_genial` no se convierte en cursiva. Nombres como `C++` también se conservan tal cual.

> [!TIP]
> En el editor de texto, selecciona un texto y presiona `Ctrl + B`, `Ctrl + I` o `Ctrl + U` (`Cmd` en macOS) para ponerlo en negritas, cursiva o subrayarlo. Consulta [Atajos de formato](/text-in-menus#formatting-shortcuts).

## Color del texto (HEX)

Coloca `%<color HEX>%` antes del texto y `%#%` después:

```
%#77fc03%¡Este texto es verde!%#%
```

El color HEX debe comenzar con `#`. También puedes usar nombres de colores:

```
%#red%¡Este texto es rojo!%#%
```

Nombres compatibles: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` y `transparent`.

## Fuentes

Para mostrar texto con otra fuente, coloca `%!!<nombre de la fuente>%` antes del texto y `%!!%` después. La fuente puede ser de Minecraft o de un paquete de recursos.

```
%!!uniform%Este texto usa la fuente uniform%!!%
```

## Alineación del texto

De forma predeterminada, el texto se alinea a la izquierda. Para centrar líneas o alinearlas a la derecha, coloca el código de alineación en una línea aparte, antes y después de ellas:

- `^^^` centra las líneas.
- `|||` las alinea a la derecha.

```
Esta línea está alineada a la izquierda.

^^^
Esta línea está centrada.
Esta también.
^^^

|||
Esta línea está alineada a la derecha.
|||
```

> [!TIP]
> En el editor de texto, `Ctrl + L`, `Ctrl + E` y `Ctrl + R` (`Cmd` en macOS) alinean las líneas seleccionadas a la izquierda, al centro o a la derecha.

## Encabezados

Comienza una línea con `# ` (el más grande), `## ` (grande) o `### ` (pequeño):

```
# ¡Te damos la bienvenida!
## Noticias
### Encabezado pequeño
```

## Listas

<img width="460" alt="Listas en Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_lists.png?raw=true">

### Listas con viñetas

Comienza una línea con `- `. Agrega dos espacios delante por cada nivel de anidación:

```
- Primer elemento
- Segundo elemento
  - Elemento anidado
    - Uno más profundo
```

### Listas numeradas

Comienza una línea con un número y un punto o un paréntesis:

```
1. Abre la barra de menús
2. Haz clic en Personalización
3) Esta opción también funciona
```

### Marcadores de notas de actualización

Las líneas también pueden comenzar con `+`, `-`, `~` o `*`. Cada uno tiene su propio marcador, ideal para notas de actualización y registros de cambios:

```
+ Se agregó un nuevo menú principal
- Se eliminó el logotipo anterior
~ Se cambiaron los colores de los botones
* Se corrigió un cierre inesperado al iniciar
```

| Marcador | Significado |
|---|---|
| `+` | Se agregó algo |
| `-` | Se eliminó algo |
| `~` | Se cambió algo |
| `*` | Algo que vale la pena destacar |

Un elemento con `-` solo recibe el marcador de «eliminado» cuando su lista también tiene un elemento con `+`. De lo contrario, es un elemento normal de una lista con viñetas. Puedes cambiar este comportamiento en **Markdown -> Lists -> Extra Markers (+ - ~ \*) -> - Marker Used**.

> [!NOTE]
> Los nuevos elementos de texto e información sobre herramientas tienen activadas las listas numeradas, los marcadores de notas de actualización y las [llamadas destacadas](#callouts). Estos están desactivados en los elementos de diseños anteriores para que su texto no cambie de repente. Actívalos en el menú **Markdown** del elemento: **Lists -> Numbered Lists**, **Lists -> Extra Markers (+ - ~ \*)** y **Callouts**.

## Citas

Comienza una línea con `> ` para convertirla en una cita. La cita continúa hasta la siguiente línea vacía:

```
> Esto es una cita.
Y esta línea también forma parte de ella.

Esta línea vuelve a ser texto normal.
```

Las líneas dentro de una cita también pueden comenzar con `>`. Además, una línea que solo contiene `>` agrega una línea vacía a la cita:

```
> Primer párrafo de la cita.
>
> Segundo párrafo de la cita.
```

## Llamadas destacadas

Las llamadas destacadas son recuadros de colores con un ícono y una etiqueta, ideales para consejos y advertencias. Escribe una cita cuya primera línea indique el tipo de llamada:

```
> [!WARNING]
> ¡No olvides guardar tu diseño!
```

<img width="640" alt="Llamadas destacadas en Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_callouts.png?raw=true">

Hay cinco tipos: `[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]` y `[!CAUTION]`.

## Hipervínculos

Encierra el texto entre `[ ]` y coloca el enlace detrás, entre `( )`:

```
[Visita nuestro sitio web](https://example.com)
```

Los enlaces pueden incluir paréntesis, como `https://en.wikipedia.org/wiki/Minecraft_(video_game)`. Para mostrar corchetes en el texto del enlace, coloca `\` delante de ellos: `[Haz clic \[aquí\]](https://example.com)`.

## Eventos al hacer clic y al pasar el cursor

El texto también puede activar [escuchas](/listeners) en lugar de abrir un sitio web. Usa el prefijo `click:` o `hover:` con el ID que prefieras:

```
[texto en el que se puede hacer clic](click:unique_text_click_event_id)
[texto sobre el que se puede pasar el cursor](hover:unique_text_hover_event_id)
```

Reacciona a ellos con las escuchas [**On Markdown Text Clicked**](/listeners#on-markdown-text-clicked) y [**On Markdown Text Hovered**](/listeners#on-markdown-text-hovered). Ambas proporcionan el ID como `$$text_event_id`.

## Imágenes

Coloca una imagen en su propia línea con `![](` + la fuente de la imagen + `)`:

```
![](https://example.com/image.png)
```

La fuente puede ser una URL web, un archivo local como `/config/fancymenu/assets/image.png` o una imagen de un paquete de recursos. Consulta [Recursos](/resources) para ver todos los tipos de fuentes.

El texto entre corchetes se convierte en el pie de foto de la imagen:

```
![Mi captura de pantalla genial](/config/fancymenu/assets/screenshot.png)
```

Los pies de foto aparecen debajo de la imagen si la opción **Markdown -> Images -> Caption** del elemento está activada.

Para hacer que se pueda hacer clic en una imagen, envuélvela en un enlace:

```
[![](https://example.com/image.png)](https://example.com)
```

## Tablas

Separa las celdas con `|`. La primera fila es el encabezado y la segunda contiene `---` para cada columna:

```
| Objeto | Precio |
|:---|---:|
| Espada de diamante | 10 |
| Manzana dorada | 5 |
```

Los dos puntos de la segunda fila alinean la columna: `:---` a la izquierda, `:---:` al centro y `---:` a la derecha. Para mostrar un `|` dentro de una celda, escribe `\|`.

<img width="640" alt="Tabla y código en Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_table_code.png?raw=true">

## Separadores

Una línea que solo contiene `---` dibuja un separador a lo ancho del texto.

## Código

El código muestra el texto tal cual, sin darle formato.

- **Código en línea:** encierra una parte de la línea entre `` ` ``, como `` `/spawn` ``.
- **Bloques de código:** coloca una línea con `` ``` `` antes y después del texto. Las líneas de los bloques de código no se ajustan automáticamente.

````
```
/give @p minecraft:diamond 64
```
````

Puedes escribir el nombre de un lenguaje después del primer `` ``` ``, por ejemplo, `` ```json ``. FancyMenu lo acepta, pero no cambia la apariencia del código.

Los [marcadores de posición](/placeholders) se siguen reemplazando dentro del código.

## Texto sin formato

El texto sin formato muestra los caracteres de formato tal cual, pero sin la apariencia del código. Encierra una parte de la línea entre `;;`:

```
Esto muestra ;;**asteriscos**;; en lugar de texto en negritas.
```

Para hacerlo con líneas completas, coloca `;;;` en una línea aparte antes y después de ellas:

```
;;;
**Sin negritas**, _sin cursiva_.
;;;
```

## Escapar caracteres

Para mostrar un carácter de formato como texto normal, coloca `\` delante. Por ejemplo, `\*sin cursiva\*` muestra `*sin cursiva*`.

Esto funciona con `\` `` ` `` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `.` `!` `|` `>` `~` y `^`.

# Formato de texto de Minecraft

Los códigos de formato de Minecraft funcionan en la mayoría de los campos de texto de FancyMenu. Usa `&` en lugar de `§`, que es el carácter de Minecraft. Por ejemplo, `&cAdvertencia` muestra texto rojo y `&l` pone el texto en negritas. `&r` restablece el formato.

Consulta la [wiki de Minecraft](https://minecraft.wiki/w/Formatting_codes) para ver todos los códigos.

Los códigos de formato también funcionan en el texto Markdown, excepto dentro del código y del texto sin formato. Para estilos como las negritas y la cursiva, Markdown suele ser más fácil de leer, pero los códigos son útiles para aplicar colores rápidamente.

# Componentes de texto de Minecraft (sistema de componentes sin procesar)

Los componentes de texto de Minecraft son texto con formato escrito en JSON. Funcionan con texto de **una sola línea**, como las **etiquetas de botones y controles deslizantes**, pero no con los elementos de texto.

Para usar uno, configura la etiqueta únicamente con el componente:

```
{"text":"Texto de la etiqueta del botón","font":"uniform"}
```

Esto muestra `Texto de la etiqueta del botón` con la fuente `uniform`. Puedes usar [marcadores de posición](/placeholders) en el valor de `text`.

Para obtener más información, consulta las páginas de la wiki de Minecraft sobre el [formato de componentes de texto](https://minecraft.wiki/w/Raw_JSON_text_format) y las [fuentes](https://minecraft.wiki/w/Resource_pack#Fonts).
