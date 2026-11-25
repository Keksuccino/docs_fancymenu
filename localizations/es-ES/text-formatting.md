---
title: Formato del texto
description: >-
  Cómo dar formato al texto con Markdown, códigos de formato de Minecraft y
  componentes de texto.
sourceBlobSha: c6ddde5939e929b3d4c04541f0b104ee6ee795bc
---
# Formato del texto

FancyMenu te ofrece tres formas de dar formato al texto:

- **Markdown** para [elementos de texto y de información emergente](/text-in-menus): títulos, listas, colores, imágenes, tablas y mucho más.
- **Códigos de formato de Minecraft**, como `&c`, para aplicar colores rápidamente. Funcionan en casi todos los campos de texto, incluido el texto Markdown.
- **Componentes de texto de Minecraft** para las etiquetas de botones y deslizadores.

> [!TIP]
> Esta página trata sobre *cómo escribir* texto con formato. Para saber cómo añadir texto a tus menús, cambiar su aspecto o hacer que se desplace, consulta [Texto en los menús](/text-in-menus).

<img width="800" alt="Markdown en un elemento de texto" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_showcase.png?raw=true">

# Markdown

Markdown da formato al texto mediante unos pocos caracteres especiales. Por ejemplo, `**negrita**` se convierte en texto en **negrita**.

Markdown funciona en [elementos de texto](/elements#text) y [elementos de información emergente](/elements#tooltip). Los caracteres que escribes determinan *qué* es algo (un título, una lista o una cita). El [aspecto](/text-in-menus#looks-and-styles) del elemento determina cómo se muestra, por ejemplo, sus colores y tamaños.

## Resumen rápido

| Escribes | Obtienes |
|---|---|
| `**negrita**` o `__negrita__` | Texto en negrita |
| `*cursiva*` o `_cursiva_` | Texto en cursiva |
| `++subrayado++` | Texto subrayado |
| `~~tachado~~` | Texto tachado |
| `` `código` `` | Código en línea |
| `[Abrir sitio web](https://example.com)` | Un enlace en el que se puede hacer clic |
| `%#ff5555%texto rojo%#%` | Texto de color |
| `# Título` | Un título |
| `- Elemento` | Una lista con viñetas |
| `1. Elemento` | Una lista numerada |
| `> Texto` | Una cita |
| `> [!TIP]` | Un cuadro informativo |
| `---` | Una línea separadora |

## Estilos de texto

| Estilo | Cómo escribirlo |
|---|---|
| **Negrita** | `**texto**` o `__texto__` |
| **Cursiva** | `*texto*` o `_texto_` |
| **Subrayado** | `++texto++` |
| **Tachado** | `~~texto~~` (también puedes usar un solo `~` a cada lado) |

Puedes combinar estilos, por ejemplo, con `***negrita y cursiva***`.

Los guiones bajos sueltos dentro de las palabras se mantienen como tales, así que `mi_diseño_genial` no aparece en cursiva. Los nombres como `C++` también se mantienen intactos.

> [!TIP]
> En el editor de texto, selecciona un fragmento y pulsa `Ctrl + B`, `Ctrl + I` o `Ctrl + U` (`Cmd` en macOS) para ponerlo en negrita, cursiva o subrayado. Consulta [Atajos de formato](/text-in-menus#formatting-shortcuts).

## Color del texto (HEX)

Escribe `%<color HEX>%` delante del texto y `%#%` detrás:

```
%#77fc03%¡Este texto es verde!%#%
```

El color HEX debe empezar por `#`. También puedes usar nombres de colores:

```
%#red%¡Este texto es rojo!%#%
```

Nombres admitidos: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` y `transparent`.

## Fuentes

Para mostrar texto con otra fuente, escribe `%!!<nombre de la fuente>%` delante y `%!!%` detrás. La fuente puede ser de Minecraft o de un paquete de recursos.

```
%!!uniform%Este texto usa la fuente uniform%!!%
```

## Alineación del texto

De forma predeterminada, el texto se alinea a la izquierda. Para centrar líneas o alinearlas a la derecha, escribe el código de alineación en una línea aparte, antes y después de ellas:

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

## Títulos

Empieza una línea con `# ` (el más grande), `## ` (grande) o `### ` (pequeño):

```
# ¡Bienvenido!
## Novedades
### Título pequeño
```

## Listas

<img width="460" alt="Listas Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_lists.png?raw=true">

### Listas con viñetas

Empieza una línea con `- `. Añade dos espacios delante por cada nivel de anidamiento:

```
- Primer elemento
- Segundo elemento
  - Elemento anidado
    - Aún más anidado
```

### Listas numeradas

Empieza una línea con un número y un punto o un paréntesis:

```
1. Abre la barra de menús
2. Haz clic en Personalización
3) Esto también funciona
```

### Marcadores de notas de actualización

Las líneas también pueden empezar por `+`, `-`, `~` o `*`. Cada uno tiene su propio marcador, ideal para notas de actualización y registros de cambios:

```
+ Se ha añadido un nuevo menú principal
- Se ha eliminado el logotipo antiguo
~ Se han cambiado los colores de los botones
* Se ha corregido un error que provocaba un cierre inesperado al iniciar
```

| Marcador | Significado |
|---|---|
| `+` | Se ha añadido algo |
| `-` | Se ha eliminado algo |
| `~` | Se ha cambiado algo |
| `*` | Algo que merece destacarse |

Un elemento con `-` solo muestra el marcador de «eliminado» si su lista también incluye un elemento con `+`. De lo contrario, se muestra como un elemento normal con viñeta. Puedes cambiar este comportamiento en **Markdown -> Lists -> Extra Markers (+ - ~ \*) -> - Marker Used**.

> [!NOTE]
> Los elementos de texto y de información emergente nuevos tienen activadas las listas numeradas, los marcadores de notas de actualización y las [notas destacadas](#callouts). En los elementos de diseños antiguos están desactivados para que el texto no cambie de repente. Actívalos en el menú **Markdown** del elemento: **Lists -> Numbered Lists**, **Lists -> Extra Markers (+ - ~ \*)** y **Callouts**.

## Citas

Empieza una línea con `> ` para crear una cita. La cita continúa hasta la siguiente línea vacía:

```
> Esto es una cita.
Esta línea también forma parte de la cita.

Esta línea vuelve a ser texto normal.
```

Las líneas de una cita también pueden empezar por `>`. Una línea que solo contenga `>` añade una línea vacía a la cita:

```
> Primer párrafo de la cita.
>
> Segundo párrafo de la cita.
```

## Notas destacadas

Las notas destacadas son cuadros de colores con un icono y una etiqueta, ideales para consejos y advertencias. Escribe una cita cuya primera línea indique el tipo de nota:

```
> [!WARNING]
> ¡No olvides guardar el diseño!
```

<img width="640" alt="Notas destacadas de Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_callouts.png?raw=true">

Hay cinco tipos: `[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]` y `[!CAUTION]`.

## Hiperenlaces

Rodea el texto con `[ ]` y escribe el enlace detrás, entre `( )`:

```
[Visita nuestro sitio web](https://example.com)
```

Los enlaces pueden incluir paréntesis, como `https://en.wikipedia.org/wiki/Minecraft_(video_game)`. Para mostrar corchetes en el texto del enlace, escribe `\` delante de ellos: `[Haz clic \[aquí\]](https://example.com)`.

## Eventos al hacer clic y al pasar el cursor

El texto también puede activar [listeners](/listeners) en lugar de abrir un sitio web. Usa el prefijo `click:` o `hover:` junto con un ID que elijas:

```
[texto en el que se puede hacer clic](click:unique_text_click_event_id)
[texto sobre el que se puede pasar el cursor](hover:unique_text_hover_event_id)
```

Puedes reaccionar a ellos con los listeners [**On Markdown Text Clicked**](/listeners#on-markdown-text-clicked) y [**On Markdown Text Hovered**](/listeners#on-markdown-text-hovered). Ambos proporcionan el ID como `$$text_event_id`.

## Imágenes

Coloca una imagen en su propia línea con `![](` + la fuente de la imagen + `)`:

```
![](https://example.com/image.png)
```

La fuente puede ser una URL web, un archivo local como `/config/fancymenu/assets/image.png` o una imagen de un paquete de recursos. Consulta [Recursos](/resources) para ver todos los tipos de fuentes.

El texto entre corchetes se convierte en el pie de foto de la imagen:

```
![Mi captura de pantalla](/config/fancymenu/assets/screenshot.png)
```

Los pies de foto aparecen debajo de la imagen si está activada la opción **Markdown -> Images -> Caption** del elemento.

Para que se pueda hacer clic en una imagen, inclúyela en un enlace:

```
[![](https://example.com/image.png)](https://example.com)
```

## Tablas

Separa las celdas con `|`. La primera fila es el encabezado y la segunda incluye `---` para cada columna:

```
| Objeto | Precio |
|:---|---:|
| Espada de diamante | 10 |
| Manzana dorada | 5 |
```

Los dos puntos de la segunda fila alinean la columna: `:---` a la izquierda, `:---:` en el centro y `---:` a la derecha. Para mostrar `|` dentro de una celda, escribe `\|`.

<img width="640" alt="Tabla y código Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_table_code.png?raw=true">

## Separadores

Una línea que solo contenga `---` dibuja un separador a lo ancho del texto.

## Código

El código muestra el texto tal cual, sin aplicarle formato.

- **Código en línea:** rodea un fragmento de una línea con `` ` ``, por ejemplo, `` `/spawn` ``.
- **Bloques de código:** escribe una línea con `` ``` `` antes y después del texto. Los bloques de código no ajustan las líneas.

````
```
/give @p minecraft:diamond 64
```
````

Puedes escribir el nombre de un lenguaje detrás del primer `` ``` ``, por ejemplo, `` ```json ``. FancyMenu lo acepta, pero no cambia el aspecto del código.

Los [marcadores de posición](/placeholders) se siguen sustituyendo dentro del código.

## Texto sin formato

El texto sin formato muestra los caracteres de formato tal cual, pero sin el aspecto del código. Rodea un fragmento de una línea con `;;`:

```
Esto muestra ;;**asteriscos**;; en lugar de texto en negrita.
```

Para hacer lo mismo con líneas enteras, escribe `;;;` en una línea aparte, antes y después de ellas:

```
;;;
**Sin negrita**, _sin cursiva_.
;;;
```

## Caracteres de escape

Para mostrar un carácter de formato como texto normal, escribe `\` delante. Por ejemplo, `\*sin cursiva\*` muestra `*sin cursiva*`.

Esto funciona con `\` `` ` `` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `.` `!` `|` `>` `~` y `^`.

# Formato de texto de Minecraft

Los códigos de formato de Minecraft funcionan en la mayoría de los campos de texto de FancyMenu. Usa `&` en lugar de `§`, que es el carácter de Minecraft. Por ejemplo, `&cAdvertencia` muestra el texto en rojo y `&l` pone el texto en negrita. `&r` restablece el formato.

Consulta la [Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes) para ver todos los códigos.

Los códigos de formato también funcionan en el texto Markdown, excepto dentro del código y del texto sin formato. Para estilos como la negrita y la cursiva, Markdown suele ser más fácil de leer, pero los códigos vienen bien para aplicar colores rápidamente.

# Componentes de texto de Minecraft (sistema Raw Component)

Los componentes de texto de Minecraft son textos con formato escritos en JSON. Funcionan para textos de **una sola línea**, como las **etiquetas de botones y deslizadores**, pero no en los elementos de texto.

Para usar uno, establece el componente como único contenido de la etiqueta:

```
{"text":"Texto de la etiqueta del botón","font":"uniform"}
```

Esto muestra `Texto de la etiqueta del botón` con la fuente `uniform`. Puedes usar [marcadores de posición](/placeholders) en el valor de `text`.

Para obtener más información, consulta las páginas de Minecraft Wiki sobre el [formato de componentes de texto](https://minecraft.wiki/w/Raw_JSON_text_format) y las [fuentes](https://minecraft.wiki/w/Resource_pack#Fonts).
