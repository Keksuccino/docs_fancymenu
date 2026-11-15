---
title: JSON 경로
description: JSON Parser 플레이스홀더에서 Jayway JsonPath를 사용하는 방법입니다.
excludeFromAiPlaintext: true
sourceBlobSha: 2aa2965bffefdb17d944b31190f40ec33198c1e4
---
# FancyMenu의 JSON 경로

FancyMenu의 **JSON Parser** 플레이스홀더는 [Jayway JsonPath](https://github.com/json-path/JsonPath)를 사용하여 JSON 파일에서 콘텐츠를 가져옵니다.
이 페이지에서는 JSON 경로를 자세히 설명합니다.

이 페이지의 텍스트는 Jayway JsonPath의 GitHub 저장소에 있는 README를 복사한 것입니다.

> [!NOTE]
> 이 텍스트에서 "JsonPath 표현식"이라는 용어는 JSON 경로를 의미합니다.

# JsonPath

JsonPath 표현식은 XML 문서와 함께 XPath 표현식을 사용하는 것과 같은 방식으로 JSON 구조를 참조합니다. JsonPath의 "루트 멤버 객체"는 객체인지 배열인지에 관계없이 항상 `$`로 나타냅니다.

JsonPath 표현식에는 점 표기법을 사용할 수 있습니다.

`$.store.book[0].title`

또는 대괄호 표기법을 사용할 수 있습니다.

`$['store']['book'][0]['title']`

## 연산자

| 연산자                    | 설명                                                               |
| :------------------------ | :----------------------------------------------------------------- |
| `$`                       | 조회할 루트 요소입니다. 모든 경로 표현식은 여기에서 시작합니다.       |
| `@`                       | 필터 조건에서 현재 처리 중인 노드입니다.                            |
| `*`                       | 와일드카드입니다. 이름 또는 숫자가 필요한 모든 위치에서 사용할 수 있습니다. |
| `..`                      | 전체 검색입니다. 이름이 필요한 모든 위치에서 사용할 수 있습니다.      |
| `.<name>`                 | 점 표기법으로 지정한 자식 요소입니다.                                |
| `['<name>' (, '<name>')]` | 대괄호 표기법으로 지정한 자식 요소 또는 자식 요소들입니다.            |
| `[<number> (, <number>)]` | 배열 인덱스 또는 인덱스들입니다.                                    |
| `[start:end]`             | 배열 슬라이스 연산자입니다.                                         |
| `[?(<expression>)]`       | 필터 표현식입니다. 표현식은 불리언 값으로 평가되어야 합니다.         |


## 함수

함수는 경로의 끝에서 호출할 수 있으며, 함수의 입력은 경로 표현식의 출력입니다.
함수의 출력 형식은 함수 자체에 따라 결정됩니다.

| 함수                      | 설명                                                               | 출력 형식 |
| :------------------------ | :----------------------------------------------------------------- |:----------- |
| min()                     | 숫자 배열의 최솟값을 반환합니다.                                    | Double      |
| max()                     | 숫자 배열의 최댓값을 반환합니다.                                    | Double      |
| avg()                     | 숫자 배열의 평균값을 반환합니다.                                    | Double      | 
| stddev()                  | 숫자 배열의 표준 편차를 반환합니다.                                  | Double      | 
| length()                  | 배열의 길이를 반환합니다.                                           | Integer     |
| sum()                     | 숫자 배열의 합계를 반환합니다.                                      | Double      |
| keys()                    | 속성 키를 반환합니다(터미널 물결표 `~`의 대안).                     | `Set<E>`    |
| concat(X)                 | 새 항목을 추가하여 경로 출력을 연결한 결과를 반환합니다.              | 입력과 동일 |
| append(X)                 | JSON 경로 출력 배열에 항목을 추가합니다.                             | 입력과 동일 |

## 필터 연산자

필터는 배열을 필터링하는 데 사용되는 논리 표현식입니다. 일반적인 필터는 `[?(@.age > 18)]`과 같으며, 여기서 `@`는 현재 처리 중인 항목을 나타냅니다. 논리 연산자 `&&`와 `||`를 사용하여 더 복잡한 필터를 만들 수 있습니다. 문자열 리터럴은 작은따옴표 또는 큰따옴표로 묶어야 합니다(`[?(@.color == 'blue')]` 또는 `[?(@.color == "blue")]`).   

| 연산자                   | 설명                                                                  |
| :----------------------- | :-------------------------------------------------------------------- |
| ==                       | 왼쪽이 오른쪽과 같습니다(1은 '1'과 같지 않음에 유의하세요).             |
| !=                       | 왼쪽이 오른쪽과 같지 않습니다.                                        |
| <                        | 왼쪽이 오른쪽보다 작습니다.                                           |
| <=                       | 왼쪽이 오른쪽보다 작거나 같습니다.                                    |
| >                        | 왼쪽이 오른쪽보다 큽니다.                                              |
| >=                       | 왼쪽이 오른쪽보다 크거나 같습니다.                                    |
| =~                       | 왼쪽이 정규 표현식과 일치합니다 `[?(@.name =~ /foo.*?/i)]`.             |
| in                       | 왼쪽이 오른쪽에 포함되어 있습니다 `[?(@.size in ['S', 'M'])]`.          |
| nin                      | 왼쪽이 오른쪽에 포함되어 있지 않습니다.                               |
| subsetof                 | 왼쪽이 오른쪽의 부분 집합입니다 `[?(@.sizes subsetof ['S', 'M', 'L'])]`. |
| anyof                    | 왼쪽과 오른쪽이 교집합을 가집니다 `[?(@.sizes anyof ['M', 'L'])]`.       |
| noneof                   | 왼쪽과 오른쪽이 교집합을 가지지 않습니다 `[?(@.sizes noneof ['M', 'L'])]`. |
| size                     | 왼쪽(배열 또는 문자열)의 크기가 오른쪽과 일치해야 합니다.              |
| empty                    | 왼쪽(배열 또는 문자열)이 비어 있어야 합니다.                          |


## 경로 예시

다음 JSON이 주어졌다고 가정합니다.

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

| JsonPath (링크를 클릭하여 테스트) | 결과 |
| :------- | :----- |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[*].author" target="_blank">$.store.book[*].author</a>| 모든 책의 저자     |
| <a href="http://jsonpath.herokuapp.com/?path=$..author" target="_blank">$..author</a>                   | 모든 저자                         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.*" target="_blank">$.store.*</a>                  | 책과 자전거를 포함한 모든 항목  |
| <a href="http://jsonpath.herokuapp.com/?path=$.store..price" target="_blank">$.store..price</a>             | 모든 항목의 가격         |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[2]</a>                 | 세 번째 책                      |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2]" target="_blank">$..book[-2]</a>                 | 뒤에서 두 번째 책            |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[0,1]" target="_blank">$..book[0,1]</a>               | 처음 두 권의 책               |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[:2]" target="_blank">$..book[:2]</a>                | 인덱스 0(포함)부터 인덱스 2(제외)까지의 모든 책 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[1:2]" target="_blank">$..book[1:2]</a>                | 인덱스 1(포함)부터 인덱스 2(제외)까지의 모든 책 |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[-2:]" target="_blank">$..book[-2:]</a>                | 마지막 두 권의 책                   |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[2:]" target="_blank">$..book[2:]</a>                | 뒤에서 두 번째 책부터의 책          |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.isbn)]" target="_blank">$..book[?(@.isbn)]</a>          | ISBN 번호가 있는 모든 책         |
| <a href="http://jsonpath.herokuapp.com/?path=$.store.book[?(@.price < 10)]" target="_blank">$.store.book[?(@.price < 10)]</a> | 매장에서 가격이 10보다 저렴한 모든 책  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.price <= $['expensive'])]" target="_blank">$..book[?(@.price <= $['expensive'])]</a> | 매장에서 "비싼" 가격이 아닌 모든 책  |
| <a href="http://jsonpath.herokuapp.com/?path=$..book[?(@.author =~ /.*REES/i)]" target="_blank">$..book[?(@.author =~ /.*REES/i)]</a> | 정규 표현식과 일치하는 모든 책(대소문자 무시)  |
| <a href="http://jsonpath.herokuapp.com/?path=$..*" target="_blank">$..*</a>                        | 모든 항목 반환   
| <a href="http://jsonpath.herokuapp.com/?path=$..book.length()" target="_blank">$..book.length()</a>                 | 책의 수                      |
