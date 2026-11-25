---
title: Marcadores de posición
description: >-
  Muestra valores en tiempo real, como el nombre del jugador, la hora o el
  número de jugadores de un servidor, en tus textos, y consulta todos los
  marcadores de posición de FancyMenu.
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# Marcadores de posición

Los marcadores de posición son códigos breves que FancyMenu sustituye por un valor en tiempo real, como el nombre del jugador, la hora o el número de jugadores de un servidor. Funcionan en los textos de los elementos, las etiquetas de los botones, la información emergente, los valores de las acciones y los requisitos, y en la mayoría de los demás textos que puedes escribir.

<img width="800" alt="Añadir el marcador de posición Nombre del jugador a un elemento de texto en el editor de diseños: marcadores de posición en el editor de texto, categoría Jugador y el texto saluda al jugador por su nombre" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> También puedes usar tus propias [variables](/variables) en esos mismos textos, con `$$` seguido del nombre, como `$$coins`.

# Añadir marcadores de posición

1. Abre el texto en el editor de texto, por ejemplo, **Contenido del texto** de un [elemento de texto](/text-in-menus). Los campos de texto de las ventanas, como los valores de las acciones, tienen un botón **Abrir en el editor** al lado.
2. Haz clic donde quieras insertar el marcador de posición.
3. Haz clic en **Marcadores de posición**, en la esquina superior derecha del editor de texto.
4. Haz clic en una categoría o busca por nombre, identificador o descripción. **ATRÁS** vuelve a las categorías. Los marcadores de posición sin categoría aparecen debajo de estas.
5. Pasa el ratón por encima de un marcador de posición para ver qué hace y haz clic en él para añadirlo.
6. Sustituye los valores de ejemplo, como el ID del mod en **Versión del mod**.

Los textos cuyo editor no tiene el botón **Marcadores de posición** no admiten marcadores de posición.

# Cómo funcionan los marcadores de posición

Un marcador de posición tiene este aspecto:

```
{"placeholder":"playername"}
```

Los marcadores de posición que tienen opciones las incluyen en `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- El identificador, como `playername`, distingue entre mayúsculas y minúsculas. A continuación se indican el identificador y los valores de cada marcador de posición.
- El orden de los valores no importa. Puedes omitir los valores opcionales.
- Si FancyMenu no puede sustituir un marcador de posición, por ejemplo, si contiene un error tipográfico, este se mantiene en el texto tal y como lo has escrito.
- Los marcadores de posición siempre devuelven texto. Si no hay nada que mostrar, devuelven un valor alternativo, como `0`, `0.0`, `---` o nada.
- Los [códigos de formato](/text-formatting) funcionan con los marcadores de posición: `&6{"placeholder":"playername"}` muestra el nombre en dorado.

> [!IMPORTANT]
> Los marcadores de posición parecen JSON, pero no lo son. No los proceses con un formateador ni un validador JSON, ya que los marcadores de posición dentro de otros marcadores de posición no forman JSON válido.

## Marcadores de posición dentro de otros marcadores

Los valores pueden contener otros marcadores de posición y [variables](/variables#showing-variables-in-text). FancyMenu sustituye primero los que están dentro de otros. No hace falta escapar las comillas de los valores.

Esto convierte la RAM máxima de MB a GB:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

Esto muestra la variable `rank` en mayúsculas:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

Cuando un marcador de posición devuelve texto que contiene otros marcadores, como un archivo leído con [**Texto de archivo**](#file-text), FancyMenu también los sustituye.

# Información útil

- Los marcadores de posición se actualizan automáticamente. FancyMenu conserva el texto sustituido durante 30 milisegundos antes de volver a sustituir sus marcadores. Puedes cambiarlo con **Duración de la caché de marcadores de posición [MS]** en **barra de menú -> Personalización -> Ajustes**. El valor `0` los sustituye en cada fotograma, lo que consume más recursos.
- Los marcadores que leen sitios web, archivos o servidores, como **Texto web** o **Estado del servidor**, se cargan en segundo plano. Hasta que terminan de cargarse, no devuelven nada o muestran un valor alternativo.
- En las [acciones](/action-scripts), los marcadores de posición obtienen su valor actual justo cuando se ejecuta la acción.
- Los marcadores de posición relativos al mundo, la pantalla y los elementos solo funcionan en el hilo principal del juego. En un [Ticker](/elements#ticker) que se ejecuta en segundo plano (de forma asíncrona), FancyMenu muestra un error en su lugar.
- **Número aleatorio** genera un número nuevo cada vez que se actualiza el texto. Para conservarlo, guárdalo en una [variable](/variables) con [**Establecer valor de variable (FM Variable)**](/action-scripts#set-variable-value-fm-variable).

> [!CAUTION]
> Algunos marcadores, como **Analizador JSON**, **Texto de archivo** y **Contenido del portapapeles**, pueden leer archivos de la carpeta del juego y el portapapeles. Si se combinan con acciones que contactan con sitios web, un diseño podría enviar esos datos a terceros. Utiliza únicamente diseños de confianza.

# Ejemplos

## Panel de bienvenida

<img width="800" alt="Un elemento de texto saluda al jugador por su nombre y muestra la versión de Minecraft, el número de mods y la hora" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### Welcome back, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"} with {"placeholder":"loadedmods"} mods
It's {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Estado del servidor y jugadores

```
Survival: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}} players
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

Estos son todos los marcadores de posición de FancyMenu. Aquí, las amplias categorías **Avanzado** y **Mundo** del menú de marcadores se dividen en grupos más pequeños.

## Variables y listas

Están en la categoría **Avanzado**. Consulta [Variables](/variables) para saber cómo crear variables y listas.

### Obtener valor de variable (FM Variable)

**Identificador:** `getvariable`

El valor de una de tus variables. Devuelve `0` si la variable está vacía o no existe, lo que resulta útil para los números. Una lista devuelve todas sus entradas como una matriz JSON, por ejemplo, `["Steve","Alex"]`.

- `name`: nombre de la variable, sin `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Obtener entrada de lista (FM Variable)

**Identificador:** `list_get`

Una entrada de una variable de lista.

- `name`: nombre de la lista
- `index`: posición de la entrada. La primera es `0`; los números negativos cuentan desde el final, así que `-1` es la última entrada.
- `fallback` (opcional): valor que se devuelve si no hay ninguna entrada en ese índice o no existe una lista con ese nombre. De forma predeterminada, está vacío.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### Tamaño de lista (FM Variable)

**Identificador:** `list_size`

Número de entradas de una lista. Devuelve `0` si no existe ninguna lista con ese nombre.

- `name`: nombre de la lista

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Índice de entrada de lista (FM Variable)

**Identificador:** `list_index_of`

El índice de la primera entrada que coincide con todo el `value`, o `-1` si la lista no la contiene.

- `name`: nombre de la lista
- `value`: entrada que se va a buscar
- `ignore_case` (opcional): `true` hace que `Apple` coincida con `apple`. De forma predeterminada, es `false`.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Unir entradas de lista (FM Variable)

**Identificador:** `list_join`

Todas las entradas de una lista en un solo texto. Devuelve un texto vacío si no existe ninguna lista con ese nombre.

- `name`: nombre de la lista
- `separator` (opcional): texto que separa las entradas. `\n` representa un salto de línea. De forma predeterminada, es `, `.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Matemáticas

Están en la categoría **Avanzado**. Los números utilizan un punto para los decimales, como `2.5`.

### Calculadora

**Identificador:** `calc`

Resuelve una expresión matemática, como `2 + 3 * 4`.

- `expression`: operación que se va a resolver
- `decimal` (opcional): `false` redondea el resultado a un número entero. De forma predeterminada, es `true` y devuelve resultados como `14.0`.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| En expresiones | Función |
|---|---|
| `+` `-` `*` `/` | Sumar, restar, multiplicar y dividir |
| `^` | Potencia, como `2 ^ 3` para obtener 8 |
| `%` | Resto, como `7 % 3` para obtener 1 |
| `( )` | Agrupar partes, como `(2 + 3) * 4` |
| `pi`, `e` | Los números π y e |
| `abs(x)` | Valor absoluto de un número |
| `sqrt(x)`, `cbrt(x)` | Raíz cuadrada y raíz cúbica |
| `pow(x, y)` | x elevado a y |
| `floor(x)`, `ceil(x)` | Redondear hacia abajo y hacia arriba |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Trigonometría, con los ángulos en radianes |
| `asin(x)`, `acos(x)`, `atan(x)` | Trigonometría inversa |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Funciones hiperbólicas |
| `log(x)`, `log2(x)`, `log10(x)` | Logaritmos en base e, 2 y 10 |
| `exp(x)` | e elevado a x |
| `signum(x)` | `1`, `-1` o `0`, como [**Signo (matemáticas)**](#sign-math) |

### Número aleatorio

**Identificador:** `random_number`

Un número entero aleatorio entre `min` y `max`. Cambia cada vez que se actualiza el texto.

- `min`, `max`: el número más bajo y el más alto

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

El número sin el signo menos: `-10.5` devuelve `10.5`.

- `num`: el número

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Cambiar el signo de un número

**Identificador:** `negnum`

Convierte un número positivo en negativo: `10.5` devuelve `-10.5`. El cero y los números negativos no cambian.

- `num`: el número

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Redondear (matemáticas)

**Identificador:** `math_round`

Redondea un número. `2.5` se redondea a `3`.

- `num`: el número
- `decimals` (opcional): número de decimales que se conservan; por ejemplo, `2` convierte `3.14159` en `3.14`. Si es `0`, `-1` o se omite, se redondea a un número entero.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Redondear hacia abajo (matemáticas)

**Identificador:** `math_floor`

Redondea un número hacia abajo a un entero: `3.7` devuelve `3` y `-3.2` devuelve `-4`.

- `num`: el número

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Redondear hacia arriba (matemáticas)

**Identificador:** `math_ceil`

Redondea un número hacia arriba a un entero: `3.2` devuelve `4` y `-3.7` devuelve `-3`.

- `num`: el número

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Signo (matemáticas)

**Identificador:** `math_sign`

Devuelve `1` para los números positivos, `-1` para los negativos y `0` para el cero.

- `num`: el número

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (matemáticas)

**Identificador:** `math_pi`

El número π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Seno trigonométrico (matemáticas)

**Identificador:** `math_sin`

El seno de un ángulo en radianes. Para usar grados, primero multiplícalos por π / 180 con la Calculadora.

- `angle`: el ángulo en radianes

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Coseno trigonométrico (matemáticas)

**Identificador:** `math_cos`

El coseno de un ángulo en radianes.

- `angle`: el ángulo en radianes

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Tangente trigonométrica (matemáticas)

**Identificador:** `math_tan`

La tangente de un ángulo en radianes.

- `angle`: el ángulo en radianes

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Seno hiperbólico (matemáticas)

**Identificador:** `math_sinh`

El seno hiperbólico de un número.

- `num`: el número

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Coseno hiperbólico (matemáticas)

**Identificador:** `math_cosh`

El coseno hiperbólico de un número.

- `num`: el número

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Tangente hiperbólica (matemáticas)

**Identificador:** `math_tanh`

La tangente hiperbólica de un número.

- `num`: el número

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Convertidor de bases numéricas

**Identificador:** `number_base_convert`

Convierte un número a otra base, por ejemplo, de decimal a binario o hexadecimal. También admite decimales, con hasta 16 cifras después del punto. Las letras del resultado van en mayúsculas, como `FF`.

- `input`: el número
- `from_base` (opcional): la base de `input`, de `2` a `36`. De forma predeterminada, es `10`.
- `to_base` (opcional): la base del resultado, de `2` a `36`. De forma predeterminada, es `10`.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Texto

Están en la categoría **Avanzado**.

### Texto en mayúsculas

**Identificador:** `uppercase_text`

Convierte el texto a mayúsculas: `Hello World` devuelve `HELLO WORLD`. Los [códigos de formato](/text-formatting), como `&a`, se mantienen igual.

- `text`: el texto

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Texto en minúsculas

**Identificador:** `lowercase_text`

Convierte el texto a minúsculas: `HELLO WORLD` devuelve `hello world`. Los códigos de formato se mantienen igual.

- `text`: el texto

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Texto en formato de título

**Identificador:** `title_case_text`

Pone en mayúscula la primera letra de cada palabra: `hello world` devuelve `Hello World`. Los códigos de formato se mantienen igual.

- `text`: el texto

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Texto en formato de oración

**Identificador:** `sentence_case_text`

Pone en mayúscula la primera letra de cada oración: `hello world. this is fancymenu!` devuelve `Hello world. This is fancymenu!`. Los códigos de formato se mantienen igual.

- `text`: el texto

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Texto en formato snake_case

**Identificador:** `snake_case_text`

Pone el texto en minúsculas y separa las palabras con `_`: `Hello World` devuelve `hello_world`. Se eliminan los códigos de formato.

- `text`: el texto

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Texto en formato kebab-case

**Identificador:** `kebab_case_text`

Pone el texto en minúsculas y separa las palabras con `-`: `Hello World` devuelve `hello-world`. Se eliminan los códigos de formato.

- `text`: el texto

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Texto con mayúsculas alternas

**Identificador:** `alternating_case_text`

Alterna las letras minúsculas y mayúsculas: `alternating case` devuelve `aLtErNaTiNg CaSe`.

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

### Quitar espacios sobrantes

**Identificador:** `trim_text`

Elimina los espacios del principio y el final del texto. Los espacios interiores se mantienen.

- `text`: el texto

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Recortar texto

**Identificador:** `crop_text`

Elimina un número de caracteres del principio y del final del texto. Si se elimina un carácter de cada extremo de `hello world`, se obtiene `ello worl`.

- `text`: el texto
- `remove_from_start`: número de caracteres que se eliminan del principio
- `remove_from_end`: número de caracteres que se eliminan del final

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Dividir texto

**Identificador:** `split_text`

Divide un texto y devuelve una de sus partes. Si se divide `Steve,Alex,Notch` por `,`, la parte `1` es `Alex`.

- `input`: el texto
- `regex`: expresión regular que indica dónde dividir. Algunos caracteres, como `.`, `|` y `?`, necesitan una `\` delante, por ejemplo, `\.`.
- `max_parts` (opcional): número máximo de partes en las que se divide el texto. El valor predeterminado, `-1`, lo divide en cada coincidencia.
- `split_index`: parte que se devuelve. La primera es `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Reemplazar texto

**Identificador:** `replace_text`

Sustituye partes de un texto: si en `Hello World!` se reemplaza `World` por `FancyMenu`, se obtiene `Hello FancyMenu!`.

- `text`: el texto
- `search`: texto que se va a buscar
- `replacement` (opcional): texto que lo sustituye. De forma predeterminada, está vacío y elimina lo que se encuentra.
- `use_regex` (opcional): `true` convierte `search` en una expresión regular. En ese caso, `$1`, `$2` y así sucesivamente en `replacement` representan los grupos encontrados. De forma predeterminada, es `false`.
- `replace_all` (opcional): `false` sustituye solo la primera coincidencia. De forma predeterminada, es `true`.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Seleccionar caso

**Identificador:** `switch_case`

Devuelve el resultado del caso que coincide con un valor. Si la variable `difficulty_level` vale `2`, el ejemplo devuelve `Hard Mode`.

- `value`: valor que se va a comprobar
- `cases`: pares de valor y resultado, como `1:Easy Mode,2:Hard Mode`. Los valores y resultados no pueden contener `,` ni `:`.
- `default` (opcional): resultado que se devuelve si no coincide ningún caso. Si se omite, el marcador de posición se mantiene tal cual.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localizar texto

**Identificador:** `local`

El texto de una clave de localización en el idioma actual del juego; por ejemplo, `Singleplayer` para `menu.singleplayer`. Funciona con las claves de Minecraft, las de los mods y las tuyas (consulta [Localización](/localization)).

- `key`: clave de localización

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Convertir en cadena segura

**Identificador:** `stringify`

Sustituye los marcadores de posición del texto y, después, añade una `\` delante de cada `"`, `{` y `}`. Así, el texto externo —por ejemplo, el de un sitio web— no puede convertirse en marcadores de posición.

- `text`: el texto

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Datos y archivos

Están en la categoría **Avanzado**. Las rutas locales parten de la carpeta del juego, por ejemplo, `/config/fancymenu/assets/news.txt`, y no pueden salir de ella (consulta [Recursos](/resources#local-resources)).

### Analizador JSON

**Identificador:** `json`

Lee un valor de JSON. Si hay varios resultados, muestra uno por línea.

- `source`: texto JSON, un archivo JSON de la carpeta del juego o la URL de un archivo JSON
- `json_path`: ruta al valor, como `$.name` o `$.players[0].name`. Consulta [json.fancymenu.net](https://json.fancymenu.net) para obtener más información sobre las rutas JSON.

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

El contenido JSON de la web se carga una vez y vuelve a cargarse cuando FancyMenu se reinicia. Los cambios en los archivos aparecen de inmediato.

| Ruta | Valor devuelto |
|---|---|
| `$.name` | El valor de `name` en el nivel superior |
| `$.player.level` | El valor de `level` dentro de `player` |
| `$.items[0].id` | El valor de `id` de la primera entrada de `items` |
| `$.scores.*` | Todos los valores de `scores` |

### Texto de archivo

**Identificador:** `file_text`

El texto de un archivo o una URL. Los archivos se vuelven a leer cada segundo y las URL, cada 10 segundos. No devuelve nada mientras carga el texto o si no se puede leer.

- `path_or_url`: archivo de la carpeta del juego o URL. Las rutas que empiezan por `.minecraft/` apuntan a la carpeta predeterminada de Minecraft.
- `mode` (opcional): `all` para mostrar todo el texto o `last` para mostrar las últimas líneas. De forma predeterminada, es `all`.
- `separator` (opcional): texto entre líneas. De forma predeterminada, es `\n` (un salto de línea).
- `last_lines` (opcional): número de líneas que devuelve `last`. De forma predeterminada, es `1`.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### Tamaño de archivo

**Identificador:** `file_size`

Tamaño de un archivo en bytes. Devuelve `0` si el archivo no existe. Las rutas que empiezan por `.minecraft/` apuntan a la carpeta predeterminada de Minecraft.

- `path`: archivo

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### MD5 de archivo

**Identificador:** `file_md5`

Hash MD5 de un archivo, como `d41d8cd98f00b204e9800998ecf8427e`. Si el archivo no existe, devuelve un texto vacío. Las rutas que empiezan por `.minecraft/` apuntan a la carpeta predeterminada de Minecraft.

- `path`: archivo

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Codificar en Base64

**Identificador:** `base64_encode`

Convierte el texto a Base64: `Hello World` devuelve `SGVsbG8gV29ybGQ=`.

- `text`: el texto

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decodificar de Base64

**Identificador:** `base64_decode`

Convierte un texto Base64 a texto normal: `SGVsbG8gV29ybGQ=` devuelve `Hello World`.

- `text`: el texto en Base64

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Obtener datos NBT (lado del cliente)

**Identificador:** `nbt_data_get`

Lee datos NBT, como `/data get`, de la información que tiene el juego sobre el mundo. Es rápido, pero los servidores no envían todos los datos a los jugadores.

- `source_type`: `entity` o `block`
- `entity_selector`: para `entity`, un selector como `@s` (tú), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]`, o el nombre o UUID de una entidad. Los selectores pueden incluir `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` y `dz`. Se utiliza la primera coincidencia.
- `block_pos`: para `block`, posición de una entidad de bloque, como un cofre: `120 64 -35`
- `nbt_path`: ruta NBT, como `foodLevel` o `Inventory[0].id`
- `scale` (opcional): multiplica los números. De forma predeterminada, es `1.0`.
- `return_type` (opcional): `value` (números y texto tal cual), `string`, `snbt` o `json`. De forma predeterminada, es `value`.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Obtener datos NBT (lado del servidor)

**Identificador:** `nbt_data_get_server`

Lee datos NBT del servidor, exactamente como `/data get`. Requiere FancyMenu en el servidor. En el modo para un jugador, siempre funciona. No devuelve nada hasta que responde el servidor y, después, se actualiza aproximadamente cada 100 milisegundos.

- `source_type`: `entity`, `block` o `storage`
- `entity_selector`: para `entity`, cualquier selector de `/data get` que encuentre una entidad, como `@s` o `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: para `block`, una posición como `120 64 -35`, `~ ~-1 ~` o `^ ^ ^1`
- `storage_id`: para `storage`, ID de un almacenamiento de comandos, como `mypack:quests`
- `nbt_path` (opcional): ruta NBT. Si se omite, se devuelven todos los datos.
- `scale` (opcional): multiplica los números. De forma predeterminada, es `1.0`.
- `return_type` (opcional): `value`, `string`, `snbt` o `json`. De forma predeterminada, es `value`.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Audio

Estos marcadores leen los [elementos de audio](/elements#audio) del menú abierto. Haz clic derecho en un elemento de audio en el editor de diseños y selecciona **Copiar ID del elemento** para obtener su ID.

### Volumen del elemento de audio

**Identificador:** `audio_element_vol`

Volumen del elemento de audio, de `0.0` (0 %) a `1.0` (100 %).

- `element_identifier`: ID del elemento de audio

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Pista de audio actual

**Identificador:** `audio_element_current_track`

Nombre del archivo de la pista que se está reproduciendo, como `menu_theme.ogg`. Si no se está reproduciendo ninguna pista, devuelve `---`.

- `element_identifier`: ID del elemento de audio
- `display_name_mappings` (opcional): nombres que se muestran en lugar de los nombres de archivo. `=>` separa el nombre de archivo y el nombre mostrado, y `%:%` separa los pares.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Duración del audio

**Identificador:** `audio_duration`

Duración de la pista actual, como `03:45`. Mientras se carga, devuelve `00:00`.

- `element_identifier`: ID del elemento de audio

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Tiempo de reproducción del audio

**Identificador:** `audio_playtime`

Posición actual de la pista, como `01:30`. Si está detenida, devuelve `00:00` (o `0`).

- `element_identifier`: ID del elemento de audio
- `show_percentage` (opcional): `true` devuelve el progreso de `0` a `100`. De forma predeterminada, es `false`.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Estado de reproducción del audio

**Identificador:** `audio_playing_state`

Devuelve `true` mientras se reproduce el elemento de audio y `false` si está en pausa o detenido.

- `element_identifier`: ID del elemento de audio

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Cliente

Estos marcadores hacen referencia al juego y sus mods.

### Versión de Minecraft

**Identificador:** `mcversion`

Versión de Minecraft, como `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Nombre del cargador de mods

**Identificador:** `loadername`

Nombre del cargador de mods, como `Fabric` o `NeoForge`.

```
{"placeholder":"loadername"}
```

### Versión del cargador de mods

**Identificador:** `loaderver`

Versión del cargador de mods, como `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Versión del mod

**Identificador:** `modversion`

Versión de un mod instalado, como `3.11.0`. Si el mod no está instalado, devuelve `0.0.0`.

- `modid`: ID del mod, como `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Número de mods activos

**Identificador:** `loadedmods`

Número de mods cargados. También cuentan las bibliotecas y los mods incluidos dentro de otros, así que el resultado suele ser superior al número de archivos de mod.

```
{"placeholder":"loadedmods"}
```

### Número total de mods

**Identificador:** `totalmods`

Cálculo aproximado del número de mods instalados, a partir de los archivos `.jar` de la carpeta `mods` y una vez al iniciar cada partida. Nunca es inferior al **Número de mods activos**.

```
{"placeholder":"totalmods"}
```

### Progreso de carga del mundo

**Identificador:** `world_load_progress`

Progreso de carga de un mundo, de `0` a `100`, mientras se muestra la pantalla de carga. Es útil para las barras de carga. En las demás pantallas, devuelve `0`.

```
{"placeholder":"world_load_progress"}
```

### Valor de una opción de Minecraft

**Identificador:** `minecraft_option_value`

Valor de una opción de Minecraft tal y como se guarda en el archivo `options.txt` de la carpeta del juego; por ejemplo, `12` para `renderDistance`. Si no existe una opción con ese nombre, devuelve un texto vacío.

- `name`: nombre de la opción en `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Tecla asignada

**Identificador:** `keybind_key`

Tecla que tiene asignada una acción en ese momento, tal como aparece en la pantalla de controles: por ejemplo, `Space` para saltar. Si no existe una acción con ese nombre, devuelve un texto vacío.

- `keybind`: nombre de la acción, como `key.jump` o `key.inventory`. Los nombres están en `options.txt`, sin el prefijo `key_`: `key_key.jump` se convierte en `key.jump`.

```
Press {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} to open your inventory!
```

### Último mundo o servidor

**Identificador:** `last_world_server`

Mundo o servidor al que se conectó el jugador por última vez. Los servidores se muestran como `play.example.net:25565`.

- `type`: `both` para mundos y servidores, `world` solo para mundos o `server` solo para servidores. Con `world` o `server`, devuelve un texto vacío si el último destino era del otro tipo.
- `full_world_path` (opcional): `false` devuelve solo el nombre del mundo, como `New World`. `true` devuelve la ruta de su carpeta. De forma predeterminada, es `true`.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## Interfaz gráfica

Estos marcadores hacen referencia a la pantalla abierta y sus elementos. Los marcadores de elementos necesitan el ID de un elemento: haz clic derecho sobre él en el editor de diseños y selecciona **Copiar ID del elemento**.

### Ancho de pantalla

**Identificador:** `guiwidth`

Ancho de la pantalla en píxeles de la interfaz gráfica. Corresponde al tamaño que utilizan los elementos, no a los píxeles del monitor.

```
{"placeholder":"guiwidth"}
```

### Alto de pantalla

**Identificador:** `guiheight`

Alto de la pantalla en píxeles de la interfaz gráfica.

```
{"placeholder":"guiheight"}
```

### Escala de la interfaz gráfica

**Identificador:** `guiscale`

Escala de la interfaz gráfica del juego, como `2`.

```
{"placeholder":"guiscale"}
```

### Identificador de la pantalla actual

**Identificador:** `screenid`

[Identificador](/screen-identifiers) de la pantalla abierta, como `title_screen`. Si no hay ninguna pantalla abierta, devuelve un texto vacío.

```
{"placeholder":"screenid"}
```

### Ancho del elemento

**Identificador:** `elementwidth`

Ancho de un elemento en píxeles de la interfaz gráfica. Si no existe ningún elemento con ese ID, devuelve `1`.

- `id`: ID del elemento

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Alto del elemento

**Identificador:** `elementheight`

Alto de un elemento en píxeles de la interfaz gráfica. Si no existe ningún elemento con ese ID, devuelve `1`.

- `id`: ID del elemento

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posición X del elemento

**Identificador:** `elementposx`

Posición del borde izquierdo de un elemento, en píxeles de la interfaz gráfica desde el borde izquierdo de la pantalla. Si no existe ningún elemento con ese ID, devuelve `1`.

- `id`: ID del elemento

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posición Y del elemento

**Identificador:** `elementposy`

Posición del borde superior de un elemento, en píxeles de la interfaz gráfica desde el borde superior de la pantalla. Si no existe ningún elemento con ese ID, devuelve `1`.

- `id`: ID del elemento

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Alto del contenido de un elemento de texto

**Identificador:** `text_element_content_height`

Altura que necesita un [elemento de texto](/text-in-menus) para mostrar todo el texto sin desplazarse, en píxeles de la interfaz gráfica. Tiene en cuenta las líneas ajustadas, la escala del texto y el espaciado entre líneas, por lo que resulta útil para crear fondos que se adapten al texto. Si el elemento no es de texto, devuelve `0`.

- `element_identifier`: ID del elemento de texto

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posición de desplazamiento del elemento

**Identificador:** `scroll_area_scroll_position`

Desplazamiento del contenido de un [área desplazable](/scrollable-areas) o un elemento de texto, en píxeles de la interfaz gráfica desde el inicio. Para los demás elementos, devuelve `0`.

- `element_identifier`: ID del elemento
- `axis`: `vertical` u `horizontal`. Cualquier otro valor indica la dirección en la que se desplaza el elemento.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Porcentaje de desplazamiento del elemento

**Identificador:** `scroll_area_scroll_percent`

Desplazamiento del contenido de un área desplazable o un elemento de texto, de `0` (inicio) a `100` (final). Para los demás elementos y cuando no hay nada que desplazar, devuelve `0`.

- `element_identifier`: ID del elemento
- `axis`: `vertical` u `horizontal`. Cualquier otro valor indica la dirección en la que se desplaza el elemento.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Tamaño del contenido desplazable del elemento

**Identificador:** `scroll_area_content_size`

Tamaño del contenido de un área desplazable o un elemento de texto: su altura para `vertical` y su anchura para `horizontal`. Para los demás elementos, devuelve `0`.

- `element_identifier`: ID del elemento
- `axis`: `vertical` u `horizontal`. Cualquier otro valor indica la dirección en la que se desplaza el elemento.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Valor del campo de entrada de texto

**Identificador:** `text_input_field_value`

Texto introducido en un [campo de entrada de texto](/elements#text-input-field) o en un campo de texto de la pantalla original. Si el elemento no es un campo de texto, devuelve un texto vacío.

- `element_identifier`: ID del elemento

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Etiqueta o texto de un widget de Minecraft

**Identificador:** `vanillabuttonlabel`

Etiqueta de un botón u otro widget de la pantalla original, como `Options...`. Haz clic derecho en el widget en el editor de diseños y selecciona **Copiar localizador del widget** para obtener su localizador.

- `locator`: localizador del widget

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Posición X del ratón

**Identificador:** `mouseposx`

Posición del ratón en píxeles de la interfaz gráfica desde el borde izquierdo de la pantalla. En el editor de diseños siempre es `10`, para que los elementos que siguen al ratón permanezcan en una posición que puedas editar.

```
{"placeholder":"mouseposx"}
```

### Posición Y del ratón

**Identificador:** `mouseposy`

Posición del ratón en píxeles de la interfaz gráfica desde el borde superior de la pantalla. En el editor de diseños siempre es `10`.

```
{"placeholder":"mouseposy"}
```

### Clics por segundo

**Identificador:** `clicks_per_second`

Número de veces que se ha hecho clic con un botón del ratón durante el último segundo.

- `mouse_button` (opcional): `left` o `right`. De forma predeterminada, es `left`.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Jugador

### Nombre del jugador

**Identificador:** `playername`

Nombre del jugador, como `Steve`.

```
{"placeholder":"playername"}
```

### UUID del jugador

**Identificador:** `playeruuid`

UUID del jugador, como `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Último mensaje de muerte

**Identificador:** `lastdeathmessage`

Último mensaje de muerte del jugador desde que se inició el juego, como `Steve was slain by Zombie`. Antes de la primera muerte, está vacío.

- `as_json_component` (opcional): `true` lo devuelve como componente de texto JSON, con sus colores. De forma predeterminada, es `false`.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Hora actual

Estos marcadores hacen referencia a la hora de tu ordenador. Los de fecha y hora tienen un valor opcional `timezone`: `system` para la zona horaria del ordenador (valor predeterminado) o un ID como `UTC`, `Europe/Berlin` o `America/New_York`. Consulta [nodatime.org/TimeZones](https://nodatime.org/TimeZones) para ver todos los ID.

### Año actual

**Identificador:** `realtimeyear`

Año actual, como `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Mes actual

**Identificador:** `realtimemonth`

Mes actual, de `01` a `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Día actual

**Identificador:** `realtimeday`

Día del mes, de `01` a `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Hora actual

**Identificador:** `realtimehour`

Hora actual, de `00` a `23`.

- `twelve_hour_format` (opcional): `true` devuelve un valor de `01` a `12`. De forma predeterminada, es `false`.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Minuto actual

**Identificador:** `realtimeminute`

Minuto actual, de `00` a `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Segundo actual

**Identificador:** `realtimesecond`

Segundo actual, de `00` a `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Hora actual en milisegundos (marca de tiempo Unix)

**Identificador:** `unix_time`

Milisegundos transcurridos desde el 1 de enero de 1970 (UTC), como `1732456789012`. Es útil para crear temporizadores: guarda el valor en una variable y réstalo de otro valor posterior con la Calculadora.

```
{"placeholder":"unix_time"}
```

## Servidor

Estos marcadores consultan el estado de un servidor, como en la lista de servidores. FancyMenu lo consulta cada 30 segundos mientras hay una pantalla personalizada abierta. Hasta que recibe la primera respuesta, el servidor se considera desconectado.

- `ip`: dirección del servidor, con el puerto si no es el predeterminado; por ejemplo, `play.example.net` o `play.example.net:25566`

### Estado del servidor

**Identificador:** `serverstatus`

Devuelve `Online` en verde o `Offline` en rojo.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Número de jugadores del servidor

**Identificador:** `serverplayercount`

Número de jugadores conectados y número máximo de jugadores, como `12/100`. Hasta que el servidor responde, devuelve `0/0`.

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

Ping al servidor en milisegundos, como `54`. Si está desconectado, devuelve `-1`.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Versión del servidor

**Identificador:** `serverversion`

Versión de Minecraft del servidor, como `1.21.1`. Algunos servidores muestran aquí un texto propio. Hasta que el servidor responde, devuelve `---`.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Vídeo

Estos marcadores leen los [elementos de vídeo y los fondos de menú de vídeo](/video) del menú abierto. Para los elementos de vídeo, haz clic derecho en uno en el editor de diseños y selecciona **Copiar ID del elemento**. Para los fondos, haz clic derecho en el fondo del editor y selecciona **Copiar identificador del fondo**.

### Volumen del elemento de vídeo

**Identificador:** `video_element_vol`

Volumen de un elemento de vídeo, de `0.0` (0 %) a `1.0` (100 %).

- `element_identifier`: ID del elemento de vídeo

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Duración del elemento de vídeo

**Identificador:** `video_element_duration`

Duración del vídeo de un elemento de vídeo, como `02:00`. Mientras se carga, devuelve `00:00` (o `0`).

- `element_identifier`: ID del elemento de vídeo
- `output_as_timestamp` (opcional): `true` devuelve milisegundos, como `120000`. De forma predeterminada, es `false`.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Tiempo de reproducción del elemento de vídeo

**Identificador:** `video_element_playtime`

Posición actual del vídeo de un elemento de vídeo, como `00:45`. Mientras se carga, devuelve `00:00` (o `0`).

- `element_identifier`: ID del elemento de vídeo
- `show_percentage` (opcional): `true` devuelve el progreso de `0` a `100`. De forma predeterminada, es `false`.
- `output_as_timestamp` (opcional): `true` devuelve milisegundos. Si ambos valores son `true`, prevalece `show_percentage`. De forma predeterminada, es `false`.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Estado de pausa del elemento de vídeo

**Identificador:** `video_element_paused_state`

Devuelve `true` mientras el elemento de vídeo está en pausa y `false` en cualquier otro caso.

- `element_identifier`: ID del elemento de vídeo

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Volumen del fondo de vídeo

**Identificador:** `video_background_vol`

Volumen de un fondo de vídeo del menú, de `0.0` (0 %) a `1.0` (100 %).

- `background_identifier`: identificador del fondo del menú

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Duración del fondo de vídeo

**Identificador:** `video_background_duration`

Duración del vídeo de un fondo de menú, como `03:00`. Mientras se carga, devuelve `00:00` (o `0`).

- `background_identifier`: identificador del fondo del menú
- `output_as_timestamp` (opcional): `true` devuelve milisegundos. De forma predeterminada, es `false`.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Tiempo de reproducción del fondo de vídeo

**Identificador:** `video_background_playtime`

Posición actual del vídeo de un fondo de menú, como `01:00`. Mientras se carga, devuelve `00:00` (o `0`).

- `background_identifier`: identificador del fondo del menú
- `show_percentage` (opcional): `true` devuelve el progreso de `0` a `100`. De forma predeterminada, es `false`.
- `output_as_timestamp` (opcional): `true` devuelve milisegundos. Si ambos valores son `true`, prevalece `show_percentage`. De forma predeterminada, es `false`.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Estado de pausa del fondo de vídeo

**Identificador:** `video_background_paused_state`

Devuelve `true` mientras el fondo de vídeo del menú está en pausa y `false` en cualquier otro caso.

- `background_identifier`: identificador del fondo del menú

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## Mundo: estadísticas del jugador

La categoría **Mundo** hace referencia al mundo en el que juegas. La mayoría de estos marcadores necesitan que haya un mundo cargado. Si no lo hay, devuelven `0`, `0.0` o nada.

### Salud actual del jugador

**Identificador:** `current_player_health`

Salud del jugador, como `20.0`. Cada corazón equivale a `2.0`.

```
{"placeholder":"current_player_health"}
```

### Salud máxima del jugador

**Identificador:** `max_player_health`

Salud máxima del jugador, como `20.0`.

```
{"placeholder":"max_player_health"}
```

### Salud actual del jugador (porcentaje)

**Identificador:** `current_player_health_percent`

Salud del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Salud de absorción actual del jugador

**Identificador:** `current_player_absorption_health`

Salud de absorción del jugador (los corazones dorados), como `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Salud de absorción máxima del jugador

**Identificador:** `max_player_absorption_health`

Salud de absorción máxima del jugador, como `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Salud de absorción actual del jugador (porcentaje)

**Identificador:** `current_player_absorption_health_percent`

Salud de absorción del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Nivel de comida actual del jugador

**Identificador:** `current_player_hunger`

Nivel de comida del jugador, de `0.0` a `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Nivel de comida máximo del jugador

**Identificador:** `max_player_hunger`

Nivel de comida máximo de los jugadores: siempre es `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Nivel de comida actual del jugador (porcentaje)

**Identificador:** `current_player_hunger_percent`

Nivel de comida del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Saturación actual del jugador

**Identificador:** `current_player_hunger_saturation`

Saturación del jugador, como `5.0`. La comida no disminuye hasta que se agota.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Armadura actual del jugador

**Identificador:** `current_player_armor`

Puntos de armadura del jugador, de `0.0` a `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Armadura máxima del jugador

**Identificador:** `max_player_armor`

Puntos de armadura máximos de la barra de armadura: siempre son `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Armadura actual del jugador (porcentaje)

**Identificador:** `current_player_armor_percent`

Puntos de armadura del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Dureza de armadura del jugador

**Identificador:** `player_armor_toughness`

Dureza de armadura del jugador, como `8.0` con una armadura de diamante completa.

```
{"placeholder":"player_armor_toughness"}
```

### Nivel de oxígeno actual del jugador

**Identificador:** `current_player_oxygen`

Aire del jugador bajo el agua, de `0.0` a `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Nivel de oxígeno máximo del jugador

**Identificador:** `max_player_oxygen`

Aire máximo del jugador, como `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Nivel de oxígeno actual del jugador (porcentaje)

**Identificador:** `current_player_oxygen_percent`

Aire del jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Nivel actual del jugador

**Identificador:** `current_player_level`

Nivel de experiencia del jugador, como `30`.

```
{"placeholder":"current_player_level"}
```

### Experiencia actual del jugador

**Identificador:** `current_player_exp`

Puntos de experiencia totales del jugador, como `1395.0`. No es el nivel.

```
{"placeholder":"current_player_exp"}
```

### Progreso de experiencia del jugador (porcentaje)

**Identificador:** `current_player_exp_progress`

Porcentaje de llenado de la barra de experiencia, de `0` a `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Fuerza de ataque del jugador (porcentaje)

**Identificador:** `player_attack_strength`

Carga del siguiente ataque, de `0` a `100`, como en el indicador de ataque.

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

Progreso del uso de un objeto por parte del jugador —por ejemplo, comer, beber o tensar un arco—, de `0.0` a `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Salud actual de la montura

**Identificador:** `current_mount_health`

Salud de la criatura que monta el jugador, como un caballo; por ejemplo, `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Salud máxima de la montura

**Identificador:** `max_mount_health`

Salud máxima de la criatura que monta el jugador.

```
{"placeholder":"max_mount_health"}
```

### Salud actual de la montura (porcentaje)

**Identificador:** `current_mount_health_percent`

Salud de la criatura que monta el jugador en porcentaje, de `0` a `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Indicador de salto actual de la montura (porcentaje)

**Identificador:** `current_mount_jump_meter`

Carga del salto de un caballo, de `0` a `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Número de efectos activos

**Identificador:** `effects_count`

Número de efectos que tiene el jugador en ese momento.

```
{"placeholder":"effects_count"}
```

### Efecto activo

**Identificador:** `active_effect`

ID de un efecto del jugador, como `minecraft:speed`, en el orden de los iconos de efecto de la parte superior derecha. Si no hay ningún efecto en ese índice, devuelve un texto vacío.

- `effect_index`: posición del efecto. El primero es `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## Mundo: inventario y objetos

Están en la categoría **Mundo**. Números de las ranuras: de `0` a `8` para la barra de acceso rápido, de `9` a `35` para el resto del inventario, de `36` a `39` para la armadura (de las botas al casco) y `40` para la mano secundaria.

### Ranura seleccionada de la barra de acceso rápido

**Identificador:** `active_hotbar_slot`

Ranura seleccionada de la barra de acceso rápido, de `0` a `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Objeto de una ranura

**Identificador:** `slot_item`

ID del objeto que hay en una ranura, como `minecraft:diamond_sword`. Las ranuras vacías devuelven `minecraft:air`.

- `slot`: número de la ranura

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Cantidad de objetos de una ranura

**Identificador:** `slot_item_count`

Cantidad de objetos que hay en una ranura, como `64`.

- `slot`: número de la ranura

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Durabilidad del objeto de una ranura

**Identificador:** `slot_item_durability`

Durabilidad del objeto de una ranura. Devuelve `0` para los objetos sin durabilidad.

- `slot`: número de la ranura
- `format` (opcional): `current` (durabilidad restante), `max`, `damage` (durabilidad perdida) o `percentage` (restante, de `0` a `100`). De forma predeterminada, es `current`.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Nombre visible del objeto de una ranura (FM)

**Identificador:** `slot_item_display_name_fm`

Nombre del objeto de una ranura como componente de texto JSON, con el color de su rareza; por ejemplo, `{"text":"Diamond Sword","color":"aqua"}`. En el modo espectador, las ranuras de la barra de acceso rápido muestran los nombres del menú de espectador.

- `slot`: número de la ranura
- `ignore_spectator` (opcional): `true` muestra también los nombres de los objetos en el modo espectador. De forma predeterminada, es `false`.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Cantidad de un objeto en el inventario

**Identificador:** `inventory_item_count`

Cantidad de un objeto que tiene el jugador en todo el inventario.

- `item`: ID del objeto, como `minecraft:diamond`. Si está vacío, cuenta todos los objetos.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Puntos de comida que restaura un objeto de una ranura

**Identificador:** `inventory_slot_food_point_restore_amount`

Puntos de comida que aporta al comerlo el objeto de una ranura; por ejemplo, `4.0` para una manzana. Devuelve `0.0` para los objetos que no son comida.

- `slot`: número de la ranura

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Categoría del objeto

**Identificador:** `item_category`

Pestaña del inventario creativo a la que pertenece un objeto, como `Combat`. Devuelve `UNKNOWN` para los objetos que no tienen pestaña.

- `item`: ID del objeto
- `as_key` (opcional): `true` devuelve el ID de la pestaña, como `minecraft:combat`. De forma predeterminada, es `false`.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Objeto del inventario bajo el cursor

**Identificador:** `hovered_inventory_item`

ID del objeto sobre el que está el ratón en una pantalla de inventario, como `minecraft:apple`. Si no hay ninguno, devuelve un texto vacío.

```
{"placeholder":"hovered_inventory_item"}
```

## Mundo: HUD y jefes

Están en la categoría **Mundo**. Los marcadores de incursión leen la incursión cuya barra aparece en la parte superior de la pantalla y necesitan FancyMenu en el servidor. En el modo para un jugador, siempre funcionan. Si no hay ninguna incursión, devuelven `0` o nada.

### Mensaje de la barra de acción (FM)

**Identificador:** `action_bar_message_fm`

Mensaje que aparece sobre la barra de acceso rápido, como componente de texto JSON; por ejemplo, `{"text":"You may not rest now","color":"red"}`. Si no hay ninguno, devuelve un texto vacío.

```
{"placeholder":"action_bar_message_fm"}
```

### Duración del mensaje de la barra de acción (FM)

**Identificador:** `action_bar_message_time_fm`

Número de ticks que seguirá apareciendo el mensaje sobre la barra de acceso rápido. 20 ticks equivalen a un segundo.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Duración del nombre del objeto seleccionado (FM)

**Identificador:** `highlighted_item_time_fm`

Número de ticks que seguirá apareciendo sobre la barra de acceso rápido el nombre del objeto seleccionado.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Título o subtítulo actual del HUD

**Identificador:** `current_title`

Título o subtítulo que se muestra en ese momento, por ejemplo, mediante `/title`. Si no hay ninguno, devuelve un texto vacío.

- `is_subtitle` (opcional): `true` devuelve el subtítulo. De forma predeterminada, es `false`.
- `as_json` (opcional): `true` lo devuelve como componente de texto JSON. De forma predeterminada, es `false`.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Número de barras de jefe

**Identificador:** `boss_count`

Número de barras de jefe que aparecen en ese momento.

```
{"placeholder":"boss_count"}
```

### Nombre del jefe

**Identificador:** `boss_name`

Nombre de una barra de jefe, como `Ender Dragon`. Si no hay ninguna barra de jefe en ese índice, devuelve un texto vacío.

- `boss_index`: posición de la barra de jefe. La de más arriba es `0`.
- `as_json` (opcional): `true` lo devuelve como componente de texto JSON. De forma predeterminada, es `false`.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Salud actual del jefe (porcentaje)

**Identificador:** `current_boss_health`

Porcentaje de llenado de una barra de jefe, de `0` a `100`.

- `boss_index`: posición de la barra de jefe. La de más arriba es `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Número total de oleadas de la incursión activa

**Identificador:** `active_raid_total_waves`

Número de oleadas de la incursión, incluida la oleada adicional.

```
{"placeholder":"active_raid_total_waves"}
```

### Oleadas restantes de la incursión activa

**Identificador:** `active_raid_remaining_waves`

Número de oleadas de la incursión que aún quedan por llegar.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Oleada actual de la incursión activa

**Identificador:** `active_raid_current_wave`

Número de la última oleada, así que devuelve `1` mientras ataca la primera. Antes de la primera oleada, devuelve `0`.

```
Wave {"placeholder":"active_raid_current_wave"} of {"placeholder":"active_raid_total_waves"}
```

### Número de saqueadores vivos de la incursión activa

**Identificador:** `active_raid_alive_raiders_count`

Número de saqueadores de la incursión que siguen vivos.

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

Están en la categoría **Mundo**.

### Coordenada X del jugador

**Identificador:** `player_x_coordinate`

Coordenada X del bloque en el que se encuentra el jugador, como `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Coordenada Y del jugador

**Identificador:** `player_y_coordinate`

Coordenada Y del bloque en el que se encuentra el jugador, como `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Coordenada Z del jugador

**Identificador:** `player_z_coordinate`

Coordenada Z del bloque en el que se encuentra el jugador, como `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Dirección de la mirada del jugador

**Identificador:** `player_view_direction`

Dirección en la que mira el jugador: `north`, `east`, `south` o `west`.

```
{"placeholder":"player_view_direction"}
```

### Diferencia de posición X del jugador (FM)

**Identificador:** `player_position_delta_x_fm`

Distancia que ha recorrido el jugador en el eje X desde el último tick, en bloques; por ejemplo, `0.12`. El valor es negativo si se mueve en la dirección opuesta.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Diferencia de posición Y del jugador (FM)

**Identificador:** `player_position_delta_y_fm`

Distancia que ha recorrido el jugador en el eje Y desde el último tick; por ejemplo, `-0.08` al caer.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Diferencia de posición Z del jugador (FM)

**Identificador:** `player_position_delta_z_fm`

Distancia que ha recorrido el jugador en el eje Z desde el último tick.

```
{"placeholder":"player_position_delta_z_fm"}
```

### Rotación X de la cámara (FM)

**Identificador:** `camera_rotation_x_fm`

Ángulo hacia arriba o abajo de la cámara, en grados, de `-90.0` (directamente hacia arriba) a `90.0` (directamente hacia abajo).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Rotación Y de la cámara (FM)

**Identificador:** `camera_rotation_y_fm`

Orientación de la cámara, en grados de `-180.0` a `180.0`. `0.0` corresponde al sur.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Diferencia de rotación X de la cámara (FM)

**Identificador:** `camera_rotation_delta_x_fm`

Ángulo que ha girado la cámara hacia arriba o abajo desde el último tick, en grados.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Diferencia de rotación Y de la cámara (FM)

**Identificador:** `camera_rotation_delta_y_fm`

Ángulo que ha girado la cámara a izquierda o derecha desde el último tick, en grados.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## Mundo: información del mundo

Están en la categoría **Mundo**.

### Hora del día en el mundo

**Identificador:** `world_daytime`

Hora del día del mundo en ticks. Un día tiene 24000 ticks y empieza a las 6:00 de la mañana. El contador sigue avanzando de un día a otro, así que `{"placeholder":"world_daytime"} % 24000` en la Calculadora devuelve la hora del día actual.

```
{"placeholder":"world_daytime"}
```

### Hora del día en el mundo (hora)

**Identificador:** `world_daytime_hour`

Hora del día del mundo, de `00` a `23`.

- `twelve_hour_format` (opcional): `true` devuelve un valor de `01` a `12`. De forma predeterminada, es `false`.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### Hora del día en el mundo (minutos)

**Identificador:** `world_daytime_minute`

Minuto de la hora del día del mundo, de `00` a `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### Tiempo de juego del mundo

**Identificador:** `game_time`

Número total de ticks que ha durado el mundo. A diferencia de la hora del día, los comandos como `/time set` no lo modifican.

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

Dimensión en la que está el jugador, como `minecraft:overworld`.

- `as_key` (opcional): `false` devuelve su nombre, como `Overworld`. Si la dimensión no tiene nombre, devuelve su ID. De forma predeterminada, es `true`.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Bioma actual

**Identificador:** `current_biome`

Bioma en el que está el jugador, como `minecraft:plains`.

- `as_key` (opcional): `false` devuelve su nombre, como `Plains`. De forma predeterminada, es `true`.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Semilla del mundo actual

**Identificador:** `current_world_seed`

Semilla del mundo para un jugador, como `-4172144997902289642`. En los servidores, devuelve un texto vacío.

```
{"placeholder":"current_world_seed"}
```

### Valor de una regla del juego

**Identificador:** `gamerule_value`

Valor de una regla del juego, como `true` o `3`. En el modo para un jugador, siempre funciona. En los servidores, requiere FancyMenu en el servidor. Si no existe una regla con ese nombre, devuelve un texto vacío.

- `name`: nombre de la regla del juego, como `keep_inventory`. En Minecraft 1.21.10 y versiones anteriores, las reglas tienen nombres como `keepInventory`; esos nombres antiguos también funcionan en las versiones más recientes.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### IP del servidor actual

**Identificador:** `current_server_ip`

Dirección del servidor en el que está el jugador, como `play.example.net`. En el modo para un jugador, devuelve un texto vacío.

```
{"placeholder":"current_server_ip"}
```

### Lista de jugadores del mundo

**Identificador:** `world_players_list`

Nombres de los jugadores del mundo que conoce el juego, ordenados alfabéticamente; por ejemplo, `Alex, Notch, Steve`.

- `separator` (opcional): texto que separa los nombres. De forma predeterminada, es `, `.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## Mundo: partidas guardadas

Están en la categoría **Mundo** y funcionan en cualquier menú, incluso si no hay ningún mundo cargado.

### Número de mundos guardados

**Identificador:** `level_save_count`

Número de mundos para un jugador.

```
{"placeholder":"level_save_count"}
```

### Nombres de los mundos guardados

**Identificador:** `level_save_names`

Nombres de todos los mundos para un jugador, en el orden en el que aparecen en la lista; por ejemplo, `Survival World, Creative Test`.

- `separator` (opcional): texto que separa los nombres. De forma predeterminada, es `, `.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### Datos de un mundo guardado

**Identificador:** `level_save_data`

Todos los datos de un mundo para un jugador en formato JSON, como `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`. Incluye `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (como marca de tiempo Unix), `minecraft_version_name` y otros datos. Lee valores concretos con [**Analizador JSON**](#json-parser).

- `level_name`: nombre del mundo, exactamente como aparece en la lista de mundos

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## Otros

No tienen categoría, así que el menú de marcadores de posición los muestra debajo de las categorías.

### FPS (fotogramas por segundo)

**Identificador:** `fps`

Fotogramas por segundo, como `120`.

```
{"placeholder":"fps"}
```

### RAM utilizada en MB

**Identificador:** `usedram`

RAM que utiliza el juego en ese momento, en MB; por ejemplo, `4096`.

```
{"placeholder":"usedram"}
```

### RAM máxima en MB

**Identificador:** `maxram`

Cantidad máxima de RAM que puede utilizar el juego, en MB; por ejemplo, `8192`.

```
{"placeholder":"maxram"}
```

### RAM utilizada en %

**Identificador:** `percentram`

Porcentaje de la RAM máxima que utiliza el juego, como `50`.

```
{"placeholder":"percentram"}
```

### Uso de CPU (JVM)

**Identificador:** `jvmcpu`

Porcentaje de CPU que utiliza el juego, como `25.5`.

```
{"placeholder":"jvmcpu"}
```

### Uso de CPU (sistema operativo)

**Identificador:** `oscpu`

Porcentaje de CPU que utiliza todo el ordenador, como `42.8`.

```
{"placeholder":"oscpu"}
```

### Información de la CPU

**Identificador:** `cpuinfo`

Nombre de la CPU, como `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### Información de la GPU

**Identificador:** `gpuinfo`

Nombre del dispositivo gráfico que utiliza el juego, como `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### Versión de OpenGL

**Identificador:** `glver`

Información del controlador del dispositivo gráfico que utiliza el juego, como `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Versión de Java

**Identificador:** `javaver`

Versión de Java con la que se ejecuta el juego, como `21.0.5`.

```
{"placeholder":"javaver"}
```

### Máquina virtual de Java

**Identificador:** `jvmname`

Nombre de la máquina virtual de Java, como `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Nombre del sistema operativo

**Identificador:** `osname`

Nombre del sistema operativo, como `Windows 11`.

```
{"placeholder":"osname"}
```

### Tiempo de actividad

**Identificador:** `uptime_duration`

Tiempo que lleva ejecutándose el juego, en segundos; por ejemplo, `742`.

- `output_as_millis` (opcional): `true` devuelve milisegundos. De forma predeterminada, es `false`.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Texto aleatorio

**Identificador:** `randomtext`

Línea aleatoria de un archivo de texto, una URL o un texto que escribas; por ejemplo, un consejo aleatorio. Los archivos y las URL se vuelven a leer cada 30 segundos.

- `source`: archivo `.txt` de la carpeta del juego, URL o líneas separadas por `\n`, como `Tip 1\nTip 2\nTip 3`
- `interval` (opcional): intervalo, en segundos, para elegir una línea nueva. El valor `0` elige una línea por sesión de juego. De forma predeterminada, es `10`.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Texto web

**Identificador:** `webtext`

Primera línea del texto de una página web, como un archivo de texto de tu sitio web. Se carga una vez y vuelve a cargarse cuando FancyMenu se reinicia. Mientras se carga, devuelve un texto vacío.

- `link`: URL de la página

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Ruta absoluta de archivo o carpeta

**Identificador:** `absolute_path`

Ruta completa de un archivo o una carpeta de la carpeta del juego, como `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: ruta dentro de la carpeta del juego

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Número de caracteres de un texto

**Identificador:** `text_character_count`

Número de caracteres de un texto: `Hello World!` tiene `12`.

- `text`: el texto

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Ancho del texto

**Identificador:** `text_width`

Anchura de un texto en píxeles de la interfaz gráfica: `Hello World!` mide `57`. Los códigos de formato, como `&l`, se tienen en cuenta igual que en el juego, así que el texto en negrita ocupa más.

- `text`: el texto

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Alto del texto

**Identificador:** `text_height`

Altura del texto en píxeles de la interfaz gráfica, con todas sus líneas. Los saltos de línea se indican con `\n`. Para ajustar un elemento a un texto, utiliza [**Alto del contenido de un elemento de texto**](#text-element-content-height), que también tiene en cuenta la escala, el espaciado entre líneas y el ajuste de línea del texto.

- `text`: el texto

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Contenido del portapapeles

**Identificador:** `clipboard_content`

Texto del portapapeles de tu ordenador. Si está vacío, devuelve un texto vacío.

```
{"placeholder":"clipboard_content"}
```
