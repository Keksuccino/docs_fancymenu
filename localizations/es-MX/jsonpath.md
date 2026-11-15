---
title: Rutas JSON
description: Cómo usar Jayway JsonPath en el marcador de posición del analizador JSON.
excludeFromAiPlaintext: true
sourceBlobSha: 2aa2965bffefdb17d944b31190f40ec33198c1e4
---
# Rutas JSON en FancyMenu

El marcador de posición **Analizador JSON** de FancyMenu usa [Jayway JsonPath](https://github.com/json-path/JsonPath) para obtener contenido de archivos JSON.
Esta página explica las rutas JSON en detalle.

El texto de esta página es una copia del README del repositorio de Jayway JsonPath en GitHub.

> [!NOTE]
> En este texto, el término "expresión JsonPath" se refiere a una ruta JSON.

# JsonPath

Las expresiones JsonPath siempre hacen referencia a una estructura JSON, de la misma manera que las expresiones XPath se usan junto con un documento XML. El "objeto miembro raíz" en JsonPath siempre se representa como `$`, independientemente de si es un objeto o un arreglo.

Las expresiones JsonPath pueden usar la notación de punto

`$.store.book[0].title`

 o la notación de corchetes

`$['store']['book'][0]['title']`

## Operadores

| Operador                  | Descripción                                                        |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | El elemento raíz que se consultará. Todas las expresiones de ruta comienzan aquí. |
| `@`                       | El nodo actual que procesa un predicado de filtro.                 |
| `*`                       | Comodín. Disponible donde se requiera un nombre o un valor numérico. |
| `..`                      | Búsqueda profunda. Disponible donde se requiera un nombre.        |
| `.<name>`                 | Hijo con notación de punto                                          |
| `['<name>' (, '<name>')]` | Hijo o hijos con notación de corchetes                              |
| `[<number> (, <number>)]` | Índice o índices del arreglo                                       |
| `[start:end]`             | Operador de segmento de arreglo                                    |
| `[?(<expression>)]`       | Expresión de filtro. La expresión debe evaluarse como un valor booleano. |


## Funciones

Las funciones pueden invocarse al final de una ruta; la entrada de una función es el resultado de la expresión de ruta.
El resultado de la función depende de la propia función.

| Función                  | Descripción                                                         | Tipo de salida |
| :------------------------ | :------------------------------------------------------------------ |:----------- |
| min()                     | Proporciona el valor mínimo de un arreglo de números               | Double      |
| max()                     | Proporciona el valor máximo de un arreglo de números               | Double      |
| avg()                     | Proporciona el valor promedio de un arreglo de números              | Double      | 
| stddev()                  | Proporciona la desviación estándar de un arreglo de números         | Double      | 
| length()                  | Proporciona la longitud de un arreglo                              | Integer     |
| sum()                     | Proporciona la suma de un arreglo de números                        | Double      |
| keys()                    | Proporciona las claves de propiedad (una alternativa a la tilde final `~`) | `Set<E>`    |
| concat(X)                 | Proporciona una versión concatenada del resultado de la ruta con un elemento nuevo | igual que la entrada |
| append(X)                 | Agrega un elemento al arreglo de resultados de la ruta JSON         | igual que la entrada |

## Operadores de filtro

Los filtros son expresiones lógicas que se usan para filtrar arreglos. Un filtro típico sería `[?(@.age > 18)]`, donde `@` representa el elemento actual que se está procesando. Se pueden crear filtros más complejos con los operadores lógicos `&&` y `||`. Los literales de cadena deben estar encerrados entre comillas sencillas o dobles (`[?(@.color == 'blue')]` o `[?(@.color == "blue")]`).   

| Operador                 | Descripción                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | la izquierda es igual a la derecha (ten en cuenta que 1 no es igual a '1') |
| !=                       | la izquierda no es igual a la derecha                                 |
| <                        | la izquierda es menor que la derecha                                  |
| <=                       | la izquierda es menor o igual que la derecha                          |
| >                        | la izquierda es mayor que la derecha                                  |
| >=                       | la izquierda es mayor o igual que la derecha                          |
| =~                       | la izquierda coincide con la expresión regular `[?(@.name =~ /foo.*?/i)]` |
| in                       | la izquierda existe en la derecha `[?(@.size in ['S', 'M'])]`        |
| nin                      | la izquierda no existe en la derecha                                  |
| subsetof                 | la izquierda es un subconjunto de la derecha `[?(@.sizes subsetof ['S', 'M', 'L'])]` |
| anyof                    | la izquierda tiene una intersección con la derecha `[?(@.sizes anyof ['M', 'L'])]` |
| noneof                   | la izquierda no tiene ninguna intersección con la derecha `[?(@.sizes noneof ['M', 'L'])]` |
| size                     | el tamaño de la izquierda (arreglo o cadena) debe coincidir con la derecha |
| empty                    | la izquierda (arreglo o cadena) debe estar vacía                      |


## Ejemplos de rutas

Dado el siguiente JSON

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

| JsonPath (haz clic en el enlace para probarlo) | Resultado |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Los autores de todos los libros     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Todos los autores                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Todos los elementos, tanto libros como bicicletas  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | El precio de todo         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | El tercer libro                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | El penúltimo libro            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Los dos primeros libros               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Todos los libros desde el índice 0 (inclusive) hasta el índice 2 (exclusive) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Todos los libros desde el índice 1 (inclusive) hasta el índice 2 (exclusive) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Los dos últimos libros                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | El libro número dos contando desde el final          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Todos los libros con número ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Todos los libros de la tienda que cuestan menos de 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Todos los libros de la tienda que no son "caros"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Todos los libros que coinciden con la expresión regular (sin distinguir mayúsculas y minúsculas)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Muéstrame todo   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | La cantidad de libros                      |
