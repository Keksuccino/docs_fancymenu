---
title: Rutas JSON
description: Cómo usar Jayway JsonPath en el placeholder JSON Parser.
---

# Rutas JSON en FancyMenu

El placeholder **JSON Parser** de FancyMenu usa [Jayway JsonPath](https://github.com/json-path/JsonPath) para obtener contenido de archivos JSON.
Esta página explica las rutas JSON en detalle.

El texto de esta página es una copia del README del repositorio de GitHub de Jayway JsonPath.

> En este texto, el término "expresión JsonPath" se refiere a una ruta JSON.
{.is-info}

# JsonPath

Las expresiones JsonPath siempre hacen referencia a una estructura JSON de la misma manera en que las expresiones XPath se usan junto con 
un documento XML. El "objeto miembro raíz" en JsonPath siempre se обозначa como `$`, sin importar si es un 
objeto o un arreglo.

Las expresiones JsonPath pueden usar la notación de punto

`$.store.book[0].title`

o la notación de corchetes

`$['store']['book'][0]['title']`

## Operadores

| Operador                  | Descripción                                                       |
| :------------------------ | :---------------------------------------------------------------- |
| `$`                       | El elemento raíz a consultar. Esto inicia todas las expresiones de ruta. |
| `@`                       | El nodo actual que se está procesando por un predicado de filtro. |
| `*`                       | Comodín. Disponible en cualquier lugar donde se requiera un nombre o un número. |
| `..`                      | Búsqueda profunda. Disponible en cualquier lugar donde se requiera un nombre. |
| `.<name>`                 | Hijo con notación de punto                                         |
| `['<name>' (, '<name>')]` | Hijo o hijos con notación de corchetes                               |
| `[<number> (, <number>)]` | Índice o índices de arreglo                                         |
| `[start:end]`             | Operador de segmento de arreglo                                     |
| `[?(<expression>)]`       | Expresión de filtro. La expresión debe evaluar a un valor booleano. |


## Funciones

Las funciones se pueden invocar al final de una ruta; la entrada de una función es la salida de la expresión de ruta.
La salida de la función la determina la propia función.

| Función                  | Descripción                                                         | Tipo de salida |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Proporciona el valor mínimo de un arreglo de números                | Double      |
| max()                     | Proporciona el valor máximo de un arreglo de números                | Double      |
| avg()                     | Proporciona el valor promedio de un arreglo de números              | Double      | 
| stddev()                  | Proporciona el valor de la desviación estándar de un arreglo de números | Double   | 
| length()                  | Proporciona la longitud de un arreglo                                  | Integer     |
| sum()                     | Proporciona el valor de la suma de un arreglo de números            | Double      |
| keys()                    | Proporciona las claves de las propiedades (una alternativa para la tilde final `~`)  | `Set<E>`    |
| concat(X)                 | Proporciona una versión concatenada de la salida de la ruta con un nuevo elemento | like input  |
| append(X)                 | agrega un elemento al arreglo de salida de json path                | like input  |

## Operadores de filtro

Los filtros son expresiones lógicas usadas para filtrar arreglos. Un filtro típico sería `[?(@.age > 18)]`, donde `@` representa el elemento actual que se está procesando. Se pueden crear filtros más complejos con los operadores lógicos `&&` y `||`. Los literales de cadena deben ir entre comillas simples o dobles (`[?(@.color == 'blue')]` o `[?(@.color == "blue")]`).   

| Operador                 | Descripción                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | el valor de la izquierda es igual al de la derecha (nota que 1 no es igual a '1')              |
| !=                       | el valor de la izquierda es distinto al de la derecha                                            |
| <                        | el valor de la izquierda es menor que el de la derecha                                               |
| <=                       | el valor de la izquierda es menor o igual que el de la derecha                                        |
| >                        | el valor de la izquierda es mayor que el de la derecha                                            |
| >=                       | el valor de la izquierda es mayor o igual que el de la derecha                                |
| =~                       | el valor de la izquierda coincide con la expresión regular  [?(@.name =~ /foo.*?/i)]             |
| in                       | el valor de la izquierda existe en el de la derecha [?(@.size in ['S', 'M'])]       |
| nin                      | el valor de la izquierda no existe en el de la derecha                                         |
| subsetof                 | el valor de la izquierda es un subconjunto del de la derecha [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | el valor de la izquierda tiene intersección con el de la derecha [?(@.sizes anyof ['M', 'L'])]    |
| noneof                   | el valor de la izquierda no tiene intersección con el de la derecha [?(@.sizes noneof ['M', 'L'])]    |
| size                     | el tamaño del valor de la izquierda (arreglo o cadena) debe coincidir con el de la derecha                     |
| empty                    | el valor de la izquierda (arreglo o cadena) debe estar vacío                                |


## Ejemplos de rutas

Dado el JSON

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

| JsonPath (haz clic en el enlace para probar) | Resultado |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Los autores de todos los libros     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Todos los autores                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Todo, tanto libros como bicicletas  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | El precio de todo         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | El tercer libro                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | El penúltimo libro            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Los primeros dos libros               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Todos los libros desde el índice 0 (incluido) hasta el índice 2 (excluido) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Todos los libros desde el índice 1 (incluido) hasta el índice 2 (excluido) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Los últimos dos libros                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | El libro número dos desde el final          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Todos los libros con número ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Todos los libros de la tienda que cuestan menos de 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Todos los libros de la tienda que no son "caros"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Todos los libros que coinciden con la expresión regular (sin distinguir mayúsculas y minúsculas)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Dame todo   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | La cantidad de libros                      |
