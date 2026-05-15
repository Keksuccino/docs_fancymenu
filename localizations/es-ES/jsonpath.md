---
title: Rutas JSON
description: Cómo usar Jayway JsonPath en el marcador de posición del analizador JSON.
---

# Rutas JSON en FancyMenu

El marcador de posición **JSON Parser** de FancyMenu usa [Jayway JsonPath](https://github.com/json-path/JsonPath) para obtener contenido de archivos JSON.
Esta página explica las rutas JSON en detalle.

El texto de esta página es una copia del README del repositorio de GitHub de Jayway JsonPath.

> En este texto, el término "expresión JsonPath" se refiere a una ruta JSON.
{.is-info}

# JsonPath

Las expresiones JsonPath siempre hacen referencia a una estructura JSON del mismo modo que las expresiones XPath se usan junto con 
un documento XML. El "objeto miembro raíz" en JsonPath siempre se denomina `$`, independientemente de si es un 
objeto o un array.

Las expresiones JsonPath pueden usar la notación con punto

`$.store.book[0].title`

o la notación con corchetes

`$['store']['book'][0]['title']`

## Operadores

| Operator                  | Description                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | El elemento raíz que se consulta. Esto inicia todas las expresiones de ruta.       |
| `@`                       | El nodo actual que está siendo procesado por un predicado de filtro.            |
| `*`                       | Comodín. Disponible en cualquier lugar donde se requiera un nombre o un valor numérico.       |
| `..`                      | Búsqueda profunda. Disponible en cualquier lugar donde se requiera un nombre.                  |
| `.<name>`                 | Hijo con notación de punto                                                  |
| `['<name>' (, '<name>')]` | Hijo o hijos con notación de corchetes                                  |
| `[<number> (, <number>)]` | Índice o índices de array                                             |
| `[start:end]`             | Operador de fragmento de array                                               |
| `[?(<expression>)]`       | Expresión de filtro. La expresión debe evaluarse como un valor booleano.    |


## Funciones

Las funciones se pueden invocar al final de una ruta: la entrada de una función es la salida de la expresión de ruta.
La salida de la función viene determinada por la propia función.

| Function                  | Description                                                         | Output type |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Proporciona el valor mínimo de un array de números                       | Double      |
| max()                     | Proporciona el valor máximo de un array de números                       | Double      |
| avg()                     | Proporciona el valor medio de un array de números                   | Double      | 
| stddev()                  | Proporciona el valor de la desviación estándar de un array de números        | Double      | 
| length()                  | Proporciona la longitud de un array                                     | Integer     |
| sum()                     | Proporciona la suma de un array de números                       | Double      |
| keys()                    | Proporciona las claves de las propiedades (una alternativa al tilde terminal `~`)  | `Set<E>`    |
| concat(X)                 | Proporciona una versión concatenada de la salida de la ruta con un nuevo elemento  | like input  |
| append(X)                 | añade un elemento al array de salida de la ruta JSON                           | like input  |

## Operadores de filtro

Los filtros son expresiones lógicas que se usan para filtrar arrays. Un filtro típico sería `[?(@.age > 18)]`, donde `@` representa el elemento actual que se está procesando. Se pueden crear filtros más complejos con los operadores lógicos `&&` y `||`. Los literales de cadena deben ir entre comillas simples o dobles (`[?(@.color == 'blue')]` o `[?(@.color == "blue")]`).   

| Operator                 | Description                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | la parte izquierda es igual a la derecha (ten en cuenta que 1 no es igual a '1')              |
| !=                       | la parte izquierda no es igual a la derecha                                            |
| <                        | la parte izquierda es menor que la derecha                                               |
| <=                       | la parte izquierda es menor o igual que la derecha                                        |
| >                        | la parte izquierda es mayor que la derecha                                            |
| >=                       | la parte izquierda es mayor o igual que la derecha                                |
| =~                       | la parte izquierda coincide con la expresión regular  [?(@.name =~ /foo.*?/i)]             |
| in                       | la parte izquierda existe en la derecha [?(@.size in ['S', 'M'])]                        |
| nin                      | la parte izquierda no existe en la derecha                                         |
| subsetof                 | la parte izquierda es un subconjunto de la derecha [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | la parte izquierda tiene una intersección con la derecha [?(@.sizes anyof ['M', 'L'])]    |
| noneof                   | la parte izquierda no tiene intersección con la derecha [?(@.sizes noneof ['M', 'L'])]    |
| size                     | el tamaño de la parte izquierda (array o cadena) debe coincidir con la derecha                     |
| empty                    | la parte izquierda (array o cadena) debe estar vacía                                |


## Ejemplos de rutas

Dado el json

```javascript
{
    "store": {
        "book": [
            {
                "category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            },
            {
                "category": "fiction",
                "author": "Herman Melville",
                "title": "Moby Dick",
                "isbn": "0-553-21311-3",
                "price": 8.99
            },
            {
                "category": "fiction",
                "author": "J. R. R. Tolkien",
                "title": "The Lord of the Rings",
                "isbn": "0-395-19395-8",
                "price": 22.99
            }
        ],
        "bicycle": {
            "color": "red",
            "price": 19.95
        }
    },
    "expensive": 10
}
```

| JsonPath (click link to try)| Resultado |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Los autores de todos los libros     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Todos los autores                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Todo, tanto los libros como las bicicletas  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | El precio de todo         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | El tercer libro                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | El penúltimo libro            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Los dos primeros libros               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Todos los libros desde el índice 0 (incluido) hasta el índice 2 (excluido) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Todos los libros desde el índice 1 (incluido) hasta el índice 2 (excluido) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Los dos últimos libros                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | El libro número dos desde el final          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Todos los libros con número ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Todos los libros de la tienda más baratos que 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Todos los libros de la tienda que no son "caros"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Todos los libros que coinciden con la expresión regular (sin distinguir mayúsculas y minúsculas)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Dame todo   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | El número de libros                      |
