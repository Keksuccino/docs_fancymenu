---
title: Caminhos JSON
description: Como usar o Jayway JsonPath no placeholder do JSON Parser.
---

# Caminhos JSON no FancyMenu

O placeholder **JSON Parser** do FancyMenu usa [Jayway JsonPath](https://github.com/json-path/JsonPath) para obter conteúdo de arquivos JSON.
Esta página explica caminhos JSON em detalhes.

O texto nesta página é uma cópia do README do repositório GitHub do Jayway JsonPath.

> [!NOTE]
> Neste texto, o termo "expressão JsonPath" refere-se a um caminho JSON.

# JsonPath

As expressões JsonPath sempre se referem a uma estrutura JSON da mesma forma que as expressões XPath são usadas em conjunto 
com um documento XML. O "objeto membro raiz" no JsonPath é sempre referido como `$`, independentemente de ser um 
objeto ou array.

As expressões JsonPath podem usar a notação com ponto

`$.store.book[0].title`

ou a notação com colchetes

`$['store']['book'][0]['title']`

## Operadores

| Operador                 | Descrição                                                         |
| :----------------------- | :---------------------------------------------------------------- |
| `$`                      | O elemento raiz a ser consultado. Isso inicia todas as expressões de caminho. |
| `@`                      | O nó atual sendo processado por um predicado de filtro.           |
| `*`                      | Coringa. Disponível em qualquer lugar em que nome ou número sejam necessários. |
| `..`                     | Varredura profunda. Disponível em qualquer lugar em que um nome seja necessário. |
| `.<name>`                | Filho com notação por ponto                                       |
| `['<name>' (, '<name>')]` | Filho(s) com notação por colchetes                               |
| `[<number> (, <number>)]` | Índice ou índices de array                                       |
| `[start:end]`            | Operador de fatiamento de array                                  |
| `[?(<expression>)]`      | Expressão de filtro. A expressão deve resultar em um valor booleano. |


## Funções

As funções podem ser invocadas no final de um caminho - a entrada de uma função é o resultado da expressão de caminho.
A saída da função é determinada pela própria função.

| Função                   | Descrição                                                          | Tipo de saída |
| :----------------------- | :----------------------------------------------------------------- |:----------- |
| min()                    | Fornece o valor mínimo de um array de números                       | Double      |
| max()                    | Fornece o valor máximo de um array de números                       | Double      |
| avg()                    | Fornece o valor médio de um array de números                        | Double      | 
| stddev()                 | Fornece o valor do desvio padrão de um array de números             | Double      | 
| length()                 | Fornece o comprimento de um array                                    | Integer     |
| sum()                    | Fornece o valor da soma de um array de números                       | Double      |
| keys()                   | Fornece as chaves das propriedades (uma alternativa para o til terminal `~`)  | `Set<E>`    |
| concat(X)                | Fornece uma versão concatenada da saída do caminho com um novo item  | igual à entrada  |
| append(X)                | adiciona um item ao array de saída do json path                      | igual à entrada  |

## Operadores de Filtro

Filtros são expressões lógicas usadas para filtrar arrays. Um filtro típico seria `[?(@.age > 18)]`, em que `@` representa o item atual sendo processado. Filtros mais complexos podem ser criados com os operadores lógicos `&&` e `||`. Literais de string devem ser colocados entre aspas simples ou duplas (`[?(@.color == 'blue')]` ou `[?(@.color == "blue")]`).   

| Operador                | Descrição                                                           |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | o lado esquerdo é igual ao lado direito (observe que 1 não é igual a '1')              |
| !=                       | o lado esquerdo é diferente do lado direito                           |
| <                        | o lado esquerdo é menor que o lado direito                            |
| <=                       | o lado esquerdo é menor ou igual ao lado direito                      |
| >                        | o lado esquerdo é maior que o lado direito                            |
| >=                       | o lado esquerdo é maior ou igual ao lado direito                       |
| =~                       | o lado esquerdo corresponde a uma expressão regular  [?(@.name =~ /foo.*?/i)]             |
| in                       | o lado esquerdo existe no lado direito [?(@.size in ['S', 'M'])]       |
| nin                      | o lado esquerdo não existe no lado direito                              |
| subsetof                 | o lado esquerdo é um subconjunto do lado direito [?(@.sizes subsetof ['S', 'M', 'L'])]       |
| anyof                    | o lado esquerdo tem interseção com o lado direito [?(@.sizes anyof ['M', 'L'])]    |
| noneof                   | o lado esquerdo não tem interseção com o lado direito [?(@.sizes noneof ['M', 'L'])]    |
| size                     | o tamanho do lado esquerdo (array ou string) deve corresponder ao lado direito                     |
| empty                    | o lado esquerdo (array ou string) deve estar vazio                                |


## Exemplos de Caminhos

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
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | Todos os livros do índice 0 (inclusive) até o índice 2 (exclusivo) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | Todos os livros do índice 1 (inclusive) até o índice 2 (exclusivo) |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | Os dois últimos livros                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | O livro número dois a partir do fim          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | Todos os livros com um número ISBN         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | Todos os livros da loja mais baratos que 10  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | Todos os livros da loja que não são "caros"  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | Todos os livros que correspondem à regex (ignorar maiúsculas/minúsculas)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | Me dê tudo   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | O número de livros                      |
