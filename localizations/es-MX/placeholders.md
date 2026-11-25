---
title: Marcadores de posición
description: >-
  Muestra valores en tiempo real, como el nombre del jugador, la hora o el
  número de jugadores de un servidor, en tus textos, y consulta todos los
  marcadores de posición de FancyMenu.
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# Marcadores de posición

Los marcadores de posición son códigos breves que FancyMenu reemplaza con un valor en tiempo real, como el nombre del jugador, la hora o el número de jugadores de un servidor. Funcionan en los textos de los elementos, las etiquetas de los botones, la información sobre herramientas, los valores de las acciones y los requisitos, y en casi cualquier otro texto que puedas escribir.

<img width="800" alt="Cómo agregar el marcador de posición del nombre del jugador a un elemento de texto en el editor de diseños: marcadores de posición en el editor de texto, la categoría Jugador y un texto que saluda al jugador por su nombre" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> Tus propias [variables](/variables) también funcionan en esos textos con `$$` seguido de su nombre, por ejemplo, `$$coins`.

# Cómo agregar marcadores de posición

1. Abre el texto en el editor de texto, por ejemplo, **Contenido del texto** de un [elemento de texto](/text-in-menus). Los campos de texto en ventanas, como los valores de las acciones, tienen un botón **Abrir en el editor** a un lado.
2. Haz clic donde quieras colocar el marcador de posición.
3. Haz clic en **Marcadores de posición**, en la esquina superior derecha del editor de texto.
4. Haz clic en una categoría o busca por nombre, identificador o descripción. **ATRÁS** vuelve a las categorías. Los marcadores de posición sin categoría aparecen debajo de las categorías.
5. Pasa el cursor sobre un marcador de posición para ver qué hace y haz clic en él para agregarlo.
6. Reemplaza sus valores de ejemplo, como el ID del mod en **Versión del mod**.

Los textos cuyo editor no tiene el botón **Marcadores de posición** no admiten marcadores de posición.

# Cómo funcionan los marcadores de posición

Un marcador de posición se ve así:

```
{"placeholder":"playername"}
```

Los marcadores de posición con opciones las tienen en `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- El identificador, como `playername`, distingue entre mayúsculas y minúsculas. A continuación se muestra el identificador y los valores de cada marcador de posición.
- El orden de los valores no importa. Puedes omitir los valores marcados como opcionales.
- Si FancyMenu no puede reemplazar un marcador de posición, por ejemplo, si tiene un error tipográfico, lo deja tal como lo escribiste.
- Los marcadores de posición siempre devuelven texto. Cuando no hay nada que mostrar, devuelven un valor alternativo, como `0`, `0.0`, `---` o nada.
- Los [códigos de formato](/text-formatting) funcionan alrededor de los marcadores de posición: `&6{"placeholder":"playername"}` muestra el nombre en dorado.

> [!IMPORTANT]
> Los marcadores de posición parecen JSON, pero no lo son. No los pases por un formateador ni un validador de JSON, porque los marcadores de posición dentro de otros marcadores de posición no son JSON válido.

## Marcadores de posición dentro de otros marcadores de posición

Los valores pueden contener otros marcadores de posición y [variables](/variables#showing-variables-in-text). FancyMenu reemplaza primero los que están dentro. No es necesario escapar las comillas dentro de los valores.

Esto convierte la RAM máxima de MB a GB:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

Esto muestra la variable `rank` en mayúsculas:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

Cuando un marcador de posición devuelve texto que contiene otros marcadores de posición, como un archivo leído con [**Texto de archivo**](#texto-de-archivo), FancyMenu también los reemplaza.

# Información útil

- Los marcadores de posición se actualizan automáticamente. FancyMenu conserva el texto reemplazado durante 30 milisegundos antes de volver a reemplazar sus marcadores de posición. Puedes cambiarlo con **Duración del almacenamiento en caché de marcadores de posición [MS]** en **barra de menú -> Personalización -> Configuración**. El valor `0` los reemplaza en cada fotograma, lo que consume más rendimiento.
- Los marcadores de posición que leen sitios web, archivos o servidores, como **Texto web** o **Estado del servidor**, se cargan en segundo plano. Mientras tanto, no devuelven nada o muestran un valor alternativo.
- En las [acciones](/action-scripts), los marcadores de posición obtienen su valor actual justo cuando se ejecuta la acción.
- Los marcadores de posición relacionados con el mundo, la pantalla y los elementos solo funcionan en el hilo principal del juego. En un [Ticker](/elements#ticker) que se ejecuta en segundo plano (de forma asíncrona), FancyMenu muestra un error.
- **Número aleatorio** genera un número nuevo cada vez que se actualiza el texto. Para conservar uno, guárdalo en una [variable](/variables) con [**Establecer valor de variable (FM Variable)**](/action-scripts#set-variable-value-fm-variable).

> [!CAUTION]
> Marcadores de posición como **Analizador JSON**, **Texto de archivo** y **Contenido del portapapeles** pueden leer archivos de la carpeta del juego y el portapapeles. Si se combinan con acciones que se conectan a sitios web, un diseño podría enviar esos datos a otro lugar. Usa únicamente diseños en los que confíes.

# Ejemplos

## Panel de bienvenida

<img width="800" alt="Un elemento de texto saluda al jugador por su nombre y muestra la versión de Minecraft, el número de mods y la hora" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### ¡Qué bueno que volviste, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"} con {"placeholder":"loadedmods"} mods
Son las {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Estado del servidor y jugadores

```
Supervivencia: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}} jugadores
```

## Fecha y hora

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}, {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Uso de RAM

```
RAM: {"placeholder":"usedram"} / {"placeholder":"maxram"} MB ({"placeholder":"percentram"}%)
```

# Todos los marcadores de posición

Aquí están todos los marcadores de posición de FancyMenu. Las categorías grandes **Avanzado** y **Mundo** del menú de marcadores de posición se dividen aquí en grupos más pequeños.

## Variables y listas

Están en la categoría **Avanzado**. Consulta [Variables](/variables) para aprender a crear variables y listas.

### Obtener valor de variable (FM Variable)

**Identificador:** `getvariable`

El valor de una de tus variables. Devuelve `0` cuando la variable está vacía o no existe, por lo que es útil para números. Una lista devuelve todas sus entradas como un arreglo JSON, por ejemplo, `["Steve","Alex"]`.

- `name`: el nombre de la variable, sin `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Obtener entrada de lista (FM Variable)

**Identificador:** `list_get`

Una entrada de una variable de lista.

- `name`: el nombre de la lista
- `index`: la posición de la entrada. La primera entrada es `0` y los números negativos cuentan desde el final, así que `-1` es la última entrada.
- `fallback` (opcional): lo que se devuelve si no hay una entrada en ese índice o no existe una lista con ese nombre. De manera predeterminada, está vacío.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"Aún no hay consejos"}}
```

### Tamaño de lista (FM Variable)

**Identificador:** `list_size`

Cuántas entradas tiene una lista. Devuelve `0` si no existe una lista con ese nombre.

- `name`: el nombre de la lista

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Índice de entrada de lista (FM Variable)

**Identificador:** `list_index_of`

El índice de la primera entrada que coincide con todo el `value`, o `-1` si la lista no la contiene.

- `name`: el nombre de la lista
- `value`: la entrada que quieres buscar
- `ignore_case` (opcional): `true` hace que `Apple` coincida con `apple`. De manera predeterminada, es `false`.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Unir entradas de lista (FM Variable)

**Identificador:** `list_join`

Todas las entradas de una lista en un solo texto. Devuelve un texto vacío si no existe una lista con ese nombre.

- `name`: el nombre de la lista
- `separator` (opcional): el texto que separa las entradas. `\n` representa un salto de línea. De manera predeterminada, es `, `.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Matemáticas

Están en la categoría **Avanzado**. Los números usan punto decimal, como `2.5`.

### Calculadora

**Identificador:** `calc`

Resuelve una expresión matemática, como `2 + 3 * 4`.

- `expression`: la operación que se va a resolver
- `decimal` (opcional): `false` redondea el resultado a un número entero. De manera predeterminada, es `true`, lo que puede dar resultados como `14.0`.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| En las expresiones | Qué hace |
|---|---|
| `+` `-` `*` `/` | Sumar, restar, multiplicar y dividir |
| `^` | Potencia, como `2 ^ 3`, que da 8 |
| `%` | Residuo, como `7 % 3`, que da 1 |
| `( )` | Agrupa partes, como `(2 + 3) * 4` |
| `pi`, `e` | Los números π y e |
| `abs(x)` | El número sin el signo negativo |
| `sqrt(x)`, `cbrt(x)` | Raíz cuadrada y raíz cúbica |
| `pow(x, y)` | x elevado a la potencia de y |
| `floor(x)`, `ceil(x)` | Redondea hacia abajo y hacia arriba |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Trigonometría, con ángulos en radianes |
| `asin(x)`, `acos(x)`, `atan(x)` | Trigonometría inversa |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Funciones hiperbólicas |
| `log(x)`, `log2(x)`, `log10(x)` | Logaritmos de base e, 2 y 10 |
| `exp(x)` | e elevado a la potencia de x |
| `signum(x)` | `1`, `-1` o `0`, como [**Signo (Matemáticas)**](#signo-matemáticas) |

### Número aleatorio

**Identificador:** `random_number`

Un número entero aleatorio entre `min` y `max`. Cambia cada vez que se actualiza el texto.

- `min`, `max`: el número menor y el mayor

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Número máximo

**Identificador:** `maxnum`

El mayor de dos números.

- `first`, `second`: los números

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Número mínimo

**Identificador:** `minnum`

El menor de dos números.

- `first`, `second`: los números

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Valor absoluto

**Identificador:** `absnum`

El número sin el signo negativo; por ejemplo, `-10.5` devuelve `10.5`.

- `num`: el número

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Negar número

**Identificador:** `negnum`

Convierte un número positivo en negativo; por ejemplo, `10.5` devuelve `-10.5`. El cero y los números negativos no cambian.

- `num`: el número

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Redondear (Matemáticas)

**Identificador:** `math_round`

Redondea un número. `2.5` se redondea a `3`.

- `num`: el número
- `decimals` (opcional): cuántos decimales conservar; por ejemplo, `2` convierte `3.14159` en `3.14`. El valor `0`, `-1` o la ausencia de este parámetro redondea a un número entero.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Piso (Matemáticas)

**Identificador:** `math_floor`

Redondea un número hacia abajo al entero más cercano; por ejemplo, `3.7` devuelve `3` y `-3.2` devuelve `-4`.

- `num`: el número

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Techo (Matemáticas)

**Identificador:** `math_ceil`

Redondea un número hacia arriba al entero más cercano; por ejemplo, `3.2` devuelve `4` y `-3.7` devuelve `-3`.

- `num`: el número

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Signo (Matemáticas)

**Identificador:** `math_sign`

Devuelve `1` para los números positivos, `-1` para los negativos y `0` para el cero.

- `num`: el número

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (Matemáticas)

**Identificador:** `math_pi`

El número π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Seno trigonométrico (Matemáticas)

**Identificador:** `math_sin`

El seno de un ángulo en radianes. Para usar grados, multiplícalos primero por π / 180 con la Calculadora.

- `angle`: el ángulo en radianes

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Coseno trigonométrico (Matemáticas)

**Identificador:** `math_cos`

El coseno de un ángulo en radianes.

- `angle`: el ángulo en radianes

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Tangente trigonométrica (Matemáticas)

**Identificador:** `math_tan`

La tangente de un ángulo en radianes.

- `angle`: el ángulo en radianes

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Seno hiperbólico (Matemáticas)

**Identificador:** `math_sinh`

El seno hiperbólico de un número.

- `num`: el número

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Coseno hiperbólico (Matemáticas)

**Identificador:** `math_cosh`

El coseno hiperbólico de un número.

- `num`: el número

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Tangente hiperbólica (Matemáticas)

**Identificador:** `math_tanh`

La tangente hiperbólica de un número.

- `num`: el número

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Convertidor de bases numéricas

**Identificador:** `number_base_convert`

Convierte un número a otra base, por ejemplo, de decimal a binario o hexadecimal. También admite decimales, con hasta 16 dígitos después del punto. Las letras del resultado se muestran en mayúsculas, como `FF`.

- `input`: el número
- `from_base` (opcional): la base de `input`, de `2` a `36`. De manera predeterminada, es `10`.
- `to_base` (opcional): la base del resultado, de `2` a `36`. De manera predeterminada, es `10`.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Texto

Estos marcadores están en la categoría **Avanzado**.

### Texto en mayúsculas

**Identificador:** `uppercase_text`

Convierte el texto a mayúsculas: `Hello World` devuelve `HELLO WORLD`. Los [códigos de formato](/text-formatting), como `&a`, no cambian.

- `text`: el texto

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Texto en minúsculas

**Identificador:** `lowercase_text`

Convierte el texto a minúsculas: `HELLO WORLD` devuelve `hello world`. Los códigos de formato no cambian.

- `text`: el texto

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Texto en formato de título

**Identificador:** `title_case_text`

Cada palabra empieza con mayúscula: `hello world` devuelve `Hello World`. Los códigos de formato no cambian.

- `text`: el texto

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Texto en formato de oración

**Identificador:** `sentence_case_text`

Cada oración empieza con mayúscula: `hello world. this is fancymenu!` devuelve `Hello world. This is fancymenu!`. Los códigos de formato no cambian.

- `text`: el texto

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Texto en formato snake_case

**Identificador:** `snake_case_text`

Convierte el texto a minúsculas y separa las palabras con `_`: `Hello World` devuelve `hello_world`. Se eliminan los códigos de formato.

- `text`: el texto

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Texto en formato kebab-case

**Identificador:** `kebab_case_text`

Convierte el texto a minúsculas y separa las palabras con `-`: `Hello World` devuelve `hello-world`. Se eliminan los códigos de formato.

- `text`: el texto

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Texto con mayúsculas alternadas

**Identificador:** `alternating_case_text`

Alterna letras minúsculas y mayúsculas: `alternating case` devuelve `aLtErNaTiNg CaSe`.

- `text`: el texto

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Invertir mayúsculas y minúsculas

**Identificador:** `toggle_case_text`

Convierte las minúsculas en mayúsculas y las mayúsculas en minúsculas: `Toggle Case` devuelve `tOGGLE cASE`.

- `text`: el texto

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Quitar espacios al inicio y al final

**Identificador:** `trim_text`

Quita los espacios del inicio y el final del texto. Los espacios internos se conservan.

- `text`: el texto

```
{"placeholder":"trim_text","values":{"text":"  ¡Te damos la bienvenida!  "}}
```

### Recortar texto

**Identificador:** `crop_text`

Quita cierta cantidad de caracteres del inicio y el final del texto. Si se quita 1 carácter de cada lado de `hello world`, el resultado es `ello worl`.

- `text`: el texto
- `remove_from_start`: cuántos caracteres quitar del inicio
- `remove_from_end`: cuántos caracteres quitar del final

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Dividir texto

**Identificador:** `split_text`

Divide un texto y devuelve una de sus partes. Si `Steve,Alex,Notch` se divide en `,`, la parte `1` es `Alex`.

- `input`: el texto
- `regex`: dónde dividirlo, mediante una expresión regular. Algunos caracteres, como `.`, `|` y `?`, necesitan un `\` antes, por ejemplo, `\.`.
- `max_parts` (opcional): el número máximo de partes en que se divide el texto. `-1` (el valor predeterminado) lo divide en cada coincidencia.
- `split_index`: la parte que se devuelve. La primera parte es `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Reemplazar texto

**Identificador:** `replace_text`

Reemplaza partes de un texto: si se reemplaza `World` por `FancyMenu` en `Hello World!`, el resultado es `Hello FancyMenu!`.

- `text`: el texto
- `search`: lo que se va a buscar
- `replacement` (opcional): lo que se pondrá en su lugar. De manera predeterminada, está vacío, así que se elimina lo que se encuentre.
- `use_regex` (opcional): `true` hace que `search` sea una expresión regular. En ese caso, `$1`, `$2` y así sucesivamente en `replacement` representan los grupos encontrados. De manera predeterminada, es `false`.
- `replace_all` (opcional): `false` reemplaza solo la primera coincidencia. De manera predeterminada, es `true`.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Selección por valor

**Identificador:** `switch_case`

Devuelve el resultado del caso que coincide con un valor. Si la variable `difficulty_level` es `2`, el ejemplo devuelve `Hard Mode`.

- `value`: el valor que se va a comprobar
- `cases`: pares de valor y resultado, como `1:Easy Mode,2:Hard Mode`. Los valores y resultados no pueden contener `,` ni `:`.
- `default` (opcional): el resultado cuando ningún caso coincide. Si no se especifica, el marcador de posición se deja tal como está.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localizar texto

**Identificador:** `local`

El texto de una clave de localización en el idioma actual del juego; por ejemplo, `Singleplayer` para `menu.singleplayer`. Funciona con las claves de Minecraft, las de los mods y las tuyas (consulta [Localización](/localization)).

- `key`: la clave de localización

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Convertir a cadena segura

**Identificador:** `stringify`

Primero reemplaza los marcadores de posición del texto y después antepone `\` a cada `"`, `{` y `}`. Así, el texto externo, como el de un sitio web, no puede convertirse en marcadores de posición.

- `text`: el texto

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Datos y archivos

Estos marcadores están en la categoría **Avanzado**. Las rutas locales empiezan en la carpeta del juego, por ejemplo, `/config/fancymenu/assets/news.txt`, y no pueden salir de ella (consulta [Recursos](/resources#local-resources)).

### Analizador JSON

**Identificador:** `json`

Lee un valor de JSON. Si hay varios resultados, muestra uno por línea.

- `source`: texto JSON, un archivo JSON de la carpeta del juego o la URL de un archivo JSON
- `json_path`: la ruta al valor, como `$.name` o `$.players[0].name`. Consulta [json.fancymenu.net](https://json.fancymenu.net) para obtener más información sobre las rutas JSON.

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

El JSON de la web se carga una vez y vuelve a cargarse cuando FancyMenu se actualiza. Los cambios en los archivos aparecen de inmediato.

| Ruta | Qué devuelve |
|---|---|
| `$.name` | El valor de `name` en el nivel superior |
| `$.player.level` | `level` dentro de `player` |
| `$.items[0].id` | El valor de `id` de la primera entrada de `items` |
| `$.scores.*` | Todos los valores dentro de `scores` |

### Texto de archivo

**Identificador:** `file_text`

El texto de un archivo o una URL. Los archivos se vuelven a leer cada segundo y las URL cada 10 segundos. No devuelve nada mientras se carga el texto o si no se puede leer.

- `path_or_url`: un archivo de la carpeta del juego o una URL. Las rutas que empiezan con `.minecraft/` apuntan a la carpeta predeterminada de Minecraft.
- `mode` (opcional): `all` para todo el texto o `last` para las últimas líneas. De manera predeterminada, es `all`.
- `separator` (opcional): el texto que separa las líneas. De manera predeterminada, es `\n` (un salto de línea).
- `last_lines` (opcional): cuántas líneas devuelve `last`. De manera predeterminada, es `1`.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### Tamaño de archivo

**Identificador:** `file_size`

El tamaño de un archivo en bytes. Devuelve `0` si el archivo no existe. Las rutas que empiezan con `.minecraft/` apuntan a la carpeta predeterminada de Minecraft.

- `path`: el archivo

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### MD5 de archivo

**Identificador:** `file_md5`

El hash MD5 de un archivo, como `d41d8cd98f00b204e9800998ecf8427e`. Devuelve un texto vacío si el archivo no existe. Las rutas que empiezan con `.minecraft/` apuntan a la carpeta predeterminada de Minecraft.

- `path`: el archivo

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Codificar en Base64

**Identificador:** `base64_encode`

El texto codificado en Base64: `Hello World` devuelve `SGVsbG8gV29ybGQ=`.

- `text`: el texto

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decodificar de Base64

**Identificador:** `base64_decode`

Convierte Base64 de nuevo a texto: `SGVsbG8gV29ybGQ=` devuelve `Hello World`.

- `text`: el texto en Base64

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Obtener datos NBT (del cliente)

**Identificador:** `nbt_data_get`

Lee datos NBT, como `/data get`, de la información que el juego tiene sobre el mundo. Es rápido, pero los servidores no envían toda la información a los jugadores.

- `source_type`: `entity` o `block`
- `entity_selector`: para `entity`, un selector como `@s` (tú), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]`, o el nombre o UUID de una entidad. Los selectores pueden tener `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` y `dz`. Se usa la primera coincidencia.
- `block_pos`: para `block`, la posición de una entidad de bloque, como un cofre: `120 64 -35`
- `nbt_path`: la ruta NBT, como `foodLevel` o `Inventory[0].id`
- `scale` (opcional): multiplica los números. De manera predeterminada, es `1.0`.
- `return_type` (opcional): `value` (números y textos tal cual), `string`, `snbt` o `json`. De manera predeterminada, es `value`.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Obtener datos NBT (del servidor)

**Identificador:** `nbt_data_get_server`

Lee datos NBT del servidor, exactamente como `/data get`. Requiere que FancyMenu esté instalado en el servidor. Siempre funciona en un mundo de un jugador. No devuelve nada hasta que el servidor responde; después, se actualiza aproximadamente cada 100 milisegundos.

- `source_type`: `entity`, `block` o `storage`
- `entity_selector`: para `entity`, cualquier selector de `/data get` que encuentre una sola entidad, como `@s` o `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: para `block`, una posición como `120 64 -35`, `~ ~-1 ~` o `^ ^ ^1`
- `storage_id`: para `storage`, el ID de un almacenamiento de comandos, como `mypack:quests`
- `nbt_path` (opcional): la ruta NBT. Si no se especifica, devuelve todos los datos.
- `scale` (opcional): multiplica los números. De manera predeterminada, es `1.0`.
- `return_type` (opcional): `value`, `string`, `snbt` o `json`. De manera predeterminada, es `value`.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Audio

Estos marcadores leen los [elementos de audio](/elements#audio) del menú abierto. Haz clic derecho en un elemento de audio en el editor de diseños y selecciona **Copiar ID del elemento** para obtener su ID.

### Volumen del elemento de audio

**Identificador:** `audio_element_vol`

El volumen del elemento de audio, de `0.0` (0 %) a `1.0` (100 %).

- `element_identifier`: el ID del elemento de audio

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Pista de audio actual

**Identificador:** `audio_element_current_track`

El nombre del archivo de la pista que se reproduce en ese momento, como `menu_theme.ogg`. Devuelve `---` si no se reproduce ninguna pista.

- `element_identifier`: el ID del elemento de audio
- `display_name_mappings` (opcional): nombres para mostrar en lugar de los nombres de archivo. `=>` separa el nombre del archivo y el nombre para mostrar; `%:%` separa los pares.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Tema del menú%:%credits.ogg=>Tema de créditos"}}
```

### Duración del audio

**Identificador:** `audio_duration`

La duración de la pista actual, como `03:45`. Devuelve `00:00` mientras se carga.

- `element_identifier`: el ID del elemento de audio

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Tiempo de reproducción del audio

**Identificador:** `audio_playtime`

El avance de la pista actual, como `01:30`. Devuelve `00:00` (o `0`) si está detenida.

- `element_identifier`: el ID del elemento de audio
- `show_percentage` (opcional): `true` devuelve el avance de `0` a `100`. De manera predeterminada, es `false`.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Estado de reproducción del audio

**Identificador:** `audio_playing_state`

Devuelve `true` mientras se reproduce el elemento de audio y `false` mientras está en pausa o detenido.

- `element_identifier`: el ID del elemento de audio

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Cliente

Estos marcadores muestran información del juego y sus mods.

### Versión de Minecraft

**Identificador:** `mcversion`

La versión de Minecraft, como `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Nombre del cargador de mods

**Identificador:** `loadername`

El nombre del cargador de mods, como `Fabric` o `NeoForge`.

```
{"placeholder":"loadername"}
```

### Versión del cargador de mods

**Identificador:** `loaderver`

La versión del cargador de mods, como `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Versión del mod

**Identificador:** `modversion`

La versión de un mod instalado, como `3.11.0`. Devuelve `0.0.0` si el mod no está instalado.

- `modid`: el ID del mod, como `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Número de mods activos

**Identificador:** `loadedmods`

Cuántos mods están cargados. También cuenta las bibliotecas y los mods incluidos dentro de otros mods, así que normalmente el resultado es mayor que la cantidad de archivos de mods.

```
{"placeholder":"loadedmods"}
```

### Número total de mods

**Identificador:** `totalmods`

Un cálculo aproximado de los mods instalados, basado en los archivos `.jar` de la carpeta `mods` que se realiza una vez al iniciar el juego. Nunca es menor que **Número de mods activos**.

```
{"placeholder":"totalmods"}
```

### Progreso de carga del mundo

**Identificador:** `world_load_progress`

El progreso de carga de un mundo, de `0` a `100`, mientras se muestra la pantalla de carga. Es útil para las barras de carga. Devuelve `0` en todas las demás pantallas.

```
{"placeholder":"world_load_progress"}
```

### Valor de opción de Minecraft

**Identificador:** `minecraft_option_value`

El valor de una opción de Minecraft, tal como se guarda en el archivo `options.txt` de la carpeta del juego; por ejemplo, `12` para `renderDistance`. Devuelve un texto vacío si no existe una opción con ese nombre.

- `name`: el nombre de la opción en `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Tecla asignada

**Identificador:** `keybind_key`

La tecla que tiene asignada una acción en ese momento, como aparece en la pantalla de Controles: `Space` para saltar. Devuelve un texto vacío si no existe una asignación con ese nombre.

- `keybind`: el nombre de la asignación, como `key.jump` o `key.inventory`. Los nombres están en `options.txt` sin `key_` al principio: `key_key.jump` es `key.jump`.

```
Presiona {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} para abrir tu inventario.
```

### Último mundo o servidor

**Identificador:** `last_world_server`

El último mundo o servidor al que se unió el jugador. Los servidores aparecen como `play.example.net:25565`.

- `type`: `both` para mundos y servidores, `world` solo para mundos o `server` solo para servidores. Si se usa `world` o `server`, devuelve un texto vacío cuando el último destino era del otro tipo.
- `full_world_path` (opcional): `false` devuelve solo el nombre del mundo, como `Nuevo mundo`. `true` devuelve la ruta de su carpeta. De manera predeterminada, es `true`.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## Interfaz gráfica

Estos marcadores muestran información de la pantalla abierta y sus elementos. Los marcadores de elementos requieren el ID del elemento: haz clic derecho en el editor de diseños y selecciona **Copiar ID del elemento**.

### Ancho de pantalla

**Identificador:** `guiwidth`

El ancho de la pantalla en píxeles de la interfaz gráfica. Corresponde al tamaño que usan los elementos, no a los píxeles de tu monitor.

```
{"placeholder":"guiwidth"}
```

### Alto de pantalla

**Identificador:** `guiheight`

El alto de la pantalla en píxeles de la interfaz gráfica.

```
{"placeholder":"guiheight"}
```

### Escala de la interfaz gráfica

**Identificador:** `guiscale`

La escala de la interfaz gráfica del juego, como `2`.

```
{"placeholder":"guiscale"}
```

### Identificador de la pantalla actual

**Identificador:** `screenid`

El [identificador](/screen-identifiers) de la pantalla abierta, como `title_screen`. Devuelve un texto vacío si no hay ninguna pantalla abierta.

```
{"placeholder":"screenid"}
```

### Ancho del elemento

**Identificador:** `elementwidth`

El ancho de un elemento en píxeles de la interfaz gráfica. Devuelve `1` si no existe un elemento con ese ID.

- `id`: el ID del elemento

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Alto del elemento

**Identificador:** `elementheight`

El alto de un elemento en píxeles de la interfaz gráfica. Devuelve `1` si no existe un elemento con ese ID.

- `id`: el ID del elemento

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posición X del elemento

**Identificador:** `elementposx`

La posición del borde izquierdo de un elemento en píxeles de la interfaz gráfica, medida desde el lado izquierdo de la pantalla. Devuelve `1` si no existe un elemento con ese ID.

- `id`: el ID del elemento

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posición Y del elemento

**Identificador:** `elementposy`

La posición del borde superior de un elemento en píxeles de la interfaz gráfica, medida desde la parte superior de la pantalla. Devuelve `1` si no existe un elemento con ese ID.

- `id`: el ID del elemento

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Alto del contenido de un elemento de texto

**Identificador:** `text_element_content_height`

El alto que necesita un [elemento de texto](/text-in-menus) para mostrar todo su texto sin desplazarse, en píxeles de la interfaz gráfica. Cuenta las líneas ajustadas, la escala del texto y el espaciado entre líneas, así que es útil para crear fondos que se adapten al texto. Devuelve `0` si el elemento no es un elemento de texto.

- `element_identifier`: el ID del elemento de texto

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posición de desplazamiento del elemento

**Identificador:** `scroll_area_scroll_position`

Cuánto se ha desplazado el contenido de un [área desplazable](/scrollable-areas) o de un elemento de texto, en píxeles de la interfaz gráfica desde el inicio. Devuelve `0` para los demás elementos.

- `element_identifier`: el ID del elemento
- `axis`: `vertical` u `horizontal`. Cualquier otro valor indica la dirección en la que se desplaza el elemento.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Porcentaje de desplazamiento del elemento

**Identificador:** `scroll_area_scroll_percent`

Cuánto se ha desplazado el contenido de un área desplazable o de un elemento de texto, de `0` (inicio) a `100` (final). Devuelve `0` para los demás elementos y cuando no hay nada que desplazar.

- `element_identifier`: el ID del elemento
- `axis`: `vertical` u `horizontal`. Cualquier otro valor indica la dirección en la que se desplaza el elemento.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Tamaño del contenido desplazable del elemento

**Identificador:** `scroll_area_content_size`

El tamaño del contenido de un área desplazable o de un elemento de texto: su alto para `vertical` o su ancho para `horizontal`. Devuelve `0` para los demás elementos.

- `element_identifier`: el ID del elemento
- `axis`: `vertical` u `horizontal`. Cualquier otro valor indica la dirección en la que se desplaza el elemento.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Valor del campo de entrada de texto

**Identificador:** `text_input_field_value`

El texto escrito en un [campo de entrada de texto](/elements#text-input-field) o en un campo de texto de la pantalla original. Devuelve un texto vacío si el elemento no es un campo de texto.

- `element_identifier`: el ID del elemento

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Etiqueta o texto de widget de Minecraft

**Identificador:** `vanillabuttonlabel`

La etiqueta de un botón u otro widget de la pantalla original, como `Options...`. Haz clic derecho en el widget en el editor de diseños y selecciona **Copiar identificador del widget** para obtener su identificador.

- `locator`: el identificador del widget

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Posición X del mouse

**Identificador:** `mouseposx`

La posición del mouse en píxeles de la interfaz gráfica, medida desde el lado izquierdo de la pantalla. En el editor de diseños siempre es `10`, para que los elementos que siguen al mouse se mantengan en una posición que puedas editar.

```
{"placeholder":"mouseposx"}
```

### Posición Y del mouse

**Identificador:** `mouseposy`

La posición del mouse en píxeles de la interfaz gráfica, medida desde la parte superior de la pantalla. En el editor de diseños siempre es `10`.

```
{"placeholder":"mouseposy"}
```

### Clics por segundo

**Identificador:** `clicks_per_second`

Cuántas veces se hizo clic con un botón del mouse durante el último segundo.

- `mouse_button` (opcional): `left` o `right`. De manera predeterminada, es `left`.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Jugador

### Nombre del jugador

**Identificador:** `playername`

El nombre del jugador, como `Steve`.

```
{"placeholder":"playername"}
```

### UUID del jugador

**Identificador:** `playeruuid`

El UUID del jugador, como `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Último mensaje de muerte

**Identificador:** `lastdeathmessage`

El último mensaje de muerte del jugador desde que se inició el juego, como `Steve fue asesinado por un zombi`. Devuelve un texto vacío antes de la primera muerte.

- `as_json_component` (opcional): `true` devuelve el mensaje como un componente de texto JSON, con sus colores. De manera predeterminada, es `false`.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Hora actual

Estos marcadores muestran la hora de tu computadora. Los de fecha y hora aceptan el valor opcional `timezone`: `system` para la zona horaria de la computadora (el valor predeterminado) o un ID como `UTC`, `Europe/Berlin` o `America/New_York`. Consulta [nodatime.org/TimeZones](https://nodatime.org/TimeZones) para ver todos los ID.

### Año actual

**Identificador:** `realtimeyear`

El año, como `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Mes actual

**Identificador:** `realtimemonth`

El mes, de `01` a `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Día actual

**Identificador:** `realtimeday`

El día del mes, de `01` a `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Hora actual

**Identificador:** `realtimehour`

La hora, de `00` a `23`.

- `twelve_hour_format` (opcional): `true` devuelve valores de `01` a `12`. De manera predeterminada, es `false`.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Minuto actual

**Identificador:** `realtimeminute`

El minuto, de `00` a `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Segundo actual

**Identificador:** `realtimesecond`

El segundo, de `00` a `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Hora actual en milisegundos (marca de tiempo Unix)

**Identificador:** `unix_time`

Los milisegundos transcurridos desde el 1 de enero de 1970 (UTC), como `1732456789012`. Es útil para crear temporizadores: guarda el valor en una variable y réstalo de un valor posterior con la Calculadora.

```
{"placeholder":"unix_time"}
```

## Servidor

Estos marcadores consultan el estado de un servidor, como la lista de servidores. FancyMenu consulta el estado cada 30 segundos mientras hay una pantalla personalizada abierta. Hasta que llega la primera respuesta, el servidor se considera desconectado.

- `ip`: la dirección del servidor, con el puerto si no es el predeterminado; por ejemplo, `play.example.net` o `play.example.net:25566`

### Estado del servidor

**Identificador:** `serverstatus`

Devuelve `Online` en verde o `Offline` en rojo.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Número de jugadores del servidor

**Identificador:** `serverplayercount`

La cantidad de jugadores conectados y el máximo, como `12/100`. Devuelve `0/0` hasta que el servidor responde.

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### MOTD del servidor

**Identificador:** `servermotd`

Una línea del mensaje del día del servidor.

- `line`: `1` o `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Ping del servidor

**Identificador:** `serverping`

El ping al servidor en milisegundos, como `54`. Devuelve `-1` mientras el servidor está desconectado.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Versión del servidor

**Identificador:** `serverversion`

La versión de Minecraft del servidor, como `1.21.1`. Algunos servidores muestran aquí un texto propio. Devuelve `---` hasta que el servidor responde.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Video

Estos marcadores leen los [elementos de video y los fondos de menú de video](/video) del menú abierto. Para los elementos de video, haz clic derecho en uno en el editor de diseños y selecciona **Copiar ID del elemento**. Para los fondos, haz clic derecho en el fondo del editor y selecciona **Copiar identificador del fondo**.

### Volumen del elemento de video

**Identificador:** `video_element_vol`

El volumen de un elemento de video, de `0.0` (0 %) a `1.0` (100 %).

- `element_identifier`: el ID del elemento de video

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Duración del elemento de video

**Identificador:** `video_element_duration`

La duración del video de un elemento de video, como `02:00`. Devuelve `00:00` (o `0`) mientras se carga.

- `element_identifier`: el ID del elemento de video
- `output_as_timestamp` (opcional): `true` devuelve milisegundos, como `120000`. De manera predeterminada, es `false`.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Tiempo de reproducción del elemento de video

**Identificador:** `video_element_playtime`

El avance del video de un elemento de video, como `00:45`. Devuelve `00:00` (o `0`) mientras se carga.

- `element_identifier`: el ID del elemento de video
- `show_percentage` (opcional): `true` devuelve el avance de `0` a `100`. De manera predeterminada, es `false`.
- `output_as_timestamp` (opcional): `true` devuelve milisegundos. Si ambos valores son `true`, tiene prioridad `show_percentage`. De manera predeterminada, es `false`.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Estado de pausa del elemento de video

**Identificador:** `video_element_paused_state`

Devuelve `true` mientras un elemento de video está en pausa y `false` en cualquier otro caso.

- `element_identifier`: el ID del elemento de video

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Volumen del fondo de video

**Identificador:** `video_background_vol`

El volumen de un fondo de menú de video, de `0.0` (0 %) a `1.0` (100 %).

- `background_identifier`: el identificador del fondo del menú

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Duración del fondo de video

**Identificador:** `video_background_duration`

La duración del video de un fondo de menú, como `03:00`. Devuelve `00:00` (o `0`) mientras se carga.

- `background_identifier`: el identificador del fondo del menú
- `output_as_timestamp` (opcional): `true` devuelve milisegundos. De manera predeterminada, es `false`.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Tiempo de reproducción del fondo de video

**Identificador:** `video_background_playtime`

El avance del video de un fondo de menú, como `01:00`. Devuelve `00:00` (o `0`) mientras se carga.

- `background_identifier`: el identificador del fondo del menú
- `show_percentage` (opcional): `true` devuelve el avance de `0` a `100`. De manera predeterminada, es `false`.
- `output_as_timestamp` (opcional): `true` devuelve milisegundos. Si ambos valores son `true`, tiene prioridad `show_percentage`. De manera predeterminada, es `false`.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Estado de pausa del fondo de video

**Identificador:** `video_background_paused_state`

Devuelve `true` mientras un fondo de menú de video está en pausa y `false` en cualquier otro caso.

- `background_identifier`: el identificador del fondo del menú

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## Mundo: estadísticas del jugador

La categoría **Mundo** muestra información del mundo en el que juegas. La mayoría de sus marcadores necesitan que haya un mundo cargado. Si no hay uno, devuelven `0`, `0.0` o nada.

### Salud actual del jugador

**Identificador:** `current_player_health`

La salud del jugador, como `20.0`. Cada corazón equivale a `2.0`.

```
{"placeholder":"current_player_health"}
```

### Salud máxima del jugador

**Identificador:** `max_player_health`

La salud máxima del jugador, como `20.0`.

```
{"placeholder":"max_player_health"}
```

### Salud actual del jugador (porcentaje)

**Identificador:** `current_player_health_percent`

La salud del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Salud de absorción actual del jugador

**Identificador:** `current_player_absorption_health`

La salud de absorción del jugador (los corazones dorados), como `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Salud de absorción máxima del jugador

**Identificador:** `max_player_absorption_health`

La salud de absorción máxima del jugador, como `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Salud de absorción actual del jugador (porcentaje)

**Identificador:** `current_player_absorption_health_percent`

La salud de absorción del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Nivel de alimento actual del jugador

**Identificador:** `current_player_hunger`

El nivel de alimento del jugador, de `0.0` a `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Nivel de alimento máximo del jugador

**Identificador:** `max_player_hunger`

El nivel de alimento máximo de los jugadores: siempre es `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Nivel de alimento actual del jugador (porcentaje)

**Identificador:** `current_player_hunger_percent`

El nivel de alimento del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Saturación de hambre actual del jugador

**Identificador:** `current_player_hunger_saturation`

La saturación del jugador, como `5.0`. El nivel de alimento no baja hasta que se agota la saturación.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Armadura actual del jugador

**Identificador:** `current_player_armor`

Los puntos de armadura del jugador, de `0.0` a `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Armadura máxima del jugador

**Identificador:** `max_player_armor`

Los puntos máximos de armadura de la barra: siempre son `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Armadura actual del jugador (porcentaje)

**Identificador:** `current_player_armor_percent`

Los puntos de armadura del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Dureza de armadura del jugador

**Identificador:** `player_armor_toughness`

La dureza de armadura del jugador, como `8.0` con una armadura de diamante completa.

```
{"placeholder":"player_armor_toughness"}
```

### Nivel de oxígeno actual del jugador

**Identificador:** `current_player_oxygen`

El aire del jugador bajo el agua, de `0.0` a `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Nivel de oxígeno máximo del jugador

**Identificador:** `max_player_oxygen`

El aire máximo del jugador, como `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Nivel de oxígeno actual del jugador (porcentaje)

**Identificador:** `current_player_oxygen_percent`

El aire del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Nivel actual del jugador

**Identificador:** `current_player_level`

El nivel de experiencia del jugador, como `30`.

```
{"placeholder":"current_player_level"}
```

### Experiencia actual del jugador

**Identificador:** `current_player_exp`

Los puntos de experiencia totales del jugador, como `1395.0`. No es el nivel.

```
{"placeholder":"current_player_exp"}
```

### Progreso de experiencia del jugador (porcentaje)

**Identificador:** `current_player_exp_progress`

Qué tan llena está la barra de experiencia, de `0` a `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Fuerza de ataque del jugador (porcentaje)

**Identificador:** `player_attack_strength`

Qué tan cargado está el siguiente ataque, de `0` a `100`, como el indicador de ataque.

```
{"placeholder":"player_attack_strength"}
```

### Modo de juego del jugador

**Identificador:** `player_gamemode`

`survival`, `creative`, `adventure` o `spectator`.

```
{"placeholder":"player_gamemode"}
```

### Progreso de uso de objeto del jugador (FM)

**Identificador:** `player_item_use_progress_fm`

Qué tanto ha avanzado el jugador al usar un objeto, por ejemplo, al comer, beber o tensar un arco, de `0.0` a `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Salud actual de la montura

**Identificador:** `current_mount_health`

La salud de la criatura que monta el jugador, como un caballo; por ejemplo, `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Salud máxima de la montura

**Identificador:** `max_mount_health`

La salud máxima de la criatura que monta el jugador.

```
{"placeholder":"max_mount_health"}
```

### Salud actual de la montura (porcentaje)

**Identificador:** `current_mount_health_percent`

La salud de la criatura que monta el jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Indicador de salto actual de la montura (porcentaje)

**Identificador:** `current_mount_jump_meter`

Qué tanto está cargado el salto de un caballo, de `0` a `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Número de efectos activos

**Identificador:** `effects_count`

Cuántos efectos tiene el jugador en ese momento.

```
{"placeholder":"effects_count"}
```

### Efecto activo

**Identificador:** `active_effect`

El ID de un efecto del jugador, como `minecraft:speed`, en el orden de los iconos de efectos de la esquina superior derecha. Devuelve un texto vacío si no hay ningún efecto en ese índice.

- `effect_index`: la posición del efecto. El primero es `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## Mundo: inventario y objetos

Estos marcadores están en la categoría **Mundo**. Los números de ranura son: de `0` a `8` para la barra de acceso rápido, de `9` a `35` para el resto del inventario, de `36` a `39` para la armadura (de las botas al casco) y `40` para la mano secundaria.

### Ranura seleccionada de la barra de acceso rápido

**Identificador:** `active_hotbar_slot`

La ranura seleccionada de la barra de acceso rápido, de `0` a `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Objeto de la ranura

**Identificador:** `slot_item`

El ID del objeto en una ranura, como `minecraft:diamond_sword`. Las ranuras vacías devuelven `minecraft:air`.

- `slot`: el número de la ranura

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Cantidad de objetos de la ranura

**Identificador:** `slot_item_count`

Cuántos objetos hay en una ranura, como `64`.

- `slot`: el número de la ranura

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Durabilidad del objeto de la ranura

**Identificador:** `slot_item_durability`

La durabilidad del objeto en una ranura. Devuelve `0` para los objetos sin durabilidad.

- `slot`: el número de la ranura
- `format` (opcional): `current` (la durabilidad restante), `max`, `damage` (la durabilidad perdida) o `percentage` (la restante, de `0` a `100`). De manera predeterminada, es `current`.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Nombre mostrado del objeto de la ranura (FM)

**Identificador:** `slot_item_display_name_fm`

El nombre del objeto en una ranura como componente de texto JSON, con el color de su rareza; por ejemplo, `{"text":"Espada de diamante","color":"aqua"}`. En el modo espectador, las ranuras de la barra de acceso rápido muestran los nombres del menú de espectador.

- `slot`: el número de la ranura
- `ignore_spectator` (opcional): `true` también devuelve los nombres de los objetos en el modo espectador. De manera predeterminada, es `false`.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Cantidad de objetos en el inventario

**Identificador:** `inventory_item_count`

Cuántas unidades de un objeto tiene el jugador en todo su inventario.

- `item`: el ID del objeto, como `minecraft:diamond`. Si está vacío, cuenta todos los objetos.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Puntos de alimento que restaura el objeto de la ranura del inventario

**Identificador:** `inventory_slot_food_point_restore_amount`

Cuántos puntos de alimento restaura al comer el objeto de una ranura; por ejemplo, `4.0` para una manzana. Devuelve `0.0` para los objetos que no son comida.

- `slot`: el número de la ranura

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Categoría del objeto

**Identificador:** `item_category`

La pestaña del inventario del modo creativo a la que pertenece un objeto, como `Combat`. Devuelve `UNKNOWN` para los objetos que no tienen pestaña.

- `item`: el ID del objeto
- `as_key` (opcional): `true` devuelve el ID de la pestaña, como `minecraft:combat`. De manera predeterminada, es `false`.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Objeto del inventario bajo el cursor

**Identificador:** `hovered_inventory_item`

El ID del objeto sobre el que está el cursor en una pantalla de inventario, como `minecraft:apple`. Devuelve un texto vacío si no hay ninguno.

```
{"placeholder":"hovered_inventory_item"}
```

## Mundo: HUD y jefes

Estos marcadores están en la categoría **Mundo**. Los marcadores de incursión leen la incursión cuya barra aparece en la parte superior de la pantalla y requieren que FancyMenu esté instalado en el servidor. Siempre funcionan en un mundo de un jugador. Si no hay ninguna incursión, devuelven `0` o nada.

### Mensaje de la barra de acción (FM)

**Identificador:** `action_bar_message_fm`

El mensaje que aparece sobre la barra de acceso rápido, como componente de texto JSON; por ejemplo, `{"text":"No puedes descansar ahora","color":"red"}`. Devuelve un texto vacío si no hay ningún mensaje.

```
{"placeholder":"action_bar_message_fm"}
```

### Duración del mensaje de la barra de acción (FM)

**Identificador:** `action_bar_message_time_fm`

Cuántos ticks seguirá mostrándose el mensaje sobre la barra de acceso rápido. 20 ticks equivalen a un segundo.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Duración del objeto resaltado (FM)

**Identificador:** `highlighted_item_time_fm`

Cuántos ticks más se mostrará sobre la barra de acceso rápido el nombre del objeto seleccionado.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Título o subtítulo actual del HUD

**Identificador:** `current_title`

El título o subtítulo que se muestra en ese momento, como el de `/title`. Devuelve un texto vacío si no hay ninguno.

- `is_subtitle` (opcional): `true` devuelve el subtítulo. De manera predeterminada, es `false`.
- `as_json` (opcional): `true` lo devuelve como componente de texto JSON. De manera predeterminada, es `false`.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Número de jefes

**Identificador:** `boss_count`

Cuántas barras de jefe se muestran en ese momento.

```
{"placeholder":"boss_count"}
```

### Nombre del jefe

**Identificador:** `boss_name`

El nombre de una barra de jefe, como `Dragón del End`. Devuelve un texto vacío si no hay una barra de jefe en ese índice.

- `boss_index`: la posición de la barra de jefe. La que está arriba es `0`.
- `as_json` (opcional): `true` lo devuelve como componente de texto JSON. De manera predeterminada, es `false`.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Salud actual del jefe (porcentaje)

**Identificador:** `current_boss_health`

Qué tan llena está la barra de un jefe, de `0` a `100`.

- `boss_index`: la posición de la barra de jefe. La que está arriba es `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Total de oleadas de incursión activas

**Identificador:** `active_raid_total_waves`

Cuántas oleadas tiene la incursión, incluida la oleada adicional.

```
{"placeholder":"active_raid_total_waves"}
```

### Oleadas de incursión activas restantes

**Identificador:** `active_raid_remaining_waves`

Cuántas oleadas de la incursión faltan.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Oleada actual de la incursión activa

**Identificador:** `active_raid_current_wave`

El número de la oleada más reciente; por ejemplo, devuelve `1` mientras ataca la primera oleada. Devuelve `0` antes de la primera oleada.

```
Oleada {"placeholder":"active_raid_current_wave"} de {"placeholder":"active_raid_total_waves"}
```

### Número de saqueadores vivos de la incursión activa

**Identificador:** `active_raid_alive_raiders_count`

Cuántos saqueadores de la incursión siguen vivos.

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Lista de saqueadores vivos de la incursión activa

**Identificador:** `active_raid_alive_raiders_list`

Todos los saqueadores que siguen vivos, separados por comas. Cada entrada contiene el ID de la criatura y el UUID del saqueador, como `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`.

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## Mundo: posición y cámara

Estos marcadores están en la categoría **Mundo**.

### Coordenada X del jugador

**Identificador:** `player_x_coordinate`

La coordenada X del bloque en el que está el jugador, como `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Coordenada Y del jugador

**Identificador:** `player_y_coordinate`

La coordenada Y del bloque en el que está el jugador, como `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Coordenada Z del jugador

**Identificador:** `player_z_coordinate`

La coordenada Z del bloque en el que está el jugador, como `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Dirección de la vista del jugador

**Identificador:** `player_view_direction`

La dirección hacia la que mira el jugador: `north`, `east`, `south` o `west`.

```
{"placeholder":"player_view_direction"}
```

### Cambio en la posición X del jugador (FM)

**Identificador:** `player_position_delta_x_fm`

Cuánto se desplazó el jugador en el eje X desde el último tick, en bloques; por ejemplo, `0.12`. El valor es negativo si se mueve en la dirección opuesta.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Cambio en la posición Y del jugador (FM)

**Identificador:** `player_position_delta_y_fm`

Cuánto se desplazó el jugador en el eje Y desde el último tick; por ejemplo, `-0.08` al caer.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Cambio en la posición Z del jugador (FM)

**Identificador:** `player_position_delta_z_fm`

Cuánto se desplazó el jugador en el eje Z desde el último tick.

```
{"placeholder":"player_position_delta_z_fm"}
```

### Rotación X de la cámara (FM)

**Identificador:** `camera_rotation_x_fm`

Cuánto apunta la cámara hacia arriba o hacia abajo, en grados, de `-90.0` (directamente hacia arriba) a `90.0` (directamente hacia abajo).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Rotación Y de la cámara (FM)

**Identificador:** `camera_rotation_y_fm`

Hacia dónde apunta la cámara, en grados, de `-180.0` a `180.0`. `0.0` corresponde al sur.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Cambio en la rotación X de la cámara (FM)

**Identificador:** `camera_rotation_delta_x_fm`

Cuánto giró la cámara hacia arriba o hacia abajo desde el último tick, en grados.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Cambio en la rotación Y de la cámara (FM)

**Identificador:** `camera_rotation_delta_y_fm`

Cuánto giró la cámara hacia la izquierda o hacia la derecha desde el último tick, en grados.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## Mundo: información del mundo

Estos marcadores están en la categoría **Mundo**.

### Hora del día del mundo

**Identificador:** `world_daytime`

La hora del día del mundo en ticks. Un día tiene 24000 ticks y empieza a las 6:00 de la mañana. El contador sigue aumentando de un día a otro, así que `{"placeholder":"world_daytime"} % 24000` en una Calculadora devuelve la hora del día actual.

```
{"placeholder":"world_daytime"}
```

### Hora del día del mundo (horas)

**Identificador:** `world_daytime_hour`

La hora del día del mundo, de `00` a `23`.

- `twelve_hour_format` (opcional): `true` devuelve valores de `01` a `12`. De manera predeterminada, es `false`.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### Hora del día del mundo (minutos)

**Identificador:** `world_daytime_minute`

Los minutos de la hora del día del mundo, de `00` a `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### Tiempo de juego del mundo

**Identificador:** `game_time`

Cuántos ticks ha estado activo el mundo en total. A diferencia de la hora del día, los comandos como `/time set` no lo cambian.

```
{"placeholder":"game_time"}
```

### Dificultad del mundo

**Identificador:** `world_difficulty`

`peaceful`, `easy`, `normal` o `hard`.

```
{"placeholder":"world_difficulty"}
```

### Dimensión actual

**Identificador:** `current_dimension`

La dimensión en la que está el jugador, como `minecraft:overworld`.

- `as_key` (opcional): `false` devuelve su nombre, como `Overworld`. Las dimensiones sin nombre devuelven su ID. De manera predeterminada, es `true`.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Bioma actual

**Identificador:** `current_biome`

El bioma en el que está el jugador, como `minecraft:plains`.

- `as_key` (opcional): `false` devuelve su nombre, como `Plains`. De manera predeterminada, es `true`.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Semilla del mundo actual

**Identificador:** `current_world_seed`

La semilla del mundo de un jugador, como `-4172144997902289642`. Devuelve un texto vacío en los servidores.

```
{"placeholder":"current_world_seed"}
```

### Valor de regla del juego

**Identificador:** `gamerule_value`

El valor de una regla del juego, como `true` o `3`. Siempre funciona en un mundo de un jugador. En los servidores, requiere que FancyMenu esté instalado en el servidor. Devuelve un texto vacío si no existe una regla con ese nombre.

- `name`: el nombre de la regla del juego, como `keep_inventory`. En Minecraft 1.21.10 y versiones anteriores, las reglas tienen nombres como `keepInventory`; esos nombres antiguos también funcionan en versiones más recientes.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### IP del servidor actual

**Identificador:** `current_server_ip`

La dirección del servidor en el que está el jugador, como `play.example.net`. Devuelve un texto vacío en un mundo de un jugador.

```
{"placeholder":"current_server_ip"}
```

### Lista de jugadores del mundo

**Identificador:** `world_players_list`

Los nombres de los jugadores del mundo que conoce el juego, ordenados alfabéticamente; por ejemplo, `Alex, Notch, Steve`.

- `separator` (opcional): el texto que separa los nombres. De manera predeterminada, es `, `.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## Mundo: partidas guardadas

Estos marcadores están en la categoría **Mundo** y funcionan en cualquier menú, incluso si no hay un mundo cargado.

### Número de partidas guardadas

**Identificador:** `level_save_count`

Cuántos mundos de un jugador hay.

```
{"placeholder":"level_save_count"}
```

### Nombres de las partidas guardadas

**Identificador:** `level_save_names`

Los nombres de todos los mundos de un jugador, en el orden en que aparecen en la lista de mundos; por ejemplo, `Mundo de supervivencia, Prueba creativa`.

- `separator` (opcional): el texto que separa los nombres. De manera predeterminada, es `, `.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### Datos de una partida guardada

**Identificador:** `level_save_data`

Todos los datos de un mundo de un jugador como JSON; por ejemplo, `{"file_name":"Mundo de supervivencia","game_type":"survival","difficulty":"normal",...}`. Incluye `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (como marca de tiempo Unix), `minecraft_version_name` y más. Lee valores individuales con [**Analizador JSON**](#analizador-json).

- `level_name`: el nombre del mundo, exactamente como aparece en la lista de mundos

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Mundo de supervivencia"}}","json_path":"$.game_type"}}
```

## Otros

Estos marcadores no tienen categoría, así que aparecen debajo de las categorías en el menú de marcadores de posición.

### FPS (fotogramas por segundo)

**Identificador:** `fps`

Los fotogramas por segundo, como `120`.

```
{"placeholder":"fps"}
```

### RAM usada en MB

**Identificador:** `usedram`

La RAM que usa el juego en ese momento, en MB; por ejemplo, `4096`.

```
{"placeholder":"usedram"}
```

### RAM máxima en MB

**Identificador:** `maxram`

La cantidad máxima de RAM que puede usar el juego, en MB; por ejemplo, `8192`.

```
{"placeholder":"maxram"}
```

### RAM usada en %

**Identificador:** `percentram`

La RAM que usa el juego como porcentaje de la RAM máxima, por ejemplo, `50`.

```
{"placeholder":"percentram"}
```

### Uso de CPU (JVM)

**Identificador:** `jvmcpu`

Cuánto de la CPU usa el juego, en porcentaje; por ejemplo, `25.5`.

```
{"placeholder":"jvmcpu"}
```

### Uso de CPU (sistema operativo)

**Identificador:** `oscpu`

Cuánto de la CPU usa toda la computadora, en porcentaje; por ejemplo, `42.8`.

```
{"placeholder":"oscpu"}
```

### Información de la CPU

**Identificador:** `cpuinfo`

El nombre de la CPU, como `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### Información de la GPU

**Identificador:** `gpuinfo`

El nombre del dispositivo gráfico que usa el juego, como `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### Versión de OpenGL

**Identificador:** `glver`

La información del controlador del dispositivo gráfico que usa el juego, como `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Versión de Java

**Identificador:** `javaver`

La versión de Java con la que se ejecuta el juego, como `21.0.5`.

```
{"placeholder":"javaver"}
```

### Máquina virtual de Java

**Identificador:** `jvmname`

El nombre de la máquina virtual de Java, como `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Nombre del sistema operativo

**Identificador:** `osname`

El nombre del sistema operativo, como `Windows 11`.

```
{"placeholder":"osname"}
```

### Duración de la sesión

**Identificador:** `uptime_duration`

Cuánto tiempo lleva ejecutándose el juego, en segundos; por ejemplo, `742`.

- `output_as_millis` (opcional): `true` devuelve milisegundos. De manera predeterminada, es `false`.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Texto aleatorio

**Identificador:** `randomtext`

Una línea aleatoria de un archivo de texto, una URL o un texto que escribas, como un consejo aleatorio. Los archivos y las URL se vuelven a leer cada 30 segundos.

- `source`: un archivo `.txt` de la carpeta del juego, una URL o líneas separadas por `\n`, como `Consejo 1\nConsejo 2\nConsejo 3`
- `interval` (opcional): cada cuántos segundos se elige una línea nueva. El valor `0` elige una línea por sesión de juego. De manera predeterminada, es `10`.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Texto web

**Identificador:** `webtext`

La primera línea del texto de una página web, como un archivo de texto de tu sitio web. Se carga una vez y vuelve a cargarse cuando FancyMenu se actualiza. Devuelve un texto vacío mientras se carga.

- `link`: la URL de la página

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Ruta absoluta de archivo o carpeta

**Identificador:** `absolute_path`

La ruta completa de un archivo o una carpeta dentro de la carpeta del juego, como `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: la ruta dentro de la carpeta del juego

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Número de caracteres del texto

**Identificador:** `text_character_count`

Cuántos caracteres tiene un texto: `Hello World!` tiene `12`.

- `text`: el texto

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Ancho del texto

**Identificador:** `text_width`

Qué ancho tiene un texto en píxeles de la interfaz gráfica: `Hello World!` mide `57`. Los códigos de formato, como `&l`, se cuentan como en el juego, así que el texto en negritas ocupa más espacio.

- `text`: el texto

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Alto del texto

**Identificador:** `text_height`

Qué alto tiene un texto en píxeles de la interfaz gráfica, con todas sus líneas. Los saltos de línea se representan con `\n`. Para ajustar algo a un elemento de texto, usa [**Alto del contenido de un elemento de texto**](#alto-del-contenido-de-un-elemento-de-texto), que también cuenta la escala del texto, el espaciado entre líneas y las líneas ajustadas.

- `text`: el texto

```
{"placeholder":"text_height","values":{"text":"Primera línea\nSegunda línea"}}
```

### Contenido del portapapeles

**Identificador:** `clipboard_content`

El texto del portapapeles de tu computadora. Devuelve un texto vacío si no hay nada.

```
{"placeholder":"clipboard_content"}
```
