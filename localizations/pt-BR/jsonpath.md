---
title: Caminhos JSON
description: Como usar o Jayway JsonPath no placeholder JSON Parser.
---

# Caminhos JSON no FancyMenu

O placeholder **JSON Parser** do FancyMenu usa [Jayway JsonPath](https://github.com/json-path/JsonPath) para obter conteúdo de arquivos JSON.
Esta página explica caminhos JSON em detalhes.

O texto desta página é uma cópia do README do repositório GitHub do Jayway JsonPath.

> Neste texto, o termo "expressão JsonPath" se refere a um caminho JSON.
{.is-info}

# JsonPath

As expressões JsonPath sempre se referem a uma estrutura JSON da mesma forma que as expressões XPath são usadas em conjunto 
com um documento XML. O "objeto membro raiz" no JsonPath é sempre referido como `$`, independentemente de ser um 
objeto ou array.

As expressões JsonPath podem usar a notação de ponto

`$.store.book[0].title`

ou a notação de colchetes

`$['store']['book'][0]['title']`

## Operadores

| Operador                 | Descrição                                                       |
| :----------------------- | :-------------------------------------------------------------- |
| `$`                      | O elemento raiz a ser consultado. Inicia todas as expressões de caminho. |
| `@`                      | O nó atual sendo processado por um predicado de filtro.         |
| `*`                      | Caracter curinga. Disponível em qualquer lugar onde um nome ou número seja necessário. |
| `..`                     | Varredura profunda. Disponível em qualquer lugar onde um nome seja necessário. |
| `.<name>`                | Filho com notação de ponto                                      |
| `['<name>' (, '<name>')]`| Filho(s) com notação de colchetes                               |
| `[<number> (, <number>)]`| Índice(s) de array                                             |
| `[start:end]`            | Operador de fatiamento de array                                 |
| `[?(<expression>)]`      | Expressão de filtro. A expressão deve ser avaliada como um valor booleano. |


## Funções

As funções podem ser invocadas no final de um caminho - a entrada de uma função é a saída da expressão de caminho.
A saída da função é determinada pela própria função.

| Função                   | Descrição                                                          | Tipo de saída |
| :----------------------- | :----------------------------------------------------------------- |:------------ |
| min()                    | Fornece o valor mínimo de um array de números                       | Double      |
| max()                    | Fornece o valor máximo de um array de números                       | Double      |
| avg()                    | Fornece o valor médio de um array de números                         | Double      | 
| stddev()                 | Fornece o valor do desvio padrão de um array de números              | Double      | 
| length()                 | Fornece o comprimento de um array                                    | Integer     |
| sum()                    | Fornece o valor da soma de um array de números                        | Double      |
| keys()                   | Fornece as chaves das propriedades (uma alternativa para o til terminal `~`)  | `Set<E>`    |
| concat(X)                | Fornece uma versão concatenada da saída do caminho com um novo item    | como a entrada |
| append(X)                | Adiciona um item ao array de saída do json path                       | como a entrada |

## Operadores de Filtro

Filtros são expressões lógicas usadas para filtrar arrays. Um filtro típico seria `[?(@.age > 18)]`, onde `@` representa o item atual sendo processado. Filtros mais complexos podem ser criados com os operadores lógicos `&&` e `||`. Literais de string devem estar entre aspas simples ou duplas (`[?(@.color == 'blue')]` ou `[?(@.color == "blue")]`).   

| Operador                 | Descrição                                                            |
| :----------------------- | :------------------------------------------------------------------- |
| ==                       | o valor à esquerda é igual ao da direita (observe que 1 não é igual a '1') |
| !=                       | o valor à esquerda é diferente do da direita                        |
| <                        | o valor à esquerda é menor que o da direita                          |
| <=                       | o valor à esquerda é menor ou igual ao da direita                    |
| >                        | o valor à esquerda é maior que o da direita                          |
| >=                       | o valor à esquerda é maior ou igual ao da direita                    |
| =~                       | o valor à esquerda corresponde à expressão regular  [?(@.name =~ /foo.*?/i)] |
| in                       | o valor à esquerda existe no da direita [?(@.size in ['S', 'M'])]    |
| nin                      | o valor à esquerda não existe no da direita                         |
| subsetof                 | o valor à esquerda é um subconjunto do da direita [?(@.sizes subsetof ['S', 'M', 'L'])] |
| anyof                    | o valor à esquerda tem uma interseção com o da direita [?(@.sizes anyof ['M', 'L'])] |
| noneof                   | o valor à esquerda não tem interseção com o da direita [?(@.sizes noneof ['M', 'L'])] |
| size                     | o tamanho do valor à esquerda (array ou string) deve corresponder ao da direita |
| empty                    | o valor à esquerda (array ou string) deve estar vazio               |


## Exemplos de Caminho

Dado o json

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

| JsonPath (clique no link para testar)| Resultado |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| Os autores de todos os livros     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | Todos os autores                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | Tudo, tanto livros quanto bicicletas  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | O preço de tudo         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | O terceiro livro                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | O penúltimo livro            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | Os dois primeiros livros               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Todos os livros do índice 0 (inclusivo) até o índice 2 (exclusivo) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Todos os livros do índice 1 (inclusivo) até o índice 2 (exclusivo) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Os dois últimos livros                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | O livro número dois a partir do fim          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Todos os livros com um número ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Todos os livros da loja mais baratos que 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Todos os livros da loja que não são "caros"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Todos os livros que correspondem à expressão regular (ignorar maiúsculas/minúsculas)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Mostre tudo   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | O número de livros                      |
